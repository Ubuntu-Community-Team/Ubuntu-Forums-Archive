---
title: "No sound!"
date: 2008-09-13
forum: General Help
---

### Post by azathrael on 2008-09-13
I have no idea where to begin.  At random points when I keep ubuntu on, the sound just disappears.  The only guess I can make is that it seems to happen after I've played videos (especially ones requiring flash?) on the internet using firefox.  After the sound disappears, I can't hear any sound from any program, and Mplayer gives me an error saying:

Could not open/initiate audio device -> no sound.

I absolutely know that the video file I'm trying to play itself has the sound, because I played the file before the sound disappeared and had no problems whatsoever.

Anyone know what's going on?

---

### Post by azathrael on 2008-09-13
Update: I also can't open the Sound Preferences window under System -> Preferences. The window is frozen...

---

### Post by am15 on 2008-09-16
I am having the same problem.  Is there a solution out there?  I have to keep restarting to get the sound to work...big pain.

---

### Post by mali2297 on 2008-09-16
Have you checked if there is any process that might be occupying the sound device?

From a terminal, type
```

ps -e

```
to list all processes. If mplayer or some other media player is running, kill it.

---

### Post by am15 on 2008-09-16
This is the output I get:

  PID TTY          TIME CMD
    1 ?        00:00:01 init
    2 ?        00:00:00 kthreadd
    3 ?        00:00:00 migration/0
    4 ?        00:00:02 ksoftirqd/0
    5 ?        00:00:00 watchdog/0
    6 ?        00:00:00 migration/1
    7 ?        00:00:01 ksoftirqd/1
    8 ?        00:00:00 watchdog/1
    9 ?        00:00:00 events/0
   10 ?        00:00:00 events/1
   11 ?        00:00:00 khelper
   46 ?        00:00:00 kblockd/0
   47 ?        00:00:00 kblockd/1
   50 ?        00:00:00 kacpid
   51 ?        00:00:00 kacpi_notify
  143 ?        00:00:00 kseriod
  185 ?        00:00:00 pdflush
  186 ?        00:00:00 pdflush
  187 ?        00:00:00 kswapd0
  228 ?        00:00:00 aio/0
  229 ?        00:00:00 aio/1
 1543 ?        00:00:00 ksuspend_usbd
 1546 ?        00:00:00 khubd
 1600 ?        00:00:00 ata/0
 1604 ?        00:00:00 ata/1
 1606 ?        00:00:00 ata_aux
 1674 ?        00:00:00 khpsbpkt
 2408 ?        00:00:00 scsi_eh_0
 2409 ?        00:00:00 scsi_eh_1
 2410 ?        00:00:00 scsi_eh_2
 2478 ?        00:00:00 knodemgrd_0
 2481 ?        00:00:01 scsi_eh_3
 2483 ?        00:00:00 scsi_eh_4
 2659 ?        00:00:00 kjournald
 2878 ?        00:00:00 udevd
 3182 ?        00:00:00 iwl3945/0
 3193 ?        00:00:00 iwl3945/1
 3241 ?        00:00:00 kmmcd
 3326 ?        00:00:00 kpsmoused
 4135 ?        00:00:01 iwl3945
 4866 tty4     00:00:00 getty
 4867 tty5     00:00:00 getty
 4869 tty2     00:00:00 getty
 4871 tty3     00:00:00 getty
 4873 tty6     00:00:00 getty
 5057 ?        00:00:00 acpid
 5091 ?        00:00:03 kondemand/0
 5092 ?        00:00:00 kondemand/1
 5175 ?        00:00:00 syslogd
 5231 ?        00:00:00 dd
 5233 ?        00:00:00 klogd
 5255 ?        00:00:07 dbus-daemon
 5271 ?        00:00:10 NetworkManager
 5285 ?        00:00:01 NetworkManagerD
 5298 ?        00:00:00 system-tools-ba
 5318 ?        00:00:00 avahi-daemon
 5319 ?        00:00:00 avahi-daemon
 5432 ?        00:00:00 freshclam
 5459 ?        00:00:00 cupsd
 5537 ?        00:00:00 winbindd
 5548 ?        00:00:00 winbindd
 5585 ?        00:00:02 dhcdbd
 5604 ?        00:00:32 hald
 5607 ?        00:00:00 console-kit-dae
 5608 ?        00:00:03 hald-runner
 5681 ?        00:00:12 hald-addon-usb-
 5682 ?        00:00:00 hald-addon-dell
 5683 ?        00:00:00 hald-addon-inpu
 5691 ?        00:00:00 hald-addon-cpuf
 5692 ?        00:00:00 hald-addon-acpi
 5730 ?        00:00:01 hald-addon-stor
 5760 ?        00:00:00 hcid
 5806 ?        00:00:00 btaddconn
 5807 ?        00:00:00 btdelconn
 5821 ?        00:00:00 bluetoothd-serv
 5822 ?        00:00:00 krfcommd
 5856 ?        00:00:00 bluetoothd-serv
 5875 ?        00:00:00 gdm
 5878 ?        00:00:00 gdm
 5882 tty7     00:11:05 Xorg
 5944 ?        00:00:00 atd
 5958 ?        00:00:00 cron
 6057 ?        00:00:00 apache2
 6142 tty1     00:00:00 getty
 6145 ?        00:00:00 apache2
 6146 ?        00:00:00 apache2
 6147 ?        00:00:00 apache2
 6148 ?        00:00:00 apache2
 6149 ?        00:00:00 apache2
 6169 ?        00:00:03 gconfd-2
 6171 ?        00:00:00 gnome-keyring-d
 6172 ?        00:00:00 x-session-manag
 6275 ?        00:00:00 seahorse-agent
 6279 ?        00:00:03 dbus-daemon
 6280 ?        00:00:04 gnome-settings-
 6288 ?        00:00:41 pulseaudio
 6293 ?        00:00:00 gconf-helper
 6310 ?        00:00:11 gnome-screensav
 6311 ?        00:00:00 compiz
 6312 ?        00:00:26 gnome-panel
 6314 ?        00:00:08 nautilus
 6318 ?        00:00:00 bonobo-activati
 6340 ?        00:00:00 gvfsd
 6381 ?        00:01:14 compiz.real
 6383 ?        00:00:00 gvfs-fuse-daemo
 6387 ?        00:00:00 bluetooth-apple
 6390 ?        00:00:01 update-notifier
 6397 ?        00:00:00 tracker-applet
 6400 ?        00:00:00 evolution-alarm
 6403 ?        00:00:00 trackerd
 6406 ?        00:00:00 gnome-volume-ma
 6407 ?        00:00:05 python
 6409 ?        00:00:32 nm-applet
 6411 ?        00:00:01 gnome-power-man
 6433 ?        00:00:00 avahi-autoipd
 6434 ?        00:00:00 avahi-autoipd
 6437 ?        00:00:00 gvfsd-burn
 6439 ?        00:00:01 wpa_supplicant
 6459 ?        00:00:00 evolution-excha
 6469 ?        00:00:00 trashapplet
 6484 ?        00:00:11 gvfsd-trash
 6492 ?        00:00:00 sh
 6493 ?        00:00:00 compiz-decorato
 6495 ?        00:00:02 gtk-window-deco
 6529 ?        00:00:00 evolution-data-
 6550 ?        00:00:00 dhclient
 6609 ?        00:00:00 mixer_applet2
 6611 ?        00:00:00 fast-user-switc
 6711 ?        00:00:14 pidgin
 6739 ?        00:05:53 skype
 6764 ?        00:00:01 knotes
 6777 ?        00:00:00 kdeinit
 6782 ?        00:00:00 dcopserver
 6785 ?        00:00:00 klauncher
 6787 ?        00:00:02 kded
 6830 ?        00:00:02 kontact
 6835 ?        00:00:01 knotify
 6838 ?        00:00:14 artsd
 6844 ?        00:03:02 minbar
 6853 ?        00:00:01 korgac
 6858 ?        00:35:41 firefox
 6859 ?        00:00:00 kio_file
 9378 ?        00:00:00 gnome-terminal
 9382 ?        00:00:00 gnome-pty-helpe
 9383 pts/0    00:00:00 bash
 9522 ?        00:00:00 kio_pop3
 9551 ?        00:00:08 amarokapp
 9562 ?        00:00:00 kio_file
 9563 ?        00:00:00 ruby
 9566 ?        00:00:00 kio_file
 9567 ?        00:00:00 kio_file
 9697 pts/0    00:00:00 ps
