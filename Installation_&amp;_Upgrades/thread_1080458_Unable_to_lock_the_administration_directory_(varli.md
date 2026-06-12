---
title: "Unable to lock the administration directory (/var/lib/dpkg/), is another process usi?"
date: 2009-02-25
forum: Installation &amp; Upgrades
---

### Post by koosfoto.hu on 2009-02-25
Greetings!

Since several days I have the message:
[I]
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process usi?[/I]

when I try to install something (like FileZilla).

Of course, all applications are closed, and even, when nothing else is running but the Adept Installer... it still displays: 

[I]Another process is using the packaging system database (probably some other Adept application or apt-get or aptitude).
Would you like to attempt to resolve this problem? No will enter read-only mode and Cancel to quit and resolve this issue yourself.[/I]

When I say Yes... and I start to install... it stops at 38%. And that's it. Nothing to do, but to kill it.

I went through the steps in post: [http://ubuntuforums.orgshowthread.php?t=519612](http://ubuntuforums.orgshowthread.php?t=519612)
and still does not work.

I am using Kubuntu on an Acer notebook.

How can I make it work again?

Thanks,

Tamas

---

### Post by taurus on 2009-02-25
Look at the output of this command to see if you have another process that uses adept.

```
ps -A
```

---

### Post by koosfoto.hu on 2009-02-25
Hello taurus!

This is the list I got:

ps -A
  PID TTY          TIME CMD
    1 ?        00:00:01 init
    2 ?        00:00:00 kthreadd
    3 ?        00:00:00 migration/0
    4 ?        00:00:00 ksoftirqd/0
    5 ?        00:00:00 watchdog/0
    6 ?        00:00:00 events/0
    7 ?        00:00:00 khelper
   41 ?        00:00:00 kblockd/0
   44 ?        00:00:00 kacpid
   45 ?        00:00:00 kacpi_notify
  135 ?        00:00:00 kseriod
  173 ?        00:00:00 pdflush
  174 ?        00:00:00 pdflush
  175 ?        00:00:00 kswapd0
  216 ?        00:00:00 aio/0
 1467 ?        00:00:00 ksuspend_usbd
 1470 ?        00:00:00 khubd
 1522 ?        00:00:00 ata/0
 1528 ?        00:00:00 ata_aux
 1531 ?        00:00:00 khpsbpkt
 2223 ?        00:00:01 scsi_eh_0
 2225 ?        00:00:00 scsi_eh_1
 2349 ?        00:00:00 scsi_eh_2
 2350 ?        00:00:00 scsi_eh_3
 2351 ?        00:00:00 scsi_eh_4
 2395 ?        00:00:00 knodemgrd_0
 2601 ?        00:00:00 kjournald
 2819 ?        00:00:00 udevd
 3097 ?        00:00:00 kmmcd
 3102 ?        00:00:00 tifm
 3108 ?        00:00:00 pccardd
 3121 ?        00:00:00 kpsmoused
 4439 ?        00:00:00 kjournald
 4766 tty4     00:00:00 getty
 4767 tty5     00:00:00 getty
 4771 tty2     00:00:00 getty
 4772 tty3     00:00:00 getty
 4774 tty6     00:00:00 getty
 4945 ?        00:00:00 acpid
 4972 ?        00:00:00 kondemand/0
 5050 ?        00:00:00 syslogd
 5104 ?        00:00:00 dd
 5106 ?        00:00:00 klogd
 5128 ?        00:00:00 dbus-daemon
 5144 ?        00:00:00 NetworkManager
 5158 ?        00:00:00 NetworkManagerD
 5178 ?        00:00:00 avahi-daemon
 5179 ?        00:00:00 avahi-daemon
 5225 ?        00:00:00 cupsd
 5284 ?        00:00:00 winbindd
 5322 ?        00:00:00 dhcdbd
 5327 ?        00:00:00 winbindd
 5342 ?        00:00:00 hald
 5345 ?        00:00:00 console-kit-dae
 5407 ?        00:00:00 hald-runner
 5421 ?        00:00:00 hald-addon-inpu
 5434 ?        00:00:00 hald-addon-acpi
 5452 ?        00:00:01 hald-addon-stor
 5483 ?        00:00:00 hcid
 5497 ?        00:00:00 btaddconn
 5498 ?        00:00:00 btdelconn
 5504 ?        00:00:00 bluetoothd-serv
 5508 ?        00:00:00 bluetoothd-serv
 5513 ?        00:00:00 krfcommd
 5548 ?        00:00:00 atd
 5562 ?        00:00:00 cron
 5660 ?        00:00:00 kdm
 5690 tty7     00:06:31 Xorg
 5704 tty1     00:00:00 getty
 6006 ?        00:00:00 wpa_supplicant
 6086 ?        00:00:00 dhclient
 6373 ?        00:00:01 artsd
 6417 ?        00:00:00 dcopserver
 6458 ?        00:00:08 adept_installer
 6532 pts/3    00:00:00 dpkg
 6533 pts/3    00:00:00 frontend
 6539 pts/3    00:00:00 msttcorefonts.c
 6548 pts/3    00:00:00 whiptail
 6744 ?        00:00:00 kdm
 6770 ?        00:00:00 dbus-daemon
 6771 ?        00:00:00 dbus-launch
 6781 ?        00:00:00 x-session-manag
 6852 ?        00:00:00 ssh-agent
 6854 ?        00:00:00 gpg-agent
 6917 ?        00:00:00 dbus-daemon
 6918 ?        00:00:00 dbus-launch
 6923 ?        00:00:00 kdeinit4
 6924 ?        00:00:00 klauncher
 6926 ?        00:00:01 kded4
 6931 ?        00:00:00 kwrapper4
 6933 ?        00:00:00 ksmserver
 6936 ?        00:01:34 kwin
 6938 ?        00:00:49 plasma
 6940 ?        00:00:17 knotify4
 6947 ?        00:00:01 krunner
 6963 ?        00:00:00 kaccess
 6966 ?        00:00:00 kmix
 6968 ?        00:15:34 firefox
 6971 ?        00:00:00 gconfd-2
 6987 ?        00:00:26 dolphin
 7015 ?        00:00:00 python
 7018 ?        00:00:00 knetworkmanager
 7019 ?        00:00:04 adept_notifier
 7022 ?        00:00:00 kdeinit
 7025 ?        00:00:00 dcopserver
 7028 ?        00:00:00 klauncher
 7043 ?        00:00:00 kded
 7049 ?        00:00:00 thunderbird
 7064 ?        00:00:00 run-mozilla.sh
 7068 ?        00:00:24 thunderbird-bin
 7095 ?        00:00:00 knotify
 7098 ?        00:00:03 klipper
 7114 ?        00:00:00 kpowersave
 7459 ?        00:00:00 kio_file
 7513 ?        00:00:00 kwrite
 7565 ?        00:00:10 skype
 7885 ?        00:00:01 kwrite
 7955 ?        00:00:02 kio_thumbnail
 7958 ?        00:00:00 kio_file
 7961 ?        00:00:00 kwrite
 7967 ?        00:00:00 kwrite
 7991 ?        00:00:00 konsole
 7992 pts/1    00:00:00 bash
 8009 pts/1    00:00:00 ps

Uff, quite a lot is running now... 

Thanks!

Tamas

---

### Post by itisbasi on 2009-02-25
# sudo kill 6458

---

### Post by taurus on 2009-02-25
> **koosfoto.hu said:**
> Hello taurus!

This is the list I got:

ps -A
  PID TTY          TIME CMD
   
[B][COLOR="Red"] 6458 ?        00:00:08 adept_installer
 6532 pts/3    00:00:00 dpkg[/COLOR][/B]

 

There you go.  Maybe kill those two processes and see if you can run apt-get from a terminal again.

```
sudo kill -9 6458
sudo kill -9 6532
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by koosfoto.hu on 2009-02-25
Hi itisbasi, taurus!

I killed both... and this is the result of the update:

light@MIND:~$ sudo kill -9 6458
[sudo] password for light:
light@MIND:~$ sudo kill -9 6532
light@MIND:~$ sudo apt-get update
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release.gpg [189B]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Translation-en_US
Hit [http://hu.archive.ubuntu.com](http://hu.archive.ubuntu.com) hardy Release.gpg
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Translation-en_US
Ign [http://hu.archive.ubuntu.com](http://hu.archive.ubuntu.com) hardy/main Translation-en_US
Ign [http://hu.archive.ubuntu.com](http://hu.archive.ubuntu.com) hardy/restricted Translation-en_US
Ign [http://hu.archive.ubuntu.com](http://hu.archive.ubuntu.com) hardy/universe Translation-en_US
Ign [http://hu.archive.ubuntu.com](http://hu.archive.ubuntu.com) hardy/multiverse Translation-en_US
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release [58.5kB]
Hit [http://hu.archive.ubuntu.com](http://hu.archive.ubuntu.com) hardy-updates Release.gpg
Ign [http://hu.archive.ubuntu.com](http://hu.archive.ubuntu.com) hardy-updates/main Translation-en_US
Ign [http://hu.archive.ubuntu.com](http://hu.archive.ubuntu.com) hardy-updates/restricted Translation-en_US
Ign [http://hu.archive.ubuntu.com](http://hu.archive.ubuntu.com) hardy-updates/universe Translation-en_US
Ign [http://hu.archive.ubuntu.com](http://hu.archive.ubuntu.com) hardy-updates/multiverse Translation-en_US
Hit [http://hu.archive.ubuntu.com](http://hu.archive.ubuntu.com) hardy Release
Hit [http://hu.archive.ubuntu.com](http://hu.archive.ubuntu.com) hardy-updates Release
Hit [http://hu.archive.ubuntu.com](http://hu.archive.ubuntu.com) hardy/main Packages
Hit [http://hu.archive.ubuntu.com](http://hu.archive.ubuntu.com) hardy/restricted Packages
Hit [http://hu.archive.ubuntu.com](http://hu.archive.ubuntu.com) hardy/main Sources
Hit [http://hu.archive.ubuntu.com](http://hu.archive.ubuntu.com) hardy/restricted Sources
Hit [http://hu.archive.ubuntu.com](http://hu.archive.ubuntu.com) hardy/universe Packages
Hit [http://hu.archive.ubuntu.com](http://hu.archive.ubuntu.com) hardy/universe Sources
Hit [http://hu.archive.ubuntu.com](http://hu.archive.ubuntu.com) hardy/multiverse Packages
Hit [http://hu.archive.ubuntu.com](http://hu.archive.ubuntu.com) hardy/multiverse Sources
Hit [http://hu.archive.ubuntu.com](http://hu.archive.ubuntu.com) hardy-updates/main Packages
Hit [http://hu.archive.ubuntu.com](http://hu.archive.ubuntu.com) hardy-updates/restricted Packages
Hit [http://hu.archive.ubuntu.com](http://hu.archive.ubuntu.com) hardy-updates/main Sources
Hit [http://hu.archive.ubuntu.com](http://hu.archive.ubuntu.com) hardy-updates/restricted Sources
Hit [http://hu.archive.ubuntu.com](http://hu.archive.ubuntu.com) hardy-updates/universe Packages
Hit [http://hu.archive.ubuntu.com](http://hu.archive.ubuntu.com) hardy-updates/universe Sources
Hit [http://hu.archive.ubuntu.com](http://hu.archive.ubuntu.com) hardy-updates/multiverse Packages
Hit [http://hu.archive.ubuntu.com](http://hu.archive.ubuntu.com) hardy-updates/multiverse Sources
Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Packages [119kB]
Get:4 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Packages [7487B]
Get:5 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Sources [22.5kB]
Get:6 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Sources [892B]
Get:7 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Packages [58.0kB]
Get:8 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Sources [9367B]
Get:9 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Packages [11.2kB]
Get:10 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Sources [1105B]
Fetched 289kB in 3s (95.4kB/s)
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.
light@MIND:~$ dpkg --configure -a
dpkg: requested operation requires superuser privilege

Sorry... it is still... 

Next step?

Thanks!

Tamas

---

### Post by taurus on 2009-02-25
You need to include the sudo in front since you want to run it with root privilege.

```
sudo dpkg --configure -a
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by koosfoto.hu on 2009-02-25
Thanks for your patiance and help!
Wow... this last one was stupid from me... Yes, I should have known sudo.

So, it WORKS now!!!!!!!!!!!! :-)

Thanks a lot!!!!!!!!!

Greetings

Tamas

---

