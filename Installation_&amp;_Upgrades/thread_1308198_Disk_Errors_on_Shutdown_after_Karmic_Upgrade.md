---
title: "Disk Errors on Shutdown after Karmic Upgrade"
date: 2009-10-31
forum: Installation &amp; Upgrades
---

### Post by CaKiwi on 2009-10-31
I upgraded from Jaunty to Karmic and all went well except when I shut down my system I get several disk error messages like

[1438.965070] Buffer I/O Error on drive loop0, logical block 2732034
[1443.000385] Aborting journal on device loop0

My system hangs and I need to press the power button to power down.

Any help greatly appreciated.

Cakiwi

---

### Post by rforums on 2009-11-01
I have the same problem too. This started happening when i upgraded from Jaunty to Karmic Beta. My laptop doesnt restart or shutdown.

---

### Post by wazzle on 2009-11-01
Same thing happens to my computer after the upgrade.

---

### Post by solmisation on 2009-11-01
I was having the same problems, but I done a clean install and all is working well now. Do a quick search on the forums and you will find some similar threads.

---

### Post by meor on 2009-11-02
This I/O error on shutdown happened to all my family's notebooks after the karmic upgrade. This happened either changing the file system to ext4 or not. And another thing it is only for those with wubi install (ubuntu in windows) but not with pure ubuntu install.

I am hoping someone has a solution for this...I am keeping tab of this thread...


Karmic rock...

---

### Post by saxonjf on 2009-11-02
Same issue here... I just want to be able to shutdown my lapper once I'm done at the coffeeshop.

---

### Post by Caracol on 2009-11-02
Same thing here:( It gave Disk Errors when I upgraded, from 9.04 to 9.10, and after a clean install with the CD too.
I have WinXP, and dual boot, on a laptop (HP nc6320).
oh and it messed up my GRUB after the clean install. I know I'm not helping much by not posting the errors but I'm feeling a bit disappointed and have no pacience left
cheers (I guess)

---

### Post by CaKiwi on 2009-11-03
The following solution corrected the problem for me

On the terminal:

   sudo gedit /etc/init.d/halt

Add the following line to the end of the halt script:

   rmmod snd-hda-intel

Proceed to a successful shutdown.

I found it in this post

[http://ubuntuforums.org/showthread.php?t=1306789&page=2](http://ubuntuforums.org/showthread.php?t=1306789&page=2)

CaKiwi

---

### Post by CaKiwi on 2009-11-03
I was too hasty with my last post. The first time shutting down after adding rmmod snd-hda-intel to the halt script worked, but it hasn't worked since.

---

### Post by CaKiwi on 2009-11-04
I found this solution in another thread. Post #19

[https://bugs.launchpad.net/ubuntu/+source/sysvinit/+bug/468589](https://bugs.launchpad.net/ubuntu/+source/sysvinit/+bug/468589)

---

