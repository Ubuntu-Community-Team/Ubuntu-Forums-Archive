---
title: "Asus F3ke"
date: 2007-09-20
forum: Hardware &amp; Laptops
---

### Post by vascot on 2007-09-20
I've an ASUS F3KE, it's a laptop with a amd turion 64 proc a AMD X2300 videocard. I'm running ubuntu feisty for 64bit, currently  a 2.6.20-16-generic kernel. The following this i've done to get ubuntu running. Not all the parts of my laptop are yet functioning well. This will become a little howto, so you (and I) can get a ubuntu installation working.

**Working:**
1) Monitor
2) tv out
3) Sound
4) webcam
5) wifi

**Work-in-progress (not working/bad functioning)**:
1) Headphone out
2) microfone
3) cardreader
4) sleep/hybernate

**Not tested yet:**
1) vga/dvi out
2) bluetooth
3) modem
4) firewire

**Relevant hardware:**
```

$ lspci
....
00:14.0 SMBus: ATI Technologies Inc SB600 SMBus (rev 14)
00:14.2 Audio device: ATI Technologies Inc SB600 Azalia
06:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 01)
07:00.0 Ethernet controller: Atheros Communications, Inc. Unknown device 001c (rev 01)
08:01.0 FireWire (IEEE 1394): Ricoh Co Ltd Unknown device 0832 (rev 05)
08:01.1 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
08:01.2 System peripheral: Ricoh Co Ltd Unknown device 0843 (rev 12)
08:01.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
08:01.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)
.....

```

Webcam: 
```

$ lsusb -v
...
Bus 006 Device 003: ID 174f:5a35  
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass          239 Miscellaneous Device
  bDeviceSubClass         2 Common Class
  bDeviceProtocol         1 Interface Association
  bMaxPacketSize0        64
  idVendor           0x174f 
  idProduct          0x5a35 
  bcdDevice            4.11
  iManufacturer           2 Sonix Technology Co., Ltd.
  iProduct                1 USB 2.0 Camera
  iSerial                 3 SN0001
  bNumConfigurations      1
.....

```

next posts will contain howtos to get that stuff working

---

### Post by fransfrans on 2007-10-01
Hello Vascot,

I have bought the same laptop and I've just tried for one day but I couldn't get wifi and the webcam to work. Which drivers did you use? I tried ndiswrapper with an winxp-x64 driver.
I also tried to compile the madwifi driver but no success either. (with ndiswrapper I could see my access point but didn't get an ip address)
I haven't put any effort in my webcam yet but it just didn't work.
btw, my microphone and headphone worked out of the box.

regards,

Frans

---

### Post by vascot on 2007-10-03
**Installation and monitor**
You can't boot from the "normal" cdrom, so you have to download the "alternative" cdrom. After installing ubuntu I've installed drivers:
```

apt-get update
apt-get install linux-restricted-modules-$(uname -r)
apt-get install xorg-driver-fglrx
depmod -a
aticonfig --initial
aticonfig --overlay-type=Xv

apt-get dist-upgrade

```

If you're resolution isn't yet 1280x800 it could beyou have to add it in /etc/X11/xorg.conf
There is a section "Screen" wich look like this:
```

Section "Screen"
        Identifier "Default Screen"
        Device     "Generic Video Card"
        Monitor    "Generic Monitor"
        DefaultDepth     24
        SubSection "Display"
                Depth     1
                Modes    "1280x800" "1200x800" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth     4
                Modes    "1280x800" "1200x800" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth     8
                Modes    "1280x800" "1200x800" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth     15
                Modes    "1280x800" "1200x800" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth     16
                Modes    "1280x800" "1200x800" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth     24
                Modes    "1280x800" "1200x800" "1024x768" "800x600" "640x480"
        EndSubSection
EndSection

```
If there is not a "1280x800" mode you have to add it. (using a editor like vim or nano etc)

**tv out**
To get my tvout working I added this line:
Option      "EnableMonitor" "tv"

to /etc/X11/xorg.conf :
```

Section "Device"
        Identifier  "aticonfig-Device[0]"
        Driver      "fglrx"
        Option      "VideoOverlay" "on"
        Option      "OpenGLOverlay" "off"
        Option      "EnableMonitor" "tv"
EndSection

```

To get video out working, you have to restart the xserver: Sometimes it works wit crtl-alt-backspace. Else you have to restart it as root: 
```

sudo killall -HUP gdm

```

Is is not the most pleasant way, I'm stil searching for another (so you don't have to kill your session, and you can use also your laptopscreen).

---

### Post by fransfrans on 2007-10-03
So how did you install your wlan? Mine (AR5007EG) is being recognized when I blacklist ath_pci and ath_hal and then install ndiswrapper with this driver:

