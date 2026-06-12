---
title: "[SOLVED] How to mount encrypted, LVM volumes?"
date: 2008-10-07
forum: General Help
---

### Post by jerome1232 on 2008-10-07
EDITED to reflect wanchai's comments and additions

Dealing with encryption and LVM from a live cd.

This is more for future refrence, I know I will have to deal with these disks from a live cd sometime. I currently have an encrypted file system that uses lvm. I have no idea how to work with these partitions! Right now I'm booted into a live cd, the file system was encrypted via luks (alternate install cd) I'm using twofish encryption.

Okay this was easier than I thought it was going to be, man pages are great.

/dev/sda1 is my /boot
/dev/sda2 is my crypto partition
```
sudo apt-get install cryptsetup            # Installs the tools we need to deal with encrypted partitions
sudo modprobe dm-crypt                      # Inserts a module we need
sudo cryptsetup luksOpen /dev/sda2 cheer   # Unlocks the partition sda2 and names it cheer
Enter LUKS passphrase: 
key slot 0 unlocked.
Command successful.
#
# Now that we have unlocked the encryption, it's just dealing with the lvm
#
#
sudo apt-get install lvm2  # installs the tools we need
sudo modprobe dm-mod       # inserts a module we need
sudo vgscan                # Scans for all volume groups
  Reading all physical volumes.  This may take a while...
  Found volume group "Ubuntu" using metadata type lvm2
sudo vgchange -a y Ubuntu  # this made the VG Ubuntu active, if you don't give it a volume group as an argument it'll make them all active        
sudo lvscan                # This command lists the logical volumes and their /dev path
  ACTIVE            '/dev/Ubuntu/Root' [15.00 GB] inherit
  ACTIVE            '/dev/Ubuntu/swap' [1.00 GB] inherit
  ACTIVE            '/dev/Ubuntu/home' [215.89 GB] inherit
#
# Now I mount them to do whatever it is I need to do, if you wanted to run a fsck on them you obviously wouldn't mount them.
#
sudo mkdir /media/root; sudo mkdir /media/home
sudo mount /dev/Ubuntu/Root /media/root; sudo mount /dev/Ubuntu/home /media/home
#
# Now to reverse the process and unmount everything
#
sudo umount /media/root; sudo umount /media/home
sudo rmdir /media/root; sudo rmdir /media/home
sudo vgchange -a n Ubuntu 
sudo cryptsetup luksClose cheer
```

---

### Post by wanchai on 2008-10-16
Thanks for your post, solved my problem. :)

Why are you saying that you are not sure how to mount them? Your last line in the code box does exactly that.


More stuff for future reference:

If you have multiple disks with LVMs, for example the disk your OS is running on plus the USB disk you're trying to mount, then *vgchange* should get the volume name as an argument, for example:
```
sudo vgchange -a y testDiskVG1
```

To un-do the whole thing, you need to unmount the logical volumes, then close the volume group and lastly close the encrypted partition. For example (using jerome1232's naming scheme):
```
sudo umount /media/root; sudo umount /media/home
sudo vgchange -a n Ubuntu 
sudo cryptsetup luksClose cheer

```


Another little problem I had: both my built-in disk and the external one used the same name for the volume group. In this case it's impossible to activate the second volume group. Use *vgdisplay* to see what you have. Important are the fields *VG Name* and *VG UUID*. Then you can use
```
vgrename oldUUID newName
```
to make the names unique.


One last thing: when you plug in a USB drive with encrypted LVM partitions, Gnome pops up a dialog "Unlock Encrypted Data". When you use that, Ubuntu will do half the job. Do
```
ls -l /dev/mapper
```
to see how far you got. You'll probably have to manually mount the partitions, and you certainly have to un-do things manually. Instead of something short, like 'cheer', this automagic ersatz cryptsetup gizmo will use a long, ugly name, but you'll see it in /dev/mapper.

---

### Post by jerome1232 on 2008-10-16
Yeah I actually just worked it over before anybody responded with an answer, so I edited my post to reflect how I got it working in case someone stumbled on the thread looking for an answer :) I see I forgot to edit out a few things. I added some of your additions.

---

### Post by wanchai on 2008-11-23
Again, for future reference:

**cryptmount after booting from Ubuntu 8.10 Desktop CD**

Basically it works in the same way, but first you need to manually install packages cryptsetup and lvm2. Unfortunately, these packages are not on the Desktop CD, so you either need network access or have them on a non-encrypted disk.

