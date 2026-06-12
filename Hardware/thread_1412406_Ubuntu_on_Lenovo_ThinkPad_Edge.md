---
title: "Ubuntu on Lenovo ThinkPad Edge"
date: 2010-02-21
forum: Hardware
---

### Post by mutvik on 2010-02-21
Has anyone tried? I could not find anything on Google.

The laptop in question: [http://shop.lenovo.com/us/landing_pages/thinkpad/2010/Edge](http://shop.lenovo.com/us/landing_pages/thinkpad/2010/Edge)

---

### Post by finite9 on 2010-02-25
it's too new.  Not even released in most shops here in Sweden.  I'm looking at buying this and as long as the WiFi Link 1000 is supported by Lucids kernel im fine.  I am a bit suspect on the performance of the SU7300 CULV chip, but I only need the laptop for surfing/email/browsing photos and playing 720p films, which it should cope with, but it is possible that multiple apps open at the same time makes the desktop feel slow, hence my suspicion.

but with 6-8 hrs battery and thinkpad-ish keyboard, im all for it!  I use a Thinkpad T61p at work, and it's the best laptop i've ever used, but cannot afford it personally, so the Edge is a great option.

I recently used an Atom N270 based Samsung NC10 with winxp... it worked, and teh desktop "feel" when running one app at a time was pretty good, but I installed Nero on it and it took 1 whole hour to install the application!

If this is to be your main computer, it might be a bit underpowered for more serious tasks.  This is going to be my "surfing" laptop, and I already have a Home Server for very processor/memory/disk intensive tasks, so it won't really matter for me if I cannot photo edit or transcode etc on this laptop.

---

### Post by Lantau on 2010-02-27
I just bought one about 2 hours ago and am currently running 9.10 from a USB stick. So far wireless is fine, as is sound. Volume and brightness buttons OK. Camera not yet working (hence my check in the forums). I'll let you know as I progress.

---

### Post by finite9 on 2010-02-27
please do let us know what the performance is like with the SU7300 processor.  Can you run firefox/thunderbird/movie player at the same time without slowdown?  Does the desktop "feel slow".  How much battery time do you get during average use?

---

### Post by MatthiasKranz on 2010-03-11
Hi all,

the ThinkPad Edge (type: 0196-2eg) works fine for me with the latest Karmic... 

WLAN, UMTS, camera, Bluetooth, 3D acceleration, sound, etc. all do work fine. 

GPS is not (yet) working.

Best,
M.

---

### Post by fierywater on 2010-03-12
No word on the AMD version, is there?

---

### Post by xasdfx on 2010-03-12
I bought the AMD version today, but the problem is WLAN doesn't work with 9.10.
Do you know what to do?
Thanks

---

### Post by grmela on 2010-03-16
Hello,
I'm currently trying to get the AMD version (model 0197-6LG) working under Karmic. I cannot get the Bluetooth and WiFi to work. Bluetooth is not present in lspci/lsusb though it works under Windows.

I've installed the WiFi driver from the Realtek site (Realtek 8192SE, version 0015) but I don't know how to enabtle the wlan interface. It is apparently disabled after the driver loads into the kernel. When I click the "Enable WiFi" button in Gnome Network Manager, nothing happens. See the dmesg output below:

```
[ 4667.662276] rtllib_crypt: registered algorithm 'NULL'
[ 4667.662282] rtllib_crypt: registered algorithm 'TKIP'
[ 4667.662285] rtllib_crypt: registered algorithm 'CCMP'
[ 4667.662288] rtllib_crypt: registered algorithm 'WEP'
[ 4667.662290] 
[ 4667.662291] Linux kernel driver for RTL8192 based WLAN cards
[ 4667.662294] Copyright (c) 2007-2008, Realsil Wlan Driver
[ 4667.663448] rtl819xSE 0000:03:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[ 4667.663502] rtl819xSE 0000:03:00.0: setting latency timer to 64
[ 4667.663789] Memory mapped space start: 0xd0300000 
[ 4667.663943] Adapter(8192SE) is found - DeviceID=8172
[ 4667.669148] =========>dm_InitRateAdaptiveMask: bUseRAMask=0
[ 4667.725098] udev: renamed network interface wlan0 to wlan2
[ 4704.821938] rtl819xSE 0000:03:00.0: firmware: requesting RTL8192SE/rtl8192sfw.bin
[ 4704.941505] rtl8192_SetWirelessMode(), wireless_mode:10, bEnableHT = 1
[ 4704.951592] ===>rtllib_start_scan()
[ 4704.964540] ADDRCONF(NETDEV_UP): wlan2: link is not ready
[ 4705.675487] GPIOChangeRF  - HW Radio OFF
[ 4705.720064] ============>sync_scan_hurryup out

```

The *rtl8192_SetWirelessMode(), wireless_mode:10, bEnableHT = 1* is the moment when I click the button. I've tried to reboot, recompile the driver, reload it but it always hangs there.

The Fn+F9 keystroke doesn't seem to work either.

Does anyone know a solution to this problem? The laptop works (excluding WiFi & Bluetooth) great under Linux and has even a better power consumption than under Windows, I really don't want to use Windows on it.

---

### Post by finite9 on 2010-03-18
On the Lenovo forums they say that you should try Ububntu 10.04 as the driver for the Wlan is not in the kernel used by Ubuntu 9.10.

10.04 gets release next month so the beta should be out soon.  Once it hits beta it should be pretty stable to use daily.

---

### Post by Paul_K on 2010-03-18
I am running Ubuntu 10.04 on my edge right now.  Out of the box it saw the wlan card and I was able to get an IP via dhcp.  I could ping myself but not my gateway.  

Works great after I downloaded the latest drivers from realtek:

[http://www.realtek.com/downloads/searchView.aspx?keyword=linux](http://www.realtek.com/downloads/searchView.aspx?keyword=linux)

click on "RTL8192SE (Software)"


sudo apt-get install build-essential linux-source-2.6.32   [10.04]
sudo apt-get install build-essential linux-source-2.6.31   [9.10]

tar -xzvf  rtl8192se_linux_2.6.0015.0127.2010.tar.gz
cd rtl8192se_linux_2.6.0015.0127.2010

sudo make
sudo su
in root shell:
  make install
  modprobe r8192se_pci

except for the change in linux source version this worked for me in 9.10 as well but the drivers were older and flakier.  These drivers should be better

I can't find the instructions I based these on.  Be sure to sudo su before the make install, sudo make install didn't work for me.

Good Luck

-PaulK

---

### Post by alex-uk on 2010-03-18
Paul_K, I'm also using an edge and 10.4, but can't get it to work. I've followed your instructions, but still no joy.

Here is what I get in the log:
```
Mar 18 21:21:54 ricardodaforce kernel: [   80.274945] rtl8192_SetWirelessMode(), wireless_mode:10, bEnableHT = 1
Mar 18 21:21:54 ricardodaforce kernel: [   80.285310] ===>rtllib_start_scan()
Mar 18 21:21:54 ricardodaforce kernel: [   80.287323] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Mar 18 21:21:56 ricardodaforce kernel: [   81.430727] GPIOChangeRF  - HW Radio OFF
Mar 18 21:21:56 ricardodaforce kernel: [   81.430748] -------------->rtl8192se_cancel_hw_scan()scan abort start...
Mar 18 21:21:57 ricardodaforce kernel: [   82.563233] ================>r8192_wx_set_scan(): hwradio off
Mar 18 21:22:21 ricardodaforce kernel: [  107.174858] rtl8192_SetWirelessMode(), wireless_mode:10, bEnableHT = 1
Mar 18 21:22:21 ricardodaforce kernel: [  107.185255] ===>rtllib_start_scan()
Mar 18 21:22:21 ricardodaforce kernel: [  107.187110] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Mar 18 21:22:22 ricardodaforce kernel: [  107.430736] GPIOChangeRF  - HW Radio OFF
Mar 18 21:22:22 ricardodaforce kernel: [  107.430751] -------------->rtl8192se_cancel_hw_scan()scan abort start...
Mar 18 21:22:22 ricardodaforce kernel: [  107.594720] rtl8192_SetWirelessMode(), wireless_mode:10, bEnableHT = 1
Mar 18 21:22:22 ricardodaforce kernel: [  107.605053] ===>rtllib_start_scan()
Mar 18 21:22:22 ricardodaforce kernel: [  107.606817] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Mar 18 21:22:24 ricardodaforce kernel: [  109.430723] GPIOChangeRF  - HW Radio OFF
Mar 18 21:22:24 ricardodaforce kernel: [  109.430744] -------------->rtl8192se_cancel_hw_scan()scan abort start...
Mar 18 21:22:26 ricardodaforce kernel: [  111.561603] ================>r8192_wx_set_scan(): hwradio off
```

Any ideas? Its a great little laptop and I really want to get wireless working!

Thanks,

Alex

---

### Post by grmela on 2010-03-18
Alex, I had exactly the same problem as you. I tried nearly everyting on the Ubuntu Karmic to get the adapter working but nothing helped. Recompiling the drivers, updating system, updating kernel, ...etc

What solved the WiFi problem? It's weird but it was solved simply by rebooting to Ubuntu Lucid Alpha 3 Live CD. The WiFi didn't work there either but after booting back to Karmic, everything was fine, even Bluetooth started working. In fact, I'm writing right now from my Edge on a WPA2 WiFi network!

---

### Post by highlandsun on 2010-03-19
Makes sense. These devices have software-enabled kill switches. If the driver is too old and doesn't enable the switch, then the device won't power up. I had that issue on my HP dv5z as well, until I got a newer rev of the driver.

Just got an AMD Edge here today, installing Lucid Alpha3 on it at the moment.

Beta1 actually.

It comes with the Realtek driver, and the driver sees one of the wifi networks in the area. But it doesn't see my network, and it looks like the network-manager app doesn't support WPA-Enterprise. What's up with that?

---

### Post by highlandsun on 2010-03-20
Ah never mind. The driver that Lucid ships with doesn't work, but replacing it with the one from the realtek web site it works fine. You just have to find and delete the Lucid driver, otherwise even though you "make install" your own, it won't be loaded (because there are actually 3 different copies of the driver under /lib/modules).

---

### Post by grmela on 2010-03-20
> **highlandsun said:**
> Ah never mind. The driver that Lucid ships with doesn't work
And that's exactly the weird thing. The WiFi didn't work there but it solved the disabled wireless killswitch problem (after booting back to Karmic with). Well, maybe I should look at the Lucid changelog to find out what related has changed.

---

### Post by finite9 on 2010-03-22
isn't this only an issue if you've bought the AMD version of the Thinkpad Edge?  The Intel version comes with an Intel WiFi Link 1000 adapter, and that should have no issues with the Ubuntu 10.04 kernel driver.

---

### Post by highlandsun on 2010-03-24
Yes, this is only an issue on the AMD version.

By the way, there's a ton of good info in this thread:

[http://forum.notebookreview.com/showthread.php?t=456688](http://forum.notebookreview.com/showthread.php?t=456688)

I downgraded back to Karmic because Lucid always said "disks need to be checked" on every boot, even though it was always cleanly shut down. But I kept the 2.6.32.9 kernel that I built for Lucid with the DSDT patch. The machine is now running very well with all these tweaks applied.

---

### Post by grmela on 2010-03-24
What is your power consumption with the DSDT patch? Powertop without the patch reports something around 20-22W what is quite high (~2 hours on 4-cell).

---

### Post by Zetheroo on 2010-03-26
Could those of you who have a Lenovo Edge and have tried Ubuntu on it let us know the following information:

1. Output of lspci

2. Version on Ubuntu used 

3. What worked out of the box and what did not work

This way users will be able to get a clear picture of what does and does not work.

;)

---

### Post by tengteng on 2010-03-26
hi everybody i also have a thinkpad edge amd version and i can't turn on the wifi in lucid beta1.  i've been reading this thread and tried paul_k's instructions but still no wifi. in network manager it still says wireless networks disconnected. Maybe im doing something wrong. I also dont know how to do highlandsun's suggestion of finding and deleteng the lucid driver in lib/modules
I'm dual booting with windows 7 starter now and it works there.. Also, in case its relevant, im using 2.6.32-17-generic-pae kernel and it sees 3.7 out of the 4 gigs i put in. 
I'd rather plug the lan cable in Lucid than use wifi on windows but it would be perfect if i can also use wifi in lucid.  
Hope somebody may be able to help.  Thanks!

---

### Post by Zetheroo on 2010-03-26
> **tengteng said:**
> hi everybody i also have a thinkpad edge amd version and i can't turn on the wifi in lucid beta1.  i've been reading this thread and tried paul_k's instructions but still no wifi. in network manager it still says wireless networks disconnected. Maybe im doing something wrong. I also dont know how to do highlandsun's suggestion of finding and deleteng the lucid driver in lib/modules
I'm dual booting with windows 7 starter now and it works there.. Also, in case its relevant, im using 2.6.32-17-generic-pae kernel and it sees 3.7 out of the 4 gigs i put in. 
I'd rather plug the lan cable in Lucid than use wifi on windows but it would be perfect if i can also use wifi in lucid.  
Hope somebody may be able to help.  Thanks!

Would you mind telling us what your lspci output is? And is everything else working except for your wifi?

---

### Post by tengteng on 2010-03-27
> 00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge
00:01.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (int gfx)
00:05.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 1)
00:07.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 3)
00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [AHCI mode]
00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:12.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:13.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3c)
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS780M/RS780MN [Radeon HD 3200 Graphics]
01:05.1 Audio device: ATI Technologies Inc RS780 Azalia controller
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 03)
03:00.0 Network controller: Realtek Semiconductor Co., Ltd. Device 8172 (rev 10)Heres the lscpi.

