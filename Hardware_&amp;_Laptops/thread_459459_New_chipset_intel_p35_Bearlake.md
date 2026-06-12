---
title: "New chipset intel p35 Bearlake"
date: 2007-05-30
forum: Hardware &amp; Laptops
---

### Post by sonnet on 2007-05-30
Hi, I just wanna ask if the new chispset Bearlake (northbridge intel p35,southbridge ich9r) is compatible with Ubuntu feisty or in general with Linux kernel.
In particular I want to buy a gigabyte motherboard.

---

### Post by Falcorian on 2007-06-05
It's a question I'd be interested in hearing the answer to as well.

---

### Post by zentagonist on 2007-06-11
same here, I have been unable to find any reviews for this chipset with linux

---

### Post by lns on 2007-06-13
I would definitely like to know as well - I have a server quote with an Asus P5K mobo (contains the Intel P35 chipset) that I want to create an LTSP5 server with, and I need to know hardware compatibility, mainly with the integrated 1GB NIC before I order it.

Thanks!

---

### Post by lns on 2007-06-13
I just got this from a newegg.com motherboard review w/the P35 chipset ( [http://www.newegg.com/Product/Product.aspx?Item=N82E16813121314](http://www.newegg.com/Product/Product.aspx?Item=N82E16813121314) ) - hope this helps a little bit. Maybe we can get some confirmation, or word of an updated BIOS that fixes the NIC issue?

-----
Meh

    Reviewed By: Badtux on 6/9/2007
    Rating + 3Rating + 3Rating + 3Rating + 3Rating + 3 
    Tech Level: high - Ownership: 1 day to 1 week

    Pros: A *lot* of USB ports (12 in all, 6 on the back panel). Two Firewire ports. 5 SATA and one ESATA port. IDE port for my CDR/DVDR. Lots of slots for add-on cards. All supported by Linux except for the network chip, which Intel inexplicably changed the PCI ID on thus the Linux network driver doesn't know about it. BIOS can be updated off of downloaded ISO image burned to CDR (who uses floppies these days?!). Very stable board.
-----

---

### Post by conjur3r on 2007-06-19
> **lns said:**
> I just got this from a newegg.com motherboard review w/the P35 chipset 

How are you going with this motherboard now?  Have you got your NIC working yet?

---

### Post by bosonflux on 2007-06-19
Just for the record, I have a Gigabyte GA G33M-DS2R. It currently only has windows xp and runs flawlessly. My linux box with a 975x chipset was also running flawless when it cratered a few days ago. I was going to replace it with another Gigabyte as above so put in the Fiesty live cd and it will not boot at all. It continuously tries to access the floppy and gives an "unexpected exit" error. I popped in PC OSLinux and it booted just fine, found the network, but missed the sound, both Realtek. Looks like some work needs to be done. I'm probably going to get a p33 or p35 Bearlake anyway, just for the future. Hopefully these issues will be worked out in time.

---

### Post by jcornwall on 2007-06-19
I've just installed Feisty onto an Asus P5K, based on the Intel P35 chipset.

Most stuff seems to be working ok except, as noted above, the sound.

**Update:** This is nonsense, I'd just forgotten to turn on-board audio back on in the BIOS. :D

Works fine but line out is very quiet. I'm tracing some ALSA mailing list posts to find a cause.

---

### Post by conjur3r on 2007-06-20
Thanks for reporting back!  It helps considerably.

According to the output, looks like something unknown related to USB?  How is the USB support there?  Are your external USB devices (thumb drives, mouse, keyboard, etc) working ok?

Have you installed the nvidia drivers yet?  Surprised it came back as unknown as well.

---

### Post by jcornwall on 2007-06-20
> **conjur3r said:**
> According to the output, looks like something unknown related to USB?  How is the USB support there?  Are your external USB devices (thumb drives, mouse, keyboard, etc) working ok?
The USB on this system is a little weird - each boot comes up with a different set of USB hub errors before the subsystem initialises, but it always works regardless.

My Logitech G15 keyboard is fine, MX 700 mouse is fine. I just connected up a Western Digital 80GB USB hard disk and that seems to work too, so I'd say USB is in good shape.

> **conjur3r said:**
> Have you installed the nvidia drivers yet?  Surprised it came back as unknown as well.
Yes, I had to use the nvidia-glx-new package because I have an 8800 GTX in this system. it's quite a new card so I wouldn't worry about the kernel not recognising it - 3D and stuff works just fine.

I've found a post suggesting the quiet sound problem is known and possibly fixed in a new version of ALSA. I'm going to compile it and see!

---

### Post by conjur3r on 2007-06-20
I'm sure this bit of news has made alot of people very happy.  Could you just confirm that your network card works?  An earlier post had a comment left by user suggesting that it didn't work.

You have the motherboard with the one network card not the dual right?

---

### Post by jcornwall on 2007-06-20
> **conjur3r said:**
> I'm sure this bit of news has made alot of people very happy.  Could you just confirm that your network card works?  An earlier post had a comment left by user suggesting that it didn't work.

You have the motherboard with the one network card not the dual right?
Yes, it's the single GigE port board. The network controller works fine. From lspci:

02:00.0 Ethernet controller: Attansic Technology Corp. L1 Gigabit Ethernet Adapter (rev b0)

And ifconfig:

eth1      Link encap:Ethernet  HWaddr 4E:24:56:31:4B:6E
          inet addr:192.168.1.4  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::4c24:56ff:fe31:4b6e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:9339 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8036 errors:0 dropped:0 overruns:0 carrier:1
          collisions:0 txqueuelen:1000
          RX bytes:9528560 (9.0 MiB)  TX bytes:1044526 (1020.0 KiB)

And a quick server to server SCP transfer:

test.wmv                             28%  219MB  23.9MB/s   00:22 ETA

---

### Post by jcornwall on 2007-06-20
And just to update on the sound issue, the newest version of ALSA brings volume back up to normal levels.

So I should expect this will all work out of the box by Gutsy!

---

### Post by jcornwall on 2007-06-21
New update.

I'm seeing system freezes when using the network adapter under heavy loads for a while. Seems to be reproducible so I'll see if it's been fixed in newer kernels and dig up some backtraces if it's not.

**Final update:**. The Attansic network driver is troublesome on systems with 4GB+ of memory. [This patch]("http://lkml.org/lkml/2007/6/24/139") is a temporary workaround and may or may not make it into a production kernel. Works for me.

---

### Post by xanium4332 on 2007-06-23
I've just bought a Gigabyte GA-P35T-DQ6, and can confirm everything works.

No problems with the NIC as of yet, but I haven't had a chance to load it with too much traffic, sound works fine, although some things are a little 'staticy', which does not occur in windows (well at least not after a driver install). SATA and Raid is fine (dmraid has no problems).

So generally things are fine, the sound is prob. more a configuration issue than a problem, and even if it is a problem I can live with it. The boards using 2gb of DDR 3 RAM (which I thought may have caused a problem, but didn't)...

---

### Post by jcliburn on 2007-06-25
> **jcornwall said:**
> New update.

I'm seeing system freezes when using the network adapter under heavy loads for a while. Seems to be reproducible so I'll see if it's been fixed in newer kernels and dig up some backtraces if it's not.

**Final update:**. The Attansic network driver is troublesome on systems with 4GB+ of memory. [This patch]("http://lkml.org/lkml/2007/6/24/139") is a temporary workaround and may or may not make it into a production kernel. Works for me.

An simpler alternative to rolling your own patched kernel exists.  Just add "mem=3000M" to your kernel command line.  This will constrain the kernel to operate within 3GB of RAM and avoid the high mem DMA issue on the L1.

---

### Post by gdp77 on 2007-06-29
> I'm sure this bit of news has made alot of people very happy. Could you just confirm that your network card works? An earlier post had a comment left by user suggesting that it didn't work.

You have the motherboard with the one network card not the dual right?


I am not confirming that. I have the following setup: 

C2D 6600
Gigabyte P35-DS3 (F2 Bios)
XFX Geforce 7900 GT
2x1 GB DDR2 800
1xSATA2 320GB
1xSATA2 80GB
1xSATA SAMSUNG DVD-RW


Everything works fine except the network. The gigabyte NIC is listed in the "hardware info" but seems that it doesn't work. 

Any help on that  would be appreciated.

---

### Post by jcornwall on 2007-06-29
> **gdp77 said:**
> I am not confirming that. I have the following setup: 

Gigabyte P35-DS3 (F2 Bios)

Everything works fine except the network. The gigabyte NIC is listed in the "hardware info" but seems that it doesn't work.
You probably have a different NIC on that from my Asus P5K. What does lspci say?

---

### Post by gdp77 on 2007-06-29
From Gigabyte's manual :

LAN RTL 8111B

---

### Post by SRParda on 2007-07-02
Same network problem with an Intel DP35DP motherboard with Intel P35 chipset.

The network card is an Intel® 82566DC Gigabit Ethernet Controller.

With Ubuntu 7.04 64bit: installation OK  but not  network card installed.

---

### Post by smothepeanut on 2007-07-02
I have the G33 (P35 with graphics) and had to install via the alternate cd and network device didnt detect. I heard somewhere on the line that you needed kernel 2.6.22 which i tried to upgrade to however it didnt work.


I would love so help

---

### Post by digweed on 2007-07-05
i have problem withe network too :(
Gigabyte GA-P35-DS4

---

### Post by gdp77 on 2007-07-06
just follow [these](http://ubuntuforums.org/showthread.php?p=2954153#post2954153) instructions. Find the drivers first from gigabyte's site.

---

### Post by skippy2007_2335 on 2007-07-25
> **jcornwall said:**
> I've just installed Feisty onto an Asus P5K, based on the Intel P35 chipset.

Most stuff seems to be working ok except, as noted above, the sound.

**Update:** This is nonsense, I'd just forgotten to turn on-board audio back on in the BIOS. :D

Works fine but line out is very quiet. I'm tracing some ALSA mailing list posts to find a cause.

jcornwall - I don't have the same luck as you ... not sure what BIOS version you are / were running at install, but my NIC isn't recognized at install.  Same motherboard - P5K from ASUS, and running with 4GB RAM, etc.  

Please let me know if you can give me a couple details on your config, as this is rather puzzling considering your success...

My Feisty image was downloaded today, and is installing fine - just without NIC support.

---

### Post by quokka on 2007-07-25
I also have P5K motherboard and no problems with NIC. Running 64 bit Feisty (Kubuntu) 

System has:

E6420 CPU
2 x NVidia NVS 285 PCI-E graphics cards
1 x NVidia NVS 280 PCI graphics card
1 x Divco Fusion DTB tuner.
2 Gig memory
1 x Western Digital AAJS 160 Gb Sata II disk

lspci output:

```

00:00.0 Host bridge: Intel Corporation Unknown device 29c0 (rev 02)
00:01.0 PCI bridge: Intel Corporation Unknown device 29c1 (rev 02)
00:1a.0 USB Controller: Intel Corporation Unknown device 2937 (rev 02)
00:1a.1 USB Controller: Intel Corporation Unknown device 2938 (rev 02)
00:1a.2 USB Controller: Intel Corporation Unknown device 2939 (rev 02)
00:1a.7 USB Controller: Intel Corporation Unknown device 293c (rev 02)
00:1b.0 Audio device: Intel Corporation Unknown device 293e (rev 02)
00:1c.0 PCI bridge: Intel Corporation Unknown device 2940 (rev 02)
00:1c.4 PCI bridge: Intel Corporation Unknown device 2948 (rev 02)
00:1c.5 PCI bridge: Intel Corporation Unknown device 294a (rev 02)
00:1d.0 USB Controller: Intel Corporation Unknown device 2934 (rev 02)
00:1d.1 USB Controller: Intel Corporation Unknown device 2935 (rev 02)
00:1d.2 USB Controller: Intel Corporation Unknown device 2936 (rev 02)
00:1d.7 USB Controller: Intel Corporation Unknown device 293a (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 92)
00:1f.0 ISA bridge: Intel Corporation Unknown device 2918 (rev 02)
00:1f.2 IDE interface: Intel Corporation Unknown device 2921 (rev 02)
00:1f.3 SMBus: Intel Corporation Unknown device 2930 (rev 02)
00:1f.5 IDE interface: Intel Corporation Unknown device 2926 (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation NV44 [Quadro NVS 285] (rev a1)
02:00.0 Ethernet controller: Attansic Technology Corp. L1 Gigabit Ethernet Adapter (rev b0)
03:00.0 SATA controller: JMicron Technologies, Inc. JMicron 20360/20363 AHCI Controller (rev 03)
03:00.1 IDE interface: JMicron Technologies, Inc. JMicron 20360/20363 AHCI Controller (rev 03)
04:00.0 VGA compatible controller: nVidia Corporation NV44 [Quadro NVS 285] (rev a1)
05:00.0 Multimedia video controller: Brooktree Corporation Bt878 Video Capture (rev 11)
05:00.1 Multimedia controller: Brooktree Corporation Bt878 Audio Capture (rev 11)
05:02.0 VGA compatible controller: nVidia Corporation NV34GL [Quadro NVS 280 PCI] (rev a1)
05:03.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev c0)

```

---

### Post by skippy2007_2335 on 2007-07-26
> **quokka said:**
> I also have P5K motherboard and no problems with NIC. Running 64 bit Feisty (Kubuntu) 

System has:

E6420 CPU
2 x NVidia NVS 285 PCI-E graphics cards
1 x NVidia NVS 280 PCI graphics card
1 x Divco Fusion DTB tuner.
2 Gig memory
1 x Western Digital AAJS 160 Gb Sata II disk

lspci output:

```


02:00.0 Ethernet controller: Attansic Technology Corp. L1 Gigabit Ethernet Adapter (rev b0)


```

Hey quokka - 

Thanks for the info - very interesting as my lspci shows the same for my ethernet, yet it hasn't acquired an address... although, an "ifconfig" does show me that it's working, but only has a loopback address of 127.0.0.1 assigned.  I have tried bringing the adapter down, and back up to see if it would pull an IP over dhcp, but to no avail.  Any thoughts or suggestions as to what i can try next?  

I was reading this link ([http://atl1.sourceforge.net/](http://atl1.sourceforge.net/)) and thought I may need to upgrade my driver based on the comment "*In general, if you want to run a vendor version of the driver and you're using a 2.6.17, 2.6.18, or 2.6.19 kernel, use driver version 1.0.41.0. Note however that NEITHER of the vendor versions will work with kernel 2.6.20 or later*." - but that didn't necessarily mean that the kernel didn't have the version from sourceforge already compiled in.  

So - I'll keep playing, and see what I can find.  Otherwise, any suggestions are greatly appreciated.

EDIT:  I also wanted to mention that I am installing straight ubuntu 7.04 Server x64, so I wonder if the differences could be in the different releases?  Thoughts are appreciated!

---

### Post by quokka on 2007-07-26
Skippy,

I should have added I'm runnin 2.6.21.5 kernel, but it worked the same with the stock Ubuntu kernel. 

2.6.21.5 was installed to get lm_sensors to work.

---

### Post by skippy2007_2335 on 2007-07-26
Ok.... so I found out a few things... first of all, when you get the device showing in lspci, that's probably a good sign to start with.  

Secondly, when you can see the interface exists with an 'ifconfig', you're also probably in a good place.  It turned out that I needed to modify my /etc/network/interfaces file to allow the eth0 device to pull a dhcp address (for now) and all was well.  

Thanks - and sorry for those of you I massively confused based on my few incidents up to this point. All appears well now however... 
:guitar:  - rock on

---

### Post by kraymore on 2007-07-29
i am interested in running feisty on a GA-P35C-DS3R gigabyte motherboard.  are you saying that you got the network and sound working without having to compile a driver for it ?

what changes did you make to /etc/network/interfaces for the network to start working ?  i always do a fresh install with new hardware so i am not sure if i will have to do the same.  

thank you

---

### Post by skippy2007_2335 on 2007-07-29
> **kraymore said:**
> i am interested in running feisty on a GA-P35C-DS3R gigabyte motherboard.  are you saying that you got the network and sound working without having to compile a driver for it ?

what changes did you make to /etc/network/interfaces for the network to start working ?  i always do a fresh install with new hardware so i am not sure if i will have to do the same.  

thank you

Regarding the sound card, since this is a server box, I didn't even attempt to try that - so I can't confirm either way.  Sorry.  

As for the network card, for some reason, during installation it doesn't appear to recognize the card, so it only configured the loopback interface.  I had to modify the file to allow my eth0 interface to obtain a dhcp address (for now, until I'm ready to assign it a permanent one on my network).  

The lines look like this: 

[FONT="Courier New"][COLOR="Blue"]# The loopback network interface
auto eth0 lo

iface eth0 inet dhcp
iface lo inet loopback[/COLOR][/FONT]

Hope that helps you out!  I think the key for me was to find that the lspci did detect my network device, but I knew I didn't have an IP address, so I just figured it out from there... hopefully your situation is similar.

---

### Post by pstate on 2007-07-31
Just to add to this thread.  I have just put together my new system using a Gigabyte GA-P35-DS3R and lastnight I successfully install Feisty Fawn (7.04) without any apparent problems.  Both the onboard NIC and sound worked out of the box.  The only problem I had was loading the Nvidia driver for my 8800 GTS.  After some work I got that to work.  It seem the that repository was missing a library.  Just for reference my rig consists of:

1) GA-P35-DS3R
2) Q6600 (quad)
3) 2GB Ram
4) LG DVD (SATA)
5) Seagate 500GB HD w/NCQ and 16MB cache
6) eVGA 8800 GTS 640MB

