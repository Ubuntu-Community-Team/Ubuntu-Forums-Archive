---
title: "Can't log in after upgrading to 9.04 - weird colors/logos/black screen"
date: 2009-04-27
forum: Installation &amp; Upgrades
---

### Post by lazypeterson on 2009-04-27
Hey, I just upgraded from 8.10 and once I installed and rebooted, Ubuntu loaded, but when it should bring up the login screen, I only see some small mashed text and small faded Ubuntu logos towards the top of the screen. 

I first let it sit for a while, but it was frozen. I rebooted, no luck. Rebooted again in recovery mode and tried to fix broken packages, no luck there either. I chose the option to try and fix graphics problems, but that didn't do anything either.

I'm running a Toshiba Satellite laptop with a Nvidia graphics card.

Any help would be greatly appreciated!!!!

---

### Post by lazypeterson on 2009-04-27
I'm getting:

ata1 softreset failed (device not ready)
ata3 softreset failed (device not ready)

before the Ubuntu load screen appears

---

### Post by luckyu on 2009-04-27
same thing as well!

---

### Post by abyrne on 2009-04-27
ata means hard drive. do you have a way of checking the status of your hard drive (ex. Other OS on same HD, Ubuntu Live CD, ect.)?

---

### Post by luckyu on 2009-04-27
yes i have a live disc

---

### Post by lazypeterson on 2009-04-27
I split my hard drive with Windows, it's working fine on here.

---

### Post by vargasman on 2009-04-27
I am also having this problem after upgrading. I know my system hardware is good as I am posting from my 8.10 live cd. Any ideas what could be the issue?

---

### Post by vargasman on 2009-04-27
After reading other posts i tried this and it worked for me.

1. reboot into recovery mode netroot (root with networking)
2. enter the following code:```
apt-get remove --purge xorg-driver-fglrx
```
3. reboot and type```
sudo apt-get install --reinstall libgl1-mesa-glx libgl1-mesa-dri
```

Hope this helps.

---

### Post by lazypeterson on 2009-04-27
> **vargasman said:**
> After reading other posts i tried this and it worked for me.

1. reboot into recovery mode netroot (root with networking)
2. enter the following code:```
apt-get remove --purge xorg-driver-fglrx
```
3. reboot and type```
sudo apt-get install --reinstall libgl1-mesa-glx libgl1-mesa-dri
```

Hope this helps.

Hooray Vargasman!!!! Thanks a million, this worked great!

---

