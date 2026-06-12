---
title: "grub help"
date: 2008-09-27
forum: General Help
---

### Post by tone33 on 2008-09-27
So I installed Kubuntu 8.04 on its own partition.  Then i installed another distro (Gentoo) on its own partition.  In Gentoo I installed grub and created a /boot/grub/grub.conf file and added the appropriate stuff.  So I can boot to my gentoo distro (and also to existing windows installations), but I now want to add my Kubuntu boot back in.  I'm not sure what to put on the kernel line for the entry for Kubuntu.  How do I find the kernel file name?  Do i need to mount that drive in Gentoo and get the name?  Or is there a standard name I can use?

```
default 0
timeout 30
#splashimage=(hd0,0)/boot/grub/splash.xpm.gz

title Kubuntu Linux 2.something
root (hd0,4)
kernel ?????

title Gentoo Linux 2.6.25 r7
root (hd0,6)
kernel /boot/kernel-2.6.25-gentoo-r7 root=/dev/sda7

title Gentoo Linux 2.6.25 r7 (rescue)
root (hd0,6)
kernel /boot/kernel-2.6.25-gentoo-r7 root=/dev/sda7 init=/bin/bb

#windows
title Windows Server 2008
rootnoverify (hd0,0)
makeactive
chainloader +1

# vim:ft=conf:


```

---

### Post by Locutus_of_Borg on 2008-09-27
yay gentoo

it would be easiest to mount the kubuntu partition and then list the files in the /boot directory

there might be a symlink of /boot/vmlinuz to the correct kernel, but there might not be so just mount it and check

---

### Post by tone33 on 2008-09-27
Bear with me here b/c i'm still fairly new to linux, to mount it from Gentoo -- I know this isn't a Gentoo forum, but both use fstab and mount so it should be the same AND this is all to get Kubuntu back up and running :) 

I add this line to my /etc/fstab

```
/dev/sda5               /kubuntu        ext3            noatime         0 0

```

and then i try to mount, but get this error.  do i have to use a pre-configured mount point?

```
desktop-gentoo tone # mount /dev/sda5
mount: mount point /kubuntu does not exist

```

---

### Post by tone33 on 2008-09-27
i figured it out by using media as a mount point, but i'm still curious as to where the mount points are configured...

Another question..  In the boot directory i see a menu.lst file, which has this:

```
title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=0ad16f25-189b-4c1d-8fcd-20ff41a66ca0 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=0ad16f25-189b-4c1d-8fcd-20ff41a66ca0 ro single
initrd		/boot/initrd.img-2.6.24-19-generic
```

can i copy/paste this into the other grub.conf file?  does ubuntu/kubuntu use a different version of grub or something?

---

### Post by louieb on 2008-09-27
Sounds like your getting it figured out. Yes you can copy those lines into your gentoo grub.conf file and they should work. You'll have to do the copy again next time there is a kernel update in Ubuntu.

To get around that look at grubs chainload and configfile option. Works great for dual booting multiple Linux distributions. 
[IDBS GRUB Page]("http://users.bigpond.net.au/hermanzone/p15.htm")  just search this page for configfile or chainloader.

Good luck

---

### Post by tone33 on 2008-09-27
i got back into Kubuntu!  Thanks for the link - i'll look into it...

So right now Gentoo has my grub configuration, and thus is my boot partition for all my OS's (and using chainloader method for windows installs).  Is this bad?  I would like to have a stand alone boot partition of, say, 500MB where grub lives...

---

### Post by zvacet on 2008-09-28
> So right now Gentoo has my grub configuration, and thus is my boot partition for all my OS's (and using chainloader method for windows installs). Is this bad?

I can be wrong but I don´t see anything bad about it.

---

### Post by louieb on 2008-09-28
> **tone33 said:**
> i... (and using chainloader method for windows installs).  Is this bad?

The only way GRUB can boot windows is to chainload it. and Any Linux distribution can be set up so it can be chainloaded too. 
> **tone33 said:**
> 
 I would like to have a stand alone boot partition of, say, 500MB where grub lives...

Don't confuse having a /boot partition shared by all distributions. (tried that - not a good - gets messy when one of the distros does a kernel update).

With a dedicated GRUB partition.  I use one, its only 16MB (only 2.5MB used).  [IDBS make a dedicated GRUB partition]("http://users.bigpond.net.au/hermanzone/p15.htm#How_to_make_a_separate_Grub_Partition_"). Works great.

---

### Post by tone33 on 2008-09-28
that's what i meant - dedicated Grub partition.  Because, like you said I will probably run into issues if i update or re-install Gentoo.  In that case I don't want to have to reconfigure Grub.  

Does it matter if the Grub parition is at the end of an extended parition i have created for all my Linux distros?  So I create an extended partition of about 150GB, then a 10GB logical partition for Kubuntu, 15GB for Gentoo, and so on.  I don't think it will matter for any reason other than organization of my partitions - or is there something i am unaware of?

---

### Post by Idontknow08 on 2008-09-28
Hello,

I am new to Ubuntu and this forum. I have a problem as well. when I start up my computer, it reads

[B]GRUB4DOS 0.4.3 2008-06-30, Memory: 640k/1013M CodeEnd: 0x21A3B
[ Minimal BASH-like line editing is supported. For the first word, TAB lists possible command completions. Anywhere else TAB lists the possible completions of a device/filename. ESC at any time exits. ]

grub> _[/B]
I think it started when I turned off the computer manually.
Thanks.

---

### Post by Idontknow08 on 2008-09-28
Can anyone help me please?
Thanks

---

### Post by louieb on 2008-09-28
> **tone33 said:**
> ... - dedicated Grub partition.  Because, like you said I will probably run into issues if i update or re-install Gentoo.  In that case I don't want to have to reconfigure Grub.  

Does it matter if the Grub partition is at the end of an extended partition ...

Should not matter. Grub will work just fine in a logical partition. 

> **Idontknow08 said:**
> Hello,

I am new to Ubuntu and this forum. I have a problem as well. when I start up my computer, it reads

[B]GRUB4DOS 0.4.3 2008-06-30, Memory: 640k/1013M CodeEnd: 0x21A3B
[ Minimal BASH-like line editing is supported. For the first word, TAB lists possible command completions. Anywhere else TAB lists the possible completions of a device/filename. ESC at any time exits. ]

grub> [/B]


Looks like you have WUBI install inside of windows. What you see is GRUB prompt.  Haven't used WUBI myself. A wubi install is quite a bit different from a dedicated partition install. Your best bet for getting help is to post a new thread in the  [WUBI section]("http://ubuntuforums.org/forumdisplay.php?f=234") of the forum.

---

