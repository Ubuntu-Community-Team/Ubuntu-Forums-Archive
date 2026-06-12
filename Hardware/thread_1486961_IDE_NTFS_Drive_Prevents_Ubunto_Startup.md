---
title: "IDE NTFS Drive Prevents Ubunto Startup"
date: 2010-05-18
forum: Hardware
---

### Post by ram2008 on 2010-05-18
[SIZE="3"]**I recently built a new computer based on the Asus M4A785-M motherboard and the AMD quadcore Athlon II X4 CPU.  The main hard drive is a 500 GB SATA drive with Ubuntu as the only operating system.  No dual boot this time.  The main board has only one IDE connector which I use for my DVD burner and a 250 GB NTFS drive for video.  I've been dismayed to learn that Ubuntu will not boot with this drive powered up.  If I remove the power plug from the IDE drive, it will boot OK.  I can then restore power to the drive and access the files on it with no problem.  My question is why Ubuntu won't boot with this drive powered up and is there a way to work around this?  I need this NTFS drive in the system for video storage.**[/SIZE]

---

### Post by kelvin spratt on 2010-05-18
You need to change your boot priority in bios so you boot the drive with Ubuntu,

---

### Post by ram2008 on 2010-05-18
Thanks for responding to my post but what you suggested has been done already.  The SATA drive that contains Ubuntu is the priority boot device or first boot device.  In spite of that, I still get the message "Error loading OS".  Most of the time I just remove the power plug from the IDE drive whenever I need to boot or reboot the computer, but that's not a very satisfactory solution.  At some point I would like to close the case. :)

---

