---
title: "Formatting SD cards"
date: 2022-04-22
forum: Hardware
---

### Post by stevenfriedrich-twc.com on 2022-04-22
Few in the technical community are aware that SD cards, as well as  microSD cards should NEVER be formatted by OSes, like Linux or Windows.   If you want to know why, visit sdcard.org.
I just bought a Raspberry Pi4 B.  I already had a Lexar 256GB microSD  card.  I had been formatting it with Windows 11.  I tried to use  Raspberry's Imager to copy Raspberry 64-bit OS to it.  It failed to  verify.  I tried again under Linux too.
I had previously downloaded the SD formatter from sdcard.org.  I formatted the 256GB microSD with that.
Now Windows11 and Linux don't recognize the device at all.
This will be discovered by the Linux community at large as more people buy 256GB microSDs.

---

### Post by TheFu on 2022-04-23
Odd, I've been formatting microSD devices for 6+ years, since I stopped buying any other type of portable storage. Never had any issues.  But be certain you select the file system required for your needs.  I don't use Windows with real storage anymore, so my requirements are purely for device compatibility or my desires.

The rules for which file system to choose are dependent on the devices that the storage must be physically inserted.

My PnS cameras only support FAT32, so I don't have any choice about that.

My 4 yr old smartphone only supports ext4 or FAT32, no exFAT. In general, I avoid journaled file systems on flash media, so FAT32 it is.  FAT32 is the 'least good' choice.

I wish my phone supported f2fs like many other phones do, then I'd select that.  f2fs is a Linux compatible, low-write, file system that has all the Unix permissions support we expect.  Great for extra storage on a Raspberry Pi, for example.

I have a video recording device that only supports NTFS or FAT32. It has a USB connection, so for spinning HDDs it will have NTFS as the file system and for USB Flash storage, it gets FAT32.

f2fs isn't pre-installed. Just add the **f2fs-tools** package to any Linux to use it.  I don't know how easy it is to allow booting from f2fs. I've never tried.

exFAT is what I'd use for a modern Win7 or later need along with Linux.  I think exFAT support has been added by default to Ubuntu desktops for the last 2 yrs, so it should be there. If not, install the **exfat-utils** package. Again, this is only if the storage will be physically inserted into Windows or a camera or phone that supports exFAT.

In summary, my order of preference for file systems used by flash storage (sd, microsd, usb) are:
[LIST=1]
[*]f2fs - if linux only AND the android device supports f2fs. Not all android devices do.
[*]exfat - if Linux AND Windows AND the android/camera devices support exfat. I think more modern cameras, phones do.
[*]fat32 - if there's no other choice.  FAT32 really shouldn't be used on devices larger than 64G. There are real scaling problems, since block sizes grow. 
[/LIST]

Don't use FAT32 on 256G flash storage. That's just a terrible idea and Windows added an arbitrary limit on the size of FAT32 supported in the WinXP days to force exfat use.  exfat is better than fat32. It supports larger file systems and was designed for use on flash media.

Wikipedia has a number of articles about different file systems that some my find interesting.

You may notice that ext2/3/4, xfs, zfs, btrfs, and NTFS really aren't suggested for flash storage.  I suppose that ext2 would be fine, since it isn't journaled, but all the others are (or CoW), which means that they may write up to 2x more to the storage. Journaling is a data corruption mitigation feature, but it is bad for flash storage with very limited writes per block.

---

### Post by him610 on 2022-04-23
> microSD cards should NEVER be formatted by OSes, like Linux or Windows
Really? How would you (re)format one? Please suggest an alternative method.

This is about sdcard formatter from sdcard.org...
Re: [https://www.sdcard.org/downloads/formatter/faq/#faq04]("https://www.sdcard.org/downloads/formatter/faq/#faq04")

> What Operating Systems are supported?
Our Formatter tool can only be executed on systems running Windows and Mac OS X/ macOS versions. However, cards formatted by the SDA’s **SD Memory Card Formatter** can be used on devices running other operating systems such as Linux, Android and across other CE offerings. Just note the [COLOR="#FF0000"]actual card formatting process must take place on either a Windows or Mac OS-based system[/COLOR] in order to format your media for peak performance.

Don't think I will purchase a Mac or Windows machine just to reformat SD cards.
I normally used *mkusb* to (re)format SD cards and USB sticks for several years now with no issues.

---

