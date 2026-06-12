---
title: "Packard Bell Laptop - No Sound, No 3d Acceleration"
date: 2007-11-26
forum: Hardware &amp; Laptops
---

### Post by dryang on 2007-11-26
Installation Of Ubuntu..

I've trawled the forums and i have found nothing relevant to my problems,
I installed ubuntu to my Packard Bell laptop model Mz-U005, about 4 months ago.
It's dual booting with Vista (no problems here).

I don't have little internet access time now, as i'm currently in Cambodia working.
I would really appreciate ANY information on the following things :-

1. The soundcard detected in Ubuntu reads,'Vendor ATI: Device:SBA 450 HDA Audio'
i'm fairly sure this is wrong and i have never heard any sounds of any description. Of course i've adjusted the mixer settings, including adjusting SPDIF and all the obvious things. Theres nothing, not even a click..I have noticed in ALSA the default mixer is seen as a REALTEK ALC861-VD, (OSS Mixer). i have also tried all the settings here, and tried all the test buttons including autodetect, but the computer reads, 'testing pipeline' and does nothing for hours.. 
My soundcard is reported in Vista as a 'Realtek High Definition Audio'
Is it possible for ubuntu to work with this soundcard??

2.My graphics card is a Radeon Express 200M Series
I was quite looking forward to seeing the 3D desktop, so i ticked the option of ATI accelerated graphics driver. The option seems to reset, showing again Not in Use, instead of enabled ???

3.How is it possible to write to certain media such as flash drives. Here again i'm back in Vista
writing this e-mail at home (saving it to my flash drive) because i'm unable to write anyting to certain medias because of permissions. i have read a fair bit about this but when i try to set permissions the options i need to select, ie, read and write, are unavailable! I'm logged on as the only user (ADMINSTRATOR) ..... AAGGGHHHH !!!!

Hmm, so to conclude, i love the interface, style and the whole ubuntu attitude..
i managed to get my father converted to ubuntu, and it does everything he wants it.. well apart from scanning, but mostly he's happy :)
BUT it seems my machine isn't running in any useable form for me under ubuntu.
Am i one of the unfortunate ones that will not be able to get my machine up and running to its full potential?  :( I am certainly no newbie to PC's in general. I'm confident in DOS, Windows and even.. a long time ago COBOL, but surely a modern O/S should now be a graphical interface able to detect hardware configurations without the need for entering terminal/command line to get the thing on it's own two feet ??? 

Thanks in advance for anyone willing to spend some time replying !

Cheers, Andy

---

### Post by dryang on 2007-12-01
hmm, thanks for all the support :P

---

### Post by Jadd on 2007-12-21
Hi

I've got a packard bell too. I have exactly the same sound card as you have (I think, mine's Realtek ALC861-VD), and it works fine... except for the headphone and microphone jacks, which I am still trying to fix. Have you tried Ubuntu Gutsy Gibbon? Ubuntu Feisty needed some tweaking to get sound working but not Gutsy.
I also have a ATI 200M graphics card! On Gutsy, getting special effects to work was a two step process: enabling the restricted driver and then installing XGL, I think. There's a HOW-TO guide in these forums somewhere, just search for 200M compiz fusion gutsy.
You should be able to access flash drives just like in Vista. Are you running normal Ubuntu? You can't possibily be logged in as Administrator, you'd be logged in as whatever you chose during installation, and can only get adminstrative priveledges after entering the password. Type sudo before a command in a terminal to get administrative priveledges, or gksudo in the run dialog.

Hope that helped Andy! Jadd

---

### Post by tupac on 2007-12-21
Hi,

I have the same soundcard as you, and also in my case it is detected as SB 450 ATI by Ubuntu.  I've been using Ubuntu for six month now and have been struggling ever since to have my audio problem solved.  There are loads of people with this problem. Many of them had it fixed and there are several threads on the issue, for example:
[http://wiki.ubuntu-it.org/Hardware/Audio/IntelRealtekHda?highlight=%28realtek%29%7C%28hda%29](http://wiki.ubuntu-it.org/Hardware/Audio/IntelRealtekHda?highlight=%28realtek%29%7C%28hda%29)

In my case I had sound from the built in speaker but not from the headphones and 
 had it fixed (after following more or less blindly many threads) by downloding the driver in the realtek site and finding the proper option to be set in the file /etc/modprobe.d/alsa-base (see method 3 in the cited threads). However after some update (probably of the linux headers) the audio disappeared completely. I was not able to fix the problem and also wanted to switch from kubuntu to ubuntu so I reinstalled everything from scratch and got speaker working (but not headphones) untill I installed again the realtek drivers and everything stopped working again!

I'm very happy with Ubuntu but this problem is very frustrating.  

Vittorio

---