Good luck!

---

### Post by fredj on 2007-08-01
I have an Abit IP35 which I have to configure as an XP/Ubuntu dual boot and after many initial
problems with the SATA mode, I have got it working well with both operating systems.

---

### Post by conjur3r on 2007-08-04
I have just recently built a new box and it's working great!  I didn't experience any problems whatsoever.

* Asus P5K Deluxe
* Q6600
* 4G ram
* Pioneer IDE dvdrw
* Asus SATA dvdrw
* 2x320G seagate SATA
* nvidia 8800GTX

Everything works.

---

### Post by lifishing on 2007-08-09
Gigabyte P35 DS3R motherboard  works fine with Feisty.  
   There is an easily fixed problem with on board network card though. For some reason, some boards has NIC deactivated by default. Linux driver doesn't know how to activate it.  You need go to BIOS, in the Integrated Peripherals, choose "On board LAN ROM", enable it. This will activate the  card.  Once your card is activated, this option can be safely **turned off again**.
    Another thing is when you install Windows XP, it can deactivate the NIC when shutting down. Just set  "**Wake-on-lan after shutdown**" to be enabled in Windows driver configuration will solve the problem 
    See [http://gentoo-wiki.com/HARDWARE_RTL8168](http://gentoo-wiki.com/HARDWARE_RTL8168) for detail.

---

### Post by fjf on 2007-08-11
Abit ip35 pro works fine with feisty; I didn't even have to reinstall it from my old computer.  The tricks (from what I've read) seem to be:

