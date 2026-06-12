---
title: "Mount Additionnal Drive at Startup from Persistent USB Key Boot."
date: 2021-11-10
forum: Hardware
---

### Post by castor27 on 2021-11-10
Hi, 
I've created with RUFUS (in Windows10) a Ubuntu 20.04LTS bootable USB key.  I've made the USB key persistent by using a (not so noticeable) control/slider to define the amount of storage to allow for persistence (default 0).  Making it persistent cares for most of configurations to be preserved between startups.  

However, after following a few trusted sites how-tos,  I still cannot mount my Windows data hard drive at startup.  It will mount fine manually with Thunar File Manager, but when I (carefully) sudo edit the fstab file,  it gets overwritten with the previous values at next boot.

Is there any thing I can do to have it mounted automatically at startup ?

Thanks for any info.

---

### Post by yancek on 2021-11-10
> Is there any thing I can do to have it mounted automatically at startup ?
 

I don't think so.  Persistent installs do not modify system files such as fstab.  You can create and save files and instal software but I've never seen a situation wherea persistent install retains modifications to system files.  I someone knows a way, I would be happy to hear it.  I think the only way is with an actual full install.

---

### Post by oldfred on 2021-11-10
I never have used a persistent install. I assume it has an UUID?
lsblk -e 7 -o name,fstype,size,fsused,label,partlabel,mountpoint,uuid

But I regularly do test or temporary installs and found manually editing fstab to be a hassle.
I always want to mount my standard data partition in every install, so scripted it.
I would think it might work for your install, but have to be run manually each time you booted.

Part of my script for a new install, I use noatime for SSD & relatime for HDD partitions:

```
#!/bin/bash

mkdir /mnt/data

# edit fstab to add mounts, UUIDs of data partitions do not change
cp -a /etc/fstab /etc/fstab.backup
#Edit fstab first Need to change from UUID to labels, so it works on both portable & DT
str1="# Entry for nvme0n1p5 :"
str2="UUID=1a44f4af-6780-4bbd-ad0b-6385ed30830b /mnt/data    ext4   noatime  0  2  "
str3="tmpfs /tmp tmpfs defaults,noatime,mode=1777 0 0"
fname=/etc/fstab
if grep -q "$str1" "$fname"; then
  echo $str1 exists # String was found
else
    echo $str1 >> $fname
    echo $str2 >> $fname
    echo $str3 >> $fname
fi
# Verify no errors in fstab & remount with new mounts
mount -a
```

I do not use NTFS any more as no Windows but have seen this as suggested parameters.
You do need Windows fast start up off which sets hibernation flag, and Windows may turn it back on with updates.
And you have to include in script the creation of a mount point like /media/WinD in below example.

