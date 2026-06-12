---
title: "problem in gstreamer plugin"
date: 2009-07-05
forum: Installation &amp; Upgrades
---

### Post by nikku.jain on 2009-07-05
I had upgraded to ubuntu 9.04 from 8.10........some days before i had updated my system. But after that ubuntu is showing problem with sound...........i.e.

"No volume control GStreamer plugins and/or devices found."
This is confusing because the sound was working up until I installed those updates and restarted. Also Ubuntu is detecting my sound card. Everything I've looked up to try to fix this has not worked. Any help is very much appreciated.

---

### Post by jeromestpierre on 2009-07-06
I am experiencing the exact same issue. I did upgrade to 9.04 about a month ago and now some updates had messed up my sound card drivers. I have been using Ubuntu for about 6 months now and it is the second time updates are messing up my system. Next time I will run an update I will first make sure I have enough time to test everything and fix any issues that could arise. 

So far I have always been able to find solutions to Ubuntu issues with Google but now I am still searching after 2 hours of trying everything that was suggested. It also seems like quite a few thread on this issue were left open without any answers.

It seems like a bug to me because I get this error message when trying to launch alsamixer that I was able to use just last week:"alsamixer: function snd_ctl_open failed for default: No such file or directory"

Does anyone has been able to sucessfully fix this issue? Any help would be really appreciated as I don't have time nor any interest to become an expert in Ubuntu sound troubleshooting. Or maybe I will. Anyways, I will keep you updated after fixing it.

---

### Post by jeromestpierre on 2009-07-06
I finally gave up and rolled back to the previous version.

For those who don't know, you can hit ESC when GRUB is loading to select which kernel version to use. 

I changed /boot/grub/menu.lst default value to 2 so that I can reboot without entering the GRUB menu and selecting the correct version each time I reboot. The ordinal index is 0 based and 2.6.28-13-generic was listed first (0), 2.6.28-13-generic-recovery in second (1) and kernel 2.6.28-11-generic was the third one (2) that is stable for me.

At least now I got sound!

---

### Post by nikku.jain on 2009-07-06
I had tried the above solution but still problem is there.........

pls anybody pls help me out

---

