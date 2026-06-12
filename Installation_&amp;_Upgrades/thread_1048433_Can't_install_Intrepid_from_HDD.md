---
title: "Can't install Intrepid from HDD"
date: 2009-01-23
forum: Installation &amp; Upgrades
---

### Post by jamadagni on 2009-01-23
I am trying to install Kubuntu Intrepid to my Compaq Presario laptop using the HDD install method of downloading the appropriate initrd and vmlinuz files from

[http://archive.ubuntu.com/ubuntu/dists/intrepid/main/installer-i386/current/images/hd-media/](http://archive.ubuntu.com/ubuntu/dists/intrepid/main/installer-i386/current/images/hd-media/)

The GRUB entry is:

title           Install Kubuntu
root            (hd0,2)
kernel          /hdinst-vmlinuz vga=normal ramdisk_size=14972 root=/dev/rd/0 rw --
initrd          /hdinst-initrd

But after "Scanning disks" and starting the partitioner, I get an empty list of partitions (i.e. no partitions indicated). Upon pressing Ctrl+Alt+F4, I get the installer's messages:

main-menu: INFO: Menu item 'partman-base' selected
partman: No matching physical volumes found

I don't understand why this is happening. I have installed upto Intrepid Alpha 6 using this method without any problems. Now with Intrepid final I am not able to do this.

Can anyone help me with this problem please?

---

### Post by SJP on 2009-02-12
Jamadagni, did you find a solution to this?

I too am having the same problem with a Xubuntu Intrepid hdd install.

Syslog:
Feb 12 09:30:31 partman:   No matching physical volumes found
Feb 12 09:30:31 partman:   Reading all physical volumes.  This may take a while...

But then it just sits there for ages.

---

### Post by jamadagni on 2009-02-13
Did not find a solution in Intrepid, but Jaunty does not have this problem.

---

### Post by jamadagni on 2009-04-02
Well looks like Jaunty has this problem too. I am trying with Jaunty beta and don't get the partitioner.

I found [bug 297492](https://bugs.launchpad.net/ubuntu/+bug/297492) in Launchpad and added my comments to it.

---

