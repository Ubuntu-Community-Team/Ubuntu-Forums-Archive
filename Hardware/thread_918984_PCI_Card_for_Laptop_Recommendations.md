---
title: "PCI Card for Laptop? Recommendations?"
date: 2008-09-13
forum: Hardware
---

### Post by raydanator on 2008-09-13
I have a p3 800 mhz, 20gb, 256mb ram..possibly upgrading to 512, laptop. Planning to run either ubuntu, or xubuntu. My question is, what are some of the best pci card options out there? I have a generic pci card, and its not doing the job...or possibly i don't know how to use it. Budgetwise, i'm thinking under $60...preferably more like $30. But I'll fork out what I have to. Thanks much

---

### Post by pytheas22 on 2008-09-13
Are you looking for a PCI wireless card?  And do you mean PCMCIA or PCI?  PCMCIA is the slot on the side of your laptop (if you have one) where you put a card in and part of it would still stick out.  PCI cards would be completely inside the laptop, but generally you can't install PCI devices into laptops unless you take them completely apart, so I suspect that you mean PCMCIA.  Please let us know so that we can make recommendations accordingly.

I'm also wondering which card you have now, however, and why you can't get it to work.  I've never met a wireless card that I can't get to run in Linux if I try hard enough.  If you post the output of these commands, perhaps we can get your existing card working at a cost of $0:
```

lshw -C Network
lspci -nn
```

Also, what's the name under which your current card is sold?

---

### Post by raydanator on 2008-09-13
Ok, well if we can get Mr. Generic card up and running, I'm game, thanks! Sorry about that, yes- I do mean PCMCIA card. 

What do you mean by 
"lshw -C Network
lspci -nn"?

I'm pretty much a newb, so pardon the slowness. This is all the info I have on my card:

Name: 22Mbs Wireless CardBus Adapter
Mac ID: 0080C6E69730
Random numbers--NWH1022    A2.01
S/N 2J5300939
FCC ID: IOU1022S01
and thanks goodness--its made in Taiwan :)

Basically, I ran Xubuntu live 8.04.1, and was clueless as to how to access the network with the card. It didn't show up anywhere, so I am at a loss for knowledge. If I can get 512mbs of ram in this machine, I'm thinking I'd try Ubuntu. Or I could do Xubuntu. What do you think? Oh, and by the way I have a driver cd for the card. It says its an 802.11b Wireless CardBus Adater. Also, the model #, I think is NWH1022. Thanks

---

### Post by pytheas22 on 2008-09-13
I think your card has an acx chipset.  There should be drivers already installed for it in Ubuntu; maybe they're not loading for some reason.  Please open a terminal (Applications>Accessories menu if you're using Gnome), run these commands and copy-and-paste the output here:
```

lshw
iwconfig
dmesg | grep -e acx -e eth1 -e wlan
```

There's also an old driver provided by the manufacturer [here]("http://www.ndclan.com/Support/Drivers/NWH1022.asp"), but it's quite outdated and I don't know if it would compile on a modern Linux kernel.  In any case it shouldn't really be necessary, because if you do have an acx chipset, it should be easy enough to get working on Ubuntu (acx in general has good Linux support).

There are also Ubuntu-specific instructions [here]("http://acx100.sourceforge.net/wiki/Distribution_list/Ubuntu") for the acx driver (don't worry about that for now; I'm mostly noting it just for organization purposes, in case we have to refer to there later).

---

### Post by raydanator on 2008-09-13
Ok, I will burn off a copy of Ubuntu, and run those cmds as soon as I can. 

I was only able to test the card out using Xubuntu, so that could explain some things. I'm taking it that if my system can handle it, Ubuntu would be the way to go over Xubuntu. Especially with the card I have. Which distro would you recommend? I'm thinking Ubuntu if I can get 512 ram, but Xubuntu or some other light weight if I can't. 

Alright, I will post as soon as I test your recommendations out. Thanks

---

### Post by pytheas22 on 2008-09-14
Sorry, I should have been clearer, but you could run those commands in Xubuntu as well as Ubuntu--they both have the same backend and the commands will return the same information.