-an all-SATA system (hard drive and DVD)
-activate the SATA AHCI mode (not IDE) in the BIOS

Done that, it works just fine.

---

### Post by oneleaftea on 2007-08-13
Hello,

I have the Gigabyte GA-G33M-S2 board, and wondering about a few specific settings. I still have not installed Ubuntu yet, so I wanted to figure a few things out ahead of time.

In the BIOS, there are two SATA settings that I can choose to enable or disable:
- SATA AHCI Mode (currently disabled)
- SATA Port0-3 Native Mode (currently enabled)

It sounds like people have had better luck with Ubuntu and Debian installs with AHCI enabled. However, the Gigabyte manual says that AHCI is for Windows Vista only. If I am running Windows XP (as a dual-boot with Ubuntu), will I have problems setting AHCI to "enable"?

Also, what is the recommended setting for the SATA Native Mode?

Overall, as a complete Ubuntu/Linux newbie, will it be difficult to get Ubuntu Feisty working on this new chipset? I am using all of the integrated features on the board (video, sound, network). I am also all-SATA (dvd-rom and hard drive), and have the IDE controller disabled. I also plan to use the Live CD to install. My only experience so far has been getting Xubuntu working on my wife's T20 Thinkpad.

Thank you very much!

---

### Post by tj.milligan on 2007-08-16
> **pstate said:**
> Just to add to this thread.  I have just put together my new system using a Gigabyte GA-P35-DS3R and lastnight I successfully install Feisty Fawn (7.04) without any apparent problems.  Both the onboard NIC and sound worked out of the box.  The only problem I had was loading the Nvidia driver for my 8800 GTS.  After some work I got that to work.  It seem the that repository was missing a library.  Just for reference my rig consists of:

