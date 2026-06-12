---
title: "[SOLVED] MTA sendmail takes forever to start"
date: 2008-09-14
forum: General Help
---

### Post by hwttdz on 2008-09-14
When booting up the system stalls at 
starting mail transport agent (MTA) sendmail
for quite a while.  Can anyone help me find out why this might be, or a way to fix it.  Thanks a bunch.

Also before someone suggests removing all MTAs, I should say that I would very much like the ability to send mails for cron jobs and from perl scripts and whatnot.  I am capable of removing all mail transfer agents.  If someone wants to recommend another go ahead though.

Solution:
So reading /var/log/mail.err, I believe I saw a whole bunch of "unable to qualify my own domain name", so I found [http://www.oreillynet.com/cs/user/view/cs_msg/6371](http://www.oreillynet.com/cs/user/view/cs_msg/6371), making the corrections to /etc/hosts was sufficient to solve the problem.  Hope this helps some other folks.  
i.e. add
127.0.0.1 computername.domainname computername 
to your hosts file.  As a side note the linux hosts file and windows hosts file do not work in the same way, no more listing 
127.0.0.1 adsite1 adsite2 adsite3 ... for me.

---

