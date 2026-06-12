---
title: "Low Brightness after update. Applet doesn't work yet"
date: 2008-12-22
forum: Hardware
---

### Post by october1917 on 2008-12-22
I run Ubuntu 8.10 on a Lenovo Thinkpad R61i

Everything was running alright. According to the Syntaptics History:
I Upgraded the following packages:
linux-generic (2.6.27.10.13) to 2.6.27.11.14
linux-headers-generic (2.6.27.10.13) to 2.6.27.11.14
linux-image-generic (2.6.27.10.13) to 2.6.27.11.14
linux-libc-dev (2.6.27-11.21) to 2.6.27-11.22
linux-restricted-modules-common (2.6.27-10.14) to 2.6.27-11.15
linux-restricted-modules-generic (2.6.27.10.13) to 2.6.27.11.14

and

Installed the following packages:
linux-headers-2.6.27-11 (2.6.27-11.22)
linux-headers-2.6.27-11-generic (2.6.27-11.22)
linux-image-2.6.27-11-generic (2.6.27-11.22)
linux-restricted-modules-2.6.27-11-generic (2.6.27-11.15)

and 

Reinstalled the following package:
libgl1-mesa-dri (7.2-1ubuntu2)

During the next boot the brightness was very low, before even the Linux boot-up, and it kept the same during the normal session. The Gnome Brightness Applet doesn't respond no more, and so do the Brightness Keys (Fn+smthing)

Could you help me?
Thank you.

---

### Post by sean22190 on 2008-12-23
Same problem with Thinkpad T61. :(

Any help out there?

---

### Post by october1917 on 2008-12-23
I fixed it my friend.

Thats a bug of the proposed kernel. To fix it do the following:

1) DO NOT SKIP THIS STEP. Restart your computer. While loading the GRUB press Esc to display the boot options. Select the previous Kernel to use for boot-up

2) Open Synaptic and go Settings-->Repositories. In the Updates tab of the new window untick the Proposed Updates to remove this repository then Close and Reload in order to load the new repositories

WARNING: during the next step you may be prompted to choose what to do with a boot configuration file. I selected "Leave the current version" or something like that, and it works fine. I suggest you that. I don't know what can happen if you select other option.

3) Close Synaptic and give in terminal the following command:
```
sudo apt-get autoremove linux-image-2.6.27-11-generic linux-headers-2.6.27-11-generic linux-headers-2.6.27-11 linux-restricted-modules-2.6.27-11-generic
```It will remove also linux-image-generic, linux-headers-generic, linux-restricted-modules-generic e.t.c

The menu.lst file will be auto-regenerated. So you have just to reboot.

Let me now it that worked for you too.

---

### Post by mariner09 on 2008-12-24
Confirmed that 2.6.27-11-generic has issues with function keys on laptops and what they control.

2.6.27-10-generic is fine.  Instead of removing it you can also modify the menu.lst file to choose the -10 kernel as the default until a new -11 is provided.

---

### Post by jonojono on 2008-12-26
Confirmed here as well on Thinkpad X300.  Is this issue being tracked in launchpad?

---

### Post by sbeattie on 2009-01-05
I reported the issue in [bug 314119]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/314119"); it appears to have been caused by fixes added to address [bug 257827]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/257827").

---

### Post by bheremans on 2009-01-06
same problem on my asus F3JC. low brightness on startup. But I can adjust it with the fn keys. but when reaching the maximum in the applet i have to hit the fn button a few more times

---

### Post by babarhaq on 2009-02-15
Confirm on my X300 as well. Booting into older kernel resolves the issue.

---

### Post by nnahler on 2009-02-17
And the same on a Thinkpad X61.

---

### Post by pintasart on 2009-04-26
I have the same problem when I upgrade 8.10 to 9.04. The brightness works well before login but after does't works. Fn+F2 don't work and the applet also and on power management configurations works but I have a quick "flash". I have a ASUS F6A series

---

### Post by Manix1 on 2009-04-27
I did a fresh clean install of 9.04 to my R61i and brightness control works flawlessly. I tried running an update from 8.10 but pretty much everything was broken afterwards. :P

---

### Post by iacchos on 2009-05-25
I was having this problem and I implemented this proposed fix and my problem has gotten worse.  I'm using ASUS F6A and since 9.04 upgrade I've been having a terrible time with managing my brightness.  None of the other solutions I've found on related topic appear to work either.  I'm feeling pretty desperate here.

---

### Post by lanruisen on 2009-06-01
I'm having the same problem with my Asus n20a, but I tried the latest Mandriva live cd and it worked flawlessly.  modeprobe -r video, and then reloading modeprobe video works so I can control the brightness, but it still flickers from time to time, and I don't want to have to reload the video module everytime I reboot.

---

### Post by Danifamous on 2009-09-09
I have a Toshiba satellite l350-203 pro, and have some trouble adjusting brightness. after a fresh install with kernel 2.6.28-11 I can dim the screen. but after updating to 2.6.28-15 or whatever the one is to date, i cannot adjust it. with the screen being full brightness my battery dies within an hour fro full charge.
this problem and the fact my volume control on the front of my laptop being over-sensitive, I am disliking using Linux.
so if I can have any workarounds, or a bug fix, that would be much appreciated.

---