1) GA-P35-DS3R
2) Q6600 (quad)
3) 2GB Ram
4) LG DVD (SATA)
5) Seagate 500GB HD w/NCQ and 16MB cache
6) eVGA 8800 GTS 640MB

Good luck!

I've got a very similar system that I'll be installing Feisty on:

GA-P35-DS3R
Q6600, G0 stepping (arrives Monday/Tuesday)
2 GB Crucial Ballistix PC6400
XFX 7800 GT (from my old rig--waiting for 8900/9800 series)

Can't wait to try it all out!

---

### Post by mcdee on 2007-08-17
> **fjf said:**
> Abit ip35 pro works fine with feisty; I didn't even have to reinstall it from my old computer.  The tricks (from what I've read) seem to be:

-an all-SATA system (hard drive and DVD)
-activate the SATA AHCI mode (not IDE) in the BIOS

Done that, it works just fine.

Hi,
   Did you install x64?  Also, did you try this with RAID?

Cheers,
Jim.

---

### Post by bimmerd00d on 2007-08-19
After updating to the Gutsy Kernel in Feisty, my NIC works on my intel DG33BU board, which is of similar architecture.

---

### Post by fjf on 2007-08-20
> **mcdee said:**
> Hi,
   Did you install x64?  Also, did you try this with RAID?

