---
title: "Add/Remove... Does not work"
date: 2009-02-19
forum: Installation &amp; Upgrades
---

### Post by LobbyDizzle on 2009-02-19
I tried to install Vuze, and the installation crashed a bit through, I delete all of the folders where Vuze and Azureus existed. Now, when I try to install anything from Add/Remove..., I click the check box and I get the error message,

[B]Cannot install '3dchess'

This application conflicts with other installed software. To install '3dchess' the conflicting software must be removed first.

Switch to the 'synaptic' package manager to resolve this conflict.[/B]

This really really sucks.

---

### Post by taurus on 2009-02-19
Close add/remove or synaptic.  Then, open a terminal and run

Applications -> Accessories -> Terminal
```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by LobbyDizzle on 2009-02-19
That looked promising, but I still get the same error, and in synaptic package manager I get the errors:

[B]
gnome-btdownload:
 Depends: bittorrent (>=3.3) but it is not installable[/B]

---

### Post by taurus on 2009-02-19
Can you post your /etc/apt/sources.list?

```
cat /etc/apt/sources.list
```

---

### Post by LobbyDizzle on 2009-02-19
sure...

jared@jared-laptop:~$ cat /etc/apt/sources.list
#deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5)]/ intrepid main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

#deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid main restricted
#deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid main restricted

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hardy universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hardy universe multiverse

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security multiverse

---

### Post by taurus on 2009-02-19
You are running intrepid but how come you have two entries for hardy?

```

deb http://archive.ubuntu.com/ubuntu **[COLOR="Red"]hardy[/COLOR]** universe multiverse
deb-src http://archive.ubuntu.com/ubuntu **[COLOR="Red"]hardy[/COLOR]** universe multiverse

```
You need to edit /etc/apt/sources.list

```
gksudo gedit /etc/apt/sources.list
```
and remove those two entries.  Save it and then run

```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by LobbyDizzle on 2009-02-19
That's f'en weird, but it didn't fix the problem. I'm still getting the error both in add/remove and synaptic package manager.

---

### Post by taurus on 2009-02-19
Can you post the whole outputs of those two commands?

---

