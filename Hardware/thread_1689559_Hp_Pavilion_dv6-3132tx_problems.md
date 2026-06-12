---
title: "Hp Pavilion dv6-3132tx problems"
date: 2011-02-17
forum: Hardware
---

### Post by Jagoly on 2011-02-17
Hello. I recently (about christmas time) purchased a HP-Pavilion dv6-3132tx Notebook PC (h10010.www1.hp.com/wwpc/au/en/ho/WF06b/321957-321957-3329744-64354-64354-4247579-4344631). It is currently Dual Booted with Windows 7 (OEM) and Linux Mint 10 Gnome (both 64 bit). I have also got a registered version Win7Home in a virtualbox VM. For this reason, I would really prefer not to reinstall Mint (unless someone knows how to safely move a VM). I don't like to call myself a linux n00b, despite the fact that I probably am one.

Last year, on my old Toshiba laptop, Mint 9 and 10 both worked flawlessy. Wireless, graphics, Webcam and touchpad and all worked out of the box. I fell in love with Ubuntu at that moment, although I have been experimenting with ubuntu for a few years now, on both my old dell desktop (I could not get my Belkin N Wireless adapter to work) and my PS3 (nothing suported ppc64). Anyway I better get to my problem.

Mint 10 isn't all that rosey on this machine. Wireless only works via NDISWrapper (sometimes). My fingerprint scanner fails, I have no webcam. I did partially manage to get the multi-touchpad working (no pinch-to-zoom).

Then there are the real problems. Almost every time I boot the Machine, I am Greeted by a useless Terminal. I do not know what causes it, it seems completely random. One in four times in does manage to boot.

There is also the freezing. It just happens randomly while I am using Mint and the only way to Quit is a Hard Reset. Most of the time this is a kernel problem, as I have read is indicated by the flashing caps lock key. I tried installing a later kernel (2.6.35 from 2.6.32). When I choose this in the grub, I cannot even start. If I do manage to avoid the terminal boot, I am greeted by my screen backlight turning on and off indefinatley.

Please. I love Ubuntu and Mint. I even managed to figure out g++ to do my programing. Help Me!:(

---

### Post by Perfect Storm on 2011-02-17
Please use the mint forum, thanks.

You'll find it here: [http://forums.linuxmint.com/](http://forums.linuxmint.com/)


Thread closed.

---

### Post by Joeb454 on 2011-02-17
Thread re-opened.

Please note, however, that the mint forums may give a better answer :)

---

### Post by Jagoly on 2011-02-17
Thank you! I really don't mind the mint forums. I used to be a frequent member of the ZodTTD forums. That was a speck compared to the mint forums. There, however I gave advice. This is fine on a small forum. Now I am seeking help, and bigger forums make that oh so much easier. I actually need a debian based OS for school very soon, so I don't have the time to wait for help on the LMF's. Thanks again!

---

### Post by bapoumba on 2011-02-17
I have changed the thread prefix > other_os.

---

### Post by Jagoly on 2011-02-18
!!!On the actuall problem!!!

When I disable the proprietary ATI graphics driver, I can boot and freezing has dramatically decreased. But:
I NEED COMPIZ!!!
No wobbly windows... No transparency... No expo... No window snap... None of my custom gconf stuff...
I NEED COMPIZ!!!

Please help... Because...
I NEED COMPIZ!!!

---

### Post by Zimmer on 2011-02-21
To answer one question: export your VM to a safe location/partition for re import when the dust has settled. :)

I am not an ATI guru and there may be no definitive answer to your problem other than the driver.I chose a DV6000 with an NVidia card when I purchased a new laptop (64bit) . However, I have always used the 32bit version of Ubuntu/Mint/PCLinuxOS Mepis (I try them out from an external drive and have a dual boot on the laptop drive with a separate partition for ALL my important files, VMs included. I can therefore run any OS and access my data...)

The point is, that without ATI expert help (or even with it) you may have to try a 32bit version and see if you can get the ATI drivers and compiz to play nicely .
If they do not, then you may have give up on Compiz .

Do you have an external drive? Worth a try.....

---

