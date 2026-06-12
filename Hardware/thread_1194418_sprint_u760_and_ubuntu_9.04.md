---
title: "sprint u760 and ubuntu 9.04"
date: 2009-06-22
forum: Hardware
---

### Post by lordkom on 2009-06-22
Here's my problem:

HP Compaq 6910p laptop

kom@laptop:~$ lsusb
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 007: ID 1410:5030 Novatel Wireless 

Ok, so the u760 is seen by USB.... but it automatically detects as usb-storage and not as a usb-serial modem.

Here's the dmesg when I plug it in, and we can see it's mounted also:

[11972.776163] usb 7-1: new full speed USB device using uhci_hcd and address 7
[11972.944088] usb 7-1: configuration #1 chosen from 1 choice
[11972.946638] scsi16 : SCSI emulation for USB Mass Storage devices
[11972.947627] usb-storage: device found at 7
[11972.947633] usb-storage: waiting for device to settle before scanning
[11972.947710] scsi17 : SCSI emulation for USB Mass Storage devices
[11972.950690] usb-storage: device found at 7
[11972.950696] usb-storage: waiting for device to settle before scanning
[11977.945337] usb-storage: device scan complete
[11977.948256] scsi 16:0:0:0: CD-ROM            Novatel  Mass Storage     1.00 PQ: 0 ANSI: 2
[11977.951650] usb-storage: device scan complete
[11977.954234] scsi 17:0:0:0: Direct-Access     Novatel  MMC Storage      2.31 PQ: 0 ANSI: 2
[11977.994214] sr1: scsi-1 drive
[11977.994429] sr 16:0:0:0: Attached scsi CD-ROM sr1
[11977.994582] sr 16:0:0:0: Attached scsi generic sg2 type 5
[11978.009036] sd 17:0:0:0: [sdb] Attached SCSI removable disk
[11978.009176] sd 17:0:0:0: Attached scsi generic sg3 type 0
[11978.269263] sr1: CDROM (ioctl) error, command: Get configuration 46 00 00 00 00 00 00 00 20 00
[11978.269277] sr: Sense Key : No Sense [current] 
[11978.269282] sr: Add. Sense: No additional sense information
[11980.766255] sr1: CDROM (ioctl) error, command: Get configuration 46 00 00 00 00 00 00 00 20 00
[11980.766284] sr: Sense Key : No Sense [current] 
[11980.766292] sr: Add. Sense: No additional sense information
[11981.315232] sr1: CDROM (ioctl) error, command: Get configuration 46 00 00 00 00 00 00 00 20 00
[11981.315252] sr: Sense Key : No Sense [current] 
[11981.315257] sr: Add. Sense: No additional sense information
[11981.322208] sr1: CDROM (ioctl) error, command: Get configuration 46 00 00 28 00 00 00 00 10 00
[11981.322222] sr: Sense Key : No Sense [current] 
[11981.322227] sr: Add. Sense: No additional sense information
[11981.329222] sr1: CDROM (ioctl) error, command: Get configuration 46 00 00 20 00 00 00 00 18 00
[11981.329239] sr: Sense Key : No Sense [current] 
[11981.329244] sr: Add. Sense: No additional sense information
[11981.350561] sr1: CDROM (ioctl) error, command: Get configuration 46 00 00 00 00 00 00 00 20 00
[11981.350569] sr: Sense Key : No Sense [current] 
[11981.350572] sr: Add. Sense: No additional sense information
[11981.377246] ISO 9660 Extensions: Microsoft Joliet Level 1
[11981.382261] ISO 9660 Extensions: IEEE_P1282

kom@laptop:~$ mount | grep sr1
/dev/sr1 on /media/Sprint SmartView type iso9660 (ro,nosuid,nodev,uhelper=hal,uid=1000,utf8)

A few moments later, ubuntu sees the modem. At this point, it used to work for me, now it's not... I don't know if a system update changed some settings.. I havent made any modifications to settings myself either thru BIOS/hardware changes, etc... Everything is stock ubuntu install and upgrade thru the ubuntu gnome updater app...

[12106.536270] usb 7-1: USB disconnect, address 7
[12106.656788] scsi 16:0:0:0: rejecting I/O to dead device
[12107.768077] usb 7-1: new full speed USB device using uhci_hcd and address 8
[12107.929386] usb 7-1: configuration #1 chosen from 1 choice
[12107.936963] usbserial_generic 7-1:1.0: generic converter detected
[12107.937100] usb 7-1: generic converter now attached to ttyUSB0
[12107.939846] usbserial_generic 7-1:1.1: generic converter detected
[12107.940040] usb 7-1: generic converter now attached to ttyUSB1
kom@laptop:~$ wvdial
--> WvDial: Internet dialer version 1.60
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
--> Sending: ATQ0
--> Re-Sending: ATZ
--> Modem not responding.
kom@laptop:~$ 

