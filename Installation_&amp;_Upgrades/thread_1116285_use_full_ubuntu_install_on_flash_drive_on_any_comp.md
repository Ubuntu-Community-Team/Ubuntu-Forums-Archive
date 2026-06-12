---
title: "use full ubuntu install on flash drive on any computer"
date: 2009-04-04
forum: Installation &amp; Upgrades
---

### Post by tamas305 on 2009-04-04
I have a USB drive w/this configuration...(these are approx)

- 2gb fat32 portion (for windows stuff)
- 5gb ext3 portion (for ubuntu install, programs, and files)
- .5gb swap portion

I was wondering if it is possible to and GRUB to the flash drive in a way that if you plug it in any computer that boots normally into windows or mac, it will temporarily boot into ubuntu, and once your done you shut down and everything goes back to normal.

Currently my flash drive only works on my home computer because I think that GRUB is split between my internal hd and my USB. Is it possible to install GRUB on my USB in working condition. I consider myself a noob w/ubuntu so please explain

Thank you very much,
tamas305

---

### Post by Herman on 2009-04-04
Yes, you just install Ubuntu to your flash memory stick in the same way as if you are installing in a hard disk. That's how I prefer to do it.

Take a look in post #3 in this thread, [How to install ubuntu on USB drive and carry entire computing system in pocket?]("http://ubuntuforums.org/showthread.php?t=789528")

---

### Post by utnubuuser on 2009-04-04
Hi -- From Intrepid Ibex onward there is a utility in System>>Create liveUSB

You should be able to follow the prompts to accomplish what you're after.

Not all computers are able to boot from USB, though most of the newer models have tha capability.  In some cases booting from USB has to be enabled in BIOS.
Also, you don't need to add grub, as the USB will function as a liveOS.  Some computers will bring up a boot-device selection list if you press F12 during startup.
There are other such boot-selection options as well,  just google the issue.

---

### Post by Herman on 2009-04-04
I agree with utnubuuser, that way it will make a USB Ubuntu that works like the Live CD but faster, and it will have the Ubuntu installer so you can use it for installing Ubuntu in more computers.

My way makes a USB Ubuntu that's the same as a hard disk installation.

---

### Post by tamas305 on 2009-04-14
Thanks Herman

if anyone wants to know the intricacies of installing read this forum
[URL="http://ubuntuforums.org/showthread.php?t=1116206&highlight=tamas305"]
@Ubuntu Forums[/URL]

It can be slow at some times but having a full ubuntu install with a fat32 partition for windows is a boon for a java programmer like me.

-tamas

---

