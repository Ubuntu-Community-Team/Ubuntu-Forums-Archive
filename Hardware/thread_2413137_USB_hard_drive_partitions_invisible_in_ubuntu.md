---
title: "USB hard drive partitions invisible in ubuntu"
date: 2019-02-21
forum: Hardware
---

### Post by autogod-cf on 2019-02-21
Hi there.

I have a USB hard drive (data drive in an enclosure) that refuses to display any partitions when connected to my Ubuntu server box on 18.04.1, or my laptop on 18.10.

It is detected by lsusb, and shows in the output from ls -l /Dec/disk/by-id, but does not show any of its partitions to Ubuntu.

It is detected an accessible to my windows machines (the laptop is dual boot, and my main machine). I have tried rebooting, disconnecting and reconnecting the drive, and testdisk, but it does not show under testdisk or fdisk -l.

Any advice would be greatly appreciated, since it's the laptop's old drive, and there are some files on the ext4 partition that I need to access.

---

### Post by yancek on 2019-02-21
You neglected to mention what filesystem you have on these partitions which is probably significant.  If they are detected on windows then I expect you have a windows filesystem on them as a default windows system will not be able to do much more than show them in Disk Mgmt or similar tools.  You won't be able to access to read/write a LInux filesystem from a default windows system.  So the most likely situation is that you have windows filesystem and you have left them hibernated.  That is the default on current windows systems and if you do turn it off, it will be turned on again on some windows updates and you will not be notified that it is being done.  If turning off hibernation doesn't work, some more details on these partitions would be useful.

---

### Post by autogod-cf on 2019-02-22
> **yancek said:**
> You neglected to mention what filesystem you have on these partitions which is probably significant.  If they are detected on windows then I expect you have a windows filesystem on them as a default windows system will not be able to do much more than show them in Disk Mgmt or similar tools.  You won't be able to access to read/write a LInux filesystem from a default windows system.  So the most likely situation is that you have windows filesystem and you have left them hibernated.  That is the default on current windows systems and if you do turn it off, it will be turned on again on some windows updates and you will not be notified that it is being done.  If turning off hibernation doesn't work, some more details on these partitions would be useful.

the drive has multiple partitions, one of them is a windows ntfs partition, this is accessible on windows, as are the recovery partitions. the ext4 partition is visible in windows disk management and inaccessible (just as it should be). the data i need is located on the ext4 partition, and of course this is not easily accessible on windows.

however, NONE of the partition are shown in ubuntu - they dont show in fdisk -l, gparted, testdisk or any other tool - except with "ls -l /dev/disk/by-id/"

this was being used as a temporary storage drive on my server for some time. i have also tried changing the usb enclosure and this hasnt helped either

---

### Post by ajgreeny on 2019-02-22
Do you remember if the partitions were primary or logical, and if logical, was the ntfs partition enclosed within the extended wrapper along with the ext4 partition?

---

### Post by autogod-cf on 2019-02-22
> **ajgreeny said:**
> Do you remember if the partitions were primary or logical, and if logical, was the ntfs partition enclosed within the extended wrapper along with the ext4 partition?

i dont remember whether it was primary, or indeed the layout that it shipped with (it was originally in a lenovo laptop, with recovery and such), but i have managed to get a screenshot from windows disk management and diskpart:

[ATTACH=CONFIG]282622[/ATTACH] [ATTACH=CONFIG]282623[/ATTACH]

using diskinternals linux reader, i have confirmed that the files and partitions are there, and accessible

EDIT: i still need to get the partitions back and figure out what on earth happened to cause this issue, and i currently dont have another drive to copy the files to

---

