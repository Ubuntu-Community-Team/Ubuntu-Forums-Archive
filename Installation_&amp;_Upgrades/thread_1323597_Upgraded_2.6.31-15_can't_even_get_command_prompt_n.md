---
title: "Upgraded 2.6.31-15 can't even get command prompt now."
date: 2009-11-11
forum: Installation &amp; Upgrades
---

### Post by Martin__ on 2009-11-11
Hi, I just upgraded my Karmic 2.6.31-15.x kernel to the newest version 2.6.31-15.y. Yesterday, I uninstalled all the other kernels on that partition in an effort to &quot;clean up&quot; (won't do that again).  Now I can get to grub, and after selecting recovery mode, I see the usual text scrolling by. But then I get a blank screen with only a blinking cursor.   I don't see the capslock and numlock leds blinking, and with alt-control-delete I can still reboot. I don't have any SSH server installed.  I do have a semi-working updated-from-alphas Karmic on another partition. And I have a karmic rescue disk as well.  Does anyone know how I can install back one of the older kernels I have from within the other Karmic or rescue disk? I tried to google, but all the keywords I can think of are too generic to get anywhere.  Thanks, Martin.

---

### Post by JoelOl75 on 2009-11-12
> **Martin__ said:**
> Hi, I just upgraded my Karmic 2.6.31-15.x kernel to the newest version 2.6.31-15.y. Yesterday, I uninstalled all the other kernels on that partition in an effort to &quot;clean up&quot; (won't do that again).  Now I can get to grub, and after selecting recovery mode, I see the usual text scrolling by. But then I get a blank screen with only a blinking cursor.   I don't see the capslock and numlock leds blinking, and with alt-control-delete I can still reboot. I don't have any SSH server installed.  I do have a semi-working updated-from-alphas Karmic on another partition. And I have a karmic rescue disk as well.  Does anyone know how I can install back one of the older kernels I have from within the other Karmic or rescue disk? I tried to google, but all the keywords I can think of are too generic to get anywhere.  Thanks, Martin.
I'm not sure why just a simple kernel update would bork everyhting... I usually can fix it using a method like:

Boot off a live cd and open up a terminal.

mkdir mp
sudo mount /dev/sda1 -t ext4 mp
sudo chroot mp
sudo apt-get install linux-image-2.6.31-14-generic


Replace the sda1 with whatever partition holds your '/' partition.  Also replace the ext4 with ext3, xfs, jfs.... if you used something different.

Also if you used a separate partition for /boot, you will need to mount that AFTER chrooting into your installation.

Just make sure grub updates and finds all the kernel images... I havn't tried this method with grub 2 so YMMV

If it doesn't, (and -14 installed but is not in the boot menu) hold the shift key down on boot and press 'e' to edit the grub entry, scroll over the -15 kernel and change the -15 to -14 in both the kernel image and the initrd image, remove the 'quiet splash' off the end will give you more information thats generally hidden behind the splash screen, then press CTRL-X to boot it.

Are you sure you didn't remove anything else besides the old kernel image? 

Hope this helps.

Joel.

---

### Post by Martin__ on 2009-11-12
Thanks. I can press:"e" in grub, remove the remove the 'quiet splash' off the end. Then it just boots.

Thanks, Martin

---

### Post by bitshifternz on 2009-11-25
I have three partitions, two ext4 and one ext3. After the 2.6.31-15 update my ext3 partition is not mounting on boot. If I try to mount it manually it says it's busy. Booting with the previous kernel works fine. Fortunately I boot off the ext4 partition.

Are you using ext3?

---

### Post by Martin__ on 2009-11-25
Hi, no I'm using ext4 only.
When I remove the 'quiet splash' off the end in the grub menu, it booted most of the time.

I then changed the grub configuration accordingly and reduced the timeout as well and now it boots about 95% of the time.

---

### Post by phillw on 2009-11-25
> **Martin__ said:**
> Hi, no I'm using ext4 only.
When I remove the 'quiet splash' off the end in the grub menu, it booted most of the time.

I then changed the grub configuration accordingly and reduced the timeout as well and now it boots about 95% of the time.

From that, you can also choose your linux version to load. >  Ok, well, if it's Grub 2, have him highlight Ubuntu, then "e". That should open an edit window with the commands visible. On the linux and initrd lines the kernel should be visible. In both lines, they can edit the line and replace -15 (or whatever) with -14, then boot.[https://help.ubuntu.com/community/Kernel/Compile](https://help.ubuntu.com/community/Kernel/Compile)  has the HowTo on putting an older kernel back on. Whilst me telling you to always keep the previous working kernel image is not a gr8 deal of help - It may help others.

> linux 14 Within Synaptic Package Manager will return the older images for you to download. You'll be wanting the ones marked as '14'. I've never done that, but it is evidently possible.

 [https://help.ubuntu.com/community/Grub2#Using%20CLI%20to%20Boot](https://help.ubuntu.com/community/Grub2#Using%20CLI%20to%20Boot)  will tell Grub which one to load

Bootijng into recovery on v15 and then repairing broken packages, either by menu or by [http://ubuntuforums.org/showthread.php?t=169013](http://ubuntuforums.org/showthread.php?t=169013)

Seems to have given good results, some have had to boot twice to get it to settle down.

As to why 15 seems to have broken some peoples computers - we're still un-aware. It was only a patch of a few 'bugs' and not a major release. If you'd like further help - I'm watching over [http://ubuntuforums.org/showthread.php?t=1335464](http://ubuntuforums.org/showthread.php?t=1335464)  and you are welcome to pop over and see what we have tried.

Regards,

Phill.

---

### Post by ergo14 on 2009-11-25
i have just submitted this:

[https://bugs.launchpad.net/ubuntu/+bug/488148](https://bugs.launchpad.net/ubuntu/+bug/488148)

maybe it will help someone ?

---

### Post by sdowney717 on 2009-11-25
I just upgraded to 2.6.31-15 and get errors. Boots me to a login command prompt

---

