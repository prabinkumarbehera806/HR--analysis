# HR Workforce and Compensation Analysis

**Tools:** MySQL · Power BI · DAX  
**Domain:** Human Resources  
**Dataset:** 107 employees across 7 related tables

---

## Why I Built This

Most HR datasets sit in spreadsheets and nobody really looks at them closely. I wanted to take a structured HR database and ask the kind of questions a real HR manager or business head would care about — not just how many employees there are, but whether the company is actually set up to run well.

The dataset covers a mid-sized company called GlobalCorp with 107 employees spread across 12 departments in two regions, Americas and Europe. I looked at three things: how the workforce is structured, how salaries are distributed, and whether employees are actually growing inside the company.

> The company name is a placeholder. This analysis was done on a sample HR dataset with realistic structure.

---

## What the Data Looks Like

Seven tables connected together in a star schema inside Power BI.

| Table | What It Contains |
|---|---|
| hr_employees | Every employee — their role, department, salary, hire date, and manager |
| hr_departments | Department names and which location they belong to |
| hr_jobs | Job titles with salary bands — minimum and maximum for each role |
| hr_job_history | Records of employees who changed roles internally |
| hr_locations | City and country for each office |
| hr_countries | Maps each country to a region |
| hr_regions | Top level — Americas and Europe |

---

## Quick Numbers

| What | Number |
|---|---|
| Total Employees | 107 |
| Total Departments | 12 |
| Regions | 2 — Americas and Europe |
| Average Salary | $6,000 |
| Employees Who Changed Roles Internally | 6 out of 107 |
| Highest Late Delivery Rate | Alagoas — 23.93% |

---

## The Dashboard

The report has three pages. Each page focuses on one area.

---

### Page 1 — Workforce Structure

![Workforce Structure Dashboard](assets/screenshots/1.jpg)

**What I found:**

Shipping and Sales together have 74% of all employees — 45 in Shipping and 34 in Sales. Every other department has between 1 and 6 people. HR, Administration, and Public Relations each have exactly one person. That means if any one of those three people leaves, that entire function disappears overnight. There is no backup.

The management structure also does not make sense when you look at it closely. Steven manages 14 people. Several other managers manage just 1. There is no clear reason for this based on department size or seniority. Some managers are clearly stretched while others have almost nothing to manage.

Europe has 36 employees but they only work in 4 roles — Sales, Sales Manager, HR, and Public Relations. There are no European employees in IT, Finance, or Administration. That means if something goes wrong with the Americas office, the company has no technical or financial backup in Europe.

---

### Page 2 — Salary Distribution

![Salary Distribution Dashboard](assets/screenshots/2.jpg)

**What I found:**

This page surprised me the most. American employees work across many more departments and job types but earn an average of $5,000. European employees work in only 4 roles but earn an average of $9,000 — about 80% more. I could not find a clear reason for this based on job complexity or workload. It looks like salary is being driven by geography rather than what the job actually involves.

The manager pay problem becomes even clearer here. Lex manages 1 employee and earns near the top of the manager salary range. Several managers handling teams of 8 earn around $3,000. The pay is going in the wrong direction relative to responsibility.

South San Francisco is the biggest office with 45 employees, but their average salary is only $3,000 — half the company average. The team doing the most operational work is also the lowest paid. That is a retention risk that does not show up anywhere in the current reporting.

---

### Page 3 — Career Mobility and Tenure

![Career Mobility Dashboard](assets/screenshots/3.jpg)

**What I found:**

Only 6 out of 107 employees have ever changed roles inside the company. That is 5.6%. The other 94% have stayed in the same role since they joined. This could mean people are satisfied and stable, but combined with the low salaries in some departments, it more likely means there are no clear paths to move up.

The speed of career growth varies a lot. Steven stayed in one role for 69 months before moving. John went from Sales Representative to Sales Manager in 9 months. Sales is the only department where fast progression seems to happen regularly.

There was also an interesting pattern in the timeline — no internal job changes at all in 1997, then a jump to 4 by 1999. Something changed in that period. It could be a budget freeze, a restructuring, or a hiring pause. The data does not say, but it is worth asking.

---

## What I Would Recommend

| Area | The Problem | What Should Change |
|---|---|---|
| Workforce | HR, Admin, and PR each have one person | Cross-train at least one person in each of these functions as a backup |
| Management | Steven manages 14, others manage 1 | Review and redistribute reports so workloads are more balanced |
| Compensation | European employees earn 80% more for fewer roles | Audit pay bands against role complexity, not just location |
| Manager Pay | Salary does not match team size | Tie manager pay to span of control as a starting point |
| Career Growth | 94% of employees have never changed roles | Build a visible internal mobility programme — Sales already shows it is possible |

---

## How I Built It

**Step 1 — Understanding the data**  
I looked at all 7 tables, mapped the relationships between them, and checked for nulls and gaps before writing a single query.

**Step 2 — SQL analysis**  
I used MySQL to answer specific business questions — salary by region, manager span of control, internal transfer counts, tenure by role. I wrote the queries by hand and cross-checked the outputs before moving to visualisation.

**Step 3 — Power BI dashboard**  
I built the three-page report in Power BI using DAX measures and calculated columns. The star schema from the original dataset was preserved in the data model.

---

## A Few Things to Note

- This is a sample dataset. The company name and employee names are not real.
- Salaries are treated as monthly figures based on the scale of the numbers.
- One column — `hr_countries.total_salary` — was excluded because its definition was unclear and including it would have skewed the salary analysis.
- Null values in city and department fields were filtered out of visuals but the rows were kept in the dataset for other calculations.

---

*Prabin Kumar · B.Tech Computer Science and Engineering (Data Science) · 2024*  
*[GitHub](https://github.com/prabinkumarbehera806)*