What can I do at this point to make the USB modem work when I plug it in and not wait for the kernel or whatever is probing USB to enable the modem? I read on forums that usb-serial is compiled and a kernel module so I cant modprobe usb-serial and enable like the the sprint docs suggest. Does ubuntu have a USB manager to make life easy? Any suggestions appreciated. Thanks.

---

### Post by GeorgeVita on 2009-06-23
Hi **lordkom**,
although I am not sure that your problem is usbserial, you are right: with Ubuntu 9.04 many things changed regarding USB modems. A recent update installs kernel **2.6.28-13-generic** which restores **usbserial** as an external driver.

Read at [http://ubuntuforums.org/showthread.php?t=1193682](http://ubuntuforums.org/showthread.php?t=1193682) the **2 methods** to use it (old/new kernel).

Another try: **eject sr1** (sr1=from your example, you may place the appropriate) and see any changes (ttyUSBx, lsusb, dmesg).

Regards,
George

---

### Post by lordkom on 2009-06-24
after a: modprobe usbserial vendor=0x1410 product=0x6000

What's up with the pause ? I need to RTFM on where/how the USB stuff is being managed by Ubuntu... Any suggestions?

[10895.412091] usb 7-1: new full speed USB device using uhci_hcd and address 2
[10895.578722] usb 7-1: configuration #1 chosen from 1 choice
[10971.660668] usbcore: registered new interface driver usbserial
[10971.660700] USB Serial support registered for generic
[10971.660804] usbcore: registered new interface driver usbserial_generic
[10971.660809] usbserial: USB Serial Driver core
(pause)
[11029.472160] usb 7-1: USB disconnect, address 2
[11030.476088] usb 7-1: new full speed USB device using uhci_hcd and address 3
[11030.642743] usb 7-1: configuration #1 chosen from 1 choice
[11030.645222] usbserial_generic 7-1:1.0: generic converter detected
[11030.645326] usb 7-1: generic converter now attached to ttyUSB0
[11030.649060] usbserial_generic 7-1:1.1: generic converter detected
[11030.649156] usb 7-1: generic converter now attached to ttyUSB1
root@laptop:~# wvdial
--> WvDial: Internet dialer version 1.60
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
--> Sending: ATQ0
--> Re-Sending: ATZ
--> Modem not responding.
root@laptop:~# dmesg
...
[11099.160137] usb 7-1: USB disconnect, address 3
[11099.162804] generic ttyUSB0: generic converter now disconnected from ttyUSB0
[11099.162834] usbserial_generic 7-1:1.0: device disconnected
[11099.163191] generic ttyUSB1: generic converter now disconnected from ttyUSB1
[11099.163216] usbserial_generic 7-1:1.1: device disconnected
[11101.592116] usb 7-1: new full speed USB device using uhci_hcd and address 4
[11101.757321] usb 7-1: configuration #1 chosen from 1 choice
root@laptop:~# 

what's going on ?

---

### Post by sprawlgeek on 2009-06-24
I am experiencing the exact same issue, with the VirginMobile Broadband2go modem, which I believe is the same model.  I have tried all versions of what is suggested with no joy.

---

### Post by GeorgeVita on 2009-06-25
Hi **lordkom** and **sprawlgeek**,
as I don't have your modem I can only give some ideas to try.

Now days a 3G modem is a multi mode USB device with at least two serial ports (data, control), one virtual CDROM (with windows drivers) and sometimes a microSD card reader. Some modems need a command/method to switch to the real modem state (ATcommand, usb_modeswitch, eject of the drive,...).

For your case, as we did not found a working solution yet (implemented by a developer or another user), you must make some basic tests hoping that you can gain the usbserial modem communication port. Some ideas:

1- boot without the modem, wait for the system to fully load
2- check kernel version with terminal command: **uname -a**
(recent version of 9.04 update is 2.6.28-13-generic)
3- attach modem, wait 10-15 seconds
4- **lsusb** (to find the vendor/product IDs)
5- **ls /dev/ttyU* /dev/ttyA* /dev/ttyH*** (to see any port created)
6- **dmesg** (last lines show ports and storage drive created sr1??)
7- **eject sr1** (replace 'sr1' with the one found on dmesg)
8- wait some seconds and retry **lsusb** and **ls /dev/...**
9- try **sudo wvdialconf** if any /dev/ttyUSBx found
10- If not managed try: **sudo modprobe usbserial vendor=0xABCD product=0xEFGH**
('ABCD' and 'EFGH' are from the last **lsusb** at point 8 if different)
11- retry **sudo wvdialconf**

Finally post here your comments for us or other readers to follow up.

Regards,
George

EDIT: read a similar case with another modem finally 'solved' using usb-modeswitch
**[http://ubuntuforums.org/showthread.php?t=1193355](http://ubuntuforums.org/showthread.php?t=1193355)**

---

### Post by sprawlgeek on 2009-06-25
Thanks much!  I will try your steps in order this evening.  Last night, doing some research, I believe that a patch was built and is being added to the kernel.  I went ahead and tried upgrading to the  2.6.30 kernel but was not successful.  (I am running 2.6.28-13-generic) on Ubuntu 9.05. LSUSB will list Novatel but nothing more descriptive.  I have not been able to ascertain any tty ports allocated. Modprobe USBSerial did not generate any errors. eject SR1 states nothing was mounted. (will provide full descriptions tonight).  wvdialconf can not locate any modems. If I go through gnome, I can see the USB storage but I am unable to mount or unmount it.  The same is true with the mount command.

USB_ModeSwitch does not locate the device. 

Here is a link to one of threads I caught on the kernel patch (I am at the limit of my knowledge in this area)

[http://www.nabble.com/-PATCH-0-1--UBUNTU:--Hardy-SRU--SAUCE--Add-signatures-to-airprime-driver-to-support-newer-Novatel-devices-td23305201.html](http://www.nabble.com/-PATCH-0-1--UBUNTU:--Hardy-SRU--SAUCE--Add-signatures-to-airprime-driver-to-support-newer-Novatel-devices-td23305201.html)

---

### Post by lordkom on 2009-06-26
sprint says it's 0x6000... that wont do it. but the 0x5030 does

[38850.405230] usbcore: registered new interface driver usbserial
[38850.405262] USB Serial support registered for generic
[38850.405311] usbserial_generic 5-1:1.0: generic converter detected
[38850.405437] usb 5-1: generic converter now attached to ttyUSB0
[38850.405456] usbserial_generic 5-1:1.1: generic converter detected
[38850.405540] usb 5-1: generic converter now attached to ttyUSB1
[38850.405568] usbcore: registered new interface driver usbserial_generic
[38850.405572] usbserial: USB Serial Driver core


root@laptop:~# lsusb
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 002: ID 1410:5030 Novatel Wireless 
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 002: ID 08ff:2580 AuthenTec, Inc. AES2501 Fingerprint Sensor
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
root@laptop:~# modprobe usbserial vendor=0x1410 product=0x5030
root@laptop:~# wvdial
--> WvDial: Internet dialer version 1.60
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
--> Sending: ATQ0
--> Re-Sending: ATZ
--> Modem not responding.
root@laptop:~# 

anyone else in the world have this problem

---

### Post by sprawlgeek on 2009-07-07
OK.  I was able to get it working...Here is how i got there:

Installed USB_ModeSwitch
added the following section to usb_modeswitch.conf

########################################################
# Novatel U760 USB modem
#
# Contributor: Richard Laager

DefaultVendor= 0x1410
DefaultProduct= 0x5031

TargetVendor= 0x1410
TargetProduct= 0x6002

# only for reference
MessageEndpoint=0x08

MessageContent="5553424312345678000000000000061b000000020000000000000000000000"


########################################################

sudo modprobe usbserial vendor=0x1410 product=0x6002
launch gnome-ppp with sudo
(sudo gnome-ppp) not good practice but it works for the moment.
click setup and then click on detect modem
set speed at 460800
Under the Options tab, click the box on "Ignore Terminal Strings (stupid mode)
Click Close
Username and password are both: "Internet"
Dial number is #777

A couple of notations.

* If you remove and re-insert the modem you have to restart with usb_modswitch.
* The configuration (?) is not holding from one bootup to the next. so you need to---
* start with usb_modeswitch each bootup including sudo modeprobe.

Its not pretty, but it is working and I am a happy camper

---

### Post by GeorgeVita on 2009-07-08
Hi **sprawlgeek**, below you can find an idea to automate this (I am not sure if it work, you have to check it):

```
sudo gedit /etc/udev/rules.d/90-u760.rules
```

```
ACTION!="add", GOTO="u760_End"

SUBSYSTEM=="usb", SYSFS{idProduct}=="5031", SYSFS{idVendor}=="1410", GOTO="u760_ZeroCD"

SUBSYSTEM=="usb", SYSFS{idProduct}=="6002", SYSFS{idVendor}=="1410", GOTO="u760_Modem"

LABEL="u760_ZeroCD"
RUN+="/usr/sbin/usb_modeswitch -W -c /etc/usb_modeswitch.conf"

LABEL="u760_Modem"
RUN+="/sbin/modprobe usbserial vendor=0x1410 product=0x6002", MODE="660", GROUP="dialout"

LABEL="u760_End"
```

The idea is to make a new 'rule' that executes 1 of 2 commands depending on the vendorID : productID when you insert and after switching of the internal mode.
 
[COLOR="Red"]NOTE:[/COLOR] replace text "with your actual usb_modeswitch command" at RUN+ line!
Check also if usbserial is at /sbin/ directory.

Regards,
George

---

### Post by sprawlgeek on 2009-07-08
Hi GeorgeVita-

Thanks!  I will definitely give this a try!  I will update the forum with the results.

---

### Post by Elludium_Q-36 on 2009-09-19
Sprawlgeek refers to the Novatel Ovation MC760 with the microSDHC slot on Virgin mobile's prepaid wireless broadband2go internet. (For the United States anyway).

I'm contemplating buying one if this can be worked out.  I have Linux kubuntu 2.6.28-15-generic #48-Ubuntu SMP Wed Jul 29 08:54:56 UTC 2009 i686 GNU/Linux

My system has been a little 'wonky', especially with modems, which I've covered in other threads.  Even a serial modem wasn't the holy grail.  I'm currently using a Motorola iDEN i425 on Boost mobile which is grindingly slow at a nominal 2Kb/second and if it hangs up or unexpectedly disconnects, I must reboot...

I think, especially in this global economy, that modems are here to stay for a while.  They may be the only option for some locations and "The modem is busy" is not what we want to see, even though the ls command sees the hardware.

I would hate to need to buy a cradlepoint to use a usb modem over ethernet but that may be the more reliable solution!!!

---

### Post by gt50 on 2010-03-03
Thanks!

I have been fight with my new U760 for about three months in Ubuntu 9.10. My laptop happens to be dual boot. After a while I found that I could boot into Vista, open sprint connection manager and reboot to Ubuntu to use it. This caused much frustration.

usb_modeswitch took care of my problem.

To make things easier I created a desktop shortcut to usb_modeswitch. I then modified the shortcut with setuid (chmod 4755) and chown root. Now I plug it in and double click the shortcut to get it working. Then I use the network manager to connect to Sprint.

I only use my card a few hours a month so even booting to vista was not a huge hassle :p

---

### Post by Elludium_Q-36 on 2010-03-18
I'm wondering if someone has worked out a more streamlined approach as I am still comtemplating a purchase and it's an extra cost to get a Cradlepoint.

There is a gui, ndisgtk for ndiswrapper but I have read that ndiswrapper can leave residual configurations which cause trouble later on down the road.

---

### Post by Davys224 on 2010-09-19
ok so here's the lowdown and you won't need USB_ModeSwitch.

- Plug the usb modem in (simple)
- In terminal:
 -> lsusb to find the vendor/product
 -> sudo modprobe -r usbserial
 -> sudo modprobe usbserial vendor=0x[ABCD] product=0x[EFGH]
 -> in our case the ABCD=1410 and EFGH=5030 -> you can adjust if you use a different one so spread this solution!!!
- Wait till it is discovered as a modem by typing a few times wvdialconf
- sudo gnome-ppp (it won't work otherwise trust me, the config doesn't seem to follow otherwise)
- then : 
click setup and then click on detect modem
set speed at 460800
Under the Options tab, click the box on "Ignore Terminal Strings (stupid mode)
Click Close
Username and password are both: "Internet"
Dial number is #777

I'm with Bell Canada and it works fine.

Points of fact:
Have it configured on windows dual boot first or it will not work with this setup.
I don't have to redo the -r routine at every boot so far, only the wvdialconf step and the later ones...still be ready to have to ready it all just in case.
If the windows connection software appears on the desktop, go to the file browser, unmount it (the eject icon) and wait for it to find it as a modem, if you keep the win prog there it'll never ID it as a USB modem.
If connection fails when gnome-ppp tries to connects, wait its only cause it can't find a cellular network.

Thank you to all those who posted and have inspired me this solution!
sprawlgeek and lordkom 

And to my gf's dad who maintains cell towers and helped me by pluging the device in a device where we could see if the network was ok...cause Linux doesn't tell us that...unles there's a problem that does it.

PS:
Not to swell my ego or something, but I started using Linux just 2 weeks ago and figured it out!!! Anyway I love this OS!!!

---

