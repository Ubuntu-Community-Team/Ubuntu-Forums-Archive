---
title: "Microtek 4800 scanner"
date: 2009-02-08
forum: Hardware
---

### Post by grashdur on 2009-02-08
Nobody responds to my posts on the relevant thread -- I think because its author has marked it "solved." I remember that on previous rounds of trying to figure out how to make my scanner work again with Ubuntu, someone said that the current 1.0.19 driver doesn't work (with this scanner) and you have to revert back to version 1.0.15. Nobody seems to be able to explain how exactly to do that -- the older version is not in the repositories, and if you look elsewhere on the web all you find are individual files with no instructions for how to fit them together into a finished and working package. 

So, does anybody at least know how to notify the developers of Xsane about this problem? I can't find out from within the program itself, because the program doesn't open without a fully working connection to a scanner.

---

### Post by geraldm on 2009-02-10
If this is a USB scanner, could you post the USB VendorID and ProductID?
The command 'lsusb' should provide this information. 
It may also be available in the /proc/bus/usb/devices file when the device is plugged in.
The device may need to be identified as a scanner first.  After that, xsane may find it.  Does the command "scanimage -L" find it?

If the scanner worked in sane 1.0.15, it is likely that the code would still remain
in newer releases.  From what you wrote, you did not try it yourself ?
Please do not report this as a problem with xsane; they are aware of similar
problems.

regards,
Gerald

---

### Post by cariboo on 2009-02-10
According to the sane database your scanner is marked as working good.

One thing to make of, is to make sure you are a member of the scanner group. Go to System-->Administration-->Users & Groups ansd make sure that you are a part of the scanner group.

It would also help if you posted any error messages you are getting.

> Nobody responds to my posts on the relevant thread -- I think because its author has marked it "solved."

You've done the right thing by starting a new thread.

Jim

---

### Post by grashdur on 2009-02-10
To geraldm: From "lsusb" I get the following output on the scanner: 
Bus 001 Device 005: ID 05da:30cf Microtek International, Inc. ScanMaker 4800

The folder proc/bus/usb is empty. 

Response to the command "scanimage -L" is: 
device `sm3840:libusb:001:005' is a Microtek ScanMaker 4800 flatbed scanner

I didn't understand "From what you wrote, you did not try it yourself ?" But if I'm guessing correctly: I'm not well-versed enough to go into the driver's code and rewrite it. In earlier versions of Ubuntu (I think the versions before Gutsy Gibbon), my scanner worked well with Ubuntu. Since then it hasn't worked any more. 

To cariboo: It's true that my scanner is listed as "good" on the Xsane database, but the database is referring to version 1.0.15. In Hardy Heron and Intrepid Ibex the default version is 1.0.19 (package name "libsane" listed in Synaptic), and this version apparently doesn't work with my scanner. 

I tried adding the relevant users to the "scanner" group, but this didn't help.

Btw, a few weeks ago I was out of town visiting family, and connected my laptop running Ibex to another printer/scanner, and was able to scan with no problems. So my problem must relate specifically to the current version of the driver for my Microtek scanner. 

The error message that I always get is: "Error    Failed to open device 'sm3840:libusb:001:005': Access to resource has been denied." Once I click "Close", the Xsane frontend GUI does not open. This is precisely the same with other scanner programs that I have installed from the repositories. (The number 3840 is because Xsane uses the same driver for the Scanmaker 4800 as for the 3840 -- apparently it's basically the same device.)

I probably have to revert to drivers version 1.0.15, but haven't figured out how to do this.

---

### Post by geraldm on 2009-02-11
Find out the USB bus and device number first.  Then change the group of that device to "scanner"
Bus 001 Device 005: ID 05da:30cf Microtek International, Inc. ScanMaker 4800
Use sudo, or as root 
chgrp scanner /proc/bus/usb/001/005

After that change, see if xsane works.
'sm3840' is part of the library name that the sane backend library loads to use your scanner.  The full name is something like /usr/lib/sane/libsane-sm3840.so.1.0.18 (the number may be different)

There is an alternate method to scan, using scanimage. After your changes adding users to the scanner group, and the device to the scanner group
the scan command would be:

scanimage -dsm3840:001:005 
(other parameters may follow.  See scanimage man page.)

If you do choose to try the above, show any error messages.  Also, the device
should not make any strange noises, or shut it off immediately.

Gerald

---

### Post by grashdur on 2009-02-12
Hi Gerald -- I tried that group change command, and got: 

```
chgrp: cannot access `/proc/bus/usb/001/005': No such file or directory
```

