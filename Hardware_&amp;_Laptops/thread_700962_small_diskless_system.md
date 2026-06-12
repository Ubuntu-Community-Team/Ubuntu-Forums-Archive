---
title: "small diskless system"
date: 2008-02-18
forum: Hardware &amp; Laptops
---

### Post by yeti.man on 2008-02-18
I am looking to possibly build a small lightweight system for a simple ssh server for the house.  I would like it to not use a disk, but instead possibly a compact flash card to act as the disk.  does anyone know where I could find any hardware and info on this.  

I would be using the ssh server as a tunneling server for security when at open wifi hotspots, etc.

---

### Post by kerry_s on 2008-02-18
have you looked at the dsl store, they specialize in small. :)
[http://damnsmalllinux.org/store/](http://damnsmalllinux.org/store/)

i been thinking about getting 1 of these to play with-> [http://damnsmalllinux.org/store/Mini_ITX_Systems/Mini_ITX_BareBones_Computer](http://damnsmalllinux.org/store/Mini_ITX_Systems/Mini_ITX_BareBones_Computer)

and just using a flash drive with a custom install, i just bought a 1gb flash drive for $9.99, when i get some more cash, i'm going to see if they still have the flash on sale, it would be great just swapping different linux installs just by swapping the flash.

---

### Post by Gen2ly on 2008-02-18
You could possibly put a very small Linux distro or Linux Distro ISO on a flash card.  Damn SmallLinux comes to thought.  Don't flash card only have about 50MB of memory?  Gentoo's LiveUSB tutorial might be able to assist in putting an ISO on the media.

---

### Post by yeti.man on 2008-02-19
I think I may have found my solution, and didn't even know it!  A week ago, I ordered a Linksys NSLU2 device to add some storage to my network.  When I received it, I searched and found it was easily hackable with OpenWRT.  With OpenWRT, I can both add storage devices and install OpenSSH!  This was exactly the solution I was looking for, and it cost less than $100, is silent, and serves exactly the purpose I want.  

I looked at the DSL pcs on their website and found them to be a little too expensive for what I wanted.  (Although, I will probably end up getting one in the long run.  They were just TOO COOL!)

I haven't done the flash on the NSLU2 yet, so I hope it works...

---

### Post by yeti.man on 2008-02-19
Forgot to add, I have also been using a minimal install of debian in a VMWare Server install.  (350 meg disk space, 120 meg resident memory) Installed OpenSSH, hardened the SSH install, changed the port number, and opened the port through my NAT router.  All is good until I get the NSLU2 up and running

---

### Post by kerry_s on 2008-02-20
> **yeti.man said:**
> I think I may have found my solution, and didn't even know it!  A week ago, I ordered a Linksys NSLU2 device to add some storage to my network.  When I received it, I searched and found it was easily hackable with OpenWRT.  With OpenWRT, I can both add storage devices and install OpenSSH!  This was exactly the solution I was looking for, and it cost less than $100, is silent, and serves exactly the purpose I want.  

I looked at the DSL pcs on their website and found them to be a little too expensive for what I wanted.  (Although, I will probably end up getting one in the long run.  They were just TOO COOL!)

I haven't done the flash on the NSLU2 yet, so I hope it works...


make sure you read the instructions very good and triple check everything, i had a friend brick his NSLU2 trying to get debian on there. luckly it was still under warrenty, so he just returned it for a new 1 and told them he didn't know what happened, he told them he thinks it got hacked. witch is kinda true, only he was the hacker.
:lolflag:

---

### Post by Gen2ly on 2008-02-23
I also saw this too:

[http://forums.gentoo.org/viewtopic-t-327295.html](http://forums.gentoo.org/viewtopic-t-327295.html)

---

### Post by yeti.man on 2008-02-24
Just an update here.  I received the NSLU2, flashed it with the Unslung release and all is working EXACTLY like promised (and how I wanted)!

This is an AMAZING little piece of hardware.  SSH tunneling works perfectly with the device.  I am truly surprised at how many packages and programs are offered for this thing. 

Grab one quick!  It is well worth it.

---

