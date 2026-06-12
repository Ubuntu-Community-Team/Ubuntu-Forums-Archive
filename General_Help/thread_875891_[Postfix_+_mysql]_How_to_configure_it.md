---
title: "[Postfix + mysql] How to configure it?"
date: 2008-07-31
forum: General Help
---

### Post by sanocli on 2008-07-31
Hello everybody,

I would like that postfix look into my database mysql and act in function of the result he found.

Actually, what I really want is when a email arrived :

[LIST]
If the recipient email address is present in my database : 
[LIST]
If the sender is granted to send email to the recipient then we send the email   
[/LIST]
[LIST]
If the sender is blocked, destroy the email.    
[/LIST]
[LIST]
If the sender email address is not present for the recipient in my database then put the email in the HOLD directory and put some information in my database
[/LIST]
[/LIST]
[LIST]
else forward the mail to another smtp. 
[/LIST]

I have looking for information and I have seen that we can customize postfix editing the main.cf file and I certainly have to edit the source code of postfix.

So I think that to begin I have to verify the sender/recipient address in the main.cf and then at the end of the cleanup just verified if the mail are granted or not and effectuate the corresponding treatment.

Is this the good way to realize that I want?

Thank you for helping a postfix newbie like me and have a good day:)

---

