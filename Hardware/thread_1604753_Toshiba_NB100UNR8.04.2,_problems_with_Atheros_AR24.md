---
title: "Toshiba NB100/UNR8.04.2, problems with Atheros AR242x wifi driver"
date: 2010-10-24
forum: Hardware
---

### Post by Magnificent 7 on 2010-10-24
This is a nice little netbook, which has been spoiled for me as I have been fighting with it ever since applying the first of several updates back in May. After these various updates GRUB shows three 8.04.2 kernels, 2.6.24-19-lpia, 2.6.24-24-lpia and 2.6.24-27-lpia, along with their recovery variants.

After the -24 update sound was broken. It did not respond to various remedies suggested in forums by others for whom the update had also broken sound. The problem continued with -27, although I could see that a linux-image-lpia update was held back in the update manager, so there was hope at some point down the line.

Coming back to the netbook this month and applying further updates, linux-image-lpia was now available among a bunch of other updates which fixed the sound but then broke the wifi driver in -24 and -27. This most recent update was applied from the 2.6.24-19-lpia kernel, as a BIOS update carried out in a previous attempt to restore sound resulted in X not loading correctly under -24 or -27, and only sluggishly under -19. Following a tip to put the HDD into 'compatibility mode' made -19 just useable enough to apply the update.

It's unclear whether applying an update from such an early kernel was the cause of the wifi problem but checking dmesg it could be seen that the ath_pci and some other ath_* modules connected with the Atheros AR242x driver were not loading and instead reporting 'unknown symbols'. Looking at the hardware drivers, the closed Atheros wifi card driver was loaded but "not in use".

After more reading of forums, I followed a tip to remove the linux-restricted-modules-lpia, in the hope that a new native 'ath5k' driver would take control of the wifi card from the Madwifi ath_pci driver. Unfortunately it did not, and trying to restore the just-deleted linux-restricted-modules-lpia did not work. Thus wifi would not work even under the -19 kernel any more. I've since discovered that ath5k would not have been delivered by these updates but is only available via backports.

So in summary after applying all the 8.04.2 updates I have working sound but no wifi and the options appear to be

a) struggle on and wait a further five months in the hope that a future update restores the restricted modules and the wifi problems have been fixed by then

b) go through the pain and learning curve of creating a bootable USB, transferring the supplied CD recovery image to this and rebuilding, in the assumption that directly applying updates to a fresh installation will make all the problems go away

c) sacrifice the Toshiba branding on their installed version of 8.04.2 and install an up-to-date netbook remix, in the hope that this will have the correct and updated native drivers for everything 'out of the box'.

I'm posting here to find out what others' experience has been of the Tosh NB100 with UNR, and which course of action they (or other Ubuntu/Netbook users) would recommend.

---

### Post by Magnificent 7 on 2010-10-28
Any input greatly appreciated.

---

