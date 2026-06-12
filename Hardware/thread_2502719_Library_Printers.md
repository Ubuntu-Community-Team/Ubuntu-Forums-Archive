---
title: "Library Printers"
date: 2024-11-26
forum: Hardware
---

### Post by cmcanulty on 2024-11-26
Since upgrading to Xubuntu 24.04 I can't install any of our HP network printers. All was fine before the upgrade. I tried the HPLIP from their website and that failed. Then I installed HPLIP from synaptic. It installed but sees no printers. Then I tried hplip from snap still no luck seeing the printers. I have had Xubuntu on all 11 of our public computers but if I can't get this fixed soon the librarian will force them back to windows after 17 years of Xubuntu success.


I always try system config printers first. Th snap app said to enter [http://localhost:8000/](http://localhost:8000/) in a browser to run the snap hplip but that gives an error unable to connect. I am sure the network is OK as I run the router and all the network equipment. I also tried localhost:631 which takes me to the cups add printer page and no luck there either here is that error. It is an HP color laser HP_OfficeJet_Pro_8740

Add Printer
Add Printer HPColor Error

Unable to get list of printer drivers:

    Success

Add Printer HPColor Error

Unable to get list of printer drivers:

    Success
 Please help

---

### Post by yancek on 2024-11-27
So you first get the message "Success" followed by the error "Unable to get list of printer drivers:".  

> I tried the HPLIP from their website and that failed. 

What failed, downloading drivers?  If the different methods you have tried were not successful, did you get any error messages?

---

### Post by him610 on 2024-11-28
Can you fall back to 22.04.n on all computers except for one to use as 24.04 test platform?

After you have worked out issues on 24.04 test platform, proceed with upgrading computers one-by-one bringing each online when you are assured the issue has been resolved.

---

### Post by cmcanulty on 2024-11-28
the main issue I think is HP uses hplip for all it's printer drivers for linux and hplip doesn't seem to work on 24.04. The latest hplip on their web site doesn't support 24.04. I have installed the hplip from the repositories for 24.04 and that version installs but when I go to add a printer hplip doesn't show as an option. hplip always worked flawlessly until recently and that's why we only use HP printers. I don't know of any other way to get printer drivers for hp in ubuntu.

---

### Post by oldfred on 2024-11-28
Printers have been driverless to work with Windows & Apple for quite a while.

Linux now supports driverless printing. And uses it for USB also, now.
[https://wiki.debian.org/CUPSDriverlessPrinting](https://wiki.debian.org/CUPSDriverlessPrinting)
[https://wiki.debian.org/CUPSDriverlessPrinting#ippoverusb](https://wiki.debian.org/CUPSDriverlessPrinting#ippoverusb)

Check you have these:
install ipp-usb and sane-airscan
avahi-browse -rt _ipp._tcp
avahi-browse -rt _uscan._tcp
 ippfind
scanimage -L
airscan-discover

[https://forums.linuxmint.com/viewtopic.php?t=344245](https://forums.linuxmint.com/viewtopic.php?t=344245)

I have a Brother printer that is both USB & Internet. But I am now at Daughter's for Thanksgiving.
It shows this, and I did not do anything. It normally shows my Brother printer. So ppd file auto created.
```
[FONT=monospace][COLOR=#54ff54]**fred@m2-noble**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**~**[/COLOR][COLOR=#000000]$  ll /etc/cups/ppd/ [/COLOR]
total 28 
drwxr-xr-x 2 root lp  4096 Nov 28 09:35 [COLOR=#5454ff]**.**[/COLOR][COLOR=#000000]/ [/COLOR]
drwxr-xr-x 5 root lp  4096 Nov 28 10:25 [COLOR=#5454ff]**..**[/COLOR][COLOR=#000000]/ [/COLOR]
-rw-r----- 1 root lp 17328 Nov 28 09:35 HP_Color_LaserJet_MFP_M180nw_CB6CFE.ppd


[/FONT]
```

---

### Post by him610 on 2024-11-28
From LTS 24.04.1
```

$ apt show hplip
Package: hplip
Version: 3.23.12+dfsg0-0ubuntu5
Priority: optional
Section: utils
Origin: Ubuntu
....
```
From LTS 22.04.5
```

$ apt show hplip
Package: hplip
Version: 3.21.12+dfsg0-1
Priority: optional
Section: utils
Origin: Ubuntu
....
```
Can you go back to earlier version 3.21.12+dfsg0-1?
Suggest follow up by submitting bug report.

Note: @oldfred #5 may have better suggestion

---

### Post by cmcanulty on 2024-11-28
OK to be clear  the printers aren't attached to a computer but by ethernet to an ethernet ports networked to the library system does this still work with ipp-usb? All the computers are on the library network. or is there another way to do it? One printer we could attach to a computer by usb. The other one HP8740 is a multi-function and is in our public area and would not be attached to a computer easily Thank you

---

### Post by yancek on 2024-11-28
The problems you reported in your initial post seem more like network problems.  Have you verified physically that the printer in question is plugged in and powered on.  Some suggestions at the link below

[https://askubuntu.com/questions/1519394/printing-not-working-on-ubuntu-24-04](https://askubuntu.com/questions/1519394/printing-not-working-on-ubuntu-24-04)

Since your printer is on a network, have you tried to ping it?  Is it detected with nmap?  More

---

### Post by cmcanulty on 2024-11-28
yes I can ping it successfully but not install it, very weird

---

### Post by oldfred on 2024-11-28
Did you run any of the commands in post #5?
They show various bits of info on my Son-in-Laws HP network printer.

---

### Post by cmcanulty on 2024-11-29
yes and no luck with anything yet when I did with local ips

```
hp-setup xxx.xxx.x.x
```

it showed the printer in some machines and in 2 let me set it up and the others it wouldn't set up and always the scanner wasn't detected. I have both users in sane and scanner groups. When I used to do printer setup in settings manager hplip was an option and set up worked flawlessly. Now that is never an option in printer setup but I googled all day yesterday and found the option of the command line hp-setup then ip address to access it

---

### Post by him610 on 2024-11-30
Well, I just read an article in The Register [https://www.theregister.com/2024/11/26/microsoft_escl_issue/]("https://www.theregister.com/2024/11/26/microsoft_escl_issue/") that Windows 11 is having issues with eSCL devices - printers, scanners, fax machines. 

Here is an interesting bit from the article,
> The eSCL protocol comes from the Mopria eSCL specification. It enables driverless scanning over a network – Ethernet or Wi-Fi – or USB connections.

Could it be a similar issue as to what Library Printers are experiencing?

---

### Post by Norm24 on 2024-11-30
I have no idea if this will help you as I'm a just home desktop user but when I first installed Mate 24.04 on my laptop I was unable to find and install my HP printer.Through some net research I downloaded and installed hplip and I was able to discover the printer but could not print anything.

The issue ended up being the firewall.I simply disabled ufw and I was able to print a test page.Re-enable ufw and was able to print again and I've had no issues since.

Again I have no idea if this will even help but I threw this out there just in case.

---

### Post by cmcanulty on 2024-11-30
I saw that but it isn't the issue. I downloaded the recommended best tar file for ubuntu 24.04-  hplip 3.23.12 and extracted it and then did ./configure and got the error 

```
configure: error: cannot find avahi_client support
```

but avahi is installed and the service is running:
 

```

librarian@Ubuntu5:~$ sudo systemctl status avahi-daemon
[sudo] password for librarian: 
&#9679; avahi-daemon.service - Avahi mDNS/DNS-SD Stack
     Loaded: loaded (/usr/lib/systemd/system/avahi-daemon.service; enabled; pre>
     Active: active (running) since Sat 2024-11-30 11:41:54 EST; 32min ago
TriggeredBy: &#9679; avahi-daemon.socket
   Main PID: 3783192 (avahi-daemon)
     Status: "avahi-daemon 0.8 starting up."
      Tasks: 2 (limit: 4372)
     Memory: 1008.0K (peak: 1.4M)
        CPU: 2.987s
     CGroup: /system.slice/avahi-daemon.service
             &#9500;&#9472;3783192 "avahi-daemon: running [Ubuntu5.local]"
             &#9492;&#9472;3783194 "avahi-daemon: chroot helper"

Nov 30 11:41:54 Ubuntu5 avahi-daemon[3783192]: Joining mDNS multicast group on >
Nov 30 11:41:54 Ubuntu5 avahi-daemon[3783192]: New relevant interface lo.IPv4 f>
Nov 30 11:41:54 Ubuntu5 avahi-daemon[3783192]: Network interface enumeration co>
Nov 30 11:41:54 Ubuntu5 avahi-daemon[3783192]: Registering new address record f>
Nov 30 11:41:54 Ubuntu5 avahi-daemon[3783192]: Registering new address record f>
Nov 30 11:41:54 Ubuntu5 avahi-daemon[3783192]: Registering new address record f>
Nov 30 11:41:54 Ubuntu5 avahi-daemon[3783192]: Registering new address record f>
Nov 30 11:41:54 Ubuntu5 avahi-daemon[3783192]: Files changed, reloading.
Nov 30 11:41:54 Ubuntu5 avahi-daemon[3783192]: No service file found in /etc/av>
Nov 30 11:41:55 Ubuntu5 avahi-daemon[3783192]: Server startup complete. Host na>
lines 1-23
```

this is just wackamole I have been running the library system 24 years and after  a week of wasting all my time on this I don't know what to do next

---

### Post by 1fallen on 2024-11-30
Will you show us this please:
```
apt depends hplip | grep python3
```
This is what I now show:
```
 Depends: python3-dbus
  Depends: python3-gi
  Depends: python3-pexpect
  Depends: python3-pil
  Depends: <python3:any>
    python3
  Depends: python3 (<< 3.13)
  Depends: python3 (>= 3.12~)
  Depends: libpython3.12t64 (>= 3.12.1)
  Suggests: python3-notify2
  Suggests: python3-reportlab



```

---

### Post by cmcanulty on 2024-11-30
weird it only gives the avahi error not any dependency issues avahi service is on and running



```
librarian@Ubuntu5:~$ apt depends hplip | grep python3

WARNING: apt does not have a stable CLI interface. Use with caution in scripts.

  Depends: python3-dbus
  Depends: python3-gi
  Depends: python3-pexpect
  Depends: python3-pil
  Depends: <python3:any>
    python3:i386
    python3
  Depends: python3 (<< 3.13)
  Depends: python3 (>= 3.12~)
  Depends: libpython3.12t64 (>= 3.12.1)
  Suggests: python3-notify2
  Suggests: python3-reportlab
```

---

### Post by 1fallen on 2024-11-30
This seems to at times and I hope very much this is one of those times that purge and reinstall helps. (Seeing how we are playing whackamole)
```
sudo apt purge hplip hplip-data hplip-doc hplip-gui hpijs-ppds libsane-hpaio printer-driver-hpcups printer-driver-hpijs
```
Then a Re-install 
```
sudo apt install hplip hplip-gui  python3-notify2  python3-reportlab  system-config-printer



```
It should not touch any edits you have previously.

Full Install will look like this:
```
Installing:                     
  hplip  hplip-gui  python3-notify2  python3-reportlab  system-config-printer

Installing dependencies:
  avahi-utils         libcamd3          libgimp2.0t64          python3-freetype
  cups-pk-helper      libccolamd3       libinih1               python3-rlpycairo
  fonts-dejavu-extra  libcholmod5       libinireader0          system-config-printer-common
  gimp-data           libcolamd3        libsane-hpaio          system-config-printer-udev
  gir1.2-polkit-1.0   libexiv2-28       libsuitesparseconfig7  xsane
  gir1.2-secret-1     libexiv2-data     libumfpack6            xsane-common
  hplip-data          libgegl-0.4-0t64  printer-driver-hpcups
  libamd3             libgegl-common    python3-cups
  libbabl-0.1-0       libgexiv2-2       python3-cupshelpers

Suggested packages:
  hplip-doc   python3-egenix-mxtexttools  gnome-software  | cuneiform      hylafax-client
  exiv2       python-reportlab-doc        python3-smbc    | tesseract-ocr  | mgetty-fax
  graphviz    rl-accel                    gimp            | ocrad
  pdf-viewer  rl-renderpm                 gocr            gv

Summary:
  Upgrading: 0, Installing: 38, Removing: 0, Not Upgrading: 0
  Download size: 33.9 MB
  Space needed: 156 MB / 462 GB available

Continue? [Y/n] 


```
Fingers Crossed

---

### Post by cmcanulty on 2024-11-30
1st command not any return like yours

```
librarian@Ubuntu5:~$ sudo apt purge hplip hplip-data hplip-doc hplip-gui hpijs-ppds libsane-hpaio printer-driver-hpcups printer-driver-hpijs
[sudo] password for librarian: 
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libhpmud0 python3-dbus.mainloop.pyqt5 python3-notify2
Use 'sudo apt autoremove' to remove them.
The following packages will be REMOVED:
  hpijs-ppds* hplip* hplip-data* hplip-doc* hplip-gui* libsane-hpaio*
  printer-driver-hpcups* printer-driver-hpijs*
0 upgraded, 0 newly installed, 8 to remove and 0 not upgraded.
After this operation, 17.9 MB disk space will be freed.
Do you want to continue? [Y/n] y
(Reading database ... 327898 files and directories currently installed.)
Removing hpijs-ppds (3.23.12+dfsg0-0ubuntu5) ...
Removing hplip-gui (3.23.12+dfsg0-0ubuntu5) ...
Removing hplip (3.23.12+dfsg0-0ubuntu5) ...
Removing hplip-data (3.23.12+dfsg0-0ubuntu5) ...
dpkg: warning: while removing hplip-data, directory '/usr/share/hplip/ui5' not empty so not removed
dpkg: warning: while removing hplip-data, directory '/usr/share/hplip/scan' not 
empty so not removed
dpkg: warning: while removing hplip-data, directory '/usr/share/hplip/prnt' not 
empty so not removed
dpkg: warning: while removing hplip-data, directory '/usr/share/hplip/pcard' not
 empty so not removed
dpkg: warning: while removing hplip-data, directory '/usr/share/hplip/installer'
 not empty so not removed
dpkg: warning: while removing hplip-data, directory '/usr/share/hplip/fax' not e
mpty so not removed
dpkg: warning: while removing hplip-data, directory '/usr/share/hplip/copier' no
t empty so not removed
dpkg: warning: while removing hplip-data, directory '/usr/share/hplip/base/pexpe
ct' not empty so not removed
Removing hplip-doc (3.23.12+dfsg0-0ubuntu5) ...
Removing libsane-hpaio:amd64 (3.23.12+dfsg0-0ubuntu5) ...
No diversion 'diversion of /lib/udev/rules.d/56-hpmud.rules to /lib/udev/rules.d
/56-hpmud.rules.usr-is-merged by usr-is-merged', none removed.
Removing printer-driver-hpcups (3.23.12+dfsg0-0ubuntu5) ...
Removing printer-driver-hpijs (3.23.12+dfsg0-0ubuntu5) ...
Processing triggers for doc-base (0.11.2) ...
Processing 1 removed doc-base file...
Processing triggers for cups (2.4.7-1.2ubuntu7.3) ...
lpinfo: Success
Processing triggers for gnome-menus (3.36.0-1.1ubuntu3) ...
Processing triggers for man-db (2.12.0-4build2) ...
Processing triggers for dbus (1.14.10-4ubuntu4.1) ...
Processing triggers for desktop-file-utils (0.27-2build1) ...
(Reading database ... 327146 files and directories currently installed.)
Purging configuration files for hplip (3.23.12+dfsg0-0ubuntu5) ...
Purging configuration files for hplip-gui (3.23.12+dfsg0-0ubuntu5) ...
Purging configuration files for libsane-hpaio:amd64 (3.23.12+dfsg0-0ubuntu5) ...
dpkg: warning: while removing libsane-hpaio:amd64, directory '/usr/share/hplip' not empty so not removed
Processing triggers for dbus (1.14.10-4ubuntu4.1) ...
librarian@Ubuntu5:~$ librarian@Ubuntu5:~$ sudo apt install hplip hplip-gui  python3-notify2  python3-reportlab  system-config-printer
librarian@Ubuntu5:~$
```

2nd command

[code]librarian@Ubuntu5:~$ sudo apt install hplip hplip-gui  python3-notify2  python3-reportlab  system-config-printer
[sudo] password for librarian: 
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
python3-notify2 is already the newest version (0.3-5).
python3-notify2 set to manually installed.
python3-reportlab is already the newest version (4.1.0-4).
system-config-printer is already the newest version (1.5.18-1ubuntu9).
system-config-printer set to manually installed.
Suggested packages:
  hplip-doc
The following NEW packages will be installed:
  hplip hplip-data hplip-gui libsane-hpaio printer-driver-hpcups
0 upgraded, 5 newly installed, 0 to remove and 0 not upgraded.
Need to get 247 kB/7,072 kB of archives.
After this operation, 15.0 MB of additional disk space will be used.
Get:1 http://archive.ubuntu.com/ubuntu noble/main amd64 printer-driver-hpcups amd64 3.23.12+dfsg0-0ubuntu5 [247 kB]
Fetched 247 kB in 0s (757 kB/s)                
Selecting previously unselected package hplip-data.
(Reading database ... 327141 files and directories currently installed.)
Preparing to unpack .../hplip-data_3.23.12+dfsg0-0ubuntu5_all.deb ...
Unpacking hplip-data (3.23.12+dfsg0-0ubuntu5) ...
Selecting previously unselected package libsane-hpaio:amd64.
Preparing to unpack .../libsane-hpaio_3.23.12+dfsg0-0ubuntu5_amd64.deb ...
Unpacking libsane-hpaio:amd64 (3.23.12+dfsg0-0ubuntu5) ...
Selecting previously unselected package printer-driver-hpcups.
Preparing to unpack .../printer-driver-hpcups_3.23.12+dfsg0-0ubuntu5_amd64.deb .
..
Unpacking printer-driver-hpcups (3.23.12+dfsg0-0ubuntu5) ...
Selecting previously unselected package hplip.
Preparing to unpack .../hplip_3.23.12+dfsg0-0ubuntu5_amd64.deb ...
Unpacking hplip (3.23.12+dfsg0-0ubuntu5) ...
Selecting previously unselected package hplip-gui.
Preparing to unpack .../hplip-gui_3.23.12+dfsg0-0ubuntu5_all.deb ...
Unpacking hplip-gui (3.23.12+dfsg0-0ubuntu5) ...
Setting up hplip-data (3.23.12+dfsg0-0ubuntu5) ...
/usr/share/hplip/base/imagesize.py:186: SyntaxWarning: invalid escape sequence '
\#'
  re.compile('\#define\s+\S+\s+\d+')     : ('image/x-xbitmap', xbmsize),
/usr/share/hplip/base/imagesize.py:187: SyntaxWarning: invalid escape sequence '
\/'
  re.compile('\/\* XPM \*\/')            : ('image/x-xpixmap', xpmsize),
/usr/share/hplip/base/imagesize.py:189: SyntaxWarning: invalid escape sequence '
\*'
  re.compile('^II\*\x00')                : ('image/tiff', tiffsize),
/usr/share/hplip/fax/ledmfax.py:46: SyntaxWarning: invalid escape sequence '\d'
  http_result_pat = re.compile(b"""HTTP/\d.\d\s(\d+)""", re.I)
Setting up printer-driver-hpcups (3.23.12+dfsg0-0ubuntu5) ...
Setting up libsane-hpaio:amd64 (3.23.12+dfsg0-0ubuntu5) ...
No diversion 'diversion of /lib/udev/rules.d/56-hpmud.rules to /lib/udev/rules.d
/56-hpmud.rules.usr-is-merged by usr-is-merged', none removed.
Setting up hplip (3.23.12+dfsg0-0ubuntu5) ...
Creating/updating hplip user account...
Setting up hplip-gui (3.23.12+dfsg0-0ubuntu5) ...
Processing triggers for desktop-file-utils (0.27-2build1) ...
Processing triggers for cups (2.4.7-1.2ubuntu7.3) ...
lpinfo: Success
Processing triggers for gnome-menus (3.36.0-1.1ubuntu3) ...
Processing triggers for man-db (2.12.0-4build2) ...
Processing triggers for dbus (1.14.10-4ubuntu4.1) ...
librarian@Ubuntu5:~$ [code]

---

### Post by cmcanulty on 2024-11-30
now i tried ```
hp-setup 192.168.1.167
``` and it pops up with the printer and 


```
Printer queue setup failed.  
```

when I hit next I get this error which google says is insufficient permissions must be run as root so I redid it with sudo 

```
sudo hp-setup 192.168.1.167
```

and get same error

then based on that error I installed  printer-driver-hpijs and then no change same error

then I installed 
```

sudo apt install python3-pip
sudo apt-get install --assume-yes python3-pyqt5
sudo apt-get install --assume-yes python3-dbus.mainloop.pyqt5
sudo apt-get install --assume-yes python3-notify

and 

sudo apt-get install libcanberra-gtk-module
```

then I got one step further it let me name the printer and location and then get same error

```
Printer queue setup failed.  
```

---

### Post by 1fallen on 2024-11-30
It just might be left over cruft, please show this again:
```
ll /etc/cups/ppd/ 


```
This is very weird to me.

Also if you spin up a bootable USB of 24.04. can you see the printer/s?

---

### Post by cmcanulty on 2024-11-30
librarian@Ubuntu5:~$ ll /etc/cups/ppd/
total 8
drwxr-xr-x 2 root lp 4096 Nov 28 16:13 ./
drwxr-xr-x 5 root lp 4096 Nov 30 14:52 ../
librarian@Ubuntu5:~$


i can't do that as I am working remotely I can try that when I go in Thursday

---

### Post by cmcanulty on 2024-11-30
I found another command that lists multiple things needed some of which aren't even in synaptic. why does hplip install without all these needed apps.

```

librarian@Ubuntu5:~$ hp-doctor

HP Linux Imaging and Printing System (ver. 3.23.12)
Self Diagnse Utility and Healing Utility ver. 1.0

Copyright (c) 2001-18 HP Development Company, LP
This software comes with ABSOLUTELY NO WARRANTY.
This is free software, and you are welcome to distribute it
under certain conditions. See COPYING file for more details.


HP Linux Imaging and Printing System (ver. 3.23.12)
Self Diagnse Utility and Healing Utility ver. 1.0

Copyright (c) 2001-18 HP Development Company, LP
This software comes with ABSOLUTELY NO WARRANTY.
This is free software, and you are welcome to distribute it
under certain conditions. See COPYING file for more details.

 

Checking for Deprecated items....
No Deprecated items are found


Checking for HPLIP updates....
error: Failed to locate hp-upgrade utility


Checking for Dependencies....
warning: ubuntu-24.04 version is not supported. Using ubuntu-23.04 versions dependencies to verify and install...

---------------
| SYSTEM INFO |
---------------

 Kernel: 6.8.0-49-generic #49-Ubuntu SMP PREEMPT_DYNAMIC Mon Nov  4 02:06:24 UTC 2024 GNU/Linux
 Host: Ubuntu5
 Proc: 6.8.0-49-generic #49-Ubuntu SMP PREEMPT_DYNAMIC Mon Nov  4 02:06:24 UTC 2024 GNU/Linux
 Distribution: ubuntu 24.04
 Bitness: 64 bit


-----------------------
| HPLIP CONFIGURATION |
-----------------------

HPLIP-Version: HPLIP 3.23.12
HPLIP-Home: /usr/share/hplip
warning: HPLIP-Installation: Auto installation is not supported for ubuntu distro  24.04 version 

Current contents of '/etc/hp/hplip.conf' file:
# hplip.conf.  Generated from hplip.conf.in by configure.

[hplip]
version=3.23.12

[dirs]
home=/usr/share/hplip
run=/var/run
ppd=/usr/share/ppd/hplip/HP
ppdbase=/usr/share/ppd/hplip
doc=/usr/share/doc/hplip
html=/usr/share/doc/hplip-doc
icon=no
cupsbackend=/usr/lib/cups/backend
cupsfilter=/usr/lib/cups/filter
drv=/usr/share/cups/drv
bin=/usr/bin
apparmor=/etc/apparmor.d
# Following values are determined at configure time and cannot be changed.
[configure]
network-build=yes
libusb01-build=no
pp-build=no
gui-build=yes
scanner-build=yes
fax-build=yes
dbus-build=yes
cups11-build=no
doc-build=yes
shadow-build=no
hpijs-install=yes
foomatic-drv-install=yes
foomatic-ppd-install=no
foomatic-rip-hplip-install=no
hpcups-install=yes
cups-drv-install=yes
cups-ppd-install=no
internal-tag=3.23.12
restricted-build=no
ui-toolkit=qt5
qt3=no
qt4=no
qt5=yes
policy-kit=yes
lite-build=no
udev_sysfs_rules=no
hpcups-only-build=no
hpijs-only-build=no
apparmor_build=no
class-driver=no


Current contents of '/var/lib/hp/hplip.state' file:
Plugins are not installed. Could not access file: No such file or directory

Current contents of '~/.hplip/hplip.conf' file:
[upgrade]
notify_upgrade = true
last_upgraded_time = 1535037295
pending_upgrade_time = 0
latest_available_version = 3.17.10

[last_used]
device_uri = hp:/net/HP_LaserJet_400_M401dw?ip=192.168.1.167
printer_name = 
working_dir = .

[installation]
date_time = 11/30/24 15:43:49
version = 3.23.12

[settings]
systray_visible = 2
systray_messages = 3

[commands]
scan = /usr/bin/xsane -V %SANE_URI%

[refresh]
rate = 30
enable = false
type = 1

[polling]
enable = false
interval = 5
device_list = 

[fax]
voice_phone = 
email_address = 


 <Package-name>        <Package-Desc>      <Required/Optional> <Min-Version> <Installed-Version> <Status>   <Comment>

-------------------------
| External Dependencies |
-------------------------

 error: cups          CUPS - Common Unix Printing System                           REQUIRED        1.1             -               INCOMPAT   'CUPS may not be installed or not running'
 gs                   GhostScript - PostScript and PDF language interpreter and previewer REQUIRED        7.05            10.02.1         OK         -
 error: xsane         xsane - Graphical scanner frontend for SANE                  OPTIONAL        0.9             -               MISSING    'xsane needs to be installed'
 scanimage            scanimage - Shell scanning program                           OPTIONAL        1.0             1.2.1           OK         -
 dbus                 DBus - Message bus system                                    REQUIRED        -               1.14.10         OK         -
 policykit            PolicyKit - Administrative policy framework                  OPTIONAL        -               -               OK         -
 network              network -wget                                                OPTIONAL        -               1.21.4          OK         -
 avahi-utils          avahi-utils                                                  OPTIONAL        -               0.8             OK         -

------------------------
| General Dependencies |
------------------------

 libjpeg              libjpeg - JPEG library                                       REQUIRED        -               -               OK         -
 error: cups-devel    CUPS devel- Common Unix Printing System development files    REQUIRED        -               -               MISSING    'cups-devel needs to be installed'
 error: cups-image    CUPS image - CUPS image development files                    REQUIRED        -               -               MISSING    'cups-image needs to be installed'
 libpthread           libpthread - POSIX threads library                           REQUIRED        -               b'2.39'         OK         -
 libusb               libusb - USB library                                         REQUIRED        -               1.0             OK         -
 sane                 SANE - Scanning library                                      REQUIRED        -               -               OK         -
 sane-devel           SANE - Scanning library development files                    REQUIRED        -               -               OK         -
 error: libavahi-dev  libavahi-dev                                                 REQUIRED        -               -               MISSING    'libavahi-dev needs to be installed'
 libnetsnmp-devel     libnetsnmp-devel - SNMP networking library development files REQUIRED        5.0.9           5.9.4           OK         -
 libcrypto            libcrypto - OpenSSL cryptographic library                    REQUIRED        -               3.0.13          OK         -
 python3X             Python 2.2 or greater - Python programming language          REQUIRED        2.2             3.12.3          OK         -
 python3-notify2      Python libnotify - Python bindings for the libnotify Desktop notifications OPTIONAL        -               -               OK         -
 error: python3-pyqt4-dbus PyQt 4 DBus - DBus Support for PyQt4                         OPTIONAL        4.0             -               MISSING    'python3-pyqt4-dbus needs to be installed'
 error: python3-pyqt4 PyQt 4- Qt interface for Python (for Qt version 4.x)         REQUIRED        4.0             -               MISSING    'python3-pyqt4 needs to be installed'
 python3-dbus         Python DBus - Python bindings for DBus                       REQUIRED        0.80.0          1.3.2           OK         -
 python3-xml          Python XML libraries                                         REQUIRED        -               2.6.1           OK         -
 python3-devel        Python devel - Python development files                      REQUIRED        2.2             3.12.3          OK         -
 python3-pil          PIL - Python Imaging Library (required for commandline scanning with hp-scan) OPTIONAL        -               10.2.0          OK         -
 python3-reportlab    Reportlab - PDF library for Python                           OPTIONAL        2.0             4.1.0           OK         -

--------------
| COMPILEDEP |
--------------

 libtool              libtool - Library building support services                  REQUIRED        -               2.4.7           OK         -
 gcc                  gcc - GNU Project C and C++ Compiler                         REQUIRED        -               13.2.0          OK         -
 make                 make - GNU make utility to maintain groups of programs       REQUIRED        3.0             4.3             OK         -

---------------------
| Python Extentions |
---------------------

 cupsext              CUPS-Extension                                               REQUIRED        -               3.23.12         OK         -
 hpmudext             IO-Extension                                                 REQUIRED        -               3.23.12         OK         -

----------------------
| Scan Configuration |
----------------------

'/etc/sane.d/dll.d/hpaio' not found.
 hpaio                HPLIP-SANE-Backend                                           REQUIRED        -               3.23.12         OK         'hpaio found in /etc/sane.d/dll.conf'
 scanext              Scan-SANE-Extension                                          REQUIRED        -               3.23.12         OK         -

------------------------------
| DISCOVERED SCANNER DEVICES |
------------------------------

No Scanner found.

--------------------------
| DISCOVERED USB DEVICES |
--------------------------

No devices found.

---------------------------------
| INSTALLED CUPS PRINTER QUEUES |
---------------------------------

 
lpstat
------
Type: Unknown
Device URI: No destinations added.


--------------
| PERMISSION |
--------------

Missing Required Dependencies
-----------------------------
error: 'libcups2' package is missing or 'cups' service is not running.
error: 'libcups2-dev' package is missing or 'cups' service is not running.
error: 'cups-bsd' package is missing or 'cups' service is not running.
error: 'cups-client' package is missing or 'cups' service is not running.
error: 'libcupsimage2-dev' package is missing or 'cups' service is not running.
error: 'libavahi-client-dev' package is missing/incompatible 
error: 'libavahi-core-dev' package is missing/incompatible 
error: 'libavahi-common-dev' package is missing/incompatible 
Missing Optional Dependencies
-----------------------------
error: 'gtk2-engines-pixbuf' package is missing/incompatible 
error: 'xsane' package is missing/incompatible 


ENTER SUDO PASSWORD
-------------------
Please enter the sudoer (librarian)'s password: 
 

Checking Permissions....


Checking for Configured Queues....
No Queue added

warning: No Queue(s) configured.


Checking for HP Properitery Plugin's....
No plug-in printers are configured.
 
Diagnose completed...



More information on Troubleshooting,How-To's and Support is available on http://hplipopensource.com/hplip-web/index.html
librarian@Ubuntu5:~$ 
```

---

### Post by 1fallen on 2024-11-30
I'm at loss now my friend, can we pick this up Thursday when you can look in Live Installer first.

One thing for certain 24.04 has been one of the worst out of the box systems I've yet seen with any Buntu installs

I've actually told friends and family to avoid it

---

### Post by cmcanulty on 2024-11-30
I agree . I waited until it was at 24.04.1 and still a mess. 3 computers ended the install with numerous unlisted errors and wouldn't even boot.

---

### Post by oldfred on 2024-12-01
Did you ever run the commands I posted in post #5?
I used to use hp-print when I had a HP printer, but now have Brother.
I still see users adding Brother drivers.

But I am not sure since ipp print if any printer needs proprietary drivers, anymore.
And then are old drivers still maintained or they may not work or work well with newer versions of Ubuntu.

---

### Post by cmcanulty on 2024-12-01
yes I did I have been working this all day for days and no luck. After 15 years of running library on linux I am going to fail over a stupid printer hassle. 24.04 is a nightmare

---

### Post by 1fallen on 2024-12-01
@cmcanulty I have one more set of commands i would like to see:
```
 apt policy cups-bsd cups
cups-bsd:
  Installed: 2.4.10-1ubuntu2
  Candidate: 2.4.10-1ubuntu2
  Version table:
 *** 2.4.10-1ubuntu2 500
        500 http://us.archive.ubuntu.com/ubuntu plucky/main amd64 Packages
        100 /var/lib/dpkg/status
cups:
  Installed: 2.4.10-1ubuntu2
  Candidate: 2.4.10-1ubuntu2
  Version table:
 *** 2.4.10-1ubuntu2 500
        500 http://us.archive.ubuntu.com/ubuntu plucky/main amd64 Packages
        100 /var/lib/dpkg/status

```
and I would like to see apparmor
```
sudo aa-status|grep cups
```
Mine looks like
```
 /usr/lib/cups/backend/cups-pdf
   /usr/sbin/cups-browsed
   /usr/sbin/cupsd
   /usr/sbin/cupsd//third_party
   /usr/sbin/cups-browsed (14703) 
   /usr/sbin/cupsd (14701) 
```
I don't suffer from adding Printers via USB or Wifi

---

### Post by cmcanulty on 2024-12-01
looks pretty similar next I am going to try adding each laptop and printer via usb then see if it will pick up over network but can't do that until thursday
```

librarian@Ubuntu5:~$  apt policy cups-bsd cups
cups-bsd:
  Installed: 2.4.7-1.2ubuntu7.3
  Candidate: 2.4.7-1.2ubuntu7.3
  Version table:
 *** 2.4.7-1.2ubuntu7.3 500
        500 http://archive.ubuntu.com/ubuntu noble-updates/main amd64 Packages
        500 http://security.ubuntu.com/ubuntu noble-security/main amd64 Packages
        100 /var/lib/dpkg/status
     2.4.7-1.2ubuntu7 500
        500 http://archive.ubuntu.com/ubuntu noble/main amd64 Packages
cups:
  Installed: 2.4.7-1.2ubuntu7.3
  Candidate: 2.4.7-1.2ubuntu7.3
  Version table:
 *** 2.4.7-1.2ubuntu7.3 500
        500 http://archive.ubuntu.com/ubuntu noble-updates/main amd64 Packages
        500 http://security.ubuntu.com/ubuntu noble-security/main amd64 Packages
        100 /var/lib/dpkg/status
     2.4.7-1.2ubuntu7 500
        500 http://archive.ubuntu.com/ubuntu noble/main amd64 Packages
librarian@Ubuntu5:~$ sudo aa-status|grep cups
[sudo] password for librarian: 
   /usr/lib/cups/backend/cups-pdf
   /usr/sbin/cups-browsed
   /usr/sbin/cupsd
   /usr/sbin/cupsd//third_party
   /usr/sbin/cupsd (1363) 
librarian@Ubuntu5:~$ 

```

---

### Post by 1fallen on 2024-12-01
> **cmcanulty said:**
>  next I am going to try adding each laptop and printer via usb then see if it will pick up over network but can't do that until thursday

Okay until then. [s]Please be aware the forums go into read only on Dec 9th.[/s]
Please see the correction in Post#30

---

### Post by coffeecat on 2024-12-01
> **1fallen said:**
> Okay until then. Please be aware the forums go into read only on Dec 9th.

Not quite. No new threads but replies will still be possible after Dec 9th. Forum goes read-only on Jan 9th.

---

### Post by 1fallen on 2024-12-01
> **coffeecat said:**
> Not quite. No new threads but replies will still be possible after Dec 9th. Forum goes read-only on Jan 9th.

You beat me  to it I just re-read the Notice... Thanks coffeecat

---

### Post by cmcanulty on 2024-12-01
weird looks like the discourse page doesn't have all the separate forums and is going to have all the topics together will be a big mess once there are hundreds or thousands of threads going

---

### Post by 1fallen on 2024-12-01
> **cmcanulty said:**
> weird looks like the discourse page doesn't have all the separate forums and is going to have all the topics together will be a big mess once there are hundreds or thousands of threads going

There is a View My Posts, it will take a beat to wrap your head around the changes.

---

### Post by Irihapeti on 2024-12-01
There is also the tags box (see attachment). Select the tag you want, and everything else is concealed.

---

