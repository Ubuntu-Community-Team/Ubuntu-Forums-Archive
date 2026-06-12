---
title: "Longcheer WM71 on Ubuntu"
date: 2010-05-16
forum: Hardware
---

### Post by YasirMX on 2010-05-16
Hello everyone. I tried the modeswitch technique to use the device as a modem but it won't work and returns the following

```
Looking for target devices ...
 No devices in target mode or class found
Looking for default devices ...
 Found devices in default mode or class (1)
Accessing device 012 on bus 001 ...
Using endpoints 0x01 (out) and 0x81 (in)
Inquiring device details; driver will be detached ...
Looking for active driver ...
 OK, driver found ("usb-storage")
 OK, driver "usb-storage" detached

SCSI inquiry data (for identification)
-------------------------
  Vendor String: USBModem
   Model String: Disk            
Revision String: 2.31
-------------------------

USB description data (for identification)
-------------------------
Manufacturer: USB Modem
     Product: USB Modem
  Serial No.: 1234567890ABCDEF
-------------------------
Setting up communication with interface 0 ...
Using endpoint 0x01 for message sending ...
Trying to send message 1 to endpoint 0x01 ...
 OK, message successfully sent

Checking for mode switch (max. 20 times, once per second) ...
 Waiting for original device to vanish ...
 Waiting for original device to vanish ...
 Waiting for original device to vanish ...
 Waiting for original device to vanish ...
 Waiting for original device to vanish ...
 Waiting for original device to vanish ...
 Waiting for original device to vanish ...
 Waiting for original device to vanish ...
 Waiting for original device to vanish ...
 Waiting for original device to vanish ...
 Waiting for original device to vanish ...
 Waiting for original device to vanish ...
 Waiting for original device to vanish ...
 Waiting for original device to vanish ...
 Waiting for original device to vanish ...
 Waiting for original device to vanish ...
 Waiting for original device to vanish ...
 Waiting for original device to vanish ...
 Waiting for original device to vanish ...
 Waiting for original device to vanish ...
 Original device still present after the timeout

Mode switch most likely failed. Bye.
```lsusb returns following:
```
Bus 002 Device 002: ID 03f0:171d Hewlett-Packard Wireless (Bluetooth + WLAN) Interface [Integrated Module]
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
**Bus 001 Device 012: ID 1c9e:f000  **
Bus 001 Device 004: ID 0408:030c Quanta Computer, Inc. HP Webcam
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```Any ideas regarding this issue??

---

### Post by z1000000 on 2010-05-18
Hi

I'm in the same boat as you, I have a Longcheer WM71 mobile internet stick. I'm looking online and it seems "ndiswrapper" may be able to emulate or convert the Windows drivers to something that may work. However it seems complicated and a bit frightening, lots of code stuff.

If anyone can point me in the right direction that would be great.

Dell Inspiron 6000, Linux Mint 8,Intel Corporation PRO/Wireless 2200BG card, and lsusb shows- Bus 001 Device 005: ID 1c9e:f000

---

### Post by YasirMX on 2010-05-18
It's a new product on the market and that's why the flip flop technique won't work since the  stick is expecting different signals to switch to a different mode. The ndiswrapper is geared towards wireless adapters and not usb sticks like hsdpa modems and thinking of it in this regard is a bad idea as your current wireless adapter present in your laptop might stop working if you mess with anything. 

I once tried loading windows drivers while my Atheros was working and it all messed up. Since then I knew that I shouldnt touch it :) :P

We need to wait for development to work on this issue :)

---

### Post by z1000000 on 2010-05-18
Hi YasirMX

I did try getting it working using the ndiswrapper tool, but it didn't work, not that I can be sure I was doing things 100% right. 

Do you think it would work if I ran it through a wireless router. They have mini routers just for the modem sticks and also proper ones where you can fit the sim card? I've never used a wireless router myself, but my laptop can pick up the signals of my neighbours using Windows machines and the same types of modem sticks.

Failing that, I may be able to change the USB stick for one of a different make, before a Huawei one worked.

Thanks

---

### Post by YasirMX on 2010-05-19
> **z1000000 said:**
> Hi YasirMX

** Do you think it would work if I ran it through a wireless router. They have mini routers just for the modem sticks and also proper ones where you can fit the sim card? **

Thanks

1. I don't get you here.. If you want to use an HSDPA modem, you may try a different brand. 
2. You might want to find drivers for your wireless card. try lspci to find the model listed on linux and then download,  compile and build the sources. by default  linux should be able to detect and install drivers..


Regards,
Yasir

---

### Post by z1000000 on 2010-05-19
Hi Yasir

I'm still looking for solutions. I found this thread, it seems interesting because the stick has the same ID as the Longcheek WM71, however that one's called a GBC China Bird Modem.
I don't know if the ID 1c9e:f000 means our stick is the same as the one they talk about, or if keep giving the ID's out to various types of stick.