[ftp://ftp.work.acer-euro.com/notebook/aspire_5100/driver/Wireless_Atheros_V5.3.0.67_XP_XB63_XB62(WHQL).zip](ftp://ftp.work.acer-euro.com/notebook/aspire_5100/driver/Wireless_Atheros_V5.3.0.67_XP_XB63_XB62(WHQL).zip) 

It is now visible in my network manager, but I still can't connect it and it doesn't see my router

I have been messing around with this for the last week

---

### Post by fransfrans on 2007-10-04
btw I have placed a wiki about my laptop on
[https://wiki.ubuntu.com/LaptopTestingTeam/AsusF3KE-AP009C](https://wiki.ubuntu.com/LaptopTestingTeam/AsusF3KE-AP009C)
Maybe it is handy if you edit this wiki with your findings

My cardreader, microphone and bluetooth are working out-of-the-box

---

### Post by fransfrans on 2007-10-05
My wireless is now also working with the driver I previously mentioned and ndiswrapper (just after apt-get upgrade)
It only gives a hardware adres 00:00:00:00:00:00 so it won't pass my routers mac-filter but that's a problem for later.
I will also edit the wiki for this

Still not working:
*Webcam - I tried modifying the [http://syntekdriver.sourceforge.net/]("http://syntekdriver.sourceforge.net/") driver but with no success till now. 
*Sleep is still not working

---

### Post by vascot on 2007-10-11
The wlan isn't working always on my laptop. Sometimes my laptop get stuck when I run iwconfig :S. I've to do a hard reboot.

Some time ago it worked better: I could use some mapping scripts in /etc/network/interfaces and wpa_supplicant. Also i could use wifi-radar to confifurate my wlan. Now i use the following script, sometimes it works, sometimes i have to reboot:

```

ifconfig wlan0 down
ifconfig wlan0 hw ether 00:00:00:00:00:01
ifconfig wlan0 up

iwconfig wlan0 essid "default"
iwconfig wlan0 mode Managed
iwconfig wlan0 channel 11
iwconfig wlan0 ap 00:50:18:4B:D7:08
iwconfig wlan0 rate 11M
iwconfig wlan0 key off

dhclient wlan0

```
I run it as root (of course). You have to copy paste youre networksettings from 
```

iwlist wlan0 scan

```

---

### Post by vascot on 2007-10-11
Did you had enabled the headphone out once with windows vista?

---

### Post by vascot on 2007-10-11
I've the webcam working (a sort of):
It works with the developent version of linux-uvc. So you have to download the code from the repository. First, you need a subversion client:
```

sudo apt-get install svn

```

Then download the code, compile and install:
```

svn export svn://svn.berlios.de/linux-uvc/linux-uvc/trunk ./linux-uvc
cd ./linux-uvc
make

sudo cp uvcvideo.ko /lib/modules/2.6.20-16-generic/kernel/ubuntu/media/usbvideo/uvcvideo.ko
sudo echo "videodev" >> /etc/modules
sudo echo "uvcvideo" >> /etc/modules

```



(I'm still using feisty faw, if you use another kernel, you have to edit the last line)

The webcam isn'y functioning good, I can use it ONLY with ekiga, and the movie is flipped.

I'll post later what i've tried with my wlan.

---

### Post by fransfrans on 2007-10-11
Hi Vasco,

Thanks for your webcam howto. I will try it later.
Do you also have the problem that your ndiswrapper always gives the HW_ADDR 00:00:00:00:00:00?
This seems to be a problem in ndiswrapper with 64 bit systems but it has been fixed in current trunk version of ndiswrapper.

just run:
 svn co [https://ndiswrapper.svn.sourceforge.net/svnroot/ndiswrapper](https://ndiswrapper.svn.sourceforge.net/svnroot/ndiswrapper) ndiswrapper

cd to the trunk/ndiswrapper directory
and run
```

make
sudo make uninstall
sudo make install

```

For me this works (at least in gutsy) with the drivers i mentioned above

---

### Post by vascot on 2007-10-11
How did you get youre asus buttons working (that 5 left of the powerbutton)?

---

### Post by fransfrans on 2007-10-11
No idea, they just work in Gutsy... 
just wait until 18 oktober and grab that upgrade!

---

### Post by fredylee on 2007-10-22
> **vascot said:**
> I've the webcam working (a sort of):
It works with the developent version of linux-uvc. So you have to download the code from the repository. First, you need a subversion client:
```

sudo apt-get install svn

```

Then download the code, compile and install:
```

svn export svn://svn.berlios.de/linux-uvc/linux-uvc/trunk ./linux-uvc
cd ./linux-uvc
make

sudo cp uvcvideo.ko /lib/modules/2.6.20-16-generic/kernel/ubuntu/media/usbvideo/uvcvideo.ko
sudo echo "videodev" >> /etc/modules
sudo echo "uvcvideo" >> /etc/modules

```


(I'm still using feisty faw, if you use another kernel, you have to edit the last line)

The webcam isn'y functioning good, I can use it ONLY with ekiga, and the movie is flipped.

I'll post later what i've tried with my wlan.

Hey Vascot, I followed your instruction to make my webcam work...It is  inbuilt in ASUS A8Jr....I am now using 7.10 and my kernel is 2.6.22-14-generic #1 , Can you tell me how to modify the last two code ?
 This is the result I get 

fredy@fredy-laptop:~/linux-uvc$ sudo echo "videodev" >> /etc/modules
bash: /etc/modules: Permission denied

Thx

---

### Post by fransfrans on 2007-10-22
hi fredylee,

You have another laptop with another webcam, so I don't think this solution will help you any further...

cheers Frans

---

### Post by vascot on 2007-10-27
Do you even have a /etc/modules:
$ cat  /etc/modules

---

### Post by vascot on 2007-11-12
My headphone out is working: ASUS have replaced my motherbord.

How do you mute the speakers and use only the headphone out? My alsamixer doesn't give a volume bar for my headphone out, only a mute. When I mute the speaker, my headpone out get also muted.

---

### Post by taz12 on 2007-11-21
Having no joy here with getting my wifi to work, keep getting things like "Can't find package ndiswrapper" or can't find package svn when I type commands into the terminal.

---

### Post by vascot on 2007-12-06
> **taz12 said:**
> Having no joy here with getting my wifi to work, keep getting things like "Can't find package ndiswrapper" or can't find package svn when I type commands into the terminal.

Did you look at this page:
[https://wiki.ubuntu.com/LaptopTestingTeam/AsusF3KE-AP009C](https://wiki.ubuntu.com/LaptopTestingTeam/AsusF3KE-AP009C)

Can you change the volume of your speakers seperately from you headphone out?

---

