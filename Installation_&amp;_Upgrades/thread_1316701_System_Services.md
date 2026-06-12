---
title: "System Services"
date: 2009-11-06
forum: Installation &amp; Upgrades
---

### Post by proxess on 2009-11-06
After upgrading, the "Services" application disappeared. The one that permitted to switch on and off System Services. Is there any way of getting it back? Or, what is the new equivalent?

---

### Post by dstew on 2009-11-06
I am not sure, but the [gnome-system-tools]("http://packages.ubuntu.com/karmic/gnome-system-tools") package says it includes services management. You might try installing this. I note you have a "minimal 9.10" system, maybe this did not get installed.

---

### Post by proxess on 2009-11-06
> **dstew said:**
> I am not sure, but the [gnome-system-tools]("http://packages.ubuntu.com/karmic/gnome-system-tools") package says it includes services management. You might try installing this. I note you have a "minimal 9.10" system, maybe this did not get installed.

I have a minimal 9.10 on my Notebook, I'm talking about my laptop which has an upgrade from 9.04 to 9.10. I have that package installed, but that's just an old description.

*Bump*

---

### Post by lucaa on 2011-01-17
I have the same issue in ubuntu 10.10, I've been looking like crazy for that "Services" managing that gnome-system-tools is advertising. Why isn't it in there? Is there an alternative to it?

---

### Post by MSPdwalt on 2011-01-17
> **lucaa said:**
> I have the same issue in ubuntu 10.10, I've been looking like crazy for that "Services" managing that gnome-system-tools is advertising. Why isn't it in there? Is there an alternative to it?

In linux there are several [runlevels]("http://en.wikipedia.org/wiki/Runlevel") (for you windows people think of them as kind of like hardware profiles)

In these runlevels you configure which services are started and which are not

runlevel 5 is the default for desktop linux

open a terminal: 

```
dwalter@dwalter-E6410:~$ ls -l /etc/rc5.d/
total 4
lrwxrwxrwx 1 root root  18 2010-11-22 10:38 K08vmware -> /etc/init.d/vmware
-rw-r--r-- 1 root root 677 2010-03-30 02:17 README
lrwxrwxrwx 1 root root  18 2010-10-14 13:11 S19tpconfig -> ../init.d/tpconfig
lrwxrwxrwx 1 root root  18 2010-11-22 10:38 S19vmware -> /etc/init.d/vmware
lrwxrwxrwx 1 root root  20 2010-10-01 05:00 S20fancontrol -> ../init.d/fancontrol
lrwxrwxrwx 1 root root  20 2010-10-01 05:00 S20kerneloops -> ../init.d/kerneloops
lrwxrwxrwx 1 root root  14 2010-11-02 10:30 S20nscd -> ../init.d/nscd
lrwxrwxrwx 1 root root  27 2010-10-01 05:00 S20speech-dispatcher -> ../init.d/speech-dispatcher
lrwxrwxrwx 1 root root  17 2010-12-28 14:45 S20winbind -> ../init.d/winbind
lrwxrwxrwx 1 root root  16 2010-10-07 15:10 S20xinetd -> ../init.d/xinetd
lrwxrwxrwx 1 root root  19 2010-10-01 05:00 S25bluetooth -> ../init.d/bluetooth
lrwxrwxrwx 1 root root  14 2010-10-01 05:00 S50cups -> ../init.d/cups
lrwxrwxrwx 1 root root  20 2010-10-01 05:00 S50pulseaudio -> ../init.d/pulseaudio
lrwxrwxrwx 1 root root  15 2010-10-01 05:00 S50rsync -> ../init.d/rsync
lrwxrwxrwx 1 root root  15 2010-10-01 05:00 S50saned -> ../init.d/saned
lrwxrwxrwx 1 root root  16 2010-12-22 09:11 S60motion -> ../init.d/motion
lrwxrwxrwx 1 root root  19 2010-10-01 05:00 S70dns-clean -> ../init.d/dns-clean
lrwxrwxrwx 1 root root  18 2010-10-01 05:00 S70pppd-dns -> ../init.d/pppd-dns
lrwxrwxrwx 1 root root  24 2010-10-01 05:00 S90binfmt-support -> ../init.d/binfmt-support
lrwxrwxrwx 1 root root  22 2010-10-01 05:00 S99acpi-support -> ../init.d/acpi-support
lrwxrwxrwx 1 root root  21 2010-10-01 05:00 S99grub-common -> ../init.d/grub-common
lrwxrwxrwx 1 root root  18 2010-10-04 08:33 S99nxsensor -> ../init.d/nxsensor
lrwxrwxrwx 1 root root  18 2010-10-04 08:35 S99nxserver -> ../init.d/nxserver
lrwxrwxrwx 1 root root  18 2010-10-01 05:00 S99ondemand -> ../init.d/ondemand
lrwxrwxrwx 1 root root  18 2010-10-01 05:00 S99rc.local -> ../init.d/rc.local
```

This shows you all of your daemons/services at runlevel5 notice they link to startup scrips in /etc/init.d

Say I don't have Bluetooth so I don't need the Bluetooth service running.

```
mv /etc/rc5.d/S25bluetooth K25bluetooth
```

This renames the link with a capital K instead of a capital S so the service will not be started on next boot.

Warning: be careful, this may be an old school method of doing this, but it's worked for me without problems.  Make sure you just change the S to a K incase you want the service again later.

---

