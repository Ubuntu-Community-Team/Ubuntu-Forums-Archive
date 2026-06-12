---
title: "Boots to black screen after 11.04 install on CF-18"
date: 2011-05-02
forum: Hardware
---

### Post by derekkrebs on 2011-05-02
I can install Ubuntu 10.10 just fine on this machine (Panasonic CF-18), however i can not do a clean install of xubuntu 11.04 or xubuntu 10.04.  

xubuntu 11.04 will go through the installation process and can boot to a live cd just fine, however after reboot the pc boots to a black screen.  I have tried holding down shift on boot and booting into recovery mode but i still get a black screen.  This also happened when I upgraded Ubuntu 10.10 to Ubuntu 11.04.  

Xubuntu 10.04 will not boot into live cd or installation, im pretty sure the install disc just doesn't include the drivers for my computer.  

I have yet to try xubuntu 10.10 to see if it works, but I was wondering if theres any way I can boot from the Ubuntu 10.10 live cd and install the video drivers that work on my laptop.

---

### Post by derekkrebs on 2011-05-02
I believe I solved the issue, I think this might work with Ubuntu 11.04 as well.  I held down shift to bring up grub.  After selecting boot into recovery mode I immediately started spamming F4 and 48 simultaneously.  I was then able to boot into failsafe graphics mode.  Then I ran sudo -configure Xorg, got an error log, rebooted, and am able to boot into the normal installation.  I have no idea why it works but it does.  For some reason GRUB shows up every time on boot.

---

### Post by derekkrebs on 2011-05-02
Doesn't work anymore.  After the first reboot things went fine.  Powered off and powered on, it skipped grub menu, i get artifacting all over the screen then it goes to black.

---

### Post by Missi0n on 2011-05-03
im having this same problem when installing Xubuntu on my sony viao - it will install Ubuntu 11.04 fine, it just doesnt run as fast as i'd like it to, so i made a live cd of Xubuntu 11.04, the live cd loaded fine, however after the install when i turned the computer on the screen just flashed and stayed black, nothing else happened? i've tried fresh installing 3 times :/

---

### Post by Missi0n on 2011-05-04
bump, please help? anyone?

---

### Post by nicks27 on 2011-05-11
I also repeatedly got a blank screen when booting Xubuntu 11.04 desktop i386 from a bootable USB stick or bootable liveCD. I found I had to disable USB Legacy Support in my laptop's BIOS (which I had previously enabled to try and get it to detect the bootable USB stick), and now I've booted from the liveCD fine.

---

### Post by krbergh on 2011-07-29
Hi!

I have the same boot problem with xubuntu 11.04. I can boot from the xubuntu 11.04 desktop CD just fine, but after I install on my computer, it just boots to black screen. However, I've noticed that when powering down after booting into a black screen (using the power button), the xubuntu splash screen appears. This indicates that there is something up with the graphics driver. I have a Dell Inspiron 500m laptop...

Any ideas for a solution?

Regards,
KrBergh
(Total Linux Noob)

---

### Post by Toz on 2011-07-29
See posts #26 & #29 of [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/685611]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/685611")

And here: ([http://ubuntuforums.org/showthread.php?t=1743535]("http://ubuntuforums.org/showthread.php?t=1743535"))

---

