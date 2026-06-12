---
title: "Move wubi System to Another Location"
date: 2009-09-11
forum: Installation &amp; Upgrades
---

### Post by plade on 2009-09-11
This is for all those people who installed a wubi system on their hard drive and now want to access the rest of the partition on which it is installed.
For people like me who use pay-per-use internet, it is really a pain to install a fresh system and have it upgraded again.

I have a workaround for this as follows : 

Suppose you are moving Ubuntu from D: drive to E: drive.

The wubi install has the following files in the system currently : 

[LIST=1]
[*]C:\wubildr and C:\wubildr.mbr   :   These files are used in the windows boot loader to start the ubuntu GRUB loader.
[*]The folder D:\ubuntu   :   This folder is where the ubuntu system lies, and contains the ubuntu installer, the wubi uninstaller and the GRUB loader in addition to the ubuntu virtual disk.
[/LIST]
Now to move the system to E:, we basically need to tell the GRUB loader where the system currently lies. 

1. Move the D:\ubuntu folder to the new location E:\.
2. Open the file E:\ubuntu\disks\boot\grub\menu.lst using an editor (not notepad)
( If you are not sure what you are doing, first copy the file somewhere, maybe in the same folder with different name. )
3. Lines starting with a "#" are comments to show you how to modify the file.
Now run to the last few lines of the file. There are a few lines with the headings "title", "root", "kernel" and "initrd".
In the lines with heading "kernel" is the location of the ubuntu system stored.
Mine shows this : 

```
kernel        /boot/vmlinuz-2.6.28-15-generic root=UUID=70FCA54AFCA50C02 loop=/ubuntu/disks/root.disk ro quiet splash 
```the UUID=70FCA54AFCA50C02 part is the identifier of the partition and we need to change that.

4. Replace all instances of UUID=70FCA54AFCA50C02 with the new UUID=XXXXXXXXXXXXXXXX
5. Save the file and you are done.

_________________________________________________________________________

To find UUID of the partition: 

Boot the system using ubuntu live cd and start ubuntu session.
Open the terminal and write :
```
sudo blkid
```Find the UUID associated with the required partition using the volume label. 
(It obviously will not show it as "E:")


Hope this helps.

---

