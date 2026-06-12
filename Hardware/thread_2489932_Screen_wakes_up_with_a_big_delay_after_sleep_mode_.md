---
title: "Screen wakes up with a big delay after sleep mode on Ubuntu 22.04 Dell XPS 13 9310"
date: 2023-08-15
forum: Hardware
---

### Post by nils-vldj on 2023-08-15
I've been using Ubuntu 22.04 on my Dell XPS 13 9310 for more than one year now without any problem. [But now I'm facing two !]("https://ubuntuforums.org/showthread.php?t=2489931") But since a few days, when I turn on the sleep mode (manually or by  closing my computer) and then try to wake up my computer, it will do it  but after a very long minute of black screen even if my keyboard  succeeded in that wake-up. I'm using Wayland, I tried on X11, but there is the same problem. Do you think I can repair my sleep mode-wake up without reinstalling the hole system ?
 Thanks in advance for your help ! Nils


Here are the results of some commands that might help :

```
nils@NilsXPS13:~$ lspci -vnn | grep -A 12 '\''[030[02]\]' | grep -Ei "vga|3d|display|kernel"
00:02.0 VGA compatible controller [0300]: Intel Corporation TigerLake-LP GT2 [Iris Xe Graphics] [8086:9a49] (rev 01) (prog-if 00 [VGA controller])
    Kernel driver in use: i915
    Kernel modules: i915
```

```
nils@NilsXPS13:~$ uname -a
Linux NilsXPS13 6.2.0-26-generic #26~22.04.1-Ubuntu SMP PREEMPT_DYNAMIC Thu Jul 13 16:27:29 UTC 2 x86_64 x86_64 x86_64 GNU/Linux
```

```
nils@NilsXPS13:~$ xrandr
Screen 0: minimum 16 x 16, current 1920 x 1080, maximum 32767 x 32767
XWAYLAND1 connected primary 1920x1080+0+0 (normal left inverted right x axis y axis) 530mm x 300mm
   1920x1080     59.96*+
   1440x1080     59.99  
   1400x1050     59.98  
   1280x1024     59.89  
   1280x960      59.94  
   1152x864      59.96  
   1024x768      59.92  
   800x600       59.86  
   640x480       59.38  
   320x240       59.52  
   1680x1050     59.95  
   1440x900      59.89  
   1280x800      59.81  
   720x480       59.71  
   640x400       59.95  
   320x200       58.96  
   1600x900      59.95  
   1368x768      59.88  
   1280x720      59.86  
   1024x576      59.90  
   864x486       59.92  
   720x400       59.55  
   640x350       59.77
```

```
nils@NilsXPS13:~$ dpkg -l | grep -v ^ii
Souhait=inconnU/Installé/suppRimé/Purgé/H=à garder
| État=Non/Installé/fichier-Config/dépaqUeté/échec-conFig/H=semi-installé/W=attend-traitement-déclenchements
|/ Err?=(aucune)/besoin Réinstallation (État,Err: majuscule=mauvais)
||/ Nom                                        Version                                         Architecture Description
+++-==========================================-===============================================-============-================================================================================
hi  thunderbird                                1:91.8.0+build2-0ubuntu1                        amd64        Email, RSS and newsgroup client with integrated spam filter
```

```


echo $XDG_SESSION_TYPE
wayland
```

```
nils@NilsXPS13:~$ journalctl --no-pager -b -p err
août 15 09:02:14 NilsXPS13 kernel: x86/mktme: No known encryption algorithm is supported: 0x0
août 15 09:02:16 NilsXPS13 gnome-session-binary[1220]: GLib-GIO-CRITICAL: g_bus_get_sync: assertion 'error == NULL || *error == NULL' failed
août 15 09:02:16 NilsXPS13 gnome-session-binary[1220]: GLib-GIO-CRITICAL: g_bus_get_sync: assertion 'error == NULL || *error == NULL' failed
août 15 09:02:16 NilsXPS13 kernel: ACPI BIOS Error (bug): Could not resolve symbol [\_TZ.ETMD], AE_NOT_FOUND (20221020/psargs-330)
août 15 09:02:16 NilsXPS13 kernel: ACPI Error: Aborting method \_SB.IETM._OSC due to previous error (AE_NOT_FOUND) (20221020/psparse-529)
août 15 09:02:18 NilsXPS13 kernel: Bluetooth: hci0: Device boot timeout
août 15 09:02:18 NilsXPS13 canonical-livepatch.canonical-livepatchd[1073]: Task "refresh" returned an error: livepatch check failed: POST request to "https://livepatch.canonical.com/v1/client/56be800040b24ae1b20429d83c89b045/updates" failed, retrying in 30s.
août 15 09:02:20 NilsXPS13 kernel: Bluetooth: hci0: Failed to read MSFT supported features (-110)
août 15 09:02:20 NilsXPS13 kernel: Bluetooth: hci0: command 0xfc1e tx timeout
août 15 09:02:23 NilsXPS13 gdm-password][1891]: gkr-pam: unable to locate daemon control file
août 15 09:02:25 NilsXPS13 systemd[1900]: Failed to start Application launched by gnome-session-binary.
août 15 09:02:25 NilsXPS13 systemd[1900]: Failed to start Application launched by gnome-session-binary.
août 15 09:02:25 NilsXPS13 systemd[1900]: Failed to start Application launched by gnome-session-binary.
août 15 09:02:25 NilsXPS13 systemd[1900]: Failed to start Application launched by gnome-session-binary.
août 15 09:02:27 NilsXPS13 gdm-launch-environment][1163]: GLib-GObject: g_object_unref: assertion 'G_IS_OBJECT (object)' failed
août 15 11:56:28 NilsXPS13 kernel: ACPI Error: Thread 553082688 cannot release Mutex [ECMX] acquired by thread 2141675328 (20221020/exmutex-378)
août 15 11:56:28 NilsXPS13 kernel: ACPI Error: Aborting method \_SB.PC00.LPCB.ECDV._Q66 due to previous error (AE_AML_NOT_OWNER) (20221020/psparse-529)
```

```
nils@NilsXPS13:~$ ls -l /var/crash
total 157236
-rw-r----- 1 nils     whoopsie 71096781 août  11 19:53 _usr_bin_gjs-console.1000.crash
-rw-r----- 1 nils     whoopsie 50518164 août  15 00:39 _usr_bin_gnome-shell.1000.crash
-rw-r----- 1 nils     whoopsie 31970367 août   8 12:20 _usr_bin_nautilus.1000.crash
-rw-rw-r-- 1 nils     whoopsie        0 août   8 12:20 _usr_bin_nautilus.1000.upload
-rw------- 1 whoopsie whoopsie       37 août   8 12:21 _usr_bin_nautilus.1000.uploaded
-rw-r----- 1 nils     whoopsie  7404298 août  15 00:39 _usr_share_apport_apport-gtk.1000.crash
```

---

