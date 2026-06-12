---
title: "Problem with telinit, rc scripts not executed?"
date: 2008-07-25
forum: General Help
---

### Post by frj on 2008-07-25
EDIT: Rebooted the system recently and tried again, seems to work as desired now. Will update thread if problem still exist.

Hi,

I have configured /etc/rc4.d/ to be one of my custom runlevels. I can boot into runlevel 4, by different grub (menu.lst) entries. The runlevel works as intended.

But i would like to be able to switch runlevel without rebooting. If i boot into default runlevel (2) and then execute ```
sudo telinit 4
```My runlevel will change, i can see it if i execute runlevel, 4 is marked as current and 2 as previous. But the scripts i want to stop in runlevel 4 is not stopped. Gdm and Bluetooth are two scripts that should stop in runlevel 4, but they are still running. 
If i do```
sudo /etc/init.d/bluetooth stop
sudo /etc/init.d/gdm stop
```Then "ps aux | grep -i bluetooth" will not show anything, though gdm still seem to be running. 

Any clues on what i need to do in order to have the stop scripts run? Output from: ls -l /etc/rc4.d/```
lrwxrwxrwx 1 root root  21 2008-07-11 20:22 K01laptop-mode -> ../init.d/laptop-m
ode
lrwxrwxrwx 1 root root  17 2008-07-11 20:24 K02usplash -> ../init.d/usplash
lrwxrwxrwx 1 root root  13 2008-07-11 20:24 K70gdm -> ../init.d/gdm
lrwxrwxrwx 1 root root  19 2008-07-11 20:25 K75bluetooth -> ../init.d/bluetooth
lrwxrwxrwx 1 root root  20 2008-07-11 20:24 K75pulseaudio -> ../init.d/pulseaudi
o
lrwxrwxrwx 1 root root  16 2008-07-11 20:23 K80apport -> ../init.d/apport
lrwxrwxrwx 1 root root  16 2008-07-11 20:17 K80cupsys -> ../init.d/cupsys
-rw-r--r-- 1 root root 556 2008-04-19 07:05 README
lrwxrwxrwx 1 root root  19 2008-07-11 20:26 S01policykit -> ../init.d/policykit
lrwxrwxrwx 1 root root  17 2008-07-11 20:22 S05vbesave -> ../init.d/vbesave
lrwxrwxrwx 1 root root  15 2008-07-11 20:10 S10acpid -> ../init.d/acpid
lrwxrwxrwx 1 root root  18 2008-07-11 20:09 S10sysklogd -> ../init.d/sysklogd
lrwxrwxrwx 1 root root  34 2008-07-11 20:15 S10xserver-xorg-input-wacom -> ../in
it.d/xserver-xorg-input-wacom
lrwxrwxrwx 1 root root  15 2008-07-11 20:09 S11klogd -> ../init.d/klogd
lrwxrwxrwx 1 root root  14 2008-07-11 20:25 S12dbus -> ../init.d/dbus
lrwxrwxrwx 1 root root  13 2008-07-13 13:59 S16ssh -> ../init.d/ssh
lrwxrwxrwx 1 root root  23 2008-07-13 14:44 S17mysql-ndb-mgm -> ../init.d/mysql-
ndb-mgm
lrwxrwxrwx 1 root root  22 2008-07-11 20:25 S18avahi-daemon -> ../init.d/avahi-d
aemon
lrwxrwxrwx 1 root root  19 2008-07-13 14:44 S18mysql-ndb -> ../init.d/mysql-ndb
lrwxrwxrwx 1 root root  15 2008-07-13 14:44 S19mysql -> ../init.d/mysql
lrwxrwxrwx 1 root root  14 2008-07-11 20:22 S20apmd -> ../init.d/apmd
lrwxrwxrwx 1 root root  28 2008-07-12 14:26 S20dkms_autoinstaller -> ../init.d/d
kms_autoinstaller
lrwxrwxrwx 1 root root  22 2008-07-11 20:24 S20hotkey-setup -> ../init.d/hotkey-
setup
lrwxrwxrwx 1 root root  23 2008-07-11 20:10 S20nvidia-kernel -> ../init.d/nvidia
-kernel
lrwxrwxrwx 1 root root  19 2008-07-11 20:24 S20powernowd -> ../init.d/powernowd
lrwxrwxrwx 1 root root  15 2008-07-11 20:22 S20rsync -> ../init.d/rsync
lrwxrwxrwx 1 root root  17 2008-07-12 14:20 S20sysstat -> ../init.d/sysstat
lrwxrwxrwx 1 root root  16 2008-07-11 20:25 S24dhcdbd -> ../init.d/dhcdbd
lrwxrwxrwx 1 root root  13 2008-07-11 20:26 S24hal -> ../init.d/hal
lrwxrwxrwx 1 root root  20 2008-07-23 18:21 S25alsa-utils -> ../init.d/alsa-util
s
lrwxrwxrwx 1 root root  17 2008-07-11 20:22 S89anacron -> ../init.d/anacron
lrwxrwxrwx 1 root root  13 2008-07-11 20:22 S89atd -> ../init.d/atd
lrwxrwxrwx 1 root root  14 2008-07-11 20:22 S89cron -> ../init.d/cron
lrwxrwxrwx 1 root root  17 2008-07-13 14:44 S91apache2 -> ../init.d/apache2
lrwxrwxrwx 1 root root  22 2008-07-11 20:22 S99acpi-support -> ../init.d/acpi-su
pport
lrwxrwxrwx 1 root root  18 2008-07-11 20:09 S99rc.local -> ../init.d/rc.local
lrwxrwxrwx 1 root root  19 2008-07-11 20:09 S99rmnologin -> ../init.d/rmnologin
```

Frj

---

