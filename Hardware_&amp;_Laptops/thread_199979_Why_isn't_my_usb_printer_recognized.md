---
title: "Why isn't my usb printer recognized?"
date: 2006-06-19
forum: Hardware &amp; Laptops
---

### Post by rvdrijst on 2006-06-19
Hello everyone,

I cannot get my HP PSC1210 (usb) to work. I've already spent many hours
searching through this forum and Google, but I just can't seem to find a
solution. What am I missing here?
According to linuxprinting.org linux should be able to print on the psc1210.

Specifically I have:
- Kubuntu 6.06 (but I think the problem is more general than *K*ubuntu)
- HP Printer/Scanner/Copier 1210, usb (though first of all I'm interested
in printing)
- hplip and hpijs and all the associated packages.

The problem:
When I use the 'System Settings'->'Printers' dialog in KDE (or localhost:631 for
the CUPS admin panel) and do an 'Add Printer', the list of printers doesn't
contain any usb entries. It does contain an lpt #1 entry, but that doesn't work
for me. It also contains an *hp no_device_found* entry. 

When I do **lsusb** I get:

[INDENT]Bus 002 Device 001: ID 0000:0000
Bus 001 Device 005: ID 03f0:2f11 Hewlett-Packard
Bus 001 Device 002: ID 046d:c01b Logitech, Inc. MX310 Optical Mouse
Bus 001 Device 001: ID 0000:0000[/INDENT] 

There's my printer! And my mouse. So far so good.

**lpinfo -v** gives:
[INDENT]network socket
network beh
network bluetooth
direct hp:/no_device_found
network http
network ipp
network lpd
direct parallel:/dev/lp0
direct canon:/dev/lp0
direct epson:/dev/lp0
network smb[/INDENT]

no_device_found? I thought it just showed my printer with lsusb?
I also tried **sudo printconf** but it didn't make a difference.

**hp-probe** (comes with hplip I think) produces:

[INDENT] HP Linux Imaging and Printing System (ver. 0.9.7)
 Device Detection (Probe) Utility ver. 1.3

 Copyright (c) 2003-5 Hewlett-Packard Development Company, LP
 This software comes with ABSOLUTELY NO WARRANTY.
 This is free software, and you are welcome to distribute it
 under certain conditions. See COPYING file for more details.

 [WARNING]: No devices found. If this isn't the result you are expecting,
 [WARNING]: check to make sure your devices are properly connected.[/INDENT]

