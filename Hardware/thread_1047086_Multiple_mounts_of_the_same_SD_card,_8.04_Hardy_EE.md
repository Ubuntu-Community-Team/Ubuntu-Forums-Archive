---
title: "Multiple mounts of the same SD card, 8.04 Hardy EEE701"
date: 2009-01-22
forum: Hardware
---

### Post by PressureGotTheDropOnYou on 2009-01-22
This problem is quite confusing to me because it is so intermittent and inconsistent. It only really happens after a resuming from suspend that I know of, but it doesn't happen every time I do that. Initially when I installed Hardy on to my EEE I had mounting problems with SD cards but I quickly found the solution to this in several forums which was to comment out a certain line in fstab and ever since then it's worked beautifully, though strangely the icon for my SD card is a hard drive so it doesn't seem to know or care what type of volume it is but that's really all by the by.

Anyway, on some unfortunate occasions, resuming from a suspend will cause the card to be mounted again and so I will have 2 icons for the same volume, this minor annoyance snowballed to a much greater one when, I began downloading a torrent. I told KTorrent to download to the card as I've very little space left on my EEE's flash drives and began downloading. The next day I restarted the computer and attempting to resume the as yet incomplete (see my post about unwanted system suspension right in the middle of downloads >:( ) download. Due to the absence of the second unnecessary mount 'disk-1' the torrent could not resume as it was missing files from the phantom 'disk-1' mount even though 'disk' was there and had these files as both 'disks' were one and the same. As there was no option to manually point to these files, nor would I be sure where to find them anyway as they were technical files pertaining to the torrent itself not the content I was downloading - I had to abandon my entire download.

Anyone know how to get Ubuntu, to recognise that disk and disk-1 are the same thing?

---

### Post by PressureGotTheDropOnYou on 2009-01-22
BUMP-ed

---

