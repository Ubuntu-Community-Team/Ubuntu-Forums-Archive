---
title: "Intel GMA X4500HD woes (Intel G45 Chipset)"
date: 2008-08-14
forum: Hardware
---

### Post by Croccydile on 2008-08-14
Well I seem to have hit a brick wall trying to get the video to work properly on this board, so I'm going to throw in the towel and see if anyone is in my boat here.

I just got and setup my new [Gigabyte GA-EG45M-DS2H]("http://www.gigabyte.com.tw/Products/Motherboard/Products_Spec.aspx?ProductID=2877") mainboard and Ubuntu 8.04 64-bit and everything works quite well apart from my video troubles.

I expected since the X4500HD is so brand spanking new, that there was not going to be much for driver support... however I took a look at [this page]("http://melchiorre.wordpress.com/2008/07/31/driver-intel-240-deb-package/") which covers the Intel 2.4.0 driver for GMA graphics, however my results were mixed

If I use "intel" for the xorg.conf driver I get the correct resolution, however my cursor is quite garbled as is the entire screen once in a while and there is no DRM, so Compiz is a no-go.

Granted I should not expect much for being so bleeding edge, I'm hoping someone else has run across this as well.  I can use a simple ATI X1300 PCI-E in the 16x video slot for the time being until I have better luck... however kind of defeats the purpose of getting a board with integrated video.

Perhaps some marginally useful info... E8400 processor with 4GB of memory

lspci output
```

00:00.0 Host bridge: Intel Corporation Eaglelake DRAM Controller (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Eaglelake Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Eaglelake HECI Controller (rev 03)
00:1a.0 USB Controller: Intel Corporation ICH10 USB UHCI Controller #4
00:1a.1 USB Controller: Intel Corporation ICH10 USB UHCI Controller #5
00:1a.2 USB Controller: Intel Corporation ICH10 USB UHCI Controller #6
00:1a.7 USB Controller: Intel Corporation ICH10 USB2 EHCI Controller #2
00:1b.0 Audio device: Intel Corporation ICH10 HD Audio Controller
00:1c.0 PCI bridge: Intel Corporation ICH10 PCI Express Port 1
00:1c.5 PCI bridge: Intel Corporation ICH10 PCI Express Port 6
00:1d.0 USB Controller: Intel Corporation ICH10 USB UHCI Controller #1
00:1d.1 USB Controller: Intel Corporation ICH10 USB UHCI Controller #2
00:1d.2 USB Controller: Intel Corporation ICH10 USB UHCI Controller #3
00:1d.7 USB Controller: Intel Corporation ICH10 USB2 EHCI Controller #1
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 90)
00:1f.0 ISA bridge: Intel Corporation ICH10 LPC Interface Controller
00:1f.2 SATA controller: Intel Corporation ICH10 6 port SATA AHCI Controller
00:1f.3 SMBus: Intel Corporation ICH10 SMBus Controller
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)
03:00.0 Multimedia video controller: Internext Compression Inc iTVC16 (CX23416) MPEG-2 Encoder (rev 01)
03:01.0 Multimedia video controller: Internext Compression Inc iTVC16 (CX23416) MPEG-2 Encoder (rev 01)
03:05.0 IDE interface: Integrated Technology Express, Inc. Unknown device 8213
03:07.0 FireWire (IEEE 1394): Texas Instruments TSB43AB23 IEEE-1394a-2000 Controller (PHY/Link)

```

I plan on running MythTV once I get it all setup.

---

### Post by McLogic on 2008-08-15
> **Croccydile said:**
> Well I seem to have hit a brick wall trying to get the video to work properly on this board, so I'm going to throw in the towel and see if anyone is in my boat here.

I am also "in your boat" with the Eaglelake chipset. The drivers for it are not in the 8.04 release. The two missing drivers are rather important: Video and SATA. 

