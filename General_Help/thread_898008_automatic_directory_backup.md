---
title: "automatic directory backup"
date: 2008-08-22
forum: General Help
---

### Post by thebrotherofasis on 2008-08-22
Hello,

I have no programming knowledge, so I came to the forum to see if someone could help me.

I want to create an automatic routine backup of a certain directory, in, say, tar.gz format, and have it automatically sent to my email, so I can have a storage of it.

Thank you very much in advance.

---

### Post by LateNiteTV on 2008-08-22
man cron
man tar
man gzip

---

### Post by thebrotherofasis on 2008-08-22
Anything more specific, please?

---

### Post by LateNiteTV on 2008-08-22
you should really try doing things on your own. the man pages will provide you with all the information you need to accomplish this. google works wonders too.

---

### Post by my_key on 2008-08-22
I would answer you, but this link has already done a better job of explaining it:

[http://linuxreality.com/docs/ep63notes.txt](http://linuxreality.com/docs/ep63notes.txt)
[http://www.linuxreality.com/podcast/episode-63-home-servers-part-9-backup-servers/](http://www.linuxreality.com/podcast/episode-63-home-servers-part-9-backup-servers/)

Hope this helps,
michael

---

### Post by thebrotherofasis on 2008-08-22
I now what you mean. 

But that is exactly why I came to this forum, because I NEED help, not a "do it yourself", kind of answer. 

If someone else has done this in the past, or has an idea of how this should be done, I'd really appreciate your support.

Thanks.

---

### Post by thebrotherofasis on 2008-08-22
I'll look into it, thank you.

---

### Post by thebrotherofasis on 2008-08-22
Ok... I've already been able to create a tar.gz file, with command line out of a Directory.

Now, I would like to know how I can create a script or a cron? to send it to my email automatically.

So close... :)

Thank you

---

### Post by ghostdog74 on 2008-08-22
> **thebrotherofasis said:**
> 
But that is exactly why I came to this forum, because I NEED help, not a "do it yourself", kind of answer. 


you are half right. People come to forums to get help, but they should also put in effort. You already have all the help you needed.

---

### Post by b9k9kiwi on 2008-08-22
> **thebrotherofasis said:**
> 
...
I now what you mean. 
...


I know what you mean too :).

I don't enjoy programming or scriptwriting and I found the answer to just the same question a few days ago by searching these forums for similar threads - there are quite a few (every question has already been asked before it seems).

I got all the pointers and script examples I needed to do it myself.

Good luck.

---

### Post by thebrotherofasis on 2008-08-22
I don't expect to be 25%, 50%, 75% or 100% right. My post is certainly not created for discussing reasons why people come to forums.

Of course you have to effort to get the results... that's why we love linux... because we are people who like to create, not have it all served on your table every time you will.

Now, anybody has more information on what command I should use to send whatever file (in this case a tar.gz file) to an email address? I am pretty possitive such command exists... and I am also possitive on finding someone how can shed some light on this and SHARE his knowledge.

Thank you very much!

---

### Post by my_key on 2008-08-22
Try [http://migas-sbackup.sourceforge.net/](http://migas-sbackup.sourceforge.net/) if you want. I haven't tried it, but it seems to do what you want to achieve.

Or just make a cron job that mails the contents of your backup directory to your e-mail. This is fairly simple using any command line e-mail program like mail, mutt, ...
> 
#!/bin/bash
tar cvzf ~/backups/backup_`date +%w`.tgz ~/folder_to_backup
mutt -s "Backup `date`" -a ~/backups/backup_`date +%w`.tgz [email]your_username@gmail.com[/email]



Edit: or [https://sourceforge.net/projects/autofilebackup/](https://sourceforge.net/projects/autofilebackup/)

---

### Post by thebrotherofasis on 2008-08-22
This was really helpful, thank you.

I have worked on this for a while, and now I have been able to create an automated backup the way i wanted it.

Thank you very much again.

---

### Post by thebrotherofasis on 2008-08-22
This was really helpful, thank you.

I have worked on this for a while, and now I have been able to create an automated backup the way i wanted it, using the params of your script.

Thank you very much again.

---

### Post by thebrotherofasis on 2008-08-23
In learning more about the topic, I came across this interesting guide, which cleared up many of the questions that came up at first:

[http://souptonuts.sourceforge.net/postfix_tutorial.html](http://souptonuts.sourceforge.net/postfix_tutorial.html)

This is a tutorial that explains how to configure my gmail account with postfix to send mail.

---

