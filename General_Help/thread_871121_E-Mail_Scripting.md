---
title: "E-Mail Scripting"
date: 2008-07-26
forum: General Help
---

### Post by Portmanteaufu on 2008-07-26
Hi All, 

A while back, I had an e-mail account on a shared Linux box on which I did not have root. By modifying the .forward file in my home directory, I was able to run incoming e-mails through the script of my choice with a simple pipe command.

Now I'm running Linux on a couple of home boxes, but I don't have an e-mail server set up. I would -love- to be able to write scripts to process e-mails I receive, but without the server I can't use the magic of a .forward file to accomplish this.

Is there some way I can do this? Or, keeping in mind that these boxes are on a home network, is there some easy way I can set up a mail server to run at home which can be reached by mailing to [user]@[ipaddress] allowing me to use .forward?

Thanks in advance for all your time and help. Let me know if any technical details are necessary.

---

### Post by Portmanteaufu on 2008-07-27
Since I didn't get any response on this one, I'll answer myself: 

[https://help.ubuntu.com/community/Dovecot](https://help.ubuntu.com/community/Dovecot)

explains how to set up Dovecot, a simple mail server which seems to support .forward. Other options exist (such as Courier), but people seem to think they're rather more complicated.

---