Cheers,
Jim.

Nope.  Single SATA HDD, Feisty x32.

---

### Post by calvinandhobbes on 2007-08-20
> **fjf said:**
> Abit ip35 pro works fine with feisty; I didn't even have to reinstall it from my old computer.  The tricks (from what I've read) seem to be:

-an all-SATA system (hard drive and DVD)
-activate the SATA AHCI mode (not IDE) in the BIOS

Done that, it works just fine.I have an Abit IP35 (not the E or the Pro), and my Live CD would not boot with the on board controller set as AHCI (i set it that way because i read to do that here).  Once i set it to IDE, it worked like a champ.  I installed, once it rebooted, it froze right as it started booting.  I changed it back to AHCI, and it worked.  DVD drive seems to work reading CD's just fine.  Need to try to burn a DVD and see how that goes.

---

### Post by laiyf on 2007-08-23
> **pstate said:**
> Just to add to this thread.  I have just put together my new system using a Gigabyte GA-P35-DS3R and lastnight I successfully install Feisty Fawn (7.04) without any apparent problems.  Both the onboard NIC and sound worked out of the box.  The only problem I had was loading the Nvidia driver for my 8800 GTS.  After some work I got that to work.  It seem the that repository was missing a library.  Just for reference my rig consists of:

1) GA-P35-DS3R
2) Q6600 (quad)
3) 2GB Ram
4) LG DVD (SATA)
5) Seagate 500GB HD w/NCQ and 16MB cache
6) eVGA 8800 GTS 640MB

Good luck!

Do you have any problem with the audio? I intend to get a new rig using this motherboard also.

Thanks

---

### Post by BitSmack on 2007-08-25
> **lifishing said:**
> Another thing is when you install Windows XP, it can deactivate the NIC when shutting down. Just set  "**Wake-on-lan after shutdown**" to be enabled in Windows driver configuration will solve the problem

You rock, lifishing!  :guitar:

I'm dual-booting Fiesty and XP, and my Fiesty networking seemed to work at random times...  quite frustrating.  I just discovered that it breaks after I use XP.  I've needed to actually remove power from the MB (not just shut it down) to restore networking to Fiesty (and Gutsy, for that matter).

I'm using the Gigabyte GA-G33M-DS2R, and it must keep some network hardware active even when shut down...

Thanks again!

-bitsmack

---

### Post by espi3d on 2007-08-28
Intel DP35DP motherboard
USB Keyboard genius slimstar
USB trackball
GeForce 8600 GT
2GB RAM

The keyboard doesnt work in live CD nor when installed. It only works on live CD's GRUB.
It doesnt work in local installed GRUB nor in Xorg.

THere's no network, usplash doesnt show up.

I have enabled USB Legacy in bios and that doesnt change.

It could be the keyboard, but usplash? the network card? Meybe I have several problems at the same time. I need help

