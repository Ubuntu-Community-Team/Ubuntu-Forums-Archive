---
title: "usb pendrive"
date: 2005-04-09
forum: Hardware &amp; Laptops
---

### Post by oldmarti on 2005-04-09
Hi,
I just install ubutnu (server configuration without gui). I want to transfer some files using usb pen. Hotplug detect pen and I can mount it with mount /dev/sda1 /media/usbstick.
It's possible to mount automaticly? (In full installation with gnome, no problem)
Thanks

---

### Post by nad on 2005-04-09
If you have to manually mount your drive, you do not have the hotplug scripts package installed. What appears to have happened is that your kernel noticed the insertion of the drive and wrote a log message.

Dan M

---

### Post by oldmarti on 2005-04-09
Here is log message from dmesg:
usb 2-2: new full speed USB device using ohci_hcd and address 4
scsi2 : SCSI emulation for USB Mass Storage devices
usb-storage: device found at 4
usb-storage: waiting for device to settle before scanning
  Vendor:           Model: USB DISK          Rev: 2.0B
  Type:   Direct-Access                      ANSI SCSI revision: 00
SCSI device sda: 128000 512-byte hdwr sectors (66 MB)
sda: Write Protect is off
sda: Mode Sense: 43 00 00 00
sda: assuming drive cache: write through
SCSI device sda: 128000 512-byte hdwr sectors (66 MB)
sda: Write Protect is off
sda: Mode Sense: 43 00 00 00
sda: assuming drive cache: write through
 /dev/scsi/host2/bus0/target0/lun0: p1
Attached scsi removable disk sda at scsi2, channel 0, id 0, lun 0
usb-storage: device scan complete
FAT: utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!

I search all fliesystem tree but nowere usb pen is mounted automaticly ;-(

---

### Post by sparks40 on 2005-04-09
#2 (Nad) - Could you please be more specific on the full name of the hotplug scripts package. I checked Synaptic but couldn't find it.

TNX

---

### Post by Lustiger Lurch on 2005-04-09
thread nr. 3456456467


search for mount usb 


fstab is the key

---

### Post by nad on 2005-04-09
The package is called just 'hotplug'.

I have noticed several posts about broken hotplug actions. I suggest that you first use apt-get to update and upgrade your installation. This may be all you need to do. Post back with any problems.

Dan M

---

### Post by oldmarti on 2005-04-09
Here all steps:
1. Install Ubuntu hoary from CD (date 07.04.2005)
2. At boot using 'server' configuration (minimal install no gui)
3. apt-get update
4. apt-get upgrade
(package hotplug is installed by default)
When connect usbpen, in \dev I found sda and sda1 file.

5.mkdir /media/usbpen
Mount with mount /dev/sda /media/usbpen
It's working! If add line in fstab no problem!
But it is possible to automount pen (and autodismount)? Like gnome? (in standard installation with gnome desktop no needed manual mount or line in fstab)

---

### Post by sparks40 on 2005-04-09
TNX Nad I will download and try.

---

### Post by nad on 2005-04-09
Am I to understand that the line in /etc/fstab is not persistent when you manually enter it as root? Also, is this a typo "Mount with mount /dev/sda /media/usbpen". Here, you are not describing the filesystem to mount, but, the device itself. You must mean "mount /dev/sda1 /media/usbpen".

If you change the line in /etc/fstab to '/dev/sda1 /media/usbpen vfat rw,user,auto' what happens. Please also post the output of 'cat /proc/mounts'. I'm trying to get a handle on the quirkiness of ubuntu.

Dan M

---

### Post by entangled on 2005-04-19
[QUOTE=oldmarti]Hi,
I just install ubutnu (server configuration without gui). I want to transfer some files using usb pen. Hotplug detect pen and I can mount it with mount /dev/sda1 /media/usbstick.
It's possible to mount automaticly? (In full installation with gnome, no problem)
Thanks[/QUOTE]

I had same problem of no automount, but manual mount working.
Fixed my problem by setting 'pmount' to 'suid root' (quaint and obscure terminology, like most of linux/unix! :-| )

i.e. type in a command shell (using backquotes around which ...)
sudo chmod +s `which pmount`
and
sudo chmod +s `which pumount`

My problem only appeared after large scale update from Warty to Hoary. I guess it is a package configuration fault

---

