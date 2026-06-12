---
title: "USB Grub as a chainloader."
date: 2009-03-13
forum: Installation &amp; Upgrades
---

### Post by EtanSivad on 2009-03-13
I have an idea I want to try, but I'm a bit lost on how to implement it.
I've installed Ubuntu to USB drive several times, and it works great.   Although, a bit on the slow side.  I picked up an 8gb Compact flash card with a PCMCIA adaptor.  My laptop will boot from the USB no trouble, but it doesn't have on option to boot from the cardslot.  

So, my thought is if I can put GRUB onto a USB drive, I can use that to boot then have grub load up the installation on the PCMCIA drive.

Any suggestions on how to put just Grub onto a USB drive?
I'm reading through the Super grub documentation.  It seems like it'll work, but it's pretty sparsely documentated at this point.

---

### Post by shark1997 on 2009-03-13
I installed an Ubuntu live cd to my flash drive, and installing grub is easy. 

Create a /boot/grub directory

In that directory copy the stage1, stage2 and fat_stage1_5 files

then got to the terminal 

```
grub
```
```
root (drive#,partition)
```
```
setup (drive#,partition)
```

And you are DONE!

---

### Post by shark1997 on 2009-03-13
One more thing-

When i said drive#, it means some hd(whatever number)

On my laptop i put in hd1

It might be different for you

Partition means the partition number; mine is 0

So in the terminal i put root (hd1,0)
and
setup (hd1,0)

---

### Post by EtanSivad on 2009-03-13
> **shark1997 said:**
> I installed an Ubuntu live cd to my flash drive, and installing grub is easy. 

Create a /boot/grub directory

In that directory copy the stage1, stage2 and fat_stage1_5 files

then got to the terminal 

```
grub
```
```
root (drive#,partition)
```
```
setup (drive#,partition)
```

And you are DONE!

Oh sweet, thanks that worked!  I've got grub on the drive now.  Hmmm, now for the next step of building a grub config for booting from the CF card.

---

### Post by shark1997 on 2009-03-13
[font="arial black"]hello?[/font]

---

### Post by EtanSivad on 2009-03-13
> **shark1997 said:**
> [font="arial black"]hello?[/font]

Hi :D

Hmmm, well this may take some reading on my part.  Grub is running, but it only sees the USB drive. Not the CF drive.  I'm assuming that I need to load up INITRD before I can start accessing the CF card.

---

