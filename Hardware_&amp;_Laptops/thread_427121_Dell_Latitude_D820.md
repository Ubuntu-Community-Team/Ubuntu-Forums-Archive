---
title: "Dell Latitude D820"
date: 2007-04-29
forum: Hardware &amp; Laptops
---

### Post by MarilenCorciovei on 2007-04-29
I recently bought a new Dell Latitude D820 with no Windows of course and installed Ubunty Feisty Fawn on it. Here are my results maybe there will be of help to someone if considering to buy this laptop.

Updated article can be found here: [http://www.len.ro/work/tools/ubuntu-feisty-fawn-on-a-dell-latitude-d820/install-ubuntu-feisty-fawn-on-a-dell-latitude-d820/view]("http://www.len.ro/work/tools/ubuntu-feisty-fawn-on-a-dell-latitude-d820/install-ubuntu-feisty-fawn-on-a-dell-latitude-d820/view")

The system


DELL Latitude D820 with Intel Core 2 Duo at 2GHz, 2GB RAM, 100 GB HDD, 1680x1050 screen, nVidia GeForce Go 7400.

00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS/940GML and 945GT Express Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile 945GM/PM/GMS/940GML and 945GT Express PCI Express Root Port (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 01)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 01)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) Serial ATA Storage Controller IDE (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
01:00.0 VGA compatible controller: nVidia Corporation GeForce Go 7400 (rev a1)
03:01.0 CardBus bridge: O2 Micro, Inc. Cardbus bridge (rev 21)
03:01.4 FireWire (IEEE 1394): O2 Micro, Inc. Firewire (IEEE 1394) (rev 02)
09:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5752 Gigabit Ethernet PCI Express (rev 02)
0c:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)


Some history


I started with a Dell I8000 almost 7 years ago on which I first ran Mandrake then Debian and for the last 4 years Gentoo. 3 years ago I got a Dell I8600 on which I ran Gentoo until 6 months ago when I switched to Ubuntu Edgy.

Installation


I used the alternate i386 cd to install everything. It took 10 minutes and all worked smoothly. After installation it suggested me to use the proprietary Nvidia drivers which installed quickly. Not very nice to reboot your machine for that but simpler than to do everything by hand.

Sources


This time I did not even modified the /etc/apt/sources.list but instead I used the software sources application to add the universe, multiverse sources and remove the cdrom one.

Root password


Not a very big fan for sudo, just added a root password:

sudo passwd
... (first the "admin user" password is asked)
... then the root password is set
... and again
$ su -
#


Fancy desktop effects


Since this was one of the advertised new features in Feisty I tried the new fancy desktop effects as soon as possible. They worked ok but they did not seem much useful or anything so I disabled them shortly after playing 10 minutes with them. It seemed to me more useful to replicate the sloppy focus and double click to rollover effects with which I am so used from the WindowMaker years. I did not switched back to WindowMaker because in the months of using Edgy I have grown a bit on using a more advanced gui.

Sound