Anyone with this motherboard or a configuration like this?

---

### Post by swp6499 on 2007-09-03
maybe a little late but anyone wanting to know i have an abit ip35 pro working perfectly with feisty now....like i said maybe a little late but just thought it might be useful to someone...

---

### Post by dsdnkm on 2007-09-15
Have just set up an Intel Dp35dp with core 2 E6750 only problem is the network interface which does not work have not tried to solve it yet have just put a spare 3 com card in for now.

---

### Post by Zenham on 2007-09-16
I can confirm the P5K series works, at least the P5K WS.

I'm updating my newly installed Feisty box right now as I post, with a simple install from the standard CD. I had some problems at first, and here's a copy of some notes I made in another thread, but here's the meat:

Two requirements, or the installer CD (and alternate CD) will fail and leave you stuck at a prompt:

1. Only use a SATA CD/DVD drive, unless you have SATA entirely disabled and are running all drives in IDE mode. 

Edit for clarification: Note that I don't mean you're using a SATA drive in IDE mode here, I mean you must either use both a SATA HD and DVD/CD drive, or an actual IDE HD and CD/DVD (withthe old school 40 pin connector).

Assuming you have SATA devices:
2. In your BIOS, turn on AHCI, and set the SATA mode to "compatible". 

You can just boot off the standard install CD and proceed normally.

This worked fine for me, posting on the box while it updates. Even came up with a working network, no hands required.

---

### Post by pwe on 2007-10-19
hello

i have an abit ip35-e on P35 and 2 SATA disk from Samsung. DVD-RW in with IDE.

so I cant:
-use DHCP (only once ubuntu didit)
- now I cant log in - i have ATA problems ??? i dont know what it is...


thanks!!

---

### Post by Malcy on 2007-11-25
Just to add to this debate, I have set a Gigabyte GA-P35-DS3L board up with both Gutsy and XP. Strangely both OS'es exhibited similar problems!! This is not an easy board/chipset to set up.

With the Gutsy install, all went well and I had no issues with the SATAII HDD and SATA DVD R/W which I expected to. However, the NIC keeps turning itself on and off and on again continiously. The sound works but is very staticy and I was never able to record anything except a lot of background noise with sound recorder or Audacity.

With XP, the NIC exhibited exactly the same behaviour until I resolved all the issues showing in hardware manager, mostly an issue with the SMBUS controller drivers. The sound drivers were a complete pig to install, often showing faults and errors. I have got there eventually but I think that both the Linux and Windows worlds have some work to do on the drivers for this chipset.

---

### Post by benkorn1 on 2007-11-28
I tried installing the 7.10 server i386, and the installer could not find my network card. Has anyone had this trouble. Btw my motherboard is a Asus P5K.

thanks

---

### Post by mrazster on 2007-12-02
I can add another sucessfull P35 installation.
Everything works perfectly well...after I fiddled around with the nic. I had winblows installed a very brief period...to get the nic working in xubuntu, I had to:

[B][I]1. Turn off the computer..turn off the PSU switch..and drain the systm from the current.

2.Turn it on and go back in bios and disable the nic.

3. Do the first step again.

4. Turn it on and enable the nic.
[/I][/B]
Then it was perfectly well detected during the install process.

Hardwareconfig as follow:

Gigabyte GA-P35-DS3
Xeon 3060 (Core 2)
8800GTS 640mb
2x1gb A-Adata 6400 EE
1 Raptor 74gb v.2
2 500gb Samsung T166

---

### Post by Eldamar on 2008-03-14
Judging from all your successes Leaves me scratching my head all the more.  

I've been trying to install the 64bit gutsy with no avail on my ip35 pro sata hdd sata dvd, 8800 gts512, 19" widescreen.  live cd goes to selection screen then no matter what I pick  the screen just goes blank indefinately.  Could be the widescreen?  doubt it.  perhaps the 64bit?..  *shrugs*

---

### Post by marvin1969 on 2008-03-17
I'm trying to configure an Asus P5K-E (no WiFi) with SATA HDD and DVD with a Q6600 quad core.  When I try to partition the drives (1 x 160GB SATA 10K RPM and 1 x 750GB SATA 7200 RPM), I get errors in the consoles (LOTS of errors).

