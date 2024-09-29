# Assignment 1: Design a Logical Model

## Question 1
Create a logical model for a small bookstore. 📚

At the minimum it should have employee, order, sales, customer, and book entities (tables). Determine sensible column and table design based on what you know about these concepts. Keep it simple, but work out sensible relationships to keep tables reasonably sized. Include a date table. There are several tools online you can use, I'd recommend [_Draw.io_](https://www.drawio.com/) or [_LucidChart_](https://www.lucidchart.com/pages/).

![Book_store_ERD](https://github.com/user-attachments/assets/b3609ff0-43d3-4283-ab16-72907ed7d1f2)

## Question 2

We want to create employee shifts, splitting up the day into morning and evening. Add this to the ERD.

![Book_store_ERD_shift_added](https://github.com/user-attachments/assets/a713118e-5516-4f1f-a8fd-75f62098b801)


## Question 3
The store wants to keep customer addresses. Propose two architectures for the CUSTOMER_ADDRESS table, one that will retain changes, and another that will overwrite. Which is type 1, which is type 2?

_Hint, search type 1 vs type 2 slowly changing dimensions._

Bonus: Are there privacy implications to this, why or why not?

There will be two architectural approaches for the customer addresses table, each utilizing a different Slowly Changing Dimension (SCD) type. This is because people typically don't change their primary residence frequently. Depending on whether we prioritize overwriting old address data or retaining a history of changes, each approach will have unique privacy implications:

Architecture 1 (type 1): Overwrite address

![Customer_adress_rewrite](https://github.com/user-attachments/assets/e15fd637-f9c4-4a61-befa-56cc43b6f7f7)

This approach raises fewer privacy concerns as it only stores the current address. However, it limits the ability to conduct trend analysis. On the other hand, given that this ERD is designed for a locally operated bookshop, this architecture may be more suitable for a starting business due to its simpler implementation and lower risk of data exposure.

Architecture 2 (type 2): Retain address
![Customer_adress_history](https://github.com/user-attachments/assets/90bad460-e788-4539-a448-898d5bbf7e7f)

Current customer's address will has an end_date of NULL. I believe this approach would be implemented when we initiate online or mail-order book sales.

## Question 4
Review the AdventureWorks Schema [here](https://i.stack.imgur.com/LMu4W.gif)

Highlight at least two differences between it and your ERD. Would you change anything in yours?
```
AdventureWorks schema is significantly more extensive and intricate, suggesting it models a larger and more complex business operation compared to the relatively simpler bookstore model.
First of all Schema modeling a wide array of business functions (Sales, Purchasing, Production, Human Resources etc) but my ERD focuses primarily on sales.
Secondly,AdventureWorks demonstrates a higher degree of establishing relationships within and between tables. This means a reliable and scalable data model.
Here are a few potential enhancements to the bookstore ERD:  introduce new entities to capture more business aspects. For instance, adding Suppliers to track book procurement, Shipping to manage order fulfillment, and Payments to record transaction details could enhance the model's functionality.
```

# Criteria

[Assignment Rubric](./assignment_rubric.md)

# Submission Information

🚨 **Please review our [Assignment Submission Guide](https://github.com/UofT-DSI/onboarding/blob/main/onboarding_documents/submissions.md)** 🚨 for detailed instructions on how to format, branch, and submit your work. Following these guidelines is crucial for your submissions to be evaluated correctly.

### Submission Parameters:
* Submission Due Date: `September 28, 2024`
* The branch name for your repo should be: `model-design`
* What to submit for this assignment:
    * This markdown (design_a_logical_model.md) should be populated.
    * Two Entity-Relationship Diagrams (preferably in a pdf, jpeg, png format).
* What the pull request link should look like for this assignment: `https://github.com/<your_github_username>/sql/pull/<pr_id>`
    * Open a private window in your browser. Copy and paste the link to your pull request into the address bar. Make sure you can see your pull request properly. This helps the technical facilitator and learning support staff review your submission easily.

Checklist:
- [ ] Create a branch called `model-design`.
- [ ] Ensure that the repository is public.
- [ ] Review [the PR description guidelines](https://github.com/UofT-DSI/onboarding/blob/main/onboarding_documents/submissions.md#guidelines-for-pull-request-descriptions) and adhere to them.
- [ ] Verify that the link is accessible in a private browser window.

If you encounter any difficulties or have questions, please don't hesitate to reach out to our team via our Slack at `#cohort-4-help`. Our Technical Facilitators and Learning Support staff are here to help you navigate any challenges.
