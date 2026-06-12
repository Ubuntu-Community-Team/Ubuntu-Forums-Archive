---
title: "2nd hard drive unmounts on reboot"
date: 2008-11-12
forum: Hardware
---

### Post by vaporjourney on 2008-11-12
Can anyone help me figure out a way to make it so my internal hard drive won't unmount each time I reboot my computer?  Sometimes this causes problems with Amarok, and makes me rescan my library folder so that it will recognize my files again.  Perhaps unmounting isn't the right term.  My media on this drive won't show up in RhythmBox until I click on the drive under Dolphin and open up a folder.  This causes ubuntu to place an icon for the drive on my desktop, just like it does when it automounts any other pieces of hardware.  This isn't a USB external hard drive, which I would understand unmounting each time I reboot.  Any ideas on how to fix this?

---

### Post by prshah on 2008-11-13
> **vaporjourney said:**
> make it so my internal hard drive won't unmount each time I reboot my computer?  
 Any ideas on how to fix this?

Try adding the "auto" option in the options list for the entry for your drive in the /etc/fstab; eg, change ```
# /dev/sda1
UUID=6EF45AC9F45A92E7 /media/sda1     ntfs    defaults,umask=007,gid=46 0       1

```
to
```
# /dev/sda1
UUID=6EF45AC9F45A92E7 /media/sda1     ntfs    defaults,umask=007,gid=46[color=red],auto[/color] 0       1

```

Make sure you add it at the end of the options. To edit your /etc/fstab file, you can use the command```
gksudo gedit /etc/fstab
``` from the Alt+f2 command box.

Be alert and careful when editing the /etc/fstab file.

---

### Post by vaporjourney on 2008-11-13
I don't see my HD listed in fstab:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/host/ubuntu/disks/root.disk /               ext3    loop,errors=remount-ro 0       1
/host/ubuntu/disks/boot /boot           none    bind            0       0
/host/ubuntu/disks/swap.disk none            swap    loop,sw         0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

However I do see the HD when I use the 'mount' command:

/dev/sda1 on /media/Video Capture type fuseblk (rw,nosuid,nodev,noatime,allow_other,blksize=4096)

---

### Post by prshah on 2008-11-13
> **vaporjourney said:**
> I don't see my HD listed in fstab:

However I do see the HD when I use the 'mount' command:
/dev/sda1 on /media/Video Capture type fuseblk (rw,nosuid,nodev,noatime,allow_other,blksize=4096)

From Intrepid onwards, optical and other removable devices have been moved under the control of fuse. Thus it is fuse (dynamic) that is handling your harddisk partition. If you make an entry similar to the one below, the hdd partition will become "static", eg always available. In short, just add the below lines to your /etc/fstab:

```
# /dev/sda1
UUID=[color=blue]6EF45AC9F45A92E7[/color] /media/sda1     ntfs    defaults,umask=007,gid=46,auto 0       1
```

Important CAVEATS:
a) [indent] - Replace the part in blue with the actual UUID for your ntfs partition; you can find this with ```
sudo blkid /dev/sda1
```[/indent]
b) [indent] I think you are running a Wubi installation (ie, Ubuntu through Windows). I'm not sure (having never worked with wubi), but mounting a Windows host partition in ubuntu can possible cause a major screwup. Please do more research before making the changes suggested above![/indent]
c) [indent] You will need to create the /media/sda1 directory before you make the changes to fstab, or atleast before you reboot. After making the changes, you need a reboot for the changes to take effect, which will at the same time let you know if the changes have worked for you or not.[/indent]
d) [indent] You will need to be a member of the plugdev group (of which all users are, by default). You can confirm your membership by just giving the command ```
groups
``` and checking if plugdev is listed.[/indent]

---

### Post by vaporjourney on 2008-11-13
This drive/partition that I'm working with is not the host partition, so I'm thinking that it won't cause any problems(?)  

How do I create a /media/sda1 directory before go into fstab?   

Also...when you say add the entry for sda1 at the end of the options in fstab, do you mean make he addition as the very last entry, at the bottom of the list?

---

### Post by prshah on 2008-11-13
> **vaporjourney said:**
> 
How do I create a /media/sda1 directory before go into fstab?   

Also...when you say add the entry for sda1 at the end of the options in fstab, do you mean make he addition as the very last entry, at the bottom of the list?

```
sudo mkdir /media/sda1
sudo chown root:plugdev /media/sda1
```

Yes, you can add the entry at the end. You can also add it anywhere in-between if you like, but at the end will reduce the chances of screwing up the existing entries.

---

### Post by vaporjourney on 2008-11-13
how do i create a directory though before I do the edit in fstab?

---

### Post by prshah on 2008-11-13
> **vaporjourney said:**
> how do i create a directory though before I do the edit in fstab?

```
sudo mkdir /media/sda1
sudo chown root:plugdev /media/sda1
```

---

### Post by vaporjourney on 2008-11-13
Thanks for all of the help prshah.  I created the directory, edited fstab, and upon rebooting the drive automounted.

---

### Post by prshah on 2008-11-13
> **vaporjourney said:**
> I created the directory, edited fstab, and upon rebooting the drive automounted.

OK, if you feel the issue is solved, can you mark this thread as solved? Click on "Thread Tools" near the upper right hand side of the page, and select "Mark Thread as Solved".

---

### Post by Tomatz on 2008-11-13
Nicely discribed howto prshah!

---

### Post by oliwally on 2008-11-17
Hi,

I tried all of this, and I did get the hdd to automount, but with my current setup, Firefox still won't play nicely (see my problem below from [http://ubuntuforums.org/showthread.php?p=6112817#post6112817](http://ubuntuforums.org/showthread.php?p=6112817#post6112817))

> I have two hard drives - one with Kubuntu 8.10 installed, and the other has windows. In Kubuntu I have pointed Firefox to the profiles folder in Windows, so that I have all my bookmarks and preferences the same in both systems. This has always worked well in 8.04 after a bit of tweaking of fstab. I was delighted to see that 8.10 recognized the windows hdd by default without trouble. However, my setup does not work and Firefox fails if I don't first 'visit' the ntfs hdd through dolphin. I'm asked for the root password and from then on all is well.

I also tried the following options in fstab:
```
UUID=B80CD0470CCFFDF6 /media/winxp auto users,umask=0000,atime,auto,rw,dev,exec,suid 0 0
```

This has always worked in the past, but not with the new installation of 8.10. Firefox and Thunderbird refuse to open, although I have access to the xp hdd.

---

### Post by oliwally on 2008-12-06
Solved it! And don't you hate it when the answer is staring you in the face and laughs at you.....

I got the auto-mounting going as per instructions by prshah.

But then I forgot to tell my Firefox and Thunderbird profiles to point to the newly created /media/sda1 (or in my case /media/winxp) mount point..... it was sill pointing to /media/disk (and thus needed the root pw). ](*,)

---