```
Mar 16 22:39:25 ubuntu syslogd 1.4.1#20ubuntu4: restart.
Mar 16 22:39:25 ubuntu kernel: Inspecting /boot/System.map-2.6.20-15-generic
Mar 16 22:39:26 ubuntu kernel: Loaded 24975 symbols from /boot/System.map-2.6.20-15-generic.
Mar 16 22:39:26 ubuntu kernel: Symbols match kernel version 2.6.20.
Mar 16 22:39:26 ubuntu kernel: No module symbols loaded - kernel modules not enabled. 
Mar 16 22:39:26 ubuntu kernel: pa_resize 1: sectors = 1465149168, hpa_sectors = 1465149168
Mar 16 22:39:26 ubuntu kernel: [  131.097148] ata5.01: configured for UDMA/33
Mar 16 22:39:26 ubuntu kernel: [  131.097153] ata5: EH complete
Mar 16 22:39:26 ubuntu kernel: [  131.103024]          res 51/04:08:00:00:00/04:00:57:00:00/f0 Emask 0x1 (device error)
Mar 16 22:39:26 ubuntu kernel: [  131.113130] ata5.01: ata_hpa_resize 1: sectors = 1465149168, hpa_sectors = 1465149168
Mar 16 22:39:26 ubuntu kernel: [  131.124832] ata5.00: ata_hpa_resize 1: sectors = 293046768, hpa_sectors = 293046768
Mar 16 22:39:26 ubuntu kernel: [  131.124836] ata5.00: configured for UDMA/133
Mar 16 22:39:26 ubuntu kernel: [  131.137124] ata5.01: ata_hpa_resize 1: sectors = 1465149168, hpa_sectors = 1465149168
Mar 16 22:39:26 ubuntu kernel: [  131.137128] ata5.01: configured for UDMA/33
Mar 16 22:39:26 ubuntu kernel: [  131.137133] ata5: EH complete
Mar 16 22:39:26 ubuntu kernel: [  131.142658]          res 51/04:08:00:00:00/04:00:57:00:00/f0 Emask 0x1 (device error)
Mar 16 22:39:26 ubuntu kernel: [  131.149102] ata5.01: ata_hpa_resize 1: sectors = 1465149168, hpa_sectors = 1465149168
Mar 16 22:39:26 ubuntu kernel: [  131.156908] ata5.00: ata_hpa_resize 1: sectors = 293046768, hpa_sectors = 293046768
Mar 16 22:39:26 ubuntu kernel: [  131.156912] ata5.00: configured for UDMA/133
Mar 16 22:39:26 ubuntu kernel: [  131.165112] ata5.01: ata_hpa_resize 1: sectors = 1465149168, hpa_sectors = 1465149168
Mar 16 22:39:26 ubuntu kernel: [  131.165116] ata5.01: configured for UDMA/33
Mar 16 22:39:26 ubuntu kernel: [  131.165121] sd 5:0:1:0: SCSI error: return code = 0x08000002
Mar 16 22:39:26 ubuntu kernel: [  131.165124] sdb: Current [descriptor]: sense key: Aborted Command
Mar 16 22:39:26 ubuntu kernel: [  131.165127]     Additional sense: No additional sense information
Mar 16 22:39:26 ubuntu kernel: [  131.165131] Descriptor sense data with sense descriptors (in hex):
Mar 16 22:39:26 ubuntu kernel: [  131.165133]         72 0b 00 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
Mar 16 22:39:26 ubuntu kernel: [  131.165141]         00 00 00 00 
Mar 16 22:39:26 ubuntu kernel: [  131.165145] end_request: I/O error, dev sdb, sector 0
Mar 16 22:39:26 ubuntu kernel: [  131.165153] ata5: EH complete
Mar 16 22:39:26 ubuntu kernel: [  131.166509] sdb: Write Protect is off
Mar 16 22:39:26 ubuntu kernel: [  131.166648]          res 51/04:08:00:00:00/04:00:57:00:00/f0 Emask 0x1 (device error)
Mar 16 22:39:26 ubuntu kernel: [  131.173093] ata5.01: ata_hpa_resize 1: sectors = 1465149168, hpa_sectors = 1465149168
Mar 16 22:39:26 ubuntu kernel: [  131.181008] ata5.00: ata_hpa_resize 1: sectors = 293046768, hpa_sectors = 293046768
Mar 16 22:39:26 ubuntu kernel: [  131.181012] ata5.00: configured for UDMA/133
Mar 16 22:39:26 ubuntu kernel: [  131.189082] ata5.01: ata_hpa_resize 1: sectors = 1465149168, hpa_sectors = 1465149168
Mar 16 22:39:26 ubuntu kernel: [  131.189086] ata5.01: configured for UDMA/33
Mar 16 22:39:26 ubuntu kernel: [  131.189090] ata5: EH complete

```
 (this goes on for a very long way and when I try to partition)

