---
title: "Help with network install!"
date: 2009-11-03
forum: Installation &amp; Upgrades
---

### Post by DejitaruJin on 2009-11-03
Jeez, I'm about to rip my hair out over this.

Okay, I need to do a network install. The "client" has no CD drive, but it has a floppy drive. The "server" (Ubuntu 9.10) has TFTP installed, and the installation files are placed appropriately in the tftpboot directory.

Problem is, DHCP is out of the question. Just, completely. So, PXE is as well, because... well, because it was designed by idiots, I guess.

So, what I need, is a boot floppy. Not one that just initializes PXE, since that won't work; something much better. Instead of having the boot file sent to the client, I need the client to *retrieve* the file from the *server*. I don't care how - I'll make the tftpboot folder a network share if I have to. It's really very, very simple, and that's really all I need. Now, does anyone have access to such advanced technology?

---

### Post by tomBorgia on 2009-11-03
Rage less...

[Etherboot]("http://etherboot.org/wiki/howtos")

---

### Post by DejitaruJin on 2009-11-03
I've tried that, but it seems that, by default, it just does the PXE thing. I can get it to its little command prompt, but I'm not sure what to do from there. How do I tell it that there's a perfectly good boot file at a specific IP on the network?

---

### Post by dstew on 2009-11-03
The grub 2 boot loader can be compiled with network capability, and then set up on a floppy drive as a TFTP client. See [this page]("http://grub.enbug.org/NetworkBoot") in the Wiki. There are not a lot of details here, but it says that the DHCP server to configure the client network is "optional". Presumably that means that grub 2, if compiled to allow network boot, should have commands that allow a fixed IP address to be used.

Once network-capable grub 2 has been booted, the commands to boot the OS start with```
root (nd)
```That is, nd = "network drive". Sounds like something that is worth looking into, if you absolutely cannot use PXE/DHCP.

---

### Post by DejitaruJin on 2009-11-03
Interesting, very interesting indeed. That just might work, with some toying around.

There *is* a DHCP server on the network, but it can not be configured for PXE. I assume the "Server" field is what I would have to manually set to be the address of the TFTP server. From there, everything should work as expected.

I just need to get GRUB 2 onto a bootable floppy...

Edit: Never mind, got a GRUB boot disk. Only problem is, it doesn't work the same. The commands bootp, dhcp, and rarp are all invalid, and (nd) isn't a valid disk.

---

### Post by dstew on 2009-11-04
Is your boot floppy grub legacy 0.97, or grub 2? It probably doesn't matter. I looked at the grub legacy manual, and it has the same section about booting a network image. [See here.]("http://www.gnu.org/software/grub/manual/grub.html#Diskless") You need the special [network stage 2]("http://www.gnu.org/software/grub/manual/grub.html#Images") though. I think you go through the process of making a grub boot floppy, but instead of the usual stage2 file, you install the **nbgrub** or **pxegrub** image.

It seems that the boot server does not have to be the same as the DHCP server, so maybe you can just use DHCP to get your client's IP address, and then try to get the kernel image from your boot server using TFTP. The bootp configuration is the same as mentioned in the grub 2 manual.

---

