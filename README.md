# Student Enrollment ETL Pipeline Using n8n and OpenAI

## Objective
Build an automated ETL workflow using n8n to extract enrollment data from a CSV, normalize inconsistent values using an OpenAI-powered Basic LLM Chain, validate records, remove duplicates, filter records, and export clean data.

## Workflow
1. Manual Trigger
2. Read/Write Files from Disk — read the input CSV
3. Extract from File — extract student rows
4. Basic LLM Chain with OpenAI Chat Model — standardize text fields
5. Code — validate email addresses, remove duplicate emails, and filter fee-paid records
6. Convert to File — generate the clean CSV
7. Read/Write Files from Disk — save the clean output

A separate branch sends records with missing or invalid email addresses to a review CSV.

## Cleaning Rules
- Trim leading and trailing whitespace.
- Normalize email addresses to lowercase.
- Standardize names, cities, and course names.
- Treat normalized email addresses as the unique student identifier.
- Keep the first occurrence of each valid email.
- Retain only records where Fee_Paid = Yes.
- Separate records with missing or invalid email addresses for manual review.

## Output Files
- students_clean.csv
- students_needs_review.csv

## Expected Results
- Input records: 50
- Records sent for email review: 21
- Valid-email records after deduplication: 29
- Records filtered out because Fee_Paid is not Yes: 10
- Clean output records: 19

## Conclusion
The workflow automates student enrollment data cleaning and export. It combines AI-assisted normalization with deterministic validation and filtering, while preserving records that require manual review.
