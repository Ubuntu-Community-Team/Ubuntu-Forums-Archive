---
title: "No USB boot option in BIOS"
date: 2010-12-24
forum: Hardware
---

### Post by Advait on 2010-12-24
Hi All,

I have a client with a MSI L2300 netbook with no internal optical drive. In the BIOS it only offers boot from hard drive or network boot. No USB appears as a boot option. I'd like to get the laptop booting Ubuntu 10.10 from a USB stik. Any way to do this? I did some googling re this issue, but most of the solutions were WAY too technical involving lots of arcane command line stuff about which I know zero.

So; with this situation; is there a simple way to get Ubuntu booting from a USB stik? Remember I have never used the command line.

If not, is there some way to copy the Ubuntu OS (ISO file?) onto the hard drive and then set up some kind of opening menu so it can boot from the hard drive? My vague understanding is that GRUB is some kind of pre-boot start up menu system. Is WUBI somehow part of the solution?

OK, Thanks in advance!

Tom

---

### Post by C.S.Cameron on 2010-12-25
The USB might be listed under hard drives when plugged in.
If it is, set it as first hard drive.

Some machines will give a choice of what to boot if Esc or F10, or some other key is pressed when booting.

If the machine is currently running Windows, plop boot manager has an option to choose USB when booting.

Good luck

---

### Post by tgalati4 on 2010-12-25
Burn a copy of SuperGRUB or Ultimate Boot CD.  Boot with it and SuperGRUB allows you to pick USB drives.  It's a common work-around for machines that don't allow booting directly from USB.

---

### Post by efflandt on 2010-12-25
Apparently tgalati4 missed the part about "**no internal optical drive**".  There are floopy or CD boot images that can boot USB, but that will not do any good if you have neither.

A netbook must have some way to boot from something other than its internal drive (flash?) otherwise how would you reinstall Windows when it gets messed up.

But like C.S.Cameron says, often BIOS only shows boot from USB when a USB device is actually connected.  Or different computers I have, use either Esc or F12 from BIOS splash screen to select boot device for that boot.

The problem with trying to install from an internal drive is attempting to repartition a drive you are running from.

---

### Post by Fafler on 2010-12-25
There has to some way of making USB boot work, for the reason explained by others in the thread. I've seen some flash drives that just couldn't work as boot drives, maybe that's the issue here. Try another, or...

If you just wan't to try out Ubuntu, you can use Wubi and install it inside the Windows partition. Ubuntu will then just reside in a large single file and can easily be removed if you want to.

---

### Post by Advait on 2010-12-27
Hello Cameron,

Your first suggestion to insert the USB stick first and then boot worked like a charm! Thanks! I inserted the USB stick (with the Ubuntu 10.10 boot files on it) then I hit F11 on the laptop which brought up a menu allowing me to choose "Boot from USB". Yay! My client and I are both very happy.

I really like the great help offered on this forum. This forum is one of the reasons I'm excited about recommending Ubuntu to my friends and clients.

Cheers,

Tom

---

