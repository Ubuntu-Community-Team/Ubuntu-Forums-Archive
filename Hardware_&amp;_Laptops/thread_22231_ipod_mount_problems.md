---
title: "ipod mount problems"
date: 2005-03-26
forum: Hardware &amp; Laptops
---

### Post by antonymous on 2005-03-26
So I've installed kubuntu on my first ever laptop (actually, it's a friend's laptop), and she loves it, except for the fact that apparently I'm too incompetent to hook up the ipod.  I tried all the steps from the README file from the GTKpod site and it still won't mount.  On to specifics...

It's a 4G 20gig ipod that I'm attempting to connect through USB.  It's already windows-formatted.  From the GTKpod readme, I have done the following things (from the section on installing on a 2.6 kernel):

1.  Made sure hotplug, udev, and autofs were installed.  Installed whichever wasn't included by default.

2.  Added the line of code
 
BUS="scsi", SYSFS{model}="iPod            ", KERNEL="sd?2", NAME="%k", SYMLINK="ipod"
to the beginning of the /etc/udev/udev.rules file.
3.  Added the line of code

/var/autofs/removable   /etc/auto.removable     --timeout=2,sync,nodev,nosuid,gid=autofs,umask=007
to /etc/auto.master

4.  The next thing on the readme told me to add

ipod            -fstype=vfat            :/dev/ipod
and
ln -s /var/autofs/removable/ipod /mnt/ipod

to /etc/auto.removable,  I didn't find such a file, so I just created one.

Also, being relatively new to command-line type stuff, a short explanation of what exactly I've been doing (and why it doesn't work) would be helpful - I'm trying to make this a learning experience...thanks for your help!

Anton

in the alternative, could you please point me to a better HOWTO?  And hopefully I haven't screwed up any files that were important or anything...

---

