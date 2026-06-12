---
title: "56K Modem Support in Ubuntu 6.06"
date: 2006-12-26
forum: Hardware &amp; Laptops
---

### Post by ScottMorris on 2006-12-26
Hi there, one of my friends is having trouble finding a Modem that works with Linux.  I am not surprised as I have heard of poor hardware support for modems.  But I also know that there is some that do work.  Most of these must be hardware modems but the Linmodem project has great advice for getting a Winmodem to work.

So far he has tried a few modems but no luck.  We tried one from Conexant but the Linux drivers cost 20 $ and I know you can buy modems cheaper than that if you know where to look.  Next he found an Acer D-1156I modem but we are unable to find any information about it.  If anyone knows anything about this modem (it seems to be made by Liteon) we would like to know if it is a candidate to work with Dapper.  As well, if anyone knows of any cheep models of modem that would also be great.  Any other suggestions are welcome.  He lives out in the country so there is no High Speed access (hence the dial-up ness).

P.S. Happy Holidays :D

---

### Post by _duncan_ on 2006-12-26
Click on the first link on my signature (linmodems.org). There you can download a tool called scanModem that will help identify the chipset used by the modem, and hopefully some suggestions on drivers to use.

---

### Post by ScottMorris on 2006-12-26
Hi, Thanks for the reply.  I have tied running that tool but it gave nothing as its information.  Just stuff about my kernel and OS.  I will try it again with this D1156I modem and see what it says.  Maybe if I can't find anything in it I will attach it as I may be reading it wrong.

---

### Post by amp_man on 2006-12-26
look for a modem that advertises a hardware dsp (these will not be $20 modems!). These should work out-of-the-box with any linux distro ;-) Either that, or most external serial modems (NOT USB!) will work also, I've got 2 here myself from my old 56k days.

---

### Post by ScottMorris on 2006-12-27
Attached is the scanModem output file.  I am unsure what I am looking for.  We have been on the search for hardware modems but they are scarce in our area.  Thanks for all your feedback.

---

### Post by towsonu2003 on 2006-12-27
Very weird, and this is a trend I have been seeing for a while now... I cannot see any information on your modem in that output... Try emailing linmodems.org. And because I am very curious about this issue, I would be real glad if you could post their reply to you...

Here's the instructions you should follow while sending an email to their list:
>  Only plain text email is forwarded by the  [email]DISCUSS@linmodems.org[/email] List Server.
 Do use the following as the email Subject Line:
           SomeName, YourCountry Ubuntu 6.06 LTS  kernel 2.6.15-23-386 
 This will alert cogent experts, and  distinguish cases in the Archives.
 YourCountry will enable Country Code guidance.
 Occassionally responses are blocked by an Internet Provider mail filters.
 So in a day, also check the Archived responses at [http://www.linmodems.org](http://www.linmodems.org) .
 Local Linux experts can be found through: [http://www.linux.org/groups/index.html](http://www.linux.org/groups/index.html) (this is from your ModemData.txt)

PS. you will send them your ModemData.txt.

---

### Post by _duncan_ on 2006-12-27
I agree with towsonu2003. In the meantime,  can you open a terminal and paste the output of the following command?
```
lspci
```

Mine looks like this:
```
00:00.0 Host bridge: VIA Technologies, Inc. VT8378 [KM400/A] Chipset Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI Bridge
00:05.0 Modem: Smart Link Ltd. Unknown device 2800 (rev 02)
00:0f.0 RAID bus controller: VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80)
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South]
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 78)
01:00.0 VGA compatible controller: VIA Technologies, Inc. VT8378 [S3 UniChrome] Integrated Video (rev 01)

```
Note that on the 3rd line, the lspci command told me the modem is Smart Link. This is inexact compared to the scanModem utility.

---

### Post by mperrin on 2006-12-27
You didn't mention if your friend was using a laptop or desktop. I had success on a desktop using a USR 2977 (OEM version of 5610) PCI hardware modem on 6.10. Ubuntu's default network configuration tool for modems didn't work. I had to install GNOME PPP. Fortunately I have a DSL connection to do that or I would have been in a Catch22 situation. GNOME PPP is a front end for wvdial and you could manually configure that and run it from the command line if you didn't have another way to install the GUI app. The situation was similar to yours: I was building a computer to be used in rural Montana where only dialup access was available. Following is the /etc/wvdial.conf file that worked, with the actual username and password deleted. Stupid mode may be required.

[Dialer Defaults]
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Modem Type = Analog Modem
ISDN = 0
Phone = 5411550
New PPPD = yes
Modem = /dev/modem
Username = your_username_here
Password = your_password_here
Baud = 115200

I have a couple 2977s laying around from my dial-up days. Your friend is welcome to one if they want it.

---

### Post by ScottMorris on 2006-12-27
My friend is using a Desktop with both ISA and PCI slots available.  I will ask him to try the lspci command and see what it outputs.  I have emailed linmodem.org and am awaiting a response from them.

---

### Post by ScottMorris on 2006-12-31
Thanks everyone for all your help.  My friend found an old serial modem that works well with Ubuntu.  We really appreciate the support.  This is a Great Community -- Gold Star for all :KS

---

