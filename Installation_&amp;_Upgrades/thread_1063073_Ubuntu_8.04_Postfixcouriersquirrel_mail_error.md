---
title: "Ubuntu 8.04 Postfix/courier/squirrel mail error"
date: 2009-02-07
forum: Installation &amp; Upgrades
---

### Post by Zhiv on 2009-02-07
For reference to a similar error that I've looked at:

[http://ubuntuforums.org/showthread.php?t=364044]("http://ubuntuforums.org/showthread.php?t=364044")

So here's my issue.  Everything seems to work, where I get the squirrelmail login and such, but when I try to log in I get the "Temporarily unavailable" error.  I look at the tail of my logs and this is what I got.

```
Feb  7 14:15:45 zhivco-lab postfix/master[22809]: terminating on signal 15
Feb  7 14:15:46 zhivco-lab postfix/master[23890]: daemon started -- version 2.5.5, configuration /etc/postfix
Feb  7 14:15:56 zhivco-lab authdaemond: failed to connect to mysql server (server=localhost, userid=mail ): Access denied for user 'mail '@'localhost' (using password: YES)
Feb  7 14:15:56 zhivco-lab imapd-ssl: LOGIN FAILED, method=CRAM-MD5, ip=[::ffff:127.0.0.1]
Feb  7 14:15:56 zhivco-lab imapd-ssl: authentication error: Input/output error


```

Now I noticed the errant space after the username 'mail' on the third line.  So I checked all my config files and such--but no spaces.  I do believe that the actual squirrelmail has nothing to do with the backend login (as it shouldn't).  

So anyone have any ideas?

Thanks in advance,
Tom

PS:  fixed the error.  Apparently when I was editing authdaemonrc, I forgot to remove the description after the varible for DEBUG_LEVEL = 2 (or something to that effect.).  So now it works enough to tell me that I'm a moron and can't remember a password... :D

---

