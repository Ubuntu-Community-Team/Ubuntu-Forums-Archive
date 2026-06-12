---
title: "anything i can change to make boot up faster"
date: 2008-08-12
forum: General Help
---

### Post by markp1989 on 2008-08-12
im trying to have my laptop boot as fast as possible, i know that 15 sec is fast as it is. i just want to see if i can get it any faster

running from a 266x CF card 

i started from a cli install , installed openbox and other programs i needed

looking at boot chart, i noticed that udevd spends most of its time as a "zombie process" is there any ways i can make udevd more efficient to speed up boot time even more?

---

### Post by linux_tech on 2008-08-12
I'm not sure if you can do anything with udev in Ubuntu version but
there are other ways to speed up performance; removing unnecessary 
services, recompiling kernal, etc. In other versions of Linux you can change 
the way udev works.

---

### Post by markp1989 on 2008-08-12
> **linux_tech said:**
> You can edit the /etc/rc.sysinit and start udev earlier in the process.

You can also comment out items such as RAID if you do not use them.

I'd make a back up first.

that file doesnt exist :S 

i already have 2 backups lol

---

### Post by lukjad on 2008-08-12
The Ubuntu devs should really make a version called Rebuntu. All it does is reboot quickly. :D

On a more serious note, do you have any processes that are running that you don't need? I don't need Bluetooth and a few other services and that cut down my boot time by 3 seconds.

---

### Post by kerry_s on 2008-08-12
> **markp1989 said:**
> im trying to have my laptop boot as fast as possible, i know that 15 sec is fast as it is. i just want to see if i can get it any faster

running from a 266x CF card 

i started from a cli install , installed openbox and other programs i needed

looking at boot chart, i noticed that udevd spends most of its time as a "zombie process" is there any ways i can make udevd more efficient to speed up boot time even more?

try a debian custom install, debian is much faster than ubuntu.

etch net installer:
[http://cdimage.debian.org/debian-cd/4.0_r4a/i386/iso-cd/debian-40r4a-i386-businesscard.iso](http://cdimage.debian.org/debian-cd/4.0_r4a/i386/iso-cd/debian-40r4a-i386-businesscard.iso)

lenny net installer:
[http://cdimage.debian.org/cdimage/lenny_di_beta2/i386/iso-cd/debian-LennyBeta2-i386-businesscard.iso](http://cdimage.debian.org/cdimage/lenny_di_beta2/i386/iso-cd/debian-LennyBeta2-i386-businesscard.iso)

at package selection, just uncheck everything, that will give you just the base to build on. from there it's the same as you did with the ubuntu cli install, just log in as root and build.

also i just noticed your using elevator=deadline, i recommend you go with ext2 file system and elevator=noop instead.

---

### Post by markp1989 on 2008-08-13
> **lukjad007 said:**
> The Ubuntu devs should really make a version called Rebuntu. All it does is reboot quickly. :D

On a more serious note, do you have any processes that are running that you don't need? I don't need Bluetooth and a few other services and that cut down my boot time by 3 seconds.

here is a list of the services that enabled/disabled , anything that is enabled that i can disable ? 
```
mark@amiloprov2030:~$ cd /etc/rcS.d
mark@amiloprov2030:/etc/rcS.d$ ls
K01readahead                        S11hwclock.sh
K39readahead-desktop                S11mountdevsubfs.sh
K39ufw                              S15module-init-tools
K45dns-clean                        S17procps
K45pppd-dns                         S20checkroot.sh
K45waitnfs.sh                       S22mtab.sh
K46mountnfs-bootclean.sh            S30checkfs.sh
K51console-setup                    S35mountall.sh
K87pcmciautils                      S36mountall-bootclean.sh
K94keyboard-setup                   S37mountoverflowtmp
K99linux-restricted-modules-common  S37udev-finish
README                              S40networking
S01mountkernfs.sh                   S70x11-common
S02hostname.sh                      S80bootmisc.sh
S08hwclockfirst.sh                  S85urandom
S08loopback                         S90console-screen.sh
S09udev
mark@amiloprov2030:/etc/rcS.d$ cd /etc/rc4.d
mark@amiloprov2030:/etc/rc4.d$ ls
K01rc.local                  K20nvidia-kernel   K99policykit  S24hal
K01rmnologin                 K20rsync           README        S30gdm
K10xserver-xorg-input-wacom  K20wirelessfix.sh  S10acpid      S99stop-bootchart
K11atd                       K89klogd           S12dbus
K11cron                      K90sysklogd        S24dhcdbd
mark@amiloprov2030:/etc/rc4.d$ 

```

---

### Post by markp1989 on 2008-08-25
managed to get boot time down to 14 sec.

by getting rid of gnome-power-manager and hal, now i just need a light weight battery applet to replace it 


udev is still a zombie for a large fraction of boot time

---