Read the Phoronix review of the x4500HD chipset, they talk a little about getting the system working:
[http://www.phoronix.com/scan.php?page=article&item=intel_x4500hd](http://www.phoronix.com/scan.php?page=article&item=intel_x4500hd)

> **Croccydile said:**
> I just got and setup my new [Gigabyte GA-EG45M-DS2H]("http://www.gigabyte.com.tw/Products/Motherboard/Products_Spec.aspx?ProductID=2877") mainboard and Ubuntu 8.04 64-bit and everything works quite well apart from my video troubles.

I looked at the Gigabyte board, as it is the only x4500HD board that has the ICH10**R** chipset for Intel MatrixRAID, and AHCI support. Unfortunatly, the 16x PCI-E slot is only the speed of a 4x slot. This does not matter if you use the intergrated graphics, and don't have any 8x or 16x cards.

I bought the [Supermicro MBD-C2SEA]("http://www.supermicro.com/products/motherboard/Core2Duo/G45/C2SEA.cfm"), as it has AHCI support on the non-R ICH10 and two 16x PCI-E slots.

> **Croccydile said:**
> Perhaps some marginally useful info... E8400 processor with 4GB of memory. I plan on running MythTV once I get it all setup.

I plan on running MythTV also, with an NTSC ATI/Phillips card. I have a Q9300 and 2GB of memory (DDR3 is expensive).

With 8.10 Alpha 3 you get support for the ICH10, but not working video. I'm currently downloading 8.10 Alpha 4 and that uses the same xorg that they use in the review. I'll post here when I try Alpha 4.

The Phoronix reviewer (Michael Larabel) had to compile xf86-video-intel DDX, Mesa, and DRM (Direct Rendering Manager) code from the respective git master branches. We may have to do the same.

.

[SIZE="4"]**Fix:**[/SIZE]** Refux** was the first to [point out]("http://ubuntuforums.org/showpost.php?p=5821933&postcount=24") that you can turn off the chip features. It will be slow, but it will not crash.
> **refux said:**
> Turns out I've run into a X bug. The workaround is to add:
```
Option "NoAccel"
```
to xorg.conf


---

### Post by Croccydile on 2008-08-17
Oh wow, thats odd about the SATA driver... mine worked without any issue right off the live disc and the installed system.  I enabled AHCI in the bios and the system did not give any complaints.

The 4x graphics slot does not bother me, though.  The SuperMicro board looks rather nice as well but I was not ready to spend that much money on memory... I wanted at least 4GB of ram.  The bill for mainboard/cpu/processor came to just under $400

> With 8.10 Alpha 3 you get support for the ICH10, but not working video. I'm currently downloading 8.10 Alpha 4 and that uses the same xorg that they use in the review. I'll post here when I try Alpha 4.

The Phoronix reviewer (Michael Larabel) had to compile xf86-video-intel DDX, Mesa, and DRM (Direct Rendering Manager) code from the respective git master branches. We may have to do the same.

This is what I am worried about.  As an ex-Gentoo user I'm still getting used to Ubuntu differences, but I royally screwed up my first two attempts at installing trying to get the 2.4.0 binary video driver working right and don't want to hose my machine to where I have to reinstall yet again.

I'm willing to wait for now until the updated packages are in repositories, however if I can find a guide at compiling the Intel/Mesa/DRM drivers I'd be willing to figure it out.

---

### Post by McLogic on 2008-08-17
Yes, the SATA works in 8.10 Alpha 4 and in 8.04 -- my mistake.

The **graphics work with some minor problems**. There are colored horizontal lines, and the wait cursor jumps around at login. The VGA output works fine on my CRT, but does something odd (see bug for more details). 

It works really well with the HDMI-DVI cable on the digital output. Make sure you get the right HDMI-DVI cable, as some cables do not connect all the pins, and some projector DVI cables have USB pins. The main problem that I have had is black VGA (analog) output on my Dell LCD (1702 FP). I can still log in, and switch to virtual terminals (Ctrl-Alt-Fn) but everything is black. 

The Ethernet card (Realtek 8111C) works fine, and it did not work at all in 8.04. It still is reported as a r8169 in the network info box, but who cares as long as it works. It appears that a updated driver has been given the same name; the old r8169 in 8.04 did not support the 8111C, this r8169 driver does.

The sound and onboard IDE/PATA controller also work fine in both 8.04 and 8.10 Alpha 4. I did not test the onboard Firewire/1394, but it was detected as the right TI chip.

I did not test 3D, but 8.10 did run with desktop effects. It would not let me get more then 2 desktops, even when I changed the number in the gnome-panel workspace switcher.

The bugs:
[Horizontal lines on Intel G45 (aka x4500hd) output]("https://bugs.launchpad.net/ubuntu/+bug/258925")
[Black VGA output on Intel G45 (aka x4500hd)]("https://bugs.launchpad.net/ubuntu/+bug/258923")
[Changes in Workspace Switcher preferences do not create more desktops]("https://bugs.launchpad.net/ubuntu/+bug/258933")
[RTL8111C gigabit ethernet chip]("https://bugs.launchpad.net/ubuntu/+source/linux-ubuntu-modules-2.6.24/+bug/212497")

The 8.10 is not ready for prime-time, that is why it is Alpha 4.
The Supermicro board is really nice, and the onboard stuff works, but video support forces 8.10.

---

### Post by Croccydile on 2008-08-18
Hmmm thats good to hear, perhaps I will try DVI and see if I get any difference in video quality.  I have a Dell 2005FPW which fits it ok, but I did notice it did have different keying than other plugs (I'm not terribly familiar with all the DVI port types) and VGA adaptors will not fit.

If not, I suppose I can also wait until 8.10 is released and upgrade my packages then.  I suppose I will be able to do this, I have never had an Ubuntu machine to upgrade to a newer version before to tell. (!)

I did notice major issues with the Realtek r8196 driver, at least with my board I got the dreaded "eth0 watchdog timeout" message quite often, the only apparent solution in the meantime is to simply reboot until it decides to work, which when it does its fine... however if it gets stuck in the timeout loop the only fix for me is to reboot until it catches on.

[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/76489](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/76489) seems to describe the problem I have been facing, as do others.  As you mention it seems to have been repaired in 8.10.

This has been a rather annoying issue at the moment more than the integrated video, since I can at least live with an add-in graphics card for the moment but don't have a PCI-E lan card to make the machine more stable on the lan side.

The perils of having cutting edge hardware... thanks for all the info you have provided also!

---

### Post by niklaskb on 2008-08-24
I also have a Gigabyte GA-EG45M-DS2H.
I've been able to install Ubuntu 8.10 alpha 4 in safe graphics mode. Seems to work fine, except that the text on the login screen is so small that it is unreadable.:confused:

When i install in normal mode then it gets stuck at boot with a blank screen. Occasionally it manages to boot and then everything seems to work fine, including desktop effects. But without HDMI sound.

The installed package xserver-xorg-video-intel sems to be version 2.4.0 but according to the description in synaptics doesn't support 4-series graphics.

Is it possible to download 2.4.1 packages anywhere?

What is planned for next alpha, will it support X4500HD?

---

### Post by Croccydile on 2008-09-05
As a follow up I've also come across this problem

[Slow Samba Performance with R8196 driver]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/161778")

I'll see if I can test that kernel in Hardy, because the mentioned issue with Samba is driving me up the wall, along with the watchdog timeout errors.  *sigh*  I'd like to avoid having to add another hardware band-aid with another add-in card.

The performance is rather abysmal, and my smb.conf file is stripped bare to eliminate any possible config issues... trying to load a few albums into Winamp over the share can take a minute or two, at the blazing speed of a few tens of k/sec.  :(

---

### Post by niklaskb on 2008-09-06
Video seems to work better with 8.10 Alpha 5.
But I still can't get HDMI audio to work....


lspci
00:00.0 Host bridge: Intel Corporation Eaglelake DRAM Controller (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Eaglelake Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Eaglelake HECI Controller (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #4
00:1a.1 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #5
00:1a.2 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #6
00:1a.7 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #2
00:1b.0 Audio device: Intel Corporation 82801JI (ICH10 Family) HD Audio Controller
00:1c.0 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Port 1
00:1c.5 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Port 6
00:1d.0 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #1
00:1d.1 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #2
00:1d.2 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #3
00:1d.7 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #1
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 90)
00:1f.0 ISA bridge: Intel Corporation 82801JIR (ICH10R) LPC Interface Controller
00:1f.2 IDE interface: Intel Corporation 82801JI (ICH10 Family) 4 port SATA IDE Controller
00:1f.3 SMBus: Intel Corporation 82801JI (ICH10 Family) SMBus Controller
00:1f.5 IDE interface: Intel Corporation 82801JI (ICH10 Family) 2 port SATA IDE Controller
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)
03:05.0 IDE interface: Integrated Technology Express, Inc. Device 8213
03:07.0 FireWire (IEEE 1394): Texas Instruments TSB43AB23 IEEE-1394a-2000 Controller (PHY/Link)


aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC885 Analog [ALC885 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC885 Digital [ALC885 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


aplay -L
default:CARD=Intel
    HDA Intel, ALC885 Analog
    Default Audio Device
front:CARD=Intel,DEV=0
    HDA Intel, ALC885 Analog
    Front speakers
surround40:CARD=Intel,DEV=0
    HDA Intel, ALC885 Analog
    4.0 Surround output to Front and Rear speakers
surround41:CARD=Intel,DEV=0
    HDA Intel, ALC885 Analog
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=Intel,DEV=0
    HDA Intel, ALC885 Analog
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=Intel,DEV=0
    HDA Intel, ALC885 Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=Intel,DEV=0
    HDA Intel, ALC885 Analog
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
iec958:CARD=Intel,DEV=0
    HDA Intel, ALC885 Digital
    IEC958 (S/PDIF) Digital Audio Output
[B]hdmi:CARD=Intel,DEV=0
    HDA Intel
    HDMI Audio Output[/B]
null
    Discard all samples (playback) or generate zero samples (capture)


Last part is intresting... how do I select that output?

---

### Post by talz13 on 2008-09-06
I just set up my new pc with a Gigabyte GA-EG43M-S2H that has intel GMA X4500, and haven't been able to set the resolution properly yet.  I'm stuck with a max 1280x1024/60hz. The display and graphics card just show up as "Configured blah blah" in xorg.conf, and in the screen resolution tool under preferences, the monitor is simply "Unknown".  Tried adding modelines to the xorg.conf, but no change.

Since the card apparently isn't supported on hardy's intel driver 2.2.1 whatever it is, I probably shouldn't bother changing it to use intel driver?

I'm running a fresh install of 8.04.1 amd64...

---

### Post by niklaskb on 2008-09-07
> **talz13 said:**
> I just set up my new pc with a Gigabyte GA-EG43M-S2H that has intel GMA X4500, and haven't been able to set the resolution properly yet.  I'm stuck with a max 1280x1024/60hz. The display and graphics card just show up as "Configured blah blah" in xorg.conf, and in the screen resolution tool under preferences, the monitor is simply "Unknown".  Tried adding modelines to the xorg.conf, but no change.

Since the card apparently isn't supported on hardy's intel driver 2.2.1 whatever it is, I probably shouldn't bother changing it to use intel driver?

I'm running a fresh install of 8.04.1 amd64...
Install 8.10 Alpha 5 and it will work.

[http://www.ubuntu.com/testing/intrepid/alpha5](http://www.ubuntu.com/testing/intrepid/alpha5)

---

### Post by talz13 on 2008-09-07
> **niklaskb said:**
> Install 8.10 Alpha 5 and it will work.

[http://www.ubuntu.com/testing/intrepid/alpha5](http://www.ubuntu.com/testing/intrepid/alpha5)

Hmmm... I guess I'll have to do that when the release version comes out!

---

### Post by fusionisthefuture on 2008-09-08
im really interested in buying the asus p5q-em with this chipset, and the x4500HD, which i intend to use.  ive pretty much convinced myself i cant have anything else, but im not going to actually spend the money on it till i hear some news about its linux driver support.  if anyone could do a mini review and list their system specs id be very grateful.  im basically interested in cpu usage during 1080p playback in mythtv.

---

### Post by Croccydile on 2008-09-10
> **fusionisthefuture said:**
> im really interested in buying the asus p5q-em with this chipset, and the x4500HD, which i intend to use.  ive pretty much convinced myself i cant have anything else, but im not going to actually spend the money on it till i hear some news about its linux driver support.  if anyone could do a mini review and list their system specs id be very grateful.  im basically interested in cpu usage during 1080p playback in mythtv.

I'm only gathering from what I've read about the X4500 driver, that HD acceleration seems to depend on the proper alignment of the sun, the moon and the stars to work properly.  At least from reading reports about the device under *Windows* and how you need Vista + HDCP + Cyberlink to get the benefit of the HD acceleration from the chipset.

I'm hoping im incorrect about this.  I can't afford to run an unstable release right now on the system I have in question and will have to wait for stable to try out also.

---

### Post by fusionisthefuture on 2008-09-10
sh!t... not the sun and moon bug

---

### Post by sbergman27 on 2008-09-10
> **fusionisthefuture said:**
> if anyone could do a mini review and list their system specs id be very grateful.

Mini-review:

In my experience with the G43 chipset with X4500 video, on my Gigabyte EG43M-S2H, with a fully updated Intrepid Ibex Alpha 5, X crashes with a backtrace immediately upon start up:

Backtrace:
0: X(xf86SigHandler+0x65) [0x481145]
1: /lib/libc.so.6 [0x7f4846d00120]
2: X [0x4a73ad]
3: X(xf86InitialConfiguration+0x1309) [0x4aaef9]
4: /usr/lib/xorg/modules/drivers//intel_drv.so [0x7f484572089b]
5: X(InitOutput+0x969) [0x46a369]
6: X(main+0x286) [0x4335d6]
7: /lib/libc.so.6(__libc_start_main+0xe6) [0x7f4846ceb466]
8: X [0x432b89]
Saw signal 11.  Server aborting.
Aborted

Hardy won't even install because the G43 sata driver is too new.  The vesa driver sort of works, but all widescreen modes are completely corrupted.  The G43/X4500 hasn't been much fun yet.

---

### Post by fusionisthefuture on 2008-09-10
is the difference between that and the G45 the HD on the end of the x4500HD?, the southbridge, or what?

---

### Post by talz13 on 2008-09-11
> **sbergman27 said:**
> Mini-review:

In my experience with the G43 chipset with X4500 video, on my Gigabyte EG43M-S2H, with a fully updated Intrepid Ibex Alpha 5, X crashes with a backtrace immediately upon start up:

Backtrace:
0: X(xf86SigHandler+0x65) [0x481145]
1: /lib/libc.so.6 [0x7f4846d00120]
2: X [0x4a73ad]
3: X(xf86InitialConfiguration+0x1309) [0x4aaef9]
4: /usr/lib/xorg/modules/drivers//intel_drv.so [0x7f484572089b]
5: X(InitOutput+0x969) [0x46a369]
6: X(main+0x286) [0x4335d6]
7: /lib/libc.so.6(__libc_start_main+0xe6) [0x7f4846ceb466]
8: X [0x432b89]
Saw signal 11.  Server aborting.
Aborted

Hardy won't even install because the G43 sata driver is too new.  The vesa driver sort of works, but all widescreen modes are completely corrupted.  The G43/X4500 hasn't been much fun yet.

It does, in fact install on this board, I just had to play with the sata settings in the bios to get it to recognize my sata dvd drive.  The graphics drivers are NOT good yet (hopefully it'll work well with 8.10 like was mentioned above), so I'm stuck on 1280x1024 on my 1680x1050 monitor for the time being...

---

### Post by jackocleebrown on 2008-09-12
Just installed Intrepid Alpha 5 64bit on HP 6730b laptop with GE45 chipset and X4500MHD. Seems to work pretty well now. Initially had a little trouble with it not waking up from sleep but that seems to be fixed with latest updates. Audio not working at the moment but not sure if this is hardware or pulseaudio config issues. Video working pretty well, including direct rendering, although it is hard to tell how fast it is going because it seems to be syncd to the screen refresh rate so everything reports 60fps irrespective of how hard it is to render. Compiz working much smoother than on my previous laptop with ATI pcie x600 radeon. Now that xorg.conf has disappeared I am not sure how to specify options for the intel driver!

I did manage to boot to the Hardy live CD and partition the disc too before moving on the Intrepid 64bit alpha incidentally.

Looking forward to alpha 6!

Jack.

---

### Post by hippolyte on 2008-09-13
> **talz13 said:**
> It does, in fact install on this board, I just had to play with the sata settings in the bios to get it to recognize my sata dvd drive.  The graphics drivers are NOT good yet (hopefully it'll work well with 8.10 like was mentioned above), so I'm stuck on 1280x1024 on my 1680x1050 monitor for the time being...

You might be able to get the native resolution by adding a modeline manually in xorg.conf. Well ... the funny thing is that, xorg.conf is gone on several Linux distros, including Ubuntu, I guess. You might have to run xorg -configure (of course as root!) to get a suitable one. It should output something in /root/xorg.conf.new that you might be able to use. Copy that file to /etc/X11/xorg.conf. DON'T do that if you already have that file and if it doesn't look silly or empty.

Here's what I do on Unix BSD when I have to replace a monitor and the driver doesn't pick the correct resolution. The method should work on Linux as well.

1) in the device section, the one describing your graphic card/graphic chipset, comment out the Driver line and add that one instead :
Driver "vesa"

2) then start Xorg with "startx" (forgot to mention that you have to do all that in the console, not in X !)

3) Exit X and take a look of /var/log/Xorg.0.log
Does it contain lines like those : 
   (II) VESA(0): Modeline "1680x1050"x0.0  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz)
(II) VESA(0): Modeline "1680x1050"x0.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz)

If so, pick one and write it in a Modes section that you will have to create in /etc/X11/xorg.conf. Mine looks like that for the 22'' LG Flatron I just bought. Yours will look different since we don't have the same monitor : 

Section "Modes"
  Identifier   "Modes[widescreen]"
  Modeline "1680x1050" 146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync
EndSection

4) Now, add the following line to the monitor section which describes your monitor : 
UseModes     "Modes[widescreen]"
Here's how my monitor section looks like :

Section "Monitor"
  Identifier   "LG W2242TQ"
  ModelName    "LG W2242TQ"
  HorizSync    30-83
  Option       "DPMS"
  VendorName   "LG"
  VertRefresh  56-75
  UseModes     "Modes[widescreen]"
EndSection

5) Now you might have to change the Defaultdepth and display subsection of your screen section into something like that ( Identifier, Device and Monitor should match your system, not mine!): 

 Section "Screen"
  Identifier  "Screen DefaultScreen"
  Device      "Geforce 6150"
  Monitor     "LG W2242TQ"
  DefaultDepth 24
  SubSection "Display"
    Depth      15
    Modes      "1680x1050" "1280x1024" "1152x864" "1024x7680" "800x600" "640x480" 
  EndSubSection
  SubSection "Display"
    Depth      16
    Modes      "1680x1050" "1280x1024" "1152x864" "1024x7680" "800x600" "640x480" 
  EndSubSection
  SubSection "Display"
    Depth      24
    Modes      "1680x1050" "1280x1024" "1152x864" "1024x7680" "800x600" "640x480" 
  EndSubSection
  SubSection "Display"
    Depth      32
    Modes      "1680x1050" "1280x1024" "1152x864" "1024x7680" "800x600" "640x480" 
  EndSubSection
  SubSection "Display"
    Depth      8
    Modes      "1680x1050" "1280x1024" "1152x864" "1024x7680" "800x600" "640x480" 
  EndSubSection
EndSection

It will start X with a 24-bit color depth and first try 1680x1050, then 1280x1024, etc in that order.

I had to do that for the Geforce chipset on that mainboard because the nv driver sucks (and we don't use proprietary nvidia drivers on a free and secure system like OpenBSD). But sometimes, a single entry like that one will enforce the 1680x1050 resolution at 60Hz without the need of modelines: 

Modes "1680x1050_60.00"

6) Almost done ... Before starting X, get rid of the Driver "vesa" line and uncomment your driver line.

This is just a generic solution to an Xorg problem, not Ubuntu and not even Linux specific. I cannot guaranty that you will succed and I'm not responsible if you fry your monitor. Getting things to work the hard way might not be in the Ubuntu philosophie. Hope it helps however ...

---

### Post by rstuart4133 on 2008-09-15
I have a Gigabyte Gigabyte GA-EG45M-DS2H motherboard, and am running Debian Lenny AMD64 on it with a 6600 (quad core).  Obviously, I am not running Ubuntu, but if you use the same versions of the packages as I do, you will probably get the same results.

I first tried the 2.6.24 i386 kernel (linux-image-2.6.26-i386_2.6.24).  As others have noted, the Realtek ethernet chip is very iffy in 2.6.24 and in my case the text console had the top line clipped.  These problems were not unexpected, as 2.6.24 doesn't support the G45 chipset.

I then decided to try the 64 bit kernel, so I reformatted and reinstalled.  The installation media again had 2.6.24  (linux-image-2.6.26-amd64_2.6.24) on it, but oddly all aforementioned issues were gone.  Anyway, installation I upgraded to the current Debian Lenny kernel 2.6.26 (linux-image-2.6.26-amd64_2.6.26) and haven't had an issue since.  This is what I would expect, as support for the G45 chipset was only added to the kernel in 2.6.26.  I don't use hardware RAID, and strong suggest none of you do either.  Use the kernels software RAID instead, and it often faster (particularly the RAID5 variants), and is always more reliable than hardware RAID.  (This comment doesn't apply if you have spent more on your RAID controller than you have on your house, of course.  But since we are talking about the onboard RAID controller of a $100 motherboard that isn't the case here.)

Lenny comes with xserver-xorg-video-intel_2.3.2, which I didn't expect to work on the G45.  I didn't actually check.  2.4.0 is supposed to work, but I have seen reports that it crashes the kernel so I wasn't keen to try it.  The current upstream version is 2.4.2.  If has 26k lines of diffs compared to 2.3.2, so it looks like work had continued on it apace.  So I installed xserver-xorg-intel_2.4.2 from Debian experimental.  Joy!  It just worked through HDMI, at 1920x1080p.  The only issue is something smart-**** piece of software seems to of decided I am viewing everything on a TV, and upscaled the fonts to humongous++, so you get this weird effect of tiny icons and huge letters.  But that isn't a driver problem.  Someone, higher up in the driver chain somewhere is decided to be "Helpful".  I will track it down one day.

It became apparent later the driver is not completely stable.  About every one in 10 times you start the X server the machine freezes.  But is definitely usable.  Another issue is I get the occasional screen flicker, but I put that down to pushing the HDMI cable right to its limit.  HDMI is rated for 1920x1080p at 3m, which is what I am using it at.  I suspect if I buy a 1m HDMI cable the problem will go away.  (Be sure to use a cable that conforms to HDMI 1.3.  I have seen stores claiming to stock 5m HDMI cables for $12 or so.  Since such a thing does not exist at any price what they are actually selling is a box with 5m and HDMI on the side, containing a piece of junk.  HDMI cables aren't expensive - $20..$30, but they aren't dirt cheap either.)

There are two outstanding issues as far as I am concerned.  Firstly, I don't know how to access the BluRay acceleration.  Is it supported?  Does it just work?  Do I have to do something?  Its likely exposed via a video4linux driver, but there are no v4l devices seen by 2.6.26.  I seen posts elsewhere that say its unlikely to be ever supported.  That may be the case, as there is probably some tie-in with HDCP.  Sad, but if my 6600 CPU can handle realtime BluRay decoding, it probably doesn't matter.  As as I have to crack the AACS anyway, then I can do the transcoding at the same time so it is probably irrelevant.

Secondly, how does one push audio through HDMI?  The impression I get it is requires ALSA drivers for the chipset, which don't exist, even in the as yet unreleased 2.6.27.  Again not good.  But the analogue sound will be just fine for now.  Unlike the BluRay decoding issue, this will almost certainly be fixed in time.

The bottom line is isn't perfect, as in it doesn't work as well as it does under Windows.  Given the hurdles HDCP puts in the way that may always be the case.  But if you know what you are doing you can make it work well enough now if for a usable HTPC.  I imagine in a 2009 release of Ubuntu it will come as close as it can to "Just Working".  So don't give up hope.

Here is a link with a bit more info:
[http://www.avsforum.com/avs-vb/showthread.php?t=1057866]("http://www.avsforum.com/avs-vb/showthread.php?t=1057866")

---

### Post by refux on 2008-09-15
That a lot for the information, I am buying a Gigabyte G45 board, so everyone keep the feedback coming (for my sake ;).

One completely non-technical commnet, I'm surprised as a AVSFORUM'er that you didn't recommend monoprice for cables! I just checked, HDMI 3.1a compliant 3FT: $2.43

---

### Post by rstuart4133 on 2008-09-15
> **refux said:**
> As a AVSFORUM'er that you didn't recommend monoprice for cables! I just checked, HDMI 3.1a compliant 3FT: $2.43

A couple of reasons.  Firstly, I am a complete newbie at this video stuff, so I don't really qualify as a avsforum'er.  I happened across them in my google searches.  They, along with phoronix, seem to have the best linux video forums.

Secondly, I am from Australia and have never heard of monoprice.  $2.43 for a 1m HDMI 1.3a cable is very cheap.  At that price I'd be looking for someone saying they actually work, or looking for a money back guarantee.  But they aren't analogue, so if the work reliably then they will work as well as the most expensive ones, and there is no point paying any more.

For what its worth, I have since found out more about BluRay acceleration.  It doesn't work now, and is a long way from working.  A lot of software interfaces have to be re-done - from the kernel API's up.  Computer programmers out there can get a feel for the state of play from [this article]("http://lwn.net/Articles/283793/") on LWN.  But Intel is putting a *lot* of effort into making it work, and so Intel's chips are probably going to be the first that actually support BluRay acceleration in a stock kernel.  At this stage it looks like we will see it surface in Xorg 1.6, which should be released some time next year.

As for sound over HDMI, it looks like for someone who knows what is involved it is probably a couple of days work - ie really simple in the scheme of things.  But I can't find any evidence that work is actually happening.

---

### Post by refux on 2008-09-19
I finished building my box last night. The motherboard is a GIGABYTE GA-EG45M-DS2H.

I installed Alpha 6 on it, and everything went wonderfully until the desktop screen came up for the first time, and actually that seemed fine until the desktop top and bottom bars rendered and then the wait cursor just stopped spinning. And that was that, I could still move the cursor around, but the system was unresponsive. Couldn't even break out to a console with ctrl alt f1.

Anyways, that's all I had time for.

---

### Post by refux on 2008-09-19
Turns out I've run into a X bug. The workaround is to add:
Option "NoAccel"
to xorg.conf

Various bugs related to this issue:
ubuntu issue: [https://bugs.launchpad.net/ubuntu/+bug/272157](https://bugs.launchpad.net/ubuntu/+bug/272157)
debian issue: [http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=497976](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=497976)
xorg issue: [https://bugs.freedesktop.org/show_bug.cgi?id=17460](https://bugs.freedesktop.org/show_bug.cgi?id=17460)

---

### Post by baryon1 on 2008-09-20
> **refux said:**
> Turns out I've run into a X bug. The workaround is to add:
Option "NoAccel"
to xorg.conf

Various bugs related to this issue:
ubuntu issue: [https://bugs.launchpad.net/ubuntu/+bug/272157](https://bugs.launchpad.net/ubuntu/+bug/272157)
debian issue: [http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=497976](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=497976)
xorg issue: [https://bugs.freedesktop.org/show_bug.cgi?id=17460](https://bugs.freedesktop.org/show_bug.cgi?id=17460)

Had to register and thank you for the above information!

The system I am running is latest alpha version of Mythbuntu for AMD64 (should be alpha 4). 

The problem I had was that everything appeared to work fine up to the login screen. After login, only thing shown were some horizontal lines. Adding Option "NoAccel" to xorg.conf solved my problems and everything appears to work fine.

Additional information about my setup in case someone is interested:

uname -r : 2.6.27-3-generic
dpkg -l | grep intel :  ii   xserver-xorg-video-intel   2:2.4.1-1ubuntu4   X.Org X server -- Intel i8xx, i9xx display driver

Only modification done to xorg.conf is the above mentioned "option" added in the Device section.

System is built using a Asus P5Q-EM motherboard with a Intel Q9550 processor.

---

### Post by Croccydile on 2008-09-23
Thank you everyone who has replied to this, I've been trying to keep tabs on the issue myself but lack of time forces me to wait until the Intrepid Ibex final packages are out.

It's good to see though that rapid progress is made, understandably bleeding edge hardware would have difficulty like this and that Intel is very forefront of development and support.

---

### Post by thechump on 2008-09-23
FYI, I am not sure if it makes a difference in terms of performance, but I had also previously tried the NoAccel option with success; changing to XAA AccelMethod also works.  But with both of these, I had to turn off XVideo to see any video with mythtv.  

With Alpha6, I turned off DRI and left everything else alone.  Now, everything video related is working great.  With DRI, it seems the X server is stucked in some infinite loop according to the xserver errors.  Unfortunately, my system at home is power off now, so I can't get you those errors.  Anyhow, turning off DRI works around the problem.

For HDMI audio, can anyone confirm whether this is being worked on at all from a source code perspective?  If not, could someone point out to this kernel newbie which part of the driver selects the audio output port?  If need be, I could try digging through it to see what bits need to be flipped.



> **baryon1 said:**
> Had to register and thank you for the above information!

The system I am running is latest alpha version of Mythbuntu for AMD64 (should be alpha 4). 

The problem I had was that everything appeared to work fine up to the login screen. After login, only thing shown were some horizontal lines. Adding Option "NoAccel" to xorg.conf solved my problems and everything appears to work fine.

Additional information about my setup in case someone is interested:

uname -r : 2.6.27-3-generic
dpkg -l | grep intel :  ii   xserver-xorg-video-intel   2:2.4.1-1ubuntu4   X.Org X server -- Intel i8xx, i9xx display driver

Only modification done to xorg.conf is the above mentioned "option" added in the Device section.

System is built using a Asus P5Q-EM motherboard with a Intel Q9550 processor.

---

### Post by refux on 2008-09-26
Well I tried just turning off DRI and X Video in xorg.conf.
x starts up just fine and seems to work ok, but when I launch MythTV it crashes. :(

So now my problem is that while I can launch MythTV with the NoAccel option in xorg.conf, I can't see video or tv :(

I was able to solve the video by changing the mplayer command line setting (in MythTV setup) to not use xv accelleration.
I also tweaked the profiles for TV playback, so it wouldn't use xv either, however still can't see any TV. This may be a set up issue with my 5500 card, so I think I'll try getting xine working first outside of MythTV.

Anyways, that's where I'm curently at, any (helpful :) comments much appreciated.

---

### Post by Modax42 on 2008-09-26
> **McLogic said:**
> I am also "in your boat" with the Eaglelake chipset. The drivers for it are not in the 8.04 release. The two missing drivers are rather important: Video and SATA. 

Read the Phoronix review of the x4500HD chipset, they talk a little about getting the system working:
[http://www.phoronix.com/scan.php?page=article&item=intel_x4500hd](http://www.phoronix.com/scan.php?page=article&item=intel_x4500hd)

With 8.10 Alpha 3 you get support for the ICH10, but not working video. I'm currently downloading 8.10 Alpha 4 and that uses the same xorg that they use in the review. I'll post here when I try Alpha 4.

The Phoronix reviewer (Michael Larabel) had to compile xf86-video-intel DDX, Mesa, and DRM (Direct Rendering Manager) code from the respective git master branches. We may have to do the same.

Thank you so much for the heads-up!  I was just about to buy a new laptop with the X4500 chipset; its a good thing I came across this thread when I did!  Its _very_ interesting that System 76 is currently selling laptops with this chipset on 8.04, seeing as how they're almost certainly not going to work properly.  What are they thinking?

I'm definitely going to wait until these issues have been resolved in 8.10 before I buy my new intel laptop...and it may not be from System76 after all.

---

### Post by cmsj on 2008-09-27
> **rstuart4133 said:**
> I have a Gigabyte Gigabyte GA-EG45M-DS2H motherboard

I have the same board as you


> **rstuart4133 said:**
> It became apparent later the driver is not completely stable.  About every one in 10 times you start the X server the machine freezes.

I see that too sometimes, although it seems to be improving with the Intel driver in Ubuntu Intrepid.

> **rstuart4133 said:**
>  But is definitely usable.  Another issue is I get the occasional screen flicker

What do you mean exactly by flicker? I see very frequent dropout of the HDMI signal. I'm not sure exactly what it is, but the screen goes black and the TV re-syncs and displays the name of the input again.

What's really interesting is that after I've booted Ubuntu it continues to happen in the BIOS, but booting into Windows stops it. In Windows it never flickers.

I'm therefore entirely convinced that it is an issue with the Linux drivers. I filed it here: [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/275152](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/275152)

---

### Post by McLogic on 2008-09-27
> **Modax42 said:**
> Thank you so much for the heads-up!

Thank you. It only took me 3.5 years of UF membership to get one!

> **Modax42 said:**
>  I was just about to buy a new laptop with the X4500 chipset; its a good thing I came across this thread when I did!  Its _very_ interesting that System 76 is currently selling laptops with this chipset on 8.04, seeing as how they're almost certainly not going to work properly.  What are they thinking?

System 76 may have their laptops set to get updates from model-specific repositories.  They could have packages setting the computers up with software rendering, and then switch on the hardware when the drivers are working by updating the package for that computer.

> **Modax42 said:**
> I'm definitely going to wait until these issues have been resolved in 8.10 before I buy my new intel laptop...and it may not be from System76 after all.

While I would like to support small Ubuntu resellers, I have only been buying Thinkpads and Dells. Dell is where I hope to get my next computer -- as soon as they make [a Dell Mini 9 w/ Touchscreen]("http://www.ideastorm.com/article/show/10090337/Touchscreen_Option_For_Dell_Inspiron_Mini__Dell_E__Dell_E_Slim").

I don't have that motherboard and memory any more. I still want a x4500 board in the future, to save on power consumption over a discrete graphics board. I did spend the extra to get the 45nm quad, will probably spend a touch more on DDR3, and bought Western Digital "Green Power" drives, all to lower power consumption.

I really want to see people post any needed info to the bugs -- if they see the bugs on their systems. I can't post logs, as I don't have the board (and have recycled the hard drive).

If you have **[Horizontal lines on Intel G45 (aka x4500hd) output,]("https://bugs.launchpad.net/ubuntu/+bug/258925")** please post!

This one below needs a log posted (again, if you see something similar). This will not get fixed unless someone re-opens it with a log file for similar odd activity.

[Black VGA output on Intel G45 (aka x4500hd)]("https://bugs.launchpad.net/ubuntu/+bug/258923")

---

### Post by fusionisthefuture on 2008-09-27
i just bought mine (asus p5q-em) and im VERY impressed with the work ubuntu's done on it.  this whole chipset/graphics card is all of what, two months old, and i installed ibex alpha 6 on it ~without any trouble~  for all intents and purposes, its as stable as any other ubuntu install that ive encountered right after install.  basically the only issue i have is a bug within mythtv that keeps the backend from starting properly on boot, and im sure a more capable person would have it figured out already.  im getting no video errors, suspend and hibernate work fine, and it automagically setup the correct resolution on my 1920x1200 dell monitor over hdmi, through an hdmi switch.  so far, i know people have been having trouble getting sound through hdmi, but i know analog works, and i think spdif does, but im not sure.  the audio through hdmi isnt supported well in windows either, and its only a matter of time (judging by the way theyre barreling along, it shouldnt be long at all)  im using full desktop effects built into gnome, havent tried any third party stuff yet. 

im running an e7200 underclocked to 1.6 Ghz and undervolted to .85v.  cpu load stays at around 30% for both cores when watching 1080p, 2Gb ram, using 800MB with mythtv running, drawing 50 watts total (for just the box) at the wall, and only 3 watts in suspend.

---

### Post by rstuart4133 on 2008-09-28
> What do you mean exactly by flicker? I see very frequent dropout of the HDMI signal. I'm not sure exactly what it is, but the screen goes black and the TV re-syncs and displays the name of the input again.

No, nothing like that.  As I said, its like its lost vsync.  What should be the top of the image displays in the middle, accompanied by the image tearing.  I am about to try a new cable.  What makes me suspect the cable is the problem gets less when I move it away from sources of interference, like the power and network cables.

---

### Post by refux on 2008-09-28
cmsj what version of ubuntu are you running?

As you may of gathered from my posts above, I'm also running a GA-EG45M-DS2H, and can't get Ubuntu Intrepid Alpha 6 to run unless it's tweaked to "NoAccel". I'm basically just trying to get a working MythTV setup, so anything that can get me pointed in the right direction would be great! :)

---

### Post by cmsj on 2008-09-29
I'm running Intrepid. hardy basically doesn't work on this hardware. I don't have the NoAccel option though, and it works fine for me other than this flickering.
What's breaking for you?

---

### Post by cmsj on 2008-09-29
weird. it's possible that our displays are interpreting the problem in different ways. unfortunately I don't have a DVI monitor available to test that with.

---

### Post by noisymime on 2008-09-30
I've just installed 8.10 on a Gigabyte GA-EG45M-DS2H and found the setup relatively painless. I had to use 'Option "DRI" "false"' to get an X session, but other than that I have a 1920x1080 resolution on a Samsung LCD TV via a DVI->HDMI cable.
The only problem I'm having though is that I have no xvideo (xv)

Xorg log contains the following entry:
```
intel(0): Xv is disabled because it needs 2D accel and AGPGART.
```

Obviously performance without XV (through mplayer at least) is very poor, can't even play SD content.

Is XV actually working for anyone with a 4500HD or is this still in the works?

---

### Post by jackocleebrown on 2008-10-01
Hello,

I have a gma4500HD. Just checked the Xorg logs, I have two messages about xV:

```
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
```

Which looks encouraging and using "gstreamer-properties" the test of xv runs fine.

Later in the log file I get another message:

```
(==) intel(0): Intel XvMC decoder disabled
```

Any ideas what XvMC is? Is this anything to do with xv?

Hope that helps.

---

### Post by McLogic on 2008-10-01
> **jackocleebrown said:**
> Hello,

I have a gma4500HD. Just checked the Xorg logs, I have two messages about xV:

```
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
```

Which looks encouraging and using "gstreamer-properties" the test of xv runs fine.

Later in the log file I get another message:

```
(==) intel(0): Intel XvMC decoder disabled
```

Any ideas what XvMC is? Is this anything to do with xv?


**Xv** (or XVideo) is for overlay and scaling, this is not the same as **XvMC** (or X-Video Motion Compensation) is for motion compensation. They are different steps on the path from video stream to your screen.

Your computer loads the motion compensation extension, but disables the API that lets hardware handle motion compensation. This means that the CPU will handle this work, but in the X-server not in the video-playing program (AFAIK).

So you can play videos fine, but you will be using CPU/software decoding and scaling.


[SIZE="1"]More Info:
X-Video Motion Compensation, or XvMC, is a API in The X Window System which allows video programs to offload motion compensation and iDCT (Inverse Discrete Cosine Transform) portions of MPEG-2 decoding to the GPU hardware [...]

A new video acceleration API is being developed, in an effort lead by Intel. This new API supports more complete offload (VLD) as well as iDCT+MC, and can support acceleration of MPEG-4 ASP (H.263), MPEG-4 AVC (H.264), VC-1/VMW3, as well as MPEG-2.

[http://www.mythtv.org/wiki/index.php/XvMC](http://www.mythtv.org/wiki/index.php/XvMC)
[http://www.freedesktop.org/wiki/Software/vaapi](http://www.freedesktop.org/wiki/Software/vaapi)[/SIZE]

---

### Post by refux on 2008-10-01
> **noisymime said:**
> I've just installed 8.10 on a Gigabyte GA-EG45M-DS2H and found the setup relatively painless. I had to use 'Option "DRI" "false"' to get an X session, but other than that I have a 1920x1080 resolution on a Samsung LCD TV via a DVI->HDMI cable.
The only problem I'm having though is that I have no xvideo (xv)

Xorg log contains the following entry:
```
intel(0): Xv is disabled because it needs 2D accel and AGPGART.
```

Obviously performance without XV (through mplayer at least) is very poor, can't even play SD content.

Is XV actually working for anyone with a 4500HD or is this still in the works?
If you look at [https://bugs.freedesktop.org/show_bug.cgi?id=17460](https://bugs.freedesktop.org/show_bug.cgi?id=17460) you can see there is a guy called Sven who seems to be making steady progress. However he and an intel engineer are working with the new new newest code.
So if you are capable of getting the newest sources of all the X development libraries and drivers, you can get further along.

Thanks to guys like Sven, we'll get some good solid G45 drivers, but probably not until the release after Ibex, whatever they call that.

Personally I'm going to have a go at getting and compiling all the newest stuff, how hard could it be? :)

---

### Post by noisymime on 2008-10-01
> **refux said:**
> 
Personally I'm going to have a go at getting and compiling all the newest stuff, how hard could it be? :)

I started down that road and got completely lost within an hour. The problem is not that you need to compile the intel driver, its that you also need to do xserver, mesa, kernel etc :(

I wonder what the chances of getting a latest build of the driver down before 8.10 releases are? 7 months from now is a long time to wait, especially considering that G45/G43 boards are going to become a lot more common in that time.

---

### Post by McLogic on 2008-10-02
> **noisymime said:**
> I started down that road and got completely lost within an hour. The problem is not that you need to compile the intel driver, its that you also need to do xserver, mesa, kernel etc :(

I could not agree with you more. I switched from Debian to Ubuntu early on, because Ubuntu was trying to work Out-The-Box. **_I want a desktop that works, not a starting point for my own software-customization project_** where I decide how to handle a USB block-storage device when it is plugged in (mount it, ftw), or get video working on a new chipset.

While I am willing to compile my own [desktop] software, it fills me with dread. It is often a huge collection of downloads to get something that is only a small margin better then what you could get out of the repositories. I don't usually mind the work it takes to compile server software.


> **noisymime said:**
> I wonder what the chances of getting a latest build of the driver down before 8.10 releases are? 7 months from now is a long time to wait, especially considering that G45/G43 boards are going to become a lot more common in that time.

If the driver is not working in [[SIZE="4"]today's beta,[/SIZE]]("http://cdimage.ubuntu.com/releases/intrepid/beta/") then it will most likely not work in the release disks. So give it a try:

[http://cdimage.ubuntu.com/releases/intrepid/beta/](http://cdimage.ubuntu.com/releases/intrepid/beta/)


I expect that the updates to 8.10 will include updated Intel Video drivers. The important thing is that people with G45/G43 (x4500 graphics) can boot the LiveDVD/CD to a desktop, install, and then get updates -- all in full graphical modes.

---

### Post by noisymime on 2008-10-02
> **McLogic said:**
> 
I expect that the updates to 8.10 will include updated Intel Video drivers. The important thing is that people with G45/G43 (x4500 graphics) can boot to a desktop, install, and then get updates -- all in full graphical modes.

Unfortunately the xserver-xorg-video-intel package hasn't been updated for the beta :(
Last update to it was on 20/9 whereas the bulk of the G4x fixes were pushed into the xorg driver on 26/9. 

As far as I'm aware, at this stage users with 4500HD cards can install OK, but they will not be able to boot into a graphical environment until a small change (NoAccel or DRI=false) is added to xorg.conf.

---

### Post by refux on 2008-10-02
Yup, I just tried it, just to see if any magic happended. Nope.

---

### Post by noisymime on 2008-10-03
Maybe I spoke to soon. There's just been an update (xserver-xorg_7.4~2ubuntu5) to the xserver-xorg package (Not the intel package) that seems to have made a difference. Not sure what the alterations were as the changelog hasn't appeared yet.

I can now load xorg without a xorg.conf file where previously it would crash and have verified Xv is working via xvinfo. There's a bit of tearing going on with the video playback, but its a lot better than it was earlier. 

:)

---

### Post by McLogic on 2008-10-03
> **noisymime said:**
> Unfortunately the xserver-xorg-video-intel package hasn't been updated for the beta :(
Last update to it was on 20/9 whereas the bulk of the G4x fixes were pushed into the xorg driver on 26/9. 

[...] not be able to boot into a graphical environment until a small change (NoAccel or DRI=false) is added to xorg.conf.
[LIST]
[*]So, how can you have to install it and what do you see on first boot?
[*]How would you describe what happens when you boot off the live disk?
[*]What experience do you have with the computer after using the alternate installer?
[/LIST]

If you can **describe the bugs** you experience, and you can point to the **changelogs**, the changes may make the first round of updates to 8.10 

[COLOR="blue"][SIZE="4"]Perhaps,[/SIZE][/COLOR] if the change is small enough, and it fixes bugs they will add it to the Release Candidate that will be out on October 23rd -- just 3 weeks from today.

---

### Post by noisymime on 2008-10-03
> **McLogic said:**
> 
If you can **describe the bugs** you experience, and you can point to the **changelogs**, the changes may make the first round of updates to 8.10 

The problem is described in detail @ [http://bugs.launchpad.net/ubuntu/+bug/272157](http://bugs.launchpad.net/ubuntu/+bug/272157)
I believe (but am not 100% sure) that the live installer will use the vesa driver so installation with a GUI is not a problem. Upon first boot however, it will attempt to use the intel driver. In my case this results in a cursor appearing (no gdm) before x crashes, at which point the screen goes blank. Eventually the cursor reappears, x crashes and the process begins again without ever actually reaching a usable point.

I've included a comment at the bottom of that bug report showing the exact commits to the intel driver that are for the G45 fixes:
[http://tinyurl.com/4wf63t](http://tinyurl.com/4wf63t)
[http://tinyurl.com/4fpep6](http://tinyurl.com/4fpep6)
[http://tinyurl.com/4pyrxx](http://tinyurl.com/4pyrxx)
[http://tinyurl.com/4owwr2](http://tinyurl.com/4owwr2)

I certainly appreciate everyones efforts in getting this right so thankyou to those working behind the scenes on it.

---

### Post by daahli on 2008-10-04
I have the same problem with my new p5q-em motherboard (x4500 graphics). System freezes on startup.

Any ideas?

---

### Post by daahli on 2008-10-04
Found a temporary solution. Add

Option "NoAccel"

to your device section in /etc/X11/xorg.conf


Unfortunately it's only a temporary fix, because performance is terrible without acceleration. But at least it's no longer crashing.

---

### Post by macoloco on 2008-10-05
Hi Everyone,

I'm not sure if this helps, but I have an Asus P5Q-EM with X4500HD working (mostly fine) with 3D acceleration. I was never able to get the 8.10 alpha cds to work, so I installed 8.04 with just vesa support. Then I upgraded to 8.10 alpha and have been keeping up to date with the releases. I now have the beta version and it works pretty well. The 3D and GLX work pretty well. Every now and then the screen goes off and then back on (similar to when you log out and then log  back in) but it doesn't freeze  or anything like that. I have had problems with the system freezing sometimes when I log out or when I try so switch users, but I'm not sure that's the driver's fault. Here's my xorg.conf if you want to look at it.

```
Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Module"
	Load		"glx"
	Load		"GLcore"
	Load		"v4l"
	Load		"dri"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection
```

Hopefully all the bugs will be ironed out by the time of the release.

JV

---

### Post by McLogic on 2008-10-07
> **macoloco said:**
> Hi Everyone,
I'm not sure if this helps, but I have an Asus P5Q-EM with X4500HD working (mostly fine) with 3D acceleration. [...] upgraded to 8.10 alpha and have been keeping up to date with the releases. [...] The 3D and GLX work pretty well. 

This could help a lot! I don't have my G45 board any more. I will get another one as soon as the driver works.

Try running this:
```
glxinfo | grep rendering
```
Do you get yes?

> **macoloco said:**
> Every now and then the screen goes off and then back on (similar to when you log out and then log  back in) but it doesn't freeze  or anything like that.

If you are seeing this bug ([launchpad]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/275152") and [freedesktop]("https://bugs.freedesktop.org/show_bug.cgi?id=17805")), please comment.
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/275152](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/275152)
[https://bugs.freedesktop.org/show_bug.cgi?id=17805](https://bugs.freedesktop.org/show_bug.cgi?id=17805)

Did you see this when you had VESA running on 8.04 ?

> **macoloco said:**
> I have had problems with the system freezing sometimes when I log out or when I try so switch users, but I'm not sure that's the driver's fault. 

[LIST]
 [*] Do you know what is locking up? 
 [*] Can you get to a virtual terminal and kill/restart X?
 [*] If you switch back to VESA, do you still see these lockups?
[/LIST]

> **macoloco said:**
> Here's my xorg.conf if you want to look at it.

```
Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Module"
	Load		"glx"
	Load		"GLcore"
	Load		"v4l"
	Load		"dri"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection
```

Hopefully all the bugs will be ironed out by the time of the release.

JV

[SIZE="4"]Has anyone else with a G45 board tried running with this xorg.conf on 8.10 beta?[/SIZE]

---

### Post by fusionisthefuture on 2008-10-07
the only problem i have is the horizontal tearing about a quarter of the screen from the bottom, during video playback.  has anyone gotten this to go away yet?

---

### Post by noisymime on 2008-10-07
> **McLogic said:**
> [SIZE="4"]Has anyone else with a G45 board tried running with this xorg.conf on 8.10 beta?[/SIZE]

I'll give this a shot when I get home. 

In case it helps anyone though, the best solution I found was running without a xorg.conf

Board is a Gigabyte GA-EG45M-DS2H running over DVI->HDMI, 1080p.
3D, Xv, DRI are all running fine without xorg.conf on 8.10 Beta (With all updates). 

The only problem I'm seeing is tearing when playing any video (MPEG2, AVC etc). Tearing is multiple horizontal lines randomly appearing and disappearing rather than the single line described above. Video is quite watchable, but the problem is noticeable, particularly under high motion.

---

### Post by armocasio on 2008-10-08
Please be patient and detailed, I am a newbie. Thanks.
Well here it goes.  My hardware:
Toshiba A305-S6872
Intel Centrino Dual Core 2 2.00 GHz
3 Gb ram
Chipset GM45
Video X4500HD
Display SEC Samsung (as reported by SUSE Enterprise)

I tried to boot once or twice, I&#7743; trying to install Ubuntu last version in 64 bit but it does not even boot, I changed the parameter in the bios for sata to compatibility.  I am not sure if I could boot that time, I was so frustrated I began to try different distributions, by the way the net card does not work either. Bad r8169 module?, Frustrated I found that Debian and openSUSE activated my net card so I proceeded.  I selected openSUSE because it is easy to configure, as Ubuntu.  That is why I wanted Ubuntu in my laptop, I have it already in my desktop.  Well I found out the following:
If you download the latest kernel from the corresponding distribution and boot the installation with boot option vga=0x317 it may work for you.  Then the OS´s graphics module must have to be configured with these parameters:

[B]Card = Intel IGD
Monitor = your make, model and type (LDC or CRT)
Activate DPMS
Diagonal Aspect Ratio = 4/3 or 16/10 depending if it is windscreen or not
Sync (very important) = specified by your manufacturer specs. Usually once you enter graphics mode, it will setup automatically.[/B]

Also I found useful information at this URL:

[B][http://www.phoronix.com/scan.php?page=article&item=intel_x4500hd&num=2](http://www.phoronix.com/scan.php?page=article&item=intel_x4500hd&num=2)

[/B]

I hope this will work, and remember I am a newbie so forgive me if I made any mistake and help me not to make it again.  I am open to suggestions and always willing to learn.

Thanks

---

### Post by Croccydile on 2008-10-08
Another follow up since I started this whole mess... I went ahead and decided to reinstall using Intrepid Ibex Alpha 6 just over a week ago in an attempt to help out with testing.

Oddly enough, everything works just fine now for me.  The only modification I had to do to xorg.conf is specify the "intel" driver and nothing else.  I *did* originally experience the "black login screen" until I updated to the latest packages, and its been fairly smooth sailing SO FAR.  Compiz works ok, 3D works ok, video works ok.  I'm using analogue VGA output.

A big thanks to those working on this problem!

> **armocasio said:**
> I changed the parameter in the bios for sata to compatibility.  I am not sure if I could boot that time, I was so frustrated I began to try different distributions, by the way the net card does not work either. Bad r8169 module?

If you are using Hardy Heron, this is a known problem with the r8169 driver in the kernel it uses.  The card will often not work at all and when it does, its very flaky.  I had this problem and reported to the buglist over the alpha kernel, which seems to fix it.  I have NOT had the issue anymore after Intrepid Ibex Aplha 6 and I'm considering it to have been mended by the kernel team.

If you have trouble booting make sure you set SATA to AHCI otherwise it *will not work properly* with ICH10.  (I dont know if non-AHCI works in Intrepid Ibex, I didnt want to try)  Ideally you should have it set to AHCI anyways since the newer sata drivers are focused around this model.

---

### Post by abandonow on 2008-10-08
It does not work for me. 

I'm running 8.10 beta, with 2.6.27-6-generic. Intel drivers 2.4.2.

Its hooked up to a 42" lcd full-hd tv trough dvi.

Tried all the above, I have to disable hw acceleration, then it runs stable. When I enable it, it sometimes run for a while and then freeze (sometimes hardlocking the box).

Everything else seems to be working ok (sound etc.)

Here is the config file I use, with hw axx disabled.

```

Section "Monitor"
       Identifier      "Toshiba42"
       VendorName      "Toshiba"
       ModelName       "42X3000PG"
       Option          "IgnoreEDID"
       VertRefresh     23-61
       HorizSync       15-68
       ModeLine		   "1080p" 148.50  1920 2448 2492 2640  1080 1084 1089 1125 +hsync +vsync
       ModeLine        "720p" 27.00  720 732 796 864  576 581 586 625 -hsync -vsync
       ModeLine		   "480p" 25.20  640 656 752 800  480 490 492 525 -hsync -vsync
       #DisplaySize             320 180
       DisplaySize            487.68 274.32
EndSection

#Modeline "1920x1080"x0.0  148.50  1920 2448 2492 2640  1080 1084 1089 1125 +hsync +vsync (56.2 kHz)
#Modeline "720x576"x0.0   27.00  720 732 796 864  576 581 586 625 -hsync -vsync (31.2 kHz)
#Modeline "640x480"x0.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)

Section "Device"
       Identifier  	"Intel GMA X4500HD"
       Driver      	"intel"
       VendorName  	"Intel"
       BoardName   	"G45 [Intel GMA X4500HD]"
       BusID       	"PCI:0:2:0"
       
       Option  		"NoAccel" "true" #temp fix for 45g problemer.
       #Disable or enable acceleration.  Default: acceleration is enabled.
       
       Option 		"SWCursor" "true"
       #Disable or enable software cursor.  Default: software cursor is disable and a hardware cursor is used  for  configurations
       #where the hardware cursor is available. 
       
       Option 		"Tiling"  "true" 
       #This  option  controls  whether memory buffers are allocated in tiled mode.  In most cases (especially for complex rendering,
       #tiling dramatically improves performance.  Default: enabled.
       
       Option 		"DRI" "true"
       #Disable or enable DRI support.  Default: DRI is enabled for configurations where it is supported.
       
   
       Option 		"XVideo" "true"
       #Disable or enable XVideo support.  Default: XVideo is enabled for configurations where it is supported.

       Option 		"Legacy3D" "true"
       #Enable support for the legacy i915_dri.so 3D driver.  This will, among other things, make the 2D driver tell libGL to load
       #the 3D driver i915_dri.so instead of the newer i915tex_dri.so.  This option  is  only  used  for  chipsets  in  the  range
       #i830-i945.   Default  for  i830-i945  series:  Enabled.   Default for i810: The option is not used.  Default for i965: The
       #option is always true.

       Option "AccelMethod" "EXA"
       #Choose  acceleration architecture, either "XAA" or "EXA".  XAA is the old XFree86 based acceleration architecture.  EXA is
       #a newer and simpler acceleration architecture designed to better accelerate the X Render extension.  Default: "EXA".

       Option "ModeDebug" "true"
       #Enable printing of additional debugging information about modesetting to the server log.
EndSection

Section "Module"
	   Load "glx"
	   Load "dri"
	  # Load "GLcore" # addon fra forum
	   Load "v4l"	# addon fra forum
EndSection

Section "DRI"
	   Mode 0666
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
      	DefaultDepth    24
        DefaultFbBpp    32 #1080p instead of 1080i

	SubSection "Display"
                Depth           24
                FbBpp           32
        EndSubSection 
EndSection

```

---

### Post by macoloco on 2008-10-09
In response to McLogic:

- The direct rendering returns yes

- Thanks for the links to the bug reports, that's exactly what I'm seeing and I made a comment on it in launchpad.

- As far as the lock up when I log out sometimes, it's a complete system freeze. The Xserver goes down as it normally does when you switch a user, but it never comes back up and the computer is completely locked - no keyboard response (numlock or capslock become dead). I have not tried the vesa driver long enough to see if that makes any difference.

---

### Post by thechump on 2008-10-09
Anyone having audio problems with beta1?  Regardless of what I do with alsamixer, I can't get any audio to work...whether it's myth or other applications.  I definitely had this working with the last alpha release but had to unmute the appropriate channels in alsamixer.  

Anyways, I was going to give up on all the accelerated playback and try to see if using the coreavc codec would speed things up to an acceptable level.  I am already using it with great results on another machine running 8.04.  But before patching the mythtv source to support it, I was going to make sure everything else was fine first...then this audio thing came up...

---

### Post by abandonow on 2008-10-09
Take a look [here (http://alsa.opensrc.org/index.php/DigitalOut)]("http://alsa.opensrc.org/index.php/DigitalOut") and try to test it with the aplay command.

I have had some issues getting sound to work in xfce, but everything works fine in gnome and fluxbox (dont ask me why). Currently sticking with gnome anyways.

I have yet not gotten any sound over dvi, but I can use the s/pdif.

---

### Post by jackocleebrown on 2008-10-09
@thechump:

I had alsa problems but fixed it with the help of this guide here:
[http://gentoo-wiki.com/HP_Compaq_6730b](http://gentoo-wiki.com/HP_Compaq_6730b)

> "options snd-hda-intel model=laptop" in modprobe.conf and reboot solves, "modprobe snd-hda-intel model=laptop" didn't (possibly because modprobe on loaded module doesn't mean "reload") 

After this all works fine. Might be relevant if you are using a laptop.

Cheers, Jack.

---

### Post by thechump on 2008-10-10
I tried both with the sound issue with no luck.  I was running the mythbuntu beta, and it defaulted to alsa...that didn't work.  I wiped the whole system and went to the standard ubuntu gnome desktop which uses pulseaudio...that didn't work....disabled pulseaudio there, still didn't work.  Anything I should try?

---

### Post by thechump on 2008-10-10
I might have stumbled on something major with our dear video problem.  Let's recount my journey:  

1) System froze for every sort of install until Alpha5.  With Alpha5, I was able to install and boot and played around with the system with the DEFAULT xorg.conf with no issues.  Seemed acceleration worked OK...so I posted earlier that turning off DRI works....well, that turned out to be false cuz my system started freezing again later.  Setting NoAccel to true works around that...

2) With Beta1, I installed the mythbuntu distro.  Install work fine but ran into freezing/crash problems.  Again, NoAccel works around it.

3) Due to not being able to get any sort of audio to work, someone suggested that the problem may be with XFCE.  So tonight I wiped out the mythbuntu install and went to the desktop version of Beta1.  After install, I updated everything including the kernel so to get the e1000 driver back.  Guess what?  X works perfectly fine without any modification to the default xorg.conf.  I must have rebooted over 20 times just to see because I got a forced fsck of my filesystem on one of the reboots because it's been so many reboots.  Every time, the default xorg worked perfectly.  So wow!  Then I proceeded to install the mythfrontend package.  Ran mythfrontend without rebooting and things seem to work great other than no audio still.  On my ATSC channel, I saw no artifacts at all!  Then I started watching a mpeg4 file and ran into some problems.  The man pages says XvMC is not turned on by default...so i modified xorg.conf to do so.  For the heck of it, I rebooted at that point.  After this point, my X session freezes everytime I tried to login in.  Went into failsafe/rescue modes and got rid of the XvMC configs and still ran into the same problem.  Now, the only way to fix it is to use the NoAccel workaround.  This brought me back to my previous one bout of success and it seemed to go this way too.  

...so, is there something in the mythtv package that's messing with the X server?  

Anyways, two things that can be tried from here on:
  1) Remove all the related mythtv packages and see
  2) Wipe the whole thing and reinstall everything except mythtv and see

Unfortunately, I probably don't have time to play with this again until Sunday night at the earliest.  If someone is got time twiddling away, could they try this out?

---

### Post by Landris on 2008-10-10
I'm having the same freezing issues with the current Beta updated to the latest packages, and only NoAccel helps. No MythTV installed yet because I figured there was no point until I got this working properly. I had to install from the alternate because the LiveCD froze when it got to the desktop. I tried the Fedora 10 Beta Gnome LiveCD and while it got to the desktop once, every time after it froze, so there seems to be something a bit inconsistent with this problem.

---

### Post by thechump on 2008-10-10
Yes, I've never been able to get the LiveCD option to install also; but the GUI install works fine with the desktop CD if you choose the "install" option directly rather than going to LiveCD first.

---

### Post by abandonow on 2008-10-10
Is there anyone who has successfully run X with hw acceleration more than 30 minutes? Anyone who has Intel GMA X4500HD, and dont have any problems?

If so, please post your hw info, and xorg file (+other usefull hints).

---

### Post by macoloco on 2008-10-10
> **abandonow said:**
> Is there anyone who has successfully run X with hw acceleration more than 30 minutes? Anyone who has Intel GMA X4500HD, and dont have any problems?

If so, please post your hw info, and xorg file (+other usefull hints).

I have an Asus P5Q-EM with an intel X4500HD chipset and its working (check my post on page 5, #50). You can try what I did, which was installing 8.04 and then do a distro upgrade to 8.10 beta.

---

### Post by abandonow on 2008-10-10
Thank you for the reply, and Ive read your post. But I cant see why installing 8.04, and then updating to the newest is any different from just installing 8.10 beta.

Do you know why, and if you do, can you elaborate?

---

### Post by daahli on 2008-10-10
Has anybody been able to get the graphics working on Hardy? 

I have a P5Q-EM motherboard and the ethernet driver is incredibly flaky in Intrepid, pretty much non-usable (but it works in Hardy).

---

### Post by Landris on 2008-10-10
> **thechump said:**
> Yes, I've never been able to get the LiveCD option to install also; but the GUI install works fine with the desktop CD if you choose the "install" option directly rather than going to LiveCD first.

That didn't work for me, it froze too.

I'm starting to wonder if it has to do with what resolution we're outputting at. Mine is outputting to an HDTV at 1920x1080p@60Hz, 24 bit.

---

### Post by abandonow on 2008-10-11
Anyone of you guys running 64bit ubuntu, is that an issue with G45?

---

### Post by Landris on 2008-10-11
Yes, I am running 64 bit.

---

### Post by abandonow on 2008-10-11
This is very weird. I just reinstalled xubuntu 8.10 beta, and now it works out of the box. Currently watching fullscreen movies with no problems videovice (i dont have sound for some reason).

This is the very same cd I installed earlier on, and then X crashed.
> mb@MediaBOX:~$ glxinfo |grep rendering
direct rendering: Yes


Haven't rebooted more than the one reboot after the install.

Edit:
- Sound fixed. Just had to check of for the digital output in the mixer.
- Currently running dist upgrade.
- Upgraded intel driver to 2.4.2
- Box hard freezed on first boot. New reboot, and X is up and running with hw axx.
- Videos get a horizontal line running down the screen, a little annoying.
- And X crashed during playback. :/

Looks like things didnt work out :(

---

### Post by lrc3 on 2008-10-11
I have KUbuntu 8.10 Beta build installed on my ASUS P5Q-EM. I am required to use the NoAccel Option, but I have no sound problem,

I'm trying to clean the system and reinstall ( G) ubuntu using the latest daily-build, but it always suck on the first graphic screen.

---

### Post by anthonyJC on 2008-10-12
I've got 3D and XAA working, but cannot get EXA. Remove   :
```

Option  "NoAccel" "True"


```
- that is required for it to work at all. Replace with:
```

  Option "AccelMethod" "XAA"

```
I would expect this to give acceleration of 2D and 3D without any further work.

If it does not, FYI, I am using xf86-video-intel git today at commit point 6cb4150160bb1e1365773561fb53294ad9248a0e. [2008-10-12 13:17:35] - xf86-video-intel is currently in beta, Ubuntu Intrepid already has the latest stable !
```

Module intel: vendor="X.Org Foundation"
129:    compiled for 1.5.1, module version = 2.4.97

```
I noticed it incorrectly detects UMA size, when my bios was 128 it was using 256. The xf86-video-intel beta appeared to leave the GPU in a better state after the driver exited. To install  **Kubuntu** Intrepid ,  select the second boot option, to launch the installer ( not the livecd) then when the installer fails to start up after X started, kill the xserver and make the changes to the xorg.conf, and then startx.

---

### Post by abandonow on 2008-10-12
If you remove the NoAccel line, I think it still will be enabled because that acceleration is on by default.

---

### Post by McLogic on 2008-10-13
> **abandonow said:**
> 
- Videos get a horizontal line running down the screen, a little annoying.

Wait that can't be true. Unless your monitor is turned sideways so that a line "down" the screen is horizontal.

Did you mean that the line is horizontal, but it moves down the screen?

---

### Post by lrc3 on 2008-10-13
```

  Option "AccelMethod" "XAA"

```


This works!!! Enjoy~

---

### Post by abandonow on 2008-10-13
> **McLogic said:**
> Wait that can't be true. Unless your monitor is turned sideways so that a line "down" the screen is horizontal.

Did you mean that the line is horizontal, but it moves down the screen?


Correct! English is not my first language, so things may look a little weird sometimes. :)

---

### Post by abandonow on 2008-10-13
> **lrc3 said:**
> This works!!! Enjoy~

Could you (or anybody that got hw acceleration working) without crashes publish their whole xorg.conf file? And state witch versions you are running (ubuntu version, intel driver, etc.)

Thx. :)

---

### Post by noisymime on 2008-10-13
> **abandonow said:**
> Could you (or anybody that got hw acceleration working) without crashes publish their whole xorg.conf file? And state witch versions you are running (ubuntu version, intel driver, etc.)

I've got acceleration working with no xorg.conf. I had nothing but problems when I was was using the xorg.conf so in the end I just deleted it and low and behold, things just worked. Mobo is a Gigabyte: GA-EG45M-DS2H. Currently running 8.10 Beta 1 with all updates.  

I've attached a copy of my xorg log in case it helps. 
 
[ATTACH]88169[/ATTACH]

---

### Post by Plexor on 2008-10-13
Anyone figure out how to get full 3d support enabled yet?

I'm hoping I don't have to wait for the ubuntu 2.6.28 kernel release.

I have X4500MHD, running updated Intrepid beta on HP Compaq CQ20-128TU notebook
```

$ uname -r
2.6.27-7-generic

$ glxinfo | grep direct
direct rendering: Yes

$ glxinfo | grep OpenGL
OpenGL vendor string: Tungsten Graphics, Inc
OpenGL renderer string: Mesa DRI Mobile Intel® GM45 Express Chipset 20061102
OpenGL version string: 1.4 Mesa 7.2
```

---

### Post by Roto314 on 2008-10-14
I've got HW acceleration working (it works with or without an xorg.conf; I didn't really have to do anything to make it work.)  It has some problems, though.  

I'm getting lines across some of my windows.  The lines are somewhere around 1000 pixels long, don't necessarily start at the left edge of the window, and wrap around to the next line when they hit the end of the window.  They're mostly black, with a fairly uniform pattern of colored pixels.  They move with the window they're in when I drag it around.  Having desktop effects turned on makes them more numerous and frequent, but they don't go away altogether when it's off.  I've yet to see them when using XAA acceleration, though, but I can't seem to get any Xvideo support under XAA.

I'm also experiencing some pretty bad tearing.  It's quite noticeable when dragging windows around quickly.  It also makes watching video pretty intolerable.  HD content plays back smoothly with no dropped frames, but it's clearly not synchronized with the vertical refresh.  I can use mplayer's gl2 output with standard def. video and the tearing goes away, but it can't handle HD.

---

### Post by McLogic on 2008-10-15
> **Roto314 said:**
> I'm getting lines across some of my windows. [...] They're mostly black, with a fairly uniform pattern of colored pixels.  They move with the window they're in when I drag it around.  Having desktop effects turned on makes them more numerous and frequent, but they don't go away altogether when it's off.  I've yet to see them when using XAA acceleration, though, but I can't seem to get any Xvideo support under XAA.

I think you are seeing this bug:
[Horizontal lines on Intel G45 (aka x4500hd) output]("https://bugs.launchpad.net/ubuntu/+bug/258925")

It sounds like you have a better description of the lines. Perhaps you should post to the bug?

> **Roto314 said:**
> I'm also experiencing some pretty bad tearing.  It's quite noticeable when dragging windows around quickly.  It also makes watching video pretty intolerable.  HD content plays back smoothly with no dropped frames, but it's clearly not synchronized with the vertical refresh.  I can use mplayer's gl2 output with standard def. video and the tearing goes away, but it can't handle HD.

Is this the same thing that abandonow is seeing?

> **abandonow said:**
> 
- Videos get a horizontal line running down the screen, a little annoying.
- And X crashed during playback. 

Is the line the lack of synchronization?

---

### Post by andreiashu on 2008-10-15
Same GA EG45M-DS2H motherboard and same problems here. I just bought a system with this mb and i was ready to full switch to Ubuntu (from Windoze).
1. With 8.04 my maximum resolution was 1600x1200 (on a 24" monitor :( )

2. With 8.10 i have the optimal 1920x1200 resolution with the XAA option in xorg.conf

I really hope the developers get this fixed soon.

---

### Post by Roto314 on 2008-10-15
> **McLogic said:**
> I think you are seeing this bug:
[Horizontal lines on Intel G45 (aka x4500hd) output]("https://bugs.launchpad.net/ubuntu/+bug/258925")

It sounds like you have a better description of the lines. Perhaps you should post to the bug?

Yes, that bug sounds exactly like the issue I'm having.  I'll post my description of the lines to the bug when I get a chance.

> **McLogic said:**
> Is this the same thing that abandonow is seeing?

Yeah, sounds like the same thing.  Certain 3D accelerated objects seem to be properly synchronized, but most of the user interface and Xvideo certainly are not.

---

### Post by abandonow on 2008-10-15
Indeed, sounds like the same thing. I have also disabled hw cursor, as an temporary fix for the cursor bug.

---

### Post by Landris on 2008-10-18
Could those people for whom it is working without needing the "NoAccel" or "AccelMethod" "XAA" options post their output resolution? Because it's still not working for me, and I'm wondering if it's because I'm outputting at 1080p.

---

### Post by noisymime on 2008-10-19
> **Landris said:**
> Could those people for whom it is working without needing the "NoAccel" or "AccelMethod" "XAA" options post their output resolution? Because it's still not working for me, and I'm wondering if it's because I'm outputting at 1080p.

Mine is running fine with no xorg.conf at 1080p. I posted my xorg log file on the previous page showing the resolution setting/modelines. Interface is DVI->HDMI, Samsung TV as display.

---

### Post by andreiashu on 2008-10-19
> **Landris said:**
> Could those people for whom it is working without needing the "NoAccel" or "AccelMethod" "XAA" options post their output resolution? Because it's still not working for me, and I'm wondering if it's because I'm outputting at 1080p.
I'm running 1920x1200 through DVI on a Samsung SyncMaster 245B plus with the XAA option in xorg.conf

---

### Post by andreiashu on 2008-10-19
With the XAA option enabled i tried to use the "solid" color with some transparency for the top panel but unfortunately after some tine (less than 5 min) ubuntu freezes.
I'm using the latest intrepid.

---

### Post by Landris on 2008-10-19
> **noisymime said:**
> Mine is running fine with no xorg.conf at 1080p. I posted my xorg log file on the previous page showing the resolution setting/modelines. Interface is DVI->HDMI, Samsung TV as display.

I tried running it with no xorg.conf but no luck. I am outputting from the HDMI port though, but that shouldn't make a difference I wouldn't think.

---

### Post by abandonow on 2008-10-19
I tried the same earlier (also outputing trough hdmi), but no luck here either. Im currently running with the alternative hw acceleration option in xorg.conf

---

### Post by McLogic on 2008-10-20
> **abandonow said:**
> [...]
- Upgraded intel driver to 2.4.2
- Box hard freezed on first boot. New reboot, and X is up and running with hw axx.
- Videos get a horizontal line running down the screen, a little annoying.
- And X crashed during playback. :/


And

> **andreiashu said:**
> XAA option enabled [...] after some tine (less than 5 min) ubuntu freezes.
I'm using the latest intrepid.

[It looks like we will [SIZE="4"]**not** have this fixed for the 8.10 release[/SIZE]. I doubt they will update all the components needed. Take a look at the posting in the bug this is related to:]("https://bugs.launchpad.net/ubuntu/+bug/272157")

[QUOTE=Bryce Harrington]
Unfortunately, git tip of -intel is not easy to pull at the moment, since it has dependencies on git-tip versions of libdrm, mesa, and perhaps more, so its a non-trivial amount of work, that would bring an indeterminate amount of risk of introducing regressions for other users.[/quote]

Millions of units will ship with x4500 graphics in the next 6 months...

---

### Post by andreiashu on 2008-10-21
So you're telling me that i'll have to wait another 7 months so i can get ubuntu working properly ? I know that this is a new chipset but how could we resolve [BUG 1]("https://bugs.launchpad.net/ubuntu/+bug/1") if we don't support a hardware device that will be installed in probably millions of computers around the world in the next months ?

---

### Post by redDEADresolve on 2008-10-22
> **andreiashu said:**
> So you're telling me that i'll have to wait another 7 months so i can get ubuntu working properly ? I know that this is a new chipset but how could we resolve [BUG 1]("https://bugs.launchpad.net/ubuntu/+bug/1") if we don't support a hardware device that will be installed in probably millions of computers around the world in the next months ?

The g45 freezing on login bug a been fixed with todays, October 22 2008, intel driver and kernel update for Ubuntu 8.10.

---

### Post by abandonow on 2008-10-22
Im testing now, I just upgraded and enabled EXA acceleration instead of XAA.

I have the latest intel driver tough, 2.4.2 (not 2.4.1). 

Currently no problems. Playing a movie, going in and out of fullscreen –*no problems. Im heading out for a bit now, so Im just going to let the movie play and see if it has crashed when Im back.

Still seeing some glitches on the screen when playing a movie, as I mentioned earlier on.

---

### Post by vtslimik on 2008-10-22
How about compiz and other visual effects on this card? you experience any problems or is it only problems when playing a movie?

---

### Post by abandonow on 2008-10-22
No crashes when I got back. I dont run compiz or other visual effects (other than what XBMC uses). But the glitches is only in movies.

---

### Post by Croccydile on 2008-10-22
I'm going to check this out also, mine was crashing if I let it sit at the desktop for a while and then opening a new window of anything made it lock completely.

More thanks to all the testers!

---

### Post by another_sam on 2008-10-22
(sorry because I don't have this card, I haven't read almost any message here, and I have to go back to my duties right now, but here it goes my quick and cheap answer!)

try this:
[http://bbs.archlinux.org/viewtopic.php?pid=433671#p433671](http://bbs.archlinux.org/viewtopic.php?pid=433671#p433671)
and if it doesn't works, try reading the whole thread.
[http://bbs.archlinux.org/viewtopic.php?id=56889](http://bbs.archlinux.org/viewtopic.php?id=56889)

hope it helps. bye.

edit.: some more raw info here:
[http://www.phoronix.com/scan.php?page=news_item&px=Njc5Nw](http://www.phoronix.com/scan.php?page=news_item&px=Njc5Nw)
[http://www.phoronix.com/scan.php?page=article&item=intel_x4500hd](http://www.phoronix.com/scan.php?page=article&item=intel_x4500hd)
[http://www.phoronix.com/scan.php?page=news_item&px=NjUzMw](http://www.phoronix.com/scan.php?page=news_item&px=NjUzMw)

---

### Post by Landris on 2008-10-23
After the latest updates, it's now working for me. Yay! Enjoying OTA HD in MythTV.

---

### Post by abandonow on 2008-10-23
> **vtslimik said:**
> How about compiz and other visual effects on this card? you experience any problems or is it only problems when playing a movie?

Looks like [intels newest driver 2.5.0](http://lists.freedesktop.org/archives/xorg/2008-October/039555.html) fixes alot of bugs (unfortunatly not the "tearing" in fullscreen videoes)

Anybody knows when this will be available as a deb package?

---

### Post by abandonow on 2008-10-23
Also, after I enabled EXA none of the visualizers in XBMC (XBox Mulitmedia Center) works. They did work with the old one.

---

### Post by orduek on 2008-10-23
is the 2.5 driver out with the latest updates already?

---

### Post by abandonow on 2008-10-23
No, you have to compile it yourself if you want it.

---

### Post by Landris on 2008-10-23
> **orduek said:**
> is the 2.5 driver out with the latest updates already?

I was referring to the fixes from Ubuntu to the xorg and intel drivers on October 22nd.

---

### Post by orduek on 2008-10-24
> **abandonow said:**
> No, you have to compile it yourself if you want it.

someone tried it?
is it worth.
I have the asus p5q-em and having some problems also.

---

### Post by thechump on 2008-10-24
Well, another report of success on the video front with the latest updates from ubuntu.  I am now able to play mpeg2 HD without any problems, no tearing, etc.  I can play about 30 seconds of mpeg4 HD before mythtv hangs.  I think this may be a decoder issue; will try with coreavc time permitting later this coming weekend.

However, I still cannot get any audio out of any audio jack!  The default install since beta6 is Pulseaudio.  But regardless of what I set, I don't get anything...I tried the optical out, hdmi out, the DG45ID's back panel ports, the front panel ports.  So I killed pulseaudio and tried with Alsa..same result.  The system does recognize the Intel HDA device.

Way back in Beta4, I was able to use alsa to output audio through the optical out...the only problem at that time was that I had to unmute that digital channel on every boot with alsamixer.

Any ideas?  I have had this problem since beta6.  A fresh install of the RC doesn't help either.

---

### Post by orduek on 2008-10-24
Does anyone able to connect it through HDMI cable?
I'm having some problems connecting it to my TV with HDMI (resolution problems and sometimes i see blurb)

---

### Post by abandonow on 2008-10-24
Im connecting it trough hdmi. No problems. 1080p running fine.

And to the sound issue, I have an .asoundrc in my user dir.

.asoundrc content:
```
.asoundrc 
pcm.!default {
       type plug
       slave.pcm "iec958:CARD=Intel,DEV=0" # taken from aplay -L 
#       slave.rate 48000 # optional resampling to 48kHz
}

```

I think I got it from a gentoo wiki or something.

---

### Post by orduek on 2008-10-24
I can't restart my cumputer to VGA mode at all (let alone HDMI).
have to go to recovery mode and resume X and through the resume boot.
otherwise - can't get in.
and...I have no audio (through regular audio connection).
any ideas?

---

### Post by andreiashu on 2008-10-24
> **redDEADresolve said:**
> The g45 freezing on login bug a been fixed with todays, October 22 2008, intel driver and kernel update for Ubuntu 8.10.
thanks !

---

### Post by Landris on 2008-10-24
I am also having no problems via HDMI to my TV at 1080p

And my sound is working via optical to my receiver no problem, the only thing I had to do was check off IEC958 or something like that in sound settings.

My board is the Gigabyte EG45M-DS2H, so it likely has a different sound chip than the Intel G45 boards.

---

### Post by orduek on 2008-10-24
sound is no longer a problem.
but I still have the other problems :(

---

### Post by niklaskb on 2008-10-25
Anyone had any success in enabling sound over HDMI?

---

### Post by andreiashu on 2008-10-25
Sound outputted from the analog jacks is not usable: interrupts and noises. It is already filled a bug in launchpad and i confirmed it: [271519]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/271519").
Does anyone have the same issues ?
alsa-info.sh output: [http://www.alsa-project.org/db/?f=93104246e46f4b3e3f063667b506937b5e875e35]("http://www.alsa-project.org/db/?f=93104246e46f4b3e3f063667b506937b5e875e35")

---

### Post by thechump on 2008-10-26
> **abandonow said:**
> I
.asoundrc content:
```
.asoundrc 
pcm.!default {
       type plug
       slave.pcm "iec958:CARD=Intel,DEV=0" # taken from aplay -L 
#       slave.rate 48000 # optional resampling to 48kHz
}

```



I tried a .asoundrc exactly like yours, and one like this to no avail:
```

pcm.!default {
	type plug
	slave.pcm "surround51:CARD=Intel,DEV=0" 
}

My aplay -L output is:
front:CARD=Intel,DEV=0
    HDA Intel, STAC92xx Analog
    Front speakers
surround40:CARD=Intel,DEV=0
    HDA Intel, STAC92xx Analog
    4.0 Surround output to Front and Rear speakers
surround41:CARD=Intel,DEV=0
    HDA Intel, STAC92xx Analog
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=Intel,DEV=0
    HDA Intel, STAC92xx Analog
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=Intel,DEV=0
    HDA Intel, STAC92xx Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=Intel,DEV=0
    HDA Intel, STAC92xx Analog
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
hdmi:CARD=Intel,DEV=0
    HDA Intel
    HDMI Audio Output
null
    Discard all samples (playback) or generate zero samples (capture)

```

I wonder why they all say "Analog".  Anyway, I've tried both surround51 and hdmi without any use.  Anyone else running with a Intel DG45ID do a "aplay -L" or send me your asoundrc file?  Shouldn't the ubuntu setup create one for me automatically at /etc during install?

---

### Post by jackocleebrown on 2008-10-26
Intrepid updates today included:

> xserver-xorg-video-intel (2:2.4.1-1ubuntu10) intrepid; urgency=low

  * 28_stolen_memory_counting_g4x.patch:
    - Fixes freeze on login for G45 hardware when X.org runs in EXA mode.
      Issue was fixed upstream in both the kernel and x driver.  This
      patch is also in Debian.
      (LP: #285572)

 -- Bryce Harrington <bryce@ubuntu.com>  Tue, 21 Oct 2008 11:35:13 -0700


Does this fix the problems for people!?!

---

### Post by abandonow on 2008-10-26
For sound issues, read these two links for tips:

[http://alsa.opensrc.org/index.php/DigitalOut](http://alsa.opensrc.org/index.php/DigitalOut)
[http://alsa.opensrc.org/.asoundrc](http://alsa.opensrc.org/.asoundrc)

---

### Post by thechump on 2008-10-27
> **abandonow said:**
> For sound issues, read these two links for tips:

[http://alsa.opensrc.org/index.php/DigitalOut](http://alsa.opensrc.org/index.php/DigitalOut)
[http://alsa.opensrc.org/.asoundrc](http://alsa.opensrc.org/.asoundrc)

I've tried all the different settings and devices suggested in that doc with zero success.  With each combination, I connected something to front headphone jack; the rear line out, the optical out, and the HDMI out.  The closest I came to hearing anything is low static on the headphone.  If something was coming out of the optical, my receiver should see a signal; it doesn't....and yes, I've unmuted every single channel with "alsamixer -Dhw".

I got so frustrated I thought my hardware was busted....cuz this used to work with Alpha4/5.  So I installed Windoze Vista to check the hardware.  With Vista, I can get perfect audio coming out of my HDMI port.  My receiver gets lit up by the optical out also, but nothing comes out from that port.  So perhaps when both HDMI and optical are connected on Vista, only HDMI works?  Line out works.

Anyhow, it can't be my optical cable cuz I hooked it up to my DVD player without changing any other settings...and perfect audio comes out from it.

So, If anyone is using the Intel DG45ID with HDMI out and optical out and have both 1080P display with audio, please help clarify whether you have audio and how did you get it?

btw, updated to the latest BIOS from Intel and still not working.  I have two of these systems, both are behaving exactly the same #$@#$#@! way.

---

### Post by kempo on 2008-10-27
> **jackocleebrown said:**
> Intrepid updates today included:



Does this fix the problems for people!?!

Hi - how would i go about getting these updates? I'm already running 8.10.

Thanks

---

### Post by andreiashu on 2008-10-27
> **kempo said:**
> Hi - how would i go about getting these updates? I'm already running 8.10.

Thanks
you should just run update manager to have the latest updates installed.

---

### Post by andreiashu on 2008-10-27
Oki, more updates about my sound problem with this motherboard: now my sound works in the **front** analog entrance but on the **back** analog entrance the sound is still very noisy.
Does someone happen to know what is the cause of this ?

Edit: although even when i connect the headphones to the front entrance(which works) the volume is still too low.

---

### Post by kempo on 2008-10-27
> **andreiashu said:**
> you should just run update manager to have the latest updates installed.

oh god... i need to have my head screwed back on today... sorry!! thanks for replying though!

kempo

---

### Post by abandonow on 2008-10-27
Ok, things are getting better, but I still have some issues.

**System info:**
- GIGABYTE GA-EG45M-DS2H (motherboard)
- 3Ghz 	INTEL Core 2 Duo E8400
- 4GB RAM (only using 3gb because 32bit system)
- Ubuntu 8.10 (with all the latest updates, as of today)
- Running latest SVN xbmc linux.
- Intel Graphics 2.4.2 from Debian unstable. (2.5.0 is released by intel, but I dont want to compile it from scratch)

This HTPC is hooked up to a 42" Toshiba full-hd LCD TV trough HDMI. Resolution is fine (full HD). Sound working trough sp/dif.

**Problems:**
- I get glitches when playing movies in XBMC (X-Box Multimedia Center)
- After I changed from the temporary fix of XAA hw acceleration, to EXA the opengl music visualizers in XBMC stopped working.
- I have problems playing 1080p mkv-container movies. Dropping frames. :(

Glitches get fixed when I enable "Vertical Blank Sync" option in XBMC, but this seems to increase cpu load. 

The glitches is probably an bug in the intel driver, still not fixed in 2.5.0 afaik.

Im pretty new to Linux as a HTPC. Ive been using linux for server os for a couple of years, but is still pretty new in this game.. and especially as HTPC OS.

[B]Questions:
Why does it lag when I play 1080p movies? My CPU should be able to handle that? Or should it?

Why does the xbmc music visualizers stop working when I enable EXA, instead of XAA?[/B]


Any tips/hints/solutions/etc. is appreciated! Thank you! :)


My xorg.conf:
```
Section "Monitor"
       Identifier      "Toshiba42"
       VendorName      "Toshiba"
       ModelName       "42X3000PG"
       Option          "IgnoreEDID"
       VertRefresh     23-61
       HorizSync       15-68
       ModeLine	       "1080p" 148.50  1920 2448 2492 2640  1080 1084 1089 1125 +hsync +vsync
       ModeLine        "720p" 27.00  720 732 796 864  576 581 586 625 -hsync -vsync
       ModeLine	       "480p" 25.20  640 656 752 800  480 490 492 525 -hsync -vsync
       Option          "PreferredMode" "1080p"
       #DisplaySize    320 180
       DisplaySize     487.68 274.32
EndSection

#Modeline "1920x1080"x0.0  148.50  1920 2448 2492 2640  1080 1084 1089 1125 +hsync +vsync (56.2 kHz)
#Modeline "720x576"x0.0   27.00  720 732 796 864  576 581 586 625 -hsync -vsync (31.2 kHz)
#Modeline "640x480"x0.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)

Section "Device"
       Identifier  	"Intel GMA X4500HD"
       Driver      	"intel"
       VendorName  	"Intel"
       BoardName   	"G45 [Intel GMA X4500HD]"
       BusID       	"PCI:0:2:0"
       
       #Option  		"NoAccel" "false" #temp fix for 45g problemer.
       #Disable or enable acceleration.  Default: acceleration is enabled.

       #Option "AccelMethod" "XAA" #skal være EXA
       Option "AccelMethod" "EXA"
       #Choose  acceleration architecture, either "XAA" or "EXA".  XAA is the old XFree86 based acceleration architecture.  EXA is
       #a newer and simpler acceleration architecture designed to better accelerate the X Render extension.  Default: "EXA".

       Option "ModeDebug" "true"
       #Enable printing of additional debugging information about modesetting to the server log.
EndSection

Section "Module"
	   Load "glx"
	   Load "dri"
	   Load "GLcore" # addon fra forum
	   Load "v4l"	# addon fra forum
EndSection

Section "DRI"
	   Mode 0666
EndSection

Section "Screen"
	Identifier	"LCDTV"
	Monitor		"Toshiba42"
	Device		"Intel GMA X4500HD"
      	DefaultDepth    24
        DefaultFbBpp    32 
	SubSection "Display"
                Depth           24
                FbBpp           32
        EndSubSection 
EndSection

```

glxinfo output:
```
name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_copy_sub_buffer, 
    GLX_OML_swap_method, GLX_SGI_swap_control, GLX_SGIS_multisample, 
    GLX_SGIX_fbconfig, GLX_SGIX_visual_select_group
client glx vendor string: SGI
client glx version string: 1.4
client glx extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_allocate_memory, 
    GLX_MESA_copy_sub_buffer, GLX_MESA_swap_control, 
    GLX_MESA_swap_frame_usage, GLX_OML_swap_method, GLX_OML_sync_control, 
    GLX_SGI_make_current_read, GLX_SGI_swap_control, GLX_SGI_video_sync, 
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, 
    GLX_SGIX_visual_select_group, GLX_EXT_texture_from_pixmap
GLX version: 1.2
GLX extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_swap_control, 
    GLX_MESA_swap_frame_usage, GLX_OML_swap_method, GLX_SGI_swap_control, 
    GLX_SGI_video_sync, GLX_SGIS_multisample, GLX_SGIX_fbconfig, 
    GLX_SGIX_visual_select_group
OpenGL vendor string: Tungsten Graphics, Inc
OpenGL renderer string: Mesa DRI Intel(R) G45/G43 20061102 x86/MMX/SSE2
OpenGL version string: 1.4 Mesa 7.2
OpenGL extensions:
    GL_ARB_depth_texture, GL_ARB_draw_buffers, GL_ARB_fragment_program, 
    GL_ARB_fragment_program_shadow, GL_ARB_fragment_shader, 
    GL_ARB_multisample, GL_ARB_multitexture, GL_ARB_point_parameters, 
    GL_ARB_point_sprite, GL_ARB_shader_objects, GL_ARB_shading_language_100, 
    GL_ARB_shading_language_120, GL_ARB_shadow, GL_ARB_texture_border_clamp, 
    GL_ARB_texture_compression, GL_ARB_texture_cube_map, 
    GL_ARB_texture_env_add, GL_ARB_texture_env_combine, 
    GL_ARB_texture_env_crossbar, GL_ARB_texture_env_dot3, 
    GL_ARB_texture_mirrored_repeat, GL_ARB_texture_non_power_of_two, 
    GL_ARB_texture_rectangle, GL_ARB_transpose_matrix, 
    GL_ARB_vertex_buffer_object, GL_ARB_vertex_program, GL_ARB_vertex_shader, 
    GL_ARB_window_pos, GL_EXT_abgr, GL_EXT_bgra, GL_EXT_blend_color, 
    GL_EXT_blend_equation_separate, GL_EXT_blend_func_separate, 
    GL_EXT_blend_logic_op, GL_EXT_blend_minmax, GL_EXT_blend_subtract, 
    GL_EXT_clip_volume_hint, GL_EXT_cull_vertex, GL_EXT_compiled_vertex_array, 
    GL_EXT_copy_texture, GL_EXT_draw_range_elements, GL_EXT_fog_coord, 
    GL_EXT_multi_draw_arrays, GL_EXT_packed_depth_stencil, 
    GL_EXT_packed_pixels, GL_EXT_point_parameters, GL_EXT_polygon_offset, 
    GL_EXT_rescale_normal, GL_EXT_secondary_color, 
    GL_EXT_separate_specular_color, GL_EXT_shadow_funcs, GL_EXT_stencil_wrap, 
    GL_EXT_subtexture, GL_EXT_texture, GL_EXT_texture3D, 
    GL_EXT_texture_edge_clamp, GL_EXT_texture_env_add, 
    GL_EXT_texture_env_combine, GL_EXT_texture_env_dot3, 
    GL_EXT_texture_filter_anisotropic, GL_EXT_texture_lod_bias, 
    GL_EXT_texture_object, GL_EXT_texture_rectangle, GL_EXT_texture_sRGB, 
    GL_EXT_vertex_array, GL_3DFX_texture_compression_FXT1, 
    GL_APPLE_client_storage, GL_APPLE_packed_pixels, 
    GL_ATI_blend_equation_separate, GL_ATI_separate_stencil, 
    GL_IBM_rasterpos_clip, GL_IBM_texture_mirrored_repeat, 
    GL_INGR_blend_func_separate, GL_MESA_pack_invert, GL_MESA_ycbcr_texture, 
    GL_MESA_window_pos, GL_NV_blend_square, GL_NV_light_max_exponent, 
    GL_NV_point_sprite, GL_NV_texture_rectangle, GL_NV_texgen_reflection, 
    GL_NV_vertex_program, GL_NV_vertex_program1_1, GL_OES_read_format, 
    GL_SGIS_generate_mipmap, GL_SGIS_texture_border_clamp, 
    GL_SGIS_texture_edge_clamp, GL_SGIS_texture_lod, GL_SGIX_depth_texture, 
    GL_SUN_multi_draw_arrays

3 GLX Visuals
   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x21 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x22 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x5f 32 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None

36 GLXFBConfigs:
   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x60  0 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x61  0 tc  0 32  0 r  .  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0x62  0 tc  0 32  0 r  y  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x63  0 tc  0 32  0 r  y  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0x64  0 tc  0 32  0 r  y  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x65  0 tc  0 32  0 r  y  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0x66  0 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x67  0 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x68  0 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x69  0 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x6a  0 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x6b  0 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x6c  0 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x6d  0 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x6e  0 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x6f  0 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x70  0 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x71  0 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x72  0 dc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x73  0 dc  0 32  0 r  .  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0x74  0 dc  0 32  0 r  y  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x75  0 dc  0 32  0 r  y  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0x76  0 dc  0 32  0 r  y  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x77  0 dc  0 32  0 r  y  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0x78  0 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x79  0 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x7a  0 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x7b  0 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x7c  0 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x7d  0 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x7e  0 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x7f  0 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x80  0 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x81  0 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x82  0 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x83  0 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow

```

---

### Post by noisymime on 2008-10-27
I have a very similar system to yourself (same mobo, ram, E8500) but I can't promise any of what I've done will work for you.

> **abandonow said:**
> 4GB RAM (only using 3gb because 32bit system)
Install packages 'linux-server' & 'linux-headers-server" then reboot. You'll then have 4gb ram addressed on your 32-bit system :)

> **abandonow said:**
> I get glitches when playing movies in XBMC (X-Box Multimedia Center)

I'm guessing by glitches you mean tearing. This is when the horizontal possition of one line does not match the position of the one above it and is most noticable on panning video. 
> **abandonow said:**
> Glitches get fixed when I enable "Vertical Blank Sync" option in XBMC, but this seems to increase cpu load. 
This almost certainly confirms that what you're seeing is tearing. Unfortunately the tearing problem is in the intel driver and is still present in 2.5.0 (See the release notes: [http://lists.freedesktop.org/archives/xorg/2008-October/039555.html](http://lists.freedesktop.org/archives/xorg/2008-October/039555.html)). Just a matter of waiting for this to improve I'm afraid. I'm guessing that the XBMC option you're enabling does the sync'ing in CPU (It should be done by the video card) and hence the spike you're seeing. 

> **abandonow said:**
> 
[B]Questions:
Why does it lag when I play 1080p movies? My CPU should be able to handle that? Or should it?[/B]

Yes it should, mine does, although it didn't initially. What app are you using to play the file? I'm using mplayer and its OK. 
Try running 'xvinfo' and see what you get back. Before the driver updates I got a 'No xv enabled adaptors' type message and HD playback was horrible. After the updates xvinfo prints a stack of info and playback is fine. 

> **abandonow said:**
> 
Why does the xbmc music visualizers stop working when I enable EXA, instead of XAA?[/B]

I use mythtv so I can't really help with this I'm afraid

---

### Post by thechump on 2008-10-28
I've worked around the sound problem.  It turns out to be an alsa issue; I had to upgrade to the latest alsa to get it to work (version 1.0.18rc3).  If you are in the same boat, follow the upgrade procedures here: [https://help.ubuntu.com/community/HdaIntelSoundHowto]("https://help.ubuntu.com/community/HdaIntelSoundHowto")

Anyhow, I can now view both ATSC and MPEG2 HD video without any artifacts and with sound!!!  Looks very smooth and such.  I didn't have time to test mpeg4 last night, so that's next on the list.

As a side note, this is just plain sad.  Atleast with the video issues, everyone knew that we needed fixes for the driver.  It seems that atleast up to this point with the Ibex RC already out, sound will not work out of the box.

---

### Post by abandonow on 2008-10-28
Thank you for the answer! Im now using 4gb of ram. :)


I can watch 720 HD files without problems (except for tearing when vsync is disabled). 

When I run 1080p in XBMC it seems fine most of the time, but when the camera is panning, it droppes frames like crazy &#8211; showing the video at 19fps at it worst. :(

I tried with mplayer (btw. im trying an Hi-Definition Reference Disc 2008 [ripped from Blu-ray @ 1080p x264], but it still drops frames (example clip is a train that is running horisontal accross the screen in the distance. Another one is cars running by).

mplayer gives me an error that says "Too many video packets in the buffer: (98 in 8492315 bytes).". I havent done anything to mplayer conf, just installed it from apt.


Output of xvinfo:
```
X-Video Extension version 2.2
screen #0
  Adaptor #0: "Intel(R) Textured Video"
    number of ports: 16
    port base: 77
    operations supported: PutImage 
    supported visuals:
      depth 24, visualID 0x21
    number of attributes: 2
      "XV_BRIGHTNESS" (range -128 to 127)
              client settable attribute
              client gettable attribute (current value is 0)
      "XV_CONTRAST" (range 0 to 255)
              client settable attribute
              client gettable attribute (current value is 0)
    maximum XvImage size: 1920 x 1088
    Number of image formats: 5
      id: 0x32595559 (YUY2)
        guid: 59555932-0000-0010-8000-00aa00389b71
        bits per pixel: 16
        number of planes: 1
        type: YUV (packed)
      id: 0x32315659 (YV12)
        guid: 59563132-0000-0010-8000-00aa00389b71
        bits per pixel: 12
        number of planes: 3
        type: YUV (planar)
      id: 0x30323449 (I420)
        guid: 49343230-0000-0010-8000-00aa00389b71
        bits per pixel: 12
        number of planes: 3
        type: YUV (planar)
      id: 0x59565955 (UYVY)
        guid: 55595659-0000-0010-8000-00aa00389b71
        bits per pixel: 16
        number of planes: 1
        type: YUV (packed)
      id: 0x434d5658 (XVMC)
        guid: 58564d43-0000-0010-8000-00aa00389b71
        bits per pixel: 12
        number of planes: 3
        type: YUV (planar)

```

My cpu is a 3ghz c2d, but is reported at 2ghz. But I tought that was just that it scales down when it doesnt need the speed?

Anyhow, cpu info:
```
cat /proc/cpuinfo
processor	: 0
vendor_id	: GenuineIntel
cpu family	: 6
model		: 23
model name	: Intel(R) Core(TM)2 Duo CPU     E8400  @ 3.00GHz
stepping	: 10
cpu MHz		: 2000.000
cache size	: 6144 KB
physical id	: 0
siblings	: 2
core id		: 0
cpu cores	: 2
apicid		: 0
initial apicid	: 0
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 13
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc arch_perfmon pebs bts pni monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr sse4_1 lahf_lm
bogomips	: 5999.31
clflush size	: 64
power management:

processor	: 1
vendor_id	: GenuineIntel
cpu family	: 6
model		: 23
model name	: Intel(R) Core(TM)2 Duo CPU     E8400  @ 3.00GHz
stepping	: 10
cpu MHz		: 2000.000
cache size	: 6144 KB
physical id	: 0
siblings	: 2
core id		: 1
cpu cores	: 2
apicid		: 1
initial apicid	: 1
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 13
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc arch_perfmon pebs bts pni monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr sse4_1 lahf_lm
bogomips	: 5999.58
clflush size	: 64
power management:

```


Any other tips? If mplayer runs 1080 fine on your [noisymime] system, it should run fine on mine.

Thank you! :)

---

### Post by niklaskb on 2008-10-28
> **thechump said:**
> I've worked around the sound problem.  It turns out to be an alsa issue; I had to upgrade to the latest alsa to get it to work (version 1.0.18rc3).  If you are in the same boat, follow the upgrade procedures here: [https://help.ubuntu.com/community/HdaIntelSoundHowto]("https://help.ubuntu.com/community/HdaIntelSoundHowto")

Anyhow, I can now view both ATSC and MPEG2 HD video without any artifacts and with sound!!!  Looks very smooth and such.  I didn't have time to test mpeg4 last night, so that's next on the list.

As a side note, this is just plain sad.  Atleast with the video issues, everyone knew that we needed fixes for the driver.  It seems that atleast up to this point with the Ibex RC already out, sound will not work out of the box.Did you get it working for sound over HDMI?

---

### Post by noisymime on 2008-10-28
> **abandonow said:**
> Thank you for the answer! Im now using 4gb of ram. :)

My cpu is a 3ghz c2d, but is reported at 2ghz. But I tought that was just that it scales down when it doesnt need the speed?
...

Any other tips? If mplayer runs 1080 fine on your [noisymime] system, it should run fine on mine.

I agree, it should run fine for you. If I were you I'd be looking at the 2ghz thing. Mine doesn't scale down that I'm aware of and even when doing nothing it gives the following in cpuinfo:

```

processor       : 0
vendor_id       : GenuineIntel
cpu family      : 6
model           : 23
model name      : Intel(R) Core(TM)2 Duo CPU     E8500  @ 3.16GHz
stepping        : 10
cpu MHz         : 3166.285
cache size      : 6144 KB
physical id     : 0
siblings        : 2
core id         : 0
cpu cores       : 2
apicid          : 0
initial apicid  : 0
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 13
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc arch_perfmon pebs bts pni monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr sse4_1 lahf_lm
bogomips        : 6332.57
clflush size    : 64
power management:

```
Then repeated for the 2nd core. 

I haven't changed any BIOS settings or anything to enable/disable power savings. If I were you I'd be checking out what you've got setup power wise, both in ubuntu and your bios.

Does cpuinfo change to say 3ghz when you start playing a video? If not it means the CPU isn't being scaled back up. 2ghz will struggle to play a 1080p file and basically show the kind of behaviour you're seeing.

---

### Post by abandonow on 2008-10-28
It looks like the cpu scales up. I started playing a 1080p movie in XBMC, and it went up to 2666mhz on one cpu core, but it doesnt look like its sticking to that clock ratio. I tried again, still playing the movie, and its back down at 2ghz (then it goes up again, and then back again, etc.).

(so far it has dropped 23 frames, but it looks like it plays this HD movie okay. CPU1 is 60-70% and CPU2 is 60-70%)

```
cat /proc/cpuinfo
processor	: 0
vendor_id	: GenuineIntel
cpu family	: 6
model		: 23
model name	: Intel(R) Core(TM)2 Duo CPU     E8400  @ 3.00GHz
stepping	: 10
cpu MHz		: 2000.000
cache size	: 6144 KB
physical id	: 0
siblings	: 2
core id		: 0
cpu cores	: 2
apicid		: 0
initial apicid	: 0
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 13
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc arch_perfmon pebs bts pni monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr sse4_1 lahf_lm
bogomips	: 5999.31
clflush size	: 64
power management:

processor	: 1
vendor_id	: GenuineIntel
cpu family	: 6
model		: 23
model name	: Intel(R) Core(TM)2 Duo CPU     E8400  @ 3.00GHz
stepping	: 10
cpu MHz		: 2667.000
cache size	: 6144 KB
physical id	: 0
siblings	: 2
core id		: 1
cpu cores	: 2
apicid		: 1
initial apicid	: 1
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 13
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc arch_perfmon pebs bts pni monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr sse4_1 lahf_lm
bogomips	: 5999.58
clflush size	: 64
power management:
```

I will try to look into it and try to lock them at 3Ghz. Any tips on how I do that, will be appreciated. :)

EDIT:

Okay, I turned off cpu frequency manager, and now its up to 2666Ghz on both, but shouldnt it be up at 3Ghz? Could it be something in the bios? Afaik I havent edited any cpu settings.

EDIT2:
I just installed cpufrequtils:

```

Report errors and bugs to linux@brodo.de, please.
analyzing CPU 0:
  driver: acpi-cpufreq
  CPUs which need to switch frequency at the same time: 0
  hardware limits: 2.00 GHz - 2.67 GHz
  available frequency steps: 2.67 GHz, 2.00 GHz
  available cpufreq governors: userspace, conservative, ondemand, powersave, performance
  current policy: frequency should be within 2.00 GHz and 2.67 GHz.
                  The governor "ondemand" may decide which speed to use
                  within this range.
  current CPU frequency is 2.00 GHz.
analyzing CPU 1:
  driver: acpi-cpufreq
  CPUs which need to switch frequency at the same time: 1
  hardware limits: 2.00 GHz - 2.67 GHz
  available frequency steps: 2.67 GHz, 2.00 GHz
  available cpufreq governors: userspace, conservative, ondemand, powersave, performance
  current policy: frequency should be within 2.00 GHz and 2.67 GHz.
                  The governor "ondemand" may decide which speed to use
                  within this range.
  current CPU frequency is 2.00 GHz.

```

It says the hw is limited to 2,67GHz, why? My cpu is suppose to be 3ghz. Anyhow, Im guessing its an BIOS issue, so I have to get in there to check. Im going to check that tomorrow (got to use my roomies usb-keyboard, all I got is bluetooth keyboard).

Thanks for all your answers. Will post back the results. :)

---

### Post by noisymime on 2008-10-28
> **abandonow said:**
> 
It says the hw is limited to 2,67GHz, why? My cpu is suppose to be 3ghz. Anyhow, Im guessing its an BIOS issue, so I have to get in there to check. 
Definitely sounds like something in the bios to me. 

> **abandonow said:**
> 
Im going to check that tomorrow (got to use my roomies usb-keyboard, all I got is bluetooth keyboard).
I have the same problem. Always hate having to find a usb keyboard to change thigns in the bios! :)

---

### Post by andreiashu on 2008-10-29
when will the intel 2.5 video driver be in the repositories as e deb package ?

---

### Post by abandonow on 2008-10-29
About the cpu issue, it was a wrong setting in the BIOS. Running @ 3ghz now. Still problems with the HD reference blueray rip disk, but not with other movies. So I guess its either some settings of the encoding of hd reference disk, or an error with that file. I dont know. Doesnt look like its using 100% of both of the cores when I play it, and Im still loosing frames.

---

### Post by Charlie708 on 2008-10-29
Anyone notice that these chips run hot?  The one in my T400 dumps a lot of heat, and chews a lot of power.

---

### Post by thechump on 2008-10-30
> **niklaskb said:**
> Did you get it working for sound over HDMI?

Nope, only SPDF.  However, I just saw the notice for the final release of 1.0.18; will try that out tomorrow night and see.

---

### Post by orduek on 2008-10-30
Well, I am still unable to connect through HDMI and only through VGA.
when connecting through HDMI the beginning is OK and I see the mythbuntu load screen but then it lost.
any ideas?

---

### Post by thechump on 2008-10-30
> **orduek said:**
> Well, I am still unable to connect through HDMI and only through VGA.
when connecting through HDMI the beginning is OK and I see the mythbuntu load screen but then it lost.
any ideas?

More than likely it's because of a resolution detection issue.  The system is trying to display at a resolution your monitor cannot support.  I see this problem with both Vista and Linux with my Pioneer plasma at 1080p.  For whatever reason, the Vista install uses a resolution my plasma cannot display; however, if I install it elsewhere and reconnect and boot with my plasma, the installed Vista detects a usable resolution.  On Ibex, the splash screen can't be display on my system, so I just get a blank screen after the grub menu until the GDM greeter.

---

### Post by orduek on 2008-10-30
> **thechump said:**
> More than likely it's because of a resolution detection issue.  The system is trying to display at a resolution your monitor cannot support.  I see this problem with both Vista and Linux with my Pioneer plasma at 1080p.  For whatever reason, the Vista install uses a resolution my plasma cannot display; however, if I install it elsewhere and reconnect and boot with my plasma, the installed Vista detects a usable resolution.  On Ibex, the splash screen can't be display on my system, so I just get a blank screen after the grub menu until the GDM greeter.

I can see the splash screen but can't see nothing afterwords.
How do I solve it?

---

### Post by thechump on 2008-10-31
> **orduek said:**
> I can see the splash screen but can't see nothing afterwords.
How do I solve it?

That's because the splash screen uses a resolution that's different than your X session.  At the grub menu, you can boot 
into recovery mode and choose the session with text root access.
Look at your X log at /var/log.  It should tell you what resolution
it was trying to run at...along with all the other ones that it
detected.  By default now, your /etc/X11/xorg.conf is pretty much empty because of the autodetect.  You'll need to manually plug in valid values for the resolution there.  I'd recommend that you disable gdm from starting up during your recovery session, then boot up fully into text mode so that you can try different values into xorg.conf and manually startup X to see which one works before enablging gdm again.

The easiest away to avoid this trial and error process is googling to see if other people have an X config for your display and use their values....or if you have had X distributions that work before, load those and grab the resolution from those xorg.conf file or from the X log....oh wait, I just noticed that you said your VGA output looks OK with the same monitor.  If that's the case, then you already a way to get valid values to put into your xorg.conf file.

---

### Post by anthonyJC on 2008-10-31
> **andreiashu said:**
> when will the intel 2.5 video driver be in the repositories as e deb package ?

It will not  be placed in the Intrepid repositories because it requires libdrm 2.4. 

Get mandatory libdrm firstly:
```

http://ppa.launchpad.net/xorg-edgers/ubuntu/pool/main/libd/libdrm/

```
then install, then secondly get the driver :
```

http://ppa.launchpad.net/thjaeger/ubuntu/pool/main/x/xserver-xorg-video-intel/

```

You will still get stability problems because of missing G43/5 stability fix in kernel 2.6.28 (you will still be using 2.6.27.) Virtual consoles are fixed. Use at your own risk (not tested by many people.)

---

### Post by orduek on 2008-10-31
> **thechump said:**
> That's because the splash screen uses a resolution that's different than your X session.  At the grub menu, you can boot 
into recovery mode and choose the session with text root access.
Look at your X log at /var/log.  It should tell you what resolution
it was trying to run at...along with all the other ones that it
detected.  By default now, your /etc/X11/xorg.conf is pretty much empty because of the autodetect.  You'll need to manually plug in valid values for the resolution there.  I'd recommend that you disable gdm from starting up during your recovery session, then boot up fully into text mode so that you can try different values into xorg.conf and manually startup X to see which one works before enablging gdm again.

The easiest away to avoid this trial and error process is googling to see if other people have an X config for your display and use their values....or if you have had X distributions that work before, load those and grab the resolution from those xorg.conf file or from the X log....oh wait, I just noticed that you said your VGA output looks OK with the same monitor.  If that's the case, then you already a way to get valid values to put into your xorg.conf file.

how do i edit files through the root command prompt?
I can't start up mousepad

---

### Post by anthonyJC on 2008-10-31
> **orduek said:**
> how do i edit files through the root command prompt?
I can't start up mousepad
```

 nano <filename>

```

---

### Post by orduek on 2008-10-31
I think I might need more help here.
I have a 26' Metz LCD screen (1366 X 768 resolution)

does anyone has some ideas about the possible xorg.conf file that should be here?
I just can't figure it out. 
I tried changing some parameters in the xorg file but to no vail :(

---

### Post by andreiashu on 2008-11-01
> **anthonyJC said:**
> It will not  be placed in the Intrepid repositories because it requires libdrm 2.4. 

Get mandatory libdrm firstly:
```

http://ppa.launchpad.net/xorg-edgers/ubuntu/pool/main/libd/libdrm/

```
then install, then secondly get the driver :
```

http://ppa.launchpad.net/thjaeger/ubuntu/pool/main/x/xserver-xorg-video-intel/

```

You will still get stability problems because of missing G43/5 stability fix in kernel 2.6.28 (you will still be using 2.6.27.) Virtual consoles are fixed. Use at your own risk (not tested by many people.)
I hope that all the problems get fixed in the sooner future so we can update those drivers :)

---

### Post by webaake on 2008-11-02
For my Sony Bravia LCD TV 32" I found it essential to use displayconfig-gtk to get the right resolution.

In a terminal do;

gksudo displayconfig-gtk

and try out differents LCD's. This app writes to xorg.conf and if you get a working setup, take a backup!! ( sudo cp /etc/X11/xorg.conf xorg_backup)

The other thing I did was to disable the EDID in xorg.conf. EDID should pass info from the display to xorg, but if that doesn't work Plug'n'play won't work at all.

Try this in xorg.conf;

Option 		"UseEDID" "FALSE"

under section Screen

Remember to backup a working xorg.conf !!
Plug'n'play is a b*tch....

---

### Post by orduek on 2008-11-02
> **webaake said:**
> For my Sony Bravia LCD TV 32" I found it essential to use displayconfig-gtk to get the right resolution.

In a terminal do;

gksudo displayconfig-gtk

and try out differents LCD's. This app writes to xorg.conf and if you get a working setup, take a backup!! ( sudo cp /etc/X11/xorg.conf xorg_backup)

The other thing I did was to disable the EDID in xorg.conf. EDID should pass info from the display to xorg, but if that doesn't work Plug'n'play won't work at all.

Try this in xorg.conf;

Option 		"UseEDID" "FALSE"

under section Screen

Remember to backup a working xorg.conf !!
Plug'n'play is a b*tch....

this option doesn't exist in Intrepid anymore :(
any alternatives?
found display manager and changed resolutions but there is no 1366X768 resolution. only one that looks OK is 1024X768.

---

### Post by thechump on 2008-11-03
MPEG4 update: I can view MPEG4 with the loopfilter detect off...with or without coreavc.  However, quality is crappy.  I see much more sync issues and artifacts, and my audio channel keeps getting loss - especially with high motion or panning effects like sports.  Movies in mpeg4 look much better as motion is limited...atleast the one I saw.  

So at this point, my AMD 4400 with a crappy nvidia 8xxx serious video card runs circles around by brand new Intel 3gz dual core on the G45 with respect to mpeg4.

---

### Post by fusionisthefuture on 2008-11-04
does anyone know what option i might append to the grub entry to get my 8.10 live usb key (made with usb-creator) to boot on one of these boards?  if i try the option to run without changing the computer, it starts up and gives me a mouse on a black screen that i can move, but no desktop ever comes up.  if i try the option to install ubuntu, it brings up the background in full resolution (1920x1200), brings up the install window, then flips out and goes black, restaring x a few times before giving up in static.  the same key works fine on an hp lappy
thanks,
-fitf

---

### Post by andreiashu on 2008-11-05
Well after waiting for more than  7 days for something good to happen with my Ubuntu (i was waiting for a proper video driver i think) i decided that i really need to get productive with my current new system so i switched to Windoze Vista.
I must tell you that neither the video card nor the sound card were detected from the start. Vista didn't recognize the network card either. The system was acting almost the same as in Ubuntu.
After installing the drivers everything works extremly smoothly i a can finally use my system at its true power.
I don't feel too good about this but at this moment Ubuntu is not usable with this motherboard, really...
I hope ppl will keep this post updated so i can try to switch back to Ubuntu when the drivers get out.

Andrei

---

### Post by metapaso on 2008-11-05
> You will still get stability problems because of missing G43/5 stability fix in kernel 2.6.28 (you will still be using 2.6.27.) Virtual consoles are fixed. Use at your own risk (not tested by many people.)

I'm new to this thread, ASUS P5Q-EM, standard-install 64-bit 8.10.  Everything is running fine for me as a desktop PC, but I have no compiz if I try to run dual monitors.  Do you know if the 2.5.0 update will help me, and if so, is the stability expected to be worse than with 2.4.x and 2.6.27 kernel?

---

### Post by mdalacu on 2008-11-06
I have Gigabyte EG45M-DS2H, Live XBMC Beta2 doesn't work. I will try to install first Ubuntu 8.10 and XBMC, so wish me luck. :)
Is anyone else using this motherboard with Ubuntu 8.10 or XBMC?

---

### Post by abandonow on 2008-11-06
I am. Everything works fine, minus some bugs.. but that could just be my system.

I got problems with PAPlayer playing music (dvdplayer works fine), and visualizations does not work after I enabled EXA hw acceleration (instead of the old XAA).

---

### Post by anthonyJC on 2008-11-07
@metapaso
Dual Monitors:
My M/B DG45FC only has one DVI out so i cannot check that. But I remember reading someone having the problem with the 2.4.1 in testing section of the forums, but you already know !

It's unstable but only in minor ways :) you can work around it, especially with 2.5. 

Ubuntu driver (been running since 20sept, from daily builds): vc's broke, video unstable after half hour, native games stable, wine opengl stable; wine directx freeze box

2.5: vc's fixed, video stable, native games stable, wine opengl stable, wine directx freeze box.

To clarify, you don't need kernel 2.6.28 to run intel 2.5.

---

### Post by niklaskb on 2008-11-08
Seems like HDMI audio support is coming.... 

[http://mailman.alsa-project.org/pipermail/alsa-devel/2008-November/012162.html](http://mailman.alsa-project.org/pipermail/alsa-devel/2008-November/012162.html)

---

### Post by abandonow on 2008-11-08
```
aplay -L
front:CARD=Intel,DEV=0
    HDA Intel, ALC885 Analog
    Front speakers
surround40:CARD=Intel,DEV=0
    HDA Intel, ALC885 Analog
    4.0 Surround output to Front and Rear speakers
surround41:CARD=Intel,DEV=0
    HDA Intel, ALC885 Analog
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=Intel,DEV=0
    HDA Intel, ALC885 Analog
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=Intel,DEV=0
    HDA Intel, ALC885 Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=Intel,DEV=0
    HDA Intel, ALC885 Analog
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
iec958:CARD=Intel,DEV=0
    HDA Intel, ALC885 Digital
    IEC958 (S/PDIF) Digital Audio Output
hdmi:CARD=Intel,DEV=0
    HDA Intel
    HDMI Audio Output
null
    Discard all samples (playback) or generate zero samples (capture)

```

I dont know that much about sound on linux, but at least HDMI Audio output is listed by aplay? Guess that is a good sign? :)

---

### Post by soniqfreq on 2008-11-12
I have a fresh 8.10 install of Mythbuntu on my Intel DG45ID, G45/x4500 and I have absolutely no sound output through analog or HDMI channels (I have no spdif/optical receiver to test the other digital output).

The sound card is recognized and appears "active" (recognized with snd-hda-intel module loaded).  Alsamixer unmuted.  

MythTV set to ALSA:default for device and mixer with PCM (of course I've tried all the combos in the Setup>General menu. tested with aplay with test .wav files and media apps outside of mythtv, too.  Nothing. not even hiss when cranked up.

I've tried rebuilding ALSA as indicated throughout the forum, compiling 1.0.18rc3 and 1.0.18 (stable) with no luck, following the intel hda sound community doc...nothing.

It seems I am not alone however some say they do have audio working on this board or with the ICH10/STAC92XX chipset. 

Any other ideas I might have missed? Is it just not ready for prime time?  do I need to go back to an alpha build that appears to have been working for someone with this board?

---

### Post by bigslip on 2008-11-13
Audio does work, although it's not perfect. I had trouble also. I had to un-mute everything, I think it turned out to be the headphones that made it work for me.  

I've bounced back and forth between F10 and 8.10 and am running F10/Rawhide now and things are getting better. The video drivers had seen a bunch of updates over the last few weeks but I don't think they have rolled out to the distros yet.

Here is the blog of the Intel developer that is working on the drivers.

[http://virtuousgeek.org/blog/index.php/jbarnes](http://virtuousgeek.org/blog/index.php/jbarnes)

---

### Post by anthonyJC on 2008-11-13
@soniqfreq
Audio works in Kubuntu.
Audio is broke in F10 Preview XFCE.

---

### Post by soniqfreq on 2008-11-16
Well I don't think I'm going to switch over to a Fedora core, and when I load up the Kubuntu Live CD I get this odd resolution where the font is illegible (way to small) and I can't try it out.  

I tried the Unbuntu-desktop edition, tried 32-bit instead of 64-bit, nothing gets that ICH10/STAC92xx analog output going.  Oh well.  I'll leave it to the pros and future releases. At any rate I have given up and reinstalled my Audigy LS (CA0106) pci sound card and disabled the onboard audio for now, not very elegant, but at least I have audio.  

Onto other issues like XV, XVMC, glx, and OpenGL sync timing issues crashing the frontend and getting the analog tuners in my DViCO Fusion HDTV7 working (no analog, only some digital channels).

All I want to do is watch and record my HDTV!

---

### Post by andreiashu on 2008-11-18
I think I should have blamed Intel for its bogus drivers/hardware all the time.
I have Vista now with the original CD drivers (compatible with Vista) and I still got some issues: sound goes away after hibernation, the sound software that came with the driver is very buggy and difficult to configure it right. And i also had some problems with the video in the beginning but after I installed the latest video drivers from Intel's site everything is oki now.

---

### Post by Topfs on 2008-11-19
> **mdalacu said:**
> I have Gigabyte EG45M-DS2H, Live XBMC Beta2 doesn't work. I will try to install first Ubuntu 8.10 and XBMC, so wish me luck. :)
Is anyone else using this motherboard with Ubuntu 8.10 or XBMC?

XBMC Live is based on ubuntu 8.04 thats why it doesnt work currently, hopefully we'll have a pre-release or unstable version of an interpid based XBMC Live, atleast I would want one :)

Anyhow, I use it on ubuntu 8.10 but there are some small random crashes which I think are driver related, hard to tell because some of them could be XBMC aswell as its not extremely stable on interpid, atleast not if you compare it to hardy :)

I am gonna try it on fedora now to see if I can get it to work better over at that side.

Cheers, Tobias from team-xbmc

---

### Post by McLogic on 2008-11-29
Has anyone with the G45 (x4500hd) tried running the new Ubuntu Lunx (GnuLinux) alpha?

[http://cdimage.ubuntu.com/releases/jaunty/alpha-1/](http://cdimage.ubuntu.com/releases/jaunty/alpha-1/)

If it fixes the problems, then we know stable fixes are on the way in 5 months. Please post here and let us know if you have tried the Jaunty (Ubuntu 9.04) Alpha release!

---

### Post by ebike on 2008-12-02
> **anthonyJC said:**
> It will not  be placed in the Intrepid repositories because it requires libdrm 2.4. 

Get mandatory libdrm firstly:
```

http://ppa.launchpad.net/xorg-edgers/ubuntu/pool/main/libd/libdrm/

```
then install, then secondly get the driver :
```

http://ppa.launchpad.net/thjaeger/ubuntu/pool/main/x/xserver-xorg-video-intel/

```

You will still get stability problems because of missing G43/5 stability fix in kernel 2.6.28 (you will still be using 2.6.27.) Virtual consoles are fixed. Use at your own risk (not tested by many people.)

Will this upgrade stop my random segfaults watching HDTV? If so, I will make the effort to compile these.

In fact I tried to compile the libdrm driver but got the following errors on ./configure

> 
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for PTHREADSTUBS... configure: error: Package requirements (pthread-stu
bs) were not met:

No package 'pthread-stubs' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables PTHREADSTUBS_CFLAGS
and PTHREADSTUBS_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.


What else apart from build-essential do I need to build these modules?

---

### Post by Croccydile on 2008-12-07
Unfortunately I still get stability problems in 8.10 with many lockups over time, so I've just relegated the machine to being headless for the time.  I can only hope that 2.6.28 gets ported somehow to 8.10 when its released otherwise I'll just get a nVidia card to fix this mess.

I don't think I can wait for Jaunty to correct these issues, since going through one Alpha already I don't want to mess with the box anymore.  Sorry.  :(

---

### Post by ChaosMonkey on 2008-12-07
Iam using the same board and am trying to get the 1080 to work on my TV. The video works fine on a monitor but appears to be using a invalid config on the TV.

I manually updated xorg.conf to use a lower resolution that was auto discovered in /var/log/Xorg.0.log which works.

When I add a manual Modeline to xorg.conf even a complete copy of the line in Xorg.0.log with a different name it fails. Its acting like it does not know about the added Modeline.

Am I specifying it incorrectly or is there a problem with the intel driver that causes it to only use "discovered" ModeLines?

Any help would be appreciated. 

Iam using ubuntu 8.10 2.6.27-9-generic

xorg.conf ===>

Section "Device"
        Identifier      "Configured Video Device"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
        Modeline "1872x1080" 135.500 1872 1944 1976 2032 1080 1086 1091 1111 -hsync -vsync
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
        Defaultdepth    24

        SubSection "Display"
                Depth           24
                Modes           "1872x1080"
        EndSubSection
EndSection

---

### Post by mathias_sundman on 2008-12-15
I have a Dell E6500 with intel GMA X4500MHD graphics and 1920x1200 display.

Ubuntu 8.10 worked out of the box with 1920x1200 resolution, however both 2D and 3D graphics performance is lousy.

x11perf --aa10text gave me about 21000/sec, and glxgears about 200 FPS.

Changing AccelMode from EAX to XAA in Xorg.conf gave me much better 2D graphics. After that change x11perf reported about 200000/sec, however glxgears remained the same.

I then tried to install Jaunty-Alpha1. After a stock install and a yum upgrade it worked just as bad as 8.10. It was still running a 2.6.27 kernel and had a lot of xorg packages kept back. After a forced upgrade of all packages I was unable to start X at all. Didn't troubleshoot why further today. Instead I moved on and tried to install Fedora Core 10.

And guess what, with Fedora 10 both 2D and 3D graphics worked well out of the box!

x11perf --aa10text gave about 150000/sec with default EAX acceleration.
glxgears now gave about 1200 FPS.

I must now just find out what differs on my ubuntu system and the fedora system that is causing the bad performance on ubuntu.

Any ideas where to look?

---

### Post by farmfield on 2008-12-17
My xorg - stolen & modded from Mandriva - gives me 800 fps.

```
# grafikkort

Section "Device"
    Identifier "intel4500mhd"
    VendorName "Intel Corporation"
    BoardName "Intel 810 and later"
    Driver "intel"
    Option "DPMS"
EndSection

# monitor

Section "Monitor"
	Identifier	"Configured Monitor"
   	Option          "DPMS"
EndSection

# Xorg-ut

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"intel4500mhd"
EndSection

Section "DRI"
	Mode            0666
EndSection

Section "Module"
    Load "dbe" # Double-Buffering Extension
    Load "v4l" # Video for Linux
    Load "extmod"
    Load "type1"
    Load "freetype"
    Load "glx" # 3D layer
    Load "dri" # direct rendering
EndSection
```

There's obvously a problem with the driver and glxgears as - and even though glxinfo reports DRI - it uses a lot of CPU when it should be using the x4500 GPU. There's also no doubt that the card accelerates some 3D very nicely, using compiz I can view full screen video with 3D-windows activated and distorted with the compiz-fusion deformation plug as I flawlessly rotate the whole thingie... Google Earth also perform very good - as long as I turn off compiz.

---

### Post by orduek on 2008-12-18
what is the best driver to use? I have the intel driver and not the i810. Should I try the i810 one?

---

### Post by McLogic on 2008-12-31
> **ebike said:**
> Will this upgrade stop my random segfaults watching HDTV? If so, I will make the effort to compile these.

In fact I tried to compile the libdrm driver but got the following errors on ./configure
> 
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for PTHREADSTUBS... configure: error: Package requirements (pthread-stu
bs) were not met:

No package 'pthread-stubs' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables PTHREADSTUBS_CFLAGS
and PTHREADSTUBS_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details. 



What else apart from build-essential do I need to build these modules?

[SIZE="4"]Do you have "libpthreads-stubs0" installed?[/SIZE] It is for the posix threads. You can find it in synampitc (apt), it is in main (i think).

On main subject:
[Jaunty may save us from this PITA.]("https://wiki.ubuntu.com/JauntyReleaseSchedule")I don't know if the fact that the Debian Import Freeze is past (Dec 25) means that we have a better idea if we will get graphics support in 9.04 ?

---

### Post by cmsj on 2009-01-06
> **orduek said:**
> what is the best driver to use? I have the intel driver and not the i810. Should I try the i810 one?

No, don't use i810, it's a very very old driver. (Actually these days it's quite likely that i810 is just a link to the intel driver).

---

### Post by cmsj on 2009-01-06
> **ChaosMonkey said:**
> 
        Modeline "1872x1080" 135.500 1872 1944 1976 2032 1080 1086 1091 1111 -hsync -vsync


Why 1872? The resolution of a 1080p TV is generally 1920x1080.

I have a G45 running Intrepid and with my Sony TV it properly detects 1920x1080 just by booting the machine with the TV switched on.

(I do have issues with the setup though, but I'll get to those later)

---

### Post by metapaso on 2009-01-06
@anthonyJC

Thanks for the help.

Between then and now I've gone through the steps to compile my own driver and Mesa to fix the 2048 width limitation bug listed in:
[https://bugs.launchpad.net/ubuntu/+source/mesa/+bug/146859](https://bugs.launchpad.net/ubuntu/+source/mesa/+bug/146859)

I've since switched to the intel-gfx-testing drivers ([https://edge.launchpad.net/~intel-gfx-testing/+archive](https://edge.launchpad.net/~intel-gfx-testing/+archive)), and here's what's working:

Dual Monitors + Compiz (1920x1080 and 1024x768)
Xv
EXA

Everything works fairly well.  I get very frequent horizontal artifacts on the DVI output @1920x1080, which appear as a green line about a third of the way across the screen for just a flicker of a second.  

When playing video the tearing on pan is almost intolerable. I tried to enable the XvMC output in mplayer, but I get errors.  Not sure what to do except wait for better drivers.

---

### Post by cmsj on 2009-01-07
> **metapaso said:**
> @anthonyJC
When playing video the tearing on pan is almost intolerable. I tried to enable the XvMC output in mplayer, but I get errors.  Not sure what to do except wait for better drivers.

My understanding is that XvMC is not relevant to this hardware, and only good for accelerating mpeg2 anyway. Intel are working on some APIs and driver support for more generic video acceleration in Linux, but I have no idea how long it will take.

I rather suspect that all you really need to do is find a vblank sync option and turn it on, since that's more likely to be the cause of the tearing than anything else (acceleration would just make the video playback easier, it wouldn't magically make the screen update at the right times)

---

### Post by metapaso on 2009-01-07
> **cmsj said:**
> I rather suspect that all you really need to do is find a vblank sync option and turn it on, since that's more likely to be the cause of the tearing than anything else 

Where do I start to find the vblank sync options?

> **cmsj said:**
> (acceleration would just make the video playback easier, it wouldn't magically make the screen update at the right times)

I thought I read somewhere that the Motion Compensation part of XvMC was specifically designed to help with tearing on pans, etc.  I also thought I read that the the new 2.6 driver (now in RC1 status) will provide a driver for XvMC output, but that will have to wait for xserver 1.6 and probably Mesa 7.3?

I guess I just have to learn to be patient.

---

### Post by igknighted on 2009-01-07
> **mathias_sundman said:**
> I have a Dell E6500 with intel GMA X4500MHD graphics and 1920x1200 display.

Ubuntu 8.10 worked out of the box with 1920x1200 resolution, however both 2D and 3D graphics performance is lousy.

x11perf --aa10text gave me about 21000/sec, and glxgears about 200 FPS.

Changing AccelMode from EAX to XAA in Xorg.conf gave me much better 2D graphics. After that change x11perf reported about 200000/sec, however glxgears remained the same.

I then tried to install Jaunty-Alpha1. After a stock install and a yum upgrade it worked just as bad as 8.10. It was still running a 2.6.27 kernel and had a lot of xorg packages kept back. After a forced upgrade of all packages I was unable to start X at all. Didn't troubleshoot why further today. Instead I moved on and tried to install Fedora Core 10.

And guess what, with Fedora 10 both 2D and 3D graphics worked well out of the box!

x11perf --aa10text gave about 150000/sec with default EAX acceleration.
glxgears now gave about 1200 FPS.

I must now just find out what differs on my ubuntu system and the fedora system that is causing the bad performance on ubuntu.

Any ideas where to look?

Do a jaunty install from the liveCD and try that.  I think you never got the new driver.  Ubuntu is still using 2.4.x for the intel driver, whereas Fedora has 2.5.x.  Many new features and optimizations, especially for the new GPU.

---

### Post by NT4usB on 2009-01-12
...replying so I can read the entire thread at home tonight.
I have a GA-EG41M-S2H running Intrepid and the drivers from the development repos. Analog works but the digital side gives no valid modes or some such error.

---

### Post by murnau on 2009-01-16
Hi! Has anyone tried out the new 2.6.0 drivers that were released yesterday on? Link: [Intel Linux Graphics]("http://intellinuxgraphics.org/")

---

### Post by metapaso on 2009-01-19
> **murnau said:**
> Hi! Has anyone tried out the new 2.6.0 drivers that were released yesterday on? Link: [Intel Linux Graphics]("http://intellinuxgraphics.org/")

looks like the ppa builds even for jaunty are failing? Requires libdrm >=2.4.3...

[https://launchpad.net/~intel-gfx-testing/+archive](https://launchpad.net/~intel-gfx-testing/+archive)




  Which kernel, xorg and server version are required for this to work?

---

### Post by densou on 2009-01-20
> **metapaso said:**
> Which kernel, xorg and server version are required for this to work?

they always suggest to use what listed on 'driver components' section, so kernel 2.6.28 + patches [I assume .28.1 includes the fixed drm], Mesa Build of January 2009, X-Server 1.6.0, libdrm 2.4.4

No words regarding Xorg, so 1.5.3 should be enough. ;)

---

### Post by trapperjohn on 2009-02-02
I have an Asus P5Q-VM board and get annoying horizontal lines all across the screen. I already tried the testing drivers from launchpad but no improvement (except a correct screen resolution in gdm ...).

I made a small video (~6 MB) to show these lines (as it is hard to describe):
[http://data.florianhaskamp.de/g45issues.avi](http://data.florianhaskamp.de/g45issues.avi)

The system is hardly usable in this state ... 
No problems in Vista :(

Any ideas?

---

### Post by trapperjohn on 2009-02-03
Just for information:
I have a Viewsonic VX2025WM display and Xorg.0.log says, it uses the following mode:

Modeline "1680x1050"x0.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz)

When I run PowerStrip in Windows, it gives me the following modeline:

Modeline "1680x1050" 146.400 1680 1784 1960 2240 1050 1053 1059 1089 +hsync +vsync

But using this one together with "NoDDC", the Intel driver says, there is no valid mode. :(

Edit: When I select for example 1440x900 in Gnome's resolution tool, the annoying lines are gone (but of course this is not a solution ...)

---

### Post by NT4usB on 2009-02-03
fwiw, I have the VX2035wm version of that monitor and I get no screens found and/or no valid modes too. Same on my Q20 so it's not the monitor.
I finally found an xorg that worked on the VGA side but the graphics are way jacked.
No screens found using the DVI side. Tried all manor of HDMI-1, TMDS-1 associations.
Gave up and put a Nvidia card in it.

ed: it's on a G41 chipset. Same x4500 but no HD, iirc.

---

### Post by trapperjohn on 2009-02-03
Here is some interesting talk about the current state of the intel driver and G45:
[http://lists.freedesktop.org/archives/xorg/2009-January/042513.html](http://lists.freedesktop.org/archives/xorg/2009-January/042513.html)

I think, nVidia is really the best option for the moment, if one wants to watch tearing-free video, etc. Sad but true. :rolleyes:

---

### Post by rstuart4133 on 2009-02-03
I have just returned from Linux Conference Australia, and since I own an X4500HD I took the time to ask Keith Packard "what version will the tearing problem be fixed".  The reply was: "no idea".  I suspect I looked a little surprised at the terse response, and he added a few moments later "look - it is a really hard problem".

Notice I wasn't asking for a date.  It was really an indirect way of asking "do you consider this problem severe enough that there is some point you won't ship another version until it is fixed".  The answer was a resounding "no".

Which isn't to say Intel isn't doing a huge amount of work on this problem.  From the talks at LCA, they are.  There was one particularly good one from the guy who writes the firmware for the GPU.  He works in assembler, and from looking at it, it is assembler from hell.  But after listening to them for a while, you could not but help get the impression Intel is learning to do 3D GPU stuff, and what you are seeing is them stumbling around trying to get a grip on the problem how best to solve it.  For example, NVidia has written a C like HLL for their GPU, but it is closed source.  Apple has done an open source version of the same thing, which Intel could use but seems to be unaware of.  

And it is a big problem.  Intel is re-engineering most parts of the video stack - from Cario at the top, to GEM and GPU code at the bottom.  So nothing is going to happen fast, although I would expect a solution in the next 12 months or so.  The good news is Intel is doing their stumbling about in an "open source" way.  I have no doubt they will find their way, and once they do the entire open source world will have learn with them how to do it too.  Needless to say I am happy to stick with Intel for a while.

---

### Post by densou on 2009-02-14
> **rstuart4133 said:**
> And it is a big problem.  Intel is re-engineering most parts of the video stack - from Cario at the top, to GEM and GPU code at the bottom.

Don't forget that UXA+dri2 are under development too....it seems UXA will discard both XAA & EXA with GEM enabled, but it's a long term hypotetic thought

my GMA950 hasn't that tearing issue at all .... it's a obsolete GPU but actually it works better than other Intel counterparts. (with compiz disabled of course, metacity runs smooth)

---

### Post by trapperjohn on 2009-02-14
Right, the GMA950 still has the overlay adapter which works without tearing. I should have bought a less expensive board with this chipset, too. You live, you learn.

I've had enough of Intel and bought a 7300GT for a handfull of Euros which works like a charm ...

---

### Post by Croccydile on 2009-02-27
(minor rant henceforth)

Well, despite progress being made I have to throw the towel in on this one myself.  I have not been able to get the integrated video to work reliably (hard to believe its 6 months already now) and it has really scared me away again from integrated video boards, seems that the GMA X4500HD has had issues outside of Linux in general.

With hindsight its easy, but now I wish I bought a G33 based board even if it was older at the time, and they are still being sold today so I imagine I screwed the pooch buying bleeding edge tech, which surprised me given that previous chips I've tested (852GM, 915G, 945G) worked fine.

To make matters worse the system seems to randomly kernel panic for no reason every so often, among the fact I have to dummy down the video to VESA video for both the fbconsole and x.org, since it hardlocks everytime now otherwise.

*sigh* My other system with its Gigabyte GA-EP45-UD3P sitting right next to it is very stable.

---

### Post by mkarnicki on 2009-03-03
Deleted the content. X4500HD on Toshiba U400-14z works with Jaunty 9.04!

---

### Post by rasmus91 on 2009-03-13
It seems that somebody have had some luck solving the performance problems by running UXA instead of EXA: [http://ubuntuforums.org/showthread.php?p=6887280#post6887280]("http://ubuntuforums.org/showthread.php?p=6887280#post6887280")

---

### Post by rasmus91 on 2009-03-14
Okay, I just upgraded to the alpha, And my performance problems has been solved!

before i get 250 fps now i get 1130+ with glxgears

---

### Post by New Reply on 2009-03-24
> **rasmus91 said:**
> Okay, I just upgraded to the alpha, And my performance problems has been solved!

before i get 250 fps now i get 1130+ with glxgears

I tried upgrading to 9.04 alpha 6 but X won't even load during installation.  Mobo is Gigabyte GA-EG45M-DS2H.

---

### Post by bigsur1 on 2009-03-24
> **metapaso said:**
> 
I've since switched to the intel-gfx-testing drivers ([https://edge.launchpad.net/~intel-gfx-testing/+archive](https://edge.launchpad.net/~intel-gfx-testing/+archive)), and here's what's working:

Dual Monitors + Compiz (1920x1080 and 1024x768)
Xv
EXA

Everything works fairly well. 

I also try to set up dual screen / dual display on the Gigabyte GA-EG43M-S2H Board. I'd like to connect two TFTs via DVI and VGA.

Do I have to configure xorg by hand, or is there a config-tool available as I was used from nvidia-xconfig for example?

---

### Post by densou on 2009-04-03
> **rasmus91 said:**
> before i get 250 fps now i get 1130+ with glxgears

glxgears isn't a good bench, I'd suggest to try:
/usr/lib/xscreensaver/glblur -window -fps

> **New Reply said:**
> I tried upgrading to 9.04 alpha 6 but X won't even load during installation.  Mobo is Gigabyte GA-EG45M-DS2H.

Try the beta with the latest updates (repos provides mesa 7.4 today !)

> **bigsur1 said:**
> Do I have to configure xorg by hand, or is there a config-tool available as I was used from nvidia-xconfig for example?

well, never had to set up a dual monitor system since I use Ubuntu (from 7.10), maybe Jaunty -beta- should be able to recognize all.
[http://intellinuxgraphics.org/dualhead.html](http://intellinuxgraphics.org/dualhead.html)
'grandr' is the one and only GUI for xrandr ;)

---

### Post by glimpse79 on 2009-04-21
I'm using ubuntu RC 9.04 and i have a lot of horizontal tearing in video playback; not any solution yet? ... i'm so frustrated :(

---

### Post by comcute on 2009-04-22
glimpse79, [http://ubuntuforums.org/showpost.php?p=7118675&postcount=12](http://ubuntuforums.org/showpost.php?p=7118675&postcount=12)

---

### Post by densou on 2009-04-25
I have just tested some stuff.
My 2 cents: UXA wasn't really worthwhile because I had an awful video output -x11, xv, xvmc- compared to EXA (the opposite on HD sources!).

So I upgraded to [new 2.7.0 release]("http://launchpad.com/~intel-gfx-testing/+archive") but I didn't see any quality improvement (SD sources -mp4, avi, flv and so on-).

How did I settle this annoying nuisance ? Got the 0.9.5 gnome mplayer .deb and :guitar:

shame on default Ubuntu's repos again :(

---

### Post by Croccydile on 2009-04-26
I'm going to try to clean reinstall 9.04 sometime later, see how things go for me.  I've pretty much had the machine running sans X.org for months because of horrible stability.  I would have it run for months without issue and the moment I would try to start X.org problems would show up.

Hopefully the machine will last more than a few hours now without spontaneous reboots.

---

### Post by kingmoffa on 2009-04-28
Tearing for me with jaunty G45 using mythtv

---

### Post by densou on 2009-04-30
> **kingmoffa said:**
> Tearing for me with jaunty G45 using mythtv

Read [this thread]("http://ubuntuforums.org/showthread.php?t=1130582"), lad :popcorn:

plus I'd strongly recommend to upgrade Gnome Mplayer (latest: 0.9.5), I don't like much Totem :P

---

### Post by CoreTech on 2009-05-02
The only program that gives tearing free video is XBMC with vsync setting enabled.

---

### Post by densou on 2009-05-04
> **CoreTech said:**
> The only program that gives tearing free video is XBMC with vsync setting enabled.

Have you tried to fix MTRR ranges first (just upgrading kernel solves tearing at >90%) ?

---

### Post by glaze on 2009-05-04
My tearing went away with xserver-xorg-video-intel 2.7.0.

---

### Post by ravy on 2009-06-24
> **glaze said:**
> My tearing went away with xserver-xorg-video-intel 2.7.0.

This may be a dumb question ... but how does one find out what version of the xorg intel driver is installed?  I'm currently running Ubuntu 9.04, so I guess it would be whatever the stock version of the intel driver that comes with that.  Also, is there an easy way to compile the 2.7.0 version of that driver? ... it seems as though some of the libraries are not fully up to the version that the xorg intel 2.7.0 driver source requires.  Or better yet, is there a .deb file of it somewhwere?

---

### Post by trapperjohn on 2009-06-25
> **ravy said:**
>  Or better yet, is there a .deb file of it somewhwere?

Yes, look here:
[https://launchpad.net/~ubuntu-x-swat/+archive/x-updates/](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates/)

Didn't help in my case though.

---

### Post by Junkieman on 2009-09-26
> **ravy said:**
> how does one find out what version of the xorg intel driver is installed?

Hi, For future use, you can use Synaptic to check the version, or run this in a terminal:

```
~$ apt-cache dump | grep video-intel
  Depends: xserver-xorg-video-intel (null)
  Package: xserver-xorg-video-intel-modesetting
  Depends: xserver-xorg-video-intel (null)
  Depends: xserver-xorg-video-intel (null)
  Package: xserver-xorg-video-intel-dbg
  Depends: xserver-xorg-video-intel 2:[COLOR="Red"]**2.4.1**[/COLOR]-1ubuntu10

```

---

### Post by emeraldgirl08 on 2010-01-29
I'm keeping my hopes up. I have a Lenovo T400 with X4500HD and the performance is spotty. Is there anyone with a T400 and Intel graphics that has good things to say about any distro that will work with this chipset? I would love to keep a linux distro on my T400 but when I switch to XP Pro it can scroll through web pages with no problem. I do have 9.10 working very well on my R51e (another user can't seem to get his to work- not sure why) and am keeping it on there for the moment.

---

