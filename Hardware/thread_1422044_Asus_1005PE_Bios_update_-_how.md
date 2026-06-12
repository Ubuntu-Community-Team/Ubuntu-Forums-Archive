---
title: "Asus 1005PE Bios update - how?"
date: 2010-03-04
forum: Hardware
---

### Post by woody22075 on 2010-03-04
I need to update the bios on my Asus eee pc 1005pe (running ubuntu nbr 9.10) to the latest version.  the file asus offers is .rom.  how can i install it on a flash drive?  i copied the .rom directly to a 8 gig flash (FAT32).  Any ideas?

thanks.

m.

---

### Post by mörgæs on 2010-03-06
[http://forum.eeeuser.com/viewtopic.php?pid=694140](http://forum.eeeuser.com/viewtopic.php?pid=694140)

---

### Post by dionblundell on 2010-03-10
This worked on my EEE 701,
have just brought a 1005pe
and it appears the same.

At boot, press ALT+F2 - make sure you only have one USB drive plugged in, it'll then search the USB drive for a file called 701.ROM, I assume in this case it'll search for 1005PE.ROM
anyway, if it doesn't find the file it tells you what it's searching for.

A _Fat32_ drive __does_not_work__ on a 701, but a Fat16 drive does.

__Instructions__
1) format a USB drive as Fat16 (I have found USB drives that will not work, Lexar for example wont work, even though it is Fat16, so try multiple drives if the BIOS doesn't find the file)
2) download your ZIP file from ASUS
3) extract the .ROM file
4) rename it something like 1005.ROM
5) copy it to Fat16 USB Drive
6) reboot
7) Press ALT + F2
8) it should now tell you it's searching for 701.ROM or similar

Hope this works

---

### Post by orangeisorange on 2010-07-17
Thank you dionblundell!  I have been searching for the past 24 hours for a way to flash the bios.  After vain attempts at bootable USBs and DOS solutions, I'm a bit annoyed that it was so simple, yet glad to have fixed it.
I have a Eee PC 1005PE and I used a 1gb USB flash drive.  I have a computer with XP on it, so I just right-clicked the USB drive (F:, in my case) and clicked "format" and chose "FAT."  I did not attempt FAT32 at your suggestion, so I don't know if it works or not with the 1005PE.  Then I copy/pasted the .rom BIOS file I downloaded from the ASUS website onto the USB.  I started up the netbook with the USB plugged in and held ALT+F2 as it loaded.
I hit a bump here, as the USB was detected, but it could not find the file.  I noticed it was looking for 1005P.rom and that the BIOS file ASUS provided was called 1005P-ASUS-1103.rom.  I believe the last part is the version of the BIOS.  So I took out the usb (the netbook was in a "found usb, can't find 1005p.rom" loop which changed to "can't find usb" when I took it out), renamed the file 1005P.rom on my M$ computer, plugged it back in while the BIOS updater was still attempting to run, it detected the USB again and the file this time and updated the bios successfully.  I shutdown per instruction, took out the USB, turned it back on, and everything worked great.  I had a brand new ASUS, barely a week old, and it had shipped with BIOS that had been updated at least 4 times since the version I had.  Flashing the BIOS fixed an issue I was having where the brightness keys weren't working properly.
Sorry for the verbosity, I like to be detailed because if other people aren't then I'm less likely to be successful when I fix things =]

---

### Post by Geo411m on 2010-07-19
I wish I would have found this last week. I had to create a bootable USB DOS and update using the command line. This is so much easier.

---

### Post by dre12b on 2010-08-05
Just to confirm - FAT32 does NOT work.  I tried it, but the EEE would not recognize the USB until it was formatted as FAT16.

---

### Post by tacit1 on 2011-03-13
Please note the FAT16 filesystem must be less than 2GB in size.

I had success formatting with the disk utility and setting the size to 667MB.

Then, after creating a FAT partition ran the following command:

```
sudo mkfs.vfat -F 16 -n bios /dev/sdb1
```

Then renamed 1005P-ASUS-1202.ROM to **1005P.ROM**

The flash was successful, and it fixed a problem with the machine hanging on a black screen and blinking cursor (failed to POST).

---