For ntfs UUID shown is example only see below:
UUID=XXXXXXXXXXX   /media/WinD ntfs defaults,nls=utf8,umask=000,uid=1000,gid=1000,windows_names 0 0
Window_names prevents the use of invalid windows characters:
(which are the nine characters &#8221; * / : < > ? \ | and those whose code is less than 0×20) 
uid=1000 should fix the trash problems as well:

---

### Post by C.S.Cameron on 2021-11-12
If you select "Write in ISO Image mode", (not dd image mode), Rufus extracts the ISO to USB as individual files. You should be able to modify these files booting from a second Live USB or from Windows. If a USB is made using dd mode then the USB is read only.

---

### Post by TheFu on 2021-11-12
You can modify the fstab for the persistent system
or
you can install and configure **autofs**, which will mount storage where you previously specify, on-demand, as needed and umount it when it is no longer in use. This is a good way to deal with NFS, CIFS, and USB storage in general.  This is how I do it on all my systems. There is an ubuntu guide for autofs.

Both of these methods require that you have write access to /etc/ on the running USB device.  I know mkusb supports that and I think others do as well (ventool/ventoy/ ven-something?).  The persistent storage cannot just be a data partition, while that would be useful for needs outside the mounting stuff in this thread.

---

### Post by castor27 on 2021-11-12
@TheFu
- As stated initially, I can modify fstab (sudo mousepad ... and verify that fstab is written), but when I reboot, the fstab does not contain my modifications.
- Does autofs works for non-bootable NTFS partition/disks (Windows 10 NTFS, not NFS) ?

---

### Post by castor27 on 2021-11-12
@C.S.Cameron
dd image ??
Ubuntu key drive was created with RUFUS 3.15.1812, mostly with default values.
Device = ... G: (32GB)
Boot selection= ...iso
Persistent partition size = 25 GB (*slider and/or entry would not allow bigger, even if available space was 32 GB)
Partition scheme = MBR
Target system = BIOS or UEFI
File system=FAT32 (Default)
Cluster size=16 kB (Default)

*Note that between boot, settings of time (local not UTC), language (french) and keyboard and mouse are preserved.

---

### Post by TheFu on 2021-11-12
if /etc/ isn't persistent between reboots - you need something else.  Use a better tool, like mkusb or ventool.
autofs works for any file system that is supported by mount.

---

### Post by sudodus on 2021-11-12
You can create a small shellscript and make a desktop file for it and put the desktop file into the directory 'autostart',

```

~/.config/autostart

```

This shellscript will run when the desktop is started.

```

udisksctl mount  --block-device /dev/disk/by-uuid/<put here the actual UUID of the partition to mount>

```

You can find the UUID with the following command (in a wide terminal window to avoid line-wrapping the output of the longer command line)

```

lsblk -o name,size,fstype,uuid,label
# or
lsblk -o name,size,fstype,uuid,label,mountpoint,model | sed 's/ *$//'

```

[hr][/hr]
Edit: I tested the following pair of files in my Ubuntu 20.04.3 LTS (in order to mount an internal NTFS file system) and it worked. Modify according to your environment.

```

tester@lenovo-v130:~$ [COLOR="#0000CD"]find bin .config/autostart/ -mtime -1 -type f -ls[/COLOR]
[B]  2622175      4 -rwxrwxr-x   1 tester   tester         67 nov 12 23:05 bin/automount
  2622365      4 -rwxrwxr-x   1 tester   tester        137 nov 12 22:49 .config/autostart/automount.desktop[/B]
tester@lenovo-v130:~$ [COLOR="#0000CD"]cat bin/automount[/COLOR]
**udisksctl mount  --block-device /dev/disk/by-uuid/5A20850E2084F1F5**
tester@lenovo-v130:~$ [COLOR="#0000CD"]cat .config/autostart/automount.desktop[/COLOR]
[B][Desktop Entry]
Type=Application
Version=1.0
Name=AutoMount
Exec=/home/tester/bin/automount
X-GNOME-Autostart-enabled=true
Terminal=true[/B]
tester@lenovo-v130:~$ 

```

---

### Post by castor27 on 2022-04-13
> **sudodus said:**
> You can create a small shellscript and make a desktop file for it and put the desktop file into the directory 'autostart',

```

tester@lenovo-v130:~$ [COLOR=#0000CD]find bin .config/autostart/ -mtime -1 -type f -ls[/COLOR]
[B]  2622175      4 -rwxrwxr-x   1 tester   tester         67 nov 12 23:05 bin/automount
  2622365      4 -rwxrwxr-x   1 tester   tester        137 nov 12 22:49 .config/autostart/automount.desktop[/B]
... 

```

Bonjour, from root (/) , I did not find  /bin/config/autostart  or /bin/config  directories (with or without "sudo" prefix)  Are these directories you created ?  If so with what user , what permission ?
Thanks for any info.

---

### Post by TheFu on 2022-04-13
~/ == HOME.
Look in $HOME/.config/autostart/ 

The suggestions above include ~/ and are relative from the current user's HOME directory.

The prompt also shows the CWD/PWD as ~/.
Learn about absolute and relative directories. This is necessary on Unix OSes.

---

### Post by castor27 on 2022-04-15
Thanks , I did not know about 'tilde' (~) !

---

### Post by castor27 on 2022-04-15
@sudodus

Still ... There are no "autostart" sub-directory in the "~/.config" directory.

Curiously, when I use the "find" command to search any "autostart" files or directories, the output mentions some directories noted as 'access denied' , even with "sudo" prefixing the command  ?!

---

### Post by TheFu on 2022-04-15
~userid/ can be used to access any userid. The current one or any others.
~root == /root   as an example.

For my username, thefu, ~/ == ~thefu == /export/home/thefu == $HOME/
They are all the same and can be used almost interchangeably anywhere.
$HOME is set by the passwd database.  **getent passwd** shows the password database (local and remote as in LDAP).  To filter those entries, use 
```
$ getent passwd {username}
$ getent passwd thefu
```
Each field in the passwd database has a specific use. It is clearly defined in the passwd file manpage.
Anyway, spelling out $HOME all the time gets old, so way, way, way, back in the beginning of Unix, ~ was added as a way for people to more easily work together and share read access with their coworkers.  Remember, in those times Unix servers would have hundreds to thousands of users and storage was tiny compared to what we have today, so many, many, disks would be needed to support different users.  /home/ just wasn't sufficient, so it would be common on large servers to have 10+ 240MB HDDs added for user HOME directories.  Where I worked, we had those drives mounted using amd (today that is called **autofs** in Linux) which mounted the storage for a user as needed when they logged in.  But since all users couldn't be on a single disk or single mount location, it was common to have 
/u1/
/u2/
/u3/
/u4/
.....
/u50/
....
as needed for where user HOME directories would be placed under.  Now the issue is removing the hassle to know which location has any specific username.  THAT is why ~ does the lookup in the passwd DB.  BTW, we weren't using LDAP back then. We used x.500 directory services then.

So ~thefu    could find the HOME in /u3/thefu
and
~castor27 could find that HOME in /u9/castor27. This avoided all the extra steps to either setup symlinks or run **getend passwd castor27** to get the HOME for each username.

Does that make sense?

Most things in Unix have very good reasons and if something isn't pretty simple, then it is likely there's a better way.  Of course, creating a bash function to perform the lookup and parsing of the passwd for a username --> HOME directory isn't hard, but it is so common in multi-user systems as to be built-into every shell that I know.

---

### Post by castor27 on 2022-04-15
@oldfred  : > I would think it might work for your install, **but have to be run manually each time you booted**.
 
Thanks but Thunar file manager does the job manually.

---

### Post by TheFu on 2022-04-15
> **castor27 said:**
> @sudodus

Still ... There are no "autostart" sub-directory in the "~/.config" directory.

Curiously, when I use the "find" command to search any "autostart" files or directories, the output mentions some directories noted as 'access denied' , even with "sudo" prefixing the command  ?!

Perhaps nobody created the autostart file? It isn't always a directory.
Or perhaps the DE involved doesn't use it?  Perhaps I missed which DE, if any, is being used?

```
$ locate autostart
```
finds a bunch of answers on my 20.04 system, even though the window manager, WM, I use doesn't use autostart.

Unix is about flexibility. We have to be flexible in our thinking.  Files aren't always pre-created if there is nothing to put inside them. That responsibility falls to us or the first program that desires to have a specific file exist.  This is a very common thing for config files.  If all the defaults are coded into the program, then there is little need to create a config file.  That would fall to us, if we want to override the defaults.  Some system-level configs ship with defaults all commented out, as a way to better document what they are, but the program also supports a {config}.local file as an local override.  Creating that .local version of the file allows us to have a way to keep both the defaults and comments about those defaults, while still overriding them. Plus, those overrides aren't part of the package manager's list of files, so it won't be overwritten in a package update or need complex merging efforts.  Good flexibility.

---