You could probably run either Xubuntu or Ubuntu on your machine.  It would of course be better to have more memory if you want to use Ubuntu, but it should still run fairly well even on just 256 megabytes.  Actually, although many would disagree with me, I've come to the conclusion that the difference between Xubuntu and Ubuntu in terms of resource usage is almost negligible--Xubuntu uses only a bit less these days.  If you want a really low-resource desktop, install something like fluxbox or twm (minimalist desktop environments).  Otherwise I generally just tell people to use whichever Ubuntu variant they like best, because in terms of resource use the difference is increasingly minimal.

Anyway, I'll look forward to the output from those commands.

---

### Post by raydanator on 2008-09-15
Alright-here's where I'm at. I installed Xubuntu, and ran the terminal lines you suggested. I am still not able to use the pcmcia card. I also cannot connect to the internet using an ethernet cable. Strange stuff. Anyway, here's the log:


danny@Danny-Laptop:~$ lshw
WARNING: you should run this program as super-user.
danny-laptop              
    description: Computer
    width: 32 bits
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 1
          size: 255MiB
     *-cpu
          product: Pentium III (Coppermine)
          vendor: Intel Corp.
          physical id: 2
          bus info: cpu@0
          version: 6.8.10
          size: 700MHz
          width: 32 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 sep mtrr pge mca cmov pat pse36 mmx fxsr sse up
        *-cache:0
             description: L1 cache
             physical id: 0
             size: 32KiB
        *-cache:1
             description: L2 cache
             physical id: 1
             size: 256KiB
     *-pci
          description: Host bridge
          product: 82815 815 Chipset Host Bridge and Memory Controller Hub
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 02
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel module=intel_agp
        *-pci:0
             description: PCI bridge
             product: 82815 815 Chipset AGP Bridge
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 02
             width: 32 bits
             clock: 66MHz
             capabilities: pci normal_decode bus_master
           *-display UNCLAIMED
                description: VGA compatible controller
                product: Rage Mobility M4 AGP
                vendor: ATI Technologies Inc
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 00
                width: 32 bits
                clock: 66MHz
                capabilities: vga_controller bus_master vga_palette cap_list
                configuration: latency=32 mingnt=8
        *-pci:1
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master
           *-multimedia
                description: Multimedia audio controller
                product: ES1983S Maestro-3i PCI Audio Accelerator
                vendor: ESS Technology
                physical id: 3
                bus info: pci@0000:02:03.0
                version: 10
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: driver=Maestro3 latency=32 maxlatency=24 mingnt=2 module=snd_maestro3
           *-communication UNCLAIMED
                description: Communication controller
                product: WinModem 56k
                vendor: Agere Systems
                physical id: 6
                bus info: pci@0000:02:06.0
                version: 01
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: latency=0 maxlatency=14 mingnt=252
           *-pcmcia:0
                description: CardBus bridge
                product: PCI4451 PC card Cardbus Controller
                vendor: Texas Instruments
                physical id: f
                bus info: pci@0000:02:0f.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pcmcia bus_master cap_list
                configuration: driver=yenta_cardbus latency=176 maxlatency=5 module=yenta_socket
           *-pcmcia:1
                description: CardBus bridge
                product: PCI4451 PC card Cardbus Controller
                vendor: Texas Instruments
                physical id: f.1
                bus info: pci@0000:02:0f.1
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pcmcia bus_master cap_list
                configuration: driver=yenta_cardbus latency=176 maxlatency=5 mingnt=192 module=yenta_socket
           *-firewire
                description: FireWire (IEEE 1394)
                product: PCI4451 IEEE-1394 Controller
                vendor: Texas Instruments
                physical id: f.2
                bus info: pci@0000:02:0f.2
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: ohci bus_master cap_list
                configuration: driver=ohci1394 latency=32 maxlatency=4 mingnt=2 module=ohci1394
        *-isa
             description: ISA bridge
             product: 82801BAM ISA Bridge (LPC)
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-ide
             description: IDE interface
             product: 82801BAM IDE U100 Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@0000:00:1f.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master
             configuration: driver=ata_piix latency=0 module=ata_piix
        *-usb
             description: USB Controller
             product: 82801BA/BAM USB Controller #1
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
     *-network
          description: Wireless interface
          product: ACX 100 22Mbps Wireless Interface
          vendor: Texas Instruments
          physical id: 0
          bus info: pci@0000:03:00.0
          logical name: wlan0
          version: 00
          serial: 00:80:c6:e6:97:30
          width: 32 bits
          clock: 33MHz
          capabilities: bus_master cap_list ethernet physical wireless
          configuration: broadcast=yes driver=acx_pci latency=64 module=acx multicast=yes wireless=IEEE 802.11b+
  *-scsi
       physical id: 1
       bus info: scsi@2
       logical name: scsi2
       capabilities: scsi-host
       configuration: driver=usb-storage
