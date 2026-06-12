---
title: "Desktop Hardware Incompatibility List - Post your hardware which does not work here"
date: 2006-07-02
forum: Hardware &amp; Laptops
---

### Post by frodon on 2006-07-02
[B]Welcome To The Desktop Hardware Incompatibility List.
[/B]
The purpose of this thread is for you, the user, to post what hardware/hardware combination don't work with your desktop Ubuntu install. 

Everyone is welcome to post here, as long as it is hardware related data. For help with hardware problems, please use the standard procedure of searching the forums, and starting your own thread for assistance if no answer is found.

**_Give detailed explanations when reporting incompatible hardware._**

**Also Do not post any lspci outputs in this thread as they will be removed with out question.**

[B]Please Only List
1)Type Of Hardware
2)Hardware Maker
3)Hardware Model
4)Known Issue[/B]

[COLOR="Red"]***NOTE* This thread is exclusively for the listing of incompatible hardware. Any idle chatter or unrelated posts will be moved/removed accordingly. *NOTE***[/COLOR]

[COLOR="navy"]**The UDSF documentation team will catalog information posted here:**[/COLOR]

Thank you.

PS: thanks to Bartender for the idea of this thread.

---

### Post by ubuntu_demon on 2006-07-02
scanner :
canon canoscan D646U
[http://www.ubuntuforums.org/showthread.php?t=19681](http://www.ubuntuforums.org/showthread.php?t=19681)
[http://www.sane-project.org/unsupported/canon-d646u.html](http://www.sane-project.org/unsupported/canon-d646u.html)

---

### Post by bluie on 2006-07-03
Sony Walkman mp3 player NW-xxx does not work with ubuntu yet.

Reason is a proprietary format for mp3-data storage on the player.

---

### Post by yota on 2006-07-03
The Via 880Pro and Via 880Ultra chipset is supported only from kernel version 2.6.17, not included in Dapper.

See:

[http://ubuntuforums.org/showthread.php?t=190341](http://ubuntuforums.org/showthread.php?t=190341)

for a patch.

---

### Post by jsimmons on 2006-07-04
ASROCK 939 Dual SATA2 motherboard - this board's SATA (and SATA2) controllers are incompatible with kernel 2.6.15 and earlier, and will prevent Drake from installing if ANY SATA drives are connected.  You have to physically disconnect your SATA drives in order to install or boot.

This affects all bios versions up to and including 2.20 (dated 06/27/2006).

A couple of possible workarounds (if you're installing to an IDE drive like me):

1) Go ahead and disconnect your SATA drives, install Ubuntu, patch/replace kernel (2.6.16 or later), reconnect SATA drives.

2) Install an add-on PCI card already supported by kernel v2.6.15, connect your SATA drive(s) to that card, and install 6.06

---

### Post by rama on 2006-07-04
D-Link DWL G122 **Rev C** 
Device is not recognized as a wifi-interface. 
Trying to figure out if [this]("http://rt2x00.serialmonkey.com/wiki/index.php/Main_Page#Latest%20News") is the right place to look for drivers although Dapper has some of them in the box.

---

### Post by hugo70 on 2006-07-05
incompatibility with ubuntu 6.06 dapper drake and "mothercard" Gigabyte GA-8VM800M-775 et proces Intel P4 631

---

### Post by frodon on 2006-07-05
could you explain a little bit more what didn't work for you hugo70 ?
networking, graphics, SATA, install, ... ?

---

### Post by ggravier on 2006-07-05
Seems that most SATA controlers I've tried (nVIDIA nForce 4) are seen on cold boot (power off then power on) but aren't seen after a warm reboot (without power off sequence).

---

### Post by Culito on 2006-07-05
Both wireless adaptors I happened to own when I switched to Linux:

D-Link DWL-120 Rev. F - USB
SMC 2602W - PCI w/AMD chipset

---

### Post by spaceman_spiff on 2006-07-06
My Mousetrapper stopped working when upgrading from Breezy to Dapper. In Breezy I had both this and an ordinary USB mouse working side-by-side.

Mousetrapper Office (USB).
[www.mousetrapper.se](www.mousetrapper.se)

---

### Post by rbmorse on 2006-07-06
HP Scanjet 4570c color scanner

This unit is a "winscanner" in the sense of "winmodem" in which some of the processing is offloaded onto the system via the device driver. No Linux driver or SANE support.

---

### Post by rocarm on 2006-07-07
My network card...
Strange one this one, it won't work with a fresh install of dapper, but an upgrade from 5.10  to 6.06 lets it work fine.

Vendor: Davicom Semiconductor Inc
Device: 21x4x DEC-Tulip compatible 10/100
Bus Type: PCI

---

### Post by christian.convey on 2006-07-07
HP dv4150 laptop.  In general it works great, except for power saving modes.  I can activate them manually using the Gnome shutdown interface.  But I can't suspend / hibernate to occur when I close the lid.  Problem is documented here:
[https://launchpad.net/distros/ubuntu/+bug/48471/+index](https://launchpad.net/distros/ubuntu/+bug/48471/+index)

---

### Post by LPent on 2006-07-07
My USB2.0 built-in WebCam.
It's a Syntec DC-1125. There is driver for linux here: [http://www.linux-projects.org/modules/mydownloads/viewcat.php?cid=6](http://www.linux-projects.org/modules/mydownloads/viewcat.php?cid=6)
but for some reason it's only available commercially.

---

### Post by DigitalXpert on 2006-07-09
D-link DGE-530T Gigabit Network Card

No longer works due to kernel module problems... reference [http://www.ubuntuforums.org/showthread.php?t=187770](http://www.ubuntuforums.org/showthread.php?t=187770)

---

### Post by mholmes on 2006-07-11
> **DigitalXpert said:**
> D-link DGE-530T Gigabit Network Card

No longer works due to kernel module problems... reference [http://www.ubuntuforums.org/showthread.php?t=187770](http://www.ubuntuforums.org/showthread.php?t=187770)

I got this card working on Dapper -- see my post here for what I did:

[http://www.ubuntuforums.org/showthread.php?t=200387]("http://www.ubuntuforums.org/showthread.php?t=200387")

---

### Post by Titus A Duxass on 2006-07-11
D-Link DWL120G WLAN Card
Edimax 7128 WLAN Card
Logictech Easy Webcam

---

### Post by frodon on 2006-07-11
Please don't forget do give some explainations of what doesn't work with your hardware.

---

### Post by ghee22 on 2006-07-14
3ware 9500 PCI card for SATA Hardware RAID 5.  The correct module is loaded, but it can't be mounted or even enabled from System, Administration, Disks.

---

### Post by Helix. on 2006-07-15
Lexmark P6250 all-in-one doesnt work, Ubuntu tells me it's a 6200 series printer, but it doenst have that type on the list.

---

### Post by sooqing on 2006-07-17
Epson EPL-6100L

I have been trying to get this to work since 5.04 to 6.06 but failed, despite 5.04 to 6.06 claiming to support it when the printer was detected. If anyone has this printer and managed to get it to work in Ubuntu, please send me the solution! I will be happy to reward you!

sooqing [at] yahoo.com.sg

---

### Post by facefur on 2006-07-19
Canon CanoScan FB620. parallel port version.  System does not recognize its existence, i.e. xsane can't see it.

---

### Post by autocrosser on 2006-07-21
> **rbmorse said:**
> HP Scanjet 4570c color scanner
 
This unit is a "winscanner" in the sense of "winmodem" in which some of the processing is offloaded onto the system via the device driver. No Linux driver or SANE support.
There is someone on the sane list that is asking for logs for the newer HP scanners--I have a Scanjet 4370 that I'm sending SnoopyPro logs. Look in SourceForge for the HP 3900 driver project for more info--I'm at work, so I can't get to it right now..

---

### Post by eXecu7or on 2006-07-21
-deleted-

---

### Post by eXecu7or on 2006-07-21
ITE8211 controller. Doesn't see hdds during or after installations of 6.06. There appears to be a linux driver available [here]("http://www.ite.com.tw/software_download/software_download2.asp#IT8211F%20IDE%20Controller").

LATER EDIT. It seems the IDE controller works after all. Just that it is not deteced correctly during setup. I had to manually set mount points & mount the partitions. So this might be mount, detection related.

---

### Post by redicqlus on 2006-07-24
Ummm... I'm not 100% because I'm new on ubuntu, but it looks like my Microtek ScanMaker 5950 isn't working and can't be seen by the OS.   Any tips?
-red-

---

### Post by cracker on 2006-07-24
A-bit NF7-S2 onboard LAN:
0000:02:0b.0 Ethernet controller: Sundance Technology Inc: Unknown device 0200 (rev 31)

Refuses to show up in ifconfig. Tried several drivers, including forcedeth, sundance, and nvidia's compiled drivers.

---

### Post by ladoga on 2006-07-25
CH Combatstick 568 USB
CH Pro Pedals USB
and probably every other CH USB device.

Details here:
[http://www.ubuntuforums.org/showthread.php?t=222584](http://www.ubuntuforums.org/showthread.php?t=222584)

---

### Post by maddog39 on 2006-07-26
Most generic USB 2.0 Keyboards, I have tried several and none worked nor were recognized, didnt even power up. Not sure about USB 1.1 keyboards yet.

---

### Post by Himmagery on 2006-07-27
Various bits on the Asus M2V motherboard.  The SATA controller is now part of the vt8237a SouthBridge chip, which doesn't seem to be supported in the kernel yet, plus lspci lists a whole pile of unknown devices:

0000:00:00.0 Host bridge: VIA Technologies, Inc.: Unknown device 0351
0000:00:00.1 Host bridge: VIA Technologies, Inc.: Unknown device 1351
0000:00:00.2 Host bridge: VIA Technologies, Inc.: Unknown device 2351
0000:00:00.3 Host bridge: VIA Technologies, Inc.: Unknown device 3351
0000:00:00.4 Host bridge: VIA Technologies, Inc.: Unknown device 4351
0000:00:00.5 PIC: VIA Technologies, Inc.: Unknown device 5351
0000:00:00.6 Host bridge: VIA Technologies, Inc.: Unknown device 6238
0000:00:00.7 Host bridge: VIA Technologies, Inc.: Unknown device 7351
0000:00:01.0 PCI bridge: VIA Technologies, Inc.: Unknown device b999

Normal PATA drives work okay, except DMA is disabled:

[17179577.728000] VP_IDE: Unknown VIA SouthBridge, disabling DMA.

The onboard gigabit LAN also doesn't appear to work (disabled in the BIOS now, so I can't find the chipset used.)

Not one of my best purchasing decisions!

---

### Post by Enverex on 2006-07-27
> **ggravier said:**
> Seems that most SATA controlers I've tried (nVIDIA nForce 4) are seen on cold boot (power off then power on) but aren't seen after a warm reboot (without power off sequence).

Works fine for me here (plain SATA on it anyway, Asus A8N-E with nForce 4 SATA controler).

nForce 4 SATA RAID doesn't work. It doesn't show up in /dev/mapper but it does still show up as two drives (say you have them in RAID0 or something ergo it should be one drive) which is bad. I had to go through hell to get it to work on Gentoo.

Saitek X52 Flight Control system doesn't work properly. It works as a basic device but it's missing 90% of its functionality. The screen doesn't work, most the lights don't even turn on and obviously none of the special controls work either.

---

### Post by Donk^^ on 2006-07-28
> **eXecu7or said:**
> ITE8211 controller. Doesn't see hdds during or after installations of 6.06. There appears to be a linux driver available [here]("http://www.ite.com.tw/software_download/software_download2.asp#IT8211F%20IDE%20Controller").

LATER EDIT. It seems the IDE controller works after all. Just that it is not deteced correctly during setup. I had to manually set mount points & mount the partitions. So this might be mount, detection related.

Subscribes to this bug:
[https://launchpad.net/distros/ubuntu/+source/initramfs-tools/+bug/47197](https://launchpad.net/distros/ubuntu/+source/initramfs-tools/+bug/47197)

---

### Post by BobSongs on 2006-07-30
Logitech's ClickSmart 820 Webcam is a hybrid digital camera/webcam. However it does **not** work as a webcam in Ubuntu. Any attempt to connect to the camera using webcam software and your system will lock up like the county jail.

You can transfer photos you've taken to your hard drive: that's possible. However look for another brand. Logitech doesn't support Linux.

---

### Post by drn8 on 2006-08-01
ASUS K8N4-E DELUXE, nforce4 sata is not recognised on booting the live cd, my root partition is on a sata drive.

>Realtek AC'97 8-channel audio is not properly configured, no audio when booting live. This is properly configured when booting on an ASUS A8N5X.

 NVIDIA (Gigabite) Geforce 6600, HP D5063 15-inch LCD.
 this is a perpetual problem, I need to start in safe graphics mode, starting in regular mode results in garbled output, on suse 10.1 even with nvidia drivers installed I can't go 1024x768, but suse decided 10.1 should be a buggy dung heap compared to 10.0, I digress. There seem to be issues with the dummy nv drivers, this card, and this monitor, every single distro I need to manualy set the timings, even those that include it in the hardware list.

AMD Athlon 64 2800+ socket 754
my cpu is not recognised by the live cd.

I have not installed dapper due to the sata issues, until default nforce sata support becomes standard I foresee issues for ubuntu 64 as sata is onbord for most 64 motherboards. Suse recognises and installes to my sata drives, mandriva also. Etch however does not, but that is to be expected >.< .

---

### Post by hinlader on 2006-08-01
My Logitech "Elite Keyboard LE" does not seem to be fully supported.
These Keys don't work:
Shift+` just creates another `, not a tilde character (very annoying...)
The = ( ) keys above the numpad don't work (Backspace does, though)
Keys with functions do not respond with F-Lock turned off (New, Reply, etc.)

---

### Post by Matchless on 2006-08-05
Lexmark multifunction 4 in 1 printer X6150 no drivers, does not work on any linux.

---

### Post by justinflavin on 2006-08-08
Epson Stylus Photo R240, via USB

its recognised as an R240, but it doesnt appear in the printer driver list.

an R2400 is in the printer list, but that isnt it.

tried using the R210 driver, but this wouldnt rescale photos down to a 10x15cm or 13x18cm size.

---

### Post by drn8 on 2006-08-08
Also my logitech g5 usb laser gaming mouse goes crazy and atarts auto clicking and moving all over the screen on it's own.

---

### Post by jzimmerman on 2006-08-10
Promise tx2300 SATA RAID Card

lspci gives....

0000:02:08.0 RAID bus controller: Promise Technology, Inc. PDC40779 (SATA 300 779) (rev 02)


Promises website only posted drivers/modules for 2.4 kernels  no 2.6 update.  The card is reported to work with 2.6.14 kernels and above under Gentoo, but no go under Ubuntu 6.06.1 or SuSE 10.1.  No response from Promise support.

---

### Post by QuadraQ on 2006-08-11
The Promise PDC20276 IDE RAID array controller on my Asus A7V333 motherboard is not working. Instead of seeing one volume, the Gnome Partition Manager sees the two hard drives seperately as unformatted volumes instead of as one NTFS volume.

---

### Post by autocrosser on 2006-08-11
To everyone with HP probucts--I had wrote a very polite letter to the Head of HP (if you look thru their site there is a way to do it) & have received a flurry of Emails & today a call from a senior member of Tech Support--looks like I hit a nerve at HP:D --I'll keep everyone informed, but I was told that they are going to increase support for LINUX!!!!!!!!
 
He is sending me a email as to what my unit is & then "will see if I can be supported with drivers for Debian"!!!!!!!!!!!!!!!!!!!!!!!!
 
If you go the same route, just make sure that you don't thrash the company--I told the Head of HP that I had bought HP products in the past & was disappointed that they are not supporting a growing group of users--If we all band together & politely ask enought times, we might really get the support we want.

---

### Post by Krislarsen on 2006-08-12
Microsoft LifeCam VX-6000 webcamera doesn't work yet.. This is a relatively new webcam with megapixel resolution on video :D

dmesg printout:

[17179842.684000] usb 5-5: new high speed USB device using ehci_hcd and address 6
[17179843.236000] 6:2:1: cannot get freq at ep 0x84
[17179843.244000] usbcore: registered new driver snd-usb-audio

The built-in mic seems to be recognized, but not the camera/video device itself.

---

### Post by djfreekshow on 2006-08-13
Atech Pro9 8-in-1 Media Card Reader with onboard iEEE1394

It is able to be edited in the BIOS, with emulation as either a floppy drive, auto, HDD, CDROM, or force FDD.  None of these emulations work with Ubuntu Dapper, and so when it is plugged in, even the LiveCD won't boot.

---

### Post by Scrappy_D on 2006-08-13
Linksys 2-Port KVM switch. With this plugged in Ubuntu does some strange things, especaily with text ... trying to login was a laugh as ubuntu kept putting in upto 20 characters each time I hit one key!

Also the Server and Desktop editions do not seem to work on old compaq pressario 5410's ... took me 3 days to eventually get it to boot (had to use the OEM install on the Alternate CD ... which by the way took over 6 hours to install!)

---

### Post by Scrappy_D on 2006-08-13
> **Scrappy_D said:**
> Linksys 2-Port KVM switch. With this plugged in Ubuntu does some strange things, especaily with text ... trying to login was a laugh as ubuntu kept putting in upto 20 characters each time I hit one key!

Also the Server and Desktop editions do not seem to work on old compaq pressario 5410's ... took me 3 days to eventually get it to boot (had to use the OEM install on the Alternate CD ... which by the way took over 6 hours to install!)


Ok looks like it wasnt the KVM switch as ubuntu is still doing it with the monitor/mouse/keyboard plugged into the PC :( 
Mouse seems fine but the keyboard is going nuts ?????

---

### Post by Aggienator on 2006-08-14
Scanner CanoScan 3200F. I did look at the unsupported bit od SANE and found an unsupported backed, but was rather frightened off by the Documentation: "IF YOU DO NOT KNOW WHAT
YOU ARE DOING, DON'T USE IT. At best it may give
some hint of where the development is going, at
worst IT MAY BURN YOUR SCANNER. So, you were warned!"

I'm still "recipe book Ubuntu" - if someone has posted clear instructions I can follow them, but the dawn of understanding is slow:confused:

---

### Post by Cephus on 2006-08-14
[COLOR="Red"]**Scanner:**[/COLOR] Canon FB620U.  This isn't a major upset - this scanner was purchased at a Savers Thrift Shop for only $3.00.  Under Windows, it works beautifully.  I bought it because it was cheap, so there is no loss related to cost, and its very small footprint, which goes nicely with my laptop.

I'll continue doing dual-boot with my laptop, though I'm really ready to eliminate Windows all together if it weren't for just a few functions.

---

### Post by Emerzen on 2006-08-14
Printer's seem to be common:

Dell AIO 942 (rebranded Lexmark but not sure which)
Lexmark Z730
(both lack drivers)

ATI TV Wonder (USB version)
(no driver)

Palm Tungsten T5 (was working w/ Hoary/Breezy), much review of the boards and google and cannot find a workaround.

---

### Post by daou on 2006-08-14
There were some comments referring to nForce4 SATA RAID not working. My NF4 SATA RAID-0 array works on Ubuntu just fine with dmraid, however I was not able to install Ubuntu on it even after a couple of tries with the RAID Howto in hand.

---

### Post by freecat on 2006-08-15
Lexmark x 1185 all-in-one also HP 3520 Printer.

---

### Post by bensexson on 2006-08-15
Texas Instruments PCI-1620 UltraMedia flash controller on my Compaq Presario r3000z.  TI has a linux driver but will not release the firmware for it.

---

### Post by heffo_j on 2006-08-19
> **freecat said:**
> Lexmark x 1185 all-in-one also HP 3520 Printer.

The printing function only (not scanning and fax) definitely works with the Z600 drivers. I use it all the time. The problem is not with Linux but with the manufacturers who don't disclose their code nor produce Linux drivers.

Regards
John

---

### Post by heffo_j on 2006-08-19
> **heffo_j said:**
> The printing function only (not scanning and fax) definitely works with the Z600 drivers. I use it all the time. The problem is not with Linux but with the manufacturers who don't disclose their code nor produce Linux drivers.

Regards
John

Sorry, point of clarification: This refers to the Lexmark printer. Use the Lexmark Z600 driver to get the printing function working.

Regards
John

---

### Post by NightwishFreak on 2006-08-21
nForce 4 SATA RAID. I understand that there is a way to get it to work with dmraid, but I wish that it would just auto-detect, and let me install Ubuntu directly on to the array.

---

### Post by Dale61 on 2006-08-22
Could be just due to my newby status, but I couldn't get my Canon MPC190 MFC to work.

No biggie, it's due for replacement anyway.

---

### Post by GeordieDS on 2006-08-22
I've got a c-media usb attached multi-card reader which after hours of fruitless googling looks like it will never work with ubuntu :-( 

Can anyone recommend a usb attached card reader that does work?

Also struggling with DSS-20 sony ericsson mobile phone cradle.

---

### Post by Bavarian29 on 2006-08-22
5-1/1 inch floppy drive not installed. Does Kubuntu include these drives during installation hardware review. I could not sofar mount (or find) this drive. Need it badly to install a DOS-based database I have to have!

---

### Post by mcewanbr on 2006-08-24
Dell Advance Port Replicator - cannot get Dual video and sound/mic to work

---

### Post by TFrog on 2006-08-24
Only hardware I have yet to get working on my desktop (specs in my sig) is my webcam (DLink DSC310).  On my laptop I've yet to get the volume buttons, the memory card reader, and ATI propriotary drivers to work.  The ATI drivers refuse to work with SidePort only on my Compaq Presario R4125US.  The only way I can use them is with UMA only.  I don't see the need to waste valuable system memory when the card has built in 128meg of ram.  Whether ATI will fix this or not is unknown.  Other than that, I look forward to when they get WPA working with the new Broadcom native linux drivers.  Till then I'm on ndiswrapper with my Broadcom 4318 chipset.  I'm typing this now with the laptop previously mentioned.

---

### Post by Toehead on 2006-08-25
the fan control on my compaq armada 6500 doesnt work.

---

### Post by Guy2 on 2006-08-26
> **drn8 said:**
> Also my logitech g5 usb laser gaming mouse goes crazy and atarts auto clicking and moving all over the screen on it's own.

Similar problems with my SITECOM KV-005 2-port KVM switch, using bog-standard Genius wheel mouse.
Works fine when I boot Ubuntu with it selected on the KVM. But if I switch to another PC and then back, the problem as above then occurs. My install is dual-boot with Windows 98SE; the latter happily swithes to and fro - so it's definitely something that Ubuntu is doing different.

---

### Post by smonteiro on 2006-08-27
Canon Powershot S3 IS is not recognised.
I think it's due to old gphoto2 drivers though

---

### Post by el3ktro on 2006-08-27
The Averatec 2460 is not working with Dapper at all, you can't install it. It hangs when detecting the hardware. SuSE, Knoppix & Gentoo also don't work. Gentoo works when I disable automatic hardware detection. The "8139too" module needed for the onboard NIC hangs the system - probably some other modules also hang the system, because if I boot the Ubuntu CD in "expert mode" and skip network detection the install hangs when it is trying to detect the harddisks.

The laptop has an Intel 945GM chipset, Intel 3945ABG Wireless, RealTek 8139C+ NIC, Intel GMA 950 graphics & Intel Centrino Core Duo CPU.

Tom

---

### Post by Guy2 on 2006-08-28
> **Guy2 said:**
> Similar problems with my SITECOM KV-005 2-port KVM switch, using bog-standard Genius wheel mouse.
Works fine when I boot Ubuntu with it selected on the KVM. But if I switch to another PC and then back, the problem as above then occurs. My install is dual-boot with Windows 98SE; the latter happily swithes to and fro - so it's definitely something that Ubuntu is doing different.
Just to add that there is a thread here:
[http://www.ubuntuforums.org/showthread.php?t=240202](http://www.ubuntuforums.org/showthread.php?t=240202)
which discusses various jumping mouse problems.

---

### Post by Belyel on 2006-08-28
Built-in webcam for Acer Travelmate 8200.  Webcam is a Logitech Quickcam 1.3MP.  VendorID: 0x46d ProductID: 0x892.  Will be supported in the future release of spca5xx v4l2.

---

### Post by ajaym on 2006-08-30
Asus M2V (Via K8T890/Socket AM2)
AMD 3800 X2
1G DDR2-533 RAM
Samsung SP2504 250G SATA drive formatted as NTFS in one partition,
Windows 2000 already installed and operating perfectly.
Liteon PATA DVD burner
Geforce 6200 256M PCI Express

Dapper 6.06 desktop

Boot from Dapper CD - will boot fine to desktop, but then selecting install from desktop, will fail to find the SATA drive and hangs while scanning for installable partition.

Attempting to administer disk from desktop shows two hard drives, one reported as tmpfs, the second as unionfs. Neither of these 'ghost drives' show any partitions. Gpart also fails to find any valid partitions.

Device manager does not appear to show the hard drive at all.

Also failed to identify and configure the Attansic gigabyte NIC integrated into motherboard.

Moved drive from SATA-1 to SATA-2 without any change in behaviour.

Understand this may be a known problem with Ubuntu. Is there any workaround. Will try booting Knoppix and will report back on whether it could find the hardware or not. Previously used the same 6.06 desktop CD successfully on an ASUS Nforce3 motherboard without these issues.

---

### Post by ajaym on 2006-08-30
Further to previous post. SATA RAID is automatically enabled on the motherboard only when multiple drives are connected. Otherwise it cannot be enabled. Therefore do not have the option to change that setting, since only one drive installed, and there are no BIOS settings that are tweakable which appear relevant in any way; BIOS is configured with standard defaults.

---

### Post by Belyel on 2006-08-30
> **ajaym said:**
> Further to previous post. SATA RAID is automatically enabled on the motherboard only when multiple drives are connected. Otherwise it cannot be enabled. Therefore do not have the option to change that setting, since only one drive installed, and there are no BIOS settings that are tweakable which appear relevant in any way; BIOS is configured with standard defaults.

I don't know how the cutting-edge ASUS boards are, but my socket 939 board has a similar SATA/RAID config as yours does.  While the RAID may auto-engage when you have two drives, there should be a jumper setting on the board that will enable the JBOD (just a bunch of disks) configuration for RAID, allowing you to use the single drive.  Look in the manual that came with the mobo or look on asus' website for the location and setting of the jumper.  I won't say I know there is such a jumper, but I'm almost positive that there will be one.

---

### Post by Cojawfee on 2006-08-31
ASUS M2N-SLI Deluxe (socket AM2, chipset nForce 570)
AMD Athlon 64 X2 4200+
Two GeForce 7600s
Two SATA Hard drives (Western Digital for what it is worth)

It boots up until the cursor and then hangs. I'll ask what to do about it in another thread.

---

### Post by ajaym on 2006-08-31
Thanks very much for the suggestion. However, I've double checked and there's definitely no jumper on the M2V for SATA RAID, unfortunately. In fact there are only 3 jumpers on the whole board, clear RTC, keyboard power and wake USB device. That's it. And definitely nothing in the BIOS to configure it at all.

I can't understand how come both Win98 and Win2K work fine with this setup - with no special drivers loaded at all. No problems there and both OS's pre-date SATA by a long way. There's something badly wrong with how Ubuntu is looking for hardware, surely.

---

### Post by ironstorm on 2006-09-03
> **Himmagery said:**
> Various bits on the Asus M2V motherboard.  The SATA controller is now part of the vt8237a SouthBridge chip

There is a kernel patch for this I just found here:

[http://lkml.org/lkml/2006/8/11/196](http://lkml.org/lkml/2006/8/11/196)

I'm rebuilding my kernel now to see if it will work...

Thought the devs would have applied it to knot 2, but maybe its still in progress.

---

### Post by butlershouse on 2006-09-04
Fujitsu Siemens Amilo L7310GW

Out of the box ( Ubuntu Lts 6.06 ) install kernel worked well for everything except external USB devices. 

title           Ubuntu, kernel 2.6.15-23-386
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.15-23-386 root=/dev/hda2 ro quiet splash
initrd          /boot/initrd.img-2.6.15-23-386
savedefault
boot


Plug in a USB device to get ->

==> /var/log/messages <==
Sep  4 21:45:46 localhost kernel: [4294839.000000] usb 4-2: new high speed USB d evice using ehci_hcd and address 8

==> /var/log/syslog <==
Sep  4 21:45:56 localhost kernel: [4294849.422000] usb 4-2: device not accepting  address 8, error -110
Sep  4 21:45:56 localhost kernel: [4294849.524000] usb 4-2: new high speed USB d evice using ehci_hcd and address 9

Kernel Updgraded to ( as per Synaptic reccomendation ) 


title           Ubuntu, kernel 2.6.15-26-686
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.15-26-686 root=/dev/hda2 ro quiet splash
initrd          /boot/initrd.img-2.6.15-26-686
savedefault
boot


And the onboard Wireless Card stopped working and the USB is still not working.

Onboard Wireless details courtesy of DMESG under working Kernel

[4294692.945000] ath_hal: module license 'Proprietary' taints kernel.
[4294692.946000] ath_hal: 0.9.14.9 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2413)
[4294693.113000] wlan: 0.8.6.0 (EXPERIMENTAL)
[4294693.114000] ath_rate_sample: 1.2
[4294693.153000] ath_pci: 0.9.6.0 (EXPERIMENTAL)
[4294693.153000] PCI: Enabling device 0000:00:06.0 (0000 -> 0002)
[4294693.153000] ACPI: PCI Interrupt 0000:00:06.0[A] -> GSI 19 (level, low) -> IRQ 185
[4294693.574000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[4294693.788000] Build date: May 29 2006
[4294693.788000] Debugging version (IEEE80211)
[4294693.788000] ath0: 11b rates: 1Mbps 2Mbps 5.5Mbps 11Mbps
[4294693.788000] ath0: 11g rates: 1Mbps 2Mbps 5.5Mbps 11Mbps 6Mbps 9Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps
[4294693.788000] ath0: H/W encryption support: WEP AES AES_CCM TKIP
[4294693.788000] ath0: mac 7.8 phy 4.5 radio 5.6
[4294693.788000] ath0: Use hw queue 1 for WME_AC_BE traffic
[4294693.788000] ath0: Use hw queue 0 for WME_AC_BK traffic
[4294693.788000] ath0: Use hw queue 2 for WME_AC_VI traffic
[4294693.788000] ath0: Use hw queue 3 for WME_AC_VO traffic
[4294693.788000] ath0: Use hw queue 8 for CAB traffic
[4294693.788000] ath0: Use hw queue 9 for beacons
[4294693.788000] Debugging version (ATH)
[4294693.788000] ath0: Atheros 5212: mem=0x44000000, irq=185


In both kernels the Fan on this is still screaming away , quite unhappy. CPU usage shows nothing important occuring.


Cheers for taking the time to read this .


Nik Butler

---

### Post by jinxed on 2006-09-06
> **Aggienator said:**
> Scanner CanoScan 3200F. I did look at the unsupported bit od SANE and found an unsupported backed, but was rather frightened off by the Documentation: "IF YOU DO NOT KNOW WHAT
YOU ARE DOING, DON'T USE IT. At best it may give
some hint of where the development is going, at
worst IT MAY BURN YOUR SCANNER. So, you were warned!"

I'm still "recipe book Ubuntu" - if someone has posted clear instructions I can follow them, but the dawn of understanding is slow:confused:

I don't think there are any instructions for using the Canoscan series scanners. Canon has been very slow to respond to providing any form of support or help in the development of drivers for their scanners. I have a Canoscan 5000F for a few years now, and have never been able to use it in Linux. In fact, I keep a dusty old installation of WinXP around just for that reason. ](*,)

---

### Post by ajaym on 2006-09-08
I'm delighted to say that my previous problem (Asus M2V/Samsung 250G SATA drive) is resolved by Knot 2 of Edgy, and GPartEd successfully resized the drive without screwing up the existing Win2K installation, which is marvellous.

Still doesn't find the Attansic NIC but realistically this is an unusual chipset. I imagine it might work through NDISWRAPPER but haven't yet explored. Also haven't looked at getting a direct wireless link going - the current connection is proxied through a hardwired cable link to a Windows laptop wirelessly connected to the downstairs router. So, good work, Ubuntu-folks. Looking forward to final release of Edgy!

---

### Post by maniacmusician on 2006-09-09
I have an ATI Radeon Xpress 200 chipset....the integrated video does not work. Well it works enough to give me high resolutions but i can't even enable compositing without it screwing up. and the glxgears numbers are really bad as I understand them (I only get about 350-ish...other people get it in the thousands right?) pretty sure i'm using the newest proprietary drivers.

---

### Post by maniacmusician on 2006-09-09
> **ajaym said:**
> I'm delighted to say that my previous problem (Asus M2V/Samsung 250G SATA drive) is resolved by Knot 2 of Edgy, and GPartEd successfully resized the drive without screwing up the existing Win2K installation, which is marvellous.

Still doesn't find the Attansic NIC but realistically this is an unusual chipset. I imagine it might work through NDISWRAPPER but haven't yet explored. Also haven't looked at getting a direct wireless link going - the current connection is proxied through a hardwired cable link to a Windows laptop wirelessly connected to the downstairs router. So, good work, Ubuntu-folks. Looking forward to final release of Edgy!
I checked the ndiswrapper wiki list, and I didn't see an Attansic card listed on it :( sorry. But maybe its not listed by name, instead, by pci id. Use the instructions on the wiki to get that number and maybe you'll find it...good luck...

---

### Post by Dale61 on 2006-09-10
Toshiba Satellite A30.

Caused me nothing but trouble, and as such, now have a laptop I can no longer use.

1/. Took 14 attempts to load Live CD when running on XP.

This should ahve set the alarm bells ringing, but as I have been trouble free on my desktop install, I decided to take the plunge and perform a clean install on my laptop.

2/. Laptop shuts down during install.  97% complete, and then nothing, nada, zip.  Can't even remove CD from drive.  Reboot, and can't read screen.  Finally regain control, re-do the install, and again, computer shuts down at 97%.  Third attempt, and finally, installation successful.

3/. Advised to remove CD from tray before rebooting.  Follow instructions, then reboot.  Reboot again.... and again.... and again, before getting any semblance of control.

4/. Hmm, no clock!  Hello, what's this, pc locked solid.  Alt-Ctrl-BckSpc to reboot.  4 more attempts to load before successful.  Still locked up and nothing accessible.  This happens 3-4 more times.

5/. Finally get control, so check Ubuntu forums (on desktop pc) for an explanation for installation difficulties.  Laptop still running, then screensaver kicks in.  Move mouse, laptop locked up.  Damn, but this doesn't surprise me.

6/. For the umpteenth time, reboot again and again, reset screensaver for 2 hours.  Attempt to add CD to repositories.  Backflips when laptop locks up AGAIN.  Enough, will sleep on the problem.

DAY TWO.

Fire up laptop, 5 attempts to get Ubuntu to load.  Can't access anything.  Alt-Ctrl-BckSp to reboot.  Gunna be a long day.

This went on for about 3.5 hours.

Finally, something can get done.  Type in:
lsmod | grep atiixp-modem
Hmm, no modem, in fact, no modem can be found anywhere.  So much for easy upgrades!  Whoa, no sound.  Follow instructions on numerous forums / wiki, to no avail.  Too late to go back to Windoze now as all I have in a backup (factory supplied) CD's.  Not looking good.

So, to cut a longish story short, 4 days and still can't get Ubuntu 6.06 to load first time, still no modem, still no sound, and to top it off, the laptop unexpectedly shuts down when I do get a chance to try whatever instructions I do happen to find.

Anyone wanna buy a cheap laptop?  ;)

---

### Post by talrasha on 2006-09-10
I have HP Deskjet 3745 and HP Deskjet 3550 printer.

I already saw the list of supported HP printer but these two printers that I have is not in the list and it only means that these printers are not supported.

Is there a way where I can configure it or I really need to wait for the drivers to be available??? When will it be?? :confused:

---

### Post by jaycee15* on 2006-09-10
I'm a newbie to Linux, recently moved to Ubuntu. I have these problems:
1) Printer HP Laserjet 1000. Not in the list of HP printers.
2) Scanner Visioneer 7300 Not supported in SANE.
3) Printer HP Laserjet 1012 - only basic functions supported.

---

### Post by John.Michael.Kane on 2006-09-12
jaycee15* here's what has been documented on the printers your using.

[http://www.linuxprinting.org/show_printer.cgi?recnum=HP-LaserJet_1000](http://www.linuxprinting.org/show_printer.cgi?recnum=HP-LaserJet_1000)
[http://www.linuxprinting.org/show_printer.cgi?recnum=HP-LaserJet_1012](http://www.linuxprinting.org/show_printer.cgi?recnum=HP-LaserJet_1012)


talrasha here's what is known on your printer models
[http://www.linuxprinting.org/show_printer.cgi?recnum=HP-DeskJet_3745](http://www.linuxprinting.org/show_printer.cgi?recnum=HP-DeskJet_3745)
[http://www.linuxprinting.org/show_printer.cgi?recnum=HP-DeskJet_3550](http://www.linuxprinting.org/show_printer.cgi?recnum=HP-DeskJet_3550)


@Dale61 have you tried installing from the alternate cd?
Dale61 your toshiba satellite A30 uses a desktop p4 cpu which is known to run hot. which could be the cause of the shutting down. also you could try passing the **noapic nolapic** command before booting



@maniacmusician there should be open drivers for that radeon xpress 200 you should be able to get aiglx working. 
[http://www.compiz.net/viewtopic.php?id=389](http://www.compiz.net/viewtopic.php?id=389)
Note: I'm pretty sure you could get composting/aiglx working with edgy.

---

### Post by Dale61 on 2006-09-12
SD-Plissken, what is this alternative CD you mention?  The only one I have is the one that took five weeks to arrive, so are you suggesting I go without my laptop for an extended period of time?

---

### Post by Joedude on 2006-09-12
Lexmark X2350 All In One (Printer/Scanner/Copier) not supported by CUPS or Sane. I would build the driver myself if I had the source info...

---

### Post by John.Michael.Kane on 2006-09-12
Joedude I don't have a lexmark to test this,however. if you want you can. it would seem that from this post [http://www.linuxprinting.org/show_printer.cgi?recnum=Lexmark-x2350](http://www.linuxprinting.org/show_printer.cgi?recnum=Lexmark-x2350) that someone was able to use the standard laserjet drivers to get this printer to work. note: the method seems to have only been tested by the org poster.

---

### Post by billd42 on 2006-09-14
> **Cojawfee said:**
> ASUS M2N-SLI Deluxe (socket AM2, chipset nForce 570)
AMD Athlon 64 X2 4200+
Two GeForce 7600s
Two SATA Hard drives (Western Digital for what it is worth)

It boots up until the cursor and then hangs. I'll ask what to do about it in another thread.

I have one of these motherboards with an A64X2 3800+ and a single GeForce 7600GT, I had to boot it with the "noapic" option to get it to boot.

Hope that's useful.

---

### Post by talrasha on 2006-09-16
Good news! I successfully installed Drapper w/ my windows server 2K3 box in a dual boot mode. Thank God for Drapper's GRUB for not giving me a frustrating dual boot first experience.

My HP Deskjet 3550 and 3745 printer was not automatically detected but is supported in Drapper. I just used the Add Printer function and then puuff!!! I can query the printer in no time! :p 

This was a good experience for me as a new Drapper user!
Thanks for the Ubuntu and its Community! ^^

God bless ya'el!!!

---

### Post by raul_ on 2006-09-18
in the add driver function , the only one that pops up is Hp DeskJet 3740 (mine is 3745) and no drivers appear...nothing at all. What do i have to do?#-o

---

### Post by JeffreyRatcliffe on 2006-09-19
> **GeordieDS said:**
> I've got a c-media usb attached multi-card reader which after hours of fruitless googling looks like it will never work with ubuntu :-( 

Can anyone recommend a usb attached card reader that does work?

Also struggling with DSS-20 sony ericsson mobile phone cradle.

My (otherwise good) Medion PC has an internal card reader which reports as:```
ID 0d8c:5200 C-Media Electronics, Inc.
```

I have also had no joy with it at all with Ubuntu (No person I have talked to has managed to get it work with any flavour of Linux)

However, I have just bought a new card reader from ebay ([http://cgi.ebay.de/ws/eBayISAPI.dll?ViewItem&rd=1&item=280026733138&ssPageName=STRK:MEWN:IT&ih=018](http://cgi.ebay.de/ws/eBayISAPI.dll?ViewItem&rd=1&item=280026733138&ssPageName=STRK:MEWN:IT&ih=018)) for €6 that worked perfectly out of the box and reports as:```
ID 058f:6362 Alcor Micro Corp.
```

---

### Post by joselin on 2006-09-19
Extrememory 4Gb SD Card PC133

---

### Post by maduranga on 2006-09-20
HUAWEI ETS2288 

  it is my cdma phone. i dnt work with ubuntu it is becoz a usbserial problem.

---

### Post by GreenfrogCT on 2006-09-22
Hardware: Microsoft Wireless Keyboard / Mouse Combination
[LIST]
[*]Wireless Optical Desktop Receiver 3.0A
[*]Wireless Optical Mouse 2.0
[*]Wireless Comfort Keyboard 1.0A
[/LIST]
Ubuntu does not seem to recognize this equipment at all.

Receiver is connected directly to USB port on motherboard.
Keyboard works during POST
Keyboard works in GRUB
Keyboard and Mouse both work fine if I boot my XP partition (of course)

Once the Linux kernel boots in Ubuntu the 3 indicator lights on the receiver (Caps Lock, Num Lock, F-Lock) flash dimly, then go out.  No response from either keyboard or mouse.

Have seen this same issue posted elsewhere on various Ubuntu forums but nobody has come up with a resolution.  I know Microsoft is a company everybody loves to hate, but I do like the keyboard and swapping my keyboard and mouse to my old wired ones to use Ubuntu is a royal pain.

Greenfrog. :mrgreen:

---

### Post by halitech on 2006-09-22
Lexmark 1020 - recognized, just doesnt seem to want to print

lexmark x2230 - no joy at all

---

### Post by Old Pink on 2006-09-25
Lexmark 2300 All-in-one printer Series (X2350)

---

### Post by bloodniece on 2006-09-26
**Lenovo 3000 C100**
Everyhting works except eth1 = BCM4319
The Broadcom BCM4319 did not work with any known Windows driver from Lenovo or elsewhere else using ndiswrapper.  It worked partially using [bcm43xx-fwcutter]("http://bcm43xx.berlios.de/?go=home") and network-manager-gnome, but when negotiating with a new ap the driver module would crash.  Restart...try again.

**What did work for wireless was:**
[LIST]
[*][ BELKIN F5D7010 Wireless G Notebook Card]("http://www.newegg.com/Product/Product.asp?Item=N82E16833314306")
[*]Atheros chipset = Ubuntu friendly wireless buddy pal
[/LIST]
Ubuntu set it up seamlessly and network-manager-gnome works quite well with it.

So, stay away from the BCM4319 chipset till the [fwcutter]("http://bcm43xx.berlios.de/?go=home") folks reverse-engineer that firmware.  They indicate as much on the [fwcutter site]("http://bcm43xx.berlios.de/?go=devices") it is flaky, so there you go.

---

### Post by liquilife on 2006-10-02
Microsoft VX-3000 lifecam. Actually they have 3 cameras all very similair.
VX-1000
VX-3000
VX-6000 (supports megapixle widelense angle)

It appears the micorphone is recognized but there is no support whatsoever of the camera its self.

---

### Post by John.Michael.Kane on 2006-10-02
***Mouse was defective***

---

### Post by acheun on 2006-10-04
*** message removed ***

---

### Post by arkangel on 2006-10-04
Lexmark X2250 
!!Never buy this not eve for windows

---

### Post by brephophagist on 2006-10-06
scanner: epson perfection 3200 photo

xsane seems to recognize it, but the scanner seems to disappear from /proc/bus/usb/devices after one pass of the bulb (either to build a preview or scan an image).  the aforementioned preview/image is garbage, as well.

I know I know--not officially supported in sane-epson(5).

---

### Post by Fitzcarraldo on 2006-10-07
Not all units of the Belkin 54g Notebook PCMCIA Wireless Card model no. F5D7010 work out of the box with Dapper Drake, necessitating much hacking:

[http://www.ubuntuforums.org/showthread.php?t=272813](http://www.ubuntuforums.org/showthread.php?t=272813)

---

### Post by Makyver on 2006-10-13
TV USB2.0  
Manufacturer: AVerMedia 
Speed: 480Mb/s (high)
USB Version:  2.00
Device Class: 00(>ifc )
Device Subclass: 00
Device Protocol: 00
Maximum Default Endpoint Size: 64
Number of Configurations: 1
Vendor Id: 07ca
Product Id: e820
Revision Number:  0.01

This has no driver even though it's pci cousins do I believe.

---

### Post by egd on 2006-10-14
Asus P5WDG2 WS Professional motherboard
- Marvell 88SE614x on-board SATAII controller is not detected on installation of Dapper Drake.

---

### Post by DavidGX on 2006-10-14
Gateway MX6448 notebook.

The built-in audio hardware does not work. It's listed as "HDA ATI SB" and also "SigmaTel ID 7634".. that's the chip I think.

I'm pretty much being forced back to windows because this isn't supported :(

---

### Post by osalo on 2006-10-14
LG M1 Express M1-J2ABV1 laptop
- Intel Core Duo T2300 (1.66GHz)
- 1GB DDR II
- NVIDIA GeForceTM Go 7400
- 80GB SATA (5400rpm)
- 15 SXGA+WVA(1400x1050)
- Intel Pro/Wireless 3945ABG(802.11a/b/g)
- 10/100/1000Mbps(Agere et131x) 

Test OS: Ubuntu 6.06 (Dapper Drake) and Ubuntu 6.1beta (Edgy Eft)

ISSUES: 
LAN: not working (et131x support not in kernel)
WIFI: not working with WPA enabled (encryption off works)
AUDIO: the line out -jack does't let audio thru, though the laptop speakers work nicely
STANDBY/HIBERNATE: not working

---

### Post by elizleisndahizle on 2006-10-14
I believe I have read this in multiple HP and Compaq laptops.
Conexant HD Audio doesn't work
Broadcom wireless doesn't work(what other than atheros and ralink does though)
I have read that the card reader doesn't work its a ricoh something.
ACPI so no battery meter, no CPU scaling, no nothing of this type.
Touchpad doesn't work right.
The only thing that I have found to work well are the shortcut keys and volume control on the top.

I <3 Ubuntu but I have switched to Sabayon on my laptop until until audio works out of the box :) and XGL/Compiz and multiple pretty themes are nice too, Sabayon has those.

---

### Post by BriGy86 on 2006-10-14
I use Kubuntu, and for some reason in the display settings it does not seem to have a driver for a samsung syncmaster 930b LCD monitor (which i have) it does have a driver for my other monitor which is an NEC accusync 700 CRT, BUT it's using that driver for my LCD monitor and the NEC monitor just doesn't display anything???????????

I don't really know why it's doing this but i figured i would mention it

---

### Post by japanguy30 on 2006-10-15
new to linux ubuntu.i have an lexmark printer x2350 printer,will this printer work with ubuntu.if it does is it hard to find the driver for my lexmark x2350 printer.any help will be very much appreciated.thank you.

---

### Post by louistan3 on 2006-10-15
sony vaio SZ integrated webcam(dont knw the name hehe)
and the fingerprint reader..

havent found anything to make it work..

---

### Post by mi_were on 2006-10-16
3Com Corporation Mini PCI 56k Winmodem does not work and would sem not to be supported by Linux.

---

### Post by Bagnaj97 on 2006-10-16
> **bloodniece said:**
> **Lenovo 3000 C100**
Everyhting works except eth1 = BCM4319
The Broadcom BCM4319 did not work with any known Windows driver from Lenovo or elsewhere else using ndiswrapper.

There is a newer version of ndiswrapper in Edgy which does work with this chipset (I'm running Edgy on my C100 for this reason).

---

### Post by Goliash on 2006-10-16
Pinnacle PCTV 310e
external USB 2.0, DVB-T, hybrid
This piece of hw unfortunately doesn't work under Linux. I looked all over the internet but with no success. Not supported.

---

### Post by crash0 on 2006-10-16
parts of my thinkpad r40e:

1. the sleep/hibernate options (or "suspend to ram/hdd" if i recall it correctly)
2. ibm special keys: volume up/down/mute, access ibm button, fn key combos
3. weird trackpoint problems (clicks random stuff sometimes)

---

### Post by RikBlankestijn on 2006-10-16
02:0a.0 Multimedia controller: Philips Semiconductors SAA7133/SAA7135 Video Broadcast Decoder (rev d1)

---

### Post by Chxta on 2006-10-17
The video card on my Acer Aspire 1640z is performing less than satisfactorily, and there is no sound at all...

---

### Post by Ambimom on 2006-10-17
Canoscan Lide 30

[Xsane recognizes it, but the only way to use it is to create jpg and then insert jpg into an open office document to print it.]

---

### Post by finalbeta on 2006-10-18
Trust 320 Spacec@m
Medion MD8080 PC system: 5.1 Sound not working, TV card sound only through OSS
Scanner LT9385

---

### Post by Jim March on 2006-10-18
My "EVDO" PCMCIA modem, Kyocera KPC650 under Verizon.  This is a $60/month mostly-unlimited wireless "low grade broadband" (in urban areas anyways) modem based on cellular tech.  If you can get a Verizon cell signal at all, you'll get at least good dialup speeds ("Nationalaccess").

EVDO modems are very weird critters indeed.  They have some characteristics of dial-up modems but "aren't".

There is a lot of info out there on getting these to work in Ubuntu but...it sometimes just doesn't work.

My solution: buy a Kyocera/D-Link "KR1" EVDO router.  This is an external box that has it's own PCMCIA slot for the KPC650 or other PCMCIA EVDO modem, and turns that into straight Ethernet, WiFi or both.  $250  but it's worth it - you can share your connection with multiple PCs/Macs/Linux/etc. boxes without any added drivers other than basic Ethernet/DHCP.

The best source of info on these:

[http://www.evdoforums.com/viewforum.php?f=17](http://www.evdoforums.com/viewforum.php?f=17)

A few people have had problems but...for most (who don't run VPN at least) it's plug'n'play.

[http://booster-antenna.com/index.php?main_page=product_info&cPath=35&products_id=99](http://booster-antenna.com/index.php?main_page=product_info&cPath=35&products_id=99)

The Top Global 6000 is supposedly even better:

[http://booster-antenna.com/index.php?main_page=product_info&cPath=35&products_id=123](http://booster-antenna.com/index.php?main_page=product_info&cPath=35&products_id=123)

...but that Godawful pyramid shape means no shlepping it around in the laptop bag.  Bzzzt.

As a bonus, any of these routers move that very high powered cell signal away from your..."reproductive organs".  With the amount of time I'm online, I could practically feel my nuts mutate.

I have no connection to that company other than being a satisfied customer.  I do recommend them; for one thing, with every KR1 they include a CD they built with three different firmware revisions and instructions on how to upgrade/downgrade and recover from mid-firmware-upload crashes.  That CD worked just fine for me under Dapper and Firefox.

---

### Post by olebole on 2006-10-20
IBM/Lenovo Thinkpad Z61m - Suspend to RAM / Suspend to Disk not working

I played around a lot with all the ACPI options - no success so far. Suspend seems to work but when waking up, the xserver continually restarts, the only option being to shutdown the system by pressing the power button, resulting in a graceful shutdown.

The only distribution which works perfectly at this moment is SuSe 10 which I personally don't like all that much...
Would it be possible to integrate that really great "s2ram"? Also, I would much prefer the "original" kpowersave - no offence meant to Sebastian Kügler but, when there are lots of powersave options for a given hardware, why keep them from the user?
Other things not working though not that annoying: fingerprint reader, modem, bluetooth (weird: works when it was enabled in BIOS AND windows...), SD-Card Reader (not really tested).
Everything else just fine, but SLEEP / HIBERNATE not working really is a show stopper :(

---

### Post by Nevermore on 2006-10-21
Panasonic CF73:
hotkeys not working
pcc_acpi not loading
no brightness change
poor battery duration
doesn't resume from suspend or hibernate unless pcmcia, pcmcia_core are blacklisted.

---

### Post by fraterm on 2006-10-21
Serial Wacom ArtPad II Tablet needs documentation and some integration into the ubuntu system.  Surprised that this kind of thing is so difficult.  Saw quite a few forum posts asking about this too.  My daughter is a happy doodler, and edubuntu with no wacom support is a let down. ](*,) 

Also:

Wacom USB Tablets need similar default easy udev configuration similar to the effort that was put into the aiptek tablet: 
```
# Create /dev/input/aiptektablet
BUS=="usb", DRIVER=="aiptek", KERNEL=="event[0-9]*", \
                                        SYMLINK+="input/aiptektablet"
```

---

### Post by cmkennedy124 on 2006-10-21
I have a Kodak Easyshare C310 camera and Printer Dock 3 package I bought last year. Ubuntu reads the printer name but has no driver listed for the printer to work. I don't see others having luck with this printer either here. There are only 2 drivers to choose from in Kodak printer list....there needs to be more.

The camera uploads pictures fine though. Just plug in the dock to the usb port, click the dock button for uploading images to computer, and Ubuntu fetches them right away! 

You can still print photos from the dock off the camera or buy photo paper for your printer that does work with Ubuntu, load the picures on the computer, and print away.

---

### Post by cfsporn on 2006-10-22
My sound card used to work in Ubuntu and now it doesn't. When I go to the Sound prefrence pane, there is no sound card there. What should I do? My sound card is a Sound Blaster SB Live! from around 2001.

---

### Post by blaxnake on 2006-10-22
SIS M661MX integrated Graphic Adapter, on an Acer Travelmate 2310 laptop.

Off: Evrything else is ok. This one don't work. It's very disturbing the wrogn refresh rate. Neither the: [http://www.winischhofer.eu/linuxsispart4.shtml](http://www.winischhofer.eu/linuxsispart4.shtml) and [http://rik.no-ip.com/~rik/?q=node/10](http://rik.no-ip.com/~rik/?q=node/10) and  does'nt helped me out...

---

### Post by cliffskoog on 2006-10-23
Hello,

I've a Dell 9400/e1705 with a core duo processor and Intel 945GM video. Most important to me, and what keeps me from using Linux, is that I cannot get a 'dual monitor'/'dual head'/'big desktop' set up on this machine. I've trawled posts and tweaked, but as yet to no avail. Help? Hope?

Thanks

---

### Post by rictus007 on 2006-10-23
Linksys Wireless-B PCI Adapter (WMP11)
Intel 82865G Graphics Controller (problem with the resolution)

---

### Post by tigerfox on 2006-10-24
I've got Sony Vaio VGN-SZ28GP/C and everything works fine except for the ff:

1) Plugging in a headset would mute speaker and no sound coming out the headset. (I dual boot to windows and headset working fine)
2) Finger Print Sensor device not working. Guess it's not yet part of the sony-pi.
3) No driver for NVidia Gefore GO 7400.
4) S1 and S2 buttons not working.
5) Unable to use any projector as VGA output not working.

---

### Post by garwaymatt on 2006-10-24
My Ipod nano 2nd gen is not recognised or mounted, apart from a split second when i plug it in. Also my canon mp170 multifunction printer fails to work, as there is no driver, which is probably canons fault more than anything.

---

### Post by Varjagy on 2006-10-24
1: Nikon CoolPix990 doesn't work with a USB cable

2: Compact Flash - PCMCIA Adapter. dmesg shows it, but I have to mount it all the time.

---

### Post by drache777 on 2006-10-24
My VIA Rhine II, an onboard ethernet adapter. 
```
dmesg
```
actually tells me that it's fine, the driver is loaded and everything functions properly. 
However activation of it fails through the networking gui and firestarter fails to acknowledge that it's active. The same results with KDE's configuring gui. 
I've tried 5.06 and the new 6.06, neither work properly.

---

### Post by xmux on 2006-10-25
Hi!

I have a problem with my SD card reader.. In Dapper times people were saying that the SD card reader will work perfectly in Edgy Eft and now i have Edgy Eft and my SD card reader doesnt work!! What can i do? i have a Toshiba Laptop and i tried almost all the forums and google pages that i found but its doesnt work... do u have some suggestions? (please dont tell me buy a external sd card reader 'cause this is not the solution, its running away from problem..)

Thanks.


i got this one with the first:

```
 description: Notebook
    product: Satellite M30
    vendor: TOSHIBA
    version: PSM30E-71022-TR
    serial: 74624011G
    width: 32 bits
    capabilities: smbios-2.31 dmi-2.31
    configuration: administrator_password=disabled boot=normal chassis=notebook frontpanel_password=unknown keyboard_password=unknown power-on_password=enabled uuid=7EFE4C80-B0FD-17A2-8030-B1D774624011
  *-core
       description: Motherboard
       product: Portable PC
       vendor: TOSHIBA
       physical id: 0
       version: Version A0
       serial: $$C04773WV
     *-firmware
          description: BIOS
          vendor: TOSHIBA
          physical id: 0
          version: Version 1.50 (05/19/2004)
          size: 128KB
          capacity: 448KB
          capabilities: isa pci pcmcia upgrade shadowing vesa escd cdboot bootselect pcmciaboot edd int13floppy720 int5printscreen int9keyboard int17printer acpi usb agp biosbootspecification netboot
     *-cpu
          description: CPU
          product: Intel(R) Pentium(R) M processor 1.50GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 6.13.6
          slot: uFC-PGA Socket
          size: 1500MHz
          capacity: 1500MHz
          width: 32 bits
          clock: 100MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr mce cx8 sep mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss tm pbe up est tm2 cpufreq
        *-cache:0
             description: L1 cache
             physical id: 12
             slot: CPU Internal
             size: 64KB
             capacity: 64KB
             clock: 1GHz (1ns)
             capabilities: internal write-back unified
        *-cache:1
             description: L2 cache
             physical id: 13
             slot: CPU Internal
             size: 2MB
             capacity: 2MB
             clock: 1GHz (1ns)
             capabilities: burst internal write-back unified
     *-memory
          description: System Memory
          physical id: 81
          slot: System board or motherboard
          size: 512MB
          capacity: 2GB
        *-bank:0
             description: SODIMM SDRAM Synchronous
             physical id: 0
             slot: DIMM 0
             size: 512MB
             width: 64 bits
        *-bank:1
             description: SODIMM SDRAM Synchronous [empty]
             physical id: 1
             slot: DIMM 1
             width: 64 bits
     *-pci
          description: Host bridge
          product: 82855PM Processor to I/O Controller
          vendor: Intel Corporation
          physical id: d0000000
          bus info: pci@00:00.0
          version: 21
          width: 32 bits
          clock: 33MHz
          resources: iomemory:d0000000-dfffffff
        *-pci:0
             description: PCI bridge
             product: 82855PM Processor to AGP Controller
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@00:01.0
             version: 21
             width: 32 bits
             clock: 66MHz
             capabilities: pci normal_decode bus_master
           *-display
                description: VGA compatible controller
                product: NV34M [GeForce FX Go5200]
                vendor: nVidia Corporation
                physical id: 0
                bus info: pci@01:00.0
                version: a1
                size: 256MB
                width: 32 bits
                clock: 66MHz
                capabilities: vga bus_master cap_list
                configuration: driver=nvidia
                resources: iomemory:c1000000-c1ffffff iomemory:e0000000-efffffff irq:10
        *-usb:0
             description: USB Controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@00:1d.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd
             resources: ioport:1800-181f irq:3
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.17-10-generic uhci_hcd
                physical id: 1
                bus info: usb@1
                logical name: usb1
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
              *-usb
                   description: Mouse
                   product: Microsoft Notebook/Mobile Optical Mouse 2.0
                   vendor: Microsoft
                   physical id: 2
                   bus info: usb@1:2
                   version: 2.00
                   capabilities: usb-1.10
                   configuration: driver=usbhid maxpower=100mA speed=1.5MB/s
        *-usb:1
             description: USB Controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@00:1d.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd
             resources: ioport:1820-183f irq:11
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.17-10-generic uhci_hcd
                physical id: 1
                bus info: usb@2
                logical name: usb2
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
        *-usb:2
             description: USB Controller
             product: 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@00:1d.7
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: ehci bus_master cap_list
             configuration: driver=ehci_hcd
             resources: iomemory:c0000000-c00003ff irq:7
           *-usbhost
                product: EHCI Host Controller
                vendor: Linux 2.6.17-10-generic ehci_hcd
                physical id: 1
                bus info: usb@3
                logical name: usb3
                version: 2.06
                capabilities: usb-2.00
                configuration: driver=hub maxpower=0mA slots=4 speed=480.0MB/s
              *-usb
                   description: Mass storage device
                   product: USB2.0 Storage Device
                   vendor: Cypress Semiconductor
                   physical id: 3
                   bus info: usb@3:3
                   logical name: scsi1
                   version: 0.01
                   serial: DEF10BA906D6
                   capabilities: usb-2.00 scsi emulated scsi-host
                   configuration: driver=usb-storage maxpower=0mA speed=480.0MB/s
                 *-disk
                      description: SCSI Disk
                      product: SP2014N
                      vendor: SAMSUNG
                      physical id: 0.0.0
                      bus info: scsi@1:0.0.0
                      logical name: /dev/sda
                      version: 0000
                      serial: 0S881JLJ
                      size: 186GB
                      capabilities: partitioned partitioned:dos
                    *-volume:0
                         description: HPFS/NTFS partition
                         physical id: 1
                         bus info: scsi@1:0.0.0,1
                         logical name: /dev/sda1
                         capacity: 58GB
                         capabilities: primary
                    *-volume:1
                         description: HPFS/NTFS partition
                         physical id: 2
                         bus info: scsi@1:0.0.0,2
                         logical name: /dev/sda2
                         capacity: 58GB
                         capabilities: primary
                    *-volume:2
                         description: HPFS/NTFS partition
                         physical id: 3
                         bus info: scsi@1:0.0.0,3
                         logical name: /dev/sda3
                         capacity: 69GB
                         capabilities: primary
        *-pci:1
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@00:1e.0
             version: 83
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master
           *-firewire
                description: FireWire (IEEE 1394)
                product: TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)
                vendor: Texas Instruments
                physical id: 7
                bus info: pci@02:07.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: ohci bus_master cap_list
                configuration: driver=ohci1394
                resources: iomemory:c2006000-c20067ff iomemory:c2000000-c2003fff irq:3
           *-network:0
                description: Ethernet interface
                product: 82801DB PRO/100 VE (MOB) Ethernet Controller
                vendor: Intel Corporation
                physical id: 8
                bus info: pci@02:08.0
                logical name: eth0
                version: 83
                serial: 00:0e:7b:2d:23:17
                size: 10MB/s
                capacity: 100MB/s
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegociation
                configuration: autonegociation=on broadcast=yes driver=e100 driverversion=3.5.10-k2-NAPI duplex=half firmware=N/A link=no multicast=yes port=MII speed=10MB/s
                resources: iomemory:c2004000-c2004fff ioport:3000-303f irq:11
           *-network:1
                description: Wireless interface
                product: PRO/Wireless 2200BG Network Connection
                vendor: Intel Corporation
                physical id: a
                bus info: pci@02:0a.0
                logical name: eth1
                version: 05
                serial: 00:0e:35:36:b6:06
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=ipw2200 driverversion=1.1.2kmprq firmware=ABG:9.0.2.6 (Mar 22 2005) ip=192.168.1.231 link=yes multicast=yes wireless=IEEE 802.11b
                resources: iomemory:c2005000-c2005fff irq:11
           *-pcmcia
                description: CardBus bridge
                product: ToPIC100 PCI to Cardbus Bridge with ZV Support
                vendor: Toshiba America Info Systems
                physical id: b
                bus info: pci@02:0b.0
                version: 33
                width: 32 bits
                clock: 33MHz
                capabilities: pcmcia bus_master cap_list
                configuration: driver=yenta_cardbus
                resources: iomemory:c2007000-c2007fff irq:3
           *-system UNCLAIMED
                description: System peripheral
                product: SD TypA Controller
                vendor: Toshiba America Info Systems
                physical id: d
                bus info: pci@02:0d.0
                version: 05
                width: 32 bits
                clock: 33MHz
                capabilities: cap_list
                resources: iomemory:c2006800-c20069ff irq:3
        *-isa UNCLAIMED
             description: ISA bridge
             product: 82801DBM (ICH4-M) LPC Interface Bridge
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@00:1f.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
        *-ide
             description: IDE interface
             product: 82801DBM (ICH4-M) IDE Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@00:1f.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master
             configuration: driver=PIIX_IDE
             resources: ioport:1840-184f iomemory:32000000-320003ff irq:11
           *-ide:0
                description: IDE Channel 0
                physical id: 0
                bus info: ide@0
                logical name: ide0
                clock: 33MHz
              *-disk
                   description: ATA Disk
                   product: TOSHIBA MK4021GAS
                   vendor: Toshiba
                   physical id: 0
                   bus info: ide@0.0
                   logical name: /dev/hda
                   version: GA224G
                   serial: 83AG6548T
                   size: 37GB
                   capacity: 37GB
                   capabilities: ata dma lba iordy smart security pm apm partitioned partitioned:dos
                   configuration: apm=off mode=udma5 smart=on
                 *-volume:0
                      description: HPFS/NTFS partition
                      physical id: 1
                      bus info: ide@0.0,1
                      logical name: /dev/hda1
                      capacity: 12GB
                      capabilities: primary bootable
                 *-volume:1
                      description: Linux swap / Solaris partition
                      physical id: 2
                      bus info: ide@0.0,2
                      logical name: /dev/hda2
                      capacity: 1027MB
                      capabilities: primary nofs
                 *-volume:2
                      description: Linux filesystem partition
                      physical id: 3
                      bus info: ide@0.0,3
                      logical name: /dev/hda3
                      capacity: 298MB
                      capabilities: primary
                 *-volume:3
                      description: Extended partition
                      physical id: 4
                      bus info: ide@0.0,4
                      logical name: /dev/hda4
                      capacity: 23GB
                      capabilities: extended partitioned partitioned:extended
           *-ide:1
                description: IDE Channel 1
                physical id: 1
                bus info: ide@1
                logical name: ide1
                clock: 33MHz
              *-cdrom
                   description: DVD-RAM writer
                   product: MATSHITADVD-RAM UJ-820S
                   physical id: 0
                   bus info: ide@1.0
                   logical name: /dev/hdc
                   version: 1.00
                   capabilities: packet atapi cdrom removable nonmagnetic dma lba iordy audio cd-r cd-rw dvd dvd-r dvd-ram
                   configuration: mode=udma2
                 *-disc
                      physical id: 0
                      logical name: /dev/hdc
        *-multimedia
             description: Multimedia audio controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller
             vendor: Intel Corporation
             physical id: 1f.5
             bus info: pci@00:1f.5
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=Intel ICH
             resources: ioport:1c00-1cff ioport:1880-18bf iomemory:c0000c00-c0000dff iomemory:c0000800-c00008ff irq:4
        *-communication UNCLAIMED
             description: Modem
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller
             vendor: Intel Corporation
             physical id: 1f.6
             bus info: pci@00:1f.6
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: generic cap_list
             resources: ioport:2400-24ff ioport:2000-207f irq:4
  *-battery
       description: Lithium Ion Battery
       product: LP644E
       vendor: TOSHIBA
       physical id: 1
       version: 04/06/14
       serial: 1100037902
       slot: 1st Battery
       configuration: voltage=10.8V
```

!!!!the second one is:
```
/dev/hda5 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.17-10-generic/volatile type tmpfs (rw)
/dev/hda3 on /boot type ext3 (rw)
/dev/hda1 on /media/hda1 type ntfs (rw,nls=utf8,umask=007,gid=46)
```

---

### Post by doobit on 2006-10-25
Can't get any carbus pcmcia adapter to work. The message when loading says something like cs:cardbus not supported "consider getting some new equipment" 

I've tried a Linksys HPNA2 adapter and two different 3Com LAN adapters.

Sorry, but this is what I have!

---

### Post by goofyheadedpunk on 2006-10-26
Lenovo 3000 N100

No sound still from the Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller. Wireless ceased to function in Edgy with the Intel Corporation PRO/Wireless 3945ABG Network Connection. Hibernation still does not function.

---

### Post by MrBurrito on 2006-10-26
06:00.0 Ethernet controller: Atheros Communications, Inc. AR5212 802.11abg NIC (rev 01)

Used to work, Doesnt work anymore....
[-(

---

### Post by MrBurrito on 2006-10-26
05:02.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)

This one doesnt work either... Used to work in Dapper[-(

---

### Post by shouravv on 2006-10-27
Dell Inspiron 1150 lid switch: closing the lid would not perform the task specified by power management tools; such as won't put system on standby etc. but would perform tasks properly for opening/lifting the lid. Using Edgy, release 6.10, Kernel 2.6,17 generic.

---

### Post by ShadowVlican on 2006-10-27
toshiba tablet protege 3500
ubuntu 6.06

the wacom pen tablet doesn't work, rendering my tablet same as a normal laptop

(there's probably a whole bunch of commands to get it to work, though as a new user to linux i don't feel like doing that, especially since WinXP TPE detects it out of the box)

but hey, wouldn't hurt to let you guys know :)

edit: still doesn't work under 6.10

---

### Post by notarikon on 2006-10-27
Canon Pixma MP150 Printer/Scanner

Ubuntu recognises the printer (including the correct model) but no drivers work for it. There is a commercial driver available, but this is for printing only, no scanning. Also, the commercial driver doesn't seem to do borderless photo prints, which is what 99% of the printing done on it is for.

---

### Post by reggert on 2006-10-27
**Marvell Yukon 88E8056 PCI-E Gigabit Ethernet Controller**
integrated on a **Gigabyte GA-965P-S3** motherboard

The Device Manager sees the device but doesn't seem to know what it is, other than that the manufacturer is Marvell and the OEM is Gigabyte.

ifconfig or network-admin won't even acknowledge that it exists.

---

### Post by kinanti on 2006-10-28
Dell Inspiron 6400 laptop with ati x1400, and 1.5gb ram [ edgy eft ] :
Stand by and hibernate don't seem to work. The computer goes on stand by, but it will only show a black screen when coming out of it. Hibernate  just doesn't work for me.

K.

---

### Post by tpg on 2006-10-28
Wacom PenPartner2 USB tablet doesn't work - used to work in Dapper

I posted a bug at [https://launchpad.net/distros/ubuntu/+source/xorg/+bug/68346](https://launchpad.net/distros/ubuntu/+source/xorg/+bug/68346)

---

### Post by didobuntu on 2006-10-28
Asus laptop W2Jc

sound card: hda-intel with the Realtek chipset ALC 882. I never heard sound under linux. I tried alsa drivers versions 1.0.10 until the last one 1.0.13. No success

---

### Post by niels_larsen on 2006-10-28
On my Thinkpad A31p there is no wireless in Edgy, but was in 
Dapper. The hardware is

Network controller: Intersil Corporation Prism 2.5 Wavelan chipset (rev 01)
Ethernet controller: Intel Corporation 82801CAM (ICH3) PRO/100 VE (LOM) Ethernet Controller (rev 42)

I filed here too:

[https://launchpad.net/distros/ubuntu/+bug/68196](https://launchpad.net/distros/ubuntu/+bug/68196)

Upgrading to shakyEdgy has made me unable to work (from home) as 
you can imagine .. but yes it looks nice .. will try Dapper next.

---

### Post by sygin on 2006-10-29
Hi,

My Voodoo 3 graphics card fails to work with Edgy. There seems to be a bug in the tdfx driver. If I use the vesa driver, there are no problems.

Symptom: Gnome will reset to login screen after logging in.
KDE: Will reset to login screen after a window is moved or resized.

Thank you,
Sygin

---

### Post by blunile on 2006-10-29
Canon printer
 PIXMA IP 1600

---

### Post by jayson23 on 2006-10-29
None of the built-in card readers are recognized on my laptop:

Fujitsu P5020, running Ubuntu 6.10

SD card reader
Sony MemoryStick PRO reader
CF card reader

---

### Post by jsnielsen on 2006-10-30
Well, NVidia 6800 card won't work here.

---

### Post by atlas95 on 2006-10-30
Sound on the Packard Bell Easynote V.

Chipset ALC260

If someone could help me ...

:'(

---

### Post by adolfotregosa on 2006-10-30
Msi tv turner usb 2.0 vox.

The kernel seems to detect it just right but no software actually works with it. They simply crash or don't detect the vox

---

### Post by Vega on 2006-10-30
Toshiba M105

FN key commands on keyboard

can't control screen brightness and volume control.

---

### Post by winter7 on 2006-10-30
intel D845PESV motherboard

in 6.01 the install cd freezes

in 6.10 it boots up fine, but no hardware is detected, no hard drives to install to, no network, no sound. 

Windows is already running on this machine.

Also on my laptop, my linksys wpc54g version 1 pcmcia card is not functioning in either 6.01 or 6.10

---

### Post by SendDerek on 2006-10-31
On my VGN-FE550G running Ubuntu 6.06:

MotionEye WebCam (Build-in)
Microphone (Build-in)
S-Video Connection
External VGA (I can't figure out how to use it)

---

### Post by kingcharles1666 on 2006-10-31
> **sygin said:**
> Hi,

My Voodoo 3 graphics card fails to work with Edgy. There seems to be a bug in the tdfx driver. If I use the vesa driver, there are no problems.

Symptom: Gnome will reset to login screen after logging in.
KDE: Will reset to login screen after a window is moved or resized.

Thank you,
Sygin

Same problem but I could not get vesa to work either. Works fine in Dapper 6.06

---

### Post by [cz]_vd on 2006-11-01
laptop model: ASUS M6V-B022

unsupported hw: integrated multi- memmory card reader

unsupported hw feature: 
Microsoft Wireless Notebook Optical Mouse 4000v1.0 
Horizontal scrolling feature on multidimensional scrolling wheel and zoom function is not supported.

---

### Post by rajasekhar.yeruva on 2006-11-01
Creative Webcam Vista Plus :(

---

### Post by beemer on 2006-11-02
[Biostar NF61VM2]("http://http://www.biostar-usa.com/mbdetails.asp?model=NF61V%20Micro%20AM2")

System boots, gives a smp kernel and everything works except:

No sound (tried intel8x0 and hda-intel)
DMA for HD/DVD does not work and will not turn on.

Doing a lspci will give several "unknown"s for NVIDIA Chipset pieces (Audio is one of them).

Beemer

---

### Post by vseehua on 2006-11-03
canon pixma mp160 all in one..doesn't seem to have a driver available anywhere

Logitech Quickcam Messenger - tried using the Open Source driver QC, but doesn't work

The ENE Semiconductors card readers found in my Laptop (Acer Aspire 5500 Series)

thanks for listening

---

### Post by marx2k on 2006-11-03
There are currently no working drivers for the Epson ActionLaser 1600 printer in Linux and there don't seem to be any substitute printers that can be used to match it.

---

### Post by sunset_studies on 2006-11-04
DVICO FusionHDTV DVB-T nano USB tv tuner. 

Dmesg shows 
[17206386.232000] usb 5-3: new high speed USB device using ehci_hcd and address 3
[17206386.364000] usb 5-3: configuration #1 chosen from 1 choice

but there's no /dev/dvb or anything else to suggest the device is supported.

---

### Post by sherirao on 2006-11-04
**Device type:** Camera + Webcam (dual mode /USB) 
**Manufacture:** JVC  
**Model]:** GC-A33
**Issue:** *ubuntu edgy could not detect this device *

---

### Post by svetj on 2006-11-05
Ununtu edgy.
Laptop: ECS Green 732
Device not working: Onboard audio :( :( :( 
Details:
00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)
        Subsystem: Elitegroup Computer Systems Unknown device b732
        Flags: bus master, medium devsel, latency 173, IRQ 9
        I/O ports at 1400 [size=256]
        I/O ports at 1080 [size=128]
        Capabilities: [48] Power Management version 2
Issue: IRQ and clock issues.
The audio is played too fast, and after some minutes,
kernel gives the error "Disabling irq 9"...
Trying with irqpoll=noacpi at boot,
the audio is played too slow, with buffer issues,
and sometimes the system hangs.


Device type: Camera + Webcam (dual mode /USB)
Manufacture: BenQ
Model]: DC 1500
Details:
[17181103.076000] usb 3-1: new full speed USB device using ohci_hcd and address 4
[17181103.292000] usb 3-1: configuration #1 chosen from 1 choice
[17181103.296000] drivers/media/video/spca5xx/spca5xx-main.c: USB SPCA5XX camera found. Benq DC 1500 Spca533

Issue: webcam mode is correctly recognized,
but is not possible to acquire video and images.

Thank you

---

### Post by SRParda on 2006-11-06
VideoSeven LTV30C (30" LCD TV).

Not Work: 
   1280x768 (LCD Native Resolution), screen flashes and lines are displaced.

Works:
   At least 1280x768 Resolution is detected (in Ubuntu Edgy) and proposed.
   1280x1024 works (Maximun resolution downscaled: but text is blurry).

P.D.:
  Info on monitor manual:
  Resolution 1280x768, Refresh: 60Hz, 
  H: 47.776, V: 59.870, D.C:79.5Mhz, Pol.H: N, Pol.V: P
  HORIZ: Sync With: 128, Back Porch: 192, Front Porch: 64, Total: 1664
  VERT:  Sync With: 7, Back Porch: 20, Front Porch: 3, Total: 798

Thank You

---

### Post by penvzila on 2006-11-11
Toshiba U205-S5200:

-Can't access native resolution, forced to use VESA instead of intel drivers to get 1280x800.

-wireless does not work.

---

### Post by Compaq Armada 7800 on 2006-11-12
Ubuntu 6.10

snd card: ESS1879 no worky on compaq armada 7800](*,)

---

### Post by psychok9 on 2006-11-12
Auzuntech 7.1 C-Media 8788:
```
lspci
04:06.0 Multimedia audio controller: C-Media Electronics Inc Unknown device 8788
```

---

### Post by cogitno on 2006-11-13
EPSON Perfection 3200 Photo working (GT9800)

Got it working on my system (via firewire) by changing the the /etc/udev/rules.d/40.permissions.rules (in the SCSI section) to:

SYSFS{type}=="3", SYSFS{vendor}=="Epson", GROUP="scanner"
            to
SYSFS{type}=="3", SYSFS{vendor}=="EPSON", GROUP="scanner"

I actually just added the capitalised version to the list. I don't know if this will have any negative consequences elsewhere, but for now it works. It reports as a GT 9800.

I noticed (after many months) that the HAL Device Manager reports the Device vendor as EPSON rather than Epson.

---

### Post by amanita on 2006-11-13
1)Type Of Hardware
2)Hardware Maker
3)Hardware Model
4)Known Issue

1)Scanner
2)Canon
3)CanoScan 4200F
4)This scanner is not working in Linux at all...

---

### Post by VosaxAlo on 2006-11-13
1)Type Of Hardware
2)Hardware Maker
3)Hardware Model
4)Known Issue
-------------------------------------------------

1) PLANon DocuPen RC800, pen color scanner
2) PLANon Systems Solutions, Inc.
   Company web address:
[http://planon.com/docupen_rc800.php]("http://planon.com/docupen_rc800.php")
3) DocuPen RC800
4) not recognized when connected through the USB port

---

### Post by TheForkOfJustice on 2006-11-13
1)Thumb Drive
2)Sandisk
3)128MB
4)USB ports on a Compaq Presario v2750CA notebook do not mount my thumb drive.

Same problem existed in Dapper (I'm now using Edgy) but at least this time the light on my drive stays lit so the situation has improved. No mount icon appears on the desktop but it mounts fine on my desktop so the stick works fine.

Must be a problem managing my laptop's USB bus.

My lspci output:

> 
00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 10)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller (rev 80)
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 81)
00:14.1 IDE interface: ATI Technologies Inc Standard Dual Channel PCI IDE Controller ATI (rev 80)
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge (rev 80)
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge (rev 80)
00:14.5 Multimedia audio controller: ATI Technologies Inc IXP SB400 AC'97 Audio Controller (rev 80)
00:14.6 Modem: ATI Technologies Inc ATI SB400 - AC'97 Modem Controller (rev 80)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc ATI Radeon XPRESS 200M 5955 (PCIE)
05:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
05:02.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
05:09.0 CardBus bridge: Texas Instruments PCIxx21/x515 Cardbus Controller
05:09.2 FireWire (IEEE 1394): Texas Instruments OHCI Compliant IEEE 1394 Host Controller
05:09.3 Mass storage controller: Texas Instruments PCIxx21 Integrated FlashMedia Controller
05:09.4 Class 0805: Texas Instruments PCI6411, PCI6421, PCI6611, PCI6621, PCI7411, PCI7421, PCI7611, PCI7621 Secure Digital (SD) Controller

ALSO:

1) mp3 player
2) iriver
3) UMS v1.70 (from the updater) firmware of the T10 (512MB)
4) Just like my above thumb drive, it doesn't mount on my laptop but the desktop mounts it fine.

---

### Post by TheForkOfJustice on 2006-11-13
1)Wifi
2)Broadcom Corporation
3)BCM4318 rev 02 - Airforce One 54g 802.11g
4)Not active by default. Will poke around with it later. Could just be my settings since I had to tweak it quite a bit in Dapper.

---

### Post by vanishedsoul on 2006-11-14
hi there!

i have:

**Intel D945GNT Motherboard**
**Creative (Sound Blaster) 24bit Audigy Live **(sound card, i have disabled the builtin aduio device from the motherboard's biaos ) **with creative 5.1 speaker system** and **Samsung SyncMaster 450B Moniter**

After the installation of UBUNTU 6.06, the video driver were working fine. Yesterday i was just trying to install some library to play the mp3 format and did installed some. After some time when i rebooted the system, the screen resolution seems to be set at the 1024 * 768 pixels but as soon as it login the UBUNTU the screen resolution turns to 640 * (something). I tried to change it through the "Screen Resolution" but it is not giving any other option previously it was working fine at the 1024*768 pixels and it still work in the Windows Xp too.

Also please tell me if i need to install the drivers for the sound card and the motherboard other than the above mentioned problem? thanks in advance

---

### Post by daengbo on 2006-11-14
O2 Micro 4-in-1 card reader for my laptop
00:09.0 CardBus bridge: O2 Micro, Inc. OZ711M1/MC1 4-in-1 MemoryCardBus Controller (rev 20)
00:09.1 CardBus bridge: O2 Micro, Inc. OZ711M1/MC1 4-in-1 MemoryCardBus Controller (rev 20)
00:09.2 System peripheral: O2 Micro, Inc. OZ711Mx 4-in-1 MemoryCardBus Accelerator
Driver available here : [ftp://scrdriver:scrdriver@209.19.104.194/Linux/O2Micro_PCMCIA_SCR_203_Linux_Kernel26_OpenSource.tar.gz](ftp://scrdriver:scrdriver@209.19.104.194/Linux/O2Micro_PCMCIA_SCR_203_Linux_Kernel26_OpenSource.tar.gz)

Dan

---

### Post by marx2k on 2006-11-14
1)Super Joybox 5
2)MayFlash
3)No specific hardware model 
4)So far there are no drivers for this item in Linux.  When this item is plugged into any USB port, Gnome freezes.  Unplugging this item does not completely unfreeze Gnome and the system has to be rebooted in order for it to return to normal.

This is the item in question:
[http://www.mayflash.com/pc/pc039/pc039-1.htm](http://www.mayflash.com/pc/pc039/pc039-1.htm)

---

### Post by geolr on 2006-11-19
**USB Hub** integrated in Dell TFT Flat Panel Monitor 1907FP (bought November 2006).

Both Dapper and Edgy hang at the progress bar when plugged in before booting.
When plugging in while in logged in as user the system freezes (no text terminals, X restart etc.)

---

### Post by sarc on 2006-11-20
HP Pavilion dv2000 webcam (USB webcam mounted on notebook). It worked fine on Dapper.

---

### Post by Eddie Wilson on 2006-11-20
ActionTec 56k External Modem.
Works great with Dapper 6.06 but will not work with Edgy 6.10
Works great with other distros I've tried.
Eddie

---

### Post by Elvish Legion on 2006-11-21
Ati Radeon Xpress 1100
No 3d accel,
All documentation for installing ATI drivers fails to enable 3d accel with this card...

---

### Post by ububaba on 2006-11-24
**[COLOR="DarkRed"]Canon MF3220[/COLOR]** Multifunctional copier, printer and scanner (Bought Nov 2006)

No drivers available.

---

### Post by dude420 on 2006-11-24
Intel 830mg integrated graphics
Dimension 2600
Intel 830mg chip set

---

### Post by jazzevan on 2006-11-24
wmp11 v. 2.1
would be really nice if this and other pci adapters were auto-detected, etc. /:

---

### Post by dude420 on 2006-11-24
.

---

### Post by mundano on 2006-11-26
Multifunction Laser Printer

Epson AcuLaser CX11N series.

Don't worl at all with ubuntu 6.10 or Ubuntu 6.06..

---

### Post by mimart7 on 2006-11-26
Sound Blaster Audigy SE

I have no sound coming from my speakers.  When I boot into XP mu audio works just fine. Can't find drivers for this card.  Any reccomendations on how I can make my Sound Card, or get audio from my speakers would be apprecaiated.  Here are the makings of my rig: 

	
A8N32-SLI Deluxe mobo
AMD 3500 + 64 bit
Saphire 64 mb video card
Sound Blaster Audigy SE 24 bit sound card
Samsung Litescribe DVD burner
Seagate 320 GB Perpendicular HD (XP on this drive)
Western Digital 40 GB HD (Ubuntu on this drive) 

Mike :-k

---

### Post by asplode on 2006-11-27
VIA S3 Unichrome video on a Gateway laptop in edgy.

---

### Post by wgaprotest on 2006-11-27
1)IR Blaster won't change channels on digital cable setop boxes
2)Hauppauge
3)WinTV-PVR-250, Retail model 980 (non MCE ver., although MCE software is included in driver disk)
4)Known Issue, got this information straight from Hauppague tech support; this is a hardware limitation of the IR blaster (only this part) that ships with this "older" card, as it's only a receiver, and won't transmit signals to the STB's as well

Please note that, other than changing channels on the STB's this card works.  It will also register the channel changes on your display, as only the internal Hauppauge card actaully gets the signal. 

Hauppauge offered to exchange the card for the "newer" 150 card that does have a better IR blaster, and pay for the shipping to return it to me; the only difference is that the 250 card is more expensive, and they couldn't refund the difference. 

Conclusion: buy the 150 model

---

### Post by cbratteli on 2006-11-27
On a Sony Vaio SZ340P, the following do not work under Ubuntu 6.10:

Webcam
Fingerprint reader
HP OfficeJet 7400 series scanning over WiFi
Stamina/Speed switch
S1/S2 buttons

---

### Post by SSBM86 on 2006-11-28
Motherboard
ASUS P4S8XMX
can't reboot

hang at

no reboot fixup found for your hardware

---

### Post by lazyd2 on 2006-11-28
1)Type Of Hardware:**Motherboard**
2)Hardware Maker:**Asus**
3)Hardware Model:[**Striker Extreme**]("http://www.asus.com/products4.aspx?modelmenu=2&model=1439&l1=3&l2=11&l3=397")
4)Known Issue:**Network card not operational**

---

### Post by Ramesis on 2006-11-28
Hardware Type: Keyboard
Manufacturer: Microsoft
Model: MS Remote Keyboard Media centre Edition (1044)                                                                                                                                                                  
Problem: Receiver detected by lirc - how ever can't use keyboard in x windows

---

### Post by penvzila on 2006-11-30
> **penvzila said:**
> Toshiba U205-S5200:

-Can't access native resolution, forced to use VESA instead of intel drivers to get 1280x800.

-wireless does not work.

This was fixed by someone who posted an xorg.conf for the U205-S5200 here:

[http://ubuntuforums.org/showthread.php?t=262438](http://ubuntuforums.org/showthread.php?t=262438)

So I no longer think it was a hardware incompatibility issue.

---

### Post by kvonb on 2006-11-30
> SSBM86:
Motherboard
ASUS P4S8XMX
can't reboot

hang at

no reboot fixup found for your hardware

If you mean the Asus P4S800MX mainboard, then there must be a problem with your system somewhere, mine works perfectly under both Dapper and Edgy.

---

### Post by Hermanas on 2006-12-02
LG L1900 Eclipse LCD needs drivers to be adjusted, but by default only windows is supported.

---

### Post by roachk71 on 2006-12-02
Software Suspend and Hibernation on HP Pavilion xt125 Notebook:

Attempts to resume, but once all the information is loaded from the HD, the system hangs.

Tweaking the ACPI options never helped, either. :-?

The battery life is also dismal (25 minutes max. with a new, freshly-charged battery.)

Another problem device, for which there is a workaround: Samsung HM120JC 120GB PATA Hard Disk (large, journalling partitions are corrupted rather quickly; use smaller, non-journalled partitions instead.)

I don't know if this is OS-related or a hardware design flaw.

In addition, if a vanilla kernel is used with this drive, the system hangs on the udev device scan (2.6.18 ), or the kernel panics and oopses randomly.

---

### Post by DOD1951 on 2006-12-02
Scanner
Canon
Canoscan LiDE 500F
USB connected not recognised by any scanner program

---

### Post by SSBM86 on 2006-12-03
> **kvonb said:**
> If you mean the Asus P4S800MX mainboard, then there must be a problem with your system somewhere, mine works perfectly under both Dapper and Edgy.

I mean P4S8X-MX it not same as P4S800MX that use SiS 661FX chipset P4S8X-MX use SiS 661GX :) 

P4S8X-MX
[http://www.asus.com/products4.aspx?l1=3&l2=12&l3=183&model=494&modelmenu=1]("http://www.asus.com/products4.aspx?l1=3&l2=12&l3=183&model=494&modelmenu=1")

P4S800MX
[http://www.asus.com/products4.aspx?l1=3&l2=12&l3=42&model=199&modelmenu=1]("http://www.asus.com/products4.aspx?l1=3&l2=12&l3=42&model=199&modelmenu=1")

I think the problem is chipset that no reboot fixup found. ;)

---

### Post by vakont on 2006-12-03
The one thing that "burns" me the most is my SATA DVD Burner on my Clevo M570U laptop. The burner model is the HL-DT-ST DVD RAM.

My Western Digital SATA hard drive works nicely though.

One other thing it seems not to recognize is the Chipset Bridge, but things seem to work so far.

I haven't tested the camera, the card reader or the firewire.

---

### Post by John.Michael.Kane on 2006-12-06
This thread is being temporarily locked while the information is transfered to the udsf database.

---

