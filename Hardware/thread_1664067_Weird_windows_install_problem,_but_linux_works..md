---
title: "Weird windows install problem, but linux works."
date: 2011-01-10
forum: Hardware
---

### Post by GhostRider22 on 2011-01-10
Ok guys, I know this is exactly a linux problem, but im at my wits end, and this forum is always very helpful. 

I am repairing a toshiba satellite e105-s1802 for a friend. 

Windows would not boot on that PC, it would just go to a blank screen, with a underscore blinking in the top left for a moment, then black screen, as if no os was found to boot from. 

I used the recovery discs, and the same thing happened. I then downloaded another copy of windows 7 home premium. It would not install on the first partition, said the bios did not support booting from this disk. 

When the recovery CDs are used it makes 2 partitions, the first 1 as a "system" partition. 

After the recovery CDs run, and make the second partition, I am able to install windows on that second partition using the CDs i downloaded.  It installs fine, then boots into windows after you do the setup.  However, Once you reboot again the computer finds no OS, and just hangs on an empty screen. 

Now the reasons i hope people here can help me, is when i install ubuntu, it seems to work, and boot just fine, and is able to be installed on one disk. 

Now from what I can put together, and guess. It seems the bios is hard codded to not let windows install on the first partition as the first partition is supposed to be used for recovery or some other sort of thing. 

It seems that the bios tries to boot from the first partition though, and since windows is not on it, it does not find anything. 

There is no option in the bios to select a different harddisk to boot from, only to select the boot order. 

I can not find any advanced bios options, or other hidden setup options. I've been workong on this for many hours a day for 3 days, and I am about to melt it. 


Im sorry if i should not post this request here, but since ubuntu works, i was hoping someone here would have an idea of how to fix the situation. 

Thanks in advance.


Update edit. After reading this out loud, i thought perhaps i'd simply delete the first partition "system" using ubuntu live cd. Doing so, the computer does not even see a harddrive at all in the bios. I ended up checking the disk drive, and making it bootable using ubuntu. 

Now It says "operating system not found" I was excited, as thats ussually easy to fix using a command prompt from a windows boot disk. Except it can not access C: drive, or find the OS.

The more I think about this, the more I think a special toshiba driver is required to view the harddisk, as the harddisk is a toshiba brand as well. Its not raid, but does ask for a driver. 

Im so lost, and google isnt helping even remotely.

---

### Post by kevin45140 on 2011-01-11
I've had issues with this in the past, especially when goofing with Ghost and a couple of Linux distros.

I'm not giving you and end solution, but to diagnose the problem, try disabling ACPI mode in the BIOS and then see if it will recognize the drive.

Hey, it's happened to me so I'm just passing the info along ;)

- Kevin

---

### Post by GhostRider22 on 2011-01-11
I found that suggestion on google, and it did not help. 

I called toshiba, and they said the harddrive is broken, i tried to explain to them linux works fine, but they kept telling me how the computer is not made to work with linux. 

This is quite an odd problem indeed.

---

### Post by kevin45140 on 2011-02-13
> **GhostRider22 said:**
> I found that suggestion on google, and it did not help. 

I called toshiba, and they said the harddrive is broken, i tried to explain to them linux works fine, but they kept telling me how the computer is not made to work with linux. 

This is quite an odd problem indeed.

That sucks.  Have you found a solution at this point?  I like to learn from everyone in any way I can. :)

---

### Post by oldfred on 2011-02-13
Standard installs of win7 have a hidden (in windows) 100MB boot/recovery partition. That is so you can encrypt the main install, but the boot files cannot be encrypted. Boot flag (active partition in windows) is on the hidden 100MB boot partition.

Some BIOS require a boot flag on a primary partition or you get a BIOS error (they only think of windows). Even if you have Linux you still have to have a boot flag. Grub does not use the boot flag, but if your BIOS needs one then you just add one on any primary partition.

---