```
Mar 17 14:42:09 ubuntu kernel: [  304.971690] program qtparted is using a deprecated SCSI ioctl, please convert it to SG_IO
Mar 17 14:42:21 ubuntu kernel: [  317.196014] end_request: I/O error, dev fd0, sector 0
Mar 17 14:42:34 ubuntu kernel: [  329.389967] end_request: I/O error, dev fd0, sector 0
Mar 17 14:42:34 ubuntu kernel: [  329.402681]          res 51/04:20:00:00:00/04:00:57:00:00/f0 Emask 0x1 (device error)
Mar 17 14:42:34 ubuntu kernel: [  329.413234] ata5.01: ata_hpa_resize 1: sectors = 1465149168, hpa_sectors = 1465149168
Mar 17 14:42:34 ubuntu kernel: [  329.425646] ata5.00: ata_hpa_resize 1: sectors = 293046768, hpa_sectors = 293046768
Mar 17 14:42:34 ubuntu kernel: [  329.425653] ata5.00: configured for UDMA/133
Mar 17 14:42:34 ubuntu kernel: [  329.437223] ata5.01: ata_hpa_resize 1: sectors = 1465149168, hpa_sectors = 1465149168
Mar 17 14:42:34 ubuntu kernel: [  329.437229] ata5.01: configured for UDMA/33
Mar 17 14:42:34 ubuntu kernel: [  329.437237] ata5: EH complete
Mar 17 14:42:34 ubuntu kernel: [  329.437454]          res 51/04:20:00:00:00/04:00:57:00:00/f0 Emask 0x1 (device error)
Mar 17 14:42:34 ubuntu kernel: [  329.445198] ata5.01: ata_hpa_resize 1: sectors = 1465149168, hpa_sectors = 1465149168
Mar 17 14:42:34 ubuntu kernel: [  329.457590] ata5.00: ata_hpa_resize 1: sectors = 293046768, hpa_sectors = 293046768
Mar 17 14:42:34 ubuntu kernel: [  329.457597] ata5.00: configured for UDMA/133
Mar 17 14:42:34 ubuntu kernel: [  329.469198] ata5.01: ata_hpa_resize 1: sectors = 1465149168, hpa_sectors = 1465149168
Mar 17 14:42:34 ubuntu kernel: [  329.469203] ata5.01: configured for UDMA/33
Mar 17 14:42:34 ubuntu kernel: [  329.469211] ata5: EH complete
Mar 17 14:42:34 ubuntu kernel: [  329.469264] SCSI device sda: 293046768 512-byte hdwr sectors (150040 MB)
Mar 17 14:42:34 ubuntu kernel: [  329.469456]          res 51/04:20:00:00:00/04:00:57:00:00/f0 Emask 0x1 (device error)
Mar 17 14:42:34 ubuntu kernel: [  329.477203] ata5.01: ata_hpa_resize 1: sectors = 1465149168, hpa_sectors = 1465149168
Mar 17 14:42:34 ubuntu kernel: [  329.489554] ata5.00: ata_hpa_resize 1: sectors = 293046768, hpa_sectors = 293046768
Mar 17 14:42:34 ubuntu kernel: [  329.489559] ata5.00: configured for UDMA/133
Mar 17 14:42:34 ubuntu kernel: [  329.501225] ata5.01: ata_hpa_resize 1: sectors = 1465149168, hpa_sectors = 1465149168
Mar 17 14:42:34 ubuntu kernel: [  329.501230] ata5.01: configured for UDMA/33
Mar 17 14:42:34 ubuntu kernel: [  329.501238] ata5: EH complete
Mar 17 14:42:34 ubuntu kernel: [  329.501298] sda: Write Protect is off
Mar 17 14:42:34 ubuntu kernel: [  329.501495]          res 51/04:20:00:00:00/04:00:57:00:00/f0 Emask 0x1 (device error)
Mar 17 14:42:34 ubuntu kernel: [  329.513183] ata5.01: ata_hpa_resize 1: sectors = 1465149168, hpa_sectors = 1465149168
Mar 17 14:42:34 ubuntu kernel: [  329.525484] ata5.00: ata_hpa_resize 1: sectors = 293046768, hpa_sectors = 293046768
Mar 17 14:42:34 ubuntu kernel: [  329.525490] ata5.00: configured for UDMA/133
Mar 17 14:42:34 ubuntu kernel: [  329.537171] ata5.01: ata_hpa_resize 1: sectors = 1465149168, hpa_sectors = 1465149168
Mar 17 14:42:34 ubuntu kernel: [  329.537176] ata5.01: configured for UDMA/33
Mar 17 14:42:34 ubuntu kernel: [  329.537184] ata5: EH complete
```


I've tried the SATA in RAID, IDE and AHCI, Compatible and Write Protect Disabled and retarded the UDMA from 5 to 3 but nothing seems to help.  Any ideas?

thx

---

### Post by king vash on 2008-03-31
My IP-35 worked great once i switched the sata harddrive to AHCI mode

---

### Post by stchman on 2008-03-31
I have a PC using the P35 chipset (Asus P5K) and everything worked out of the box with Feisty.  All I needed was a video driver for the 8800GT card.

---

### Post by ori_ab on 2008-04-06
I recently upgraded my mobo to gigabyte ga-p35-ds3l - everything worked fine with gutsy + hardy but my wifi usb dongle is not working as it should and causes soft lockups. i suspect it has to do with the ich9r on the p35 though 2 other usb drives are working. using 32bit version. (xp works fine).

---

### Post by Efros on 2008-04-06
Just installed 8.04Beta AMD64 Alternate onto my GIGABYTE GA-EP35C-DS3R, with 8Gb of RAM and 2 mirrored RAIDs. After some messing about with disk numbers due to a coexisting windows installation and switching HD boot priorities, everything booted up into 64 bit goodness.

Everything seems to have been picked up including the Nvidia 8600GT, the RAIDed drives were listed as the individual drives that made up the mirrors. files were accessible and all drives were mountable. Compiz needed some kicking about to get it to appear in the menus but as far as I can see all is working.

---

