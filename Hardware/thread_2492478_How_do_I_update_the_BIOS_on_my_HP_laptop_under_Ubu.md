---
title: "How do I update the BIOS on my HP laptop under Ubuntu?"
date: 2023-11-12
forum: Hardware
---

### Post by furtivehippo on 2023-11-12
So I need to update the BIOS on my HP laptop (2017 250 G6), but the update I have downloaded from the HP website is in the form of a Windows executable.

Must I re-install Windows (laptop is currently running Ubuntu 23.10) in order to carry out the update, or is there a way it can be done from Ubuntu? Thanks.

---

### Post by Yellow Pasque on 2023-11-12
You can use wine to run the .exe file . It won't do the BIOS/EFI update for you, but you should be able to extract the files and put them on a USB stick. There are 5 different .bin and .sig file pairs inside the .exe
The pair of files you need depends on your system board ID. You can find this ID either on the POST/start screen, or (if a logo covers the start text), you can enter the BIOS/EFI and look at "System Information".

NOTE: You may get an error window before you get to the menu that allows you to extract the files, but it will eventually go away if you keep clicking "OK"

---

### Post by oldfred on 2023-11-13
HP UEFI update - extract .bin from .exe file and copy into FAT32 partition.
[https://askubuntu.com/questions/539120/how-to-perform-a-hp-bios-upgrade-with-only-ubuntu/1234098#1234098](https://askubuntu.com/questions/539120/how-to-perform-a-hp-bios-upgrade-with-only-ubuntu/1234098#1234098) & 
[https://h30434.www3.hp.com/t5/Notebooks-Archive-Read-Only/How-to-update-BIOS-on-Linux/m-p/5441775#M1205498](https://h30434.www3.hp.com/t5/Notebooks-Archive-Read-Only/How-to-update-BIOS-on-Linux/m-p/5441775#M1205498)

Also some have used FreeDOS.
HP freeDOS BIOS update
[https://ubuntuforums.org/showthread.php?t=2478456](https://ubuntuforums.org/showthread.php?t=2478456)

---

### Post by Yellow Pasque on 2023-11-13
You can use 7zip to unpack the sp<number>.exe, but in this case, all you get is another .exe (InsydeFlash.exe) and no .bin files. To get the .bin files, I had to run the program (which I don't think would run under FreeDOS, but don't quote me on that).
Maybe InsydeFlash.exe could be unpacked in some way without running it, but I couldn't figure it out.

---

### Post by sudodus on 2023-11-13
You can also create a Windows PE system in a USB drive boot from there and run the BIOS upgrading exe file.

See for example this link about WinPE for Windows 11: [learn.microsoft.com/en-us/windows-hardware/manufacture/desktop/winpe-intro?view=windows-11](https://learn.microsoft.com/en-us/windows-hardware/manufacture/desktop/winpe-intro?view=windows-11)

---

### Post by furtivehippo on 2023-12-03
Update... so I tried all of the suggestions here without success and, in desperation, decided to take the one course of action that was sure to  work - backed the machine up, wiped it and re-installed Windows.

Of course it didn't work, because the HP BIOS flashing software won't run while the machine is on battery power as a security measure... Catch 22.

Time for a new laptop, preferably one that doesn't say 'HP' on the lid.

Thanks for the help anyway.

---

### Post by oldfred on 2023-12-03
While most vendors do not specifically support Linux, if they have updates on fwupdate site then they indirectly do.
I would consider systems that allow Linux updates to firmware.

Devices using LVFS for firmware updates
[https://fwupd.org/lvfs/devicelist](https://fwupd.org/lvfs/devicelist)

[https://fwupd.org/](https://fwupd.org/)
Fwupd 1.8.5 Supports More USB4 Docks, New AMD SMU Firmware Version Plugin Sept 2022
[https://www.phoronix.com/news/Fwupd-1.8.5-Released](https://www.phoronix.com/news/Fwupd-1.8.5-Released)
Dell would not update with TPM on
[https://ubuntuforums.org/showthread.php?t=2487324](https://ubuntuforums.org/showthread.php?t=2487324)

---

### Post by Yellow Pasque on 2023-12-03
Why are you trying to flash the BIOS on battery power? No sane laptop is  going to let you do that whether it says 'HP' on the lid or not.

---

### Post by furtivehippo on 2023-12-04
> **Yellow Pasque said:**
> Why are you trying to flash the BIOS on battery power? No sane laptop is  going to let you do that whether it says 'HP' on the lid or not.

The reason for the BIOS update is that the laptop no longer works on mains power, only the battery. I was advised that this is caused by one of three things: the battery (replaced - no difference), the PSU (replaced - no difference) or BIOS needing an update... but no mains power = no update, hence the 'Catch 22' comment. 

If there *was* a way to over-ride this I'd be interested, as I have little to lose at this point.

---

### Post by Yellow Pasque on 2023-12-04
Looking through the changelog for the BIOS updates, I don't see anything related to battery/power.  All the updates in the past 2 years are just security updates and there are a couple older updates related to supporting newer versions of Windows, and a couple with a vague "Provide Updated BIOS" changelog.
Have you tried resetting the laptop in any way, like restoring BIOS defaults, or pulling the power and battery and holding the power button for 30 seconds?

---

### Post by furtivehippo on 2023-12-04
> **Yellow Pasque said:**
> Have you tried resetting the laptop in any way, like restoring BIOS defaults, or pulling the power and battery and holding the power button for 30 seconds?

'fraid so... neither had any effect unfortunately.

---