which is strange because I *did* connect the printer, obviously, and it's
turned on as well (and it's in the lsusb output)

**ls -l /dev/usb/lp*** gives:

[INDENT]crw-rw---- 1 root lp 180,  0 2005-09-26 11:12 /dev/usb/lp0
crw-rw---- 1 root lp 180,  1 2005-09-26 11:12 /dev/usb/lp1
crw-rw---- 1 root lp 180, 10 2005-09-26 11:12 /dev/usb/lp10
...
*etc.*
where the '/dev/usb/lp*' are in yellow in my Konsole though I'm not sure
what that means.[/INDENT]

And **dmesg | grep usb** (after turning off and on the printer) lists:

[INDENT][   22.949822] usbcore: registered new driver usbfs
[   22.949839] usbcore: registered new driver hub
[   30.241627] usb 1-7: new low speed USB device using ohci_hcd and address 2
[   32.383301] usbcore: registered new driver hiddev
[   32.392605] input: USB HID v1.10 Mouse [Logitech USB-PS/2 Optical Mouse] on
usb-0000:00:02.0-7
[   32.392614] usbcore: registered new driver usbhid
[   32.392616] drivers/usb/input/hid-core.c: v2.01:USB HID core driver
[  181.807831] usb 1-9: new full speed USB device using ohci_hcd and address 3
[ 1023.706349] usb 1-9: USB disconnect, address 3
[ 1028.671830] usb 1-9: new full speed USB device using ohci_hcd and address 4[/INDENT]

Finally, **cat /proc/bus/usb/devices** ends with:
[INDENT][...]
T:  Bus=01 Lev=01 Prnt=01 Port=08 Cnt=02 Dev#=  4 Spd=12  MxCh= 0
D:  Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS= 8 #Cfgs=  1
P:  Vendor=03f0 ProdID=2f11 Rev= 1.00
S:  Manufacturer=Hewlett-Packard
S:  Product=psc 1200 series
S:  SerialNumber=MY39KF74SK5H
C:* #Ifs= 3 Cfg#= 1 Atr=c0 MxPwr=  2mA
I:  If#= 0 Alt= 0 #EPs= 3 Cls=ff(vend.) Sub=cc Prot=00 Driver=(none)
E:  Ad=01(O) Atr=02(Bulk) MxPS=  64 Ivl=0ms
E:  Ad=81(I) Atr=02(Bulk) MxPS=  32 Ivl=0ms
E:  Ad=82(I) Atr=03(Int.) MxPS=   8 Ivl=10ms
I:  If#= 1 Alt= 0 #EPs= 3 Cls=07(print) Sub=01 Prot=02 Driver=(none)
E:  Ad=03(O) Atr=02(Bulk) MxPS=  32 Ivl=0ms
E:  Ad=83(I) Atr=02(Bulk) MxPS=  32 Ivl=0ms
E:  Ad=84(I) Atr=03(Int.) MxPS=   8 Ivl=10ms
I:  If#= 2 Alt= 0 #EPs= 3 Cls=ff(vend.) Sub=ff Prot=ff Driver=(none)
E:  Ad=05(O) Atr=02(Bulk) MxPS=  32 Ivl=0ms
E:  Ad=85(I) Atr=02(Bulk) MxPS=  64 Ivl=0ms
E:  Ad=86(I) Atr=03(Int.) MxPS=   8 Ivl=10ms
I:  If#= 2 Alt= 1 #EPs= 3 Cls=ff(vend.) Sub=d4 Prot=00 Driver=(none)
E:  Ad=05(O) Atr=02(Bulk) MxPS=  32 Ivl=0ms
E:  Ad=85(I) Atr=02(Bulk) MxPS=  64 Ivl=0ms
E:  Ad=86(I) Atr=03(Int.) MxPS=   8 Ivl=10ms[/INDENT]

What frustrates me most is that all the guides that tell you how to get usb printers
running, expect that they are in the list you see when you do 'Add Printer', but
mine isn't! 

I already tried using different usb ports for the printer, restarting hplip,
restarting cupsys and a lot of the other tips given on forums. In other words:
I'm desparate! :( 

I would greatly appreciate any help in getting this printer printing. :) 
I do have some experience with linux in general (no guru, though) but as
far as printing goes I'm quite a n00b ;) . 

I realize this is quite a long post but I'm trying to give as much relevant
information as possible, it should make the troubleshooting easier. 

Kind regards and thanks in advance for your help,

-Robin

---

### Post by rvdrijst on 2006-06-20
Ok, I'm beginning to think this is more a usb problem than a printer problem.
Because when I insert my usb stick, nothing happens. It appears nowhere as 
a drive.

It appears to me that *Kubuntu doesn't recognize any of my usb devices*! Apart from my mouse, that is, because that is working fine.

Some more info:
With my usb stick and the printer plugged in **lsusb** gives:
[INDENT]Bus 002 Device 006: ID 08ec:0015 M-Systems Flash Disk Pioneers
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 003: ID 03f0:2f11 Hewlett-Packard
Bus 001 Device 002: ID 046d:c01b Logitech, Inc. MX310 Optical Mouse
Bus 001 Device 001: ID 0000:0000[/INDENT]

When I do **tail -f /var/log/messages** and plug in the stick, this gets appended:

[INDENT]Jun 20 11:43:18 localhost kernel: [ 1380.826620] usb 2-6: new high speed USB device using ehci_hcd and address 7[/INDENT]

And with every disconnect/connect cycle the address is incremented.

According to forum posts I found on this topic, there should be more information, even if the device doesn't get mounted! :confused: 

I must say I'm a bit disappointed by Kubuntu. :(  A lot of things don't work 'out of the box'. I already had major trouble getting the sound running (still not the best quality), the special buttons on my mouse or keyboard don't work, printer, usb stick, tv-tuner... But I really want to give this a try and I need some help! O:) 

-Robin

---

### Post by ledj0 on 2006-06-21
Hello,

I had the exactly same problem with my HP 1000. I have found the exact cause of it although I cannot garantee it is the same as yours. It is actually a combination of causes:

1- it seems that the hplip 0.9.7 has some problems recognising usb printers. Solution is to install the latest HPLIP version from hplip.sourceforge.net. This is no small task (at least for a linux newbie like me) as you have to uninstall the actual version, install the full compiling environment for the new version, dowload the version and patch, aplly the patches, compile, install, restart hplip and cups, etc (alouette...local joke). Current version is 1.6.6 and I sincerely wish that Ubuntu upgrades it's packaged version. In the meantime, carefully read and follow the installation instructions provided on the HPLIP site and everything should go fine.

2- some printers are special: like mine for instance (HP laserjet 1000) requires that it's firmware be downloaded to the printer at every power up. When I tried to install the printer in the new environment, there was no driver for my specific printer. I went ahead selecting a "close model" and I get the exact same result as "everything works as expected but the printer does not print". After some research, I discovered the pecurliar behavior of my printer when I found a linux printer driver for it at [http:// foo2rjs.rkkda.com]("http://foo2zjs.rkkda.com").

I can correlate this behavior with some people having "intermittent" problems with their printer if they shut them off between their computing sessions. So, in cases like this, make sure that you have the exact driver for your printer. I have found the link to my driver in Google by searching with "linux HP 1000 printer driver". Try it with your printer and see what comes out of it.

One final detail: make sure that user cupsys is registered in the lpadmin group. Another detail that I am not sure if it makes a difference (I did not test all possibilities) but I set the access right to /dev/usblp0 to rw for owner, group and others.

After setting all other CUPS and Samba networking configuration, I can now print from the local linux workstation, the remote linux workstation and any windows workstations on my network (I am a newbie with linux but and old, old goat with computers in general :) 

Hope this can help...

---

### Post by rvdrijst on 2006-06-21
ledj0, thank you a billion times! =D>  It worked! 'All' it took was the latest hplip version :) I cannot believe I didn't try that myself. ](*,) Although I must say version that new version 1.6.6 is only a week old... :-\" 

Well, 1 down, 999 to go... usb stick, tv-tuner, special mouse and keyboard functions, monitor standby, wine, firefox *with* flash video plugins etc, perfect sound, dvd playback, ntp without router crash, etc, etc :roll: Some of these are supposedly hard because I have an amd64x2... At least I know there's help in times of trouble :)

Well, keeps me off the street ;)

Thanks again

-Robin

---

### Post by JohnQ on 2006-06-21
[QUOTE=rvdrijst]Ok, I'm beginning to think this is more a usb problem than a printer problem.
Because when I insert my usb stick, nothing happens. It appears nowhere as 
a drive.

It appears to me that *Kubuntu doesn't recognize any of my usb devices*! Apart from my mouse, that is, because that is working fine.
[/QUOTE]

I think that you might have something with the *Kubuntu* not detecting your usb devices.  My HP 5440 worked great with my Ubuntu install, USB stick worked great, etc... When I installed kubuntu-desktop my printer stopped working and now I can't detect my usb drive or xD card reader either!

(edit to describe the fix)
Since you had described installed the latest hplip version, I figured that given my issues, it was probably a Kubuntu package that broke the whole usb-ness.  So I went through and re-installed (in synaptic) every package that had to do with usb, hal, dbus, and cups.  My system works great now.  My non-scientific approach doesn't help identify *what* the problem is though... #-o

---

### Post by rvdrijst on 2006-06-22
[QUOTE=JohnQ]So I went through and re-installed (in synaptic) every package that had to do with usb, hal, dbus, and cups.  My system works great now.  My non-scientific approach doesn't help identify *what* the problem is though... #-o[/QUOTE]

I tried your solution but unfortunately, no luck, still no recognition of my usb stick :( But thanks for the suggestion!:D 

-Robin

---

### Post by kenklay on 2006-06-26
i had problems with my usb printer and memory stick after I tried to upgrade to 6.06 from breezy.  Too many problems, so I reinstalled using a downloaded iso file and burning it to a disk.  I was able to install my Epson usb printer and my stick was recognized.

---

### Post by ivoks on 2006-07-05
/dev/usb/lp* is from old kernel. You are using Breezy's kernel. Install linux-[386 686 k7 amd64] package.

---