### Post by Zimmer on 2011-02-21
[http://wiki.cchtml.com/index.php/Hardware](http://wiki.cchtml.com/index.php/Hardware)
There are other links here proposing various workarounds, but it seems there is little (no ?) formal support for that card..
[http://ubuntuforums.org/showthread.php?t=1422762](http://ubuntuforums.org/showthread.php?t=1422762)
[http://ubuntuforums.org/showthread.php?t=1629799](http://ubuntuforums.org/showthread.php?t=1629799)

Might be relevant .. not sure..

[http://kubuntuforums.net/forums/index.php?topic=3109821.0](http://kubuntuforums.net/forums/index.php?topic=3109821.0)

---

### Post by cascade9 on 2011-02-22
Sure soudns like it could be a GPU driver problem. 

AFAIK, the PPAs dont have the newest Catalyst 11.2 drivers (released 15-02-2011), manualy installign them might be the only way to get them going. See here- 

[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

Should work for mint as well. ;) 
****

---

### Post by Jagoly on 2011-02-23
I actually had already tried that... It made the OS completely unbootable (until removed with the live cd).

Anyway I stuffed up mint anyway. I sort of accidentally set the permissions for the entire mint partion to user access. I can no longer boot mint. I had to re-install, so I thought I would give regular ubuntu a shot. With latest (in the repo) kernel and the repo ati drivers, everything (graphically) works fine. Guess mint may have had some strange compatibility issues.

But now I cannot get the wireless working. I attempted to compile some drivers and tried some other stuff, but failed miserabely. Now there is not even a wireless icon on the menubar. Is there a way to wipe a kernel back to generic or some other wireless-fixing magic to get it working?

Ubuntu 10.10 GNOME 64bit
rt2860/rt3090/(?) wireless

---

### Post by Zimmer on 2011-02-23
[https://help.ubuntu.com/community/NetworkDevices](https://help.ubuntu.com/community/NetworkDevices)
if there is any magic the spells could be found above.

(guess what, when I picked this HP laptop I checked out the wireless card first.... it was a minefield of specs and still is very difficult to get the gen on the hardware in laptops at a store. It requires a lot of internet searching the full model codes...and even then you may not find the info :(  )

---

### Post by Jagoly on 2011-02-24
Thanks, but there is a big problem: previouse attempts of getting the wireless to work had completeley screwed the wireless. When ubuntu was first installed, it showed a wireless icon, and sometimes even picked up my router, but I could never connect. Now there isn't even a wireless icon on the panel and I can't try anything new at the moment.

Does anyone know how to wipe away my faulty kernel modules so that I can try again?

---

### Post by Jagoly on 2011-02-25
Come on... I really don't want to reinstall again...I have stuff.
The wireless worked on mint, so I know this isn't a lost cause.

---

### Post by Jagoly on 2011-02-27
If it is impossible to reset at least say so.
That way I can just reinstall.
Getting annoyed.

---

### Post by Yellow Pasque on 2011-02-27
It would really help to know what kind of hardware you have:
```
sudo update-pciids
lspci
```
Also, it would good to know the output of:
```
sudo iwconfig
```

---

### Post by Jagoly on 2011-02-28
Thanks! I'll edit in about half an hour with the results.
```
00:00.0 Host bridge: Intel Corporation Core Processor DMI (rev 11)
00:03.0 PCI bridge: Intel Corporation Core Processor PCI Express Root Port 1 (rev 11)
00:08.0 System peripheral: Intel Corporation Core Processor System Management Registers (rev 11)
00:08.1 System peripheral: Intel Corporation Core Processor Semaphore and Scratchpad Registers (rev 11)
00:08.2 System peripheral: Intel Corporation Core Processor System Control and Status Registers (rev 11)
00:08.3 System peripheral: Intel Corporation Core Processor Miscellaneous Registers (rev 11)
00:10.0 System peripheral: Intel Corporation Core Processor QPI Link (rev 11)
00:10.1 System peripheral: Intel Corporation Core Processor QPI Routing and Protocol Registers (rev 11)
00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 05)
00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 05)
00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a5)
00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 05)
01:00.0 VGA compatible controller: ATI Technologies Inc Redwood [Radeon HD 5600 Series]
01:00.1 Audio device: ATI Technologies Inc Redwood HDMI Audio [Radeon HD 5600 Series]
**02:00.0 Network controller: RaLink RT3090 Wireless 802.11n 1T/1R PCIe**
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 03)
7f:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-Core Registers (rev 04)
7f:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 04)
7f:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 04)
7f:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 04)
7f:03.0 Host bridge: Intel Corporation Core Processor Integrated Memory Controller (rev 04)
7f:03.1 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Target Address Decoder (rev 04)
7f:03.4 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Test Registers (rev 04)
7f:04.0 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 0 Control Registers (rev 04)
7f:04.1 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 0 Address Registers (rev 04)
7f:04.2 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 0 Rank Registers (rev 04)
7f:04.3 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 0 Thermal Control Registers (rev 04)
7f:05.0 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 1 Control Registers (rev 04)
7f:05.1 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 1 Address Registers (rev 04)
7f:05.2 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 1 Rank Registers (rev 04)
7f:05.3 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 1 Thermal Control Registers (rev 04)


```

and

```
lo        no wireless extensions.

eth0      no wireless extensions.

```

---

### Post by Jagoly on 2011-03-01
Please help... I went on a rant today about the awesomeness of ubuntu/Linux and how terrible windows is. Don't make me have to take my laptop to school next week running windows...

---

### Post by cascade9 on 2011-03-01
Try post #3 from this thread- 

[http://ubuntuforums.org/showthread.php?t=1600498](http://ubuntuforums.org/showthread.php?t=1600498)

---

### Post by Jagoly on 2011-03-01
No luck... I have messed it up beyond repair. I'll try this again after a reinstall on the weekend. Would you say that it is worth bothering to update the fresh install first? It's very difficult to get a wired net connection. Much arguing with my computer-hating mum. Also our monthly download allowance is tiny.

---

### Post by Jagoly on 2011-03-02
[B]I love everyone!
IT WORKED!!!
IT WORKED!!!
I'M WRITING THIS IN FIREFOX FROM (DOUBLE CAPITAL) UBUNTU!!!
I REINSTALLED, TRIED THE ABOVE AGAIN, AND, YAY!!!
WI-FI!!!
NO NEED TO UPDATE FIRST!!!
And with that, this problem is solved (until I stuff up something else, of course).[/B]

:popcorn:

---

### Post by bigbadsi on 2011-03-04
Hi Jagoly

I'm considering buying this notebook and would appreciate your opinion on its Ubuntubility (yes, that's a word now).

Does all your hardware work out of the box and what sort of performance does your video card give?  Can you game on your notebook?  If the machine came with Windows 7, were you able to repartition and retain the Windows install and recovery partitions?

Thanks.

---

### Post by Jagoly on 2011-03-05
> **bigbadsi said:**
> Hi Jagoly

I'm considering buying this notebook and would appreciate your opinion on its Ubuntubility (yes, that's a word now).

Does all your hardware work out of the box and what sort of performance does your video card give?  Can you game on your notebook?  If the machine came with Windows 7, were you able to repartition and retain the Windows install and recovery partitions?

Thanks.

I feel special now...
Out of the box, for me, it was a nightmare.
But after my last reinstall i had almost everything working in half an hour (60% of which was downloading)
You just need to know what to do.

I currently have working n-wireless (no adhoc yet), accelerated 2d/3d graphics via the ATI raedon card, support for the multi-touch pad, all of the shortcut keys except one, headphone jack and Bluetooth.
However, it terms of what I haven't gotten to work yet, there is the fingerprint scanner, webcam and microphone. I haven't tried to set up the webcam or microphone yet, because I would rarely use them. But I do miss the fingerprint scanner. There are no Linux drivers for it.

Partitioning is no problem. When I tried to install ubuntu on my friends laptop, we were unable to partition. However there are no problems here. Just DO NOT CLOSE THE LID DURING A PARTITION. IT WILL FREEZE AND CORRUPT THE HARD DRIVE. Also make sure in power settings that the machine won't go onto standby or turn off the screen. Stay near the machine to monitor it at all times.

If anyone wants them, I will write instructions to set up everything I have working

---

### Post by Jagoly on 2011-03-09
Just an update: Bluetooth DOES NOT work. I hadn't tried it. Don't know why I said it did. The wireless driver I installed says that it is for my ralink wireless/ motorola Bluetooth combo. Anyone know a quick fix?

---

### Post by Yellow Pasque on 2011-03-09
These things usually get fixed in newer kernels. Compiling new kernel modules for your current kernel is also a possibility, but you need to know what module is in question.
See what the output of this produces:
```
sudo lshw -C network
```

---

### Post by Jagoly on 2011-03-09
```
  *-network               
       description: Wireless interface
       product: RT3090 Wireless 802.11n 1T/1R PCIe
       vendor: RaLink
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 00
       serial: 70:f3:95:e7:5b:3c
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rt2860 ip=10.0.0.1 latency=0 multicast=yes wireless=Ralink STA
       resources: irq:16 memory:d3000000-d300ffff
  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 03
       serial: 60:eb:69:6f:ac:28
       size: 10MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 1bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10MB/s
       resources: irq:48 ioport:2000(size=256) memory:d1004000-d1004fff memory:d1000000-d1003fff memory:d1010000-d101ffff
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: vboxnet0
       serial: 0a:00:27:00:00:00
       capabilities: ethernet physical
       configuration: broadcast=yes multicast=yes
```

i can't see anything about bluetooth. the bt applet thinks it is working, but can't find any devices and doesn't emmit any signal. thanks

---

### Post by bigbadsi on 2011-03-18
Hi Jagoly

Thanks for your advice.  

This hardware is thoroughly kick-****.

Alas, I'm committed to only buying kit that works out of the box.

Definitely post your work-arounds.  This is how we learn.

Thanks again.

S

---

### Post by Jagoly on 2011-03-18
I write it tonight, after I finish my homework.
Huzza!

---

### Post by kalex on 2011-04-02
I dual-boot Windows 7 and Ubuntu on my dv6-3132tx. 

I originally installed Ubuntu 10.04 (32-bit) with no major problems (Wi-Fi, LAN, network printer and video all worked fine), but as it was 32-bit, it could only access the first 4 GB of my 8 GB RAM. So I installed 10.10 (64-bit) to get access to all 8 GB.

The 8 GB ws fine on 64-bit Linux, but it didn't work with the WiFi driver. I solved this by doing this: [http://ubuntuforums.org/showthread.php?t=1600498]("http://ubuntuforums.org/showthread.php?t=1600498")

The next problem was that I couldn't load the driver for my Fuji-Xerox laser printer because alien refused to install a 32-bit driver on 64-bit hardware. So I did it myself.

Now everything works fine on Ubuntu 1.10 (64-bit) except:  bluetooth (not tested, but might work with the updated WiFi driver above - anyway WiFi, USB and SD card reader are more useful) and fingerprint reader (no drivers - suggested driver doesn't compile as it requires qt3 when only qt4 is available now). The lack of a fingerprint driver is my only complaint. 

The webcam works fine; use cheese, for example, to view the webcam output.

By the way, the only problem with partitioning the disk is that there is a limit of 4 primary partitions, of which 2 are used by Windows (System and C:) and 2 by HP (HP tools and HP Recovery). No problem to delete HP tools (appears to be a waste of space) and HP recovery can deleted after you use the HP Recovery Manager to make DVDs, which is all you can use anyway if your disk is not recoverable.

All in all, very happy with Ubuntu 10.10 on dv6-3132tx, especially as I can boot into Windows 7 if I ever need to use bluetooth.

---

### Post by Jagoly on 2011-04-03
> **kalex said:**
> I dual-boot Windows 7 and Ubuntu on my dv6-3132tx. 

I originally installed Ubuntu 10.04 (32-bit) with no major problems (Wi-Fi, LAN, network printer and video all worked fine), but as it was 32-bit, it could only access the first 4 GB of my 8 GB RAM. So I installed 10.10 (64-bit) to get access to all 8 GB.

The 8 GB ws fine on 64-bit Linux, but it didn't work with the WiFi driver. I solved this by doing this: [http://ubuntuforums.org/showthread.php?t=1600498]("http://ubuntuforums.org/showthread.php?t=1600498")

The next problem was that I couldn't load the driver for my Fuji-Xerox laser printer because alien refused to install a 32-bit driver on 64-bit hardware. So I did it myself.

Now everything works fine on Ubuntu 1.10 (64-bit) except:  bluetooth (not tested, but might work with the updated WiFi driver above - anyway WiFi, USB and SD card reader are more useful) and fingerprint reader (no drivers - suggested driver doesn't compile as it requires qt3 when only qt4 is available now). The lack of a fingerprint driver is my only complaint. 

The webcam works fine; use cheese, for example, to view the webcam output.

By the way, the only problem with partitioning the disk is that there is a limit of 4 primary partitions, of which 2 are used by Windows (System and C:) and 2 by HP (HP tools and HP Recovery). No problem to delete HP tools (appears to be a waste of space) and HP recovery can deleted after you use the HP Recovery Manager to make DVDs, which is all you can use anyway if your disk is not recoverable.

All in all, very happy with Ubuntu 10.10 on dv6-3132tx, especially as I can boot into Windows 7 if I ever need to use bluetooth.

Cool! 

I find the fact lack of the fingerprint scanner to be my biggest complaint too. For me, the Bluetooth doesn't work with the latest wireless drivers, I would use it to connect ps3 controllers for use with emulators :(

Great that the webcam works for you. I still need to try it. I don't really use it myself. I don't really like live chat. I prefer forums and email. Or real life people :)

PS: What's wrong with just using extended partitions?

---

### Post by kalex on 2011-04-03
> **Jagoly said:**
> Cool! 

I find the fact lack of the fingerprint scanner to be my biggest complaint too. For me, the Bluetooth doesn't work with the latest wireless drivers, I would use it to connect ps3 controllers for use with emulators :(

Great that the webcam works for you. I still need to try it. I don't really use it myself. I don't really like live chat. I prefer forums and email. Or real life people :)

PS: What's wrong with just using extended partitions?

You need at least 1 spare primary partition on which to install Linux. This primary partition can then be divided into any number of extended partitions to give you separate root and swap partitions, and I also have another which I formatted as NTFS so that both Linux and Windows can read & write files on it.

---

### Post by Jagoly on 2011-04-04
Hmm... My computer never actually had a HP recovery partition

My drive originally:

System
Windows
HP Tools


My Drive now:

System
Windows
{Ubuntu, Swap}
HP Tools

---