### Post by LobbyDizzle on 2009-02-19
jared@jared-laptop:~$ sudo apt-get update
[sudo] password for jared: 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security Release.gpg
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/restricted Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates Release.gpg        
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/main Translation-en_US
Hit [http://repository.akirad.net](http://repository.akirad.net) akirad-intrepid Release.gpg         
Ign [http://repository.akirad.net](http://repository.akirad.net) akirad-intrepid/main Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/multiverse Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security Release             
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid Release.gpg
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates Release
Hit [http://repository.akirad.net](http://repository.akirad.net) akirad-intrepid Release             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid Release                    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main Packages                 
Hit [http://repository.akirad.net](http://repository.akirad.net) akirad-intrepid/main Packages       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/multiverse Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/multiverse Sources
Reading package lists... Done
jared@jared-laptop:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
jared@jared-laptop:~$

---

### Post by taurus on 2009-02-19
```
sudo apt-get install 3dchess
```

---

### Post by LobbyDizzle on 2009-02-19
jared@jared-laptop:~$ sudo apt-get install 3dchess
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  3dchess: Depends: xaw3dg (>= 1.5+E-1) but it is not installable
E: Broken packages
jared@jared-laptop:~$

---

### Post by taurus on 2009-02-19
Edit /etc/apt/sources.list again and remove the # in front of these two lines.

```

deb http://archive.canonical.com/ubuntu intrepid partner
deb-src http://archive.canonical.com/ubuntu intrepid partner

```
Save it and then run

```
sudo apt-get update
sudo apt-get install 3dchess
```

---

### Post by LobbyDizzle on 2009-02-19
I got the same message.

---

### Post by LobbyDizzle on 2009-02-19
This is weird though, installed Thunderbird and Lightning around 2am using add/remove.

---

### Post by pirate_tux on 2009-02-19
> **LobbyDizzle said:**
> This is weird though, installed Thunderbird and Lightning around 2am using add/remove.

Post the outpout of this:

aptitude -s install xaw3dg

---

### Post by LobbyDizzle on 2009-02-19
jared@jared-laptop:~$ aptitude -s install xaw3dg
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
No candidate version found for xaw3dg
No candidate version found for xaw3dg
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Would download/install/remove packages.
jared@jared-laptop:~$

---

### Post by pirate_tux on 2009-02-19
> **LobbyDizzle said:**
> jared@jared-laptop:~$ aptitude -s install xaw3dg
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
No candidate version found for xaw3dg
No candidate version found for xaw3dg
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Would download/install/remove packages.
jared@jared-laptop:~$

Ok. It seems there's no current version of xaw3dg on the repositories you have on your sources.list. That's why you can't install 3dchess.

---

### Post by LobbyDizzle on 2009-02-19
Well, 3dchess isn't the only thing I can't install, I can't install anything at all...

[B]jared@jared-laptop:~$ sudo apt-get install bittorrent
[sudo] password for jared: 
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

jared@jared-laptop:~$ sudo apt-get install vuze
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
jared@jared-laptop:~$ [/B]

and in Synaptic:

[B]gnome-btdownload:
 Depends: bittorrent (>=3.3) but it is not installable[/B]

---

### Post by pirate_tux on 2009-02-19
> **LobbyDizzle said:**
> Well, 3dchess isn't the only thing I can't install, I can't install anything at all...

[B]jared@jared-laptop:~$ sudo apt-get install bittorrent
[sudo] password for jared: 
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

jared@jared-laptop:~$ sudo apt-get install vuze
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
jared@jared-laptop:~$ [/B]

and in Synaptic:

[B]gnome-btdownload:
 Depends: bittorrent (>=3.3) but it is not installable[/B]

That's probably because automatic update is working...

---

### Post by LobbyDizzle on 2009-02-19
What do I do to fix that?

---

### Post by pirate_tux on 2009-02-19
> **LobbyDizzle said:**
> What do I do to fix that?

Just wait for automatic update to terminate and then you will be able to install software.

---

### Post by LobbyDizzle on 2009-02-20
Autoupdate is not running and I still cannot install anything.

---

### Post by Partyboi2 on 2009-02-20
> [B]E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?[/B]
It normally means that you are trying to run a package manager when there is already one open or working. Make sure you have only one package manager open like synaptic, update manager, apt-get.
You can also open a terminal and check what processes are running by
```
ps -e
```If there is already a package manager listed you can end it by 
```
killall process
``` Change process to actual name.

Edit: After you have made sure there is no package manager running open a terminal and type
```
sudo apt-get -f install
```

---

### Post by LobbyDizzle on 2009-02-20
Here's the output of the two commands other than kill:

[B]jared@jared-laptop:~$ ps -e
  PID TTY          TIME CMD
    1 ?        00:00:01 init
    2 ?        00:00:00 kthreadd
    3 ?        00:00:00 migration/0
    4 ?        00:00:01 ksoftirqd/0
    5 ?        00:00:00 watchdog/0
    6 ?        00:00:00 migration/1
    7 ?        00:00:05 ksoftirqd/1
    8 ?        00:00:00 watchdog/1
    9 ?        00:00:00 events/0
   10 ?        00:00:00 events/1
   11 ?        00:00:00 khelper
   51 ?        00:00:00 kintegrityd/0
   52 ?        00:00:00 kintegrityd/1
   54 ?        00:00:00 kblockd/0
   55 ?        00:00:00 kblockd/1
   57 ?        00:00:00 kacpid
   58 ?        00:00:00 kacpi_notify
  167 ?        00:00:00 cqueue
  171 ?        00:00:00 kseriod
  216 ?        00:00:00 pdflush
  217 ?        00:00:00 pdflush
  218 ?        00:00:00 kswapd0
  260 ?        00:00:00 aio/0
  261 ?        00:00:00 aio/1
 1422 ?        00:00:00 ksuspend_usbd
 1424 ?        00:00:00 khubd
 1453 ?        00:00:00 khpsbpkt
 1472 ?        00:00:00 ata/0
 1473 ?        00:00:04 ata/1
 1474 ?        00:00:00 ata_aux
 2263 ?        00:00:00 scsi_eh_0
 2264 ?        00:00:00 usb-storage
 2286 ?        00:00:00 knodemgrd_0
 2296 ?        00:00:00 scsi_eh_1
 2302 ?        00:00:00 scsi_eh_2
 2357 ?        00:00:00 scsi_eh_3
 2359 ?        00:00:06 scsi_eh_4
 2524 ?        00:00:00 kjournald
 3047 ?        00:00:00 udevd
 3414 ?        00:00:00 kmmcd
 3552 ?        00:00:00 kpsmoused
 5359 tty4     00:00:00 getty
 5360 tty5     00:00:00 getty
 5367 tty2     00:00:00 getty
 5368 tty3     00:00:00 getty
 5369 tty6     00:00:00 getty
 5574 ?        00:00:00 acpid
 5618 ?        00:00:00 kondemand/0
 5619 ?        00:00:00 kondemand/1
 5703 ?        00:00:00 syslogd
 5762 ?        00:00:00 dd
 5770 ?        00:00:00 klogd
 5808 ?        00:00:03 dbus-daemon
 5833 ?        00:00:02 avahi-daemon
 5834 ?        00:00:00 avahi-daemon
 6044 ?        00:00:00 cupsd
 6227 ?        00:00:00 chipcardd4
 6228 ?        00:02:56 chipcardd4
 6299 ?        00:00:00 winbindd
 6327 ?        00:00:00 winbindd
 6331 ?        00:00:23 hald
 6334 ?        00:00:00 console-kit-dae
 6400 ?        00:00:00 hald-runner
 6449 ?        00:00:00 hald-addon-inpu
 6468 ?        00:00:00 hald-addon-cpuf
 6469 ?        00:00:00 hald-addon-acpi
 6503 ?        00:00:09 hald-addon-stor
 6590 ?        00:00:02 NetworkManager
 6610 ?        00:00:00 wpa_supplicant
 6613 ?        00:00:00 nm-system-setti
 6642 ?        00:00:00 gdm
 6645 ?        00:00:00 gdm
 6655 tty7     00:05:35 Xorg
 6719 ?        00:00:00 system-tools-ba
 6769 ?        00:00:00 atd
 6809 ?        00:00:00 cron
 7016 tty1     00:00:00 getty
 7025 ?        00:00:00 gnome-keyring-d
 7036 ?        00:00:00 x-session-manag
 7092 ?        00:00:00 dbus-launch
 7093 ?        00:00:00 dbus-daemon
 7096 ?        00:02:15 pulseaudio
 7099 ?        00:00:00 gconf-helper
 7101 ?        00:00:08 gconfd-2
 7107 ?        00:00:00 seahorse-agent
 7110 ?        00:00:00 gvfsd
 7115 ?        00:00:00 gnome-keyring-d
 7121 ?        00:00:00 gvfs-fuse-daemo
 7125 ?        00:00:09 gnome-settings-
 7126 ?        00:00:00 compiz
 7190 ?        00:01:28 compiz.real
 7194 ?        00:00:11 gnome-screensav
 7199 ?        00:00:00 sh
 7200 ?        00:00:00 compiz-decorato
 7202 ?        00:00:07 gtk-window-deco
 7203 ?        00:00:22 gnome-panel
 7205 ?        00:00:03 nautilus
 7207 ?        00:00:00 bonobo-activati
 7217 ?        00:00:00 gvfs-hal-volume
 7219 ?        00:00:00 gvfs-gphoto2-vo
 7223 ?        00:00:00 gvfsd-burn
 7226 ?        00:00:05 trashapplet
 7231 ?        00:00:02 gvfsd-trash
 7273 ?        00:00:09 gweather-applet
 7276 ?        00:00:00 battstat-applet
 7279 ?        00:00:00 fast-user-switc
 7287 ?        00:00:51 conduit
 7288 ?        00:00:00 python
 7289 ?        00:00:00 bluetooth-apple
 7297 ?        00:00:01 update-notifier
 7298 ?        00:00:00 evolution-alarm
 7299 ?        00:00:00 trackerd
 7301 ?        00:00:00 tracker-applet
 7302 ?        00:02:38 python
 7303 ?        00:00:00 python
 7304 ?        00:00:02 nm-applet
 7305 ?        00:00:00 python
 7307 ?        00:00:02 gnome-power-man
 7350 ?        00:00:00 evolution-data-
 7379 ?        00:00:00 evolution-excha
 7415 ?        00:00:00 python
 7477 ?        00:00:00 dhclient
 7518 ?        00:00:03 notification-da
17643 ?        00:04:14 firefox
18505 ?        00:00:00 anacron
18718 ?        00:00:00 sh
18719 ?        00:00:00 run-parts
18730 ?        00:00:00 apt
18746 ?        00:00:00 sleep
19005 ?        00:00:00 sh <defunct>
19010 ?        00:00:00 sh
19011 ?        00:00:00 gnome-terminal
19013 ?        00:00:00 gnome-pty-helpe
19014 pts/0    00:00:00 bash
19032 pts/0    00:00:00 ps
jared@jared-laptop:~$ sudo apt-get -f install
[sudo] password for jared: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
jared@jared-laptop:~$ 
[/B]

---

### Post by Partyboi2 on 2009-02-20
> [B]jared@jared-laptop:~$ sudo apt-get -f install
[sudo] password for jared: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
jared@jared-laptop:~$ [/B]
Looking at that you are know longer getting
> [B]E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?[/B]I tried using your sources.list to install  gnome-btdownload but received the same dependency problem you are getting > gnome-btdownload:
 Depends: bittorrent (>=3.3) but it is not installable But when I replaced the sources.list with a clean one, it installed gnome-btdownload with no problems. So what I would suggest is go [[COLOR=Blue]here[/COLOR]]("http://repogen.simplylinux.ch/") and create a new sources.list
Then backup your current sources.list
```
sudo cp /etc/apt/sources.list /etc/apt/sources.list.broken
```Then Open /etc/apt/sources.list and delete the contents and replace with the new one
```
gksu gedit /etc/apt/sources.list
``` Once you have replaced it and saved, back in the terminal
```
sudo apt-get update
sudo apt-get install gnome-btdownload 3dchess
```

---

### Post by LobbyDizzle on 2009-02-20
Holy ****! it work! Thank you sir, you are a saint.

---

