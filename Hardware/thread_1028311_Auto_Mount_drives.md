---
title: "Auto Mount drives"
date: 2009-01-02
forum: Hardware
---

### Post by Chamillionaire2 on 2009-01-02
Hello.

OK Basically i find it a little bit of a pain to keep going to the drive and manully mounting it, is there a way i can make it auto mount at startup?

Thanks Bye.

---

### Post by ibutho on 2009-01-02
You can put an entry in /etc/fstab for a device that you want to be automatically mounted at boot time.

---

### Post by Chamillionaire2 on 2009-01-02
> **ibutho said:**
> You can put an entry in /etc/fstab for a device that you want to be automatically mounted at boot time.

Im a complete and utter noob with linux, what do i put for it to boot?

name of the drive is "32.2 GB Media"

---

### Post by ajgreeny on 2009-01-02
Below are some examples of lines to add to fstab to automount various different filetype partitions.  Change partition info (eg /dev/hdb1, etc) and path (eg /media/xxxx) to suit the situation, and make sure either that it exists or you have made the mount point first.

Automount linux partition.  Add line to /etc/fstab:-
/dev/hdb1       /media/linux   ext3    defaults  0  1

Manual mount linux:-
sudo mount /dev/hdb1       /media/linux/ -t ext3

Automount fat32 windows.  Add line to /etc/fstab:-
/dev/hda1       /media/windows  vfat    iocharset=utf8,umask=000   0       0

Manual mount fat32 windows:-
sudo mount /dev/hda1 /media/windows/ -t vfat -o iocharset=utf8,umask=000

Automount ntfs windows.  Add line to /etc/fstab:-
/dev/hda1       /media/windows  ntfs    nls=utf8,umask=0222 0       0

Manual mount ntfs windows:-
sudo mount /dev/hda1 /media/windows/ -t ntfs -o nls=utf8,umask=0222

Mount an iso file:-
sudo  mount -o loop -t iso9660 path/to/file.iso /mount/path

EDIT:
PS:  Another very useful thing is to use the disk mounter applet in your taskbar.  Right click in an empty space and use the **Add to panel** option.  It's what I use as I don't want to mount drives I almost never use or need every time I boot.

---

### Post by 1jackjack on 2009-01-06
good reply! i would add that the preferred way to identify partitions is with their UUID, which you can get with the command sudo blkid. then you could add something like this to your /etc/fstab

UUID=1ff05f7f-9433-4b91-b84d-a7c2320a739d /home/jack/music ext3 defaults 0 0

(note: i think that last number denotes the priority of the check on boot, and for most partitions people just leave it as 0). anway, i've got a slight niggle: when i automount my music partition with this line, it works, but the partition ALSO appears as an icon on my desktop, which is just annoying... anyone know a way to prevent this?

cheers,
jack

---

### Post by uidb4056 on 2009-01-06
> **1jackjack said:**
> good reply! i would add that the preferred way to identify partitions is with their UUID, which you can get with the command sudo blkid. then you could add something like this to your /etc/fstab

UUID=1ff05f7f-9433-4b91-b84d-a7c2320a739d /home/jack/music ext3 defaults 0 0

(note: i think that last number denotes the priority of the check on boot, and for most partitions people just leave it as 0). anway, i've got a slight niggle: when i automount my music partition with this line, it works, but the partition ALSO appears as an icon on my desktop, which is just annoying... anyone know a way to prevent this?

cheers,
jack

You can look at [http://godawski.oxyhost.com/unvisiblefiles.html](http://godawski.oxyhost.com/unvisiblefiles.html) it could help you.:D

---

