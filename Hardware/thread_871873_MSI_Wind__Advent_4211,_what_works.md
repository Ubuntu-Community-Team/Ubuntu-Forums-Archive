---
title: "MSI Wind / Advent 4211, what works?"
date: 2008-07-27
forum: Hardware
---

### Post by Zorael on 2008-07-27
Could any owner of an MSI Wind or an Advent 4211 netbook confirm what works and what doesn't? Obviously after some tinkering; from what I understand you need to install new wireless drivers, for one.

But is there something that you plain *can't* get to work yet? Suspend/hibernate? Sound? Card reader? Extra/multimedia keys?

Thanks.

---

### Post by The Cog on 2008-07-29
I haven't got wireless working yet. Oddly, even running windows it says no networks detected. I'm hoping to pick up an intel wireless card tonight, to replace the Realtek one. See this thread:
[http://wiki.msiwind.net/index.php/Ubuntu_8.04_Hardy_Heron](http://wiki.msiwind.net/index.php/Ubuntu_8.04_Hardy_Heron)

The card reader doesn't seem to see the only SD card I've got. I don't know if thats because of the sd card (haven't tried it in anything else or in windows) or another compatibility issue.

---

### Post by Naralas on 2008-07-29
Getting the right pendrive ubuntu so I could install to my Wind took way longer than I would have liked, and now, it does not seem to see the ethernet card so I cannot even try install wifi drivers.

I graphically installed 8.04.1...

*cough* as I wrote this I found that I had a bad port on the back of my cheap *** 10 dollar wireless router. It seems my ethernet might be working after all. I'll post how it goes~

---

### Post by The Cog on 2008-07-30
I reinstalled Hardy and things are looking better:

Ethernet works. I have seen it fail to pick up until I reboot (i.e. reboot with the cable already connected), but that may be because I hadn't configured it in System->Administration->Networking. Time will tell if its really working now.

