---
title: "Input/Output Error when trying to mount Internal Hard Drive"
date: 2014-11-16
forum: Hardware
---

### Post by ENunn on 2014-11-16
Hello.

I am unable to mount my internal hard drive in Ubuntu 14.04. I can't remember what brand or model it is.

I get this error:
Error creating mount point `/media/ubuntu/harddriveserial': Input/output error

Why can't I mount my Hard Drive! I'M STARTING TO FREAK OUT!!!!!!!!!!!!!!!!!!!!!!!

Can anyone help? :(

---

### Post by Bashing-om on 2014-11-16
ENunn; Hello;

You do not advise us of how you are attempting to mount this internal drive;
```

cat /etc/fstab
cat /etc/mtab
mount
ls -al /media

```
You do not advise of the file system on that internal drive:
```

sudo fdisk -lu
sudo parted -l

```

Does the system 'see' the internal hard drive(s) ?
```

sudo blkid

```

Once these are know we can 1st mount the hard drive (maybe) manually, then depending on your usage perhaps 'automount' the internal hard drive.

[INDENT][INDENT]we be look'n
[/INDENT][/INDENT]

---

### Post by ENunn on 2014-11-16
> **Bashing-om said:**
> You do not advise us of how you are attempting to mount this internal drive

I'm just clicking the drive in the launcher.

> **Bashing-om said:**
> You do not advise of the file system on that internal drive

Oops. Sorry 'bout that. Forgot to put it in there. My file system is NTFS.

> **Bashing-om said:**
> Does the system 'see' the internal hard drive(s) ?

Yes it does!
```

/dev/loop0: TYPE="squashfs" 
/dev/loop1: LABEL="casper-rw" UUID="6668ddbf-53bf-d743-896e-fad52966e72f" TYPE="ext2" 
/dev/sda1: LABEL="SYSTEM" UUID="B4A05970A0593A56" TYPE="ntfs" 
/dev/sda2: UUID="F4145FEE145FB27A" TYPE="ntfs" 
/dev/sda3: UUID="54B5-745C" TYPE="vfat" 
/dev/sda4: LABEL="HP_TOOLS" UUID="169D-B845" TYPE="vfat" 
/dev/sdb1: LABEL="UUI" UUID="80B0-363C" TYPE="vfat" 

```

---

### Post by Bashing-om on 2014-11-16
ENunn; Humm ...

I do not see 'ubuntu' anywhere here, is this a WUBI install for ubuntu  ?
What does Windows' check disk utility report for the file system health of the NTFS (?) drive; OR are we looking at the 2nd hard drive ( sdb) that is listed as having a 'vfat' file system imposed on it ? In any respect, what does Windows report ?

We be try'n
[INDENT][INDENT][INDENT]to get to the bootpm of things
[/INDENT][/INDENT][/INDENT]

---

### Post by ENunn on 2014-11-16
> **Bashing-om said:**
> I do not see 'ubuntu' anywhere here

Its because I'm running Ubuntu off of a USB Stick. Windows isn't booting, so I'm trying to back up all my data and reinstall. Any help?

EDIT: I have another Linux distro on another USB and it can detect my drives fine. So how can I make it work again in Ubuntu?

---

### Post by Bashing-om on 2014-11-16
ENunn; Well ...

Have you considered making a true dual boot - with ubuntu installed "along side" onto the hard drive ?

The support to repair a Windows' file system is very limited in 'buntu. Much better to use Windows' tools for Windows' problems.

Clarify please, that you can not at this time boot Windows. It is your goal to boot up a liveUSB of ubuntu to recover your Windows' files ?

Do you have access to the Windows' recovery CD ?

[INDENT]'buntu is great,
[INDENT][INDENT][INDENT]but it is not magic
[/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by ENunn on 2014-11-16
> **Bashing-om said:**
> Have you considered making a true dual boot - with ubuntu installed "along side" onto the hard drive ?

I have no plans to do so.

> **Bashing-om said:**
> Clarify please, that you can not at this time boot Windows. It is your goal to boot up a liveUSB of ubuntu to recover your Windows' files ?
Yes. I'm just trying to burn my Documents, Music, and Videos to a lot of DVDs. Ugh so many... xD

> **Bashing-om said:**
> Do you have access to the Windows' recovery CD ?
I got an iso from MS's website and tried reapiring, and no luck. I'm just gonna back up my files and reinstall...like I said.

> **Bashing-om said:**
> 'buntu is great,[INDENT][INDENT][INDENT][INDENT]but it is not magic
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]


Agreed.

---

### Post by Bashing-om on 2014-11-16
ENunn; Yuk,

I am not the best person to offer advise in this situation - I have had nothing to do with Windows in many years. Let's await others to advise.

Else, well we can try and manually mount the Windows' partition(s) from the liveUSB , in terminal, of ubuntu, and see what can be done ?

[INDENT][INDENT]if I knew everything
[INDENT][INDENT][INDENT]I would not be me
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by ENunn on 2014-11-16
> **Bashing-om said:**
> ENunn; Yuk,

I am not the best person to offer advise in this situation - I have had nothing to do with Windows in many years. Let's await others to advise.

Else, well we can try and manually mount the Windows' partition(s) from the liveUSB , in terminal, of ubuntu, and see what can be done ?
[INDENT][INDENT]if I knew everything[INDENT][INDENT][INDENT]I would not be me
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]


I'm just going to reinstall Ubuntu and see if it helped. I'll get back once its done.

---

### Post by Mark Phelps on 2014-11-16
Unfortunately, I/O errors reported on hard drives often indicate hardware failure -- and if that is the case, no Linux distro is going to work to recovery your files.

Furthermore, if the drive is physically OK, but the filesystem is corrupted, Linux distros will refuse to allow you to mount the filesystem to prevent further damage to it.

If you really want to recover files and folders from the drive, you need to seriously consider using Windows data recovery apps.  To do that, you would need to remove the drive and connect it to a working Windows PC.  Once you do that, you could install "Recuva" to see what files and folders it finds on the drive.

---

### Post by ENunn on 2014-11-16
Got it working again. All I needed to do was to reinstall Ubuntu. It was probably Ubuntu on crack which made it disk not mount. Thanks again!

---

### Post by Bashing-om on 2014-11-16
ENunn; Great !

Glad it all worked out.

[INDENT][INDENT]all's well that ends well
[/INDENT][/INDENT]

---

