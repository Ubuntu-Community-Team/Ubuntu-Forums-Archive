---
title: "No bootable disk found??????? need help"
date: 2008-08-02
forum: General Help
---

### Post by jrharvey on 2008-08-02
Ok so i have 3 primary partitions setup for 1 windows XP, 1 Ubuntu and 1 Test OS. I had 32bit vista living on my test OS and dont really use it. Sooo i decided to delete the Test OS and leave it unformated. Well, i reboot and all of a sudden my GRUB is gone so i stick in my supergrub disk and go through the steps to fix grub. Well it doesnt work so i try to use grub and boot into windows. It tells me that "NTLDR is Missing" and to reboot. So i use super grub again to boot into ubuntu and it works but i cannot install grub on the hard disk. Now if i want to boot i need to use super grub disk. Whats the deal?

BTW: when i reboot without super grub disk it tells me that "No Bootable Disk Found"

---

### Post by phidia on 2008-08-02
> So i use super grub again to boot into ubuntu and it works but i cannot install grub on the hard disk.

What error messages do you get when you try to do "sudo grub-install (hd0)"?

---

### Post by jrharvey on 2008-08-02
> syntax error near unexpected token `('
Hmmm havnt tried that yet.

---

### Post by jrharvey on 2008-08-02
> jrharvey@jrharvey-desktop:~$ sudo grub-install hd0
[sudo] password for jrharvey: 
Searching for GRUB installation directory ... found: /boot/grub
Installation finished. No error reported.
This is the contents of the device map /boot/grub/device.map.
Check if this is correct or not. If any of the lines is incorrect,
fix it and re-run the script `grub-install'.

(hd0)	/dev/sda
 This is what i get

---

### Post by phidia on 2008-08-03
From that it looks like it re-installed grub-can you now boot to your installs?

---

### Post by jrharvey on 2008-08-03
no still the same error message.

---

### Post by jrharvey on 2008-08-03
Hmmm look like no more windows. This is sooo weird but the windows partition is completely gone. Both of them are missing. I have not even been into the partition manager since b4 all this happened. Do you think re-installing grub deleted my windows partition. There is literally nothing there.

---

### Post by phidia on 2008-08-03
grub-install (hd0) installs to the MBR not a partition which would be (hd0,X) where X=an actual partition number. 
I do not see how grub install would have done that.
Get [system rescue cd]("http://www.sysresccd.org/Main_Page") if you can and sorry you had that happen.

---

### Post by jrharvey on 2008-08-04
No its ok. I backed up everything. I did however figure out the problem as to why GRUB wasnt loading upon restart. I went into Gparted and Flagged my ubuntu partition to boot and that fixed everything. Im not sure why that fixed the problem but it did.

---

