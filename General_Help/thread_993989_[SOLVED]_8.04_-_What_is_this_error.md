---
title: "[SOLVED] 8.04 - What is this error?"
date: 2008-11-26
forum: General Help
---

### Post by benenglish on 2008-11-26
I'm on 8.04 and when I get a notification that updates are available, I install them.  All of them, all the time, without review.  I don't know if that's a good thing or a bad thing but it's the way I've done business.

This morning there was a long list up updates so I started the update process and went about my business.  A short while later, I got a popup box with an error.  I have no clue which of the many updates caused this or even if the timing is just a coincidence.

The error popup box title was "Assertion Failed".  The text in the box was as follows:> 
[INDENT]
ASSERT: *** Search:_installLocation: engine has no file!
Stack Trace:
0:ENSURE_WARN(false,_installLocation: engine has no file!,2147500037)
1:()
2:()
3:()
4:epsGetAttr([object Object],hidden)
5:()
6:()
7:currentEngine()
8:get_currentEngine()
9:updateDisplay()
10:init()
11:([object XULElement],86)[/INDENT]

If I clicked the "x" in the top-right corner to close the box, it comes back in a few seconds.  In the lower-right corner of the box is what appears to be a button, only it's squashed: three times wider than a normal "OK" button and not tall enough to display any text.  I clicked on it and the box closed.  It has not returned.

Normally, I wouldn't worry about such things but my computer has been running quite slow lately so I'm a bit sensitive to anomalous behavior.

Can anybody give me a clue as to what caused the popup and whether it's anything I need to track down and fix?  

TIA for any insight.

Ben

---

### Post by tjwoosta on 2008-11-26
so did this happened a little while after the updates, or during the updates?

if it happened a while after the updates, did you remember to reboot after the updates?

alot of times when i install updates and forget to reboot strange things start to happen, until i finally reboot and everything goes back to normal

---

### Post by Wayne_V on 2008-11-26
I would also check /var/log/dpkg.log and see if there are interesting messages around that time period.

---

### Post by benenglish on 2008-11-26
> **tjwoosta said:**
> so did this happened a little while after the updates, or during the updates?It happened during the updates, iow while they were installing.  

After clicking the squashed button in the box, the error went away and hasn't been seen since.  That includes for a long time until I rebooted and subsequent to the reboot.

Is it possible to tell from the text of the error what caused the problem?  Is there a log file somewhere I could read?

---

### Post by benenglish on 2008-11-26
> **Wayne_V said:**
> I would also check /var/log/dpkg.log and see if there are interesting messages around that time period.

One of my most obvious problems is that I have no idea what is "interesting", if anything, in this log file.  I've edited it to show just the session where the error occurred and inserted it, below.  

If you see anything interesting in it, I'd be grateful to know what it is and why it's interesting.

I see a bunch of packages that go through the same steps of 

> [INDENT]<time> configure <name>
<time> status unpacked <name>
<time> status half-configured <name>
<time> status installed <name>[/INDENT]

I assume that's what I'm supposed to see as updates get installed.  However, note the third from last line with the "trigproc" in it.  Is that normal?

Here's the entire thing for the session in question:

