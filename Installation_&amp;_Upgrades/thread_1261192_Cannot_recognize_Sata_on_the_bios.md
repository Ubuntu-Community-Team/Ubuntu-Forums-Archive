---
title: "Cannot recognize Sata on the bios"
date: 2009-09-08
forum: Installation &amp; Upgrades
---

### Post by lhide on 2009-09-08
I'm looking for drivers for a Hitachi Deskstar 7K160 SATA hard drive. 
The MB is Asus A7V600, chipset is AMD Semprom 2400+.
Any help would be greatly appreciated.

---

### Post by stlsaint on 2009-09-08
quick question...how is your mobo setup to read hdd...is it set to read sata first or second or do you only have one hdd?

---

### Post by lhide on 2009-09-08
> **stlsaint said:**
> quick question...how is your mobo setup to read hdd...is it set to read sata first or second or do you only have one hdd?

Sata first... i have 2 hdds but the bios only recognize one wich is the samsung (sata)


-edit-
i could post screen shots of the bios if you find necessary


thanks for the fast reply

-edit²-
anyone?

---

### Post by lhide on 2009-09-08
Someone please help me!

---

### Post by cak3 on 2009-09-08
The BIOS doesn't really use drivers. You could see if there are any BIOS updates available from ASUS and/or try clearing the CMOS. 

It could also be the drive, do you have anywhere else you can test it?

what SATA mode is your bios using? i.e. IDE, AHCI, RAID, etc...

---

### Post by StuartN on 2009-09-08
Probably stating the obvious, but your problem is not that you need a driver to read the SATA drive (because the driver would be on the unreadable disc...).

What happens at bootup time?

---

### Post by lhide on 2009-09-08
> **cak3 said:**
> The BIOS doesn't really use drivers. You could see if there are any BIOS updates available from ASUS and/or try clearing the CMOS. 

It could also be the drive, do you have anywhere else you can test it?

what SATA mode is your bios using? i.e. IDE, AHCI, RAID, etc...

i tested it in another computer and everything went fine... the hd has been recognized by the bios. and i installed ubuntu 9.04 in it!
it is in raid mode
> **StuartN said:**
> Probably stating the obvious, but your problem is not that you need a driver to read the SATA drive (because the driver would be on the unreadable disc...).

What happens at bootup time?

if there is only the Deskstar 7K160 on the mobo bios doesnt recognize it and then it states something is missing tdsl or something, i could post screens if u want...
if the two satas are on the mobo (Deskstar 7K160 and the samsung) it recognize the samsung, and freezes at the windows loading window!
(it only has windows os in it because im not willing to format it before i can backup the files in it to the Deskstar 7K16)

---

### Post by lhide on 2009-09-08
anyone?

---

### Post by StuartN on 2009-09-08
> **lhide said:**
> if there is only the Deskstar 7K160 on the mobo bios doesnt recognize it ... if the two satas are on the mobo (Deskstar 7K160 and the samsung) it recognize the samsung

It sounds like you have one unformatted disc and connected it to the first (or first-ordered in BIOS) SATA cable. Try swapping the drives.

Also, you could boot off a Live CD or RescueCD or some other Linux and run the partition editor to check the discs.

---

### Post by lhide on 2009-09-08
> **StuartN said:**
> It sounds like you have one unformatted disc and connected it to the first (or first-ordered in BIOS) SATA cable. Try swapping the drives.

Also, you could boot off a Live CD or RescueCD or some other Linux and run the partition editor to check the discs.

already tried to swap the drives...
im out of cds now, so im thinkin about updating the bios, what do you think about it?

---

### Post by StuartN on 2009-09-08
> **lhide said:**
> already tried to swap the drives...
im out of cds now, so im thinkin about updating the bios, what do you think about it?

I can see no reason why updating the BIOS would make any difference.

If you have ANY Linux live CD, either one you burned or a magazine cover disc, then you should be able to check the hard drives by booting from the CD.

SystemRescueCD also has a USB stick install now: [http://www.sysresccd.org/Sysresccd-manual-en_How_to_install_SystemRescueCd_on_an_USB-stick](http://www.sysresccd.org/Sysresccd-manual-en_How_to_install_SystemRescueCd_on_an_USB-stick)

---

### Post by lhide on 2009-09-08
> **StuartN said:**
> I can see no reason why updating the BIOS would make any difference.

If you have ANY Linux live CD, either one you burned or a magazine cover disc, then you should be able to check the hard drives by booting from the CD.

SystemRescueCD also has a USB stick install now: [http://www.sysresccd.org/Sysresccd-manual-en_How_to_install_SystemRescueCd_on_an_USB-stick](http://www.sysresccd.org/Sysresccd-manual-en_How_to_install_SystemRescueCd_on_an_USB-stick)

even if the hd is not recognized in the bios or by booting with ubuntu cd?

---

### Post by lhide on 2009-09-08
i really need your help in this guys...
please give me advice!

---

### Post by StuartN on 2009-09-09
At some point you obviously had functioning hardware because you were able to format the drive and install an operating system. Put it back in that configuration and work from there. There is no driver or software setting you need at this stage, this is a hardware issue at the level of recognizing a bootable partition. Reset the BIOS if you have changed many settings.

And yes, System RescueCD on a USB will boot whatever the state of the partitions, as long as your BIOS supports USB booting and is configured to boot from USB (some systems, like mine, need the USB stick installed in order for the USB option to display in the BIOS menu).

---

### Post by Mr. Noob on 2009-09-09
Sata drives are by cable order and you should only see one listed in bios, if you can catch it on startup you might see a flash of a screen showing both...they are there. I just went through a dual boot dual drive scenario myself if that is what your attempting.
 
What is it your trying to do that you noticed the other drive not listed in bios?
 
What's not working?

---

