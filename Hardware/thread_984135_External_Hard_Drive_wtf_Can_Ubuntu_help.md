---
title: "External Hard Drive wtf: Can Ubuntu help?"
date: 2008-11-16
forum: Hardware
---

### Post by KeithA45 on 2008-11-16
I've posted this in the "Apple Users" forum as well, as I'm not sure which forum would be most appropriate for this question.

Almost a year ago I got [this external hard drive]("http://www.lacie.com/us/products/product.htm?pid=11023") (although an earlier model) for my Macbook Pro to use Time Machine with, and about a month ago it went on the fritz for no obvious reason. At best I can get my computer to recognize the hardware (but not the drive) anymore. Even DiskWarrior doesn't help. Of course I'd like the data on the drive preserved, but at this point I'd be happy to be able to start over and use it at all!

My question is this: I have Ubuntu dual-booted on my old Compaq also, although I have no idea how to use it. Is there anything Ubuntu can do to let me use the drive again?

---

### Post by srt4play on 2008-11-16
Plug the external drive into your Ubuntu system.  If Ubuntu recognizes the drive it will place an icon for it on the desktop and open a file manager displaying its contents.  If nothing happens, open Applications -> Accessories -> Terminal and enter the command "dmesg" to look for clues about what's wrong.

---

### Post by KeithA45 on 2008-11-16
Wow sure enough it loads! Most of the files are gone, but that's ok, I'm just happy it works at all.

Ok what can I do to wipe this thing clean so my Macbook Pro will at least recognize the drive so I can format it and what-not?

---

### Post by KeithA45 on 2008-11-16
Great, now since I told it to unmount, I can't get it to mount again (although shows up in Computer as "FireWire Drive").

EDIT: Scratch that, I got it to mount again.

Is there a "kill" command to wipe out the formatting on the drive or something so I can start over?

Thanks in advance,
 - Keith

---

### Post by srt4play on 2008-11-16
Assuming you have internet access on the Ubuntu system, install the program gparted using synaptic.  System -> Administration -> Synaptic package manager.  Search for gparted and install it.  Once installed it will be in System -> Administration.  Use it to reformat the drive, and be careful of which drive you are working on (drive selection drop-down menu in top right).  Also be careful of what filesystem you format it as, I am not familiar with OSX or time machine compatability issues.

---

### Post by KeithA45 on 2008-11-16
> **srt4play said:**
> Assuming you have internet access on the Ubuntu system, install the program gparted using synaptic.  System -> Administration -> Synaptic package manager.  Search for gparted and install it.  Once installed it will be in System -> Administration.  Use it to reformat the drive, and be careful of which drive you are working on (drive selection drop-down menu in top right).  Also be careful of what filesystem you format it as, I am not familiar with OSX or time machine compatability issues.

Unfortunately I tried that, GParted doesn't recognize the drive. Anything else that can do that?

---

### Post by srt4play on 2008-11-17
If the drive is mounting then gparted should see it. In the terminal you can use the mkfs command. For HFS support you need to install the package hfsprogs.

---

### Post by KeithA45 on 2008-11-23
> **srt4play said:**
> If the drive is mounting then gparted should see it. In the terminal you can use the mkfs command. For HFS support you need to install the package hfsprogs.

You'll have to forgive my amateurishness, Linux is new to me

I installed hfsprogs, but to no avail. The hard drive is still not showing up in GParted, although with every device refresh I can tell it's getting checked.

Is there a command to tell what hardware is connected (and it's location), and then a command to format one of them?

thanks,
 - Keith

---

