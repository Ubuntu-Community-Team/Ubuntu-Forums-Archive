---
title: "Brother ADS-2400N scanner on Xubuntu 18.04 - can only scan as superuser"
date: 2020-01-09
forum: Hardware
---

### Post by chris6672 on 2020-01-09
Hi

I have installed Xubuntu 18.04LTS on a desktop. Everything's fine, apart from the scanner.

I downloaded the driver from the Brother website and installed it according to the instructions [on this page]("https://support.brother.com/g/b/producttop.aspx?c=gb&lang=en&prod=ads2400n_all").

It works, but only if I run the scanner as superuser. There is a link that is supposed to give instructions which I followed, but it's broken. I found it by searching on Google another link but the last version of Ubuntu mentioned is [10.10]("https://support.brother.com/g/s/id/linux/en/instruction_scn1c.html?c=us_ot&lang=en&redirect=on#u13.04").

I looked for anything that might help in the documentation. I found [this page]("https://help.ubuntu.com/community/sane") which mentions Brother drivers but nothing there was appropriate to me and the troubleshooting guide was a link to a nonexistent page.

sudo scanimage -L gives me:
```
found USB scanner (vendor=0x04ca [Broadcom Corp], product=0x200b [BCM20702A0]) at libusb:003:004
found USB scanner (vendor=0x04f9 [Brother], product=0x03b7 [ADS-2400N]) at libusb:003:002
```ls -al /dev/bus/usb/003/002 gives me:

```
crw-rw-r--+ 1 root root 189, 257 Jan  9 12:48 /dev/bus/usb/003/002

```


I checked my normal user is a member of the *saned *and *scanner* groups following [this advice]("https://help.ubuntu.com/community/ScanningHowTo#Permission%20issues") from the Ubuntu documentation. No change.

I put in these symlinks following [this post on Ubuntu forums]("https://ubuntuforums.org/archive/index.php/t-1988296.html"). 

```
sudo ln -s /usr/lib64/libbrscandec3.so.1.0.0 /usr/libsudo ln -s /usr/lib64/sane/libsane-brother3.so.1.0.7 /usr/lib/sane
sudo ln -s /usr/lib64/sane/libsane-brother3.so.1 /usr/lib/sane
sudo ln -s /usr/lib64/sane/libsane-brother3.so /usr/lib/sane
sudo ln -s /usr/lib64/libbrscandec3.so /usr/lib
sudo ln -s /usr/lib64/libbrscandec3.so.1 /usr/lib
```
Not all the files exist. I also created the file **/lib/udev/rules.d/40-libsane.rules**
```
# Brother scanners
ATTRS{idVendor}=="04f9", ENV{libsane_matched}="yes"
```

I don't know what to do next.

---

### Post by chris6672 on 2020-01-15
Hello folks.

I managed to get this working with Vuescan. It is not really a satisfactory solution, because Vuescan is (a)expensive and (b)not as good as Simple Scan. I had this device working on my old Bunsenlabs box. So maybe Debian is the way to go. 

The other option is to scan directly to USB stick. That is frankly a bit of a faff.

I am sure this is fixable. I just don't know what to do, or where to look for more help.

---

### Post by brian_p on 2020-01-15
> **chris6672 said:**
> 
I am sure this is fixable. I just don't know what to do, or where to look for more help.

Try [https://wiki.debian.org/Scanner](https://wiki.debian.org/Scanner). What do get for ```
getfacl /dev/bus/usb/003/002
``` and ```
sane-find-scanner
```

---

### Post by him610 on 2020-01-16
> I downloaded the driver from the Brother website and installed it according to the instructions on this page.
Which driver did you download from the down load page, [https://support.brother.com/g/b/downloadlist.aspx?c=gb&lang=en&prod=ads2400n_all&os=128]("https://support.brother.com/g/b/downloadlist.aspx?c=gb&lang=en&prod=ads2400n_all&os=128")
There is a 32bit and a 64bit driver. I would think the 64bit driver is the one you should have installed.
Did you follow the instructions to the letter?
```
How to Install
Download the driver.
 
Login as a superuser (or use "sudo" option if required) .
 
Check if pre-required procedures are completed 
For Debian, Ubuntu
 
Install the driver.
Turn on your MFC/DCP and connect the USB cable.
Open the terminal and go to the directory where the driver is.
Install the scanner driver.
Command (for dpkg) : dpkg -i --force-all  (scanner-drivername)
Check if the driver is installed.
Command (for dpkg) : dpkg -l | grep Brother
 

For USB Users:
Use your scanning application by a superuser and try a test scan.
Use your usb-connectrd scanner by a normal user

For Network Users:
***Use brsaneconfig (for brscan models), brsaneconfig2 (for brscan2 models), brsaneconfig3 (for brscan3 models), brsaneconfig4 (for brscan4 models) or brsaneconfig5 (for brscan5 models) accordingly.

Add network scanner entry
Command : brsaneconfig4 -a name=(name your device) model=(model name) ip=xx.xx.xx.xx

Confirm network scanner entry
Command : brsaneconfig4 -q | grep (name of your device)

Open a scanner application and try a test scan.
Please refer the FAQ pages also for other information.
```
Brother does a pretty good job supporting its products with Linux. I own a Brother MFC6360N that I usually wind up reinstalling the drivers about once every six months due to my installing the latest release on one or more of my computers. Latest one was 20.04 a few weeks ago no issues. Whenever some installation does go awry, I always look to myself first - Did I screw something up? Did I try do it from memory instead of following the instructions? I am probably not the one to give advice on troubleshooting or corrective action because I never had anything go wrong. I also never had to use "sudo" to test the scan function. 
I hope you get things worked out.

Another thought - You might want to discuss your issue with Brother support.

---

### Post by zacktu on 2020-05-16
I just found this thread, and the suggestion worked like a charm.  I installed the Brother scanner driver, but simplescan and scanx didn't find the scanner.  The suggestion to use brsaneconfig4 for my network scanner was what I needed.  Thanks very much.

---

