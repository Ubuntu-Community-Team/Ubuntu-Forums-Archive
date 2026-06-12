---
title: "Brother DCP-110c Scan not working"
date: 2009-11-29
forum: Hardware
---

### Post by fatdadkev on 2009-11-29
If your using the DCP-110C and find the scan function not working (XSane will respond with no devices found and the Scan to file will not work from the printer) then there's a simple fix but it can take some time to find all the information so I've put it all in this post.

I found this issue after upgrading from 9.40 to 9.10 so the fix is slightly different for 9.10, i've put both solutions here though.

Download the brscan and brscan-skey files.
**[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_scn.html](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_scn.html)**
You will notice if you install the packages (Brscan first then the Scan key package) you may still not see the device or be able to scan.

You can force a re-install..
Change to the directory you saved the .deb files.
**sudo dpkg  -i  --force-all  (name of the deb file)**
i.e mine was **sudo dpkeg -i --force-all brscan2-0.2.4-0.i386.deb**
Then do the same for the skey deb package.

Check the drivers installed.
**sudo dpkg  -l  |  grep  Brother**

For my system I see....
[B]ii  brscan-skey                               0.2.1-1                                    Brother Linux scanner S-KEY tool
ii  brscan2                                   0.2.4                                      Brother Scanner Driver
ii  cupswrapperdcp110c                        1.0.2-3                                    Brother DCP110C CUPS wrapper driver
ii  dcp110clpr                                1.0.2-1                                    Brother lpr Inkjet Printer Definitions[/B]


So the drivers are installed, but why can't I scan ?
We're almost done though, we need to change a file to enable the functionality. 

For Ubunut 9.10 edit the following file 
**sudo gedit /lib/udev/rules.d/40-libsane.rules**

and add the following two lines at the bottom
[B]# Brother scanners
ATTRS{idVendor}=="04f9", ENV{libsane_matched}="yes"[/B]

If your using Ubuntu 9.04 then the edit this file.... 
**sudo gedit /lib/udev/rules.d/50-udev-default.rules**

Edit the line
[B]# libusb device nodes
SUBSYSTEM=="usb", ENV{DEVTYPE}=="usb_device",   ...   , MODE="0664"[/B]

to this...
[B]# libusb device nodes
SUBSYSTEM=="usb", ENV{DEVTYPE}=="usb_device",   ...   , MODE="0666"[/B]

Either way, save the file and reboot.


lsub will show the Brother device now (it was not showing before although the printer was working fine).

Bus 001 Device 003: ID 0d49:3200 Maxtor 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 003: ID 045e:0083 Microsoft Corp. Basic Optical Mouse
**Bus 004 Device 002: ID 04f9:0169 Brother Industries, Ltd DCP-110C RemovableDisk**
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 046d:c001 Logitech, Inc. N48/M-BB48 [FirstMouse Plus]
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

You should fine XSane will now scan and offer all the facilities.

If you intend to use the "Scan to file" function then the skey program will need enabling.

Command is **brscan-skey** 
you can check the scankey can see your scanner 
brscan-skey -l
mine shows.
** DCP-110C          : brother2:bus3;dev2  : USB                  Active**

If you use scan to file on the printer you should see similar to this (in the console window)
[B]scanimage: rounded value of br-x from 215.9 to 215.88
scanimage: rounded value of br-y from 355.6 to 355.567[/B]

the file will be sent to **/home/yourhome/brscan/filename**.

As mentioned before these instructions are in the Brother Solution Center but it took me considerable time to find the final solution due to it being placed over several pages.

Credit to Brother for supporting the Linux community so all acknowledgements to them for information included here.

---

### Post by Alfred_Jodocus on 2010-02-24
This solution worked perfectly for me and my Brother DCP-110c. Thanks!

---

### Post by Legendário on 2010-03-21
I don't know if it is a hardware problem, but I followed everything here to help a friend who owns this printer on karmic and it is just starting with linux, but it didn't work out.

