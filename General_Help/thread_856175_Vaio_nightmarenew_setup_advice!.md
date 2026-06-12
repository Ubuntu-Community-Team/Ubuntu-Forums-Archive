---
title: "Vaio nightmare/new setup advice!"
date: 2008-07-11
forum: General Help
---

### Post by cptasker on 2008-07-11
Hi all,

I have a Sony Vaio laptop apparently bought before I grew a brain and realised what a load of poop they are. It looked nice, we had a short love affair, but like most short lived obsessions with good looking things I soon woke up to the fact that the pretty case and screen hid an ugly and unsatisfying interior. 

My first problems started when my DVD RW packed in, first not writing then not reading DVDS which after 10 seconds on Google I found was a common problem amongst Vaios. 

Then, after having it for only 16 months I got the blue screen and it refused to boot windows. I was pretty sure the hard drive was dying, I did a bit of research (on my mobile phone) and Vaio suggested I should send it in for repair, which I didn't want to do as they charge a fortune to even look at it. 

I opened it up, cleaned the fan and did all the other things that you're supposed to do but still nothing. My Vaio repair disks did nothing and I was just about to give in when I stumbled across Linux. Ubuntu seemed like the right distribution for me so I burned a live cd on my auntie's computer and installed it.

I absolutely LOVED it! No issues with anything, it worked right out of the box and I started to get stuck in and became a lifetime convert. Then about 2 weeks on and out of nowhere it shuts down and refuses to boot. I'm pretty certain its my hard drive dying, it will boot then freeze at the Debian screen and start a disk check, stopping at 11% and give me the terminal prompt. 

I'm not very good with the terminal yet, but tried the chkdisk thing and it says there is a problem with sda1. Other things I can remember it saying are:

Boot I/O error

something like - chkdisk cannot be completed due to an error and must be run manually

I tried loading gnome from the terminal, I tried gdm (i think) and it came up with some stuff saying /usr/bin/ so I tried /usr/bin sudo gdm
or something similar and it tried to load gnome and came up with a blue screen with a white box which said something along the lines of 
graphical interface could not be loaded and some other stuff.. I'm sorry for being vague, I don't want to try it again unless I have to incase the live cd won't work again (I'm currently online with it) 

So.. is my hard drive off to hard drive heaven?!

If so... I would like to continue using linux and I'm pretty much sick of this Vaio. I would like a decent setup, I know there's an awful lot out there and there is a great computer fair every couple of weeks just down the road. I'm quite handy with a screwdriver and have qualifications in electrical engineering so do you guys think my skills could be transferred to building my own computer? Where to start, any recommendations for a setup that could be built with minimum conflicts and hassle? 

Sorry for the essay! 

Claire x

---

### Post by cptasker on 2008-07-11
I just ran smartmontools - 

code: sudo smartctl -t short /dev/sda && sudo smartctl -l selftest /dev/sda

results:

ubuntu@ubuntu:~$ sudo smartctl -t short /dev/sda && sudo smartctl -l selftest /dev/sda
smartctl version 5.37 [i686-pc-linux-gnu] Copyright (C) 2002-6 Bruce Allen
Home page is [http://smartmontools.sourceforge.net/](http://smartmontools.sourceforge.net/)

=== START OF OFFLINE IMMEDIATE AND SELF-TEST SECTION ===
Sending command: "Execute SMART Short self-test routine immediately in off-line mode".
Drive command "Execute SMART Short self-test routine immediately in off-line mode" successful.
Testing has begun.
Please wait 2 minutes for test to complete.
Test will complete after Fri Jul 11 13:03:02 2008

Use smartctl -X to abort test.
smartctl version 5.37 [i686-pc-linux-gnu] Copyright (C) 2002-6 Bruce Allen
Home page is [http://smartmontools.sourceforge.net/](http://smartmontools.sourceforge.net/)

=== START OF READ SMART DATA SECTION ===
SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Short offline       Completed: read failure       00%      6623         11259970


Any ideas?

---

### Post by brimlar on 2008-07-11
I'm not a hard drive diagnostic wizard, but after having worked on computers for the last six years, I'd say the issues you've experienced are classic symptoms of a hard drive going bad (or a loose IDE/SATA cable.)

---

### Post by cptasker on 2008-07-11
Aye, after trawling the forums I think so too.. time to hit that computer fair! 

Anybody want to buy a vaio case? :lolflag:

---

