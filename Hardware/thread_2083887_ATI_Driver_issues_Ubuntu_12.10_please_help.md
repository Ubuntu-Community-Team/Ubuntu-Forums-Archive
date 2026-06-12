---
title: "ATI Driver issues Ubuntu 12.10 please help?"
date: 2012-11-13
forum: Hardware
---

### Post by RandyPro on 2012-11-13
SO.. I have made the switch from Windows to Ubuntu, Ive tried 12.04 then switched to 12.10. I have only 1 issue.. I cant seem to sort out the drivers for my ATI Mobility 4200 HD here are the specs on my lap top just in case it helps:
Gateway NV-53
AMD Anthlon II X2 M300
4 Gigs Ram
250Gb hdd

So ive downloaded and attempted to run the drivers on my laptop but i keep getting a message stating "tools" are missing while im installing. Ive looked for a step by step guide and have struck out everywhere i look or i get similar errors. Ill admit it doesnt bother me much the only thing ive noticed being an issue is a few 720p videos, all 1080p videos and anytime i try to use youtube it lags.. doesnt matter if its HD or 360p as soon as i put any youtube video in full screen the video lags and begins to fall behind and the sound works flawlessly
Thanks in advance, I LOVE ubuntu, the more i learn and use it the more i fall in love with it but this issue could be a deal breaker for me, never had any issues like this with windows 7.

---

### Post by samsom63 on 2012-11-13
> **RandyPro said:**
> SO.. I have made the switch from Windows to Ubuntu, Ive tried 12.04 then switched to 12.10. I have only 1 issue.. I cant seem to sort out the drivers for my ATI Mobility 4200 HD here are the specs on my lap top just in case it helps:
Gateway NV-53
AMD Anthlon II X2 M300
4 Gigs Ram
250Gb hdd

So ive downloaded and attempted to run the drivers on my laptop but i keep getting a message stating "tools" are missing while im installing. Ive looked for a step by step guide and have struck out everywhere i look or i get similar errors. Ill admit it doesnt bother me much the only thing ive noticed being an issue is a few 720p videos, all 1080p videos and anytime i try to use youtube it lags.. doesnt matter if its HD or 360p as soon as i put any youtube video in full screen the video lags and begins to fall behind and the sound works flawlessly
Thanks in advance, I LOVE ubuntu, the more i learn and use it the more i fall in love with it but this issue could be a deal breaker for me, never had any issues like this with windows 7.

Do you use the open source or the proprietary drivers? You can use the legacy version of the proprietary drivers for a Radeon HD 4200 BUT those are not supported in ubuntu 12.10 (as opposed to ubuntu 12.04). As far as I know, the legacy drivers are not compatible with the xserver version that comes with ubuntu 12.10. You can downgrade the xserver and install the legacy drivers in one go but it did not work for me. More info here: [http://www.mail-archive.com/desktop-packages@lists.launchpad.net/msg170845.html](http://www.mail-archive.com/desktop-packages@lists.launchpad.net/msg170845.html)

---

### Post by RandyPro on 2012-11-13
Ive tried installing the legacy drivers from the Ati/AMD website, I'll give that site a look over thanks for the quick reply. SO your having a similar issue you havnt been able to resolve? where might i find the open source drivers? again thanks!

---

### Post by samsom63 on 2012-11-13
> **RandyPro said:**
> Ive tried installing the legacy drivers from the Ati/AMD website, I'll give that site a look over thanks for the quick reply. SO your having a similar issue you havnt been able to resolve? where might i find the open source drivers? again thanks!

The open source drivers are pre-installed so you have those, but they might not be as good as the proprietary ones. I don't know about that, that's why I wanted to install the legacy drivers but it turned out I am one of those for which it did not work.

---

### Post by RandyPro on 2012-11-13
i understand, and ya that sucks... im currently running that work around with my fingers crossed. If i have to i might try a totally different linux like desbian or fedora, i have to admit i absolutely love it since switching. But not being able to watch anything on youtube is a huge deal breaker... sucks cuz the thought of going back to windows after using this UI literally turns my stomach..

---

### Post by RandyPro on 2012-11-13
ok.. so that didnt work.. after i restarted the computer i have a new loading screen and then nothing.. just a black screen?? anyway i can go back or safe mode my computer??

---

### Post by samsom63 on 2012-11-13
> **RandyPro said:**
> ok.. so that didnt work.. after i restarted the computer i have a new loading screen and then nothing.. just a black screen?? anyway i can go back or safe mode my computer??

did you try to install the legacy drivers? If so, drop to root shell (one of the option in recovery mode), and remove the package:

apt-get purge fglrx-legacy

---

### Post by RandyPro on 2012-11-13
> **samsom63 said:**
> did you try to install the legacy drivers? If so, drop to root shell (one of the option in recovery mode), and remove the package:

apt-get purge fglrx-legacy
how do i access the recovery mode? not sure what you mean by drop to root? sorry i am still a bit of a noob with this

---

### Post by samsom63 on 2012-11-13
> **RandyPro said:**
> how do i access the recovery mode? not sure what you mean by drop to root? sorry i am still a bit of a noob with this

If you're stuck on black screen when booting then you'll have to hard shut down. When you turn on your computer again, hold shift to go into grub menu, and from there, choose recovery mode, and then drop to root shell.

---

### Post by RandyPro on 2012-11-13
> **samsom63 said:**
> 

apt-get purge fglrx-legacy
when i enter this in from that screen i get an error:

W: not using locking for read only lock file /var/lib/dpkg/lock
E: unable to write to var/cache/apt
E: the package list or status file could not be parsed or opened

??

---

### Post by samsom63 on 2012-11-13
> **RandyPro said:**
> when i enter this in from that screen i get an error:

W: not using locking for read only lock file /var/lib/dpkg/lock
E: unable to write to var/cache/apt
E: the package list or status file could not be parsed or opened

??

Oh yeah, i had that too. Type:

mount -o remount,rw /

---

### Post by RandyPro on 2012-11-13
> **samsom63 said:**
> Oh yeah, i had that too. Type:

mount -o remount,rw /
  before typing apt-get purge-legacy?

---

### Post by samsom63 on 2012-11-14
> **RandyPro said:**
> before typing apt-get purge-legacy?

Yes, sorry it was 4am my time when I answered you and I did not explain much.

Type first 
mount -o remount,rw /

and then

apt-get purge fglrx-lecgacy

The first command will give you authorisation to modify files and directories and the second one will un-install the package.

let me know if that works.

---

