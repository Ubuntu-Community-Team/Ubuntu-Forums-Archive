---
title: "1131:1004 Integrated System Solution Corp. Bluetooth Device not detected by 9.10"
date: 2009-12-27
forum: Hardware
---

### Post by s0l1dsnak3123 on 2009-12-27
Hi there, I am trying to get my "1131:1004 Integrated System Solution Corp. Bluetooth Device" working under 9.10 - it has worked in every other release before since hardy (i think it was hardy).

lsusb:
```
snak3@Panther:~$ lsusb
Bus 002 Device 009: ID 1131:1004 Integrated System Solution Corp. Bluetooth Device
Bus 002 Device 004: ID 413c:3200 Dell Computer Corp. Mouse
Bus 002 Device 003: ID 413c:2105 Dell Computer Corp. Model L100 Keyboard
Bus 002 Device 002: ID 093a:2468 Pixart Imaging, Inc. Cammaestro 2.5DU/X-EYE/Orite SC-120/ICGear TravelCam/Easy Snap Snake Eye Webcam
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 019: ID 05ac:1209 Apple, Inc. iPod Video
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

hciconfig:
```
snak3@Panther:~$ hciconfig
snak3@Panther:~$ 

```

hcitoolscan:
```
snak3@Panther:~$ hcitool scan
Device is not available: No such device
snak3@Panther:~$ 

```

sudo /etc/init.d/bluetooth:
```
snak3@Panther:~$ sudo /etc/init.d/bluetooth start
snak3@Panther:~$ sudo /etc/init.d/bluetooth status
 * bluetooth is running
snak3@Panther:~$
```

sudo hidd --search:
```
snak3@Panther:~$ sudo hidd --search
sudo: hidd: command not found
snak3@Panther:~$ 

```

---

### Post by anothermikemiller on 2009-12-28
I have the same problem.
 
$ lsusb
...
Bus 002 Device 002: ID 1131:1001 Integrated System Solution Corp. KY-BT100 Bluetooth Adapter

$ hciconfig
hci0:	Type: USB
	BD Address: 00:00:00:00:00:00 ACL MTU: 0:0 SCO MTU: 0:0
	DOWN 
	RX bytes:0 acl:0 sco:0 events:0 errors:0
	TX bytes:0 acl:0 sco:0 commands:0 errors:0

Take a look at the reviews here:

[http://www.newegg.com/Product/ProductReview.aspx?Item=N82E16833361001](http://www.newegg.com/Product/ProductReview.aspx?Item=N82E16833361001)

All mention that the adapter doesn't work with the Windows stack and had to buy a 3rd party software driver to make it work. I remember it working under the old (immature) BlueZ about a year ago. The company website doesn't list the product any longer either.

---

### Post by s0l1dsnak3123 on 2009-12-28
Good news, I fixed this problem by simply rebooting.

Some info about my setup to help others:
```

sudo apt-get install bluetooth bluez bluez-alsa bluez-cups bluez-gstreamer gnome-bluetooth libbluetooth3 libgnome-bluetooth7 obex-data-server pulseaudio-module-bluetooth totem-plugins

```

reboot and you should be fine too! You should get the bluetooth icon in your system tray menu, then you need to right click on that and choose "turn bluetooth on". Then it should work

Good luck, guys :popcorn:

---

