---
title: "Another LaserJet 1000 issue (usb related)."
date: 2006-04-04
forum: Hardware &amp; Laptops
---

### Post by Scratty on 2006-04-04
Hi!
Yesterday I decided to connect mom's HP LaserJet 1000 to my computer with Ubuntu Breezy 5.10 (linux 2.6.12.16.1). Concidering that I've had no bigger troubles installing hardware on Breezy previously, I thought I'd get the printer up and running in no time. But alas, I was proven to be wrong. So after a lot of tinkering and tweaking, viewing virutally every thread regarding LaserJets here on the Ubuntuforums, checking out linux-printing.org etc.. I concluded that something is seriously wrong with my usb-ports or at least the detection of them.
I'll try to list some of the steps I've taken in as much a chronological order as is possible:

The first thing I notice that might be an issue is at bootup. Among other things, Ubuntu lists this action:
```
Starting hotplug system	
```
However unlike the other actions listed at bootup, no [ok] signature is shown at the end this action string.

The first few times I tried to get the printer working, I utilized the printer configuration tool. I select local printer, and since the "Use detected printer" box is empty and deselected by default, I chose a port from the list. The list has the preselected value: **hp no_device_found**. I then select **USB Printer #2** since USB port 1 was accidentally (physically) broken quite a while ago. In the next step I select HP and select LaserJet 1000. The setup-tool shows that foo2zjs is recommended (no surprise here). I finally select "Apply" to finish the setup.

Then I try to print the testpage, and nothing happens. The status line tells me:
```

Printing: Printer not connected; will retry in 30 seconds...

```
Now, changing the port to USB #1 doesn't work either. Interresting to note is that no property changes will be updated when closing the property-GUI (as I see some other people have noticed). The only way to work around this is to remove the printer and add the printer anew.

I check with synaptic and notice that foo2zjs is not installed. I install it. Then make another go, and nothing...

I look around for hints on how to fix this and discover quite a lot of info (much of which is repeated) here on the forums. Got the tip to look at [www.linux-printing.org](www.linux-printing.org). List my ppd setting file and see some info about it. I download the source, compile according to instructions without any problems and see that the firmware folder now contains my printer (as was not the case when installing foo2zjs from synaptic).
```

:/etc/hotplug/usb$ ls
foo2zjs.usermap  hplj1020            libsane.usermap  logitechmouse.usermap
hplj1000         libgphoto2          libusbscanner
hplj1005         libgphoto2.usermap  logitechmouse

```
I also have the sihp1000.dl file which wasn't there before when using the driver from synaptic:
```

:/usr/share/foo2zjs/firmware$ ls
sihp1000.dl  sihp1005.dl  sihp1020.dl

```

