---
title: "Cannot boot from USB Stick"
date: 2009-07-02
forum: Installation &amp; Upgrades
---

### Post by Jackie78 on 2009-07-02
Hello,

I have just downloaded the latest Ubuntu CD version 9.04 (jaunty jackalope 9.04 64-bit), and it boots up properly on my laptop (Toshiba Satellite A210-14s). I have then created a bootable USB stick (2GB Kingston USB) using *System - Systemadministration - Create a USB startup disk *from the Gnome Desktop menu.

USB Legacy support is enabled, and the stick boots properly, I can select a language from the boot menu, and then Linux starts booting. However, after a short while I fall into Busybox, and get the following error:

modprobe: FATAL: Could not load /lib/modules/2.6.28-11-generic/modules.dep: no such file or directory.

I can see the "ubuntu" graphical bootlogo for a while, but then it enters busybox, I get a shell and nothing more happens. I'd rather boot up to gnome instead :(

What is going wrong here?

---

### Post by C.S.Cameron on 2009-07-02
Try installing to USB using Unetbootin, you can get a Windows or Linux version.
If this works you should be able to just erase all data on the stick and reinstall as you have previously, using usb-creator.

---

### Post by Jackie78 on 2009-07-02
> **C.S.Cameron said:**
> Try installing to USB using Unetbootin, you can get a Windows or Linux version.
If this works you should be able to just erase all data on the stick and reinstall as you have previously, using usb-creator.

Thanks for your reply, I tried as you said, but finally get the same error upon booting the system. The strange thing is that I can see the start menu from the USB stick, and the boot logo flashes for about a minute, but then finally itswitches to textmode and shows me the busybox.

It look to me as if the BIOS recognizes the USB stick correctly, but as soon as Linux takes control over the device something fails.

Is there anything else I could try?

I have done two things:
- booted the stick on another computer, the stick works fine
- made a video showing the startup on my laptop, so you can better see what's failing, and when. I have cut around 45 seconds when the graphical Ubuntu logo shows up in order to decrease filesize:

[http://www.youtube.com/watch?v=JVnVvugmn2M](http://www.youtube.com/watch?v=JVnVvugmn2M)

---

### Post by C.S.Cameron on 2009-07-02
I have had similar, (busybox), failures installing from what I figure were bad CD's that booted ok themselves. Have you tried installing 32 bit?

---

### Post by Jackie78 on 2009-07-03
> **C.S.Cameron said:**
> I have had similar, (busybox), failures installing from what I figure were bad CD's that booted ok themselves. Have you tried installing 32 bit?

I haven't tried 32 Bit, but the CPU is an AMD Turion 64, and when I start the same image from CD, it works on that laptop. It's only failing from USB.

The USB is definitely errorfree too, since it starts on a desktop PC, and fails only on my laptop computer (see video).

---

### Post by nickmcg on 2009-07-06
I have the exact same problem with 9.04 32-bit on a 2Gb pny stick.

So far I can't find any way to make it work

Nick

---

### Post by schnelle on 2009-07-06
I think the problem is in Ubuntu 9.04 kernel and it seems it is not solved yet. I was installing 8.04 and 8.10 Ubuntu from usb stick on my laptop without problems, but since Jaunty came out I have the exact problem. I even started my own thread about this problem when Jaunty beta came out but nobody helped me ( [http://ubuntuforums.org/showthread.php?t=1124259](http://ubuntuforums.org/showthread.php?t=1124259) ).
So I burned Jaunty on CD and have installed it from it. I got the same error but installation continues.

---

