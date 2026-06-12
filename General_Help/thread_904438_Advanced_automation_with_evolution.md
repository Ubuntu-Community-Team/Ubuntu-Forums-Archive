---
title: "Advanced automation with evolution?"
date: 2008-08-29
forum: General Help
---

### Post by QwUo173Hy on 2008-08-29
I find the signatures feature in Evolution really handy for sending standard emails to common queries we get in our business. Is it possible to make them even more complete by including a subject title in the template and such?

---

### Post by Cheesehead on 2008-08-29
Subject line from the *signature* template? No.

However...
You CAN use the filters (which will pipe and run commands based on criteria in the mail that you specify) and a script to generate custom Evolution e-mail.

For example,
If an e-mail arrives that says "My foo isn't working",
your rule catches the item and pipes it to the script.

Your script parses the e-mail (question? complaint? compliment?) and composes the correct stock response. "Foo is inert. Just sitting there *is* working properly. Can you send us a video of it spontaneously moving? Love, Your Company"

Obviously, your script can be very complex, or very simple, depending on your needs.

Your script creates the evolution e-mail using a shell command, complete with e-mail address, subject, body, and attachments.


I use this system for invoicing my customers, sending an e-mail duplicate of the mailed invoice from Evolution.

This works very well for e-mail *that you review* before sending. Evolution has no method to send unattended e-mail.

-----

If all you need is the shell command for Evolution,
```
evolution mailto:person@example.com?cc="second_person@example.com"\&subject="This Is The Subject"\&body="This is the body of the message"\&attach=path/to/test_file1.odt\&attach=path/to/test_file2.odt
```

---

### Post by QwUo173Hy on 2008-08-30
Wow, thank you so much Cheesehead. I couldn't have hoped for a more informative reply! That's exactly what I'm looking for. I have a book on scripting so I'll look into the parsing side of things as well.

Thank you so much,
Jarlath

---

### Post by QwUo173Hy on 2008-09-14
Can someone point me to some further info on the scripting side of things? Theres nothing in the Evolution help files or in the PDF on their website, except for the very basics.

I use HTML emails to embed the company logo etc. I currenly have a signature set up with this and a standard invoice, but I can't select the signature from the command line at the moment.

Even better again would be if I could run a filter on a message that would take the senders name and insert it into my "Dear <name>" part of the message body. Is this stuff possible?

---