Wireless partially works. I used this driver: rtl8187se_linux_26.1016.0716.2008.tar.gz
linked from this conversation: [https://bugs.launchpad.net/ubuntu/+source/linux-meta/+bug/246141](https://bugs.launchpad.net/ubuntu/+source/linux-meta/+bug/246141)
It cannot scan and list networks, but it does at least connect if you configure the essid and wpa password.
CORRECTION: It produced a proper "iwlist scan" list of cells for me just now. Maybe it's to do with the order in which I do things. Needs experimenting with.

The card reader sort of works. I have to mount the SD card manually because the automount seems to try to open it as a CD. I see these two log messages:
  UDF-fs: No partition found (1)
  ISOFS: Unable to identify CD-ROM format
which is no real surprise for a FAT32 flash drive. Doh!

Sound works.
3D acceleration works.
Bluetooth not tested yet, but the bluetooth tray icon appears when I turn it on.
The swapped Fn and Ctrl keys are starting to irritate me.

---

### Post by CbrPad on 2008-07-30
I had no webcam until I did this (running Ear Os)..

sudo aptitude install subversion sudo aptitude install Subversion

svn co SVN Co svn://svn.berlios.de/linux-uvc/linux-uvc/trunk svn: / / svn.berlios.de / linux-uvc /

linux-uvc / trunk linux-uvc Linux-UVC

cd linux-uvc CD Linux-UVC

sudo make Make Sudo

sudo make install Sudo make install

sudo modprobe -r uvcvideo Sudo modprobe-r uvcvideo

sudo mv /lib/modules/$(uname -r)/ubuntu/media/usbvideo/uvcvideo.ko /lib/modules/$(uname -r)/ubuntu/media/usbvideo/uvcvideo.ko.original sudo mv / lib / modules / $ (uname-r) / ubuntu / media / usbvideo / uvcvideo.ko / lib / modules / $ (uname-r) / ubuntu / media / usbvideo / uvcvideo.ko.original

sudo cp uvcvideo.ko /lib/modules/$(uname -r)/ubuntu/media/usbvideo/uvcvideo.ko uvcvideo.ko sudo cp / lib / modules / $ (uname-r) / ubuntu / media / usbvideo / uvcvideo.ko

sudo modprobe uvcvideo Sudo modprobe uvcvideo

Just to make sure, I also did a..

sudo gedit /etc/modules

and added... uvcvideo

A reboot, a couple of Fn-F6s and what hey, it was working.

---

### Post by Zorael on 2008-08-12
I just got my Advent 4211 and it's crippled with a Sentelic touchpad. I haven't gotten a pendrive to boot properly yet (complaining about missing ubnkern when it's *there*) so I'm still running Windows.

I assume the Synaptics driver rejects it? Or is there any way to force the driver to load? No side-scrolling sucks.

---

### Post by Tito1337 on 2008-08-23
Just got an MSI Wind Black with Suse

I replaced openSux with Ubuntu making a pendrive with IsoToStick script, it worked only with Ubuntu 8.10.1 liveCD

I had to compile the wireless driver (see on wiki.msiwind.net). The webcam works out of the box (don't forget to active it with Fn+F6)

But... I HAVE THIS F*CKING SENTELIC TOUCHPAD ! To scroll I have to tap in one of the right corner >_< Maybe I could replace it with a synaptics touchpad found on eBay? :(

---

### Post by nischg on 2008-08-23
Same issue here with the touchpad. If you happen to find a solution that allows us slide to scroll, please let us know. If it requires to swap the touchpad let me know where you found the hardware. Tap to scroll is driving me mad. 

Also my battery life is a little to short compared with what Suse used to claim it was (Suse near 5:30 hrs and Ubuntu 4 hours of battery life).

---

### Post by cuby on 2008-09-02
> Also my battery life is a little to short compared with what Suse used to claim it was (Suse near 5:30 hrs and Ubuntu 4 hours of battery life).

What battery do you have?
The 3 cell 2100mAh model?

---

### Post by nischg on 2008-09-02
> **cuby said:**
> What battery do you have?
The 3 cell 2100mAh model?

No, the 6 cell one

---

### Post by shaemarks on 2009-05-24
I am veiwing MSI Wind with SUSE
I changed over the UBUNTU to OpenSux.
I also compiled driver ..
[SIZE=6][COLOR=DarkRed]
What should i do next[/COLOR][/SIZE]

---

### Post by ricojonah on 2009-11-18
I know this is a longshot, but I saw this thread, which discussed attempts to get sentelic touchpads to have slide-scrolling functionality on the toucpad: 

[http://ubuntuforums.org/showthread.php?t=345728]("http://ubuntuforums.org/showthread.php?t=345728")

The trouble is that the thread refers to a different type of laptop (though it might still be the same--or close enough model touchpad), and the even-bigger issue is that the potential fix involves editing the old-school xorg.conf file (which, in Karmic, is basically not used anymore).

Maybe the information from that thread can be adapted to those differences. I'd try it myself, but I'm honestly too lame & afraid to mess with anything else on my MSI Wind (I just finished trying to get other out-of-the-box  issues resolved, and I'm too afraid to touch anything now!)

---

### Post by ricojonah on 2009-11-18
> **Tito1337 said:**
> Just got an MSI Wind Black with Suse

I replaced openSux with Ubuntu making a pendrive with IsoToStick script, it worked only with Ubuntu 8.10.1 liveCD

I had to compile the wireless driver (see on wiki.msiwind.net). The webcam works out of the box (don't forget to active it with Fn+F6)

But... I HAVE THIS F*CKING SENTELIC TOUCHPAD ! To scroll I have to tap in one of the right corner >_< Maybe I could replace it with a synaptics touchpad found on eBay? :(

I posted some information later in this thread about a possible solution to enable the touch-slide scrolling functionality for the sentelic touchpade (I probably should have just replied here--sorry!), but I just found another workaround that works pretty well for me.

Take a look at mouseemu (it's in synaptic). After installing it, uncommenting the "SCROLL=" line in /etc/defaults/mouseemu, and then restarting the server (sudo /etc/init.d/mouseemu restart), you'll be able to scroll with the touchpad by holding the ALT key and sliding your finger on the touchpad. It's not the greatest solution, but it works well enough for me.

---

