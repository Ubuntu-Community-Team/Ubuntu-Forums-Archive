---
title: "hibernate prob:/dev/sda* changes to /dev/sdb* when booting with usb device plugged in"
date: 2007-08-30
forum: Hardware &amp; Laptops
---

### Post by flowbot on 2007-08-30
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/bugs/136214](https://bugs.launchpad.net/bugs/136214) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				I recently installed Feisty on a clients laptop and went through a million hoops to get hibernate working for him. i thought i'd succeeded, but when we plugged in his HP Photosmart printer via USB before booting, this changed all the drive partitions from /dev/sda* to /dev/sdb* - hence the resume file could not be found. it's pretty strange that a printer can shift the HDD device nodes!

Anyway, I thought I'd be able to get around this by referencing the swaps UUID in uswsusp.conf, but it appears that uswsusp doesn't accept disk UUID's .

Why is this happening when a USB device that isn't even a disk drive is plugged in? I really need to get to the bottom of this - hibernate works fine so long as Feisty doesn't switch device nodes on the HDD's without my asking it to.

---

### Post by kidders on 2007-09-02
Hi there,

It's possible that this could be normal behaviour.

Linux (along with most other OSs) obeys disk ordering information specified by BIOS. Linux may be re-ordering your disks because your BIOS is telling it to ... so you should investigate your BIOS configurator, and see if you can get it to stop dynamically reordering internal devices. (I have had several computers that do this sort of thing if not properly configured.)

---

