---
title: "Gutsy upgrade: cron now crashes system?"
date: 2007-10-21
forum: Hardware &amp; Laptops
---

### Post by tomWright on 2007-10-21
Hi all:
First, system is:
HP zd8000 laptop with 4.30 processor, 1gb memory, using pci wireless card and/or wired network

I upgraded to Gutsy from Feisty, yesterday, via the upgrade notice I received, and now the system crashes without warning. 
Every time it has crashed, I was on Firefox, but doing different things. I has crashed while watching videos, or just browsing a web page. With and without Open Office being open.

Looking at the system log, multiple sessions of cron were running just before the crash, yet I have no scripts in the cron directories.

syslog entries:

Oct 20 18:16:29 thing -- MARK --
Oct 20 18:17:01 thing /USR/SBIN/CRON[6406]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Oct 20 18:36:29 thing -- MARK --
Oct 20 18:56:29 thing -- MARK --
Oct 20 19:16:29 thing -- MARK --
Oct 20 19:17:01 thing /USR/SBIN/CRON[7850]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Oct 20 19:36:29 thing -- MARK --
Oct 20 19:56:29 thing -- MARK --
Oct 20 20:16:29 thing -- MARK --
Oct 20 20:17:01 thing /USR/SBIN/CRON[9400]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Oct 20 20:36:29 thing -- MARK --
Oct 20 20:56:29 thing -- MARK --
Oct 20 21:16:29 thing -- MARK --
Oct 20 21:17:01 thing /USR/SBIN/CRON[10985]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Oct 20 21:36:29 thing -- MARK --
Oct 20 21:56:29 thing -- MARK --
Oct 20 22:16:29 thing -- MARK --
Oct 20 22:17:01 thing /USR/SBIN/CRON[12503]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Oct 21 07:41:06 thing syslogd 1.4.1#21ubuntu3: restart.



You will notice that there is nothing between the last crash and the restart the next morning

I do not have any scripts in the cron.hourly directory, it is empty except for the .placeholder file, and I have not added any scripts to the other cron.* directories. Whatever is there was added by ubuntu or possibly other software.

What else can I look at to try to diagnose this?

---

### Post by komsas on 2007-10-24
Same problem. +1

---

### Post by tomWright on 2007-10-27
not cron, seems to be related to firefox and certain pages

This page crashes FF and the entire system every time I go to it:
[http://www.thesun.co.uk/sol/homepage](http://www.thesun.co.uk/sol/homepage)

It does not crash 6.06 LTS or windows when using FF in either.

---

### Post by komsas on 2007-10-29
Now I using Opera and if I will not have more freeze I will be very happy :)

---

### Post by komsas on 2007-10-30
Same problem without firefox.. ;/ can someone help me? I don`t know how to find problem..

---

### Post by Hashte on 2007-10-30
Are you using Compiz? 
If yes, is than the crash is like a gradual fading to white of the screen en then the halting (suddenly turn off) the computer?

---

### Post by komsas on 2007-10-30
No problem is like in other post, freeze came random.

---

### Post by brue68 on 2007-11-04
I have a similar problem, but it's hourly

---

### Post by brue68 on 2007-11-05
hey, what kind of mobo do you have?  I have an Intel DP35DP and I found a possible solution here [http://forums.microsoft.com/TechNet/ShowPost.aspx?PostID=2344047&SiteID=17]("http://forums.microsoft.com/TechNet/ShowPost.aspx?PostID=2344047&SiteID=17")

just changed my fan settings in the BIOS and no more problems.

changed Processor Zone Response to "aggressive"
Processor Zone Damping to "high"
and Automatic Fan Detect to "always"
:guitar:

---

### Post by petermck on 2007-11-14
I've been struggling with a similar problem on an older IBM desktop machine for several months. Every week around 6:45 am on Sunday it becomes non responsive. The only fix is a hard reboot and nothing appears in the logs after about 6:45am except marks. 
This box is actually a Feisty server build with no desktop. I occassionally see similar problems on this forum with different hardware, but as yet no solution...

---

