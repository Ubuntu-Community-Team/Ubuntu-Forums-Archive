---
title: "Bluetooth setup problem"
date: 2012-08-12
forum: Hardware
---

### Post by onebir on 2012-08-12
In Xubuntu 11.10, I failed to get bluetooth working using the applet & various wheezes I've since forgotten. So I decided to try again via the CLI to make documenting what I'd done a bit easier:

1) Built-in bluetooth
```
onebir@dell640m:~/Desktop$ lsusb | grep -i bluetooth
Bus 003 Device 002: ID 413c:8103 Dell Computer Corp. Wireless 350 Bluetooth
onebir@dell640m:~/Desktop$ hcitool dev
Devices:
	hci1	00:16:41:57:F5:55
onebir@dell640m:~/Desktop$ sudo hcitool scan
[sudo] password for onebir: 
Scanning ...
onebir@dell640m:~/Desktop$
```

Checked for information on "Dell Computer Corp. Wireless 350 Bluetooth". Discovered [there can be problems with the driver](http://www.question-defense.com/2011/02/20/get-dell-wireless-350-bluetooth-module-working-with-backtrack-dell-bluetooth-350-with-ubuntu)
This laptop has a (little-used) win$ dual-boot - installed & updated since that post. Looks like that particular issue's fixed.

Decided to go through [BluetoothSetup](https://help.ubuntu.com/community/BluetoothSetup#Ubuntu_11.04_Install_via_the_command_line) in Ubuntu documentation (using 11.04 instructions, couldn't find updates for 11.10):

```
onebir@dell640m:~$ sudo apt-get install bluez python-gobject python-dbus
[sudo] password for onebir: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
python-dbus is already the newest version.
bluez is already the newest version.
python-gobject is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
# But what are the newest versions...
onebir@dell640m:~$ apt-cache show bluez python-gobject python-dbus  |egrep "Package|Version"
Package: bluez
Version: 4.96-0ubuntu3
Package: python-dbus
Version: 0.84.0-2
Package: python-gobject
Version: 3.0.0-0ubuntu2
Package: bluez
Version: 4.96-0ubuntu4
Package: python-gobject
Version: 3.0.0-0ubuntu4
# Why two versions of bluez & python-gobject? :s
onebir@dell640m:~$ hcitool dev
Devices:
	hci1	00:16:41:57:F5:55
onebir@dell640m:~$ sudo bluez-simple-agent hci1 00:16:41:57:F5:55
Creating device failed: org.bluez.Error.ConnectionAttemptFailed: Page Timeout

```

Googling suggests it's a problem with bluez...

2) USB dongle.
But I also have a [$2 USB Bluetooth adapter](http://www.tinydeal.com/super-mini-usb-bluetooth-dongle-adapter-for-laptop-p-2194.html?zenid=antl4q3pgf250dgf8h0kpr3083) (also available for [a mere $34 here](https://www.thinkpenguin.com/gnu-linux/penguin-usb-bluetooth-micro-adapter) - what a deal, thinkpenguin!). Plug it in:

```
onebir@dell640m:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 413c:8103 Dell Computer Corp. Wireless 350 Bluetooth
Bus 004 Device 002: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode) # Same manufacturer as thinkpenguins'...
onebir@dell640m:~$ hcitool dev
Devices:
	hci0	00:16:41:57:F5:55 # built-in one
	hci1	00:1F:81:00:08:30 # USB one
onebir@dell640m:~$ sudo bluez-simple-agent hci1 00:1F:81:00:08:30
[sudo] password for onebir: 
Creating device failed: org.bluez.Error.ConnectionAttemptFailed: Page Timeout
```

Googling the error led me to an explanation of [how-ubuntus-broken-bluetooth-support-came-to-be](http://blog.projectnibble.org/2010/08/08/how-ubuntus-broken-bluetooth-support-came-to-be/) - but no solutions.

Has anyone had any luck (in 11.10 or 12.04, since I guess my upgrade is overdue)? Thanks....

---

### Post by onebir on 2012-08-13
So Bluez has been broken (or undocumented to the point no one knows how to use it) since August 2010? & that's just the way things go?

---

### Post by ahallubuntu on 2012-08-13
I've been using bluetooth in Ubuntu 10.04 LTS, 10.10, and 11.04 for months, even years routinely - with internal bluetooth as well as USB bluetooth dongles.  I tether my cell phone to get my laptop on the internet with it.  I connect bluetooth mice and headsets.  I've never had to do anything to make it work - it has been pretty automatic.  Never had to install any packages.  It's much simpler to use than Windows for sure.

I've also at least tested it with later versions of Ubuntu - even if I haven't used it extensively.  But it seems like the same kind of built-in support.

I can't speak for Xubuntu - maybe that's part of the problem you're having?  Have you booted a regular Ubuntu live CD to see if it can pick up your bluetooth hardware, at least?

---

### Post by onebir on 2012-08-13
Well, that's good to know, thanks :)

There's actually no problem with hardware recognition AFAICT:

```
onebir@dell640m:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 413c:8103 Dell Computer Corp. Wireless 350 Bluetooth
Bus 004 Device 002: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode) # Same manufacturer as thinkpenguins'...
onebir@dell640m:~$ hcitool dev
Devices:
	hci0	00:16:41:57:F5:55 # built-in one
	hci1	00:1F:81:00:08:30 # USB one
```
The problems arise when I try to do anything with it with bluez:
```
onebir@dell640m:~$ sudo bluez-simple-agent hci1 00:16:41:57:F5:55
Creating device failed: org.bluez.Error.ConnectionAttemptFailed: Page Timeout
```
I think I had a similar problem when I tried with the Blueman GUI (it was a couple of weeks ago).

---

### Post by onebir on 2012-08-14
bluez-simple-agent also looks broken in Xubuntu 12.04; I tried it on a T91 netbook with an internal adapter (not how to find out the make; lsusb, lspci & lshw don't give me anything bluetooth-related) & the same $2 dongle used earlier.

```
onebir@T91:~$ lsb_release -rd
Description:	Ubuntu 12.04.1 LTS
Release:	12.04
onebir@T91:~$ apt-cache show bluez python-gobject python-dbus | egrep "Package|Version"
Package: bluez
Version: 4.98-2ubuntu7
Package: python-gobject
Version: 3.2.2-1~precise
Package: python-gobject
Version: 3.2.0-3
Package: python-dbus
Version: 1.0.0-1ubuntu1

#Trying inbulit card - not sure of hardware
onebir@T91:~$ hcitool dev
Devices:
        hci0 00:25:D3:A4:4A:A7
onebir@T91:~$ hcitool scan
Scanning ...
onebir@T91:~$ sudo bluez-simple-agent hci 00:25:D3:A4:4A:A7
[sudo] password for bir:
Traceback (most recent call last):
  File "/usr/bin/bluez-simple-agent", line 102, in <module>
    path = manager.FindAdapter(args[0])
  File "/usr/lib/python2.7/dist-packages/dbus/proxies.py", line 70, in __call__
    return self._proxy_method(*args, **keywords)
  File "/usr/lib/python2.7/dist-packages/dbus/proxies.py", line 145, in __call__
    **keywords)
  File "/usr/lib/python2.7/dist-packages/dbus/connection.py", line 651, in call_blocking
    message, timeout)
dbus.exceptions.DBusException: org.bluez.Error.NoSuchAdapter: No such adapter

# Plug in USB Bluetooth dongle as used in *
onebir@T91:~$ hcitool dev
Devices:
        hci0 00:25:D3:A4:4A:A7
        hci1 00:1F:81:00:08:30
onebir@T91:~$ sudo bluez-simple-agent hci 00:1F:81:00:08:30
Traceback (most recent call last):
  File "/usr/bin/bluez-simple-agent", line 102, in <module>
    path = manager.FindAdapter(args[0])
  File "/usr/lib/python2.7/dist-packages/dbus/proxies.py", line 70, in __call__
    return self._proxy_method(*args, **keywords)
  File "/usr/lib/python2.7/dist-packages/dbus/proxies.py", line 145, in __call__
    **keywords)
  File "/usr/lib/python2.7/dist-packages/dbus/connection.py", line 651, in call_blocking
    message, timeout)
dbus.exceptions.DBusException: org.bluez.Error.NoSuchAdapter: No such adapter
```

Is it just me, or is Bluetooth resoundingly broken in the last few releases of (X)ubuntu?

---

### Post by onebir on 2012-08-15
Same problem occurs on Dell Inspiron 640m with Xubuntu 12.04 running from live USB, once again with both inbuilt Bluetooth & USB dongle:
```
xubuntu@xubuntu:~$ apt-cache show bluez python-gobject python-dbus | egrep "Package|Version"
Package: bluez
Version: 4.98-2ubuntu7
Package: python-gobject
Version: 3.2.2-1~precise
Package: python-gobject
Version: 3.2.0-3
Package: python-dbus
Version: 1.0.0-1ubuntu1
xubuntu@xubuntu:~$ hcitool dev
Devices:
	hci0	00:16:41:57:F5:55
	hci1	00:1F:81:00:08:30
xubuntu@xubuntu:~$ lsusb
...snip...
Bus 003 Device 002: ID 413c:8103 Dell Computer Corp. Wireless 350 Bluetooth
Bus 004 Device 002: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)
xubuntu@xubuntu:~$ sudo bluez-simple-agent hci0 00:16:41:57:F5:55
Creating device failed: org.bluez.Error.ConnectionAttemptFailed: Page Timeout
xubuntu@xubuntu:~$ sudo bluez-simple-agent hci1 00:1F:81:00:08:30

Creating device failed: org.bluez.Error.ConnectionAttemptFailed: Page Timeout
```

---

### Post by onebir on 2012-08-23
To summarise, I've now tried to use bluez-simple-agent with the six following combinations hardware & Ubuntu versions: 

- Dell 640m, (builtin) Dell Wireless 350 BT chip, Xubuntu 11.10
- Dell 640m, USB Cambridge Silicon Radio BT chip, Xubuntu 11.10
- Dell 640m, (builtin) Dell Wireless 350 BT chip, Xubuntu 12.04
- Dell 640m, USB Cambridge Silicon Radio BT chip, Xubuntu 12.04
- Asus T91m, builtin BT chip, Xubuntu 12.04
- Asus T91m, USB Cambridge Silicon Radio BT chip, Xubuntu 12.04

**None of these has worked** and this thread has only had one reply. I've also raised a couple of bug reports, these haven't had any replies.

Does anyone have any suggestions about how I might proceed? (I haven't tried vanilla Ubuntu, for example. Is it possible there are some Xubuntu-only Bluetooth bugs?)

---

### Post by Inoki on 2013-06-05
I'm having this issue with my Xubuntu. Currently using 13.04 x64. I can't get Bluetooth to work since........ forever.

---

### Post by tonysonney on 2014-02-18
@onebir
           Probably not of much help. But some information which may be helpfull. I did not have any problem with the blueZ 4.98 which came along with ubuntu 12.04. The BT pairing worked fine. But this was all throught he GUI. To see how the BlueZ works, I uninstalled the default version and built 4.101 which is the latest of 4 series. Guess what I couldnt pair with any BT devices anymore, and I am using bluez-simple-agent!

---

