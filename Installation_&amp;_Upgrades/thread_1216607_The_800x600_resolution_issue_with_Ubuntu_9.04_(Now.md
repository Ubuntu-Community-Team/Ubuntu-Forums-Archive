---
title: "The 800x600 resolution issue with Ubuntu 9.04 (Now including Mint 7!)"
date: 2009-07-18
forum: Installation &amp; Upgrades
---

### Post by Ubeeshee on 2009-07-18
Hello!

First time poster and first time user of Linux(finally installed correctly!) here. Well, I should say a full-blown distro as I use Easy Mode Xandros on my EEE pc. 

The title of my post is pretty self explanatory but I will  run you through what I've experienced so far with this problem. A problem, which seems to be plaguing a few members and people who have recently installed or upgraded to Ubuntu 9.04 or Mint 7.

Initially all I wanted to install was Ubuntu 9.04, got a live disk in a magazine, got it running live and noticed I could only choose 800x600 screen resolution or lower. Thinking it was maybe the fact that I was in live mode (noob), I installed expecting a change it but got the same results. 

I then dug up an old Linux Mint 4 DVD which came with a magazine I buy from time to time. Ran it live and what-do-you-know I could choose 1024x768! I quickly installed Mint but was sad to find out how out-of-date it was/is. I tried the newest Mint 7 and it had the same problem as Ubuntu 9.04! When I say this I mean that the graphical menu was the same (guess from the fact Mint derives from Ubuntu) and the low resolution choices were also the same. 

So then I gave it the 3rd strike try and downloaded Mint 5 being that it'll be supported for so long. It worked I am now the proud owner of a Compaq Presario SR1020NX running Mint 5. BUT!!

I want to run Ubuntu 9.04 or at least Mint 7!   

I need to know why these two related distros aren't even giving the choice of a decent resolution. I 'd love to know what to do to change whatever it is that is causing this problem. 

Now, I've searched around and it seems like I'm not the only one in this pickle. On the Mint forums and here. None of the answers seem to work. So, maybe, hopefully there is someone out there who can help me out with this. Tell me what you need to know about my system (and the commands to run so that my machine will spit them out) so we can solve this issue for everyone (well most everyone! since most, it seems, don't have this problem)

Thanks!

ps. I hope I haven't blasphemed in any way by mentioning Mint hehehee. I haven't got the slightest clue about how this community feels about that distro.

---

### Post by running_rabbit07 on 2009-07-18
Do you know if you have an NVIDIA graphics? If you do have NVIDIA you can go into Synaptic Package Manager under System>Administration and search nvidia. This is with Ubuntu 9.04., by the way. 

When the search shows the results, you will want the newest one(the one with the number 180 in it.) When I installed 9.04 and when I went to 8.04 LTS, both offered proprietary drivers.

If you have a different chipset I am not sure what to tell you. If you post which set you have, someone here will help you.

We look forward to helping you.

---

### Post by Ubeeshee on 2009-07-18
How awesome! A super fast reply! :D

Thanks for that. 

Well I looked around and found out about the "lspci" command. Like I said, TOTAL noob here!

Here is what it spat out: 

00:00.0 Host bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface (rev 03)
**00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 03)**
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 82)
00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 02)
01:09.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev 46)
01:0b.0 Communication controller: Agere Systems V.92 56K WinModem (rev 03)
01:0c.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)


I'm guessing what's in bold is the important bit. I also checked if there were any drivers for it using the Administration > Hardware Drivers thing and there was nothing there. Honestly, I don't even know how to go about finding , re-installing, etc. this driver if that's what has to be done. 

Oh and I found [https://bugzilla.redhat.com/show_bug.cgi?id=446558](https://bugzilla.redhat.com/show_bug.cgi?id=446558) but it has to do with redhat. Either way it seems ubuntu isn't the only distro w/ this problemo...

Thanks!

---

### Post by Ubeeshee on 2009-07-20
Well, I guess this isn't all that important then. That, or no one knows how to fix it. I'm going to try some other places to see if they know how or can help. If I find a/the fix I'll be sure to post it back in this post. 

Later!

---

### Post by Vakman on 2009-07-20
Whoa we don't always respond that fast :P
Anyway, Intel graphics and 9.04 had some issues.
Follow [this]("http://ubuntuforums.org/showthread.php?t=1130582") to fix it.
If that does not work I will send a different way to fix it.

---

### Post by Ubeeshee on 2009-07-20
Sorry, wasn't trying to come off the way you implied. 

Unfortunately the advice didn't work. I didn't go further than the "safe" configuration though as I really don't want to mess anything up just yet. 

Reading through the post kind of confirms my guess that it's something to do w/ drivers/config files. 

Being that everything works fine in 8.04 I thought the fix would be simple. Then again I'm no where near understanding what's under the hood of Linux.

Thanks

---

### Post by Vakman on 2009-07-23
I was only kidding around. Anyway, [http://www.ivankristianto.com/2009/06/howto-fix-ubuntu-jaunty-904-intel-graphics-problem/](http://www.ivankristianto.com/2009/06/howto-fix-ubuntu-jaunty-904-intel-graphics-problem/) - try this.
And yeah, 8.04 is the LTS version so things often work quite well.

---

