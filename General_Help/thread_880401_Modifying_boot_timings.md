---
title: "Modifying boot timings"
date: 2008-08-05
forum: General Help
---

### Post by jamesdcarroll on 2008-08-05
I installed an app that starts at runtime (Oracle XE).  It takes a little longer to start than apparently Ubuntu likes because it kinks out the pretty orange progress bar and gives me list of things as it boots. I know its a minor thing, but I just kinda wish it didn't do that. 

Is a way to tell Ubuntu to wait longer?  Is there someplace where what gets loaded is kept? I looked in /boot but I didn't see anything.

Thanks!!

---

### Post by p_quarles on 2008-08-05
I'm not completely clear on what you're describing. Do you mean the splash screen (i.e., the progress bar and accompanying graphics) is completely gone, or that it finishes before the boot sequence is done?

Second, can you post the output of the following?:
```
ls /etc/rc2.d
```

---

### Post by jamesdcarroll on 2008-08-05
Yes, the Ubuntu graphic/splash and progress bar disappear and are replaced with a black and white scroll of things that are (it seems) starting up. They all say ok and the system boots/runs fine.

The output that you requested is:

README                       S20atieventsd      S25bluetooth
S01policykit                 S20cupsys          S25pulseaudio
S05vbesave                   S20hotkey-setup    S30gdm
S10acpid                     S20nvidia-kernel   S89anacron
S10powernowd.early           S20oracle-xe       S89atd
S10sysklogd                  S20powernowd       S89cron
S10xserver-xorg-input-wacom  S20rsync           S91apache2
S11klogd                     S20samba           S98usplash
S12dbus                      S20vboxdrv         S99acpi-support
S17portmap                   S20vboxnet         S99laptop-mode
S18avahi-daemon              S20virtualbox-ose  S99rc.local
S20apmd                      S24dhcdbd          S99rmnologin
S20apport                    S24hal             S99stop-readahead

---

### Post by pauper on 2008-08-05
```
sudo mv /etc/rc2.d/S98usplash /etc/rc2.d/S99usplash
```

But console-screen.sh will be rerun and there are 5 more scripts queued at the
end so you still might catch some kernel messages.

---

