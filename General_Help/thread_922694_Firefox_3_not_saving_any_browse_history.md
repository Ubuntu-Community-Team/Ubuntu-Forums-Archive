---
title: "Firefox 3 not saving any browse history"
date: 2008-09-17
forum: General Help
---

### Post by CleverJake on 2008-09-17
A few weeks back, I was online and I went to go back a page, and the icons were greyed out, as though it was the first page I had gone to. I didnt give it much thought until next time I went to start firefox, and clicked restore last session, it went to a blank page and not my home page.
This minor issue has resulted in me essentially having no saved history of browsing. 
I checked my preferences, and I have history set to be saving up to 90 days. I have no browse history in any window, and the issue was not resolved by a safe-mode start or a complete removal and re installation of firefox 3, and no error is given when starting firefox through the terminal


firefox 2 DID work without this issue when installed, but firefox 3 is a much better browser IMO and I would really prefer to continue using it.
 

any advice would be lovely

thanks

---

### Post by Washer on 2008-09-17
press ctrl-h see if anything shows up

if it does, i don't know, try using tab mix plus's sessionsaver, you'll need the dev build version for ff3

when you reinstall, try deleting ~/.mozilla

---

### Post by CleverJake on 2008-09-17
yeah, ctrl h shows nothing, there is nothign on the url bars history, my bookmarks wont even come up
the url bar wont even change to the current page
its really weird

I was underthe impression that a compelte removal through snaptic would delete the .mozilla file, but I will give it a shot anyway

---

### Post by howefield on 2008-09-17
most likely not this simple but.. in Edit > Preferences > Privacy tab,  is there a checkmark next to "Always clear my private data when I close Firefox"

---

### Post by CleverJake on 2008-09-17
Thanks, but no, that didnt do it either
I havea  feeling that its somethign much larger than a preferance somewhere, since I am unable to even save current browsing history

I cant even go back page
=/


Something is interfering with firefox, but I dont know what

---

### Post by CleverJake on 2008-09-17
Im not sure if this is of any help, but here is the current processes running via the output of ps -e 

