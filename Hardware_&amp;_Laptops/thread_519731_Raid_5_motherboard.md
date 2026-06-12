---
title: "Raid 5 motherboard"
date: 2007-08-07
forum: Hardware &amp; Laptops
---

### Post by realalehunter on 2007-08-07
Hi, I have the job of building a server for file storage, svn, development web server for work. We want to have Raid 5 using four 500GB hard drives. Iv read around on the forum about not using a motherboard that has fake raid (raid software that is stored on the board as firmware for which getting linux driver is a pain).

I am wanting to use the Linux software raid instead of using a fake raid or paying out for an expensive 3ware card or other non fake hardware raid. Can anyone recommend any motherboards that will suit this purpose and will I just be able to plug the hard drives into it and then configure the raid when doing the installation.

Thanks for any help.
Matt

---

### Post by kidders on 2007-08-08
> **realalehunter said:**
> Can anyone recommend any motherboards that will suit this purposeNaturally, software RAID is hardware-independent.

Incidentally, I would expect a 4-device software RAID 5 implementation to perform rather poorly on a standard motherboard. As you can imagine, equipping the average, general-purpose board with the ability to transfer data at full throttle to & from that many devices simultaneously would be a waste. Are you sure a hardware solution wouldn't better suit your needs?

---

### Post by psusi on 2007-08-08
It sounds like you want hardware raid, which is going to cost money.  If you want to save money, they go with software raid.  If you are a masochist, see [https://wiki.ubuntu.com/FakeRaidHowto](https://wiki.ubuntu.com/FakeRaidHowto).

---

### Post by realalehunter on 2007-08-09
Thanks. I am now looking into getting a proper hardware raid from the advice of a few people. 3 options I am looing into are a3ware raid, an Adaptec or  an LSI Logic.

---

### Post by realalehunter on 2007-08-09
Iv decided to go with the 3ware I think. Iv added a full shopping list at 
[http://ubuntuforums.org/showpost.php?p=3159230&postcount=15](http://ubuntuforums.org/showpost.php?p=3159230&postcount=15)

Thanks for the help

---

### Post by psusi on 2007-08-09
As kidders said, one of the advantages of software raid is that it is not tied to the hardware.  I had a server with a hardware raid card crap out last year and lost all the data on the disks and had to have a replacement card overnighted in.  Had it been software raid and the motherboard had fried, I could have plugged the disks into another machine to get at the data.

---

### Post by kidders on 2007-08-09
> **psusi said:**
> I had a server with a hardware raid card crap out last year and lost all the data on the disks and had to have a replacement card overnighted in.Nasty. :-(

It's probably worth mentioning that FakeRAID essentially *is* software RAID ... except that it's buggier, and doesn't have that major advantage of hardware-independence. I always go for OS-level software RAID, except in cases where the array I want is prohibitively large.

Realalehunter ... I know this is sort of a statement of the obvious, but it really is worth taking a look around to see what you can find out about how happy other Linux users are with the card you've chosen. Aside from that, be sure you've got enough power, and plenty of ventilation. I'm not altogether sure 550W is enough to provide a stable supply to 5 hard disks & an optical drive. :-k What do you think, Psusi?

---

### Post by fjgaude on 2007-08-09
> **psusi said:**
> As kidders said, one of the advantages of software raid is that it is not tied to the hardware.  I had a server with a hardware raid card crap out last year and lost all the data on the disks and had to have a replacement card overnighted in.  Had it been software raid and the motherboard had fried, I could have plugged the disks into another machine to get at the data.

Man, I second kidders suggestions... from vast experience!

There are many MBs out there now that have their SATA ports controlled by PCI-E bus, which is even faster than PCI-X. One of them is the Asus M2N32-SLI and it handles six SATAs... and it's price is less than you would pay for any hardware raid board or external setup. DFI ICFX3200 is another. Just make sure the SATA controller, nForce4 does, runs from the PCI-Express bus.

Linux md and mdadm is all you need to get the speed that is fast, like 270 MB/sec sequential read, full-throttle speed as kidders says. I'm not sure what a hardware setup that is that fast would cost you.

PCI-E, modern SATA drives, and Linux software raid5 rocks! <smile>

frank

---

### Post by psusi on 2007-08-09
> **kidders said:**
> Nasty. :-(

It's probably worth mentioning that FakeRAID essentially *is* software RAID ... except that it's buggier, and doesn't have that major advantage of hardware-independence. I always go for OS-level software RAID, except in cases where the array I want is prohibitively large.


While it does still have some kinks to be worked out, FakeRAID is not hardware dependent because it is software raid like you said.  If the motherboard craps out, you can plug the disks into any other computer and mount them to get your data off.

---

### Post by fjgaude on 2007-08-09
> **psusi said:**
> While it does still have some kinks to be worked out, FakeRAID is not hardware dependent because it is software raid like you said.  If the motherboard craps out, you can plug the disks into any other computer and mount them to get your data off.

You mean as long as the chipset is the same? If one MB has a nvidia controller and the other has a Silicon Image will what you say work?

frank

---

### Post by psusi on 2007-08-09
> **fjgaude said:**
> You mean as long as the chipset is the same? If one MB has a nvidia controller and the other has a Silicon Image will what you say work?

frank

No, no hardware requirements, aside of course, from enough ( presumably sata ) ports to connect the drives.

---

### Post by fjgaude on 2007-08-09
Okay, I guess all the so-called raid controllers on MBs can be setup for Linear, JBOD sockets for SATA drives.

You see just about every MB I've looked at lately has fakeraid with lots of SATA connections, usually four to eight through two differrent-brand controllers.

But here we use md and mdadm with our Linux boxes, right, yes.

For home users the MBs with SATA ports driven off PCI-Express bus is the way to go. Areca 1220s are for businesses with big budgets, eh?

frank

---

