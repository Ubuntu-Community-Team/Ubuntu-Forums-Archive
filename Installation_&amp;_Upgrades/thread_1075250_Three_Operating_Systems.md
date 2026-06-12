---
title: "Three Operating Systems"
date: 2009-02-20
forum: Installation &amp; Upgrades
---

### Post by daniel014 on 2009-02-20
Hi. I have Windows XP and Ubuntu on my laptop (120GB).

How do I set up a tri-boot to add Archlinux to the HDD and boot menu.

I would go into GPartEd on the Live CD and make a new partition for Archlinux, but I would like Ubuntu to take control of GRUB.

Thanks for your help.

---

### Post by caljohnsmith on 2009-02-20
I've never installed Arch Linux, but I would assume there is some way you can specify where Grub gets installed to when you install Arch. If that is true, just specify to have Grub installed to the boot sector of the partition you are installing Arch to, which is usually done by telling the installer to install Grub to the same partition as the distro you are installing. Then you can boot Arch from Ubuntu's Grub menu by adding an entry in the menu.lst like:
```
title Arch Linux
root (hdX,Y)
chainloader +1
```
And of course replace (hdX,Y) with the Arch partition. Good luck and let me know how it goes.

---

### Post by lha on 2009-02-21
Herman has made a nice page on Grub settings: [http://users.bigpond.net.au/hermanzone/p15.htm#Operating_System_Entries_for_Multiple_Booting_More_Linux_Systems]("http://users.bigpond.net.au/hermanzone/p15.htm#Operating_System_Entries_for_Multiple_Booting_More_Linux_Systems"). It's a good read, shows you three ways to get what you want. Just make sure you don't overwrite Ubuntu's Grub with Arch's.

---

### Post by philuwa on 2009-02-21
Good Day House! I'm new to Ubuntu, Can anyone send me materials aside the official Ubuntu Guide, I want to become a ubuntu professional. Thanks!

---

### Post by daniel014 on 2009-02-22
caljohnsmith, in your post you said

```
title Arch Linux
root (hdX,Y)
chainloader +1
```

but according to this page [http://users.bigpond.net.au/hermanzone/p15.htm#Operating_System_Entries_for_Multiple_Booting_More_Linux_Systems]("http://users.bigpond.net.au/hermanzone/p15.htm#Operating_System_Entries_for_Multiple_Booting_More_Linux_Systems")
the 'chainloader' is only for proprietry operating systems like Windows.

---

### Post by caljohnsmith on 2009-02-22
> **daniel014 said:**
> caljohnsmith, in your post you said

```
title Arch Linux
root (hdX,Y)
chainloader +1
```

but according to this page [http://users.bigpond.net.au/hermanzone/p15.htm#Operating_System_Entries_for_Multiple_Booting_More_Linux_Systems]("http://users.bigpond.net.au/hermanzone/p15.htm#Operating_System_Entries_for_Multiple_Booting_More_Linux_Systems")
the 'chainloader' is only for proprietry operating systems like Windows.
I think you might have misread that page, because you can use "chainloader" to boot a Linux OS if you first install the Linux's OS boot loader (Grub/Lilo) to its partition boot sector. From that web page regarding using "chainloader" for a Linux partition:
> In order for this to work, the IPL or stage1 file for a boot loader needs to be installed in the boot sector of the other operating system's partition. Normally, Linux Operating Systems don't have anything installed it their boot sectors unless we install it there ourselves. If the other Linux distro uses GRUB, you can install GRUB to it's partition boot sector at installation time, or after installation with some GRUB commands or with Super Grub Disc, Re-install GRUB with a GRUB shell.
And then Herman gives an example of chainloading a Linux distro with:
> Here's an example of a typical chainloader booting command,
```
title        Ubuntu Edgy Eft
root        (hd0,5)
chainloader    +1
```
Where: Edgy Eft is a Linux operating system on partition number 6, and it has GRUB or LiLo or some other boot loader installed in the first sector of the partition.
So yes, it is possible to use "chainloader" with a linux distro, you just have to install Grub/Lilo to the partition boot sector first like I mentioned in my previous post. :)

---

