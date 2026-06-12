---
title: "Random Popping Sound | Acer Aspire R11"
date: 2016-10-13
forum: Hardware
---

### Post by scarboro on 2016-10-13
I'd be most grateful for some help. 

I'm not sure whether this is a hardware problem or a software problem.  This week I installed Xubuntu 16.04.1 on an Acer Aspire R11.  I wiped out Windows 10.  Xubuntu runs beautifully, except ...

There is a continual gentle random popping sound (a muted crackle) in the right speaker.  I have tried every advice I could find, but have not had any success (yet) in removing it.  So far, I can only remove it by clicking Mute.

Kind regards,
Thomas Scarborough,
in Cape Town.

---

### Post by mpb_ on 2017-07-18
Hello,

In 2011, I ordered an Acer Aspire One.  I ran Ubuntu on it.  Eventually, one of the two speakers stopped working.

In 2017, I tried to install Ubuntu and also GalliumOS to run on an Acer R11 Chromebook.  In this process, I found your post, and also this warning on the GalliumOS website:

[https://wiki.galliumos.org/Support/Braswell](https://wiki.galliumos.org/Support/Braswell)

> We have received several reports of hardware speaker damage in Braswell models with the Realtek ALC5650 audio chip. This includes most Braswells, except the Acer R11 Chromebook (CYAN), which has a Maxim MAX98090 chip instead.

This issue is not limited to GalliumOS or Linux, but it seems to happen more frequently when the machine is not booted into ChromeOS (i.e. at the Developer Mode screen, in firmware, in GRUB, or running Linux).

When your Chromebook is powered on or rebooted, the ChromeOS bootloader (depthcharge) is loaded first, regardless of what operating system you will be running. Depthcharge performs the first initialization of the audio chip. The chip is re-initialized later by ChromeOS, but if the Chromebook is booted into another operating system instead (or not booted at all), no further initialization is performed. It is possible that depthcharge is leaving the chip in an inappropriate state, but that should not be an adequate explanation -- unless some percentage of the Realtek chips are faulty.

See also similar information on this page:

[https://github.com/GalliumOS/galliumos-distro/issues/270](https://github.com/GalliumOS/galliumos-distro/issues/270)

> Braswell Chromebooks come with one of two audio chips: Maxim 98090 or Realtek ALC5650/5654. There are several reports of hardware speaker failures on models with the Realtek chip. There is a lot more discussion in the comments below.

I don't know if these problems with R11's are related to the problem with my 2011 Acer.  Nor to I know what sound chip is inside your R11.  Sound did not work on my R11, so if you had sound working, it is probably a different sound chip from the R11 Chromebook.

But I wanted to let you know it is possible that you are encountering a driver bug, and/or faulty hardware.  And also it is possible that you may damage the sound hardware in your laptop.

Cheers,

mpb

---