I was able to get the wifi working already... ended up using sudo nautilus search in /lib/modules and sure enough there were 3 rtl8192se files there. wifi worked after those were deleted.  

I tried suspend and it worked too. Didn't try hibernate and the webcam. Regarding its bluetooth, if i shut down windows 7 with it turned on it will be on when i boot into Lucid. And vice versa.  So I guess i'll be using Win7 as my glorified bluetooth switch.. :D

Oh yeah.. acpi -V says Thermal 0= 26.8 celsius so i guess there's something wrong there if it refers to the cpu temp.

Anyways, Lucid is running fine so far. No freezes and other weird stuff.

---

### Post by highlandsun on 2010-04-01
> **grmela said:**
> What is your power consumption with the DSDT patch? Powertop without the patch reports something around 20-22W what is quite high (~2 hours on 4-cell).

Sorry, powertop triggers a kernel panic on my 2.6.32.9 kernel. I'll have to try a newer kernel.

---

### Post by gkkg on 2010-04-02
I installed Lucid beta on my Intel Edge. The one problem I have is with sound: at first all worked as it should, until I hit the mute key. After that, I get sound coming out from internal speakers and headphones at the same time, or from speakers only when headphones plugged in. Tried restarting, but problem persists.

Suspend and hibernate work fine, I haven't had a chance to check wireless yet. Webcam works.

I have had the battery state indicating 8 hours after some tweaking with powertop and dimming the screen all the way down.

lspci:

00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 03)
00:1c.5 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M-E LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
03:00.0 Network controller: Intel Corporation WiFi Link 1000 Series
05:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 03)

---

### Post by finite9 on 2010-04-07
Just got my tp EDGE 13 (Intel version) yesterday in matte black casing :)

I installed Win7 to see what it was like...  I was surprised that there was stuttering on the desktop when moving windows/opening applications!  I thought Win7 was better than Vista in respect to low powered laptops...oh well.  So I booted into Ubuntu 10.04 beta, and what a difference!  The desktop is very snappy even with full compiz compared to Win7.  Haven't had chance to test everything yet but once I do i'll put it up on the Laptop testing page.

By the way, was VERY pleased to see that the webcam worked OOTB as well as audio over HDMI!! But I had to select the correct output in the Sound options before I got audio over HDMI.

---

### Post by alex-uk on 2010-04-08
I had got Wifi to work fine following the instructions earlier, but it looks to have broken after the Beta 2 update.

Wireless networks are found and can be connected to, but after about 30 seconds the connection is lost (although it still says it is connected). Trying to reconnect fails until after a reboot.

Anyone else had this problem?

Anyone know a solution?

Alex


***** UPDATE *****
I have managed to fix it...

sudo nautilus and searched for any rtl8192se files in /lib/modules. Deleted them.
Installed fresh drivers from Realteck as per instructions on page 1.
Wireless connected straight away and stayed connected.
Rebooted just in case! Working fine ever since :-)

---

### Post by gkkg on 2010-04-17
If anyone has the same problem with sound I mention above (sound in both headphones and speakers), a fix can be found here:
[https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/549289]("https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/549289")

---

### Post by vickoxy on 2010-04-18
Hi,
i plan to buy this laptop. I have some questions:
1) Is it really (amd processor) capable to be used as main computer (+ external dvd drive)?
2) Should i buy it if i intend to use linux as main system?
3) How high is fan/noise level? (i use dell mini10v-fanless, and macbook white - has no disturbing noise leve)

---

### Post by ppafin on 2010-04-18
> **vickoxy said:**
> Hi,
i plan to buy this laptop. I have some questions:
1) Is it really (amd processor) capable to be used as main computer (+ external dvd drive)?
2) Should i buy it if i intend to use linux as main system?
3) How high is fan/noise level? (i use dell mini10v-fanless, and macbook white - has no disturbing noise leve)

I think you should prefer intel version. I have 13" Intel version running ubuntu 9.10, no show stoppers, but audio and integrated 3G are pain. Gobi2000 firmware loading is not yet working without tweaking and audio is unable to mute speakers with headset attached.

Noise level is nice, hardly nothing can be heard. Display is awesome, but touchpad is a bit in a way when using mouse buttons bellow it.

---

### Post by vickoxy on 2010-04-18
> **ppafin said:**
> I think you should prefer intel version. I have 13" Intel version running ubuntu 9.10, no show stoppers, but audio and integrated 3G are pain. Gobi2000 firmware loading is not yet working without tweaking and audio is unable to mute speakers with headset attached.

Noise level is nice, hardly nothing can be heard. Display is awesome, but touchpad is a bit in a way when using mouse buttons bellow it.

Thanks for answer. I openned here one new thread:

