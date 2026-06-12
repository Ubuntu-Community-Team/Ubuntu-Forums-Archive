---
title: "DRIVERS: HP Color LaserJet Pro MFP M479fdw"
date: 2020-08-14
forum: Hardware
---

### Post by suomalainen on 2020-08-14
Hello,

I have a HP Color LaserJet Pro MFP M479fdw but in Ubuntu 18.04 it is being recognized as HPColor Laserjet-Pro M478f-9f. I guess this is a range within which mine would be included?

I can print from the printer just fine but 'simple scan' and Sane will not work.

What do I need to do?

Thanks,

Suomalainen

---

### Post by Autodave on 2020-08-15
First off, your driver is fine: the number is to a range of models, not necessarily to a specific model. So, no worries there.  To scan, you need to install *hplip *from the repositories.  Be sure to obtain that through *synaptic* package manager rather than the Software manager as the one in there appears to be a snap package and I see complaints about that one.

---

### Post by CelticWarrior on 2020-08-15
> **Autodave said:**
> First off, your driver is fine: the number is to a range of models, not necessarily to a specific model. So, no worries there.  To scan, you need to install *hplip *from the repositories.  Be sure to obtain that through *synaptic* package manager rather than the Software manager as the one in there appears to be a snap package and I see complaints about that one.

... or just run 'sudo apt install hplip-gui'... This will install all the dependencies in one go.

---

### Post by suomalainen on 2020-08-15
Thanks to everyone that has replied thus far!!!

I reinstalled the HPLIP via 'synaptic package manager" and now I have a HP icon in the top panel. See attached. The weirdthing about this HP panel icon is that I was able to open 'settings' just one time. Never made any system adjustments of any kind and it worked just once. Really weird. 

When I tried to launch Sane or simple scan I get the message HPLIP Device Status. See also attached.

Nonetheless printing appears to work fine for time being although I can print to both sides of page and I cannot scan with the AIO scanner.

I've spend 4 hours trying to solve this myself and now its time to ask for assistance.

Thanks again,

Suomalainen[ATTACH=CONFIG]286704[/ATTACH][ATTACH=CONFIG]286706[/ATTACH]

---

### Post by suomalainen on 2020-08-15
Although I'm having a ton of problems getting everything to work with HPLIP I came across a post where a guy got so fed up with HP that he discovered a piece of SW called VueScan. I downloaded a trial version and it worked intermediately! In seconds. But it comes with a $100 price tag.

Would still like to get my HP sw working if possible. 

Looking forward to hearding from you!

Suomalainen

---

### Post by brian_p on 2020-08-15
The problem is that you can print but not scan?

You never said whether you are on the network or using USB.

Give the outputs of ```
lpinfo -v
``` ```
lpstat -t
```

---

### Post by suomalainen on 2020-08-15
@Brian and Everyone else, I am connected to the desktop via USB.

Below is the output I received per Brian's request. Looking forward to getting this licked!

paavo@Paavo:~$ lpinfo -v
network ipp
network beh
file cups-brf:/
serial serial:/dev/ttyS0?baud=115200
serial serial:/dev/ttyS4?baud=115200
network http
network socket
network ipps
network https
network lpd
direct parallel:/dev/lp0
network smb
direct hp
direct hpfax
paavo@Paavo:~$ lpstat -t
scheduler is running
no system default destination
device for Generic-CUPS-BRF-Printer: cups-brf:/
device for Zebra-LP2844: usb://Zebra/LP2844?serial=42A055102024
Generic-CUPS-BRF-Printer accepting requests since Sat 15 Aug 2020 09:46:21 AM EDT
Zebra-LP2844 accepting requests since Fri 14 Aug 2020 08:23:24 PM EDT
printer Generic-CUPS-BRF-Printer is idle.  enabled since Sat 15 Aug 2020 09:46:21 AM EDT
printer Zebra-LP2844 is idle.  enabled since Fri 14 Aug 2020 08:23:24 PM EDT
paavo@Paavo:~$

---

### Post by brian_p on 2020-08-15
> **suomalainen said:**
> @Brian and Everyone else, I am connected to the desktop via USB.

