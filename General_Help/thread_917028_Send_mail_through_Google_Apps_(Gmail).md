---
title: "Send mail through Google Apps (Gmail)"
date: 2008-09-11
forum: General Help
---

### Post by glave on 2008-09-11
I have been trying for the last two days to get this to work properly, I'm close, but its still not happening.

I use Google Apps to host all of my email. I'm aiming to get my Hardy box to send emails out to Google Apps when it needs too. The only time this box should ever need to is for system messages, ie- cron is complaining, mdadm sends me something about the raid setup, etc.

I have tried several walkthroughs trying to get postfix to play nice with google. (Do I NEED postfix? I'm only sending email). Currently, I can kick something out via sendmail to anywhere at all and it works GREAT, except my own domain >.<  Emails to my own domain appear to be accepted just fine by google's smtp, but they never arrive. They don't hit spam, and I've got a catchall address where they don't show up either.


Do I need postfix for this? Nullmailer? Ruby? Anyone know what I could've missed that's making my own domain emails never arrive?

---

### Post by glave on 2008-09-11
:lolflag:


Well, I did even more investigating... I could send to any account at all, even OTHER gmail accounts... Once I noticed this, I dug deeper, and I discovered I could search my inbox and the emails have been there all along!!!!!!

...........since *I* technically was the sender to my own account, it was putting them in the Sent mail folder and marking them read, so I never saw them arrive....  :oops:

---

