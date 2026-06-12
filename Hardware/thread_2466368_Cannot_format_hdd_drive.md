---
title: "Cannot format hdd drive"
date: 2021-08-26
forum: Hardware
---

### Post by joerack2 on 2021-08-26
I'm having some trouble with external storage devices.
Found this 750gb hdd and tried to format it with gparted and it errors out, tried with ubuntu disk, and no luck.
Gparted says it needed to create a partition table, did so, and it crashed, and had to remove the usb cable.

Inserted in a windows pc, used system disk management, and it was ready in seconds with ntfs.
Tested the hdd with crystal disk and it's working perfectly.

What am I missing here? The only reason I haven't remove my windows partition is to format drives and use rufus (balena etcher also is giving me woes)

---

### Post by Autodave on 2021-08-26
What error(s) did you get?  What were you trying to format it to?

---

### Post by sudodus on 2021-08-26
I suggest that you

1. check the external drive according to [this link](https://askubuntu.com/questions/972978/fsck-reports-that-filesystem-still-has-errors/972983#972983): Check the S.M.A.R.T. information about the hardware (and check/repair the file system if ext4).

2. Then you can wipe the first mibibyte (overwrite the head end with zeros) and try again with gparted.

3. If still problems you can analyze it according to [this link](https://askubuntu.com/questions/144852/cant-format-my-usb-drive-i-have-already-tried-with-mkdosfs-and-gparted/933035#933035), and I think also make it work with Ubuntu.

---

### Post by joerack2 on 2021-08-29
thanks for the answers, I solved it the end plugging the mono usb3 cable to the back of the motherboard.
Must have had something weird like not enough current to the front ports

---

