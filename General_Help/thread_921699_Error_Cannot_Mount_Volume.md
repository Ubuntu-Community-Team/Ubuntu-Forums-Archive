---
title: "Error Cannot Mount Volume"
date: 2008-09-16
forum: General Help
---

### Post by thinkpadder21 on 2008-09-16
I recently wanted my windows files or drive to mount automatically (I dual boot). I went into the drive properties and changed the command strings for the volume (don't ask what I changed them to - I can't recall... I know I'm an idiot!!!).  Anyway, since that time I am not able to mount my windows drive/volume and I receive the following error (see attached screenshot).

Anyone with a way to fix or restore my volume?

Thanks for any help!

[My only consolation now is that I can access that volume in windows.]

---

### Post by Pro-reason on 2008-09-16
You seem to have given the drive a name that contains the illegal character “/”.  Change it.

Go to the terminal and type “sudo blkid”.  Post the output here.

---

### Post by mc4man on 2008-09-16
a simple fix may be to run this from a terminal
```
gconf-editor
```

Browse down to system -> volumes and see if they're are any entries, if so click on.
Look at screenshot1 to see an example of misnamed mount point. The mount point can only contain a name, not a directory (/media/, ect.

If you find this right click on the entry -> edit key. Either delete the entry or just leave a name. (screen2

you would typically create this situation by editing imprpoerly in a volumes properties as such (or worse) That box can *only* contain a name -  screen3

---

### Post by thinkpadder21 on 2008-09-16
> **Pro-reason said:**
> You seem to have given the drive a name that contains the illegal character “/”.  Change it.

Go to the terminal and type “sudo blkid”.  Post the output here.
/dev/sda1: UUID="9A0C670D0C66E3AB" LABEL="ServiceV002" TYPE="ntfs"
/dev/sda2: UUID="E626A3F926A3C8BF" LABEL="Ron's Drive" TYPE="ntfs"
/dev/sda5: UUID="954a16b9-3db2-446e-9a1c-39d8daedaa6c" TYPE="ext3"
/dev/sda6: TYPE="swap" UUID="7a70bba3-92f1-4b88-acdb-0bfa70af88b8"

---

### Post by thinkpadder21 on 2008-09-16
> **mc4man said:**
> a simple fix may be to run this from a terminal
```
gconf-editor
```

Browse down to system -> volumes and see if they're are any entries, if so click on.
Look at screenshot1 to see an example of misnamed mount point. The mount point can only contain a name, not a directory (/media/, ect.

If you find this right click on the entry -> edit key. Either delete the entry or just leave a name. (screen2

you would typically create this situation by editing imprpoerly in a volumes properties as such (or worse) That box can *only* contain a name -  screen3
Part of my problem also lies in the fact that I cannot get to the volume editing screen (your screen 3 attachment).  I get the same error window as before.

---

### Post by Pro-reason on 2008-09-17
> **thinkpadder21 said:**
> 
/dev/sda2: UUID="E626A3F926A3C8BF" LABEL="Ron's Drive" TYPE="ntfs"

It seems to be having a problem with the space and/or apostrophe in the volume label.

Do this:

```

sudo apt-get install ntfsprogs
sudo ntfslabel /dev/sda2 Ron

```

It will hopefully be OK on the next reboot.  (If not, you may have to edit /etc/fstab.)

---

### Post by mc4man on 2008-09-17
> Part of my problem also lies in the fact that I cannot get to the volume editing screen
That was just an example of how you may have *made* the volume 'unmountable'
Obviously you can't go to the properties of a volume that's not mounted.

Did you run gconf-editor and look there as described?

Changing the volume name may or may not help. (if the UUID stays the same it won't 
Giving it an entry in fstab and new mount point probably will work (though not normally needed to mount ntfs volumes and will also give you the 'auto mount' you wished.

While it's not a great idea to have symbols in a volume name (when creating a partition it's not allowed) that should have no bearing on whether it can be mounted.

EX.
> /dev/sda2: UUID="B2E8B188E8B14AFD" LABEL="PROG'S @" TYPE="ntfs"
It mounts just fine to /media/PROG'S @

Seeing as how you have windows you can also change the volume name of any ntfs or fat32 partition there ( and add symbols

control panel -> administrative tools -> computer management -> disk management. Right click on the partition -> properties and alter the name

---

### Post by thinkpadder21 on 2008-09-17
> **Pro-reason said:**
> It seems to be having a problem with the space and/or apostrophe in the volume label.

Do this:

```

sudo apt-get install ntfsprogs
sudo ntfslabel /dev/sda2 Ron

```

It will hopefully be OK on the next reboot.  (If not, you may have to edit /etc/fstab.)
I tried those commands without success.  I did close Windows properly, so that is not the issue.  I wonder if there might be a conflict with the volume name being different in windows?  I will try changing the volume name in windows to match ubuntu.  When I tried using the commands you suggested, here is what I ended up with:

:~$ sudo ntfslabel /dev/sda2 Ron
Failed to mount '/dev/sda2': Operation not supported.
Access is denied because the NTFS journal file is unclean. Choices are:
 A) Shutdown Windows properly.
 B) Click the 'Safely Remove Hardware' icon in the Windows taskbar
    notification area before disconnecting the device.
 C) Use 'Eject' from Windows Explorer to safely remove the device.
 D) If you ran chkdsk previously then boot Windows again which will
    automatically initialize the journal.
 E) Submit 'force' option (WARNING: This solution it not recommended).
 F) ntfsmount: Mount the volume read-only by using the 'ro' mount option.

UPDATE...
I rebooted to Windows, shut down, then booted to Ubuntu and that error message disappeared.  However, I still can't access the volume I want.

Is there a way to re-install or re-mount (sorry my linux terms are unsure) that drive/volume from scratch?  So far, I'm getting nowhere...

---

### Post by Pro-reason on 2008-09-17
Please post the output of ```
cat /etc/fstab
```

---

### Post by thinkpadder21 on 2008-09-17
> **Pro-reason said:**
> Please post the output of ```
cat /etc/fstab
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=954a16b9-3db2-446e-9a1c-39d8daedaa6c /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda6
UUID=7a70bba3-92f1-4b88-acdb-0bfa70af88b8 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

---

### Post by Pro-reason on 2008-09-17
Do  this:

```

sudo mkdir /media/Ron
gksu gedit /etc/fstab

```

Add this line to the file, and save.

```

LABEL=Ron   /media/Ron    ntfs-3g    defaults,umask=007,gid=46,user,auto 0       1

```

---

### Post by thinkpadder21 on 2008-09-18
> **Pro-reason said:**
> Do  this:

```

sudo mkdir /media/Ron
gksu gedit /etc/fstab

```

Add this line to the file, and save.

```

LABEL=Ron   /media/Ron    ntfs-3g    defaults,umask=007,gid=46,user,auto 0       1

```
That worked - got my volume back!  Fantastic!  I'm not sure how much I learned from all this, but I will say that I won't screw around with that again!

Appreciate your patience and help.

---

