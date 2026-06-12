---
title: "Another question - problem with display and wireless card drivers"
date: 2006-08-28
forum: Hardware &amp; Laptops
---

### Post by TheMatt on 2006-08-28
I just got Ubuntu installed, but I have two drivers that seem to be causing trouble.
 
My display driver - I can only set the resolution to 1024 x 768. My laptop screen is 1280 x 800.
 
My wireless card driver - My wireless card is recognized in the device manager correctly, but I cannot connect to our wireless network
 
Help with these issues would be greatly appreciated.

---

### Post by ltmon on 2006-08-28
Hi,

What kind of graphics card and wireless card do you have?  If you don't know how to find this out let me know and I'll show you.

Also, what kind of laptop is it?

Cheers,

L.

---

### Post by TheMatt on 2006-08-28
Hi, and thanks for the response.

The graphics card is an integrated SiS M760GX (SiS Mirage 330) 128 MB IGP.
[http://www.sis.com/products/sism760gx_features.htm](http://www.sis.com/products/sism760gx_features.htm)


The Wireless Card is a Broadcom BCM4318 AirForce card.
[http://www.broadcom.com/products/Wireless-LAN/802.11-Wireless-LAN-Solutions/BCM4318E](http://www.broadcom.com/products/Wireless-LAN/802.11-Wireless-LAN-Solutions/BCM4318E)


The laptop is an Acer Aspire 3003WLCi.
Here is the complete (and very detailed) specs.
```
Acer Aspire 3003WLCi Laptop Specs:

Operating System:
  OS1 Name: Windows XP Home
  Service Pack: SP2 
  Version: 5.1.2600
  OS2 Name: Linux
  Distribution: Ubuntu
  Version: Dapper Drake 6.06
Motherboard:
  Chipset: SiS M760GX
  Northbridge: SiS 760
  Southbridge: SiS LPC Bridge
  FSB Type: AMD Hammer
  FSB Clock: 800 MHz x 2 HT
  CPU Socket: Socket 754
  Supported CPUs: Mobile AMD Sempron, AMD Turion 64 Mobile
  RAM Type: 200 Pin DDR333
  RAM Slots: 2
  Max supported RAM: 4096 MB
  PATA Storage: 2 x ATA/100
  SATA Storage: No
  Ports: 3 x USB 2.0
  Onboard Devices: Graphics, Sound, LAN, Modem
BIOS:
  Name: Phoenix NoteBIOS
  Version: 3A27
  Date: 8/24/05
Processor (CPU):
  Brand: Mobile AMD Sempron LV
  Model: 3000+
  Core: Palermo
  Package: Socket 754
  Clock Speed: 1.8 Ghz (9 x 200 MHz)
  L1 Code Cache: 64 KB Parity
  L1 Data Cache: 64 KB ECC
  L2 Cache: 128 KB On-die, ECC
  Instruction Sets: MMX, SSE, SSE2, 3DNow! Professional
  Process Type: 90 nm
  64 Bit Instruction Support: No
  Voltage: 1.4 v
  Wattage: 25 W
  Power Management: Yes, Disabled
  Overclocked: Yes
  Overclock Amount: 11 %
Memory (RAM):
  Brand: Corsair ValueSelect
  Amount: 2 x 512 MB
  Type: DDR400 SDRAM
  Pins: 200
  Memory Speed: PC3200
  Clock Speed: 200 MHz x 2
  Timings: 2.5-3-3-7
  Dual Channel: Yes, Enabled
Hard Disk Drive:
  Brand: Hitachi (IBM) Travelstar
  Size: 2.5"
  Capacity: 80 GB 
  Interface: PATA (IDE)
  Max Transfer Rate: 100 MB/s
  Active UDMA Transfer Mode: UDMA 5
  Rotational Speed: 4200 RPM
  Buffer Size (Cache): 8 MB
  Sectors Per Track: 63
  Bytes Per Sector: 512
  Average Latency: 7.1 ms
  Average Seek Time: 12 ms
  S.M.A.R.T.: Yes, Enabled
  Configguration: Primary Master
Optical Drive:
  Brand: Pioneer
  Interface: ATAPI
  Type: CD/DVD±RW DL
  Reading Capabilities: 24x CD-ROM, 8x DVD-ROM
  Writing Capibilities: 24x CD-R/RW, 8x DVD±R/RW, 4x DVD±R DL
  Configguration: Secondary Master
Graphics Card (IGP):
  Brand: SiS Mirage 330
  Interface: AGP (Integrated)
  Bus Speed: 8x
  Core Clock: 166 MHz
  Pixel Pipelines: 4
  Memory Type: DDR
  Memory Width: 64 Bit
  Memory Clock: 200 x 2 MHz
  Onboard Memory: 32 MB
  Shared Memory: 96 MB
  Total Memory: 128 MB
  Max Resolution: 2048 x 1536 @ 75 Hz
  RAMDAC Clock: 350 MHz
  Outputs: VGA
  SLI: No
  VIVO: No
  Overclocked: No
Sound Card:
  Brand: Realtek AC'97
  Interface: PCI (Onboard)
  Supported Channels: 6
  Outputs: Line-out (Front, Rear, Center/Sub)
  Inputs: Mic, Line-in
Ethernet Adapter:
  Brand: SiS 900-Based
  Interface: PCI (Onboard)
  Speed: 10/100 MB/s
Wireless Network Adapter:
  Brand: Broadcom BCM4318 AirForce
  Interface: PCI
  Bands: b,g
Modem/Phone Line:
  Brand: Agere Systems AC'97
  Interface: PCI (Onboard)
  Speed: 56 KB/s
Monitor:
  Size: 15.4" Widescreen
  Type: Active Matrix TFT LCD
  Resolution: 1280 x 800 WXGA
  Aspect Ratio: 5:3
  Response Time: 16 ms
  Vertical Refresh Rate: 60 Hz
Keyboard:
  Brand: IBM
  Interface: PS2
  Keys: 102
Touchpad:
  Brand: Synaptics
  Interface: PS2
  Buttons: 2 + 4-way scroller

Programs:

Virus scanner: McAfee VirusScan
Spy/adware scanner: McAfee VirusScan malware remover
Firewall: McAfee PresonalFirewall Plus
Registry cleaner: TweakNow RegCleaner
Internet browser: Mozilla Firefox 1.5
FTP client: FileZilla
HTML editor: Microsoft Word/Publisher 2003
E-mail program: Microsoft Outlook 2003
Word processor: Microsoft Word 2003
Zip utility: WinZip 9.0
CD/DVD burner: NTI CD & DVD-Maker Platinum
Back-up program: Backup Utility
Media player: Windows Media Player 10.0
Sound recorder/editor: WavePad
Photo Editor: Microsoft PictureManager
Instant messenger: Trillian

Drives:

3½ Floppy (A:)- External Flash Memory Device formated hold 1.4 MB (FAT)
Local Disk (C:)- Local Hard Disk Partition (NTFS)
Back-up (D:)- Local Hard Disk Partition (NTFS)
DVD-RW Drive (E:)- Internal Double Layer CD/DVD±RW Drive
Matt Stuff (F:)- External Flash Memory Device Partition (FAT)
MP3 Player (G:)- External Flash Memory Device (FAT)
Removable Disk (H:)- External SD Memory Card Slot
Remote Disk (I:)- Remote Hard Disk (NTFS)
DVD-RW Drive (K:)- Remote Double Layer CD/DVD±RW Drive

Other Devices & Info:

ISP: Comcast High Speed Broadband Internet
Motorola SURFboard SB5100 Modem
Linksys BEF11S4 Wireless-B Router 2.4 GHz 11.0 MB/s
4-Port USB 2.0 Hub
External Stereo Speakers (Built into hub, USB powered)
External Microphone
Microsoft  Basic USB Optical Mouse
Sandisk Sansa e130 512 MB MP3/WMA Player
IBM 256 MB Flash drive
Keyspan Digital Media Remote UIA11
Samsung YP-T7J MP3/WMA/JPEG Player/Viewer/Recorder
``` 
Hope this helps.

---

### Post by ltmon on 2006-08-28
Well fixing your resolution problem needs the console, but it shouldn't be much of a problem.  Here's someone with a very similar laptop model describing how to do it: [https://wiki.ubuntu.com/LaptopTestingTeam/AcerAspire3002WLC](https://wiki.ubuntu.com/LaptopTestingTeam/AcerAspire3002WLC).  The instructions are at the bottom of the page.

Again with the wireless card you have managed to pick a complicated one :) It's quite possible to use however by following the documents at: [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Dapper](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Dapper).  I recommend using NetworkManager once you have the drivers and firmware set up: [https://help.ubuntu.com/community/WifiDocs/NetworkManager](https://help.ubuntu.com/community/WifiDocs/NetworkManager).

Good luck!

L.

---

### Post by TheMatt on 2006-08-29
Thanks for the links. I haven't tried the console method of adjusting the screen resolution, but it looks like it is fairly simple.
 
When I tried to install the network manager, i got the following message:
 
'network-manager-gnome' is not available in any software channel
The application might not support your system architecture.
 
There was also a wireless LAN manager, but when I tried to install that, I got the same message.
 
EDIT: I just tried to change the screen resolution. The instructions say to log in as root, but what is the password? Sorry, I'm a Linux Noob.
 
EDIT2: I got in, but how do I 'select' (put an asterisk next to) 1280 x 800 as a resolution for the xserver to use??? I tried pushing enter, but that just brought me to the next screen. Help! ](*,)

---

### Post by ltmon on 2006-08-29
> **TheMatt said:**
> Thanks for the links. I haven't tried the console method of adjusting the screen resolution, but it looks like it is fairly simple.
 
When I tried to install the network manager, i got the following message:
 
'network-manager-gnome' is not available in any software channel
The application might not support your system architecture.

Because NetworkManager is non-standard software (i.e. the Ubuntu team won't support it at this stage) it exists in a different repository to a lot of the other software.  I think it's in the "universe" repository (?).  See: [https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu) for how to enable the different repositories.

>  
EDIT: I just tried to change the screen resolution. The instructions say to log in as root, but what is the password? Sorry, I'm a Linux Noob.

It's bad instructions.  In Ubuntu you rarely (if ever) log in as root, rather it's set up so that you "sudo" everything.  This means run a given program as if you had root (administrator) privileges.  You seem to have worked it out in any case.

>  
EDIT2: I got in, but how do I 'select' (put an asterisk next to) 1280 x 800 as a resolution for the xserver to use??? I tried pushing enter, but that just brought me to the next screen. Help! ](*,)

I just checked, and you use space to select different items.

L.

---

### Post by TheMatt on 2006-08-29
Thanks fr the help. I got the resolution issue fixed (it was space), so now we can focus on the wireless card problem.
 
My wireless card now shows in the network adapters window, but when I enable it I still can't connect. I'm not sure what is wrong, but the orange light on my laptop that lights up when my wireless card is enabled does not light up and I still cannot connect to the internet, so it is still disabled.

---

### Post by ltmon on 2006-08-29
Well it seems we have the drivers loaded at least.

First thing to do is turn off all encryption on your access point and make sure it is broadcasting it's ESSID.  If that works or not we can start narrowing down the problem.

Secondly the LEDs on laptops are often software controlled, and so don't really reflect what your hardware is doing.  Basically if your laptop manufacturer doesn't provide specific linux drivers for your laptop then that light will not do anything.

L.

---

### Post by TheMatt on 2006-08-29
> Secondly the LEDs on laptops are often software controlled, and so don't really reflect what your hardware is doing. Basically if your laptop manufacturer doesn't provide specific linux drivers for your laptop then that light will not do anything.
Thats good to know. The router is broadcasting the ESSID. The network name is linksys_jupiter. How do I view the wireless networks?

---

### Post by ltmon on 2006-08-29
Ok here is where i'm getting a little hazy.  I've been using NetworkManager since just after I first installed Ubuntu... so I can't really remember the official way of doing things.

A quick command line trick to get a list of all devices in range is:
```

sudo iwlist scan

```

This for me returns my neighbour's completely unprotected and default setup access point:
```

eth1      Scan completed :
          Cell 01 - Address: 00:09:5B:FE:97:7C
                    ESSID:"NETGEAR"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:11
                    Encryption key:off
                    Bit Rates:54 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 6 9 11 12 18 24 36 48 54
                    Quality=79/100  Signal level=-55 dBm  Noise level=-55 dBm
                    Extra: Last beacon: 168ms ago

```

At the moment I'm just following the advice in the documents: [https://help.ubuntu.com/community/WifiDocs/WirelessNetworking](https://help.ubuntu.com/community/WifiDocs/WirelessNetworking) and [https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide)

L.

---

### Post by TheMatt on 2006-08-29
UnfortunatleyI can't use the network manager because I need an internet connection to get it!
 
Once I have the network, how do I connect to it?

---

### Post by ltmon on 2006-08-29
Does using the gnome network manager gui not work for you?

It's shown in one of the links from my last post.

If it for some reason doesn't want to play ball I'll show you how to write the configuration file manually, but it shouldn't really come to that :(

L.

---

### Post by TheMatt on 2006-08-29
Whenever I close the networks window, my wireless card gets disabled. I don't know why this. My wireless card does support scanning, but the networks list doesn't appear in the pulldown menu.

---

### Post by ltmon on 2006-08-29
But did the "sudo iwlist scan" command work?  In any case, can you manually just type in your essid as long as you know it anyway?

But here's how to set it up manually without the gui if that fails:

First you need to modify the file /etc/network/interfaces
```

gksu gedit /etc/network/interfaces
[code]

Now delete any references you have to your wireless interface (eth1 probably, but other values are possible - if you don't know show me the output from the command "iwconfig").  Leave everything else in the file alone.

Now add in the following lines:
[code]
auto eth1
iface eth1 inet dhcp
wireless-essid linksys_jupiter

```

Now you should save this, close the text editor and issue the following commands in a terminal:
```

sudo /etc/init.d/networking restart

```
When that finishes you should hopefully have an internet connection!

If it doesn't work that command might print out some useful error message.

L.

---

### Post by Papa-san on 2006-08-30
I have the same wireless card.
When I upgraded to Dapper, it killed my wireless. (Which had been working fine in Breezy)Two days, and a lot more grey hairs later, I realized something:

The developers tried to make this more simple for those of us with this card... They bundled the drivers in the software. I guess it worked for a lot of people, but in my case (and yours) it fell short. 
I wish I would have written all this down, but I didn't. Check my sig line, and follow the links there. We have the card that requires the ndiswrapper option to be used...

---

### Post by ltmon on 2006-08-30
> **Papa-san said:**
> We have the card that requires the ndiswrapper option to be used...

I don't have the Broadcom myself but I thought (based on reading the wiki) that Dapper included the bcm4xxx drivers, and as such didn't require ndiswrapper any more?

L.

---

### Post by Papa-san on 2006-08-30
> **ltmon said:**
> I don't have the Broadcom myself but I thought (based on reading the wiki) that Dapper included the bcm4xxx drivers, and as such didn't require ndiswrapper any more?

L.
LOL... Yes they did... However, though the thought and effort was HUGELY appreciated by most of us, it didn't work as it was supposed to with all of the Bcom cards...

Seriously, though, I think the 'wireless help' link in my signature helped me work through it. Give it a shot!

---

### Post by ltmon on 2006-08-30
> **Papa-san said:**
> LOL... Yes they did... However, though the thought and effort was HUGELY appreciated by most of us, it didn't work as it was supposed to with all of the Bcom cards...

Ahhh... the old half working drivers trick.  Well you should follow what Pap-san says, as he actually has the same card as you.

I'm just glad I got the intel (works out of the box :))

L.

---

### Post by TheMatt on 2006-08-30
I think its with the driver. I read and I think this is the problem:
> Sometimes ndiswrapper is used prematurely. There may be a native driver that comes with Ubuntu which is taking the primary driver position and conflicting with ndiswrapper.
I will try the steps and let you guys know how it goes.

---

### Post by TheMatt on 2006-08-31
I need to create a file in */etc/modprobe.d* but I don't have permission, root is the owner and I can't change the permissions.

---

### Post by ltmon on 2006-08-31
> **TheMatt said:**
> I need to create a file in */etc/modprobe.d* but I don't have permission, root is the owner and I can't change the permissions.

You shouldn't change the permissions, rather do the operation as root.

Can you open a Nautilus (file manager) window as root? (I'm not really sure as I use KDE).

If not do this instead:
```

gksu gedit /etc/modprobe.d/<yourfilename>

```

gksu asks for your password and sets you as the root user for the rest of the command, and "gedit" just opens an editor to the file you give as an argument.

L.

---

### Post by TheMatt on 2006-08-31
Creating the file did not work. I tried the other steps. I ran the lsmod command to check if the kernal was communicating with the device. I got this:
```
mattmodica@Stargate:~$ lsmod | grep bcm
bcm43xx                    124044  0
ieee80211softmac       29696  1 bcm43xx
ieee80211                   37064  2 bcm43xx,ieee80211softmac

```
I'm not sure what it means. I tried the next thing, which was to scan for access points. I got a message saying the device doesn't support scanning, which it does. Could this be because its disabled?

---

### Post by ltmon on 2006-08-31
It's a bit hard to tell myself without access to the device, sorry.

The "lsmod" output shows that the bcm43xx driver is loaded, and the other entries show some other drivers which the bcm driver depends upon.

Going back to the docs for the bcm cards, what is the output of:
```

iwconfig

```
at this stage?

It might help me work out where you are up to and what you have working so far.

L.

---

### Post by TheMatt on 2006-09-01
OK, I got the blacklist file to work, so the wireless card doesn't show up in networks anymore. How do I get ndiswrapper to recognize it? I tried the modprobe command, but that just brought me back to the way it was before.
 
Also, I tried plugging the laptop directly into the router with ethernet, but i couldn't get a connection with that either. :confused:

---

### Post by compwiz18 on 2006-09-01
Howdy

I have the same card as you...

I just use [http://ubuntuforums.org/showthread.php?t=197102](http://ubuntuforums.org/showthread.php?t=197102) to get mine working, but before you do that try

try **sudo rmmod bcm43xx** as papa-san suggested...that kills the infamous half working bcm43xx driver and then run **sudo dhclient** and see if your internet works now.

Anyway, the easiest way to get any connection (be in wired or wireless) is to open a terminal and run **sudo dhclient** this will connect to any wifi network in range and if you are plugged into ethernet it should get a connection for that too.  Note that this only works for wireless if the wireless card is already working.

as other people suggested, try running **sudo iwlist eth1 scan** and see if you can see your network (sorry if you already answered that and I missed it...I tried to read the whole thread, but I may have missed something)

if you haven't tried to many other methods, it should work for you.  if not, try reinstalling Ubuntu, that's when it works best.

If you have any more questions I'm subscribed to this thread with instant updates so just post away.

EDIT: What graphics card do you have?  If you've got a ATI 200M I can point you in the right direction with that too...
EDIT 2: Just reread, you don't have a 200M so ignore that.

---

### Post by TheMatt on 2006-09-02
When I put *sudo ./ndiswrapper_setup *into the terminal, I get command not found. ???

---

### Post by ltmon on 2006-09-02
That command is trying to run the program "ndiswrapper_setup" inside whatever directory you are now with ("./").  You much go to the directory where that program exists ("cd <directory>") then run the command again.

L.

---

### Post by TheMatt on 2006-09-02
Got it. Before running the setup command, I had to run *cd ~/Desktop/BCM4318* Then I ran the setup command, which installed ndiswrapper and everything worked after that. Thanks for all the help guys, I really appreciate it. Cheers!

---

### Post by Seany1986 on 2006-09-03
I seem to be having the same problem with my widescreen display and wireless card.  I'm not sure what type they are but the laptop is a Dell Latitude 120L.  HELP ME.lol

---

### Post by compwiz18 on 2006-09-03
After a search I found: [http://support.intel.com/support/notebook/sb/cs-006408.htm](http://support.intel.com/support/notebook/sb/cs-006408.htm)

Take a look at that, and see what you can figure out...

As for the display, edit /etc/X11/xorg.conf, find the resolution section, and add the resolution you want (replace the 1024x768 one, or whatever is biggest)...MAKE SURE TO BACK THAT FILE UP BEFORE YOU TOUCH IT.

---

### Post by compwiz18 on 2006-09-03
if you could run lspci and post the output here that would be helpful too.

---