[http://ubuntuforums.org/showthread.php?t=1457175](http://ubuntuforums.org/showthread.php?t=1457175)

Well, i am inerested in amd version-i can get it for 399 EUR with 2GB Ram. And i have 2GB extra. So at the end i could have 4GB Ram. And the cheapest Intel version goes up to 600-650 EUR-and that is actually too expencive now for me.

Thanks

---

### Post by Brianspilner on 2010-05-01
hello!

&#305; have recently bought edge 13 amd version and installed 9.10ubuntu.

with skype 2.1 &#305; have the camera work&#305;ng ootb but not the mic. then i have installed pulse audio and it worked after restart (including sound recorder), but after talking on skype for afew minutes or less, it stoppes working.

all is fine after reboot and after the first call it stoppes again..

any ideas ??

---

### Post by highlandsun on 2010-05-02
Looks like the same thing happening here. No ideas yet, sorry.

---

### Post by Brianspilner on 2010-05-03
I have foundthis tutorial which allowed me to use trackpoint middle button scrolling, but the second part which is about press-to-select did not work for me cause theres no such file.. any ideas about that?

```
1. Introduction

The TrackPoint is the red nub in the middle of the keyboard and the three buttons right below the keyboard. By default Press-To-Select, the process of pushing down on the TrackPoint to click, is turned off. Also, by default the TrackPoint's middle click performs the Paste function.

In this tutorial I will describe how to adjust these settings activate the middle click scroll and Press-To-Select similar to Windows.

2. Configure TrackPoint Middle Mouse Scroll

I wanted to configure the middle click on the TrackPoint to scroll just like in Windows so I used the following commands to achieve it.

2.1: Find the ID number for the TrackPoint

The first step is to find the xinput id number for the IBM TrackPoint. Run the following command.

xinput list

 

You should receive all the available devices for xinput. One of the devices should say:

"TPPS/2 IBM TrackPoint"    id=9    [XExtensionPointer]
    Type is MOUSE
    Num_buttons is 5
    Num_axes is 2
    Mode is Relative
    Motion_buffer is 256
    Axis 0 :
        Min_value is -1
        Max_value is -1
        Resolution is 1
    Axis 1 :
        Min_value is -1
        Max_value is -1
        Resolution is 1

 

Or something very similar. The "id=#" is the important number we will be using in the following commands. Later it will save the headache of typing that very long device name.

2.2: TrackPoint Middle Mouse Scroll

Next run the following commands to enable the middle mouse scroll.

xinput set-int-prop # "Evdev Wheel Emulation" 8 1
xinput set-int-prop # "Evdev Wheel Emulation Button" 8 2
xinput set-int-prop # "Evdev Wheel Emulation Timeout" 16 200

*** Replace # with the id number for the TrackPoint from the previous command.

Now you should be able to middle scroll by pressing the middle mouse button for the TrackPoint and moving the TrackPoint up and down.

3. Enable Press-To-Select

Press-To-Select is the process on pushing down on the TrackPoint to click on objects.

In the directory "/sys/devices/platform/i8042/serio1/serio2/" There is a file called "press-to-select". That is the file we will be focusing on.

3.1: Change directory

Open up the terminal and change the directory to "/sys/devices/platform/i8042/serio1/serio2/"

cd /sys/devices/platform/i8042/serio1/serio2/

 

3.2: Change Permissions of "press-to-select"

Change the permissions of the "pres-to-select" file to allow others modify the file.

sudo chmod o=rw ./press_to_select

 

3.3: Turn on/off Press-To-Select

To turn on/off Press-To-Select is just a matter of adding a 1 or 0 to the file.

~Turn Press-To-Select On~
echo -n 1 >  /sys/devices/platform/i8042/serio1/serio2/press_to_select

 

~Turn Press-To-Select Off~
echo -n 0 >  /sys/devices/platform/i8042/serio1/serio2/press_to_select

 

Now you should be able to click by pushing straight down slightly on the TrackPoint.

```

---

### Post by jasonhoekstra on 2010-05-05
Thank you!!! This worked for my Thinkpad R61i after upgrading to Ubuntu 10.04 LTS (Lucid Lynx).  After applying the 2.2 commands as mentioned, the middle mouse button now scrolls pages ... great and thank you!!

---

### Post by LordChaos73 on 2010-06-03
Hi all,

Bought the Thinkpad Edge 13 a few weeks ago (Intel model - 01962EG), here's what worked out of the box on 10.04 x86_64:

1. Wireless networking works fine, although the adapter doesn't detect my wireless N access point at home, need to look into that ( I have the same issue when running Windows 7 on this laptop)
2. Webcam
3. Sound, including mic
4. Suspend / Resume
5. Media player keys, brightness keys, volume keys

What didn't work:

1. Qualcomm Gobi 2000 WWAN adapter, I haven't looked into this yet, since I don't use it
2. When a heaphone is plugged in, there's still sound coming out of the speakers. Add the following line to /etc/modprobe.d/alsa-base.conf and reboot your machine to fix this:

```
options snd-hda-intel model=olpc-xo-1_5
```

3. Static noise and hissing in the background when a headphone is plugged in, this is OS independent and unfortunately looks like a design issue. I am in contact with Lenovo support on this, for me this is a major issue.
4. Wireless "kill switch" key
5. No Bluetooth adapter is detected
6. Multitouch, including two-finger scrolling
7. Trackpoint middle button, see post above this one

Output of lspci:

```
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 03)
00:1c.5 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M-E LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
03:00.0 Network controller: Intel Corporation WiFi Link 1000 Series
05:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 03)
```

Don't forget to update the BIOS to the latest version:

[http://www-307.ibm.com/pc/support/site.wss/MIGR-74581.html](http://www-307.ibm.com/pc/support/site.wss/MIGR-74581.html)

Regards,

Eric

---

### Post by grmela on 2010-06-03
Thanks for the headphone jack solution. My AMD Edge 13 works nearly perfectly after that (excluding the wireless killswitch and occasional lockups due the buggy WiFi driver).

With the DSDT patch (I had to recompile the kernel) and the latest BIOS, I got abot 17-19W power consumption which gives me about 2+ hours runtime. Nearly the same as under Windows.

Offtopic: Does anyone have problem with Lenovo battery gauge under Windows 7 saying "Battery not installed"? The integrated Windows indicator works great but the Lenovo's one reports this error. My drivers and ThinkVantage software are up-to-date.

---

### Post by LordChaos73 on 2010-06-03
How do you check on your power consumption ? I get about 4,5 to 5 hrs of battery (wireless surfing, office tasks).

---

### Post by grmela on 2010-06-03
Using powertop or just simply by clicking the Gnome battery indicator. There are some battery information like number of cycles, capacity, and also the current power consumption displayed.

---

### Post by anna_vt on 2010-06-05
> **highlandsun said:**
>  But I kept the 2.6.32.9 kernel that I built for Lucid with the DSDT patch. 

I have just got a ThinkPad Edge 13 (AMD) and installed Lucid on it.  I am having problems with it just crashing - goes to a blank screen.  So far this has happened frequently when the mains power is connected, but not when running on battery power.

I'm guessing that the power management is causing these crashes. Do you think that I need use the DSDT patch mentioned above? 
I have read [this page]("http://www.lesswatts.org/projects/acpi/overridingDSDT.php") but am wary of continuing as I have no experience of tinkering with the kernal.

Additionally I am having the above mentioned problems with the headphones and the trackpoint middle button, and will try the fixes mentioned above for these.  The wireless is working fine.  

My output for lscpi is:
[INDENT]00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge
00:01.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (int gfx)
00:05.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 1)
00:07.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 3)
00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [AHCI mode]
00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:12.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:13.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3c)
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS780M/RS780MN [Radeon HD 3200 Graphics]
01:05.1 Audio device: ATI Technologies Inc RS780 Azalia controller
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 03)
03:00.0 Network controller: Realtek Semiconductor Co., Ltd. Device 8172 (rev 10)[/INDENT]

Would really appreciate any help on the power/crashing issue

---

### Post by romidhaka on 2010-06-06
hi just bought a thinkpad edge 13 (intel SU 7300). installed ubuntu 10.04 everything seems to work fine except touchpad 2 finger scrolling

anyone know how to acivate two finger scrolling?

thnx

---

### Post by romidhaka on 2010-06-07
found a solution by searching around. [[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/554980]](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/554980])

just open terminal and copy:

xinput --set-prop --type=int --format=8 "SynPS/2 Synaptics TouchPad" "Synaptics Two-Finger Scrolling" 1 0
xinput --set-prop --type=int --format=32 "SynPS/2 Synaptics TouchPad" "Synaptics Two-Finger Pressure" 4

---

### Post by fethio on 2010-06-10
> **LordChaos73 said:**
> 

Don't forget to update the BIOS to the latest version:

[http://www-307.ibm.com/pc/support/site.wss/MIGR-74581.html](http://www-307.ibm.com/pc/support/site.wss/MIGR-74581.html)

Regards,

Eric

Eric, 

How did you get to update the bios? At the lenovo site there is a newer versin of bios (1.17/1.13) in .iso format, however I was not able to boot with it using a USB flash disk (tried writing it with unetbootin).

Fethi

---

### Post by fethio on 2010-06-23
the bios upgrade using grub2 works... it is described here [BIOS Upgrade - ThinkWiki](http://www.thinkwiki.org/wiki/BIOS_Upgrade)

---

### Post by LordChaos73 on 2010-06-23
> **fethio said:**
> Eric, 

How did you get to update the bios? At the lenovo site there is a newer versin of bios (1.17/1.13) in .iso format, however I was not able to boot with it using a USB flash disk (tried writing it with unetbootin).

Fethi

USB stick doesn't work, I used an external DVD/RW drive instead.

---

### Post by fethio on 2010-06-26
Some observations about performance. For the last three weeks, I've been running an in-house kernel compiled to include the dsdt file provided in [http://forum.notebookreview.com/lenovo-ibm/456688-thinkpad-edge-amd-impressions-6.html]("http://forum.notebookreview.com/lenovo-ibm/456688-thinkpad-edge-amd-impressions-6.html"). My bios/ecp version was 1.12/1.04. 

Before compiling with the provided dsdt file, I got an error after login, about not being able to use CPU frequency scaling. The dsdt included kernel got rid of that and I could see the change in CPU freq in idle times thru the panel CPU monitor.

However, that really did not have an impact on battery life, at least not as much as I thought it would. After I upgraded my BIOS/ECP firmware yesterday to version 1.18/1.09, I switched back to kernel without dsdt file override (hpoing that the 1.18 upgrade may have implemented a fix in the dsdt table). But nope, its still not fixed as I still get the CPU freq scaling error.

The interesting thing is there is virtually no difference in power rating between kernels with or without a dsdt override. The power consumption remains in the same level, around 21W.

Additionally, when I used a kernel with a dsdt override the backlight adjustment keys on the top row of the keyboard did not respond. Actually the level indicator appeared on the screen and the level changed as the key was pressed, however the actual brightness level did not change.

Another thing is when I close the lid and the machine goes to suspend, it wakes back up, but is totally unresponsive and requires a forced reboot by pressing the power button. This problem occured regardless of the type of kernels used (with or without the dsdt override), however it is fixed with the bios upgrade (to ver 1.18).

Overall, the battery drains fast as it feels, it takes less than two hours, at a rate of approx 21 W. 

However, using the proprietary ATI catalyst driver reduces power rate to a band 12-14 W, representing a reduction of around 30% in comparison with the ubuntu's own ATI drivers.

---

### Post by LordChaos73 on 2010-06-30
Is everybody seeing a bluetooth adapter with this laptop in Ubuntu ? Mine seems not be detected...

Cheers,

Eric

---

### Post by rCXer on 2010-07-01
Just got Ubuntu 10.04 running on my Edge 14 and I'm really enjoying it :D If you have time, can you guys submit your findings to the [ThinkWiki]("http://www.thinkwiki.org")? [Here's](http://www.thinkwiki.org/wiki/Installing_Ubuntu_10.04_%28Lucid_Lynx%29_on_a_ThinkPad_Edge_14%22_%28Intel%29) an article I wrote.

Has anyone gotten hdaps working?

---

### Post by flo2010 on 2010-07-08
i have recently installed lucid on a thinkpad edge 13 " (intel core2duo)..
almost everything i need worked out of the box..
the most annoying problem: RESUME AFTER SUSPEND

the screen turns black, the red light (i) indicates sleep mode, but the fan continues to run and the machine is stuck and i need to switch it off.

does anybody have the same problem or knows a fix? i have read in this thread that resume after suspend works..

and another question: how to enable 2-finger-scrolling in a persistent way? restarting disables it.

thanks a lot!

---

### Post by LordChaos73 on 2010-07-08
> **flo2010 said:**
> i have recently installed lucid on a thinkpad edge 13 " (intel core2duo)..
almost everything i need worked out of the box..
the most annoying problem: RESUME AFTER SUSPEND

the screen turns black, the red light (i) indicates sleep mode, but the fan continues to run and the machine is stuck and i need to switch it off.

does anybody have the same problem or knows a fix? i have read in this thread that resume after suspend works..

and another question: how to enable 2-finger-scrolling in a persistent way? restarting disables it.

thanks a lot!

What is the version of your BIOS ?

---

### Post by flo2010 on 2010-07-08
1.14 / i ran a bios update 2 weeks ago

---

### Post by LordChaos73 on 2010-07-08
> **flo2010 said:**
> 1.14 / i ran a bios update 2 weeks ago

Strange, resume from suspend works flawlessly on my machine. You do have a big enough swap file right ?
Is resume from suspend working in Windows ?

---

### Post by flo2010 on 2010-07-08
on win7 no suspend/resume problem. swap 4 GB (usage 0 %), RAM 4 GB (usage 13 %).
swap is in an encrypted LVM together with the rest (except boot partition).

---

### Post by fethio on 2010-07-08
There are three ways to get into suspend mode as far as I know. 
1- from the panel menu
2- by closing the lid
3- power manager (after being idle for minutes)

I've also had a similar WAKEUP problem when the machine suspended by closing the lid (if I chose to suspend via panel menu I did NOT have that).

During wake up keyboard was totally unresponsive. I've loaded the latest bios update 1.18/1.14 which solved that problem, only partially however.

Now the same WAKEUP problem is observed ONLY when power manager sends the machine to suspend after being idle for so many minutes.

---

### Post by flo2010 on 2010-07-09
i know that. it makes no difference..

---

### Post by Pjukern on 2010-07-09
Im running 10.4 on a edge (intel) everything but wifi works.
I saw the guide for the AMD version. But since everyon with intel reports that all works ootb there is no such guide for me.

My problem is that i cant enable the radio. It is detected, but disabled.

lspci: 
> 
espen@edge:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 03)
00:1c.5 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M-E LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
03:00.0 Network controller: Intel Corporation WiFi Link 1000 Series
05:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 03)
espen@edge:~$ 



