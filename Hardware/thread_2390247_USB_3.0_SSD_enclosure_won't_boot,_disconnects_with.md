---
title: "USB 3.0 SSD enclosure won't boot, disconnects within seconds, works on 2.0"
date: 2018-04-27
forum: Hardware
---

### Post by bravofox on 2018-04-27
Hello !

Here it is: I have a Win7 installed on my PC and I wanted to have Ubuntu on an external SSD in order to get a portable / backup Linux installation for use.

The BIOS is configured on LEGACY boot (it doesn't even boot on UEFI and sends me back to BIOS configuration).

My SSD is formatted in one big ext4 partition and obviously a swap.

In Ubuntu, whenever I plug the cable in the USB 3.0 port, Ubuntu detects my SSD and lets me open it, but within ten seconds it just switches it off as if I physically unplugged it. Likewise, it won't boot the computer from it, as the disk just goes off during the boot sequence.

If I plug it in the 2.0 port instead, I don't have any problem.

Can you figure this out?

---

### Post by TheFu on 2018-04-27
Not all USB ports support booting.
Not all BIOS support booting from any USB.

I have a similar issue with my laptop. USB2 or SDHC slot - both boot fine. They are connected to the USB2 bus.
USB3 - won't boot anything.

It could be that booting from the specific storage device doesn't work as well.  I have 20 flash memory USB sticks. Only 5 can be booted from the laptop. Most of those same sticks work fine for booting other machines.  Some USB controllers are just picky.

I wouldn't rule out any issue until checking the exact chips used inside the enclosure and inside the computer for USB boot ability.

---

### Post by bravofox on 2018-04-28
Actually, it's not a problem of booting in itself but rather of disconnecting within seconds. When I try and boot from the 3.0, the grub menu does show up and the boot sequence does start indeed, until the Ubuntu logo shows up and the white dots start becoming orange one after another.

But then it's like the system simply cuts off the drive, exactly as if I unplugged it physically from the port.

---

### Post by TheFu on 2018-04-28
Interesting. Anything in the boot logs immediately after the failure?

---

### Post by oldfred on 2018-04-28
What brand/model system?

Is that just when it is switching graphics mode?
If you have nVidia you may need nomodeset.
On one of my older systems, I found it still was booting, but it just had turned monitor off. 

       At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
How to add boot parameters,  grub menu after install (also grub when UEFI)
[https://wiki.ubuntu.com/Kernel/KernelBootParameters](https://wiki.ubuntu.com/Kernel/KernelBootParameters)
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

---

