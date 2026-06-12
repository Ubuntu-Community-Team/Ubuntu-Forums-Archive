---
title: "Umount/eject trouble with USB HDD"
date: 2007-06-07
forum: Hardware &amp; Laptops
---

### Post by carpetn on 2007-06-07
Running Feisty Fawn on a Lenovo 3000 N100. Problem with Maxtor Personal Storage 3100 USB 80GB external HDD.

When I connect my Maxtor external HDD and try to unmount/eject it I get a strange result with my Gnome desktop. When I right-click one of the volumes in my file browser (there are three: Linux, FAT, and NTFS) and choose "unmount," I get this error message:

"There is data that needs to be written to the device Maxtor 6 Y080L0 before it can be removed. Please do not remove the media or disconnect the drive."

I also get a warning box: "Cannot eject volume."

Also the Maxtor cranks for a minute and opens three additional file browsers, one for each of the volumes. But nothing else happens. Nothing is getting written and the system just sits at that stage.

If I go to a terminal and unmount them ("sudo umount /media/disk", for example), they still show in my file browser as if waiting to be ejected, and I get the same error message when I right click and chose "eject."

Does anyone what's happening here? Do I have to use the eject command or is that only relevant for CDROM and floppy drives? Can I just pull the USB plug once the three volumes have been umounted? I've tried that and don't seem to have a problem when I remount the volumes. I've also tried shutting down the computer with the Maxtor plugged in. That doesn't seem to make it behave differently when I restart it.

It's hard to remember, for sure, but I may have lost power to the Maxtor at one point, which could be connected to this problem?


Thanks.
Carpetn

---

### Post by louistan3 on 2007-06-07
i think there's a bug with the feisty unmount tool...

this happens to me too.. 

what i do for now is use the command line to unmount it which works..

```
sudo umount <diskVolumetobeUnmounted>
```

in my case i just use /media/disk* so it unmounts everything that is in /media directory with the name disk on it... 

hope this helps.. 

:)

EDIT: what do you mean by "they are still in the file browser"? it might just be the directories... or you might be unmounting the wrong diskVolume..

---

