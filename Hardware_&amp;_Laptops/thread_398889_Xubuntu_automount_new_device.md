---
title: "Xubuntu automount new device"
date: 2007-04-01
forum: Hardware &amp; Laptops
---

### Post by jjalocha on 2007-04-01
I'm trying to make the built-in SD Card reader work in [my notebook]("http://ubuntuforums.org/showthread.php?t=367898") under Xubuntu. So far, I've been able to [get the device working]("http://ubuntuforums.org/showpost.php?p=2383785&postcount=39") as [FONT="Fixedsys"]/dev/mmcblk0p1[/FONT] and mount it manually. But I would like to have it automatically mounted, just like the USB drives.

It has been asked quite many times in different forums, but I couldn't find how automount works under xubuntu.

I've added the following line to [FONT="Fixedsys"]/etc/pmount.allow[/FONT] with no result:

```

/dev/mmcblk0p1 mmc

```

I tryed to look for my device in the [FONT="Fixedsys"]/etc/udev/rules.d/[/FONT] directory, but I didn't understand a single line of the [FONT="Fixedsys"]20-names.rules[/FONT] and [FONT="Fixedsys"]40-permissions.rules[/FONT] files.

I suppose it has nothing to do with the [FONT="Fixedsys"]/etc/fstab[/FONT] file, since that manages mount at boot time(?). The only devices in fstab are: [FONT="Fixedsys"]proc[/FONT], some [FONT="Fixedsys"]sda[/FONT] partitions (my hard drive), and the cd drive as [FONT="Fixedsys"]hda[/FONT].

Output of [FONT="Fixedsys"]mount[/FONT] with the SD Card inserted:

```

/dev/sda2 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.17-11-generic/volatile type tmpfs (rw)
/dev/sda4 on /home type ext3 (rw)

```

---

### Post by jjalocha on 2007-04-02
bump...

(I've been trying to understand why CD's and USB drives appear "magigally" in Thunar and the Desktop ("Allow Xfce to manage the desktop"), but why it doesn't for the "freshly installed" SD Card reader. I'm using Xubuntu Edgy.)

---

### Post by jjalocha on 2007-04-03
Sadly enough, this seems not to be a configuration issue, as I had supposed, but a bug. It is reported as [Xfce Bug 2652]("http://bugzilla.xfce.org/show_bug.cgi?id=2652"), and has been solved in later versions. I hope it's included in Feisty.

---

### Post by dummy_load on 2007-12-23
It looks like the bug has been fixed, but no flash or external drives are showing up.  Does anyone know how to enable this?

---