21579 ?        00:00:00 notification-da

I tried killing amarok and restarting it but no effect.  Also tried changing device in Sound settings.

---

### Post by am15 on 2008-09-16
Check this out:

Looks like amarok keeps trying and trying:

ps aux | grep amarok
aamina    8057  0.0  0.0   3004   772 pts/0    S+   21:08   0:00 grep amarok
aamina@aamina-laptop:~$ ps aux | grep amarok
aamina    8063  0.0  0.0   3004   760 pts/0    R+   21:09   0:00 grep amarok
aamina@aamina-laptop:~$ ps aux | grep amarok
aamina    8072  0.0  0.0   3004   756 pts/0    R+   21:09   0:00 grep amarok
aamina@aamina-laptop:~$ ps aux | grep amarok
aamina    8074  0.0  0.0   3004   756 pts/0    R+   21:09   0:00 grep amarok
aamina@aamina-laptop:~$ ps aux | grep amarok
aamina    8080  0.0  0.0   3004   764 pts/0    R+   21:09   0:00 grep amarok
aamina@aamina-laptop:~$ ps aux | grep amarok
aamina    8082  0.0  0.0   3004   772 pts/0    S+   21:09   0:00 grep amarok
aamina@aamina-laptop:~$ ps aux | grep amarok
aamina    8085  0.0  0.0   3004   756 pts/0    R+   21:09   0:00 grep amarok
aamina@aamina-laptop:~$ ps aux | grep amarok
aamina    8090  0.0  0.0   3004   764 pts/0    R+   21:09   0:00 grep amarok
aamina@aamina-laptop:~$ ps aux | grep amarok
aamina    8093  0.0  0.0   3004   768 pts/0    R+   21:09   0:00 grep amarok
aamina@aamina-laptop:~$ ps aux | grep amarok
aamina    8095  0.0  0.0   3004   768 pts/0    R+   21:09   0:00 grep amarok
aamina@aamina-laptop:~$ ps aux | grep amarok
aamina    8100  0.0  0.0   3004   768 pts/0    R+   21:09   0:00 grep amarok
aamina@aamina-laptop:~$ ps aux | grep amarok
aamina    8102  0.0  0.0   3004   764 pts/0    R+   21:09   0:00 grep amarok
aamina@aamina-laptop:~$ ps aux | grep amarok
aamina    8104  0.0  0.0   3004   772 pts/0    S+   21:09   0:00 grep amarok

