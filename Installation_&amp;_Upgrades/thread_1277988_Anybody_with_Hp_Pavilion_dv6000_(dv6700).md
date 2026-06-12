---
title: "Anybody with Hp Pavilion dv6000 (dv6700)"
date: 2009-09-29
forum: Installation &amp; Upgrades
---

### Post by tpho2500 on 2009-09-29
I have tried googling but the current tutorials on ndiswrapper and windows drivers do not work so i'm here requesting some drivers. 

Network Adapter: Intel Wireless WiFi link 4965AGN

I tried downloading from the official intellinux website but it does not work if anybody could provide me with this 1 driver so i can go online and get the other drivers i would appreciate it. :)

Thanks,

---

### Post by dstew on 2009-09-29
What version of Ubuntu do you have? Also, to see what the problem is, we can look at the system messages. The command **dmesg** will print the entire kernel boot message log, and you will see messages in there that will tell you something about why the wireless is not working. To narrow down the messages you see, you can use the **grep** pipe. For example, to see only the messages that have the string "wireless" in them, use```
dmesg | grep -i wireless
```This group of messages will at least tell you what module the kernel is trying to use. Once you know the module name, you can get the messages that are coming out of that module.

---

### Post by tpho2500 on 2009-09-29
> **dstew said:**
> What version of Ubuntu do you have? Also, to see what the problem is, we can look at the system messages. The command **dmesg** will print the entire kernel boot message log, and you will see messages in there that will tell you something about why the wireless is not working. To narrow down the messages you see, you can use the **grep** pipe. For example, to see only the messages that have the string "wireless" in them, use```
dmesg | grep -i wireless
```This group of messages will at least tell you what module the kernel is trying to use. Once you know the module name, you can get the messages that are coming out of that module.
 
Well it's not working because the drivers aren't installed. The drivers aren't installed because not all drivers are included in the ubuntu package. I'm sure ubuntu will automatically install new drivers when it connects to the internet but at the moment I'm trying to figure that part out. 
 
I'll try that when i get home.

---

### Post by Tlynyrd on 2010-01-21
Yes I do, and it seems I have the same problem. Maybe you found an answer yet?? First of all I'm a Ubuntu-beginner, so Linux is not my strength....  :confused:  I'm working on a HP DV6700, AMD Turion64, 3gig mem, 160gig HD,  and after the 3rd time getting Spam, Trojans, and Viruses I just had enough with Windows!! Ubuntu 9.10 runs really great, so far, but it would be nice if I could get the Wifi to work. I found some older posts, and someone was talking about trying to install the windows driver (ini-file). Tried that, but no luck so far. When I open the "Wireless Network Drivers" (system-administration-wireless drivers), it tells me this: "Unable to see if hardware is present". I managed to install a windows driver, which comes up in the list of wireless drivers, but as I mentioned already, it cannot see the hardware. 

Anyone have an Idea?
Thanks, so much!

Tlynyrd
HP DV6700 AMD Turion64, running Ubuntu 9.10

---

### Post by hardev on 2010-01-21
Try the following for Intel 4965AGN
[http://www.linwik.com/wiki/configuring+the+iwl4965+driver+for+the+intel+4965agn+wireless+controller](http://www.linwik.com/wiki/configuring+the+iwl4965+driver+for+the+intel+4965agn+wireless+controller)


Tlynyrd, which Wifi card do you have?

---

### Post by Leppie on 2010-01-21
i have an intel 4965AGN and am using the kernel modules...
```
lsmod | grep iwl
iwlagn                109052  0 
iwlcore               112796  1 iwlagn
mac80211              181140  2 iwlagn,iwlcore
cfg80211               93052  3 iwlagn,iwlcore,mac80211
led_class               4096  2 iwlcore,acer_wmi
```

> **Tlynyrd said:**
> HP DV6700 AMD Turion64
i could be wrong, but i don't think your pc has intel wifi

---

### Post by spcwingo on 2010-01-21
My wife has a DV6000 with an Atheros wireless card.  I can't remember exactly which model of Atheros card it is, but what I did to get this going in Hardy was to use the Windows driver via ndiswrapper.  After that it kept dropping the wireless so I installed WICD over Gnome network manager.  She's had no problems ever since.  Although this worked for her laptop, YMMV (your mileage may vary).

---

### Post by Tlynyrd on 2010-01-23
As far as I know it's a Atheros AR5100, because by typing this: lshw -c network  I get this:
tlynyrd@HPDV6700:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: MCP67 Ethernet
       vendor: nVidia Corporation
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: eth0
       version: a2
       serial: 00:1e:68:2c:78:3d
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=forcedeth driverversion=0.64 ip=192.168.1.108 latency=0 maxlatency=20 mingnt=1 multicast=yes
       resources: irq:27 memory:f6488000-f6488fff ioport:30f8(size=8) memory:f6489c00-f6489cff memory:f6489800-f648980f
  *-network UNCLAIMED
       description: Ethernet controller
       product: AR5001 Wireless Network Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0
       resources: memory:f6000000-f600ffff
tlynyrd@HPDV6700:~$

---

### Post by spcwingo on 2010-01-23
If you want to try the ndiswrapper solution, just keep reading.  :)