```
jake@a900:~$ ps -e
  PID TTY          TIME CMD
    1 ?        00:00:01 init
    2 ?        00:00:00 kthreadd
    3 ?        00:00:00 migration/0
    4 ?        00:00:01 ksoftirqd/0
    5 ?        00:00:00 watchdog/0
    6 ?        00:00:00 migration/1
    7 ?        00:00:01 ksoftirqd/1
    8 ?        00:00:00 watchdog/1
    9 ?        00:00:00 events/0
   10 ?        00:00:00 events/1
   11 ?        00:00:00 khelper
   16 ?        00:00:00 ftraced
   53 ?        00:00:00 kintegrityd/0
   54 ?        00:00:00 kintegrityd/1
   55 ?        00:00:00 kblockd/0
   56 ?        00:00:00 kblockd/1
   58 ?        00:00:00 kacpid
   59 ?        00:00:00 kacpi_notify
  134 ?        00:00:00 kseriod
  179 ?        00:00:00 pdflush
  180 ?        00:00:00 pdflush
  181 ?        00:00:00 kswapd0
  223 ?        00:00:00 aio/0
  224 ?        00:00:00 aio/1
  880 ?        00:00:00 aufsd
  881 ?        00:00:00 aufsd
  882 ?        00:00:00 aufsd
  883 ?        00:00:00 aufsd
 1008 ?        00:00:00 cqueue
 1885 ?        00:00:00 ksuspend_usbd
 1898 ?        00:00:00 khubd
 1921 ?        00:00:00 ata/0
 1924 ?        00:00:00 ata/1
 1925 ?        00:00:00 ata_aux
 1979 ?        00:00:00 scsi_eh_0
 1980 ?        00:00:00 scsi_eh_1
 1981 ?        00:00:00 scsi_eh_2
 2004 ?        00:00:00 scsi_eh_3
 2005 ?        00:00:00 scsi_eh_4
 2121 ?        00:00:00 scsi_eh_5
 2122 ?        00:00:00 usb-storage
 2179 ?        00:00:09 kjournald
 2469 ?        00:00:01 udevd
 3499 ?        00:00:00 btaddconn
 3502 ?        00:00:00 btdelconn
 3551 ?        00:00:00 kpsmoused
 4319 tty4     00:00:00 getty
 4320 tty5     00:00:00 getty
 4322 tty2     00:00:00 getty
 4323 tty3     00:00:00 getty
 4326 tty6     00:00:00 getty
 4500 ?        00:00:00 acpid
 4535 ?        00:00:05 kondemand/0
 4536 ?        00:00:00 kondemand/1
 4620 ?        00:00:00 syslogd
 4664 ?        00:00:00 dd
 4666 ?        00:00:00 klogd
 4689 ?        00:00:15 dbus-daemon
 4709 ?        00:00:00 avahi-daemon
 4710 ?        00:00:00 avahi-daemon
 4738 ?        00:00:00 sshd
 4782 ?        00:00:00 cupsd
 5040 ?        00:00:00 exim4
 5107 ?        00:00:00 nmbd
 5109 ?        00:00:00 smbd
 5131 ?        00:00:00 smbd
 5209 ?        00:00:00 winbindd
 5224 ?        00:00:00 winbindd
 5228 ?        00:00:00 dhcdbd
 5249 ?        00:00:06 hald
 5252 ?        00:00:00 console-kit-dae
 5253 ?        00:00:00 hald-runner
 5339 ?        00:00:00 hald-addon-cpuf
 5340 ?        00:00:00 hald-addon-acpi
 5345 ?        00:00:00 hald-addon-inpu
 5381 ?        00:00:00 hald-addon-stor
 5384 ?        00:00:01 hald-addon-stor
 5400 ?        00:00:01 hcid
 5413 ?        00:00:00 krfcommd
 5432 ?        00:00:23 NetworkManager
 5444 ?        00:00:04 wpa_supplicant
 5449 ?        00:00:00 nm-system-setti
 5458 ?        00:00:00 gdm
 5460 ?        00:00:00 gdm
 5467 tty7     00:09:28 Xorg
 5480 ?        00:00:00 system-tools-ba
 5581 ?        00:00:00 atd
 5609 ?        00:00:00 cron
 5687 tty1     00:00:00 getty
 5833 ?        00:00:00 gnome-keyring-d
 5844 ?        00:00:00 x-session-manag
 5902 ?        00:00:00 dbus-launch
 5903 ?        00:00:00 dbus-daemon
 5909 ?        00:00:00 seahorse-agent
 5911 ?        00:00:00 gvfs-hal-volume
 5914 ?        00:00:00 gvfsd
 5916 ?        00:00:02 gconfd-2
 5920 ?        00:00:00 gvfs-gphoto2-vo
 5924 ?        00:00:00 gvfs-fuse-daemo
 5932 ?        00:00:00 gnome-keyring-d
 5935 ?        00:00:03 gnome-settings-
 5936 ?        00:00:00 compiz
 5974 ?        00:00:00 pulseaudio
 5994 ?        00:00:42 compiz.real
 5997 ?        00:00:00 gconf-helper
 6016 ?        00:00:04 gnome-screensav
 6023 ?        00:00:06 gnome-panel
 6024 ?        00:00:15 nautilus
 6026 ?        00:00:00 bonobo-activati
 6028 ?        00:00:00 tracker-applet
 6029 ?        00:00:00 update-notifier
 6030 ?        00:00:00 evolution-alarm
 6031 ?        00:00:00 trackerd
 6033 ?        00:00:01 nm-applet
 6034 ?        00:00:00 bluetooth-apple
 6035 ?        00:00:00 python
 6037 ?        00:00:00 blueproximity
 6038 ?        00:00:07 emerald
 6039 ?        00:01:40 python
 6043 ?        00:00:03 checkgmail
 6052 ?        00:00:02 cairo-dock
 6066 ?        00:00:04 gnome-power-man
 6079 ?        00:00:00 obex-data-serve
 6081 ?        00:00:00 notification-da
 6085 ?        00:00:00 evolution-excha
 6100 ?        00:00:00 gvfsd-burn
 6126 ?        00:00:00 evolution-data-
 6177 ?        00:00:22 dropboxd
 6186 ?        00:00:00 mixer_applet2
 6191 ?        00:00:00 gvfsd-trash
 6192 ?        00:00:00 fast-user-switc
 6215 ?        00:00:00 gvfsd-cdda
 6263 ?        00:00:00 dhclient
 6553 ?        00:00:00 cifsoplockd
 6556 ?        00:00:00 cifsdnotifyd
 6588 ?        00:12:30 firefox
 6701 ?        00:00:00 jockey-backend
 6716 ?        00:00:00 cups-deviced
 6717 ?        00:00:00 hp <defunct>
 6718 ?        00:00:00 dnssd <defunct>
 6729 ?        00:00:00 cups-deviced <defunct>
 6730 ?        00:00:00 beh <defunct>
 6731 ?        00:00:00 python <defunct>
 6734 ?        00:00:00 snmp <defunct>
 6737 ?        00:00:00 bluetooth
 6750 ?        00:00:00 sh
 6751 ?        00:00:02 gnome-terminal
 6753 ?        00:00:00 gnome-pty-helpe
 6754 pts/0    00:00:00 bash
 7146 ?        00:00:00 gvfsd-http
11869 pts/1    00:00:00 bash
11932 pts/1    00:00:00 ps
```

---

### Post by Washer on 2008-09-17
I really don't know what it could be. Try making a new profile with "firefox -P"

nah that couldn't be it if deleting ~/.mozilla didn't work.

---

### Post by CleverJake on 2008-09-18
actually...that worked
wtf? haha

Thanks alot mate

---

