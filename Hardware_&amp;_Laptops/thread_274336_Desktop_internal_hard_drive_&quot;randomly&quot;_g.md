---
title: "Desktop: internal hard drive &quot;randomly&quot; going to sleep"
date: 2006-10-09
forum: Hardware &amp; Laptops
---

### Post by tommcfarlin4 on 2006-10-09
Hey guys,

I apologize ahead of time if this is in the wrong place in the forum and if this has already been asked (I was unable to find it anywhere in the forums..)..

I've got a desktop PC with two internal hard drives - one containing windows and another of storage (images, music, etc). I'm running Dapper Drake from an external USB hard disk. Everything is working fine, but I've noticed that whenever I come back to my computer after a significant amount of time (overnight, or coming back from class) when I go to access my storage drive I hear it spinning up as if it has been asleep.

A quick look at the power settings yielded no results and the closet thing I came to finding to address this issue was the hparm tool, but before I did anything drastic I wanted to ask all of you if you were familiar with this issue and how I can prevent the hard disk from being put to sleep (I don't like relatively frequent sleep/wakeup cycles - I just assume leaving it running). 

Thanks ahead of time,
Tom

---

### Post by tgalati4 on 2007-03-13
In a terminal:

sudo hdparm -S 0 /dev/hda               (or whatever your disk drive device is called)

The units are in muliples of 5 seconds.  -S 10 will cause the drive to sleep after 50 seconds.

sudo hdparm -iI /dev/hda

will give you drive information.

man hdparm

will give you more information on all of  the hdparm switches.

Sometimes the drive BIOS will override or ignore the hdparm settings--so the drive may still go to sleep after a long period of time.  Server, commercial drives are designed for continuous use.  Consumer drives may spin down to save wear on the bearings.  Depending on the quality of the drive, the drive BIOS may dictate how it behaves.

Welcome to the community and good luck.

---