danny@Danny-Laptop:~$ iwconfig
lo        no wireless extensions.

wlan0     IEEE 802.11b+  ESSID:""  Nickname:"acx v0.3.36"
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Bit Rate:22 Mb/s   Tx-Power=18 dBm   Sensitivity=176/255  
          Retry min limit:7   RTS thr:off   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

danny@Danny-Laptop:~$ dmesg | grep -e acx -e eth1 -e wlan
[   60.536094] acx: Loaded combined PCI/USB driver, firmware_ver=default
[   60.536109] acx: compiled to use 32bit I/O access. I/O timing issues might occur, such as non-working firmware upload. Report them
[   60.536344] acx: found ACX100-based wireless network card at 0000:03:00.0, irq:11, phymem1:0x20010000, phymem2:0x20000000, mem1:0xd09de000, mem1_size:4096, mem2:0xd0b40000, mem2_size:65536
[   60.537393] acx: loading firmware for acx100 chipset with radio ID 15
[   60.610380] acx: firmware image 'acx/default/tiacx100c15' was not provided. Check your hotplug scripts
[   60.894682] acx: loading radio image for radio 15
[   61.570218] acx: === chipset TNETW1100A, radio type 0x15 (Ralink), form factor 0x01 ((mini-)PCI / CardBus), EEPROM version 0x05: uploaded firmware 'Rev 1.9.8.b' ===
[   61.571054] acx v0.3.36: net device wlan0, driver compiled against wireless extensions 22 and Linux 2.6.24-19-generic
[   61.571148] usbcore: registered new interface driver acx_usb
[   75.762317] wlan0: changing radio power level to 18 dBm (41)
[  178.474630] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  480.914561]  [<d0b13876>] acxpci_free_desc_queues+0x26/0xf0 [acx]
[  480.914615]  [<d0b13982>] acxpci_s_delete_dma_regions+0x42/0x60 [acx]
[  480.914644]  [<d0b1509c>] acxpci_e_remove+0x7c/0x2d0 [acx]
[  480.915101]  [<d0b138aa>] acxpci_free_desc_queues+0x5a/0xf0 [acx]
[  480.915128]  [<d0b13982>] acxpci_s_delete_dma_regions+0x42/0x60 [acx]
[  480.915157]  [<d0b1509c>] acxpci_e_remove+0x7c/0x2d0 [acx]
[  480.915546]  [<d0b138e8>] acxpci_free_desc_queues+0x98/0xf0 [acx]
[  480.915572]  [<d0b13982>] acxpci_s_delete_dma_regions+0x42/0x60 [acx]
[  480.915601]  [<d0b1509c>] acxpci_e_remove+0x7c/0x2d0 [acx]
[  480.915986]  [<d0b1391c>] acxpci_free_desc_queues+0xcc/0xf0 [acx]
[  480.916013]  [<d0b13982>] acxpci_s_delete_dma_regions+0x42/0x60 [acx]
[  480.916042]  [<d0b1509c>] acxpci_e_remove+0x7c/0x2d0 [acx]
[  491.121340] acx: found ACX100-based wireless network card at 0000:03:00.0, irq:11, phymem1:0x20010000, phymem2:0x20000000, mem1:0xd09de000, mem1_size:4096, mem2:0xd0b40000, mem2_size:65536
[  491.122382] acx: loading firmware for acx100 chipset with radio ID 15
[  491.169133] acx: firmware image 'acx/default/tiacx100c15' was not provided. Check your hotplug scripts
[  491.448870] acx: loading radio image for radio 15
[  492.116371] acx: === chipset TNETW1100A, radio type 0x15 (Ralink), form factor 0x01 ((mini-)PCI / CardBus), EEPROM version 0x05: uploaded firmware 'Rev 1.9.8.b' ===
[  492.118029] acx v0.3.36: net device wlan0, driver compiled against wireless extensions 22 and Linux 2.6.24-19-generic
[  492.224364] wlan0: changing radio power level to 18 dBm (41)
[  492.368571] ADDRCONF(NETDEV_UP): wlan0: link is not ready
danny@Danny-Laptop:~$ 


