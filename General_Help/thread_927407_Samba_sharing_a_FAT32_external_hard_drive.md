---
title: "Samba sharing a FAT32 external hard drive"
date: 2008-09-22
forum: General Help
---

### Post by un_dave on 2008-09-22
I have a ubuntu server with an external 1tb hard drive which is formatted FAT32, I am attempting to share the folder with Samba, for guest read/write access, but users receive a permissions error when attempting to write. 

While I would like to reformat the drive, this is not currently an option. 

This is my setup:

This drive has a media folder, which should be shared with samba, to allow read/write access to all users, including guest users.  

The drive is mounted with this script, and should allow write permissions to the drive. 

```

sudo umount /dev/sdd1
sudo mount -t vfat /dev/sdd1 /media/TERRY_EXT -o iocharset=utf8,umask=000

```

This is my smb.conf. The dropbox share works correctly, allowing read/write. Note the commented out section, which removes the user permission requirement which I initially tried, and means that the share should now function the same as the dropbox. 

```

[global]
        server string = %h server (Samba, Ubuntu)
        map to guest = Bad User
        obey pam restrictions = Yes
        passdb backend = tdbsam
        passwd program = /usr/bin/passwd %u
        passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n *passwd:*password\supdated\$
        syslog = 0
        log file = /var/log/samba/log.%m
        max log size = 1000
        dns proxy = No
        ldap ssl = no
        usershare allow guests = Yes
        panic action = /usr/share/samba/panic-action %d
        invalid users = root

[dropbox]
        comment = guest writable dropbox (not backed up)
        path = /data/drop
        read only = No
        guest ok = Yes

[TERRY-media]
        comment = TERRY WD External - Media Folder (no backups)
        path = /media/TERRY_EXT/Media
#       write list = +tbu
# now anyone should be able to write to this drive...
        read only = No
        guest ok = Yes

```

At this point I'm stumped. If anyone has any ideas or suggestions, they'd be greatly appreciated. 

Cheers,

Dave.

---

### Post by wolfen69 on 2008-09-22
did you add the users to the sambashare group? ```
sudo adduser username sambashare
```

---

### Post by un_dave on 2008-09-22
No, I don't think so, because the users will be guests, connecting from windows xp *or* osx, without a username/password, they shouldn't need to have explicitly defined permissions. 

The section where I was previously assigning write access to a group has been commented out, and now i'm just aiming for guest read/write access for all. 

Note that the dropbox share has exactly the same setup, and works fine, allowing anyone to read and write.

---

### Post by un_dave on 2008-09-24
Anyone?

I've got a feeling that the issue has something to do with the umask=000 parameter to mount. But I'm not sure on the specifics of the umask parameter, and there doesn't seem to be any reference to it in man mount.  

```

sudo mount -t vfat /dev/sdd1 /media/TERRY_EXT -o iocharset=utf8,umask=000

```

---

### Post by jimmyridge on 2008-10-13
i've just ran into this and i think it might have to do with fat32 not having POSIX permision support [http://en.wikipedia.org/wiki/Comparison_of_file_systems](http://en.wikipedia.org/wiki/Comparison_of_file_systems)

and since samba sort of stanfs on top of what the main FS permissions are, i hope i'm wrong but i guess i could leave the fat32 as readonly and a ext3 "/" folder as writable (can always move the file later to the readonly folder)

---

### Post by geirha on 2008-10-13
What does the permissions look like on the mounted filesystem?
```
ls -ld /media/TERRY_EXT/Media
```

---

### Post by un_dave on 2008-10-14
That code returns this:
```

drwxrwxrwx 9 root root 32768 2008-09-23 11:03 /media/TERRY_EXT/Media

```

---

### Post by geirha on 2008-10-14
All users have full access to that drive, so I don't see why you'd get a permission problem. Could you try mounting it on the same box, and see what messages you get in the terminal?

```
sudo mount -t cifs -ouser=guest //localhost/TERRY-media /mnt
```

Then try to creating an empty file
```

ls -ld /mnt
sudo touch /mnt/empty-file.txt
ls -l /mnt/empty-file.txt
```
Does that give an error?

---

### Post by un_dave on 2008-10-14
Thanks for the assistance geirha, when I run the first line provided, I get the error below.
Do I need to mount it to some folder in the /mnt directory? or is the cifs fs type wrong?

```
$ sudo mount -t cifs -ouser=guest //localhost/TERRY-media /mnt
mount: wrong fs type, bad option, bad superblock on //localhost/TERRY-media,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```

---

### Post by geirha on 2008-10-15
Ah, right, you need the package [smbfs](apt://smbfs) installed to mount smbfs and cifs.

---