---

### Post by heatpumpcontrol on 2008-09-16
I had a similar situation not too long ago. I tried this howto

[http://ubuntuforums.org/showthread.php?t=766683]("http://ubuntuforums.org/showthread.php?t=766683")

It worked for some things but after some more troubleshooting I decided to create a new user. Under the new user, all the sounds worked.

Try deleting the .asoundrc and the asoundrc.asoundconf files in your home directory. Make a copy of them somewhere else first.....

Log out and back in and see if that helps.

For me I ended up getting frustrated due to some other issues and just clean installed everything. Even my user account....

---

### Post by mali2297 on 2008-09-17
> **am15 said:**
> Check this out:

Looks like amarok keeps trying and trying:

ps aux | grep amarok
aamina    8057  0.0  0.0   3004   772 pts/0    S+   21:08   0:00 grep amarok
aamina@aamina-laptop:~$ ps aux | grep amarok
aamina    8063  0.0  0.0   3004   760 pts/0    R+   21:09   0:00 grep amarok
aamina@aamina-laptop:~$ ps aux | grep amarok
aamina    8072  0.0  0.0   3004   756 pts/0    R+   21:09   0:00 grep amarok
aamina@aamina-laptop:~$ ps aux | grep amarok
aamina    8074  0.0  0.0   3004   756 pts/0    R+   21:09   0:00 grep amarok
aamina@aamina-laptop:~$ ps aux | grep amarok
aamina    8080  0.0  0.0   3004   764 pts/0    R+   21:09   0:00 grep amarok
aamina@aamina-laptop:~$ ps aux | grep amarok
aamina    8082  0.0  0.0   3004   772 pts/0    S+   21:09   0:00 grep amarok
aamina@aamina-laptop:~$ ps aux | grep amarok
aamina    8085  0.0  0.0   3004   756 pts/0    R+   21:09   0:00 grep amarok
aamina@aamina-laptop:~$ ps aux | grep amarok
aamina    8090  0.0  0.0   3004   764 pts/0    R+   21:09   0:00 grep amarok
aamina@aamina-laptop:~$ ps aux | grep amarok
aamina    8093  0.0  0.0   3004   768 pts/0    R+   21:09   0:00 grep amarok
aamina@aamina-laptop:~$ ps aux | grep amarok
aamina    8095  0.0  0.0   3004   768 pts/0    R+   21:09   0:00 grep amarok
aamina@aamina-laptop:~$ ps aux | grep amarok
aamina    8100  0.0  0.0   3004   768 pts/0    R+   21:09   0:00 grep amarok
aamina@aamina-laptop:~$ ps aux | grep amarok
aamina    8102  0.0  0.0   3004   764 pts/0    R+   21:09   0:00 grep amarok
aamina@aamina-laptop:~$ ps aux | grep amarok
aamina    8104  0.0  0.0   3004   772 pts/0    S+   21:09   0:00 grep amarok

It isn't amarok that is listed but the grep command. Try
```

ps aux | grep hello

```
or anything else. :-)

---

### Post by shane19174 on 2008-09-17
In addition to the howto mentioned by heatpumpcontrol above, I can recommend the following two guides: psyke83's "HOWTO: PulseAudio Fixes & System-Wide Equalizer Support (Hardy Heron)" ([http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)) and markbuntu's "Multiple Sound Solution (ALSA w Pulseaudio)" ([http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)). Each of these guides is more comprehensive than the titles might lead you to expect. I followed them in the order I've listed and got all of my sound problems straigthened out!

Hope this helps,
Shane

---

