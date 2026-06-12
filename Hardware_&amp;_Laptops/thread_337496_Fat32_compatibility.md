---
title: "Fat32 compatibility"
date: 2007-01-13
forum: Hardware &amp; Laptops
---

### Post by emacdonald on 2007-01-13
I have various Ubuntu PC's configured for my children to use. They also have USB style MP3 players, which they want to be able to copy tracks from and to. But the issue is that the FAT32 formatted players generally do not cope very well with these files being transferred from the Ubuntu PC. Symptoms include:-

1.The MP3 player directories can become corrupted.
2. If a file is deleted, Ubuntu creates a delete directory, which turns out to be inaccessible.
3. The only way to recover the MP3 Player is to plug it back into the windows machine, & reformat in FAT32, and reload the tracks!.

So in order for the guys to use their MP3 players easily they are reverting back to using windows, which is what I was trying to avoid.

Does anybody know how to drag and drop & delete files on FAT32 devices without compromising the device?

---

### Post by studiesrule on 2007-01-13
Ubuntu has full compatability with FAT32. I have a USB device aswell, that is FAT32 formatted, hoever I don't face any problems with it. IPOD's also have no interfacing problem. Perhaps Ubuntu adds a few files (a .Trash folder for example) that may interfere with the MP3 player.  Just try and delete these folders before you remove the usbdisk . Also remember to umount the disk before removing it, because that may screw up the data stored.

---

### Post by louistan3 on 2007-01-13
yeh.. i think you or your children might've forgotten to unmount the mp3 players before taking them out.. which would mean corrupted data.. i thnk.. :)

---