Any ideas?

---

### Post by rCXer on 2010-07-10
> **Pjukern said:**
> Im running 10.4 on a edge (intel) everything but wifi works.
I saw the guide for the AMD version. But since everyon with intel reports that all works ootb there is no such guide for me.

My problem is that i cant enable the radio. It is detected, but disabled.

lspci: 


Any ideas?
The wireless key, F9, on the keyboard doesn't seem to work.  I had to right click on the "NetworkManager Applet" and select "Enable Wireless" and "Enable Networking"

---

### Post by Pjukern on 2010-07-10
The "Enable Wireless" text is grey/disabled. "Enable networking" works though.

---

### Post by echosystm on 2010-07-10
Hi all,

I'm interested in buying an Edge 13. However, I have heard the headphone port is very noisy. Has anyone here experienced this? Has anyone here NOT experienced this?

Cheers!

---

### Post by rCXer on 2010-07-10
> **Pjukern said:**
> The "Enable Wireless" text is grey/disabled. "Enable networking" works though.

Hmm, that's strange and I have the same wireless device as you.  

From lspci on my Intel Edge 14":
```

03:00.0 Network controller: Intel Corporation WiFi Link 1000 Series

```

---

### Post by rCXer on 2010-07-10
> **echosystm said:**
> Hi all,

I'm interested in buying an Edge 13. However, I have heard the headphone port is very noisy. Has anyone here experienced this? Has anyone here NOT experienced this?

Cheers!

I haven't experienced this on my Intel Edge 14" (yet...).  I have been using this computer for about a month.

---

### Post by rCXer on 2010-07-13
> **grmela said:**
> Offtopic: Does anyone have problem with Lenovo battery gauge under Windows 7 saying "Battery not installed"? The integrated Windows indicator works great but the Lenovo's one reports this error. My drivers and ThinkVantage software are up-to-date.

I am experiencing this problem as well.  And I solved it using the suggestion in the 2nd post of [this thread]("http://forums.lenovo.com/t5/ThinkVantage-Technologies/Power-Manager-says-No-battery-is-installed/td-p/58873").

> 
If it is hardware related, please take your battery out.
Then power up with AC only. Power down, unplug AC and hit power button ten times.
Then install your battery pack, plug in AC and power up.


---

### Post by twisted_steel on 2010-07-15
Does anyone have the video camera working on the Edge 14 (Intel)?  I tried looking at the video input section gstreamer-properties.  The camera is listed as 'integrated camera' and the green light turns on.  However, whenever I try to run the test, all I get is a gray box.  The same thing happens when I run Cheese.  In the end, it would be nice to be able to use it with Skype.

---

### Post by rCXer on 2010-07-17
I haven't been able to get it to work either (I also have an Intel Edge 14).  If you want to, could you add your experiences or expand [this article]("http://www.thinkwiki.org/wiki/Installing_Ubuntu_10.04_%28Lucid_Lynx%29_on_a_ThinkPad_Edge_14%22_%28Intel%29") on thinkwiki?  It would really help out other Edge users.

---

### Post by twisted_steel on 2010-07-18
Actually the experiences over here are pretty much the same.  I did a little more digging into the camera situation.

Location in lsusb:
```
Bus 002 Device 003: ID 17ef:4810 Lenovo
```

Relevant section from dmesg:
```
[   15.767878] uvcvideo: Found UVC 1.00 device Integrated Camera (17ef:4810)
[   15.769101] input: Integrated Camera as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.4/2-1.4:1.0/input/input5
[   15.769200] usbcore: registered new interface driver uvcvideo
[   15.769204] USB Video Class driver (v0.1.0)
```

This appears to be the same camera in other laptops.  I found a post with a [SL510 user]("http://sysphere.org/~anrxc/j/articles/thinkpad/") saying that the camera works with Arch.  I did notice that the kernel version is newer (2.6.34 vs 2.6.32).

Here is the output from luvcview:
```
luvcview 0.2.6

SDL information:
  Video driver: x11
  A window manager is available
Device information:
  Device path:  /dev/video0
Stream settings:
  Frame format: MJPG
  Frame size:   640x480
  Frame rate:   30 fps
```

I still see the gray box even with that.

---

### Post by twisted_steel on 2010-08-08
> **rCXer said:**
> I haven't been able to get it to work either (I also have an Intel Edge 14).  If you want to, could you add your experiences or expand [this article]("http://www.thinkwiki.org/wiki/Installing_Ubuntu_10.04_%28Lucid_Lynx%29_on_a_ThinkPad_Edge_14%22_%28Intel%29") on thinkwiki?  It would really help out other Edge users.

Have you tried the 10.10 Alpha 3 LiveCD yet (I have not)?  Maybe that has some fixes.

---

### Post by rCXer on 2010-08-12
Hmm... now the camera is working (probably because of an update).

---

### Post by rockprincess on 2010-08-15
anyone got the microphone e.g on skype working yet??? i've got major problems...sound is working, but not the mic.
found this bug report, but the mentioned fix does nothing for me :(
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/445889](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/445889)

the webcam works fine for me btw...

---