First, connect your laptop to your router via a cat5 cable.

Next, download the driver from [here]("http://www.mediafire.com/?cfdzj3eaizt") or [here]("http://rapidshare.com/files/155349338/AR5007_XP.zip") and extract.

After that, open a terminal and input this command:

```
sudo apt-get install ndisgtk
```

Now, look under System>Administration>Windows Wireless Drivers.  When that opens click "install new driver", then the button to the right of "location", lastly select the .inf file located in the extracted folder under the ndis5x folder.  You should now be all set.

BTW, you may or may not experience random wireless disconnects.  If this happens you can open a terminal and issue this command:

```
sudo apt-get install wicd
```

I think that WICD is now in the standard repos...if not and you get an error something to the effect of:

```
E: Couldn't find package wicd
```

just let me know and we'll get the WICD PPA added so you can install it.  :)  Either way let me know how it turns out.

---

### Post by DanlG on 2010-01-24
I have an intel dv6700 which uses a Broadcom network card.  It worked right out of the box.  You can get the network card using the command 'lspci', which in my case shows a BCM4312.

I had to modify /etc/network/interfaces and add 'pre-up sleep 10' to give the card enough time to warm up on startup.

good luck!

---

### Post by Tlynyrd on 2010-01-25
Hi SPCWINGO
Tried the "ndisgtk" command, but didn't work, I'm getting:
Invalid operation ndisgtk
Not sure what this means, I'm connected through my router, and I know I have access, since I can go online...

thanks for Your help

Tlynyrd

---

### Post by Leppie on 2010-01-25
> **Tlynyrd said:**
> Hi SPCWINGO
Tried the "ndisgtk" command, but didn't work, I'm getting:
Invalid operation ndisgtk
Not sure what this means, I'm connected through my router, and I know I have access, since I can go online...

thanks for Your help

Tlynyrd
did you put the "install" part in the command? this typically shows when the operation is omitted (in this case install).
```
sudo apt-get install ndisgtk
```

---

### Post by Tlynyrd on 2010-01-25
OK, I've downloaded and installed the inf driver (net5211.inf), but like before it still comes up as, "unable to see if hardware is present". I also rebooted, thinking that might activate the wifi card, but nothing. When the wifi switch is turned off, it's amber (or orange) when I turn it on, it just goes out, as far as I remember it should turn blue... This laptop used to have, when we first bought it, Vista (AAARRRGGHHH) on it. I managed to install XP-Pro, but I remember I had a hard time finding the correct drivers too. I need to find the driver disk, that I burnt at the time, maybe that would work....
Thanks for your help anyway!!

Tlynyrd

---

### Post by spcwingo on 2010-01-25
If you could find that disk, that would be the ticket to getting it going.  In the meantime could you post the terminal output of lspci?

---

### Post by Leppie on 2010-01-25
there's a how to on installing the madwifi drivers for use with atheros cards: [http://ubuntuforums.org/showthread.php?t=1309072](http://ubuntuforums.org/showthread.php?t=1309072)

---

