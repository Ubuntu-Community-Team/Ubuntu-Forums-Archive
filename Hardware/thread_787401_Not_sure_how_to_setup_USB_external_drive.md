---
title: "Not sure how to setup USB external drive"
date: 2008-05-08
forum: Hardware
---

### Post by virbonus on 2008-05-08
I am a relative newbie to Linux but not to computers and networking. I installed Ubuntu 8.04 Server on a Dell with the desire to create NAS for my Windows network. I have Samba correctly (I think) installed (at least I can see the Linux box on my network. I want to be able to plug in several USB drives and use two of them as backup drives which I can take home and swap out with others. I want the third as a permanently attached file server. I'm happy to have all formatted as EXT2 or EXT3 or whatever is best re. Linux as long as they are usable on my network. My first problem is that I don't if this is workable. The second is that I have been unable to figure out how to mount the USB drives. Any suggestions, help, comments would be appreciated.

---

### Post by kidders on 2008-05-10
Hi there,

I suppose the main problem you're likely to have is finding a graceful way to disconnect your shared drives, when you want to take them home with you. Perhaps something like this would work for you...[LIST]
[*]Prepare two Samba configurations, one set up to share filesystems on your two removable disks, and the other without them.
[*]Create a script that sends a Windows network message to your users warning them they're about to lose access to your shared filesystems, waits a few minutes, shuts Samba down, swaps configuration files, restarts Samba, and unmounts your backup filesystems.
[*]Install the script somewhere sensible (eg /usr/local/sbin), so you can get at it easily.
[/LIST]
I suppose you'll know best what approach suits your particular circumstances.

Regarding setting up the sharing in the first place...

With most sharing protocols (Samba included), sharing removable filesystems works by pointing them at a directory (eg /mnt/backup1), where your filesystem is mounted. The problem arises when your USB disks are not plugged in ... Samba will continue to share the mount point, and allow users to write to your root filesystem, which is why I suggested using two configuration files.

To set your disks up in the first place, I always recommend using **cfdisk** (a reliable, easy-to-understand disk partitioner) and **mkfs**. You could...[LIST]
[*]Plug in your USB disk.
[*]Use **dmesg | tail** to see that it's been recognised, and to be sure you know what /dev node got assigned to it. With disk partitioners, there's always at least a *small* chance you'll accidentally repartition the wrong thing [insert evil cackle] ... so it's a good idea to get into the habit of actually checking (rather than guessing) the correct /dev path to use.
[*]Once you're sure, run **sudo cfdisk /dev/sd[?]** and erase & re-create the partition table, whatever way you'd like.
[*]Once you're done, you can disconnect & reconnect the disk, or (if it's safe to do so) run **partprobe** to re-probe your disk configuration.
[*]Create filesystems in the partition(s) you configured with **mkfs**. Ext2 is not normally an appropriate choice for a removable device, but depending on the size & purpose of your new filesystem(s), Ext3 might be.
[*]Then you're essentially done. You can mount your new filesystem somewhere & point Samba at it.
[/LIST]

There are a few additional issues to consider.

**I - File access control**
Samba can't override filesystem-level permissions set on the places you're sharing. Normally, when you create a new filesystem & mount it for the first time, root is the only user that can write to it, which means Samba (and hence your remote users) won't be able to. You'll need to strike a balance that's permissive enough not to cause problems for people using your shares, but no so lax as to present a security problem. The **chmod** and **chown** commands will help you there.

**II - Persistent configuration**
Depending on how often you reboot your server, this may or may not be terribly important. With internal hard disks, BIOS is normally in control of disk order, which means your Linux always gets a pretty consistent picture of which device is your "first" disk, "second" disk, and so on. As a result, you can normally write lines like this into /etc/fstab, and trust that they will always work...```
/dev/sdb2 / ext3 defaults 0 1
```
USB devices are less clear-cut, and tend to re-order themselves depending on whether they were connected when you booted, and if not, the order in which you subsequently connected them. As a result, disconnecting and reconnecting your USB disks will immediately create problems. If that's not something you know how to deal with, I can give you some suggestions. Particularly on server boxes, it's nice to be able to reboot without having to wonder "Will my Samba still work when I'm done?".

Anyhow, I hope this gives you some ideas.

---

