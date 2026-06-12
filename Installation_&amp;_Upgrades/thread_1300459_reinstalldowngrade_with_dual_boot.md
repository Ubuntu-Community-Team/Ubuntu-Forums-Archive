---
title: "reinstall/downgrade with dual boot"
date: 2009-10-25
forum: Installation &amp; Upgrades
---

### Post by clear_runway on 2009-10-25
after upgrading to 9.10 I ran into a ton of problems and therefore I have decided that the best way to get back to 9.04 is to do a fresh reinstall over the ubuntu partition.

however, I have a dual-boot machine with vista on the other partition, and I need to keep vista. would somebody please explain to me - like you would an idiot - how to reinstall jaunty over karmic whilst preserving vista?

I understand there are a set of advanced options for partitioning in the installer, but frankly they scare me, and I would seek your advice before taking actions that could destroy my vista partition.

I really know very little about Linux or Ubuntu or even partitioning as a I am a recent windows convert so please forgive my ignorance.

---

### Post by MelDJ on 2009-10-25
follow: [http://bobmorris.wordpress.com/2008/02/09/how-to-uninstall-ubuntu-on-dual-boot-windows-xp-using-windows-only/](http://bobmorris.wordpress.com/2008/02/09/how-to-uninstall-ubuntu-on-dual-boot-windows-xp-using-windows-only/)

if its not broken, maybe you could keep karmic for 4 more days and then upgrade to the stable version

---

### Post by clear_runway on 2009-10-25
naw, its destroyed. some driver thing. I think I'll wait another six months and upgrade then.

---

### Post by MelDJ on 2009-10-25
if thats the case, just wait another 4 days for karmic to come out. why go through installing jaunty when you can get a newer edition of ubuntu in just 4 days?

---

### Post by clear_runway on 2009-10-25
well, that was and adventure. I ended up wrecking grub with the partition manager, so nothing would boot at all (my computer came with a backup partition, useless because it also came with 2 restore disks, so I got rid of that)

after much panicking, I figured if I reinstalled ubuntu it would reinstall grub, which it did. problem solved. then all I had to do was repair my vista installation (this happened last time, so I was expecting it)

if I was unable to  save my vista install I would have had to use the restore disks, and would have been well and truly screwed. boy, was that scary.

---

### Post by raymondh on 2009-10-25
DOWNGRADE instructions

On ubiquity (the installer ....) in step 4

- choose manual
- highlight the intended partition (where karmic is).  make sure it is not VISTA
- Click EDIT > USE AS > select mountpoint (/) > format (ext 3 or ext4)
- proceed with the install

The above was assuming that you DO NOT HAVE a separate /home.  Root (/) will install of which /home will be a part of root.  

IF YOU HAVE A SEPARATE /HOME......

To keep /home intact:

- do the above selecting the appropriate root partition
- highlight the /home > edit > USE AS > mountpoint (/home) > **DO NOT FORMAT**

GRUB ought to install itself over GRUB 2.  If not, you can reinstall that later on using the liveCD.  Here's a how to:

[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)



To have a new /home ....  format.

As always, back-up your files.  Post back if you need clarifications before proceeding.

---

### Post by clear_runway on 2009-10-25
a little late.

---

