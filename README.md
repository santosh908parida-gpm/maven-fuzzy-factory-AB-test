# maven-fuzzy-factory-AB-test
A/B test analysis of homepage vs new landing page — Growth PM case study
# Landing Page A/B Test Analysis — Maven Fuzzy Factory

A growth PM case study analyzing whether a new landing page reduced bounce rate on cold paid-search traffic.

## The Problem

Maven Fuzzy Factory (an online children's toy retailer) had an unusually high homepage bounce rate of ~60%. The marketing team built a new landing page (`/lander-1`) and tested it against the original homepage (`/home`) for nonbrand paid-search traffic.

**The question:** Did the new landing page drive a statistically significant improvement?

## My Approach

1. **Scoped the test window from raw data** — identified June 19, 2012 to January 13, 2013 as the clean two-way test period (before `/lander-2` muddied the experiment).
2. **Identified the test segment** — confirmed via UTM data that the test was run on nonbrand paid search traffic only.
3. **Found true landing pages** — for each session, identified the first pageview (since `/home` is also an internal page that visitors navigate back to).
4. **Calculated bounce rates** — sessions with exactly one pageview, divided by total sessions, per variant.
5. **Ran statistical significance testing** — two-proportion z-test to verify the difference wasn't random noise.

## Findings

| Variant | Sessions | Bounces | Bounce Rate |
|---|---|---|---|
| `/home` (control) | 2,328 | 1,365 | **58.63%** |
| `/lander-1` (treatment) | 42,617 | 22,661 | **53.17%** |

- **Absolute improvement:** 5.46 percentage points
- **Relative improvement:** 9.31%
- **P-value:** < 0.000001 (highly significant)
- **95% confidence interval:** [3.40%, 7.52%]

## Recommendation

**Roll out `/lander-1` to 100% of nonbrand paid search traffic.**

The improvement is statistically significant with a large effect size. Even the pessimistic end of the confidence interval (3.4 percentage points) represents a meaningful reduction in wasted ad spend.

### Caveats and next steps
- Sample sizes were imbalanced (95/5 favoring `/lander-1`), suggesting this was likely a gradual rollout rather than a strict 50/50 split.
- Bounce rate improvement should be validated against downstream metrics (conversion rate, revenue per session).
- The company ran subsequent tests (`/lander-2`, `/lander-3`, etc.) — natural follow-up is to analyze whether each iteration kept improving things.

## Tech Used

- **Python** (pandas, scipy)
- Data: Maven Fuzzy Factory sample dataset

## Files

- `ab_test_analysis.py` — full analysis script
- `website_pageviews.csv` — source pageview data(could not be uploaded due to bigger size)
- `website_sessions.csv` — source session data(could not be uploaded due to bigger size)
