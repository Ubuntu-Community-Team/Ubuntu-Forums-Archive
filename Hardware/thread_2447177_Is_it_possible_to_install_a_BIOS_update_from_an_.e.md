---
title: "Is it possible to install a BIOS update from an .exe file?"
date: 2020-07-14
forum: Hardware
---

### Post by torspedia on 2020-07-14
My dad has asked me to do a fresh-install of Ubuntu (he had 19.10 on there previously). Before I do this, however, he needed me to do a complete BIOS upgrade, as recommended by his laptop's manufacturer. The only trouble is, is that they've sent a link which contains a .exe file, as they only provide BIOS updates for Windows. We're both not happy about this, obviously. 

 While he's trying to sort out the manufacturer, in the meanwhile I've been trying to find out how I am able to install this update. Haven't found anything suitable, thus far. What's the recommended way to do this, if any?

---

### Post by CatKiller on 2020-07-14
UEFI can update itself. Even the ancient BIOS was updated from DOS/FreeDOS rather than Windows. Don't assume from the name what the process is.

---

### Post by crip720 on 2020-07-14
There are ways of doing it with Linux, usually installing FreeDOS on USB stick.  I think the easiest way is just to install windows on a partition(temp if not wanted) and do the bios update, usually just a couple clicks.  Bios updates usually tested for windows only to work well.

---

### Post by oldfred on 2020-07-14
Most new UEFI can update directly from UEFI reading the update file on a FAT32 formatted partition. I use my ESP, since FAT32 & I made it larger. And most vendors also have that file as a download.
You may be able to extract update file with 7zip or similar from the .exe.
HP UEFI update - extract .bin from .exe file and copy into FAT32 partition.
[https://askubuntu.com/questions/539120/how-to-perform-a-hp-bios-upgrade-with-only-ubuntu/1234098#1234098](https://askubuntu.com/questions/539120/how-to-perform-a-hp-bios-upgrade-with-only-ubuntu/1234098#1234098)
[https://h30434.www3.hp.com/t5/Notebooks-Archive-Read-Only/How-to-update-BIOS-on-Linux/m-p/5441775#M1205498](https://h30434.www3.hp.com/t5/Notebooks-Archive-Read-Only/How-to-update-BIOS-on-Linux/m-p/5441775#M1205498)

Some very new systems now support UEFI update from Linux. Even if vendor still says they do not support Linux. Dell seems to have been one of the first to offer updates on many systems and Lenovo is now adding more of its new systems.
[https://fwupd.org/lvfs/devicelist](https://fwupd.org/lvfs/devicelist) & 
[https://fwupd.org/vendorlist](https://fwupd.org/vendorlist)

---

### Post by CatKiller on 2020-07-14
> **oldfred said:**
> You may be able to extract update file with 7zip or similar from the .exe.

In my experience you generally don't need to even need to do that; just point the UEFI at the file and it does the rest itself.

---

### Post by torspedia on 2020-07-14
> **CatKiller said:**
> UEFI can update itself. Even the ancient BIOS was updated from DOS/FreeDOS rather than Windows. Don't assume from the name what the process is.

How would that work, if I don't have to download anything?

---

### Post by torspedia on 2020-07-14
> **crip720 said:**
> There are ways of doing it with Linux, usually installing FreeDOS on USB stick.  I think the easiest way is just to install windows on a partition(temp if not wanted) and do the bios update, usually just a couple clicks.  Bios updates usually tested for windows only to work well.

Will have to put that by him, as he doesn't really want 10 on there!

---

### Post by torspedia on 2020-07-14
Will have a good look at that, ta.

---

### Post by torspedia on 2020-07-14
> **CatKiller said:**
> In my experience you generally don't need to even need to do that; just point the UEFI at the file and it does the rest itself.

How would I do that? BIOS is not something I generally mess about with (I'm not that technical enough).

---

### Post by Yellow Pasque on 2020-07-14
> **torspedia said:**
> How would I do that? BIOS is not something I generally mess about with (I'm not that technical enough).

Depends on the BIOS. What is the laptop model?

---

### Post by CatKiller on 2020-07-14
> **torspedia said:**
> How would I do that? BIOS is not something I generally mess about with (I'm not that technical enough).

You'd put the file somewhere that the UEFI can read from - the ESP or a FAT-formatted flash drive are good candidates. Then there'll be a button that you can press to get into the UEFI setup, which varies by manufacturer and is generally displayed early in the boot process, or you can select it from the Grub menu or run a command to reboot into the UEFI setup. From there there'll be an option to update the firmware. Where the option is also depends on the manufacturer. You point it at the file you downloaded and let it do its thing. It will restart the machine when it's finished. A firmware update will generally reset everything to defaults, so you might need to go back into the setup if you'd previously made changes.

Edit to add: the idea of changing the UEFI firmware from within Windows gives me chills; if users can do it then malware can do it, too. Ugh. Also, the UEFI settings page isn't something to be scared of: you can't generally *break* anything in there, although you can make things not work. There is usually a *reset to defaults* option somewhere, which, again, varies by manufacturer, if you've played and made things not work.

---

### Post by torspedia on 2020-07-15
> **Yellow Pasque said:**
> Depends on the BIOS. What is the laptop model?

It's an Acer ConceptD #N17C2.

---

### Post by &amp;wP*!) on 2020-07-15
BTW, the systemd service **fwupd** is useless for very old laptops to get any of its firmware like SSD etc. At least for my E7440 laptop, which is 8 years old now. The laptop has Ubuntu since 2017 and fwupd never did anything automatically. Better to download these directly at BIOS/UEFI.

---

### Post by Yellow Pasque on 2020-07-15
I looked at an example Acer BIOS file and it really looks like it requires Windows. I couldn't even get it to run in my FreeDOS VM ("will not run in DOS mode")

Maybe the best way to do this is:
1) create bootable Win10 USB stick
2) copy the BIOS .exe to it
3) Boot the USB
4) Press Shift+F10 to get to command prompt at the intro screen
5) Try to run the .exe from there

> N17C2
FYI: I'm pretty sure that's the screen model.

---

### Post by torspedia on 2020-07-16
> **Yellow Pasque said:**
> I looked at an example Acer BIOS file and it really looks like it requires Windows. I couldn't even get it to run in my FreeDOS VM ("will not run in DOS mode")

Maybe the best way to do this is:
1) create bootable Win10 USB stick
2) copy the BIOS .exe to it
3) Boot the USB
4) Press Shift+F10 to get to command prompt at the intro screen
5) Try to run the .exe from there


