>   **SENG 438 - Software Testing, Reliability, and Quality**

**Lab. Report \#1 – Introduction to Testing and Defect Tracking**

| Group: 18      |
|-----------------|
| Abdul Rafay                |   
| Mohammed Azmath Khan              |   
| Taiwu Chen               |   
| Hashir Naved                |   


**Table of Contents**

(When you finish writing, update the following list using right click, then
“Update Field”)

[1 Introduction	1](#_Toc439194677)

[2 High-level description of the exploratory testing plan	1](#_Toc439194678)

[3 Comparison of exploratory and manual functional testing	1](#_Toc439194679)

[4 Notes and discussion of the peer reviews of defect reports	1](#_Toc439194680)

[5 How the pair testing was managed and team work/effort was
divided	1](#_Toc439194681)

[6 Difficulties encountered, challenges overcome, and lessons
learned	1](#_Toc439194682)

[7 Comments/feedback on the lab and lab document itself	1](#_Toc439194683)

# Introduction

The first lab focuses on understanding and practicing different software testing methods through an ATM simulation system. It introduces testing under three categories: exploratory, manual scripted, and regression testing. Using these methods, the lab highlights different ways to identify software defects. Additionally, it provides instructions on how to use a bug tracking system and properly track and document findings.

Prior to the lab, there was rudimentary knowledge of software testing. Testers typically interact freely with the software and note down any defects. However, the concept of a structured and detailed documentation process was new. This lab introduced real-world examples of software testing, showcasing multiple methods used in the industry.

# High-level description of the exploratory testing plan

The exploratory testing plan is aimed at finding defects in the ATM simulation system by simulating real world user interactions. The plan focuses on testing authentication, transactions, system controls, and error handling to make sure the ATM functions correctly under different conditions. Since this is exploratory testing, there is no predefined script to follow, so the approach is more open ended, allowing testers to freely interact with the system and observe any unexpected behavior.

The testing begins with basic interactions like turning the system on and inserting a card. If the ATM starts properly and requests the initial cash amount, that is a sign the startup sequence is functioning correctly. The next step is verifying the authentication process by inserting a valid card and entering the correct PIN. If the PIN is accepted, the ATM should display the transaction menu. However, testing is not just about checking if things work, but also seeing how the system handles errors. For example, when entering an incorrect PIN, the system should display an error message and prompt for another attempt. During testing, the expected behavior was that the ATM would allow three attempts before retaining the card, and this was confirmed in the test results.

Another key part of exploratory testing is verifying transaction functionalities, such as withdrawals, deposits, transfers, and balance inquiries. The ATM should allow withdrawals within the account balance and ATM cash limits, and it should reject withdrawals that exceed these limits. A test was conducted where a withdrawal request was made for an amount higher than what was available in the ATM. The expected outcome was for the system to deny the request and notify the user, but during testing, the system incorrectly displayed that there was insufficient ATM cash when there was actually enough, showing a defect in cash verification.

Deposits were also tested by entering a valid amount and simulating envelope insertion. The ATM should accept the deposit, print a receipt, and update the balance. However, during the test, the receipt showed the correct deposit amount, but the updated balance was incorrect. This indicates an issue with how the system updates account balances after a deposit is made. Transfers were tested in a similar way, where a valid transfer amount was entered, and the expectation was that both account balances would be updated correctly. In one test, the receipt displayed incorrect details, and the balances did not update as expected, highlighting another defect.

Error handling and transaction cancellations were tested to see how the ATM responds to invalid inputs or when a user decides to cancel a transaction. A test was conducted where a withdrawal was started but canceled before confirming the amount. The system should have returned to the main menu, but instead, the transaction went through despite being canceled, which was a major defect. Another issue found was with the cancel button during a transfer. Even after pressing cancel, the transfer was still processed, which is a serious flaw because users should be able to stop a transaction at any stage before confirmation.

This exploratory testing approach helped uncover defects that may not have been noticed through scripted testing alone. By testing common actions like withdrawals and deposits, as well as edge cases like incorrect PIN attempts and system cancellations, the lab highlighted how exploratory testing can expose real-world issues in a system. The findings from these tests will be useful in refining the system and improving its reliability.

# Comparison of exploratory and manual functional testing

Exploratory testing and manual functional testing take very different approaches to finding defects in a system. Exploratory testing is open ended and relies on testers interacting with the system freely, following their intuition and curiosity to uncover bugs. Manual functional testing, on the other hand, follows a structured test plan with predefined steps, ensuring that every function is tested in a systematic way. Both methods have their strengths and weaknesses, and the lab demonstrated how they complement each other in real world software testing.

Exploratory testing allows testers to go beyond the expected and push the system in ways that may not have been considered during development. It gives room for creativity and helps in finding unexpected issues. For example, during exploratory testing, a withdrawal was made where the amount selected was within the ATM’s available cash, yet the system incorrectly displayed an error message saying there was insufficient cash. This was not something that would have necessarily been covered in a structured test plan, yet it revealed a serious flaw in how the ATM tracks its cash reserves. Another example came from deposit transactions, where a deposit was made successfully, but the balance was updated incorrectly. This kind of issue might not have been immediately obvious in a rigid test case but was discovered by freely interacting with the system and observing discrepancies in the outputs.

Manual functional testing, on the other hand, ensures that every feature is tested in a controlled and repeatable way. The structured nature of this testing makes it reliable for verifying expected behavior. Each test case has a defined starting condition, specific inputs, and an expected outcome. This helps confirm that the system is functioning correctly in the scenarios it was designed for. A good example from the lab was verifying the ATM’s ability to process balance inquiries. A test case was executed where a balance inquiry was performed on a checking account, and the expected output was for the correct balance to be displayed and logged. Since the system returned the correct balance, the test was marked as passed. Another example involved testing the system’s ability to reject invalid card insertions. A test case was performed where an unreadable card was inserted, and the ATM was expected to eject the card and display an error message. The system behaved exactly as expected, confirming that this function was working correctly.

While manual functional testing provides structure and ensures thorough coverage of all core functions, it does not always catch unexpected behaviors. The limitations of this approach became clear when testing transaction cancellations. A predefined test case was executed to check if a transaction could be canceled at different points. When canceling a withdrawal before selecting an amount, the system should have displayed a cancellation message and returned to the transaction menu. However, during exploratory testing, it was discovered that in some cases, the system did not display the cancellation message and instead ejected the card immediately. This was a behavior that was not explicitly covered in the test cases but was found when testers explored the system beyond the scripted steps.

Another key difference between the two approaches is the ability to adapt to new findings. Exploratory testing is flexible, allowing testers to quickly shift focus when they notice unusual behaviors. If something unexpected happens, testers can immediately investigate further, following the issue to see if it leads to deeper problems. In contrast, manual functional testing follows a set sequence, making it less adaptable. If a defect is found during a structured test case, it is logged, but the tester typically moves on to the next test rather than investigating further.

Both testing methods played an important role in the lab. Exploratory testing was effective in uncovering surprising defects that would not have been explicitly checked in a test plan. It allowed for a deeper understanding of how the ATM system behaves in different scenarios, particularly in edge cases. Manual functional testing ensured that all essential functions were tested in an organized and repeatable way, confirming that expected behaviors were working as designed. Together, these methods provided a well rounded approach to testing, making it clear why both are necessary in real world software development.

# Notes and discussion of the peer reviews of defect reports

We found, on reviewing the defect report of the other pair, several similarities of their test cases to ours, such as both teams tested the same core ATM functions: withdrawals, deposits, transfers, and balance checking, and therefore it would be expected that both pairs would replicate some tests on it. Another similarity: both sets of defect reports were clear and easy to follow. It made it so easy to redo the tests and pinpoint the mistakes in retesting.

However, there were some dissimilarities, one of which was a range of amounts tested in the examples of withdrawals and deposits; the variance revealed some mathematical problems had been programmed. Additionally, certain errors in the program’s outputs weren’t always documented by each team.

Ultimately, the possession of two sets of defect reports would serve to detect some of the other team's missed points for creating a better test set that would be much more thorough and precise.

# How the pair testing was managed and team work/effort was divided 

Pair testing was managed and divided in a way to ensure complete understanding and responsibility of each team member, with contributions evenly distributed at 25% each. The team was structured to maximize functionality and efficiency, allowing testing to be completed in a timely manner while making sure all aspects of the system were properly examined.

# Difficulties encountered, challenges overcome, and lessons learned

Some difficulties encountered included creation of tests and choosing highly effective tests that would ensure each functionality of the system is thoroughly operational. We used a implementation of generative AI to help, analyze and extract. Key tests required to analyze the functionality. This was integrated into exploratory testing from both pairs allowing a more in-depth review overall. Some lessons we learned as a team was how to write bug reports as well as clearly demonstrate testing of each functionality and identifying bugs efficiently. We also learned how to communicate and distribute work efficiently to create optimal results.

# Comments/feedback on the lab and lab document itself

The lab was very informative and gave a great introduction to different types of software testing. It provided a clear understanding of exploratory, manual scripted, and regression testing, allowing us to see firsthand how each method is used to identify defects. One of the biggest takeaways was the importance of detailed language in testing. It really drilled into us how critical it is to be precise in defect reports to ensure that issues can be properly replicated and addressed.

The lab was structured in a way that gave us a taste of everything, from identifying bugs to documenting them thoroughly. However, it also left us eager to go deeper into debugging the defects we found. While finding and reporting issues was valuable, we are excited to learn more about how to fix the problems uncovered during testing. Overall, it was a solid introduction to software testing, and we look forward to building on these skills in future labs.
