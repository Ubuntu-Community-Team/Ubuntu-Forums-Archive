---
title: "trouble with Xubuntu boot disk."
date: 2009-04-23
forum: Installation &amp; Upgrades
---

### Post by caspertk on 2009-04-23
I've been using linux for a while and it's a little slow on my laptop, so i tried to get Xubuntu. I burned it do a disk, but when I tried to use it as a boot disk, nothing happened. I changed the boot order to make the disk boot first, but still no results. Any advice would be awesome. 

Thanks guys
casper

---

### Post by caspertk on 2009-04-23
bump...please help

---

### Post by Yucko on 2009-04-23
I had the same thing. But then I booted in Windows XP on my laptop and from there browse the install-cd and run the install from there.

---

### Post by caspertk on 2009-04-23
ok ill give it a shot and let you know if it worked. thx.

---

### Post by caspertk on 2009-04-23
yeah. unfortunately i dont have a boot disk to go back to windows, and I can't find any free downloads or trials. so...?

---

### Post by chessnerd on 2009-04-23
Do you have a way to verify that the disk burned the image successfully? I recently downloaded and burned a Puppy Linux CD that didn't load the kernel when I tried it. I reburned it on a new disk and it worked on that one, so it could be that there is an error on the disk.

Also, if you are working with the Live CD, and you are sure you want to install Xubuntu, you could try the Alternate CD and see if that works. (Although, unless your computer has pretty low specs, you shouldn't have a problem with a Live CD for Xubuntu.)

Next, which version did you burn? If you burned Jaunty (9.04), you could try an Intrepid (8.10) disk and then, if that works, you could upgrade once it installs. If you tried for Hardy (8.04), you could get a Dapper Drake (6.06) disk and try to upgrade from that.

Finally, if you already have Ubuntu, you can get the Xubuntu desktop (Xfce) under Synaptics by installing xubuntu-desktop. This also means that if Xubuntu isn't working, you could install Ubuntu and then put Xfce on it under Synaptics.

Hope this helps.

---

### Post by sirwhiteout on 2009-04-23
I just had the same problem, not from a burned CD, but from a USB startup of the Xubuntu desktop 9.04 amd64 live image. I checked the MD5 sum of the iso file, and it was fine.

It worked fine when I went through the same procedure for Xubuntu 8.10, though.

Now I'm downloading the Ubuntu 9.04 image to see if the same thing happens.

---

### Post by sirwhiteout on 2009-04-24
> **sirwhiteout said:**
> Now I'm downloading the Ubuntu 9.04 image to see if the same thing happens.

Yep. Same thing. It seems to be unable to find a modules file during bootup, which causes it to crash.

---

