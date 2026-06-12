---
title: "Removing and installing drivers, help please"
date: 2008-07-17
forum: General Help
---

### Post by the lemming on 2008-07-17
I am attempting to remove my wireless drivers and re-installing another version from this site

[http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=4&PFid=4&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true#RTL8110S-32/RTL8110SB(L)/RTL8169SB(L)/RTL8169SC(L)%3Cbr%3ERTL8169](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=4&PFid=4&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true#RTL8110S-32/RTL8110SB(L)/RTL8169SB(L)/RTL8169SC(L)%3Cbr%3ERTL8169)

The only problem is that I haven't got a clue how to go about this.

I have got the file on my desktop and I am trying to follow the ReadMe file contained in the tar file.

What seems like a simple project is causing quite a large learning curve.

For a start I don't know what a tar file is and following the instructions gives error messages.

I take it that if I want to change anything I need to type sudo at the beginning of everything?
or is there another way?

Any help or advice on this would be most helpfl.

I appreciate that this seems like a rudamentary question for many Linux users and if somebody asked me a similar question on how to replace a Windows driver then I too would think that it was simple to achieve.

Sadly it is only simple once you know what you are doing.

Cheers

---

### Post by Taxman415a on 2008-07-17
Usually it's better to tell us what you're trying to do and why. That way we can figure out if there is a better/easier way.  Also we need more specifics on what wireless card you have and what driver you're trying to replace. Usually with linux you don't need to do that. Also what error messages are you getting. Be specific, ie. cut and paste them.

And in general, you don't always need sudo, you just need it when the commands you are running need superuser priviledges. Drivers and things involving the kernel would. One way to tell is in hindsight. If you got a permission denied error, you should have used sudo. Otherwise you don't want to use sudo when you don't need it. Eventually you'll get a feel for it.

A tar file is like a zip file, it's a bunch of files grouped into one. you use the command tar with the right options to un-tar it and get all the files out. The command is tar -xjf <filename> in this case since it is a .tar.bz2 file

Ok, I dl'd the linux driver file for the 8169 etc because that's where your link goes to. The instructions call for building a module so you'll need to run these commands first as well (assuming you've updated to the latest kernel. If not you'd have a different version number)
```
sudo aptitude install linux-headers-2.6.24-19
```
```
sudo aptitude install build-essential
```

Then more or less follow the instructions in the readme file that came with the driver if you'd still like to try this.

---

### Post by coffeecat on 2008-07-17
> **Taxman415a said:**
> Usually it's better to tell us what you're trying to do and why. That way we can figure out if there is a better/easier way.


Agreed. It looks as though you know at least the make of the chipset of your wireless card, but if you don't know the exact version, open a terminal and:

```
sudo lspci
```..or if it's a usb dongle:

```
sudo lsusb
```..and find the line that describes the wireless chipset. If you search the forums with that chipset identifier you might find a howto infinitely to be preferred to compiling source code or whatever that Realtek site is telling you to do.

Apologies if you know this/have done this already, but it needs saying for others who might come across this thread.

---

### Post by the lemming on 2008-07-17
> **coffeecat said:**
> Agreed. It looks as though you know at least the make of the chipset of your wireless card, but if you don't know the exact version, open a terminal and:

```
sudo lspci
```..or if it's a usb dongle:

```
sudo lsusb
```..and find the line that describes the wireless chipset. If you search the forums with that chipset identifier you might find a howto infinitely to be preferred to compiling source code or whatever that Realtek site is telling you to do.

Apologies if you know this/have done this already, but it needs saying for others who might come across this thread.


I typed lspci into a terminal and got the following





00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Proces
sor to DRAM Controller (rev 04)
00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Exp
ress Graphics Controller (rev 04)
00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Gr
aphics Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Ex
press Port 1 (rev 04)
00:1c.1 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Ex
press Port 2 (rev 04)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) US
B UHCI #1 (rev 04)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) US
B UHCI #2 (rev 04)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) US
B UHCI #3 (rev 04)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) US
B UHCI #4 (rev 04)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) US
B2 EHCI Controller (rev 04)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d4)
00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (IC                                            H6 Family) AC'97 Audio Controller (rev 04)
00:1e.3 Modem: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem                                             Controller (rev 04)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev                                             04)
00:1f.2 IDE interface: Intel Corporation 82801FBM (ICH6M) SATA Controller (rev 0                                            4)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Contr                                            oller (rev 04)
06:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8169 Gigabit Et                                            hernet (rev 10)
06:04.0 Network controller: Intel Corporation PRO/Wireless 2200BG Network Connec                                            tion (rev 05)
06:09.0 CardBus bridge: Texas Instruments PCIxx21/x515 Cardbus Controller
06:09.2 FireWire (IEEE 1394): Texas Instruments OHCI Compliant IEEE 1394 Host Co                                            ntroller
06:09.3 Mass storage controller: Texas Instruments PCIxx21 Integrated FlashMedia                                             Controller
06:09.4 SD Host controller: Texas Instruments PCI6411/6421/6611/6621/7411/7421/7                                            611/7621 Secure Digital Controller









As usual I am non the wiser as to what this all means but I am all the more confused by this section

06:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8169 Gigabit Et                                            hernet (rev 10)
06:04.0 Network controller: Intel Corporation PRO/Wireless 2200BG Network Connec                                            tion (rev 05)


Do thee two things stake the chip set and the model make?
Or are they different things?

I would hate to bugger things up and lose my wireless internet connection all together because I killed the wrong things.

Cheers

---

### Post by Taxman415a on 2008-07-17
Bah! So we see you have the Realtek 8169, but what about the other stuff? :) Why you're trying to do what you're doing, the specific error messages, etc.

Since you have wireless, I take it you currently have the r8169 driver (the stock driver for that chipset that comes with the kernel) working?

---

### Post by coffeecat on 2008-07-17
> **the lemming said:**
> As usual I am non the wiser as to what this all means but I am all the more confused by this section

06:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8169 Gigabit Et                                            hernet (rev 10)
06:04.0 Network controller: Intel Corporation PRO/Wireless 2200BG Network Connec                                            tion (rev 05)

This is good news. Your ethernet (wired) interface has a Realtek chipset. That's not a problem. You don't need to do anything. That should already be working. The really good news is the Intel 2200BG wireless chipset. That works absolutely out of the box with Ubuntu 8.04 (has done for several versions of Ubuntu) and all you have to do is click on the Network Manager applet icon in the panel, choose your wireless network, put in the WPA/WEP password (if you have one) and Bob should be your Uncle. You do this once and next time you boot up it will connect automatically.

I have the Intel 2200BG chipset in my laptop. It works no trouble at all. No fiddling. No installation of drivers. No mucking around in the terminal. Better than in Windows.

So - why are you trying to remove the wireless drivers? What problems have you had?

**Edit:** Oh dear, I see from one of your other threads that someone misled you by saying that you had a Realtek wireless chipset. I can assure you that the wireless interface is the Intel 2200BG. Out of interest, what make and model of laptop is that?

---

### Post by coffeecat on 2008-07-17
> **Taxman415a said:**
> Bah! So we see you have the Realtek 8169, but what about the other stuff? :) Why you're trying to do what you're doing, the specific error messages, etc.

Since you have wireless, I take it you currently have the r8169 driver (the stock driver for that chipset that comes with the kernel) working?

Well, I see from his first post that he's trying to replace his wireless drivers with ones from the Realtek website - which would be a very bad idea in the circumstances. As you can see from the edit to my previous post, I think he was misled on another thread. But you're right, we need to know exactly what it is he is trying to do.

---

