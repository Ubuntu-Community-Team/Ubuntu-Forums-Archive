---
title: "External USB Drives - Any Gotchas? (before I buy one)"
date: 2008-11-05
forum: Hardware
---

### Post by sadams on 2008-11-05
[FONT="Arial"]Hi,
I am looking to buy a large capacity (say 500GB) external USB drive to use for some extra storage and backups.

I anticipate that I can buy (pretty much) any decent brand/manufacturer and plug it in, partition/format/mkfs the drive as I like (in Ubuntu 8.04 or 8.10) and use it.

I assume I can ignore the "certified with Win XP, Vista and OSX" type messages safe in the knowledge that I can just "plug it in" and use it in ubuntu.

So... 
 - any concerns about my assumptions... any "gotchas" before I go and shop for a bargain?
 - Anyone like to recommend anything specific based upon your experiences? 

Notes:
  - I'm not overly concerned about speed/performance.. this will be for archives and backups... not hot I/O bound applications :-)
  - Form Factor not too important to me... cute/small/quiet is nice.. but cute/cool won't trump nos of GBs/£££

Thanks in anticipation of your help,

Regards, Steve.
  -[/FONT]

---

### Post by Coreigh on 2008-11-05
Stay away from the ones that use a special client program to access it. You want to have free and clear access and a non-proprietary file system. You don't want to be stuck relying on a system that you can not bypass.

---

### Post by btiefert on 2008-11-05
I can also confirm that you have very little to worry about. 

 I'm not sure of the actual standard being followed, but USB hd's seem to work fairly universally with Ubuntu, automount and all.   I say this as someone who, in the past week, has connected five different USB hard drives to my Ubuntu 8.04 and 8.10 systems and consolidated their data to my new RAID array.  The devices I used spanned a few generations in hard drive technology and all connected without a problem.

The only thing that might cause a problem are NAS devices that masquerade as external hard disks.   Some of those list features such as one-touch backups that are often only made possible by Windows-only client software.   So you probably won't get all the "features" you'll see on removable hard drives - especially the ones with security features lists that encrypt contents or have biometric (thumb print) authentication.   But you're safe with pretty much any plain-jane external USB HD.

Any NAS device that actually advertises itself as a NAS device will also probably work just fine, but might take a little tinkering with smbclient in the off chance that they don't serve up NFS.  The real irony is that almost all such NAS devices are based on GNU/Linux, but there are a few that only serve SMB shares.

---

### Post by fireoptic on 2008-11-05
If you plan on booting from the drive you will have to modify your /boot/grub/menu.lst and /etc/fstab to make sure they are pointing at the right drive on your computer. Not difficult but can be a headache if you dont know.

Also make those mods after install but befor you remove the live cd

---

### Post by sadams on 2008-11-06
Hi People,
Thanks for your responses and reassurance.

btiefert Re NAS: Yes - agreed and understood. 
I was looking into such a thing - I liked the Infrant ReadyNAS stuff (now owned by Netgear) - impressive tech at a decent price - linux based and friendly... but I can't really justify the cost (UK£ 600 for the right config) right now compared to a chunk of half a TB! (< UK£100).

fireoptic Re booting: Understood - no need for this - as stated I'm just looking for a place to park some archives and backups really - I run an Ubuntu based MythTV setup and have taken to exporting stuff to xvid/avi for "archival purposes".. but after a while those GBs get eaten up!
plus always good to backup home dirs/file/photos etc to multiple places.

Coreigh Re: "special client program to access" - are you saying that (apart from NAS devices - I am talking about straight USB external single drives) such software/methods are *required* to access the drive? 
I had assumed i could ignore all that "Insert your windows CD now" stuff.. plug in the drive and get stuck in under Linux.
Care to clarify?

Thanks again, Steve.

---

