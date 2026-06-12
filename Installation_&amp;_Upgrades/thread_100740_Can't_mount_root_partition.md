---
title: "Can't mount root partition"
date: 2005-12-08
forum: Installation &amp; Upgrades
---

### Post by bertilow on 2005-12-08
Trying to solve a problem with sudo-ing I've managed to screw my system up so that there is no root account and no one is in the sudoers file.

As I understand the solution is to boot from a live CD, and then correct things that way (editing the password files or the sudoers file).

I've tried to do that, but somehow I can't manage to mount the root partition of the hard drive.

I can mount the home partition like this:

  sudo mount -t ext3 /dev/hda6 /mnt
  ls /mnt
  bertilow  lost+found

But mounting the root partition (which should be "hda2") doesn't work:

  ubuntu@ubuntu:/$ sudo mount -t ext3 /dev/hda2 /mnt
  mount: wrong fs type, bad option, bad superblock on /dev/hda2,
       missing codepage or other error
       (aren't you trying to mount an extended partition,
       instead of some logical partition inside?)
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

Here's what fdisk says:

sudo fdisk -l

Disk /dev/hda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
  /dev/hda1   *           1         851     6835626   83  Linux
  /dev/hda2             852        4864    32234422+   5  Extended
  /dev/hda5             852        1023     1381558+  82  Linux swap / Solaris
  /dev/hda6            1024        4864    30852801   83  Linux

Perhaps the problem is that "/dev/hda2" is an extended partition. But how do I mount it then?

What am I doing wrong? Please help.

I use Breezy Kubuntu.

---

### Post by towsonu2003 on 2005-12-08
I think your root partition is /dev/hda1

The extended partition holds logical(?) partitions. so this
/dev/hda2 **852 4864** 32234422+ 5 Extended

holds these two: 
/dev/hda5 **852** 1023 1381558+ 82 Linux swap / Solaris
/dev/hda6 1024 **4864** 30852801 83 Linux

where (guessing) /dev/hda5 is swap and /dev/hda6 is /home

---

### Post by bertilow on 2005-12-08
[QUOTE=towsonu2003]I think your root partition is /dev/hda1[/QUOTE]

Thank you! That was it. Somehow I got confused.

So, now I'm back in charge. But now I still have the original problem: Sudo never asks me for my password. Never. I can start e.g. synaptic, or go into administrator mode in kde system settings, without giving my password. The same happens in Gnome.

My sudoers file has this:

Defaults !lecture,tty_tickets,!fqdn
root ALL= (ALL) ALL
%admin ALL= (ALL) ALL

That ought to mean that I need to provide the password. But no. In the console "sudo synaptic" is enough. No password needed. "sudo -k" does not change anything.

This seems so insecure. What can I do?

I think this all started when I chose "expert mode" in the installation: A root account was created, and originally the ordinary user wasn't in the sudoers file. I've managed to put myself in the sudoers file, but the password problem remains.

What can I do? Please help.

---