Anyway, hope this helps.

 [http://forum.vectorlinux.com/index.php?topic=9443.0](http://forum.vectorlinux.com/index.php?topic=9443.0)

---

### Post by YasirMX on 2010-05-19
Thanks a lot for the link. This helped a lot and now I'm able to get my HSDPA modem working under linux..
in /etc/usb_modeswitch.conf get rid of the line "CheckMessage=" and it should look like

```

######################################################## 
# ST Mobile Connect HSUPA USB Modem 
#
# Use /dev/ttyUSB2 for connecting
#
# Contributor: Vincent Teoh

DefaultVendor=  0x1c9e
DefaultProduct= 0xf000

TargetVendor=   0x1c9e
TargetProduct=  0x9063

# only for reference
MessageEndpoint=0x01

MessageContent="55534243123456788000000080000606f50402527000000000000000000000"


```

create a shell script called inithsdpa.sh in /usr/sbin
it should contain the following line

```
usb_modeswitch -c /etc/usb_modeswitch.conf
sleep 1
modprobe cdc_acm
sleep 1
modprobe usbserial vendor=0x1c9e product=**0xf000**

```

[COLOR=Red]_Notice: If you own WM71 longcheer, product will always return **0xf000**_[/COLOR] 
 
after you execute the above script, a new terminal will be created ttyUSB0..to confirm, type dmesg and you should probably get something like

```

[  259.274717] usbcore: registered new interface driver usbserial
[  259.274758] USB Serial support registered for generic
[  259.279185] usbserial_generic 1-6:1.0: generic converter detected
[  259.279398] usb 1-6: generic converter now attached to ttyUSB0
[  259.279448] usbcore: registered new interface driver usbserial_generic
[  259.279456] usbserial: USB Serial Driver core

```

make sure you have wvdial and ppp installed..

```
sudo apt-get install wvdial
```
```
sudo apt-get install ppp
```

you need to edit /etc/wvdial.conf  mine looks like this

```

[Dialer Defaults]
Phone =
Username =
Password =
New PPPD = yes

[Dialer smartbro]
Init1 = ATZ
Init2 = ATE1
Init3 = AT+CGDCONT=1,”IP”,”smartbro”,”",0,0
Modem Type = USB Modem
Phone = *99#
Modem = /dev/ttyUSB0
New PPPD = yes
Baud = 912600
Stupid Mode = 1
Dial Command = ATD

```

Thus when dialing, i use following command in terminal

```

wvdial smartbro

```

That's all man :)

---

### Post by z1000000 on 2010-05-20
Hello

Sorry to be a pain but all is not going well.

I've followed your instructions, but I think the shell script is causing me problems, I'm actually
a scripting novice.

I've edited and saved the modeswitch.conf to remove the ; bits.

In Geddit, I made a shell script with-


#!/bin/bash


usb_modeswitch -c /etc/usb_modeswitch.conf

sleep 1

modprobe cdc_acm

sleep 1

modprobe usbserial vendor=0x1c9e product=0xf000





and saved it as you said, in usr/sbin as inithsdpa.sh

Did I mess up with #!/bin/bash, should it have been #!/sbin/bash, or nothing at the top?

Anyway, I managed to change permissions and execute it, once it mentioned ttyUSB0
but it and I can't find it.

And I just copied your code to the wvdial.conf, I guess those details are for your ISP, I
don't know the details of mine.

So I'm stuck, 

any help/advice would be great thanks.

PDM

---

### Post by YasirMX on 2010-05-20
**_Discard the shell script i made for you_**

Follow all the steps found @ [http://forum.vectorlinux.com/index.php?topic=9443.msg65146#msg65146](http://forum.vectorlinux.com/index.php?topic=9443.msg65146#msg65146) **until the usb_modeswitch.conf** Your config file should look as follows.. save it in /etc/usb_modeswitch.conf

```

######################################################## 
# ST Mobile  Connect HSUPA USB Modem 
#
# Use /dev/ttyUSB2 for connecting
#
#  Contributor: Vincent Teoh

DefaultVendor=  0x1c9e
DefaultProduct=  0xf000

TargetVendor=   0x1c9e
TargetProduct=  0xf000

#  only for reference
MessageEndpoint=0x01

MessageContent="55534243123456788000000080000606f50402527000000000000000000000"

```

instead of typing ```
usb_modeswitch
``` try ```
usb_modeswitch -c /etc/usb_modeswitch.conf
``` This will tell the modeswitch program to explicitly load the config file

The next command is ```
modprobe cdc_acm
``` This is important as the system should "probe" for the module cdc_acm

Type the following...Notice the product code below, it's **0xf000** - The WM71 Longcheer
```
modprobe usbserial vendor=0x1c9e **product=0xf000**
```

This should create a usb terminal ttyUSB0, ```
dmesg
``` should confirm this 

You can now dial, ```
wvdial smartbro
``` in my case...


Post all your results and just let me know.. if it doesn't work, this means you've probably missed some important steps..

---

### Post by z1000000 on 2010-05-21
Hi there

I'm still having problems, however, after a few goes I'm down to the wvdial bit.

I copied and edited your wvdial conf file, my modem/ISP is mobily, so-

[Dialer Defaults]
Phone = 
Username = 
Password = 
New PPPD = yes

[Dialer mobily]
Init1 = ATZ
Init2 = ATE1
Init3 = AT+CGDCONT=1,”IP”,”mobily”,”",0,0
Modem Type = USB Modem
Phone = *99#
Modem = /dev/ttyUSB0
New PPPD = yes
Baud = 912600
Stupid Mode = 1
Dial Command = ATD

I'm sure this is wrong as when I tried 

sudo wvdial mobily

I got this

--> WvDial: Internet dialer version 1.60
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
--> Sending: ATQ0
--> Re-Sending: ATZ
--> Modem not responding.

Oh dear, on a positive note I've filed two bug reports for the two 3G usb modems I can't get to work. My APN is web2, am I supposed to put that somewhere?

Any ideas, and thanks for all your help, you've been very kind.

---

### Post by YasirMX on 2010-05-22
When you plug in your mobily (btw I own mobily as well :guitar: but I'm from mauritius), unmount it.. right click on the cdrom icon on the desktop and click unmount

in your wvdial.conf, your apn should replace the phone number :)

Try the steps @ [http://sakis.tel4u.gr/blog/sakis3g/](http://sakis.tel4u.gr/blog/sakis3g/) it should help you out definitely :)

Note: It might be a pain to use it under linux but I Linux is the most stable OS ever and I find it very cool to use terminal to fire applications

---

### Post by YasirMX on 2010-05-22
I've tried to simplify things a little @ [http://killershock.online.fr/?p=13](http://killershock.online.fr/?p=13) hope this helps for other visitors :)

---

### Post by z1000000 on 2010-05-28
Hi Yasir

Sorry for the delay in getting back to you but I've had a few problems.

First, thanks for all your help, I've saved it all in my Bookmarks and will 
try it later. I still haven't got that Longcheer modem to work. I bought a 
second Alcatel one and still no luck. As I was using Mint 8, I thought trying 
a more modern distro may help, especially one of the Netbook friendly ones.  
So I tried a clean install of Fedora, Mandriva, Ubuntu 9.10 and an upgrade to 
10.4 and UNR, and while I sometimes got a newer version of Usb_modeswitch 
included, neither modem could be made to work. 

While in a computer shop, I found a BandLuxe C270 usb modem that actually 
said it's compatible with Ubuntu on the back of the box! So back to a clean 
install of Mint 8, and as long as I eject the CD drive when it shows up, 
(not safely remove), and set up Network manager properly, it works reliably.

I'm still testing other distros, the new Mint 9 sees the modem when the CD drive 
is ejected, but so far the best distro is Crunchbang 9.04, once you eject the CD 
drive it comes up with the wizard to set up the modem as it should.

On the good side I've learnt a lot, found my first bit of hardware with Linux 
actually mentioned on the box, and found a reliable work around. 

On the bad side surely 3G modems aren't new, surely Netbooks are made 
for that type of mobile computing? I'm patient and very keen to get Linux 
to work, but with the frustrations of trying to get online over the past week, 
well I nearly gave up and bought a Windows machine. I even thought of 
loading Mac OS until I found that wasn't so easy on a standard laptop. A new 
Linux user would have just given up, for a very long time.

Rant over. Hopefully other people who have 3G Usb modem problems will 
see your advice and it will help them. And hopefully developers will realise 
that if Linux doesn't work with these popular devices, then no one will stick 
around. Maybe Meego or Google OS will get this problem fixed.

Thanks again and the best of luck.

Right, I'm off to try and get my 4G Wimax modem to work on Linux, DOH!!!!!!

---

### Post by YasirMX on 2010-05-28
Hi there, sincerely there was no need to buy a new modem. I really find it interesting to get hardware working under linux. So far, the longcheer saga has been most challenging. I only found some steps missing on some websites and thankx to your link, i've been able to help myself out and created a tutorial. I'm on mint 8.0 Helena since the 9.0 is an unstable distro.

Compared to windows, Linux rocks since the kernel is more stable and makes efficient use of resource utilisation compared to windows. As far as possible, I try to stick to open source except for games.. That's irresistible :'( 

Best of luck mate, if in anyway I can help, post here :)

---

### Post by cbbl on 2010-06-19
Using the script from Sakis Dimopoulos located at [http://www.sakis3g.org/](http://www.sakis3g.org/) was the simplest solution to getting the WM71 working for me.  The GUI and documentation is superb.

---

