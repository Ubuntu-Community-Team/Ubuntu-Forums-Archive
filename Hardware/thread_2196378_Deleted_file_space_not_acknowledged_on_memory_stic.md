---
title: "Deleted file space not acknowledged on memory stick"
date: 2013-12-29
forum: Hardware
---

### Post by Alan_Dean on 2013-12-29
I use Ubuntu 12.04 LTS on my laptop and 13.10 on my PC. I have several memory sticks all formatted using gparted to fat32. When a stick gets full I delete the files (mostly avi video files that play back on the TV) to make more space. Although the files are deleted I am unable to add more files - I am advised that the drive is full and looking on the properties tab it still shows that the memory stick is still 100% full. Is there a reason why the space released by deleted files is not acknowledged?

Thank you

Alan

---

### Post by vanadium on 2013-12-29
The files are not deleted immediately, but moved to a Trash folder, in case you want to change your mind. In order to fully delete the file, empty the tash bin.

If you immediately want to delete a file while bypassing the trash, you can do so with Shift+delete.

---

### Post by ajgreeny on 2013-12-29
The trash folder is also a hidden folder so you will need to use Ctrl+H to see it in nautilus or other file manager.

---

### Post by tripp98 on 2013-12-29
With the usb drive plugged in, empty trash.  it will then free empty space.

---

### Post by ajgreeny on 2013-12-29
> **tripp98 said:**
> With the usb drive plugged in, empty trash.  it will then free empty space.
That will only delete the user trash, not any trash in the flash drive, as far as I'm aware.

---

### Post by Alan_Dean on 2013-12-29
Thanks to all. I deleted and then emptied rubbish bin and this was acknowledged in the properties windows. Problem solved thanks

Alan

---

