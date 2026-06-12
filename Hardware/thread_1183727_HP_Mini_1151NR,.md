---
title: "HP Mini 1151NR,"
date: 2009-06-10
forum: Hardware
---

### Post by jonathonblake on 2009-06-10
All:

I'm toying with getting the HP Mini 1151NR, and replacing the OS with Ubuntu Remix.

Questions:
a) How feasible is this?
b)How practical is this?


According to the release data I have, the following are the specs for the Mini 1151 NR.

    Mobile Broadband – EV-DO Revision A (Rev. A) Embedded
·          GlobalAccess – Qualcomm Gobi chipset (quad-band GPRS/EDGE/GSM and tri-band HSPA/UMTS)
·          802.11b/g WLAN and Bluetooth®
·          Wired Ethernet RJ-45
·          Display – 10.1” Flush Glass (1024 x 576) diagonal LED BrightView Infinity display
·          Weight – 2.4 Pounds
·          Dimensions – 1” x 10.3” x 6.6”
·          Power – three-cell battery, 30W AC Adapter
·          Processor – Intel Atom N270
·          Processor Speed – 1.6 GHz
·          System Memory – 1 GB RAM
·          Storage Hard Drive – 80 GB hard disk drive
·          Operating System – Windows XP Home Edition; Service Pack 3
·          USB Ports – Two USB 2.0 ports
·          Video – VGA out (requires optional accessory); built-in Webcam 640 x 480, 30 fps
·          Audio – Stereo speakers, integrated microphone, combo headphone/microphone jack
·          Removable memory – combo SD/MMC card slot
·          Limited Warranty – one-year

###

a)   The contract costs are _not_ a factor in whether or not I get this system;
b) I don't see the point of it shipping with WinXP, because, according to HP, there is no WinXP for this specific chip architecture, other than what is provided with this netbook;

jonathon

---

