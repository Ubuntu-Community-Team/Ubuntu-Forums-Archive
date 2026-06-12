---
title: "Has anyone got mediagate35 NDAS installed and working?"
date: 2007-03-15
forum: Hardware &amp; Laptops
---

### Post by keithkiss on 2007-03-15
I have a mediagate 35 NDAS.
Is there anyway to access the data via LAN?

I got it working in Windows no problem and the USB works great in any OS  ;)

Thanks for any tips.

Keith
;)

---

### Post by zeifertstc on 2007-03-27
*bump*
Anybody got any ideas on a possible NDAS SCSI controller driver for Linux/Ubuntu?

EDIT: Following beta driver progress... will update thread as soon as something turns up working.

---

### Post by zeifertstc on 2007-04-02
I think it is about time for a little collaboration on this NDAS project. I have a NetDisk that uses NDAS, perhaps the information contained on this site I found will be of use to you. If you manage to get it working between all systems simultaneously (or even Linux individually) please be sure to let me know by posting the steps you may have followed outside of this if any.

```
http://code.ximeta.com/trac-ndas/wiki/Ubuntu6.10
```

You will find the NDAS driver on this page, please note that in order to get the ndasadmin driver you'll likely only find it under the full list (3rd link under drivers) you will need this in order to get the following instructions to work which can be found at:

```
http://code.ximeta.com/trac-ndas/wiki/Usage
```

For my setup, it seems as if this will work but it looks like it requires exclusive access to the drive instead of working like it does on windows. For windows systems, two or more computers can access the drive at the same time. I have a write key for my NDAS device but don't see a place in the instructions to go ahead and plug it in.

Since I have classwork I need to get on to, I will leave this here for you and hope you have some success with it. Please post back here either way and we'll go from there.

---

### Post by daldinit on 2007-04-10
Hello,

I could not figure out if you got this disk working or not but either way, read this:

I got my trekstor (which is also a NetDisk under a different name) to work with Ubuntu...somewhat...here is what i did:

- i got the 2.6.15-26-686 kernel (it doesn't work on a 386 kernel) through synaptic.
  I don't know how to compile my own drivermodule...so i took the easy way.

Next, i read this:
[http://forums.gentoo.org/viewtopic-t-413143-start-0-postdays-0-postorder-asc-highlight-ximeta.html?sid=753b2acbd41537103d958157365afd19](http://forums.gentoo.org/viewtopic-t-413143-start-0-postdays-0-postorder-asc-highlight-ximeta.html?sid=753b2acbd41537103d958157365afd19)

Eventually, I'll i did was getting the ndas admin and ndas kernel deb packages and installed them using the package installer. From then on i used ndasadmin to register and enable the disk. (see gentoo forumlink)

I could mount my ntfs disk, but i had no access to it. Then i just put all the data on a fat32 partition on the disk...and voila. I have only tested read only access up till know, but it seems the linuxdrivers don't require the write key...(i think)

I think it's not possible to have simulaneous write access using the linux driver with a ext3 formatted disk...i think i have read somewhere it works with a netdisk formatted with the GFS filesystem.

---