FYI: I'm pretty sure that's the screen model.


I've tried twice now to create a bootable Win 10 USB, each time it came back saying that the **install.wim** file was too large. I even tried copying that file on its own, to no avail. Trying to install it onto a 16GB USB.

---

### Post by Yellow Pasque on 2020-07-16
Is the file larger than 4GB? If so, it won't work on a FAT32 filesystem. (There are ways around  that. Google it.)
Where did you obtain the .iso?

---

### Post by oldfred on 2020-07-16
The latest versions of Windows have the .wim file over 4GB and FAT32 has a 4GB limit.
I used a Windows system and its installer, and it split the .wim file to make it smaller.

Most of instructions you find on Internet are for older versions of Windows where .wim was smaller and fit fine on a FAT32 partition. You need the newer instructions.
Do not know why Microsoft just does not split file in the download ISO to avoid issues. But I guess they only want Windows users to download and use ISO.

Dell has this info on how to do it. But I think it is using Windows commands.
[https://www.dell.com/support/article/en-us/sln313422/windows-10-iso-contains-wim-file-that-is-big-for-fat32-file-system?lang=en](https://www.dell.com/support/article/en-us/sln313422/windows-10-iso-contains-wim-file-that-is-big-for-fat32-file-system?lang=en)

Using Linux:
[https://techbit.ca/2019/02/creating-a-bootable-windows-10-uefi-usb-drive-using-linux/](https://techbit.ca/2019/02/creating-a-bootable-windows-10-uefi-usb-drive-using-linux/)

---

### Post by torspedia on 2020-07-16
> **Yellow Pasque said:**
> Is the file larger than 4GB? If so, it won't work on a FAT32 filesystem. (There are ways around  that. Google it.)
Where did you obtain the .iso?

Yes, it was. I was following the guide from It's FOSS. (Now to think of what to search for)

---

### Post by CatKiller on 2020-07-16
> **torspedia said:**
> I've tried twice now to create a bootable Win 10 USB

Have you tried just going into the UEFI setup yet? The videos on the Acer website of their process show the Windows part of it as simply automatically rebooting into UEFI setup with the particular file already selected for update; it's still the UEFI that's doing all the work.

---

### Post by torspedia on 2020-07-16
> **CatKiller said:**
> You'd put the file somewhere that the UEFI can read from - the ESP or a FAT-formatted flash drive are good candidates. Then there'll be a button that you can press to get into the UEFI setup, which varies by manufacturer and is generally displayed early in the boot process, or you can select it from the Grub menu or run a command to reboot into the UEFI setup. From there there'll be an option to update the firmware. Where the option is also depends on the manufacturer. You point it at the file you downloaded and let it do its thing. It will restart the machine when it's finished. A firmware update will generally reset everything to defaults, so you might need to go back into the setup if you'd previously made changes.

I've copied the .exe file over to the USB that's been formatted into FAT32. Unfortunately, however, I could not see any option to "update the firmware" in any of the BIOS settings. The machine has BIOS v1.23 and most of what I've come across, thus far, hasn't shown me where to find the update firmware option!

---

### Post by torspedia on 2020-07-16
> **CatKiller said:**
> Have you tried just going into the UEFI setup yet? The videos on the Acer website of their process show the Windows part of it as simply automatically rebooting into UEFI setup with the particular file already selected for update; it's still the UEFI that's doing all the work.

Yes, I have, but haven't found the option to boot from the .exe file, that I have on a FAT32 formatted USB.

I haven't looked at the videos on the Acer site yet, so will have a shufty, ta!

---

### Post by oldfred on 2020-07-16
Many older Acer, required you to set an UEFI password to open up additional settings. Some now require control-S.
Never lose that password or you may have a brick, or reset to blank when done making UEFI setting changes.

Acer Swift 5 (2019) ctrl-s  in UEFI required to be able to change to AHCI mode.
[https://askubuntu.com/questions/1217061/installation-on-acer-swift-5-freezes-no-partitions-shown](https://askubuntu.com/questions/1217061/installation-on-acer-swift-5-freezes-no-partitions-shown)
Acer Aspire 5 Model A515-54-5649  Intel Core i5-10210U Install Tutorial
[https://ubuntuforums.org/showthread.php?t=2437702](https://ubuntuforums.org/showthread.php?t=2437702)
Acer Aspire E15 will not dual boot, many details Trust settings in step 35
[http://askubuntu.com/questions/627416/acer-aspire-e15-will-not-dual-boot](http://askubuntu.com/questions/627416/acer-aspire-e15-will-not-dual-boot)
 InsydeH20 setup utility
[https://askubuntu.com/questions/870022/how-to-get-grub-boot-option/870074](https://askubuntu.com/questions/870022/how-to-get-grub-boot-option/870074)
[https://askubuntu.com/questions/886536/how-to-install-ubuntu-on-an-acer-with-preinstalled-windows-10-home](https://askubuntu.com/questions/886536/how-to-install-ubuntu-on-an-acer-with-preinstalled-windows-10-home)

---

### Post by Paulgirardin on 2020-08-18
[QUOTE=oldfred;13972999]Many older Acer, required you to set an UEFI password to open up additional settings. Some now require control-S.
Never lose that password or you may have a brick, or reset to blank when done making UEFI setting changes./QUOTE]

This is correct.
I recently had to discover this fact. 
The safest option is create the password ,make the changes and then set the password back to blank when done ,as Oldfred suggests

---