### Post by rCXer on 2010-08-15
Just tried the sound recorder.  No sound either :(

---

### Post by rCXer on 2010-08-16
I got the camera working.  All you have to do is left-click on the panel's sound button and select "Sound Preferences...".  On the "Input" tab uncheck "Mute" and increase the "Input Volume" to 100%.  

The microphone can be tested by the "Sound Recorder" (Applications->Sound & Video->Sound Recorder).  Just press the record button, say something, press the stop button and then press the play button.

---

### Post by axyelp on 2010-08-18
i wonder how come you're having problems with the webcam or microphone! to me, surprisingly everything ran out of the box! even two finger scroll and stuff runs smoother than windows 7! i'm just a bit lazy to get the pinch zoom working,.. will do it tonight!

i'd first recommend to update the system!

edge config: 0578-hnq, i5(450m), 2gb memory, 500gb hdd bla bla bla!

the only thing i couldn't geth working was the keyboard backlight!

---

### Post by axyelp on 2010-08-18
you experience it when the little latch below is disturbed! i found it immediately when i put the machine to hibernate!

---

### Post by rockprincess on 2010-08-18
axyelp: do you have the NVLDHGE model?
looks like you have the exact same model as I have.

out of curiosity, do you use UBUNTU (with Gnome) or KUBUNTU (KDE)?
from what I've read only people with Gnome have posted their experiences....and I'm here alone struggeling with Kmix...maybe I should switch to Gnome :(

---

### Post by axyelp on 2010-08-23
> **rockprincess said:**
> axyelp: do you have the NVLDHGE model?
looks like you have the exact same model as I have.

out of curiosity, do you use UBUNTU (with Gnome) or KUBUNTU (KDE)?
from what I've read only people with Gnome have posted their experiences....and I'm here alone struggeling with Kmix...maybe I should switch to Gnome :(

ummm, no! mine is edge 14. your is 15 i guess.
i too use kmix(on gnome! lol), gives me a better control! ;)
but i had my sound configured before kmix!

---

### Post by rockprincess on 2010-08-23
> **axyelp said:**
> ummm, no! mine is edge 14. your is 15 i guess.
i too use kmix(on gnome! lol), gives me a better control! ;)
but i had my sound configured before kmix!

so basically i now need to install the ubuntu-desktop package, to configure the microphone?

that's a bit much effort to get a microphone working...hmm

how did you "configure" the sound on gnome, before you used kmix
what program on gnome, etc...

---

### Post by quietplease on 2010-08-28
in a terminal enter
alsamixer

---

### Post by axyelp on 2010-09-10
I bought this edge 14 i5 540M. my other reason for buying the intel version was the chipsets working out of the box. have tried various intel and nonintel(motherboards - asus n gigabyte) desktop machines and drivers has almost always been a pain. first reason was - i wanted a cooler machine.

have updated the bios once through the thinkvantage suite on windows. all of the things worked well except for the multitouch and fingerprint reader.

$ uname -a
Linux zed 2.6.32-24-generic #42-Ubuntu SMP Fri Aug 20 14:21:58 UTC 2010 x86_64 GNU/Linux
$ lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 10.04.1 LTS
Release:	10.04
Codename:	lucid

this is my experience so far with this machine on ubuntu

-battery life is barely above 2:30 hours. with heavy usage, about 2 hours.

-got the multitouch working by installing gsynaptics, and using $synclient to enable/disable multitouch properties. i just run a script every login which sets it up. multitouch experience is far more responsive and beautiful compared to that on windows!

-couldn't get fingerprint working whatsoever.

-network manager could not detect my wifi network. did a full update via update manager, which did the job. 

-the wifi reconnection freezes the machine just too often.

-cpu temperature: 39C-45C on nil/low load, 55C-65C on heavy load. 

-had to disable a number of services to keep the memory usage down. disabled bluetooth from starting by default to add to battery life.

-using cpufreq-selector to change cpu frequency to 'ondemand'.

-speakers/mic/speaker jack work out of the box.

-disabled the new Fn-key behavior from bios. ctrl+alt+fn+f1 is just too much!

-all fn keys work perfectly except for Fn+F4 which is supposed to switch off the mic. and couldn't get the point of Fn+F9. can't integrate Fn key in shortcut combinations.



here's my lspci:
```

00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 02)
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 02)
00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 06)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 06)
00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 06)
00:1c.2 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 3 (rev 06)
00:1c.3 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 4 (rev 06)
00:1c.4 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 5 (rev 06)
00:1c.5 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 6 (rev 06)
00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a6)
00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 06)
00:1f.2 IDE interface: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA IDE Controller (rev 06)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 06)
00:1f.6 Signal processing controller: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem (rev 06)
03:00.0 Network controller: Realtek Semiconductor Co., Ltd. Device 8172 (rev 10)
09:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 03)
ff:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers (rev 02)
ff:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 02)
ff:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 02)
ff:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 02)
ff:02.2 Host bridge: Intel Corporation Core Processor Reserved (rev 02)
ff:02.3 Host bridge: Intel Corporation Core Processor Reserved (rev 02)

```

and
#lshw -short
```
H/W path           Device      Class          Description
=========================================================
                               system         0578HNQ
/0                             bus            0578HNQ
/0/0                           memory         117KiB BIOS
/0/4                           processor      Intel(R) Core(TM) i5 CPU       M 450  @ 2.40GHz
/0/4/5                         memory         32KiB L1 cache
/0/4/6                         memory         256KiB L2 cache
/0/4/7                         memory         3MiB L3 cache
/0/1b                          memory         2GiB System Memory
/0/1b/0                        memory         2GiB SODIMM Synchronous 1066 MHz (0.9 ns)
/0/1b/1                        memory         SODIMM Synchronous [empty]
/0/100                         bridge         Core Processor DRAM Controller
/0/100/2                       display        Core Processor Integrated Graphics Controller
/0/100/16                      communication  5 Series/3400 Series Chipset HECI Controller
/0/100/1a                      bus            5 Series/3400 Series Chipset USB2 Enhanced Host Controller
/0/100/1b                      multimedia     5 Series/3400 Series Chipset High Definition Audio
/0/100/1c                      bridge         5 Series/3400 Series Chipset PCI Express Root Port 1
/0/100/1c.1                    bridge         5 Series/3400 Series Chipset PCI Express Root Port 2
/0/100/1c.1/0      wlan0       network        Realtek Semiconductor Co., Ltd.
/0/100/1c.2                    bridge         5 Series/3400 Series Chipset PCI Express Root Port 3
/0/100/1c.3                    bridge         5 Series/3400 Series Chipset PCI Express Root Port 4
/0/100/1c.4                    bridge         5 Series/3400 Series Chipset PCI Express Root Port 5
/0/100/1c.5                    bridge         5 Series/3400 Series Chipset PCI Express Root Port 6
/0/100/1c.5/0      eth0        network        RTL8111/8168B PCI Express Gigabit Ethernet controller
/0/100/1d                      bus            5 Series/3400 Series Chipset USB2 Enhanced Host Controller
/0/100/1e                      bridge         82801 Mobile PCI Bridge
/0/100/1f                      bridge         Mobile 5 Series Chipset LPC Interface Controller
/0/100/1f.2        scsi0       storage        5 Series/3400 Series Chipset 4 port SATA IDE Controller
/0/100/1f.2/0      /dev/sda    disk           500GB FUJITSU MJA2500B
/0/100/1f.2/0/1    /dev/sda1   volume         40GiB Windows NTFS volume
/0/100/1f.2/0/2    /dev/sda2   volume         29GiB Windows NTFS volume
/0/100/1f.2/0/3    /dev/sda3   volume         395GiB Extended partition
/0/100/1f.2/0/3/5  /dev/sda5   volume         169GiB HPFS/NTFS partition
/0/100/1f.2/0/3/6  /dev/sda6   volume         79GiB HPFS/NTFS partition
/0/100/1f.2/0/3/7  /dev/sda7   volume         70GiB HPFS/NTFS partition
/0/100/1f.2/0/3/8  /dev/sda8   volume         29GiB Linux filesystem partition
/0/100/1f.2/0/3/9  /dev/sda9   volume         20GiB Linux filesystem partition
/0/100/1f.2/0/3/a  /dev/sda10  volume         23GiB Linux filesystem partition
/0/100/1f.2/0/3/b  /dev/sda11  volume         2047MiB Linux swap / Solaris partition
/0/100/1f.2/1      /dev/cdrom  disk           DVD RW AD-7700H
/0/100/1f.3                    bus            5 Series/3400 Series Chipset SMBus Controller
/0/100/1f.6                    generic        5 Series/3400 Series Chipset Thermal Subsystem
/0/101                         bridge         Core Processor QuickPath Architecture Generic Non-core Registers
/0/102                         bridge         Core Processor QuickPath Architecture System Address Decoder
/0/103                         bridge         Core Processor QPI Link 0
/0/104                         bridge         Core Processor QPI Physical 0
/0/105                         bridge         Core Processor Reserved
/0/106                         bridge         Core Processor Reserved
/0/1               scsi2       storage        
/0/1/0.0.0         /dev/sdb    disk           SCSI Disk

```

---

### Post by vickoxy on 2010-09-11
Hi,
could anyone say how loud the fan under linux is? Is there some fan control tool working with edge?

Thanks

---

### Post by emdeem on 2010-09-11
Just installed Lucid on a 14" Intel Edge.  Couldn't get bluetooth to work no matter what I tried.  Looking in the BIOS revealed no settings to turn BT on/off.  I was almost convinced that Lenovo had failed to installed it.  I finally tried the "reset to default" option in the BIOS and Lucid now sees my BT.  Probably not Ubuntu specific, but I hope this helps someone.

---

### Post by rockprincess on 2010-09-12
dear all, 

to keep you updated, i finally found the solution to my problem!!

for anyone who's interested or has the same problem:

i had to add the following line at the end of /etc/modprobe.conf/alsa-base.conf:

options snd-hda-intel model="olpc-xo-1_5"

i then rebooted, and then both the mic finally worked and the speaker allowed me a higher volume :)

---

### Post by axyelp on 2010-09-13
> **vickoxy said:**
> Hi,
could anyone say how loud the fan under linux is? Is there some fan control tool working with edge?

Thanks

fan's as loud(i meant quiet) as in windows! i mean, its pretty inaudible! 
'thinkfan' available in the repo controls fan! i don't know how well it does, but at times i do feel the fan throwing air a little faster than normal, esp if its under load! so yes, i believe it does work!

---

### Post by acid_kewpie on 2010-09-13
> **emdeem said:**
> Just installed Lucid on a 14" Intel Edge.  Couldn't get bluetooth to work no matter what I tried.  Looking in the BIOS revealed no settings to turn BT on/off.  I was almost convinced that Lenovo had failed to installed it.  I finally tried the "reset to default" option in the BIOS and Lucid now sees my BT.  Probably not Ubuntu specific, but I hope this helps someone.

Absolutely! I got a 15" Edge a month ago and gave up trying to get it turned on. Was contemplating a temporary windows install to enable it, but no need now! Thanks muchly so. This was on FC13 for what it matters,

---

### Post by vickoxy on 2010-09-13
> **axyelp said:**
> fan's as loud(i meant quiet) as in windows! i mean, its pretty inaudible! 
'thinkfan' available in the repo controls fan! i don't know how well it does, but at times i do feel the fan throwing air a little faster than normal, esp if its under load! so yes, i believe it does work!

Can anyone confirm that thinkfan controls fan in edge 13? Could someone post how many RPMs are there at level 1 (just type sensors in terminal). Thanks...:popcorn:

---

### Post by dvdgc13 on 2010-09-13
> **vickoxy said:**
> Can anyone confirm that thinkfan controls fan in edge 13? Could someone post how many RPMs are there at level 1 (just type sensors in terminal). Thanks...:popcorn:
I've also found that my fan has been noisier lately... but I don't know if it's been before or after I've installed the last beta version or Ubuntu 10.10 which I did because I couldn't manage to make the bluetooth and the mic work in 10.04.  Finally I managed to make the thing works updating the BIOS and with a clean installation and using the "olpc-xo-1_5" trick... but now, the mic is recording the fan noise!! which is painfully amplified when recorded!

My fan values from sensor are:
```
acpitz-virtual-0
Adapter: Virtual device
temp1:       +26.8°C  (crit = +100.0°C)                  

k8temp-pci-00c3
Adapter: PCI adapter
Core0 Temp:  +54.0°C                                    
Core0 Temp:  +53.0°C                                    
Core1 Temp:  +50.0°C                                    
Core1 Temp:  +51.0°C                                    

thinkpad-isa-0000
Adapter: ISA adapter
fan1:        652 RPM
temp1:        +0.0°C                                    
temp2:       +58.0°C                                    
temp3:       +58.0°C                                    
temp4:        +0.0°C                                    
temp5:        +0.0°C                                    
temp6:        +0.0°C                                    
temp7:       +30.0°C                                    
temp8:        +0.0°C                                    

```By the way I'm having a ARM Edge 13.

---

### Post by vickoxy on 2010-09-14
> **dvdgc13 said:**
> I've also found that my fan has been noisier lately... but I don't know if it's been before or after I've installed the last beta version or Ubuntu 10.10 which I did because I couldn't manage to make the bluetooth and the mic work in 10.04.  Finally I managed to make the thing works updating the BIOS and with a clean installation and using the "olpc-xo-1_5" trick... but now, the mic is recording the fan noise!! which is painfully amplified when recorded!

My fan values from sensor are:
```
acpitz-virtual-0
Adapter: Virtual device
temp1:       +26.8°C  (crit = +100.0°C)                  

k8temp-pci-00c3
Adapter: PCI adapter
Core0 Temp:  +54.0°C                                    
Core0 Temp:  +53.0°C                                    
Core1 Temp:  +50.0°C                                    
Core1 Temp:  +51.0°C                                    

thinkpad-isa-0000
Adapter: ISA adapter
fan1:        652 RPM
temp1:        +0.0°C                                    
temp2:       +58.0°C                                    
temp3:       +58.0°C                                    
temp4:        +0.0°C                                    
temp5:        +0.0°C                                    
temp6:        +0.0°C                                    
temp7:       +30.0°C                                    
temp8:        +0.0°C                                    

```By the way I'm having a ARM Edge 13.

Thanks-strange-my thinkpad r500 works on 1900 RPMs and is barely audible. And 625 seems to be very low speed....

---

### Post by axyelp on 2010-09-14
> **dvdgc13 said:**
> 
My fan values from sensor are:
```
acpitz-virtual-0
Adapter: Virtual device
temp1:       +26.8°C  (crit = +100.0°C)                  

k8temp-pci-00c3
Adapter: PCI adapter
Core0 Temp:  +54.0°C                                    
Core0 Temp:  +53.0°C                                    
Core1 Temp:  +50.0°C                                    
Core1 Temp:  +51.0°C                                    

thinkpad-isa-0000
Adapter: ISA adapter
fan1:        652 RPM
temp1:        +0.0°C                                    
temp2:       +58.0°C                                    
temp3:       +58.0°C                                    
temp4:        +0.0°C                                    
temp5:        +0.0°C                                    
temp6:        +0.0°C                                    
temp7:       +30.0°C                                    
temp8:        +0.0°C                                    

```By the way I'm having a ARM Edge 13.

two questions:
1. since when did Lenovo begin selling ARM Edge 13? well since when did Lenovo began selling ARM based machines anyway!