> [INDENT]2008-11-26 07:17:50 startup archives unpack
2008-11-26 07:17:58 upgrade login 1:4.0.18.2-1ubuntu2 1:4.0.18.2-1ubuntu2.1
2008-11-26 07:17:58 status half-configured login 1:4.0.18.2-1ubuntu2
2008-11-26 07:17:58 status unpacked login 1:4.0.18.2-1ubuntu2
2008-11-26 07:17:58 status half-installed login 1:4.0.18.2-1ubuntu2
2008-11-26 07:17:59 status half-installed login 1:4.0.18.2-1ubuntu2
2008-11-26 07:17:59 status unpacked login 1:4.0.18.2-1ubuntu2.1
2008-11-26 07:17:59 status unpacked login 1:4.0.18.2-1ubuntu2.1
2008-11-26 07:18:00 startup packages configure
2008-11-26 07:18:00 configure login 1:4.0.18.2-1ubuntu2.1 1:4.0.18.2-1ubuntu2.1
2008-11-26 07:18:00 status unpacked login 1:4.0.18.2-1ubuntu2.1
2008-11-26 07:18:00 status unpacked login 1:4.0.18.2-1ubuntu2.1
2008-11-26 07:18:00 status unpacked login 1:4.0.18.2-1ubuntu2.1
2008-11-26 07:18:00 status unpacked login 1:4.0.18.2-1ubuntu2.1
2008-11-26 07:18:00 status unpacked login 1:4.0.18.2-1ubuntu2.1
2008-11-26 07:18:00 status half-configured login 1:4.0.18.2-1ubuntu2.1
2008-11-26 07:18:00 status installed login 1:4.0.18.2-1ubuntu2.1
2008-11-26 07:18:01 startup archives unpack
2008-11-26 07:18:02 upgrade hplip-data 2.8.2-0ubuntu8 2.8.2-0ubuntu8.1
2008-11-26 07:18:02 status half-configured hplip-data 2.8.2-0ubuntu8
2008-11-26 07:18:02 status unpacked hplip-data 2.8.2-0ubuntu8
2008-11-26 07:18:02 status half-installed hplip-data 2.8.2-0ubuntu8
2008-11-26 07:18:02 status half-installed hplip-data 2.8.2-0ubuntu8
2008-11-26 07:18:03 status unpacked hplip-data 2.8.2-0ubuntu8.1
2008-11-26 07:18:03 status unpacked hplip-data 2.8.2-0ubuntu8.1
2008-11-26 07:18:03 upgrade hplip 2.8.2-0ubuntu8 2.8.2-0ubuntu8.1
2008-11-26 07:18:03 status half-configured hplip 2.8.2-0ubuntu8
2008-11-26 07:18:06 status unpacked hplip 2.8.2-0ubuntu8
2008-11-26 07:18:06 status half-installed hplip 2.8.2-0ubuntu8
2008-11-26 07:18:06 status half-installed hplip 2.8.2-0ubuntu8
2008-11-26 07:18:07 status unpacked hplip 2.8.2-0ubuntu8.1
2008-11-26 07:18:07 status unpacked hplip 2.8.2-0ubuntu8.1
2008-11-26 07:18:07 upgrade libxml2 2.6.31.dfsg-2ubuntu1.2 2.6.31.dfsg-2ubuntu1.3
2008-11-26 07:18:07 status half-configured libxml2 2.6.31.dfsg-2ubuntu1.2
2008-11-26 07:18:07 status unpacked libxml2 2.6.31.dfsg-2ubuntu1.2
2008-11-26 07:18:07 status half-installed libxml2 2.6.31.dfsg-2ubuntu1.2
2008-11-26 07:18:07 status half-installed libxml2 2.6.31.dfsg-2ubuntu1.2
2008-11-26 07:18:07 status unpacked libxml2 2.6.31.dfsg-2ubuntu1.3
2008-11-26 07:18:07 status unpacked libxml2 2.6.31.dfsg-2ubuntu1.3
2008-11-26 07:18:07 upgrade openoffice.org-calc 1:2.4.1-1ubuntu2 1:2.4.1-1ubuntu2.1
2008-11-26 07:18:07 status half-configured openoffice.org-calc 1:2.4.1-1ubuntu2
2008-11-26 07:18:08 status unpacked openoffice.org-calc 1:2.4.1-1ubuntu2
2008-11-26 07:18:08 status half-installed openoffice.org-calc 1:2.4.1-1ubuntu2
2008-11-26 07:18:10 status half-installed openoffice.org-calc 1:2.4.1-1ubuntu2
2008-11-26 07:18:11 status unpacked openoffice.org-calc 1:2.4.1-1ubuntu2.1
2008-11-26 07:18:11 status unpacked openoffice.org-calc 1:2.4.1-1ubuntu2.1
2008-11-26 07:18:12 upgrade openoffice.org-impress 1:2.4.1-1ubuntu2 1:2.4.1-1ubuntu2.1
2008-11-26 07:18:12 status half-configured openoffice.org-impress 1:2.4.1-1ubuntu2
2008-11-26 07:18:12 status unpacked openoffice.org-impress 1:2.4.1-1ubuntu2
2008-11-26 07:18:12 status half-installed openoffice.org-impress 1:2.4.1-1ubuntu2
2008-11-26 07:18:12 status half-installed openoffice.org-impress 1:2.4.1-1ubuntu2
2008-11-26 07:18:12 status unpacked openoffice.org-impress 1:2.4.1-1ubuntu2.1
2008-11-26 07:18:12 status unpacked openoffice.org-impress 1:2.4.1-1ubuntu2.1
2008-11-26 07:18:13 upgrade openoffice.org-draw 1:2.4.1-1ubuntu2 1:2.4.1-1ubuntu2.1
2008-11-26 07:18:13 status half-configured openoffice.org-draw 1:2.4.1-1ubuntu2
2008-11-26 07:18:13 status unpacked openoffice.org-draw 1:2.4.1-1ubuntu2
2008-11-26 07:18:13 status half-installed openoffice.org-draw 1:2.4.1-1ubuntu2
2008-11-26 07:18:14 status half-installed openoffice.org-draw 1:2.4.1-1ubuntu2
2008-11-26 07:18:14 status unpacked openoffice.org-draw 1:2.4.1-1ubuntu2.1
2008-11-26 07:18:14 status unpacked openoffice.org-draw 1:2.4.1-1ubuntu2.1
2008-11-26 07:18:14 upgrade openoffice.org-style-human 1:2.4.1-1ubuntu2 1:2.4.1-1ubuntu2.1
2008-11-26 07:18:14 status half-configured openoffice.org-style-human 1:2.4.1-1ubuntu2
2008-11-26 07:18:14 status unpacked openoffice.org-style-human 1:2.4.1-1ubuntu2
2008-11-26 07:18:15 status half-installed openoffice.org-style-human 1:2.4.1-1ubuntu2
2008-11-26 07:18:16 status half-installed openoffice.org-style-human 1:2.4.1-1ubuntu2
2008-11-26 07:18:16 status unpacked openoffice.org-style-human 1:2.4.1-1ubuntu2.1
2008-11-26 07:18:16 status unpacked openoffice.org-style-human 1:2.4.1-1ubuntu2.1
2008-11-26 07:18:17 upgrade openoffice.org-common 1:2.4.1-1ubuntu2 1:2.4.1-1ubuntu2.1
2008-11-26 07:18:17 status half-configured openoffice.org-common 1:2.4.1-1ubuntu2
2008-11-26 07:18:17 status unpacked openoffice.org-common 1:2.4.1-1ubuntu2
2008-11-26 07:18:17 status half-installed openoffice.org-common 1:2.4.1-1ubuntu2
2008-11-26 07:18:24 status half-installed openoffice.org-common 1:2.4.1-1ubuntu2
2008-11-26 07:18:26 status unpacked openoffice.org-common 1:2.4.1-1ubuntu2.1
2008-11-26 07:18:27 status unpacked openoffice.org-common 1:2.4.1-1ubuntu2.1
2008-11-26 07:18:27 upgrade openoffice.org-gtk 1:2.4.1-1ubuntu2 1:2.4.1-1ubuntu2.1
2008-11-26 07:18:27 status half-configured openoffice.org-gtk 1:2.4.1-1ubuntu2
2008-11-26 07:18:27 status unpacked openoffice.org-gtk 1:2.4.1-1ubuntu2
2008-11-26 07:18:27 status half-installed openoffice.org-gtk 1:2.4.1-1ubuntu2
2008-11-26 07:18:27 status half-installed openoffice.org-gtk 1:2.4.1-1ubuntu2
2008-11-26 07:18:27 status unpacked openoffice.org-gtk 1:2.4.1-1ubuntu2.1
2008-11-26 07:18:27 status unpacked openoffice.org-gtk 1:2.4.1-1ubuntu2.1
2008-11-26 07:18:27 upgrade openoffice.org-gnome 1:2.4.1-1ubuntu2 1:2.4.1-1ubuntu2.1
2008-11-26 07:18:27 status half-configured openoffice.org-gnome 1:2.4.1-1ubuntu2
2008-11-26 07:18:27 status unpacked openoffice.org-gnome 1:2.4.1-1ubuntu2
2008-11-26 07:18:27 status half-installed openoffice.org-gnome 1:2.4.1-1ubuntu2
2008-11-26 07:18:27 status half-installed openoffice.org-gnome 1:2.4.1-1ubuntu2
2008-11-26 07:18:27 status unpacked openoffice.org-gnome 1:2.4.1-1ubuntu2.1
2008-11-26 07:18:27 status unpacked openoffice.org-gnome 1:2.4.1-1ubuntu2.1
2008-11-26 07:18:27 upgrade python-uno 1:2.4.1-1ubuntu2 1:2.4.1-1ubuntu2.1
2008-11-26 07:18:27 status half-configured python-uno 1:2.4.1-1ubuntu2
2008-11-26 07:18:27 status unpacked python-uno 1:2.4.1-1ubuntu2
2008-11-26 07:18:27 status half-installed python-uno 1:2.4.1-1ubuntu2
2008-11-26 07:18:28 status half-installed python-uno 1:2.4.1-1ubuntu2
2008-11-26 07:18:28 status unpacked python-uno 1:2.4.1-1ubuntu2.1
2008-11-26 07:18:28 status unpacked python-uno 1:2.4.1-1ubuntu2.1
2008-11-26 07:18:28 upgrade ttf-opensymbol 1:2.4.1-1ubuntu2 1:2.4.1-1ubuntu2.1
2008-11-26 07:18:28 status half-configured ttf-opensymbol 1:2.4.1-1ubuntu2
2008-11-26 07:18:28 status unpacked ttf-opensymbol 1:2.4.1-1ubuntu2
2008-11-26 07:18:28 status half-installed ttf-opensymbol 1:2.4.1-1ubuntu2
2008-11-26 07:18:29 status half-installed ttf-opensymbol 1:2.4.1-1ubuntu2
2008-11-26 07:18:29 status unpacked ttf-opensymbol 1:2.4.1-1ubuntu2.1
2008-11-26 07:18:29 status unpacked ttf-opensymbol 1:2.4.1-1ubuntu2.1
2008-11-26 07:18:29 upgrade openoffice.org-writer 1:2.4.1-1ubuntu2 1:2.4.1-1ubuntu2.1
2008-11-26 07:18:29 status half-configured openoffice.org-writer 1:2.4.1-1ubuntu2
2008-11-26 07:18:29 status unpacked openoffice.org-writer 1:2.4.1-1ubuntu2
2008-11-26 07:18:29 status half-installed openoffice.org-writer 1:2.4.1-1ubuntu2
2008-11-26 07:18:32 status half-installed openoffice.org-writer 1:2.4.1-1ubuntu2
2008-11-26 07:18:33 status unpacked openoffice.org-writer 1:2.4.1-1ubuntu2.1
2008-11-26 07:18:34 status unpacked openoffice.org-writer 1:2.4.1-1ubuntu2.1
2008-11-26 07:18:34 upgrade openoffice.org-core 1:2.4.1-1ubuntu2 1:2.4.1-1ubuntu2.1
2008-11-26 07:18:34 status half-configured openoffice.org-core 1:2.4.1-1ubuntu2
2008-11-26 07:18:34 status unpacked openoffice.org-core 1:2.4.1-1ubuntu2
2008-11-26 07:18:34 status half-installed openoffice.org-core 1:2.4.1-1ubuntu2
2008-11-26 07:18:50 status half-installed openoffice.org-core 1:2.4.1-1ubuntu2
2008-11-26 07:18:51 status unpacked openoffice.org-core 1:2.4.1-1ubuntu2.1
2008-11-26 07:18:52 status unpacked openoffice.org-core 1:2.4.1-1ubuntu2.1
2008-11-26 07:18:52 upgrade openoffice.org-base-core 1:2.4.1-1ubuntu2 1:2.4.1-1ubuntu2.1
2008-11-26 07:18:52 status half-configured openoffice.org-base-core 1:2.4.1-1ubuntu2
2008-11-26 07:18:52 status unpacked openoffice.org-base-core 1:2.4.1-1ubuntu2
2008-11-26 07:18:52 status half-installed openoffice.org-base-core 1:2.4.1-1ubuntu2
2008-11-26 07:18:52 status half-installed openoffice.org-base-core 1:2.4.1-1ubuntu2
2008-11-26 07:18:52 status unpacked openoffice.org-base-core 1:2.4.1-1ubuntu2.1
2008-11-26 07:18:52 status unpacked openoffice.org-base-core 1:2.4.1-1ubuntu2.1
2008-11-26 07:18:53 upgrade passwd 1:4.0.18.2-1ubuntu2 1:4.0.18.2-1ubuntu2.1
2008-11-26 07:18:53 status half-configured passwd 1:4.0.18.2-1ubuntu2
2008-11-26 07:18:53 status unpacked passwd 1:4.0.18.2-1ubuntu2
2008-11-26 07:18:53 status half-installed passwd 1:4.0.18.2-1ubuntu2
2008-11-26 07:18:53 status half-installed passwd 1:4.0.18.2-1ubuntu2
2008-11-26 07:18:54 status unpacked passwd 1:4.0.18.2-1ubuntu2.1
2008-11-26 07:18:54 status unpacked passwd 1:4.0.18.2-1ubuntu2.1
2008-11-26 07:18:55 startup packages configure
2008-11-26 07:18:55 configure passwd 1:4.0.18.2-1ubuntu2.1 1:4.0.18.2-1ubuntu2.1
2008-11-26 07:18:55 status unpacked passwd 1:4.0.18.2-1ubuntu2.1
2008-11-26 07:18:55 status unpacked passwd 1:4.0.18.2-1ubuntu2.1
2008-11-26 07:18:55 status unpacked passwd 1:4.0.18.2-1ubuntu2.1
2008-11-26 07:18:55 status unpacked passwd 1:4.0.18.2-1ubuntu2.1
2008-11-26 07:18:55 status unpacked passwd 1:4.0.18.2-1ubuntu2.1
2008-11-26 07:18:55 status half-configured passwd 1:4.0.18.2-1ubuntu2.1
2008-11-26 07:18:55 status installed passwd 1:4.0.18.2-1ubuntu2.1
2008-11-26 07:18:56 startup archives unpack
2008-11-26 07:18:57 upgrade xulrunner-1.9-gnome-support 1.9.0.3+build1+nobinonly-0ubuntu0.8.04.1 1.9.0.4+nobinonly-0ubuntu0.8.04.1
2008-11-26 07:18:57 status half-configured xulrunner-1.9-gnome-support 1.9.0.3+build1+nobinonly-0ubuntu0.8.04.1
2008-11-26 07:18:57 status unpacked xulrunner-1.9-gnome-support 1.9.0.3+build1+nobinonly-0ubuntu0.8.04.1
2008-11-26 07:18:57 status half-installed xulrunner-1.9-gnome-support 1.9.0.3+build1+nobinonly-0ubuntu0.8.04.1
2008-11-26 07:18:57 status half-installed xulrunner-1.9-gnome-support 1.9.0.3+build1+nobinonly-0ubuntu0.8.04.1
2008-11-26 07:18:57 status unpacked xulrunner-1.9-gnome-support 1.9.0.4+nobinonly-0ubuntu0.8.04.1
2008-11-26 07:18:57 status unpacked xulrunner-1.9-gnome-support 1.9.0.4+nobinonly-0ubuntu0.8.04.1
2008-11-26 07:18:57 upgrade xulrunner-1.9 1.9.0.3+build1+nobinonly-0ubuntu0.8.04.1 1.9.0.4+nobinonly-0ubuntu0.8.04.1
2008-11-26 07:18:57 status half-configured xulrunner-1.9 1.9.0.3+build1+nobinonly-0ubuntu0.8.04.1
2008-11-26 07:18:57 status unpacked xulrunner-1.9 1.9.0.3+build1+nobinonly-0ubuntu0.8.04.1
2008-11-26 07:18:57 status half-installed xulrunner-1.9 1.9.0.3+build1+nobinonly-0ubuntu0.8.04.1
2008-11-26 07:18:59 status half-installed xulrunner-1.9 1.9.0.3+build1+nobinonly-0ubuntu0.8.04.1
2008-11-26 07:18:59 status unpacked xulrunner-1.9 1.9.0.4+nobinonly-0ubuntu0.8.04.1
2008-11-26 07:18:59 status unpacked xulrunner-1.9 1.9.0.4+nobinonly-0ubuntu0.8.04.1
2008-11-26 07:19:00 upgrade firefox-3.0-gnome-support 3.0.3+build1+nobinonly-0ubuntu0.8.04.1 3.0.4+nobinonly-0ubuntu0.8.04.1
2008-11-26 07:19:00 status half-configured firefox-3.0-gnome-support 3.0.3+build1+nobinonly-0ubuntu0.8.04.1
2008-11-26 07:19:00 status unpacked firefox-3.0-gnome-support 3.0.3+build1+nobinonly-0ubuntu0.8.04.1
2008-11-26 07:19:00 status half-installed firefox-3.0-gnome-support 3.0.3+build1+nobinonly-0ubuntu0.8.04.1
2008-11-26 07:19:00 status half-installed firefox-3.0-gnome-support 3.0.3+build1+nobinonly-0ubuntu0.8.04.1
2008-11-26 07:19:00 status unpacked firefox-3.0-gnome-support 3.0.4+nobinonly-0ubuntu0.8.04.1
2008-11-26 07:19:00 status unpacked firefox-3.0-gnome-support 3.0.4+nobinonly-0ubuntu0.8.04.1
2008-11-26 07:19:00 upgrade firefox-3.0 3.0.3+build1+nobinonly-0ubuntu0.8.04.1 3.0.4+nobinonly-0ubuntu0.8.04.1
2008-11-26 07:19:00 status half-configured firefox-3.0 3.0.3+build1+nobinonly-0ubuntu0.8.04.1
2008-11-26 07:19:00 status unpacked firefox-3.0 3.0.3+build1+nobinonly-0ubuntu0.8.04.1
2008-11-26 07:19:00 status half-installed firefox-3.0 3.0.3+build1+nobinonly-0ubuntu0.8.04.1
2008-11-26 07:19:00 status half-installed firefox-3.0 3.0.3+build1+nobinonly-0ubuntu0.8.04.1
2008-11-26 07:19:00 status unpacked firefox-3.0 3.0.4+nobinonly-0ubuntu0.8.04.1
2008-11-26 07:19:00 status unpacked firefox-3.0 3.0.4+nobinonly-0ubuntu0.8.04.1
2008-11-26 07:19:01 upgrade firefox 3.0.3+build1+nobinonly-0ubuntu0.8.04.1 3.0.4+nobinonly-0ubuntu0.8.04.1
2008-11-26 07:19:01 status half-configured firefox 3.0.3+build1+nobinonly-0ubuntu0.8.04.1
2008-11-26 07:19:01 status unpacked firefox 3.0.3+build1+nobinonly-0ubuntu0.8.04.1
2008-11-26 07:19:01 status half-installed firefox 3.0.3+build1+nobinonly-0ubuntu0.8.04.1
2008-11-26 07:19:01 status half-installed firefox 3.0.3+build1+nobinonly-0ubuntu0.8.04.1
2008-11-26 07:19:01 status unpacked firefox 3.0.4+nobinonly-0ubuntu0.8.04.1
2008-11-26 07:19:01 status unpacked firefox 3.0.4+nobinonly-0ubuntu0.8.04.1
2008-11-26 07:19:01 upgrade firefox-gnome-support 3.0.3+build1+nobinonly-0ubuntu0.8.04.1 3.0.4+nobinonly-0ubuntu0.8.04.1
2008-11-26 07:19:01 status half-configured firefox-gnome-support 3.0.3+build1+nobinonly-0ubuntu0.8.04.1
2008-11-26 07:19:01 status unpacked firefox-gnome-support 3.0.3+build1+nobinonly-0ubuntu0.8.04.1
2008-11-26 07:19:01 status half-installed firefox-gnome-support 3.0.3+build1+nobinonly-0ubuntu0.8.04.1
2008-11-26 07:19:01 status half-installed firefox-gnome-support 3.0.3+build1+nobinonly-0ubuntu0.8.04.1
2008-11-26 07:19:01 status unpacked firefox-gnome-support 3.0.4+nobinonly-0ubuntu0.8.04.1
2008-11-26 07:19:01 status unpacked firefox-gnome-support 3.0.4+nobinonly-0ubuntu0.8.04.1
2008-11-26 07:19:01 upgrade hpijs 2.8.2+2.8.2-0ubuntu8 2.8.2+2.8.2-0ubuntu8.1
2008-11-26 07:19:01 status half-configured hpijs 2.8.2+2.8.2-0ubuntu8
2008-11-26 07:19:01 status unpacked hpijs 2.8.2+2.8.2-0ubuntu8
2008-11-26 07:19:01 status half-installed hpijs 2.8.2+2.8.2-0ubuntu8
2008-11-26 07:19:01 status half-installed hpijs 2.8.2+2.8.2-0ubuntu8
2008-11-26 07:19:01 status unpacked hpijs 2.8.2+2.8.2-0ubuntu8.1
2008-11-26 07:19:01 status unpacked hpijs 2.8.2+2.8.2-0ubuntu8.1
2008-11-26 07:19:01 upgrade mysql-common 5.0.51a-3ubuntu5.3 5.0.51a-3ubuntu5.4
2008-11-26 07:19:01 status half-configured mysql-common 5.0.51a-3ubuntu5.3
2008-11-26 07:19:01 status unpacked mysql-common 5.0.51a-3ubuntu5.3
2008-11-26 07:19:02 status half-installed mysql-common 5.0.51a-3ubuntu5.3
2008-11-26 07:19:02 status half-installed mysql-common 5.0.51a-3ubuntu5.3
2008-11-26 07:19:02 status unpacked mysql-common 5.0.51a-3ubuntu5.4
2008-11-26 07:19:02 status unpacked mysql-common 5.0.51a-3ubuntu5.4
2008-11-26 07:19:02 upgrade libmysqlclient15off 5.0.51a-3ubuntu5.3 5.0.51a-3ubuntu5.4
2008-11-26 07:19:02 status half-configured libmysqlclient15off 5.0.51a-3ubuntu5.3
2008-11-26 07:19:02 status unpacked libmysqlclient15off 5.0.51a-3ubuntu5.3
2008-11-26 07:19:02 status half-installed libmysqlclient15off 5.0.51a-3ubuntu5.3
2008-11-26 07:19:02 status half-installed libmysqlclient15off 5.0.51a-3ubuntu5.3
2008-11-26 07:19:02 status unpacked libmysqlclient15off 5.0.51a-3ubuntu5.4
2008-11-26 07:19:02 status unpacked libmysqlclient15off 5.0.51a-3ubuntu5.4
2008-11-26 07:19:02 upgrade libpq5 8.3.3-0ubuntu0.8.04 8.3.5-0ubuntu0.8.04
2008-11-26 07:19:02 status half-configured libpq5 8.3.3-0ubuntu0.8.04
2008-11-26 07:19:02 status unpacked libpq5 8.3.3-0ubuntu0.8.04
2008-11-26 07:19:02 status half-installed libpq5 8.3.3-0ubuntu0.8.04
2008-11-26 07:19:03 status half-installed libpq5 8.3.3-0ubuntu0.8.04
2008-11-26 07:19:03 status unpacked libpq5 8.3.5-0ubuntu0.8.04
2008-11-26 07:19:03 status unpacked libpq5 8.3.5-0ubuntu0.8.04
2008-11-26 07:19:03 upgrade pidgin-data 1:2.4.1-1ubuntu2.1 1:2.4.1-1ubuntu2.2
2008-11-26 07:19:03 status half-configured pidgin-data 1:2.4.1-1ubuntu2.1
2008-11-26 07:19:03 status unpacked pidgin-data 1:2.4.1-1ubuntu2.1
2008-11-26 07:19:03 status half-installed pidgin-data 1:2.4.1-1ubuntu2.1
2008-11-26 07:19:03 status half-installed pidgin-data 1:2.4.1-1ubuntu2.1
2008-11-26 07:19:04 status unpacked pidgin-data 1:2.4.1-1ubuntu2.2
2008-11-26 07:19:04 status unpacked pidgin-data 1:2.4.1-1ubuntu2.2
2008-11-26 07:19:04 upgrade libpurple0 1:2.4.1-1ubuntu2.1 1:2.4.1-1ubuntu2.2
2008-11-26 07:19:04 status half-configured libpurple0 1:2.4.1-1ubuntu2.1
2008-11-26 07:19:04 status unpacked libpurple0 1:2.4.1-1ubuntu2.1
2008-11-26 07:19:04 status half-installed libpurple0 1:2.4.1-1ubuntu2.1
2008-11-26 07:19:05 status half-installed libpurple0 1:2.4.1-1ubuntu2.1
2008-11-26 07:19:05 status unpacked libpurple0 1:2.4.1-1ubuntu2.2
2008-11-26 07:19:05 status unpacked libpurple0 1:2.4.1-1ubuntu2.2
2008-11-26 07:19:05 upgrade libxml2-utils 2.6.31.dfsg-2ubuntu1.2 2.6.31.dfsg-2ubuntu1.3
2008-11-26 07:19:05 status half-configured libxml2-utils 2.6.31.dfsg-2ubuntu1.2
2008-11-26 07:19:05 status unpacked libxml2-utils 2.6.31.dfsg-2ubuntu1.2
2008-11-26 07:19:05 status half-installed libxml2-utils 2.6.31.dfsg-2ubuntu1.2
2008-11-26 07:19:05 status half-installed libxml2-utils 2.6.31.dfsg-2ubuntu1.2
2008-11-26 07:19:05 status unpacked libxml2-utils 2.6.31.dfsg-2ubuntu1.3
2008-11-26 07:19:05 status unpacked libxml2-utils 2.6.31.dfsg-2ubuntu1.3
2008-11-26 07:19:05 upgrade pidgin 1:2.4.1-1ubuntu2.1 1:2.4.1-1ubuntu2.2
2008-11-26 07:19:05 status half-configured pidgin 1:2.4.1-1ubuntu2.1
2008-11-26 07:19:27 status unpacked pidgin 1:2.4.1-1ubuntu2.1
2008-11-26 07:19:27 status half-installed pidgin 1:2.4.1-1ubuntu2.1
2008-11-26 07:19:27 status half-installed pidgin 1:2.4.1-1ubuntu2.1
2008-11-26 07:19:27 status unpacked pidgin 1:2.4.1-1ubuntu2.2
2008-11-26 07:19:27 status unpacked pidgin 1:2.4.1-1ubuntu2.2
2008-11-26 07:19:28 upgrade python-libxml2 2.6.31.dfsg-2ubuntu1.2 2.6.31.dfsg-2ubuntu1.3
2008-11-26 07:19:28 status half-configured python-libxml2 2.6.31.dfsg-2ubuntu1.2
2008-11-26 07:19:28 status unpacked python-libxml2 2.6.31.dfsg-2ubuntu1.2
2008-11-26 07:19:28 status half-installed python-libxml2 2.6.31.dfsg-2ubuntu1.2
2008-11-26 07:19:28 status half-installed python-libxml2 2.6.31.dfsg-2ubuntu1.2
2008-11-26 07:19:28 status unpacked python-libxml2 2.6.31.dfsg-2ubuntu1.3
2008-11-26 07:19:29 status unpacked python-libxml2 2.6.31.dfsg-2ubuntu1.3
2008-11-26 07:19:30 startup packages configure
2008-11-26 07:19:30 configure hplip-data 2.8.2-0ubuntu8.1 2.8.2-0ubuntu8.1
2008-11-26 07:19:30 status unpacked hplip-data 2.8.2-0ubuntu8.1
2008-11-26 07:19:30 status half-configured hplip-data 2.8.2-0ubuntu8.1
2008-11-26 07:19:30 status installed hplip-data 2.8.2-0ubuntu8.1
2008-11-26 07:19:30 configure hplip 2.8.2-0ubuntu8.1 2.8.2-0ubuntu8.1
2008-11-26 07:19:30 status unpacked hplip 2.8.2-0ubuntu8.1
2008-11-26 07:19:31 status unpacked hplip 2.8.2-0ubuntu8.1
2008-11-26 07:19:31 status unpacked hplip 2.8.2-0ubuntu8.1
2008-11-26 07:19:31 status unpacked hplip 2.8.2-0ubuntu8.1
2008-11-26 07:19:31 status half-configured hplip 2.8.2-0ubuntu8.1
2008-11-26 07:19:32 status installed hplip 2.8.2-0ubuntu8.1
2008-11-26 07:19:32 status triggers-pending libc6 2.7-10ubuntu4
2008-11-26 07:19:32 configure libxml2 2.6.31.dfsg-2ubuntu1.3 2.6.31.dfsg-2ubuntu1.3
2008-11-26 07:19:32 status unpacked libxml2 2.6.31.dfsg-2ubuntu1.3
2008-11-26 07:19:32 status half-configured libxml2 2.6.31.dfsg-2ubuntu1.3
2008-11-26 07:19:32 status installed libxml2 2.6.31.dfsg-2ubuntu1.3
2008-11-26 07:19:32 configure openoffice.org-base-core 1:2.4.1-1ubuntu2.1 1:2.4.1-1ubuntu2.1
2008-11-26 07:19:32 status unpacked openoffice.org-base-core 1:2.4.1-1ubuntu2.1
2008-11-26 07:19:32 status half-configured openoffice.org-base-core 1:2.4.1-1ubuntu2.1
2008-11-26 07:19:32 status installed openoffice.org-base-core 1:2.4.1-1ubuntu2.1
2008-11-26 07:19:32 configure ttf-opensymbol 1:2.4.1-1ubuntu2.1 1:2.4.1-1ubuntu2.1
2008-11-26 07:19:32 status unpacked ttf-opensymbol 1:2.4.1-1ubuntu2.1
2008-11-26 07:19:32 status half-configured ttf-opensymbol 1:2.4.1-1ubuntu2.1
2008-11-26 07:19:50 status installed ttf-opensymbol 1:2.4.1-1ubuntu2.1
2008-11-26 07:19:50 configure xulrunner-1.9 1.9.0.4+nobinonly-0ubuntu0.8.04.1 1.9.0.4+nobinonly-0ubuntu0.8.04.1
2008-11-26 07:19:50 status unpacked xulrunner-1.9 1.9.0.4+nobinonly-0ubuntu0.8.04.1
2008-11-26 07:19:50 status unpacked xulrunner-1.9 1.9.0.4+nobinonly-0ubuntu0.8.04.1
2008-11-26 07:19:50 status unpacked xulrunner-1.9 1.9.0.4+nobinonly-0ubuntu0.8.04.1
2008-11-26 07:19:50 status half-configured xulrunner-1.9 1.9.0.4+nobinonly-0ubuntu0.8.04.1
2008-11-26 07:19:50 status installed xulrunner-1.9 1.9.0.4+nobinonly-0ubuntu0.8.04.1
2008-11-26 07:19:50 configure xulrunner-1.9-gnome-support 1.9.0.4+nobinonly-0ubuntu0.8.04.1 1.9.0.4+nobinonly-0ubuntu0.8.04.1
2008-11-26 07:19:50 status unpacked xulrunner-1.9-gnome-support 1.9.0.4+nobinonly-0ubuntu0.8.04.1
2008-11-26 07:19:50 status half-configured xulrunner-1.9-gnome-support 1.9.0.4+nobinonly-0ubuntu0.8.04.1
2008-11-26 07:19:51 status installed xulrunner-1.9-gnome-support 1.9.0.4+nobinonly-0ubuntu0.8.04.1
2008-11-26 07:19:51 configure firefox-3.0 3.0.4+nobinonly-0ubuntu0.8.04.1 3.0.4+nobinonly-0ubuntu0.8.04.1
2008-11-26 07:19:51 status unpacked firefox-3.0 3.0.4+nobinonly-0ubuntu0.8.04.1
2008-11-26 07:19:51 status unpacked firefox-3.0 3.0.4+nobinonly-0ubuntu0.8.04.1
2008-11-26 07:19:51 status unpacked firefox-3.0 3.0.4+nobinonly-0ubuntu0.8.04.1
2008-11-26 07:19:51 status unpacked firefox-3.0 3.0.4+nobinonly-0ubuntu0.8.04.1
2008-11-26 07:19:51 status unpacked firefox-3.0 3.0.4+nobinonly-0ubuntu0.8.04.1
2008-11-26 07:19:51 status unpacked firefox-3.0 3.0.4+nobinonly-0ubuntu0.8.04.1
2008-11-26 07:19:51 status unpacked firefox-3.0 3.0.4+nobinonly-0ubuntu0.8.04.1
2008-11-26 07:19:51 status unpacked firefox-3.0 3.0.4+nobinonly-0ubuntu0.8.04.1
2008-11-26 07:19:51 status half-configured firefox-3.0 3.0.4+nobinonly-0ubuntu0.8.04.1
2008-11-26 07:19:51 status installed firefox-3.0 3.0.4+nobinonly-0ubuntu0.8.04.1
2008-11-26 07:19:51 configure firefox-3.0-gnome-support 3.0.4+nobinonly-0ubuntu0.8.04.1 3.0.4+nobinonly-0ubuntu0.8.04.1
2008-11-26 07:19:51 status unpacked firefox-3.0-gnome-support 3.0.4+nobinonly-0ubuntu0.8.04.1
2008-11-26 07:19:51 status half-configured firefox-3.0-gnome-support 3.0.4+nobinonly-0ubuntu0.8.04.1
2008-11-26 07:19:51 status installed firefox-3.0-gnome-support 3.0.4+nobinonly-0ubuntu0.8.04.1
2008-11-26 07:19:51 configure firefox 3.0.4+nobinonly-0ubuntu0.8.04.1 3.0.4+nobinonly-0ubuntu0.8.04.1
2008-11-26 07:19:51 status unpacked firefox 3.0.4+nobinonly-0ubuntu0.8.04.1
2008-11-26 07:19:51 status half-configured firefox 3.0.4+nobinonly-0ubuntu0.8.04.1
2008-11-26 07:19:51 status installed firefox 3.0.4+nobinonly-0ubuntu0.8.04.1
2008-11-26 07:19:51 configure firefox-gnome-support 3.0.4+nobinonly-0ubuntu0.8.04.1 3.0.4+nobinonly-0ubuntu0.8.04.1
2008-11-26 07:19:51 status unpacked firefox-gnome-support 3.0.4+nobinonly-0ubuntu0.8.04.1
2008-11-26 07:19:51 status half-configured firefox-gnome-support 3.0.4+nobinonly-0ubuntu0.8.04.1
2008-11-26 07:19:51 status installed firefox-gnome-support 3.0.4+nobinonly-0ubuntu0.8.04.1
2008-11-26 07:19:51 configure hpijs 2.8.2+2.8.2-0ubuntu8.1 2.8.2+2.8.2-0ubuntu8.1
2008-11-26 07:19:51 status unpacked hpijs 2.8.2+2.8.2-0ubuntu8.1
2008-11-26 07:19:51 status half-configured hpijs 2.8.2+2.8.2-0ubuntu8.1
2008-11-26 07:19:51 status installed hpijs 2.8.2+2.8.2-0ubuntu8.1
2008-11-26 07:19:51 configure mysql-common 5.0.51a-3ubuntu5.4 5.0.51a-3ubuntu5.4
2008-11-26 07:19:51 status unpacked mysql-common 5.0.51a-3ubuntu5.4
2008-11-26 07:19:51 status unpacked mysql-common 5.0.51a-3ubuntu5.4
2008-11-26 07:19:51 status half-configured mysql-common 5.0.51a-3ubuntu5.4
2008-11-26 07:19:51 status installed mysql-common 5.0.51a-3ubuntu5.4
2008-11-26 07:19:51 configure libmysqlclient15off 5.0.51a-3ubuntu5.4 5.0.51a-3ubuntu5.4
2008-11-26 07:19:51 status unpacked libmysqlclient15off 5.0.51a-3ubuntu5.4
2008-11-26 07:19:51 status half-configured libmysqlclient15off 5.0.51a-3ubuntu5.4
2008-11-26 07:19:51 status installed libmysqlclient15off 5.0.51a-3ubuntu5.4
2008-11-26 07:19:51 configure libpq5 8.3.5-0ubuntu0.8.04 8.3.5-0ubuntu0.8.04
2008-11-26 07:19:51 status unpacked libpq5 8.3.5-0ubuntu0.8.04
2008-11-26 07:19:51 status half-configured libpq5 8.3.5-0ubuntu0.8.04
2008-11-26 07:19:51 status installed libpq5 8.3.5-0ubuntu0.8.04
2008-11-26 07:19:51 configure pidgin-data 1:2.4.1-1ubuntu2.2 1:2.4.1-1ubuntu2.2
2008-11-26 07:19:51 status unpacked pidgin-data 1:2.4.1-1ubuntu2.2
2008-11-26 07:19:51 status unpacked pidgin-data 1:2.4.1-1ubuntu2.2
2008-11-26 07:19:51 status half-configured pidgin-data 1:2.4.1-1ubuntu2.2
2008-11-26 07:19:52 status installed pidgin-data 1:2.4.1-1ubuntu2.2
2008-11-26 07:19:52 configure libpurple0 1:2.4.1-1ubuntu2.2 1:2.4.1-1ubuntu2.2
2008-11-26 07:19:52 status unpacked libpurple0 1:2.4.1-1ubuntu2.2
2008-11-26 07:19:52 status half-configured libpurple0 1:2.4.1-1ubuntu2.2
2008-11-26 07:19:52 status installed libpurple0 1:2.4.1-1ubuntu2.2
2008-11-26 07:19:52 configure libxml2-utils 2.6.31.dfsg-2ubuntu1.3 2.6.31.dfsg-2ubuntu1.3
2008-11-26 07:19:52 status unpacked libxml2-utils 2.6.31.dfsg-2ubuntu1.3
2008-11-26 07:19:52 status half-configured libxml2-utils 2.6.31.dfsg-2ubuntu1.3
2008-11-26 07:19:52 status installed libxml2-utils 2.6.31.dfsg-2ubuntu1.3
2008-11-26 07:19:52 configure pidgin 1:2.4.1-1ubuntu2.2 1:2.4.1-1ubuntu2.2
2008-11-26 07:19:52 status unpacked pidgin 1:2.4.1-1ubuntu2.2
2008-11-26 07:19:52 status half-configured pidgin 1:2.4.1-1ubuntu2.2
2008-11-26 07:20:03 status installed pidgin 1:2.4.1-1ubuntu2.2
2008-11-26 07:20:05 configure python-libxml2 2.6.31.dfsg-2ubuntu1.3 2.6.31.dfsg-2ubuntu1.3
2008-11-26 07:20:05 status unpacked python-libxml2 2.6.31.dfsg-2ubuntu1.3
2008-11-26 07:20:05 status half-configured python-libxml2 2.6.31.dfsg-2ubuntu1.3
2008-11-26 07:20:05 status installed python-libxml2 2.6.31.dfsg-2ubuntu1.3
2008-11-26 07:20:05 configure openoffice.org-style-human 1:2.4.1-1ubuntu2.1 1:2.4.1-1ubuntu2.1
2008-11-26 07:20:05 status unpacked openoffice.org-style-human 1:2.4.1-1ubuntu2.1
2008-11-26 07:20:05 status half-configured openoffice.org-style-human 1:2.4.1-1ubuntu2.1
2008-11-26 07:20:05 status installed openoffice.org-style-human 1:2.4.1-1ubuntu2.1
2008-11-26 07:20:05 configure openoffice.org-core 1:2.4.1-1ubuntu2.1 1:2.4.1-1ubuntu2.1
2008-11-26 07:20:05 status unpacked openoffice.org-core 1:2.4.1-1ubuntu2.1
2008-11-26 07:20:05 status half-configured openoffice.org-core 1:2.4.1-1ubuntu2.1
2008-11-26 07:20:05 status installed openoffice.org-core 1:2.4.1-1ubuntu2.1
2008-11-26 07:20:05 configure openoffice.org-calc 1:2.4.1-1ubuntu2.1 1:2.4.1-1ubuntu2.1
2008-11-26 07:20:05 status unpacked openoffice.org-calc 1:2.4.1-1ubuntu2.1
2008-11-26 07:20:05 status half-configured openoffice.org-calc 1:2.4.1-1ubuntu2.1
2008-11-26 07:20:07 status installed openoffice.org-calc 1:2.4.1-1ubuntu2.1
2008-11-26 07:20:07 configure openoffice.org-draw 1:2.4.1-1ubuntu2.1 1:2.4.1-1ubuntu2.1
2008-11-26 07:20:07 status unpacked openoffice.org-draw 1:2.4.1-1ubuntu2.1
2008-11-26 07:20:07 status half-configured openoffice.org-draw 1:2.4.1-1ubuntu2.1
2008-11-26 07:20:07 status installed openoffice.org-draw 1:2.4.1-1ubuntu2.1
2008-11-26 07:20:07 configure openoffice.org-impress 1:2.4.1-1ubuntu2.1 1:2.4.1-1ubuntu2.1
2008-11-26 07:20:07 status unpacked openoffice.org-impress 1:2.4.1-1ubuntu2.1
2008-11-26 07:20:07 status half-configured openoffice.org-impress 1:2.4.1-1ubuntu2.1
2008-11-26 07:20:07 status installed openoffice.org-impress 1:2.4.1-1ubuntu2.1
2008-11-26 07:20:07 configure openoffice.org-gtk 1:2.4.1-1ubuntu2.1 1:2.4.1-1ubuntu2.1
2008-11-26 07:20:07 status unpacked openoffice.org-gtk 1:2.4.1-1ubuntu2.1
2008-11-26 07:20:07 status half-configured openoffice.org-gtk 1:2.4.1-1ubuntu2.1
2008-11-26 07:20:07 status installed openoffice.org-gtk 1:2.4.1-1ubuntu2.1
2008-11-26 07:20:07 configure openoffice.org-gnome 1:2.4.1-1ubuntu2.1 1:2.4.1-1ubuntu2.1
2008-11-26 07:20:07 status unpacked openoffice.org-gnome 1:2.4.1-1ubuntu2.1
2008-11-26 07:20:07 status half-configured openoffice.org-gnome 1:2.4.1-1ubuntu2.1
2008-11-26 07:20:07 status installed openoffice.org-gnome 1:2.4.1-1ubuntu2.1
2008-11-26 07:20:07 configure python-uno 1:2.4.1-1ubuntu2.1 1:2.4.1-1ubuntu2.1
2008-11-26 07:20:07 status unpacked python-uno 1:2.4.1-1ubuntu2.1
2008-11-26 07:20:07 status half-configured python-uno 1:2.4.1-1ubuntu2.1
2008-11-26 07:20:08 status installed python-uno 1:2.4.1-1ubuntu2.1
2008-11-26 07:20:08 configure openoffice.org-writer 1:2.4.1-1ubuntu2.1 1:2.4.1-1ubuntu2.1
2008-11-26 07:20:08 status unpacked openoffice.org-writer 1:2.4.1-1ubuntu2.1
2008-11-26 07:20:08 status half-configured openoffice.org-writer 1:2.4.1-1ubuntu2.1
2008-11-26 07:20:08 status installed openoffice.org-writer 1:2.4.1-1ubuntu2.1
2008-11-26 07:20:08 configure openoffice.org-common 1:2.4.1-1ubuntu2.1 1:2.4.1-1ubuntu2.1
2008-11-26 07:20:08 status unpacked openoffice.org-common 1:2.4.1-1ubuntu2.1
2008-11-26 07:20:08 status unpacked openoffice.org-common 1:2.4.1-1ubuntu2.1
2008-11-26 07:20:08 status unpacked openoffice.org-common 1:2.4.1-1ubuntu2.1
2008-11-26 07:20:08 status unpacked openoffice.org-common 1:2.4.1-1ubuntu2.1
2008-11-26 07:20:08 status unpacked openoffice.org-common 1:2.4.1-1ubuntu2.1
2008-11-26 07:20:08 status half-configured openoffice.org-common 1:2.4.1-1ubuntu2.1
2008-11-26 07:20:09 status installed openoffice.org-common 1:2.4.1-1ubuntu2.1
2008-11-26 07:20:09 trigproc libc6 2.7-10ubuntu4 2.7-10ubuntu4
2008-11-26 07:20:09 status half-configured libc6 2.7-10ubuntu4
2008-11-26 07:20:10 status installed libc6 2.7-10ubuntu4
[/INDENT]

Thanks for any thoughts you may have.

ben

ps - How do I put long snips of text into one of those smaller, easier-to-handle scrolling boxes?  I figured the QUOTE tag would do that but I was wrong.

---

### Post by Wayne_V on 2008-11-26
See [https://bugs.launchpad.net/ubuntu/+source/firefox-3.0/+bug/212465](https://bugs.launchpad.net/ubuntu/+source/firefox-3.0/+bug/212465)

The error was from firefox, not related to the update other than that firefox was updated and you didn't restart it.

If your system is running slow, try adding System Monitor to your task bar and turning all the monitors on to see what's going on.   Or just run  top.

---

### Post by benenglish on 2008-11-26
> **Wayne_V said:**
> The error was from firefox, not related to the update other than that firefox was updated and you didn't restart it.

If your system is running slow, try adding System Monitor to your task bar and turning all the monitors on to see what's going on.   Or just run  top.

That's it.  Thanks so much.  I appreciate knowing what's going on.

---

