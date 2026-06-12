---
title: "Cannot get bluetooth keyboard and mouse to connect at startup"
date: 2006-11-05
forum: Hardware &amp; Laptops
---

### Post by Nightdrive on 2006-11-05
I need some serious help getting my Bluetooth ketboard and mouse connected at bootup. I have read pretty much all forum posts about bluetooth HID, and that includes forums for other flavours of linux.

Currently, bluez-utils is installed, and I can get the KB and mouse connected, if after booting up, I open a terminal (with a non-bluetooth wireless keyboard) and do:
**sudo hidd --search**
As long as the devices haven't gone to sleep, they always connect - though sometimes the keyboard needs some furious pressing of the 'connect' button.
My problem is that I can't get them to work automatically at startup.
I've followed instructions to put the '**hidd --search**' or '**hidd --connect ab:cd:ef:12:34:56**' into **/etc/init.d/bluetooth** (I don't have the bluez folder most walkthroughs insist I should have - I suspect they're out of date)
I've also tried: **/etc/rc.local** though I've no idea what this folder does, I was just following suggestions.
Also tried: **/etc/bootmisc.sh** - as suggested by someone on #ubuntu IRC, and no joy there either.
I even installed '**Boot up manager**' using Automatix2. That give me the option to enable '**bluetooth~**' ??? No difference.
As a linux noob, I've no idea when the various scripts run, what their intended use is, or what user they run under. It's such a simple requirement, but as usual with Linux, it's taken days of my life expectancy to get even this far :(

Any help would be appreciated

---

### Post by stfu on 2006-11-06
Try to add what's said in this thread in /etc/rc.local
[http://www.ubuntuforums.org/showthread.php?t=285386](http://www.ubuntuforums.org/showthread.php?t=285386)

---

### Post by Nightdrive on 2006-11-06
Thanks for the reply, but the post you linked to is one of several I've digested, and I've already added the following to my /etc/rc.local file:

/usr/bin/hidd --server --master
/usr/bin/hidd -i 00:0a:3a:59:55:74 --connect 00:03:c9:57:29:d0
/usr/bin/hidd -i 00:0a:3a:59:55:74 --connect 00:03:c9:66:b2:fc
/usr/bin/hidd --dev

It's a bit more verbose, but from what I can tell, does the same thing (nothing in my case!)

Any other ideas are appreciated.

---

### Post by Nightdrive on 2006-11-12
Where are all the Linux gurus when you need them eh?

---

### Post by Nightdrive on 2006-11-19
Update: 
I read in the Linux kernel change logs that the last couple of versions of the kernel have had updates regarding bluetooth. One of the updates even mentions my Belkin bluetooth keyboard and mouse by name.  So, I rebuilt the kernel - a feat I was quite proud of for a newbie!
However, still no luck. My symptoms are the same. From other stuff I've read about Ubuntu, it could even be that the earlier Ubuntu kernel had borrowed these later changes anyway.
My current version 2.6.18.2

---

### Post by defishguy on 2006-11-21
I have a Logitech MX5000 Bluetooth mouse & keyboard combo, and finally got the thing to connect on startup.  This is what I did:

type "sudo gedit /etc/init.d/bluetooth"

Add the following line immediately after the commented lines at the beginning of the file (without the quotes).

"exit 0"

It should look like this:

[I]#! /bin/bash
### BEGIN INIT INFO
# Provides: bluetooth
# Required-Start:    $local_fs $syslog $remote_fs
# Required-Stop:     $local_fs $syslog $remote_fs
# Default-Start:     2 3 4 5
# Default-Stop:      0 1 6
# Short-Description: Start bluetooth daemons
### END INIT INFO
#
# bluez-utils    Bluetooth subsystem starting and stopping
#
# originally from bluez's scripts/bluetooth.init
#
# Edd Dumbill <ejad@debian.org>
# LSB 3.0 compilance and enhancements  by Filippo Giunchedi <filippo@debian.org>
#
# startup control over dund and pand can be changed by editing
# /etc/default/bluez-utils

exit 0
[/I]

Save the file and do the next step.

Type "sudo gedit /etc/default/bluetooth"

Change  the following 

HIDD_ENABLED=1
HIDD_OPTIONS="--connect 00:01:02:03:04:05 --connect 00:01:02:03:04:05 --master --server"

Replace the 00:01:02:03:04:05 with YOUR keyboard / mouse mac addresses.  You can usually find them on the bottom of each on a sticker.

Thanks to the folks at this thread for the second part
[http://www.ubuntuforums.org/showthread.php?t=285386](http://www.ubuntuforums.org/showthread.php?t=285386)


Save, Reboot, and if it works for you like it works for me you will be enjoying some sweet yet laggy bluetooth goodness on the next boot.

---

### Post by Nightdrive on 2006-11-24
Thanks for the response, but still no joy I'm afraid.
Since it works flawlessly in Windows, I'll be chalking this one down to a bug. If it's not a bug in one of Ubuntu, Linux or Debian, then it's certainly a design bug in the distribution not making this stuff easy to use.

I officially give up. My living room PC will just have to make do with the 1.5m range of my cheap wireless kb and mouse.

---

### Post by GhettoPuNKkiD on 2006-11-29
I'm experiencing the same thing. I've got my bluetooth mouse/kb combo up now.. I've tried everything.. I just installed Dapper (new install) because Edgy wouldn't work with my setup. I'm afraid to reboot my computer right now because I hate having to set everything back up.. and I'd prefer not to use a USB keyboard :-)

I'm using: M$ Optical Desktop Elite for Bluetooth

I've read lots so far, maybe I'll get it soon. Let's hope.

Anybody with ideas please help.

---

### Post by sherlockth on 2006-12-07
I tried defishguy's solution and it worked just fine for my logitech cordless desktop for bluetooth, on edgy.

Many Thanks defishguy

---

