---
title: "How Do I List USB Devices?"
date: 2005-12-23
forum: Hardware &amp; Laptops
---

### Post by kimvall on 2005-12-23
Hello all. I am trying to sync my new k750i with Evolution. I've installed MultiSync but in the setting I need to refer to the USB port (/dev/"USB DEVICE").

I've searched the /dev/ folder but found no items with a name even remotely resempling "usb".

lsusb output (it indicated that Linux has found the cell phone):

Bus 002 Device 008: ID 0fce:d016 Sony Ericsson Mobile Communications AB
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 004: ID 046d:c012 Logitech, Inc. Optical Mouse
Bus 001 Device 001: ID 0000:0000

In spite of my problems, I have managed to copy a couple of mp3s to it and play them so it is connected, and the communication seems to be working just fine.

I simply need to find the "path" to the USB port it is connected to.

Thanks in advance.

---

### Post by Quirky on 2005-12-23
Do they appear in /media/? Or how about typing "mount" to see what usb devices are mounted and where?

---

### Post by Susana on 2005-12-23
try fdisk -l

---

### Post by kimvall on 2005-12-23
[QUOTE=Quirky]Do they appear in /media/? Or how about typing "mount" to see what usb devices are mounted and where?[/QUOTE]

They don't appear in /media/

Mount output:

proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
tmpfs on /dev/shm type tmpfs (rw)
usbfs on /proc/bus/usb type usbfs (rw)
tmpfs on /lib/modules/2.6.12-10-k7/volatile type tmpfs (rw,mode=0755)
/dev/hdb1 on /home type ext3 (rw)
tmpfs on /dev type tmpfs (rw,size=10M,mode=0755)
/dev/sda1 on /media/sda1 type vfat (rw,nosuid,nodev,quiet,shortname=winnt,uid=10 00,gid=1000,umask=077,iocharset=utf8)

---

### Post by kimvall on 2005-12-23
[QUOTE=Susana]try fdisk -l[/QUOTE]

Hmm, what did that do? I tried it and then it umounted the Sony Ericsson device.

---

### Post by Lambert on 2005-12-23
Not sure if this will list what you need but try this.

sudo lshw -businfo

---

### Post by randy on 2005-12-24
There are several different ways that you could find a listing of your usb devices.  The first and probably most complicated is browsing through the /sys/devices directory and looking for your device.  You probably don't want to do that, it'll take a little while to get used to.

Another way that you can list your usb devices is by installing the utility lsusb and running it from a terminal with no arguments.

---

### Post by xmastree on 2005-12-24
[QUOTE=randy]Another way that you can list your usb devices is by installing the utility lsusb and running it from a terminal with no arguments.[/QUOTE]Erm, randy, I hate to say this but... If you read the first post you'll se he already tried that. :rolleyes:

---

### Post by jliedeka on 2005-12-24
What do mean by finding the "path" to your device?  The last line in your mount output shows /dev/sda1 mounted on /media/sda1.  What else are you trying to find out?

---

### Post by kimvall on 2005-12-24
[QUOTE=jliedeka]What do mean by finding the "path" to your device?  The last line in your mount output shows /dev/sda1 mounted on /media/sda1.  What else are you trying to find out?[/QUOTE]

Hmm, this is where my English litterary comes to a screeching halt. ;-) But I'll try ot explain:

In the settings for the IrMC Mobile Device plugin, i need to enter the device it is connected to (i.e. the USB port). If it had been connected to the computer via one of the serials ports I would have to have entered "/dev/ttyS0" or "/dev/ttyS1". That's what I mean by the path. I need to find out the USB ports such "path".

Do you know what I'm talking about?

Could /media/sda1 be it? I entered that value but alas. Also tried /dev/sda1.

Perhaps it's the wrong word, I am fairly new and self helped to the world of Unix/Ubuntu... :-)

In any case, thanks for the help everyone!

---

### Post by afhp on 2005-12-24
If I remember correctly, you need to load the usbserial module to get the ttyUSBx devices. Look for HOWTOs pertaining to the USB Handspring Visor, that should help.

---

### Post by kashms on 2006-01-04
The k750 connects via usb through either /dev/ttyACM0 or /dev/ttyACM1. You can see this with dmesg or in /var/log/messages when you connect the phone.

If you are able to sync with evolution post it here.

---

