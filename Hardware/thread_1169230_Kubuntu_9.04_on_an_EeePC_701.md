---
title: "Kubuntu 9.04 on an EeePC 701?"
date: 2009-05-25
forum: Hardware
---

### Post by Takmadeus on 2009-05-25
Greetings!

Now I come to you in search of knowledge...

I have an EeePC 701 4G, and after trying to get UNR 9.04 working with no success, I had to stick to easypeasy.

Well, here is the thing, unfortunately UNR makes use of some nifty icon animations that render my netbook useless, because just moving the cursor makes the system slow at the point of almost freezing.

Now, I always liked how KDE looked, and with KDE 4 well, I could not ask for more. The point is that I was wondering if it ran properly in an EeePC.

Does any of you have tried Kubuntu 9.04 in such a netbook?, how well did it ran?, does Ubuntuone work well in kubuntu?, which considerations should I take into account when installing it (apart from installing array's kernel and whatnot)

does it run fluently?

Thanks in advance for the answers, any help is much appreciated.

---

### Post by paulkingnz on 2009-06-11
I am running jaunty, 9.04 and everything is running fine. I installed it from a sd card and then did an apt-get upgrade. I did have a problem with running out of disk space so I had to install some of the upgrades incrementally. At the moment I'm up to kernel 2-6-28-12.

---

### Post by mendieta on 2009-06-28
> **paulkingnz said:**
> I am running jaunty, 9.04 and everything is running fine. I installed it from a sd card and then did an apt-get upgrade. I did have a problem with running out of disk space so I had to install some of the upgrades incrementally. At the moment I'm up to kernel 2-6-28-12.

What are you guys doing with the wifi driver? I just upgraded from 8.04 to 9.04. I could see my wifi router at home for a couple hours. But now I can't see it anymore (no wireless network is detected). Enabling/disabling the atheros binary driver in "Hardware Drivers" is not making a difference. How frustrating! Many thanks in advance

---

### Post by mendieta on 2009-06-29
I fixed the problem by removing old blacklisting in /etc/modprobe.d/, I am using the default (Open Source) driver (ath5k) with no issues now.

---

### Post by mendieta on 2009-07-04
Back to the original post, KDE 4 looks fantastic in my again eee 701. The only issue is boot time: even on ext-4, it boots in 30 seconds to the X server, but then it takes 55 additional seconds to complete the autologin. A little too much, but that's the only thing really. I love it.

---

### Post by mendieta on 2009-07-04
Ah, I forgot to add, I did have to adjust the graphics following the advice from a very popular thread here in Ubuntuforums:
[http://ubuntuforums.org/showthread.php?t=1130582](http://ubuntuforums.org/showthread.php?t=1130582)

(I use gdm to run the shell script recommended there automatically)

---