Thanks again

---

### Post by pytheas22 on 2008-09-15
From the output that you posted above, things actually look like they should be working--the wireless interface exists and seems to be functioning correctly.  The only possible problem is this line from dmesg:
```

acx: firmware image 'acx/default/tiacx100c15' was not provided. Check your hotplug scripts
```

But I'm not sure whether that's a real problem or not.  Are you unable to see networks?  What is the output of:
```

iwlist scan
```

---

### Post by raydanator on 2008-09-15
Here is the output: 


danny@Danny-Laptop:~$ iwlist scan
lo        Interface doesn't support scanning.

wlan0     No scan results

danny@Danny-Laptop:~$ iwlist
Usage: iwlist [interface] scanning [essid NNN] [last]
              [interface] frequency 
              [interface] channel 
              [interface] bitrate 
              [interface] rate 
              [interface] encryption 
              [interface] keys 
              [interface] power 
              [interface] txpower 
              [interface] retry 
              [interface] ap 
              [interface] accesspoints 
              [interface] peers 
              [interface] event 
              [interface] auth 
              [interface] wpakeys 
              [interface] genie 
              [interface] modulation 
danny@Danny-Laptop:~$ scan
The program 'scan' can be found in the following packages:
 * dvb-utils
 * nmh
 * mailutils-mh
Try: sudo apt-get install <selected package>
bash: scan: command not found
danny@Danny-Laptop:~$ 



I don't have a router as of yet, but tried to access my cousin's network yesterday. He used some different terminal commands, but couldn't connect through the card. 

I tried to get updates with an ethernet, but am so far not having luck. I've got no network connections on the desktop, and under Network Settings-Connections, I've got a Wireless Connection and Point to point connection. Both are faded.

 Under 'point to point' properties, enable this connection is not checked, but I can't seem to get the right settings to enable it.

---

### Post by pytheas22 on 2008-09-15
I think I know what the problem is.  You need to install a firmware file named 'tiacx100c15' into your /lib/firmware directory...hence the complaint in dmesg regarding the inability to find that firmware.  Unfortunately, I'm not able to find that particular firmware file anywhere.  There are firmwares for everything else available from the [acx project site]("http://acx100.sourceforge.net/wiki/Firmware"), but I can't find the particular firmware that your driver wants.  Do you have a Windows driver for this card?  If so, please upload it here...hopefully there will be a way to extract the firmware from it.

Also, do you know the exact name that this card was sold under?  Or does it say anything on the card itself?  Maybe we can find a Windows driver that way.

---

### Post by raydanator on 2008-09-16
Alright I copied the User Guide, Driver, and Utility folders from the disc: 

