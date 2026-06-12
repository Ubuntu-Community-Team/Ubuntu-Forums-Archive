---
title: "Please help, MicroSolutions Back Pack CD-RW issue, USB style"
date: 2006-07-18
forum: Hardware &amp; Laptops
---

### Post by dannyboy79 on 2006-07-18
Whoever can help me I would forever owe you. I have been on linux for about a month now. I installed Ubuntu on a desktop that I built myself and am using it as a media server sort of and now I have installed Xubuntu on an old Hitachi Laptop 266Mhz with 128mb RAM. I own a Microsolutions CD-RW that I use with the laptop. When I was using Win98 I used to use USB cause it's way better than the the alternative Parallel port. Anyway, on the microsolutions website they list the models of the cd-rw that work out of the box with usb but mine isn't one of them so for mine they have either a .rpm or a .tar that I downloaded. Trouble is, they don't tell me what I am suppose to do with the files once I extract them???? I tried using alien on the .rpm but it didn't create a .deb file so I am stuck. Can someone please please tell me what I am suppose to do with the files that I have from Microsolutions website? I did try going to the directory using the terminal and I typed ./configure but nothing happened, it gave me an error I believe? Anyone's help would be great. By the way, I am loving Ubuntu so far. I figured out how to get my machines networked (1 Winxp, 1 Xubuntu, 1 Ubuntu), I figured out how to get the pcmcia wireless netgear card to work with xubuntu, i figured out how to be able to print to the windoz box from both ubuntu's using CUPS. It has been a struggle but I did usintg gogle and this great site. But I am afraid I have met my match with this one!!!!!! HELP, thank you. Sorry this is so long.

](*,)

---

### Post by dannyboy79 on 2006-07-27
I can't believe that no one has tried to get an old back pack to work with linux???? ANYONE HELP PLEASE?

---

### Post by wpshooter on 2006-07-27
> **dannyboy79 said:**
> I can't believe that no one has tried to get an old back pack to work with linux???? ANYONE HELP PLEASE?

It just happens that we have some of these old drives here at work.  I might try to see if I can get one to work on one of my home installations of Ubuntu when I get a chance.  But may be a fairly long time.  Will posted back, when I get a chance.

However, in the mean time maybe you can give me some clues as to how to get a printer working using CUPS.  I have an HP setup as a **LOCAL** printer (on LPT1/parallel) on one Ubuntu machine and I want to be able to print to this same printer from my other Ubuntu machines.  I have tried to do a setup as a network printer on one of the **other** Ubuntu machines but I am not sure as to exactly what it is that I am supposed to put in the URL/device line.  I have tried almost every possible combination of parameters I can think of and still can not get it to work.  The closest I have come is getting it setup as a network printer, but when I try to print the test page, it says that the printer is busy and will try again in 30 seconds.  

Thanks.

---

### Post by dannyboy79 on 2006-07-28
WPSHOOTER,
I am a linux newbie but it just so happens that I have my laptop running xubuntu setup so that it can connect and print to a printer that is hooked via usb to a winxp box on my network. When I get home from work, I'll view what I put in my cups setup to get it work and I'll let you know asap. It should be around 4 p.m. central time or so. I was rather surprised that I figured it out since I am linux newbie and ubuntu is my first linux distro ever. I work with ubuntu dapper drake and also xubuntu dapper drake. The only things that I really still struggling with is mounting a networked folder on my laptop (xubuntu) and then obviously gettting my laptop to be able to burn cd's using this old back pack by microsolutions that is hooked up via usb. Like I said, their website has an .rpm as well as .tar but I just don't know what to do with all the files. I'll post as soon as I get home. Talk to you later. I'll just have to remember how to edit my cups config. I know it has to do with entering something on my browser address line and then the cups administration pages come up. I'll gogle it and probably find it right away. Bye for now.

---

### Post by dannyboy79 on 2006-07-28
If you have cups installed that came with ubuntu 6.06 than you should be able to type in "http://locaslhost:631/printers" into your web browser and that'll take you to the cups web based config gui. When I look at the printers installed the device url is "smb://WINXP/HPOfficeJet" without the quotes obviously. I don't know if you are using nfs instead of samba cause you have all linux boxes but that's what works for me when printing from xubuntu to a printer that is hooked to a winxp box thru usb. If you have any more questions please feel free to ask but we should probably start a new thread titled cups config for printer over network or something like that. Just send me a private message with your question and paste the link to the new thread you start and I'll answer your questions. Later dude. Hope this helps ya.

---

### Post by dannyboy79 on 2006-09-05
bump, please someone help me. The tar file has a install.sh but I don't know what to do with it. I go to the command line where the file is located and type in "sudo install.sh" but nothing happens. WHat the readme says is that this package uses the hotplug system to upload new firmware into the backpack cd-writer but I don't know how to do what I need to do. Someone please help me!