### Post by tz1 on 2009-07-01
I got one and am using the NORMAL Ubuntu desktop from a USB memory stick.  Everything works now except sound (which is probably a magic modprobe parameter in /etc/modprobe.d/alsa-base.conf - I'm still looking into it as it recognizes things but no sound comes out).

Side note:

The 1151NR will take and recognize a 2GB RAM memory stick (the same one for an Asus EEE PC 900A).

This includes the Verizon EVDO (as USB serial), at least according to a post in another forum.  It is a qualcomm CDMA modem so needs a patched version of that driver.

Note the front switch can turn the LAN, WiFi, Bluetooth, and/or the EVDO off, so that needs to be on to work.

Even 3d like Stellarium or Google earth runs fast.

Also, I used GParted to shrink the 80Gb XP partition to around 8Gb (I could go less), since I rarely, but occasionally do need to use XP, like for the Activation and PRL update for the EVDO chip.  I usually do the following partition scheme: XP-native, Linux system root , Linux /home, FAT32 transfer and warehouse.

That is what I have on my full system stick (P1 is DOS native FAT and has various recovery tools)

---

### Post by shadowstalkersb on 2009-07-28
> **tz1 said:**
> I got one and am using the NORMAL Ubuntu desktop from a USB memory stick. Everything works now except sound (which is probably a magic modprobe parameter in /etc/modprobe.d/alsa-base.conf - I'm still looking into it as it recognizes things but no sound comes out).
 
Side note:
 
The 1151NR will take and recognize a 2GB RAM memory stick (the same one for an Asus EEE PC 900A).
 
This includes the Verizon EVDO (as USB serial), at least according to a post in another forum. It is a qualcomm CDMA modem so needs a patched version of that driver.
 
Note the front switch can turn the LAN, WiFi, Bluetooth, and/or the EVDO off, so that needs to be on to work.
 
Even 3d like Stellarium or Google earth runs fast.
 
Also, I used GParted to shrink the 80Gb XP partition to around 8Gb (I could go less), since I rarely, but occasionally do need to use XP, like for the Activation and PRL update for the EVDO chip. I usually do the following partition scheme: XP-native, Linux system root , Linux /home, FAT32 transfer and warehouse.
 
That is what I have on my full system stick (P1 is DOS native FAT and has various recovery tools)
 
 
Where did you get a patched driver for the onboard Verizon EVDO Broadband card?  I can't get the Mobile Broadband to connect or even show an option to connect.  I am new to Ubuntu and am trying to have this alternate OS to work with.

---

### Post by DarkHelmet46 on 2009-08-15
I also have Ubuntu Netbook Remix running on an HP Mini 1151NR, and would love to find a way to get the interegrated Verizon 3G card to work.  Can anyone help?
 
-Helmet

---

### Post by hortonwho on 2009-09-05
I have my 1151NR 100% functional with the evdo by using wine to extract the firmware from the HP firmware binary called sp43936.exe, gobi_loader, and qcserial module in 2.6.30+. By using trial and error, and halting the device each time between gobi firmware boots. I was able to find/load the correct firmware for my provider. The 1151NR has the Gobi card. Basically it's a card that can do CDMA/GSM but you have to use the correct firmware to choose the provider/band. Using the 9.10 ubuntu remix with a 2.6.30+ kernel you use the qcserial module to get the card recognisable and flashable. qcserial stages the qualcomm gobi card for flashing. You then use [http://www.codon.org.uk/~mjg59/gobi_loader/]("http://www.codon.org.uk/~mjg59/gobi_loader/") and udev to actually load the firmware. When I extracted my firmware there were 11 directories each with different provider/band info. The firmware in directory 1 worked for my provider on verizon. In each firmware directory are 2 files amss.mbn and apps.mbn. I followed the gobi_loader instructions and have /dev/ttyUSB0 flashing on boot with udev. I also had to dump the b43 driver for the wireless and use the wl module to get my wifi working. I am using UNR 9.10 Karmic. You need the 2.6.30+ kernel for the qcserial and hp-wmi modules which allow you to program the gobi with the correct firmware.

---

### Post by shortman69 on 2009-10-12
I would like to personally thank everyone who has worked on this project; I was getting so frustrated with this problem that I almost went back to Windows but I am happy to say that my Verizon Wireless Broadband Connection is now fully functional. Thanks again.

---

### Post by heyshadylady on 2009-11-04
> **hortonwho said:**
> I have my 1151NR 100% functional with the evdo by using wine to extract the .....


I have read through this thread in it's entirety, as well as the link you included, hortonwho.

I like to consider myself pretty intelligent, however I am COMPLETELY new to the Linux and Ubuntu world, and I have not one single clue what that post of yours directed me to do.  I am extremely frustrated that I'm not able to understand it either, but I just can't.

Is there anyway possible you could dumb it down to it's lowest possible form so that a total noob would know how to complete those steps?




I also have an HP Mini 1151nr with the built in Verizon broadband card. I have tried I can't even tell you how many ways to connect to it. It just won't do it. I'm about to rip my hair out trying to get this work, and am even considering just buying the Windows XP install disk to be done with this.

I can't even connect through DSL anymore on my mini, so as of right now, my laptop only serves the purpose of letting me play the few included games on it.  Absolutely no internet.







I apologize for the lengthy post - in short, I need stupid-proof instructions on how to do what you have already explained. 
I simply do not understand.

---

### Post by jonathonblake on 2009-11-04
> **heyshadylady said:**
> 
Is there anyway possible you could dumb it down to it's lowest possible form so that a total noob would know how to complete those steps?

The following is my rough translation into something less technical. Like all translations, it suffers from imprecision, and oversimplification.

> 
[quote]
I have my 1151NR 100% functional with the evdo by using wine to extract the firmware from the HP firmware binary called sp43936.exe, gobi_loader, and qcserial module in 2.6.30+.


The 1151NR can run Ubuntu and use EVDO. 

EVDO is a connection protocol that is optimised for wireless connection to the Internet. Think WiFi,  but through your cell phone carrier.

You need to download the following programs first:
* sp43936.exe from [http://h20000.www2.hp.com/bizsupport/TechSupport/SoftwareDescription.jsp?lang=en&cc=us&prodTypeId=321957&prodSeriesId=3688868&prodNameId=3688870&swEnvOID=2096&swLang=8&mode=2&taskId=135&swItem=ob-73450-1](http://h20000.www2.hp.com/bizsupport/TechSupport/SoftwareDescription.jsp?lang=en&cc=us&prodTypeId=321957&prodSeriesId=3688868&prodNameId=3688870&swEnvOID=2096&swLang=8&mode=2&taskId=135&swItem=ob-73450-1)
(This is the first result on a Google search for "sp43936.exe")
* gobi_loader from [http://www.codon.org.uk/~mjg59/gobi_loader/](http://www.codon.org.uk/~mjg59/gobi_loader/)
* qcserial in 2.6.30 or higher linux kernel, from kernel.org.   

Those three programs are device drivers and loaders. You will need to run *make*  and [make install[/i] for at least qcserial. (Badly translating into normal English, you'll need to compile the program, so it is in the right directory.)

To find the right part of those device drivers to install on your system, you'll need to use WINE (available from the Ubuntu repository) to locate the specific drivers used in the HP 1151.

>  By using trial and error, and halting the device each time between gobi firmware boots. I was able to find/load the correct firmware for my provider. 

This describes how the OP found out what was needed.

> The 1151NR has the Gobi card. Basically it's a card that can do CDMA/GSM but you have to use the correct firmware to choose the provider/band. 

Gobi card is card that has G3 and GPS chips on it. (G3 is a cell phone standard, or rather, set of standards. GPS is global positioning satellite, used for navigation.) This is what enables the 1151NR to communicate with the cell phone carrier.  You may (probably will) have to hunt for the right drivers for your specific cell phone carrier, and the version of G3 and GPS that your carrier uses.

> Using the 9.10 ubuntu remix with a 2.6.30+ kernel you use the qcserial module to get the card recognisable and flashable.

qcserial is the program that sets up your netbook, so that it works with Ubuntu.  One of the things that it does, is rewrites the chip programming in the netbook, so that it works with Ubuntu. Done incorrectly, this can result in your netbook being totally unusable. Done correctly, your system will work properly. 

If you don't know what you are doing, don't run any programs that rewrite the programming in the chips. 

>  qcserial stages the qualcomm gobi card for flashing. You then use [http://www.codon.org.uk/~mjg59/gobi_loader/]("http://www.codon.org.uk/~mjg59/gobi_loader/") and udev to actually load the firmware.

Qcserial tells the chip that it is going to be rewritten.  
gobi_loader has the data that is rewritten in the chip.
udev rewrites the chip.
(I think I have the right functionality for each program there.  At any rate, those programs work together to provide the new programming for the G3 chip in the netbook, so that it works with Ubuntu.)

>  When I extracted my firmware there were 11 directories each with different provider/band info. The firmware in directory 1 worked for my provider on verizon.

If you use Verizon in the united states, you need the files in directory 1. If you use a different carrier, you'll need to look in each directory, to find the right firmware for your specific carrier.

>  In each firmware directory are 2 files amss.mbn and apps.mbn. I followed the gobi_loader instructions and have /dev/ttyUSB0 flashing on boot with udev. 

Read the instructions and documentation that comes with gobi_loader.  
The specific files you'll be using are amss.mbn and apps.mbn. (But check to be sure that they are for your specific carrier.)

udev uses /dev/ttyUSB0, so be sure that that device is readable, on your system.

> I also had to dump the b43 driver for the wireless and use the wl module to get my wifi working.

You may need to replace the wireless driver with the wl module.

>  I am using UNR 9.10 Karmic. You need the 2.6.30+ kernel for the qcserial and hp-wmi modules which allow you to program the gobi with the correct firmware.


These directions work for Ubuntu Netbook Remix 9.10 Karmic.  Two specific modules from the 2.6.30 Linux kernel are required:   The qcserial module and the hp-wmi module.  Both of these are used to tell gobi_loader what it is dealing with, and what it needs to do.  
[/quote]

> my laptop only serves the purpose of letting me play the few included games on it.  Absolutely no internet.


This sounds like you are well on your way to bricking your system.  Not  a good place to be in. 

> I need stupid-proof instructions on how to do what you have already explained. 

The problem with stupid proof instructions, is that they won't protect the user from bricking the device.  

Basically, if you aren't willing to risk bricking your device, you shouldn't be trying the procedure that is described. (This is one reason why Verizon requires people to sign off on liability, when their phones are flashed. Even when the person supposedly knows what they are doing, the device still can be bricked, due to unanticipated factors, and software.)

jonathon

---

### Post by heyshadylady on 2009-11-04
> **jonathonblake said:**
> The following is my rough translation into something less technical. Like all translations, it suffers from imprecision, and oversimplification.
 
 
 
 
Jonathan, I cannot tell you how much I really really really appreciate you breaking that down for me. Once I get home from work, I am going to have my brother (who is a little more experienced with the Linux processes) sit down and help me try to figure this out. I really really love what I am able to use of Ubuntu, but if it means no internet... then I'm going to have to sadly revert back to Windows ):
 
I'll post my results as well, just in case anyone else is using this as a learning experience.
 
 
Thanks again!
 
~ty

---

### Post by cerberez on 2009-11-04
I just bought an HP mini 1050nr with UNR already installed. It's got pretty much the exact same statistics (except a solid state disk and no bluetooth :().

It runs beautifully. Only thing is, bootup takes 45-60 seconds, and from what I've heard, that's not so fast for ubuntu.

but I'm astonished by the speed with which programs load.

> **jonathonblake said:**
> All:

I'm toying with getting the HP Mini 1151NR, and replacing the OS with Ubuntu Remix.

Questions:
a) How feasible is this?
b)How practical is this?


According to the release data I have, the following are the specs for the Mini 1151 NR.

    Mobile Broadband – EV-DO Revision A (Rev. A) Embedded
·          GlobalAccess – Qualcomm Gobi chipset (quad-band GPRS/EDGE/GSM and tri-band HSPA/UMTS)
·          802.11b/g WLAN and Bluetooth®
·          Wired Ethernet RJ-45
·          Display – 10.1” Flush Glass (1024 x 576) diagonal LED BrightView Infinity display
·          Weight – 2.4 Pounds
·          Dimensions – 1” x 10.3” x 6.6”
·          Power – three-cell battery, 30W AC Adapter
·          Processor – Intel Atom N270
·          Processor Speed – 1.6 GHz
·          System Memory – 1 GB RAM
·          Storage Hard Drive – 80 GB hard disk drive
·          Operating System – Windows XP Home Edition; Service Pack 3
·          USB Ports – Two USB 2.0 ports
·          Video – VGA out (requires optional accessory); built-in Webcam 640 x 480, 30 fps
·          Audio – Stereo speakers, integrated microphone, combo headphone/microphone jack
·          Removable memory – combo SD/MMC card slot
·          Limited Warranty – one-year

###

a)   The contract costs are _not_ a factor in whether or not I get this system;
b) I don't see the point of it shipping with WinXP, because, according to HP, there is no WinXP for this specific chip architecture, other than what is provided with this netbook;

jonathon

---