2. and if its ARM based, how come you've got two cores!

my sensors output is:

```
$ sensors 
acpitz-virtual-0
Adapter: Virtual device
temp1:       +39.0°C  (crit = +105.0°C)                  

```

no fans! no other cores!
while booting, it shows:
thinkpad_acpi: Not yet supported ThinkPad detected

any Edge owner got this sorted?

---

### Post by rCXer on 2010-09-15
> **axyelp said:**
> while booting, it shows:
thinkpad_acpi: Not yet supported ThinkPad detected

any Edge owner got this sorted?

I get that error as well.  It is a [known bug]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/552880") and people are working on it.

---

### Post by vickoxy on 2010-09-16
That is why am i asking-i had sl510 and it has same/similar firmware as Edge-no "real" Thinkpad...

---

### Post by lovefro on 2010-10-06
Hey I have a think pad edge, I got headphones to work on my computer(thanks to this forum) and for a while I had problems with the hibernate/suspend disconnecting me from the INTERNET then freezing when I tried to reconnect.  However after a unnoticed update these problems where "fixed" as far is I could tell.  However in the last update or two the suspend hibernate problems have resurfaced.  This time with a vengeance.

Whenever I close the lid or let it go into suspend/hibernate my computer freezes on a black screen.  And I think I might be experiencing overheating; it seems hotter and is significantly slower.

Has anyone else been experiencing these problems?

I have a think-pad edge with AMD chip-set

I know this does not help but I am also fairly Linux illiterate.  However I really do appreciate a lot of things about Ubuntu.

---

### Post by axyelp on 2010-10-06
> **lovefro said:**
> Hey I have a think pad edge, I got headphones to work on my computer(thanks to this forum) and for a while I had problems with the hibernate/suspend disconnecting me from the INTERNET then freezing when I tried to reconnect.  However after a unnoticed update these problems where "fixed" as far is I could tell.  However in the last update or two the suspend hibernate problems have resurfaced.  This time with a vengeance.

Whenever I close the lid or let it go into suspend/hibernate my computer freezes on a black screen.  And I think I might be experiencing overheating; it seems hotter and is significantly slower.

Has anyone else been experiencing these problems?

I have a think-pad edge with AMD chip-set

I know this does not help but I am also fairly Linux illiterate.  However I really do appreciate a lot of things about Ubuntu.


