---
title: "Intel Audio Problem"
date: 2007-06-13
forum: Hardware &amp; Laptops
---

### Post by shadows on 2007-06-13
Hi All

I've read many forums and done a lot of googling but I can't seem to find out how to fix the sound on my laptop. It worked fine on the live cd and it worked for a few weeks after installation, but after a while it just stopped working. The volume control, or any application that tries to access audio, reports the following: "No volume control GStreamer plugins and/or devices found." 

I have tried quite a few of the suggested solutions from other posts but have been unsuccessful thus far. I have listed my system details below.

My System: Fujitsu Siemens Amilo M6450G

OS:  Ubuntu Feisty Fawn 7.04

cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.14rc1 (Tue Jan 09 09:56:17 2007 UTC).

lspci -vv | fgrep Audio
00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 04)

cat /proc/asound/card0/codec#0
Codec: Motorola Si3054
Address: 0
Vendor Id: 0x10573055
Subsystem Id: 0x10573055
Revision Id: 0x100700

aplay -l
aplay: device_list:222: no soundcards found...

Thanks in Advance

---

### Post by mdwuznik on 2007-06-13
Is your user added to the appropriate groups ?
media/lp/audio/video/games etc ?

Michal

---

### Post by shadows on 2007-06-13
Not sure. How do I check?

---

### Post by servo153 on 2007-06-28
You can check groups and whether or not you are a member by clicking on System, Administration, Users and Groups.  Then click on the Manage Groups button and you can look at all the groups on your machine

---