This was my greatest fear with this new laptop as it has a completely shity sound card (intel hda). Unfortunately this seem to be present in all laptops I have seen including the intel based mac.
I first tried to play a sound which worked ok but the sound quality is bad. As so many on the net say, I was happy at least it worked. Trying to record was another story. The default recorder behaved strangely at best and audacity which I installed complained about not finding any recording device at all. I lost about 1h trying to make it work by mixing information from the following threads which described similar problems:

    * [http://ubuntuforums.org/showthread.php?t=347081&highlight=hda+intel+recording](http://ubuntuforums.org/showthread.php?t=347081&highlight=hda+intel+recording)
    * [http://ubuntuforums.org/showthread.php?t=201887&highlight=dell+inspiron+SigmaTel+STAC9200](http://ubuntuforums.org/showthread.php?t=201887&highlight=dell+inspiron+SigmaTel+STAC9200)
    * [http://ubuntuforums.org/showthread.php?p=2210477#post2210477](http://ubuntuforums.org/showthread.php?p=2210477#post2210477)


Wireless


It worked without any effort, all the drivers where installed (using ipw3945) and clicking on the network manager icon showed me the networks to connect to. Talk about simplicity.

USB data storage


I am a bit disappointed as it seems there was a change from Edgy. I have an external hdd with 2 partitions (sda1 and sda2) which are mounted automatically in /media/sda1 and /media/sda2. In Edgy when I used the desktop icon to unmount one of the partitions both of them where unmounted. Now when I do that, there is an error and they are mounted again so I have to unmount them manually at the same time using the command:

umount /media/sda1 /media/sda2 as root


Photo camera


The Cannon PowerShot A95 worked as expected as it worked in Edgy also. It detects it and prompts for a place to save the images.

The service tag


You can use the i8k module to check your service tag, BIOS version, fan speed and so on

modprobe i8k
root@black:/# cat /proc/i8k 
1.0 A06 XXXXXX 44 -22 1 27660 71250 -1 -22

[Len]("http://www.len.ro")

---

### Post by MarilenCorciovei on 2007-04-29
From: [http://www.len.ro/work/tools/ubuntu-feisty-fawn-on-a-dell-latitude-d820/use-the-ir-port-with-ubuntu](http://www.len.ro/work/tools/ubuntu-feisty-fawn-on-a-dell-latitude-d820/use-the-ir-port-with-ubuntu)

Use the IR port with ubuntu feisty fawn

This is more of a fuss as I wanted to connect to my Sony Ericsson T630 phone over infrared, hopefully at some point I will be able to use it's modem for GPRS access.

Activate the ir (COM2 - /dev/ttyS1) in bios

Install the irda-utils and openobex packages

apt-get install irda-utils obexfs obexftp openobex-apps

Load the needed kernel modules

modprobe irda 
modprobe ircomm 
modprobe ircomm-tty 
modproble irtty-sir

edit /etc/modules and add

irda
ircomm
ircomm-tty
irtty-sir

such that the modules will be loaded automatically next time you boot.

Test with obex_test:

obex_test -i
Using IrDA transport
OBEX Interactive test client/server.
> c
Connect OK!
Version: 0x10. Flags: 0x00
> 

Test with obex_ftp

obexftp -iv -l
Connecting...done
Receiving "(null)"... <?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE folder-listing SYSTEM "obex-folder-listing.dtd">
<!--
Generated by XML Coder.
xml_coder.c (Jun 29 2004 21:44:28)
(C) 2001 Sony Ericsson Mobile Communications AB, Lund, Sweden
-->
<folder-listing version="1.0"><folder name="Pictures"/>
<folder name="Sounds"/>
<folder name="Themes"/>
</folder-listing>

done.

[Len]("http://www.len.ro")

---

### Post by MarilenCorciovei on 2007-05-04
Making bluetooth work on my Dell Latitude D820 with my Sony Ericsson T630 phone was rather easy. I just needed to enable bluetooth in bios and then install the following packages:

apt-get install bluetooth gnome-bluetooth

apt-get install bluez-gnome bluez-utils


Afterword I started the bluetooth-applet. A bluetooth icon appeared in the notification area and I was able to add the laptop to my phone as a bluetooth friend and send a file from the phone to the laptop.

Original link here: [http://www.len.ro/work/tools/ubuntu-feisty-fawn-on-a-dell-latitude-d820/use-the-bluetooth-port-with-ubuntu/]("http://www.len.ro/work/tools/ubuntu-feisty-fawn-on-a-dell-latitude-d820/use-the-bluetooth-port-with-ubuntu/")

---

### Post by MarilenCorciovei on 2007-05-04
Disabling avahi-daemon
One of the things I quickly found to be bothering me is the fact that there was an apparently long and unexplicable delay for all new network connections which resembled to a dns resolving. No reason for lengthy dns resolving though. So I did a strace:

socket(PF_FILE, SOCK_STREAM, 0)         = 4
fcntl64(4, F_GETFD)                     = 0
fcntl64(4, F_SETFD, FD_CLOEXEC)         = 0
connect(4, {sa_family=AF_FILE, path="/var/run/avahi-daemon/socket"}, 110) = 0
fcntl64(4, F_GETFL)                     = 0x2 (flags O_RDWR)
fstat64(4, {st_mode=S_IFSOCK|0777, st_size=0, ...}) = 0
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb7f35000
_llseek(4, 0, 0xbfa7d918, SEEK_CUR)     = -1 ESPIPE (Illegal seek)
write(4, "RESOLVE-ADDRESS 10.0.0.6\n", 25) = 25
read(4,  <unfinished ...>


the results shows a connection to a avahi-daemon which I have no ideea what is good for so I should not need it. I disabled it in /etc/default/avahi-daemon

cat /etc/default/avahi-daemon 
# 0 = don't start, 1 = start
AVAHI_DAEMON_START=0

Hope it helps. Original article here: [http://www.len.ro/work/tools/ubuntu-feisty-fawn-on-a-dell-latitude-d820/disabling-avahi-daemon/view]("http://www.len.ro/work/tools/ubuntu-feisty-fawn-on-a-dell-latitude-d820/disabling-avahi-daemon/view")

---

### Post by el escocés on 2007-12-07
[CENTER]**[COLOR=Red]ONLY APPLYS TO INTEL GRAPHIC USERS[/COLOR]**
[/CENTER]
 
I've found a very neat app that has proved very handy to me.

I have my dell connected to an external monitor with the lid closed, my pre-gutsy problem was that when I had to go to a meeting I disconnected the monitor and had to reset X to get the screen working.

That was using the i810 driver, now in Gutsy you can use the intel driver, which gives you the possibility to use the xrandr app.

To change to the intel driver run 

```
sudo dpkg-reconfigure xserver-xorg
```When it asks for the driver select 'intel' all the other options should remain the same as you are using the current configuration settings.

Reboot.

In terminal run

```
xrandr -q
```This will display the possible config setting for your display(s).

In my case when I want to switch from my monitor to my laptop I run this command

```
xrandr --output VGA --off --output LVDS --mode 1280x800
```and back to the monitor

```
xrandr --output LVDS --off --output VGA --mode 1280x1024
```We can now make a script that detects what is connected and turn on the necessary display :

```
#! /bin/bash

if xrandr -q | grep -q  "VGA connected"; then
  xrandr --output LVDS --off --output VGA --mode 1280x1024
else
  xrandr --output VGA --off --output LVDS --mode 1280x800
fi
```Be sure to disable sleep mode when the lid is closed System>Preferences>Power Management 'When laptop lid is closed' Do nothing.

Make the script executable

```
sudo chmod +x FILENAME.sh
```Then we can assign a shortcut key to run this script: [http://www.howtogeek.com/howto/ubuntu/assign-custom-shortcut-keys-on-ubuntu-linux/](http://www.howtogeek.com/howto/ubuntu/assign-custom-shortcut-keys-on-ubuntu-linux/)

PS. I also run this script on startup (Preferences>Sessions>Startup Programs)

hth!

---

