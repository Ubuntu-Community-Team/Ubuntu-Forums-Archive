---
title: "upgrading computer, new motherboard has UEFI"
date: 2020-05-07
forum: Hardware
---

### Post by darksidedude on 2020-05-07
hello all. I haven't upgraded my computer in awhile as I still have an old BIOS motherboard. the one i am getting for my new Ryzen processor is a UEFI board. 

I don't know much if anything about UEFI because it never applied to me. My question is will my MBR formated SSD just boot with the new board? or will I have to reinstall?


thanks for the hints and help as I join the UEFI future.

---

### Post by slickymaster on 2020-05-07
*Thread moved to **Hardware**.*

---

### Post by CelticWarrior on 2020-05-07
> **darksidedude said:**
> I don't know much if anything about UEFI because it never applied to me. My question is will my MBR formated SSD just boot with the new board? or will I have to reinstall?

The answer is: Maybe (with Legacy/CSM enabled and the proper boot order)
Of course, reinstalling gives the best results.

---

### Post by The Cog on 2020-05-07
I moved my disks and video card from an old and failing non-UEFI box to a borrowed newer box (while I wait for my Ryzen parts to arrive). The non-UEFI disk booted just fine except for one oddity: The console output rate was very slow (5 lines/second maybe) and clearly passing through a behind-the-scenes screen buffer somewhere. One of the boot messages (from the BIOS) gave a warning about having a non-uefi-supported video card. However, once Linux got started it fair screamed along. Made me realise how old my last PC was getting.

Long story short, yes it should boot just fine.

---

### Post by grahammechanical on 2020-05-07
There is something to watch out for: Video drivers. If you are using a proprietary video driver and you are going to upgrade the graphic card as well as the motherboard, then I suggest reverting to the open source video driver before taking the SSD out of the old motherboard set up.

Remember, At the Grub boot menu we can go into Advanced options for Ubuntu and select Recovery Mode and at that menu select Resume and Ubuntu will load without the standard video driver (open source or proprietary). The desktop will not look good but with a working desktop we can install the correct video driver.

You will want Software & Updates>Additional Drivers

Regards

---

### Post by kurt18947 on 2020-05-07
As others have said
1) disable any proprietary drivers
2) Be sure CSM is enabled on the new motherboard. 
3) It might be wise to disable/purge any PPAs. I don't have any PPAs that are in any way hardware related but it may still be a good idea to disable/purge, move the disk(s) then re-enable PPAs.

Before you do anything though, be sure you have backups of your data that you know you can restore.

---

