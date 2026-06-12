---
title: "NTFS x ExFAT on 2022"
date: 2022-03-16
forum: Hardware
---

### Post by hikariws on 2022-03-16
Hello All!


I use some USB HDs permanently connected on my server, I had some odd issue that made Ubuntu lose USB driver and all USB devices became unavailable. The driver was back after reboot, but I was unable to connect the HDs. For safety I disconnected them and am verifying them on a PC with Windows, at least 1 of them had its NTFS corrupted and Windows was unable to mount, luckly I was able to use a recovery tool to recover 90% of its content.


I made a full surface test on the faulty HD, reformatted it with ExFAT and Ubuntu mounted it. I set fstab to mount as readonly.


So I'm considering using ExFAT instead of NTFS because it's simpler. I'm hoping this will reduce risk of corrupting the file system.


A few years ago I had read that ExFAT driver wasn't stable and NTFS was a better choice, but now I had read that M$ was open sourcing ExFAT and support was better.


How is it now? Is it reliable to use ExFAT? Specially if I mount them as readonly. I don't need any permission features on them.

---

### Post by TheFu on 2022-03-16
NTFS and FAT-whatever should only be used when there isn't any other choice on a Linux system. Always go with native Linux file systems unless there is non-computer hardware device which requires one of those file systems
or
if, for some reason, you think that physically connecting the HDD to a Windows PC is required.  If only a network connection is required from the Linux system, do not use NTFS or FAT-whatever.

Use NTFS over exFAT for all SSDs and spinning HDDs that much be physically attached to MS-Windows.  NTFS is a journaling file system, which is 10000000x safer than any non-journaling  file system. The fact that chkdsk wasn't used to let Windows use the journal to save any partially written data is the issue, I think.  Journaled file systems are amazing, when compared to non-journaled file systems. They can survive all sorts of terrible failures with minimal effort.

exFAT should be used on slow, flash media only, that doesn't support a better file system. Nothing else.
The native Linux solution is f2fs. Use that on SDcards and flash USB "thumb/pen" drives if only Linux will be used with the storage. Otherwise, use exFAT for those (if the devices it gets inserted into support exFAT).  My cameras and cell phones don't support exFAT, so I'm forced to use FAT32 still on those.  I'd much rather use f2fs, especially on Android. Then the OS storage and external storage can be used interchangeably, which would be very nice.

---