[http://www.mediafire.com/?sharekey=228737620b99d04fab1eab3e9fa335ca7e195b2b7b56f6ed](http://www.mediafire.com/?sharekey=228737620b99d04fab1eab3e9fa335ca7e195b2b7b56f6ed)

[http://www.mediafire.com/?sharekey=228737620b99d04fab1eab3e9fa335caec6f7d86dfbd0859](http://www.mediafire.com/?sharekey=228737620b99d04fab1eab3e9fa335caec6f7d86dfbd0859)

[http://www.mediafire.com/?sharekey=228737620b99d04fab1eab3e9fa335cabf57b81b2de03ec2](http://www.mediafire.com/?sharekey=228737620b99d04fab1eab3e9fa335cabf57b81b2de03ec2)

The User Guide should have the most detailed info on the card, but I think its called "NWH1022 802.11b+ CardBus Adapter". I'm still concerned as to why I couldn't connect with an ethernet cable though. Was I just doing something wrong? Thanks for your continued patience.

---

### Post by pytheas22 on 2008-09-16
Thanks for those files.  I'll go through them and see if I can figure out where the firmware is (I've never done stuff like that before, but I assume Google has instructions somewhere).

In the meantime, I found a firmware file that might work (probably not, but it's worth a try).  You can install it by downloading [this file]("http://www.ivor.it/wireless/Acx100Drv/acx100sta.o.gz") on a computer that has a connection, then moving it (via a USB drive for example) to your desktop on Ubuntu and running:
```

cd ~/Desktop
gunzip acx100sta.o.gz
sudo cp acx100sta.o /lib/firmware
```

As for the ethernet, did it ever work on this computer under Linux?  In the 'lshw' output that you posted a few days ago, I don't see an ethernet interface even mentioned--normally it would at least be listed, even if there's no driver for it or it won't work for some other reason.  Are you sure that your ethernet card is securely in the computer and that it works (that is, that the hardware itself is not broken)?  Also, are you sure you weren't trying to plug an ethernet cable into the 56k modem jack?  You have a modem, and it would look similar to an ethernet jack, but the modem port would be a bit smaller.

---

### Post by pytheas22 on 2008-09-16
I found a few firmwares file that might work for you: they are [here]("http://burnthesorbonne.com/files/tiacx100") and [here]("http://burnthesorbonne.com/files/tiacx100r15") (you may need to right-click and say 'save target as' to download them properly).  Please save each of the files to your desktop on Ubuntu, then run these commands to copy them to the firmware directory:
```

cd ~/Desktop
sudo cp tiacx100 /lib/firmware
sudo cp tiacx100r15 /lib/firmware
```

Then reboot.  Hopefully the wireless will work.  If not, please post the output of:
```

iwconfig
lshw -C Network
dmesg | grep -e acx
```

---

### Post by raydanator on 2008-09-16
Dude, you are the man! Thank you very much. I will try out those firmware upgrades and reply soon. 

I tried the previous one you gave me and am not sure if it worked, since I don't have my router yet. I will run the second code by you after I install the firmware, and hopefully you can tell if it worked or not. Or I will know in a couple days. 

Its a weird thing with that ethernet- I'm sure I have both the 56k and ethernet connections, telling from the logos. I popped a cap out of the ethernet port before using it, which is odd, and it didn't work. 

Maybe the hardware has been taken out, or damaged like you said. Is there a code I should run to check that? 

Anyway, even if this doesn't work thank you very much for all the help. I really appreciate it! 

I'll post back as soon  as I can.

---

### Post by pytheas22 on 2008-09-16
You could check the output of the command:
```

lspci -nn
```

to see if that finds any ethernet device (lspci lists all devices in your computer).  I doubt it will, though.  I suspect hardware failure if there's an ethernet device but Linux can't see that it's there at all.

Hoping those firmware files work...

---

### Post by raydanator on 2008-09-19
Sorry to take so long in getting back, classes have been crazy. So here’s where I’m at: I ran the firmware codes you modded, as well as the previous ones. I ran into a problem though, as you can tell by the log.

 After copying the text files to my desktop, I was prompted for sudo password, and after entering (it was blank by the way, I suppose that’s normal) was given the ‘no such file’ message. I ran the other codes anyway, but am I doing something wrong? I have been booting the system in “Run Xclient Script”, but I think that’s the normal boot option. 

One thing though- in windows I can view the entire text firmware file. But in Xubuntu, I’m seeing three or four characters only…which seems kind of odd. Hope that helps 

danny@Danny-Laptop:~$ cd ~/Desktop
danny@Danny-Laptop:~/Desktop$ sudo cp tiacx100 /lib/firmware
[sudo] password for danny: 
cp: cannot stat `tiacx100': No such file or directory
danny@Danny-Laptop:~/Desktop$ sudo cp tiacx100r15 /lib/firmware
cp: cannot stat `tiacx100r15': No such file or directory
danny@Danny-Laptop:~/Desktop$ iwconfig
lo        no wireless extensions.

wlan0     IEEE 802.11b+  ESSID:""  Nickname:"acx v0.3.36"
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Bit Rate:22 Mb/s   Tx-Power=18 dBm   Sensitivity=176/255  
          Retry min limit:7   RTS thr:off   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

danny@Danny-Laptop:~/Desktop$ lshw -C Network
WARNING: you should run this program as super-user.
  *-network               
       description: Wireless interface
       product: ACX 100 22Mbps Wireless Interface
       vendor: Texas Instruments
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 00
       serial: 00:80:c6:e6:97:30
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=acx_pci latency=64 module=acx multicast=yes wireless=IEEE 802.11b+
danny@Danny-Laptop:~/Desktop$ dmesg | grep -e acx
[   56.962619] acx: Loaded combined PCI/USB driver, firmware_ver=default
[   56.962631] acx: compiled to use 32bit I/O access. I/O timing issues might occur, such as non-working firmware upload. Report them
[   56.962839] acx: found ACX100-based wireless network card at 0000:03:00.0, irq:11, phymem1:0x20010000, phymem2:0x20000000, mem1:0xd0a78000, mem1_size:4096, mem2:0xd0ae0000, mem2_size:65536
[   56.963883] acx: loading firmware for acx100 chipset with radio ID 15
[   57.038013] acx: firmware image 'acx/default/tiacx100c15' was not provided. Check your hotplug scripts
[   57.349527] acx: loading radio image for radio 15
[   58.024985] acx: === chipset TNETW1100A, radio type 0x15 (Ralink), form factor 0x01 ((mini-)PCI / CardBus), EEPROM version 0x05: uploaded firmware 'Rev 1.9.8.b' ===
[   58.025800] acx v0.3.36: net device wlan0, driver compiled against wireless extensions 22 and Linux 2.6.24-19-generic
[   58.025937] usbcore: registered new interface driver acx_usb
danny@Danny-Laptop:~/Desktop$ lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation 82815 815 Chipset Host Bridge and Memory Controller Hub [8086:1130] (rev 02)
00:01.0 PCI bridge [0604]: Intel Corporation 82815 815 Chipset AGP Bridge [8086:1131] (rev 02)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev 03)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801BAM ISA Bridge (LPC) [8086:244c] (rev 03)
00:1f.1 IDE interface [0101]: Intel Corporation 82801BAM IDE U100 Controller [8086:244a] (rev 03)
00:1f.2 USB Controller [0c03]: Intel Corporation 82801BA/BAM USB Controller #1 [8086:2442] (rev 03)
01:00.0 VGA compatible controller [0300]: ATI Technologies Inc Rage Mobility M4 AGP [1002:4d46]
02:03.0 Multimedia audio controller [0401]: ESS Technology ES1983S Maestro-3i PCI Audio Accelerator [125d:1998] (rev 10)
02:06.0 Communication controller [0780]: Agere Systems WinModem 56k [11c1:0448] (rev 01)
02:0f.0 CardBus bridge [0607]: Texas Instruments PCI4451 PC card Cardbus Controller [104c:ac42]
02:0f.1 CardBus bridge [0607]: Texas Instruments PCI4451 PC card Cardbus Controller [104c:ac42]
02:0f.2 FireWire (IEEE 1394) [0c00]: Texas Instruments PCI4451 IEEE-1394 Controller [104c:8027]
03:00.0 Network controller [0280]: Texas Instruments ACX 100 22Mbps Wireless Interface [104c:8400]
danny@Danny-Laptop:~/Desktop$

---

### Post by pytheas22 on 2008-09-19
It looks like the firmware files were not on your desktop in Ubuntu when you ran the commands that were supposed to copy them into the system directory where they need to be.  Did you download those two files that I linked to in post #13 and put them on your Ubuntu desktop?  If they were transferred correctly, you should see two files on your desktop named 'tiacx100' and 'tiacx100r15'

I'm not sure what the Xclient option does.  Is there a reason you're not logging in with the default options (you're using Gnome, right)?  Do you see any icons on your desktop (if there are any; by default I think it comes empty in Ubuntu, but you could add an icon by right-clicking and creating a launcher)?

Please make sure that those two firmware files are on your desktop, then try running the commands from post #13 again.
> 
I was prompted for sudo password, and after entering (it was blank by the way, I suppose that’s normal)

Yes, it's supposed to be that way for security reasons.

---

### Post by raydanator on 2008-09-20
Yes, I did save them to my desktop. Dragged both text files directly from jump drive to Desktop and made two icons. Isn't it a little strange for most of the text to be missing from them though? Or is that just how xubuntu reads the files? 

The reason I am not sure about the login is that a friend was in a different mode, and it might not have reverted back. But I tried several different types of login, and they all worked about the same. 
 
I've run the commmands in terminal several times before, but to no avail. I doubt its the login honestly, since I can still transfer files, and type commands just fine. If you're at a loss for ideas though, I can just buy a card...it wouldn't be the end of the world. Let me know, thanks

---

### Post by pytheas22 on 2008-09-20
Let's at least get the files copied--it really shouldn't be hard--and if they don't do the trick, maybe then you can think about getting a new card.

Here's an alternate way to copy the files.  First, type this in a terminal:
```

sudo thunar /lib/firmware
```

and a graphical file-browser window should open up, to the location /lib/firmware (if you're not at /lib/firmware, navigate to it).  Then drag and drop the two firmware files from your USB drive into the /lib/firmware window.  If it works, you should see icons for the firmware files appear in the /lib/firmware window.  Does this happen?

Also, yes, it's strange that the text in the firmware files is different in Xubuntu and Windows.  Perhaps it's just caused by the different methods used to try to read the files--they're binary files, not text (when you read them in Windows, it's all just jumbled garbage, right?), so you're not supposed to be able to open them in a text editor, but maybe Windows can open more of the file than Xubuntu.  Look at the sizes of the files in Windows and Xubuntu, though--are they the same size under both operating systems?  If not, that could be a problem.

---

### Post by raydanator on 2008-09-24
Sorry about the delay again. I did what you suggested, copying the firmware files to the /lib/firmware folder from terminal. I actually found the acx100sta.o.gz folder in there as well...or it may have been the extracted file, one of the two. When I tried accessing a network though, it kept loading and loading, and finally gave the 'no connections' icon. I plugged in my friend's linksys usb drive, and it worked almost instantaneously. So, I think I might buy something like that. 

I used my cousin's usb card here: [http://www.amazon.com/gp/product/product-description/B000CRFI8A/ref=dp_proddesc_0?ie=UTF8&n=172282&s=electronics](http://www.amazon.com/gp/product/product-description/B000CRFI8A/ref=dp_proddesc_0?ie=UTF8&n=172282&s=electronics)

But am thinking of getting something like this here: [http://www.amazon.com/Linksys-WPC54GS-Wireless-G-Notebook-SpeedBooster/dp/B0001D3JXG/ref=pd_bbs_4?ie=UTF8&s=electronics&qid=1222270784&sr=8-4](http://www.amazon.com/Linksys-WPC54GS-Wireless-G-Notebook-SpeedBooster/dp/B0001D3JXG/ref=pd_bbs_4?ie=UTF8&s=electronics&qid=1222270784&sr=8-4)

And a router such as: [http://www.amazon.com/Linksys-WRT54GS-Wireless-G-Broadband-SpeedBooster/dp/B0001D3K8A/ref=pd_bbs_sr_3?ie=UTF8&s=electronics&qid=1222271285&sr=8-3](http://www.amazon.com/Linksys-WRT54GS-Wireless-G-Broadband-SpeedBooster/dp/B0001D3K8A/ref=pd_bbs_sr_3?ie=UTF8&s=electronics&qid=1222271285&sr=8-3)

Anyway, hope I'm not letting you down or anything. I appreciate all the work you've put into helping me get this working, but I think it would be best to buy a different one for linux, especially if the old card gives my mom trouble.

Also, do I need to get an 'N' network or a 'G' Network?  Thanks for all the help!

---

### Post by pytheas22 on 2008-09-24
Sorry that the attempts to get the original card working were not successful.  It could probably be done if you try long and hard enough (I guess that's the desideratum of Linux) but I agree that it might make more sense just to buy a new card that you know will work well.  

The cards you link to might "just work," but one of the problems with wireless cards is that manufacturers tend to change the insides of them (the chipset) without changing the name under which they're sold.  Sometimes they'll change the "version" or "revision" number of the card when they change the chipset, but sometimes they don't even bother to do that.  So this can lead to a lot of confusion, since you might have two wireless cards that look exactly the same and are sold under exactly the same name, yet are completely different on the inside, with very different behavior in Linux as a result.

I've heard of the WUSB54GC working great for some people, but being a disaster for others, and I suspect (haven't looked into it enough to be sure) that the problem is that there's one version of the WUSB54GC that has a chipset that Linux likes, and another version that doesn't--even though the name on the box is identical in both cases.

So what this really means is that you should be careful when purchasing the card to make sure that it has a chipset that will be supported.  You might want to try emailing Amazon to ask if they can tell you which chipset is going to be in the card that you buy from them.  Either that, or buy from a local store where you can return the card easily if it doesn't work (these stores, e.g. Best Buy, tend to be drastically more expensive than Internet vendors, however, and have a poor selection to choose from when buying hardware, in my experience).

In general, cards with Ralink, Atheros, Intel, Prism and (usually) Broadcom chipsets should work pretty painlessly in Linux.

[This page]("https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported") has a list of wireless cards that are supposed to work well in Ubuntu, but again, be sure that the version of the card that you buy is the same as the one that's supposed to work.

The router shouldn't matter; any home router should work with Linux as well as any other.  Just buy whatever fits your budget.  Make sure it supports at least G mode (some very old routers may only support B or A modes, but I doubt that these are even on the market anymore).

As for G vs N mode: N mode is the newest wireless standard and supports faster transfer rates and wider wireless range than G, so N is better if you can afford it (but G will still work fine for most people).  However, keep in mind that not all wireless drivers (in Linux or Windows) have full support for N mode yet, so you may not be able to use it.  In addition, not all routers support N mode (if you buy an N card and want to use it in N mode, be sure to also buy an N router).  On the other hand, most N cards and routers are backwards-compatible, meaning that they should be able to operate in G mode as well without issue.  So the bottom line: N is better if you can afford it and all of your hardware and software will support it; otherwise G should get the job done almost as well.

---

### Post by raydanator on 2008-09-26
Yes, I think with enough time the card could certainly be made to work, but like you said, it makes more sense to spend the money for a working card.

Thanks for explaining the difference in networks. I think we will buy an 'N' router at Best Buy this weekend, and I'll purchase the card online.

And thanks for that link, it's exactly what I needed. I learned that there are about 7 -10 chipset/version combinations of the WUSB54G PCMCIA. I emailed some of the Amazon dealers, and am sure I could find a correct one eventually, but I'm leaning towards this USB Linksys here: 

[http://www.amazon.com/Linksys-WUSB54GC-Compact-Wireless-G-Adapter/dp/B000CRFI8A/ref=pd_bbs_2?ie=UTF8&s=electronics&qid=1222453856&sr=8-2](http://www.amazon.com/Linksys-WUSB54GC-Compact-Wireless-G-Adapter/dp/B000CRFI8A/ref=pd_bbs_2?ie=UTF8&s=electronics&qid=1222453856&sr=8-2)

 Is there a big difference between USB and PCMCIA besides port availability? It might be harder to find the PCMCIA card in the right version, plus I know this card works with my system (I tried my cousin's). And it seems that USB are more versatile-- on desktops for example. The downside being that it consumes one of my two usb ports. What do you think? Do you have a preference over one?

---

### Post by pytheas22 on 2008-09-27
In terms of performance, I don't know of any major differences between PCMCIA and USB.  I tend to prefer USB because, as you mention, you can use it in a desktop as well if you ever have a reason to.  I guess the only disadvantage is that USB is a little more awkward sticking out of your laptop, but if you get a small-profile card it shouldn't be a big deal.

---

### Post by raydanator on 2008-09-28
Ok, I'll keep that in mind. Thanks for the advice, and all the help!

---

