---
title: "Bandluxe c 120 (HSDPA) ?"
date: 2008-08-11
forum: Hardware
---

### Post by turkey_204 on 2008-08-11
Hi evryone

I am new to ubuntu and I am using  ubuntu 7.10 and I want to access internet using bandluxe c 120. 
can anyone help me please?

---

### Post by codrus on 2008-08-30
There's a driver here, although I haven't tried it yet.

[http://www.bandrich.com/download03.aspx?id=2&c=25&lang=3](http://www.bandrich.com/download03.aspx?id=2&c=25&lang=3)

---

### Post by arensal on 2008-12-06
Hi cordus,

You point to a Fedora 8 manual for the c120. I have tried my best with both Ubuntu 8.10 and Fedora 8 and could not get it to work. I  follow the guide carefully but without success.

Is there actually anyone in this universe who got the thing working under linux?

thanks,

---

### Post by zilvia on 2009-03-08
Here is how I did - a bit rough, but working...

1. At first the thing is recognized as an external storage device. So you have to remove it manually:

```
eject /dev/scd1
```


2. It's wvdial that takes care of the connection. First it has to be automatically configured via wvdialconf, that detects your modem and adds a few strings into /etc/wvdial.conf. You do this as root:

```
sudo wvdialconf /etc/wvdial.conf
```

3. Then you manually edit the config file, as root
```
sudo gedit /etc/wvdial.conf
```

This is my configuration file. You need to put your ISP's name instead of"YOUR.ISP.NAME". Keep the commas.

```
[Dialer Defaults]
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Init3 = at+cgdcont=1,"ip","YOUR.ISP.NAME"
Modem Type = Analog Modem
Baud = 460800
New PPPD = yes
Modem = /dev/ttyUSB0
ISDN = 0
Phone = *99#
Password = (usually blank, or ISP name again)
Username = 


```4. There it is! type

```
sudo wvdial
```

and you're in. Don't worry if it takes some 30 sec to connect, apparently it has to thik about it for a while. Ctrl-c to disconnect.

5. If you want something more elegant, just configure gnome-ppp with the same stuff you put into wvdial.conf, and start it as root.

---

### Post by acho on 2009-04-25
i have some problem. Can u fix it?
i got this on my console
==================================================

Scanning your serial ports for a modem.

Modem Port Scan<*1>: S0   S1   S2   S3   


Sorry, no modem was detected!  Is it in use by another program?
Did you configure it properly with setserial?

Please read the FAQ at [http://open.nit.ca/wiki/?WvDial](http://open.nit.ca/wiki/?WvDial)

If you still have problems, send mail to <wvdial-list@lists.nit.ca>.
==========================================================

:confused::confused::confused:

---

### Post by pvicc on 2009-08-22
Its very strange. My Thinkpad Z61T is a updated ubuntu box 9.04. When I connected my Bandluxe C120, there is no light, no mounted disc as informed in this forum. I installed wvdial. No change. lsusb produced no device connected. I lost my hope. 
Just today when i again plugged in, and forgot that it was plugged in. After one hour, i wanted to switch off my blue tooth using Fn+F5. As usuall the wifi & blue tooth switched off. Within a second there was a life in this modem and started to blink green, Red and automatic mobile broad band configuration window came with all the Indonesia providers.

I did not do any configuration mentioned in this forum.

Now everytime, i plugin the modem, it blinks green, blue :):guitar:

cheers

---

### Post by pvicc on 2009-08-22
my lsusb now
Bus 001 Device 004: ID 0c45:627b Microdia PC Camera (SN9C201)
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 0483:2016 SGS Thomson Microelectronics Fingerprint Reader
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 046d:c51b Logitech, Inc. 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 1a8d:1002  
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

---

### Post by pvicc on 2009-08-22
I did not use wvdial, The network manager is able to identify the Mobile brandband and connect.

Cheers

---

### Post by vdaraujo on 2009-08-23
I am using Ubuntu 8.10 with the latest updates in a Sony Vaio VGN-SR150A.
I managed to configure and use the HDSPA USB 3G modem from Bandrich,
the Bandluxe C120, adapting a configuration script made by the maker
of this USB card for the Eee PC. You can download all the files from
this link

[http://www.bandrich.com/Data-Card_C100_down_3.html](http://www.bandrich.com/Data-Card_C100_down_3.html)

and click download. 

You get a file named

EeePC patch.zip

Uncompress it and you get two pdf files and another compressed file

bandluxe-eeepc.tar.bz2

Uncompress this file too. You should get a directory named bandluxe-eeepc.

Inside you have a script eeepc3g.sh.

Do not run this script just yet!
Unless you are using a Eee PC with the version of the
gnu-linux operating system that is shipped from Asus!

This script reads

============FILE eeepc3g.sh====================================

#!/bin/sh


MODDIR=/lib/modules/`uname -r`

echo "Backup file modules.alias"
cp -v ${MODDIR}/modules.alias ./modules-eeepc.alias
echo "Patching file modules.alias"
sed -f vidpid.sed ./modules-eeepc.alias > ${MODDIR}/modules.alias 


echo "Unload the kernel module"
/sbin/rmmod option

echo "Backup file option.ko"
cp -v ${MODDIR}/kernel/drivers/usb/serial/option.ko ./option-eeepc.ko 
echo "Add support of Bandluxe Data Card"
cp -v option-bandluxe.ko ${MODDIR}/kernel/drivers/usb/serial/option.ko 

echo "Rules for auto switch from CDROM to Modem"
cp -vf 10-bandluxe.rules /etc/udev/rules.d/10-bandluxe.rules

mkdir -p /usr/share/hal/fdi/preprobe/20thirdparty/
cp -vf bandluxe.fdi /usr/share/hal/fdi/preprobe/20thirdparty/bandluxe.fdi

============END of FILE eeepc3g.sh====================================

You should comment everything which is kernel-specific, as follows,
and save it in a new file named say "Bandluxe-c120.sh" IN THE SAME
DIRECTORY bandluxe-eeepc.

==================FILE Bandluxe-c120.sh=============================
#!/bin/sh


MODDIR=/lib/modules/`uname -r`

echo "Backup file modules.alias"
cp -v ${MODDIR}/modules.alias ./modules-eeepc.alias
echo "Patching file modules.alias"
sed -f vidpid.sed ./modules-eeepc.alias > ${MODDIR}/modules.alias 


#echo "Unload the kernel module"
#/sbin/rmmod option

#echo "Backup file option.ko"
#cp -v ${MODDIR}/kernel/drivers/usb/serial/option.ko ./option-eeepc.ko 
#echo "Add support of Bandluxe Data Card"
#cp -v option-bandluxe.ko ${MODDIR}/kernel/drivers/usb/serial/option.ko 

echo "Rules for auto switch from CDROM to Modem"
cp -vf 10-bandluxe.rules /etc/udev/rules.d/10-bandluxe.rules

mkdir -p /usr/share/hal/fdi/preprobe/20thirdparty/
cp -vf bandluxe.fdi /usr/share/hal/fdi/preprobe/20thirdparty/bandluxe.fdi

==============End of File Bandluxe-c120.sh=============================

If you just edited the file with gedit, then it will remain an executable
file and you can just run it with

cd "path to bandluxe-eeepc"
sudo ./Bandluxe-c120.sh

The script now just adds some rules for the system udev to recognize the
Bandluxe C120 USB device, let it open the modem devices /dev/ttyUSBx 
where x depends on the installed hardware of your machine,
but when the Bandluxe tries to identify itself as a CDROM the udev system
sends a kind of sleep signal and ignores this device. It keeps the other
ttyUSBx devices open however, and this enables one to then connect to the
modem through either gnome-ppp or kppp or even NetworkManager in 
Ubuntu 9.04.

I cannot put this 3G USB modem to work through NetworkManager in my Ubuntu 8.10, I can only use it through gnome-ppp (you need probably
to install gnome-ppp with synaptic first) as follows.

Create a Laucher on your desktop clicking the right mouse buttom on
the background of the desktop and select "Create Launcher". In the
window that opens choose Application, give it a name to appear in your
desktop, click on the icon on the upper left of the window to choose some
icon for the desktop, and on the command entry form write

gksudo gnome-ppp

since we have to open the gnome frontend to ppp with root privileges.
Click ok and you shoudl have a new icon on your desktop. Double-click it,
enter your password and then gnome-ppp window opens.

Write the unsername and passwork of your 3G connection, then the
phone number to dial (should be something like *99#, depending on
the GSM operator) and then click on SETUP.

Here you should write \dev\ttyUSBx where x=0,1,2,... on the DEVICE entry field, depending on your hardware -- you should use lsusb or dmesg to find out which is the right number for you (more on this below). Then

TYPE choose Analog Modem
Speed: choose the highest 460800

then click on "Init Strings" and enter the following

Inti2 = AT+CGDCONT=1,"IP","www address of your provider"
Init3 = at+cgatt=1
Init4 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0

On the Networking tab choose Dynamic IP address and you may choose also
Automatic DNS. I prefer to use Open DNS, so I click Manual DNS and enter

DNS1 = 208.67.222.222
DNS2 = 208.67.220.220

On the options tab I selected:

Abort connecting if no dialtone
Check carrier line
Check default route
Ignore terminal strings (stupid mode)

and 

Idle time is set to 0 (disabled).

You can close the window and get back to the gnome-ppp window.

Now, plug-in the C120 USB and wait some 15 seconds. Then click
Connect on the small gnome-ppp window. You should be online in no time.

The setup of the gnome-ppp is kept between sessions so you should
make this setup only once.

Finally, to find out which /dev/ttyUSBx to write in the device form above,
I did this: pluged the USB modem C120, waited half a minute, open a terminal and entered "dmesg". The last few lines are

[128169.940927] usb 4-1: new full speed USB device using uhci_hcd and address 4
[128170.108853] usb 4-1: configuration #1 chosen from 1 choice
[128170.112856] scsi11 : SCSI emulation for USB Mass Storage devices
[128170.113735] usb-storage: device found at 4
[128170.113740] usb-storage: waiting for device to settle before scanning
[128170.122409] option 4-1:1.1: GSM modem (1-port) converter detected
[128170.122565] usb 4-1: GSM modem (1-port) converter now attached to ttyUSB0
[128170.133087] option 4-1:1.2: GSM modem (1-port) converter detected
[128170.133177] usb 4-1: GSM modem (1-port) converter now attached to ttyUSB1

The last lines show that I got two new devices

/dev/ttyUSB0
/dev/ttyUSB1

I use /dev/ttyUSB1 on the devices form field of the gnome-ppp setup.
It works well and fast!


Hope this helps you folks here!

---

### Post by LSkinn on 2009-10-07
@[vdaraujo]("http://ubuntuforums.org/member.php?u=641618")

just wanna say Thanks a lot for posting this. Tried it on Jaunty with the bandluxe c120 and it worked! :D 
I'll be posting a blog post about this and I'll link this forum and you :D

many many thanks to you! :)

---

### Post by nilufer on 2009-11-08
Hi vdaraujo,

That works really well on my just installed Ubuntu 9.10.
I have been waiting for more than a year to get this device work with Ubuntu but no look until today.
Its just works.
I did not do a single step other than the mentioned ones.
Thank you very much.

Hope to remove the Windows installation soon and use the Ubuntu alone as the Internet Modem finally works with Ubuntu.

Here my gnome-ppp connection window.
[IMG]http://i36.tinypic.com/o8iirm.jpg[/IMG]

Hurray,
Nilufer

---

### Post by techniquehelp on 2009-12-17
Hi this can be help to you

[http://www.techniquehelp.com/Hsdpa.html](http://www.techniquehelp.com/Hsdpa.html)

Tnx

---

### Post by ddreamer on 2010-08-19
Hi, all:
    Thanks to vdaraujo at #9 of this thread. The method works like a magic in Ubuntu 10.04. I have worked on this problem for so long. Thank you again, vdaraujo. I have set up NetworkManager. I use "fetims" for APN, and "*99#" for number since the SIM card is obtained from Far EasTone.

    The exact steps(commands in the terminal are highlighted):

[LIST=1]
[*]Download the driver for EeePC from
[http://www.bandrich.com/Data-Card_C100_down_3.html](http://www.bandrich.com/Data-Card_C100_down_3.html) to "~/bandluxec120"
[*]Unzip it at "~/bandluxec120" by "**unzip EeePC patch.zip**", and you get bandluxe-eeepc.tar.bz2 in addition to ".pdf" files.
[*]At "~/bandluxec120", untar bandluxe-eeepc.tar.bz2 by
"**tar xjvf bandluxe-eeepc.tar.bz2**", you get eeepc3g.sh
[*]At "~/bandluxec120","**cp eeepc3g.sh bandluxe-c120.sh**"
[*]Modify bandluxe-c120.sh by putting some "#"(no quotes, in red) at the beginning of some lines as below:[B]
[I]#!/bin/sh


MODDIR=/lib/modules/`uname -r`

echo "Backup file modules.alias"
cp -v ${MODDIR}/modules.alias ./modules-eeepc.alias
echo "Patching file modules.alias"
sed -f vidpid.sed ./modules-eeepc.alias > ${MODDIR}/modules.alias 


[COLOR=Red]#[/COLOR]echo "Unload the kernel module"
[COLOR=Red]#[/COLOR]/sbin/rmmod option

[COLOR=Red]#[/COLOR]echo "Backup file option.ko"
[COLOR=Red]#[/COLOR]cp -v ${MODDIR}/kernel/drivers/usb/serial/option.ko ./option-eeepc.ko 
[COLOR=Red]#[/COLOR]echo "Add support of Bandluxe Data Card"
[COLOR=Red]#[/COLOR]cp -v option-bandluxe.ko ${MODDIR}/kernel/drivers/usb/serial/option.ko 

echo "Rules for auto switch from CDROM to Modem"
cp -vf 10-bandluxe.rules /etc/udev/rules.d/10-bandluxe.rules

mkdir -p /usr/share/hal/fdi/preprobe/20thirdparty/
cp -vf bandluxe.fdi /usr/share/hal/fdi/preprobe/20thirdparty/bandluxe.fdi[/I][/B]
[*]Save the file. Run "sudo ./bandluxe-c120.sh"
[*]Reboot
[*]Plug the BandRich BandLuxe C120 into a USB hub.
[*]It will connect to the internet like a magic.
[/LIST]

I heard from the company that this model is sort of old (though mine looked new), and they don't support it for Ubuntu 10.04. The engineer tried upgrading the firmware and said that it also worked. This might be useful for people who are in Taipei, Taiwan ROC. The website of the company: [http://www.bandrich.com/](http://www.bandrich.com/) But, without upgrade of firmware, the above method really worked!!

Hope you guys work it out as well. Now I am connecting through the BandLuxe C120 in Ubuntu 10.04 Lucid Lynx !!! :lolflag:

---