When I tried to open Xsane I got the same error message as usual (as in discussion above).

I tried the scanimage command, and got this response:

```
Segmentation fault
```

---

### Post by geraldm on 2009-02-14
First, my apology for the permissions reply that I provided.  That was the right answer for the older software, but Ibex does not use it, and I do not have Hardy here. 
My objective was to find "scanner" in the menus, and see how to get
the correct permissions set for the "scanner" group, and also get the user
in the scanner group.  So try your hand at getting the user into the 
scanner group.  

Next step is to get the device identified in the group "scanner".
Try this:  plug in your scanner, and issue the command "lsusb"
That should show a list of your devices.  My scanner comes up like this:
Bus 004 Device 004: ID 04a9:2213 Canon Inc. Canoscan LiDE 50/LiDE 35/LiDE 40

Now use the Bus and Device to change the permissions.  Look at all usbdevS by issuing the following command:
"ls /dev/usbdev*"
This should show a list including the scanner device.  Mine shows 4 lines like:
crw-rw---- root root 253,  13 2009-02-14 21,37 /dev/usbdev4.4_ep00

You can see that the Bus 004 and Device 004 comes out as "4.4", so I would issue the command using "4.4" like this:
"sudo chgrp scanner /dev/usbdev4.4*"

After that, issue 
"sane-find-scanner"
It should show your scanner.  If it does, try xsane again.

Your scanner should work as Ibex has it.  You do not need to revert to the older version 1.0.15, with patches.  

regards,
Gerald

---

### Post by grashdur on 2009-02-15
Hi Gerald: I was able to add all users to the "scanner" group earlier, with System > Administration > Users & Groups. 

I'm still not getting anywhere, even though the scanner was apparently "found". Here is what happened: 

```
grashdur@Gateway3:~$ lsusb
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 004: ID 05da:30cf Microtek International, Inc. ScanMaker 4800
Bus 001 Device 003: ID 058f:9360 Alcor Micro Corp. 8-in-1 Media Card Reader
Bus 001 Device 002: ID 0d8c:000c C-Media Electronics, Inc. Audio Adapter
Bus 001 Device 001: ID 0000:0000  
grashdur@Gateway3:~$ ls /dev/usbdev*
/dev/usbdev1.1_ep00  /dev/usbdev1.3_ep01  /dev/usbdev1.4_ep83
/dev/usbdev1.1_ep81  /dev/usbdev1.3_ep82  /dev/usbdev2.1_ep00
/dev/usbdev1.2_ep00  /dev/usbdev1.4_ep00  /dev/usbdev2.1_ep81
/dev/usbdev1.2_ep83  /dev/usbdev1.4_ep02
/dev/usbdev1.3_ep00  /dev/usbdev1.4_ep81
grashdur@Gateway3:~$ sudo chgrp scanner /dev/usbdev1.4*
[sudo] password for grashdur: 
grashdur@Gateway3:~$ sane-find-scanner

  # sane-find-scanner will now attempt to detect your scanner. If the
  # result is different from what you expected, first make sure your
  # scanner is powered up and properly connected to your computer.

  # No SCSI scanners found. If you expected something different, make sure that
  # you have loaded a kernel SCSI driver for your SCSI adapter.

found USB scanner (vendor=0x05da, product=0x30cf) at libusb:001:004
  # Your USB scanner was (probably) detected. It may or may not be supported by
  # SANE. Try scanimage -L and read the backend's manpage.

  # Not checking for parallel port scanners.

  # Most Scanners connected to the parallel port or other proprietary ports
  # can't be detected by this program.

  # You may want to run this program as root to find all devices. Once you
  # found the scanner devices, be sure to adjust access permissions as
  # necessary.
```

Still, when I try to open Xsane I get the usual error message, 

> Error Failed to open device 'sm3840:libusb:001:005': Access to resource has been denied.

---

### Post by cariboo on 2009-02-15
Just out of curiosity have you tried running Xsane as root? Press Alt-F2 and type:

```
gksu xsane
```

You will get a message saying that is dangerous to run as as root, just click continue at your own risk, and see if you can scan.

Jim

---

### Post by geraldm on 2009-02-15
I think the device was opened and closed while it was Bus 001 Device 004
It disconnected, and reconnected, and then became Bus 001 Device 005
The command failed because the permissions on the device would then be
root root

