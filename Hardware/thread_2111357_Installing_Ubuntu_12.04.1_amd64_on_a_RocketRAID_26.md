---
title: "Installing Ubuntu 12.04.1 amd64 on a RocketRAID 2640x4"
date: 2013-02-01
forum: Hardware
---

### Post by MrMusic25 on 2013-02-01
So I have been running Ubuntu 12.04.1 from a USB drive on a computer I have set up using an external RAID card, a Highpoint RocketRAID 2640x4. I needed it for the RAID 5. After following the [tutorial]("http://ubuntuforums.org/showthread.php?t=1899544"), I was able to get Ubuntu to recognize the hard drive and do an installation. When it completed I powered down and removed the USB, and changed BIOS to boot from the RocketRAID. Then, it showed the familiar purple screen, but never fully loaded. I let it sit for about 12 mins before pressing the restart button. When I turned it on again, it then brought me to the GRUB screen, and I selected to load Ubuntu. After just 2-3 mins, it entered the shell saying it could not boot. I tried rebooting to the recovery mode, only to see the same screen.

Right now, I have re-done the steps from the other tutorial and am going to re-install it, as I have made a change to the RAID configuration to see if it helps. But my question is: how do I get this to work? It's almost like under the USB I can install the driver, but when I try to boot from the RAID card, it can't recognize itself... Even though it can load GRUB... Thoughts on how to get it working? Thanks!

---

### Post by greg finnegan on 2013-02-02
If i where you i would just re-install! i have had many installs like what you are describing. it usually is just a bad install. If it still messes up i would do it on a CD. I'm not sure if that is the problem but it could be.

---

