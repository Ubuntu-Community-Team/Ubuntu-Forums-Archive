---
title: "Syslog :  Endless entries of nullmailer"
date: 2008-07-29
forum: General Help
---

### Post by rpat333 on 2008-07-29
I noticed a gradual slowing down of my system : Hardy 8.04... upon checking the syslog I found entries that the nullmailer program was attempting to send mail however the Host was not found. Having trouble determining what exactly is happening. The syslog is over 100,000 lines and climbing. I removed the nullmailer program through synaptic however the problem persists. Any help would be appreciated.

---

### Post by pcozzy on 2008-09-06
i have realized I am having the same problem I stop klogd and still get endless unsuccessful mail piling up.

I even added mailx to see if I can find source no luck yet.

thanx

---

### Post by quincymd on 2009-01-30
Hi,

I found my system was trying to use nullmailer to send messages via mail which I haven't installed.

The source of these messages were Cron mailing the output from additional program entries I had made to anacrontab.  Each time they were executed a new message was added to the queue.

To remove these messages I had to open a root terminal and cd /var/spool/nullmailer/queue/ and deleted the messages. All the messages waiting in the queue are stored here.

Hope this helps you.

---