What may be needed is to get the device identified by UDEV as a scanner, and
set the group to "scanner" and the group permissions to rw-
Then there would be no permissions problem, and no need to run as root.
Add this line to have Ibex recognize the scanner by vendor and product ID
After that, then plug in the scanner, and it should show group scanner.
# append  to file: /etc/udev/rules.d/40-permissions.rules
# lsusb returns for Microtek 4800 scanner: ID 05da:30cf 
ATTRS{idVendor}=="05da", ATTRS{idProduct}=="30cf", MODE="0660", GROUP="scanner"


Also note an error in my previous post.  
"ls /dev/usbdev*" <- posted
"ls -l /dev/usbdev*" <- corrected.  From the displayed difference, this is obvious.

Regards,
Gerald

---

### Post by grashdur on 2009-02-16
Hi cariboo: I tried to open XSane as root like you suggested -- but still got the same old error message:

> Error Failed to open device 'sm3840:libusb:001:005': Access to resource has been denied. 

Hi Gerald: If root can't run the scanner, then your suggestion in your last post doesn't apply. Or am I wrong?

---

### Post by geraldm on 2009-02-16
You still need to change the file /etc/udev/rules.d/40-permissions.rules 
by appending the rule to recognize the scanner so that the group will get
set correctly.
The only reason that access would be denied would be that the device is still in use.  Only one app can access at a time.
You may need to unplug/replug after the file change.
Try again.

---

### Post by grashdur on 2009-02-16
Hi Gerald: Thanks for persisting with this. I followed this instruction:

# append to file: /etc/udev/rules.d/40-permissions.rules

```
# lsusb returns for Microtek 4800 scanner: ID 05da:30cf
ATTRS{idVendor}=="05da", ATTRS{idProduct}=="30cf", MODE="0660", GROUP="scanner"
```

And then I plugged the scanner in, and tried to open XSane. Interesting: This time I got a different error message: A little message box popped up saying:

> No devices available.

---

### Post by geraldm on 2009-02-16
The code I posted worked here in Ibex.  xsane starts here by popping the "scanning for devices", finds the scanner, and is then ready for work.

It appears that something went wrong with setting the group scanner permissions.  Review the code below on your system.  Check carefully to confirm that the group for the device is set to "scanner".  I suspect that is where it fails.

I followed this procedure:
I start with the live disk.
(on your system the user is to be in the "scanner" group)
make the change to /etc/udev/rules.d/40-permissions.rules # using ID

code:
# -- test checks --
grep scanner /etc/group  # user is to be in the scanner group
tail -n1 /etc/udev/rules.d/40-permissions.rules # scanner to identify
ls /usr/lib/sane/libsane-sm3840.so.1.0.1* # check for backend you are using
ls /etc/sane.d/sm3840.conf  # check for necessary backend aid

# Plug in the scanner's usb connection here.
lsusb # Find out the bus and device number

ls -l /dev/usbdev4.3* # (use your Bus Device numbers that were just returned)
# Confirm that the device is owned by root, group is "scanner", rw- <-- IMPORTANT

# start xsane &
/code

regards,
Gerald

---

### Post by cgate on 2009-02-18
I'm also trying to get this same scanner running on Hardy.  I've made the entry in /etc/udev/rules.d and and added my user to the scanner group. ls -l gives:
crw-rw-r-- 1 root scanner 254, 10 2009-02-18 07:48 /dev/usbdev1.6_ep00
crw-rw-r-- 1 root scanner 254, 12 2009-02-18 07:48 /dev/usbdev1.6_ep02
crw-rw-r-- 1 root scanner 254, 11 2009-02-18 07:48 /dev/usbdev1.6_ep81
crw-rw-r-- 1 root scanner 254, 13 2009-02-18 07:48 /dev/usbdev1.6_ep83
I continue to get the same error: Access to resource has been denied

I tried opening each of the 4 devices from a c program as root and got an errno of 6: ENXIO - file is a device special file and no corresponding device exists.

Any clues from this?

- Chris

---

### Post by geraldm on 2009-02-18
cgate:
It looks good.  Try the xsane app, and see if looks workable, or gives error message.

