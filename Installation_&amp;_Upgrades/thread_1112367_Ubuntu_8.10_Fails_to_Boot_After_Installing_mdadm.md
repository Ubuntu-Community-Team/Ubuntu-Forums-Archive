---
title: "Ubuntu 8.10 Fails to Boot After Installing mdadm"
date: 2009-03-31
forum: Installation &amp; Upgrades
---

### Post by burningapathy on 2009-03-31
Greetings,
     I have a desktop/file server I'm trying to bring up and it currently has 1 IDE drive to hold the OS and 4 SATA drives which will be put in Raid 1 pairs to hold my data.  I am able to install Ubuntu Desktop 8.10 just fine but I then want to install mdadm to create the Raid 1 arrays, but installing mdadm does something to cause my system to fail to boot.  
     It loads grub fine and then gets to the Ubuntu splash screen before giving some errors about a degraded raid array and drops me to the BusyBox dialog screen.  I started it with the console output and everything was going fine until it got to the md portion of bootup where md was trying to bind the drives.  I believe it ultimately freezes when it tries to bind /dev/sde which is the IDE hard drive containing the OS (which it shouldn't be touching because I'm not doing anything raid-related to that device).
     I don't understand why simply installing mdadm breaks the boot process.  Is there something I can do so that mdadm doesn't try to automatically change my boot image or whatever it is doing.  Can someone point me in the right direction or tell me what to look into?  I've read some posts that say I need a new initrd image or something.  I don't have a deep knowledge of the boot up process, but if anyone can point me in the right direction, I'm willing to learn.  I'm just not sure if this is:

1) mdadm being too cavalier on install and trying to do more than it should
2) me not configuring mdadm properly after it is installed to ensure that I can boot properly
3) some kernel bug similar to this one because it is very similar behavior:
[https://bugs.launchpad.net/ubuntu/jaunty/+source/mdadm/+bug/334994](https://bugs.launchpad.net/ubuntu/jaunty/+source/mdadm/+bug/334994)
4) some other issue my noobishness will not allow me to see

I've tried googling but there are a million pages about how to set up a raid so that you can boot from it, but that's not what I'm trying to do.  I had almost the exact same set up on an old slackware box where I had an IDE drive for the OS and 2 mirrored IDE drives for data so I know it's possible.

Any help would be very much appreciated.  Because I don't know how to solve the problem, I perform a full re-install every time and I have reinstalled about 7 times now and it is getting old.

---

