---
title: "Configuring GRUB to load Windows XP on non primary SATA drive"
date: 2005-04-13
forum: Hardware &amp; Laptops
---

### Post by Jump on 2005-04-13
Ok I have two hard drives, both SATA. One has a working Windows XP install. The other has a working Ubuntu Hoary 5.04 install.

I have no problems booting under either OS by swapping the SATA cables on the motherboard. However, I'd like to be able to choose the right OS as the computer starts without having to open the computer and swap the cables.

I assume this can be done via GRUB. Since I currently have the Ubuntu drive in the primary slot, I can ESC and access the GRUB boot menu. I know I need to edit something in /boot/grub/menu.lst to make this work but I haven't had any luck so far.

There are the settings I've tried so far:

```
title Windows XP
map (hd0) (hd1)
map (hd1) (hd0)
chainloader (hd0)+1
```

The above setting causes it to spam me with GNU GRUB loading 1.5 messages. It just keeps cycling through the same thing and fills up the screen. Nothing loads. I also tried this:

```
title Windows XP
map (hd0) (hd1)
map (hd1) (hd0)
rootnoverify (hd0,3)
makeactive
chainloader (hd0)+1
```

This one causes it to say Error 12: Invalid device detected. I also tried this:

```
title Windows XP
rootnoverify (hd1,0)
makeactive
chainloader (hd1)+1
```

This one says Error loading operating system. 

Is there any way for me to get this working?

---

### Post by Cmdr_K00n on 2005-04-13
My Setup
/dev/hda - Primary IDE bootable, WinXPPro, 

/dev/sda - Primary SATA, Ubuntu

In BIOS I have the ide dive to boot before the sata one

When the ubuntu setup is finishing it tells you that it has found another OS, 
and asks if you would like to install the bootlaoder to the MBR of the first hard drive.

Say yes.

My grub menu is now gives the option of Ubuntu, or XP

---

