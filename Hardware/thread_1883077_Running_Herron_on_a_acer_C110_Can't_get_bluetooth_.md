---
title: "Running Herron on a acer C110 Can't get bluetooth working"
date: 2011-11-18
forum: Hardware
---

### Post by Flyingdutchman87 on 2011-11-18
I've got an old Acer Travelmate C110 I'm running 8.04 on at work to steam Internet radio. I want to get the internal bluetooth working to match up to my insignia headphones. 

I can't seem to get it to recognize the internal adapter. I did some forum searching and it seems that people have gotten it to work, but they didn't list where they got the drivers or what commands they ran to get it up and working. 

Any help would be appreciated. I'm a linux noob and I'm not quite sure where to get started on this.

---

### Post by matt_symes on 2011-11-18
Hi

> **Flyingdutchman87 said:**
> I've got an old Acer Travelmate C110 I'm running 8.04 on at work to steam Internet radio. I want to get the internal bluetooth working to match up to my insignia headphones. 

Any reason you are using 8.04 ? It's passed its EOL.  Have you considered 10.04 or will it not work on that old laptop ?

> I can't seem to get it to recognize the internal adapter. I did some forum searching and it seems that people have gotten it to work, but they didn't list where they got the drivers or what commands they ran to get it up and working. Let's run thought some basic commands. Open  a terminal and type

```
lspci
```Copy and paste the results from the terminal by highlighting the text, right clicking and select copy and paste it into your next post. Do the same for these commands. All commands are case sensitive.

You can also copy and paste these commands into the terminal. This is the preferred method as typos are less lightly.

```
lsusb
``````
sudo apt-get install rfkill
```Enter your password. It will not be echoed to the screen.

```
rfkill list
``````
hcitool dev
``````
hcitool scan
``````
ps aux | grep -i blue
``````
lsmod | grep -E "blue|rf"
```> Any help would be appreciated. I'm a linux noob and I'm not quite sure where to get started on this.I don't really use Bluetooth and for the few occasions i have it has always worked out of the box for me so i may not be much help but i am hoping that someone with more experience with it will chime in.

Kind Regards

---

### Post by Flyingdutchman87 on 2011-11-18
> **matt_symes said:**
> Hi



Any reason you are using 8.04 ? It's passed its EOL.  Have you considered 10.04 or will it not work on that old laptop ?


Kind Regards

Yeah i can't get anything over 8.04 to install on it. I can upgrade it to 9.04 with the update tool, but if it breaks i have to start over at 8 again.

10.04 wont work at all. Pretty sure is an issue with the display drivers.

---

### Post by matt_symes on 2011-11-18
Hi

> **Flyingdutchman87 said:**
> Yeah i can't get anything over 8.04 to install on it. I can upgrade it to 9.04 with the update tool, but if it breaks i have to start over at 8 again.

10.04 wont work at all. Pretty sure is an issue with the display drivers.

It could be kernel mode setting. That came in for 9.10. 

Did you try to disable it with the *nomodeset* kernel parameter ?

The again it could be an unsupported card. *lspci* will tell us a bit about your graphics card as well.

Kind regards

---

### Post by Flyingdutchman87 on 2011-11-18
Commands

lspci

00:00.0 Host bridge: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.1 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.3 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:01.0 PCI bridge: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to AGP Controller (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:02.1 Display controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 83)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 03)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 03)
02:01.0 CardBus bridge: Ricoh Co Ltd RL5c475 (rev b8)
02:01.1 FireWire (IEEE 1394): Ricoh Co Ltd R5C551 IEEE 1394 Controller
02:05.0 Network controller: Intel Corporation PRO/Wireless 2200BG Network Connection (rev 05)
02:08.0 Ethernet controller: Intel Corporation 82801DB PRO/100 VE (MOB) Ethernet Controller (rev 83)

 lsusb

Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 004: ID 0a5c:4503 Broadcom Corp. 
Bus 001 Device 003: ID 0a5c:4502 Broadcom Corp. 
Bus 001 Device 002: ID 0a5c:4500 Broadcom Corp. 
Bus 001 Device 001: ID 0000:0000  

 Thats an external adapter i brought in to mess with. Although reading around no-one can get it to work. 

kevin@kevin-laptop:~$ sudo apt-get install rfkill
[sudo] password for kevin: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package rfkill
kevin@kevin-laptop:~$ ps aux | grep -i blue
root      5059  0.0  0.1   2968   904 ?        S    09:19   0:00 /usr/lib/bluetooth/bluetoothd-service-audio
root      5073  0.0  0.1   2904   828 ?        S    09:19   0:00 /usr/lib/bluetooth/bluetoothd-service-input
kevin     5540  0.0  1.1  22088  6068 ?        S    09:19   0:01 bluetooth-applet --singleton
root      6086  0.0  0.1   2904   816 ?        S    09:24   0:00 /usr/lib/bluetooth/bluetoothd-service-serial
root      7474  0.0  0.1   2940   968 ?        S    09:51   0:00 /usr/lib/bluetooth/bluetoothd-service-network
kevin    11793  0.0  0.1   3012   848 pts/0    S+   11:33   0:00 grep -i blue
kevin@kevin-laptop:~$ lsmod | grep -E "blue|rf"
rfcomm                 42000  4 
l2cap                  25728  16 bnep,rfcomm
bluetooth              61028  5 bnep,rfcomm,l2cap
kevin@kevin-laptop:~$

---

### Post by matt_symes on 2011-11-18
Hi

This is your graphics card.

> 00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)Check this out

[http://ubuntuforums.org/showthread.php?t=1464239](http://ubuntuforums.org/showthread.php?t=1464239)

> Bus 001 Device 004: ID 0a5c:4503 Broadcom Corp. 
Bus 001 Device 003: ID 0a5c:4502 Broadcom Corp. 
Bus 001 Device 002: ID 0a5c:4500 Broadcom Corp.According to [www.pcidatabase.com]("http://www.pcidatabase.com") all these are your USB bluetooth devices.

I don't quite understand that. I would have expected only one device.

For these interested 0a5c is the vendor ID and 4503, 4502, 4500 are the device ids to enter into pcidatabase.

This is the only usb device plugged in ?

I have just found out that rfkill was not in until Lucid and that is why its not installed and it cannot be found.

> E: Couldn't find package rfkillFrom the terminal type

```
ls /sys/class/rfkill/
```Does it say No such file or directory ?

You have bluetooth services running (need to check they are the correct ones) and kernel modules loaded.

I will need to look into this more.

Kind regards

---

### Post by Flyingdutchman87 on 2011-11-18
I get a no-such file or directory error.

and that is the only thing i have plugged into a USB.

---

### Post by matt_symes on 2011-11-19
Hi

I think you might really struggle to get this working under 8.04. I think your best bet is to get 10.04 working, others have done that, and then try to get your bluetooth adapter working under 10.04. Others have had success at doing that as well.

Kind regards

---