Using a C program is unlikely to work unless you also observe the USB protocol,
which is available in libusb package.  As part of the protocol, the driver (perhaps)
must set the configuration, grab the device interface, and then can use the device.  The sane-backends package has the protocol in use, as an example.
If you are just trying to learn to work with a USB device, it should be possible to
find a simpler device to work with than the sane-backends.  I just do not have
a ready example of simplicity.

You might also want to try "scanimage -L" command to see if the device responds.  I think it is easiest to try xsane, as it is easier when the work is 
mostly done ? 

Gerald

---

### Post by cgate on 2009-02-19
Gerald,



Here's what I'm getting (all run from root):



ls -l /dev/usbdev*

crw-rw-r-- 1 root scanner 254, 10 2009-02-19 07:17 /dev/usbdev1.2_ep00

crw-rw-r-- 1 root scanner 254, 12 2009-02-19 07:22 /dev/usbdev1.2_ep02

crw-rw-r-- 1 root scanner 254, 11 2009-02-19 07:22 /dev/usbdev1.2_ep81

crw-rw-r-- 1 root scanner 254, 13 2009-02-19 07:22 /dev/usbdev1.2_ep83



lsusb

Bus 001 Device 002: ID 05da:30cf Microtek International, Inc. ScanMaker 4800



scanimage -L

