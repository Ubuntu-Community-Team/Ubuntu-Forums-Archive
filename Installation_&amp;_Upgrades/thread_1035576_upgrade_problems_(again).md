---
title: "upgrade problems (again)"
date: 2009-01-09
forum: Installation &amp; Upgrades
---

### Post by banter25 on 2009-01-09
Third time something has flipped out when trying to install simple upgrades via the upgrade manager.  I am running 8.10 Intrepid on a dual core AMD and this is the new error I'm getting.


E: Could not get lock /var/cache/apt/archives/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the download directory


So the question is, how do you unlock the download directory?:confused:

Thanks for any info you can give me on this.

---

### Post by taurus on 2009-01-09
There is something running in the background like adept or apt-get.  Just for a few minutes.  If not, see which one is it.

```
ps -A
```

---

### Post by banter25 on 2009-01-09
Let it stop and now it's throwing out a new one.


E: /var/cache/apt/archives/linux-image-2.6.27-7-generic_2.6.27-7.16_amd64.deb: unable to make backup link of `./boot/vmlinuz-2.6.27-7-generic' before installing new version

and this is what I get when I run ps -a

 PID TTY          TIME CMD
23655 pts/0    00:00:00 ps

---

### Post by TeeRev on 2009-02-06
Is there any solution to this second problem?  It's the exact same as I am having, but when I enter ps -A I get:

  PID TTY          TIME CMD
    1 ?        00:00:00 init
    2 ?        00:00:00 kthreadd
    3 ?        00:00:00 migration/0
    4 ?        00:00:00 ksoftirqd/0
    5 ?        00:00:00 watchdog/0
    6 ?        00:00:00 migration/1
    7 ?        00:00:00 ksoftirqd/1
    8 ?        00:00:00 watchdog/1
    9 ?        00:00:00 events/0
   10 ?        00:00:00 events/1
   11 ?        00:00:00 khelper
   49 ?        00:00:00 kintegrityd/0
   50 ?        00:00:00 kintegrityd/1
   52 ?        00:00:00 kblockd/0
   53 ?        00:00:00 kblockd/1
   55 ?        00:00:00 kacpid
   56 ?        00:00:00 kacpi_notify
  145 ?        00:00:00 cqueue
  149 ?        00:00:00 kseriod
  200 ?        00:00:00 pdflush
  201 ?        00:00:00 kswapd0
  247 ?        00:00:00 aio/0
  248 ?        00:00:00 aio/1
 1274 ?        00:00:00 ksuspend_usbd
 1275 ?        00:00:00 khubd
 1361 ?        00:00:00 ata/0
 1374 ?        00:00:00 ata/1
 1375 ?        00:00:00 ata_aux
 2046 ?        00:00:00 scsi_eh_0
 2047 ?        00:00:00 scsi_eh_1
 2061 ?        00:00:00 scsi_eh_2
 2062 ?        00:00:00 scsi_eh_3
 2300 ?        00:00:01 loop0
 2318 ?        00:00:00 kjournald
 2462 ?        00:00:01 udevd
 2825 ?        00:00:00 kpsmoused
 3997 ?        00:00:01 loop1
 3998 ?        00:00:00 kjournald
 4274 tty4     00:00:00 getty
 4275 tty5     00:00:00 getty
 4280 tty2     00:00:00 getty
 4282 tty3     00:00:00 getty
 4283 tty6     00:00:00 getty
 4471 ?        00:00:00 acpid
 4515 ?        00:00:00 kondemand/0
 4516 ?        00:00:00 kondemand/1
 4599 ?        00:00:00 syslogd
 4652 ?        00:00:00 dd
 4654 ?        00:00:00 klogd
 4677 ?        00:00:00 dbus-daemon
 4699 ?        00:00:00 avahi-daemon
 4700 ?        00:00:00 avahi-daemon
 4735 ?        00:00:00 cupsd
 4896 ?        00:00:00 hald
 4899 ?        00:00:00 console-kit-dae
 4900 ?        00:00:00 hald-runner
 4982 ?        00:00:00 hald-addon-inpu
 4995 ?        00:00:00 hald-addon-acpi
 5002 ?        00:00:00 hald-addon-stor
 5043 ?        00:00:00 bluetoothd
 5050 ?        00:00:00 btaddconn
 5051 ?        00:00:00 btdelconn
 5063 ?        00:00:00 krfcommd
 5105 ?        00:00:00 NetworkManager
 5114 ?        00:00:00 wpa_supplicant
 5118 ?        00:00:00 nm-system-setti
 5143 ?        00:00:00 gdm
 5146 ?        00:00:00 gdm
 5149 tty7     00:01:49 Xorg
 5167 ?        00:00:00 system-tools-ba
 5204 ?        00:00:00 atd
 5232 ?        00:00:00 cron
 5312 tty1     00:00:00 getty
 5404 ?        00:00:00 gnome-keyring-d
 5415 ?        00:00:00 x-session-manag
 5503 ?        00:00:00 dbus-launch
 5504 ?        00:00:00 dbus-daemon
 5507 ?        00:00:00 pulseaudio
 5510 ?        00:00:00 gconf-helper
 5512 ?        00:00:00 gconfd-2
 5518 ?        00:00:00 seahorse-agent
 5521 ?        00:00:00 gvfsd
 5522 ?        00:00:00 gnome-keyring-d
 5527 ?        00:00:01 gnome-settings-
 5528 ?        00:00:00 compiz
 5538 ?        00:00:00 gvfs-fuse-daemo
 5601 ?        00:00:24 compiz.real
 5605 ?        00:00:03 gnome-screensav
 5610 ?        00:00:00 sh
 5611 ?        00:00:00 compiz-decorato
 5613 ?        00:00:05 gtk-window-deco
 5614 ?        00:00:10 gnome-panel
 5616 ?        00:00:02 nautilus
 5618 ?        00:00:00 bonobo-activati
 5628 ?        00:00:00 gvfs-hal-volume
 5630 ?        00:00:00 gvfs-gphoto2-vo
 5632 ?        00:00:00 gvfsd-trash
 5637 ?        00:00:00 trashapplet
 5647 ?        00:00:00 gvfsd-burn
 5666 ?        00:00:00 fast-user-switc
 5669 ?        00:00:00 mixer_applet2
 5680 ?        00:00:00 update-notifier
 5681 ?        00:00:00 python
 5682 ?        00:00:00 tracker-applet
 5683 ?        00:00:00 evolution-alarm
 5692 ?        00:00:00 nm-applet
 5693 ?        00:00:00 trackerd
 5694 ?        00:00:00 bluetooth-apple
 5696 ?        00:00:00 gnome-power-man
 5703 ?        00:00:01 notification-da
 5813 ?        00:00:38 firefox
 8596 ?        00:00:00 pdflush
 8606 ?        00:00:00 dhclient
 9374 ?        00:00:00 gnome-terminal
 9377 ?        00:00:00 gnome-pty-helpe
 9378 pts/0    00:00:00 bash
 9395 pts/0    00:00:00 ps


Any help?  I had installed ubuntu 8.10 on this very machine a few weeks ago and it was all running fine, but I had a major virus issue with XP( which is on the same drive) so I formatted everything and started fresh.  Everything has been going the same as the first install except for this update, not sure what the problem is.

Thanks in advance.

---

### Post by taurus on 2009-02-06
> **TeeRev said:**
> Is there any solution to this second problem?  It's the exact same as I am having, but when I enter ps -A I get:

Any help?  I had installed ubuntu 8.10 on this very machine a few weeks ago and it was all running fine, but I had a major virus issue with XP( which is on the same drive) so I formatted everything and started fresh.  Everything has been going the same as the first install except for this update, not sure what the problem is.

Thanks in advance.

Try these.

```
sudo kill -9 5680
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by TeeRev on 2009-02-06
Thanks for the quick reply.  I've done what you said, but now I am getting this error during the upgrade:


