---
title: "Dual boot with Gentoo et al"
date: 2009-07-24
forum: Installation &amp; Upgrades
---

### Post by VinzC on 2009-07-24
Hi.

I know similar questions have been asked all over the place but maybe not this one especially so here we go :) .

I have installed Gentoo on my laptop and I'd like to keep control over my boot partition, which is handled by syslinux -- yup, I like to do everything by hand ;) . Now I'd like to add Ubuntu to my hard disk.

I fear Ubuntu installer replaces my boot loader with Grub. Is there a simple way I can install Ubuntu, say 9.04 to start with something fresh, without touching the MBR and boot loader?

I'm also considering installing other distributions on the same hard drive (e.g. CentOS or Arch) so the same question will popup, I think.

Thanks for any hint/suggestion.

---

### Post by presence1960 on 2009-07-24
> **VinzC said:**
> Hi.

I know similar questions have been asked all over the place but maybe not this one especially so here we go :) .

I have installed Gentoo on my laptop and I'd like to keep control over my boot partition, which is handled by syslinux -- yup, I like to do everything by hand ;) . Now I'd like to add Ubuntu to my hard disk.

I fear Ubuntu installer replaces my boot loader with Grub. Is there a simple way I can install Ubuntu, say 9.04 to start with something fresh, without touching the MBR and boot loader?

I'm also considering installing other distributions on the same hard drive (e.g. CentOS or Arch) so the same question will popup, I think.

Thanks for any hint/suggestion.

When you get to the Ready to install window click the advanced button and select the partition Ubuntu is being installed onto (i.e. sda6). This will put Ubuntu's GRUB onto that partition only, it won't touch the MBR.

---

### Post by VinzC on 2009-07-25
> **presence1960 said:**
> When you get to the Ready to install window click the advanced button and select the partition Ubuntu is being installed onto (i.e. sda6). This will put Ubuntu's GRUB onto that partition only, it won't touch the MBR.

Thanks presence1960. You mean Grub will be installed anyway but it won't be setup to take control at boot, is that correct? Or does it mean Grub will be installed and setup as if the partition on which it is installed just needs the bootable flag to be effective?

---

### Post by presence1960 on 2009-07-25
> **VinzC said:**
> Thanks presence1960. You mean Grub will be installed anyway but it won't be setup to take control at boot, is that correct? Or does it mean Grub will be installed and setup as if the partition on which it is installed just needs the bootable flag to be effective?

GRUB will be installed to that partition but will not take control on boot. As far as the bootable flag goes Linux does not need one to boot.

I have Ubuntu jaunty, Mint 5, Sabayon 4.1 & Windows7 RC on my machine. I have Jaunty's GRUB on MBR of my boot disk. Mint 5 & Sabayon are installed as I suggested. Mint and Sabayon are chainloaded on Jaunty's menu.lst. Their GRUB does not take over until I choose their entries in Jaunty's menu.lst. Here is  My OS section of Jaunty's menu.lst :
```

## ## End Default Options ##

title		Ubuntu 9.04, kernel 2.6.28-13-generic
uuid		0054ec31-5f5f-4997-aef3-a68d64e3b7e7
kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=0054ec31-5f5f-4997-aef3-a68d64e3b7e7 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-13-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-13-generic (recovery mode)
uuid		0054ec31-5f5f-4997-aef3-a68d64e3b7e7
kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=0054ec31-5f5f-4997-aef3-a68d64e3b7e7 ro  single
initrd		/boot/initrd.img-2.6.28-13-generic

title		Ubuntu 9.04, kernel 2.6.28-11-generic
uuid		0054ec31-5f5f-4997-aef3-a68d64e3b7e7
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=0054ec31-5f5f-4997-aef3-a68d64e3b7e7 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		0054ec31-5f5f-4997-aef3-a68d64e3b7e7
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=0054ec31-5f5f-4997-aef3-a68d64e3b7e7 ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
uuid		0054ec31-5f5f-4997-aef3-a68d64e3b7e7
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root

title           Sabayon 4
rootnoverify    (hd1,1)
chainloader     +1

title           Linux Mint 5 64 bit 
rootnoverify    (hd0,6)
chainloader     +1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows 7 RC (loader)
rootnoverify	(hd0,1)
chainloader	+1
```

---

### Post by VinzC on 2009-07-25
Aaaah, chainloading, I thought of that. Thanks a lot for the info.

I think I won't use chainloading but copy back the respective distributions' kernel lines into syslinux configuration file. Nice tip; thanks again :) .

