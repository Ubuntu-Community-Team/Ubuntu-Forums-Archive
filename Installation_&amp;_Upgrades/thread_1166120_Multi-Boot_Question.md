---
title: "Multi-Boot Question"
date: 2009-05-21
forum: Installation &amp; Upgrades
---

### Post by invenit on 2009-05-21
I'm new to multi-booting, but I have no problems getting WinXP, Ubuntu 9.04 and CrunchBang to work OK on a 250 GB drive. Here's the problem: PCLinuxOS 2009. When I install just PCLinuxOS & WinXP then all is well. OTOH, if I try to keep Ubuntu or CrunchBang + WinXP + PCLinuxOS, then grub does not work for the Ubuntu distros. ](*,)

To get around this, maybe I should look at a payware solution like BootIT? Anybody comment on this, or maybe suggest a better alternative?

---

### Post by Mark Phelps on 2009-05-21
> **invenit said:**
> To get around this, maybe I should look at a payware solution like BootIT? Anybody comment on this, or maybe suggest a better alternative?

If GRUB isn't working now, I seriously doubt that a payware solution is going to fix that.

Need to post more details about GRUB not working, like, what are you seeing and what error messages are you getting?

---

### Post by Bucky Ball on 2009-05-21
You might like to try LILO:

[http://users.bigpond.net.au/hermanzone/p4.html](http://users.bigpond.net.au/hermanzone/p4.html)

That could be of some help. Might work.

---

### Post by ashmew2 on 2009-05-21
I think PCLinuxOS uses GRub (?) , you just need to install grub separately to each OS's root and then install Grub to MBR as a whole. After that just use chainloading.

Maybe taking a look here will help : [http://ubuntuforums.org/showthread.php?t=724817](http://ubuntuforums.org/showthread.php?t=724817)

---

### Post by Bucky Ball on 2009-05-21
It is not up to the OS. Grub bootloads Windows or Ubuntu or whatever, not the other way around. Some say LILO is more efficient. PCLinuxOS does not require a particular bootloader, it requires the right commands from *a* bootloader. :)

---

### Post by invenit on 2009-05-21
Thanks for the quick replies, folks.

I just reinstalled PCLinuxOS (in place of CrunchBang). Grub works fine for WinXP & PCLinuxOS, but I get this error message when I select Ubuntu: root (hd0,5) filesystem type is ext2fs, partition type 0x83 chainloader +1 Error 13: invalid or unsupported format.

I use ext4 for Ubuntu. No matter, however, since grub didn't work for Ubuntu when I used a different format.

I'm exploring some of your suggestions now. Let me know if you need more information.

P.S. On one of my previous installs, I did try Lilo (it's an option with PCLinuxOS), but it also did not allow me to start Ubuntu.

---

### Post by Bucky Ball on 2009-05-21
> **invenit said:**
> root (hd0,5) filesystem type is ext2fs, partition type 0x83 chainloader +1 Error 13: invalid or unsupported format.



Run:

```
sudo blkid
```

in a terminal and post. I think your Grub is just finding the wrong drive perhaps ... that can be fixed.

---

### Post by invenit on 2009-05-21
Thanks! Here's the output:

/dev/hda1: UUID="FE7886ED7886A3CD" TYPE="ntfs"
/dev/hda5: UUID="9a48f4f7-0fe9-41d8-a621-a066cbdc70e0" TYPE="ext3" SEC_TYPE="ext2"
/dev/hda6: UUID="f8d3de95-7815-4435-87de-ddf338debca5" TYPE="ext4"
/dev/hda7: TYPE="swap" UUID="0af97ed5-d1a3-4bed-9f63-2abdc47c4ec0"

---

### Post by ashmew2 on 2009-05-21
> **Bucky Ball said:**
> It is not up to the OS. Grub bootloads Windows or Ubuntu or whatever, not the other way around. Some say LILO is more efficient. PCLinuxOS does not require a particular bootloader, it requires the right commands from *a* bootloader. :)

Sorry for not phrasing myself clearly there but I meant that "Does it install Grub when it installs itself to the hard disk or does it install LILo or some other boot loader ? Like Ubuntu/Fedora install Grub to the MBR or the partition you specify." 
:D

---

