---
title: "Cannot Hotsync with Treo 650"
date: 2006-06-20
forum: Hardware &amp; Laptops
---

### Post by dan4444 on 2006-06-20
I have looked at all the threads I could possibly find on this, tried various potential solutions to no avail, and remain stuck at the following:

I launch jpilot, click hotsync on my treo, and then I click hotsync within jpilot.

"dmesg | grep usb" reveals:

[4300943.238000] usb 1-2: new full speed USB device using uhci_hcd and address 19
[4300943.418000] usb 1-2: configuration #1 chosen from 1 choice
[4300943.424000] usb 1-2: Handspring Visor / Palm OS converter now attached to ttyUSB0
[4300943.425000] usb 1-2: Handspring Visor / Palm OS converter now attached to ttyUSB1

so, ubuntu is noticing when my treo is attempting to sync (I know this, because when the hotsync on my treo fails, the following line gets added to the "dmesg | grep usb" results)

[4301066.282000] usb 1-2: USB disconnect, address 19

Meanwhile, the results of my hotsync from Jpilot were:

****************************************
 Syncing on device /dev/pilot
 Press the HotSync button now
****************************************
pi_bind error: /dev/pilot Too many levels of symbolic links
Check your serial port and settings
Exiting with status SYNC_ERROR_BIND
Finished


I will obviously need to first address the error of "Too many levels of symbolic links", but I have no idea of how to do so. Please help.

---

### Post by dan4444 on 2006-06-20
Oops... So, I corrected the jpilot settings to connect to /dev/ttyUSB1 as opposed to /dev/pilot

And now my clicking on Hotsync within jpilot reveals:

****************************************
 Syncing on device /dev/ttyUSB1
 Press the HotSync button now
****************************************
pi_bind error: /dev/ttyUSB1 No such file or directory
Check your serial port and settings
Exiting with status SYNC_ERROR_BIND
Finished

Can someone please instruct me on the proper way to create and configure this device (/dev/ttyUSB1)?

---

### Post by wastrel on 2006-06-20
The USB devices nodes /dev/ttyUSB* aren't created until you hit the hotsync button.  I know you said in your first post that you hit hotsync on the treo then on jpilot, but did you do that the 2nd time after you'd fixed the jpilot settings?

If you've plugged any other USB devices in in the meantime, they may now be on /dev/ttyUSB0 and 1 and you may need to switch jpilot to /dev/ttyUSB2

Once you've got jpilot working you can set up your udev rules to create /dev/pilot automatically when you sync - there's a thread around somewhere about that.

---

### Post by nolongerlivecd on 2006-06-20
Sorry for hijacking, but I followed all the steps above with my LifeDrive.

It doesn't work.

User@Ubuntu:~$ dmesg | grep usb
[17179576.320000] usbcore: registered new driver usbfs
[17179576.320000] usbcore: registered new driver hub
[17179576.772000] usb 2-1: new low speed USB device using uhci_hcd and address 2[17179577.528000] usb 2-1: new low speed USB device using uhci_hcd and address 3[17179590.976000] usbcore: registered new driver hiddev
[17179590.996000] input: USB HID v1.10 Mouse [HID 062a:0000] on usb-0000:00:1d.1-1
[17179590.996000] usbcore: registered new driver usbhid
[17179590.996000] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[17181191.012000] usb 5-1: new high speed USB device using ehci_hcd and address 3
[17181191.584000] usbcore: registered new driver usbserial
[17181191.588000] drivers/usb/serial/usb-serial.c: USB Serial support registered for generic
[17181191.588000] usbcore: registered new driver usbserial_generic
[17181191.588000] drivers/usb/serial/usb-serial.c: USB Serial Driver core
[17181191.624000] drivers/usb/serial/usb-serial.c: USB Serial support registered for Handspring Visor / Palm OS
[17181191.624000] drivers/usb/serial/usb-serial.c: USB Serial support registered for Sony Clie 3.5
[17181191.628000] drivers/usb/serial/usb-serial.c: USB Serial support registered for Sony Clie 5.0
[17181191.928000] usb 5-1: palm_os_4_probe - error -110 getting connection info
[17181191.928000] usb 5-1: Handspring Visor / Palm OS converter now attached to ttyUSB0
[17181191.928000] usb 5-1: Handspring Visor / Palm OS converter now attached to ttyUSB1
[17181191.932000] usbcore: registered new driver visor
[17181191.932000] drivers/usb/serial/visor.c: USB HandSpring Visor / Palm OS driver
[17181201.356000] usb 5-1: USB disconnect, address 3


It still shows 

****************************************
Syncing on device /dev/ttyUSB1
Press the HotSync button now
****************************************
pi_bind error: /dev/ttyUSB0 No such file or directory
Check your serial port and settings
Exiting with status SYNC_ERROR_BIND
Finished

---

### Post by wastrel on 2006-06-20
argh.  

OK, try setting jpilot to /dev/ttyUSB0, not /dev/ttyUSB1

