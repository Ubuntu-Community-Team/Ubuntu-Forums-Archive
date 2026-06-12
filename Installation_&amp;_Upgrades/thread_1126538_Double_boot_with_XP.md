---
title: "Double boot with XP"
date: 2009-04-15
forum: Installation &amp; Upgrades
---

### Post by cedric_libre on 2009-04-15
Hi,
I've a pc were I currently use Ubuntu 7.10 and also another hard drive with only XP .
I prefer to use ubuntu but for several programs that don't exist on linux I switch to XP .

As I don't trust windows and am a bit scared to have my datas f**ked up by a virus, XP is on a different hard drive
When I use XP, I plugg off the two hard drives I use for linux and plug in the one that holds XP .

I am bit fed up with this, thus I'd like to install Kubuntu 8.04 in double-boot .

The whole XP hard-drive is formatted.
How can I do to install without risk Kubuntu in double-boot ?

Thanks for your help,

 Cédric
I mean

---

### Post by ronparent on 2009-04-15
If ubuntu is formated in ext2 or ext3, the xp would never see it in a dual boot setup. Although you provide little information, the ubuntu disk would be the boot disk if attached to an ide port through the 'master' position on the cable. The windows disk would then be on the secondary location. Grub could be setup to find both operating systems.

Or, you could simply switch them in bios on boot. In any event there is no need to physically disconnect the one you do nor wish to boot to.

---

### Post by tamas305 on 2009-04-15
> **ronparent said:**
> If ubuntu is formated in ext2 or ext3, the xp would never see it in a dual boot setup. Although you provide little information, the ubuntu disk would be the boot disk if attached to an ide port through the 'master' position on the cable. The windows disk would then be on the secondary location. Grub could be setup to find both operating systems.

Or, you could simply switch them in bios on boot. In any event there is no need to physically disconnect the one you do nor wish to boot to.

True. Windows does not recognise the ext3 partition that Ubuntu uses, so I doubt any virus that affects windows will also effect your Linux boot. However this may happen, so the dual hard drive set up is warranted, however, the need to physically disconnect one hard drive each time is a little bit overkill. If I remember correctly hard drives cannot communicate to each other especially if they are formatted differently.

-tamas

---

