---
title: "Lenovo W530"
date: 2013-10-23
forum: Hardware
---

### Post by RichardET on 2013-10-23
I am curious - and I am a bit afraid to find out the answer - if I were to run Ubuntu natively on my W530, would I see the same quality of video output with its NVIDIA graphics, or would I be disappointed?

---

### Post by lah-ca on 2013-10-23
Hi,

If you get the the live ISO (generally the one you download by default from the Ubuntu website) and burn a DVD or create a bootable USB key, you can boot into Ubuntu and try it without installing so that you can get a general idea of how it will function on your system.  Just make sure you read everything carefully before pushing any keys or making any mouse clicks - ;)  The 64 bit version is good if you have lots of RAM in your system.  There are generally fewer issues with the 32 bit version, though - IMHO.

Note that booting to the DVD/USB key will be very much slower than if Ubuntu were installed on your hard drive; this is because when you do things with Ubuntu running from the installation media, it is constantly having to pull files from the media and decompress them and also because the optical drive/USB key is slower than a hard drive.  Ubuntu will run a lot faster when actually installed.  Its speed is generally comparable to or better than that of Windows on the same hardware. 

Note also that there will probably be better NVidia drivers available through a (proprietary) driver update wizard once Ubuntu is installed.  The installation of these will improve things in a number of ways, not necessarily in general desktop display quality but in performance with games and things that are more demanding on the video hardware - if you get around to installing, choose the driver that says "(recommended)."

 My experience is that NVidia support for Linux is generally very good and that the display quality in Ubuntu is largely comparable to that in Windows running on the same hardware.

This all said Ubuntu is not Windows.  Don't expect it to be.  It is good.  It is different.

---

### Post by buzzingrobot on 2013-10-23
I run my W530 on the Intel because I don't do anything that requires the Nvidia. I've installed and used the Nvidia driver and did not notice any difference, other than a small increase in temperature.

That applies to my usage patterns, of course.

If you set your BIOS to use the Nvidia card (not Intel or Optimus) then the live image should boot with the open source Nouveau driver for Nvidia.  I do not know if a proprietary Nvidia driver can be installed into a live image session.

---

### Post by RichardET on 2013-10-25
Yeah I guess I should try a live CD first.  It's ok to continue to use a VM on it, but I do enjoy running Ubuntu natively on my B590.

---

