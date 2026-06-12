---
title: "Kodak ESP 3250"
date: 2013-03-08
forum: Hardware
---

### Post by CK000 on 2013-03-08
I have a Kodak ESP 3250 and everything works, but the scanner. None of the programmes I have downloaded from the software centre seem to recognise it at all as a scanner. 

I apologise if this has already been posted, but does anyone know how to get this (printer) scanner (copier) to work fully on Ubuntu 12.04 please.

Thank you very much in advance.

---

### Post by paulnewall on 2013-03-08
see instructions here
[http://sourceforge.net/projects/cupsdriverkodak/files/Scanning%20-%20sane%20backend/]("http://sourceforge.net/projects/cupsdriverkodak/files/Scanning%20-%20sane%20backend/")
ubuntu 12.04 should already have a version of sane that supports the scanner.
Try following the section on testing / permissions / troubleshooting.
If that is not sucessful, you could try installing sane from git.

---

### Post by CK000 on 2013-03-08
Hello, and many thanks for your reply. I have read and followed these instructions (or at least tried to follow them) but my scanner is still not recognised. Perhaps I have done something wrong, I am not sure, but I must confess I am rather a newbie still. 

I wonder if you (or anyone else) could walk me through this please.

Many thanks in advance.

---

### Post by paulnewall on 2013-03-09
It's one of the difficulties with sane, that it is quite hard to set up and debug.
Step one is to confirm your setup:
You have ESP 3250 is that connected via usb or WiFi? apologies if that model does not have WiFi I can't remember which model has what features.

Step two is to try and see if linux can actually see the device is connected:
Since you can print, You should expect success, but it's worth going through the whole process.

If it is usb, open a terminal and try
    sudo sane-find-scanner
You should see the device listed. If it is listed, also try without the sudo
    sane-find-scanner
Do you still see it listed?

If it is WiFi, get the IP address from the menus on the printer. (Mine is 192.168.1.3)
Open a terminal and try (using your printer's IP address)
    ping 192.168.1.3
use control-c to stop the ping
if the device is found you get replies like
    PING 192.168.1.3 (192.168.1.3) 56(84) bytes of data.
    64 bytes from 192.168.1.3: icmp_req=1 ttl=64 time=2.95 ms
if the device is not found you get
    PING 192.168.1.3 (192.168.1.3) 56(84) bytes of data.
    ^C
    --- 192.168.1.3 ping statistics ---
    14 packets transmitted, 0 received, 100% packet loss, time 13104ms

---

### Post by CK000 on 2013-03-10
Hello, and many thanks for your detailed and extensive reply. The ESP 3250 is certainly not wi-fi, so we do not need to worry about that.

I have tried editing the configuration file and trying the command you suggested in the terminal. The scanner does show up to an extent with that command, but I get messages which say no scanner detected. However I obtained some details to edit the configuration file but when I use any scanner programme it is not detected. Also it does not show up to the extent I think it should with that command.

---

### Post by paulnewall on 2013-03-10
Can you paste the output from sane-find-scanner into a reply?
If sane-find-scanner detects the scanner, the next step (I'd call it step 3) would be to try (again in a terminal)
sudo scanimage -L
does that detect the scanner?
Paste the output into a reply.

---

### Post by CK000 on 2013-03-12
This is the output from sane-find-scanner

ck@ck-eM250:~$ sane-find-scanner

  # sane-find-scanner will now attempt to detect your scanner. If the
  # result is different from what you expected, first make sure your
  # scanner is powered up and properly connected to your computer.

  # No SCSI scanners found. If you expected something different, make sure that
  # you have loaded a kernel SCSI driver for your SCSI adapter.

found USB scanner (vendor=0x040a, product=0x4043) at libusb:001:003
  # Your USB scanner was (probably) detected. It may or may not be supported by
  # SANE. Try scanimage -L and read the backend's manpage.

  # Not checking for parallel port scanners.

  # Most Scanners connected to the parallel port or other proprietary ports
  # can't be detected by this program.

  # You may want to run this program as root to find all devices. Once you
  # found the scanner devices, be sure to adjust access permissions as
  # necessary.

And the results for the second command you kindly provided are:-

ck@ck-eM250:~$ sudo scanimage -L

No scanners were identified. If you were expecting something different,
check that the scanner is plugged in, turned on and detected by the
sane-find-scanner tool (if appropriate). Please read the documentation
which came with this software (README, FAQ, manpages).

---

### Post by paulnewall on 2013-03-12
So sane-find-scanner gave us a normal response. The scanner is communicating trough the usb system OK.
Next we have to get scanimage to work. I'll post more soon.

---

### Post by paulnewall on 2013-03-12
Getting scanimage -L to work :

Look at the file: /etc/sane.d/dll.conf
It has a line for each backend. Some lines may be commented out by starting with a #
Check there is a line for kodakaio, which does not start with # like this:
**kodakaio**

Look at the file /etc/sane.d/kodakaio.conf
If it does not exist, you probably do not have the kodakaio backend installed.
This file needs to have a line which just says
**usb**
that should allow any usb connected that is supported to work

now open a terminal, and enter
[B]export SANE_DEBUG_KODAKAIO=10
sudo scanimage -L
[/B]the debug value enables debug messages, which should indicate whether the kodakaio backend is running and why it might not be detecting the scanner.
copy the results of that into a post here.

---

### Post by CK000 on 2013-03-12
Hello, and many thanks for your post a few minutes ago.
I have checked the two configuration files you mentioned and edited the first one adding in a line for 'kodakaio'. Incidentally there is already a line which says 'kodak'.

The second file already has a line which simply says **usb **as you mention it should.

I am about to open the terminal and try the last part of your post this is the output:

ck@ck-eM250:~$ export SANE_DEBUG_KODAKAIO=10
ck@ck-eM250:~$ sudo scanimage -L
device `kodakaio:libusb:001:003' is a Kodak KODAK ESP 3200 Series AiO flatbed scanner
ck@ck-eM250:~$

---

### Post by paulnewall on 2013-03-12
Now sudo scanimage -L seems to detect the scanner
Try scanimage -L
 (that's without the sudo)
If that detects the scanner, any other scan program should work too

---

### Post by CK000 on 2013-03-12
Hello, and thank you once again for your help and detailed replies. 

This is the output from the command without the sudo:-

ck@ck-eM250:~$ scanimage -L

No scanners were identified. If you were expecting something different,
check that the scanner is plugged in, turned on and detected by the
sane-find-scanner tool (if appropriate). Please read the documentation
which came with this software (README, FAQ, manpages).
ck@ck-eM250:~$

So, I deduce the scanner is not being fully detected, certainly scan2pdf still does not work for example.

---

### Post by paulnewall on 2013-03-13
Setting permissions for a usb connection
======================================== 
If you can scan as root, but not as user, you have a permissions issue.  
Current Ubuntu releases use udev to set permisions. Some previous  releases used HAL. 
To set permissions for udev:  
look for a file something like /etc/udev/rules.d/90-libsane.rules
edit it as root, for example by typing
**gedit /etc/udev/rules.d/90-libsane.rules**
in a terminal
 add the following  two lines
[B]# Kodak ESP 3200
ATTRS{idVendor}=="040a", ATTRS{idProduct}=="4043", MODE="0664", GROUP="scanner", ENV{libsane_matched}="yes"
[/B]
 Save the file, exit your text editor and try
**scanimage -L**
again
If it works, scanning software like simple-scan should work.

---

### Post by CK000 on 2013-03-13
Thank you once again for your reply. I have edited the file accordingly, however the output from the command:

**scanimage -L**

is still:-

ck@ck-eM250:~$ scanimage -L

No scanners were identified. If you were expecting something different,
check that the scanner is plugged in, turned on and detected by the
sane-find-scanner tool (if appropriate). Please read the documentation
which came with this software (README, FAQ, manpages).
ck@ck-eM250:~$

---

### Post by paulnewall on 2013-03-13
Now I'm not sure.
It may be necessary to restart the PC after editing the udev rules.
Or it may be necessary for you to belong to the group called scanner.

On the menu go to: Settings manager; users and groups; manage groups; scanner;
Then tick your user name in the list of user names
Then OK or close everything

and try again (maybe after another restart)?

---

### Post by CK000 on 2013-03-13
Thank you very much indeed Paul, I did exactly as you suggested including the restart and scan2pdf now recognises my scanner. 

You deserve a :KS gold star. 

Many thanks indeed.

Note to moderators, can I possibly suggest that other threads concerning this particular scanner are linked here please as this walk-through has helped immensely and I think the matter has been solved. However upon the new forum format I cannot find the mark thread as solved button.

Thank you to everyone for their help once more.

:)

---

### Post by paulnewall on 2013-03-13
I think one reason why it is so difficult to get sane set up is that installing a new version, where an old version already exists, does not replace all the configuration files with new ones. This is probably intended to preserve any special entries that the user has made. Unfortunately it preserves any faults or missing entries too.
It would be nice to find a way to force all the new configuration files to replace the old ones.

---