I see a lot of people giving hints on issuing the following command. But instead I get:
```

:~$ sudo cat /usr/share/foo2zjs/firmware/sihp1000.dl > /dev/usb/lp0
bash: /dev/usb/lp0: No such file or directory

```
(Ok, I've seen an alternate solution using sihp1000.img , but if the above doesn't work then that won't work too of course).

Ok, this is weird. Isn't linux aware of my usb-ports? After some struggeling, I find out the following info:
```

:~$ ls /dev/usb
ls: /dev/usb: No such file or directory

:~$ lsusb
Bus 001 Device 001: ID 0000:0000

:~$ usbmodules --device /proc/bus/usb/001/001
usbcore

:/etc/udev/rules.d$ more udev.rules | grep usb
BUS=="usb", KERNEL=="hiddev*",          NAME="usb/%k"
BUS=="usb", KERNEL=="auer[0-9]*",       NAME="usb/%k"
BUS=="usb", KERNEL=="legousbtower*",    NAME="usb/%k"
BUS=="usb", KERNEL=="dabusb*",          NAME="usb/%k"
BUS=="usb", KERNEL=="cpad[0-9]*",       NAME="usb/%k"
BUS=="usb", KERNEL=="lp[0-9]*",         NAME="usb/%k"
BUS=="usb", KERNEL=="ttyUSB*", SYSFS{product}=="Palm Handheld*", \

```
I noticed that /proc/bus/usb/001/001 is the only available usb definition(?) I have. There should be two of them AFAIK.

Using the device manager to check my usb-devices I get the following info:
[color=red]See attachments.[/color]

I set the CUPS LogLevel to debug and retrieve the following information:
```

:/var/log/cups$ more error_log
I [04/Apr/2006:14:23:14 +0200] Listening to 7f000001:631
D [04/Apr/2006:14:23:14 +0200] AddLocation: added location '/'
D [04/Apr/2006:14:23:14 +0200] DenyIP: / deny 00000000/00000000
D [04/Apr/2006:14:23:14 +0200] AllowIP: / allow 7f000001/ffffffff
D [04/Apr/2006:14:23:14 +0200] AddLocation: added location '/jobs'
D [04/Apr/2006:14:23:14 +0200] AddLocation: added location '/admin'
D [04/Apr/2006:14:23:14 +0200] DenyIP: /admin deny 00000000/00000000
D [04/Apr/2006:14:23:14 +0200] AllowIP: /admin allow 7f000001/ffffffff
I [04/Apr/2006:14:23:14 +0200] Loaded configuration file "/etc/cups/cupsd.conf"
I [04/Apr/2006:14:23:14 +0200] Configured for up to 100 clients.
I [04/Apr/2006:14:23:14 +0200] Allowing up to 100 client connections per host.
I [04/Apr/2006:14:23:14 +0200] Full reload is required.
E [04/Apr/2006:14:23:14 +0200] LoadAllClasses: Unable to open /etc/cups/classes.
conf - No such file or directory
D [04/Apr/2006:14:23:14 +0200] LoadDevices: Added device "ipp"...
D [04/Apr/2006:14:23:14 +0200] LoadDevices: Added device "http"...
D [04/Apr/2006:14:23:15 +0200] LoadDevices: Added device "bluetooth"...
D [04/Apr/2006:14:23:15 +0200] LoadDevices: Added device "epson:/dev/lp0"...
D [04/Apr/2006:14:23:16 +0200] LoadDevices: Added device "canon:/dev/lp0"...
D [04/Apr/2006:14:23:16 +0200] LoadDevices: Added device "hp:/no_device_found"..
.
D [04/Apr/2006:14:23:17 +0200] LoadDevices: Added device "smb"...
D [04/Apr/2006:14:23:17 +0200] LoadDevices: Added device "lpd"...
D [04/Apr/2006:14:23:17 +0200] LoadDevices: Added device "parallel:/dev/lp0"...
D [04/Apr/2006:14:23:17 +0200] LoadDevices: Added device "socket"...
D [04/Apr/2006:14:23:18 +0200] LoadDevices: Added device "usb:/dev/usb/lp0"...
D [04/Apr/2006:14:23:18 +0200] LoadDevices: Added device "usb:/dev/usb/lp1"...
D [04/Apr/2006:14:23:18 +0200] LoadDevices: Added device "usb:/dev/usb/lp2"...
D [04/Apr/2006:14:23:18 +0200] LoadDevices: Added device "usb:/dev/usb/lp3"...
D [04/Apr/2006:14:23:18 +0200] LoadDevices: Added device "usb:/dev/usb/lp4"...
D [04/Apr/2006:14:23:18 +0200] LoadDevices: Added device "usb:/dev/usb/lp5"...
D [04/Apr/2006:14:23:18 +0200] LoadDevices: Added device "usb:/dev/usb/lp6"...
D [04/Apr/2006:14:23:18 +0200] LoadDevices: Added device "usb:/dev/usb/lp7"...
D [04/Apr/2006:14:23:18 +0200] LoadDevices: Added device "usb:/dev/usb/lp8"...
D [04/Apr/2006:14:23:18 +0200] LoadDevices: Added device "usb:/dev/usb/lp9"...
D [04/Apr/2006:14:23:18 +0200] LoadDevices: Added device "usb:/dev/usb/lp10"...
D [04/Apr/2006:14:23:18 +0200] LoadDevices: Added device "usb:/dev/usb/lp11"...
D [04/Apr/2006:14:23:18 +0200] LoadDevices: Added device "usb:/dev/usb/lp12"...
D [04/Apr/2006:14:23:18 +0200] LoadDevices: Added device "usb:/dev/usb/lp13"...
D [04/Apr/2006:14:23:18 +0200] LoadDevices: Added device "usb:/dev/usb/lp14"...
D [04/Apr/2006:14:23:18 +0200] LoadDevices: Added device "usb:/dev/usb/lp15"...
I [04/Apr/2006:14:23:18 +0200] LoadPPDs: Read "/etc/cups/ppds.dat", 4118 PPDs...
I [04/Apr/2006:14:23:21 +0200] LoadPPDs: No new or changed PPDs...
D [04/Apr/2006:14:23:21 +0200] LoadAllJobs: Scanning /var/spool/cups...
I [04/Apr/2006:14:23:21 +0200] Full reload complete.
D [04/Apr/2006:14:23:21 +0200] StartListening: NumListeners=1
D [04/Apr/2006:14:23:21 +0200] StartListening: address=7f000001 port=631
D [04/Apr/2006:14:23:21 +0200] ResumeListening: setting input bits...
D [04/Apr/2006:14:24:40 +0200] AcceptClient: 4 from localhost:631.
D [04/Apr/2006:14:24:40 +0200] ReadClient: 4 POST / HTTP/1.1
D [04/Apr/2006:14:24:40 +0200] ProcessIPPRequest: 4 status_code=0
D [04/Apr/2006:14:24:40 +0200] AcceptClient: 5 from localhost:631.
D [04/Apr/2006:14:24:40 +0200] ReadClient: 4 POST / HTTP/1.1
D [04/Apr/2006:14:24:40 +0200] ProcessIPPRequest: 4 status_code=0
D [04/Apr/2006:14:24:40 +0200] CloseClient: 5
D [04/Apr/2006:14:24:45 +0200] ReadClient: 4 POST / HTTP/1.1
D [04/Apr/2006:14:24:45 +0200] ProcessIPPRequest: 4 status_code=0
D [04/Apr/2006:14:24:50 +0200] ReadClient: 4 POST / HTTP/1.1
...

```
**Note:** The log was made after I had removed the printer from the print manager (which might be pretty foolish, I admit).



So, it seems that the usb ports are there, only the linux kernel can't use the ports properly since /dev/usb/lp* are non-existent and can thus not detect the printer.

I tried to fix this by looking at the linux-usb site and it told me to use mknode on /dev/usb/lp0 with some peculiar values I don't understand. So I issued a mkdir /dev/usb and then issued the mknode command, but to no avail (probably needed to set up /dev/usb/lp1 or /dev/usb/lp2, not sure which one of them and not sure which values to use too).

I'd don't have a 100% knowledge of all things I've tried out, so I might have messed something up on the way.

If anyone has any clues on how to resolve this usb issue, I would rejoyce myself to death!

Thanx!

---

