# Who Should We Try to Keep? A Churn Story from a Telco Snapshot

![Story overview](dashboard/00_story_overview.png)

## The situation
A telecom company in California lost 1,869 of its 7,043 customers in the third quarter, a churn rate of 26.54%. Those customers also carried 30.50% of all monthly charges, more than their share of the customer count. Losing customers is costly, but retention effort is limited. The question I set out to answer was:

**Which customer groups should be prioritized for retention evaluation, and what is the basis for choosing them?**

## Where the problem is concentrated
The first clue is the contract type. Month-to-Month customers are only 51.26% of the base, yet they make up 88.55% of everyone who left. Their churn rate is 45.84%, compared with 10.71% on one-year and 2.55% on two-year contracts. Since almost all churn sits in one contract type, the rest of the analysis focuses there.

Inside Month-to-Month, internet type and tenure separate the groups sharply. Fiber customers in their first 1–6 months churn at 77.49%, the highest of any group. Fiber customers with more than 6 months churn at 50.65%, but they are a bigger group, so they produce the most churners (663). Together, these two Fiber segments account for 68.7% of all churned monthly charges. Fiber on a monthly contract is where both the rate and the money are.

![Churn overview dashboard](dashboard/01_churn_overview.png)

## What these customers say and what their services show
The recorded reasons point outward. Competitor-related reasons are the most common, 841 of 1,869 churners, with better devices and better offers from competitors leading. In the two Fiber segments, 49.55% and 45.85% of churners recorded a competitor reason. Price comes up far less (211 churners). Churned and retained Fiber customers also pay almost the same median monthly charge, so the data does not suggest that price alone explains the exit.

Services add a second signal. Among Fiber monthly customers, churn is 65.7% for those with neither Online Security nor Premium Tech Support, against 41.6% for those with at least one. The gap appears in every tenure band. This group makes up 47.2% of all churners and 53.7% of churned charges. This is an association, not proof that adding the services would reduce churn.

## From patterns to a priority group
Churn history tells us who left, but retention work targets customers who are still here. Among active customers (Stayed or Joined), 775 are Fiber monthly customers, and 460 of them have neither Security nor Tech Support. These 460 customers are the focus group. Of them, 95 sit in the top CLTV quartile, which gives a sense of customer value but is not a prediction of who will churn.

![Retention priorities dashboard](dashboard/02_retention_priorities.png)

## What I would recommend
1. **Focus evaluation on Fiber monthly customers.** The two Fiber segments hold 68.7% of churned charges. Review the early experience of customers in months 1–6 and why customers beyond 6 months stay or leave. Track churn rate per group over the same period.
2. **Review offers and devices against competitors.** Competitor devices and offers are the leading specific reasons. Find out what customers see as better, then test changes against a comparison group. Measure the revenue benefit after the cost of the program.
3. **Check the need for Security and Tech Support.** Ask the 460 focus customers about their needs and obstacles. If a fix is tested, compare churn with a similar group that did not receive it, and track complaint resolution and satisfaction.

## What this analysis cannot say
The data is a single-quarter snapshot with no dates, so the churn rate here is a proportion, not a monthly or annual rate, and trends or cohorts cannot be built. Recorded reasons do not prove cause. Satisfaction Score and Churn Score look like they were measured after the customer left, so I did not use them as drivers. Acquisition cost cannot be computed because the data has no cost columns. Measuring whether a recommendation works needs follow-up data after an action is tested.

## Project files
| What | Where |
|---|---|
| Analysis notebook | [notebooks/Telco_Churn_Analysis.ipynb](notebooks/Telco_Churn_Analysis.ipynb) · [Open in Colab]([colab link]) |
| Power BI dashboard (2 pages) | [dashboard/Telco_Churn_Dashboard.pbix](dashboard/Telco_Churn_Dashboard.pbix) |
| Dashboard screenshots | [dashboard/](dashboard/) |
| Raw data | [data/raw/Telco_Churn_Data.zip](data/raw/Telco_Churn_Data.zip) |
| Power BI ready dataset | [data/processed/telco_churn_powerbi.csv](data/processed/telco_churn_powerbi.csv) |
| Slides (PDF) | [slides/Telco_Customer_Churn_Slides.pdf](slides/Telco_Customer_Churn_Slides.pdf) |

## How the analysis was built
Six source tables were merged into one row per customer. Missing values were treated by their meaning, for example "No Internet" and "Not Applicable". Eleven customers with tenure 0 were flagged for review rather than filled in. The notebook then moves from the overall churn rate to contract, internet type and tenure, reasons, services, and CLTV, and exports the dataset used by the dashboard.

## How to run
1. Open the notebook in Google Colab.
2. Upload `Telco_Churn_Data.zip` to Colab before running the notebook.
3. Run all cells. The final cell exports `telco_churn_powerbi.csv`.
4. Open the `.pbix` in Power BI Desktop (Windows).

*The infographic at the top was designed with AI assistance from my analysis results. All figures come from the notebook.*

Author: Sabila Rahma Utomo
