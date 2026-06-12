---
title: "My external Sata and Internal Sata Battle It off."
date: 2008-07-17
forum: General Help
---

### Post by krooked on 2008-07-17
I have the internal 300gb sata drive that i used to install ubuntu,  no other operating systems present. 
Then i have an external Terabyte drive that is ntfs that i use to hold most my backup info, it goes to a windows laptop and ubuntu.

The problem it seems to give is when it is plugged in at startup it makes grub fail, after researching it seems this is caused by my normal Sda1 on my MBR which used to be the internal drive is now replaced with the External drive as Sda1, therefore becomming Sdb1.  Is there a way to keep these drives from switching around, it would make it alot easier if they didnt because i also would like to have the external ntfs drive set to automount, but last time i set the permissions and did that, it locked me out of my internal drive when they switched at a reboot.

---

### Post by coffeecat on 2008-07-17
This sounds like a BIOS configuration issue, not a Linux or grub one. I would guess that your BIOS is set to look for a usb drive to boot from before the internal drive. If no usb drive is plugged in, it will boot from the internal HD, making that sda. If a usb drive is plugged in, it tries to boot from that but can't, but it has already designated that as drive 1 = sda and the internal drive as drive2/sdb.

Have a look in the BIOS and see what the boot order is. It's easily changed if that's the problem.

---

### Post by krooked on 2008-07-17
yeah, thats what i thought. because i actually got a ntdlr error missing once while i failed to boot, making me realize it was trying to boot off the external. well it fixed it that time, but now it is set to having to boot from the internal and still giving me that error. 
there is something fishy about the installation with the external plugged in or not becuase i just re-installed all my ubuntu os. everything worked great, got it setup
plugged in the external, had to force mount. then when i rebooted it was giving a grub 1.5 error. 
now my internal isnt being reckognized properly by the live cd to reinstall grub, even though its still detected by my bios. i there went to super grub disk and the partition is reckognized, but when i tried to repair the grub and then reboot it is hanging after loading and getting all sorts of i/o errors and then going to recovery console.

---

