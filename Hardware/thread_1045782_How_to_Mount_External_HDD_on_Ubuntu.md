---
title: "How to Mount External HDD on Ubuntu"
date: 2009-01-20
forum: Hardware
---

### Post by gordanr on 2009-01-20
Hello All,

Please I need help,

I'am new with Ubuntu - Linux,
I have external HDD that I used with my Windows before, I would like to use it now on Ubuntu. As soon as I plug it in, it tells me that HDD cannot be mounted!!??

What to do?

Please help

Thank you All

---

### Post by taurus on 2009-01-20
Make sure you use the _safely remove hardware_ (little icon in the lower right corner) in windows to unmount it first before you unplug it.

Otherwise. open a terminal and post the output of this command here.

Applications -> Accessories -> Terminal
```
sudo fdisk -**l**
```
That is a lower case letter L, not number 1.

---

### Post by gordanr on 2009-01-20
yes I did what you said, but still nothing, and this is what I get:

server@server-laptop:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x90909090

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19128   153645628+  83  Linux
/dev/sda2           19129       19457     2642692+   5  Extended
/dev/sda5           19129       19457     2642661   82  Linux swap / Solaris

Disk /dev/sdb: 750.1 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa4b57300

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       91201   732572001    7  HPFS/NTFS
server@server-laptop:~$

---

### Post by taurus on 2009-01-20
What is the error message when you try to mount it by hand from a terminal?

```
sudo mkdir /media/sdb1
sudo mount -t ntfs-3g /dev/sdb1 /media/sdb1
```

---

### Post by gordanr on 2009-01-20
This is the message:

Cannot mount volume
Unable to mount the volume FreeAgent Drive.

THEN TELLS ME THIS MESSAGE below:

DBus error org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

---

### Post by gordanr on 2009-01-20
Failed to mount '/dev/sdb1': Operation not supported
Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by
          clicking on the 'Safely Remove Hardware' icon in the Windows
          taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for
          your own responsibility. For example type on the command line:

            mount -t ntfs-3g /dev/sdb1 /media/sdb1 -o force

    Or add the option to the relevant row in the /etc/fstab file:

---

### Post by gordanr on 2009-01-20
Got it to work :))

Thank you.

---

### Post by taurus on 2009-01-20
> **gordanr said:**
> Failed to mount '/dev/sdb1': Operation not supported
Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by
          clicking on the '**[COLOR="Red"]Safely Remove Hardware[/COLOR]**' icon in the Windows
          taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for
          your own responsibility. For example type on the command line:

            mount -t ntfs-3g /dev/sdb1 /media/sdb1 -o force

    Or add the option to the relevant row in the /etc/fstab file:

Didn't I say something about that in my initial reply?

1.  You can boot into windows and unmount it first before you unplug it.

2.  You can install ntfsprogs and use ntfsfix to fix it.
```
sudo apt-get update
sudo apt-get install ntfsprogs
sudo ntfsfix /dev/sdb1
```

3.  Or you can use the force option to mount it.
```
sudo mount -t ntfs-3g /dev/sdb1 /media/sdb1 -o force
```

---

### Post by gordanr on 2009-01-20
You are Genius,

Now can you tell me how can I share this External HDD on my Network - Lan? with Ubuntu.

---

