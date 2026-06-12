---
title: "windows Mount problem"
date: 2008-08-17
forum: Hardware
---

### Post by rmx on 2008-08-17
Hi.

I have a double boot ubuntu 8.04/ XP.
the thing is that the /boot directory was erased from XP and I don't have the CD.
i have a backup on an external drive.
so Everything would be ok if ubuntu let me mount my xp drive.

I've done this several times:
```

rui@rmx:~$ sudo mount -t ntfs-3g /dev/sda1 /media/windows -o remove_hiberfile
$LogFile indicates unclean shutdown (0, 0)
Failed to mount '/dev/sda1': Operation not supported
Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by
          clicking on the 'Safely Remove Hardware' icon in the Windows
          taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for
          your own responsibility. For example type on the command line:

            mount -t ntfs-3g /dev/sda1 /media/windows -o force

    Or add the option to the relevant row in the /etc/fstab file:

            /dev/sda1 /media/windows ntfs-3g force 0 0

```

and

```

rui@rmx:~$ sudo mount -t ntfs-3g /dev/sda1 /media/windows -o force
Windows is hibernated, refused to mount.
Failed to mount '/dev/sda1': Operation not permitted
The NTFS partition is hibernated. Please resume and shutdown Windows
properly, or mount the volume read-only with the 'ro' mount option, or
mount the volume read-write with the 'remove_hiberfile' mount option.
For example type on the command line:

            mount -t ntfs-3g /dev/sda1 /media/windows -o remove_hiberfile


```

And I added to fstab the following line
/dev/sda1 /media/windows ntfs-3g force 0 0 


But last time I shutdown XP (when I erased the /boot), so windows is not hibernated.

Anyway I can't boot windows, so I guess I must "cheat" ubuntu somehow.

Any clue?

Thanks 

Rmx

---

### Post by jualin on 2008-08-17
Add the "ro" command suggested.

---

### Post by rmx on 2008-08-17
Yeah
That way I can mount the drive, but only read only
And I need to write on it

---

### Post by rmx on 2008-08-17
Anyone has a clue?

Thanks

Rui

---

### Post by finito on 2008-08-17
just curious did you try 

mount -t ntfs-3g /dev/sda1 /media/windows -o remove_hiberfile

---

### Post by rmx on 2008-08-17
I've done that as I said before:

> **rmx said:**
> Hi.

I've done this several times:

```

rui@rmx:~$ sudo mount -t ntfs-3g /dev/sda1 /media/windows -o remove_hiberfile

$LogFile indicates unclean shutdown (0, 0)
Failed to mount '/dev/sda1': Operation not supported
Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by
          clicking on the 'Safely Remove Hardware' icon in the Windows
          taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for
          your own responsibility. For example type on the command line:

            mount -t ntfs-3g /dev/sda1 /media/windows -o force

    Or add the option to the relevant row in the /etc/fstab file:

            /dev/sda1 /media/windows ntfs-3g force 0 0

```

and

```

rui@rmx:~$ sudo mount -t ntfs-3g /dev/sda1 /media/windows -o force

Windows is hibernated, refused to mount.
Failed to mount '/dev/sda1': Operation not permitted
The NTFS partition is hibernated. Please resume and shutdown Windows
properly, or mount the volume read-only with the 'ro' mount option, or
mount the volume read-write with the 'remove_hiberfile' mount option.
For example type on the command line:

            mount -t ntfs-3g /dev/sda1 /media/windows -o remove_hiberfile


```

And I added to fstab the following line
/dev/sda1 /media/windows ntfs-3g force 0 0 

Rmx

---

### Post by rmx on 2008-08-18
anymore sugestions please?

---

### Post by rmx on 2008-08-19
please please please?
:)

---

