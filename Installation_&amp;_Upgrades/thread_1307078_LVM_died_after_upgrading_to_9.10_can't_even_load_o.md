---
title: "LVM died after upgrading to 9.10 can't even load operating system anymore :("
date: 2009-10-30
forum: Installation &amp; Upgrades
---

### Post by Captain_Glen on 2009-10-30
I just tried to upgrade my ubuntu desktop to 9.10.  Now it won't even boot. :(

It just drops to the Busy Box Shell and gives errors about my LVM.

It says:

There appears to one or more degraded LVM volumes, and your root device may depend on the LVM volumes being online.  One or more of the following LVM volumes are degraded"
Reading all physical volumes.  This may take a while...
Couldn't find device with uuid 'my uuid'.
Couldn't find all physical volumes for volume group glen-desktop.
Couldn't find device with uuid 'my uuid'.
Couldn't find all physical volumes for volume group glen-desktop.
Volume group "glen-desktop" not found
Gave up waiting for root device.  Common problems"
- Boot args (cat /proc/cmdline)
- Check rootdelay = (did the system wait long enough?)
- Check root = (did the system wait for the right device?)
-Missing modules (cat /proc/modules; ls /dev)
ALERT! /dev/mapper/glen--dekstop-root does not exist.  Dropping to a shell!

How do I repair my degraded LVM?

Any help would be appreciated.

---

### Post by Captain_Glen on 2009-11-17
Okay I have found out what the problem was and fixed it.

For anyone having the same problem here is the solution.

There is a bug in 9.10 that means if you had an encrypted home directory and you try to upgrade you won't be able to boot.

If you want to recover your data here is how to do it:

If you have encrypted data in an LVM you have to mount the LVM before you can get to your home directory.  If you do not have LVM skip this next part
[INDENT]
Boot a live CD (9.04 or 9.10.  Earlier versions won't work)

Type the following commands into the terminal and press enter.

```
sudo apt-get install lvm2

sudo pvscan
```

You should see some physical volumes

```
vgchange -a y
```

This should activate your volume group.

now mount your volume group

```
mount /dev/your_volume_group/your_root_logical_volume /mnt
```

mine was mount /dev/glen-desktop/root /mnt

[/INDENT]

Okay so now you just have to decrypt your files.  There a few tutorials on how to do this.  But a lot of them don't work.  Here is one that worked for me: [http://blog.dustinkirkland.com/2009/03/mounting-your-encrypted-home-from.html]("http://blog.dustinkirkland.com/2009/03/mounting-your-encrypted-home-from.html")

The first line is just mounting your hdd partition.  You must specify your hard drive partition.  If you had LVM, skip this line, as you have already mounted your hdd partition.  If you don't have LVM and you don't know what your hdd partition is called you can look it up in gparted.

Also when it says su - kirkland,  replace kirkland with your username.  Your phasephrase is whatever you typed in when you setup your encrypted home directory.

I found the easiest way to get my computer back up and running again once I had retrieved my data was to do a fresh install of 9.10.  Here is how to do it:[ http://ubuntuforums.org/showthread.php?t=1316369]("http://ubuntuforums.org/showthread.php?t=1316369")

---

