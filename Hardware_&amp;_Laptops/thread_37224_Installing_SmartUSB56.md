---
title: "Installing SmartUSB56"
date: 2005-05-26
forum: Hardware &amp; Laptops
---

### Post by Ee_ on 2005-05-26
Hi..

I need to know how to install SmartUSB56 into my Ubuntu (5.04). After following [this](http://www.ubuntulinux.org/wiki/BinaryDriverHowto) tutorial.. i get this error msg everytime i plug my modem into the USB port.

> 
May 26 22:47:29 localhost kernel: ohci_hcd 0000:00:02.1: wakeup
May 26 22:47:30 localhost kernel: usb 2-3: new full speed USB device using ohci_hcd and address 4
May 26 22:47:30 localhost usb.agent[7683]:      slusb: can't be loaded
May 26 22:47:30 localhost kernel: slusb: Unknown symbol usb_endpoint_halted
May 26 22:47:30 localhost kernel: slusb: Unknown symbol usb_endpoint_halted



This is the msg that i got when i restart the daemon thing using */etc/init.d/sl-modem-daemon restart*

> 
Shutting down SmartLink Modem driver normally ... no slmodemd daemon running.
Loading ALSA modem driver into kernel ... done.
Starting SmartLink Modem driver for: .
Creating /dev/modem symlink, pointing to: /dev/ttySL0.


FYI, i've installed these packages before compiling the drivers

- module-assistant_0.9_all.deb
- sl-modem-source_2.9.9a-1_i386.deb
- sl-modem-daemon_2.9.9a-1_i386.deb

I also got this warning msg when i build the driver

> 
Warning: could not find /media/fat/download/terai/modules/sl-modem/drivers/.amrlibs.o.cmd for 

/media/fat/download/terai/modules/sl-modem/drivers/amrlibs.o
*** Warning: "usb_endpoint_halted" [/media/fat/download/terai/modules/sl-modem/drivers/slusb.ko] undefined!


So, what should i do ? I tried googling and searching in the forum but none of them seems to help me.. ok, maybe i've missed the correct soloution  :neutral: . I've tried this for 2 days, so, please, can anyone help me so that i can get connected to the internet using linux for the first time :lol:

---

### Post by popot on 2007-04-09
This worked for me, I have a dell dimension 8200, P4 2GHZ Machine, on Ubuntu Edgy Eft 6.10 Server, the modem is Aztech UM9100-U. I used: [ungrab-winmodem.tar.gz]("http://phep2.technion.ac.il/linmodems/packages/smartlink/ungrab-winmodem.tar.gz") 
[slmodem-2.9.11-20070204.tar.gz ]("http://phep2.technion.ac.il/linmodems/packages/smartlink/slmodem-2.9.11-20070204.tar.gz")
[sl-modem-daemon_2.9.10+2.9.9d+e-pre2-5build1_i386.deb]("http://altruistic.lbl.gov/mirrors/ubuntu/pool/multiverse/s/sl-modem/sl-modem-daemon_2.9.10+2.9.9d+e-pre2-5build1_i386.deb")

Follow [Howto get Smartlink winmodem working in edgy Method A]("http://ubuntuforums.org/showthread.php?t=190728") to the letter, stop at Step 9. Hat tip to Matchless.

At Step 10, I did a dpkg - i sl-modem-daemon_2.9.10+2.9.9d+e-pre2-5build1_i386.deb

This is followed by,
/etc/default/sl-modem-daemon, change all instances of slamr to slusb and SLMODEMD_DEVICE=auto to SLMODEMD_DEVICE=slusb0. SLMODEMD_COUNTRY= ; choose your appropriate country, use slmodemd --countrylist, to find out the available countries.

In /etc/modprobe.d/sl-modem-daemon.modutils,

Change: (if you can't locate this line, you might be at the other file with the same name but different location)
install slamr modprobe --ignore-install ungrab-winmodem ; modprobe --ignore-install slamr ; test -e /dev/slamr0 || (/bin/mknod -m 660 /dev/slamr0 c 242 0 2>/dev/null && chgrp dialout /dev/slamr0)

To:
install slusb modprobe --ignore-install slusb ; test -e /dev/slusb0 || (/bin/mknod -m 660 /dev/slusb0 c 243 0 2>/dev/null && chgrp dialout /dev/slusb0)

Continue with step 11 of [Howto get Smartlink winmodem working in edgy Method A]("http://ubuntuforums.org/showthread.php?t=190728") and the rest. Tried with both Kppp and wvdial and hylafax (sending and receiving), works great.

;p
Better late than never.

Ps:
For Feisty Fawn

Instead of ungrab-winmodem, use [ungrab-winmodem-20070505.tar.gz]("http://phep2.technion.ac.il/linmodems/packages/smartlink/ungrab-winmodem-20070505.tar.gz") instead.

Instead of slmodem-2.9.11-20061021.tar.gz, use [slmodem-2.9.11-20070813.tar.gz]("http://phep2.technion.ac.il/linmodems/packages/smartlink/slmodem-2.9.11-20070813.tar.gz").

Stop at step 10 instead of 9. Instead of dpkg - i sl-modem-daemon_2.9.10+2.9.9d+e-pre2-5build1_i386.deb, stop at step 10 of [Howto get Smartlink winmodem working in edgy Method A]("http://ubuntuforums.org/showthread.php?t=190728").

Everything else follow above. 

Maybe a bug!!! I have used wvdial, pon, gnome-ppp, upon disconnection and reconnection, modem not found.
To rectify it,
> sudo modprobe ungrab-winmodem
sudo modprobe slusb
sudo /etc/init.d/sl-modem-daemon restart 
or just restart your computer.

Can anyone help?

---

### Post by tabo101 on 2007-06-04
> **popot said:**
> This worked for me, I have a dell dimension 8200, P4 2GHZ Machine, on Ubuntu Edgy Eft 6.10 Server, the modem is Aztech UM9100-U. I used: [ungrab-winmodem.tar.gz]("http://phep2.technion.ac.il/linmodems/packages/smartlink/ungrab-winmodem.tar.gz") 
[slmodem-2.9.11-20070204.tar.gz ]("http://phep2.technion.ac.il/linmodems/packages/smartlink/slmodem-2.9.11-20070204.tar.gz")
[sl-modem-daemon_2.9.10+2.9.9d+e-pre2-5build1_i386.deb]("http://altruistic.lbl.gov/mirrors/ubuntu/pool/multiverse/s/sl-modem/sl-modem-daemon_2.9.10+2.9.9d+e-pre2-5build1_i386.deb")

Follow [Howto get Smartlink winmodem working in edgy Method A]("http://ubuntuforums.org/showthread.php?t=190728") to the letter, stop at Step 10. Hat tip to Matchless.

At Step 10, I did a dpkg - i sl-modem-daemon_2.9.10+2.9.9d+e-pre2-5build1_i386.deb

This is followed by,
/etc/default/sl-modem-daemon, change all instances of slamr to slusb and SLMODEMD_DEVICE=auto to SLMODEMD_DEVICE=slusb0. SLMODEMD_COUNTRY= ; choose your appropriate country, use slmodemd --countrylist, to find out the available countries.

In /etc/modprobe.d/sl-modem-daemon.modutils,

Change: (if you can't locate this line, you might be at the other file with the same name but different location)
install slamr modprobe --ignore-install ungrab-winmodem ; modprobe --ignore-install slamr ; test -e /dev/slamr0 || (/bin/mknod -m 660 /dev/slamr0 c 242 0 2>/dev/null && chgrp dialout /dev/slamr0)

To:
install slusb modprobe --ignore-install slusb ; test -e /dev/slusb0 || (/bin/mknod -m 660 /dev/slusb0 c 243 0 2>/dev/null && chgrp dialout /dev/slusb0)

Continue with step 11 of [Howto get Smartlink winmodem working in edgy Method A]("http://ubuntuforums.org/showthread.php?t=190728") and the rest. Tried with both Kppp and wvdial and hylafax (sending and receiving), works great.

;p
Better late than never.

Hi. I´m running Ubuntu 6.10 Edgy and I´m having a hard time setting up with my usb softmodem. I followed your instructions and so far so good. Can you post you /dev/wvdial.conf file to see which configuration you are using for wvdial? Please mask you username/password and tel# for privacy.

This would be of great  help since I have found many different configurations for wvdial out there and they all change parameters.

Best regards!

---

### Post by popot on 2007-06-07
I used wvdialconf to generate the wvdial, I did not do it myself, as for the /dev/ttySL0, I typed "ls /dev/slusb0", and it gave me "slusb0 -> ttySL0". And so I used "Modem = /dev/ttySL0". 

How did I get slusb0?
sudo modprobe slusb
dmesg | grep slusb 
from [Howto get Smartlink winmodem working in edgy Method A]("http://ubuntuforums.org/showthread.php?t=190728")
You must do it before reboot.

wvdial.conf,

> [Dialer Defaults]
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 
Carrier Check = no
Modem Type = Analog Modem
Baud = 460800
New PPPD = yes
Modem = /dev/ttySL0
ISDN = 0
Phone = 
Password = 
Username = 

Hope this helps!!! :)

---