device `sm3840:libusb:001:002' is a Microtek ScanMaker 4800 flatbed scanner



scanimage >tmp/test.pnm

scanimage: open of device sm3840:libusb:001:002 failed: Access to resource has been denied



xsane gives the same error as scanimage.



I tried opening these devices from C (with no intention of any i/o) hoping for a more specific error but I see this was a bit naive - more complicated usb configuration is required.  If you have C code using libusb that might reveal something, I'd be happy to try it.



All I really want is to get this scanner working for my brother - I recently set him up with Ubuntu.  I've been very happy with Ubuntu on other machines but his has been a struggle!



- Chris

---

### Post by cgate on 2009-02-19
Gerald,

This may or may not be useful.  I used strace with scanimage.  One thing of interest is there was no indication it used /dev/usbdev1.* but did use /dev/bus/usb/001/00? .

The last of the strace output (before a series of munmap's and exit) was this:

open("/dev/bus/usb/001/002", O_RDWR)    = 11
ioctl(11, USBDEVFS_SETCONFIGURATION, 0xbfd44544) = 0
ioctl(11, USBDEVFS_CLAIMINTERFACE, 0xbfd44544) = 0
write(2, "scanimage: open of device sm3840"..., 91) = 91

I would think the USBDEVFS_CLAIMINTERFACE ioctl must have returned some failure status.

- Chris

---

### Post by grashdur on 2009-02-19
This is getting a little complicated for me to follow (and your discussion with cgate is totally over my head), so I'd like to go over these steps with you before I proceed:

> Check carefully to confirm that the group for the device is set to "scanner".  I suspect that is where it fails.

Does the procedure below include this? If not, then I don't know how to set a group for the device. 

> I followed this procedure:
I start with the live disk.
(on your system the user is to be in the "scanner" group)
make the change to /etc/udev/rules.d/40-permissions.rules # using ID

Just curious: Why with the live disk? And if I've made those changes on my system already, do the new changes go into a temporary live-disk version of the file? And if I succeed in using my scanner using Live Disk, I would then try to do the same thing without Live Disk?

> code:
# -- test checks --
grep scanner /etc/group  # user is to be in the scanner group
tail -n1 /etc/udev/rules.d/40-permissions.rules # scanner to identify
ls /usr/lib/sane/libsane-sm3840.so.1.0.1* # check for backend you are using
ls /etc/sane.d/sm3840.conf  # check for necessary backend aid

I assume these are all done in Terminal, while still in the Live-CD version of Ubuntu. I do understand that the parts after the "#" are just your comments to me here.

> # Plug in the scanner's usb connection here.
lsusb # Find out the bus and device number

So while still in Live CD, at this point I plug in my scanner. (?)

> ls -l /dev/usbdev4.3* # (use your Bus Device numbers that were just returned)

Here I get lost: to use my bus device numbers here, there must be some particular format or code with which I do this -- maybe this was posted earlier in our discussion but right now I'm not finding it. 

> # Confirm that the device is owned by root, group is "scanner", rw- <-- IMPORTANT

This is all information that will be returned after I enter that last command. Right?

> # start xsane &
/code

I still stay in Live CD at this point, right? 

And I think that "/code" means it's the end of the steps you're offering in this posting, not something I type in Terminal. Right?

---

### Post by geraldm on 2009-02-20
grashdur:
The instructions that I have posted are from a live Ubuntu DVD, Linux Magazine Pro, January 2009.  Your system is installed, so you do not have to enter some of the instructions more than once.  With the live DVD, the instructions are needed each time the system starts.  I have tried to be very careful to include all the instructions I used to obtain the preview scan from xsane.
The procedure should be the same, whether using live DVD or installed.
I do not use installed here because I do not have available space on the hard disk yet.

lsusb # This instruction is needed to discover the Bus and Device numbers that were assigned to the scanner.  If you already know them, this instruction is not needed.  The bus and device numbers have leading zeroes.

ls -l /dev/usbdev4.3* # The format strips leading '0' zeroes from the Bus and Device numbers that "lsusb" returned for the scanner.

# Confirm ... It is necessary to confirm that the permissions were actually changed because when xsane begins, it reports that "Access to resource has been denied. -- which usually means a permissions problem.

# /code <- This is my blunder.  The older forum format had two sentinals surrounding a code block, and formatted the block for display.  I have since forgotten the correct spelling of the sentinals.


cgate:
/dev/bus/usb/001/00? <-- be careful here.  In the development of USB drivers it was necessary to find a way to assign permissions to a device.  Developers then used a filesystem "usbfs".  This filesystem had a line entry in /etc/fstab and it had to be mounted at /proc/bus/usb.  It supplied a file "devices" and had subdirectories for bus, and another for the devices on that bus.  This filesystem needed to have the group permissions named "scanner" for scanner programs to use the device.


From the strace you displayed, the USSBDEVFS_CLAIMINTERFACE succeeded.  Upon the open of the device, there was an error 91, which means an EPROTOTYPE error, the protocol was the wrong type for the socket.

forum post #17 - This is what I expected, and shows similar to what works in my system.

forum post #18 - This might be the needed clue.  If you have any devices under directory /dev/bus/usb/ then it is necessary to see if there is a scanner device in it.
The Bus and Device numbers would be the same numbers returned by "lsusb" for the scanner.
If there is, change group to "scanner" and access to read/write.  This might be tne reason for the Access to resource has been denied.  Try xsane again after the change.

Gerald

---

### Post by cgate on 2009-02-21
Gerald,

Here's what I'm getting now:

lsusb
Bus 001 Device 003: ID 05da:30cf Microtek International, Inc. ScanMaker 4800

ls -l /dev/bus/usb/001/
crw-rw-r--  1 root root    189, 0 2009-02-20 05:04 001
crw-rw-r--+ 1 root scanner 189, 2 2009-02-20 05:04 003

strace -otmp/scan.txt scanimage >tmp/test.pnm
scanimage: open of device sm3840:libusb:001:003 failed: Access to resource has been denied

tmp/scan.txt:
open("/dev/bus/usb/001/003", O_RDWR)    = 11
ioctl(11, USBDEVFS_SETCONFIGURATION, 0xbfa13a14) = 0
ioctl(11, USBDEVFS_CLAIMINTERFACE, 0xbfa13a14) = 0
write(2, "scanimage: open of device sm3840"..., 91) = 91

I think what's happening here is:

1. The open() syscall is succeeding  (returns file descriptor 11)

2. The 2 ioctl() syscalls are succeeding but USBDEVFS_CLAIMINTERFACE must be returning some sort of failure information

3. The write() syscall is to standard error 2 and it is writing the message we see; 91 is just the length of the message.

- Chris

---

### Post by grashdur on 2009-02-21
Hi Gerald: 

So I appended those lines to /etc/udev/rules.d/40-permissions.rules, then did the following in Terminal:

```
grashdur@Gateway3:~$ lsusb
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 005: ID 05da:30cf Microtek International, Inc. ScanMaker 4800
Bus 001 Device 004: ID 058f:9360 Alcor Micro Corp. 8-in-1 Media Card Reader
Bus 001 Device 003: ID 0d8c:000c C-Media Electronics, Inc. Audio Adapter
Bus 001 Device 002: ID 03f0:0317 Hewlett-Packard LaserJet 1200
Bus 001 Device 001: ID 0000:0000  
grashdur@Gateway3:~$ grep scanner /etc/group
scanner:x:105:hplip,ellsworth,grashdur,root
grashdur@Gateway3:~$ tail -n1 /etc/udev/rules.d/40-permissions.rules

