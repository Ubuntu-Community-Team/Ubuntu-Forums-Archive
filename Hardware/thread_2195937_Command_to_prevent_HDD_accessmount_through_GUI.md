---
title: "Command to prevent HDD access/mount through GUI"
date: 2013-12-27
forum: Hardware
---

### Post by Dominicus on 2013-12-27
I'm running Ubuntu 12.04.3 on a LiveUSB with persistent file system.

Although the "Try Ubuntu" LiveUSB boot doesn't mount the HDD, by default it will query for its existence and, since it's a LiveUSB, the HDD is listed in the file explorer Nautilus and the user has capability to mount the HDD through the interface.

I wish to enter a startup command line such that existing HDD(s) are not listed or visible in Nautilus GUI by default.  Other USB or CD/DVD devices are OK to automount, but I wish HDD access be disabled, or at least require knowledgeable terminal access to mount.

---

### Post by tgalati4 on 2013-12-27
I don't know of a sure-fire way to do that.  As long as the hard disk is connected to power and a cable, the operating system will detect it.  So you would need to disable hard disk detection during boot--and not break the rest of the system.  Is this a desktop or laptop computer?  If this is a desktop computer, then install a pull-out cradle.  You can't mount a drive that is not physically in the system.

There is some mounting control using FUSE--filesystem in userspace:

```
man fuse
```

And some by-user policy control in /etc/fuse.conf, but I don't know if that provides the bullet-proof lockdown of a disk drive from a live session.

---

### Post by Dominicus on 2013-12-27
Since LiveUSB creates an admin-level account, anyone with enough knowledge of Linux should be able to open a terminal and mount the HDD through command line.

For my use purpose, which is to setup a LiveUSB OS environment that doesn't mount the PC boot HDD, it'd be sufficient to just get Nautilus GUI to hide listing any connected HDD by default.  This way, users not familiar with Linux won't stumble upon their HDD, and get curious clicking on the icon, which will automatically mount it with single-click.

It's not practical to ask users to unplug or remove HDD's for this purpose, as this would severly limit the user experience.

With my limited ubuntu experience, I thought of a couple places to do this:

First: the ubuntu persistent LiveUSB uses syslinux.cfg to control some aspects of the boot process for LiveUSB:
```
kernel /casper/vmlinuz
append  file=/cdrom/preseed/ubuntu.seed boot=casper persistent initrd=/casper/initrd.lz quiet splash noprompt --
```
I'm not familiar with the boot options for casper/vmlinuz kernel, but wondered if there's an option to hide or disable the existing hdd there.

Second, I configured the LiveUSB to run the following startup command to shut down networking by default:
```
nmcli nm enable false
```
I wondered if there might be a similar type of command that would get Nautilus to "forget" any detected HDD's, and just not list them, while linux still auto-mounts USB's or CD/DVD's media.

Thanks

---

### Post by Dominicus on 2013-12-27
Found this post, seems related if not inverse to what I wish to accomplish:
[http://zurlinux.com/?p=35](http://zurlinux.com/?p=35)

---

### Post by Dominicus on 2013-12-28
Found a disk-specific solution that works using a "Disks" app in Ubuntu 13.10, but apparently the GUI is different in 12.04.3, which doesn't show mount options:
[http://ubuntuforums.org/showthread.php?t=2183447](http://ubuntuforums.org/showthread.php?t=2183447)

Since udisks is implemented in 12.04, I still have hope there's a way to accomplish similar to what Disks is doing.

---

