---
title: "UEFI boot loader [SOLVED]"
date: 2015-03-02
forum: Hardware
---

### Post by patopoo-3 on 2015-03-02
Hello, I have an Asus X550C, with UEFI as boot loader. 
The first time I had to create several partitions to get boot my notebook. One partition to ??, the second 300mb to the bootloader, the remainings as usual, OS, swap and /home. Also is needed turn disabled the new loader (PXE OpROM disabled)
It has become a headache to reinstall linux, the first attempt I get a message from Grub couldn't load, I tried to run boot-repair but it refused because UEFI wasn't enabled, I did it enabled and getting the same mesage.
Trying anything I assign the first partition as /boot and the things go wrong. Now I get an "Reboot or Select proper Boot device or insert Boot Media in selected boot device and press a key" message.
Can someone help me to restore mi notebook?
Thanks in advance.

---

### Post by oldfred on 2015-03-02
Really need you to boot Ubuntu installer and then install Boot-Repair into that. Post link to summary report.
       Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
Precise, Trusty, Vivid, & Utopic all should work now with current ppa
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

Please review link in my signature, also.

Some possibly similar Asus:
   [SOLVED] Dual Boot on Asus K55vd SX696H - 8 GB (Solved) EFI
[http://ubuntuforums.org/showthread.php?t=2151394](http://ubuntuforums.org/showthread.php?t=2151394)

 ASUS K55A  Windows 8 & Ubuntu   Some Asus need this boot parameter pci=nomsi
[http://ubuntuforums.org/showthread.php?t=2088499](http://ubuntuforums.org/showthread.php?t=2088499)

---

### Post by patopoo-3 on 2015-03-03
Thank you oldfred
I solved this according to this page [https://help.ubuntu.com/community/Installation/UEFI-and-BIOS](https://help.ubuntu.com/community/Installation/UEFI-and-BIOS)
cheers :p

---

