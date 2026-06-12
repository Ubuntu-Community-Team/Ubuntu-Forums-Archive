---
title: "Multiple mount links in Places and Nautilus"
date: 2009-12-22
forum: Hardware
---

### Post by nicknefarious on 2009-12-22
I have a Samsung 500GB internal hard drive and there are some problems when Ubuntu Karmic mounts the partitions. When I boot, these partitions have been set to automount using fstab, so they appear in the Places (removable media) menu and the sidebar menu of a nautilus browser screen. Problem is, for each of the mounted partitions, they appear twice or three times (some with icons representing the drive as mounted and some with icons representing the drive as unmounted). Only one is the correct link which takes me to the partition contents while the other/s is/are sorts of dead links which give errors if I try to mount, unmount or even access the partitions using them.

I also have a Samsung 320GB internal hard drive mounted in an external USB enclosure. Divided up similarly to the internal drive (except smaller - relatively). When I plug this in, again multiple entries appear in both Places (removable media) and Nautilus sidebar links and it is increasingly confusing.

It seems that plugging USB drives with more than one partition seems to make things even worse. And having USB drives plugged in at boot also causes errors which delay the boot process.

How can I get rid of these? I have seen a number of threads around about this problem but no real solutions. Some aesthetic fix suggestions have been made but I want to rectify the underlying problem.

Thanks,

Nick

---

### Post by vanadium on 2009-12-22
You have an internal drive. I would mount this using /etc/fstab.

You also have a removable drive. I would not mount drives that can be physically disconnected using /etc/fstab.

To "clean" your system
* create a backup of your current /etc/fstab
* edit your /etc/fstab and remove all extra drives that you mounted there yourself. check for an error free /etc/fstab with the command: "sudo mount -a": there should not be any output.
* Delete any bookmarks to your drives that are left in the left pane of nautilus.
* Shut the system down and disconnect the removable drive
* Start the system, and remove any directory under /media which (once) were assigned as mount points for your drives. Leavo only the "cdrom" directories in place. If thee are hidden files under /media, delete these as well. (you will also need root permissions for this)

This should clean the mess. Your safest bet is to restart another time.

* Now add the partitions on your internal drives back to /etc/fstab. Execute "sudo mount -a" to see if your edits went properly. After that, the partitions should be available, yet will not show in nautilus. You can use bookmarks to include them in the left pane of nautilus, or use symbolic links in your home directory to have convenient access.
* Connect your external drive: it should automatically appear in the left pane of nautilus.

---

### Post by nicknefarious on 2009-12-22
vanadium... thanks for your reply.

A couple of issues.

1. Even when the internal drive partitions are mounted using fstab they still show up in the "removable media" section of the "Places" dropdown menu. Is this the way it should be? I haven't used fstab to mount any of the external drive partitions they automount themselves on connection.

2. I have tried a number of previous times to remove links and bookmarks from the Nautilus side pane but always get permission errors - need to be root. Have tried running Nautilus a couple of times as root, but it was buggy and messy... Maybe this has changed during an update and I'll give it another go.

3. Can you recommend (read - provide to me) a standard line of code for automounting each of my internal drive partitions in fstab? There seems to be a lot of conflicting information out there as to what options should or should not be included... and whether I should be mounting them by partition descriptors ie. sda5, or by UUID or by textual name "Media_Store". I have four partitions that are ext4 three of which are used for data - documents, media and audio and a fourth which stores virtual machines and virtual hard drives. I also have a fifth partition which is NTFS - currently blank, but will be looking to use in the future.

Sorry for long reply... 

Hope you can help. It is greatly appreciated.

Thanks again,

Nick

---

### Post by vanadium on 2009-12-23
> 1. Even when the internal drive partitions are mounted using fstab they still show up in the "removable media" section of the "Places" dropdown menu. Is this the way it should be? I haven't used fstab to mount any of the external drive partitions they automount themselves on connection.

Partitions mounted in /etc/fstab should not appear under "Places" unless you added a bookmark yourself.