In Breezy it worked to sync with either /dev/ttyUSB0 or /dev/ttyUSB1 (iirc), but (I'm testing this now) in Dapper I am unable to sync with /dev/ttyUSB1 - it only works with /dev/ttyUSB0.

---

### Post by gjaffe on 2006-06-21
I got my Treo 650 to work with jpilot on Dapper (sort of).  I set jpilot to use /dev/ttyUSB1.  I have to press the Hotsync button on the usb cable about 1 second before I click on the Hotsync button in jpilot.  The timing is critical.  Waiting too long (or too short) causes the Hotsync to freeze.  I can only get it to work about 40% of the time.

If anyone knows of a way to eliminate the critical timing, I'd love to hear.

---

### Post by nolongerlivecd on 2006-06-21
I tested with both ttyUSB0 and ttyUSB1

---

### Post by ivanwillsau on 2006-06-23
I am getting a similar problem with my Treo 650.

I have tried /dev/pilot symlink as well /dev/ttyUSB0,1,2,3 which are all being created by udev.

I have been careful to press the sync button before running the applications and checked that the devices are actually there while trying to synchronise.

I have tried gpilot and jpilot all to noavail.

I have added to /usr/share/gnome-pilot/devices.xml the following lines

 <!-- Palm Treo 650 -->
 <device vendor_id="0830" product_id="0061" />

is there something that I could be missing?

---

### Post by pito on 2006-06-28
I had BIG problems to synchronize TE2 after I updated to Draper.

I managed it to synch with pilot-xfer only three times out of maybe hundreds. 
I tried different tricks, nothing helped.

But...after rumors that kernel 2.6.15 is broken regardin udev and usb stuff.

What I did today was that I switched back the kernel from Version 2.6.15 to 2.6.12, and the sync works every time both from command line,pilot-xfer, and via jpilot.

I recovered the old archived manu.lst~ from Breeze and rebooted the OS.
Then I ran "sudo modprobe visor" and I am back in the bussines.

There are unconfirmed infos that the new kernel for Draper 2.6.17 work perfect as well.

Hope it will help others.

/piotr

---

### Post by tragen on 2008-03-25
This page worked for me:

[http://www.h8n.com/tiki-index.php?page=Treo%20650%20setup%20with%20Ubuntu](http://www.h8n.com/tiki-index.php?page=Treo%20650%20setup%20with%20Ubuntu)

but on the offchance that page/site goes goodbye:

```

1) Hook up Treo to computer via USB
Check to see if the OS sees your Treo

tail -f /var/log/messages


2) Click HotSync? button
You should see something like the following output in /var/log/messages

Jul 21 08:34:43 laptop kernel: [31222.449600] usb 2-2: new full speed USB device using uhci_hcd and address 3
Jul 21 08:34:43 laptop kernel: [31222.623557] usb 2-2: configuration #1 chosen from 1 choice
Jul 21 08:34:54 laptop kernel: [31232.920043] usb 2-2: USB disconnect, address 3


This means your computer can see the USB message but doesn't know what it is

Tell Ubuntu what the hardware is trying to talk to it

c8h10n4o2@laptop:~$ sudo /sbin/modprobe usbserial
c8h10n4o2@laptop:~$ sudo /sbin/modprobe visor


Now when you try to sync your Treo, you should see something like the following output in /var/log/messages

Jul 21 08:37:27 laptop kernel: [31385.682799] usb 2-2: USB disconnect, address 5
Jul 21 08:37:27 laptop kernel: [31385.683606] visor ttyUSB0: Handspring Visor / Palm OS converter now disconnected from ttyUSB0
Jul 21 08:37:27 laptop kernel: [31385.683751] visor ttyUSB1: Handspring Visor / Palm OS converter now disconnected from ttyUSB1



You can also look at your lsmod to see if Ubuntu knows what your hardware is

c8h10n4o2@laptop:~$ sudo /sbin/lsmod | grep visor
visor                  20364  0
usbserial              32488  1 visor
usbcore               134280  9 visor,usbserial,usbhid,ndiswrapper,usb_storage,libusual,ehci_hcd,uhci_hcd



Tell your OS what the hardware is for next time you boot
sudo vi /etc/modprobe.d/options
Add the following line:

options visor vendor=0x830 product=0x61



Create /dev/pilot as a symlink every time the palm mounts
c8h10n4o2@laptop:/$ sudo vi /etc/udev/rules.d/10-custom.rules

KERNEL="ttyUSB*", NAME="%k", SYMLINK="pilot", GROUP="uucp", MODE="0666"



Now you must log out & back in to pick up these changes.
Now when you sync, it will create /dev/ttyUSB0 or /dev/ttyUSB1 or whatever the next number is. However, this will not be writable to world (you will not be the owner or a group member. I tried adding myself to the group dialout but it did not fix things. Thus:

<ls /dev>
lrwxrwxrwx 1 root root 7 2007-07-21 08:38 pilot -> ttyUSB1
crw-rw-r-- 1 root dialout 188, 1 2007-07-21 08:38 ttyUSB1

Configure ttyUSB* to give the world RW access when they mount

root@laptop:/etc/udev/rules.d# vi 40-permissions.rules
Need to modify MODE of ttyUSB* from 0660 to 0666

# Serial devices
SUBSYSTEM=="tty",                       GROUP="c8h10n4o2"
SUBSYSTEM=="capi",                      GROUP="dialout"
SUBSYSTEM=="slamr",                     GROUP="dialout"
SUBSYSTEM=="zaptel",                    GROUP="dialout"
KERNEL=="ttyLTM[0-9]*",                 GROUP="dialout", MODE="0666"



When you rebooted, the drivers were lost. Thus, add the following

vi /etc/modules
c8h10n4o2@laptop:/var/log/vmware$ more /etc/modules

# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
sbp2
snd-intel8x0
# ADD THE NEXT 2 LINES SO YOU CAN SEE YOUR PDA
usbserial
visor

```

---