Errors were encountered while processing:
 /var/cache/apt/archives/linux-image-2.6.27-7-generic_2.6.27-7.16_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

I've found some other forum posts about it just searching google, but no solutions.

---

### Post by taurus on 2009-02-06
> **TeeRev said:**
> Thanks for the quick reply.  I've done what you said, but now I am getting this error during the upgrade:


Errors were encountered while processing:
 /var/cache/apt/archives/linux-image-2.6.27-7-generic_2.6.27-7.16_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

I've found some other forum posts about it just searching google, but no solutions.

```
sudo apt-get clean
sudo apt-get update
sudo apt-get dist-upgrade
```

---

### Post by TeeRev on 2009-02-08
Tried that, same result..

---

### Post by Kevbert on 2009-02-08
It looks like your /boot partition may be filled up. In terminal enter
```
cd /boot
ls -l
```
If you have any .bak files there remove them with
```
rm *.bak
```
Also if you have a number of old kernels (grub menu items) that you no longer use you can remove these via Synaptic (make a note of the kernel). Close terminal. Now go to Synaptic and search for linux-image and remove the linux-image...generic files that you don't want (be careful that you don't remove the one you are using). This will also remove the grub entries automatically. You should now be able to update with
```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade

```

---

### Post by TeeRev on 2009-02-08
I don't think it should be full, I partitioned off 10gb to install ubuntu on and clicking on file system from places I still have 1.9gb left.  When I go to /boot directly it says there are 915 mb left, so it should still be enough right?

