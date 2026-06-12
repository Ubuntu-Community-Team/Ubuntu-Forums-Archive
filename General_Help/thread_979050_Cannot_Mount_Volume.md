---
title: "Cannot Mount Volume"
date: 2008-11-11
forum: General Help
---

### Post by relaxedcrazyman on 2008-11-11
Cannot Mount Volume
You are not privileged to mount the volume 'CORSAIR'.


DBus error org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.


i keep getting these errors whenever i plug in my newly formatted to NTFS (in vista) thumb drive. i also tried to mount it in Storage Device Manager. It just does not want to mount.

I have read so many threads about people having problems mounting drives, but could not find a solution. Plus i am a super noober to ubuntu, still trying to learn. if any responses could be dumbed down for me to understand would be greatly appreciated.

---

### Post by taurus on 2008-11-11
See if you can mount it from a terminal.

Applications -> Accessories -> Terminal
```
sudo mkdir /media/thumbdrive
sudo mount -t ntfs-3g /dev/sdc1 /media/thumbdrive
```
Assume your USB thumbdrive is /dev/sdc1.

---

### Post by relaxedcrazyman on 2008-11-11
themaster@themaster-desktop:~$ sudo mount -t ntfs-3g /dev/sdc1 /media/thumbdrive
NTFS signature is missing.
Failed to mount '/dev/sdc1': Invalid argument
The device '/dev/sdc1' doesn't have a valid NTFS.
Maybe you selected the wrong device? Or the whole disk instead of a
partition (e.g. /dev/hda, not /dev/hda1)? Or the other way around?


[SIZE="4"]I tried with sdd1 this is what i got[/SIZE]
Failed to mount '/dev/sdd1': Operation not supported
Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by
          clicking on the 'Safely Remove Hardware' icon in the Windows
          taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for
          your own responsibility. For example type on the command line:

            mount -t ntfs-3g /dev/sdd1 /media/thumbdrive -o force

    Or add the option to the relevant row in the /etc/fstab file:

            /dev/sdd1 /media/thumbdrive ntfs-3g force 0 0

---

### Post by relaxedcrazyman on 2008-11-11
it seems to work now, but to mount it or unmount it i have to go through Storage Device Manager, is there anyway around this? when i try to right click and unmount on my desktop, it says i dont have permission:  You are not privileged to unmount the volume 'CORSAIR'.

---

### Post by taurus on 2008-11-11
The last time you used that USB thumbdrive in windows, did you just unplug it without doing through the safe remove device first?  Why don't you just plug it back to a windows machine and go through the safe remove device option (bottom right, next to the clock).  Then, see if Ubuntu would automount it when you plug it in.

---

### Post by relaxedcrazyman on 2008-11-12
> **taurus said:**
> The last time you used that USB thumbdrive in windows, did you just unplug it without doing through the safe remove device first?  Why don't you just plug it back to a windows machine and go through the safe remove device option (bottom right, next to the clock).  Then, see if Ubuntu would automount it when you plug it in.



no such luck, went onto vista and "safely" removed it, still doesnt auto mount when i plug it in in ubuntu. and i still have to go through storage device manager to mount and unmount

---

### Post by nothingspecial on 2008-11-12
Here`s something you could try
[SIZE="4"]
Do not do this on a mounted drive, unmount it first.[/SIZE]
```

sudo apt-get install ntfsprogs
```

Then ```
 sudo ntfsfix /dev/sdd1
```

Read about it first


[http://www.linux-ntfs.org/doku.php?id=ntfsfix](http://www.linux-ntfs.org/doku.php?id=ntfsfix)

[http://man.linux-ntfs.org/ntfsfix.8.html](http://man.linux-ntfs.org/ntfsfix.8.html)

---