I don't know why but brscan-key -l doesn't return anything. Can you help me to find out what are the possible problems?

EDIT:

I found out what was wrong. I don't know if it has changed since the last posts on the thread but I am supposed to install brscan2 instead of brscan for Brother DCP-110C. After this everything got fine.

---

### Post by sfowler on 2010-03-25
Wow dude.  I must have gone plodded through 10 go bys before I found your thread and fixed my problem in less than 10 minutes.  Thank you so much.  I was having a hard time editing that file and your fix was perfect.

EDIT:  I connected a brother MFC-8460N printer/scanner.

---

### Post by mummerx on 2010-12-28
Thanks, that is a very clear summary. Done all that, and brscan-skey works for my own login (in which I installed the drivers), but not for my wife's login. It's weird what happens:
1, Login as wife
2, Start terminal and enter brscan-skey
3, Enter brscan-skey -l    ... nothing reported.
4, Try Scan-to-file anyway
5, Device hangs trying to connect to PC
6, Logout from wife's login and try my own
7, Scanner immediately bursts into life and scans to my ~/brscan folder
   (Note - this is even before I have had a chance to run brscan-skey in my account)

If I enter brscan-skey in my login I get a report of the attached scanner, so step 3 is where it all goes worng for my wife's login.

I have a Brother DCP-6690CW, with brscan3 driver, on Ubuntu 10.04 (32 bit). Scanning initiated by GIMP (in either logins) works fine.
Grateful for any suggestions.