hi!
the problem i believe is not with the suspend or hibernate, but with the wifi connection. it happens a lot of time with me.
so if you have a wifi connection, which 'connects automatically', that's the cause of freeze!
check out this thread, i posted nearly the same thing! its reported to have a driver problem! :D
[http://goo.gl/DbvB](http://goo.gl/DbvB)

---

### Post by colinkingswood on 2010-10-07
[http://blog.zorinholdings.com/post/501557101/lenovo-thinkpad-edge-wifi-with-ubuntu-10-04](http://blog.zorinholdings.com/post/501557101/lenovo-thinkpad-edge-wifi-with-ubuntu-10-04)

This page has a better description of how to install the driver (the link above deoesn't decribe how to remove the ubuntu driver). Installing the Realtek driver stoped my connection dropping as often and I get a better reception. I had to reinstall it after a kernel update though, as it went back to using the Ubuntu driver.

---

### Post by lovefro on 2010-10-07
Thanks for the quick reply however!
I went to your link and it says:
 "[B]STOP PRESS: As of the update providing kernel 2.6.32-22 Wifi  appears to work out of the box, thus rendering this article redundant."

[FONT=Arial][SIZE=1]My problem started recently[/SIZE][/FONT][SIZE=1].  I did notice the problem with the wi-fi and I believe it to be fixed with the above mentioned update.  I'll try the fix just to be sure over the weekend unless anyone here thinks it to be redundant.

Again thank y'all
[/SIZE][/B]

---

### Post by axyelp on 2010-10-08
> **colinkingswood said:**
> [http://blog.zorinholdings.com/post/501557101/lenovo-thinkpad-edge-wifi-with-ubuntu-10-04](http://blog.zorinholdings.com/post/501557101/lenovo-thinkpad-edge-wifi-with-ubuntu-10-04)

This page has a better description of how to install the driver (the link above deoesn't decribe how to remove the ubuntu driver). Installing the Realtek driver stoped my connection dropping as often and I get a better reception. I had to reinstall it after a kernel update though, as it went back to using the Ubuntu driver.


thanks a lot mate! was waiting for a tutorial! :P
it worked, after a bit of here and there!

---

### Post by colinkingswood on 2010-10-10
> **lovefro said:**
> Thanks for the quick reply however!
I went to your link and it says:
 "[B]STOP PRESS: As of the update providing kernel 2.6.32-22 Wifi  appears to work out of the box, thus rendering this article redundant."

[FONT=Arial][SIZE=1]My problem started recently[/SIZE][/FONT][SIZE=1].  I did notice the problem with the wi-fi and I believe it to be fixed with the above mentioned update.  I'll try the fix just to be sure over the weekend unless anyone here thinks it to be redundant.

Again thank y'all
[/SIZE][/B]

Hi Lovefro, I know the article says it works out of the box - it does, but not as well. Having used the official Realtek driver for a while now it definitely works better. I noticed that the reception went down after upgrading the kernel (and reverting to the old driver).

---

### Post by usprey on 2010-10-18
Good news everyone!
I finally got my hands on the new Lenovo ThinkPad Edge 13 NV12YMD, that became available here on thursday.
Primary new features are **Intel Core i3-380UM 1.33GHz** and **4GB 1333MHz DDR3 SDRAM (PC3-10600)**.


[SIZE="2"][CENTER]*****IMPORTANT BATTERY FIRMWARE UPDATE ONLY APPLICABLE FROM WINDOWS*****[/CENTER][/SIZE]
There is an important firmware update for the battery that you, at the moment, can only install from windows. Make sure you install it before you purge windows from your harddrive.
> Version 1.02
[Important] Fixed an issue where the battery indicated incorrect full charge capacity then the battery life might be reduced.
You can install the update with [this utility]("http://www-307.ibm.com/pc/support/site.wss/document.do?lndocid=MIGR-70811"), or from the preinstalled ThinkVantage Toolbox.
Based on [this link]("http://brainstorm.ubuntu.com/idea/25427/"), I don't think there's any other way of doing the update.


[SIZE="3"]Specifications and version information[/SIZE]
[LIST]
[*]Hardware 1 - lshw
```
lshw -short:
H/W path             Device     Class          Description
==========================================================
                                system         02172YG
/0                              bus            02172YG
/0/0                            memory         117KiB BIOS
/0/4                            processor      Intel(R) Core(TM) i3 CPU       U 
/0/4/5                          memory         32KiB L1 cache
/0/4/6                          memory         256KiB L2 cache
/0/4/7                          memory         3MiB L3 cache
/0/1b                           memory         4GiB System Memory
/0/1b/0                         memory         2GiB SODIMM Synchronous 1334 MHz 
/0/1b/1                         memory         2GiB SODIMM Synchronous 1334 MHz 
/0/100                          bridge         Core Processor DRAM Controller
/0/100/2                        display        Core Processor Integrated Graphic
/0/100/16                       communication  5 Series/3400 Series Chipset HECI
/0/100/1a                       bus            5 Series/3400 Series Chipset USB2
/0/100/1b                       multimedia     5 Series/3400 Series Chipset High
/0/100/1c                       bridge         5 Series/3400 Series Chipset PCI 
/0/100/1c.1                     bridge         5 Series/3400 Series Chipset PCI 
/0/100/1c.1/0        wlan0      network        Centrino Wireless-N 1000
/0/100/1c.4                     bridge         5 Series/3400 Series Chipset PCI 
/0/100/1c.5                     bridge         5 Series/3400 Series Chipset PCI 
/0/100/1c.5/0        eth0       network        RTL8111/8168B PCI Express Gigabit
/0/100/1d                       bus            5 Series/3400 Series Chipset USB2
/0/100/1e                       bridge         82801 Mobile PCI Bridge
/0/100/1f                       bridge         Mobile 5 Series Chipset LPC Inter
/0/100/1f.2          scsi0      storage        5 Series/3400 Series Chipset 4 po
/0/100/1f.2/0.0.0    /dev/sda   disk           500GB WDC WD5000BEVT-0
/0/100/1f.2/0.0.0/1  /dev/sda1  volume         121MiB EXT4 volume
/0/100/1f.2/0.0.0/2  /dev/sda2  volume         19GiB EXT4 volume
/0/100/1f.2/0.0.0/3  /dev/sda3  volume         438GiB EXT4 volume
/0/100/1f.2/0.0.0/4  /dev/sda4  volume         7812MiB Linux swap volume
/0/100/1f.3                     bus            5 Series/3400 Series Chipset SMBu
/0/100/1f.6                     generic        5 Series/3400 Series Chipset Ther
/0/101                          bridge         Core Processor QuickPath Architec
/0/102                          bridge         Core Processor QuickPath Architec
/0/103                          bridge         Core Processor QPI Link 0
/0/104                          bridge         Core Processor QPI Physical 0
/0/105                          bridge         Core Processor Reserved
/0/106                          bridge         Core Processor Reserved
/0/1                 scsi5      storage        
/0/1/0.0.0           /dev/sdb   disk           SCSI Disk

```

[*]Hardware 2 - lspci
```
lspci:
00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 02)
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 02)
00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 06)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 06)
00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 06)
00:1c.4 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 5 (rev 06)
00:1c.5 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 6 (rev 06)
00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a6)
00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 06)
00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA AHCI Controller (rev 06)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 06)
00:1f.6 Signal processing controller: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem (rev 06)
03:00.0 Network controller: Intel Corporation Centrino Wireless-N 1000
09:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 03)
ff:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers (rev 02)
ff:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 02)
ff:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 02)
ff:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 02)
ff:02.2 Host bridge: Intel Corporation Core Processor Reserved (rev 02)
ff:02.3 Host bridge: Intel Corporation Core Processor Reserved (rev 02)

```

[*]Ubuntu version
```
lsb_release -a:
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 10.10
Release:	10.10
Codename:	maverick

```

[*]Kernel
```
uname -a:
Linux HOSTNAME 2.6.35-22-generic #34-Ubuntu SMP Sun Oct 10 09:26:05 UTC 2010 x86_64 GNU/Linux

```
[/LIST]


[SIZE="3"]Functionality[/SIZE]

No major problems, all function buttons, networking, suspend, webcam and wifi works.

[SIZE="2"]BIOS[/SIZE]
The system uses a new BIOS, version starts with 84, see below.
```
*-firmware
          description: BIOS
          vendor: LENOVO
          physical id: 0
          version: 84ET20WW (1.04 ) (08/09/2010)
          size: 117KiB
          capacity: 4032KiB
          capabilities: pci pnp upgrade shadowing escd cdboot acpi usb biosboots
```

[SIZE="2"]Hibernation[/SIZE]
Works, albeit very slowly. Might be due to low swappiness.

[SIZE="2"]Microphone[/SIZE]
Works after unmuting, had to increase input volume to max to be audible in skype.

[SIZE="2"]Sound[/SIZE]
Fix still works. Append ```
options snd-hda-intel model=olpc-xo-1_5
``` to the end of */etc/modprobe.d/alsa-base.conf*

[SIZE="2"]TouchPad/TrackPoint[/SIZE]
TrackPoint scrolling works via gpointing-device-settings after following [this guide.]("http://www.thinkwiki.org/wiki/Installing_Ubuntu_10.04_(Lucid_Lynx)_on_a_ThinkPad_Edge_14%22_(Intel)")
Haven't got two-finger scrolling working yet. Have disabled TouchPad in favor of TrackPoint because of this.
gpointing-device-settings are forgotten after suspend, but work after reboot. [https://bugs.launchpad.net/ubuntu/+source/gpointing-device-settings/+bug/489830]("https://bugs.launchpad.net/ubuntu/+source/gpointing-device-settings/+bug/489830")

[SIZE="2"]Wireless-N[/SIZE]
Is currently software disabled, works after applying the solution from [this post]("http://ubuntu.ubuntuforums.org/showthread.php?t=1592846"). The Intel Centrino Wireless-N only operates in the 2.4GHz sprectrum, although 300Mbps is theoretically possible I only achieve 65Mbps at the moment.

[SIZE="2"]Not tested[/SIZE]
eSATA
Bluetooth (Disabled)
HDMI
Qualcomm Gobi-2000 WWAN (Not detected?)
VGA-out

---

### Post by sjonnie85 on 2010-11-09
**[SIZE="3"]*Suspend mode freeze _Solution_*[/SIZE]**; The following worked for my thinkpad edge 13 intel (I did not update my bios)

Solution here: [http://ubuntuforums.org/showpost.php?p=10092297&postcount=4](http://ubuntuforums.org/showpost.php?p=10092297&postcount=4)

---

### Post by msjones on 2010-12-17
I have the thinkpad edge AMD model. When plugging in after running from batter the system will freeze. Disabling CPU scaling in the bios prevents this, but battery life is very poor after. Is there a solution to this?

Thanks

---

### Post by rCXer on 2010-12-17
This is a [known bug](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/596565) with no solution yet.  Pages 6 and 7 of [this thread](http://forum.notebookreview.com/lenovo-ibm/456688-thinkpad-edge-amd-impressions-6.html) has discussions of this problem.

---

### Post by Rudolf1986 on 2010-12-27
Hey, I still have many Problems with Ubuntu 10.10 and my Edge 11 AMD Version.
On 24 or 25 of Dezember I made an auto-Update of Ubuntu, since this Update my Wifi does not work any longer. (Installed the Realtek Driver as descriped) I tried to install the driver again, but it dont solved my Problem. So I only have Internet connection via Ethernet.

(Other Problems: Sound via Headphones dont work and the internal Mic)

I am very bad in Ubuntu, so I would need something like an description for dummies :-( 


Thank u all for trieing to help me.


PS: I googled my problem but I dont found anything similuar, but I think it must be something, maybe my english is to bad to find the solution in other forums.

---

### Post by yyon on 2010-12-28
The fix to the headphone/speaker sound problem (appending an option to */etc/modprobe.d/alsa-base.conf*) didn't work for me. I made a work-around:
```
#! /usr/bin/env python
# sound fix

import alsaaudio

# get speakers and headphones
Speakers = alsaaudio.Mixer("Speaker")
Headphones = alsaaudio.Mixer("Headphone")

# switch volumes
if Speakers.getvolume()[0] == 0:
    newSpeakerVolume = 100
    newHeadphoneVolume = 0
else:
    newSpeakerVolume = 0
    newHeadphoneVolume = 100

# set volumes
Speakers.setvolume(newSpeakerVolume, alsaaudio.MIXER_CHANNEL_ALL)
Headphones.setvolume(newHeadphoneVolume, alsaaudio.MIXER_CHANNEL_ALL
```
with python-alsaaudio.
Then I made a keyboard shortcut to run it. It seems to work pretty well so far.

---

### Post by Rudolf1986 on 2010-12-29
@yyon
First question is this proceder for "EDGE 11"?

I tried ur way, but I must do something wrong, first I installed python-alsaaudio, then I tipped the code into Terminal, but there come only errors...

Maybe u can tell me what I do wrong. (Tried to open the file manual, but I can not write there...)

I must say, I am very new on Ubuntu, excuse my stupid questions. 

Thank U 

PS. I postet 2 days ago something about my Wifi, maybe u can help me there to, or give me a Tip, where I can found help?

---

### Post by msjones on 2010-12-30
Just to let you all know, after upgrading to the latest 2.5.35-24 I seem to have lost my freezing issues due to the DSDT table.

Now I have only tested this for about 6 hours but after numerous reboots and updates poweroffs etc I am yet to get the issue. I will keep you posted.

---

### Post by GammaStream on 2011-02-06
Running Ubuntu 10.10 on the Thinkpad Edge with the 11 inch screen and intel CPU. Worked out of the box for me.

Thank you all for contributions on this thread, it made the decision about installing Ubuntu and my laptop selection a lot easier.

---

### Post by Redsandro on 2011-03-14
I have **Ubuntu 10.04.2 LTS** running on my Lenovo **ThinkPad Edge 15 NVLGPMH** (with Intel **Core i3 370M**) and suspend works fine. But when waking from **hibernate**, system **freezes** when the display comes up [SIZE="1"](the last one seen when hibernation started)[/SIZE].

Any ideas?

**dmesg** does mention:
*[   14.851351] thinkpad_acpi: Not yet supported ThinkPad detected!*

---

### Post by Rasa1111 on 2011-03-14
> **Brianspilner said:**
> I have foundthis tutorial which allowed me to use trackpoint middle button scrolling, but the second part which is about press-to-select did not work for me cause theres no such file.. any ideas about that?

```
1. Introduction

The TrackPoint is the red nub in the middle of the keyboard and the three buttons right below the keyboard. By default Press-To-Select, the process of pushing down on the TrackPoint to click, is turned off. Also, by default the TrackPoint's middle click performs the Paste function.

In this tutorial I will describe how to adjust these settings activate the middle click scroll and Press-To-Select similar to Windows.

2. Configure TrackPoint Middle Mouse Scroll

I wanted to configure the middle click on the TrackPoint to scroll just like in Windows so I used the following commands to achieve it.

2.1: Find the ID number for the TrackPoint

The first step is to find the xinput id number for the IBM TrackPoint. Run the following command.

xinput list

 

You should receive all the available devices for xinput. One of the devices should say:

"TPPS/2 IBM TrackPoint"    id=9    [XExtensionPointer]
    Type is MOUSE
    Num_buttons is 5
    Num_axes is 2
    Mode is Relative
    Motion_buffer is 256
    Axis 0 :
        Min_value is -1
        Max_value is -1
        Resolution is 1
    Axis 1 :
        Min_value is -1
        Max_value is -1
        Resolution is 1

 

Or something very similar. The "id=#" is the important number we will be using in the following commands. Later it will save the headache of typing that very long device name.

2.2: TrackPoint Middle Mouse Scroll

Next run the following commands to enable the middle mouse scroll.

xinput set-int-prop # "Evdev Wheel Emulation" 8 1
xinput set-int-prop # "Evdev Wheel Emulation Button" 8 2
xinput set-int-prop # "Evdev Wheel Emulation Timeout" 16 200

*** Replace # with the id number for the TrackPoint from the previous command.

Now you should be able to middle scroll by pressing the middle mouse button for the TrackPoint and moving the TrackPoint up and down.

3. Enable Press-To-Select

Press-To-Select is the process on pushing down on the TrackPoint to click on objects.

In the directory "/sys/devices/platform/i8042/serio1/serio2/" There is a file called "press-to-select". That is the file we will be focusing on.

3.1: Change directory

Open up the terminal and change the directory to "/sys/devices/platform/i8042/serio1/serio2/"

cd /sys/devices/platform/i8042/serio1/serio2/

 

3.2: Change Permissions of "press-to-select"

Change the permissions of the "pres-to-select" file to allow others modify the file.

sudo chmod o=rw ./press_to_select

 

3.3: Turn on/off Press-To-Select

To turn on/off Press-To-Select is just a matter of adding a 1 or 0 to the file.

~Turn Press-To-Select On~
echo -n 1 >  /sys/devices/platform/i8042/serio1/serio2/press_to_select

 

~Turn Press-To-Select Off~
echo -n 0 >  /sys/devices/platform/i8042/serio1/serio2/press_to_select

 

Now you should be able to click by pushing straight down slightly on the TrackPoint.

```

wow, thanks!!
That worked perfectly! 
:D

Very happy to have my trackpoint scroll back! You rock! :D
Many thanks. <3 :KS

---

### Post by Redsandro on 2011-03-22
When setting IDE ACPI to Legacy in BIOS, Hibernate does work (albeit is 1990s slow waking up). But this affects the eSata port.

And the message still shows:
```
root@RedEdge:mysql$ dmesg | grep acpi
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x04] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x05] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x03] high edge lint[0x1])
[    3.623665] acpi device:05: registered as cooling_device4
[   10.592710] thinkpad_acpi: Not yet supported ThinkPad detected!
```

> **Redsandro said:**
> I have **Ubuntu 10.04.2 LTS** running on my Lenovo **ThinkPad Edge 15 NVLGPMH** (with Intel **Core i3 370M**) and suspend works fine. But when waking from **hibernate**, system **freezes** when the display comes up [SIZE="1"](the last one seen when hibernation started)[/SIZE].

Any ideas?

**dmesg** does mention:
*[   14.851351] thinkpad_acpi: Not yet supported ThinkPad detected!*

---

### Post by Redsandro on 2011-07-10
> **rCXer said:**
> I get that error as well.  It is a [known bug]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/552880") and people are working on it.
Seems to be fixed in kernel 2.6.38.8. Cannot verify, I still have the message, maybe it's only for newer distro's than LTS.

---

### Post by Redsandro on 2011-07-12
You can install the 2.6.38 kernel by **temporarily** enabling the *lucid-propopsed* [SIZE="1"](Pre-releases)[/SIZE] repository, update, and run
*apt-get install linux-image-generic-lts-backport-natty linux-headers-generic-lts-backport-natty*
as root.

But, for me it makes things worse. Suspend doesn't work anymore. At least we had that in 2.6.32

---

### Post by freechelmi on 2011-08-05
Hi , just Got 11.04 installed on a lenovo thinkpad Edge E325 (AMD Fusion) .

Everything worked great, BUT , the fan is loud very often.

It can be controlled easily with thinkfan, but first step is around 700 rpm which is already very loud. 

I've set first step to start at 59 Degrees Celsius, which is hit when you just browse a web page ....

It seems that I'm hearing  two fans but the sensors see twice the same it seems.

then I guess the second loud fan should start at very high temps and the silent one should start first? anyone having infos on this ?

---

### Post by qualtch on 2011-09-10
Does there happen to be any people with experiences with Thinkpad Edge E325 or E320, and Ubuntu 11.04 installed? These laptops seem really interesting due to their excellent price/performance point, but compatibility with latest Ubuntu is a bit of a concern.

In the Ubuntu Certified Hardware page it notes that E325 it is not yet fully certified for self-installation, so it might be interesting to hear more user & community experiences of either of these laptops with Ubuntu (if there are any) :)

---

### Post by balkie99 on 2011-10-06
Hi all,

I own a Thinkpad Edge 13, intel,

with Intel Wifilink 1000,

use lucid,

everything works fine, except wifi. I have tried all things, no solution.

I have installed realtek module,

but in essence, my iwlagn driver works, but only when situated very close (within 2 metres) from wifi, and only when I set th rate to 54M. This is the behavior elsewhere too, very week performance of the wifi. Now I began to use a netgear wifi adapter, without it, my wifi is unusable.

could anyone suggest the solution? this subnotebook is brand new, and this problem...
no progress with natty, fedora, tried with live usb

thank yout

---

### Post by Redsandro on 2011-10-06
Hi **balkie99**, 

I have a Thinkpad Edge 15 which is different, but had some problems with Lucid as well. This version is not compatible with the latest Edge series.

Try [Linux Mint 11]("http://www.linuxmint.com/download.php") (which is a nicer version of Ubuntu 11.04 with codecs) because it has Kernel 2.6.38 iirc. You need at least 2.6.35 for Edge. Lucid has 2.6.32.

Try live images to see if wifi works.

---

### Post by balkie99 on 2011-10-07
Thank You,

I have just tried it, but nothing different. The wifi is up, I see the possible networks, but cannot connect to them (as at home, only if I would be very close to source...). So it is maybe not a driver problem.

Does anyone experience that the performance of the wifi is this weak with thinkpad edge 13?

What should I change and where?

thanks for ideas.

---

### Post by Redsandro on 2011-10-07
Strange. You shouldn't need extra drivers. Wifi works out of the box. And you can see networks, which means that the Wifi chip is active.

Random ideas:
Check bios setting?
Press Fn + Wifi (F9 on Edge 15)
Hardware failure -> return to shop?
Boot into Windows and see if you can connect?

Thought:
I have doubleboot Windows 7 (came with the laptop) and Linux. Bluetooth didn't work in Linux until I enabled it in Windows.

---

### Post by bks07 on 2011-10-10
Hi,

This is what I got:
 	o [B]Lenovo ThinkPad Edge 11" - 2545-A25
[/B]o AMD 1,4GHz - 4GB RAM - Samsung SSD 128GB
o Ubuntu 11.04 x64[SIZE=1]
[/SIZE] 

Thing is, WiFi installation is successful and it connects to my router via WLAN but it resets wifi connection every two minutes or less. What about the ndiswrapper driver option... has anyone tried yet?

Thanks,
bks07

---

### Post by bks07 on 2011-10-10
Hi,

I solved the problem for me.

At first I tried to install ndiswrapper drivers - without any success. ;)
But then i uninstalled everything from ndiswrapper and I installed the original realtek linux driver, upgradet to 11.10 and typed in "sudo modprobe rtl8192ce" for adding my controller and - *tada* - it works!

I hope this helps someone out there.

Cu,
bks07

---

### Post by Redsandro on 2011-10-10
Thanks for sharing! :)

It puzzles me that it didn't work in the first place though, but glad you figured it out.

---

### Post by Eddyah on 2011-11-15
Grr first time I've had to post a problem when searching has come up dry haha

I've tried installing ubuntu twice now and both times after the reset, it doesn't go into the grub2 menu, rather skips it entirely and boots straight into windows 7.

Anyone has any clues as to why it didn't modify the mbr?

---

### Post by axyelp on 2011-11-15
> **Eddyah said:**
> Grr first time I've had to post a problem when searching has come up dry haha

I've tried installing ubuntu twice now and both times after the reset, it doesn't go into the grub2 menu, rather skips it entirely and boots straight into windows 7.

Anyone has any clues as to why it didn't modify the mbr?

Try live booting again to see if its installed. If the installation said successful, you might want to check the disk settings at the bios. There's one setting under disk setting which sets to AHCI more or something. Change it to the other option, which is IDE or legacy, can't recall the exact thing.

That should probably work. It worked on a few laptops and my desktop.

---

### Post by Gregorybekkers on 2011-11-15
Ì have the Thinkpad Edge 15" Intel i3 Works fine for me. 
Only with 10.04 LTS I have wireless problems. 

But  from 11.04 and up Thinkpad Edge is Ubuntu Certified. 
And that works fine.

---

### Post by Eddyah on 2011-11-15
> **axyelp said:**
> Try live booting again to see if its installed. If the installation said successful, you might want to check the disk settings at the bios. There's one setting under disk setting which sets to AHCI more or something. Change it to the other option, which is IDE or legacy, can't recall the exact thing.

That should probably work. It worked on a few laptops and my desktop.

There are two settings i've played with trying all 4 possibilities:

SATA mode: AHCI OR Compatibility mode

Boot: UEFI OR Legacy

Changing to compatibility mode ruins any chance of me booting into windows due. Comes up with a repair message about the operating system.

UEFI or Legacy + AHCI does nothing sadly.

I'll have to try installing grub from the live cd and see if that fixes my problem. Fingers crossed I don't destroy my windows partition beyond repair!

---

### Post by jgratero on 2011-12-21
I recently owned a Thinkpad Edge 13'', model 01962CS... I'm using Xubuntu 11.10 on it (along with Windows7) and so far, my only complain is that the mic problem is still there. The mic is only functional when I'm using W7, so, no hardware problem there...

---

### Post by rockprincess on 2012-01-14
Guys,

I need your help.
I have a 15" Intel (i5) Edge running Kubuntu 11.10 on it. Everything seems to work except the F1-F12 keys. It's freaking me out.
And some of the FN keys like (volume up or down or mute) don't seem to work either. I get a visual feedback that the volume is reduced, but the system doesn't react to it, it still has the same volume as before. Then i have to manually change it in kmix myself, which is not the purpose, right?!

If I press Fn+F1 in most applications help pages should open, but it doesn't do anything.

How can I change the key mappings of these keys, that F1-F12 will finally work.

Do you have any ideas?
The strange thing is, when I used Kubuntu 11.04 all these keys worked out of the box.

please help, as it's getting a little frustrated :(

---

### Post by Redsandro on 2012-01-14
Strange, I have an Edge 15 running Ubuntu 11.10 and everything works.
I reckon it's a BIOS or forgotten config setting.

In the last case, try Kubuntu from Live CD. If keys work, you need to add a new user so you DO NOT inherit your old home with bad configs.

---

### Post by rockprincess on 2012-01-14
I've checked the BIOS, everything is looking fine there. I haven't changed it since i've got the laptop. and as said earlier in my post above, the F1-F12 keys worked fine in the previous releases e.g 11.04

now when I press F1 i get an A
when I press F2 i get a B
.....and so on.

I've checked the shortcut settings in the system preferences, but didn't find anything.

any clues on how I can fix this phenomenon?! ;)

I'd appreciate any advice.

many thanks in advance x

PS: i've added a user, the same problem occurs with the new user/home/config settings.

**EDIT**:

i think i've found what my problem was...the problem was located in the keymappings of the "Konsole" program. pretty weird, huh?! ;)

---

### Post by rx78pilot on 2012-01-27
Hi guys, it just for information. Before buying it, I have already performed many research but still get into several unbelieve situation.
 
Lenovo Thinkpad Edge 11 E120 (3043AB)
- Intel i3-2357M
- 8G RAM
- 120G SSD 2.5" 7.5mm (DIY)
- Ubuntu 11.10 64bit Desktop using EFI boot
 
Hardware Issue:
1) Keyboard missing the "Insert" key and therefore cannot use the Midcommand in console.
2) Can only access 6.7G RAM (where is the remaining 1.3G?).
3) Wifi cannot be turned on after sleep, hibernate. Tried "rfkill" but failed. However, it only works upon restart reboot the entire machine. So, wherever cafe, outdoor meeting I went, I have to wait for the reboot.
4) Quite hard to find 2.5" 7.5mm 7200RPM harddisk for replacement. The SATA slot design make one has no choice to insert a 9.5mm cos the SATA connector is upside down.
5) Battery drained very fast. I means the full capacity. Newly bought is 67.5V in full and just for 2 months, it's now 55.5V in full and cannot find original replacement even from Lenovo.
 
