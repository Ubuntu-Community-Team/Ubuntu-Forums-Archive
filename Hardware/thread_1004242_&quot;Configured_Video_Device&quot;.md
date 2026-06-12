---
title: "&quot;Configured Video Device&quot;"
date: 2008-12-07
forum: Hardware
---

### Post by vendetta23 on 2008-12-07
I was looking around on how to install my video card and I found [this.]("http://ubuntuforums.org/showthread.php?t=207794")

The problem is, under Section "Device", instead of having all that, I just have "Configured Video Device." Can anyone help me finish that howto? 

Thanks in advance.

---

### Post by blackened on 2008-12-07
This is due to changes in the way the xserver functions under 8.04 and 8.10. Because everything is auto-detected it leaves the xorg configuration file looking spartan, as you've seen. The good news is that any usable changes to xorg.conf override the autodetection, so, in theory, you should be able to add the appropriate information to xorg.conf's device section (overwriting the Configured Video Device part) and it should work. May I suggest that you use "intel" in place of i810. I'm pretty sure the driver name has changed.

Pre-changes your xorg.conf device section should look similar to this:
```
Section "Device"
	Identifier	"Configured Video Device"
EndSection
```

Overwrite that with this:
```
Section "Device"
Identifier "Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller"
Driver "intel"
Option "XAANoOffscreenPixmaps"
BusID "PCI:0:2:0"
EndSection
```

Also make sure you check the BusID against your hardware in lspci.

---

### Post by vendetta23 on 2008-12-07
00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d3)
00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)
00:1e.3 Modem: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller (rev 03)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
06:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
06:06.0 Network controller: Intel Corporation PRO/Wireless 2200BG [Calexico2] Network Connection (rev 05)
06:09.0 CardBus bridge: Texas Instruments PCIxx21/x515 Cardbus Controller
06:09.2 FireWire (IEEE 1394): Texas Instruments OHCI Compliant IEEE 1394 Host Controller
06:09.3 Mass storage controller: Texas Instruments PCIxx21 Integrated FlashMedia Controller
06:09.4 SD Host controller: Texas Instruments PCI6411/6421/6611/6621/7411/7421/7611/7621 Secure Digital Controller


I'm not sure what im looking for after lspci.

---

### Post by blackened on 2008-12-07
Looks good, you should be able to overwrite the devices section with what's in the howto and be good to go.

---

### Post by vendetta23 on 2008-12-07
Hmm... I tried replacing my currernt one with the one in the howto and the one you gave to me. Both times I had the same error; I had to restore to default configurations to post this. I'm not sure what the problem is.:-?

---

### Post by blackened on 2008-12-07
Do you have the intel driver installed?

```
sudo apt-get install xserver-xorg-video-intel
```

Then try it again.

---

### Post by vendetta23 on 2008-12-07
It looks like I already have the driver. But there is another problem I'm having after I upgraded to 8.10. It always says something is wrong with screenlet and always end installation commands with this:




Reading package lists... Done
Building dependency tree       
Reading state information... Done
xserver-xorg-video-intel is already the newest version.
The following packages were automatically installed and are no longer required:
  libopencdk10-dev linux-headers-2.6.24-19-generic python-gtk2-doc
  libgnutlsxx13 libavutil1d python-pexpect libdc1394-13
  icedtea6-plugin python-twisted-web g++-4.2 python-pycurl
  libwebkit-1.0-1 libpostproc1d python-dev libaccess-bridge-java
  python2.5-dev libavformat1d openjdk-6-jre-headless tzdata-java
  libjpeg62-dev openjdk-6-jre openjdk-6-jre-lib libawn0-trunk
  libstdc++6-4.2-dev liblzo2-dev rhino libavcodec1d python-smartpm
  ca-certificates-java linux-headers-2.6.24-19
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.


***************************
Setting up screenlets (0.1.2-3ubuntu1) ...
pycentral: pycentral pkginstall: not overwriting local files
pycentral pkginstall: not overwriting local files
dpkg: error processing screenlets (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 screenlets
E: Sub-process /usr/bin/dpkg returned an error code (1)
*****************************

---

### Post by blackened on 2008-12-07
> **vendetta23 said:**
> It looks like I already have the driver. But there is another problem I'm having after I upgraded to 8.10. It always says something is wrong with screenlet and always end installation commands with this:...

To fix the screenlets problem do:
```
sudo dpkg --configure -a
```


Per the driver problem:
Try changing the driver in xorg.conf to vesa instead of intel, then restart X. Just to eliminate that it might be something else in xorg.conf interfering.

---

### Post by vendetta23 on 2008-12-07
After dpkg:

Setting up screenlets (0.1.2-3ubuntu1) ...
pycentral: pycentral pkginstall: not overwriting local files
pycentral pkginstall: not overwriting local files
dpkg: error processing screenlets (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 screenlets


and I will try yhat you suggested about the driver later when time permits.

---

### Post by blackened on 2008-12-07
Weird that the install script crapped out. Did you try removing then reinstalling screenlets?

---

### Post by vendetta23 on 2008-12-08
No. I didn't bother because my screenlets were working fine. Is it necessary?

---

### Post by nova47 on 2009-02-26
Does anyone happen to know how to reconfigure the x windows configuration file via VI after you've installed the restricted drivers for the EVGA Nvidia 9800 GTX? I installed them and now of course can't boot to a GUI and since they changed the xwindows format there aren't any good posts on how to fix it.

---

### Post by blackened on 2009-02-27
As you can see, the last post in this thread was nearly three months ago and thread hijacking is discouraged.

Please start a new thread with a descriptive title about your particular problem so that others with similar issues can use the search function to find answers should you find any.

---