> 
2. I have tried a number of previous times to remove links and bookmarks from the Nautilus side pane but always get permission errors - need to be root. Have tried running Nautilus a couple of times as root, but it was buggy and messy... Maybe this has changed during an update and I'll give it another go.

Never had these issues. This suggests your current user configuration is somewhat broken. To make that sure, create a new temporary account, and see wether the problems also occurs there.

> 
3. Can you recommend (read - provide to me) a standard line of code for automounting each of my internal drive partitions in fstab? There seems to be a lot of conflicting information out there as to what options should or should not be included... and whether I should be mounting them by partition descriptors ie. sda5, or by UUID or by textual name "Media_Store". I have four partitions that are ext4 three of which are used for data - documents, media and audio and a fourth which stores virtual machines and virtual hard drives. I also have a fifth partition which is NTFS - currently blank, but will be looking to use in the future.

A standard line in /etc/fstab consists of 6 lines, (1) the identifier (UUID or LABEl or device name) (2) the mount point (3) the file system type, (4) the options and (5) and (6) two numbers for "dump" (5) and "check" (6).

Preferably mount by UUID, alternatively by LABEL. Avoid using the device name: on modern hardware, this is not always the same between boots.

Check the output of "sudo mount -a" to see if your /etc/fstab contains errors.

---

### Post by Junkieman on 2010-01-21
I have the same issue Nick, running Ubuntu Karmic 9.10. Funny thing is it worked fine, until I added another drive (and removed it after). I restored my original fstab backup, but the extra drive link remained.

Also found various other posts, with no solution, and even a [bug that seems similar]("https://bugs.launchpad.net/ubuntu/+source/gnome-vfs2/+bug/42017").

To show the rest what it looks like, the drive 'disk' appears twice in Nautilus. 
[[IMG]http://img193.imageshack.us/img193/4148/browserl.png[/IMG]](http://img193.imageshack.us/i/browserl.png/)

The first instance (with eject button) is mounted and working, clicking on the second instance gives us *'mount: /dev/sda1 already mounted or /media/disk busy; mount: according to mtab, /dev/sda1 is already mounted on /media/disk'*

fstab only lists this drive once, shown here (its sda1):

```

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
[COLOR="Blue"]# / was on /dev/sda1 during installation
UUID=71123120-9dbc-4eb5-ac09-dc81cbfc44a4 /               ext4    errors=remount-ro 0   [/COLOR]    1
# /home was on /dev/sda6 during installation
UUID=f7218493-e7e4-4e59-b77b-8615050c1f96 /home           ext4    defaults        0       2
# swap was on /dev/sda5 during installation
UUID=a9b2d34c-a410-4a48-876a-7277d6a999d6 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
UUID=c31ee921-0f81-4fb8-9ba5-2785b0766876 /media/disk     auto    user 0 3

```

Note: if I comment out the fstab line for 'disk' sda1, and reboot, the drive shows only one link in Nautilus, but it doesn't auto mount at startup.

Any ideas anyone can give us? :)

---

### Post by rossmoore on 2010-02-01
Can't help you, but I have the same issue with my eSata connected external drive. I've added it to fstab because I keep it permanently connected and I have various other things depending on the location in /media (I share it via samba) over my wifi network...).

I can pick the right one, the one that's mounted, but it does look a bit messy and a bit like a "hundred cuts" bug.

---

### Post by phelge on 2010-02-01
Hi

Same issue for me, but here is a workaround that worked for me :
[https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/442130](https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/442130)

Use /dev/disk/by-uuid prefix instead of UUID=

---

### Post by Cas07 on 2010-02-01
> **phelge said:**
> Hi
Use /dev/disk/by-uuid prefix instead of UUID=

Thanks!

---

### Post by robawalsh on 2012-06-04
> **phelge said:**
> Hi

Same issue for me, but here is a workaround that worked for me :
[https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/442130](https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/442130)

Use /dev/disk/by-uuid prefix instead of UUID=

I have the same issue. 

I keep seeing this "Use /dev/dosl/by-uuid", but **for what?**

Editing the fstab file?

---