Hardware Solution:
1) No solution. have tried to remap key in GNOME, X but failed. Any help, suggestion from u guys?
2) Update BIOS to version "1.14" can access 7.7G RAM which acceptable now.
3) Update BIOS to version "1.14" seems solved the problem but still in testing.
4) Cos the reboot time of (3), bought a 9.5mm SSD and disassembly the casing to fit into the socket to shorten the reboot time.
5) Trying to locate compatible battery one instead.
 
So, seems the BIOS update is a must for fixing the machine problem. However, before you perform the BIOS update and you've already installed everything into the hardisk like me. Check whether you are using EFI to boot. If yes, please get a bootable CD or media in USB on hand, cos after the update the EFI boot information is also erased and need to recreate manually or else you cannot boot up.
 
Delete the EFI boot info in the BIOS and boot Ubuntu 11.10 installation CD using usb, open a terminal and login as root, perform the following instructions
> modprobe efivars
> apt-get install efibootmgr
> efibootmgr --create --gpt --disk /dev/sda --part 1 --wirte-signature --label "ubuntu" --loader "[\\EFT\\ubuntu\\grubx64.efi]("file://\\EFT\\ubuntu\\grubx64.efi")"
 
Be careful the last command cannot be re-issue. If anything wrong, go to the BIOS to delete the EFI boot info labeled - "ubuntu" and start it over again.
 
Overall, after using so much time to re-search, test & check, the notebook now is ok. At least to me. Ubuntu running on it is quite stable, fast (cos SSD and resume just need 3 seconds). 
 
However, from consumer point of view, it's not a cheaper one and how come so many minor problems in their BIOS and their design, plus aftersales services.
 
Conclusion, I don't recommend this notebook to anyone without sufficient technical knowledge but I am happy to have it.

---