Below is the output I received per Brian's request. Looking forward to getting this licked!

paavo@Paavo:~$ lpinfo -v

This output doesn't show any USB printer connection
> 
paavo@Paavo:~$ lpstat -t
scheduler is running
no system default destination
device for Generic-CUPS-BRF-Printer: cups-brf:/
device for Zebra-LP2844: usb://Zebra/LP2844?serial=42A055102024

You have these two printer connections. *cups-brf:/* is for a braille print queue. Is this wanted? The other device is for a Zebra printer. There isn't any connection to a LaserJet.

Mystifying. I cannot understand how you are printing.

---

### Post by brian_p on 2020-08-15
Forgot: What does ```
scanimage -L 
``` give?

---

### Post by suomalainen on 2020-08-15
scanimage -L gives:

No scanners were identified. If you were expecting something different,
check that the scanner is plugged in, turned on and detected by the
sane-find-scanner tool (if appropriate). Please read the documentation
which came with this software (README, FAQ, manpages).


AND lsusb gives:

 lsusb
Bus 002 Device 003: ID 058f:6362 Alcor Micro Corp. Flash Card Reader/Writer
Bus 002 Device 002: ID 0c45:6340 Microdia Camera
Bus 002 Device 004: ID 03f0:c52a Hewlett-Packard 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 003: ID 046d:c517 Logitech, Inc. LX710 Cordless Desktop Laser
Bus 004 Device 002: ID 046d:c52f Logitech, Inc. Unifying Receiver
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


My printer is listed as the usb Hewlwtt Packard.

Thanks!

---

### Post by suomalainen on 2020-08-15
I ran the lpstat -t again and got different result this timne. Now it says:

scheduler is running
system default destination: HP_Color_LaserJet_Pro_M478f_9f_B1E168_
device for HP_Color_LaserJet_Pro_M478f_9f_B1E168_: ipps://HPE8D8D1B1E168.local:631/ipp/print
device for Zebra-LP2844: usb://Zebra/LP2844?serial=42A055102024
HP_Color_LaserJet_Pro_M478f_9f_B1E168_ accepting requests since Sat 15 Aug 2020 05:31:52 PM EDT
Zebra-LP2844 accepting requests since Fri 14 Aug 2020 08:23:24 PM EDT
printer HP_Color_LaserJet_Pro_M478f_9f_B1E168_ is idle.  enabled since Sat 15 Aug 2020 05:31:52 PM EDT
printer Zebra-LP2844 is idle.  enabled since Fri 14 Aug 2020 08:23:24 PM EDT
paavo@Paavo:~$

---

### Post by brian_p on 2020-08-15
> **suomalainen said:**
> scanimage -L gives:

No scanners were identified. If you were expecting something different,
check that the scanner is plugged in, turned on and detected by the
sane-find-scanner tool (if appropriate). Please read the documentation
which came with this software (README, FAQ, manpages).


AND lsusb gives:

 lsusb
Bus 002 Device 003: ID 058f:6362 Alcor Micro Corp. Flash Card Reader/Writer
Bus 002 Device 002: ID 0c45:6340 Microdia Camera
Bus 002 Device 004: ID 03f0:c52a Hewlett-Packard 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 003: ID 046d:c517 Logitech, Inc. LX710 Cordless Desktop Laser
Bus 004 Device 002: ID 046d:c52f Logitech, Inc. Unifying Receiver
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


My printer is listed as the usb Hewlwtt Packard.

Thanks!

Thanks. I am still mystified. CUPS says you do not have a LaserJet on USB.

Would using a network connection be a possibility? If so, ```
avahi-browse -rt _ipp._tcp
``` and ```
avahi-browse -rt _uscan._tcp
``` would give useful outputs to know.

---

### Post by brian_p on 2020-08-15
> device for HP_Color_LaserJet_Pro_M478f_9f_B1E168_: ipps://HPE8D8D1B1E168.local:631/ipp/print

This is a network URI, not a USB URI.

---

### Post by brian_p on 2020-08-15
> This is a network URI, not a USB URI. 

Are you running ippusbxd?

```
ps ax | grep ippusbxd
```

---

### Post by brian_p on 2020-08-15
If you are running ippusbxd, the two avahi-browse commands should work with the USB connection.

---

### Post by suomalainen on 2020-08-15
@Brian, Thanks for helping me. Here are the details you requested.

paavo@Paavo:~$ avahi-browse -rt _ipp._tcp
+ wlp5s0 IPv6 HP Color LaserJet Pro M478f-9f [B1E168]       Internet Printer     local
+ wlp5s0 IPv4 HP Color LaserJet Pro M478f-9f [B1E168]       Internet Printer     local
= wlp5s0 IPv6 HP Color LaserJet Pro M478f-9f [B1E168]       Internet Printer     local
   hostname = [HPE8D8D1B1E168.local]
   address = [192.168.1.6]
   port = [631]
   txt = ["Fax=T" "rfo=ipp/faxout" "mopria-certified=2.0" "Scan=T" "kind=document" "URF=CP1,MT1-2-8-9-10-11,PQ3-4-5,RS600,SRGB24,OB10,W8,DEVW8,DEVRGB24,ADOBERGB24,DM3,IS19-1-2,V1.4,FN3" "PaperMax=legal-A4" "pdl=application/vnd.hp-PCL,application/vnd.hp-PCLXL,application/postscript,application/msword,application/pdf,image/jpeg,image/urf,image/pwg-raster,application/PCLm,application/vnd.openxmlformats-officedocument.wordprocessingml.document,application/vnd.m" "Duplex=T" "Color=T" "usb_MDL=Color LaserJet Pro M478f-9f" "usb_MFG=HP" "ty=HP Color LaserJet Pro M478f-9f" "product=(HP Color LaserJet Pro M478f-9f)" "UUID=7aa95d78-8df0-58a8-ca66-6a90258f9ea7" "rp=ipp/print" "TLS=1.2" "qtotal=1" "priority=20" "note=" "adminurl=http://HPE8D8D1B1E168.local./#hId-pgAirPrint" "txtvers=1"]
= wlp5s0 IPv4 HP Color LaserJet Pro M478f-9f [B1E168]       Internet Printer     local
   hostname = [HPE8D8D1B1E168.local]
   address = [192.168.1.6]
   port = [631]
   txt = ["Fax=T" "rfo=ipp/faxout" "mopria-certified=2.0" "Scan=T" "kind=document" "URF=CP1,MT1-2-8-9-10-11,PQ3-4-5,RS600,SRGB24,OB10,W8,DEVW8,DEVRGB24,ADOBERGB24,DM3,IS19-1-2,V1.4,FN3" "PaperMax=legal-A4" "pdl=application/vnd.hp-PCL,application/vnd.hp-PCLXL,application/postscript,application/msword,application/pdf,image/jpeg,image/urf,image/pwg-raster,application/PCLm,application/vnd.openxmlformats-officedocument.wordprocessingml.document,application/vnd.m" "Duplex=T" "Color=T" "usb_MDL=Color LaserJet Pro M478f-9f" "usb_MFG=HP" "ty=HP Color LaserJet Pro M478f-9f" "product=(HP Color LaserJet Pro M478f-9f)" "UUID=7aa95d78-8df0-58a8-ca66-6a90258f9ea7" "rp=ipp/print" "TLS=1.2" "qtotal=1" "priority=20" "note=" "adminurl=http://HPE8D8D1B1E168.local./#hId-pgAirPrint" "txtvers=1"]
paavo@Paavo:~$ avahi-browse -rt _uscan._tcp
+ wlp5s0 IPv6 HP Color LaserJet Pro M478f-9f [B1E168]       _uscan._tcp          local
+ wlp5s0 IPv4 HP Color LaserJet Pro M478f-9f [B1E168]       _uscan._tcp          local
= wlp5s0 IPv4 HP Color LaserJet Pro M478f-9f [B1E168]       _uscan._tcp          local
   hostname = [HPE8D8D1B1E168.local]
   address = [192.168.1.6]
   port = [8080]
   txt = ["mopria-certified-scan=1.2" "duplex=T" "is=platen,adf" "cs=binary,color,grayscale" "pdl=application/octet-stream,application/pdf,image/jpeg" "ty=HP Color LaserJet Pro M478f-9f" "rs=eSCL" "representation=images/printer.png" "vers=2.63" "UUID=7aa95d78-8df0-58a8-ca66-6a90258f9ea7" "note=" "adminurl=http://HPE8D8D1B1E168.local." "txtvers=1"]
= wlp5s0 IPv6 HP Color LaserJet Pro M478f-9f [B1E168]       _uscan._tcp          local
   hostname = [HPE8D8D1B1E168.local]
   address = [192.168.1.6]
   port = [8080]
   txt = ["mopria-certified-scan=1.2" "duplex=T" "is=platen,adf" "cs=binary,color,grayscale" "pdl=application/octet-stream,application/pdf,image/jpeg" "ty=HP Color LaserJet Pro M478f-9f" "rs=eSCL" "representation=images/printer.png" "vers=2.63" "UUID=7aa95d78-8df0-58a8-ca66-6a90258f9ea7" "note=" "adminurl=http://HPE8D8D1B1E168.local." "txtvers=1"]
paavo@Paavo:~$ ps ax | grep ippusbxd
 2677 pts/0    S+     0:00 grep --color=auto ippusbxd

---

### Post by brian_p on 2020-08-16
Hello suomalainen,

You are not using ippusbxd but have a wireless connection to the device on the wlp5s0 interface. This is ok. Nothing to worry about.

The are two ways to get you scanning. The first involves altering the printing setup and using HPLIP. I m not going to follow that route because what you have already is good and I will not interfere with it.

The second way is to go to [https://github.com/alexpevzner/sane-airscan](https://github.com/alexpevzner/sane-airscan) and download and install sane-airscan. The file you need is at [https://download.opensuse.org/repositories/home:/pzz/xUbuntu_18.04/amd64/](https://download.opensuse.org/repositories/home:/pzz/xUbuntu_18.04/amd64/).

After testing, I would be very interested in what you get for ```
scanimage -L
``` and ```
airscan-discover
```

You may find it useful to read [https://wiki.debian.org/SaneOverNetwork#escl](https://wiki.debian.org/SaneOverNetwork#escl)

---

### Post by suomalainen on 2020-08-16
Hi Brian and thank you for getting me up and running! I really appreciate your help and assistance on this thank you!!!

I have never owned had such a nice printer as this one before that when I set it up I used usb cable and also I connected the printer to Wifi. I guess thats the reason why it is seen as a network printer?

Here is what you asked for:

paavo@Paavo:~$ scanimage -L
device `airscan:e0:HP Color LaserJet Pro M478f-9f [B1E168]' is a eSCL HP Color LaserJet Pro M478f-9f [B1E168] eSCL network scanner
paavo@Paavo:~$ airscan-discover
[devices]
  HP Color LaserJet Pro M478f-9f [B1E168] = [http://192.168.1.6:8080/eSCL/](http://192.168.1.6:8080/eSCL/), eSCL
  HP Color LaserJet Pro M478f-9f [B1E168] = [https://192.168.1.6:443/eSCL/](https://192.168.1.6:443/eSCL/), eSCL
  HP Color LaserJet Pro M478f-9f [B1E168] = [http://192.168.1.6:53048](http://192.168.1.6:53048), WSD
  HP Color LaserJet Pro M478f-9f [B1E168] = [http://[Fe80::ead8:d1FF:Feb1:e169%253]:53048](http://[Fe80::ead8:d1FF:Feb1:e169%253]:53048), WSD
paavo@Paavo:~$ 

Would you by any chance feel up to helping me with my  Zebra LP 2844 label printer?

Thanks again!

Suomalainen

---

### Post by brian_p on 2020-08-16
> **suomalainen said:**
> Hi Brian and thank you for getting me up and running! I really appreciate your help and assistance on this thank you!!!

Glad it worked out for you, suomalainen. You are now using driverless printing and scanning. HPLIP is not involved, so you can now decide whether to remove it or not.

> 
Would you by any chance feel up to helping me with my  Zebra LP 2844 label printer?

I know nothing about label printers. Best would be to start a new post.

Thanks for your engagement with the issue and the info. Please do not forget to mark the thread as solved.

---

