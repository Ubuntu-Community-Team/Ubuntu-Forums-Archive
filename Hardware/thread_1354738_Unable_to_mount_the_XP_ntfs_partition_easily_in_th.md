---
title: "Unable to mount the XP ntfs partition easily in the netbook remix"
date: 2009-12-14
forum: Hardware
---

### Post by siddartha on 2009-12-14
The netbook remix comes with a very nice interface (probably the main reason why I bother to write of the so many issues with Ubuntu). Yet that interface comes with one major problem: clicking on the listed partition in the files/bookmarks section would lead to nothing. Only after starting up nautilus by clicking up on a bookmark, than clicking in nautilus (places) on the WinXp partition would lead to a demand of password and would result in the partition being mounted. Is there a work around to make it from the interface directly and without the intermediate steps?

---

### Post by dvlchd3 on 2009-12-14
Add a line in /etc/fstab.

Get the device number:
```

sudo fdisk -l

```
Look for something like /dev/hda1 that is an NTFS partition.

Make a folder to mount the drive to:
```

sudo mkdir /media/windows

```

Backup your fstab file:
```

sudo mv /etc/fstab /etc/fstab.bak

```

Now enter this command to add that device to the fstab file, and automount on startup.  (Make sure to change /dev/hdaX to match your device you got above)
```

sudo echo "/dev/hdaX /media/windows ntfs auto,noexec 0 0" >> /etc/fstab

```

To make sure it will mount on the next start, enter this command to mount everything listed in fstab:
```

sudo mount -a

```

---

### Post by siddartha on 2009-12-14
Hehehe
I can do that. Only I don't want to have it always mounted. So can it be done to mount if clicked?

---

### Post by siddartha on 2009-12-29
Never mind. I just mounted two external drives in the same interface. One was reported with its size. The other one was with the USB icon, yet reported the same size as the NTFS partition. There is a loooong way ahead before having this remix as a solution. Nice try.

---

