---
title: "Ubuntu is crashing on me"
date: 2005-04-20
forum: Hardware &amp; Laptops
---

### Post by ppyvras on 2005-04-20
Although new to linux I have managed to install it fine on two pcs but my own one is giving me a serious headache.  Ubuntu installs ok and seems to work as it should until a seemingly random crash (the mouse still moves).  The only things I can link to are when it is particularly busy.  I have reinstalled a couple of times with the same problem occuring.  I even tried Mandrake 10.1 and that stalled during the installation.  On my last attempt I installed linux with something close to 'boot: linux sp8cxx=safe' and so far no crash but I am not holding out too much hope.

I have a Maxtor Diamond Plus 9 SATA 160Gb hard drive, with a windows partition (which works absolutely fine, sorry to say) on the first 60Gb and Ubuntu on the rest.  These partitions are detected as sda and sdb.

My motherboard is an ASUS A7V600 with the via KT600 chipset.

Also DMA is not enabled by default on my DVD drives

My questions are:
Should the partitions be detected as sda instead of hda?  I thought sda was for SCSI devices?

Is there a kernel module that will sure up my system?

Can anyone recommend any hardware testers just in case there is a fault? - I would be suprised because windows has never had problems.

If the mouse moves then I guess the system can be recovered without a reboot.  Is there a way to kill everything and get back to the ubuntu splash screen?

I welcome any (expert) advice.

Cheers
Rob

---

### Post by accuser on 2005-04-20
> Should the partitions be detected as sda instead of hda? I thought sda was for SCSI devices?
As far as I am aware - and someone tell me if I am wrong - but hd* is for IDE (or PATA) hard disks and sd* is for SATA and SCSI.
> Is there a kernel module that will sure up my system?
Doubt it - if it isn't already loaded, you're not currently needing it. :-)
> If the mouse moves then I guess the system can be recovered without a reboot. Is there a way to kill everything and get back to the ubuntu splash screen?
Have you tried CTRL+ALT+BACKSPACE to kill the X Server and go back to GDM?

---

### Post by ppyvras on 2005-04-27
cheers for those answers, helped a lot  O:)

---