### Post by Tlynyrd on 2010-01-26
Ok, here is the lspci -tv
cathee@HPDV6700:~$ lspci -tv
-[0000:00]-+-00.0  nVidia Corporation MCP67 Memory Controller
           +-01.0  nVidia Corporation MCP67 ISA Bridge
           +-01.1  nVidia Corporation MCP67 SMBus
           +-01.2  nVidia Corporation MCP67 Memory Controller
           +-01.3  nVidia Corporation MCP67 Co-processor
           +-02.0  nVidia Corporation MCP67 OHCI USB 1.1 Controller
           +-02.1  nVidia Corporation MCP67 EHCI USB 2.0 Controller
           +-04.0  nVidia Corporation MCP67 OHCI USB 1.1 Controller
           +-04.1  nVidia Corporation MCP67 EHCI USB 2.0 Controller
           +-06.0  nVidia Corporation MCP67 IDE Controller
           +-07.0  nVidia Corporation MCP67 High Definition Audio
           +-08.0-[0000:02]--+-05.0  Ricoh Co Ltd R5C832 IEEE 1394 Controller
           |                 +-05.1  Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter
           |                 +-05.2  Ricoh Co Ltd R5C843 MMC Host Controller
           |                 +-05.3  Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter
           |                 \-05.4  Ricoh Co Ltd xD-Picture Card Controller
           +-09.0  nVidia Corporation MCP67 AHCI Controller
           +-0a.0  nVidia Corporation MCP67 Ethernet
           +-0c.0-[0000:04-05]--
           +-0d.0-[0000:03]----00.0  Atheros Communications Inc. AR5001 Wireless Network Adapter
           +-12.0  nVidia Corporation C67 [GeForce 7150M / nForce 630M]
           +-18.0  Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
           +-18.1  Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
           +-18.2  Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
           \-18.3  Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
cathee@HPDV6700:~$

Not sure why it says AMD K8 Athlon64/Opteron at the end, supposingly the laptop has a AMD Turion64 installed...

---

### Post by Tlynyrd on 2010-01-28
HI Guys,
It finally worked, I followed the link that Leppie had displayed. Even though every so often it looses the wifi conneciton, especially when I shut the lid, it has a hard time to re-connect. But I can live with that for now....

Thanks again! Great support!

Tlynyrd

---

### Post by Leppie on 2010-01-28
you're welcome, glad it's working (more or less) :)

---

### Post by oblivion2k on 2010-07-23
Wow, all I have to say is thank goodness this thread is here. My friend's got a dv6000, and I'm trying to convince him that Ubuntu is awesome and all of that, and basically I'm having the same nightmare all of you are in trying to get the ethernet and wireless working, but with an extra twist. Ubuntu can see the wired and wireless networks, but can't connect to them. With ethernet it'll try for roughly 30 seconds and disconnect me, and with wireless (wep encrypted, with correct key entered) it will do the same but instead of disconnecting me, it'll ask me for the key again, as if I entered it wrong. I've got the atheros 5001 card, and got ndiswrapper and the windows driver that spcwingo mentioned installed, but it's still having the same problems it did before I ever touched it. I'm sure it's just something simple I'm missing but it's late and I'm tired. Anything I can try on this? Thanks in advance.

---

### Post by Jim281 on 2012-04-07
> **tpho2500 said:**
> I have tried googling but the current tutorials on ndiswrapper and windows drivers do not work so i'm here requesting some drivers. 

Network Adapter: Intel Wireless WiFi link 4965AGN

I tried downloading from the official intellinux website but it does not work if anybody could provide me with this 1 driver so i can go online and get the other drivers i would appreciate it. :)

Thanks,

I can relate! (have HP Pavillion dv6700). Bought it used last week; the HD had been wiped - in fact, unformatted. No restore disks. So I decided to take the Linux plunge (glad I did). Using Ubuntu 11.1 Totally new territory for me. But I'm getting there. At first i connected to the internet by ethernet, because under 'wireless', I wasn't detecting anything. Not sure if the wireless driver came with ver 11.1 or if i got it as an update download. I THINK I had to play with a few settings at 1st; entered the mac address from my wireless modem. Security WPA/WPA2. (Why not use ver 11.1? Just curious.)

---

