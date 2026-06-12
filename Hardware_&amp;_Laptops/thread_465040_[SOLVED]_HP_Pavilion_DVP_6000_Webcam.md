---
title: "[SOLVED] HP Pavilion DVP 6000 Webcam"
date: 2007-06-05
forum: Hardware &amp; Laptops
---

### Post by Kristopher on 2007-06-05
So far I have managed to get 98% to work under Ubuntu 7.04 the only ones to do are Lightscribe (not yet on linux), the remote (most buttons work) and the built in webcam.

I have seen a few posts that say to do this and that and so far no one has replied saying if it worked or not, so I havnt tried it in case it messed my laptop.

How to do I get the webcam to work? is there an easy way? I am new to linux/Ubuntu (2 months)

Sorry its a DVP 6000 not 9000 typo in the title

---

### Post by teaker1s on 2007-06-05
firstly you need to find out the webcam model using either
```
lspci
```
or more likely connected via usb then
```
lsusb
```

also worth a look here may help
[https://wiki.ubuntu.com/hp_dv6000_series_%28dv6116eu%29?highlight=%28dv6000%29%7C%28hp%29#head-1c7180cbcc04dae94420ec64f775311b0fe93bf2]("https://wiki.ubuntu.com/hp_dv6000_series_%28dv6116eu%29?highlight=%28dv6000%29%7C%28hp%29#head-1c7180cbcc04dae94420ec64f775311b0fe93bf2")

---

### Post by drpaul on 2007-06-05
Neat How to but none of the uvc packages appear in my Synaptic. Is a special repo needed?

Paul

---

### Post by teaker1s on 2007-06-05
Hi, someone else wrote that part of the howto, you may need to enable your extra repositories by uncommenting sources in your sources file to include multiverse etc
```
gedit /etc/apt/sources.list
```

remove [COLOR="Red"]#[/COLOR]in front of a source to uncomment it.
save file and reload synaptic

---

### Post by drpaul on 2007-06-05
I've had multiverse enabled all along. Is it perhaps an Edgy thing?

uvc just doesn't show.

Paul

---

### Post by Atomic Dog on 2007-06-06
Did you run lsusb and find out whether you have a Ricoh or Microdia webcam?  Depending on what you have, you will need to search out the manufacturer name to find the right drivers to install.  

The Ricoh recently got drivers working, and I did test them and they worked (not great, but worked).  The microdia drivers...well I just don't care enough to fuss with it as I never use the webcam anyway, but you can get it working too.

---

### Post by Kristopher on 2007-06-06
Thanks teaker1s   will do this when I get home and let you know.

---

### Post by Kristopher on 2007-06-08
Hi teaker sorry for the late reply been busy with work. Here is the output from lspci

00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS/940GML and 945GT Express Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile 945GM/PM/GMS/940GML and 945GT Express PCI Express Root Port (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801GBM/GHM (ICH7 Family) Serial ATA Storage Controller AHCI (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation GeForce Go 7400 (rev a1)
02:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
05:00.0 Ethernet controller: Intel Corporation 82573L Gigabit Ethernet Controller
07:05.0 FireWire (IEEE 1394): Ricoh Co Ltd Unknown device 0832
07:05.1 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
07:05.2 System peripheral: Ricoh Co Ltd Unknown device 0843 (rev 01)
07:05.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)
07:05.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 05)

---

### Post by Kingsley on 2007-06-09
I used this guide to set up my dv6000t camera. Afterwards, I used Ekiga to test it out.

[http://ubuntuforums.org/showthread.php?t=280121&highlight=webcam](http://ubuntuforums.org/showthread.php?t=280121&highlight=webcam)

---

### Post by Kristopher on 2007-06-11
Tried that last night didnt work i just keep seeing Ekiga's icon float up and down :(

---

### Post by Kobalt on 2007-06-11
Can you please post the output of the command line *lsusb*. The webcam is not listed in *lspci*.

---

### Post by doldett on 2007-06-13
webcam does not work on my dv9000 laptop as well. However, i did find on another thread to download driver from [http://lsb.blogdns.net/ry5u870/](http://lsb.blogdns.net/ry5u870/) and i did that but i don't know how to do next;) (i'm new).

here is the "lspci" result

00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS/940GML and 945GT Express Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile 945GM/PM/GMS/940GML and 945GT Express PCI Express Root Port (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801GBM/GHM (ICH7 Family) Serial ATA Storage Controller AHCI (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation G70 [GeForce Go 7600] (rev a1)
02:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
05:00.0 Ethernet controller: Intel Corporation 82573L Gigabit Ethernet Controller
07:05.0 FireWire (IEEE 1394): Ricoh Co Ltd Unknown device 0832
07:05.1 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
07:05.2 System peripheral: Ricoh Co Ltd Unknown device 0843 (rev 01)
07:05.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)
07:05.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 05)

and this is "lsusb" result

Bus 005 Device 003: ID 05ca:1810 Ricoh Co., Ltd 
Bus 005 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 001 Device 004: ID 046d:c50e Logitech, Inc. MX-1000 Cordless Mouse Receiver
Bus 001 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000 

Please help me out ^_^

---

### Post by Kristopher on 2007-06-14
when i type lsusb all are blank apart from this line

Bus 005 Device 002: ID 05ca:1810 Ricoh Co., Ltd 

the other read like

Bus 005 Device 003: ID 0000:0000 etc

---

### Post by Kristopher on 2007-08-01
WOOHOO i got it to work and here is how i did it.

Taken from [http://lsb.blogdns.net/ry5u870/](http://lsb.blogdns.net/ry5u870/)

Go Here (Latest Kernal at time of post) [http://www.arakhne.org/spip.php?article51](http://www.arakhne.org/spip.php?article51)

Follow the top part of the instructions then the following

sudo apt-get update
search for webcam find the file
sudo apt-get install FILE

I had to install AMSN to test it and it worked 1st time.

---

### Post by drpaul on 2007-08-01
Do you think this will work for 

paul@hppaul:~$ lsusb
Bus 005 Device 004: ID 0c45:62c0 Microdia 

???

Paul

---

### Post by buntunub on 2007-08-01
Whats weird is that while I still had Vista on my notebook, my webcam wouldnt work no matter what I tried. After I wiped vista (but left the recovery partition intact for warrenty) and did a clean Fiesty reinstall, Every bloomin thing on the Laptop works including the webcam and builtin mics out of the box (wireless with ndiswrapper). I am damned impressed with both this HP laptop and Ubuntu for pulling this off. Heck, even the remote works. Ive been doing some hardcore stress testing on this thing with Fiesty from everything to trying to overload the CPUs, stress RAM/swap, hibernate/suspend, multimedia and gstreamer, beryl/compiz, power consumption and CPU/GPU temps, overclocking, wireless stress testing - longevity/signal/encryption consistency, and currently still testing uptime. All results are pretty much stellar with some minor tweaks here and there, like optimizing xorg.conf for better beryl performance which can sometimes be choppy. Wireless has been good enough to actually stream TV broadcasts from another server which has a TV card via vlc AND still have enough bandwidth to stream a movie from my media server on top of that with 60% or better signal strength and the quality of BOTH is just outstanding. Working on 11 days uptime now and still going. 

Oops, about the webcam hehe. Use the builtin uvcvideo (lsmod | grep uvc anyone?). The webcam works out of the box on Ekiga. Use luvcview from berlios.de for general stuff, and use ffmpeg for audeo/video recording. Works flawlessly.

---