Then you need to "modprobe dm-crypt". If you don't do the modprobe, cryptsetup openLuks will give you an error that sounds like "wrong password" ([https://bugs.launchpad.net/ubuntu/+source/cryptsetup/+bug/267192](https://bugs.launchpad.net/ubuntu/+source/cryptsetup/+bug/267192))

---

### Post by gauthma on 2008-12-21
After having installed Kubuntu on my laptop using this [tutorial]("http://learninginlinux.wordpress.com/2008/04/23/installing-ubuntu-804-with-full-disk-encryption/"), (which an almost identical setup to the one used in the explanation), I had become concerned about to do if I ever encountered problems and needed to boot from a live CD. This post cleared it out for me (worked in the first attempt, and was so much simpler of what I had imagined!)

Anyway, great work!
Big thanks

---

### Post by jerome1232 on 2008-12-21
> **gauthma said:**
> 
Anyway, great work!
Big thanks

I'm glad it helped you :)

> **wanchai said:**
> Unfortunately, these packages are not on the Desktop CD, so you either need network access or have them on a non-encrypted disk.

Good point I had never thought about if I was stranded without access to a repository, I think I'll be downloading these packages and putting them somewhere unencrypted/lvm'd.

---

### Post by wanchai on 2008-12-23
I built myself a customised boot CD that includes the missing packages (deleted games to create space) following this guide:
[https://help.ubuntu.com/community/LiveCDCustomization](https://help.ubuntu.com/community/LiveCDCustomization)

---

### Post by John Wiersba on 2009-01-09
> **wanchai said:**
> Again, for future reference:
_cryptmount after booting from Ubuntu 8.10 Desktop CD_


Wanchai:  what did you mean by this?  Was this supposed to be a be a link to an article?

---

### Post by wanchai on 2009-01-12
John, it wasn't a link, just underlined text, changed it to bold, hopefully that's less confusing

---

### Post by jerremy-tamlin on 2009-01-29
Hi, I don't suppose you guys have hade any trouble remounting an LVM filesystem have you?

I posted a tread [http://ubuntuforums.org/showthread.php?t=1018525](http://ubuntuforums.org/showthread.php?t=1018525) a month ago but got no responces. Haven't been able to figure out the answer. Basically My LVMs all mount fine at boot with the options I specify in fstab but if I try to remount them any options I specify are ignored.

Since you seem to be active and using LVM I thought I'd ask.

Sorry if I'm breaking into the conversation but you seemed to have solved your problem. If you ignore me I'll go away.
Cheers
Jesse

---

### Post by giac0m0 on 2009-10-14
Hi there, thanks for posting the solution to your boggle.

I had a Fedora install with LVM and couldn't access the files until I used your instructions on my Jaunty 9.04 desktop with the LVM drive attached via usb.

Two things; firstly I couldn't depmod dm_mod - I got a module not found error although this did not impact my success.

```
FATAL: Module dm_mod not found.
```

Secondly to unmount the drive I had to use the -l switch on the umount command:

```
sudo umount -l /media/root
```

otherwise the unmount failed due to a process or user accessing it.

Thanks again!

---

### Post by jerome1232 on 2009-10-14
It's been awhile since I wrote this thread but

dm_mod is for encryption, so if you were just using lvm and not encryption and didn't install luks then that's why dm_mod wasn't found. Since you weren't using luks encryption it worked anyways.

Happy lvm'ing!

---

### Post by whitenight639 on 2012-08-07
Sorry to drag up old threads from the dead but I'm having a similar problem unmounting the drive;

[root@jaguar mapper]# ls -al /dev
brw-rw----.  1 root disk      8,   0 Aug  7 21:34 sda
brw-rw----.  1 root disk      8,   1 Aug  7 21:34 sda1
brw-rw----.  1 root disk      8,   2 Aug  7 22:19 sda2
brw-rw----.  1 root disk      8,  16 Aug  7 21:34 sdb
brw-rw----.  1 root disk      8,  17 Aug  7 21:34 sdb1
brw-rw----.  1 root disk      8,  18 Aug  7 21:34 sdb2
[root@jaguar mapper]# umount -f /dev/sda2 
**umount: /dev/sda2: not mounted**

[root@jaguar mapper]# umount -f /dev/sda1 
umount: /dev/sda1: not mounted

[root@jaguar mapper]# umount -f /dev/sda
umount: /dev/sda: not mounted

[root@jaguar mapper]# cryptsetup luksOpen /dev/sda2 oldsystem
Enter passphrase for /dev/sda2: 
**Cannot use device /dev/sda2 which is in use (already mapped or mounted)**.
[root@jaguar mapper]# 

whats all that about is there something using the drive that I can kill off?

---

### Post by wildmanne39 on 2012-08-07
If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.

---