---

### Post by raymondh on 2009-07-25
Just to add an experience,

A couple of weeks ago, I re-did my test machines' configuration with Presence1960's assistance.  2 drives. Each drive with GRUB and chainloaded with each other.  Bios set to boot my preferred drive which dual-boots.

Works fine.

---

### Post by VinzC on 2009-07-25
Thanks for the hint but I'm too n00b in Debian/Ubuntu to dare have any doubt against presence1960's skills ;) .

---

### Post by markbuntu on 2009-07-25
> **VinzC said:**
> Aaaah, chainloading, I thought of that. Thanks a lot for the info.

I think I won't use chainloading but copy back the respective distributions' kernel lines into syslinux configuration file. Nice tip; thanks again :) .

You can do that, but you will need to do it every time you get a kernel update.

I use chainload for the 6 distros on the 4 drives my machine and have one grub on the MBR to rule them all. It makes it easy to replace a distro in a partition. no changes necessary to the master grub.

---

### Post by presence1960 on 2009-07-25
> **markbuntu said:**
> You can do that, but you will need to do it every time you get a kernel update.

I use chainload for the 6 distros on the 4 drives my machine and have one grub on the MBR to rule them all. It makes it easy to replace a distro in a partition. no changes necessary to the master grub.

+1

That is exactly why I chainload. I have Jaunty, Sabayon 4.1 & Mint 5. Chainloading makes life easier on kernel upgrades and really makes installing/reinstalling to those partitions a breeze.

---

### Post by VinzC on 2009-07-25
> **markbuntu said:**
> You can do that, but you will need to do it every time you get a kernel update.

I use chainload for the 6 distros on the 4 drives my machine and have one grub on the MBR to rule them all. It makes it easy to replace a distro in a partition. no changes necessary to the master grub.

> **presence1960 said:**
> +1

That is exactly why I chainload. I have Jaunty, Sabayon 4.1 & Mint 5. Chainloading makes life easier on kernel upgrades and really makes installing/reinstalling to those partitions a breeze.

I know. However I prefer not using chainloading. BTW I can also create a script to update syslinux configuration and avoid doing that by hand ;) .

Currently all distributions I tried work as if they were alone on a disk. Nothing (to my knowledge at least) allows for updating a boot loader that is common to several distributions. 

I think update managers should at least provide a hook system so that whenever a new kernel is installed, for instance, it would allow for updating a common boot loader for instance. I'm going to write a script with that idea in mind.

---

### Post by markbuntu on 2009-07-25
> **VinzC said:**
> I know. However I prefer not using chainloading. BTW I can also create a script to update syslinux configuration and avoid doing that by hand ;) .

Currently all distributions I tried work as if they were alone on a disk. Nothing (to my knowledge at least) allows for updating a boot loader that is common to several distributions. 

I think update managers should at least provide a hook system so that whenever a new kernel is installed, for instance, it would allow for updating a common boot loader for instance. I'm going to write a script with that idea in mind.

That does not sound like a bad idea but it seem the distros are going the other way. I tried to install fedora11 but it wanted to take over an entire drive and there was no way to tell it to not do that and I just was not that interested to install it manually. Studio64 installed its grub on my MBR without asking me, I fixed that, filed a bug report, and deleted it. The latest ubuntu9.04 crashed on install before installing grub because migration assistant could not parse all my distros to migrate all my firefox bookmarks. Apparently this has been a back and forth issue for a few years now.

These are the problems we face. The ability to control an installation is getting away from us because distro maintainers decided to automate the installation to the point where it will totally kludge your system if you are not in their very narrow target range.

I think the distros loose out on this. I would be reporting bugs and trying to help them fix things if these stupid decisions did not dissuade me about the quality of their management thinking.

---

### Post by presence1960 on 2009-07-25
> **VinzC said:**
> I know. However I prefer not using chainloading. BTW I can also create a script to update syslinux configuration and avoid doing that by hand ;) .

Currently all distributions I tried work as if they were alone on a disk. Nothing (to my knowledge at least) allows for updating a boot loader that is common to several distributions. 

I think update managers should at least provide a hook system so that whenever a new kernel is installed, for instance, it would allow for updating a common boot loader for instance. I'm going to write a script with that idea in mind.

That is the beauty of Linux: there is usually more than one way to accomplish what one needs to be done. Your way will work as well as the chainload method from a GRUB on MBR. So really it comes down to what suits your needs best. That is entirely your decision & choice. Most in here respect each others' opinions and the choices each of us make.

---

