---
title: "Problems with playing video on an old Acer Travelmate 2300"
date: 2010-06-26
forum: Hardware
---

### Post by xpan on 2010-06-26
Hi,

I' ve managed to install ubuntu 10.04 on my old acer travelmate 2300 laptop. In order to do this, however, I needed to do this trick:

[https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes](https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes)

an re-enable the KMS.

Since then ubuntu runs fine. 

Today I tried to play some videos and dvds but with no luck. Ubuntu starts the default media player (have also installed vlc and tried both), then goes into shell writes something and then gives a black screen of death. Then I need to force shutdown and start over. 

In this post I read this: ([https://wiki.ubuntu.com/LucidLynx/ReleaseNotes](https://wiki.ubuntu.com/LucidLynx/ReleaseNotes))

> Working around bugs in the new kernel video architecture

Ubuntu 10.04 LTS enables the new kernel-mode-setting (KMS) technology by default on most common video chipsets. While this is a major step forward for the graphics architecture in Ubuntu, in some rare cases KMS will prevent your video output from working correctly, or from working at all. If you need to disable KMS, you can do so by booting with the nomodeset option. You can also save this setting so that it's applied at every boot by adding it to your grub config (for GRUB 2: edit /etc/default/grub and add nomodeset to GRUB_CMDLINE_LINUX, then run sudo update-grub; for GRUB 1: edit /boot/grub/menu.lst and add nomodeset to the line beginning with # kopt=, then run sudo update-grub). (533784, 541501) 

Any ideas what should I do now?

---

### Post by ieee488 on 2010-06-26
You probably don't have the codecs for playing MPEG2 and MPEG4 files.

---

### Post by xpan on 2010-06-26
> **ieee488 said:**
> You probably don't have the codecs for playing MPEG2 and MPEG4 files.

but how? I have installed vlc plus most of the ffmpeg packages. Is there something else to do? Some repositories to add?

---

### Post by khelben1979 on 2010-06-26
I just checked at the specifications [on this website]("http://archive.laptopmag.com/review/acer-travelmate-2300.ht") and from it I can see it uses intel graphics.

How old is that laptop and have you ever blowed out any dusts from it's vents? When the laptop gets warmer because of high cpu load, then dust inside it can cause the computer to freeze, I've had some experience on this on other computer configurations as well.

I don't think this is a codec issue as the previous poster mentioned..

---

### Post by xpan on 2010-06-26
> **khelben1979 said:**
> I just checked at the specifications [on this website]("http://archive.laptopmag.com/review/acer-travelmate-2300.ht") and from it I can see it uses intel graphics.

How old is that laptop and have you ever blowed out any dusts from it's vents? When the laptop gets warmer because of high cpu load, then dust inside it can cause the computer to freeze, I've had some experience on this on other computer configurations as well.

I don't think this is a codec issue as the previous poster mentioned..

Thanks. It is a very old laptop. My father bought 7-8 years ago. He gave it to me with windows xp pre-installed. I removed windows XP (xp was playing just fine, tho) and installed ubuntu 10.04.

I can try to open it and remove the dust, if you think it might help, but I am doing some dirty things on it already without problem (i.e. programming in eclipse or running TeamViewer and using it for remote desktop operations or even image processing with gimp).

can you tell me if there is any way to find the message it is displayed (for a second) before the screen becomes totally black? It might give us a hint.

---

### Post by khelben1979 on 2010-06-26
I'm not sure exactly, but you can start searching in /var/log for what you're looking for. You got crash reports in there.

---

### Post by xpan on 2010-06-27
Just a note. 

It seems that Lucid has some issues with intel graphic chipsets like mine. I tried 1 or 2 solutions but to no avail.

Can someone point me to a solution that might do the trick?

---

