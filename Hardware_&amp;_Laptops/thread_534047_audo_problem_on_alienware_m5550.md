---
title: "audo problem on alienware m5550"
date: 2007-08-24
forum: Hardware &amp; Laptops
---

### Post by sabbath06 on 2007-08-24
I just installed feisty 64 bit on my alienware m5550 notebook. When I had windows on this machine, the audio would stop coming out of the built in speakers when I would plug in a set of headphones. Now, on feisty, when I plug in headphones, the sound continues to come out of the built in speakers as well as the headphones. Is there anyway to get the sound to only come out of the headphones?

lcpci tells me I have 

00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)

Also there is a volume knob on the side of the unit that worked under windows but does not work under ubuntu.

---

### Post by Iamiko on 2008-03-13
I have the same laptop and the same problem. It's nice when I need a little more treble to counter my very bass-intensive portable speakers but annoying when I want to listen to my music privately :(

A class-mate of mine has an idea what might solve it but we haven't tried it yet. WIll try it and update here if it works or not.

---

### Post by Kongzi on 2008-03-17
I've been having the same problem. My brother and I have tried installing the realtek sound driver for linux on their sight but haven't made any progress there either. The driver seems to simply not work. I recommend emailing realtek for help.

---

### Post by genfly on 2008-04-28
Also have the same problem :(

i did a lot of research and found the laptop is the same as the uniwill model...

[http://www.uniwill.com/UserDownload/P53In/P53In.php](http://www.uniwill.com/UserDownload/P53In/P53In.php)


can anyone get these sound drivers for linux?!

thanks in advance!

---

### Post by genfly on 2008-05-02
can noone figure out how to solve this problem? :(

The uniwill P53IN laptop is sold to tons of companies such as alienware, novatech, computerplnet etc...

A LOT of people have this laptop... there has to be a solution somewhere


in windows xp this problem is solved by installing these windows drivers:

[http://www.uniwill.com/UserDownload/P53In/P53In.php](http://www.uniwill.com/UserDownload/P53In/P53In.php)

---

### Post by genfly on 2008-05-02
here is my lspci

genfly@genfly-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express PCI Express Root Port (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation G70 [GeForce Go 7600] (rev a1)
04:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
05:04.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)
05:05.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8169 Gigabit Ethernet (rev 10)

and 
lspci -v|grep Audio =
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)

Thanks again in advance :D

ps. im using Ubuntu Hardy Heron with all latest updates + suggested updates

---

### Post by genfly on 2008-05-02
I tried this:

sudo apt-get install module-assistant alsa-source

and opened it:
sudo module-assistant

tried everything, no luck

.....the sound continues to come out of the built in speakers as well as the headphones

---

### Post by zentropy on 2008-05-03
hello

I also have the same laptop! same problem!

can anyone PLEASE help?

thanks

00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
	Subsystem: Uniwill Computer Corp Unknown device 9077
	Flags: medium devsel, IRQ 10
	I/O ports at 18e0 [size=32]



&#9474;       &#9474;/proc/asound/cards:                                          &#9618;        &#9474;
&#9474;       &#9474;===================                                          &#9618;        &#9474;
&#9474;       &#9474; 0 [pcsp           ]: PC-Speaker - pcsp                      &#9618;        &#9474;
&#9474;       &#9474;                      Internal PC-Speaker at port 0x61       &#9618;        &#9474;
&#9474;       &#9474; 1 [Intel          ]: HDA-Intel - HDA Intel                  &#9618;        &#9474;
&#9474;       &#9474;                      HDA Intel at 0xb0000000 irq 21

---

