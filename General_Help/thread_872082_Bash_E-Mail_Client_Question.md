---
title: "Bash E-Mail Client Question"
date: 2008-07-27
forum: General Help
---

### Post by rzermatt on 2008-07-27
I have recently installed Ubuntu Server on one of my old PCs, and I was looking for a mail client I could run right out of the shell.

Just had a few specifics...

Since I just crossed over from Server 2003, I know outlook had a feature which could check for certain strings in email headers and then perform actions within the system. For example, I could have Outlook automatically check mail at an inbox every 10 minutes. If it found an email that had the subject line 'Shutdown' I could have it run a script to shut down the computer.

Are there any alternatives which can do the same thing on Ubuntu but right out of bash?

Just wondering...

Thanks in advance for all the help!

---

### Post by tamoneya on 2008-07-27
im not sure how to do it with bash but i have done a bunch of email stuff with python. (it had to be cross platform so bash wasnt an option).  You could write a python script and call it with a cron job.  The script could check for emails and then using the os module it could send commands to shutdown the computer or whatever else you like.

This should get you started on python email modules: [http://www.devshed.com/c/a/Python/Python-Email-Libraries-SMTP-and-Email-Parsing/](http://www.devshed.com/c/a/Python/Python-Email-Libraries-SMTP-and-Email-Parsing/)

---

### Post by ghostdog74 on 2008-07-27
your system should already have mail or mailx. You can use these tools to send your emails.
```

echo "test" | mailx -s "this is subject" recipient@somewhere.com

```
see the mailx/mail man page

---

### Post by TheSpecs on 2008-08-03
Hey, i'm also looking for a way in which i can email commands to my server through email and it execute them if the correct format and possibly pin code is received? 

Any have any luck?

Cheers

---

