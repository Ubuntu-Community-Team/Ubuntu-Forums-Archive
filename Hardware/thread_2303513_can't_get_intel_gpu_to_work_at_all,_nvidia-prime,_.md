---
title: "can't get intel gpu to work at all, nvidia-prime, ubuntugnome 15.10"
date: 2015-11-19
forum: Hardware
---

### Post by Halpm on 2015-11-19
Could use some help troubleshooting and fixing this one.
I've just bought a new custom laptop ([here]("https://www.mm-vision.dk/Vision-S-Series-S6564-15-6-baerbar")) with a  i7-6700HQ CPU and a GeForce GTX 960M. I put Ubuntu 15.10 on it, even though I usually stick to LTS versions, 14.04 couldn't find the hardware and didn't boot.
But I can't switch to the intel card in nvidia-prime. When I logout and login, it goes black and returns to the login screen. I can then go to tty1 and switch the nvidia card back on and then I can login again.
I'm running nvidia-358.09 and have upgraded to kernel 4.3 to see if that helped, but it didn't. I don't think the system is loading i915, but I'm not sure. I'm not even sure if that's the right driver?
As it is, the computer is usable - I'm just not getting very good battery times as I'm stuck using the nvidia card.
Installing bumblebee as I did in previous versions just gives me a black screen at startup.

---

### Post by Halpm on 2015-11-24
*Bump?*

---

### Post by Halpm on 2015-12-02
Ok - I'll bump one last time, then leave this here :(

---

### Post by oldfred on 2015-12-02
Have you tried this?
 Skylake needs this boot parameter: 
 i915.preliminary_hw_support=1
[http://www.phoronix.com/scan.php?page=news_item&px=Intel-SKL-Prelim-Support](http://www.phoronix.com/scan.php?page=news_item&px=Intel-SKL-Prelim-Support)

---

### Post by Halpm on 2015-12-07
Yep, tried that - assuming I put it in the right line? Needs to go in the same line as "quiet splash" yeah?

---

### Post by oldfred on 2015-12-07
I suggest replacing quiet splash and then maybe you can see boot process and if something else shows issues. But new systems are so fast it scrolls by too quick to see much.

---

### Post by Halpm on 2015-12-07
Yep tried that - didn't work. Goes to fast to see anything else either.

---

### Post by oldfred on 2015-12-07
If you are able to boot then all that info is in log files.

Newer systems with systemd:
       systemd-analyze blame 
systemd-analyze critical-chain 
systemd-analyze plot

            [http://www.dedoimedo.com/computers/systemd-blame.html](http://www.dedoimedo.com/computers/systemd-blame.html)
[https://wiki.archlinux.org/index.php/Improve_boot_performance](https://wiki.archlinux.org/index.php/Improve_boot_performance)
[https://bbs.archlinux.org/viewtopic.php?id=189354](https://bbs.archlinux.org/viewtopic.php?id=189354)

    
Older systems with Upstart
 gksudo gedit /var/log/dmesg
sudo grep -E -i "error|warning" /var/log/dmesg

---

### Post by Halpm on 2015-12-07
Well, according to this plot, there's nothing obviously taking a long time, but I'm often getting the message that xorg has crashed when I log in for the first time after booting up, and do I want to send an error report? Could that have anything to do with it? How do you check if the right modules are even loading?
[ATTACH=CONFIG]266034[/ATTACH]

---

### Post by oldfred on 2015-12-07
I have not paid attention to xorg for years. When I first started Ubuntu with nVidia, I had to manually edit xorg to get system working. And after every upgrade. But Since about 10.10 it has just worked with nomodeset.
I saw where they wanted to eliminate xorg, but do not think that has happened.

---

