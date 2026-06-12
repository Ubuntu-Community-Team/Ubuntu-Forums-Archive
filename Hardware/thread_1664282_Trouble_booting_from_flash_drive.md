---
title: "Trouble booting from flash drive"
date: 2011-01-10
forum: Hardware
---

### Post by Oloty on 2011-01-10
I recently installed xubuntu on my 4GB flash drive. 
After I finished installing I restarted my computer and set it to boot from "Flash memory" first. 
I got an error like this:
```

Intel (R) Bootagent FE v4.1.18
Pxe-e61 media test failure, check cable
Pxe-MOF Exiting intel bootagent

```

I Googled and someone suggested to someone else to turn of Lan. 
I did but the computer just booted right to Windows.

So, how can I have my computer boot from the flash drive?

Computer = Toshiba Satellite A105-S4074

---

### Post by oldfred on 2011-01-10
My A105 just boots fine from flash. I think I used f12 but get confused with desktop. I have only booted flash once or twice to prove it works and install 10.10.

The network boot should have been last on the boot list. You can set flash, hard drive and CD as choices. 

If need be I can reboot and see exactly what you see.

Are you sure flash is bootable. If not it just skips to next device.

---

### Post by Oloty on 2011-01-10
IDK if my flash drive is bootable.
Its a 4GB Sony Micro Vault.

I have it set to boot in this order:
```

Flash Memory
CD/DVD Drive
FDD
HDD
LAN

```

But, it still gos straight to Windows?

Edit: If it helps I believe my BIOS version is 1.8.
Maybe I need to update?

---

### Post by Oloty on 2011-01-10
[BUMP] Really need a fix for this problem =/

---

### Post by Oloty on 2011-01-10
Why can't anyone help me with my problem. T.T

---

### Post by efflandt on 2011-01-10
How did you install Xubuntu to the flash, Startup Disk Creator in Ubuntu, a regular installation with grub, or something else?

One mistake I often make with Startup Disk Creator is formatting the drive (like sdb) instead of the partition (like sdb1).  Then I have to use gparted to recreate an msdos partition table and the partition.  Is your flash able to boot from any other computer?

PXE sounds like it is trying to do a network boot (from LAN).

I don't know if your model is older or just different than my A105-S4384, but with following boot order it boots USB flash without even having to press F12 in BIOS splash screen.

USB Memory
CD/DVD
HDD
FDD
LAN

If you do press F12 during BIOS splash, does it even list USB?  I believe you have to make sure that in BIOS you have: **Legacy USB Support: Enabled**

---