---

### Post by wonton180 on 2007-02-06
this is a bit of hack, but it works to get you using the CDROM and burning CD-Rs.  I have the Backpack 24x CDRW drive (model 186100, series 6 driver) using the USB interface.  Ubuntu 6.10.  You'll need the package from microsystems with all the firmwares.

1) install "fxload".  Use synaptic to download and install this firmware util.

2) plug in the drive via USB and navigate the using the Device Manager offered from System->Administration->Device Manager menu item.  We are looking for where the USB system has allocated the device.  Look over all your USB entries and look for the unknown Microsystems device.  Once you found it, select the "USB Raw Device Access" item.  On the right, look for the following attribute: linux.device_file.  make note of the listed file.  For example, mine is listed as: /dev/bus/usb/005/008.  (side note: "005" is the USB bus number, and "008" is the device number allocated by the bus).  If you plug into the same USB port, you'll get the same bus number, but the device numbers are dynamic.

3) load away.  Using the fxload utility, load the firmware to the target usb file.

root@ion:~/Desktop/bpck-usb-firmware-1.1# fxload -v -t fx2 -D /dev/bus/usb/005/008 -I firmware/BP2CD6.HEX
microcontroller type: fx2
single stage:  load on-chip memory
open RAM hexfile image firmware/BP2CD6.HEX
stop CPU
write on-chip, addr 0x0000 len    3 (0x0003)
write on-chip, addr 0x000b len    3 (0x0003)
write on-chip, addr 0x0040 len    5 (0x0005)
write on-chip, addr 0x0033 len    3 (0x0003)
write on-chip, addr 0x0100 len 1013 (0x03f5)
write on-chip, addr 0x04f5 len 1013 (0x03f5)
write on-chip, addr 0x08ea len  413 (0x019d)
write on-chip, addr 0x0aa6 len  152 (0x0098)
write on-chip, addr 0x0bc0 len 1021 (0x03fd)
write on-chip, addr 0x0fbd len 1013 (0x03f5)
write on-chip, addr 0x13b2 len   16 (0x0010)
... WROTE: 4655 bytes, 11 segments, avg 423
reset CPU
root@ion:~/Desktop/bpck-usb-firmware-1.1# 

You'll notice the drive reset and then be recognized by linux.   From dmesg:

[17186968.376000] usb 5-8: new high speed USB device using ehci_hcd and address 8
[17186968.508000] usb 5-8: configuration #1 chosen from 1 choice
[17189149.276000] usb 5-8: USB disconnect, address 8  (DEVICE RESET HERE!!!!)
[17189151.028000] usb 5-8: new high speed USB device using ehci_hcd and address 9
[17189151.160000] usb 5-8: configuration #1 chosen from 1 choice
[17189151.160000] scsi3 : SCSI emulation for USB Mass Storage devices
[17189151.160000] usb-storage: device found at 9
[17189151.160000] usb-storage: waiting for device to settle before scanning
[17189156.160000] usb-storage: device scan complete
[17189156.168000]   Vendor: TEAC      Model: CD-W216E          Rev: 1.0A
[17189156.168000]   Type:   CD-ROM                             ANSI SCSI revision: 00
[17189156.180000] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
[17189156.180000] sr 3:0:0:0: Attached scsi CD-ROM sr0
[17189156.180000] sr 3:0:0:0: Attached scsi generic sg1 type 5

Note device was reallocated a new device id (009) by the bus after reset.

4) burn, baby, burn!

You'll have to use some smarts to figure out which firmware is appropriate for the target device.  the BPxCD6.HEX worked for me.  Series2 devices support USB2.0 which is why i choose that firmware.  good luck!

oh, and this is a hack because as soon as you disconnect the device or reboot, you'll lose the device.  since the change in the hotplug system to udev and stuff, i don't know yet how to have the OS scripts manage this process.

- John

---

### Post by wonton180 on 2007-03-12
an update:  I created a shell small script to search thru the USB tree for the device once plugged in.  Works like a charm...there's is probably a more elegant way thru udev management, but i'm not familiar with those tools, config.  enjoy!

---- load_backpack.sh -----

#!/bin/bash
#
# searches for Backpack CDRW drive on USB device tree.
#
# if found, loads the firmware update to the device so Linux
# may detect and recognize the drive

grep -B 2 "Vendor=0ac9 ProdID=0001" /dev/bus/usb/devices | head -1 | awk '{ \

fieldcount = split($0, fullstr);
busstr = fullstr[2];
fieldcount = split(busstr, busnum, "=");
devnum = fullstr[8];

targetdev = "/dev/bus/usb/0" busnum[2] "/00" devnum;
execstr = "sudo fxload -t fx2 -D " targetdev " -I /etc/backpack_usb/BP2CD6.HEX"
print "Loading USB Backpack firmware to " targetdev;
system(execstr);

}'

---

