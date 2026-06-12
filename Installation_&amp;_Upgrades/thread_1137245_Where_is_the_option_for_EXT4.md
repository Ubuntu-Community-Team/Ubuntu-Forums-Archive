---
title: "Where is the option for EXT4?"
date: 2009-04-25
forum: Installation &amp; Upgrades
---

### Post by Kaneda187 on 2009-04-25
Just doing a clean install of 9.04 dual booting with vista, I cant seem to find the option for Ext4.

Anybody know?

Would this have anything to do with dual booting with vista?

---

### Post by Kaneda187 on 2009-04-25
bump

---

### Post by autocrosser on 2009-04-25
Should be in custom partitioning---you can also change ext3 to ext4 after your install---look thru the closed Jaunty testing forum.

---

### Post by briandu on 2009-04-25
when you install you have the opportunity to set file system to ext4

you should be able so state using mkfs command

---

### Post by ELMIT on 2009-04-25
I use Ubuntu Remix, but I have not found the option during partitioning to use ext4.

Have I just excitingly overlooked it or is it not available for Remix version?
Can I still convert it?

bye

R.

---

### Post by autocrosser on 2009-04-26
As I said above--look in the closed Jaunty testing forum---there are detailed instructions to convert a ext3 install to ext4---

You need to be using a LiveCD or from another install on your system--The other thing that you need to remember is that you MUST be using Grub from Jaunty--if you updated your install, the grub from Intrepid or older WILL NOT BOOT from ext4--

You will need to uninstall the older grub COMPLETELY & then install the newer grub that comes with Jaunty...I can not stress this enough---if you use the older grub your system will be UNBOOTABLE as soon as you convert to ext4.

I'll look thru the closed forum for some links--I'll post them shortly. Generally, ext4 is about 10~50% faster--You will see a large difference with large file transfers--a very small difference with lots of little file transfers. My system (1.5TB of drives--4 SATAII units & i7 920 desktop) went from a average of 30MB/s to 50~55MB/s on large transfers--up from 15~18MB/s to 25MB/s on small batch transfers---Your mileage will vary depending on your system.

Links: 

[http://ubuntuforums.org/showthread.php?t=1118295](http://ubuntuforums.org/showthread.php?t=1118295)
[http://ubuntuforums.org/showthread.php?t=1107027&highlight=ext4](http://ubuntuforums.org/showthread.php?t=1107027&highlight=ext4)
[http://ubuntuforums.org/showthread.php?t=1108452&highlight=ext4](http://ubuntuforums.org/showthread.php?t=1108452&highlight=ext4)
[http://ubuntuforums.org/showthread.php?t=1090488&highlight=ext4](http://ubuntuforums.org/showthread.php?t=1090488&highlight=ext4)

---

### Post by whoop on 2009-04-29
Or read the howto convert ext3 to ext4: [http://ubuntuforums.org/showthread.php?t=1118295](http://ubuntuforums.org/showthread.php?t=1118295)

---

