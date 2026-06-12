---
title: "USB 3 external NTFS-disk has a few bad sectors.."
date: 2013-04-10
forum: Hardware
---

### Post by Azyx on 2013-04-10
Hi.
I had some problem to read and even copy files from an 2.0TB USB3. I get like 'in-out error' and the copy stop and nautilus hangs. The SMART-test shows an error.

Under Disk utility S.M.A.R.T saying there are some bad sectors...

How can I fix a  NTFS-system in Ubuntu 12.04LTS?

/Cheers

---

### Post by ahallubuntu on 2013-04-10
~

---

### Post by Azyx on 2013-04-10
> **ahallubuntu said:**
> What kind of "bad sectors" are they?  Reallocated sectors are not catastrophic unless there are a lot of them.  Reallocated sectors are sectors that already failed and were marked "do not use" by the drive firmware and replaced with spare sectors on the drive.  

Pending sectors are really bad though - means some sectors (presumably within files you were trying to access) could not be read.

You can use a Windows disc to run the Windows chkdsk command to try to fix the NTFS filesystem.  I would not recommend trying Linux-based tools to repair NTFS filesystems.  You can always download a Windows disc legally and free.  I think Softpedia still has ISO images of WIndows 7 can you download.

You can't "repair" failed sectors.  If they are pending, you can try clearing the entire drive (after copying files you need) and erasing it with a tool like Darik's Boot and Nuke (DBAN), then seeing if the pending sectors still persist according to S.M.A.R.T.  If there are still pending sectors after clearing it, replace the drive.  You usually have to replace a drive that has pending sectors, though.

Just now i make a S.M.A.R.T self test in a tool in Disk Utilities, and that takes a lot of times (seems to take several hours according to the screen shot below. I have a W7 on a vbox, so I can mount then there, but I don't know if I have a usb 3 driver to windows? Should probably use a usb 2 port instead...Anyway, after the test I should try chkdisk under windows 7?

Below there are a screen-shot of the error message in the S.M.A.R.T module in Disk-Utility

---

### Post by |{urse on 2013-04-10
-also- You can run a program called HDD Regenerator which will usually fix them for good if there are only a few.

You need to download and burn Hiren's bootdisc and boot to it, if you get the right version (cough cough: [COLOR=#000000][FONT=Verdana]**Hiren's Boot 15.1 Rebuild by DLC v2.0**[/FONT][/COLOR]) it should be there under Hard Disk Tools in the dos menu.

Sorry I can't provide you a link to Hiren's boot disc but you can find a .torrent pretty easily if you look in the right places.

---

### Post by Azyx on 2013-04-12
Have now saved files from the disk. I think it was the SATA-USB3 adapter in externa disk that messed up the HDD, cos it some times did not ger mounted, before there was any errors on the disk.

The original [http://www.hiren.info/pages/bootcd](http://www.hiren.info/pages/bootcd) have a tool called:

**HDAT2 4.9B1** *The main function is testing and repair  (regenerates) bad sectors for detected devices. A freeware alternative  of* **HDD Regenerator.**

Have you any bad experience of [B]HDAT2 4.9B1 ?

[COLOR=#ffd700]/Cheers[/COLOR]
[/B]

---

### Post by |{urse on 2013-04-16
Sure. HDAT does the same thing ^^

---

### Post by Azyx on 2013-04-16
> **|{urse said:**
> Sure. HDAT does the same thing ^^

It worked with, remove partition and  'normal' full reformat. No bad sectors :)

But thanks good to now in the future.

---