If it helps, here is the result of brsaneconfig3 -d (as used in my wife's login - it appears no different to when I use it in my login):

```

-----------------------------
cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda6 during installation
UUID=86a23483-b692-4565-b5ac-59f97c8e0f06 /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sda5 during installation
UUID=80f001bc-425a-40ba-9419-0e91411308a5 /boot           ext4    defaults        0       2
# /home was on /dev/sda7 during installation
UUID=b0d6d96b-a452-4fd3-ae57-53cb99dca682 /home           ext4    defaults        0       2
# swap was on /dev/sda1 during installation
UUID=dd0cf9c0-e9d3-4cb7-831b-42902e6a724f none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
-----------------------------
sane-find-scanner

  # sane-find-scanner will now attempt to detect your scanner. If the
  # result is different from what you expected, first make sure your
  # scanner is powered up and properly connected to your computer.

  # No SCSI scanners found. If you expected something different, make sure that
  # you have loaded a kernel SCSI driver for your SCSI adapter.

found USB scanner (vendor=0x04a9 [Canon], product=0x1725 [MP610 series]) at libusb:002:003
found USB scanner (vendor=0x04f9 [Brother], product=0x01f1 [DCP-6690CW]) at libusb:002:002
  # Your USB scanner was (probably) detected. It may or may not be supported by
  # SANE. Try scanimage -L and read the backend's manpage.

  # Not checking for parallel port scanners.

  # Most Scanners connected to the parallel port or other proprietary ports
  # can't be detected by this program.

  # You may want to run this program as root to find all devices. Once you
  # found the scanner devices, be sure to adjust access permissions as
  # necessary.
-----------------------------
ls -R -all /proc/bus/usb
ls: cannot access /proc/bus/usb: No such file or directory
-----------------------------
cat /proc/bus/usb/devices
cat: /proc/bus/usb/devices: No such file or directory
-----------------------------
scanimage -L
device `brother3:bus7;dev2' is a Brother DCP-6690CW USB scanner
device `pixma:04A91725_48C610' is a CANON Canon PIXMA MP610 multi-function peripheral
-----------------------------
-----------------------------
/usr/local/Brother/sane/brsanenetdevice3.cfg:

-----------------------------
/usr/local/Brother/sane/Brsane3.ini:
[Support Model]


0x0206,14,2,"DCP-145C"
0x0204,14,2,"DCP-165C"
0x0205,13,2,"DCP-185C"
0x0201,14,2,"DCP-385C"
0x0200,14,2,"DCP-585CW"
0x01ff,13,2,"DCP-535CN"
0x01fe,14,1,"MFC-250C"
0x01fd,13,1,"MFC-290C"
0x01fb,13,1,"MFC-490CW"
0x01fa,13,1,"MFC-490CN"
0x01f9,13,1,"MFC-790CW"
0x01f8,13,1,"MFC-990CW"
0x01f7,14,1,"MFC-670CD"
0x01f6,13,1,"MFC-930CDN"
0x01f5,13,1,"MFC-5490CN"
0x01f4,13,1,"MFC-5890CN"
0x01f1,13,2,"DCP-6690CW"
0x01f3,13,1,"MFC-6490CW"
0x01f2,13,1,"MFC-6490CN"

0x01f0,13,1,"MFC-6890CDW"
0x01ef,13,1,"MFC-6890CN"

0x0207,14,2,"DCP-163C"
0x0208,14,2,"DCP-167C"
0x0203,14,2,"DCP-383C"
0x0202,14,2,"DCP-387C"
0x01fc,13,1,"MFC-297C"

0x01ee,1,1,"MFC-7450",131,4
0x01ed,1,1,"MFC-7840N",131,4
0x01eb,1,1,"MFC-7320",131,4
0x01ea,2,2,"DCP-7030",131,4
0x01e9,1,2,"DCP-7040",131,4
0x01e8,1,2,"DCP-7045N",131,4
0x01e7,1,1,"MFC-7340",131,4
0x01e6,1,1,"MFC-7440N",131,4
0x01e5,1,1,"MFC-7840W",131,4
	


0x0218,17,1,"DCP-8080DN",133,4
0x021f,117,1,"DCP-8085DN",133,4


0x0217,17,1,"MFC-8480DN",133,4

0x0215,117,1,"MFC-8890DW",133,4





[ModelTypeName]
1=MFC Scanner
2=DCP Scanner

[Driver]
scanfast24=0
NoUseCM=0
compression=1
Inqueue=32000
LogFile=0
xshift_c=0


-----------------------------
/usr/local/Brother/sane/models3/ext2.ini:
[Support Model]

0x23e,14,2,"DCP-197C"
0x235,14,2,"DCP-377CW"
0x23a,14,1,"MFC-257CW"

-----------------------------
/usr/local/Brother/sane/models3/ext4.ini:
[Support Model]

0x0257,13,2,"DCP-J715W"
0x025d,13,1,"MFC-J615W"

0x0254,14,2,"DCP-J315W"
0x025B,14,1,"MFC-J265W"
0x026B,13,1,"MFC-J630W"
-----------------------------
/usr/local/Brother/sane/models3/ext3.ini:
[Support Model]
0x01c9,  17,2,"DCP-9040CN",133,4
0x01ca,  17,1,"MFC-9440CN",133,4
0x01cb, 117,2,"DCP-9045CDN",133,4
0x01cc, 117,1,"MFC-9840CDW",133,4
0x01ec, 117,1,"MFC-9640CW",133,4

0x020d ,17,1,"MFC-9450CDN",133,4
0x020c ,17,2,"DCP-9042CDN",133,4

-----------------------------
/usr/local/Brother/sane/models3/ext1.ini:
[Support Model]

0x0222,14,2,"DCP-195C"

0x0223,14,2,"DCP-365CN"
0x0224,14,2,"DCP-375CW"
0x0225,14,2,"DCP-395CN"

0x0229,13,1,"MFC-295CN"
0x022a,13,1,"MFC-495CW"
0x022c,13,1,"MFC-795CW"
0x0228,14,1,"MFC-255CW"
0x0236,14,2,"DCP-390CN"
0x0227,13,2,"DCP-595CN"
0x022b,13,1,"MFC-495CN"
0x022d,14,1,"MFC-675CD"
0x022e,14,1,"MFC-695CDN"
0x022f,14,1,"MFC-735CD"
0x0230,13,1,"MFC-935CDN"

0x021b,17,2,"DCP-8070D",133,4
0x021a,17,1,"MFC-8370DN",133,4
0x0219,117,1,"MFC-8380DN",133,4
0x023f,117,1,"MFC-8680DN",133,4

0x0216,117,1,"MFC-8880DN",133,4


0x021d,17,1,"MFC-9120CN"
0x021c,17,1,"MFC-9320CW"
0x0220,17,1,"MFC-9010CN"
0x021e,17,2,"DCP-9010CN"

-----------------------------
MODEL:"DCP-197C",ID:0x4f9:0x23e,TYPE:14,2,RE:0xffff,WE:0xffff CM:,,
MODEL:"DCP-377CW",ID:0x4f9:0x235,TYPE:14,2,RE:0xffff,WE:0xffff CM:,,
MODEL:"MFC-257CW",ID:0x4f9:0x23a,TYPE:14,1,RE:0xffff,WE:0xffff CM:,,
MODEL:"DCP-J715W",ID:0x4f9:0x257,TYPE:13,2,RE:0xffff,WE:0xffff CM:,,
MODEL:"MFC-J615W",ID:0x4f9:0x25d,TYPE:13,1,RE:0xffff,WE:0xffff CM:,,
MODEL:"DCP-J315W",ID:0x4f9:0x254,TYPE:14,2,RE:0xffff,WE:0xffff CM:,,
MODEL:"MFC-J265W",ID:0x4f9:0x25b,TYPE:14,1,RE:0xffff,WE:0xffff CM:,,
MODEL:"MFC-J630W",ID:0x4f9:0x26b,TYPE:13,1,RE:0xffff,WE:0xffff CM:,,
MODEL:"DCP-9040CN",ID:0x4f9:0x1c9,TYPE:17,2,RE:0x85,WE:0x4 CM:,,
MODEL:"MFC-9440CN",ID:0x4f9:0x1ca,TYPE:17,1,RE:0x85,WE:0x4 CM:,,
MODEL:"DCP-9045CDN",ID:0x4f9:0x1cb,TYPE:17,2,RE:0x85,WE:0x4 CM:,,
MODEL:"MFC-9840CDW",ID:0x4f9:0x1cc,TYPE:17,1,RE:0x85,WE:0x4 CM:,,
MODEL:"MFC-9640CW",ID:0x4f9:0x1ec,TYPE:17,1,RE:0x85,WE:0x4 CM:,,
MODEL:"MFC-9450CDN",ID:0x4f9:0x20d,TYPE:17,1,RE:0x85,WE:0x4 CM:,,
MODEL:"DCP-9042CDN",ID:0x4f9:0x20c,TYPE:17,2,RE:0x85,WE:0x4 CM:,,
MODEL:"DCP-195C",ID:0x4f9:0x222,TYPE:14,2,RE:0xffff,WE:0xffff CM:,,
MODEL:"DCP-365CN",ID:0x4f9:0x223,TYPE:14,2,RE:0xffff,WE:0xffff CM:,,
MODEL:"DCP-375CW",ID:0x4f9:0x224,TYPE:14,2,RE:0xffff,WE:0xffff CM:,,
MODEL:"DCP-395CN",ID:0x4f9:0x225,TYPE:14,2,RE:0xffff,WE:0xffff CM:,,
MODEL:"MFC-295CN",ID:0x4f9:0x229,TYPE:13,1,RE:0xffff,WE:0xffff CM:,,
MODEL:"MFC-495CW",ID:0x4f9:0x22a,TYPE:13,1,RE:0xffff,WE:0xffff CM:,,
MODEL:"MFC-795CW",ID:0x4f9:0x22c,TYPE:13,1,RE:0xffff,WE:0xffff CM:,,
MODEL:"MFC-255CW",ID:0x4f9:0x228,TYPE:14,1,RE:0xffff,WE:0xffff CM:,,
MODEL:"DCP-390CN",ID:0x4f9:0x236,TYPE:14,2,RE:0xffff,WE:0xffff CM:,,
MODEL:"DCP-595CN",ID:0x4f9:0x227,TYPE:13,2,RE:0xffff,WE:0xffff CM:,,
MODEL:"MFC-495CN",ID:0x4f9:0x22b,TYPE:13,1,RE:0xffff,WE:0xffff CM:,,
MODEL:"MFC-675CD",ID:0x4f9:0x22d,TYPE:14,1,RE:0xffff,WE:0xffff CM:,,
MODEL:"MFC-695CDN",ID:0x4f9:0x22e,TYPE:14,1,RE:0xffff,WE:0xffff CM:,,
MODEL:"MFC-735CD",ID:0x4f9:0x22f,TYPE:14,1,RE:0xffff,WE:0xffff CM:,,
MODEL:"MFC-935CDN",ID:0x4f9:0x230,TYPE:13,1,RE:0xffff,WE:0xffff CM:,,
MODEL:"DCP-8070D",ID:0x4f9:0x21b,TYPE:17,2,RE:0x85,WE:0x4 CM:,,
MODEL:"MFC-8370DN",ID:0x4f9:0x21a,TYPE:17,1,RE:0x85,WE:0x4 CM:,,
MODEL:"MFC-8380DN",ID:0x4f9:0x219,TYPE:17,1,RE:0x85,WE:0x4 CM:,,
MODEL:"MFC-8680DN",ID:0x4f9:0x23f,TYPE:17,1,RE:0x85,WE:0x4 CM:,,
MODEL:"MFC-8880DN",ID:0x4f9:0x216,TYPE:17,1,RE:0x85,WE:0x4 CM:,,
MODEL:"MFC-9120CN",ID:0x4f9:0x21d,TYPE:17,1,RE:0xffff,WE:0xffff CM:,,
MODEL:"MFC-9320CW",ID:0x4f9:0x21c,TYPE:17,1,RE:0xffff,WE:0xffff CM:,,
MODEL:"MFC-9010CN",ID:0x4f9:0x220,TYPE:17,1,RE:0xffff,WE:0xffff CM:,,
MODEL:"DCP-9010CN",ID:0x4f9:0x21e,TYPE:17,2,RE:0xffff,WE:0xffff CM:,,
MODEL:"DCP-145C",ID:0x4f9:0x206,TYPE:14,2,RE:0xffff,WE:0xffff CM:,,
MODEL:"DCP-165C",ID:0x4f9:0x204,TYPE:14,2,RE:0xffff,WE:0xffff CM:,,
MODEL:"DCP-185C",ID:0x4f9:0x205,TYPE:13,2,RE:0xffff,WE:0xffff CM:,,
MODEL:"DCP-385C",ID:0x4f9:0x201,TYPE:14,2,RE:0xffff,WE:0xffff CM:,,
MODEL:"DCP-585CW",ID:0x4f9:0x200,TYPE:14,2,RE:0xffff,WE:0xffff CM:,,
MODEL:"DCP-535CN",ID:0x4f9:0x1ff,TYPE:13,2,RE:0xffff,WE:0xffff CM:,,
MODEL:"MFC-250C",ID:0x4f9:0x1fe,TYPE:14,1,RE:0xffff,WE:0xffff CM:,,
MODEL:"MFC-290C",ID:0x4f9:0x1fd,TYPE:13,1,RE:0xffff,WE:0xffff CM:,,
MODEL:"MFC-490CW",ID:0x4f9:0x1fb,TYPE:13,1,RE:0xffff,WE:0xffff CM:,,
MODEL:"MFC-490CN",ID:0x4f9:0x1fa,TYPE:13,1,RE:0xffff,WE:0xffff CM:,,
MODEL:"MFC-790CW",ID:0x4f9:0x1f9,TYPE:13,1,RE:0xffff,WE:0xffff CM:,,
MODEL:"MFC-990CW",ID:0x4f9:0x1f8,TYPE:13,1,RE:0xffff,WE:0xffff CM:,,
MODEL:"MFC-670CD",ID:0x4f9:0x1f7,TYPE:14,1,RE:0xffff,WE:0xffff CM:,,
MODEL:"MFC-930CDN",ID:0x4f9:0x1f6,TYPE:13,1,RE:0xffff,WE:0xffff CM:,,
MODEL:"MFC-5490CN",ID:0x4f9:0x1f5,TYPE:13,1,RE:0xffff,WE:0xffff CM:,,
MODEL:"MFC-5890CN",ID:0x4f9:0x1f4,TYPE:13,1,RE:0xffff,WE:0xffff CM:,,
MODEL:"DCP-6690CW",ID:0x4f9:0x1f1,TYPE:13,2,RE:0xffff,WE:0xffff CM:,,
MODEL:"MFC-6490CW",ID:0x4f9:0x1f3,TYPE:13,1,RE:0xffff,WE:0xffff CM:,,
MODEL:"MFC-6490CN",ID:0x4f9:0x1f2,TYPE:13,1,RE:0xffff,WE:0xffff CM:,,
MODEL:"MFC-6890CDW",ID:0x4f9:0x1f0,TYPE:13,1,RE:0xffff,WE:0xffff CM:,,
MODEL:"MFC-6890CN",ID:0x4f9:0x1ef,TYPE:13,1,RE:0xffff,WE:0xffff CM:,,
MODEL:"DCP-163C",ID:0x4f9:0x207,TYPE:14,2,RE:0xffff,WE:0xffff CM:,,
MODEL:"DCP-167C",ID:0x4f9:0x208,TYPE:14,2,RE:0xffff,WE:0xffff CM:,,
MODEL:"DCP-383C",ID:0x4f9:0x203,TYPE:14,2,RE:0xffff,WE:0xffff CM:,,
MODEL:"DCP-387C",ID:0x4f9:0x202,TYPE:14,2,RE:0xffff,WE:0xffff CM:,,
MODEL:"MFC-297C",ID:0x4f9:0x1fc,TYPE:13,1,RE:0xffff,WE:0xffff CM:,,
MODEL:"MFC-7450",ID:0x4f9:0x1ee,TYPE:1,1,RE:0x83,WE:0x4 CM:,,
MODEL:"MFC-7840N",ID:0x4f9:0x1ed,TYPE:1,1,RE:0x83,WE:0x4 CM:,,
MODEL:"MFC-7320",ID:0x4f9:0x1eb,TYPE:1,1,RE:0x83,WE:0x4 CM:,,
MODEL:"DCP-7030",ID:0x4f9:0x1ea,TYPE:2,2,RE:0x83,WE:0x4 CM:,,
MODEL:"DCP-7040",ID:0x4f9:0x1e9,TYPE:1,2,RE:0x83,WE:0x4 CM:,,
MODEL:"DCP-7045N",ID:0x4f9:0x1e8,TYPE:1,2,RE:0x83,WE:0x4 CM:,,
MODEL:"MFC-7340",ID:0x4f9:0x1e7,TYPE:1,1,RE:0x83,WE:0x4 CM:,,
MODEL:"MFC-7440N",ID:0x4f9:0x1e6,TYPE:1,1,RE:0x83,WE:0x4 CM:,,
MODEL:"MFC-7840W",ID:0x4f9:0x1e5,TYPE:1,1,RE:0x83,WE:0x4 CM:,,
MODEL:,ID:0x4f9:0xffff,TYPE:35,65535,RE:0xffff,WE:0xffff CM:,,
MODEL:"DCP-8080DN",ID:0x4f9:0x218,TYPE:17,1,RE:0x85,WE:0x4 CM:,,
MODEL:"DCP-8085DN",ID:0x4f9:0x21f,TYPE:17,1,RE:0x85,WE:0x4 CM:,,
MODEL:"MFC-8480DN",ID:0x4f9:0x217,TYPE:17,1,RE:0x85,WE:0x4 CM:,,
MODEL:"MFC-8890DW",ID:0x4f9:0x215,TYPE:17,1,RE:0x85,WE:0x4 CM:,,
-----------------------------
  0 "DCP-197C"
  1 "DCP-377CW"
  2 "MFC-257CW"
  3 "DCP-J715W"
  4 "MFC-J615W"
  5 "DCP-J315W"
  6 "MFC-J265W"
  7 "MFC-J630W"
  8 "DCP-9040CN"
  9 "MFC-9440CN"
 10 "DCP-9045CDN"
 11 "MFC-9840CDW"
 12 "MFC-9640CW"
 13 "MFC-9450CDN"
 14 "DCP-9042CDN"
 15 "DCP-195C"
 16 "DCP-365CN"
 17 "DCP-375CW"
 18 "DCP-395CN"
 19 "MFC-295CN"
 20 "MFC-495CW"
 21 "MFC-795CW"
 22 "MFC-255CW"
 23 "DCP-390CN"
 24 "DCP-595CN"
 25 "MFC-495CN"
 26 "MFC-675CD"
 27 "MFC-695CDN"
 28 "MFC-735CD"
 29 "MFC-935CDN"
 30 "DCP-8070D"
 31 "MFC-8370DN"
 32 "MFC-8380DN"
 33 "MFC-8680DN"
 34 "MFC-8880DN"
 35 "MFC-9120CN"
 36 "MFC-9320CW"
 37 "MFC-9010CN"
 38 "DCP-9010CN"
 39 "DCP-145C"
 40 "DCP-165C"
 41 "DCP-185C"
 42 "DCP-385C"
 43 "DCP-585CW"
 44 "DCP-535CN"
 45 "MFC-250C"
 46 "MFC-290C"
 47 "MFC-490CW"
 48 "MFC-490CN"
 49 "MFC-790CW"
 50 "MFC-990CW"
 51 "MFC-670CD"
 52 "MFC-930CDN"
 53 "MFC-5490CN"
 54 "MFC-5890CN"
 55 "DCP-6690CW"
 56 "MFC-6490CW"
 57 "MFC-6490CN"
 58 "MFC-6890CDW"
 59 "MFC-6890CN"
 60 "DCP-163C"
 61 "DCP-167C"
 62 "DCP-383C"
 63 "DCP-387C"
 64 "MFC-297C"
 65 "MFC-7450"
 66 "MFC-7840N"
 67 "MFC-7320"
 68 "DCP-7030"
 69 "DCP-7040"
 70 "DCP-7045N"
 71 "MFC-7340"
 72 "MFC-7440N"
 73 "MFC-7840W"
 74 
 75 "DCP-8080DN"
 76 "DCP-8085DN"
 77 "MFC-8480DN"
 78 "MFC-8890DW"

Devices on network
ping


```


EDIT: SOLVED!!! Apparently I needed to add all login accounts to the scanner group, as follows...
> 
gpasswd -a username scanner

I hope this is useful to someone else "out there".

---

### Post by fatdadkev on 2011-05-31
Just to add to the replies so far, I'm now on 10.10 (actually 11.04 on some machines but my server is 10.10) and completely forgot about my scanner until this week.

The same instructions seem to be valid, I realize I put one or two basic typing mistakes in my first post so apologies for that.

The Steps I did are to install the Brother files as before (cups driver, brscan etc), xsane does not find the scanner and will give an error message. 
Simple Scan will show the DCP-110C but will give a nice warning message and force you to quit.

The file I needed to edit was 

**/lib/udev/rules.d/40-libsane.rules**


First in terminal type

**lsusb**

This lists the scanner/printer USB ident, in my case it showed

Bus 003 Device 002: ID 04f9:0169 Brother Industries, Ltd DCP-110C RemovableDisk


The bits you need ad the ID 04f9 and 0169.

Next edit the 40-libsane.rules as sudo i.e

**sudo gedit /lib/udev/rules.d/40-libsane.rules**

At the end add the following

#Brother DCP-110c
ATTRS{idVendor}=="04f9", ATTRS{idProduct}=="0169", ENV{libsane_matched}="yes"

Save the file

I just restarted my system to make sure the changes are loaded.

xsane and simple scan both work as expected now.

I think it fair to say there's enough posts on here to get most people working, people have found work around etc for their problems and shared their experiences and this is why Ubuntu succeeds.

It's been more than 5 years since I ran W!nd0wz at home and I still have no need to run it for my day to day tasks.

p.s the scan to file button not working yet on the scanner but since I purchased it I think I've used that twice so it's easier for me to launch xsane or simple scan and do it that way.

I'll perhaps look at it one day .... or not.

---

### Post by Doublehelix22 on 2011-10-15
> **fatdadkev said:**
> .

The file I needed to edit was 

**/lib/udev/rules.d/40-libsane.rules**


First in terminal type

**lsusb**

(snip )

.

[COLOR=Blue]Thanks, that worked a treat for my Brother DCP-J315W and I can scan in Simple Scan and X-sane[/COLOR]

---

### Post by doubtful wisdom on 2011-12-10
My MFC-J430W now scans.  The Brother scanner driver was installed, per instructions on the Brother site.  Ubuntu 11.10 Xsane and Simplescan did not find the scanner.  It was only necessary to determine the equipment ID and add the MFC-J430W just as Doublehelix22 did.  Thank you so much fatdadkev.

---

### Post by Oupadupa on 2012-01-03
Thanks - just used your method to get my Brother MFC-5890CN working. Very quick and easy.

I am using Ubuntu 11.10 and I found the following adjustments were needed.

After forcing the driver  installation

- For Ubuntu 11.10 edit the following file 
**sudo gedit /lib/udev/rules.d/40-libsane.rules**

and add the following two lines between LABEL="libsane_usb_rules_begin"  and LABEL="libsane_usb_rules_end"
[B]# Brother scanners
ATTRS{idVendor}=="04f9", ENV{libsane_matched}="yes"[/B]

If you are using Ubuntu 11.10 then the edit this file.... 
**sudo gedit /lib/udev/rules.d/50-udev-default.rules**

Edit the line
[B]# ENV{DEVTYPE}=="usb_device", MODE="0664", OWNER="root", GROUP="root"

to this

ENV{DEVTYPE}=="usb_device", MODE="0666", OWNER="root", GROUP="root"[/B]


As I'm new to this, I'm not sure what I've done - but I can watch it working :D

---

### Post by snarf77 on 2012-01-11
Hi all,

I'm trying to make my Brother DCP-9010CN work under ubuntu 11.10 (like most you it worked fine with prior install of ubuntu following brother recommendation) and I have the same behaviour as you (Sane or XSane just don't detect the device).

I have tried the fix consisting in declaring the equipment with no luck and I realize after test that it most probably work for usb printer - scanner, right ?

Is there a similar tips for network printer - scanner ? 

Thanks in advance

Snarf77

---

### Post by Adam_GUI on 2012-02-02
> **doubtful wisdom said:**
> My MFC-J430W now scans.  The Brother scanner driver was installed, per instructions on the Brother site.  Ubuntu 11.10 Xsane and Simplescan did not find the scanner.  It was only necessary to determine the equipment ID and add the MFC-J430W just as Doublehelix22 did.  Thank you so much fatdadkev.

Just got home with this exact model printer.
Thanks to you, this thread, and a google search, I have printing working so far.

Kudos.

EDIT: And there's the scanner after reading and following instructions from Oupadupa.

Beautiful.  Thanks all.

---

### Post by jonaypelluz on 2013-04-21
And don't forget to do this in the terminal, after all the solutions I found, my scan started to work wireless after I wrote this on the terminal:

brsaneconfig3 -a name=Brother DCP-J315W model=DCP-J315W ip=192.168.1.16 <-----------

:D

---

