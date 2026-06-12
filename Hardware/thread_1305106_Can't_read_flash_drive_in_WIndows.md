---
title: "Can't read flash drive in WIndows"
date: 2009-10-29
forum: Hardware
---

### Post by thirdI on 2009-10-29
I have 2 PC's (Vista and Ubuntu) and a Mac. I reformatted my flash drive to hfs+ so that it can read on my Mac. When I reformatted it again back to ntfs, Windows recognizes it in the disk management utility but it will not mount the drive. I tried the option to change the drive letter and path with the utility but it keeps giving me an error saying that the window needs to be refreshed, the utility needs to be restarted or the computer needs to reboot. I did all of those and end up with the same error. Any suggestions?

---

### Post by coffeecat on 2009-10-29
How did you reformat it? Did you use Gparted in Linux or some Windows utility? Just theorising here, but if you used Gparted, it's possible you've got yourself an NTFS partition with an Apple partition table. Which would be odd and, tbh, I don't even know if this is possible. But it might explain the problem Windows is having.

Whatever - try this. Use Gparted from the live CD, or install it to your Ubuntu installation if you haven't done so already. Plug the flash drive in and open Gparted. Make sure Gparted is showing your flash drive contents in the main screen and go to Device > Create Partition Table. Under "Advanced" make sure it is showing "msdos" as the partition table type - that's the default anyway. Click on "Create" and you will end up with a drive entirely unallocated which you can now re-format.

By the way, are you sure you want a flash drive formatted with a journalling filesystem? Which is what NTFS is. It'll wear out quicker than with FAT32.

---

### Post by thirdI on 2009-10-30
> **coffeecat said:**
> How did you reformat it? Did you use Gparted in Linux or some Windows utility? Just theorising here, but if you used Gparted, it's possible you've got yourself an NTFS partition with an Apple partition table. Which would be odd and, tbh, I don't even know if this is possible. But it might explain the problem Windows is having.

Whatever - try this. Use Gparted from the live CD, or install it to your Ubuntu installation if you haven't done so already. Plug the flash drive in and open Gparted. Make sure Gparted is showing your flash drive contents in the main screen and go to Device > Create Partition Table. Under "Advanced" make sure it is showing "msdos" as the partition table type - that's the default anyway. Click on "Create" and you will end up with a drive entirely unallocated which you can now re-format.

By the way, are you sure you want a flash drive formatted with a journalling filesystem? Which is what NTFS is. It'll wear out quicker than with FAT32.

Thanks for the quick response. You were absolutely correct: the partition table was set up in GUID format and Gparted did the trick. The only reason I even formatted the flash drive into hfs+ was so that I could use it as a second hard drive on my Mac in order to install the the updated Snow Leopard OS. But all is well now; thank you very much!

---

### Post by coffeecat on 2009-10-30
Glad it's sorted and glad my poor tired old brain can come up with something useful on occasion. :wink:

Actually, that's useful to me. I've got a flash drive which I formatted to hfs+ in MacOS, and which I'll probably reformat sometime. I'll try to remember to re-create the partition table first.

---

### Post by John Bean on 2009-10-30
> **coffeecat said:**
> Actually, that's useful to me.
And me. I don't have a mac but I've had flash disks handed to me "to fix" and experienced this very problem. Never thought to use that Gparted option though (I didn't even know it was there!) and ended up zapping the whole disk  with dd and starting again from scratch.

---

