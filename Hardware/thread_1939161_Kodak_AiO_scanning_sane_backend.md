---
title: "Kodak AiO scanning sane backend"
date: 2012-03-11
forum: Hardware
---

### Post by paulnewall on 2012-03-11
There is a sane backend for scanning using the Kodak AiO printers, like ESP 5250, ESP C310, Hero 9.1
 
Installation is by compiling from the source code here
 
[https://sourceforge.net/projects/cupsdriverkodak/files/Scanning%20-%20sane%20backend/](https://sourceforge.net/projects/cupsdriverkodak/files/Scanning%20-%20sane%20backend/)
 
A number of people have downloaded it, but I have had no feedback, apart from one or two people having difficulty installing.
If you have managed to do a scan with this backend I'd appreciate some feedback.
Particularly regarding USB. For me it's only working properly using the WiFi connection. Can anyone tell me about their experience with USB?

---

### Post by jmcook79 on 2012-09-30
I have a esp 5200 working in Linux Mint at with wifi and usb. All I did was plug it in and it automatically set it up. Since Mint is based on Ubuntu it should work for you as well, although I can't get the scanner working. No big deal though since I can still use it to make copies and it's been years since i actually needed to scan anything.

---

### Post by paulnewall on 2012-10-01
Yes, I wrote the cups printer driver that you are using.
The scanner driver is completely separate from the printer driver. It is now included in sane-backends 1.0.23 and may appear in future releases of ubuntu.

---

### Post by jmcook79 on 2012-10-02
I downloaded the packages from Ubuntu Quantal and got my scanner working but only via usb the wifi is not detected. How would I go about getting it to detect the wifi? BTW thanks for the cups drivers! I just recently started using linux again and compared to 10 years ago printer support is pretty much plug and play, Linux has come so far!

Update: Just got wifi working I just had to manually add the IP to the kodakaio.conf!

---

### Post by paulnewall on 2012-10-02
The kodakaio sane backend uses cups to autodetect network printers.
This works OK in ubuntu 12.04 (cups 1.5.x).
It would not be surprising if we find some problems with the autodetection in ubuntu 12.10 (cups 1.6.x) because cups 1.6 is a bit different from 1.5
Which cups version does your Mint have?
If you want to try and see what is going on during the autodetection, you need to enable debug output for kodakaio. (this should be explained in the kodakaio man page)

---

### Post by jmcook79 on 2012-10-02
I'm using Mint 13 Maya and my cups version is 1.5.3. This version of cups audodetects the printer of my kodak esp 5200. Here's the debugging results.

mike@mike-Aspire-5534 ~ $ export SANE_DEBUG_KODAKAIO
mike@mike-Aspire-5534 ~ $  scanimage -L
[sanei_debug] Setting debug level of kodakaio to 40.
[kodakaio] ========================================== 
[kodakaio] sane_kodakaio_init: sane-backends 1.0.23
[kodakaio] kodakaio backend, version 2.4.3
[kodakaio] sane_kodakaio_init: called
[kodakaio] sane_kodakaio_get_devices: called
[kodakaio] attach_one_config: len = 17, line = snmp-timeout 1500
[kodakaio] attach_one_config: len = 22, line = scan-data-timeout 7000
[kodakaio] attach_one_config: len = 20, line = request-timeout 5000
[kodakaio] attach_one_config: len = 17, line = net autodiscovery
[kodakaio] attach_one_config: len = 3, line = usb
[kodakaio] sane_kodakaio_get_devices: found 0 scanner(s)
[kodakaio] sane_kodakaio_get_devices - results:

No scanners were identified. If you were expecting something different,
check that the scanner is plugged in, turned on and detected by the
sane-find-scanner tool (if appropriate). Please read the documentation
which came with this software (README, FAQ, manpages).
[kodakaio] sane_kodakaio_exit
[kodakaio] free_devices

---

### Post by jmcook79 on 2012-10-02
Here is a snip from the kodakaio.conf  that says autodoscovery is broken, strange since cups detects my printer! I did notice however, that it almost got it right the default ip in the config file was 192.168.1.1 0x404 and mine is 192.168.1.68 0x404

very strange...

Network: Format is "net IP_ADDRESS [USB_ID]" or "net autodiscovery"
###          if USB_ID is left out, SNMP is used to detect the device type
###          _Currently autodiscovery seems to not work_
###          So always use "net IP_ADDRESS [USB_ID]" as shown below
###          You can find the printer's IP address on its control panel
###          There is a list of USB_IDs at the end of this file

---

### Post by paulnewall on 2012-10-04
Now I am trying ubuntu 12.10 with cups 1.6  and I have the same problem, no auto-detection of network scanner. So I can work on the problem now.

---

### Post by paulnewall on 2012-10-05
It seems that the kodakaio backend in ubuntu 12.10 might have been compiled without cups, so the autodetection is not compiled into it.
I compiled the backend myself, and autodetection worked in 12.10
Installation was tricky. In 12.10 the sane libraries are in /usr/lib/i386-linux-gnu/sane.
I manually copied the kodakaio libs there after installation to /usr/lib/sane

---

### Post by paulnewall on 2012-10-21
If you compile sane-backends , the network auto detection should work.
If you use the latest git version, the difficulties with install ing in ubuntu 12.10 should have been fixed.
 
Instructions for installing from git are here
[https://help.ubuntu.com/community/CompileSaneFromSource](https://help.ubuntu.com/community/CompileSaneFromSource)

---

### Post by jansgar on 2012-12-17
Just installed git-version of sane on Ubuntu 12.10 and Kodak ESP5210 works perfect with usb.

regarding the installation instruction:
libcupsdriver1-dev is not available, it's somehow moved to the cups package?

thanx a lot! (any way to donate a small amount?)

---

### Post by dykidw on 2012-12-19
Thank you very much - my Kodak C310 works perfectly now.    I am running LinuxMint 14.

---