When I entered the ls -l command in /boot, I didn't see any .bak files either.

As for old kernel menus, I am not sure which ones I would want to delete here.  Here is what comes up:

administrator@ubuntu:~$ cd /boot
administrator@ubuntu:/boot$ ls -l
total 25976
-rwxr-xr-x 1 root root  504280 2009-01-29 15:52 abi-2.6.27-11-generic
-rwxr-xr-x 1 root root  503560 2008-10-24 08:55 abi-2.6.27-7-generic
-rwxr-xr-x 1 root root   85310 2009-01-29 15:52 config-2.6.27-11-generic
-rwxr-xr-x 1 root root   85316 2008-10-24 08:55 config-2.6.27-7-generic
drwxr-xr-x 2 root root    8192 2009-02-08 03:01 grub
-rwxr-xr-x 1 root root 8927694 2009-02-06 16:42 initrd.img-2.6.27-11-generic
-rwxr-xr-x 1 root root 8903579 2009-02-06 21:24 initrd.img-2.6.27-7-generic
-rwxr-xr-x 1 root root  124152 2008-09-11 21:11 memtest86+.bin
-rwxr-xr-x 1 root root 1354796 2009-01-29 15:52 System.map-2.6.27-11-generic
-rwxr-xr-x 1 root root 1352144 2008-10-24 08:55 System.map-2.6.27-7-generic
-rwxr-xr-x 1 root root    1131 2009-01-29 15:56 vmcoreinfo-2.6.27-11-generic
-rwxr-xr-x 1 root root    1130 2008-10-24 08:57 vmcoreinfo-2.6.27-7-generic
-rwxr-xr-x 1 root root 2344192 2009-01-29 15:52 vmlinuz-2.6.27-11-generic
-rwxr-xr-x 1 root root 2339712 2009-01-23 19:01 vmlinuz-2.6.27-7-generic

The update that I am trying to get is 2.6.27-7, so would I want to get rid of the -11 ones or the -7 ones or neither?

---

### Post by TeeRev on 2009-02-26
bump...(sorry if I shouldn't bump?)  Just a bit annoyed with this..  Everytime I log on it tells me to update it and it still won't.  

By looking at my last post, the 2.6.27-7 files are almost all older than the 2.6.27-11 ones.  Does that mean those are the ones that should be removed before I can move forward?  I don't want to go ahead and do anything on my own in case I screw it up.  I have Ubuntu installed on this computer so I can work on my C and Java assignments at home instead of going into the lab to do them, and this update isn't causing me any big problems, just a minor annoyance I would like to fix if I can.

---

