---
title: "[solved] sd card recovery"
date: 2016-02-13
forum: Hardware
---

### Post by Jens_Steenfadt on 2016-02-13
Hey All,

I'm trying to help a friend of mine, currently having a messed up sd card in his hands.

It's in Intenso micro card with 8GB in a HC adapter card, not mounting anymore.

lsusb will show the reader
```
Bus 001 Device 006: ID 05e3:0723 Genesys Logic, Inc. GL827L SD/MMC/MS Flash Card Reader
```

dmesg does show the card is recognized to some point, but gives i/o errors for sectors 0 and 24.

```

[39889.427217] blk_update_request: I/O error, dev sdf, sector 0[39889.427221] Buffer I/O error on dev sdf, logical block 0, async page read
[39889.429448] sd 8:0:0:0: [sdf] FAILED Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[39889.429453] sd 8:0:0:0: [sdf] Sense Key : Not Ready [current]
[39889.429458] sd 8:0:0:0: [sdf] Add. Sense: Medium not present
[39889.429460] sd 8:0:0:0: [sdf] CDB: 
[39889.429462] Read(10): 28 00 00 00 00 18 00 00 08 00
[39889.429474] blk_update_request: I/O error, dev sdf, sector 24
[39889.429478] Buffer I/O error on dev sdf, logical block 3, async page read
[39889.433709]  sdf: unable to read partition table

```

Testdisk does not even show up the drive and ddrescue fails with a "ddrescue: Can't open input file: No medium found". Also disk will not list anything on /dev/sdf

I used DiskDrill Pro under Mac OS, as well as SanDisk's Rescue Pro Deluxe. None of them will detect the drive.


The owner of the card had sent it to some specialists, who say they can recover, but at >600€ charge.
There are holiday pics on the card, but for 600€, he could book a flight, go there again and re-shoot all the pics, actually. So he doesn't want to spend.

So, with my limit knowledge I'm actually running out of ideas. No clue how to "force" ddrescue to proceed (if at all possible?)

Any suggestion highly welcome :-)
Thanks!

---

### Post by sudodus on 2016-02-13
Welcome to the Ubuntu Forums :-)

I'm afraid that the card is damaged beyond repair with the tools that we have available. But I can suggest checking if it can be seen as a mass storage device /dev/sdx, where x is the drive letter (maybe **f** according to your hint in post #1).

You can try with different card readers, different computers and different USB ports.

In linux you can run the following command and try to 'see it' a mass storage device /dev/sdx.

```
sudo parted -ls
sudo ls -l /dev/disk/by-id|grep /sd.$
```

If you can see it, you should be able to make a cloned copy with ***ddrescue*** and after that use tools to repair the file system on the closed copy and finally, if nothing else works, try ***photorec***.

[https://www.cgsecurity.org/](https://www.cgsecurity.org/)

If you cannot see it, I'm afraid we have no cheaper method that what was offered by the commercial specialists.

---

### Post by Jens_Steenfadt on 2016-02-13
Thanks' for the quick feedback. I was a bit afraid of this answer, so maybe not so surprising after all.

Parted will not show the drive, only the sda HDD and the /dev/mapper drives are listed.

/dev/disk/by-id:
```

[FONT=Menlo]lrwxrwxrwx 1 root root  9 Feb 13 14:57 ata-HDS728080PLA380_40Y9028LEN_PF1H75S8UY4MGL -> ../..[COLOR=#c33720]**/sda**[/COLOR][/FONT]
[FONT=Menlo]lrwxrwxrwx 1 root root  9 Feb 13 14:55 usb-Generic_STORAGE_DEVICE_000000009451-0:0 -> ../..[COLOR=#c33720]**/sdf**[/COLOR][/FONT]
[FONT=Menlo]lrwxrwxrwx 1 root root  9 Feb 13 13:48 usb-USB2.0_CF_CardReader_1234600-0:0 -> ../..[COLOR=#c33720]**/sdb**[/COLOR][/FONT]
[FONT=Menlo]lrwxrwxrwx 1 root root  9 Feb 13 13:48 usb-USB2.0_MS_CardReader_1234600-0:3 -> ../..[COLOR=#c33720]**/sde**[/COLOR][/FONT]
[FONT=Menlo]lrwxrwxrwx 1 root root  9 Feb 13 13:48 usb-USB2.0_SD_CardReader_1234600-0:2 -> ../..[COLOR=#c33720]**/sdd**[/COLOR][/FONT]
[FONT=Menlo]lrwxrwxrwx 1 root root  9 Feb 13 13:48 usb-USB2.0_SM_CardReader_1234600-0:1 -> ../..[COLOR=#c33720]**/sdc**[/COLOR][/FONT]
[FONT=Menlo]lrwxrwxrwx 1 root root  9 Feb 13 14:57 wwn-0x5000cca30df786a5 -> ../..[/FONT][COLOR=#C33720][FONT=Menlo][B]/sda
[/B][/FONT][/COLOR]
```

As you can see, there're two readers attached, one multi and on single SD XC (sdf). None of them was able to read good enough to make ddrescue work.

---

### Post by sudodus on 2016-02-13
The very last attempt would be to install and try photorec directly (not via ddrescue)

```
sudo apt-get install testdisk

sudo photorec /dev/sdx
```

where x is the drive letter (for example **f**). (But I think the SD card is beyond repair with 'free' methods.)

---

### Post by ajgreeny on 2016-02-13
Could this also be a dirty micro adapter rather than the micro-sd itself?

It may be worth trying with another adapter (and another computer) just to test such minor things.

Can you also plug in the empty card reader (if it's external) run ```
dmesg | tail
``` then plug the micro-sd card into the reader and run the command again to see if you get any clues from the differences shown in those final lines of dmesg, though it looks as if you have already thought about that.

---

### Post by Jens_Steenfadt on 2016-02-14
> **ajgreeny said:**
> Could this also be a dirty micro adapter rather than the micro-sd itself?

It may be worth trying with another adapter (and another computer) just to test such minor things.

Can you also plug in the empty card reader (if it's external) run ```
dmesg | tail
``` then plug the micro-sd card into the reader and run the command again to see if you get any clues from the differences shown in those final lines of dmesg, though it looks as if you have already thought about that.


Thanks' for the help, but I think I've now tried each and every combination:

- used the card reader on a Mac -> no success
- used two different micro sd card adapters -> same result
- used two different card readers (one single, one multi) which are using separate USB cards (multi is plugged into a PCI USB 2 card), the single one is using onboard USB

So, I'll need to accept the fact that the micro sd card is seriously broken.

But good to know that I can can get support here so quickly!!! =d>

---

