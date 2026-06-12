---
title: "Can't Sync my Palm m515"
date: 2006-07-02
forum: Hardware &amp; Laptops
---

### Post by Cris987 on 2006-07-02
I've looked around and tried the "solutions", but I still haven't been able to sync my palm m515.

There was ONE (just one)  time when I got it to sync, and that was when I used jpilot and configured the serial port to dev/ttyUSB1, but it only worked once. I tried it again, and it would not connect. 

So, is it true that this is simply a problem in the kernel regarding usb devices? If yes, when can I expect a fix to be released?

---

### Post by Cris987 on 2006-07-02
Just adding a reply to enable email notification...

---

### Post by wazoo on 2006-07-03
I have an M505 Palm, and recently scrapped my whole Ubuntu install to do a fresh Dapper Drake. Lo and behold, the first setup for Evolution worked great, and I got a sync. And never again.

JPilot continues to work for me, on any Linux machine, every time, with no problems. I'm baffled as to why this is such a problem for Evolution. But after banging my head against it for a week or so, I just went back to JPilot and Thunderbird -- there's a little duplication involved, for sure (I output all my contacts as an ldif file, then read them into Thunderbird). But it's stable and predictable.

Incidentally, try this in JPilot: don't mess with trying to set up a /dev/pilot. In Jpilot>File>Preferences>Settings, try /dev/ttyUSB0, then /dev/ttyUSB1. One of those will probably do it for you. And good luck.

---

### Post by Cris987 on 2006-07-04
No luck. Any suggestions?

---

### Post by bruceliz on 2006-07-05
After installing Dapper I tried many of the suggestions in this forum for syncing a USB Palm device using jpilot configured in sundry ways,  with results ranging from highly unreliable to plain impossible.

Finally built a 2.6.17.3 kernel, installed it, **have had absolutely no problems since**. (Aside from the new kernel reporting EVMS errors on boot, that is -- until the official Dapper kernel is fixed I'll boot with 2.6.17.3 only when wanting to sync my Palm device .)

In short, it seems to be a Dapper 2.6.15 kernel bug relating to USB. [See later comments in bug #38574]("https://launchpad.net/distros/ubuntu/+source/gnome-pilot/+bug/38574").

---

### Post by Cris987 on 2006-07-05
[QUOTE=bruceliz]After installing Dapper I tried many of the suggestions in this forum for syncing a USB Palm device using jpilot configured in sundry ways,  with results ranging from highly unreliable to plain impossible.

Finally built a 2.6.17.3 kernel, installed it, **have had absolutely no problems since**. (Aside from the new kernel reporting EVMS errors on boot, that is -- until the official Dapper kernel is fixed I'll boot with 2.6.17.3 only when wanting to sync my Palm device .)

In short, it seems to be a Dapper 2.6.15 kernel bug relating to USB. [See later comments in bug #38574]("https://launchpad.net/distros/ubuntu/+source/gnome-pilot/+bug/38574").[/QUOTE]

YES. Building  a new kernel (namely 2.6.17) worked perfectly. 

However, I have some probs using with using jpilot. For one, how do you backup/synchronize programs on palm with jpilot?

Thanks.

---

### Post by wazoo on 2006-07-05
Wow, I sure didn't have to mess with the kernel -- but glad it worked for you.

You asked, "how do you backup/synchronize programs on palm with jpilot?"

There are three kinds of "syncing" in JPilot.

1. the Jpilot sync button, which compares the databases between the PC and Palm, and updates both so they match.

2. the sync and backup -- which syncs AND does a complete file dump of your handheld into ~/.jpilot/backup. (I often go into here and fetch a ShadowPlan file, for instance.)

3. Install a program. This installs from the PC to the handheld. Use File>install.

Is that what you're asking?

---

### Post by Cris987 on 2006-07-05
[QUOTE=wazoo]Wow, I sure didn't have to mess with the kernel -- but glad it worked for you.

You asked, "how do you backup/synchronize programs on palm with jpilot?"

There are three kinds of "syncing" in JPilot.

1. the Jpilot sync button, which compares the databases between the PC and Palm, and updates both so they match.

2. the sync and backup -- which syncs AND does a complete file dump of your handheld into ~/.jpilot/backup. (I often go into here and fetch a ShadowPlan file, for instance.)

3. Install a program. This installs from the PC to the handheld. Use File>install.

Is that what you're asking?[/QUOTE]


Yes. Thank you very much for the info. One more newbie question before I go...where can I find the files that Jpilot has copied?

---

