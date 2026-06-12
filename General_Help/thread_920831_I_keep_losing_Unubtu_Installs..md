---
title: "I keep losing Unubtu Installs."
date: 2008-09-15
forum: General Help
---

### Post by rmjohnson144 on 2008-09-15
I have 6 Hard drives installed on my computer and several Ubuntu Installs as well as a Vista x64 install.  anyway, I seem to be losing my hard drives all the time.  not sure if it is this last ubuntu working install or windows or what. 

My History of installs:

I install Ubuntu on my Jmicron controller in IDE mode.  all is fine.  I install Vista HP x64 on my 2 drive RAID 0 and all is well.

I then have issues with my eSATA drive and RAID 0 in Ubuntu.  Then I install Ubuntu in hopes a fresh install will find everything from start and all work.  all works except my RAID 0 drive and this version of Ubuntu created a new GRUB file and put all OSes on creating a huge multi-boot menu I didn't want.  

I undo my Vista RAID and reinstall Vista on a single drive (after failing to get raid working in Ubuntu) then Install Ubuntu 32-bit to run my real player files as 64-bit Ubuntu wouldn't support real player. This time it didn't create a new Ubuntu menu(but it seems to wait for it as it never errors or times out) and added this one to the main multi-boot menu (yes, I set the drive as first boot, but it still used the grub from the other drive)

Then the other day I lose my grub menu completely and errors out(error 15 and was about the time I added my extra 1TB backup drive).  Luckily the Jmicron install has it's GRUB menu still intact and all is fine.  Then after switch from Vista the other day I find my Ubuntu now takes forever to load after giving me several hard drive failures(boot time now takes 5 minutes.  I get some sort of revalidation errors.). and I lose ALL nhard drives except my eSATA drive.  I even added a 6th 1TB hard drive a couple weeks ago for data storage and it isn't recognized either.

Yesterday I fired up Vista and it sees everything fine after installing a EXT3 file program to allow me to read Linux partitions.

so, does anyone know why my Ubuntu installs keep getting corrupted?  Or why Linux won't read my hard drives, but Vista will?

-=Mark=-

---

### Post by Sef on 2008-09-15
>  so, does anyone know why my Ubuntu installs keep getting corrupted?  Or why Linux won't read my hard drives, but Vista will?

I would redownload the iso.

1) Don't forget to md5sum the download.

2) Burn it at 4x or less.

3) Possibly your disk is bad.

4) Check the cd by going down to 'check disk for errors' instead of running the live cd or installing.

5) Try using the alternate cd instead.

---

### Post by rmjohnson144 on 2008-09-15
> **Sef said:**
> I would redownload the iso.

1) Don't forget to md5sum the download.

2) Burn it at 4x or less.

3) Possibly your disk is bad.

4) Check the cd by going down to 'check disk for errors' instead of running the live cd or installing.

5) Try using the alternate cd instead.

Considering it has been working fine for a couple of months now, then I'd assume it is fine.

I mean I can reinstall and everything will probably be fine, it just won't tell me what's going on.

anyway, I went to recobery mode earlier and it gave more extensive error listings and when I rebooted I stopped getting the error.  I continued on and installed my ATI drivers and messed itup and went back into recivery mode and now I'm getting those errors again.

ata4.00: qc timeout (cmd 0x27)
failed to read native max address (err_mask=0x4)
revalidation failed (errrno=-5)

it repeats this over and over covering all my drives.

Then afterwards I get something to recover complete this time and the drives all show up at the desktop.  atleast they did when I had a desktop.  I've installed the ATI drivers and now I just get a white screen with a cursor and nothing else.  but that's another issue.

Thanks for the advice.
-=Mark=-

---

### Post by whizbaby on 2008-09-15
If you have multiple OSs its not a bad idead to have a separate /boot partition for GRUBs use. At least multiple ubuntus will less confuse you :)

---

### Post by rmjohnson144 on 2008-09-16
> **whizbaby said:**
> If you have multiple OSs its not a bad idead to have a separate /boot partition for GRUBs use. At least multiple ubuntus will less confuse you :)

considering I have a set of 4 150gb Raptors it would probably help to have the multiboot menu.  I just hate having to deal with the screen every boot.  I like the Windows version better in that it selects the first boot drive as the drive for the boot menu.  I see Ubuntu/grub chooses the first or closest to the first drive in device " order.  ie. sata port 0 device 0(master).  I found that out after giving up on the boot order and removed all the raptors and installed mty 1TB and 500GB drive and went to install Ubuntu on my 500GB drive, but grub went to the 1tb drive and it wouldn't boot.  I then switched my first boot device as the 1tb and then grub gave me a error 17 and wouldn't boot either.  Right now I have 500GB as only drive connected and Ubuntu installed without a hitch - lol

I think I also found out why it was messing up on the drive recognition.  I had my system overclocked and noticed when reconfiguring my new hard drive setup with the aptors gone that a lot of my setting were wrong.  sure enough my whole bios was reset probably because my overclock failed and was reset to use system defaults.  I'm too lazy to reinstall those drives for a test as they are a pain to hook back up in my P182 case now that everything is uninstalled that i didn't think I needed anymore.  But I'm at least 99.999% positive it was the case as all my drives were in IDE mode and only that one drive was in IDE mode beforehand.  the rest were in RAID/AHCI mode for extra speed, assuming Ubuntu can take advatage of the AHCI command sets.

Thanks again everyone for the help.
-=Mark=-

---

### Post by TenPlus1 on 2008-09-16
Why not install Windows first then use wubu.exe on the Ubuntu CD to install, this'll place Ubuntu on your windows partition and add an entry to the windows boot menu and both OS' still work seperately and fine :)

---