grashdur@Gateway3:~$ ls /usr/lib/sane/libsane-sm3840.so.1.0.1*
/usr/lib/sane/libsane-sm3840.so.1.0.19
grashdur@Gateway3:~$ ls /etc/sane.d/sm3840.conf
/etc/sane.d/sm3840.conf
grashdur@Gateway3:~$ ls -l /dev/usbdev4.3*
ls: cannot access /dev/usbdev4.3*: No such file or directory
```

Everything looked fine until that last response. Perhaps I did something wrong here. But I tried Xsane anyway to see what happens, and got my usual message, "Access to resource is denied." I did this in my grashdur (administrative) account, which is listed above as having access.

---

### Post by DocEsq on 2009-02-21
grashdur:

As I mentioned in my post I am getting the same error message that you are.  Using the "lsusb" command my scanner is identified.

As I had mentioned my research has indicated that I need to revert to SM3840,so,1.0.15 and then install the patch.
[http://www.ziplabel.com/sm3840/index.html](http://www.ziplabel.com/sm3840/index.html)
and
[https://bugs.launchpad.net/ubuntu/+source/sane-backends/+bug/115898](https://bugs.launchpad.net/ubuntu/+source/sane-backends/+bug/115898)

I am not exactly sure how to go about all of this, even installing the patch, as I am a novice when it comes to Ubuntu.

I have read in more than one place that there is a bug with SM3840 versions after 1.0.15 so I am thinking that reverting is the way to go.  I think the permission problem is due to the SMS3840 version that is installed which is preventing Ubuntu from properly identifying the scanner and providing the right permissions.

So how do I step by step go about installing SM3840,so,1.0.15 and the patches?

---

### Post by geraldm on 2009-02-21
cgate:
You are right.  I did not expect the code to fail at that point.
The sane-backend has separate parts, one part for the common (for all backends) and various backends, which support groups of scanners.  The instruction to claim the USB interface is in the common part, so I expected that to work for most of the scanners.

grashdur:
You were to use the "lsusb" command to identify YOUR Bus and Device number for t
he scanner.  It returned Bus 001 Device 005.  Then use these numbers for the "ls
 -l /dev/usbdev1.5* 
Your 40-permissions.rules file has a blank line at the end.  Either edit that li
ne out, or use "tail -n2 <filepath>" to show the last two lines. 

--:
I have downloaded the 1.0.19 code, and will look a bit into the sm3840 backend over the weekend.

Gerald

---

### Post by grashdur on 2009-02-22
Hi DocEsq: Looks like we're in the same boat, both regarding our scanner problem and our confusion of what to do next. I came across that link you provided some time ago and then misplaced it. When people say, "Just copy this to over there, and install that..." I'm usually lost as to where the files are located what specific commands to use.

---

### Post by grashdur on 2009-02-22
Hi Gerald: Okay, deleted the blank line. Still getting the same error message from XSane.

I wanted to know what format or wording to write the device and bus numbers for that command. I probably was unclear. When you didn't respond to that I thought you meant I don't type it there, but just look for that in the response to the command.

So:
```
grashdur@Gateway3:~$ ls -l /dev/usbdev4.3* bus 1 device 5
ls: cannot access /dev/usbdev4.3*: No such file or directory
ls: cannot access bus: No such file or directory
ls: cannot access 1: No such file or directory
ls: cannot access device: No such file or directory
ls: cannot access 5: No such file or directory
```

That link that DocEsq mentioned -- [https://bugs.launchpad.net/ubuntu/+s...ds/+bug/115898]("https://bugs.launchpad.net/ubuntu/+s...ds/+bug/115898") -- is interesting: I came across it some time ago, but when looking for it this time I couldn't locate it. It looks promising as a fix, but the discussion in it is somewhat above my level of knowledge so I haven't been able to apply it.

---

### Post by DocEsq on 2009-02-23
With nothing better to do at work I performed a google search and found a German post of the same problem.

The translated version through google is [http://translate.google.com/translate?hl=en&sl=de&u=http://forum.ubuntuusers.de/post/1131723/%3Fhighlight%3Dsan&ei=chKjSZ_4I4_ftgfm49CVDQ&sa=X&oi=translate&resnum=1&ct=result&prev=/search%3Fq%3DSM3840,so,1.0.15%2Bdeb%26start%3D10%26hl%3Den%26rls%3DGGGL,GGGL:2006-18,GGGL:en%26sa%3DN](http://translate.google.com/translate?hl=en&sl=de&u=http://forum.ubuntuusers.de/post/1131723/%3Fhighlight%3Dsan&ei=chKjSZ_4I4_ftgfm49CVDQ&sa=X&oi=translate&resnum=1&ct=result&prev=/search%3Fq%3DSM3840,so,1.0.15%2Bdeb%26start%3D10%26hl%3Den%26rls%3DGGGL,GGGL:2006-18,GGGL:en%26sa%3DN)

The original version is [http://forum.ubuntuusers.de/topic/microtek-scanmaker-4800-funktioniert-nicht-un/?highlight=san#post-1131723](http://forum.ubuntuusers.de/topic/microtek-scanmaker-4800-funktioniert-nicht-un/?highlight=san#post-1131723)

The relevant post states:
"I had the same problem and could solve it as follows

It seems the libsane-sm3840.so.1.0.17 responsible for the problem, since the libsane-sm3840.so.1.0.15 the scanner works Scanmaker 4800.

I have at http / / packages.debian.org/de/sarge/i386/libsane-extras/download me the file libsane-extras_1.0.15.9_i386.deb downloaded.

Then open File Roller, and there data.tar.gz open the file libsane-sm3840.so.1.0.15 unpacked.

The file in this directory

/ usr / lib / sane

Now open a terminal window up and down following commands 
sudo rm libsane-sm3840.so.1

and

sudo ln-s libsane-sm3840.so.1.0.15 libsane-sm3840.so.1

Then ran the Microtek Scanmaker 4800 re 1a!

I came out with the following article

https / / bugs.launchpad.net / ubuntu / + source / sane-backends / + bug/115898/comments/6

Have fun scanning"


Note that this may not be an exact translation but it seems that we will have to install the previous backend.

This is the best set of directions I have found.  If anyone knows of a better way please post.  Also let us know if the translation is correct.

Doc

---

### Post by grashdur on 2009-02-23
Woo-hoo!! :guitar: Great use of your idle time, Doc! That solution you found really worked for me! Now I can scan!!! :p :p

I know German, so I could use the posting you found. There were a couple of shortcomings/mistakes in that posting, but I was able to resolve them. Here is my translation, with my corrections added in square brackets:

==========================

I had the same problem and was able to solve it in the following way[:]

Apparently libsane-sm3840.so.1.0.17 is responsible for the problem, since with libsane-sm3840.so.1.0.15 the scanner Scanmaker 4800 works. 

At http//packages.debian.org/de/sarge/i386/libsane-extras/download I downloaded the file libsane-extras_1.0.15.9_i386.deb. [The colon : is missing from the web address, but the address is no longer valid anyway as a location for that file. On Google I found a current place from which you can download it: [http://ftp.kaist.ac.kr/debian-archive/pool/main/s/sane-backends-extras/]("http://ftp.kaist.ac.kr/debian-archive/pool/main/s/sane-backends-extras/")] 
Then opened it with File Roller [that's probably the Archive Manager], there opened data.tar.gz and unpacked the file libsane-sm3840.so.1.0.15 [inside that file it can be found at this path: /./usr/lib/sane].

Then copy the file into the following directory[:]

/usr/lib/sane

Now open a Terminal window and put the following commands on a line[:]

[For relative n00bs like myself, I add the following necessary instruction before the next one the German user gives: 
```
cd /usr/lib/sane
```
So, continuing:]

```
sudo rm libsane-sm3840.so.1
```

and

```
sudo ln -s libsane-sm3840.so.1.0.15 libsane-sm3840.so.1
```

After that the Microtek Scanmaker 4800 again ran gr8!

I came across this in the following article[:]

https//bugs.launchpad.net/ubuntu/+source/sane-backends/+bug/115898/comments/6

[Instead of that address, try [https://bugs.launchpad.net/ubuntu/+source/sane-backends/+bug/115898]](https://bugs.launchpad.net/ubuntu/+source/sane-backends/+bug/115898])

Have fun scanning.

==============================

{posting by listless on German Ubuntu Forums: link http://forum.ubuntuusers.de/topic/microtek-scanmaker-4800-funktioniert-nicht-un/?highlight=san#post-1131723}

By the way: In another ten years, cheap or free software is going to put professional translators out of work!

Also: How do I mark this post as SOLVED?

---

### Post by DocEsq on 2009-02-23
I must be doing something wrong as I can not get it to work.

I downloaded the file and tried to use the GDebi Package Installer but got an error message when I did.  I then found another libsane-extras_1.0.15.9_i386.deb. on the internet which opened correctly.

I then looked for and found libsane-sm3840.so.1.0.15 in /usr/lib/sane (I never did see the data.tar.gz)

I then entered:
cd /usr/lib/sane

followed by:
sudo rm libsane-sm3840.so.1

and

sudo ln -s libsane-sm3840.so.1.0.15 libsane-sm3840.so.1

It all seemed to work well until I then clicked on Xsane Image Scanner I kept getting that it was searching for the scanner.  I had to force quit this after about 20 min.

I then decided to see if the original libsane-extras_1.0.15.9_i386.deb from the link would now work and it did.  I then followed the commands for the terminal window and when I entered:
sudo rm libsane-sm3840.so.1
I got a message that there was no file to remove.

I continued any way and Xsane Image Scanner and the Scanner utility would both hang while finding the scanner.  

After force quitting I then saw that I could update to libsane-extras_1.0.18 from the update manager.  At this point I figured that I had nothing to loose since the scanner was not working any way.  It all seemed to download and install properly but again I get that the programs are searching for the scanner and I have to force quit.

I am not sure what I need to do at this point so any help would be great

---

### Post by grashdur on 2009-02-24
Sorry, Doc, I steered you wrong in one crucial detail: When "lustlos" in the German posting mentioned the "File Roller," I think he meant the *Archive Manager*. Just now I corrected that in my last post, for the benefit of anyone else who might read it. So if you've downloaded the file libsane-extras_1.0.15.9_i386.deb and it's sitting on your desktop, what I do is right-click on it for "Open with..." and I choose "Archive Manager" -- Ubuntu's utility for extracting zipped archive files. So I go in, find libsane-sm3840.so.1.0.15, and just click on it to extract it (I just put on on the desktop). 

More details, just in case it's useful to you or anybody else: At this point you can press ALT-F2, and in the little window that pops up, type "gksu nautilus" -- which will open a copy of the Nautilus file browser, but with root privileges. Then you can paste the file in the required folder. 

Also: When you did your second try, did you first say cd /usr/lib/sane before those two commands? That's necessary, otherwise the computer will look for the file in the wrong folder, and not find it.

So you can try it with the copy of the file you downloaded from somewhere else, or with the file I downloaded and gave a link to. Perhaps there's a difference, or perhaps not.

I hope it'll work out easily for you at this point. If not, I'll try to help further.

---

### Post by DocEsq on 2009-02-25
Thanks grashdur.

I got it to work.  The problem was that I had not used *Archive Manager*  so I could not see the data file I needed to extract to the desktop.  I also needed press ALT-F2, and type "gksu nautilus" so that I can then have root privileges so as to paste libsane-sm3840.so.1.0.15 into /usr/lib/sane.  After that I just followed the rest of the directions.

Scanner Utility, XSane Image Scanner and gscan2pdf all work now.

Having the scanner work allows me to use XP even less than I was doing.

The directions for what we did should be posted as a sticky or How To somewhere as I am sure that there are a lot of other people having the same problem.

My only question now is how do I set the ScanMaker 4800 so that the bulb turns off after a certain period of time?

---

### Post by grashdur on 2009-02-26
I have no clue on the bulb-sleep issue. 

I also have no idea how to mark this thread as "solved" or to make it into a sticky thread. 

But it's so great to be able to use my scanner again without having to reboot into Windows! We solved it!

---

### Post by samfatboy on 2009-03-24
Will they ever update the libsane-extras sm3840 to correct the drivers for Microtek Scanners?  

Thanks to this forum I was able to follow the instructions to replace the current 1.0.19.7 version with the old 1.0.15 version in order to make my scanner work, but it is kind of a hassle to have the update manager constantly tell me that updates are available.  What would really aggravate me would be if in a less defensive state I forget to uncheck the libsane update and re-load 1.0.19 again.

---

### Post by grashdur on 2009-03-24
I have absolutely no idea how to report it, or to whom. The Help Menu in Xsane leads me only to dead links. The Xsane website is for the Xsane project, not Ubuntu, and as I recall it only shows the older, correctly-functioning driver. 

This problem has already gone unfixed in several versions of Ubuntu.

Though so far, although I've been watching out for them, I have not been receiving any (unwanted) updates on XSane. I don't know why it's any different for me.

---

