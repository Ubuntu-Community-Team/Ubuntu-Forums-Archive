---
title: "Gutsy on HP and Compaq Laptops"
date: 2007-08-19
forum: Hardware &amp; Laptops
---

### Post by EXCiD3 on 2007-08-19
If you have tried installing Gutsy Gibbon on an HP or Compaq laptop, please post feedback on your experience.

Please post the following things:
[B]Model:
Processor:
Wireless Card:
Graphics Card:
Gutsy Tribe (Version):
Boot Parameters: [/B](Only if extra boot options are needed in order to boot)
 
and a detailed description of anything you think is relevant to running Gutsy on HP/Compaq laptops. Once Gutsy is released I plan on creating a Howto which possibly covers most (hopefully almost all) of the hardware in the various HP and Compaq laptops, this way there would be one central location for information regarding compatibility with this hardware and Gutsy Gibbon.

---

### Post by EXCiD3 on 2007-08-19
**Model:** HP dv9000t
**Processor:** Core 2 Duo 1.83Ghz
**Wireless Card:** Intel 3945
**Graphics Card:** Nvidia 7600 Go
**Gutsy Tribe (Version):** 4 32bit
**Kernel Options:** None

Without spending much time testing Gutsy Tribe 4, the one thing I did notice was that support of the Intel 3945 has been overlooked during development so far. The card is still in the Restricted Drivers Manager, it is detected, but it could not scan for any networks. Has anyone else been having the same problem, or one related to this?

I will post more once I get time.

---

### Post by Jukka-Pekka on 2007-08-19
Model:nc8430
Processor:Intel Core2Duo T7200
Wireless Card:Broadcom 4311 -based integrated WLAN
Graphics Card:ATI Mobility Radeon X1600
Gutsy Tribe (Version): 4 amd64, daily build 19.8.2007

Screen resolution (native 1680x1050) was not recognized
Graphics acceleration does not work properly (no advanced effects for desktop) and crashes with the restricted driver manager.
If i get ATI fglrx running properly, there is a problem with the screen resolution...when screen is fine, fglrxinfo reports the mesa drivers again, simultaneously the restricted driver manager shows ATI-drivers to be in use...strange.

WLAN did not work (the card was not recognized, no wireless connections showed up) and network manager crashes when setting up manually. Changed to ndiswrapper and proprietary HP WLAN driver, works flawlessly now! (Edit:20.8.)

Power management problems: High heat and a lot of fan noise -> low battery life.
Could it be that CPU voltage regulation does not work properly? The 1-2 GHz steppings seem to work, but still the heat is up a lot compared to WinXP.
Maybe the graphics card is constantly on full "revs" as well?

CD/DVD combo works
USB memory sticks work
SD-card reader works
Tv-tuner (Terratec Cinergy DT USB XS Diversity) does not work out-of-the-box.

Will return and edit as i test more...
Jukka

---

### Post by popch on 2007-08-19
I have an hp laptop (compaq nc6220) but will not able to install Gutsy as it is my only computer (at the moment). Will a function check using the live CD be useful as well?

---

### Post by EXCiD3 on 2007-08-19
> **popch said:**
> I have an hp laptop (compaq nc6220) but will not able to install Gutsy as it is my only computer (at the moment). Will a function check using the live CD be useful as well?

By all means, go right ahead. As usually if it won't work in the Live CD, then it probably won't work after installation.

---

### Post by Ayuthia on 2007-08-19
**Model:** dv6338se
**Processor:** AMD Turion 64 X2 1.8Mhz
**Wireless Card:** Broadcom 4311 (Dell Wireless 1390)
**Graphics Card:** Nvidia GeForce Go 6150
**Gutsy Tribe (Version)**: 4 (Installed using Tribe 3)

Currently using noapic noirqdebug to see if it overcomes the USB disabling issue.  Still using ndiswrapper although bcm43xx-fwcutter appears to work better with WEP encryption.  Does not seem to work with MAC address routers (dhclient fails).  The native driver now does go up to 54 Mbps and the antenna is stronger than the ndiswrapper version.

---

### Post by Jukka-Pekka on 2007-08-19
HP nc8430 with Broadcom 4311-based  WLAN

I had serious problems with the original bcm43xx -solution provided by the restricted-driver-manager. It just wouldn't work.

Finally, I  got the WLAN (non-broadcasting, WPA/TKIP) working in gutsy with ndiswrapper by following these steps:

1.Install ndiswrapper from the Ubuntu repository with Synaptic Package Manager 

2.Remove the old driver: 
# sudo modprobe -r bcm43xx

3.Bblacklist it from not loading again by adding this line to the file /etc/modprobe.d/blacklist:
blacklist bcm43xx

3.Get the proprietary driver from the HP-site: sp34152.exe

4.Extract it: (you may need to install cabextract first with Synaptic as I had to)
# cabextract -a ./sp34152.exe

5.Change into the directory you extracted these files to and: 
# sudo ndiswrapper -i bcmwl5.inf
# sudo ndiswrapper -l

6.To configure ndiswrapper to start on every boot (along with the new driver): 
#sudo ndiswrapper -m
#sudo modprobe ndiswrapper
#sudo echo ndiswrapper > /etc/module

Now I have a fully-functional WLAN. The network-manager works better with this solution in Gutsy (amd64) than with the original driver.

All the best,
Jukka

---

### Post by EXCiD3 on 2007-08-21
Yesterday I tried reinstalling Gutsy. I was unable to get the wireless to work. In the restricted drivers manager it claims to be using the intel 3945 driver, however any time i attempt to use the Network-Manager it crashes. I tried reporting the bug but it was unable to send. 
 
Also, Firefox was not usable. It crashed as soon as it started to display the window.
 
Has anyone else attempted Gutsy installation?

---

### Post by popch on 2007-08-21
Model: hp Compaq nc6220
Processor: Intel(R) Pentium(R) M processor 1.86GHz
Wireless Card: PRO/Wireless 2200BG Network Connection (product ID 16928 (0x4220))
Graphics Card: Mobile 915GM/GMS/910GML Express Graphics Controller (product ID 9618 (0x2592))
Gutsy Tribe (Version):5, I believe. Where do I find that if I forgot to write it down?

Those things work out of the box:
[LIST]
[*]Configuring WLAN with 128 bix hex WEP key with the control panel applet
[*]WLAN on/off hardware key (but apparently not the LED in the key)
[*]SPR on/off key with LED, volume up/down keys
[*]Headphone plug recognition (when activated in control panel)
[*]Info key (brings up help)
[*]fn+F8 (battery state key)
[*]fn+f9..f11 brightness 1/-, contrast
[*]Lid closed key
[*]Num Lock (with LED); embedded numeric keys
[*]Swiss keyboard (partially tested, seems OK)
[*]Touchpad
[*]USB mouse
[*]Menu key
[/LIST]

The following does not work (and lost me all data entered above when I tried before)
[LIST]
[*]fn+f3 (that's the blue moon or crescent which hibernates the machine). It
hibernates OK but does not appear to wake up again. This works fine in Feisty Fawn.[/LIST]

I've run out of things to test. All but hibernate appears to work just fine, out of the box, with no fiddling at all. 

Sorry, forgot to post that I have not installed Gutsy on my laptop as it is my only PC at home. I run it off the live CD.

:)

---

### Post by EXCiD3 on 2007-08-24
**Update: **After yesterday's release of Tribe 5, the ipw3945 driver still does not work correctly. My card never gets configured in order to connect to a network. However I am still finding wireless connections. Anyone else attempt Tribe 5 yet? I just booted off the LiveCD only.

---

### Post by bj139 on 2007-08-25
HP Compaq Presario 2405US  
Full install of Gutsy works well except for wireless.  I installed the bcmwl5.inf driver using ndiswrapper.  The card was detected but I could never get network connectivity with WEP.  I tried the automatic broadcom installer from the forum, now the card is not detected.  I am not sure how to go back since a lot of aptitude packages were updated and upgraded.
I installed Gutsy to a hard disk (160GB) which contained 2 WinXP partitions, system(37GB) and data(37GB).  I reserved half the disk for kubuntu with 3 partitions, /home(57GB),  linux swap(2GB) and /(17GB).  I use GRUB for bootloading.  AVG antivirus showed the MBR had changed and I ignored it in the list.  Eventually, I think it messed up my WinXP installation.  After trying FIXMBR  from recovery console and several recovery installations with no success, I decided to reformat and reinstall WinXP.  Kubuntu was not seen listed in NTLDR so I reinstalled GRUB to the MBR using 2 simple commands someone posted to the forum and was then able to dual boot Win and Kubuntu again.  When AVG noted the changed MBR I then made sure I told it to ignore changes.  It has been fine for the past two weeks.  If only I could get the wireless working it would be almost perfect.  The minor problems with Gutsy seem to be no worse than new Windows releases.  
I would love to be able to eliminate Windows completely but there are a few programs that only work under Windows.  I have been meaning to search for a Windows emulator  for Kubuntu to get around this problem.

---

### Post by EXCiD3 on 2007-08-25
> **bj139 said:**
> HP Compaq Presario 2405US  
Full install of Gutsy works well except for wireless.  I installed the bcmwl5.inf driver using ndiswrapper.  The card was detected but I could never get network connectivity with WEP.  I tried the automatic broadcom installer from the forum, now the card is not detected.  I am not sure how to go back since a lot of aptitude packages were updated and upgraded.
I installed Gutsy to a hard disk (160GB) which contained 2 WinXP partitions, system(37GB) and data(37GB).  I reserved half the disk for kubuntu with 3 partitions, /home(57GB),  linux swap(2GB) and /(17GB).  I use GRUB for bootloading.  AVG antivirus showed the MBR had changed and I ignored it in the list.  Eventually, I think it messed up my WinXP installation.  After trying FIXMBR  from recovery console and several recovery installations with no success, I decided to reformat and reinstall WinXP.  Kubuntu was not seen listed in NTLDR so I reinstalled GRUB to the MBR using 2 simple commands someone posted to the forum and was then able to dual boot Win and Kubuntu again.  When AVG noted the changed MBR I then made sure I told it to ignore changes.  It has been fine for the past two weeks.  If only I could get the wireless working it would be almost perfect.  The minor problems with Gutsy seem to be no worse than new Windows releases.  
I would love to be able to eliminate Windows completely but there are a few programs that only work under Windows.  I have been meaning to search for a Windows emulator  for Kubuntu to get around this problem.

Yeah, I'm not too sure about Gutsy's status on wireless support. My intel 3945 drivers claim they are correct, they detect wireless connections however they cant actually connect. 

For a windows emulator you will want to see if the program is compatible with [Wine.]("http://www.winehq.org/") It is the fastest way of running Windows apps on Linux...However, if it is not compatible you will want to install Windows in a Virtual Machine. Two of the best VM programs are Virtualbox and VMWare. Look into these as each have pros/cons.

---

### Post by Ayuthia on 2007-08-25
> **bj139 said:**
> HP Compaq Presario 2405US  
Full install of Gutsy works well except for wireless.  I installed the bcmwl5.inf driver using ndiswrapper.  The card was detected but I could never get network connectivity with WEP.  I tried the automatic broadcom installer from the forum, now the card is not detected.  I am not sure how to go back since a lot of aptitude packages were updated and upgraded.

If you want to go back to ndiswrapper, all you would need to do is blacklist the bcm43xx driver in /etc/modprobe.d/blacklist, remove the bcm43xx module (via rmmod), and put ndiswrapper back in.  If you need more detail, feel free to ask.

I have been testing out both ndiswrapper and the native bcm43xx drivers and both seem to work (I have the 4311 version).  However I am running into some interference with the native driver that I don't with ndiswrapper.  However the native driver reports a better signal and does now allow up to 54Mps speeds for my chipset.

---

### Post by 3rods on 2007-08-25
Make/Model: HP dv9000t (2.0ghz, GeForce 7600-512mb, Intel 3954ABG, dual SATA HD's)
OS: Vista Ult/XP Pro/Ubuntu Gutsy Herd 4 (5 now after upgrade???) 

Not sure if I'm running herd 5, but I installed herd 4 and then ran the upgrade manager and it installed ~500 updates, so I'm guessing I'm running 5 now. How would I tell for sure? 

On first boot wlan found networks, but it found networks that I usually don't find (i.e. networks I only pickup outside the house) and it didn't pick up my neighbor's. Weird. 

Configuring the WPA2 (psk) network through the GUI in the networking menu would not connect.I manually changed the /etc/network/interfaces to include my (non-broadcast) wlan WPA2 configuration. Then I ran /etc/init.d/networking restart , but it did not link up. So I rebooted and then it worked.

I installed the restricted drivers manager and checked the nVidia driver for later cards (both were checked after reboot- not sure why there are two if it installs both anyway) and restarted. I enabled desktop effects (now in appearance menu), but my window bar with minimize/maximize/etc was missing. I restarted X, and changed the settings (back and forth) and reloaded the theme- now it seems to work.

STAND BY AND HIBERNATE WORK!!!! 
These seem to be working great so far. 

Three issues so far: 

1. Sound does not work. VLC and totem appear to be playing, but no sound. When I go to the sound menu under the system tab, the test plays a LOUD beep, but it won't play MP3's (after restricted auto install). 

2. The mute button does not switch colors when muted. I know this seems minor, but I mention it b/c I think it might be related to not hearing sound output. The on-screen pop-up shows the raising, lowering and muting of the sound, but the hardware mute never changes.  

3. Screen brightness. For some reason the screen will dim of get brighter automatically for no reason. (Am I hitting a short-cut by accident w/ the touchpad scroll??)

Feisty did not have issues with the buttons or the sound. It DID, however, have issues with hibernate and stand by and that's why I'm going to stick with alpha/beta testing Gutsy all the way to release. 


I hope this helps. (is this even helpful)

Anyone have ideas on how to get sound/hareware keys going?

---

### Post by pamagen on 2007-08-25
Model: NX7400, v.RU427ET, bios F.0B
Processor: Intel Core2 T5600  @ 1.83GHz
Wireless Card: Intel 3945ABG
Graphics Card:  Intel 945GM
Gutsy Tribe (Version): Tribe 5

This is upgraded from Feisty.

Broken as writing:
sound (buttons works, gui responses as should, but mute-lied stays on)
vmware-server (this is really bad)

Pros:
native resolution works without 915resolution (1680x1050, started with wrong DPI, though)
thunderbird 2
pidgin

Cons:
too much eyecandy by default
4gb memory not recognized out-off-the--box

Everything else seems to work as well then before upgrading.
Reason to upgrade is newer intel-vgadriver, and to finally make hibernation work as should.
After those, this laptop is just perfect.

---

### Post by Ayuthia on 2007-08-25
> **3rods said:**
> Anyone have ideas on how to get sound/hareware keys going?

Sound is currently being fixed by the developers and it sounds like an update will be coming soon.  The mute is not switching colors because of the same reason--I think it has something to do with the volume keys are pointing to the headphones instead of the speakers.  Here are some links from the Gutsy forum that explain and show ways to fix if you don't want to wait for the update:
[http://ubuntuforums.org/showthread.php?t=532408&page=2](http://ubuntuforums.org/showthread.php?t=532408&page=2)
[http://ubuntuforums.org/showthread.php?t=533668](http://ubuntuforums.org/showthread.php?t=533668)

---

### Post by EXCiD3 on 2007-08-25
> **Ayuthia said:**
> Sound is currently being fixed by the developers and it sounds like an update will be coming soon.  The mute is not switching colors because of the same reason--I think it has something to do with the volume keys are pointing to the headphones instead of the speakers.  Here are some links from the Gutsy forum that explain and show ways to fix if you don't want to wait for the update:
[http://ubuntuforums.org/showthread.php?t=532408&page=2](http://ubuntuforums.org/showthread.php?t=532408&page=2)
[http://ubuntuforums.org/showthread.php?t=533668](http://ubuntuforums.org/showthread.php?t=533668)


Thanks for this info. Sounds like this will get fixed in the next release or so. After all Gutsy isnt even near completion...

---

### Post by pamagen on 2007-08-28
sound did get fixed in today's update. laptop is NX7400 with Intel HD Audio.

---

### Post by EXCiD3 on 2007-08-28
Ah, good to know. I may reinstall and update to see what gets fixed. Thanks for the update!

---

### Post by doug98382 on 2007-08-28
Compaq Presario F572US 
AMD Athlon 64x2 Dual Core TK 53
1.7 GHz 960 Mb RAM
nVidia GeForce Go 6100
HD 80 Gb Toshiba SCSI

Gutsy Gibbon Tribe 5 hung up during Live Disk at loading drivers.

So I went back to 7.04 install with a forum suggestion to use NOAPIC, which now has me into the install. 

Conclusion - I believe the nVidia 6100 is not yet supported in gutsy. 
Staples had a big sale, good deal on these laptops.
doug98382

---

### Post by EXCiD3 on 2007-08-28
Yes, there have been plenty of problems going around with the Nvidia 6100 series of graphics cards. Hopefully Gutsy's final release will fix these problems.

---

### Post by doug98382 on 2007-08-28
Regarding ... "problems with the Nvidia 6100 series of graphics cards," prior to Gutsy's final release, can you point me to areas that I can research to fix this? 

The installation completed itself - using Alternative 7.04 amd64 - burned 26aug07.
But after removing the install disk and rebooting, it now stops/hangs (several tries) with the orange install indicator about half way completed. 

How can one start ubuntu with graphics disabled?

compaq presario F572US 1.7 MHz AMD Athlon 64x2 dualcore TK 53
nVidia GeForce Go 6100
RAM 1 Gb
HD 80 GB Toshiba SCSI SATA

I am learning as I go and appreciate suggestions, thanks.
I have 7.04 on my desktop and am at the point where I use Ubuntu almost exclusively.

---

### Post by marc66thomas on 2007-08-28
doug98382:
I believe you, and I have almost the same issues and you're just two steps in front of me on the install. [http://ubuntuforums.org/showthread.php?t=504255&highlight=compaq+Presario+F500](http://ubuntuforums.org/showthread.php?t=504255&highlight=compaq+Presario+F500) if this post  helps you, can you confirm you get it booting properly? 
PS the hang is (based upon my recent reading), may be, the noapic or the nolapic add to the grub boot will get you past the Orange hang screen (but probably reduced functionality).

Hope you get it loading

---

### Post by EXCiD3 on 2007-08-28
After reading an article posted on Digg.com yesterday, I found out that there is a possiblity of the Broadcom Drivers being included in the Restricted Drivers Manager. Can anyone confirm this?

---

### Post by johskar on 2007-09-01
Model: HP Pavilion tx1128ea ( tx1000 series )
Processor: AMD Turion(tm) 64 x2 Mobile Technology TL-52
Wireless Card: Broadcom bcm43xx based (using ndiswrapper)
Graphics Card: nVidia Corporation C51 [Geforce 6150 Go]
Gutsy Tribe (Version): TR5 (alternate x86 install cd)

Needs noapic opion in boot string for not to freeze, and irqpoll option for usbports to work.

Graphics card works nicely out of the box with the bundled nvidia-glx-new binary driver and I can Alt-F1-F6 without X crashing like it did in Feisty.

The WLan I got working by reading this [guide]("http://ubuntuforums.org/showthread.php?t=297092"), as the bcm43xx kernel module did not work for me.

Sound I got working by editing in the following line in the end of /etc/modprobe.d/alsa-base
> options snd-hda-intel index=0 model=3stack position_fix=0 single_cmd=0

Haven't tried to get the touchscreen to work yet, but lsusb show it as:
> Bus 002 Device 006: ID 0eef:0001 D-WAV Scientific Co., Ltd eGalax TouchScreen

Mabye I'll get it working by using this [guide]("http://www.cartft.com/support/drivers/TFT/Linux_HowTo") with some modifications.

Wlan volume and mute buttons works nice, except for the light on mute button wich is orange(muted) all the time.
So far Gutsy is nice :) Will try and add more after I get some more testing and configuring done 8)

More:

Webcamera doesn't work, throu gstreamer-properties I  get the error:
> gstreamer-properties-Message: Error running pipeline 'Video for Linux 2 (v4l2)': Could not get buffers from device '/dev/video0'. [v4l2src_calls.c(1025): gst_v4l2src_capture_init (): /pipeline0/v4l2src3:
error requesting 0 buffers: Cannot allocate memory]
But reading this [bug report]("http://bugzilla.gnome.org/show_bug.cgi?id=467214") I was able to get a feed from the camera.
so this will probably be fixed before Gusty launches.
>  gst-launch-0.10 v4l2src queue-size=2 ! ffmpegcolorspace ! xvimagesink

---

### Post by EXCiD3 on 2007-09-02
Thanks for the info johskar. Looks like 4 days till the Gutsy Tribe 6 release! Please try a fresh install of it and let me know if you notice any differences. Hopefully there will be alot of fixes between Tribe 5 and Tribe 6. It is getting pretty close now to the final release and hopefully it will start shaping up nicely.

---

### Post by fogNL on 2007-09-02
Please post the following things:
Model:    HP-COMPAQ NC6400  (P/N: RB519UA#ABA)
Processor:  Intel Core 2 Duo T7200 @ 2.0GHz
Wireless Card:  Intel 3945
Graphics Card:  ATI Radeon Mobility X1300  (PCIID: 1002:714A)
Gutsy Tribe (Version): Tribe 5

Experiences:

With all K/Ubuntu releases from Feisty to present I have not been able to run the Live Installer cd's without first letting it kicking me to console and then connecting to the internet and downloading the ati proprietary driver (xorg-driver-fglrx).  This is something that I feel should be fixed asap.

The wireless works fine, looks like the power management works fine, resolution defaults to the optimal 1280x800 for this 14.1" screen (after ati binary driver install).

Further information can be found on my wiki page:
[https://wiki.ubuntu.com/LaptopTestingTeam/HPNC6400]("https://wiki.ubuntu.com/LaptopTestingTeam/HPNC6400")

---

### Post by EXCiD3 on 2007-09-02
> **cquilliam said:**
> With all K/Ubuntu releases from Feisty to present I have not been able to run the Live Installer cd's without first letting it kicking me to console and then connecting to the internet and downloading the ati proprietary driver (xorg-driver-fglrx).  This is something that I feel should be fixed asap.

Fortunately for us this will be resolved with the release of Bulletproof X. Essentially it is a failsafe for the xserver. If it detects problems, instead of just crashing with an error (reminds me of Windows ;)) it will detect which driver (usually vesa, nv, etc.) works correctly and will use that driver instead of dropping you to a terminal. Unfortunately the Proprietary drivers will still be unable to come packaged with Ubuntu as they do not fit the definition of "free software."

Taken from the Bulletproof X Wiki:
> Live CD  If there is an Xorg startup failure when running the live-cd, then it should directly go to vesa mode without requiring any configuration step.

This should hopefully fix many issues trying to get the Live CD to boot and/or running an installed copy of Ubuntu. Unfortunately KDE users are out of luck as they have not been able to integrate it into KDM as of now.

---

### Post by bereanone on 2007-09-02
Model:HP Pavillion dv5040us
Processor: AMD Turion64
Wireless Card:Broadcom 4311
Graphics Card:ATI Mobility Radeon Xpress 200 series
Gutsey Tribe: I tried several Gutsey downloads one for the desktop and lap top because I thought I might get different results from either one, gutsy-desktop-amd64 was one, the other I didn't save the name of.  So far I haven't gotten ANY of them to boot. The furthest I have gotten is a textured brown screen with nothing on it.  Fiesty Fawn at least opens although I have yet to get the wireless card to work. I also can't get ANYONE to help me with it. If I can't boot from CD and get wireless, I cannot afford to ditch windows.  I would no longer be able to use my laptop on the internet.VERRY frustrating.
Dean

---

### Post by bereanone on 2007-09-02
Posted earlier no luck. Saw Tribe 5 available, downloaded it, and it boots o.k. but same results as Fiesty Fawn, NO BROADCOM 4311 SUPPORT!!!  
Dean

---

### Post by EXCiD3 on 2007-09-03
I read somewhere that it was going to be included in the Restricted Drivers Manager, as of now it appears that it is not. You would be best off using Feisty until Gutsy's final release in October...

---

### Post by 4partee on 2007-09-03
> **bj139 said:**
> so I reinstalled GRUB to the MBR using 2 simple commands someone posted to the forum and was then able to dual boot 

Please! could someone post those commands?  I had to restore Vista after installing Gutsy Tribe 5 AMD64.



Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x75d10501

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4207    33792696    7  HPFS/NTFS
/dev/sda2            8873        9729     6883852+   7  HPFS/NTFS
/dev/sda3            4208        8675    35889210   83  Linux
/dev/sda4            8676        8872     1582402+   5  Extended
/dev/sda5            8676        8872     1582371   82  Linux swap / Solaris

Partition table entries are not in disk order
ubuntu@ubuntu:~$ 

root@ubuntu:/mnt/boot/grub# grep -v "#" menu.lst

default         0

timeout         10

title           Ubuntu, kernel 2.6.22-10-generic
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.22-10-generic root=UUID=5cc8d91f-59cb-4063-8715-b2e0bbff275a ro quiet splash noapic
initrd          /boot/initrd.img-2.6.22-10-generic
quiet

title           Ubuntu, kernel 2.6.22-10-generic (recovery mode)
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.22-10-generic root=UUID=5cc8d91f-59cb-4063-8715-b2e0bbff275a ro single
initrd          /boot/initrd.img-2.6.22-10-generic

title           Ubuntu, memtest86+
root            (hd0,2)
kernel          /boot/memtest86+.bin
quiet


title           Other operating systems:
root


title           Windows Vista/Longhorn (loader)
root            (hd0,1)
savedefault
makeactive
chainloader     +1

root@ubuntu:/mnt/boot/grub#

---

### Post by EXCiD3 on 2007-09-03
> **4partee said:**
> Please! could someone post those commands?  I had to restore Vista after installing Gutsy Tribe 5 AMD64.

This is taken from another thread on the forums: >  Boot into the live Ubuntu cd. This can be the live installer cd or the older live session Ubuntu cds.

When you get to the desktop open a terminal and enter. (I am going to give you the commands and then I will explain them later)

     Code:
     sudo grub 
This will get you a "grub>" prompt (i.e. the grub shell). At grub>. enter these commands

     Code:
     find /boot/grub/stage1 
This will return a location. If you have more than one, select the installation that you want to provide the grub files.
Next, THIS IS IMPORTANT, whatever was returned for the find command use it in the next line (you are still at grub>. when you enter the next 3 commands)

     Code:
     root (hd?,?) 
Again use the value from the find command i.e. if find returned (hd0,1) then you would enter root (hd0,1)

Next enter the command to install grub to the mbr

     Code:
     setup (hd0) 
Finally exit the grub shell
     Code:
     quit 
That is it. Grub will be installed to the mbr.
When you reboot, you will have the grub menu at startup.Original thread can be found here: [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

I have done this several times before on my own systems and can help you out if you encounter any problems. Make sure you read through the Howto in the link before asking any other questions. If you do have a question, either PM or IM me or post on THAT thread, not here as this has to do with running Gutsy not installing Grub.

---

### Post by arieloq on 2007-09-04
Model:Compaq Presario V3317la
Processor:AMD Sempron 3500+ 1800Mhz
Wireless Card:Bradcom 4311 (Dell 1390)
Graphics Card:Nvidia 6150 Go
Gutsy Tribe (Version):Gutsy Tribe 5

Live cd only with acpi=off, when the serverx starts fail to detect the resolution... crtl+alt+backspace and he comes alive, mouse stop response 5 seconds latter...
Instalation no response some times... stop working when partitioning hard drive, i have 3 partitios with ntfs and 2 ext3 1 swap, restricted drives doesnt work because i not conected to network the nvidia restricted driver not download, bmc43xx_firmware doesnt load... i going to cut my left egg... well is an apha software... y wait for the beta...

---

### Post by EXCiD3 on 2007-09-04
lol, sounds like you dont like it so far ;) In the next couple of days Tribe 6 is going to be released, you might want to try it out. Its the last tribe before the prerelease andthen the final release...hopefully things will start coming together.

---

### Post by drf_av on 2007-09-11
[B]Model: HP dv6560el
Processor: Intel Core 2 Duo T7300
Wireless Card: Intel Wireless PRO 3945ABG
Graphics Card: nVidia 8600M
Gutsy Tribe (Version): Tribe 5 constantly apt-upgraded[/B]

Everything works out of the box execpt for audio ( I had to install realtek drivers ) and for the integrated webcam. A great improvement over Feisty

---

### Post by dgadola on 2007-09-15
**Model:** HP Pavilion dv6565us
**Processor:** Intel Core 2 Duo T5250 @ 1.5Ghz
**Wireless Card:** Intel PRO/Wireless 4965AGN
**Graphics Card:** Intel GMA X3100
**Gutsy Tribe (Version):** Tribe 5 for amd64

i cant boot the livecd... freezes when try to start bluetooth services  "*Starting Bluetooth services", i add options before booting but nothing changes (noapic irqpoll noirqdebug). it`s strange to stop when loading bluetooth because the laptop doesn`t have bluetooth!.

sorry for my english.

thanks

---

### Post by ydeardorff on 2007-09-22
hello, to all this is my first post in this forum.

I am new to linux, so be nice lol.

First off,

Model: 2002 HP ze5375us 
Processor: P4 2.4
Wireless Card: unknown but doesnt work
Graphics Card: ATI PCI IGP 340M
Gutsy Tribe (Version): ubuntu studio (feisty) pure lin-no-win

I have for quite sometime found many computer expert migrate to linux.
In my irritation to MS win I decided to do the same.
Overall Im very satisfied with Ubuntu Studio. I do think its kinda of silly to not include DVD playback, and MP3 support with a base operating system though lol.

I have found, My main issues are drivers, and especially figuring out how to install things (NOT USING THE NET) If you download its almost not usable. LOL I have scoured the net for days till 2am often and most every how to I find is written well, but written for someone whom knows there way around linux already.
 I need pictures! Im a guy ok :lolflag:

I have attemted mant time to install the ATI linux drivers, only to lose my laptop until the xorg recevery command can be typed in. I have the ATI console installed, but no 3D. No wireless card drivers, even simply things like a recoil game pad for playing SNES ROMS, doesnt work. Is there some sort of PNP download I can get to make things alittle easier?

Even people I talk to about linux tell me if theres issues with drivers they wouldnt switch from windows. We all played this game with windows 95. Has anyone fixed this for linux yet? 
Please help! My job doesnt have internet except for work so not even WIFI, I can get file to my laptop from my desktop via flash drive but thats it. I really need some help.
I only figured out today how to switch into the root or super user mode.
And where my desktop folder is, ect very basic stuff.
Im looking for all the ease of use found in windows, with out all the hassles of windows. 

Any ideas?

Thanks

Please feel free to email or PM me. Im apparently alone here, no other linux users to ask Q's 2.

---

### Post by jack_mcdowell on 2007-09-23
Model:HP Pavilion dv6000us
Processor:Turion X2 1600Mhz
Wireless Card:Broadcom 4311 (Dell 1390)
Graphics Card:Nvidia 6150 Go
Gutsy Tribe (Version):Gutsy Tribe 5

I have had a lot of problems with gutsy and this computer, to boot I need to use noapic nolapic as well as irqpoll if I want my usb ports to work, And this only means that it will boot about half the times. But that I can deal with, what really troubles me is that my wifi card, which worked in feisty has disappeared. And by that I mean, gone, completely, it does not even show up if I do an lspci. The 'funny' thing is that twice when I ran upgrades, the card showed up and installed it's drivers, and even let me connect to a network. However, when it asked me to reboot, it disappeared completely again...
Any ideas?
Thank you, Jack

---

### Post by Ayuthia on 2007-09-23
> **jack_mcdowell said:**
> Model:HP Pavilion dv6000us
Processor:Turion X2 1600Mhz
Wireless Card:Broadcom 4311 (Dell 1390)
Graphics Card:Nvidia 6150 Go
Gutsy Tribe (Version):Gutsy Tribe 5

I have had a lot of problems with gutsy and this computer, to boot I need to use noapic nolapic as well as irqpoll if I want my usb ports to work, And this only means that it will boot about half the times. But that I can deal with, what really troubles me is that my wifi card, which worked in feisty has disappeared. And by that I mean, gone, completely, it does not even show up if I do an lspci. The 'funny' thing is that twice when I ran upgrades, the card showed up and installed it's drivers, and even let me connect to a network. However, when it asked me to reboot, it disappeared completely again...
Any ideas?
Thank you, Jack
I am not too sure about your network card.  I have a similar setup, but I am using noapic noirqdebug and it seems to be working fine.  I can still get access to my USB without any lockups.  I used to have some spurious irq 15 problems, which killed ndiswrapper, but it seems to be stable now since I have not seen it for a couple of weeks.

---

### Post by EXCiD3 on 2007-09-23
Probably the best idea is just to check for updates as much as possible. Gutsy is finally pulling together and getting lots of the bugs fixed.

---

### Post by jack_mcdowell on 2007-09-24
> **Ayuthia said:**
> I am not too sure about your network card.  I have a similar setup, but I am using noapic noirqdebug and it seems to be working fine.  I can still get access to my USB without any lockups.  I used to have some spurious irq 15 problems, which killed ndiswrapper, but it seems to be stable now since I have not seen it for a couple of weeks.

I really don't know what it could be. Irq 7 was giving me a lot of problems until I started running irqpoll. On the irc channel someone recommended that I try a previous kernel but I haven't gotten around to it yet, and the newest one (23-rc7) has not fixed it either. Does someone know what the earliest kernel which fully supports gutsy is?
Thanks,
Jack

---

### Post by R.Saud on 2007-09-25
[CENTER][SIZE="4"]Model: HP Pavilion dv2297ea
Processor: Core 2 Duo 2Ghz
Graphics Card: Nvidia GeForce Go 7200

I can't find the Graphics Card driver

can you help me[/SIZE][/CENTER]

---

### Post by EXCiD3 on 2007-09-25
> **R.Saud said:**
> [CENTER][SIZE=4]I can't find the Graphics Card driver

can you help me[/SIZE][/CENTER]


[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

---

### Post by Ayuthia on 2007-09-27
A couple of days ago, I wiped out my linux partitions (by mistake).  On the positive side, I rebuilt Kubuntu using Gutsy (from the tribe-3 CD) and was able to get ndiswrapper to work by using only the live cd!  All I needed was to find a working driver to use and I was ready to go!  The bcm43xx-fwcutter option also appeared in the linux-restricted-drivers again which is a positive also.  I did not use it because I was getting a lot of interference while using it, but it does now provide 54Mb speeds for the 4311.

Nvidia was also in the restricted drivers and I used that to get my graphics card (6150 Go) running.

---

### Post by EXCiD3 on 2007-09-27
Hey thanks alot, I think I am going to go ahead and try out a fresh install of Tribe 5 and see what works for the Intel based laptops. Intel 3945 wireless was broken in Tribe 5 last time I checked, hopefully its owrking now.

---

### Post by skinnie on 2007-09-28
Model:HP DV9575Ep
Processor:Intel T7300 2.0Ghz 4mb Cache 
Wireless Card: Intel® PRO/Wireless 3945ABG
Graphics Card:Nvidia 8600M Gs
Gutsy Tribe (Version):Gutsy Tribe 5

with 7.10 I don't have the windows vista in my grub,I couldn't run envy,it said that the os was not supported,and have no sound..
If anyone could point me to get vista as option in grub I think I could live with the others things or find solutions in the forum.

---

### Post by olavjunior on 2007-09-29
Model:HP DV2130ea
Processor: Intel® Core&#8482; Duo T2250, 1,73 GHz , 2-cache 2 MB, 533 MHz
Wireless Card: IIntel® PRO/Wireless 3945 802.11a/b/g
Graphics Card:Nvidia geforce go 7200
Gutsy (Version):Gutsy beta

Had to install in text-mode. But almost everything work fine. Have the latest nvidia restricted drivers, and they work good. The sound is louder then it was in feisty with the latest alsa. Very nice! The jack work fine as well. There's some bugs with the volume-control though, but it's not hardware-related. 

But sleep and hibernate is still buggy! I have to restart x after the awakening. AND the display-brightness control doesn't work! It worked somewhat in feisty (had to push the button many times until it reduced the brightness).

---

### Post by satempler on 2007-09-30
Model:Compaq Persario V2608WM
Processor:AMD Semperon 3000+ 1.8GHz
Wireless Card:Broadcom AirForce One 4318
Graphics Card:ATI Radeon Xpress 200M
Gutsy Tribe (Version):Beta
 
 After install was completed. System booted without problems. After logging in, I was notified I had 3 peaces of hardware that required restricted drivers. I installed fglrx driver, softmodem drivers, and broadcom firmware. After that was complete, I installed XGLl to be configured later. After i rebooted I logged in and found XGL started automagicly and desktop effects was enabled. Aparently it's not required to create the startxgl.sh script or add a XGL session. All effects are fast and responsive like they should be.

---

### Post by Vispen74 on 2007-09-30
Model: HP Pavilion tx1270 (tx1200-series)
Processor:AMD 64 Turion X2 TL-60
Wireless Card: Broadcom a/b/g/Draft-N
Graphics Card:Nvidia GeForce 6150 Go
Gutsy Tribe (Version): Gutsy AMD64 Beta 1

Live-DVD will start if pressing "F6" and add "noapic" in the first screen.

Installs with text-install, then it is not able to boot. Adding command "noapic" in GRUB makes the computer boot.

Following is NOT working after install:
* Boot up without editing GRUB
* Braodcom WLAN
* Touchscreen
* Soundcard
* Fingerprint Reader
* media and rotate buttons

No success with the BCM43xx driver or Ndiswrapper for the WLAN yet.

Working on these problems....

---

### Post by Cuppa-Chino on 2007-09-30
> **johskar said:**
> Model: HP Pavilion tx1128ea ( tx1000 series )
Processor: AMD Turion(tm) 64 x2 Mobile Technology TL-52
Wireless Card: Broadcom bcm43xx based (using ndiswrapper)
Graphics Card: nVidia Corporation C51 [Geforce 6150 Go]
Gutsy Tribe (Version): TR5 (alternate x86 install cd)

Needs noapic opion in boot string for not to freeze, and irqpoll option for usbports to work.

Graphics card works nicely out of the box with the bundled nvidia-glx-new binary driver and I can Alt-F1-F6 without X crashing like it did in Feisty.

The WLan I got working by reading this [guide]("http://ubuntuforums.org/showthread.php?t=297092"), as the bcm43xx kernel module did not work for me.

Sound I got working by editing in the following line in the end of /etc/modprobe.d/alsa-base


Haven't tried to get the touchscreen to work yet, but lsusb show it as:


Mabye I'll get it working by using this [guide]("http://www.cartft.com/support/drivers/TFT/Linux_HowTo") with some modifications.

Wlan volume and mute buttons works nice, except for the light on mute button wich is orange(muted) all the time.
So far Gutsy is nice :) Will try and add more after I get some more testing and configuring done 8)

More:

Webcamera doesn't work, throu gstreamer-properties I  get the error:

But reading this [bug report]("http://bugzilla.gnome.org/show_bug.cgi?id=467214") I was able to get a feed from the camera.
so this will probably be fixed before Gusty launches.

hmmm -- I was totally unsucessful with my gutsy upgrade, could NOT get WPA to work on Ndiswrapper consistently (wpasupplicant problems, need manual restarts, transmission was slow), Fan was always on, machine seemed to be hot all the time .. pointers welcome

---

### Post by mwacky on 2007-10-02
Model:HP Pavilion zv6000
Processor:AMD 64 3200
Wireless Card:Broadcom 802.11 b/g WLAN
Graphics Card:ATI Radeon Xpress 200M
Gutsy Tribe (Version):Beta AMD64

No success with the BCM43xx driver could not see wireless networks or connect.

Didn't check into graphics, just booted into Live CD and cleared space, will try graphics and wireless later.

---

### Post by Ayuthia on 2007-10-02
> **mwacky said:**
> Model:HP Pavilion zv6000
Processor:AMD 64 3200
Wireless Card:Broadcom 802.11 b/g WLAN
Graphics Card:ATI Radeon Xpress 200M
Gutsy Tribe (Version):Beta AMD64

No success with the BCM43xx driver could not see wireless networks or connect.

Didn't check into graphics, just booted into Live CD and cleared space, will try graphics and wireless later.
Can you post your lspci -nn information for your wireless card?  I am guessing that if you install Ubuntu, the linux-restricted-drivers will find your card and provide an option to have bcm43xx-fwcutter installed (you will need an internet connection to make it work unless you have the driver available).

---

### Post by john_brown_jr on 2007-10-02
Model: HP Compaq NX7400
Processor: Intel Celeron 1.7
Wireless Card: Broadcom
Graphics Card: Intel
Gutsy Tribe (Version): Gutsy Beta + all updates as of 2nd October, 2007

Allmost everything seems to function properly. I did not test WiFi, but my neighbours net was deteced all-right.

1) Screen resolution was not detected automatically, and I had to edit xorg.conf even after having changed it in the screen-res configuration applet.

2) ACPI support is broken, though. It has problems waking up from suspend/hibernate. It actually wakes up, but it takes a very long (30 sec.) time. Pressing Fn+Brightness up/down helps in case it does not wake up after 30 sec.

3) Switching users kills the mouse (i mean, trackpad support). It is possible to re-enable it by executing 'sudo modprobe psmouse'.

---

### Post by Ayuthia on 2007-10-02
When posting your information, can you also include your kernel parameters (noapic noirqdebug...)?  It would be nice to see which ones you are using and see which works well and which options causes problems.

---

### Post by smurphy_it on 2007-10-02
Model: HP Dv2020CA
Processor: AMD Turion 64 X2 ML-50 1.6GHz
Network Card: nVidia chipset
Wireless Card: Broadcom 4311 (Dell Wireless 1390 Wlan mini-pci card)
Graphics Card:  nVidia Geforce 6150 go
Sound Card:  nVidia chipset (hda-intel)

1.) Install went through no problem. :)
2.) Network Card works no problem.  :)
3.) Native WIFI Linux driver not working (bcm43xx)   :(
4.) Sound works fine.  Headphones have auto jack sensing enabled, and automatically swap to headphones when plugged in.  When you unplug headphones, it is detected and automatically swapped back to normal speakers.  :guitar:
5.) Internal Microphone and External microphone work out of the box. (didn't with feisty).  :popcorn:
6.) Video Card Direct Rendering shut off (Using Mesa GLX Indirect driver).  Envy should fix this.
7.)  Web Cam works out of the box using videoview, and should work fine with Amsn etc (that part is untested at the moment).
8.)  5-in-1 Card reader will read SD cards no problem.  (never tested this in previous Ubuntu versions).

Hibernation mode = Not Working.  Gives a screen full of errors as it is attempting to enable hibernation, then on bootup you get the "Unlock screen" prompt to login, and a message shows up indicating that hibernation mode failed. :(

Suspend Mode = Enables (only error message is regarding the wifi bcm43xx device) then power light blinks continually. Upon hitting the standby button, the screen stays black and never initializes. :(

---

### Post by Ian Milligan on 2007-10-02
Model: HP dv9500z
Gutsy: Beta AMD64
Processor: AMD Turion 64 X2 TL-62 2.2GHz
Wireless: Broadcom BCM4321AG
Graphics: NVidia Geforce 8400GM

installed from the alternative CD.  Noapic or addition IRQ paramaters NOT needed to boot.  HOWEVER, the splash simply turned my screen off (no signal from laptop) while the computer was still running.  Let run for several minutes, nothing ever popped up.  If the splash parameter is removed it boots fine, and X starts fine.  Ethernet works, but wireless is completely unsupported (no option under restricted).  Firefox crashes immediately.  Various packages have errors installing.  Screen is black resuming from a suspend.  I'm currently working on getting wireless through ndiswrapper.  I find it odd that X starts fine, it even detected the 1680x1050 resolution but the splash is completely broken.  I have not found anyone else without that problem.
Update:
Today I updated from kernel 2.6.22-15 to 2.6.22-17.  The GTK tool found  [here](http://ubuntuforums.org/showthread.php?t=405990) allowed me to get wireless working quite effortlessly with ndiswrapper.  Nothing was necessary except that program and an internet connection (presumably through ethernet).  After the tool terminated I was immediately able to connect to a wireless network with two clicks, no rebooting or configuration necessary, and it now works flawlessly.  I was quite impressed.  The restricted driver manager was able to install the nvidia drivers fine, and strangely after this happened not only did the 3d effects work, but the sound started working as well.  I have no idea why.  I then tested suspend and hibernate, and they are both working now.  Even the media key things are working without any work on my part, yet strangely enabling the splash kernel option still hangs the boot.  Hardly a serious issue but baffling non the less.  Well that's it, I now plan on figuring out what is wrong with the splash.  Perhaps its not a problem specific to this laptop.

---

### Post by Azrael Nightwalker on 2007-10-02
Model: HP Compaq nx6325 EY349EA
Processor: AMD Turion64 X2 1.6 Ghz
Wireless Card: Broadcom BCM4312 (or 4310 as reported in previous Ubuntu versions)
Graphics Card: ATI Radeon Xpress 200M (RS485 [Radeon Xpress 1100 IGP])
Gutsy Tribe (Version): beta1
Kernel Options: none

Desktop CD hangs while starting Gnome - you have to use it in safe graphics mode. Alternate CD hangs at installation.
Wifi works with ndiswrapper.
Graphics works with fglrx.
Bluetooth works, but when you install gnome-vfs-obexftp you can easily browse your phone in nautilus thru the bluetooth system tray icon.

Details:
[https://wiki.ubuntu.com/LaptopTestingTeam/HPNX6325](https://wiki.ubuntu.com/LaptopTestingTeam/HPNX6325)

---

### Post by EXCiD3 on 2007-10-02
To ensure the most compatibility, use the most up to date release of Gutsy. The beta is the most recent official release, however you can get a daily build also which will probably have even better support.

---

### Post by Ian Milligan on 2007-10-02
I'm sorry, I'm confused as to why the *alpha* tribe 5 would be newer than the beta.  Sorry if I'm missing something here.

---

### Post by EXCiD3 on 2007-10-03
> **Ian Milligan said:**
> I'm sorry, I'm confused as to why the *alpha* tribe 5 would be newer than the beta.  Sorry if I'm missing something here.

Sorry I meant to say the Beta...sorry if i confused anyone.

---

### Post by dinub1 on 2007-10-03
> **EXCiD3 said:**
> If you have tried installing Gutsy Gibbon on an HP or Compaq laptop, please post feedback on your experience.

Please post the following things:
[B]Model:
Processor:
Wireless Card:
Graphics Card:
Gutsy Tribe (Version):
Kernel Options:
[/B] 
and a detailed description of anything you think is relevant to running Gutsy on HP/Compaq laptops. Once Gutsy is released I plan on creating a Howto which possibly 
covers most (hopefully almost all) of the hardware in the various HP and Compaq laptops, this way there would be one central location for information regarding compatibility with this hardware and Gutsy Gibbon.

OK. Here:

Model: HP Pavilion ZE4145
Processor: AMD Athlon XP1800+
RAM: 512 MB PC2100 (266 MHz)
Wireless Card: D-Link AirPlus XtremeG DWL-G650 (works fine with Knetworkmanager)
Graphics Card: Bulit in ATI Radeon IGP 320M, 32 MB RAM
Gutsy Tribe (Version): Kubuntu/Ubuntu 7.10 beta
Kernel Options: Linux ubuntu 710 2.6.22-12-generic

Detailed description; Upgraded from Ubuntu 7.04. Upgrade went fine, After reboot CPU cooling fan worked continuously and CPU temp reached 65F. Couldnt regulate fan operation as CPU worked continously at full speed. Also CPU load was excessive. Close to 100% on idle. After checking forums and no tips worked, I decided to backup and erase the Linux partitions.However if I regulated the CPU frequency to go to "powersave" mode, temps dropped back to normal, however applictions ran slowly. Reinstalled Kubuntu 7.10 beta from scratch and added Ubuntu to it. Works like a KING and flawlessly now. Temps are normal, fan works internittently and CPU load at idle is only 5 -7%. CPU/Battery condition show now in system tray reporting CPU working in "dynamic" mode. It allocates power only when needed by applications. Othewise goes into powersave mode (662 MHz instead of 1523 MHz). Just as claimed by developers.

Some more... Sounds works now fine, before this, following the upgrade there was no sound. As far as I could see after reinstallation from scratch, Firefox and Opera browsers work fine, I attempted to install Seamonkey, downloaded latest version, couldn't install. Gives mea lib C++ library missing etc... cannot figure out why it doesnt. Attemting to repair using synaptic did not help. Running dual boot with Windows XP Home edition in different partition. After reinstall I needed to edit the /boot/grub/menu.lst file manually in order to enable GRUB hidden menus and added line for Windows XP. Also the NTFS partition needed reconfiguration. It woundt mount by default. Fixed it into the fstab. 
The reistall from scratch has been dome using the Kubuntu 7.10 beta I386 Live CD, alternative options, in text mode, Otherwise all fine.
Otherwise all work fine.

---

### Post by mwacky on 2007-10-03
Hi, had this post the other day:


> Quote:
Originally Posted by mwacky View Post
Model:HP Pavilion zv6000
Processor:AMD 64 3200
Wireless Card:Broadcom 802.11 b/g WLAN
Graphics Card:ATI Radeon Xpress 200M
Gutsy Tribe (Version):Beta AMD64

No success with the BCM43xx driver could not see wireless networks or connect.

Didn't check into graphics, just booted into Live CD and cleared space, will try graphics and wireless later.

Response
Can you post your lspci -nn information for your wireless card? I am guessing that if you install Ubuntu, the linux-restricted-drivers will find your card and provide an option to have bcm43xx-fwcutter installed (you will need an internet connection to make it work unless you have the driver available).

Definitely correct, I did an install and was able to get the wireless going well with ndiswrapper - bcm43xx-fwcutter and restricted driver manager firmware.  Followed this [howto]("http://ubuntuforums.org/showthread.php?t=405990"). 

It actually is performing awesome, but the suspend doesn't seem to work.  

Looks like the graphics is going well, picked up and installed from the restricted drivers manager without breaking it, but don't know that for sure until I can clear more space and install Google Earth.

---

### Post by untjake on 2007-10-04
Please post the following things:
Model: HP dv6626us
Processor: Intel Core 2 Duo T5.25 @ 1.5GHz
Wireless Card: Intel 3945
Graphics Card: Intel GMA x3100
Gutsy Tribe (Version): Tribe 5

I have the same issue with muted sound and mute button color, but I also wanted to mention my problem with the touchpad.

My touchpad mouse enable/disable button opens the help dialog (Ubuntu Help Center) when I press it to enable. A minor issue but I thought it was worth mention.

---

### Post by EXCiD3 on 2007-10-04
I have noticed the same thing when I enable/disable the touchpad also. It is just a minor keybinding issue as the button is detected incorrectly. However if anyone knows how we can disable this that would be a great help as I usually avoid turning it on/off with that button because of this.

---

### Post by Tagallo on 2007-10-04
Model: Compaq Presario V6210BR
Processor: Sempron 3500+
Wireless Card: Broadcom
Graphics Card: NVIDIA GoForce 6150
Gutsy Tribe (Version): Beta i386
Boot Parameters: acpi=off

Well, seams that the only way to get Gutsy to boot here is using acpi=off, with no parameters or with the parameters I use today with Feisty (noapic, ircpoll, noircdebug) the system hangs during boot...
With ACPI off I could not test the power manager, which was the reason for me to try Gutsy... so I'm bit sad right now. I will do further investigations.

---

### Post by JimmyBEng on 2007-10-04
> **EXCiD3 said:**
> I have noticed the same thing when I enable/disable the touchpad also. It is just a minor keybinding issue as the button is detected incorrectly. However if anyone knows how we can disable this that would be a great help as I usually avoid turning it on/off with that button because of this.
This is easy to get rid of.
--go into Perferences->Keyboard Shortcuts
--find the Launch Help Browser option in the Desktop section
--either disable or reassign the shortcut

That had me puzzled for a little bit too.

---

### Post by EXCiD3 on 2007-10-04
> **JimmyBEng said:**
> This is easy to get rid of.
--go into Perferences->Keyboard Shortcuts
--find the Launch Help Browser option in the Desktop section
--either disable or reassign the shortcut

That had me puzzled for a little bit too.

Hey thanks alot! :popcorn:

---

### Post by ydeardorff on 2007-10-05
I had to comopletely dump ubuntu studio from my hard drive. Having only a 40 gig on my HP ZE5375us laptop, I tried to dual boot, everything seemed to work ok, but alas, not having internet while Im out to sea in the Navy makes it impossible to install ubuntu studio, and install anything since it seems you have to have an active internet connection available to update the system. Ill keep an eye on linux for now, I like what I see. But I dont think its quite there yet. Its still too difficult to install and configure, unless your a fairly adept person with computers.

---

### Post by EXCiD3 on 2007-10-05
> **ydeardorff said:**
> I had to comopletely dump ubuntu studio from my hard drive. Having only a 40 gig on my HP ZE5375us laptop, I tried to dual boot, everything seemed to work ok, but alas, not having internet while Im out to sea in the Navy makes it impossible to install ubuntu studio, and install anything since it seems you have to have an active internet connection available to update the system. Ill keep an eye on linux for now, I like what I see. But I dont think its quite there yet. Its still too difficult to install and configure, unless your a fairly adept person with computers.

I am currently working on an innovative solution to update Ubuntu without an active internet connection with [Ayuthia]("http://ubuntuforums.org/member.php?u=286983"). It is called APTonUSB. APTonUSB is a way to access repositories using a client that runs in Windows from a USB drive. This allows easy access to the repositories for people who have no internet, dialup, or low bandwidth internet at home. APTonUSB allows you to dowload updates and packages from the repositories inside Windows allowing access to the repositories on a vast number of computers, providing updates and/or new software for your Ubuntu installation even if you do not have an active internet connection to the machine. Because APTonUSB runs on Windows, it allows users to download these packages at School, Work, an Internet Cafe, friend's house, etc.

For more information on APTonUSB check the links in my signature. ;)

---

### Post by Bannor on 2007-10-05
this issn't really a gutsy thing but I take it from the title that people are having trouble with Compaq and as it happens I am having trouble intalling Ubuntu on my compaq.  If someone would be kind enough to point me to a how to for compaq my errors range from 

freezing at the point were it loads Hardware drivers (fiesty 64 bit) 
freezing when loading network  generally after a series of Firmware load errors 

I also had a no buffer space avalible error

with the alt install Cd the error came back that It could not resize the drive to partition. 

I think the hardware error was related to my wireless mouse.  does noapic issue relate to any of the above mentioned problems.   I am not sure it is my problem because the only tutorial I saw was for a system that had Ubuntu already installed and I can't get that far.  

Finnally I am horrible with terminal, does Gutsy address these issues?  Should I just wait for that to come out?

AMD Turion(TM) 64 X2 Dual-Core Mobile Technology TL-58 (1.9 GHz, 512KB+512KB L2 Cache ) 
1GB DDR2 System Memory (2 Dimm
NVIDIA(R) GeForce Go(R) 7150M 
802.11b/g WLAN 
120GB 5400RPM SATA Hard Drive

---

### Post by allenb on 2007-10-05
[B]Model: Compaq NW8440
Processor: Intel Core 2 Duo T7200 @ 2.00 GHz
Wireless Card: Intel PRO/Wireless 3945ABG
Graphics Card: ATI FireGL V5200
Gutsy Tribe (Version): 5
Boot Parameters: [/B]

I have been running Gutsy Tribe 5 for about a week and a half, and have been pleasantly pleased with the hardware support.  I have my laptop on a docking station (my keyboard, mouse, LAN, and monitor connect though the dock)  and Gutsy detected and set up everything correctly with one exception.

The ATI graphics chip used in this model (FireGL V520) does not work correctly with the drivers included on the Gutsy CD.  To get the video to work, boot from the CD and wait until X tries to load, can't, gripes at you about it, and dumps you to a command line.  Here, you need to do:
sudo apt-get update
sudo apt-get install xorg-driver-fglrx
sudo depmod -a
sudo aticonfig --initial

Note: Internet connection required
Now, type "startx" and X should load properly, albeit possibly not at an ideal resolution.  Install Ubuntu and let your computer reset.  When it tries to load X the next time, you will get the same problem.  This time, all you have to do is:
sudo apt-get install xorg-driver-fglrx
startx

Now, your video should be good to go and you shouldn't have any more problems with X crashing on startup.


Other hardware on the machine:
 * **Touchpad/Touchpoint** - works great
 * **Wired Ethernet** - works great
 * **Wireless LAN** - Gutsy detects the card properly, but I haven't tested it yet
 * **Sound** - works great
 * **Special Keys/Hotkeys** - mute/volume keys work, wireless key toggles bluetooth, "information" button loads Ubuntu help

---

### Post by Traut on 2007-10-05
Model: nx7400 
Processor: Core 2 Duo
Wireless Card: Broadcom Corporation BCM94311MCG wlan mini-PCI
Graphics Card: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller
Gutsy Tribe (Version): Beta


all works just fine. some unusual problems with keyboard module (quite rare I must say) - sometimes when pressing func key it seems like this module is unloading from kernel and then you can't type on keyboard untill system restart

---

### Post by JimmyBEng on 2007-10-06
First the specs:
Model: dv9500t
Processor: Intel Core 2 Duo T7500 (2.2 GHz)
Wireless Card: Intel PRO/wireless 4965 AGN with Bluetooth
Graphics Card: NVIDIA GeForce 8600M GS

I had originally planned to get several more things working and then post how, but I have hit a wall.

Here's what I've done so far:
-64-bit Gutsy Live CD didn't work - regardless on any combinations of the usually suggested parameters (noapic nolapic noacpi irqpoll noirqdebug)
-Installed with 64-bit alternate CD, with no problems

-After installation, had to boot without the splash parameter (i had also deleted quiet)
-boot was hanging on 'Starting Bluetooth Services'
-disabled bluetooth startup script with help from here [UbuntuBootupHowto]("https://help.ubuntu.com/community/UbuntuBootupHowto")

EDIT: there are a couple of ways to disable bluetooth. the way i tried initially caused my USB problems. ([see solution]("http://ubuntuforums.org/showpost.php?p=3512665&postcount=95"))

-Once bluetooth was disabled, boot completed with no problems (splash still disabled).
-Desktop appeared without need for NVIDIA driver (a pleasant surprise)
-was able to install NVIDIA driver with restricted drivers manager
-wireless mostly works (the problems have been trivial and could be network manager)
-all special keys and buttons work (mute doesn't change color, but i don't care)

Problems:
-USB does not work, tried lots of boot parameter combinations. **--SOLVED--** (see edit above)
-sound does not work, have not tried much yet. **[---SOLVED---]("http://ubuntuforums.org/showpost.php?p=3488939&postcount=76")**

Any suggestions on fixing these or places to look for more info on these areas??

---

### Post by AbredPeytr on 2007-10-06
Model:  HP Pavilion dv5053EA
Processor:  AMD Turion 64 
Wireless Card: Broadcom BCM4318
Graphics Card:  Radeon XPRESS 200M 
Gutsy Tribe (Version):  beta release from 29 September / 64 bit

I've been using Gutsy for a week and have wholly enjoyed this upgrade. The installation went faster than that for Feisty Fawn and getting the wireless card to function was much easier (once I activated it in the restricted drivers). I think getting WPA to work was also made easier once I activated the Broadcom driver. 

I was also able to get Compiz to work fairly easily. 

Overall, it is a major advancement in terms of ease of installation.

I did have a scare yesterday after installing some upgrades. After restarting, wireless and sound weren't working. They are now, but I have no idea what I did, other than restarting once again.

---

### Post by JimmyBEng on 2007-10-06
First the specs again:
Model: dv9500t
Processor: Intel Core 2 Duo T7500 (2.2 GHz)
Wireless Card: Intel PRO/wireless 4965 AGN with Bluetooth
Graphics Card: NVIDIA GeForce 8600M GS

I have gotten sound working, and it is all working well.
-all controls work, volume is ok.
-built-in speakers mute automatically with headphones
-microphone jack also works well for input

I found the solution at this site: [http://aldeby.wordpress.com/2007/09/11/howto-ubuntu-on-hp-dv65xx-series-laptop/](http://aldeby.wordpress.com/2007/09/11/howto-ubuntu-on-hp-dv65xx-series-laptop/)
(looks like it was inspired by EXCiD3's feisty HOWTO)

Steps from there reproduced:
> 
```
# apt-get update && apt-get install mercurial build-essential libncurses5 automake autoconf

$ hg clone http://hg.alsa-project.org/alsa-driver alsa-driver
$ hg clone http://hg.alsa-project.org/alsa-kernel alsa-kernel

$ cd alsa-driver
$ ./hgcompile

$ sudo make install-modules

$ hg clone http://hg.alsa-project.org/alsa-util alsa-utils
$ cd alsa-utils
$ ./hgcompile
$ sudo make install

$ sudo alsaconf

```

you can find alsaconf inside alsa-utils/alsaconf/ folder
it may be worth removing ubuntu alsa module too

```

$ sudo mv /lib/modules/2.6.22-12-generic/ubuntu/media/snd-hda-intel/snd-hda-intel.ko /tmp
$ sudo depmod -a

```

now reboot

I had problems with the alsa-utils related steps, but the end result came out ok.

Still working on the USB issue.

---

### Post by EXCiD3 on 2007-10-07
> **JimmyBEng said:**
> looks like it was inspired by EXCiD3's feisty HOWTO

hmmm....it sure does...and he didnt even bother to let me know about it...:confused: At least he linked up to both my threads :D

Looks like it contains some good information...I will have to read through it, personally, i dont know much about any of the laptops except for the Intel based ones...

---

### Post by n1uro on 2007-10-07
Model: HP dv6604nr
Processor: AMD Athlon 64 x2 Dual-Core Processor   TK-55
Wireless Card: Broadcom
Graphics Card: NVIDIA GoForce 7150m
Gutsy Tribe (Version): 5
Boot Parameters: none

Note: when I installed Ubuntu, I had to load the cd with noapci  but after install it's been fine and no lockups. Ubuntu detects the broadcom wifi fine however the wifi doesn't work with the native drivers. I had to blacklist them in modprobe.d and use ndiswrapper. The nVidia-glx-new driver works but I had to hack it. What I did was blacklisted it also in modprobe.d as well as edited kdm so that the first line after start) was "modprobe -r nvidia". It seems xorg prefers to load it by itself as after kdm loads, it appears in lsmod, and before kdm loads, the nVidia splash screen appears for a couple of seconds.

Sound is fine, no problems there at all.

Problems: Ethernet controller: nVidia nForce loads but each boot renames itself! First boot it'll be eth0, next boot it'll be eth1 third boot eth2, and so on.
IEEE 1394  Bus host: Ricoh, detected but not properly functioning

If anyone has the nForce NIC properly working so that it doesn't change it's interface name, please let me know how you did it.

---

### Post by nawitus on 2007-10-07
Model: HP Pavilion dv6544eo
Processor: AMD Turion 64
Wireless Card: Broadcom BCM43xx
Graphics Card: NVIDIA 8400M
Gutsy Tribe (Version): beta / 32 bit

I updated using the update-manager, and had only one problem. Cupsys couldn't install, which I fixed using dpkg -i --force-overwrite (can't recall the exact command). I used Envy script to install my drivers and that was it.

---

### Post by ydeardorff on 2007-10-07
Is linux going to be "ever" as user friendly as windows?
I mean just having to do the sudo apt get, or install stuff via text, is enough for alot of people to say nay right on the spot. Not to mention being able to play linux, windows, and mac software seamlessly, with no issues.

If theres a way to remove the whole text based stuff, AND allow installation from USB, or CD/DVD drive, now that would be a huge leap forward for linux, sure you could leave it in there for advanced users, but not having to use it would be a big plus.
i have been bragging alot about linux to my friends and co workers, but they all say the same thing, loks too complicated, or if I "have" to have an internet connection, or cannot play DVD's, or listen to music right out of the OS  install then no thanks.
I currently only have a 5 year old laptop, with a 40 gig HDD. So Ill be waiting to really give linux a hard try out. But 
Im looking for something to replace windows, with all of its ease of use, but none of its BS.

---

### Post by nawitus on 2007-10-07
> **ydeardorff said:**
> Is linux going to be "ever" as user friendly as windows?
I mean just having to do the sudo apt get, or install stuff via text, is enough for alot of people to say nay right on the spot. Not to mention being able to play linux, windows, and mac software seamlessly, with no issues.

If theres a way to remove the whole text based stuff, AND allow installation from USB, or CD/DVD drive, now that would be a huge leap forward for linux, sure you could leave it in there for advanced users, but not having to use it would be a big plus.
i have been bragging alot about linux to my friends and co workers, but they all say the same thing, loks too complicated, or if I "have" to have an internet connection, or cannot play DVD's, or listen to music right out of the OS  install then no thanks.
I currently only have a 5 year old laptop, with a 40 gig HDD. So Ill be waiting to really give linux a hard try out. But 
Im looking for something to replace windows, with all of its ease of use, but none of its BS.

You can install programs using a graphical user interface (two actually) with Ubuntu. Windows doesn't have a program like that.

Windows doesn't run Mac or Linux binaries.

Windows usually needs a internet connection so you can download drivers (or use driver cd's) so there is not much difference there.

The problem with Ubuntu and linux in general is software and hardware support, and that's not exactly the fault of linux. You need to complain to hardware producers to make linux drivers and release specifications. You can do this "complaining" to buy products that have good linux support.

---

### Post by FrancoNero on 2007-10-07
> **EXCiD3 said:**
> 
[B]Model: HP compaq nx7400
Processor: core 2 duo
Wireless Card: intel
Graphics Card: intel 945 or something
Gutsy Tribe (Version): beta
.

as reported earlier, suspend/resume works now. but hibernating just does not work at all. i have said this numerous times, but I just don't understand why that would be so hard to realize, especially since dell is now cooperating with ubuntu and dell and hp's hardware can't be too different, most laptop acpi stuff is generic anyways..

aside from that, gutsy beta doesnt get screen res and font sizes right immediately, especially not during the live cd run.

it uses way more battery than under windoze.

aside from that, most things work just fine.

---

### Post by ydeardorff on 2007-10-08
> **nawitus said:**
> You can install programs using a graphical user interface (two actually) with Ubuntu. Windows doesn't have a program like that.

Windows doesn't run Mac or Linux binaries.

Windows usually needs a internet connection so you can download drivers (or use driver cd's) so there is not much difference there.

The problem with Ubuntu and linux in general is software and hardware support, and that's not exactly the fault of linux. You need to complain to hardware producers to make linux drivers and release specifications. You can do this "complaining" to buy products that have good linux support.


HE HE,
 I am not by any means complaining about linux, I like linux alot. But at present its not "out of the box" ready yet. I am going to dual boot linux on my next laptop, I just dont have room now. Hell If I knew C++ Id start coding right now for linux to attempt to knock MS win right off the shelves. Offer it like those many AOL coasters Ive had over the years, sitting in a box at the end of every check out stand.

I totaly agree with the soft/hard-ware support issue. Im sure its primarily because linux hasnt taken off yet as a major, or mainstream OS. If I had a winning lottery ticket I would deffo dump money into the development of linux!

True you need to be online to do many things with both OS's, 
However, I think if the text commands were removed or minimized, the ability to run MS win, and OSX software. Having built in DVD/MP3 playback/burning support,  the ability to run/install pretty much anything via CD/DVD rom or USB drive, or directly from the intenet this system would leap to the cover of most major magazines and conversations overnight!

Most people I know do the following with their computers:

ipods, movies, games, roms, or music. Some further uses Ive seen other than myself is A/V editing, 3D game/architectural design.

Other than the ipods I do most of those as well. Thats why I jumped toward Ubuntu studio, both its features, and look. But even with my computer experience, it took me about a week (on and off) to figure alot of it out. 
And I like what I saw. But even trying to grab stuff off the net to install via a USB drive proved nearly impossible to very difficult.
And I also have the dreaded 345M ATI 3d chipset which didnt help. running ubuntu feisty left me in a 2D world.

Im going to keep watching, and reading. I like what I see!  I would really like windows to be bested by linux somday, While still remaining opensource at the same time!

Too bad we cannot open source access to the internet!

Hmm maybe that can be next on the linux to do list! :lolflag:

---

### Post by buntunub on 2007-10-08
After last weekends xorg mishandling with that kernel update, my hp dv2415nr can no longer get dual screens working. In fact, ive had major issues getting the nvidia driver to work at all with xorg nicely and have had to do some fancy shmancy cli stuff to even get it working normally. For some reason, they have disabled the nvidia-settings tool so that wont work either like it did in Feisty. Strange thing is, every time you change settings via that Graphics and Displays tool, it makes a backup of xorg.conf. I now have 112 backups of xorg.conf LOL! Bottom line, Ubuntu  no longer recognizes any of my Displays and cant seem to handle 1280x800, instead it defaults to 1280x960 so my display is just a tad too big, and it can only be done using GENERIC layouts. I did sort of manage to get dual screens working, but only by rewriting xorg.conf by hand so that it was identical to my xorg.conf used in Feisty... But on reboot, it overwrote it and sent it to hell somewhere, and replaced it with another buggy one. Also, Apport reports repeatedly that the Graphics and Displays utility crashes over and over, and attempts to upload a report, but quits halfway through (probably due to overloaded bugtracker servers from this weekends fiasco). So, all this has brought on a couplle questions..

1. Why did they release a half formed kernel update?
2. Is there a patch in the works now to fix the Graphics and Displays utility that seems to have broken xserver config's and... 
3. Why cant Ubuntu recognize my displays any longer? Does that have anything to do with the half-a**ed kernel update?.. Or was it a screw up somewheres else?

Oh, btw, this is a Fresh Install of the Beta release. NOT an upgrade were talking about here. Understood that it is Beta. Understand that development is rapid and fast paced. Yet still, these types of things should not be happening if there is a person at the helm steering the show to ensure that things like this dont happen! Its not hard to do, trust me, I know.


As far as that whole Windows vs. Linux thing.. 

1. How much did/do you pay for one licenced copy of Windows? How much do you pay for one licenced copy of Linux? How many computers can you legally put Windows on with that ONE legally purchased copy of Windows? How many computers can you put Linux on with that one licenced copy of Linux?

2. How is the driver support situation going these days with Vista?.. Oh wait! SP1 out yet? Oh crap! Did you already buy Vista or buy a computer bundled with it (thus paying the M$ tax) just to find out that its a DRM infected mess that only half supports existing hardware?.. But thats not M$'s fault is it? Blame it on the Hardware Vendors for not catering to M$.. Ya! That sounds good! Blame it on the Hardware Vendors! One cannot expect M$ to support backwards compatibility now can they?.. Especially given the fact that they are going to discontinue support on XP soon!

3. How bout them viruses, trojans, and spyware? Gotta love um! Those crazy crackers out there just coding their hearts out sending you the love they never got as a child. Fear not though, McCaffee and Norton to the rescue!!.. Wait.. Thats, to the rescue for $49.95+, and lets not forget how that Antivirus Software does not seem to play too nicely with all those other Programs you paid $$$$ for!!

4. Dont you just love the BSOD? Its so pretty. I hear that by Vista SP2 they are going to make it more than one color! I just cant wait!

5. DRM. Need I say more?.. Do you even know what DRM is, or what it entails and how its going to destroy your ability to have full freedom over your Computer or OS?

6. OOXML. Now I know I should not have to say more about this one. If I do, then I truly fear for our worlds future.

7. Microsoft. This is another one I should not have to say more about. Take a walk down memory lane and review that Corporations history. Take a real close peek at their business practices when it comes to antitrust and monopolistic business practices. Actually, you wont have to walk very far at all because they never stopped breaking laws, using FUD and strongarm tactics, and using somewhat legal extortion tactics. You call that business?.. Hey, I know this guy named Luigi in Vegas I would love for you to meet! He wrote the M$ playbook. Or follows it. Cant really tell.

8. Ever tried Compiz-Fusion? Its awesome isnt it?.. Tried it on Vista yet?.. Oh thats right I forgot. It wont run on Vista!!.. But you can get Vista Aero if you have a supercomputer. But M$ said pre Vista release that it would run fine on an older system with 512M Ram!!

9. How much does your average Linux Distro (or application) Developer get paid to bring you all those Distro's you have tried, and even loved?.. How much?.. Come on take a guess!.. Ill clue you in. 0$, zero, nada, nothing, zilch! The majority work on donations, if they even get that! Yet, they consistently produce results that rival anything Proprietary on the market today!

10. Last but certainly not least, are you dense? Seriously! Not to be rude, but anyone that has more than one brain cell can handle Linux and use a command line for simple things. Dont underestimate the "average user", and DONT judge what other people can/cant do. Do you know some guy/girl named "average user"? Do you even know what an "average user" is?.. Sorry, but ive never met this guy named "average user" so I couldnt tell you wether he can handle Linux or not. I CAN tell you that for over 20 years I was a devoted M$ slave and diligently paid my M$ taxes wherever I could. One day, I picked up a copy of SabayonLinux, tried it, fell it love with it, and got rid of every copy of Windows I could find in my house. Never looked back. Never will. There is no need to because Linux handles every one of my needs without exception... But I guess that means im not an "average user".

---

### Post by EXCiD3 on 2007-10-08
> **buntunub said:**
> After last weekends xorg mishandling with that kernel update, my hp dv2415nr can no longer get dual screens working. In fact, ive had major issues getting the nvidia driver to work at all with xorg nicely and have had to do some fancy shmancy cli stuff to even get it working normally. For some reason, they have disabled the nvidia-settings tool so that wont work either like it did in Feisty. Strange thing is, every time you change settings via that Graphics and Displays tool, it makes a backup of xorg.conf. I now have 112 backups of xorg.conf LOL! Bottom line, Ubuntu  no longer recognizes any of my Displays and cant seem to handle 1280x800, instead it defaults to 1280x960 so my display is just a tad too big, and it can only be done using GENERIC layouts. I did sort of manage to get dual screens working, but only by rewriting xorg.conf by hand so that it was identical to my xorg.conf used in Feisty... But on reboot, it overwrote it and sent it to hell somewhere, and replaced it with another buggy one. Also, Apport reports repeatedly that the Graphics and Displays utility crashes over and over, and attempts to upload a report, but quits halfway through (probably due to overloaded bugtracker servers from this weekends fiasco). So, all this has brought on a couplle questions..

1. Why did they release a half formed kernel update?
2. Is there a patch in the works now to fix the Graphics and Displays utility that seems to have broken xserver config's and... 
3. Why cant Ubuntu recognize my displays any longer? Does that have anything to do with the half-a**ed kernel update?.. Or was it a screw up somewheres else?

Oh, btw, this is a Fresh Install of the Beta release. NOT an upgrade were talking about here. Understood that it is Beta. Understand that development is rapid and fast paced. Yet still, these types of things should not be happening if there is a person at the helm steering the show to ensure that things like this dont happen! Its not hard to do, trust me, I know.

Give it a rest. Gutsy is still in development, they still have 10 days or so until everything has to be packaged correctly. They are probably still patching things together to ensure a quality launch release. The beta really means nothing, you could be running Tribe 1 and have the exact same things so long as you update. I'm sure they are making sure they have as much patched as they can before the release, and they are going to wait until the official release to include it.

IF YOU ARE HAVING TROUBLES WITH GUTSY, GIVE IT ABOUT 9 MORE DAYS! Hopefully once the official release comes out many of our problems should be fixed. I too am using Gutsy Beta with Dual monitors and having a hell of a time configuring hte graphics driver for dual monitors. But stick with it, give it time, it will get better.

---

### Post by FrancoNero on 2007-10-08
graphics/sscreenres is totally screwed up since gutsy beta. either the x or intel or something. either i have the correct screen size, OR the correct screen res or the correct graphics driver. a combination doesnt work, and it breaks my X. crap

---

### Post by ATrentino on 2007-10-08
Model: dv9408nr
Processor: AMD Turion 64x2 TL 56
Wireless Card: Broadcomm 4311
Graphics Card: nVidia GeForce 6150 Go
Gutsy Tribe (Version): Don't know. Where do I look?

I upgraded from Feisty (NB not freshly installed) following [[COLOR="Blue"]these instructions[/COLOR]]("https://help.ubuntu.com/community/GutsyUpgrades"). But I ended up with this kernel: 2.6.22-13-386. With this, the second core wasn't recognized and sound didn't work. I changed kernel to 2.6.22-13-generic and everything works fine now, except that I get errors related to the Wireless Card. Since I don't have opportunities to use wireless, I haven't yet tried to sort it out. Also, while booting I get the same error message that I used to get in Feisty, about BIOS Bug #81. Don't know what, if any, consequences this bug has but it seems to be common.

Thanks to EXCiD3 and all of you for the energy you put into this. This is what makes for a successful community.

---

### Post by buntunub on 2007-10-08
Wireless via Ndiswrapper works as good or better than in Feisty. However, my Dell 1390 (renamed bcm 4311) would not work out of the box via Restricted Driver Manager. It did download the firmware when I enabled it, but it would not work. To test this I even reinstalled to try it out on a new system and still no Wifi. I am impressed that Gutsy is integrating Wifi with the Restricted Driver Manager utility this time around, and it actually does go out and grab the firmware, or give you the option to install your own. Perhaps the firmware Gutsy grabs from whatever site it goes to is wrong? Maybe it would work if you used your own firmware instead?.. This is possible. However, Ndiswrapper works very well too so long as you blacklist the bcm43xx. No complaints with that as I am getting the full 54mbps out of the card as I type (psst.. A good wifi access point helps out alot too!). Graphics and Displays.. Another story entirely!

---

### Post by jpmontalbo on 2007-10-08
**Model:** Compaq Presario v6420us
**Processor:** AMD X2 Athlon 64 bit 1.7 ghz
**Wireless Card:** broadcom
**Graphics Card:** Nvidia GeForce Go 6150
**Gutsy Tribe (Version):** Gutsy Beta 1
**Boot Parameters: ** kernel version prior to 2.6.22-13, "noapic irqpoll noirqdebug" was required.

**sidenote:** wireless card woks only with ndiswrapper and xp drivers, fw-cutter method does not work.

---

### Post by umberstark on 2007-10-09
Model: HP G5056EA (UK model number, no longer being sold)
Processor: Intel Dual-Core T2080 1.73GHz
Wireless Card: broadcom
Graphics Card: Intel 945GM
Gutsy Tribe (Version): Gutsy Beta, fully up-to-date

Wireless worked no problem using the restricted driver (after doing a "reload" in Synaptic Package Manager)

Still had a problem, as I did with 7.04, with my Intel HDA sound, the speakers wouldn't cut out when I plugged in my headphones. Doing the following resolved it however,

```
sudo apt-get install alsa-base alsa-tools alsa-oss alsa-utils alsa-firmware-loaders
```

then adding the following line to the end of the  */etc/modprobe.d/alsa-base* file,

```
options snd-hda-intel model=laptop
```

1280x800 resolution worked out-of-the-box, without having to use "915resolution".

That's about it so far.

---

### Post by Ian Milligan on 2007-10-10
> I think if the text commands were removed or minimized
Why?  Why dumb down an operating system, simply because the *option* to use a text command confuses you?  Have you not noticed that Ubuntu has been adding graphical interfaces for almost all the command-line functions you are likely to use?  Aptitude, tar, system configuration et cetera can all be done without opening the dreaded terminal!
> the ability to run MS win, and OSX software
Huh?  Its called Windows or OSX software for a reason... because it was built to run in one of those environments!  The only reason a Linux version of a program would not be available would be if the program was closed source, and the developers never even bothered porting it to Linux.  Not much we can do about that now can we?  Asking why Linux doesn't natively support Windows software is like asking why your new diesel truck won't run on hydrogen fuel cells. Of course you can run most windows software in ubuntu using an emulator (or a compatability layer, or whatever you want to call Wine), and I couldn't give a flying crap about OSX software...  Have you ever tried running Linux software in Windows or OSX?
> **ydeardorff said:**
>  the ability to run/install pretty much anything via CD/DVD rom or USB drive, or directly from the intenet this system would leap to the cover of most major magazines and conversations overnight!
I'm sorry, is that not EXACTLY what Aptitude does?  You can find software to do just about anything in the repos, and yes, DVD playback is one of them.
> And I also have the dreaded 345M ATI 3d chipset which didnt help. running ubuntu feisty left me in a 2D world.
If this is a problem for you, you should try buying linux-compatible hardware (I.E. NOT ATI).
> Too bad we cannot open source access to the internet!
umm.....
what?

ok, this is a joke right?  Not only does your post make no sense, it seems as though you just picked a thread at random and posted in it.  If you actually have something to say, try saying it in a **pertinent** thread.  Do you run Gutsy? No.  Do you own an HP or Compaq laptop?  Once again, no.

---

### Post by anoncow on 2007-10-10
**Model:**  Compaq Presario 2500 (Circa late 2003)
**[B]Processor:**[/B] Pent 4 2.8ghz, not HT, 512k cache
**Wireless Card:**  Broadcom BCM4306 b/g
**Graphics Card:  **Radeon IGP 345M

Graphics are a no go. LCD shows garbage (screen spit 90/10 vertically, terrible waves).  I need some assistance -- anyone seen this before or have an idea how to fix it?  Using stock 'ati' Xorg driver, and seen both in a upgrade and with a LiveCD.

-anoncow

---

### Post by EXCiD3 on 2007-10-10
> **anoncow said:**
> **Model:**  Compaq Presario 2500 (Circa late 2003)
**[B]Processor:**[/B] Pent 4 2.8ghz, not HT, 512k cache
**Wireless Card:**  Broadcom BCM4306 b/g
**Graphics Card:  **Radeon IGP 345M

Graphics are a no go. LCD shows garbage (screen spit 90/10 vertically, terrible waves).  I need some assistance -- anyone seen this before or have an idea how to fix it?  Using stock 'ati' Xorg driver, and seen both in a upgrade and with a LiveCD.

-anoncow
I would recommend installing the binary Official ATI drivers from the repositories. This should fix any problems related to the graphics drivers. I'm not an ATI user, but at least that is somewhere to start.

---

### Post by Ian Milligan on 2007-10-10
> **umberstark said:**
> Model: HP G5056EA (UK model number, no longer being sold)
Processor: Intel Dual-Core T2080 1.73GHz
Wireless Card: broadcom
Graphics Card: Intel 945GM
Gutsy Tribe (Version): Gutsy Beta, fully up-to-date

Wireless worked no problem using the restricted driver (after doing a "reload" in Synaptic Package Manager)

Still had a problem, as I did with 7.04, with my Intel HDA sound, the speakers wouldn't cut out when I plugged in my headphones. Doing the following resolved it however,

```
sudo apt-get install alsa-base alsa-tools alsa-oss alsa-utils alsa-firmware-loaders
```

then adding the following line to the end of the  */etc/modprobe.d/alsa-base* file,

```
options snd-hda-intel model=laptop
```

1280x800 resolution worked out-of-the-box, without having to use "915resolution".

That's about it so far.

interesting.  This fixed my headphone jacks as well, even though lspci listed my sound card as nvidia-hda, not intel.  Not sure what's going on here.

---

### Post by JimmyBEng on 2007-10-10
First the specs again:
Model: dv9500t
Processor: Intel Core 2 Duo T7500 (2.2 GHz)
Wireless Card: Intel PRO/wireless 4965 AGN with Bluetooth
Graphics Card: NVIDIA GeForce 8600M GS

In order to get my laptop to boot, I had to disable bluetooth ([see post]("http://ubuntuforums.org/showpost.php?p=3486001&postcount=74")).  I did this by removing the execute permission from the bluetooth script.

```
sudo chmod /etc/init.d/bluetooth -x
```

This had the side effect of making my usb not detect any devices, caused lsusb to hang, etc (anyone know why?).  It will work in the short term, but there is a better way to disable this script at start-up that doesn't have this side effect.

The proper way to disable bluetooth:
--install BootUp-Manager
```
sudo apt-get install bum
```
--start BootUp-Manager (System->Administration->BootUp-Manager)
--check Advanced at bottom of the window
--select the Services tab
--uncheck bluetooth

So now bluetooth is not being started, but that is not a priority for me at the moment.

---

### Post by raeb on 2007-10-11
Model: HP dv6119us
Processor: TurionX2 TL-50
Wireless Card: Broadcomm 43xx variety
Graphics Card: Nvidia geforceGo
Gutsy Tribe (Version): 2.6.22-14 (linux versino)
Boot Parameters: Must include noacpi or system hangs during boot (be it from cd or hd)

Problem free.  Everything works perfect.  Wireless is using the Broadcomm 43xx drivers and WCID (don't like the provided network manager much, wcid also handles encrypted networks better imo).

---

### Post by acfreema on 2007-10-12
Model: dv2617us
Processor: c2d t5250
Wireless Card: intel 3945abg 
Graphics Card:mobile gm965 (x3100)
Gutsy Tribe (Version): x86_64 release candidate?
Boot Parameters: live disc worked fine, but i had to "don't use" the ntfs partitions to install properly (using the 32bit or the 64bit)

my biggest complaint is the package manager: every time i open it, it's "out of date".  every time i click to select an application, same thing.  no matter how many times it updates, nothing works.  i can't apt-get many things, it's very angering.
this is my first experience with a 64bit distro of linux... and i am not happy.  am i better off using the 32bit version?

"good" news, i just tried installing the 32bit version and the package manager works just fine.  i just used apt-get to install a few things... so, perhaps i should stick to the 32bit?

---

### Post by samuraiche on 2007-10-12
model: HP Pavillion dv6000
Processor: inter centrino duo
Wireless intel3945
Graphiccard :Intel GMA 945

Everything works just fine except suspend/hibernate :)

---

### Post by wadpro on 2007-10-14
Model:
 Processor:AMD 1.60 X2
 Wireless Card:Broadcom 4312
 Graphics Card:ATI Xpress X1150
 Gutsy Tribe (Version):7.10 RC

Thx

---

### Post by infra_red_dude on 2007-10-14
> **anoncow said:**
> **Model:**  Compaq Presario 2500 (Circa late 2003)
**[B]Processor:**[/B] Pent 4 2.8ghz, not HT, 512k cache
**Wireless Card:**  Broadcom BCM4306 b/g
**Graphics Card:  **Radeon IGP 345M

Graphics are a no go. LCD shows garbage (screen spit 90/10 vertically, terrible waves).  I need some assistance -- anyone seen this before or have an idea how to fix it?  Using stock 'ati' Xorg driver, and seen both in a upgrade and with a LiveCD.

-anoncow
The newest binary ATI drivers will not work with IGP345M. You will need to used the open source 'radeon' driver.

---

### Post by FrancoNero on 2007-10-14
since a couple weeks and ever since, gutsy can't handle graphics anymore. might be the intel driver or X, i dont know, it just can't handle it anymore. flickering, crashes, wrong screen res, the works... not even recovery mode fixes it anymore. feisty was so beautifully flawless in setting itself up in a way that it at least worked!

---

### Post by EXCiD3 on 2007-10-14
> **FrancoNero said:**
> since a couple weeks and ever since, gutsy can't handle graphics anymore. might be the intel driver or X, i dont know, it just can't handle it anymore. flickering, crashes, wrong screen res, the works... not even recovery mode fixes it anymore. feisty was so beautifully flawless in setting itself up in a way that it at least worked!

Yeah, I agree that feisty is better as of now, but you have to take into account that Gusty isn't finished yet. There are still 4 days till release.

---

### Post by boralyl on 2007-10-14
**Model:**  Compaq Presario F730US
**Processor:**  AMD Athlon&#8482; 64 X2 Dual-Core Mobile Technology TK-55 (1.8GHz) processor
**Wireless Card:**  Broadcom 4311 rev(02)
**Graphics Card:**   Nvidia GeForce Go 6100
**Gusty Version:**  Release Canidate 1

Had to use the Alternate install disc and do the text install, since kdm wouldn't start b/c of the graphics card.  After installing I had to hit esc on boot up to enter the grub menu, hit 'e' to edit the specified kernel, then hit 'e' again to add "noapic irqpoll" to the end.  After this it boot up just fine, although I need to find out how to make those settings stick, b/c I have to input those options on every boot.  I used ndiswrapper with this [guide]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#head-818e0ccb34dc3e6733f798494fb6ce95ea5548c6"), and wireless works fine, didn't test WPA yet, although it's supposed to support it.

**Edit:**  I found where to add those lines after you have booted up /boot/grub/menu.lst  Also this isn't an ideal solution, noapic disables one of the processors.  Looking at [this link on the gentoo forums]("http://forums.gentoo.org/viewtopic-t-598475.html") it may be a graphics driver issue.  Don't have time to look into it now, but will post back when I have fiddled with it.

---

### Post by Corgana on 2007-10-14
I think it should be known that an IGP 320m (mobility u1) graphics card (found in a few of 2-year old presarios) cannot handle dual-monitors in ubuntu (any version) whatsoever.

---

### Post by siodine on 2007-10-15
Model: dv2500t
Processor: Core 2 Duo T7??? (2.0GHz)
Wireless Card: Intel 4965 AGN
Graphics Card: nVidia 8400 G
Gutsy Tribe (Version): RC

Well, I'm able to install gusty fine on my laptop. However, there are some real odd problems with the wireless connection. See here: [http://ubuntuforums.org/showthread.php?t=574379&highlight=dv2500t](http://ubuntuforums.org/showthread.php?t=574379&highlight=dv2500t)

I even have that same problem with Arch linux installed and trying to connect to my router via the CLI. iwlist actually disconnects all the other computers in my house from our wireless router.

---

### Post by leofreyed on 2007-10-15
Model: Pavilion DV2000T
Processor: Core 2 Duo 1.83
Wireless Card: Intel ipw3945
Graphics Card: Nvidia Geforce Go 7200
Gutsy Tribe (Version): RC
Boot Parameters: none.

Well, I did a complete format, but several issues still occur, as when using 7.04.
-Wireless works, but after standby it's quite iffy
-Brightness controls don't work
-After a reboot from Windows there is no sound

I was really hoping these things would be fixed with Gutsy.

---

### Post by 4leite on 2007-10-16
Model: HP compaq 6715b
Processor: AMD Turion 64 X2 TL-64
Wireless Card: BCM4310 UART (rev 02)
Graphics Card: ATI X1250 radeon
Gutsy Tribe (Version): 7.10 RC 64 desktop live
Boot Parameters: (none)

I discovered an easy way to avoid "no screens found error"...

If you have an external screen and wired internet connection on clean install:
Plug it in and press the fn+f4 button at boot splash until the external screen is working and the laptop screen is disabled. This will mean that you can run the live cd and graphical install. After you have booted into the newly installed system, enable the restricted ati driver, disconnect the external screen and on reboot you should have full 3d support out of box. [edit: forgot to mention, xgl 3d, so apt-get xserver-xgl for desktop effects] 

Haven't got hibernation or suspend to work yet.

Sound works (haven't tested recording)

Wireless works with ndiswrapper + bcmw15. Had some funny problems enabling the card - restarting a few times seems to have fixed it.

[edit: still having some problems with wpa, but I don't think they are hardware related]

---

### Post by revenant_org on 2007-10-17
Model: HP Pavilion dv6238eu
Processor: AMD Turion 64 X2 TL-52
Wireless Card: Broadcom 4311 rev(02)
Graphics Card: Nvidia Geforce Go 6150
Gutsy Tribe (Version): 7.10 RC 64 
Boot Parameters: noapic irqpoll noirqdebug

Everything is working fine, usb, wireless and sound. [COLOR="Red"]**But the system is always busy handling hardware *irqs* ** [/COLOR]; htop reports high cpus usage at all the time. :mad:

---

### Post by raeb on 2007-10-17
> **revenant_org said:**
> Model: HP Pavilion dv6238eu
Processor: AMD Turion 64 X2 TL-52
Wireless Card: Broadcom 4311 rev(02)
Graphics Card: Nvidia Geforce Go 6150
Gutsy Tribe (Version): 7.10 RC 64 
Boot Parameters: noapic irqpoll noirqdebug

Everything is working fine, usb, wireless and sound. [COLOR="Red"]**But the system is always busy handling hardware *irqs* ** [/COLOR]; htop reports high cpus usage at all the time. :mad:

Try booting with the kernel options noirq and/or noirqdebug ?

---

### Post by revenant_org on 2007-10-17
> **raeb said:**
> Try booting with the kernel options noirq and/or noirqdebug ?
Nope, none of them was usefull. However, after a few hours of searching, I have found an optimal solution by appending "*acpi_irq_balance*" to boot flags which reduces the load on of one of the CPUs.  :guitar:

---

### Post by cubeist on 2007-10-17
I am not impressed with gutsy, I have been running it since tribe 5 and one day before the release there are too many things that don't feel right... I will stick with feisty for a while..

Model: hp dv9000z (technically the dv9408 but is recognized as the 9000z)
Processor: AMD Athlon X2 TK-53
Wireless Card: BCM Dell Wireless 1390 WLAN Mini-PCI Card (rev 02)
Graphics Card: Nvidia 6150
Gutsy Tribe (Version): RC - 64bit
Boot Parameters: noapic

Up until a couple days ago I still needed to boot with noapic, nolapic, noirqpoll, noapci, and nosmp.  Yes I tried booting without those one by one and they were all needed, now I only have to boot with noapic... but this is still a regression from feisty.  (UPDATE: Oct 22 - still have to boot with noapic)

Here is my list of things that aren't quite right:
- the noapic thing mentioned above

- My internet is dog slow... actually the pages load fast, but every single web page takes at least 15 - 30 seconds to get the dns info... This problem seems to be unique to me and it is very frustrating. (regular dhcp wired ethernet) (UPDATE: Oct 22 - I have tested everything, wired, wireless, ISP, no matter what, dns takes 30 seconds plus per page - feisty is near instant...)
(UPDATE Oct 23 - I disabled IPV6 and Internet runs at normal speed now)

- After every boot the processor runs at full speed for about five minutes, but when I open system monitor (or top) to see what is running... nothing shows up using more than a couple percent... this might just be a quirk in system monitor in the panel... (UPDATE: Oct 22 - I think I solved this - tracker was running for the silly deskbar applet thing, I have shut this off and it seems better)

- Powernowd refuses to load on boot.  I keep adding it to my sessions list and it keeps forgetting to load.  When it is working (manually loaded), it seems that gutsy requires the processor to run at full speed a lot more than feisty. (UPDATE: Oct 22 - I still have to load powernowd manually, and it doesn't run as economically as feisty - ie, the processor runs at full speed more often than half speed as it does in feisty)

- Random boot ups into 640x480.  Very frustrating... I have to boot into recovery mode and restore my old xorg.conf.  Checking the sys log I cannot determine why this happens, I am using the restricted driver.
(UPDATE: Oct 22 - solved.  the new screen & graphics app was messing things up - use nvidia-settings instead... much better)

- compiz works ok but my menu bars still disappear every once in a while and sometimes windows will come up empty (see image)
(UPDATE: Oct 22 - Still not working correctly, perhaps new 0.6.0 will fix things)

- And lastly! gutsy just feels slower... every app takes longer to load... it feels like a single core system but both cores are recognized.
(UPDATE: Oct 22 - it still feels slower, but I think the slow internet dns problem is what is causing my bias)

---

### Post by stinkerweed999 on 2007-10-18
Model: HP Pavillion dv2116wm laptop
Processor: AMD Turion(tm) 64 X2, 1.6GHz
Wireless Card: 01:00.0 Network controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 01)
Graphics Card: 00:05.0 VGA compatible controller: nVidia Corporation C51 [Geforce 6150 Go] (rev a2) (prog-if 00 [VGA])
Gutsy Tribe (Version): ubuntu-7.10-desktop-amd64.iso (fresh out of the oven!)
Boot Parameters: (none)

The native bcm43xx driver in the kernel was unstable and the range of my wifi was bad.

I followed Jukka's howto for installing ndiswrapper on the first page of this thread and had instant success.

I've distilled it down for my notes as follows:

sudo aptitude install ndiswrapper-common
sudo aptitude install ndiswrapper-utils-1.9
sudo modprobe -r bcm43xx
vi /etc/modprobe.d/blacklist   - append "blacklist bcm43xx" to the end
- Get proprietary driver from the HP-site: sp34152.exe
cabextract -a ./sp34152.exe
sudo ndiswrapper -i bcmwl5.inf
sudo ndiswrapper -l
sudo ndiswrapper -m
sudo modprobe ndiswrapper
sudo echo ndiswrapper > /etc/module

---

### Post by buntunub on 2007-10-18
Im on the 2415 and just today got all effects up and running. Stay away from that crap Screens and Graphics Utility they packaged with this version. It WILL cause you no end of grief. Use the nvidia-settings tool for all your needs and youll be fine. Be sure to save xconfigs from that (yes the new Nvidia drivers seem to run pretty nice). I ...............still................ experience many and lots of random lockups for a few seconds at a time. VERY annoying and this bug continues into Gutsy with Compiz running. Dual screens run flawless without Compiz, again with the nvidia-settings tool. Its neat they are trying to include more utility with this version, but its all useless fluff if it creates more problems for people than its worth. My vote is for stability and bug fixes over fluff any day.

---

### Post by Tagallo on 2007-10-19
I have a Compaq V6000 series with Sempron processor, Broadcomm wireless and NVIDIA 6150 graphics.

I tried Hurd 5 and beta with no success to boot...
I thought it would be different with final... 
But I expend the last hours trying to boot the alternate install cd, and it keep hanging.

Now I managed to boot with noapic, nolapic, noirqpoll, noacpi, and nosmp options, and installation was going fine until it stopped at 40% on "Scanning the mirror". I'm a bit dissapointed with Gutsy up to now... because I never had these problems with Feisty.

I tried every combination of these parameters (noapic, nolapic, noirqpoll, noapci, and nosmp), but the only way it goes is with all. I'm not sure what noapic and nolapic disable, but I definitely don't want ACPI disable on my laptop, so if this is the only way to get Gutsy running, probably i will stick to Feisty or change to another distro.

Cheers
Thiago

---

### Post by xcafeus on 2007-10-19
Model: Pavillion dv6520ea
Processor: Core Duo 1.8GHz
Wireless Card: Intel Pro 3945
Graphics Card: Intel 965 (x3100)
Gutsy Tribe (Version): 64bit
Boot Parameters: Vista Home Premium / Ubuntu Gutsy

Sound does not work (seems to be a known bug - can be fixed but not 100%).
Sound Touch Button is always orange color although it seems to mute/unmute the sound system (which doesnt work anyway).
Fingerprint reader does not work.

---

### Post by BjornLunde on 2007-10-19
Compaq Evo N1020v notebook.

Processor: Pentium 4
Wireless: None integrated
Graphics card: ATI IGP 340M
Gutsy Gibbon 7.10 Final

Upgraded from 7.04 using upgrade manager. Most things work. Slight graphics problem, which wasn't present with 7.04, where black or white lines seem to linger after a window is opened or closed. Not really more than a slight annoyance. No serious hardware issues.

3d acceleration is not working at all, while there was some erratic 3d functionality in 7.04 with compiz although not stable. 3d acceleration should, according to some sources, be possible for this chipset using the radeon drivers and some tweaking (see [http://www.free3d.org/](http://www.free3d.org/) for details and compatibility list). Haven't gotten it to work so far.

Volume buttons are the only one proprietary buttons that seem to work. Not a really big issue.

For wireless connectivity I use a 3Com Wireless USB plug (3CRUSB10075) which worked out of the box with WPA support and proper 54 Mbps connection speed (would only run at 11Mbps in 7.04).

Be aware that the Texas instruments Cardbus controller used in this laptop will refuse to work with some wireless PCMCIA cards (e.g. the 3Com Officeconnect 3CRG10075 Wireless PC Card). This is a hardware/firmware issue and has nothing to do with the OS.

To sum it up then, its only the 3D acceleration that you'll be missing out on. On such an old laptop, this is hardly a decisive issue if considering an install / upgrade.

Update: I have also encountered the following issues on the Evo N1020n:

Resume from suspend does not seem to work at all. Not a major issue for me because I never use it anyway.

Hibernate does seems to work, but there is a delay in shutting down the USB ports. It will power down after a while, but only after repeated PM status messages. Resume from hibernate works, but the display is corrupted until login. After that the display is ok, but the USB ports seems not to function. If you are using a USB wireless adapter (like me), this is an obvious drawback. Again, this is not a big issue for me, because I do not use hibernate either, but I guess this will be an annoying problem for some users.
The Wireless Manager reports connection state as "Connected" and the connection strength the device had when hibernate was initiated (even if you physically unplug the plug from the USB port), and plugging / unplugging the device does not resolve the issue.

For me, at least, a full reboot is needed to get my wireless USB plug to work.

Good luck,

Bjorn

---

### Post by stinkerweed999 on 2007-10-19
Must add also that since going with ndiswrapper my bandwidth has jumped.  When I was able to connect with the native driver I got 0.9MB/sec max, with ndiswrapper I get 2.6MB/sec at 20 feet from wrt54gl router in both cases.

Latency is very much improved.  Native bcm43xx driver tooks multiple seconds to connect with the router (or whatever it was doing) on web page or ssh hits.  Ndiswrapper feels like ethernet latency.

---

### Post by sixstorm on 2007-10-19
I just bought the Compaq C714NR laptop that is on sale at Best Buy this week.  I actually sold my two Macs for it plus to put some money back for the future marriage.  

Processor:  Intel Dual Core T2310 @ 1.43GHz
RAM:  1GB PC5300 DDR2
Graphics:  Intel X1300 Integrated Graphics
Hard Drive Space:  Hitachi 120GB
Wireless:  Broadcom (Not exactly sure what model)

So I just installed 7.10 x64 Final and of course, the original wireless drivers don't work.  I don't have a place to plug my laptop into the network physically so I'll have to wait in order to get that working.  

How does Compiz-Fusion do on the Intel X1300?  Also, how is battery life?

---

### Post by erniequintero on 2007-10-19
i have a compaq presario V3000(V3218la), i download the Gutsy 7.10 RC on monday it install fine on my desktop, and boots right away from a dell laptop at work. but when i try to boot from that cd on the ubuntu splash with the progress bar moving it locksup randomly. i also try with the options for noapic irqpoll noirqdebug but still the same thing. also download the alternate cd and locks up when is trying to load the modules from the cd to start the setup right away you select the keyboard layout. then i have a feisty disc that i recieve from shipit page and thats boot fine and install right away, then i try to perform the upgrade but that gives me errors. any body can help me out thanks.

System specs:
---------------------------------------------------------------------------------------------------------
Microprocessor 2.0 GHz AMD Turion™ 64 Mobile Technology MK-36
Memory 512MB 667MHz DDR2
Video Graphics NVIDIA GeForce Go 6150
Hard Drive 120GB 5400RPM
Multimedia Drive SuperMulti 8X DVD±R/RW with Double Layer Support
Display 14.1” WXGA High-Definition HP BrightView Widescreen Display (1280 x 800)
Fax/Modem High speed 56K modem
Network Card Integrated 10/100BASE-T Ethernet LAN (RJ-45 connector)
Wireless Connectivity 802.11b/g WLAN
1 ExpressCard/54 Slot (also supports ExpressCard/34)

---

### Post by cwbar_1 on 2007-10-19
Model: HP Pavilion dv6449us
Processor: AMD Turion (tm) 64 X2 Mobile Technology TL-56 1.8  GHz
Wireless Card:Broadcom4328 802.11a/b/g/n
Graphics Card:Nvidia Geforce 6150 GO
Gusty Gibbon Oct. 2007 release
boot parameters: noaoic irqpoll noirqdebug (to use live cd and install, I don't know if they are used after installation of Nvidia restricted driver)

Used the above boot parameters to get into live CD.
Installation went uneventful.
Used the following to get wireless going.
1. Copied bcmwl5.inf from downloaded HP XP driver to "home directory"
2. Installed w/ndiswrapper instructions the following found on this forum.  (thanks!)
	sudo ndiswrapper -i /home/my_name/bcmwl5.inf

	ndiswrapper -l

	sudo depmod -a

	sudo modprobe ndiswrapper

	sudo cp /etc/network/interfaces /etc/network/interfaces.orig

	echo -e 'auto lo\niface lo inet loopback\n' | sudo tee /etc/network/interfaces

	sudo ndiswrapper -m

	echo 'ndiswrapper' | sudo tee -a /etc/modules

	echo 'ENABLED=0' | sudo tee -a /etc/default/wpasupplicant
Still looking into xD-Picture card reader and Sonix USB 2 web cam.
Dual booting w/Vista ****Not for Long****
Thanks to the talents of the posters on this site.

---

### Post by millfarm on 2007-10-20
Model: HP Compaq nc6400
Processor: Intel Centrino Core 2 Duo T7200 @ 2GHz
Wireless Card: PRO/Wireless 3945ABG Network Connection
Graphics Card: Mobility Radeon X1300
Gutsy Tribe (Version): 7.10
Boot Parameters:?

I'm having 3 problems right out of the box.

1. Wireless network
Finding the active networks properly, but unable to conneting - even when removing all encryption.

2. Appearance preferences
Unable to enable the visual effects, "The Composite extension is not available" (the "ok" button for this alert isn't working)

3. Dual monitor
Attempting to run with one desktop on dual monitors, I have 2 setups that the laptop must work with. One with a 19" LDC in 1280x1024 + laptop 1440x900. And one with a 22" LCD in 1680x1050(?) and the laptop in 1440x900. And I'm trying to make them run as one shared desktop (external screen on the left), And this works fine if both use laptops resolution, and works well in full resolution if I use dual-head.


This is beginning to annoy me quite a bit..

---

### Post by millfarm on 2007-10-20
My 2. problem with the composite extension was resolved by following this: [http://ubuntuforums.org/showthread.php?t=576624](http://ubuntuforums.org/showthread.php?t=576624)

But now I can't get my external monitor to work.. :(

---

### Post by renim on 2007-10-20
**Model**: Compaq Presario V3000Z (V3019US)
**Processor**: AMD Turion 64 X2 TL 50 @ 1.6GHz[B]
Wireless Card[/B]: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 01)[B]
Graphics Card[/B]: Nvidia Geforce Go 6150[B]
Gutsy (Version)[/B]: 7.10 32bit.

The installation with the Live CD went fine. No need for any special boot settings. The Broadcom and the Nvidia drivers installed properly after I enabled the correct sources in the admin panel. The HP provided Broadcom driver for my wifi card didnt work but the download option works fine. The wireless is stable and works with WPA.

The only issue was the sound, it seems to be temperamental. Works on random reboots. Maybe recompiling alsa might work. If anyone has suggestion on how to fix this or come across a similar situation pls let me know.

Overall, Gutsy seems to be OK but will have to use it for a while and see how it goes.

---

### Post by seanfred on 2007-10-21
Model: Compaq Presario F730US
Processor: AMD Athlon 64 X2 TK-55 (1.8GHz) processor
Wireless Card: Broadcom 4311 rev 02; also shows up as Dell 1390
Graphics Card: Nvidia 6100
Gusty Version: 7.10 64-bit

i added "noapic irqpoll irqdebug" to boot the system from the cd, then i added it to grub to get into the system once loaded and once i booted up the first time i made those changes permanent in /boot/grub/menu.lst. i used ndiswrapper with the guide for Broadcom cards on these forums and wireless works great. my biggest thing was being able to use a windows based baseball sim for my online league to export my lineups, but WINE worked great for that purpose and I am glad to report that i am Vista free!

---

### Post by Dimitrov on 2007-10-21
Model: HP-Compaq nx9010
Processor: Intel Pentium4 2,66Ghz
Wireless Card: -not integrated-
Graphics Card: ATi IGP 345M
Gutsy (Version): 7.10 32bit.

I installed the 7.04 earlier, it works good.But the new 7.10 don't, because the VGA driver is not too good...every second horizontal pixel-line shake left-right-left-right on the screen, and i see a dark verical line on the right side of the screen.So i cant try the other hardwares...

---

### Post by gerat on 2007-10-21
After updating to 7.10 from 7.04, there is no sound. Sound card is Intel ICH3 82801CA AC'97.
With 7.04 it was working great just after installing the OS (no configuration needed).
Don't know how to solve this problem. 

Compaq 2710EU. P-3 1.13 GHZ, 256MB, 20GB HD.

---

### Post by Thanawho on 2007-10-21
Laptop: HP dv6500 
Sound: HDA Intel
ALSA Version: 1.0.14

I'm having a similar sound problem with my HP laptop. The sound in gnome is not muted and ALSA shows that it is not muted in the terminal. HP Quickplay button is orange, signifying "off", but displays proper functions when pressed(but it remains orange). Sound works on my windows partition. The quickplay sound button is blue (on) when first booting Ubuntu but turns to orange(off) after Ubuntu is finished loading. It's almost like Ubuntu thinks that it is turning the sound on while it is actually turning it off. 

Another parallel: A friend with a similar HP dv65xx laptop installed ubuntu with his sound on and got sound. I installed ubuntu with my sound off and got no sound. I'm not sure how to attack this problem, since my sound card is definitely recognized by Ubuntu.

---

### Post by skinnie on 2007-10-21
> **Thanawho said:**
> Laptop: HP dv6500 
Sound: HDA Intel
ALSA Version: 1.0.14

I'm having a similar sound problem with my HP laptop. The sound in gnome is not muted and ALSA shows that it is not muted in the terminal. HP Quickplay button is orange, signifying "off", but displays proper functions when pressed(but it remains orange). Sound works on my windows partition. The quickplay sound button is blue (on) when first booting Ubuntu but turns to orange(off) after Ubuntu is finished loading. It's almost like Ubuntu thinks that it is turning the sound on while it is actually turning it off. 

Another parallel: A friend with a similar HP dv65xx laptop installed ubuntu with his sound on and got sound. I installed ubuntu with my sound off and got no sound. I'm not sure how to attack this problem, since my sound card is definitely recognized by Ubuntu.

You have to compile and install alsa 1.0.15rc3..search in the forum for realtek 268 alsa

---

### Post by DRAGONPOWER on 2007-10-21
I fixed audio with the newest ALSA drivers: version 1.0.15. [Here's]("http://ubuntuforums.org/showthread.php?t=583150") how I did it for HP dv9500.

---

### Post by Mimsy on 2007-10-21
I am posting this confirm the below report. I installed Gutsy on the nc6220, by installing from the Feisty live CD and then I used the Upgrade button in the update manager. I was not able to test everything below (no USB mouse available, for example), but I saw enough similarities that I feel safe in assuming that what worked for popch would work for me as well.

Two exceptions:

1. The blue LED in the WLAN on/off key works just fine.

2. Although the WLAN adapter clearly works perfectly, and lets me configure my wireless setup fine, it cannot actually connect. Judging by other posts in this thread, that's a common problem.

Actually, make that three:

3. The SD-card reader does not work out of the box. Booting with card in reader or inserting card later makes no difference, it is not recognized. Typing lspci into a terminal shows the reader listed with all the other components, however, it won't open an SD card.

> **popch said:**
> Model: hp Compaq nc6220
Processor: Intel(R) Pentium(R) M processor 1.86GHz
Wireless Card: PRO/Wireless 2200BG Network Connection (product ID 16928 (0x4220))
Graphics Card: Mobile 915GM/GMS/910GML Express Graphics Controller (product ID 9618 (0x2592))
Gutsy Tribe (Version):5, I believe. Where do I find that if I forgot to write it down?

Those things work out of the box:
[LIST]
[*]Configuring WLAN with 128 bix hex WEP key with the control panel applet
[*]WLAN on/off hardware key (but apparently not the LED in the key)
[*]SPR on/off key with LED, volume up/down keys
[*]Headphone plug recognition (when activated in control panel)
[*]Info key (brings up help)
[*]fn+F8 (battery state key)
[*]fn+f9..f11 brightness 1/-, contrast
[*]Lid closed key
[*]Num Lock (with LED); embedded numeric keys
[*]Swiss keyboard (partially tested, seems OK)
[*]Touchpad
[*]USB mouse
[*]Menu key
[/LIST]

The following does not work (and lost me all data entered above when I tried before)
[LIST]
[*]fn+f3 (that's the blue moon or crescent which hibernates the machine). It
hibernates OK but does not appear to wake up again. This works fine in Feisty Fawn.[/LIST]

I've run out of things to test. All but hibernate appears to work just fine, out of the box, with no fiddling at all. 

Sorry, forgot to post that I have not installed Gutsy on my laptop as it is my only PC at home. I run it off the live CD.

:)

---

### Post by terrrorr on 2007-10-21
Model: HP Compaq NX7300
Processor: Intel Centrino Core 2 Duo T5600
Wireless Card: PRO/Wireless 3945ABG Network Connection
Ubuntu Gutsy Gibbon

Ok.... my problem:

1. When i use capitalized letters in my accespoints SSID (ESSID) it cannot find my wireless network. Solved this problem by using lower case letters in SSID

2. After reboot wireless network settings try to make the connection with WEP-settings. For some reason it returns all wireless setting back to WEP

I hope you find something which will fix these problems.


- Terrrorr -

---

### Post by Oatworm on 2007-10-21
Model:  HP Compaq Presario V6000Z
Processor:  AMD Sempron 3500+ 
Wireless Card:  Broadcom 1390 WLAN
Graphics Card:  NVidia GForce 6150 Go
Gutsy Tribe (Version):  Non-beta 32-bit (7.10)
Boot Parameters: (Only if extra boot options are needed in order to boot):  Removed "quiet" and "splash" for debugging purposes, kept "noapic irqpoll noirqdebug" from the previous installation

Did an update from a working Feisty installation.  Rebooted - system would not boot.  Tried "recovery mode" - system seems to hang on a DMA check.  Removed "quiet" and "splash" on the main version from GRUB's menu.lst, discovered the main version was freezing there most of the time as well.  Did have an option to boot from the previous kernel - that worked, though some things were a little buggy due to Gutsy trying to point at the new kernel.  Visited the forums, decided I'll come back to it later.

What worked:
Default kernel (2.6.22 series, if I remember correctly):  Nothing.
Old kernel:  Most everything, though the screensaver would crash Gnome for no apparent reason.  I use the restricted nvidia-glx driver

Is it my imagination, or are HP laptops are little more fussy when it comes to Ubuntu?

---

### Post by Jive Turkey on 2007-10-22
Model: zv5469us
Processor: Athlon64 3200+
Wireless Card: bcm4306
Graphics Card: nvidia geforce 440
Gutsy Tribe (Version): final release

I got fed up with very slow winXP performance and decided to try 64-bit ubuntu agian.  My hopes for better support on the wireless card were fulfilled with gutsy.  I formatted the whole hd except for a small partition with some backup files on it and I'm not looking back.

I havent tried writing with the DVD burner yet, nor have I tried the SD card reader.  The bluetooth hardware isn't recognised at all, but I never use it anyway.

I'm very satisfied

---

### Post by EXCiD3 on 2007-10-22
> **Oatworm said:**
> Is it my imagination, or are HP laptops are little more fussy when it comes to Ubuntu?

HP laptops are very picky when it comes to linux. Luckily for us most of the problems have been sorted out, however with the release of Gutsy many more problems have been found. My dv9000T has had a bunch of problems that did not exist in Feisty. Until Gutsy gets fixes for these problems I would recommend HP users to use Feisty. Gutsy seems to lack a lot of continued support for HP's hardware. Obviously this release has been geared towards Dell users as HP has had great support in Feisty.

---

### Post by edemark on 2007-10-22
[B]Model: Hp Compaq nx9010
Processor: Intel p4 3.06
Wireless Card:Trendnet TEW-226PC (pcmcia)
Graphics Card: ati radeon igp 345m
Gutsy Tribe (Version): 7.10 release
Boot Parameters: [/B](Only if extra boot options are needed in order to boot)

How things are working out on this new release? Well I would say terribly as since Gutsy i have lost dri and thus compiz and also the ability to play tuxracer etc. If someone had any good idea how to get dri back waorking than please HELP!!!

Thanks in advance

---

### Post by rhricik447 on 2007-10-22
Jukka - I was having a problem that even after following your directions, I was still getting bcm43xx listed as the alternate driver for ndiswrapper.  The solution is to remember to **turn off the Broadcom restricted driver** before starting.  Once I did that and rebooted, I now have 54G, WEP enabled wireless on a:
HP Pavilion dv6451us
AMD Turion X2 64bit
Broadcom 4312 rev 2 miniPCI HP card
2 Gb RAM
160 Gb SATA drive
Bluetooth working

Thanks a million for the post - I've been fighting with this through 3 different distros (Fedora 6 & 7, Ubuntu 7.04) without success.

---

### Post by calebhoward on 2007-10-22
> If you have tried installing Gutsy Gibbon on an HP or Compaq laptop,
> please post feedback on your experience.

Generally good.  Just no audio/perpetually amber mute button


Please post the following things:
Model:  HP dv9653cl
Processor: Pentium
Wireless Card:Intel PRO/Wireless 4965AGN
Graphics Card:NVIDIA GeForce 8600M GS 
Gutsy Tribe (Version): 7.10 release
Boot Parameters: (Only if extra boot options are needed in order to boot)

I installed with ubuntu alternative disk, and upgraded to kubuntu.  kubuntu install failed.

and a detailed description of anything you think is relevant to running Gutsy on HP/Compaq laptops. Once Gutsy is released I plan on creating a Howto which possibly covers most (hopefully almost all) of the hardware in the various HP and Compaq laptops, this way there would be one central location for information regarding compatibility with this hardware and Gutsy Gibbon.

I had a tough time getting audio to work under Feisty Fawn, but managed.  wifi didn't work under Feisty, so I upgraded to Gutsy as soon as it released.  Now wifi works, but I can't get the audio to play.  I upgraded to alsa 1.0.15 - no dice.  The mute button/light is always amber, but touching it or the volume touch slider overlays control info as appropriate.  It really just seems like it's muted.  drivers are functioning, and the card is recognized.

I want audio, but apart from that, gutsy gibbon is an improvrmrnt from feisty fawn, as far as I can tell.

I'll be grateful for audio help!!!

-caleb

---

### Post by nsegative on 2007-10-22
I installed 7.10, turned it on. No wireless, and the orange does not turn blue if I switch it back and forth. I have DV6000T

---

### Post by frank_costanza on 2007-10-23
Compaq Presario V3000 - Gutsy works much better out-of-the-box than Feisty

Model:V3018CL
Processor:AMD Turion 64x2 1.6GHz
Wireless Card: broadcomm 9431 ???
Graphics Card: nVidia GeForce 6150
Gutsy Tribe (Version): release version

I've had a good experience so far with Gutsy. Sound works, Video works (w/restricted drivers and Compiz Fusion). Touch buttons for volume control work. Wireless seems to be working after installing the drivers using the Restricted Drivers GUI. I don't actually use wireless since I'm plugged in at my desk. So I'm not sure if wireless is totally working, But I was at least able to see available networks.

Things not tested: internal microphone (didn't work in Feisty), CD/DVD writing (worked in Feisty).

All things considered, Gutsy is a very solid release and I would recommend it to anyone with a Compaq V3000.

---

### Post by ra300z on 2007-10-23
These are the problems I've experienced with Gutsy on my DV2000:

(1)  The laptop runs very hot.  The estimated battery time is 1h40m compared with 2h40m on Feisty.
(2)  The GUI sometimes locks up, but does come back after about 5 seconds.
(3)  The title bar at the top sometimes disappears.

Everything works great on Feisty once you get the wireless working using ndiswrapper.  The only thing about Feisty is that once you've run Windows Vista, when you go back into Ubuntu, you don't get any sound (solution:  unplug and remove battery for 5 seconds, then boot back into Feisty, sound will start working again)

---

### Post by c_c on 2007-10-23
Hi,

   I have a Compaq F730US and am running Ubuntu Gutsy 64 bit with the restricted Nvidia driver.

Configuration
AMD Dual core TK 55 64 bit
Nvidia GeForce 6100
Broadcom Wireless 94311 - works with ndiswrapper
Nvidia MCP 51 / C51

        Was able to install Gutsy only with 'noapic'. Otherwise the machine would lock up at 'Loading Drivers' - seemingly just before the audio system makes a click sound with the 'noapic' flag.
 in. 
       Have tried editing the DSDT. There are no errors in the table and only one warning related to _WAK (which seems to pretty common across manufacturers). Found a table that lists the following options in the DSDT 
  Linux, Windows 2001, Windows 2001 SP1, Windows 2001 SP2, Windows 2006.

      This could indicate attempts by Compaq to make this BIOS compatible with Linux, XP and Vista.

      Tried to boot using acpi_os-name = "Linux". Seemed to have improved performance - and the system booted into Gnome without the noapic option. However scrolling down in the device manager caused a hang with the speaker emitting a continuous beep.
 
      Am currently using noapic and acpi_os_name="Linux". Just about everything seems to work - including the fn+www, fn+?, fn+brightness and sound control, fn+sound control - stop, play, fwd and rev keys. 

     There is a problem though - the USB ports seem to stop working all of a sudden and need a reboot to start again. 

     In addition - I notice a 'nvidia: module license 'NVIDIA' taints kernel' message. Probably that is the cause of my usb problems. Will investigate the matter further and post results.

     Is anybody else facing USB problems with similar laptops?

---

### Post by slafko on 2007-10-23
> **c_c said:**
> 

     There is a problem though - the USB ports seem to stop working all of a sudden and need a reboot to start again. 

     In addition - I notice a 'nvidia: module license 'NVIDIA' taints kernel' message. Probably that is the cause of my usb problems. Will investigate the matter further and post results.

     Is anybody else facing USB problems with similar laptops?

I'm also having USB problem with my HP Pavillion dv6000. I don't know how to fix this.

---

### Post by #Reistlehr- on 2007-10-23
Stats are in the sig.


Have to boot with noapic. First i did an upgrade, then i reinstalled so i can document what worked and what didnt.

--**Upgrade:**--
Everything but Suspend/Hibernate and WebCam worked out of the box. 

--**Clean Install:**--
Only problems i had was the install killed my SLAX install. I got the wireless working in 5 minutes. Sound worked, All the functions but suspend and hibernate worked.

--**In General**--
It's nice because i can COMPLETELEY turn off the backlight now, to save battery life. I've been using this as a remedy for no suspend right now, although everything is still on. Media card reader works fine. Boots faster. Wireless loads on boot wih ndiswrapper, no keyring manager, finally. Compiz runs amazing. 

The only problem is, and i posted a thread about it, other than the whole no suspend/sleep/hibernate, is that there is a 30~ second delay from when you enter your credentials, to when a  desktop or wallpaper/gui is displayed. I don't know why this lag. You have a mouse though. It's annoying, but atleast it works!

---

### Post by stickx911 on 2007-10-23
Model:  DV2000 CTO
Processor: Core 2 solo 1.3ghz
Wireless Card: ipw3945
Graphics Card: intel
Gutsy Tribe (Version):final
Boot Parameters: n/a

I went through the upgrade (which was nice btw)

Problem: When I mute, fiesty used to recognize the media button color change when muted, but GG does not. (from blue to orange when muted if you know what I am talking about).

Other items:
This is the first version and distro in general that recognized my bluetooth and ipw3945 (usually is just one or the other). That is nice
 
GG also goes not maintain mute when rebooting. This can be annoying if I have to reboot in the middle of class and the gtk noise blares over everything. This was an easy fix (just turn off the gtk sound), but I didn't want to have to remove it.

I miss the desktops on a cube effect. was this just removed on this release or is it just me?

---

### Post by trarman on 2007-10-23
Model: DV9408ca
Processor: AMD X2 Turion
Wireless Card: Broadcom 43xx
Graphics Card: NVidia Go 6150
Gutsy Tribe (Version):final
Boot Parameters: noapic

I tried the upgrade, but had trouble even getting it to boot.  So tried a fresh install. Using "noapic" boot parameter seemed to be sufficient to get everything running.

Problems:  
 - Wireless "looks" like it's working, but doesn't actually connect to anything, and when I try to configure it my network icon vanishes (seg fault?).  Looks like I'll have to resort to the NDIS driver I used in feisty
 - Performance seems to have taken a huge hit.  Even with desktop effects turned off, something as simple as opening a terminal window takes too long (about 7 seconds)
 - VMWare guest OS pegs itself at 100% CPU doing routine stuff like Explorer, Svchost, etc.  (This is not the cause of the performance issue above, since VMWare wasn't even installed yet).  This is using the same Virtual Machine as was well behaved in Feisty.
 - Accessing the webcam hangs the process trying to access it

Overall I'm pleased with the features and compatibility.  I just wish I knew what was slowing it down.  It seems like everything is starving for CPU.

---

### Post by bogdanmarian on 2007-10-23
> **c_c said:**
> 
     In addition - I notice a 'nvidia: module license 'NVIDIA' taints kernel' message. Probably that is the cause of my usb problems. Will investigate the matter further and post results.


this is because nvidia leverages their driver code base across multiple platforms and industry secret intellectual property yada yada... basically the source of the driver is not public therefore can not be supported by kernel developers. so the driver ships as a binary and only the shim code is available. luckily the driver usually works rather well ;) 

i would guess your usb issue is unrelated. just picked up a F730US and haven't plugged any usb devices in yet

---

### Post by crazytigger on 2007-10-23
Model:Compaq Evo N1015v
Processor: Athlon 1500xp
Wireless Card: None
Graphics Card:ATI Mobilty U1 IGP 320m
Gutsy Tribe (Version):7.10

Clean upgrade from 7.04 to 7.10 (standard ubuntu with nothing installed and all previous upgrades done first)

Second monitor (external) doesnt function, when attempting to use the gui to enable it you end up going round in circles, always in low resolution modes.

Because my LCD monitor is physically broken i am unable to use X at all because external monitor goes to sleep as soon as X is started.

---

### Post by EXCiD3 on 2007-10-23
> **crazytigger said:**
> Second monitor (external) doesnt function, when attempting to use the gui to enable it you end up going round in circles, always in low resolution modes.

I have been having the exact same problem. The Nvidia driver does not properly run when an external monitor is available. I hope this gets fixed soon.

---

### Post by nbayiha on 2007-10-23
**Mode**: pavilion dv6040us
**Processo**r: AMD2 turion64 1.6ghz
**Wireless Card**: broadcom 43XXX
**Graphics Card**:Nvidia Geforce 7200
**Gutsy Tribe (Version)**: 7.10
**Boot Parameters**: none.

The is a bug with the nvidia driver the make gutsy freezing for minutes and sometines the only solution is to restart.

---

### Post by romana on 2007-10-23
Model: Compaq nc4000
Processor: Intel Pentium M 1.6ghz
Wireless Card: Atheros Communications, Inc. AR5212/AR5213
Graphics Card: ATI Radeon IGP 350M
Gutsy Tribe (Version): 7.10
Boot Parameters: none.

Restricted Drivers have taken care of wireless - works flawlessly since Tribe 3, when I first installed Gutsy.

No suspend/hibernate:( Would LOVE that.

The video drivers are the nightmare - there is a reall issue with fglrx drivers with the 2.6.22 kernel - the ati work fine, but forget Compiz/3D rendering. Bother. (Actually, all I want is for Neverwinter Nights to run better than wading through treacle level).

---

### Post by Loffe_ on 2007-10-24
**Model:** HP 6510b
**Processor:** Intel Core 2 Duo CPU  T7100  @ 1.80GHz
**Wireless Card:** PRO/Wireless 3945ABG Network Connection
**Graphics Card:** intel GM965/ X3100
**Gutsy Tribe (Version):** Final Release

Desktop effects is not available unless a fix at [http://linux.dell.com/wiki/index.php/Ubuntu_7.10/Issues/Compiz_Fusion_965GM_Incompatibility](http://linux.dell.com/wiki/index.php/Ubuntu_7.10/Issues/Compiz_Fusion_965GM_Incompatibility)

With the fix video playback will not work. It logs me out when trying to play video.
Google Earth is not working good. It flickers on the screen.

---

### Post by zoogTHOMzoog on 2007-10-24
**Model:** HP Pavillion zv6000
**Processor:** AMD Sempron 3200+ 
**Wireless Card:** Broadcom 4318
**Graphics Card:** ATI Radeon 200M
**Gutsy Tribe** (Version): Final Release 64 bit version

I have everything working... my wireless worked fine with the use of the restricted bcm43xx driver and netapplet (sudo apt-get netapplet). CompizFusion works fine with an xgl session (sudo apt-get xserver-xgl). 

**BUT** it takes approximately 3 minutes to load (i.e. from the grub menu to the gdm menu). So if anyone knows how to fix this, please let me know!

Thanks, 
Thom

---

### Post by zoogTHOMzoog on 2007-10-24
**UPDATE:**

I fixed (well hacked really) the problem with the insane boot time. I just removed the splash option from my grub list (i.e.I deleted "splash" from /boot/grub/menu.lst from the default kernel [Ubuntu 7.10] so that it ends with "ro").

So, if someone who knows a lot about splashes and why this is halting the system let me know.

Thanks,
Thom

---

### Post by #Reistlehr- on 2007-10-24
> **zoogTHOMzoog said:**
> **UPDATE:**

I fixed (well hacked really) the problem with the insane boot time. I just removed the splash option from my grub list (i.e.I deleted "splash" from /boot/grub/menu.lst from the default kernel [Ubuntu 7.10] so that it ends with "ro").

So, if someone who knows a lot about splashes and why this is halting the system let me know.

Thanks,
Thom
Theres an option in i think /etc/usplash.conf for the resolution. It's bigger than your screen, so set the values to 1024 and 768 respectivly.

---

### Post by animaniacs on 2007-10-24
Model: HP Compaq nx9010
Processor: Pentium IV 2,80 GHz
Wireless Card: -not integrated- PCMCIA : MSI PC54G2 (chip: ralink rt2500)
Graphics Card: Radeon IGP 345M (RS200)
Gutsy Tribe (Version): Ubuntu 7.10 Gutsy Gibbon (32bit Alternate CD install)
Boot Parameters: -

I'm using the earlier Feisty 7.04 since it has come out and never have trouble.
Since I had install the 7.10, X.org server shakes pixel left-right-left-right and it's impossible to read the screen.

One solution (partial) is to use the vesa driver, so we can't use hardware acceleration.

The bug seems to be reports here :
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/155954](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/155954)

Animaniacs
;o)

> **Dimitrov said:**
> Model: HP-Compaq nx9010
Processor: Intel Pentium4 2,66Ghz
Wireless Card: -not integrated-
Graphics Card: ATi IGP 345M
Gutsy (Version): 7.10 32bit.

I installed the 7.04 earlier, it works good.But the new 7.10 don't, because the VGA driver is not too good...every second horizontal pixel-line shake left-right-left-right on the screen, and i see a dark verical line on the right side of the screen.So i cant try the other hardwares...

---

### Post by #Reistlehr- on 2007-10-24
Ani.. you should try the new ATI drivers taht came out yesturday

---

### Post by flightless bird on 2007-10-24
I have a clean install of gutsy on an HP G5056EA. The restricted drivers were installed fine, and wireless works, as do the function keys. There have been one or two minor hitches though:

- The speakers do not mute when headphones are plugged in - there is no option for audio jack sense in volume control.
- I had to recompile alsa to get any sound at all. 
- While Gnome is able to deal with the wireless fine, KDE recognises that I have wireless, but is unable to use it to connect, unless I connect in Gnome and then switch session (not a big deal, as I only wanted to give KDE a try, and prefer Gnome anyway).

---

### Post by flightless bird on 2007-10-24
You can enable desktops on a cube by installing the compiz manager and choosing 'custom' in preferences->appearance->desktop effects.

---

### Post by EXCiD3 on 2007-10-24
> **flightless bird said:**
> You can enable desktops on a cube by installing the compiz manager and choosing 'custom' in preferences->appearance->desktop effects.

Technically no. If you use the Extra Effects option you get the cube. If you want to customize Compiz in any way you DO need to install compiz manager, which can be found in the repositories. Search Synaptic for Compiz and install the packages there. Other extras should be in there too. :D

Compiz > Aero - I dont care what Windows users say, nothing beats Compiz.

---

### Post by edemark on 2007-10-24
> **#Reistlehr- said:**
> Ani.. you should try the new ATI drivers taht came out yesturday

Hi i have the same card as ani but as far as i am concerned fglrx does not support this card (i have always used open ati/radeon driver that comes with xorg) or something have changed and the new driver has better backward compatibility?

---

### Post by buntunub on 2007-10-24
> **EXCiD3 said:**
> Technically no. If you use the Extra Effects option you get the cube. If you want to customize Compiz in any way you DO need to install compiz manager, which can be found in the repositories. Search Synaptic for Compiz and install the packages there. Other extras should be in there too. :D

Compiz > Aero - I dont care what Windows users say, nothing beats Compiz.

Actually, if you just choose Extra, because Ubuntu has Compiz set to "Desktop Plane", you will NOT get the cube. All you will get is wobbly windows for the most part. If you want the spinning cube, you must add ccsm and enable Cube and rotate, and disable Desktop Plane.

Edit.. Forgot too that you will have to change your workspaces to 4 also, since Ubuntu defaults to 2.

---

### Post by EXCiD3 on 2007-10-24
Oh right! I think it was the beta that had the cube. My bad. I haven't spent much time playing with Gutsy stable as it cant run my dual monitors nor get my nvidia driver working correctly....Back to Kubuntu Feisty for me :D

---

### Post by mk04 on 2007-10-24
**Model:** HP ze5375us
**Processor:** Pentium 4 mPGA 478 socket @ 2.4GHz
**Wireless Card:** Netgear WG511 v1
**Graphics Card:** ATI Radeon IGP 345M
**Gutsy Tribe (Version):** Final Release, Ubuntu

I had no problems with the graphics card. Everything basically worked out of the box. Wireless was a bit of an issue.

---

### Post by nooken on 2007-10-24
HP Compaq 6510b
Core 2 Duo T7100
2GB RAM
Intel X3100

Most works out of box, havent tried wifi yet though. And compiz needs to be run with checks off to work. Otherwise its all good!

---

### Post by buntunub on 2007-10-24
> **EXCiD3 said:**
> Oh right! I think it was the beta that had the cube. My bad. I haven't spent much time playing with Gutsy stable as it cant run my dual monitors nor get my nvidia driver working correctly....Back to Kubuntu Feisty for me :D

Not so fast dude! Ill tell you how to get it all working.

1. DO NOT USE Screens and Graphics Utility. If you have, your xorg.conf is now a total disaster.

2. Use the nvidia-settings utility. If you dont have it, get it.

3. DO NOT use Xinerama with Gutsy. Ensure you have this option disabled.

4. Setup dual screens via nvidia-settings utility as either Twinview, or dual X screens. Reboot. Yes, thats right, reboot. 

5. If that does not work, then you must rebuild your xorg.conf from scratch using dpkg-reconfigure xserver-xorg from one of the other consoles (alt+f1). Remember to first do an #mv /etc/X11/xorg.conf /etc/X11/xorg.conf.old. Once thats done, reboot into your fresh new X server (that is now properly configured), and ensure you have the Restricted Drivers enabled with the proper Nvidia driver. Assuming thats good, then open terminal and #nvidia-settings &. Setup your dual screens and resolutions as above remembering NOT to enable Xinerama. This should fix any Compiz issues as well.

Ok. Welcome to Gutsy with a nice new 3D screen and dual monitors!

---

### Post by Diskdoc on 2007-10-24
**Model:** HP Pavilion DV6111EU
**Processor:** AMD Sempron 3400+
**Wireless Card:** Broadcom 94311MCG mini-PCI
**Graphics Card:** NVidia Geforce 6150 Go 
**Gutsy:** 7.10 final + updates
**Boot Parameters:** Still booting with Feisty kernel 2.6.20-16-generic with parameter vga=791

Upgraded from Feisty and unhappily discovered freezing on boot with the new 2.6.22 kernel. The boot process comes a bit further using noapic but still freezes.

With Feisty, I also had freezes on boot with a strangely garbled screen as the boot proceeded starting X. Digging around I found some people had solved that using the vga= parameter. The resolution during boot is wrong but at least it works. Using the OSS NVidia-driver as the new closed source binary is installed for the Gutsy kernel.

[edit]

Tireing of my Gutsy problems (no 3D with old kernel+OSS NVidia driver..some glx messup I guess) I booted SystemRescueCD to repartition and pull in Gentoo from my old harddrive. During boot the bootprocess hung early on, just like in Gutsy. There however, I could see the output from the boot (guess I should have removed the "quiet" option for that one in Ubuntu) and some PNP-initialization messages were the last to be seen.

The kernel has been complaining about some BIOS bug (but as mentioned, the Feisty-kernel boots nonetheless) so I had a thought: maybe this is related to the Plug'n'play BIOS-support? True enough: **passing "pnpbios=off pnpacpi=on" to the Gutsy kernel helped the boot process past the freezing early on!** If I understand this correctly, the newer kernels use the BIOS PNP by default rather than ACPI PNP. Why?

Gutsy still hangs on me when switching to X, though. The vga=791 parameter doesn't do anything here. Rather than searhing for the solution to that one I'm reverting to Gentoo. Gutsy is a bit too tricky for me on this laptop.

---

### Post by mnederlanden on 2007-10-24
Model: HP Pavilion dv9009nr
Processor: 1.6 GHz AMD Turion™ 64 X2 Dual-Core Mobile Technology TL-52
Wireless Card: Broadcom 802.11b/g WLAN
Graphics Card: NVIDIA GeForce Go 6150 (UMA)
Gutsy: 7.10 final + updates
Boot Parameters: apci=off

I initially had major problems with my monitor, but I told it I had a LCD Panel 1440x900 widescreen at 60hz and used the nv - nVidia Riva 128, RIVA TNT, GeForce, nf... driver...

it runs a little slow but it works in much better than what was before...

Restricted driver manager will screw up 9009nr's! Do not use NVDIA accelerated graphic driver...

Firmware for Broadcom 43xx chipset family works... (I never could get it to work in fiesty)... however the switch on the front of my pc that allows me to turn off my wireless to conserve power is in constant off mode according to ubuntu...

Still its better than feisty for me as the display works about the same and the broadcom 43xx works somewhat....

---

### Post by edemark on 2007-10-24
> **mk04 said:**
> **Model:** HP ze5375us
**Processor:** Pentium 4 mPGA 478 socket @ 2.4GHz
**Wireless Card:** Netgear WG511 v1
**Graphics Card:** ATI Radeon IGP 345M
**Gutsy Tribe (Version):** Final Release, Ubuntu

I had no problems with the graphics card. Everything basically worked out of the box. Wireless was a bit of an issue.

mk04 please can you post your xorg.conf to this thread:
[http://ubuntu-utah.ubuntuforums.org/showthread.php?t=581485](http://ubuntu-utah.ubuntuforums.org/showthread.php?t=581485)

thaks in advance

---

### Post by pescez on 2007-10-24
> **zoogTHOMzoog said:**
> **Model:** HP Pavillion zv6000
**Processor:** AMD Sempron 3200+ 
**Wireless Card:** Broadcom 4318
**Graphics Card:** ATI Radeon 200M
**Gutsy Tribe** (Version): Final Release 64 bit version

I have everything working... my wireless worked fine with the use of the restricted bcm43xx driver and netapplet (sudo apt-get netapplet). CompizFusion works fine with an xgl session (sudo apt-get xserver-xgl). 

**BUT** it takes approximately 3 minutes to load (i.e. from the grub menu to the gdm menu). So if anyone knows how to fix this, please let me know!

Thanks, 
Thom

to shorten boot time try to add the word 'profile' among kernel boot options. press 'e' during grub menu time and add it to your kernel line. it's enough to do it just once, this generates a file that allow a very shorter boot time.

---

### Post by zoogTHOMzoog on 2007-10-24
> **#Reistlehr- said:**
> Theres an option in i think /etc/usplash.conf for the resolution. It's bigger than your screen, so set the values to 1024 and 768 respectivly.

Thanks, but I forgot to mention in my first post that the splash worked fine, it just took 3 minutes from grub to gdm... and now that I have disabled the splash it takes about 3 seconds. But I will double check the /etc/usplash.conf file to see if something is wonky.

Thanks for your help,

~T

---

### Post by Keyper7 on 2007-10-25
**Model:** HP Pavilion dv6258se
**Processor:** Turion X2
**Wireless Card:** Broadcom
**Graphics Card:** GeForce Go 6150
**Gutsy Version:** Final
**Boot Parameters:** noapic acpi_irq_balance

acpi_irq_balance is not needed to boot, but using it avoids the spurious interrupt storm that ehci_hcd would generate otherwise. After installing the proprietary nvidia drivers, I don't need the parameters to boot anymore.

Wireless drivers are working and wireless networks are being detected, but once I try to connect to a not-listed non network, the network manager crashes. After a few tries it doesn't crash anymore, but either keeps trying to connect and never suceeds or apparently succeeds but doesn't work at all (plus, the wireless signal in this case is shown as being 100%, which is not true). (problem happens both if I'm using bcm43xx or ndiswrapper)

Rebooting or shutting down randomly hangs the computer after the "stopping GNOME" stage. Hard hang, not even SysRq works.

Console randomly hangs if I use a command that produces a lot of output, like dmesg. This problem does not happen if I use nvidiafb, though, or if I keep the noapic parameter.

Fsck hangs at a random percentage unless I use noapic.

Of all problems listed, only the last two (console and fsck) happen on Feisty. The wireless and shutdown problems only appeared on Gutsy.

---

### Post by Inxsible on 2007-10-25
**Model:** HP Pavilion dv9000t
**Processor:** Intel Core 2 Duo 1.83GHZ
**Wireless Card:** Intel Pro Set 3945 A/B/G 
**Graphics Card:** GeForce Go 7600
**Gutsy Version:** Final (64 bit)
**Boot Parameters:** none

I have just one problem that my screen keeps flickering. This is a problem a lot of people are facing and it is said to have been because of the NVidia driver. This never happened to me in my Feisty install.

Wireless, sound, resolution everything worked out of the box, just like it did in Feisty :)

---

### Post by midknight51 on 2007-10-25
Model: Compaq F572US
Processor: AMD 64 AthlonX2
Wireless Card: Broadcom 4311
Graphics Card: GeForce 6150
Gutsy Version: Final (64 bit)
Boot Parameters: noapic irqpoll

Wireless is a bit of a bugger to get working perfectly, following the guide to installing the Broadcom wireless([https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff")) I successfully got the wireless working however it cannot connect to any wireless that has any sort of encryption so im not sure if there was a bug in the installation process.

Video card can cause problems but i just ran the Restricted Hardware program and it fixed it perfectly.

---

### Post by ghonz on 2007-10-25
how did you get the headphone jack to work?
I'm using a HP Pavilion Tx1138ea and struggling to get the headphone jack to work

---

### Post by ibison on 2007-10-25
Model: hp Compaq 8510w
Processor: Intel® Core™ 2 Duo processor T7500 2.20 GHz
Wireless Card: intel 4965AGN
Graphics Card: NVIDIA Quadro FX 570M 1920x1200
Gutsy Tribe (Version): 64 bit

Install of Gutsy possible only with text-based alternative installer.

Could not get Ubuntu-supplied partitioning function to work during install, so used a 3rd party partitioner; now have dual boot, with Vista still sitting around. HP has its own recovery partition also, which left only two out of 4 available for Ubuntu. So assigned / and /home only - no swap. (Have 2GB RAM.)

Could not get auto detect to recognize screen 1920x1200 so overwrote xorg.conf by hand. Also works to select 'widescreen' in the 'screens & graphics' menu item in system / admin.

Cannot get hibernate to work. System starts up again almost immediately. Any help on this issue appreciated!

---

### Post by dan l on 2007-10-25
Obviously, this will be the least interesting post in the thread.  

F730US - Compaq
Configuration
AMD Dual core TK 55 64 bit
Nvidia GeForce 6100
Broadcom Wireless 94311
Nvidia MCP 51

**Trying* to run a dual boot - vista/gutsy.  

LiveCD installer won't boot.  Locks up upon the display of options.  

Text installer works with no visible errors.  Upon attempting to boot into Gutsy, it locks up at the splash screen.

---

### Post by edemark on 2007-10-25
[B]Model: Compaq presario 1825
Processor: Intel pentium II 365mhz
Wireless Card: NO
Graphics Card: Ati mach64
Gutsy Tribe (Version): final release installed with minicd (netinstall base system and xubuntu)
Boot Parameters: [/B](Only if extra boot options are needed in order to boot) none even though i sould have used noapic as i get an error message in startup stating that i have not got acpi wich is true (I only have apm)

The two issues to mention are that according to the installer my hd is scsi which is not true (but seems to be working) and second that even tough the system was installed with the minicd (that means that everything was downloaded from the internet) now i just cannot connect to the same red. 
Any ideas?

---

### Post by grEnAlEins on 2007-10-26
**Model:** Compaq Presario C501NR
**Processor:** Intel Celeron 430 @ 1.73GHz
**Wireless Card:** Broadcom 802.11b/g WLAN
**Graphics Card:** Intel Graphics Media Accelerator 950 (945GM chipset)
**Gutsy Tribe (Version):** Final
**Boot Parameters:** Have to select Ubuntu instead of Vista/Longhorn.  Ubuntu is the default.

Almost everything works just perfectly.  No problems with anything.  Even using the wireless card went smoothly.  Just used a restricted driver.  A few issues to work out, but thrilled overall.:guitar:

Headphones get sound, but speakers will not mute when headphones are in.
Problems coming back from sleep.
Wireless only works at half speed 20 or 22 M.
Something else that I am forgetting...:confused:

---

### Post by Tokke on 2007-10-28
Model: HP Pavilion DV5157eu (DV5000 series)
Processor: AMD Turion(tm) 64 Mobile Technology ML-34
Wireless Card: Broadcom BCM4311 [AirForce 54g]
Graphics Card:ATI Radeon XPRESS 200M
Gutsy Gibon: Final


Wireless works by enabling the restricted drivers and downloading the necessary drivers from the internet.  Speed is only 24 MB/s while I have a 54 MB/s card.

I had an issue when booting.  Once I selected ubuntu from Grub the screen went black until after a few minutes the loginscreen appeared. I didn't see the Ubuntu progress bar. This was fixed by installing Startup Manager and changing the resolution to 1024 x 768.  

Compiz was also a problem.  When I tried to activate it by selecting System -> Preferences -> Appearance -> Visual effects -> Extra I  had an error message "The composite extension is not available"
I solved this in 3 steps:
1) enabled the restricted drivers of my ATI card
2) changed the Option "Composite" parameter to 1 in the xorg.conf file
3) sudo apt-get install xserver-xgl
After a ctrl-alt-backspace I could enable Compiz.

I still have one unsolved problem.  I use the touchpad of my portable a lot and the mouse freezes/disappears a lot for a second or 2-3.  I already installed qsynaptics but that didn't do the trick.
There is alreay a topic started concerning this problem -> [http://ubuntuforums.org/showthread.php?p=3645537#post3645537]("http://ubuntuforums.org/showthread.php?p=3645537#post3645537")

---

### Post by rbsis on 2007-10-28
Model: Hp Omnibook 6000
Processor: Pentium 3 @ 900mhz (Stop laughing!)
Wireless Card: Zonet wireless CardBus (ZEW1502)
Graphics Card: ATI Rage Mobility P/M AGP 2x (rev 64)
Gutsy Tribe (Version): 7.10
Boot Parameters:

I had a problem with the wireless card, but after about an hour and a headache I got it up, now I just need compiz...

---

### Post by HankB on 2007-10-28
[B]Model: HP Special Edition L2000
Processor: AMD Turion (ML-37)
Wireless Card: Broadcom Corporation BCM4318 [AirForce One 54g]
Graphics Card: ATI Technologies Inc Radeon XPRESS 200M 5955 (PCIE)
Gutsy Tribe (Version): release
Boot Parameters: [/B] none required to boot
 

The flash memory card slot works for my SD cards.
WiFi just worked after I configured it. (I need to figure out what the roaming thing means as I had to disable that to configure the card.) I'm not sure if it is using OS drivers or ndiswrapper (which I used with Dapper.)

Video seems correctly configured out of the box.

Suspend locks up the computer. :confused: With Dapper (kernel 2.6.15) I added the following to the boot line:
**noapic acpi_sleep=s3_bios ignore_ff_buttons=PWRF**
I tried this with 2.6.22 and it still locks up. Anyone with pointers on how to get suspend working with this kernel, please let me know!

---

### Post by mangoHead84 on 2007-10-29
Model: Compaq Presario v3240AU
Processor: AMD Turion 64 X2 TL-52 1.6Gz
Wireless Card: Broadcom BCM4312
Graphics Card: nVidia GeForce 6150 Go
Gutsy Tribe (Version): Ubuntu 7.10

Only problem I have is that suspend doesn't work. After clicking on the shutdown icon and selecting suspend, the computer goes into suspend mode. However if you then press the power button to wake up from suspend the computer 'wakes up' but the screen remains blank. I tried then restarting X (Ctrl+Alt+Backspace), opening up the terminals (Ctrl+Alt+F2) to no avail. This behaviour is no different whether you select the option from the shut down menu or whether you close the lid. It worked once when I tried it the first time, but hasn't worked since then. I'm sure someone knows how to fix this problem. 

On the positive side, Gutsy immediately detected that I needed the nVidia restricted driver and installing that was a breeze. The wireless card was detected without problem, but I had to download firmware for the card, which was also automatically done. The resolution 1280x800 was recognised straight away as well and the sound worked as well.

---

### Post by chiskop on 2007-10-29
[B]Model: dv6000 something-something
Processor: AMD Sempron 3500+
Wireless Card: Broadcom Corporation BCM4318 
Graphics Card: nvidia geoforce go 6150
Gutsy: release
Boot Parameters: noapic nolapic irqpoll noirqdebug[/B]

Read through this thread with some trepidation, but decided to go ahead 'cos I'm completely the moer in with Vista. (Running ubuntu on my desktop and server, but had kept the vista that the laptop came with, until now).

The Live CD ran fine, sound and touchpad working without me having to fiddle with anything. Installed kubuntu alongside vista, and that too seemed to go fine.

On rebooting I have a grub menu with both kubuntu and Vista available (though hoping to be able to dispense with Vista at some stage :) ). 

But, problems begin when i try to login to the kubuntu side. I get a terminal login, though it still seems to be busy with the boot. The last message before the boot is something about usplash, and various sizes that it is trying and failing (the live cd found the resolution no problem). If i login it stills gives me [bcmxxxx] errors. If I try to run startx, it tells me there is an error, and that xserver 0:0 is already in use. 

So, it looks like I have two problems:
1. Something to do with usplash, which seems to mean that kdm won't start.
2. Trying repeatedly to load the bcm module, and failing.

Configuring the wireless driver is low on my list of priorities -  I don't require it for day-to-day work.

EDIT: Okay, Up and running.
First off, I blacklisted the bcm module, as explained [here]("http://ubuntuforums.org/showpost.php?p=3566393&postcount=7").
Secondly, sorted out xorg.conf using "sudo dpkg-reconfigure xserver-xorg".

Still have to look at getting twinview running, then virtualbox -> then I'll be happy. :)

---

### Post by Ayuthia on 2007-10-29
Model: dv6338se
Processor: AMD Turion 64 X2 1.8Mhz
Wireless Card: Broadcom 4311 (Dell Wireless 1390)
Graphics Card: Nvidia GeForce Go 6150
Gutsy Tribe Kubuntu (release) Ubuntu (upgrade from Feisty using Linux Magazine CD)
Boot Parameters: Kubuntu (noapic noirqdebug) Ubuntu (none!)

I decided that I wanted to try an upgrade to see if there is a difference between a fresh install vs. an upgrade.  Overall, I did not see any differences except for the boot parameters.

Has anyone that has done an upgrade tried booting without the noapic parameters?  I was surprised that I have not had to use it as of yet.  I even tried rebooting a few times just to see what would happen.

I would like to know if anyone else has experienced this.  I am trying to figure out what fixed this because Kubuntu still needs the parameters and it doesn't make any sense to me.

---

### Post by scifi007 on 2007-10-29
Model: HP omnibook 6100
Processor: intel 1Ghz PIII- M
Wireless Card: Intersil Prism 2.5 Wavelan
Graphics Card: Radeon Mobility M6 LY
Gutsy Tribe (Version): Ubuntu 7.10 RC (fresh install)
Kernel Options: None

Problems: splash screen not displayed on boot (see bug [#150930]("https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/150930"))

Also, during the 'Loading hardware drivers' step of boot, the laptop will sometimes shutdown unexpectedly.  Doesn't happen every time and I'm still not sure what's happening here.  Booted fine with 5.10 and 6.10 previously

---

### Post by #Reistlehr- on 2007-10-29
scifi: yeah ive noticed this myself.

everyone: Go through the thread's ive posted, and youll find a Suspend fix that works for my laptop.

---

### Post by mangoHead84 on 2007-10-29
Thanks Reistlehr, but could you provide a link to the post you're referring to to fix the suspend problem? 
Did you mean this thread [http://ubuntuforums.org/showthread.php?t=593845]("http://ubuntuforums.org/showthread.php?t=593845")?

---

### Post by #Reistlehr- on 2007-10-29
Yessir, that was it. 

A few friend with an older compaq, and a ien with a dv6000z said this fix worked for them also.

---

### Post by KevLeviathan on 2007-10-29
Model: Compaq V6215CA
Processor: Turion 64 X2 TL-50
Wireless Card: Broadcom 43XX series
Graphics Card: nVidia Geforce Go 6150
Using LiveCD of Gutsy 64Bit
Boot Parameters: nosplash noapic

LiveCD will boot if I use safe graphics mode, select a resolution of 800x600x32 and use noslpash and noapic as boot options. Installs fine and runs fine after that but noapic must be a permanent option or else the system will freeze when its booting.
Also the broadcom was a nightmare to set up, bcm43xx restricted driver did NOT work, it was very flaky and randomly decided not to work at times. I reinstalled ubuntu entirely and used the ndiswrapper method with great success!

---

### Post by halfmanhalfbug on 2007-10-31
Model: HP Special Edition L2000
Processor: AMD Turion (ML-37)
Wireless Card: Broadcom Corporation BCM4318 [AirForce One 54g]
Graphics Card: ATI Technologies Inc Radeon XPRESS 200M 5955 (PCIE)
Still on Feisty

Hi HankB. I have exactly the same model and suspend and hibernate do not work in Feisty. Disappointing to see the same problem in Gutsy. In Feisty suspend is handled by pmi by default. I downloaded uswsusp with apt-get and installed scripts to make it the default handler for suspending. It works in Feisty (though you must edit the scripts to change "s2ram" to "s2ram -f"). Interesting to see if it works in Gutsy. See
[http://blog.paulbetts.org/...]("http://blog.paulbetts.org/index.php/2007/02/11/fixing-software-suspend-hibernate-with-uswsusp-in-ubuntu-feisty-and-edgy/")
and
[ubuntuforums 483553]("http://ubuntuforums.org/showthread.php?t=483553")
I wish the developers would make uswsusp the default. And HP has an updated version of the BIOS (see their website) that fixes the clock issue but it is a .exe so to flash the BIOS you need a Windows dual-boot. Did you upgrade or do a fresh install?

---

### Post by Inw on 2007-10-31
I can't remember the details of my compaq, will post again from home. I installed two days ago, and i have the following problem: the login screen and everything after that is "shaking", if that makes any sense.... i can see multiple icons, multiple cursors, and everything is wobbly. I obviously can't use it at all, and since i'm a beginner i haven;t got a clue what to do...

---

### Post by HankB on 2007-10-31
> **halfmanhalfbug said:**
> Model: HP Special Edition L2000
Processor: AMD Turion (ML-37)
Wireless Card: Broadcom Corporation BCM4318 [AirForce One 54g]
Graphics Card: ATI Technologies Inc Radeon XPRESS 200M 5955 (PCIE)
Still on Feisty

Hi HankB. I have exactly the same model and suspend and hibernate do not work in Feisty. Disappointing to see the same problem in Gutsy. 

Hi halfmanhalfbug,
This worked for me previously, IIRC with Edgy, so it was a disappointment  that it did not work with Gutsy. Then I remembered... The ATI drivers had this bug back then, so I stuck with open source drivers. I did have other issues, like having to unload/reload ndiswrapper WiFi drivers and running aumix to restore sound on resume. But as long as it suspended, I was happy.

And then I thought... ATI drivers. So I went into the restricted driver manager and disabled the ATI video driver, rebooted and WOO!!! The system suspended and came back.

I still have the boot arguments listed above and I'll probably leave them there.

I upgraded. I think I wound up doing an install for Edgy when the upgrade from Dapper went bad. In the mean time, I had upgraded my old Thinkpad (T30) to Feisty and the built in wireless - flawless under stuff going way back - wasn't handled correctly. I held off until I could upgrade it to Gutsy. With Gutsy, wireless, suspend and hibernate all worked on the first try so I plunged ahead on the L2000. I did the upgrade in two steps using the upgrade manager. It all went pretty well.

I didn't try hibernate as I don't really care about that.

Thanks for the pointers to the other resources. I'll check them out. But for now I'm good!

-hank

---

### Post by stevetxt on 2007-11-03
Model: HP Compaq 2510p
Processor: Intel Core 2 Duo U7600, 1.2 GHz
Wireless Card: Intel abgn
Graphics Card: Mobile Intel GM965
Ubuntu version: 7.10 Gutsy
Boot Parameters: No extra options added 

Install went pretty much out of the box.  However, resume from suspend does not work.  Does anyone have a solution to this?

---

### Post by besada on 2007-11-04
Model: HP Compaq 8510w
Processor: Intel Core 2 Duo 7500 2.2 GHz
Wireless Card: Intel 4965 abgn
Graphics Card: Nvidia Quadro FX 570 M
Ubuntu version: 7.10 Gutsy
Boot Parameters: No extra options added 

Almost everything worked, but:

- Had to install using safe graphics mode (normal boot will not enter). No need for alternate cd.
- Nvidia graphics and new applets do not function well altogether. use nvidia-settings. Using twinview + compiz fusion with the wall and expo plugins ... new world in usability.
- Suspend to ram or to disk do not work at the beginning. I think I have solved it, but as I think it is a problem for many more people I will give "the solution" in other post, later (tonight).
- Brightness Fn keys applets do not function at all. It is my latest point of friction.

I have dual boot with vista, but I really doubt I will use vista at all .... jus in case I will leave it there.

---

### Post by stevetxt on 2007-11-04
I'm interested in what solution worked for you on the suspend/resume.

---

### Post by besada on 2007-11-04
I have just posted it

[http://ubuntuforums.org/showthread.php?t=602806](http://ubuntuforums.org/showthread.php?t=602806)

---

### Post by sleepwalker on 2007-11-06
Model: hp dv2125nr
Processor: Turion x2
Wireless Card: (see below)
Graphics Card: Built in (see below)
Gutsy Tribe (Version): 7.10
Boot Parameters: Dual-booting Windows Vista.


Any ideas on intermittent sound?

lspci:

00:00.0 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.1 RAM memory: nVidia Corporation C51 Memory Controller 0 (rev a2)
00:00.2 RAM memory: nVidia Corporation C51 Memory Controller 1 (rev a2)
00:00.3 RAM memory: nVidia Corporation C51 Memory Controller 5 (rev a2)
00:00.4 RAM memory: nVidia Corporation C51 Memory Controller 4 (rev a2)
00:00.5 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.6 RAM memory: nVidia Corporation C51 Memory Controller 3 (rev a2)
00:00.7 RAM memory: nVidia Corporation C51 Memory Controller 2 (rev a2)
00:02.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:03.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:05.0 VGA compatible controller: nVidia Corporation C51 [Geforce 6150 Go] (rev a2)
00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)
00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a3)
00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a3)
00:0a.3 Co-processor: nVidia Corporation MCP51 PMU (rev a3)
00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0d.0 IDE interface: nVidia Corporation MCP51 IDE (rev f1)
00:0e.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev f1)
00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2)
00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a3)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 Network controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 01)
05:09.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller
05:09.1 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
05:09.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 01)
05:09.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)
05:09.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 05)

---

### Post by drf_av on 2007-11-06
Ok guys, so after some months i've managed to get everything to work on my hp dv6560el. So here's the most tricky components:

Webcam: It's a video4linux2 device. Note it's 2, not just v4l. It works flawlessly and I managed to use it with amsn. Also the useless blue lights next to it works ._.

Fingerprint reader: It actually works, if you apt-get install aes2501-wy, but I don't know if there's a way to integrate it in GDM and/or elsewhere. Answers here are welcome.

Audio Card: It won't work at first boot. It will work after you issue sudo ./install in realtek's audio codecs. Here they are: [http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=24&PFid=24&Level=4&Conn=3&DownTypeID=3](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=24&PFid=24&Level=4&Conn=3&DownTypeID=3)

Wireless Card: working flawlessly from live cd. Thanks Intel :)

Video Card: Works with latest nVidia Drivers, but I've run into some troubles on login and on wakeups from suspend. It just randomly crashes everything, so you have to press the poweron button and restart. Annoying, I just hope nVidia Drivers will work as good as they claim they are in next releases.

This was for Gutsy, I'm not able to start Feisty's live CD, probably video card's fault. But I have to say that this laptop is so great, and really Linux Friendly.

---

### Post by 34.50 on 2007-11-06
Model: Compaq V5303nr
Processor: AMD Turion ML-32 1.8GHz
Wireless Card: Broadcom 802.11 B/G (don't know the exact one)
Graphics Card: ATI Radeon X200M (Up to128MB Shared, using 32MB set in BIOS)
Ubuntu 7.10 Gutsy Gibbon
RAM: 512MB

Dual booted with XP Pro, works nicely. Can't figure how to get the wireless setup, as I don't have an access point at the moment, and the blue light to enable it, won't come on upon pressing it. Upon hitting the mute button, orange light on the button doesn't come on, this is a minor problem. On the software side, I can't get get Flash to install for Opera. :( 

Other than that, I'm amazed at how great the community for HP/Compaq laptops is, considering about everything works. It amazed me when things like the FN buttons worked, wasn't expecting that. 

This is my first time actually installing Linux on the hard drive. I've ran it in VMWare before, but the speed isn't great, especially considering I can dedicate only 260MB of RAM to it. 

Overall, I have a positive attitude towards Ubuntu.

---

### Post by vinsk1 on 2007-11-07
Model: HP Compaq nx9000
Processor: Intel Pentium 4 2GHz
Wireless Card: Intersil Prism 2/2,5/3 (?) Intersil Prism anyway
Graphics Card: ATI RS200 IGP 340m
Gutsy Tribe (Version): 7.10
Boot Parameters: default

Everything worked fine after install. I only had small problems with gfx-card, couldn't use it with other driver than vesa, if i tried other drivers (ati, fglrx etc) i only got blurry screen.

That problems fixed after i configured X with:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

and added this line to xorg.conf Device section manually:
```
Option		"LVDSBiosNativeMode" "false"
```

and push ctrl+alt+backspace..

with vesa driver i got glxgears ca. 150fps and couldnt play divx in fullscreen now i got ca. 350fps and DV-avis and divx files play fine in fullscreen.

I found fix to problem from here:
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/155954]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/155954")

---

### Post by speedster8 on 2007-11-07
See my sig for uppto date Hp/compaq tests.

Have a Omnibook XE3 that is nextone upp :)
:popcorn::KS

---

### Post by EXCiD3 on 2007-11-07
For more information on Gutsy and HP and Compaq laptops, please read my website: [http://excid3.pcriot.com]("http://excid3.pcriot.com/drupal/") Some important information is included on there.

Also, if anyone would like to contribute their laptop experiences and tweaks please register and post to your blog! Once enough information has been gathered I will be writing a tutorial for Gutsy so any information you would like to post on the site that you think would be relevant for the tutorial feel free to post. I would appreciate it.

---

### Post by kubel on 2007-11-07
Model: HP Pavilion DV6000Z CTO (RX950AV)
Processor: AMD Turion 64 X2 TL-56 (1.8GHz)
Wireless Card: BCM4312
Graphics Card: GeForce Go 6150
Gutsy Tribe (Version): 32-bit Stable
Boot Parameters: *noapic* (press F6 at CD boot menu, type, press enter)


WIRELESS:
I know most people with AMD HP's have BCM4311. After a failed attempt at installing ndiswrapper myself using step-by-step instructions here on the forums, and then using a script someone made, I gave up and went with the easiest method I could think of... I installed a program through Add/Remove Applications called "Windows Wireless Drivers" (or  "ndisgtk". I then used sp36684.exe to obtain bcmwl5.sys, started ndisgtk, loaded my driver, and within 15 seconds, I could see a list of access points near my house. Worked perfectly. I then added *modprobe ndiswrapper* to /etc/rc.local so ndiswrapper would load the driver automagically. Since then, I've only experienced one dropped connection (Ubuntu swears I was connected, but I wasn't). 

BLUETOOTH:
Appears to be working fine, but I haven't tested it yet. 

GRAPHICS: 
Worked perfectly out-of-box. I'm using the restricted nvidia driver, but I don't think that was even necessary. Native resolution worked even without it installed.

PORTS:
Here's where I'm having a problem. None of my 3 USB ports are working (I've tried my SOYO thumbdrive, a Logitech joystick, and my Pentax DSLR). I don't know about FireWire since I have no devices to test. The card reader works perfectly (at least for SD cards, which is all I ever use). The front two audio-out ports work fine as well. Unknown about the front mic port.

QUICKPLAY BUTTONS:
Volume buttons work perfectly. I haven't tested anything left of the mute button, and probably have no intention to since I never used them even in Vista. 

SPEAKERS:
I've heard a lot of people have problems with getting speakers to work. Mine work perfectly. As I mentioned before, front two audio outs work fine, unknown about mic port.

WEBCAM/INTERNAL MIC:
Unknown, never got a chance to test them. But I read ACER has drivers for it. 

POWERNOW:[B]
[fixed]
Ran *sudo dpkg-reconfigure gnome-applets* and then used (left click to set speed) the CPU Frequency Monitor Utility on the panel. Now it's cool n' quiet.
[/fixed][/B]
I absolutely despise the way Ubuntu is throttling my processor. Even typing text causes my processor to open all the way up to 1800MHz (probably full voltage as well), and my fan (while almost always on low in Vista) runs at full speed whenever the processor kicks up to maximum. I have a feeling there's incorrect undervolting going on while at 800MHz as well. I would really like to find a way to permanently force minimal clock and voltage in an easy-to-change method (much like Vista has). But I fear I will be digging through text files changing Hz settings manually. But at least my laptop stays nice and toasty through this cold Michigan season. Oh, and did I mention battery life is horrible? Expect about a 33% decrease in battery life compared to what you get in Windoze. 

SUSPEND: 
I can't resume from suspend without the system locking up, although I can't tell if it's locking up or if the video just isn't kicking in. I'll have to look more into this, but if I were you, avoid using Suspend. I haven't tried Hibernate. 


I think that's all of my complains/suggestions.Wireless was the only thing that I was able to fix. Everything else is pretty much broken, but I guess I'm lucky to have this much stuff working anyway. I'll be lurking around the forums for solutions you all have to USB, power management, etc... If I find anything useful I'll post my experience here. 

Good luck fellow HP users!

---

### Post by sfgiants16 on 2007-11-07
Hello. I am an extreme newbee to Linux in general. I just bought an HP DV6500t and Visa has been less than impressive. I'm really impressed with Ubuntu but I've not been able to resolve the sound issue, most likely due to my limited experience with Linux. If anyone can help, I'd really appreciate it. Here's what I've done so far:

I've attempted to follow the instructions at: [https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

I downloaded the most recent alsa files: alsa-driver-1.0.9rc4a, alsa-lib-1.0.9rc4, and alsa-utils-1.0.9rc4a. I have copied them into /usr/src/alsa

I started with the driver. I believe that the ./configure command worked successfully. However, I received errors when I used the "make" command:

code:
> 
root@jeff-laptop:/usr/src/alsa/alsa-driver-1.0.9rc4a# make
make[1]: Entering directory `/usr/src/alsa/alsa-driver-1.0.9rc4a/acore'
gcc -D__KERNEL__ -DMODULE=1 -I/usr/src/alsa/alsa-driver-1.0.9rc4a/include -I/lib/modules/2.6.22-14-generic/build/include -I/lib/modules/2.6.22-14-generic/build/include/asm-i386/mach-default -O2 -mpreferred-stack-boundary=2 -march=i586 -D__SMP__ -DCONFIG_SMP -DLINUX -Wall -Wstrict-prototypes -fomit-frame-pointer -Wno-trigraphs -O2 -fno-strict-aliasing -fno-common -pipe -DALSA_BUILD -nostdinc -iwithprefix include -DMODVERSIONS -include /lib/modules/2.6.22-14-generic/build/include/linux/modversions.h -DKBUILD_BASENAME=hpetimer -c -o hpetimer.o hpetimer.c
cc1: error: /lib/modules/2.6.22-14-generic/build/include/linux/modversions.h: No such file or directory
In file included from hpetimer.c:22:
/usr/src/alsa/alsa-driver-1.0.9rc4a/include/sound/driver.h:29:26: error: linux/config.h: No such file or directory
In file included from /lib/modules/2.6.22-14-generic/build/include/asm/processor.h:22,
from /lib/modules/2.6.22-14-generic/build/include/asm/thread_info.h:16,
from /lib/modules/2.6.22-14-generic/build/include/linux/thread_info.h:21,
from /lib/modules/2.6.22-14-generic/build/include/linux/preempt.h:9,
from /lib/modules/2.6.22-14-generic/build/include/linux/spinlock.h:49,
from /lib/modules/2.6.22-14-generic/build/include/linux/module.h:9,
from /usr/src/alsa/alsa-driver-1.0.9rc4a/include/adriver.h:45,
from /usr/src/alsa/alsa-driver-1.0.9rc4a/include/sound/driver.h:42,
from hpetimer.c:22:
/lib/modules/2.6.22-14-generic/build/include/linux/cpumask.h:88: error: ‘CONFIG_NR_CPUS’ undeclared here (not in a function)
In file included from /lib/modules/2.6.22-14-generic/build/include/asm/thread_info.h:16,
from /lib/modules/2.6.22-14-generic/build/include/linux/thread_info.h:21,
from /lib/modules/2.6.22-14-generic/build/include/linux/preempt.h:9,
from /lib/modules/2.6.22-14-generic/build/include/linux/spinlock.h:49,
from /lib/modules/2.6.22-14-generic/build/include/linux/module.h:9,
from /usr/src/alsa/alsa-driver-1.0.9rc4a/include/adriver.h:45,
from /usr/src/alsa/alsa-driver-1.0.9rc4a/include/sound/driver.h:42,
from hpetimer.c:22:
/lib/modules/2.6.22-14-generic/build/include/asm/processor.h:83: error: ‘CONFIG_X86_L1_CACHE_SHIFT’ undeclared here (not in a function)
/lib/modules/2.6.22-14-generic/build/include/asm/processor.h:83: error: requested alignment is not a constant
/lib/modules/2.6.22-14-generic/build/include/asm/processor.h: In function ‘cpuid_count’:
/lib/modules/2.6.22-14-generic/build/include/asm/processor.h:618: warning: pointer targets in passing argument 1 of ‘native_cpuid’ differ in signedness
/lib/modules/2.6.22-14-generic/build/include/asm/processor.h:618: warning: pointer targets in passing argument 2 of ‘native_cpuid’ differ in signedness
/lib/modules/2.6.22-14-generic/build/include/asm/processor.h:618: warning: pointer targets in passing argument 3 of ‘native_cpuid’ differ in signedness
/lib/modules/2.6.22-14-generic/build/include/asm/processor.h:618: warning: pointer targets in passing argument 4 of ‘native_cpuid’ differ in signedness
In file included from /lib/modules/2.6.22-14-generic/build/include/linux/gfp.h:4,
from /lib/modules/2.6.22-14-generic/build/include/linux/slab.h:14,
from /lib/modules/2.6.22-14-generic/build/include/linux/percpu.h:5,
from /lib/modules/2.6.22-14-generic/build/include/asm/desc.h:11,
from /lib/modules/2.6.22-14-generic/build/include/asm/elf.h:50,
from /lib/modules/2.6.22-14-generic/build/include/linux/elf.h:7,
from /lib/modules/2.6.22-14-generic/build/include/linux/module.h:15,
from /usr/src/alsa/alsa-driver-1.0.9rc4a/include/adriver.h:45,
from /usr/src/alsa/alsa-driver-1.0.9rc4a/include/sound/driver.h:42,
from hpetimer.c:22:
/lib/modules/2.6.22-14-generic/build/include/linux/mmzone.h: At top level:
/lib/modules/2.6.22-14-generic/build/include/linux/mmzone.h:43: error: requested alignment is not a constant
/lib/modules/2.6.22-14-generic/build/include/linux/mmzone.h:93: error: requested alignment is not a constant
/lib/modules/2.6.22-14-generic/build/include/linux/mmzone.h:305: error: requested alignment is not a constant
In file included from /lib/modules/2.6.22-14-generic/build/include/linux/module.h:21,
from /usr/src/alsa/alsa-driver-1.0.9rc4a/include/adriver.h:45,
from /usr/src/alsa/alsa-driver-1.0.9rc4a/include/sound/driver.h:42,
from hpetimer.c:22:
/lib/modules/2.6.22-14-generic/build/include/asm/module.h:64:2: error: #error unknown processor family
In file included from /lib/modules/2.6.22-14-generic/build/include/linux/sched.h:51,
from /lib/modules/2.6.22-14-generic/build/include/asm/irq.h:13,
from /lib/modules/2.6.22-14-generic/build/include/linux/irq.h:23,
from /lib/modules/2.6.22-14-generic/build/include/asm/hardirq.h:5,
from /lib/modules/2.6.22-14-generic/build/include/linux/hardirq.h:7,
from /lib/modules/2.6.22-14-generic/build/include/linux/interrupt.h:11,
from hpetimer.c:26:
/lib/modules/2.6.22-14-generic/build/include/linux/jiffies.h:33:3: error: #error You lose.
/lib/modules/2.6.22-14-generic/build/include/linux/jiffies.h:225:31: error: division by zero in #if
/lib/modules/2.6.22-14-generic/build/include/linux/jiffies.h:225:31: error: division by zero in #if
/lib/modules/2.6.22-14-generic/build/include/linux/jiffies.h:225:31: error: division by zero in #if
/lib/modules/2.6.22-14-generic/build/include/linux/jiffies.h:225:31: error: division by zero in #if
/lib/modules/2.6.22-14-generic/build/include/linux/jiffies.h:225:31: error: division by zero in #if
/lib/modules/2.6.22-14-generic/build/include/linux/jiffies.h:225:31: error: division by zero in #if
/lib/modules/2.6.22-14-generic/build/include/linux/jiffies.h:225:31: error: division by zero in #if
/lib/modules/2.6.22-14-generic/build/include/linux/jiffies.h:225:31: error: division by zero in #if
/lib/modules/2.6.22-14-generic/build/include/linux/jiffies.h:225:31: error: division by zero in #if
/lib/modules/2.6.22-14-generic/build/include/linux/jiffies.h:225:31: error: division by zero in #if
/lib/modules/2.6.22-14-generic/build/include/linux/jiffies.h:225:31: error: division by zero in #if
/lib/modules/2.6.22-14-generic/build/include/linux/jiffies.h:225:31: error: division by zero in #if
/lib/modules/2.6.22-14-generic/build/include/linux/jiffies.h:225:31: error: division by zero in #if
/lib/modules/2.6.22-14-generic/build/include/linux/jiffies.h:225:31: error: division by zero in #if
/lib/modules/2.6.22-14-generic/build/include/linux/jiffies.h:225:31: error: division by zero in #if
/lib/modules/2.6.22-14-generic/build/include/linux/jiffies.h:225:31: error: division by zero in #if
In file included from /lib/modules/2.6.22-14-generic/build/include/linux/pid.h:4,
from /lib/modules/2.6.22-14-generic/build/include/linux/sched.h:72,
from /lib/modules/2.6.22-14-generic/build/include/asm/irq.h:13,
from /lib/modules/2.6.22-14-generic/build/include/linux/irq.h:23,
from /lib/modules/2.6.22-14-generic/build/include/asm/hardirq.h:5,
from /lib/modules/2.6.22-14-generic/build/include/linux/hardirq.h:7,
from /lib/modules/2.6.22-14-generic/build/include/linux/interrupt.h:11,
from hpetimer.c:26:
/lib/modules/2.6.22-14-generic/build/include/linux/rcupdate.h:71: error: requested alignment is not a constant
/lib/modules/2.6.22-14-generic/build/include/linux/rcupdate.h:74: error: requested alignment is not a constant
In file included from /lib/modules/2.6.22-14-generic/build/include/asm/hardirq.h:5,
from /lib/modules/2.6.22-14-generic/build/include/linux/hardirq.h:7,
from /lib/modules/2.6.22-14-generic/build/include/linux/interrupt.h:11,
from hpetimer.c:26:
/lib/modules/2.6.22-14-generic/build/include/linux/irq.h:176: error: requested alignment is not a constant
In file included from /lib/modules/2.6.22-14-generic/build/include/linux/hardirq.h:7,
from /lib/modules/2.6.22-14-generic/build/include/linux/interrupt.h:11,
from hpetimer.c:26:
/lib/modules/2.6.22-14-generic/build/include/asm/hardirq.h:12: error: requested alignment is not a constant
make[1]: *** [hpetimer.o] Error 1
make[1]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.9rc4a/acore'
make: *** [compile] Error 1


I really have no idea what I am doing or what these commands are supposed to acomplish. I am simply trying to follow the instructions. Given that, are there any steps that I can take to resolve this?

Here are the results of cat /proc/asound/card0/codec#* | grep Codec
Code:

> Codec: Realtek ID 268
Codec: Motorola Si3054
Thanks for any help you can provide.

Jeff

---

### Post by Cyber-J on 2007-11-07
Model: DV6305US
Processor: Turion/X2
Wireless Card: BCM4311
Graphics Card: NVIDIA Go 6150
Gutsy Tribe (Version): 64-bit Stable LiveCD
Boot Parameters: noapic nolapic noirqdebug irqpoll

Wireless: Using restricted drivers with firmware available at [http://downloads.openwrt.org/sources/wl_apsta-3.130.20.0.o](http://downloads.openwrt.org/sources/wl_apsta-3.130.20.0.o)

Video: Using restricted drivers on dual monitor setup - Finally working! :popcorn:

Note: Had to boot gutsy into single user (safe recovery) mode and then do 'nvidia-xconfig -twinview' to finally get things working on the external monitor after enabling the restricted driver. I can always to 'sudo nvidia-settings' in a terminal window to adjust any settings but otherwise I'm getting full 1440x900 resolution on the external monitor. I don't know if you need to have dynamic-twinview enabled also, but things are running fine without it. 

Sound: working.

Other:  Haven't tried messing with any power management settings or sleep/hibernate or suspend/resume yet.

---

### Post by fatmano on 2007-11-08
Model: Compaq Presario x6000
Processor: P4 HT
Wireless Card : Broadcom 43xx ( not exactly sure how to tell specifics ) 

I am a noob to Kubutu semi noob to *nix.  I upgraded my desktop at work in ~40 mins...flawless.  I had Fiesty on before and had installed / with a 10gb partition and /usr with the rest.  I just wiped the the old / partition and did a new install of Gusty.  Worked great!  So great that I decided that I would upgrade my laptop.  That did not go nearly so well.  

I ended up installing from the rescue mode from kubuntu-alternates and going thru the steps manually.  I obviously missed some steps b/c now when I boot I only boot to a terminal and once I login there I have to issue the command : startx

What I ran into when installing was when it came time to the step of install linux-generic my laptop would just shutdown like someone hit the power switch.  This still happens every now and again now while I running.  Not really sure why, there is nothing in the syslog.  I am tempted to drop back to Fiesty, but I have installed all the software that I need and if I get X to startup when I boot, I think that the I will keep it.

I am going to muttle thru it keep you posted on what I find out.  I am going to continue my quest to find the solution to the random shutdowns.

btw - any help on getting X to start would be great, although this thread may not be the place to do it.  

-eo

---

### Post by lopez1941 on 2007-11-08
Compaq Presario F579WM.  It's just like the F500.  I had to use ndiswrapper to get the wireless working.  I followed the instructions here:[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#head-d8ce0e35a4ccdbeddd6cf36f9cb23a11d8e0e9dc](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#head-d8ce0e35a4ccdbeddd6cf36f9cb23a11d8e0e9dc)
Used the restricted driver for Nvidia.  Everything is working great: desktop effects, keyboard shortcut keys, suspend.  Thanks, Donnie.

---

### Post by dasos on 2007-11-08
**Model:** HP DV2116WM (Branded as dv2000)
**Processor:** AMD64 X2
**Wireless Card:** Broadcom 43xx
**Graphics Card:** GeforceGo 6150
**Gutsy Tribe (Version):** AMD64 7.10 Desktop final version
**Boot Parameters:** None

Out of the box and installed, I had the following experiences:
On first boot had no menus/toolbars pop up so had to restart from command line (no big deal)
Restricted drivers for Nvidia and Broadcom were OK (made the mistake of trying my own .sys file from a windows partition instead of downloading broadcom drivers first)
Synaptic update worked fine
[B]
Problems:[/B]
NM-Applet won't do anything wireless related, if i go to network manager and try to change to browse mode it does nothing and nm-applet disappears.  Set up manually is fine, but I do plan on taking the laptop places.

I have no audio, tried to play some of the example files but no dice on output.
I don't know how to check my webcam, will concern with later (but direction appreciated).

Boomeranging back to linux after a long while (mostly b/c eve online has a supported client now =) and am not upset about the audio issues, I've always had that with linux and can figure it out later.  My concern is with a wifi network browser, as i see that as somewhat critical and can't seem to google my way around it.

Any help appreciated

---

### Post by Cranchh on 2007-11-08
> **xcafeus said:**
> Model: Pavillion dv6520ea
Processor: Core Duo 1.8GHz
Wireless Card: Intel Pro 3945
Graphics Card: Intel 965 (x3100)
Gutsy Tribe (Version): 64bit
Boot Parameters: Vista Home Premium / Ubuntu Gutsy

Sound does not work (seems to be a known bug - can be fixed but not 100%).
Sound Touch Button is always orange color although it seems to mute/unmute the sound system (which doesnt work anyway).
Fingerprint reader does not work.

you can use this : [https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)
to fix the sound and the sound buttons problem.
use 1.0.15 ver of alsa.

---

### Post by bduvall3 on 2007-11-09
Model: HP ze4600
Processor:AMD Athlon 2500+-m
Wireless Card:D-link PCMCIA
Graphics Card:ATi Radeon Mobility
Gutsy Tribe (Version): x86

Everything seems to be working fine. I haven't installed wireless yet, so I don't know if it will just plug-n-play, but I had no trouble getting it to work with ndiswrapper under Feisty, so probably not a problem here either.

The only thing I can't get to work is Dual Screen. I tried setting it up with Xinerama, but it was a no go.

---

### Post by chrischris349 on 2007-11-09
Model: c502us
Processor: Celeron M
Wireless Card: Broadcom 43xx
Graphics Intel GMA 950
Gutsy 7.10
When i restart i have to reinstall the wifi driver

---

### Post by buntunub on 2007-11-10
GAWD once again I got bit by that stupid sound bug with these HP lappys. I decided to try a dual boot of Fedora8 and Gutsy and somehow that new PulseAudio caused me to lose my sound...again. Had the same issue dual booting Vista for the one or two days I had it on there before wiping it off completely. Anyway, after recompiling the latest ALSA drivers back in needlessly, I finally tried what fixed sound for me with Vista... Unplug the power and reboot. I now have sound back again.

---

### Post by jonny_sicoli on 2007-11-10
Model: Compaq nx6110
Processor: Intel Pentium M 740 / 1.73 GHz
Wireless Card: Intel PRO/Wireless 2915ABG
Graphics Card: Intel GMA 900
Gutsy Tribe (Version): uhm... 32 bit?
Boot Parameters: none I know of.

Gutsy WOULD work fine, except the darn thing keeps crashing every so often.  I'm working on some thing, and suddenly, BAM! blank screen, command line pops up for a sec, and i'm booted to the login screen.  On KDE and Fluxbox, while I'm not booted to the login, the screen blanks out much more often when I'm idling, and sometimes when I'm not.  Usually a mouse wiggle takes care of that but it's ANNOYING!  And I can't for the life of me diagnose it.  Help, please?

EDIT:  The problem seems to have taken care of itself.  However,  i seem to have a new one - the mouse jumps slightly, without me touching the mousepad.  Usually, it's not a problem, but it can be a pain.

---

### Post by ptn107 on 2007-11-10
**Model:**v2000z
**Processor**:turion 64 bit (2ghz)
**Wireless Card:**broadcom airforce 4318
**Graphics Card:**ati radeon express 200m
**Gutsy Tribe (Version):**ubuntu 7.10 64-bit final release
**Boot Parameters:**none

flawless installation, works like a charm

---

### Post by Mondoman on 2007-11-11
Model: Compaq R3000Z
Processor: Athlon XP-M 3000+ (1.6GHz)
Wireless Card: Broadcom 54g 802.11b/g
Graphics Card: nVidia 64MB GeForce(M) 4 440 Go
Gutsy Tribe (Version): 7.10 (release version)
Boot Parameters: 

Installed from Live CD.  First, partitioned disk to free up about 30GB from XP partition.  When booting Live, had to select compatible VGA option in order to get readable display, but install to hard disk worked fine (guided onto free space) with defaults/automatic selection.  Used restricted nVidia graphics, modem, and wireless drivers.  After switching to restricted nVidia graphics driver, defaulted to native 1280x800 screen resolution and Compiz/Fusion fancy features worked fine.

---

### Post by Orval on 2007-11-12
HP Pavilion Media Center dv9580ed

AMD Turion 64 X2 TL-56

Level 2 cache 512 KB + 512 KB, 1600-MHz systembus
2048 MB memory

nVidia GeForce 8400M

160 GB SATA harddrive 5400-rpm

17-inch WXGA+ high-definition BrightView

Broadcom 4312 802.11a/b/g WLAN



Ubuntu 7.10 x86-64

Everything works out of the box (even the webcam), exept for the Broadcom WLAN. I still have to try to get it to work with ndiswrapper, but the driver file from the HP website doesn't seam to have a inf-file.

[edit] restart does not work. Ubuntu shuts down, but does not turn off the computer.

One concern though. The laptop gets very warm, even with low activity and the battery life is at most 1.5 hours. Maybe this will gets better when I tweak some services.

---

### Post by d1ss0nant on 2007-11-13
Model: Compaq R3000Z
Processor: AMD 64 3400 
Wireless card: Broadcom (can't recall #)
Graphics card: Nvidia Geforce4 440

With the help of this forum, i have been able to get everything working except:

Hibernate/standby
5-in-1 integrated card reader
"fn+F4" (switch between laptop monitor and external monitor)  I have to reboot :(
Java for firefox (admittedly i have not tried to fix this yet)
Screensavers to work will running compiz

---

### Post by d_fiant_1 on 2007-11-14
Model:Compaq Presario M2000
Processor:AMD Sempron +2800
Wireless Card:BCM4318
Graphics Card:Radeon xpress 200m
Gutsy Tribe (Version):7.10 is all i can tell you (14th Nov downloaded)
Boot Parameters: (Only if extra boot options are needed in order to boot)

I'm an absolute novice, Have never used and linux distro before, I now have Ubuntu Gutsy on 2 computers including the above laptop.

Installing on the above laptop was a breeze, installed, tweeked for about 10 minutes and everything 'just worked'

---

### Post by mosestruong on 2007-11-14
[B]Model: dv2308t
Processor: Centrino Core 2 Duo 1.73GHz
Wireless Card: Intel Corporation PRO/Wireless 3945ABG Network (ipw3945)
Graphics Card: nVidia Corporation GeForce Go 7200 (nvidia-glx-new)
Gutsy Tribe (Version): 7.10 Final 2.6.22-14-rt #1 SMP 
Boot Parameters: [/B]

Audio works out of the box. Graphics and wireless works out of the box after activating restricted module drivers. :)
Bluetooth works. short cut buttons and remote control mostly work.

Cannot get hibernate/suspend to work. brightness control doesn't work :(

---

### Post by TheIdiotThatIsMe on 2007-11-14
**Model**: Compaq Presario V4435NR (V4000 series).
**Processor**: Intel Pentium M 1.7Ghz
**Wireless Card**: Intel Pro/Wireless
**Graphics**: Integrated Intel GMA (up to 128MB)
**Gutsy 7.10 Final**

Installs and works flawlessly for what I've tested, even runs Compiz-Fusion without problems when using the simple effects, can do heavier effects but not as smooth and hurts CPU usage somewhat. Video worked flawlessly, no extra setup needed or drivers to download, sounds is good, but have not tested the media card readers. No suspend.

Rock on :guitar:

---

### Post by pndragon on 2007-11-14
**Model:** HP Pavilion dv9628nr
**Processor:** AMD Turion 64 x 2 TL-58
**Wireless Card:** BCM94311MCG wlan mini-PCI
**Graphics:** NVIDIA GeForce Go 7150
**Gutsy 7.10 Final**

I installed from the LiveCD using info found here: [http://ubuntuforums.org/showthread.php?t=575750]("http://ubuntuforums.org/showthread.php?t=575750").  I wanted to have a KDE desktop (just because that was what I was used to, having started Linux with Suse10.0), but that was a no go. Apparently gutsy, kdm and HP didn't play well together. That was ok. Kubuntu with with gdm works just fine... but kwifimanager wouldn't let me use WEP 64/128 bit hex passkey (KDE really needs to do something about this).

Anyway, my complaints so far don't have anything to do with the installation. Everything seems to be working within acceptable limits.

---

### Post by oysterpog on 2007-11-15
Model: HP-Compaq NX5000
Processor: 1.6gHz Pentium M
Wireless Card: intel 2200 something
Graphics Card: 855GM
7.10

gday all!

everything seems to work good. install was fine from alternate i386 cd.

lots of shutdown/suspend/hibernate issues. shutdown doesn't always work, from both gnome and the terminal; the system hangs and the screen goes blank at the point where it normally goes to the shutdown script things (sorry, i am uber noob)

it suspends fine, but when waking up the screen goes berko and all crazy colours and have to restart.

hibernate just doesn't work. real shame cause i like hibernate :) worked fine on feisty.

everything else is sweet as! desktop effects run surprisingly smoothly.

if anyone has the same prob with hibernate and has managed to fix it pleaaaase let me know!

ta all

---

### Post by gsuveg on 2007-11-16
Hi,

i installed gutsy to my nx7400 notebook, all works, only the cpufreq doesnt.

cpuinfo:

model name      : Intel(R) Core(TM)2 CPU         T5500  @ 1.66GHz
stepping        : 6
cpu MHz         : 1662.644
cache size      : 2048 KB

and cpufreq doenst works.
in  /sys/devices/system/cpu/cpu0/ directory i dont find the cpufreq dir.

[www.suveg.hu/dmesg](www.suveg.hu/dmesg) < here is my dmesg

~$ lsmod  | grep cpu
cpufreq_stats           7232  0 
cpufreq_ondemand        9612  0 
freq_table              5792  2 cpufreq_stats,cpufreq_ondemand
cpufreq_powersave       2688  0 
cpufreq_conservative     8072  0 
cpufreq_userspace       5280  0 

anybody have idea ?

---

### Post by gsuveg on 2007-11-16
after bios upgrade it works, but only

cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_available_frequencies 
1667000 1333000 1000000 

enabled... more idea ?

---

### Post by hortimech on 2007-11-16
Model: HP Pavilion dv9576ea
Processor: Intel Core2Duo T7300 2.00G
Wireless Card: Intel 4965AGN
Graphics: NVIDIA GeForce 8600M GS
Gutsy 7.10 Final

Installed Kubuntu from live-cd ok, Installed drivers for the WiFi card as per instructions near the start of this epic thread. Installed linux-uvc ( cannot remember where from, do a web search) for the chinony webcam, installed Nvidia graphics driver via Envy, this was the easy bit took about a couple of hours, everything seems to work ok apart from the sound!!
Tried everything I could find on the web, but Alsa/Gutsy seems to be broken and is known to be broken, so will probably get fixed in time.
Finally got sound by downloading the OSS drivers, again I cannot remember where I got them from, but see this post 

[http://ubuntuforums.org/showpost.php?p=3768914&postcount=60](http://ubuntuforums.org/showpost.php?p=3768914&postcount=60)

I now have sound, just about everything works that I need, I will have to find some memory cards to find out if the card reader works.:):)

---

### Post by noisebeard on 2007-11-17
I had to install Gutsy off the alternate cd.  Installed without any problems.  Used a wired connection to update the restricted drivers manager to handle my nVdia drivers.  I used some tutorials on this forum to get my BroadCom wireless card working.  And to finish everything off, I used another tutorial to recompile the alsa drivers for sound.

Everything works great now with the exception of

1. Headphone jack doesn't mute when plugged in
2. Flash plugin in ForeFox sometimes leaves weird grainly window when the browser is closed
3. When booting to Windows, you have to unplug the power cord to get the sound to work.  Same for booting back into Ubuntu.

I'm very happy with my Ubuntu and don't ever plan on going back to Winblows ;)

Sean

Specs:

HP Pavillion dv2610us
AMD Turion 64 x2
nVidia nForce 630a GPU
BroadCom Wireless
2GB Ram
150GB HD

---

### Post by beherenow on 2007-11-20
Please post the following things:
Model:HP Special Edition L2005 US Lance Armstrong Livestrong Laptop
Processor:AMD Turion64
Wireless Card: Broadcom 802.1 b/g 54g wifi card
Graphics Card:ATI Radeon XPress 200M IGP video/graphics card
Gutsy Tribe (Version):7.19 Gutsy Gibbon
Boot Parameters: (Only if extra boot options are needed in order to boot)

Installation went very smooth.  WIFI card didn't read automatically, but after install, I access the Systems/Administration/Restricted Drivers Manager, and it installed the firmware and driver for my Broadcom.  This is the first install I've made without relying on NDSWrapper and some other tweaks to get my wifi network card working.  It's worked flawlessly since the first install.

IAlso in the Restricted Drivers Manager was an option to install the ATI drivers for my graphics card.  DO NOT INSTALL THESE DRIVERS if you have this graphics card.  There may still be some glitch in getting the actual ATI drivers to work for this graphics card in Ubuntu.  My previous attempts to install them in 7.04 Feisty Fawn resulted in disaster.  No graphics at all.  Since the Ubuntu graphics driver works without a hitch, and I believe in the notion, "If it works, don't fix it," I did not install the ATI drivers

No other hardware issues except for the following:
long boot up time;
 occasional jumping cursor when typing:

I am enjoying Ubuntu, with only two minor complaints.  The first is about three or more minutes for Ubuntu to fully boot to the desktop.  If anyone has any ideas on how to reduce the boot up time, I am all ears and eyes.  The second is a tendency for the cursor to jump to another place or line in my text as I am typing from the keyboard.  Is there some setting or configuration that would eliminate this?  It doesn't happen with much frequency, but it is a bit annoying when it occurs.

Beyond these two minor glitches, I am pleased to say that my HP Special Edition L2005US notebook works extremely well with this latest, and best version of Ubuntu.  Good work and thanks to the developers and programmers.:)

---

### Post by HankB on 2007-11-20
> **beherenow said:**
> Please post the following things:
The second is a tendency for the cursor to jump to another place or line in my text as I am typing from the keyboard.  Is there some setting or configuration that would eliminate this?  It doesn't happen with much frequency, but it is a bit annoying when it occurs.


Look for the Synaptics setup program. qsynaptics. Once you have your settings made, it can be run in batch mode (qsynaptics -r IIRC) and put in the programs that run at login.

IIRC, the setting I used was to disable the touchpad during typing.

HTH,
hank

---

### Post by naja on 2007-11-20
Model:HP Pavilion ze4400
Processor:AMD Athlon XP-M
Wireless Card: none -Using PCIMCA with Realtekchip(rtl8185)+Ndiswrapper +wicd -
Graphics Card:ATI Radeon 320M
7.10 Gutsy Final
Most of the parts were autodetect, use acpi=off at installations boot, or it would hang at hardwaredetection near the setups end.
I only miss undervoltingtool -Lower than stock volts-
EDIT:
YES you can undervolt.See thread:
[http://ubuntuforums.org/showthread.php?t=608783](http://ubuntuforums.org/showthread.php?t=608783)

---

### Post by stunner on 2007-11-20
**Model:** HP DV8210us
**Processor:** AMD64
**Wireless Card:** Broadcom 4318 (rev 02)
**Graphics Card:** ATI 200m
**Gutsy Tribe (Version):** 7.10 Final (direct upgrade from Feisty)

Feisty -> Gutsy upgrade went smooth.  CPU is 64bit, but I've been running 32bit for convenience.  Everything from repos, except for wifi driver which comes from 32bit WinXP + ndiswrapper compiled from source.  Last I checked, lm-sensors doesn't support this motherboard.  Compiz (or perhaps it's Gutsy?) seems to make everything run faster (Openoffice writer starts much faster as well).  Main gripe: 2 special keyboard keys (QuickPlay) don't work - but all the rest do.  Otherwise, all is well.

---

### Post by dak0808 on 2007-11-25
Model: Compaq V3042AU
Processor:Turion64X2
Wireless Card: Broadcom
Graphics Card:Nvidia Go 6150
Gutsy : 7.10

It's no sound and Bluetooth.

---

### Post by skroops on 2007-11-26
Model: HP zd8000 (customized)
Processor: P4 3.0 Ghz
Wireless Card: Broadcom w/ Bluetooth
Graphics Card: ATI Mobility X600
Gutsy Tribe (Version): x86

I decided to install  zd8000 laptop. The dvd drive had stopped working a while ago, and I figured it wasn't long til my 3 year old windows install needed to be refreshed. So I figured I would start now with ubuntu so that I wouldn't have to worry about it any more. Well at first I had intended to dual-boot xp so that I could still play games, but my first attempt ended up screwing over my MBR and I just went with a full-on install.

I attempted to do an install via PXE with my Windows MCE maching hosting the TFTP server. This part was unproblematic. After getting the installer up and running, I directed it to an Apache server on the same machine to get to the alternate CD I had already downloaded. For some reason when I extracted the ISO(s) with WinRAR, they would sometimes lose part of their extensions (filename length issues I assume), but this was only on about 8 or 9 files, and I could correct them as the installer prompted me for them. Well this first attempt was reminiscent of my next 12 or so attempts.

The installation would go fine, and then when it hit the base system installation, at 82%, while installing the kernel, my PC would just shut off. I'm new to linux, (though I tried it about 10 years ago and gave up on it) and I thought maybe I was doing something wrong. After checking google searches and things like that, I eventually tried a variety of things, including the noacpi argument on the install, installing the server version, installing off the live mirror, and just trying again and praying. Nothing worked, almost every time it would shut off at 82%, (something about initramfs),  except a few times it shut off during the 70's, so I gave up on ubuntu and installed debian. Had no problems, everything worked perfectly, in respect to the installation atleast, so I knew it wasn't a problem with my PC.

Well I already had my mind on ubuntu and I really wanted to have it, so I decided for one last attempt I installed Feisty, this went through without a hitch. Then as soon as I started it up the first time, I just chose to upgrade to 7.10, and it went perfectly as well. I have no idea why I had such a difficult time getting Gutsy installed, but I hope it'll be worth it, and look forward to figuring everything out.  All in all about 10 hours to get it installed including research.

I tried wireless and it didn't work at all.  No error messages or anything, it just did nothing.  I'm going to research this more later, but I see I may need the unregistered drivers. 

Desktop effects work fine now that I installed the xserver-xgl package, and installed the unrestricted drivers.

Mute button and volume control buttons work fine, but the indicator lights don't do anything

---

### Post by groetz on 2007-11-27
HP Pavilion dv6140us Wide Screen w/Webcam
AMD Turion 64x2 TL-56
2 GB RAM
120 GB SATA Hard Drive
Nvidia GeForce Go 6150 Video
DVD/CD RW LightScribe drive
Broadcom 802.11B/G (94311) Network Adapter
 
Before I began, I connected an Ethernet cable. I installed Gutsy dual-boot w/XP. I used spare space to do a clean install, ie., format Ext 3 partitions before installing. At the first prompt, I entered "noapic nolapic", I answered the rest of the prompts as needed until the Restricted drivers prompt - I selected Restricted drivers for the Broadcom adapter and selected the one offered over the Internet. Everything proceeded as expected. After the initial boot, I updated as suggested. After that was finished, I dis-connected the Ethernet cable and set about setting up the wireless. I was able to get it to connect w/WPA-TKIP :) But when I shut down and restarted, wireless wouldn't connect. I'm not sure what I did then but I think I did more research and found good information @ [www.debianadmin.com/enable-wpa-wireless-access-point-in-ubuntu-linux.html](www.debianadmin.com/enable-wpa-wireless-access-point-in-ubuntu-linux.html). I followed the instructions and was able to successfully connect. Occasionally when I do a cold start there is no wireless - I just click the network symbol, select the appropriate network, and enter my password, if required.

Today there was no wireless - so I followed the above-referenced directions in that I did "sudo gedit /etc/network/interfaces" and commented all entries except those that refer to "lo". As soon as I saved the file, there was a dialog box asking for password, etc. That worked, as I am typing this on my laptop :)

However, I have a problem with this unit - since the wireless slider is on the front, I have accidentally moved it to the off position and then cursed because I lost connectivity :):)
All other features seem to operate as expected.

---

### Post by shark25 on 2007-11-27
HP Pavilion ZE4610US
15.0" XGA TFT (1024x768) display 
Mobile AMD Athlon XP-M 2500+ processor 1.87GHz
768 MB RAM
ATI MOBILITY RADEON 4X AGP

   I just installed a brand new 60 GB HD, which I split into a small (6 GB WinXP) partition and the rest dedicated to a linux distro. Even though I succeeded getting it to dual boot, the linux part leaves much to be desired. The linux distro I used was:

xubuntu-7.10-alternate-i386 (Gutsy)

but I can't seem to get anything to work (modem/dvd-drive etc.). I should preface this by saying that I have absolutely no experience with Linux, so I followed blindly the recommendations of the linux install disc. So far I've been unable to get the modem recognized in the Linux partition (works just fine in the WinXP part). I also tried to insert a commercial dvd, which also wasn't recognized. This leads me to believe that the driver(s) are missing, but how do I go about getting them when I can't even log on the internet when I'm booting up in xubuntu? I've read several posts mentioning that Gutsy has several issues with HP laptops and Feisty might be the way to go - is this true? And if so where would I be able to DL it from? (I checked the archive on xubuntu's homepage - but I weren't able to find it). Any advice would be much appreciated (f.ex. should I use a completely different distro?) - thanksin advance.

---

### Post by menace34 on 2007-11-28
Hey shark25, I've got the same laptop (my sister-in-law was going to throw it away), and I'm trying to get ubuntu going as well.  I'm going with ubuntu 7.10.  The LiveCD boots and seems to work ok, however once I do the install and reboot, the system hangs with the orange background.  Not sure what that is about, but I'll let you know if I get it working.

I would think anything that is in 7.04 would also be in 7.10, but I may be wrong about that.

---

### Post by Ayuthia on 2007-11-28
> **groetz said:**
> HP Pavilion dv6140us Wide Screen w/Webcam
AMD Turion 64x2 TL-56
2 GB RAM
120 GB SATA Hard Drive
Nvidia GeForce Go 6150 Video
DVD/CD RW LightScribe drive
Broadcom 802.11B/G (94311) Network Adapter
 
Today there was no wireless - so I followed the above-referenced directions in that I did "sudo gedit /etc/network/interfaces" and commented all entries except those that refer to "lo". As soon as I saved the file, there was a dialog box asking for password, etc. That worked, as I am typing this on my laptop :)

However, I have a problem with this unit - since the wireless slider is on the front, I have accidentally moved it to the off position and then cursed because I lost connectivity :):)
All other features seem to operate as expected.

Have you checked to see if the bcm43xx module is loaded (by typing lsmod in the Terminal) after rebooting?  If it is not there, you should add bcm43xx to /etc/modules and the module will get loaded whenever you reboot.

---

### Post by somegirl on 2007-11-29
Model:Compaq Presario V5304 (screen just says Presario V5000)
Processor:AMD Sempron (32-bit)
Wireless Card: Broadcom
Graphics Card:ATI Radeon Xpress 200M
Gutsy Tribe (Version): 7.10

I hope I'm not too late. I wanted to add some of my experience with my laptop.

When I initially booted from the live CD, it was using the wrong driver for the wireless card. Once I got it installed, a friend of mine helped with getting the right driver. I wish I could provide more details in that arena, but being new at this I sort of passively watched and have no idea how he found it, etc. 

Moving on, it's still using the wrong driver for the Radeon card, it's saying it's one type when it's another. It's a 3D acceleration card, so naturally I'm disappointed that it isn't being used (YET) to it's full capabilities. One of the main things I've noticed is not being able to use the desktop effects. EDIT: I got my graphics card working properly by going to System - Administration - Software Sources and then checking the box for Proprietary drivers, then go to System - Administration - Restricted Drivers Manager and checking the box for the Radeon card. While this properly installed the Xorg driver, I still couldn't use desktop effects because the fglrx driver won't run compiz (not sure if it will do the in the box system desktop effects), so I installed xgl. It works. It's pretty. I'm a happy camper.

Other than that, the thing runs like a dream. It smokes, because I've got 2gigs of RAM installed. Another issue I had was a slow boot up time, because I have XP on here. From what I understand it's a problem because windows is on the hard drive as well, but for reference I used this suggestion: [http://ubuntuforums.org/showthread.php?t=580903](http://ubuntuforums.org/showthread.php?t=580903) to fix the problem. This thread has two different fixes for the slow boot issue, the first worked for me. I clocked it, my laptop boots in 33.5 seconds, from the time I hit "return" after the GRUB loading thing until it gets to the login screen.

Anyway, I'll be working at this over the next couple months, learning things (sometimes the hard way) as I go. If there's other hardware specific stuff I'll be sure to add it here somewhere.

---

### Post by layzphil on 2007-11-30
Model: HP 6715b
Processor: Turion X2 2.0Ghz
Wireless Card:  Broadcom
Graphics Card: ATI Radeon X1270
Gutsy Tribe (Version): 7.04 (64 bit)

I had no luck with 7.10 install - couldn't even get to a command line, simply the bmc43xx wireless driver error over and over, so I tried 7.04. This gave the same error but it didn't completely halt the install.

X wouldn't start, but after I followed the instructions in [this](http://ubuntuforums.org/showpost.php?p=3479978&postcount=72) post I got the live install to work. Had to do it again after install. Now its up and running.

Sound works, USB works, the touchpad works. Wireless needs fixing but its mostly there.

Ok update - hope this helps others with this model.

Got the wireless finally working after hours of trying. This model has the BCM4312 wireless adapter rev 02. It wouldn't work with the sticked python installer, with the ndiswrapper or the firmware. I only got it to work following [these](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff) instructions. I used the firmware for the 4311 v2 for this and it finally worked.

---

### Post by wizardofyendor on 2007-11-30
I've got a Compaq Presario V6025 and I fought for hours getting gutsy installed.  I'm pretty experienced, and and distro that makes me use:
```
noapic nolapic noapci noirqpoll noirqdebug nosmp
```
just to boot the live CD is too much trouble.  I've been a feisty supporter since the begining, but this just isn't right.  I've finally got everything working, with the exception of video play back.  I'm using the 32 bit edition, and it doesn't matter which player I use (I've even tried VLC to make sure it's not my codecs) the video will play for only a few minutes then my whole computer locks up.

Oh and If I wish to reboot or shutdown, I click the [(|)] button and gnome locks up.  I have to hit alt+f2 to shutdown or reboot.

all in all disapointing.  I still looking for a viable solution before I just give up and go back to feisty.

---

### Post by enlightend1 on 2007-11-30
**Model:**Pavilion DV6308nr
**Processor:**AMD Turion64x2 TL-50
**Graphics:**Nvidia GeForceGo 6150
**Wireless Card:**Broadcom 4311
**OS:**Ubuntu Gutsy Gibbon 7.10 final AMD64

  After trying Fiesty I had a few problems getting my wireless to work then connecting to my router. Using envy, Feisty loaded my nviidia drivers and all was good until I tried some eye candy(Beryl). 

  I clean installed Gutsy and my wireless and video card were both there waiting for me in the restricted drivers folder. Compiz-Fusion works great. Firefox 32 is installed with java and    
flash support.

  Only issue is on boot up. I have to edit the boot line and erase the splash or it will not boot at all. However, my brother has a Dell Inspirion with XP Pro and the other night we had a reboot race. I shut down, started, edited the boot line ,logged in and got online while his XP was still "preparing to shut down windows".  So now he's considering making the switch(among many other reasons).

---

### Post by brunoscunha on 2007-12-01
Model: hp/compaq nx 7010
Processor:centrino
Wireless Card: iintel
Graphics Card:ati radeon mobility 9200
Gutsy Tribe (Version): 7.10
Boot Parameters:

Never could get the video card to work porperly. In fiesty the graphics card worked just great , and also lost the portguese keyboard layout over night.

---

### Post by HarleySteve on 2007-12-01
Model:Compaq Presario V2140US (screen just says Presario V2000)
Processor: Intel Centrino 1.5Ghz (32-bit)
Wireless Card: Intel 2200BG
Graphics Card: Intel 82852/82855GME
Gutsy Tribe (Version): 7.10

After much debate on trying Gutsy(I haven't used Linux since 2002,Suse).  I said what the heck.  At the same time I decided to install Ubuntu I replaced my 60 Gig Hard Drive with a 160gig drive.  I also upgraded memory from 512mb to 2048mb.System is a XP Dual Boot.  Grub installed to MBR. No extra commands used at boot time.

Bottom Line Up Front: Darn near everything worked right out of the box.

Graphics - Check
Wireless - Check(Using now to connect to AP with WPA-TKIP)
Compiz - Check(ALL The Bells and Whistles)
DVD - Check(Protected and otherwise)
Sound - Check
Grub - Check (Absolutely no problems with using installer to put this on MBR)
Slow Boot ups - Not Happening (24 Secs to boot, and 14 secs to shutdown, EVERYTIME)
Those seemed to be the main areas giving people fits.

Things I like:
Was able to setup Slingbox via Wine with the help of a VERY useful HOWTO from these forums.
Was able to automount NTFS shared folder without any problems


Only issues I have:
-  And I think just about everybody is having this one, is Suspend/Hibernate.  I can get the machine to Supend, but not wake properly.  Trying turning off Compiz, and it will wake, but freeze as soon as I turn on Compiz without rebooting.

- LinHDD doesn't work.  Installed package via Add/Remove Software.  It just shutsdown as soon as it opens.

- Small Annoyance, Desktop Drapes will only allow me to add new backgrounds once per boot.  For instance, I can turn on machine and import 10 Backgrounds.  If I close the application I will not be able to add any more until I reboot.  I and reproduce this at will.

- Slightly More Annoying, Gnome Appearance.  I just used the Appearance Applet to change the system font.  While the applet was open I could change the system font and anything else as much as I wanted to.  Once I closed it that first time, it has never allowed back to that part of the app to change fonts.  It just stays on the first tab of the applet that chooses themes.  Rebooting doesn't help.

-Had to apply Ugly Fix to slow down Load/Unload Cycle Count.  Brand New drive was over 5000 cycles within 2 days.  Applied fix and has been sane ever since.

Over all I am VERY happy with how far Linux Distro's have come over the last few years.  I would say that it is at a 90% solution for completely new users, that don't enjoy the challenge of learning a new operating system.

Thanks Ubuntu for a great Distro.

Steve

---

### Post by skinnie on 2007-12-02
Model:HP dv9575ep
Processor:Intel T7300
Wireless Card: Intel PRO/Wireless 3945ABG
Graphics Card: Nvidia 8600M GS
Gutsy Tribe (Version): Final

The final version of gutsy was perfect for me,no issues in installing it (alternate cd),no issues in grub (like tribe 5),all works like a charm,except one thing..my wireless card..
Let me explain,it works good,but @home with a buffalo WHR-G54S router,the connection sometimes falls,and can't reconnect..must restart ubuntu..in windows it doesn't happen (even if the signal is weaker)
any solution?

---

### Post by deep.tinker77 on 2007-12-05
Model: HP DV9500T
Processor: Intel Core2 T7500 @ 2.20GHz
Wireless Card: Intel 4965 AGN
Graphics Card: nVidia GeForce 8600 GM
Gutsy Tribe (Version): Final


Installation went without a hitch. I don't have an internet connection that i can use to update my graphic's driver and get the sound and wireless working yet, but when i do, i will update my post.

Update 07 Dec: Sound still not working, read and tried to apply the fixes that were mentioned here and still no joy, but I have wireless working and my graphics's are beautiful. If anyone has anymore suggestions on corrections for sound, please let me know.

---

### Post by firemagican2845 on 2007-12-05
Model: DV5029US
Processor: AMD Turion 64
Wireless Card: Broadcom BCM4318 [AirForce One 54g] 802.11g Wireless LAN
Graphics Card: ATI Radeon Xpress 200M
Gutsy Tribe (Version): Gutsy 7.10 Not sure on the build as I have no idea how to pull that info up.

OK well for the most part things worked well. Below will be a list of things I found work and don't work.

Wireless Card: No support for this card at all out of the box. I had to use the Ndiswrapper guide to get it up and running and even with that it "decides" when it wants to work at times.

Graphics Card: I can get it to work well enough to run Wine thats it. The 3D Graphics effects etc. do not work. Compiz fails every time it attempts to load. 

Gnome; I'm not a fan of it. I attempted to install the KDE Version of Ubuntu and couldn't even get ndiswrapper to work so I live with it.

Modem: Had to use the dell drivers to get the modem up and working. Other than that it works flawless.

Verizon Wireless Card: Worked just fine after I used the "modprobe airprime" command. So I'm happy there. 

Boot: When the computer starts I never see a splash screen past GRUB. I have to hit CTRL + Alt + F1 right after it starts to load up or it hangs in the ATI Black Screen of Death for hours. (Still working on this issue)

Wine: Wine works WELL. I was able to get WoW up and running among a few other pieces of software. 

Network Control: I don't care for it. It seems very differcult to use so I always do the commands in the terminal. It doesn't seem to support Ndiswrapper at all for the wireless (Or maybe I am doing something wrong who knows)

Battery Life; WAAAAAY better under Ubuntu than Windows XP. I can go about 2-3 hours on the Battery over about 45 minutes in XP. So thats a major plus

Overall I'd say it runs well. I'd give it a 6/10. (For Windows Xp it was a 1/10 so its a major improvement on my scale) I would like to see the ATI Driver issues sorted out. We don't really have a choice as to upgrading it as you can't swap a video card out in a laptop to my knowledge. Also I would like to see the wireless card issues sorted out. I think if they added Ndiswrapper support right off the bat instead of you having to track it down yourself things would be better.

---

### Post by wizardofyendor on 2007-12-05
> **skinnie said:**
> Model:HP dv9575ep
Processor:Intel T7300
Wireless Card: Intel PRO/Wireless 3945ABG
Graphics Card: Nvidia 8600M GS
Gutsy Tribe (Version): Final

The final version of gutsy was perfect for me,no issues in installing it (alternate cd),no issues in grub (like tribe 5),all works like a charm,except one thing..my wireless card..
Let me explain,it works good,but @home with a buffalo WHR-G54S router,the connection sometimes falls,and can't reconnect..must restart ubuntu..in windows it doesn't happen (even if the signal is weaker)
any solution?

Try using Wicd instead of network manager.  I was having the same problem using my feisty install, but wicd works like a charm.

[HTML]http://wicd.sourceforge.net/[/HTML]

---

### Post by lswest on 2007-12-07
Hey, i run gutsy on my hp laptop, no problems whatsoever after the initial driver troubles (propriety driver for broadcom didnt work, had to ndiswrapper the bcmwl5 drivers)

Model: HP Pavilion DV6545EG
Processor: AMD Turion 64 x2 Mobile TL-56 @ 1.8GHz
Wireless: Broadcom 43xx
Graphics Card: Nvidia MCP67M chipset, 64MB dedicated, up to 560MB shared
Release: Official Gutsy 7.10 release

---

### Post by sabrann on 2007-12-07
Model: HP Pavilion DV6000
Processor: intel centrino duo t7200 @ 2.GHz
Wireless: Broadcom: 
Graphics Card: Nvidia GeForce Go 7400
Release: Official Gutsy 7.10 release


I switched over to ubuntu last week and the only problem  I have had is with the Nvidia card and the problem that other's are having with it locking on bootup and acting stupid and a strange error that my battery is at only 35% but...i always plug it up via adapter anyway so i have ignored that error..... it loaded my vpn client with no trouble and picked up all other drivers no issue. 

the video thing is just a annoyance for me really, after working with vista and xp, i'm just glad that it runs fast as hell and is so stable :)

---

### Post by pndragon on 2007-12-07
> Try using Wicd instead of network manager.
Does Wicd support WEP with 64/128-bit hexdexicmal passkey encryption? I couldn't find any clear answers at the site and I don't really to install it without knowing.

---

### Post by icest0rm on 2007-12-07
hi guys...
i'm having a problem with my DV2699el (DV2500 series)...
frequency scaling it's not working, 
when doing a modprobe acpi-cpufreq it returns no such device...
so my CPU it's always running @ 2.2GHz and temps goes from 70 to 80°C and fan is always spinning...no-one with same probls?

---

### Post by wizardofyendor on 2007-12-07
> **pndragon said:**
> Does Wicd support WEP with 64/128-bit hexdexicmal passkey encryption? I couldn't find any clear answers at the site and I don't really to install it without knowing.

It supports everything your driver supports.  WPA-PSK, radius, WEP...

---

### Post by animesh_ea on 2007-12-09
I am planning 2 buy a laptop so could anyone temme if the following is compatible with ubuntu 7.10
Model: special edition HP Pavilion dv2600
Processor: Intel® Core™2 Duo processor T5250 1.50 GHz , Level 2 cache 2 MB, 667 MHz Bus speed 
Wireless Card: Intel® PRO/Wireless 3945 802.11a/b/g Integrated Wireless LAN
Graphics Card: NVIDIA® GeForce™ 8400M GS

---

### Post by lswest on 2007-12-09
install powernowd, might solve your CPU scaling issues, did for me

---

### Post by icest0rm on 2007-12-09
> **lswest said:**
> install powernowd, might solve your CPU scaling issues, did for me

no, same issues, can't detect cpu-scaling :(

---

### Post by jeromio on 2007-12-11
Model: Compaq Presario V6000
Processor: AMD64 dual core @ 1.7GHz
Wireless Card: Broadcom 4311
Graphics Card: nVidia GeForce Go
Gutsy Tribe (Version): Final

RAM = 1.5G

Multiple problems. 
With Kubuntu, video and sound worked. Compiz didn't work (and the Compiz settings manager displayed generic "tear off" icons for each element, rather than the normal individual icons?). Wireless did not work. System was very sluggish. Decided to start over with Ubuntu....

With Ubuntu, video only works at 800X600. Tried both open and proprietary drivers. Impossible to change (I can change w/ settings dialog, but the change is ignored). Sound works. Wireless does not work, even after enabling proprietary drivers. System is beyond sluggish - unusably slow. Everything takes eons - even opening windows or moving them around. No Compiz (obviously).

BTW, the LiveCD was fine. Video came up in native resolution. System was usable (no wireless though). First boot after install, there was a video error and I was asked to pick a resolutoin (which it ignored).

---

### Post by groetz on 2007-12-11
I have noticed another issue with this HP dv6140us w/Gutsy... Frequently the system will appear to halt - after a few seconds it will continue. The CPU portion of System Monitor will also freeze during this time, but then displays 100% CPU usage. Anyone have an idea?

---

### Post by groetz on 2007-12-11
> **Ayuthia said:**
> Have you checked to see if the bcm43xx module is loaded (by typing lsmod in the Terminal) after rebooting?  If it is not there, you should add bcm43xx to /etc/modules and the module will get loaded whenever you reboot.

I have now...:)
Thanks!!!

---

### Post by vishnuhari on 2007-12-12
Model:   Compaq Presario V3424AU
          Processor:  AMD Turion 64 , 2.21 GHz processor                
                             512 MB RAM, 
            Graphics:  NVIDIA GeForce Go 6150 graphics
            Chipset  :  NVIDIA Nforce chipset
            Wireless:   Broadcom Wireless Lan

I've a Compaq Presario V3424AU model laptop. its too difficult to install Ubuntu 7.1 into it. initially when i just followed the instructions in the graphical interface(start or install Ubuntu), the system freezes even before going on to the live desktop that we get. 

I just changed the boot option to "live acpi=off" and then i could proceed to install it.
(NOTE PLEASE: i don't know what that command is for, i just tried out what ever was given in the help menu and luckily, this one worked)

but it was not without problems. during start up, it shows a big list of errors and messages. Like....

   "PnPBIOS unable to get node information; Aborting"
   "reboot using pnpbios=off option"

   "dev_node_info unexpected status 0x37"
   "check with your vendor for an updated BIOS"

It doesnt end here. the usb mouse stops responding at times. even then the touchpad works fine. 

But anyhow, unlike Ubuntu 6.1, the advantage for 7.1 is that the display is perfectly OK. As for 6.1, the screen resolution was very low(as like in windows prior to the installation of the Driver software).
i tried many Nvidia-glx Drivers, but it didnt work. (If anyone knows the method to fix it, do inform me please)

And finally, there is the big problem of shutting down. it doesn't shut down and shows the following messages...

      "Network Manager:<WARN>nm_hal_deinit():libhal shutdown failed-connection is closed."
      "Network Manager:nm_dbus_signal_device_status_chang:assertion 'cb_data->data->dbas_    
                                                                                                                                   connection failed"   

What are all these thing? Can anyone please help me what to do........... Please..

---

### Post by dasbooter on 2007-12-12
Compaq Presario r4000 (variant)
# AMD Athlon 64 4000+ (2.4GHz/1MB L2 Cache)
# 128MB ATI Radeon Xpress 200M w/Hypermemory (chuckles, omg it has hypermemory, not chuckling mentally smacks HP's advertising copy writer in the head)
# 54g Integ. Broadcom 802.11b/g WLAN & Bluetooth 
Gutsy 7.10 official Desktop rls Wubi install [http://wubi-installer.org/devel/minefield/]("http://wubi-installer.org/devel/minefield/")
Restricted fglrx drivers via rest. driver manager

Problems:

Wireless. Used bcwcutter ala restricted driver process and network manager. Laptop can join my WPA encrypted network, ping the router etc. when using the roam mode (also sees 2 other networks in my area). Unfortunately my router is only an access point and is behind a linux computer which hooks to the internet. In roam mode the default gateway in this setup is wrong and also the default dns servers are wrong. Using manual entry with network manager did not help? Had to remove network manager and enter info with system-->administration-->network. Followed this tutorial 
[http://icebreaker.wordpress.com/2007/11/03/wireless-ubuntu-710-love/]("http://icebreaker.wordpress.com/2007/11/03/wireless-ubuntu-710-love/")

Slow boot no splash.Fixed slow boot with [http://ubuntuforums.org/showthread.php?t=580903&highlight=slow+boot]("http://ubuntuforums.org/showthread.php?t=580903&highlight=slow+boot")
but lost splash could maybe fix that too I suppose.

Absolute Show Stopper. Cannot get system to go into standby hibernate  or anything like that. These options are not even available in my shutdown menu nor are they available as an option when the battery gets low in the power manager. I am not having problems after suspending my laptop I cant even get the thing to go into standby. Closing the lid simply turns off the screen and I have heard that closing a running laptop is bad for cooling especially for these older less efficient processors. The standby option was not available b4 or after I installed the fglrx drivers via the restricted drivers manager. Some of my ills may stem from a Wubi install but I seem to be reading alot of similiar complaints on non wubi installs.

Thanks for reading. If you can solve my stdby problem let me know.

---

### Post by aescnt on 2007-12-12
Model: Compaq Presario V3532TU
Processor: Intel(R) Core(TM)2 Duo CPU     T7100  @ 1.80GHz
Wireless: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
Graphics: Intel GMA965
Gutsy version: 7.10

Everything works, EXCEPT:
 - Audio, which I had to fix by installing linux-backports-modules-generic and compile ALSA 1.0.15 from source.
 - Compiz-fusion (since GMA965 is blacklisted), but the simple SKIP_CHECKS fix works ([http://wiki.compiz-fusion.org/Hardware/Blacklist](http://wiki.compiz-fusion.org/Hardware/Blacklist)). After that, Compiz worked flawlessly, but video had to be set to X11 to work.
 - "Screens and graphics" preferences applet. I had to use xrandr via command line to get VGA output or dual monitors working.

---

### Post by longboarder on 2007-12-12
Back in October I tried to install 7.1 on my HP Pavilion dv6604nr and found that now my graphics worked, but my wifi didn't. It's a Broadcom 43xx. I couldn't get it to work. 

I went back to Feisty Fawn and installed the new driver that I found in ENVY. I ended up randomly pushing a button to try to look at the list of NVIDIA cards that driver supported because I couldn't see the buttons that went off the bottom of my screen. I accidently installed the driver. It put a new tool in the same menu that the driver was in so that I could actually change my screen from 800x600 to 1280x800. It took a trick or two to get the xorg.conf file written out. I ended up saving the old one, writing the new one to my home directory, then copying it to where the old one had been.

I hope this helps.

---

### Post by cframes1 on 2007-12-13
Model:v5108eu
Processor: AMD Sempron 1.8gHz
Wireless Card:broadcom air force one
Graphics Card:ATI Radeon express 200M
Gutsy Tribe (Version): 7.10

Fresh install did not work from live CD.  I had to install 7.04 FF and upgrade through the update manager.
Wireless card was dead at install but it eventually worked with some manipulation of the open source driver, got the info from here: [http://ubuntuforums.org/showthread.php?t=197102&highlight=presario+v5000](http://ubuntuforums.org/showthread.php?t=197102&highlight=presario+v5000)

CD/ DVD worked just fine, S-video TV out was dead until I went here:
[http://ubuntuforums.org/showthread.php?t=580748](http://ubuntuforums.org/showthread.php?t=580748)

Currently having problems getting the machine to wake up from standby mode.  Also won't wake up if I leave in screen lock mode too long.

The multimedia keys for the sound volume and mute that are above the keyboard worked great for a few weeks but now are dead, that's a project for next week.

---

### Post by 1tiger1 on 2007-12-17
**Computer:** Compaq 8510w (hp)
**Processor:** Centrino dual core 2.2ghz
**Ram:** 2gb
**Video Card:** Nvidia Quadro 570m

I had a little issue at first making it work with the docking station, but I got it to work great. I am running dual displays- one at 1920x1200 and the other at 1280x1024, but it only works in the docking station. If I try to boot to the laptop, I get nothing. (I got this to work using "sudo nvidia-settings" once I installed the restricted driver). 

runs great, lasts long time.

---

### Post by besada on 2007-12-17
> **1tiger1 said:**
> **Computer:** Compaq 8510w (hp)
**Processor:** Centrino dual core 2.2ghz
**Ram:** 2gb
**Video Card:** Nvidia Quadro 570m

I had a little issue at first making it work with the docking station, but I got it to work great. I am running dual displays- one at 1920x1200 and the other at 1280x1024, but it only works in the docking station. If I try to boot to the laptop, I get nothing. (I got this to work using "sudo nvidia-settings" once I installed the restricted driver). 

runs great, lasts long time.
I have the exact same laptop as you  8510w (hp), and it works both at the docking station and out of it.

I have included my xorg.conf in the following thread

[http://ubuntuforums.org/showthread.php?t=602806](http://ubuntuforums.org/showthread.php?t=602806)

I hope it helps

---

### Post by NineseveN on 2007-12-17
Here are two posts of mine from another thread like this on the forum ([http://ubuntuforums.org/showthread.php?t=582220](http://ubuntuforums.org/showthread.php?t=582220)), I figured I'd just copy and paste them into one post here:


> 
The 7.04 alternate CD installed fine on my dv6324us, but after the updates in the Update Manager, I couldn't boot into the new Kernel (just hung with a black screen no matter which boot options I tried). I had tried the live CD of 7.10 on it a few weeks ago and it worked great, so I installed 7.10 on it and now it's downloading the 7.10 updates.

I'm reasonably confident that I can get it working on 7.10 now after having gone through 7.10 with an ATi card and the restricted drivers fiasco on my desktop...we'll see though. So far, everything I tested worked (sound/audio playback, headphones, SD card reader, media controls-volume/mute/play etc...).

As long as the updates don't hose my laptop and my Broadcom card works as well with the Gutsy driver as it does for others, I can't see a reason to even think of going back to Feisty on this machine...but that seems to be a big "IF". I'm keeping my fingers crossed.


I don't even care if the Nvidia drivers work, it's mostly a work/internet laptop, but it looks like I should be able to get them working as well.


*hopes updates don't hose his system again*


> Okay, so an update.

The updates stalled when trying to start CUPS for some reason (though CUPS has been known to hang on my desktop as well so no big deal).

I had to force quit the updater after an hour of watching it sit there. When I logged back into Ubunutu, my window borders were gone (no close, minimize/maximize controls) and my terminal was solid white. After a quick search on these forums, I found out it's a Compiz bug/issue, all I needed to do was open the blank terminal and type "compiz" and hit enter. Totally solve the issue. The laptop has been running perfectly with 7.10, everything I need works and it even boots faster than my desktop machine.

Suspend locks the system, but this laptop doesn't need to use suspend anyway (though maybe there's a fix for it in 7.10 somewhere).

Overall, 7.10 was easier for me to install and it didn't get hosed like Feisty did. I was even able to use the Live CD for install and only had to add noapic irqpoll noirqdebug to get it to boot fully.

I'm still keeping an eye on it for issues, but so far, things are running great. USB works, sound works, wireless works, Nvidia card works with the right resolution and refresh rate. It's all good from here.

---

### Post by LinuxIsInnovation on 2007-12-17
Model:HP Compaq nx6320 [GA839PA]
Processor: Intel Core2 Duo T7200
Memory(RAM):4GB DDR2 
Graphics Card:Intel GMA950
Gutsy Tribe (Version): 7.10

---

### Post by Yves-Michel on 2007-12-17
Model: HP compaq 6715b
Processor: AMD Turion 64 X2 TL-60
Wireless Card: Broadcom Corporation BCM4312 802.11a/b/g (rev 02)
Graphics Card: ATI X1250 radeon
Gutsy Tribe (Version): 7.10 RC 64 desktop live
Boot Parameters: (none)

I did not have any issues during installation. However, as 4leite wrote, Wireless works only with ndiswrapper + bcmwl5 (do not worke with bcmwl6),  hibernation or suspend do not worke so far and also HP's fingerprint reader dose not worke till now. All other functions seems running fine, incl. VirtualBox.

---

### Post by Surfrock66 on 2007-12-17
Model: HP Pavillion dv6433cl
Processor: Dual Intel Centrino 1.73
Memory: 2GB
Version: Gutsy 7.10
Boot Params: (None)

Everything works great right off the bat (wireless, video, sound, card reader, burner, quick-play buttons, everything) except the webcam...kind of.  The webcam works in ekiga as a v4l2 device "USB 2.0 Camera" but in everything else (xsane, gimp, camorama) it gives me errors, particularly "/dev/video0" errors, which is a 0 byte file.

In "lsusb -v" it shows my camera as /dev/bus/usb/005/002 and calls it "USB 2.0 Camera" but I can't figure out how to make it work.  I uninstalled everything v4l (not v4l2) in synaptics, but still nothing works.  I'm kind of an ubuntu newb, but I'm savvy in general, and this is the one problem I can't seem to fix.

---

### Post by HeWhoE on 2007-12-20
Model: Compaq Presario C300
Processor: Intel Celeron M 430 @ 1.73GHz
Wireless Card: Broadcom BCM94311MCG wlan mini-PCI
Graphics Card: Intel Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller
Gutsy (Version): 2.6.22-14-generic

Issues:
During boot, I get a few BIOS errors.
> [    9.414446] PCI: Cannot allocate resource region 7 of bridge 0000:00:1c.0
[    9.414511] PCI: Cannot allocate resource region 8 of bridge 0000:00:1c.0
[    9.414573] PCI: Cannot allocate resource region 7 of bridge 0000:00:1c.2
[    9.414634] PCI: Cannot allocate resource region 8 of bridge 0000:00:1c.2
[    9.414727] PCI: Cannot allocate resource region 0 of bridge 0000:06:00.0

Running lspci gives me the following.
> 00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 01)
06:00.0 Network controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 01)
The driver loaded by default for my wireless device does not work.  I use ndiswrapper with the drivers provided by the hp website.

The time it takes from the GDM login to a usable desktop takes an annoyingly long time.

---

### Post by Boy With A Coin on 2007-12-20
hello to all, this is my first post in this forum.


I am new to linux and I am learning a lot, this is an amazing support community.

Model: Compaq Presario V2000
Processor: AMD Turion 64
Wireless Card: Broadcom BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
Graphics Card: ATI Radeon something
Gutsy Gibbon 7.10

My first major problem I an unable to resolve: My CPU fan is going almost always on, between 50-100% full speed. It did this every onece a while when XP would get tied up and the CPU was at like 90-100% capacity, but Linux isn't anywhere near that.


How do I regulate my fan/cpu power usage?


> **dinub1 said:**
> OK. Here:

Model: HP Pavilion ZE4145
Processor: AMD Athlon XP1800+
RAM: 512 MB PC2100 (266 MHz)
Wireless Card: D-Link AirPlus XtremeG DWL-G650 (works fine with Knetworkmanager)
Graphics Card: Bulit in ATI Radeon IGP 320M, 32 MB RAM
Gutsy Tribe (Version): Kubuntu/Ubuntu 7.10 beta
Kernel Options: Linux ubuntu 710 2.6.22-12-generic

Detailed description; Upgraded from Ubuntu 7.04. Upgrade went fine, After reboot CPU cooling fan worked continuously and CPU temp reached 65F. Couldnt regulate fan operation as CPU worked continously at full speed. Also CPU load was excessive. Close to 100% on idle. After checking forums and no tips worked, I decided to backup and erase the Linux partitions.However if I regulated the CPU frequency to go to "powersave" mode, temps dropped back to normal, however applictions ran slowly. Reinstalled Kubuntu 7.10 beta from scratch and added Ubuntu to it. Works like a KING and flawlessly now. Temps are normal, fan works internittently and CPU load at idle is only 5 -7%. CPU/Battery condition show now in system tray reporting CPU working in "dynamic" mode. It allocates power only when needed by applications. Othewise goes into powersave mode (662 MHz instead of 1523 MHz). Just as claimed by developers.

Some more... Sounds works now fine, before this, following the upgrade there was no sound. As far as I could see after reinstallation from scratch, Firefox and Opera browsers work fine, I attempted to install Seamonkey, downloaded latest version, couldn't install. Gives mea lib C++ library missing etc... cannot figure out why it doesnt. Attemting to repair using synaptic did not help. Running dual boot with Windows XP Home edition in different partition. After reinstall I needed to edit the /boot/grub/menu.lst file manually in order to enable GRUB hidden menus and added line for Windows XP. Also the NTFS partition needed reconfiguration. It woundt mount by default. Fixed it into the fstab. 
The reistall from scratch has been dome using the Kubuntu 7.10 beta I386 Live CD, alternative options, in text mode, Otherwise all fine.
Otherwise all work fine.

---

### Post by aree1987@gmail.com on 2007-12-20
I can`t change contrast and birghtness of my lcd panel ( I have hp dv4305us laptop). I've tried ddcontrol, but it doesnt recognize my lcd.
Please help!

---

### Post by drfox on 2007-12-22
HP dv9617
NVIDIA GeForce G 7150M
Broadcom 94311 WLAN

Installed Gutsy 64 and worked out of the box except for the WLAN. I used the restricted driver for NVIDIA. The restricted driver for the WLAN loaded, but didn't work. I uninstalled it and I had to use: 

[https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_(ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_(ndiswrapper)) 

to get the WLAN working. 


I'm very happy with this laptop.

---

### Post by DonDodge on 2007-12-22
Dumb question. Where does someone look to find their ubuntu tribe information?

---

### Post by drfox on 2007-12-23
> **DonDodge said:**
> Dumb question. Where does someone look to find their ubuntu tribe information?

Tribe refers/referred to pre-release (alpha) versions. You shouldn't be using a tribe version; you should be using 7.04 or 7.10.

HTH

Larry

---

### Post by sherirao on 2007-12-25
Model:Compaq Presario Media Center V6450EN Notebook PC (GS628EA#ABB)
Processor, operating system and memory
Processor type
	Intel® Core™ Duo processor T2450
• 2 GHz, Level 2 cache 2 MB
memory
	1024 MB
Internal drives

Internal hard disk drive
	160 GB
Hard disk controller
	SATA Hard Disk Drive

Network interface
	Ethernet 10/100BT integrated network interface

Wireless technologies
	Intel® Pro/Wireless 2200 802.11b/g Integrated Wireless LAN
Wireless capability
	Bluetooth® wireless networking

External I/O ports
	3 USB 2.0, 1 VGA port, 1 RJ11 modem connector, 1 RJ45 ethernet connector, S-video TV out, 1 Headphone-out, 1 mic-in, 1 IEEE 1394, remote control infrared port (remote optional), integrated stereo mic, cable docking connector
Video capture interface
	IEEE 1394 FireWire® Interface
Expansion slots
	One ExpressCard/54 slot (also supports ExpressCard/34)
Display size
	15.4” WXGA High Definition BrightView Widescreen
Display resolution
	1280 x 800
Video adapter
	Intel® Graphics Media Accelerator 950
Video RAM
	Up to 224 MB total available graphics memory
Speakers and microphone
	Altec Lansing® speakers
Keyboard
	101 key compatible keyboard
Pointing device
	Touch Pad with On/Off button and dedicated vertical and horizontal Scroll Up/Down pad, volume control, mute buttons, 1 Quick Launch Button
Power supply type
	65 W AC Power Adapter

I installed ubuntu 7.10 while i completely removed vista. only problem when i tried to compile new kernel . prob was with audio ALSA and Wireless drivers.

---

### Post by Jonathan Harford on 2007-12-25
Ubuntu 7.10 x86 Desktop on a...

[B]Compaq V5101US
Sempron 2 GHz
ATI RADEON XPRESS 200M IGP
Broadcom 4318 Wifi[/B]

The LiveCD works great, so I install. It's painless... but the first time I boot off GRUB, I get the messages:
```
PCI : Cannot allocate resource region 7 of bridge (and some hex codes)
PCI : Cannot allocate resource region 8 of bridge (and some hex codes)
```
...and the screen suddenly turns black. The hard drive light is ominously dark. Did it break? No, after a minute or two it starts to flicker. The login screen appears.

My first priority is to install the Broadcom restricted drivers so I can connect to my wifi router. This has been a major sticking point in past installs -- I've gotten it to work... kinda... but never for very long, and never like in WinXP, where I turn on the computer and it automatically connects to my router.

I click on the checkbox to enable the Broadcom driver, but **"The software source for the package bmc43xx-fwcutter is not enabled"**. This... is not... a very helpful error message. But a little ubuntuforums research tells me what boxes to tick in Add/Remove Programs. I plug in an ethernet cord and update, and then try to install again. This time I'm successful.

And now that I'm connected (wired, not yet via wifi), Ubuntu wants to update. This takes a while. When I hover over the Network Manager, I can see the twenty or so routers in my neighborhood! I don't unplug the ethernet, but it looks like I have wifi!

But then the update hangs when attempting to restart CUPS, of all things. The machine still works, but clicking the upper-right [x] of the package manager has no effect.

Reboot.

And now the black screen hanging is so bad I can't even get to the login screen.

Hard reboot.

I switch to Windows and see that there's been an update to my BIOS since last I checked (over a year ago). I flash my BIOS, and try booting into Linux again. Still getting the PCI errors and painful long dark waits.

More research suggests that adding **pci=noacpi** to GRUB might help. Indeed, it now boots lightning-fast, but I soon discover I again have no wi-fi. On a whim, I tell Ubuntu to stop using Restricted wi-fi drivers. It interprets this as a request to uninstall them. This is not intuitive behavior -- I'd thought it would just disable the driver! I plug my ethernet cable back into the side of the laptop and click the checkbox to reinstall, only to discover that wired ethernet doesn't even work!

Reboot.

I remove **pci=noacpi** from GRUB, as well as **quiet **and **splash **(which I should have done initially for the diagnostic info). But now when I boot, the PCI errors do not appear (or -- now that I think about it -- do they quickly scroll off the screen with all of the new information?) and I make it to the login screen in record time. I log in and try to connect to my wifi router and it works great! I don't know what happened, but I'm happy.

The V5101 has an ATI 200M, so the ATI restricted drivers should improve my performance, right? I install them and am told to reboot.

Reboot.

No noticeable difference, but that's okay.

Grrr. Network Manager doesn't remember my router's key, and there's no obvious way to tell it to remember it.

I use Automatix to install Flash, Java, DVD without (apparent) hitch. The machine is shaping up nicely.

Let's try that compiz thingy! I go to Preferences > Appearance Preferences > Visual Effects > Extra. A dialog pops up: "**The Composite extension is not available**". I click [OK], and nothing happens. Click click click. Only [X] has an effect.

After a wee bit more research, I edit xorg.conf:

```
Section "Extensions"
Option "Composite" "0"
EndSection
```

changes to:
```

Section "Extensions"
Option "Composite" "1"
EndSection
```

I log out and log back in to restart X. Now when I click "Extra" in "Visual Effects", I get a dialog that tells me "**Desktop effects could not be enabled**".  Never mind.

I load Firefox and go to YouTube to see how that Flash plugin works. What? No Flash? Okay, Firefox, go ahead and install it. Restart Firefox. What? No Flash? Okay, I'll uninstall it using Synaptics, then let Firefox install it. Nope, doesn't work. Finally, I get the tar.gz from Adobe and run its script, pointing it at /usr/lib/firefox. Hey! Dramatic Chipmunk!

I use the laptop as my TV's DVD player already and would like to do the same via Ubuntu. I plug a VGA cable from my laptop (1280x800) into my Olevia HDTV (1366x768). Rather than extending the desktop, it clones it, but such that the parts of the screen get cut off. I take a look at the "Screens" settings, and there is a place to describe my monitor. No Olevia drivers, but I can declare my monitor to be an LCD with a resolution of 1360x768. Even after I do that, I'm only allowed to have a maximum resolution of 1024x768. Gah.

Let's see what ubuntuforums says... ah! There are four different hacks one can do to one's X server to get desktop extension. I mean... seriously? I'd rate desktop extension along the lines of USB drive mounting -- I'd expect it to Just Work, y'know?

I give Big Desktop one attempt. Both screens go wonky. I reset xorg.conf, and go back on the internet to find other possible solutions...

But I can't connect to any sites. Sure, I'm connected to the router, and my desktop (going through the same router) is connecting to the internet fine -- but I can't connect to even Google! But I haven't done anything that should alter my wi-fi!

I give up. I swear, I've been trying to install Linux for ten years.

---

### Post by ulver on 2007-12-26
Bought a HP Compaq 6820s yesterday and immidiately installed gusty on it.
Most things work out of the box, except for the graphics card ati x1250, tried the restricted driver, the amd ati driver, nothing seems to enable the card to use compiz :/
Because the downloaded driver didnt work tried to revert to fglxr but the display stayed slow, showing only a few fps. Got the old xorg.conf back, reinstalled the restricted driver but the same story again. 
Here is my xorg.conf;
> # xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"hr"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/mice"
	Option		"Protocol"	"ImPS/2"
	Option		"ZAxisMapping"	"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"	"/dev/psaux"
	Option		"Protocol"	"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"stylus"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"eraser"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"cursor"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"ATI Technologies Inc ATI Default Card"
	Driver		"fglrx"
	Busid		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	Horizsync	30-70
	Vertrefresh	50-160
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc ATI Default Card"
	Monitor		"Generic Monitor"
	Defaultdepth	24
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
	
	# Uncomment if you have a wacom tablet
	#	InputDevice     "stylus"	"SendCoreEvents"
	#	InputDevice     "cursor"	"SendCoreEvents"
	#	InputDevice     "eraser"	"SendCoreEvents"
	Inputdevice	"Synaptics Touchpad"
EndSection
Section "Module"
	Load		"glx"
EndSection
Section "Extensions"
	Option		"Composite"	"0"
EndSection

And my lspci;
> 00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 0c)
00:19.0 Ethernet controller: Intel Corporation 82562GT 10/100 Network Connection (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Contoller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
01:00.0 VGA compatible controller: ATI Technologies Inc Unknown device 7196
10:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)


The card is x1250 but it shows as an unkown device 7196 :S

Please help because I cant even browse like this :(

---

### Post by Cavalryman on 2007-12-26
The *very* first thing to do with a new HP computer is to make the "resore" disks. That way, if anything goes wrong, you can put it back to factory configuration.

I just installed Gutsy Gibbon on a brand-new HP Pavilion 2660es which came with Vista. I wasn't brave enough to completely eliminate Vista because I use the computer for work and I was afraid I might run into some compatibility issues with other people's documents. Initially, I did a standard dual-boot install via the live CD, but then whenever I tried to boot Vista, it told me that one of my disks needed to be "checked for consistency" and tried to do disk checking on the Ubuntu partition. I had to partition the disk, do a clean install of Vista on the first partition, then reinstall Ubuntu on the second partition. Since I have a 250 GB hard drive, I have plenty of room on both partitions. It runs fine now. Ubuntu identified all my hardware and installed drivers. Even the little remote control works!

---

### Post by anvo on 2007-12-27
**Model:**  G5055EA
**Processor:**  Core 2 Duo T2080 @ 1.73GHz
**Wireless Card:**  Broadcom BCM94311wlan mini-PCI
**Graphics Card:**  Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller
**Gutsy Tribe (Version):**  32-bit
**Boot Parameters:**  nothing special.

Surpisingly, BCM94311 is working from the very moment I installed G.G.  Sound and sound buttons are OK, only the touchpad (Synaptics) is kind of annoying and I'll start searching to configure the Fn combinations...!

  Greetings,
  George.

---

### Post by anvo on 2007-12-28
> **Jonathan Harford said:**
> Ubuntu 7.10 x86 Desktop on a...

```
PCI : Cannot allocate resource region 7 of bridge (and some hex codes)
PCI : Cannot allocate resource region 8 of bridge (and some hex codes)
```

  I get the same messages, but I already have installed Gutsy and the system works OK, though!


> I give up. I swear, I've been trying to install Linux for ten years.

  Me too, I'm still finding the hard way to Linux for ten or more years!  I do not give up simply because I hate proprietary OS's!!!

---

### Post by TheAxeR on 2007-12-28
**Model: **dv2500t
**Processor:** Core 2 Duo T5250 @ 1.5 GHz
**Wireless Card:** Intel PRO/Wireless 3945ABG
**Graphics Card:** Intel Mobile GM965/GL960 Integrated Graphics Controller
**Gutsy:** Final Release
**Boot Parameters: **nothing special.

Everything worked out of the box except for sound.  I have an Intel 82801H (ICH8 Family) HD Audio Controller.  However, with some searching that was easily fixed by installing 

> linux-backports-modules-generic

I found this on this site [http://linuxtechie.wordpress.com/2007/10/19/getting-intel-ich8-family-rev-3-sound-card-to-work-in-gutsy/]("http://linuxtechie.wordpress.com/2007/10/19/getting-intel-ich8-family-rev-3-sound-card-to-work-in-gutsy/").

---

### Post by mmichalik on 2007-12-28
I bought a Compaq Presario C700T about 2 weeks ago and installed 7.10 on it the moment it came out of the box.

Everything worked great except for the Broadcom BCM94311MCG WLAN MINI PCI wireless network card.

I found this website:

[http://invaleed.wordpress.com/2007/11/20/install-bcm94311mcg-wlan-mini-pci-ubuntu-710/](http://invaleed.wordpress.com/2007/11/20/install-bcm94311mcg-wlan-mini-pci-ubuntu-710/) 

It helped me set up the wireless in less then 30 minutes and the laptop has been solid ever since.

---

### Post by seandee on 2007-12-29
**Model**: Presario R3000Z
**Processor:** AMD Athlon 64
**Memory:** 1.2 GB
**Graphics:** Nvidia Geforce4 440 Go
**Wireless:** Broadcom BCM4306
**OS:** Ubuntu Gutsy

So far install works fine but:
1. Wireless Card had issues, so I removed disabled restricted driver and used    Ndiswrapper with Broadcom XP drivers. Works great
2. Video card works, but I get black windows with desktop effects enabled, and large number of windows open.
3. SD card - no attempt has been made to configure, though i will try in future.

---

### Post by Dynaflow on 2007-12-30
**Model:** Compaq Presario C706NR (C700 series)
**Processor:** Celeron M 530, 1.73 GHz
**Wireless Card:** BCM94311MCG wlan mini-PCI
**Graphics Card:** Intel Graphics Media Accelerator X3100 
**Gutsy Tribe (Version):** 7.10 Final

This thing was a godawful beast ... and I did two of them.  Using the Restricted Drivers Manager to bring the Broadcom wifi card to life didn't work, so I ended up using [these instructions]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff") to get the driver working with ndiswrapper.

Sound sort of worked out of the box, but fancy, extra frills, like having the speakers mute when headphones were plugged in, required compiling the latest version of ALSA.  I did it the lazy man's way and used the script I found [here]("http://www.antonywilliams.com/2007/10/bash-script-to-automate-compiling-alsa.html").

By the time I had gotten those fixes in, the SATA hard drive had already racked up a load-cycle count into the thousands, due to the drive's aggressive power management and its apparent propensity to self-destruct when either running a journaling file system, not running Windows, or both (the [jury still seems to be out]("https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/59695")).  I applied Ubuntudemon's ["Ugly Fix"]("http://ubuntuforums.org/showpost.php?p=3675960&postcount=26"), uninstalled Tracker, installed the latest, Debian version of [Laptop Mode Tools]("http://samwel.tk/laptop_mode/packages/debian") and enabled laptop mode by editing /etc/default/acpi-support to get that under control.  

Suspend and Hibernate work beautifully, and problems only arise if you try to wake the computer up.
-------------------
[EDIT:] I found the solution to the above [here]("http://ubuntuforums.org/showthread.php?t=471855").  Do this:

```
sudo apt-get install uswsusp
```

```
sudo gedit /usr/lib/hal/scripts/linux/hal-system-power-suspend-linux
```

Replace everything in the file that opens with 

```
#!/bin/sh

/sbin/s2both
```

Save.  Then, 

```
sudo gedit /usr/lib/hal/scripts/linux/hal-system-power-hibernate-linux
```

and replace everything in *that* file with 

```
#!/bin/sh

/sbin/s2disk
```

Save the file.
-----------------------
I can't, for the life of me, get graphics acceleration going enough to run Compiz, but at least the computer is functional now and not in immanent danger of hard-drive suicide.  (EDIT: The graphics problem seems to be the result of the current driver for the Intel graphics hardware being so abysmally bad that the Compiz people felt the need to specifically blacklist it.  I've seen some posts floating around about how to take the card off the blacklist and get Compiz running, but you apparently do so at the cost of your video playback, so no thank you.  Supposedly a fix has already been made, and it's slated for release with Hardy Heron in a few months.  Let's hope for a backport.)

Oh yes, there is one other little issue that I haven't been able to resolve (besides the winmodem -- don't get me started on that).  Since I set up the laptop to dual-boot between Gutsy and its original Windows Vista (I end up needing to see how things look in Windows from time to time), the need occasionally arises to reboot from Windows to get into Linux, via GRUB.  If I do not do a complete, power-off shutdown of Windows before booting Gutsy, I will have control of the keyboard and touchpad in GRUB and the GDM log-in screen, but once GNOME starts, they will become totally unresponsive, and the laptop will require a hard power-off in order to unlock itself.  That bizarre problem is reliably reproducible on both of the C706NRs I Linuxed-out by booting or rebooting into Windows Vista, rebooting into Gutsy, and logging into GNOME, and I'm presuming it's some sort of issue specific to some component or another of this particular model.

---

### Post by EXCiD3 on 2007-12-31
I would like to let everyone know that the Zen Kernel fixes important bugs related to the AMD based HP Laptops. I strongly encourage anyone interested in fixing these problems take a look at the Zen Kernel here: [http://ubuntuforums.org/showthread.php?t=623874](http://ubuntuforums.org/showthread.php?t=623874)

[B]Important Information: 
[/B]-Kernel fix for the nolapic issue...it's a patch that disables C1E on AMD machines, which is causing the kernel to incorrectly report lapic is broken. This allows us (with newer custom kernels like zen) to use High Res Timers and Dynamic Ticks. 
 
On kernels without this patch, reported to work on the dv9205us, without disabling lapic (even though it is broken without C1E disabled):
```
noisapnp iommu=off noirqdebug noapic pci=assign-busses
```
 The patch can be found here (may have to mod it to work depending on which kernel source you are using):
 [http://tinyurl.com/ytyhfe](http://tinyurl.com/ytyhfe)
 
This fix allows you to boot without using nolapic, fully enabling nolapic. If you have a kernel like Zen, you can use the features Dynamic Ticks and High Resolution timers, which should increase both speed and battery life. The boot parameters I posted allow you to do the same with older kernels without patching, without high resolution timers and dynamic ticks, as they are experimental features added in the newest bleeding edge kernels.

Much thanks to ilikenwf, Official Zen Kernel Maintainer!!!

---

### Post by motin on 2008-01-02
I hope you guys all can spend a minute or two and update the wiki on HP laptops: 
[SIZE="4"][https://wiki.ubuntu.com/LaptopTestingTeam/HewlettPackard](https://wiki.ubuntu.com/LaptopTestingTeam/HewlettPackard)[/SIZE]

I have added a Pavilion DV4000 Series laptop ( DV4268 ): [https://wiki.ubuntu.com/LaptopTestingTeam/HPDV4000](https://wiki.ubuntu.com/LaptopTestingTeam/HPDV4000)

General Info:
[https://wiki.ubuntu.com/LaptopTesting](https://wiki.ubuntu.com/LaptopTesting)

---

### Post by EXCiD3 on 2008-01-02
Hey thanks. I would like to encourage everyone also to update the wiki. I havent had the time/willingness to play with Gutsy and will post my DV9000 on the wiki as soon as i get the chance.

---

### Post by RyanKage on 2008-01-02
Model: Compaq Presario X1000
Processor: 1.3GHz single core Intel m
Wireless Card: (not sure...)
Graphics Card: Radeon 9200
Gutsy: 7.10

Yes, I know this is a very old laptop but my buddy gave it to me for only $50.00 for me to use at college since I can't afford a laptop right now :(. So far everything works. Boot time is incredibly slow... But it only has 512MB of ram and a 1.3GHz single core processor, so that's fine. Miro has been giving me problems with crashing... That could be just Miro and not Ubuntu, I'm not sure. It's kind of funny but I have a similarly old desktop like the Compaq, but I built it myself and both have wireless cards and surprisingly the laptop gets 96-100% all the time and yet my desktop stays at a measly 34-45% and it's about 3 feet away from the wall... Anyways, the X1000 is all-in-all a good Linux laptop. I just wish the boot time was just a tad bit faster.. Maybe 1-2 minutes faster? Lol. Ah well, it was only $50.00 so I'm happy :).

---

### Post by EXCiD3 on 2008-01-02
RyanKage, try something like this tutorial to speed up your boot: [http://kmandla.wordpress.com/2007/04/22/howto-set-up-feisty-for-speed/](http://kmandla.wordpress.com/2007/04/22/howto-set-up-feisty-for-speed/)
This was written for Feisty, however some of the things still apply in Gutsy. I successfully got my boot to ~25 seconds using this guide on Feisty.

---

### Post by Sproid on 2008-01-02
Model: HP Compaq 6710b laptop
Processor: Intel Core 2 Duo Processor T7100 (1.80-GHz)
Wireless Card: 802.11a/b/g Wireless
Graphics Card: Intel Graphics Media Accelerator X3100
Gutsy Tribe (Version): 7.10 Final x64

Almost all work fine. Got problems with compiz, but solve installing xserver-xgl ([http://ubuntuforums.org/showthread.php?t=529087&page=3)(it](http://ubuntuforums.org/showthread.php?t=529087&page=3)(it) happened in my desktop clone too), other problem is it freeze/crash most time closing the lid (still looking for a solution) and when playing with the screen saver most or full screen videos.I had to install libdvdread3 to play original dvds movies ([https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs?highlight=%28dvd%29).I](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs?highlight=%28dvd%29).I) have to mention I am dual booting with vista business which it su**s but it run my windows games, limewire and nero 8 suite. Hope my info is useful.

---

### Post by cdtech on 2008-01-02
**Model:** dv9608nr
**Processor:** 1.9 GHz AMD Turion 64 X2 Dual-Core Mobile Technology TL-58
**Wireless Card:** Broadcom BCM94311MCG wlan
**Graphics Card:** NVIDIA GeForce Go 7150M (UMA)
**Gutsy Tribe (Version):** 64 bit 7.10 final
**Boot Parameters:** none

Other than blacklisting the original wlan driver supplied with the kernel (echo 'blacklist bcm43xx' | sudo tee -a /etc/modprobe.d/blacklist), the wlan was fairly straight forward. Using the restricted drivers manager and using nidswrapper helped enable my wlan (don't forget to setup the interfaces file with your iface settings) such as I did here:

iface wlan0 inet dhcp
wireless-essid **XXXXXXX**
wireless-key **XXXXXXXXXX**
auto wlan0

Still in the process of testing everything but so far so good. I'm running a dual boot system with Windows Vista (two separate hard drives). I wanted full control over both through Bios selection.

All quick launch buttons work great.

---

### Post by RyanKage on 2008-01-02
Cool, I'll give it a try. I'll give you a quick post if it works :). Thanks again.

---

### Post by tpls on 2008-01-02
Is there anyone who is facing the same problem as i do in dv6059ea? If anything usb device is plugged in while i boot up my laptop, they all are working great (for example usb mouse and memorystick). But if i unplug them and plug again Gutsy doesn't detect any usb device at all. It detects them only in boot. What could be wrong? Thanks for help in advance.

---

### Post by ArcticD00d on 2008-01-02
[B]Model:dv2500t
Processor:Intel Core 2 Duo T7500 2.2 Ghz
Wireless Card: Intel Pro/Wireless 3945
Graphics Card:Nvidia 8400M GS
Gutsy Tribe (Version): whatever current release is
Boot Parameters:none[/B]

Overall I'm pretty happy I went with Gutsy instead of Feisty... it seems there's been many bugfixes released for it. The only problems I have with this laptop are dimming the screen automatically (the Fn keys work), sound after a windows boot, and suspend (works once, maybe twice per boot, then just goes to a blank screen). 

If anybody has solutions for the above that I've missed looking around the forums, let me know.

---

### Post by fenixartzz on 2008-01-02
Model:dv6500t
Processor:Intel Core 2 Duo T7500 2.2 Ghz
Wireless Card:4965 AGN
Graphics Card:Nvidia 8400M GS
Gutsy Tribe (Version): whatever current release is
Boot Parameters:none

It did work better then  any of my previous experiences with linux
Just had issue getting sound and video drivers, sound had to install backdrop support and nvidia drivers are working now 
managed to get few apps running in wine too so very much everything is normal

---

### Post by phidia on 2008-01-04
Product Name    	 dv6604nr
processor 	1.8 GHz AMD Athlon 64 X2 Dual-Core Mobile Technology TK-55
Memory 	1024 MB DDR2 (2 Dimm)
Video Graphics 	NVIDIA GeForce Go 7150M (UMA)
Video Memory 	Up to 287MB
Hard Drive 	160 GB (5400 RPM) (SATA)
Multimedia Drive 	Super Multi 8X DVD±R/RW with Double Layer Support
Display 	15.4" WXGA High-Definition BrightView Widescreen (1280 x 800)

I installed gutsy on this but although I could enable the propritary nvidia driver (also the wifi broadcom) the video would fail-the screen turns grainy and totally unusable after a few minutes.. I'm not sure if it's a hardware issue or not. This thing has been a real pain. I'm waiting for the restore discs from HP to see what those will show.

---

### Post by phelge on 2008-01-05
Product Name : 8710w
processor : Core 2 Duo T7700 2.4 Ghz
Memory 2048 MB DDR2 (1 Dimm)
Video Graphics NVIDIA Quadro FX1600M (equiv : 8700GT)
Video Memory : 512M
Hard Drive 200 GB (7200 RPM) (SATA)
Multimedia Drive Super Multi DVD±R/RW with Double Layer Support Lightscribe
Display 17.0" WUXGA AntiGlare (1920 x 1200)

I've installed Gutsy and almost everything is ok : wireless, usb, sound, display, nvidia driver 169.07. Compiz performs quite poorly, but I've added the hack indicated here  : [http://www.nvnews.net/vbulletin/showthread.php?t=99554&highlight=performance](http://www.nvnews.net/vbulletin/showthread.php?t=99554&highlight=performance)
and it's much better.
The SD Card reader will not work. Probably there are some setpci hacks to do, but nothing that I read works : lspci | grep Ricoh returns :
02:06.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev b9)
02:06.1 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev b9)
02:06.2 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 03)
02:06.3 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 20)
02:06.4 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 10)
02:06.5 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 10)
02:06.6 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 10)
if someone has success with the same, please tell me. Thanks.
I didn't try yet suspend and hibernate.

---

### Post by Upper on 2008-01-05
[B]Modell:[/B Compaq Presario R3000
**Processor:**] AMD 64 Athlon
**Wireless Card:** Broadcom 802.11 b/g
**Graphics Card:** NVIDIA GE Force4 440 GO 64M
**Gutsy Version:** 7.10
**Boot:** CD Image

Have not gotten past boot.  Video goes bonkers and displays a series of light gray slaches on a black background.:(

System is two years old, and a good candidate to evaluate OSs.:)

---

### Post by sergiom99 on 2008-01-05
**Product Name : HP DV 6646us**
processor : 1.9 GHz **AMD** Turion 64 X2 Dual-Core Mobile Technology TL-58
Memory 2Gb
Video Graphics **NVIDIA** GeForce Go 7150M (UMA)
Video Memory : Up to 559MB
Hard Drive 160 GB (5400 RPM) (SATA)
Multimedia Drive Super Multi DVD±R/RW with Double Layer Support Lightscribe
Display 15.4"
**BroadCom** BCM4328 wireless
(more: [http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01163905&lc=en&cc=us&dlc=en&product=3552675&rule=44703&lang=en#](http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01163905&lc=en&cc=us&dlc=en&product=3552675&rule=44703&lang=en#))


I got my DV6646us working without any problems. I used the Kubuntu Gutsy 32bit alternate CD and the followed some of the instructions from this excellent post:
[http://ubuntuforums.org/showthread.php?t=575750](http://ubuntuforums.org/showthread.php?t=575750)
(make sure to read the whole post... always)
and now works like a charm sound, video, wireless, etc.

---

### Post by compaqui on 2008-01-06
Model: Compaq presario v3217LA
proccesor: amd mobile sempron
graphic card: Nvidia GEforce go 6150
wireless card:Broadcom bcmxx
Ram:512 MB

it hangs up in text mode installation i cannot even get to the partiton menu it hangs up in 11% when reading cd rom. i checked my cd for defects and it hanged too. i checked in another computer and the cd was perfect BIOS is up to date im trying to install gutsy gibbon 7.10 but i cant plz someone help me.:(    i wont buy another notebook maybe i should try with dapper drake.

---

### Post by simon_ives on 2008-01-07
**Model**: Compaq Presario V3118AU
**Proccesor**: AMD Turion X86_64 Dual Core
**Graphic Card**: Nvidia GEforce 
**Wireless Card**:Broadcom
**Ram**: 512 MB

I've installed the 64bit version of Gutsy and everything seems to be working fine out of the box.

Wireless and Graphics work with no issues using the restricted drivers and the sound works with no configuration...even the headphone switch works (shuts off the main speakers) without any configuration, something that was needed in Feisty.

The CD/DVD drive works well along with all the USB ports, Firewire port, Memory Card ports, Ethernet port etc.  The touchpad functions well as do the S-Video and Monitor outputs.  The monitor is properly recognized as a wide-screen, even with the NV driver.

I am yet to test the dialup modem (didn't function in Feisty with the sound enabled) nor the expansion port.

I dual boot with Windows XP Home which seems to cause no problems.  My 60Gig hard drive has two equal partitions of which Windows XP Home is on the first.

My Windows XP Home partition is recognized by Gutsy and so is my Wife's computer running Windows XP Professional which functions as a kind of file server.  My Gutsy install is recognized on the home network and I can access all of the media stored on the 'file server'.  Rhythmbox even has it's library set to the networked Windows XP Professional 'My Music' folder and functions well.

Thanks Ubuntu for a great release!

---

### Post by EvilRick on 2008-01-07
Model: nc8000
Processor: Intel Pentium-M 2GHz
Wireless Card: Intel Pro Wireless 2200BG
Graphics Card: ATi Radeon Mobility 9600 M10 (RV350)
Gutsy Tribe (Version): 7.10

Everything seems to work fine.

- The blue LED for the wireless doesn't work.  It worked fine in Fiesty.

EDIT - I just reloaded 7.04 back on and now the wireless LED doesn't work after software updates.  Go figure.

---

### Post by Greg T. on 2008-01-07
**Model:** Compaq Presario F730US
**Proccesor:** AMD Athlon 64 X2 - TK-55
**Graphic Card:** Nvidia Geforce GO 6100
**Wireless Card:** Broadcom
**Ram:**1024 MB

I installed Hoary on this as a Christmas gift for my parents. Two weeks in, all's well. Quirks:

[LIST]
[*] I had to compile the latest version of ndiswrapper for wireless to work properly. The .deb version I tried didn't do the trick.
[*] wicd may work better with this laptop than nm-applet. YMMV.
[*] If I dual boot into Vista, I have to power down completely and remove the battery (!) for sound to work when returning to Ubuntu
[*] Running Compiz caused problems with suspend (aside from "sync to vblank" issues); I had to go with Metacity
[*] I have to use "acpi_sci=level" to get suspend to work properly; at least one other has used "noapic" with good results on Gutsy (at a minimum, it seems needed as a boot parameter for installation)
[/LIST]

There's a separate thread just on this laptop: [http://ubuntuforums.org/showthread.php?t=643195](http://ubuntuforums.org/showthread.php?t=643195)

---

### Post by kedar.bhave on 2008-01-08
> **EXCiD3 said:**
> Yeah, I'm not too sure about Gutsy's status on wireless support. My intel 3945 drivers claim they are correct, they detect wireless connections however they cant actually connect. 


Has this been fixed yet? I have the same problem, I can detect wireless connections but can't connect, even if I give a manual wireless configuration.

---

### Post by EXCiD3 on 2008-01-08
This is fixed with the final release. As noted I was using a prerelease of Gutsy that had broken intel3945 drivers. It was fixed for the final release and should work just fine. What exactly is the problem with your wireless?

---

### Post by slayer^_^ on 2008-01-09
i've posted my experience on installing Ubuntu **7.10** Gutsy Gibbon on a **HP Compaq 6720S** here:

[HTML]http://ubuntuforums.org/showthread.php?t=659027[/HTML]

i've found issues with the video card, the ethernet and wi-fi device.

hope it helps someone.

---

### Post by kedar.bhave on 2008-01-09
> **EXCiD3 said:**
> This is fixed with the final release. As noted I was using a prerelease of Gutsy that had broken intel3945 drivers. It was fixed for the final release and should work just fine. What exactly is the problem with your wireless?

The restricted drivers section tells me that the Intel 3945ABG driver is enabled. When I search for available networks, it shows me the list but when I try to connect to a network, it keep on trying and finally fails after around 4-5 minutes.
I tried giving a manual configuration, but there is no option to connect to an unsecured network.

---

### Post by EXCiD3 on 2008-01-09
Do you know if it is a problem with the network? Theoretically there shouldnt be any problems with the Intel driver.

---

### Post by kedar.bhave on 2008-01-09
There is no problem with the network, I can connect to it from Windows just fine. I will try installing the development version of the driver (if there is one) later today and post the results.

---

### Post by EXCiD3 on 2008-01-09
Hmmm interesting. Reinstalling the driver might do the trick. Post your ouput of ```
[SIZE=-1]lshw -C network
```

Also I would like everyone to know that I have created a new thread for testing Hardy 8.04 prerelease on HP and Compaq laptops. If you have tried or are going to try out a prerelease of Hardy, please post any information you have here: [http://ubuntuforums.org/showthread.php?t=660384](http://ubuntuforums.org/showthread.php?t=660384)
 [/SIZE]

---

### Post by jkyamog on 2008-01-09
**Model:** HP 6910p[B]
Processor:[/B] Intel T7700
**Wireless Card:** Intel 4965
**Graphics Card:** Radeon X2300
**Gutsy:** 7.10

Some of the hardware would not work out of box, I needed to upgrade and/or fix.  Most notably the wireless and video card.  I written a [short write up]("http://jkyamog.blogspot.com/2007/12/linux-install-on-hp-6910p-using-ubuntu.html") on what I did to make the laptop run on Gutsy.

**Model:** HP Pavilion dv6000[B]
Processor:[/B] Intel T7400
**Wireless Card:** Broadcom 1390
**Graphics Card:** Nvidia 7400 go
**Gutsy:** 7.10

Laptop works pretty well.  wireless is crippled only runs at 802.11b speed.  Hibernate will not work if binary nvidia is used.

---

### Post by kedar.bhave on 2008-01-11
> **EXCiD3 said:**
> This is fixed with the final release. As noted I was using a prerelease of Gutsy that had broken intel3945 drivers. It was fixed for the final release and should work just fine. What exactly is the problem with your wireless?

It seems I can login to secured networks, but I cannot login to unsecured networks using automatic configuration. I did not see an option for unsecured networks in manual configuration too.

---

### Post by pablosanchezuy on 2008-01-11
To Ulver :

I also have a 6820, almost everything works fine, except that the daamit driver (7.11) 
keeps me from suspending to ram and to disk. 

When i have some time, i will move to 7.12 .

Pablo .

---

### Post by EXCiD3 on 2008-01-11
> **kedar.bhave said:**
> It seems I can login to secured networks, but I cannot login to unsecured networks using automatic configuration. I did not see an option for unsecured networks in manual configuration too.

Interesting...it might be a problem with Network Manager (assuming you use Gnome). Have you ever tried using a replacement such as WICD? [http://wicd.sourceforge.net/download.php](http://wicd.sourceforge.net/download.php)

---

### Post by Lloydus on 2008-01-13
Model: HP Pavilion dv9605ea
Processor:AMD TK-55 (1.8ghz)
Wireless Card:802 11a/b/g WLAN
Graphics Card: nVidia Geforce 7150M with shared graphics memory

Hi

I am a bit of a beginer with ubuntu, but I have fortunately only experienced a few problems!

I believe that I have a currently un supported wireless card - has anyone else had similar experiences?

Perhaps I will get an Ubuntu friendlly USB adaptor in the short term!

Other than that it im very impressed with my first ubuntu laptop!

Thanks

Lloydus

---

### Post by EXCiD3 on 2008-01-13
What exactly is the brand/make/model of your wireless card?

---

### Post by beherenow on 2008-01-13
> **HankB said:**
> Look for the Synaptics setup program. qsynaptics. Once you have your settings made, it can be run in batch mode (qsynaptics -r IIRC) and put in the programs that run at login.

IIRC, the setting I used was to disable the touchpad during typing.

HTH,
hank

Hank
This is very late in coming, but thanks for the qsynaptics batch recommendation. It was THE solution to my errant jumping cursor problem while typing.  Due to some necessary work for customers' Windows systems, I had to temporarily uninstall UBUNTU from my HP Special Edition L2005US laptop, for storage space, and just reinstalled it today, along with the startup batch file for qsynaptics to turn off the touchpad while typing.  I'm glad I found this three-month old post.  All is well.

MH
beherenow

---

### Post by Leo the Lion on 2008-01-13
I have a HP Pavillion dv2000 and almost everything worked fine after a fresh install of Ubuntu 7.10. The only problems I'm having are with hibernate/sleep (apparently this is a general thing) and my webw cam.
Can anyone explain to me how to get the webcam working?
I'm fairly new to LINUX, so go easy on me :).

Thanks

---

### Post by jkyamog on 2008-01-13
You will need to identify first the webcam.  Maybe "lsusb" might give you some more details.  Try to also look at [www.linux-on-laptops.com](www.linux-on-laptops.com) or [www.tuxmobil.org](www.tuxmobil.org) there seems to be a good share of guides posted there for the dv2000.

As for the suspend and hibernate issue maybe playing with /etc/default/acpi-support file may help.  Does you dv2000 come with a ati/amd radeon card?  They normally work after setting SAVE_VBE_STATE=false and POST_VIDEO=false

---

### Post by pras29gb on 2008-01-13
hi all , 
i recently got compaq v6608tu , i tried installing gusty from the live cd but GDM has failed to startup, so 
i tried with alternate CD of gusty , the installation went fine and on logging in it prompeted to install the
restricted driver (nvidia driver)  i installed it , and restarted the machine. After the system started 
it said like the restriced driver installed cannot be configured in this laptop . but still i could able to have the compiz effects.:)
The only problem i have is it detects the video driver my laptop is show in 800*600 mode :(  but it tried to 
use in 1024*xxx mode its not working and the gdm crashes , if any one have any pointers on this please let me know abt it ........

---

### Post by drfox on 2008-01-13
> **pras29gb said:**
> hi all , 
i recently got compaq v6608tu , i tried installing gusty from the live cd but GDM has failed to startup, so 
i tried with alternate CD of gusty , the installation went fine and on logging in it prompeted to install the
restricted driver (nvidia driver)  i installed it , and restarted the machine. After the system started 
it said like the restriced driver installed cannot be configured in this laptop . but still i could able to have the compiz effects.:)
The only problem i have is it detects the video driver my laptop is show in 800*600 mode :(  but it tried to 
use in 1024*xxx mode its not working and the gdm crashes , if any one have any pointers on this please let me know abt it ........

What video card do you have?

Larry

---

### Post by ripgut on 2008-01-14
Compaq Presario X1000
1.4Ghz PentiumIV

Ati Radeon RV250 Mobility 9000

768Mb DDR RAM

60Gb HDD

AC97 Audio Intel ICH4

[Can't get the drivers to installl for anything](http://ubuntuforums.org/showthread.php?t=666823)

PLEASE help!

---

### Post by sundial on 2008-01-14
I am having problems with Gutsy wireless on my laptop Compaq.
Model: C500
Processor: Intel Celeron M 1.6ghz
Wireless Card: Broadcom 4311 
Graphics Card: Not sure
Gutsy Tribe:   (?)

I installed the restricted driver that the system selected and I got the system to light the button on the deck showing that my wireless was working.  But that was not really true.  My base computer could ping the laptop and I could ping out from the laptop to the Netgear wireless address 192.168.1.1.

However, the system could not show that it was detecting any wireless access points and I could not get out to the internet.  After looking at the Ubuntu Forums, I downloaded the Wicd software and that permitted me to get out an on to the net.  That is what I am using to send this note.  However, the range is very much limited.  If I go more than 20 feet from the Netgear access point I will lose the signal.  Now since the system is a dual boot one, I can boot Vista and use the wireless connection from more than 50 feet (most I have tested it).  So the question is what is wrong with my Ubuntu installation of the wireless?

Is this a common problem?  And is a fix available?  I want to get rid of Vista but until I have a reliable wireless connection using Ubuntu, I cannot afford to cash out the Vista partition  and finally get rid of it.

BTW, I am not very experienced using linux and have some problems using linux commands.

---

### Post by EXCiD3 on 2008-01-14
For broadcom wireless you might want to refer to these two threads: 
[http://ubuntuforums.org/showthread.php?t=405990](http://ubuntuforums.org/showthread.php?t=405990)
[http://ubuntuforums.org/showthread.php?t=587549](http://ubuntuforums.org/showthread.php?t=587549)

Also, im sure it has been mentioned SEVERAL times through out this thread, just search the thread/forums and you should find your answer. Once Hardy is released my new Howto will cover these topics to make it easier for everyone.

---

### Post by sundial on 2008-01-14
Thanks for the quick response.  I looked at the two items below.  the first one is where I found out about Wicd.  The second really is of no help to me.

Let me restate the problem.  I can now use the wifi BUT, the range from the access point is very restricted.  

I do not understand how the driver and Wicd can effect the signal strength?

I am getting about 1/4 of the distance from the AP as I get when I boot with Vista.

BTW, I did do a search and found nothing on signal strength.

Thanks again,
PCR


[http://ubuntuforums.org/images/uf/editor/separator.gif](http://ubuntuforums.org/images/uf/editor/separator.gif)
> **EXCiD3 said:**
> For broadcom wireless you might want to refer to these two threads: 
[http://ubuntuforums.org/showthread.php?t=405990](http://ubuntuforums.org/showthread.php?t=405990)
[http://ubuntuforums.org/showthread.php?t=587549](http://ubuntuforums.org/showthread.php?t=587549)

Also, im sure it has been mentioned SEVERAL times through out this thread, just search the thread/forums and you should find your answer. Once Hardy is released my new Howto will cover these topics to make it easier for everyone.

---

### Post by EXCiD3 on 2008-01-14
I think this is caused by the drivers not actually being written for native linux. Essentially the windows driver is being emulated on your machine causing a loss of signal strength. I'm not sure what else you can do other than move the wireless router.

---

### Post by sundial on 2008-01-14
Thank again. Do you think the next version due in April will be better?

---

### Post by EXCiD3 on 2008-01-14
Your welcome, just trying to help out! :) Yes, Hardy's release is a LTS release meaning it will be supported for a long time. Basically they are going to makeover gutsy a little and FIX many of the bugs that were created in Gutsy's release. Hopefully, it will be the easiest release yet!

---

### Post by gRoberts on 2008-01-15
Well since no one will reply to my original post:

Model: Compaq Presario V6560EA
Processor: Intel(R) Core(TM)2 Duo CPU T5250 @ 1.50ghz
Wireless Card: Intel Pro/Wireless 3945ABG
Graphics Card: Intel 965 (Express)
Gutsy Tribe (Version): 7.10?
Boot Parameters: N/A

Everything works fine apart from the sound and the mute button led (stays red regardless of muted or not) while running from the Live CD.

When I try installing, it takes a little while to get the partitions, and then displays the current partitions created by Compaq. I delete both partitions and create a root / at 159.50gb and the remaining 500mb left for swap.

Upon clicking next, it takes a little while and then goes back to the partition select screen.

This time I told it to use the whole hard drive and it done the same.

Any idea's?

Cheers

---

### Post by kurbacik on 2008-01-15
I have a HP ZV5000 laptop with 32bit Gutsy, and everything works great. I had to install the version network-manager_0.6.5-0ubuntu15 (and corresponding libraries) to be able to access the university network here at Purdue, but besides that all is fine. If anyboday has my laptop, reply back to me and I can give you a hand. I have a lot of experience working Linux into this laptop :) 

Cheers!

---

### Post by PissedApache on 2008-01-17
Model: HP DV6615em
Processor:AMD  64 X2 TK55
Wireless Card: BCM94311MCG
Graphics Card: Nvidia GeForce 7150M 
Gutsy Tribe (Version): 7.10 x86 Alternate CD install
Boot Parameters: N/A

I used G-Parted to partition the hard drive and then used the largest free space option when installing.

Used this to get the wireless working:
[http://ubuntuforums.org/showthread.php?t=297092](http://ubuntuforums.org/showthread.php?t=297092)

And this to fix the sound for Enemy Territory :)
[http://ubuntuforums.org/showthread.php?t=362231](http://ubuntuforums.org/showthread.php?t=362231)

Just need to find the thread about the speakers working when using headphones......... btw

\\:D/

---

### Post by horobi on 2008-01-17
Model: Compaq 6720s
Processor: Celeron
Wireless Card: BCM4312
Graphics Card: gm965/gl960
Gutsy Tribe (Version): 7.10
Boot Parameters: none

had to upgrade bios to latest version because the network interface didn't worked out of the box due to a bios bug :)

---

### Post by lebiathan on 2008-01-18
Yello ubuntu (great) forum! :)

Model: Compaq 6328ea
Processor: Intel Core Duo T2350
Wireless Card: (i'm not sure which one i've got... but works like a charm!)
Graphics Card: GMA950 (it's in the GMA945 family, from what I've read)
Gutsy Tribe (Version): 7.10
Boot Parameters: none

Ubuntu runs solo on the laptop. Wireless plays just fine upon installation of the OS. I firstly installed Edgy (6.10 i think) and updated to Feisty 7.04, when the update manager said so :p :) (and now have Gutsy 7.10) 

I'm actually having a problem with the resolution of the computer. Currently, I'm viewing things under 800x600.. I'd like to move to 1024x768 resolution preferably.. Thing is, the x-server crashes upon restart, if I change the resolution from the "Screens and Graphics" section. I've read (and tried) the 

sudo apt-get install xserver-xorg-video-intel

command, with no success. Actually, from what I recall, the message displayed was that the particular driver was already installed. Thing is that I can actually change the resolution while running ubuntu, and the display will also change to the desired resolution. The problem pops up when I actually restart the system. After displaying the splash screen, it blinks for about three times (trying to initialize the x-server i suppose) and then halts, prompting me to the command line. If I manually try to initialize the x-server via the xinit (or xorg, or X), I get the error message found in the attachment.

I don't really mind about the resolution being a 800x600.. I just don't get it why it works fine on one occasion but not after a restart. Plus, sometimes the resolution will be changed on its own (i'm not kidding, I don't change the settings very often) after a fresh boot-up to 1024x768.. and after rebooting it will again be 800x600 :(

When prompted to the console, i'm forced to a 
sudo dpkg-reconfigure -phigh xserver-xorg
so that I can then restart the xserver.

Any help is greatly appreciated.. I didn't want to start a new thread since there is a specific one for HP laptops.

Thanx all! :)
George

---

### Post by ritergal on 2008-01-18
I installed Gutsy on an older Compaq Presario 2100 laptop. All is working well except for the Netgear WG511 cardbus wireless card. Gutsy recognizes my Windows network and is able to move files back and forth via ethernet, but the Windows network does not see Gutsy.

Now, if only I can get the Netgear card going.

I'm new to Linux. When I try to do things in folders I assume are root folders, I get messages that I do not have access. Everything is taking ages as I dig out each thing, piece-by-piece, from the Forum. Anyone have a shortcut?:confused:

---

### Post by Dynaflow on 2008-01-18
> **ritergal said:**
> I installed Gutsy on an older Compaq Presario 2100 laptop. All is working well except for the Netgear WG511 cardbus wireless card. Gutsy recognizes my Windows network and is able to move files back and forth via ethernet, but the Windows network does not see Gutsy.

Now, if only I can get the Netgear card going.

I'm new to Linux. When I try to do things in folders I assume are root folders, I get messages that I do not have access. Everything is taking ages as I dig out each thing, piece-by-piece, from the Forum. Anyone have a shortcut?:confused:

```
sudo nautilus
``` will give you a graphical file navigator/manager with carte blanche to open and edit pretty much whatever you want.  Use it with caution.

For the Netgear card, have you tried this (you'll have to open a terminal window)?:  [https://help.ubuntu.com/community/WifiDocs/Device/NetgearWG511andNdiswrapper]("https://help.ubuntu.com/community/WifiDocs/Device/NetgearWG511andNdiswrapper").  That should still work for Gutsy, except for the kernel version named.

---

### Post by dogshoe21 on 2008-01-18
I have a compaq presario 2100 series and I have a problem with the resolution. When the machine first boots I can't make out anything because everything is distorted. If I find my way through the blur and can change my resolution to 800 x 600 and then everything is fine. I want 1027 x 768!!! any ideas? this is the only problem I've had so far

---

### Post by ReedyCreek on 2008-01-19
Installed on HP/Compaq nc6220 with no issues.  Since, I've only encountered 3 issues, 1 of which I don't believe is a distro problem.

1. Intel 2200BG Wireless not recognized out-of-box.  Gnome Network Manger did recognize a wireless interface and I was able to use it (manually configured) to connect to my Belkin 802.11g wireless router using WPA-PSK 128bit encryption and a hidden SSID and DHCP.  My only gripe with NM is having to re-enter all information after every reboot. I finally installed a tool called "Wireless Connection Manager 1.10" (sorry, I didn't save the pkg path) that saves connection information across reboots and also allows for automatic reconnect to preferred networks and management of multiple wireless networks.

2. I don't believe this is a distro problem, but a problem with Linux and wireless in general.  I use this same machine to connect to the wireless network at my office, it uses hidden SSID and 128bit WEP with the encryption being provided automatically via certificate.  I have yet to be able to get Gutsy to automatically accept the WEP key from our network.  I've download and installed the certificate but the connection manager keeps asking for the WEP key.  May be a solution for this but I've not found it yet...

3. Power management seems to work ok until you check "Always display an icon" on the General tab of Power Management Preferences.  With this option on, the session crashes and logs you off every time the utility checks icon status (approx. every 2-5 minutes).

These three issues notwithstanding, the distro is working well on this machine so far.

Thanks for the great build!!

---

### Post by Link_ on 2008-01-19
hp6720s
core2duo 1.6
both wireless and wired - intel
for first time network was not working. until bios upgrade to F.07
now I have problem only with suspend to ram:
[https://answers.launchpad.net/ubuntu/+question/22545](https://answers.launchpad.net/ubuntu/+question/22545)

---

### Post by old_salt on 2008-01-20
Bear with me as I will document my complete install process and thoughts;

Model: Pavilion Dv 9000z
Processor: AMD Turion X2 2,2Ghx
Wireless: Broadcom 4311 Rev01
Graphics: nVidia 6150go
Boot Param: nolapic pnpacpi=on
Kubuntu Gutsy 64 bit Alternate Install
------------------------------------------------------------

Thank goodness for a 3day weekend as I will document my entire install process.

TRY 1
no boot parameters = Stopped during boot after install at;
UVCVIDEO event message no buffer space available

TRY2
added pnpbios=off to kernel boot parameters
Stopped on reboot after install at 
UVCVIDEO failed to initialize device -5 UVCVIDEO

TRY3
added pnpbios=off pnpacpi=on to kernel boot parameters
Error [30.522134] USB 1-6 not accepting address 4 error -62 continues boot then stops at UVCVIDEO: no buffer space

TRY4
Added nolapic to kernel boot paramters
system installs and boots however performance VERY slow. Not all hardware detected. Suspend and Hibernate inoperable. System report from top is excellent.

TRY5
added nolapic pnpacpi=on to kernel boot parameters
Installs and boots with good performance. All hardware appears to be identified and operational for those devices not requiring additional configuration or software to install. USB works, Bluetooth works, Suspend/Hibernate are still inop.

Not concerned with suspend or hibernate - not used for me.

System performance is acceptable and the hi% in top at 0%. NOW my system isn't having a meltdown at idle. 
-----------------------------
All other boot parameters as identified in this and other postings to include other Distro forums failed. I can't understand why no distro adopts the same hardware detection process a Knoppix which is astounding and even better than Winblows.......
-----------------------------

Now that I can install the OS and not have a meltdown I will proceed with probably doing a good job of ticking off a lot of developers and Canonical folks but I don't care as this info needs to be made known and documented.

- A US Install should properly setup the default printing paper size and measurement system vice manually adjusting through System Settings-Country Region-Other. Other distros don't have this issue.
- System Settings window is not scalable therefore you must resize the window to view & access the action buttons. Once again other distro's don't have this issue.
- Click "Administrator Mode" in System Settings-Restricted Drivers after initial system boot after install is inoperable. Once the "Restricted Drivers" icon is gone from kicker there's no access. Attempts to Command Line bringing up kde-restricted-manager results in a DCOP error. At this point forget trying to install the restricted drivers for your display or wireless.
- Restart X using CTRL+ALT+BACKSPACE renders no mouse
- Power button does work properly to shutdown the system however even with my boot parameters, Suspend & Hibernate do not work. Must hard reset.
- Never could get Video driver installed. Will try Automatix or Envy. (NOTE: At least these apps provide a restore script to use in failsafe mode to restore an X session.) Mucking through the xconfig is NOT a workaround or solution outside a developer's skillset. FIX THIS!!!!
- No Lightscribe support outside an RPM based distro. Oh PLEASE !!!!! Can't someone get this going for the deb side?
- SANE - Unless you have a 2yr old scanner........... forget it. Folks, scanners are as common as printers at home now. Get with it will you?
- Initial update - MUST use a command prompt for this as it will stop at 75% at which point your system is toast and you re-install from scratch again. You have to answer a prompt of "N" to a question to complete the initial update which the Adept updater can't handle. (Thank the QT folks for the QT-Plugin module install for this. --- IDIOTS!)
- Broadcomm firmware installed a 4312 driver for my 4311 wireless so I only have 24Mb connection. Mepis actually worked at 54Mb.
- Click Adept notify after initial update and it STILL opens 2 instances of the app. I thought this bug was fixed? It says 2 updates are remaining yet 37 showed up and installed. What the? Are we now going to have issues like the RPM distros?
- No wireless using WPA. After install of Broadcom firmware, wired connection is inop as well. Remove and use wired connection and try the ndiswrapper route.
- Synaptic - must move mouse off and back onto the tool bar button to use. Cannot leave mouse cursor on an icon to re-use this. (Sloppy Coding)
- Flash Install - Oh my; still getting the MD5 checksum error after how many months now? Geez folks, fix it or else remove this option from the system. 
- Kpilot & Jpilot are both inop. Gnome pilot does work with Evolution mail client however it's a 1-way communication only. From Evolution to your device. Come on now, how many years have PDA's and smartphones been around now? I'm even more shocked PALM isn't even supported now. 
- Why must half of the KDE apps require gnome libraries? Synaptic dialog window;
:unable to initialize frontend:gnome
:falling back to frontend: dialog
:Dialog frontend will not work on a dumb terminal, emacs shell buffer, or without a controlling terminal. 
- Dolphin - remove this piece of garbage that fills your files system full of hidden files and corrupts home folder permissions. 
- AppArmor - Remove this as well as I've yet to find even the developers are able to expain what this is for.
- Remove Strigi - Just what anyone needs, a TSR search app - Just like Microcrap. Use the tools already provided or learn where you put things is my advice on this. . 


------------my dissertation--------------------------

I have formal education in Electronic Warfare and IT with 20+yr experience as an IT professional; I have to ask - Does this sound like a "Final Release"? Heck no!!!! It's "pre-Alpha" at best. Where's the QA folks and process at Canonical? Better yet - Where's those claiming to be testing on this HP Platform? I don't see where they've even installed the OS because if they did, they certainly didn't provide feedback to developers or the developers have a problem with HP. The various forums ARE NOT the place for average users to have to troubleshoot major show stopping issues. That's what he Bug reporting areas for testers is for however without designates for this, this venue is non-productive. Forums were designed for "Tips & Tricks" and minor support issues, instead it's been relegated over the past year to a major source for identifying and resolving serious issues. How Sad!!!! The Linux system should at least install. Microcrap does. then you update the drivers. Linux? Your not even close yet.

In either case, Canonical needs to court ALL major vendors identical to the way they did with Dell. HP is the oldest supporter of the *nix platform and of course they aren't going to divulge specifics to some individual developer or coder via email. They will do as they're told and support only the formal sanctions handed down from corporate. 

The items above are the result of incompetence, lack of organization & communication,  laziness and lack of attention to detail by developers and coders. Sure they are not paid to do what they do however if you give your "Word" and publicly volunteer your efforts; then at the very least, you should show no different the same measure of professionalism, dedication to duty, attention to detail and thoroughness that which you are paid for. If not then stay away!

I also see common major hardware issues across multiple disto's yet no efforts have been made to "Bridge the gap" in efforts to resolve an issue mutually beneficial to all in the context or support of "The Community". "The Community" means Linux as a whole - spans all distros and doesn't mean just one flavor. As reported in numerous articles in many magazines; (And I quote LinuxMagazine and PCWorld on this) The biggest obstacle for Linux to overcome is the internal feuding and competition amongst itself. Until this obstacle is overcome, then Linux will never progress beyond what it is now. 

I could have taken a U.S. State agency to a full Linux environment however I could not overcome the reports as identified in the above paragraph, Instead they opted to spend $$$$ on Microcrap because of it. Linux had the "Perfect 4 yr Window" of opportunity to gain mainstream acceptance but instead opted for reshuffling, merging and entering into contracts with the competition as well as allowed paranoia with regards to so-called patents which are currently being overturned in favor of Open Source to stand in it's way. Once again the result of sloughing off efforts because of pride and individuality instead of unity. 

I applaud Mr. Torvalds efforts with regards to the 2.6.24 kernel. It's long overdue in my opinion and I welcome his direct involvement once again in efforts to stabilize this platform. I would like to propose that there be a "General Counsel" established that would receive major bug reports from the various distro's reporting to Mr. Torvalds directly who would correlate common major issues across all distros and platforms for direction and assignment for resolution. 

-------------My pledge--------------------
I pledge my sincerest support of the Linux platform and will continue to provide advice as and where needed across all platforms. I suffered serious verbal abuse as Excid3 can verify when attempting to point out serious issues with Ubuntu developers and kernel developers for the HP platform and the USB Kernel issues for Gutsy development. This was unjustified and my claims were immediately dismissed which resulted in my being labeled inappropriately. My postings were even retracted by the moderators because of pressure from higher levels. I believe this posting substantiates my previous remarks in prior postings and I hope that this serves as a wake-up call to everyone. I think it's high time we all just get along together for the better of Linux and stop playing the "Politically Offended" game and take the criticism and remarks in stride and just make things work like we know how.

Sincerely,
Old_Salt

---

### Post by timsath on 2008-01-20
Model: Compaq F756NR
Processor:AMD 64 1.9 gHz
Wireless Card: Atheros AR5006EG
Graphics Card: Nvidia GeForce 7000M
Ubuntu Version: Gutsy 7.10 x86 32-bit
Boot Parameters: N/A

Had to boot from LiveCD using safe graphics mode.  1280x800 resolution did not work by default.  nVidia restricted drivers WERE NOT installed.  Installed nvidia-glx-new, then enabled them in the restricted drivers manager.  After that, I had to reconfigure my video card to use the nv driver, and set the monitor to a default LCD 1280x800.  DO NOT set it to widescreen or you will not get a proper resolution.  Reconfigured Xorg to use 1280x800.  Wireless card would not work with madwifi, used ndiswrapper instead.  Downloaded the 32bit WinXP drivers from [www.atheros.cz](www.atheros.cz).  Card worked fine after that.  Sound works, but headphone jack sense does not.  You can hear music from the external speakers and the headphones, but there is no way to mute the external speakers.  Only work around is buying a cheap USB sound card off eBay.  You cannot use the full desktop effects or the xserver will crash.  If anyone has this laptop and needs assistance installing ubuntu, let me know.  Also, if anyone has a solution to the sound card issues, please PM me, or reply to this thread.  Thanks!

---

### Post by Dynaflow on 2008-01-20
> **timsath said:**
> Model: Compaq F756NR
...
 Sound works, but headphone jack sense does not.  You can hear music from the external speakers and the headphones, but there is no way to mute the external speakers.  ...  Also, if anyone has a solution to the sound card issues, please PM me, or reply to this thread.  Thanks!

I had the same problem with my Compaq C706NR, and the problem turned out to be the support (or lack thereof) of the [HDA Intel]("https://help.ubuntu.com/community/HdaIntelSoundHowto") sound hardware in the version of ALSA shipped with Gutsy.  I updated ALSA to its latest version (using [this script]("http://www.antonywilliams.com/2007/10/bash-script-to-automate-compiling-alsa.html")), and now everything works like a charm.

---

### Post by timsath on 2008-01-20
> **Dynaflow said:**
> I had the same problem with my Compaq C706NR, and the problem turned out to be the support (or lack thereof) of the [HDA Intel]("https://help.ubuntu.com/community/HdaIntelSoundHowto") sound hardware in the version of ALSA shipped with Gutsy.  I updated ALSA to its latest version (using [this script]("http://www.antonywilliams.com/2007/10/bash-script-to-automate-compiling-alsa.html")), and now everything works like a charm.

Thanks, I'll try that out!  :)

---

### Post by timsath on 2008-01-20
> **Dynaflow said:**
> I had the same problem with my Compaq C706NR, and the problem turned out to be the support (or lack thereof) of the [HDA Intel]("https://help.ubuntu.com/community/HdaIntelSoundHowto") sound hardware in the version of ALSA shipped with Gutsy.  I updated ALSA to its latest version (using [this script]("http://www.antonywilliams.com/2007/10/bash-script-to-automate-compiling-alsa.html")), and now everything works like a charm.


What options did you use on the alsa-base file?  Also, my Conexant card comes up using the OSS driver...do you know anything about that???  Thanks!

---

### Post by Dynaflow on 2008-01-20
> **timsath said:**
> What options did you use on the alsa-base file?  Also, my Conexant card comes up using the OSS driver...do you know anything about that???  Thanks!

Ah, I forgot to mention that important step.  :oops:

Enter ```
gksudo gedit /etc/modprobe.d/alsa-base
``` append ```
options snd-hda-intel model=hp
``` to the file, and reboot.

It should be using the ALSA driver, not OSS.  See if you can change it through System -> Preferences -> Sound.

---

### Post by timsath on 2008-01-20
> **Dynaflow said:**
> Ah, I forgot to mention that important step.  :oops:

Enter ```
gksudo gedit /etc/modprobe.d/alsa-base
``` append ```
options snd-hda-intel model=hp
``` to the file, and reboot.

It should be using the ALSA driver, not OSS.  See if you can change it through System -> Preferences -> Sound.

Still having the same issues, I'm wondering if just disabling the Conexant sound card would fix the issue, but I don't know how to do that.  Whats the file that contains all the modules that are loaded?? Thanks again, I'm not exactly a newbie, but I'm still new to linux.  :)

---

### Post by Dynaflow on 2008-01-20
> **timsath said:**
> Still having the same issues, I'm wondering if just disabling the Conexant sound card would fix the issue, but I don't know how to do that.  Whats the file that contains all the modules that are loaded?? Thanks again, I'm not exactly a newbie, but I'm still new to linux.  :)

I think what you want is for the card to use that driver.  Take a look at [this]("http://ubuntuforums.org/showthread.php?t=205449") and [this]("https://help.ubuntu.com/community/HdaIntelSoundHowto"), and see if anything looks like it might apply to what you're experiencing.

Actually, before you do that, try right-clicking the volume icon in the Gnome desktop, clicking Preferences, and seeing what driver is selected.

---

### Post by push_harder on 2008-01-21
I have a Acer Extensa 5220, and after much messing around.
I finally got everything to work.
Many tutorials later, i now have a fully working version of gutsy :D

---

### Post by timsath on 2008-01-21
> **Dynaflow said:**
> I think what you want is for the card to use that driver.  Take a look at [this]("http://ubuntuforums.org/showthread.php?t=205449") and [this]("https://help.ubuntu.com/community/HdaIntelSoundHowto"), and see if anything looks like it might apply to what you're experiencing.

Actually, before you do that, try right-clicking the volume icon in the Gnome desktop, clicking Preferences, and seeing what driver is selected.

What's interesting about that, is I have "two" soundcards enabled, HDA nVidia, and Conexant ID 5051...but, if I change the master or pcm on the Conexant, it kills the volume on the nVidia, and vice versa.  It's as if both cards are linked, but what's weirder, is that the Conexant uses an OSS driver and the nVidia uses Alsa.  Quite strange...thanks for your help :)

Edit:  Doesn't Alsa make use of some OSS drivers though?

---

### Post by Keeg on 2008-01-24
HP Pavilion dv6386

Needs the "noapic" boot option to boot, both from the live CD/alternate and later on when you've installed. Other than that stuff seems to work fine.

(Not much content I know, but info about the model is almost non-existant, so I thought I'd throw in a post in the vain hope it'll show up in searches for other frustrated people, like me)

---

### Post by Leo the Lion on 2008-01-26
HP Pavilion dv2000
Intel Core 2 Duo
Wireless Card:802 11a/b/g WLAN
Graphics Card: Intel

I'm running Ubuntu 7.10 and everything is working fine except for the suspend/hibernate function. I'm not sure if this is something to do with running Compiz Fusion. Has anybody gotten this to work properly? If so, how?

---

### Post by EXCiD3 on 2008-01-26
For suspend/hibernate, several people have found this thread to be useful: [http://ubuntuforums.org/showthread.php?t=471855](http://ubuntuforums.org/showthread.php?t=471855)

---

### Post by fiprojects on 2008-01-28
Model: dv9000 (actual product label underneath says dv9618ca)
Processor: AMD Turion64x2
Wireless Card: Broadcom Corporation BCM4312 802.11a/b/g (rev 02)
Graphics Card: Nvidia (sysinfo says device 0531 (rev a2))
Audio device: nVidia Corporation MCP67 High Definition Audio (rev a1)
Webcam: HP Webcam (I know - no model name but that is how I seen it referenced in 'cheese')
Gutsy Tribe (Version): Ubuntu 7.10, kernel 2.6.22-14-generic
Boot Parameters: None

Ethernet and sound worked from install.  I couldn't get compiz working without downloading the restricted drivers.  Same for the Broadcom drivers.  Bluetooth seemed to work from install though I never got to test it until some time after I was happy with the install.

Now? Sound and webcam is no longer working!  I'm not too bothered about the web cam but I would really really love the sound back.  Can someone advise? Perhaps even share with me the output to /etc/modules.d/options ? I don't have enough experience for desktop linux configuration...

I really really really would love my sound back. Thanks!

---

### Post by jmagsho on 2008-01-28
**Model:** Compaq Armada E500
**Processor:** Pentium III M 650 Mhz
**Wireless Card:** Netgear WGT511NA
**Graphics card:** ATI Rage Mobility AGP 2d
**Gutsy Tribe**: Final version 7.10

Wireless, sound, and most everything else worked from the get go.  About the only thing I have left to get working are the Function keys to enable on screen settings like brightness and contrast.   I believe I came across the instructions here on the boards someplace but have not gotten around to it yet.

For a 7 year old laptop with only 512 mb of ram, this thing runs Ubuntu like a champ.  It still cracks me up that this machine seemingly runs at least twice as fast as one of my desktops running Windows XP with 2 GB of ram and a 2.6ghz processor!  To be honest, I don't use the Windows machine much anymore as I've grown quite fond of Ubuntu since I started using it when 5.10 came out.

---

### Post by rookie76 on 2008-01-30
Model:  Compaq 6820s
Processor:  Intel Core 2 Duo T7250 @2.00 GHz
Wireless Card:  Intel Wireless Wifi Link 4965AGN
Grafics Card:  ATI Mobility Radeon X1350
Gutsy Tribe: 7.10

First let me state that I'm new to Linux but loving it.

I've been struggling to get Ubuntu up on a dual boot with vista on my new lap top for a couple of days...  I can complete the installation but my network card won't talk to my router.  The ethernet card is recognized by the OS but I can't set it up to talk to my router through pppoeconf...  I have two other machines running Ubuntu (7.10 and 6.06) with no problems at all.  Can anyone help?

---

### Post by dondragon2 on 2008-01-30
Model: HP Compaq nc6400
Processor: Centrino Duo 1.83Ghz
Wireless Card: Intel 3945
Graphics Card: Intel
Gutsy Tribe (Version): 7.10 kernel 2.6.20-15

All works well so far.

Built in Microphone: did not work initially

made the following changes to resolve that.

sudo gedit /etc/modprobe.d/alsa-base

add the following line at the end of the file.
options snd-hda-intel model=hp

save and restart. VOILA!!! you've got mic :)

---

### Post by phidia on 2008-01-31
Model:dv6707us
Processor:AMDx2 tk-57 
Wireless Card:Ahteros AR5007EG
Graphics Card:Nvidia Geforce go 7150M
Gutsy Tribe (Version):final 64bit
Boot Parameters:none required

The biggest problem I had with this was getting the atheros wireless chip working but after many tries (documented at these forums) it appeares to be working well now.
I will definately be checking out other links from this thread. I can say though that most everything I use works...sound, ia32-libs (for 32 bit games like SL)
Everything works ok.

---

### Post by bones_83 on 2008-02-06
Model: HP Pavilion dv1000
Processor:1.7 Ghz Pentium M 
Wireless Card:Intel PRO/Wireless 2200BG

Ok I'm new to linux but Ubuntu is growing on me. I installed 7.10 as a dual boot on my notebook. Everything installed fine but I'm having the same problems everyone else is having...my wifi card detects networks but can't connect. I have browsed through the forum and people recommend using Feisty over Gutsy. My question is would installing Feisty over Gutsy be the best route for me???

---

### Post by andii on 2008-02-07
nx6325
My main concern is about the ability to use the fn f4 key which in Feisty as in Windoze toggles to allow me to project presentations. After upgrade to gutsy this didn't happen any more, although the fn key will allow me still to adjust the brightness. The specialised presentation button doesn't work but the sound and mute buttons still seem to operate.
These did work under Feisty but not in Gutsy; I'd love to have them back.
Also mic input is not working.

---

### Post by SCSI15 on 2008-02-07
> **rhricik447 said:**
> Jukka - I was having a problem that even after following your directions, I was still getting bcm43xx listed as the alternate driver for ndiswrapper.  The solution is to remember to **turn off the Broadcom restricted driver** before starting.  Once I did that and rebooted, I now have 54G, WEP enabled wireless on a:
HP Pavilion dv6451us
AMD Turion X2 64bit
Broadcom 4312 rev 2 miniPCI HP card
2 Gb RAM
160 Gb SATA drive
Bluetooth working

Thanks a million for the post - I've been fighting with this through 3 different distros (Fedora 6 & 7, Ubuntu 7.04) without success.

I am assuming you're using Ubuntu 7.10. I am trying to use it on the exact same laptop you have  I cannot get past the black screen when it loads. I have tried disababling the splash screen. That didn't change anything.  It loads the drivers needed and I get this blank screen with a cursur in the upper left hand corner. 

I tried hitting esc to get into the terminal and I am stuck at boot: and it will not let me do anything. I've tried loading the nvidia driver and no success. What did you do to get it to work?

---

### Post by andii on 2008-02-08
In my case I upgraded from 7.04, so maybe that preserved some settings? I'm not technical enough to know what might have gone wrong. I tried changing keyboard in the appropriate preferences menu but that doesn't seem to have helped. It seems strange that the volume buttons and the brightness fn keys should work but not the extra monitor button.

---

### Post by maeleh on 2008-02-08
Model: dv9000
Processor: Intel Core 2 Duo 2.0GHz
Wireless Card: Intel Wireless N
Graphics Card: Nvidia GeForce 8600 GS 256mb
Gutsy Tribe (Version): 7.10

Hi, I'm having trouble getting the sound to work on my Ubuntu setup. It recognises the soundcard, I can adjust the volume and other properties, however I am getting no output at all.....

Any ideas??

Sean

---

### Post by link141 on 2008-02-08
Hi everyone
About a month ago I got a shiny new Compaq Presario on New Years Eve.  Here's the specs:

Model: Compaq Presario F756NR
Processor: AMD Turion64x2 1.9ghz 64-bit Dual core cpu
Wireless: Atheros AR5007(eg?) wifi
Graphis: NVidia GeForce 7000M nForce 610 (can use up to 335MB of system memory 900MB turbo-cache)
Memory: 2GB
OS version: Kubuntu 7.10 AMD64 Final and Vista (Yuck! my dad made me keep it on there for my siblings)

I had to boot the Kubuntu live/install CD in safe graphics mode, because the graphics didn't work out of the box.  The display was also the incorrect resolution.  However, the restricted drivers manager picked up the card great, and installed the correct drivers over my wired ethernet connection.  I was then able to change my moniter type and resolution, and my widescreen display is now working great.  I can run the really, really fancy effects in Compiz Fusion much faster than the default effects in Vista.  

The brightness and lock keys didn't work out-of-the-box so I did this:
1. Found the key codes with Xev by typing "xev", pressing the keys, and recording the keycodes

2. Made a new text file called ".Xmodmap" and added the keys one by one like this:
keycode 101 = F13
keycode 212 = F14

keycode 146 = F16

I could test it with "xmodmap .Xmodmap"
This file always loads at start-up.

3. I could now map the lock button to the command "dcop kdesktop KScreensaverIface lock" the kde accessibility settings (under input actions).

4. First I found the script from [https://wiki.ubuntu.com/KubuntuPowerManagementFeedback](https://wiki.ubuntu.com/KubuntuPowerManagementFeedback) and figured that I could change the brightness as well.  So I tried the dcop command with brightnessUp and brightnessDown instead, and it worked!!  I added these lines to the script:
  *brightnessDown*)
      dcop $PM power-manager brightnessDown
      ;;
  *brightnessUp*)
      dcop $PM power-manager brightnessUp
      ;;
and saved it as /usr/bin/pm-hotkey.

5.  I made symbolic links with:
sudo ln -s /usr/bin/pm-hotkey /usr/bin/pm-brightnessDown
sudo ln -s /usr/bin/pm-hotkey /usr/bin/pm-brightnessUp
sudo ln -s /usr/bin/pm-hotkey /usr/bin/pm-suspend
sudo ln -s /usr/bin/pm-hotkey /usr/bin/pm-hibernate
sudo ln -s /usr/bin/pm-hotkey /usr/bin/pm-showTip

and made them executable with:
sudo chmod +x /usr/bin/pm-brightnessUp
sudo chmod +x /usr/bin/pm-brightnessDown
sudo chmod +x /usr/bin/pm-suspend
sudo chmod +x /usr/bin/pm-hibernate
sudo chmod +x /usr/bin/pm-showTip

6. I was then able to assign my keys to the brightness up and down functions in the kde accessibility settings.  I also mapped the break key to show the battery and cpu frequencies, and all my buttons now worked.

Next was my wireless which I couldn't get working until just last week.  The chip is an AR5007eg, and needed an extra setting to work.  NDiswrapper was setting my Mac address to all zeros and I had to add an extra setting I found from a user on this forum to set the mac address.  Without the Mac address, the card would only list the ten routers down the block and hang on the IP Configuration step when trying to connect with them.  Here's what I did to get it to connect:

1. Install and configure ndiswrapper by following most of the instructions here:  [http://ubuntuforums.org/showthread.php?t=512828&amp](http://ubuntuforums.org/showthread.php?t=512828&amp)
*No need to reboot, I believe you just need to restart networking with:
sudo invoke-rc.d networking restart

2. To get the Mac address assigned I had to add:
pre-up /sbin/ifconfig wlan0 hw ether 00:1E:4C:2D:7F:0A

to /etc/network/interfaces and commented out "auto wlan0" (or else it found two interfaces)
*Thanks to Afterstep13 for pointing this out ([http://ubuntuforums.org/showthread.php?t=512828&page=30](http://ubuntuforums.org/showthread.php?t=512828&page=30))

3. I restarted the network a few times, and finally, I got it to connect to my router after a month of banging my head against the wall.  The light doesn't light up, but the switch to turn off wifi works.

I custom-installed a regression version of flash and used nspluginwrapper to get it working with Konqueror.  I also installed several multimedia codecs, got encrypted dvds to play, and installed some software.

The sound works great out-of-the-box and so do the multimedia buttons (such as volume up, down, next track, previous track, stop, and pause/play).  I believe mute button worked out-of-the-box, but it stopped working after an update and the "mute: on/off" pop-up stopped appearing shortly after.  I tried assigning the mute button to the mute function in kmix, but it doesn't work.  The headphone jack also works out-of-the-box but not after the laptop has been suspended.  The headphone jack sense doesn't work (there's no switch for it in kmix), so the sound plays out of both the speakers and headphones at the same time.  The headphone-jack sense works fine in Windows, so it's a software issue.  Apparentely, there's a patch to fix this, but the audio sounds like crap at a higher volume.  I haven't tried the built-in microphone yet.

I also have an SD-card reader integrated into my laptop that works out of the box (it was having problems with my Dad's 4GB SD-card, but works fine with my 2GB card and my sisters 1GB card).  I have a moniter-out and an s-video out, but haven't tried them yet.  I also haven't tried my modem.  My CD/DVD-DL burner works out of the box, but I haven't tried burning any DVDs with it (I heard K3b has bugs with the larger size (>1GB) mediums, but I'm not sure about this).

Suspending by closing the lid works out-of-the-box, but not after suspending it once.  The suspend button always works.  Besides the headphone jack not working after suspend, I haven't noticed any problems with/after suspending it.  I think power management works better than on Windows Vista.  I haven't tried hibernate yet, but it probably works.

In terms of performance, this laptop is blazingly fast.  Kubuntu runs circles around Vista.  Overall, this laptop works awesome with linux.  I've been able to get almost everything working, and it runs very well.  I'd reccommend getting this laptop and putting linux on to anyone interested.

[quote=bones_83]my wifi card detects networks but can't connect[/quote]
NDiswrapper is known to set your MAC address to all 0s.  Type "ifconfig -a" in a terminal, look for where it says wlan0, and look after where it says "HWaddr".  If this is set to all 0s, than find your MAC address.  To find your MAC address in windows, open a terminal Startmenu>run>cmd and type "ipconfig /all".  look under "wireless lan adapter settings" for the line that says physical address and write it down.  You can also do a "ifconfig /all >ifconfig-output.txt" to save the output and access it from Ubuntu.  When you find your MAC address try doing what I did to set mine (where "00:1E:4C:2D:7F:0A" is the MAC address of your card.  Make sure you use ":" to separate the letters/numbers instead of "-").  Restart networking, and see if you can connect.

[quote=andii]My main concern is about the ability to use the fn f4 key which in Feisty as in Windoze toggles to allow me to project presentations. After upgrade to gutsy this didn't happen any more, although the fn key will allow me still to adjust the brightness. The specialised presentation button doesn't work but the sound and mute buttons still seem to operate.  These did work under Feisty but not in Gutsy; I'd love to have them back.[/quote]
First, make sure the key(s) aren't already mapped.  I believe if you go to System > Preferences > Keyboard Shortcuts , you can set global shortcuts (I use Kubuntu).  Try making one for the command "openoffice -impress" and see if your key is picked up.  If it isn't, open a terminal, and type xev.  Press your fn key, and record it's keycode (you can also do this for the other keys you want to map).  Save each keycode to its respective key in a file called .Xmodmap in your home directory as I did above.  Supposedly, the name of the key can be arbitrary, (meaning you could assign it to "presentation" instead of an extra F key), but it gave me errors when trying it.  Then type "xmodmap .Xmodmap" in a terminal.  Your keys should now be detected.  It loads this file every time I login, so it should do the same for you.  Now you can map the keys as global shortcuts.

Hope this helps
link141

---

### Post by zgoda on 2008-02-08
Model: HP Compaq 6510b
Processor: Intel Centrino Duo T7500 2.2GHz
Wireless: Intel 3945ABG
Video: Intel X3100

Installing from alternate CD,had to specify VGA resolution, otherwise blank screen.

After installation everything looks pretty good, except:
 * freezing on laptop lid close or after screensaver activated;
 * keyboard lags, sometimes single keystroke produces few characters;
 * surprisingly short battery time (little bit more than 3.5 hours).

---

### Post by mauser on 2008-02-08
Model: HP/Compaq Presario C551NR
Processor: Celeron M 440 1.86ghz
Wireless Card: Broadcom BCM94311MCG
Graphics Card: Intel 945GMA

Ubuntu 7.10 dual boot with WinVistaB
Neverwinter Nights plays well.  I just copied the files over from the Win partition, and applied the fixinstall.  I am also looking at switching TA over from Win also.
Getting the Broadcom 4311 to work was simple.  It just took a little bit of forum search.

---

### Post by vacadepollo on 2008-02-09
Model: Compaq Presario F545 EA
Processor: Amd Turion 64x2 1.6
Wireless Card: Broadcom 4311
Graphics Card: Nvidia GeForce 6100 Go
Gutsy Tribe (Version): 7.10 Alternate
Boot option:**_ pci=routeirq irqdebug_**

After many attempts with boot parameters: * noapic, noapic+irqpoll, noapic+irqpoll+noirqdebug, noapic+ irqpoll + pci=routeirq+noirqdebug+acpi_osi=!Linux*,.... i have found the correct boot parameters to usb works and kernel dont show errors of  Disabling IRQ 7 and/or cpus overloading, only with _**pci=routeirq irqdebug**_ the problem solved.

**Usb works and cpus rest in peace** XDXDXDXDXD!!!! No kernel errors!!!!!

[U]
nvidia works[/U] with restricted drivers 
_Broadcom works_ perfectly only installing this .deb: [http://debian.cafuego.net/pool/feisty-cafuego/bcm43xx/bcm43xx-firmware_1.3-1ubuntu2_all.deb](http://debian.cafuego.net/pool/feisty-cafuego/bcm43xx/bcm43xx-firmware_1.3-1ubuntu2_all.deb)  (doent works with ndiswrapper or ethernet active)
_Sound works_
_Bright works_
_Hotkeys works_


I'm very very happy with my usbs!!!!! finally!!!! :popcorn:


Now I'll attempt with hardy heron and this parameters (same problems with noapic and company.)...

---

### Post by Mr.Carioca on 2008-02-10
Model: Compaq Presario V6210 US
Processor: MK-86
Wireless Card: Broadcom BCM94311MCG
Graphics Card: Go 6150
Tribe (Version):32 bit I guess?
Boot Parameters (if any): Don't know, but just downloaded the .iso so it should be the lastest.

Alright, here is my problem.

Let me just make the story shorter:
I can't boot to the desktop, when the desktop starts to load I get this screen:
[IMG]http://i91.photobucket.com/albums/k311/DiscoveryVACEO/Picture001.jpg[/IMG]
Now I tried the Alt. installation, the instalation went fine but then when is time to load the desktop the white screen shows up again.

---

### Post by CPL Tack on 2008-02-10
Hi all,

Am new to Ubuntu and was very impressed by the install, and the compatibility.  I have an HP ZX5000 laptop that installed the ATI driver automatically, and it also installed the infamous broadcom driver that noone seems to be able to get to work.

I have a Broadcom BC4303 wireless 802.11B network card in the laptop.  It is able to find my home network but the WEP key does not seem to work.  I have compared with my other machine running wireless, and have never had a problem with the same WEP key I have used for years.  Any idea why the card seems to work but will not connect? By the fact the wireless finds my home network I believe it might be correct, but the lack of connection bothers me.  Also the wireless on/off button in the case does not work in ubuntu this far.  Any suggestions to steer me in the right direction would be greatly appreciated.  I have reviewed a lot of posts to make sure I wasn't posting duplicate question.  My problem isn't the lack of seeing my card, it's not the problem of finding the network. It's that I just can't get it to connect.

Thanks

Jay

---

### Post by cybo on 2008-02-11
Model: HP Compaq nx9110
Processor: Intel Pentium 4
Wireless Card: Broadcom BCM4306 802.11b/g
Graphics Card: ATI Mobility Radeon 9000 IGP
Gutsy Gibbon (Version): 7.10

I'm new to Ubuntu and barely know anything about it. It works fine but I have a problem with a wireless card. I won't enable. Here is what Restricted Drivers tell me after I click enable firmware:

The software source for the package bcm 43xx-fwcutter is not enabled. 

Can anyone advise what should I do? If possible in a step by step process since I'm VERY new to Ubuntu.

Thank you.

---

### Post by Malamus on 2008-02-12
Model: Compac nw8440
Processor: Intel Core 2.16GHz
Wireless Card: Broadcom BCM4312 802.11 a/b/g
Graphics Card: ATI FireGL V5200 (mobile)
Tribe (Version):32 bit 
Boot Parameters (if any):N/A

---

### Post by s0ullight on 2008-02-12
hello i got a hp G5002 ea 
had two partitions, deleted one and installed ubuntu 7.10
everything works fine except one thing:
my bcm 4311 card doesn't work
I succeeded those things about the firmware etc.
I see available networks in my neighboorhood
the only thing is i can't connect to them
i want the bcm43XX driver to work and not a windows emulated one with ndiswrapper
can someone just help me ubuntu is useless for me without internet ( i only have a wireless network) :(
tnx allready i know this community will help me ;]

---

### Post by Ayuthia on 2008-02-12
> **s0ullight said:**
> hello i got a hp G5002 ea 
had two partitions, deleted one and installed ubuntu 7.10
everything works fine except one thing:
my bcm 4311 card doesn't work
I succeeded those things about the firmware etc.
I see available networks in my neighboorhood
the only thing is i can't connect to them
i want the bcm43XX driver to work and not a windows emulated one with ndiswrapper
can someone just help me ubuntu is useless for me without internet ( i only have a wireless network) :(
tnx allready i know this community will help me ;]
Do you know which 4311 rev you have (lspci -nn)?  I am not for sure if you have tried to connect manually or not (by using iwconfig), but you might try that first.  You might also check dmesg to see if any messages come up when trying to connect.

---

### Post by s0ullight on 2008-02-13
it is revision 01
but now i got bigger problems 
tryed ndiswrapper anyway but 
now i can't see my wireless interface with ifconfig nor iwconfig :s
i'll probably reinstall ubuntu because it is quite fast (20 minutes for me last time :D)
but u can still post messeges :D 
:( ubuntu is useless for me without internet :'(

---

### Post by Ayuthia on 2008-02-13
> **s0ullight said:**
> it is revision 01
but now i got bigger problems 
tryed ndiswrapper anyway but 
now i can't see my wireless interface with ifconfig nor iwconfig :s
i'll probably reinstall ubuntu because it is quite fast (20 minutes for me last time :D)
but u can still post messeges :D 
:( ubuntu is useless for me without internet :'(

If you used ndiswrapper, which windows driver did you use (one from XP, from the HP site, or another driver)?  Also which version of ndiswrapper did you use (ndiswrapper -v)?  Also did you blacklist the bcm43xx driver in /etc/modprobe.d/blacklist?  bcm43xx and ndiswrapper do not play well together.  In some odd cases, ndiswrapper might not start up until you reboot.

If you are still going the bcm43xx route, does dmesg say anything about the bcm43xx driver?  If you have both ndiswrapper and bcm43xx installed, make sure that you blacklist ndiswrapper if you are using bcm43xx.  Also how have you tried to connect (did you use Network Manager or went to command line)?  Also, it might help to see what lshw -C network shows for your wireless.  It will tell you what drivers it is trying to use.

---

### Post by s0ullight on 2008-02-14
heh never mind 
but i did blacklist the bcm43xx driver
and used the xp sp... driver wich i downloaded from the hp site
but now i reinstalled ubuntu and i looked up some alternatives:
they got a new driver wich is named b43 
it has a lot of new functions
i need to install the kernel headers etc. 
to install it (compile :s)
if you want to you can search it too
if you can make it work plz let me know :D
tnx in advance :D

---

### Post by Cha1n5aW on 2008-02-14
Model: Compaq Presario 2105CA
Processor: AMD Athlon 1800+
Wireless Card: Linksys WPC54Gv2 & Netgear WPNT511 (both pcmcia)
Graphics Card: ATI Radeon 320M
Gutsy Tribe (Version): 7.10

Almost everything works great.  The only issue is that  I havent been able to get any external display to work (s-vid or vga).  I had some difficulty with my Linksys card the first time I installed, but it was because I had the card plugged in while installing.  Turns out, its best to install with nothing plugged into the pcmia slots.  Plug in any pcmcia devices after the installation is complete.  I've also found that the computer needs to boot with the pcmcia card plugged in, as nothing happens if I plug it in hot.  Ubuntu has native drivers for all the integrated hardware, and the Linksys card.  Unfortunately I had to use ndiswrapper and winXP airgo drivers for the Netgear card.  If anyone wants to see how I got that working, here is a link to that thread. 
[http://ubuntuforums.org/showthread.php?t=696903]("http://ubuntuforums.org/showthread.php?t=696903")
If anyone knows how to get my external displays to work, please pm me.  Aside from that I've very much enjoyed the Ubuntu experience thus far.

Thanks
- Shawn

---

### Post by ahorriblemess on 2008-02-15
Model:**HP Pavilion dv6704nr**
Processor: **AMD Athlon 64 X2 Dual-Core Precessor TK-57 and 512KB L2 Cache (1.9 GHz)**
Wireless Card:**Not sure actually, I had to do the ndiswrapper thing to get it working**
Graphics Card: **nVidia GeForce Go 7150M**
Boot Parameters: **If this means what I think it does, I couldn't boot the LIveCD unless I highlighted safe graphics mode, then clicked F6, then deleted "Quiet" and "Splash", moved the cursor to the spot just after the "--" and pressed Enter**

I was able to get the graphics and wireless cards working by following instructions on the dv6636nr (found on the forums) but I still can't get the speakers to switch off when I plug in my headphones. I just get sound out of both, and when I follow instructions, i always end up cutting out my sound card. I can't adjust the volume or anything because it says there is no driver recognized. 

OH... and another thing. Before going into xserver-xorg to get it to recognize my graphics card, I had to download the updates. I tried doing that before getting the updates, and I had problems with Gnome, the display wasn't working right. So... updates first, then tweak, that's how it worked for me.

---

### Post by sir4taye on 2008-02-15
> **EXCiD3 said:**
> By all means, go right ahead. As usually if it won't work in the Live CD, then it probably won't work after installation.

That's crap!! A lot of things that might not work on the liveCD can be configured and updated after installation. To address the restricted drivers not allowing functionality; try ndiswrapper to make restricted driver equipment work. 

Note this has worked for many with the broadcom 4311 and others, though if you have any other wlan than the broadcom you'll need the hardware specific .inf file for that hardware instead of the one you download in step 3 and turn on in step

everything inbetween # signs (without the #signs themselves) needs to be typed into a terminal screen (under applications then accessories then terminal -this is the command line, somewhat like dos)

1)you must uninstall ndiswrapper & bcm43xx-fwcutter

#sudo apt-get remove ndiswrapper-common ndiswrapper-utils-1.9#
#sudo apt-get remove bcm43xx-fwcutter#

2)Add bcm43xx to the /etc/modprobe.d/blacklist file

#sudo vi /etc/modprobe.d/blacklist#
a text editor will activate add this line "blacklist bcm43xx" (without "") by hitting i once and moving to the bottom and typing the new line then hit escape then enter ":wq" (without the "")

3)Reboot
#sudo reboot#

Download driver for BCM94311MCG wlan mini-PCI here:
http://www.stosha.net/WLANBroadcom.tar.gz or
http://stosha.stylet-software.com/WLANBroadcom.tar.gz

#cd ~/home/(yourusername)/Desktop#

#tar -xzvf WLANBroadcom.tar.gz#

4)move the folder WLANBroadcom (or other hardwaredriver folder) to your home directory

#mv WLANBroadcom/ /home/(yourusername)/#
(replace WLANBroadcom with the name of the file you need for your equipment)

5)Install ndiswrapper from source :

#sudo apt-get update#
#sudo apt-get install build-essential#
#sudo apt-get install linux-headers-`uname -r`#
#sudo ln -s /usr/src/linux-`uname -r` /lib/modules/`uname -r`/build#
#mkdir -p ~/bcm43xx/ndiswrapper#
#cd ~/bcm43xx/ndiswrapper#
#sudo wget http://downloads.sourceforge.net/ndiswrapper/ndiswrapper-1.49.tar.gz?modtime=1193538074&big_mirror=0#
#tar -xvzf ndiswrapper-1.49.tar.gz#
#cd ndiswrapper-1.49#
#make distclean#
#make#
#sudo make install#

6)Install windows driver (BCM94311MCG wlan mini-PCI) with ndiswrapper (or other windows driver as needed) 

#cd /home/yourname/WLANBroadcom/#
(if other than BC use name of file made in step 4)
 
#sudo ndiswrapper -i bcmwl5.inf#
(or other appropriate .inf file)

#ndiswrapper -l#

#sudo vi /etc/modules#
an editor will activate add this line by typing i then going to the last line press enter and type "ndiswrapper" (without "") then esc then :wq

#sudo modprobe ndiswrapper#

#sudo ndiswrapper -m#

7)Reboot
#sudo reboot#

____________________________________
Model: Presario f700 (f730us)
Processor: amd64 tk-55 1.6Ghz
Wireless Card: Broadcom 4311 mini-pci
Graphics Card: nVidia GeForce 6100 (64Mb shared mem)
Gutsy Tribe (Version): 7.10
Boot Parameters: noapic nolapic from liveCD

---

### Post by EXCiD3 on 2008-02-15
I'm sorry for the misunderstanding. I meant that if they didnt work on the livecd they wouldnt work out of the box after installation. Yes, you can get almost anything you want running given time and the tools. I didnt mean to discourage anyone. if you have any problems search the forums and google can usually find a solution to most things you may come across.

---

### Post by skinnie on 2008-02-16
sorry,wrong thread

---

### Post by brunoscunha on 2008-02-16
Model: hp-compaq 6910p
Processor: INtel Core 2 duo
Wireless Card: firmware forBroadcom 43xx chipset family (restrited driver)
Graphics Card: Mobile GM956/GL960 integrated graphics controller
Gutsy Tribe (Version): 7.10 installed from CD
Boot Parameters: (Only if extra boot options are needed in order to boot)

Wireless does not work at all, and the graphics card is detected as a generic card

---

### Post by haemphyst on 2008-02-17
[B]Model dv6444us
CPU  Core 2 Duo T2450 @ 2.0GHz w/ 2GB RAM
R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter[/B] *(Ricoh)*
**Toshiba 250GB 5400RPM HD** *(Toshiba, and entire drive capacity is dedicated)*
**R5C592 Memory Stick Bus Host Adapter** *(Ricoh)*
**R5C832 IEEE 1394 Controller** *(Ricoh)*
**R5C843 MMC Host Controller** *(Ricoh)*
**xD-Picture Card Controller** *(Ricoh)*
**PRO/100 VE Network Connection** *(Intel)*
**PRO/Wireless 3945ABG Network Connection** *(Intel)*
**Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller** *(Intel)*
**82801GBM/GHM (ICH7 Family) SATA IDE Controller** *(This will only function correctly if the BIOS is setup as a NON-RAID controller, i.e.NATIVE mode,  Cannot see the drive, if left in RAID mode.  I have not figured out any difference - there is only one drive bay.)*
**82801G (ICH7 Family) USB UHCI Controller #1 through #4** *(And so far, has hit every device I have plugged in.)*
**82801G (ICH7 Family) High Definition Audio Controller** *(Intel)*
**LG CDMA USB Modem**
**Apple iPos Classic, 160GB**


I had to do absolutely ZERO massaging after installation.  Out of the box, every device was nailed; I even didn't have to configure the LG cellphone modem (the vx-10000, aka "Voyager")  Now if I can get other apps to recognize it so I can use some of the apps for actually _*managing*_ the phone, I'll be ECSTATIC!!!  Any suggestions, anybody?

As I mentioned, the BIOS has a setting within, for RAID or NATIVE mode for the SATA controller.  Without the Compaq OEM XPPro image, even another XPPro install will not recognize the controller while in RAID mode...  A permanent yellow bang in device manager.  Not in an F6 install, not after installation...  Nowhere.  I even extracted the driver from the OEM XP install, and it will not install within XP anywhere...  It apparently ONLY works in the Compaq install of XP.

---

### Post by kavoura on 2008-02-19
I recently convinced a friend to install Ubuntu on her HP laptop (Omnibook xe4500) and we went ahead and did that. However, when the laptop boots up, the normal splash screen with the Ubuntu logo and the orange progress bar do not appear, instead the screen is just blank.

Model: HP Ominbook xe4500
Processor: Pentium 1.7 GHz
Wireless Card: none
Graphics Card: built in ATI
Gutsy Tribe (Version): 7.10, installed from a DVD-ROM that came with a magazine called Linux Format

I installed the same version of Ubuntu on my PC at home and have had no problems like this with it. I also did a second installation on another PC, which is also okay, but as the DVD-ROM comes with KDE files as well as Gnome, I set it up on the second PC as KDE and it loads up with the Kubuntu logo splash screen.

Anyway, on my friend's PC, being new to Linux, she chose to use KDE, as it is more like Windows than Gnome is.

But whether logging in using Gnome or KDE, the boot up sequence just gives a blank screen.

Sequence:
Turn on laptop, normal text appears and HP logo. 
Grub boot menu appears with Ubuntu and Windows XP listed.
Select Ubuntu or just wait to boot by default into Ubuntu.
Screen goes blank, but hard disk light is flashing.
After a while, the Ubuntu login screen appears, enter username and password and log in (no more problems with the screen), until logging out and shutting down, then screen goes blank again instead of seeing Ubuntu logo.

There is also another problem in OpenOffice. When running OpenOffice (in KDE), the icons on the toolbars are replaced with text. 

So, what can be done to fix these problems? I assume that there is a simple change to the Grub options in menu.lst that would fix the boot up screen?
But what about the OpenOffice problem? Is that caused by using KDE instead of Gnome? Is there an update or piece of software that needs to be installed to make OpenOffice work properly with Ubuntu running KDE?

---

### Post by archman on 2008-02-23
Model:nx6310 ey588es
Processor:intel celeron
Wireless Card:bcm4311
Graphics Card: onboard intel shared
Gutsy 7.10

First, install pack for building: sudo apt-get install build-essential
Installing dsl.... sudo pppoeconf
follow the instructions...

adding repos: in /etc/apt/sources.list add:

        deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy main universe restricted multiverse
	deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) gutsy free non-free
	deb [http://hr.archive.ubuntu.com/ubuntu/](http://hr.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
	deb-src [http://hr.archive.ubuntu.com/ubuntu/](http://hr.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

divx, mp3 support: on add/remove install ubuntu-restricted-extras, mplayer and audacious or xmms if you want...

bcm4311 works with ndis-1.52:
-------- 
# echo 'blacklist bcm43xx' | sudo tee -a /etc/modprobe.d/blacklist
-get ndis utils, common, ndisgtk via synaptics...
-cd to ndis source folder
# make uninstall
# make
# make install
-system->admin->win wireless drivers
insert bcmwl5.inf
# depmod -a
# modprobe ndiswrapper

bcm is on- see: tail /var/log/messages      (eth1?)    (check)

# echo ndiswrapper >> /etc/modules


56K MODEM (not sure if it works...)
---------------------------------------------

-get slmodemd source, cd to extracted folder
# chmod a+x slmodemd
# cp slmodemd /usr/sbin
# find /usr -name slmodemd        ---should only 1 new added
# modprobe snd-intel8x0m					?
# slmodemd --alsa -c CTR21EUROPE hw:0,6			?   -leave terminal, open new and:
# wvdial        ---- to dialout   (edit /etc/wvdial.conf for accounts)?


-enjoy in this beautiful ubuntu release !!!

---

### Post by mcdan on 2008-02-25
yeah, i have a presario v2000 with an AMD Sempron, and Gutsy is giving me some trouble.  it initially took 3 minutes to boot, and didn't recogonize my wireless card, the forums have helped me fix these problems, and y system is not up and running great.

---

### Post by themightymegatron on 2008-02-25
Don't ask me how I pulled this one off but here's what I've got: 


Model: Compaq Presario V2608WM
Processor: Mobile AMD Sempron 3000+ (Tops out at about 1.9GHz)
Wireless Card: Broadcom 4318
Graphics Card: ATI Radeon Xpress 200M 5955
RAM: 512MB
HDD: 80GB
Gutsy Tribe (Version): Gutsy 7.10 w/ Kubuntu & WinXP SP2

One thing that I found kind of useful in this setup was to eliminate the swap space entirely. I partitioned my hard drive to 10GB a piece for Ubuntu and XP. Then another 10GB to /home, and then, taking advantage of my new favorite OS's ability to read/write to NTFS, spent the last 50GB on an NTFS partition. Since I use this laptop for school purposes, and am too broke to upgrade even my ram, I kinda just dove in and hoped for the best. Turns out I seemed to have gotten it right, as I have my windows for school programs and such that sometimes don't like to run under wine, and then I've got Ubuntu, which I upgraded to Kubuntu recently. I had never used linux before this project started. I downloaded the Gutsy LiveCD, a copy of GParted, and took a crack at it. I've had nothing but success with Gutsy in the past 2 1/2 months since I installed it, and within the first week or so it was apparent I would only use windows when absolutely necessary, hahaha.

---

### Post by Superevil on 2008-02-26
Model: NC8230
Processor: Pentium Centrino 2.0 gHz
Wireless Card: Intel Wireless
Graphics Card: ATI Radeon Mobility x600
Gutsy Tribe (Version): I'm guessing 4. It's 32 bit.
Boot Parameters: Dual Booting with XP Pro

Everything is set up properly and working great except for the X600 card. I used Envy after the initial install to download and install the driver which I assume wasn't installed right because even though I can get some eyecandy (sliding minimize windows, fading when windows are closed, installed and setup KibaDock but was crashing when I turned physics on, also can't watch avi movies in full screen without lag), although I can't access the compiz settings anymore and I can't seem to access the ATI Control Panel because it says the driver isnt installed properly. How do I can check and make sure the driver is installed correctly?

---

### Post by motang on 2008-02-26
Model: dv5000z
Processor: Turion 64
Wireless Card: Broadcom
Graphics Card: ATi Xpress 200M
Gutsy Tribe (Version): 32bit
Boot Parameters: none really well I do dual boot but don't boot into Windows XP

Works like a charm.  I use my laptop on a daily basis, and it is very much usable, works very well with everything I throw at it weather it be media flies like MP3 or DiVX, surf the web with Opera or Firefox 3.0 Beta 3, chat with Pidgin, and work on homework when in school weather it be programming and write paper in OpenOffice Writer. XGL works so I got all the eye candy I could ask for.  All the extra buttons the laptop has works (volume up, mute, brightness, etc.).  I couldn't be happier with an OS.

---

### Post by johnnylavah on 2008-02-27
> **bones_83 said:**
> Model: HP Pavilion dv1000
Processor:1.7 Ghz Pentium M 
Wireless Card:Intel PRO/Wireless 2200BG

Ok I'm new to linux but Ubuntu is growing on me. I installed 7.10 as a dual boot on my notebook. Everything installed fine but I'm having the same problems everyone else is having...my wifi card detects networks but can't connect. I have browsed through the forum and people recommend using Feisty over Gutsy. My question is would installing Feisty over Gutsy be the best route for me???

did u ever get wifi working on your dv1000?

---

### Post by wm2 on 2008-02-28
Compaq Presario F755US
AMD Turion TL-58
Broadcom Wireless LAN

I just got this laptop on Monday. This is the first time I've ever put Linux on a computer. I've worked with it in the past, but never used it on one of my own machines. I'm dual booting with Vista Ultimate. I've gotten just about everything but the wireless working on this. Wireless works perfectly fine with Vista. I had a hell of a time trying to get the nvidia drivers working on this thing too. It still likes to go back to 800x600 when I restart. I've been reading solutions on here all day, but so far I have yet to find something to fix the wifi. At first I couldn't get the screen resolution above 800x600, but now it's playing nice at 1280x800.

---

### Post by keenwerkz on 2008-03-01
Model: HP dv2715
Processor: AMD Turion64 x2
Wireless Card: broadcom 4310 rev 01
Graphics Card: nvidia 7150m
Gutsy Tribe (Version): 7.10 amd64
Boot Parameters: 

installed right out of the live cd, no need for alternate cd,

installed nvidia-glx-new thru synaptics to get compiz running, 
installed ndiswrapper thru synaptics and used DELL drivers to get wireless card working
(for those who still can't setup search "dv2715" in ubuntuforums and the solution is there 


currently what's not running is the webcam (ive got no use for it though) -  - -  edit --->> runs just fine with ekiga without drivers

edit: i found out that if im using headphones my speakers are also working... :(

---

### Post by fatdadkev on 2008-03-02
HP 4200 Notebook (1gb ram, Pentium M processor 1.87ghz) 

Installed fine, I think the only thing I can't get to work straight out the box is the screen brightness sensor (I think it sets auto brightness if your in dim environment etc) but that's hardly going to be an issue. I can control it quite adequately with Fn-F9 and Fn-F10 just as I would with Windows and would most likely disable it anyway as every notebook I've ever used that has it has been annoying.

Graphics card is Intel Mobile 915GM
Wireless is Intel Pro 2200BG 
Bluetooth works
TPM appears to be detected but I'm not using the full features at the moment.

All in all it took about 45 mins to install 7.10 as the CD drive is USB on these machines. Once built everything works fine including Compiz i.e 3d cube etc.

Power management is fine, I have also enabled CPU scaling so I can over ride the CPU on demand scaling and manually set CPU i.e conservative mode, power mode, economy mode etc and can also lock it into a speed if required. All this works fine.

I messed around with it a lot and somehow set up an Xconf keyboard config that over rode the gnome config but that was no problem to sort out.

All in all it works perfectly and is totally stable,

---

### Post by maconlysource on 2008-03-05
Can you share how you enabled the scaling?

---

### Post by jebasan on 2008-03-05
Here my experience installing ubuntu gutsy on hp pavilion:
Model: 6629ca
Processor: 1.50 GHz Intel Centrino Core 2 Duo processor T5250
Wireless card: Intel Corporation PRO/Wireless 4965 AG or AGN (Bluetooth)
Graphic card: Intel Graphics Media Accelerator X3100 (shared) up to 384MB
Gutsy tribe (version): 7.10 AMD64
Integrated webcam, mic.
______________________________________________________________________________

I've run the live CD and test it and installed, first boot, everything worked out of the box! - but sound and webcam. 
as for webcam, i just have add the [Cheese] and configure the [ekiga softphone].works great! - My printer, HP4100 (all in one) also everything works out of the box. Wireless, network, cd/dvd recording, [microsoft wireless mouse], touch pad, [SD,MS,Pro,MMC,XD - memory cards] also worked out of the box, no problem at all!
The only problem i'm still having is with the sound and mic; they still not working althow i follow a few instructions found in the Forums.
To tell you the truth, i'm very happy with ubuntu in my Laptop and i just need to configure the sound to work so i can get rid of the windows "forever"!

Problems that i still have:

As i mentioned: 1) sound card not working.
		2) when i use the visual effects, if i'm surfing on the web, it freezes! the wlan0 still on and can see my IP but no packages came or go nowere. if i quit the visual effects, everything works geat.
		3) those are actually the only problem i'm having! :)

What did i do to make everything work? just read a lot on this forum and some information helped me a lot. I would like to help more, but i don'd have advanced knowlage to pass on, sorry folks! - here is my thought: i rather have my laptop with no sound (for now) and no WINDOWS. Ubuntu rocks!

---

### Post by midboe on 2008-03-06
[B]Model: NC6400
Processor: Intel Core 2 Duo Processor T7200 (2.0-GHz, 667-FSB, 4-MB L2 cache)*
Wireless Card: Broadcom NetXtreme Gigabit Ethernet PCI Express Controller
Graphics Card: ATI Mobility Radeon X1300
Gutsy Tribe (Version): 7.10
[/B]

Installation worked like a charm... :) I use the fglrx driver with compiz and emerald. USB, fingerprint scanner, external display through dock, SD-card reader and soundcard works perfect.
A couple of things that I'm not satisfied with:
Fan goes at high speed all the time...
Sleep function does'nt work.
Ubuntu eats my battery under an hour.

---

### Post by archman on 2008-03-06
> **archman said:**
> Model:nx6310 ey588es
Processor:intel celeron
Wireless Card:bcm4311
Graphics Card: onboard intel shared
Gutsy 7.10

First, install pack for building: sudo apt-get install build-essential
Installing dsl.... sudo pppoeconf
follow the instructions...

adding repos: in /etc/apt/sources.list add:

        deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy main universe restricted multiverse
	deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) gutsy free non-free
	deb [http://hr.archive.ubuntu.com/ubuntu/](http://hr.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
	deb-src [http://hr.archive.ubuntu.com/ubuntu/](http://hr.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

divx, mp3 support: on add/remove install ubuntu-restricted-extras, mplayer and audacious or xmms if you want...

bcm4311 works with ndis-1.52:
-------- 
# echo 'blacklist bcm43xx' | sudo tee -a /etc/modprobe.d/blacklist
-get ndis utils, common, ndisgtk via synaptics...
-cd to ndis source folder
# make uninstall
# make
# make install
-system->admin->win wireless drivers
insert bcmwl5.inf
# depmod -a
# modprobe ndiswrapper

bcm is on- see: tail /var/log/messages      (eth1?)    (check)

# echo ndiswrapper >> /etc/modules


56K MODEM (not sure if it works...)
---------------------------------------------

-get slmodemd source, cd to extracted folder
# chmod a+x slmodemd
# cp slmodemd /usr/sbin
# find /usr -name slmodemd        ---should only 1 new added
# modprobe snd-intel8x0m					?
# slmodemd --alsa -c CTR21EUROPE hw:0,6			?   -leave terminal, open new and:
# wvdial        ---- to dialout   (edit /etc/wvdial.conf for accounts)?


-enjoy in this beautiful ubuntu release !!!

edit: modem WORKS !!!

you have to: slmodemd --alsa -c CTR21EUROPE hw:0,6

leave terminal opened running, open new terminal and wvdial !

---

### Post by Taoye on 2008-03-11
Please post the following things:
Model: HP / Compaq nc8000
Processor: Intel Pentium M Centrino 1.5GHz processor
Wireless Card: Intel PRO Wireless 2100
Graphics Card: Mobility Radeon 9600
Gutsy Tribe (Version): v7.10 32-bit
Boot Parameters: n/a

2 issues:

The wireless has a connectivity issue-- I haven't delved too deeply into the problem but after a while the connection drops and I seem to have to reboot the laptop to get it working again.

For some reason the processor is working all the time. If I leave it alone but turned on for a few hours I will come back to find it very hot with the fan going consistently. Not sure if this is an issue with the laptop itself or if Ubuntu isn't idling well...

---

### Post by cmburch on 2008-03-11
Model: HP dv1000
Processor: Intel Pentium M processor 1.60GHz
Wireless Card: Intel Pro Wireless 2200 b/g
Graphics Card: Intel Mobile 915 / 910 Express Graphics Controller
Gutsy Tribe (Version): 7.10


No problems with installation or with wireless.  I've had some problems with the system randomly shutting itself down.  Other than that, seems to be going well.

---

### Post by Mursalin on 2008-03-12
**Model:** Pavilion dv2500 
**Processor:** Intel Core 2 Duo processor 2.2 GHz (2 GB RAM)
**Wireless Card:** Intel PRO/Wireless 3945ABG
**Graphics Card:** nVidia GeForce 8400M GS
**Gutsy Tribe (Version):** 7.10

Almost all works perfectly after installation. But there are some things that I still can't  figure out to work;
1. 5 in 1 cards reader (SD-MS/MS Pro-MMC-XD) 
>> I have an OLYMPUS camera using an XD picture card. (Window$) Vista reads the card immediately when I insert the XD card into the slot, but under Ubuntu (until now) the card's un-read/mount-able.
2. Fingerprint scanner
>> Is there any program required for Ubuntu to make the fingerprint usable? 
3. Sound
>> Sometime after switching from Vista to Ubuntu, the sound wont work. I can overcome it by shooting down the laptop and powering it on again, while the usual restart still give no sound.
Other than that, all works fine. By the way, yess; I'm dual-booting Ubuntu with Vista. But surely I'll get rid that OS (Window$) off, someday.
[Is my English that bad, guys?]

---

### Post by EXCiD3 on 2008-03-12
> **Mursalin said:**
> **Model:** Pavilion dv2500 
**Processor:** Intel Core 2 Duo processor 2.2 GHz (2 GB RAM)
**Wireless Card:** Intel PRO/Wireless 3945ABG
**Graphics Card:** nVidia GeForce 8400M GS
**Gutsy Tribe (Version):** 7.10

Almost all works perfectly after installation. But there are some things that I still can't  figure out to work;
1. 5 in 1 cards reader (SD-MS/MS Pro-MMC-XD) 
>> I have an OLYMPUS camera using an XD picture card. (Window$) Vista reads the card immediately when I insert the XD card into the slot, but under Ubuntu (until now) the card's un-read/mount-able.
2. Fingerprint scanner
>> Is there any program required for Ubuntu to make the fingerprint usable? 
3. Sound
>> Sometime after switching from Vista to Ubuntu, the sound wont work. I can overcome it by shooting down the laptop and powering it on again, while the usual restart still give no sound.
Other than that, all works fine. By the way, yess; I'm dual-booting Ubuntu with Vista. But surely I'll get rid that OS (Window$) off, someday.
[Is my English that bad, guys?]

This tutorial might be somewhat helpful for you. Its based off my HP Tutorial but he has added lots of information for the HP laptops in general: [SIZE=-1]http://aldeby.wordpress.com/2007/09/11/howto-ubuntu-on-hp-dv65xx-series-laptop/[/SIZE]

---

### Post by csents on 2008-03-13
Sorry, I don't know all the specs for sure on my laptop but I'll try
Model: Compaq Presario V4000
Processor: 1.7 GHz Pentium M
Wireless Card: PRO/Wireless 2200BG Network Connection
Graphics Card: unknown
Gutsy Tribe (Version): Latest as of 3/08 (ubuntu 7.10)
I'm pretty sure the hardware's the same for this model of Compaq so anyone else with it should get a pretty good idea

Most everything seems to work fine out of box, which is good cause I'm pretty much a n00b when it comes to linux if you haven't noticed already.  The first time I tried to install, I had some trouble with the partitioner, so I went back into Windows, got rid of all unnecessary files, defragged the drive again, and it worked fine the second time.  Everything I've checked works fine with no extra help (VGA port, ethernet, wireless, USB peripherals, sound and monitor), but there are a few things I haven't tried yet, most notably the s-video port and dial-up jack that other people have had trouble with.  The Wireless wizard light or whatever it is doesn't light up, but I never really saw the point of that anyways.

Hope this helps!

---

### Post by shivam.seth on 2008-03-21
**Model:** Compaq V3155AU
**Processor:** Amd Turion 64 X2 1600 Mhz
**Wireless Card:** [COLOR="Red"]Broadcom Corp BCM 94311MCG wlan mini-PCI (eth1)[/COLOR]
**Graphics Card:** [COLOR="Red"]nVidia Corp C51 Motherboard with **Geforce Go 6150 graphics card**[/COLOR]
**Gutsy Tribe (Version):** I don't really know .... I am very new to Ubuntu(...or Linux)

***_Main Problem _:-***
I am not able to get my wLan card working. I have loaded bcm43xx-fwcutter properly and extracted firmware to it properly too. My wLan lights have turned blue from orange too but it still cannot detect any network. A friend got it working somehow using some tutorial on Ubuntu Forum itself a few months back but I had to reformat and reinstall Ubuntu again. **The problem that persists here is that every time my computer boots, it loads b44 drivers instead of b43.** I want to know how to edit and correct that problem!

***_Less Important Problem_ :-***
After I have loaded the nvidia-glx-new package for my graphics card, my computer takes more time to login and for opening any window such as xterm or even to show home directory. Can you help me with this problem too. I have a 512 MB DDR2 ram and a 80 GB harddrive. Tell me if you need any other information!
[COLOR="SeaGreen"][B]
Hoping a prompt response as I am doing a project on wireless which requires my wLan card to work properly![/B][/COLOR]

---

### Post by troupa on 2008-03-21
**Model:** HP Pavilion 9500 series model dv9617nr
**Processor:** AMD Athlon(tm) 64 X2 Dual-Core Processor TK-53
**Wireless Card:** Broadcom bcm94311mcg
**Graphics Card:** Nvidia GeForce Go 7150M

The Fn Brightness keys for the display backlight _***do***_ work.  I've seen quite a few posts about them not working on other laptops so I thought I'd start off with that.

Wireless:  Had to blacklist the bcm43xx module and use ndiswrapper and the bcmwl5 driver.  I found instructions at  [[COLOR="Blue"]THIS SITE[/COLOR]]("http://invaleed.wordpress.com/2007/11/20/install-bcm94311mcg-wlan-mini-pci-ubuntu-710/").
Anyone with the Broadcom 94311MCG card should be able to use those instructions.  It works perfectly now.

Installation notes:  Could only get to 800x600 graphics on liveCD to install, but upon first boot and installing the nvidia-glx-new (and related) packages, the screen resolution was brought to its full 1440x900 with hardware acceleration.  Compiz worked like a dream.

This notebook comes with a 23-button infrared remote control.  The volume buttons work correctly and do not change depending on which application has focus.  Most of the other buttons depend on what application has focus.  For example, the directional arrows will skip forward/backward if mplayer has focus.  The "Windows Media Center" button opens Rhythmbox.  I'm not sure if there's a way to change that or not.  The "DVD" button does not do anything, and neither does the button normally assigned to HP QuickPlay.  

Other than having to do a bit of configuring for the wireless card (which is usually to be expected anyway), everything works as it should.  Pretty happy with it.  

As an afterthought:  I use metacity instead of compiz so I'm not sure how that effects it, but the battery lasts almost twice as long as it did using Windows Vista.

---

### Post by shivam.seth on 2008-03-22
Ndiswraper will work but it won't give as good signal strength as the native bcm43xx-fwcutter. My project is based on wireless signal strength measurement and that's the reason I want a solution for bcm43xx drivers specifically. Since I have done it before I know we can do it. The problem with it as I figured it the last time is that when Ubuntu logs in, it loads b44 drivers instead of b43. We need to edit the file which loads all the drivers on starting. We need to load b43 drivers instead of b44. We did it last time by using alias command. But I cannot recall how we did it! Hope this will narrow up my question ......

**Which file loads all the drivers when Ubuntu starts and how to edit it to load b43 instead of b44 drivers???**

---

### Post by kjuliano on 2008-03-22
i would like to revise my original post.

the sound is working funny in hardy.

it is connecting the internal speaker volume to the main volume instead of leaving it separate.

in gutsy this was not a problem.

so if my system volume is high and i try using say tab complete at a console i get a horrible internal speaker beep thats really obnoxious and loud.

[edit] this should of gone in a different thread  for gutsy acpi_cpufreq doesn't work

---

### Post by shivam.seth on 2008-03-23
I think I got what I have been searching for .....[COLOR="SeaGreen"]**THE SOLUTION**[/COLOR]

After installing bcm43xx-fwcutter and extracting the firmware. Reboot! If your wLan light turned ON, then this should work for you as well ....

Run **echo 'blacklist bcm43xx' | sudo tee -a /etc/modprobe.d/blacklist**

This should do the job. Reboot after doing so and try connecting. 

I still have to try it myself. I will come back to this thread with my results tomorrow!

I got this solution from [http://ubuntuforums.org/showthread.php?t=649038&highlight=solved+b43]("http://ubuntuforums.org/showthread.php?t=649038&highlight=solved+b43")

This thread might further help you!

---

### Post by Drittponken on 2008-03-24
Model: HP Compaq nc6000
Processor: Intel Pentium M  1.60Ghz
Wireless Card: AR5212/AR5213    (Don't know really)
Graphics Card: Ati Mobile Radeon 9600
Gutsy Tribe (Version): don't know. i'm kind of a noob ^^ 
Boot Parameters: none


Most thing work fine out of the box.

Bibernate doesn't work, neither suspend.

---

### Post by vijaym on 2008-03-26
Model: HP Pavilion dv 661ei
Processor: AMD Athlon tk-55 1.8Ghz
wireless card: Broadcom bcm94311g
Graphics Card: nVidia GeForce  7150m
Gusty: 32 bit - as too many problems with 64 bit
Boot parameters: none

Boots ok, no wireless tried all sorts things with no luck. At some stage the orange light went blue without being able to link to the wireless router.

Then reinstalled vista to do dual boot so that I can have wireless when travelling and when linking to some hardware without having to reconfigure ubuntu to work with printers or data projectors etc.

screen resolution does not stay fixed. have used envy as well as the restricted drivers manager with no luck

Otherwise it works well. sound fine, have not tried the lightscribe thingy, but DVDs copy ok

---

### Post by mcframe on 2008-03-28
Model:2710p
Core Duo U7600 2x 1.20GHz ULV &#8226; 2048MB (2x 1024MB) 
Intel PRO/Wireless 4965 802.11abg
Intel GMA X3100 onboard Grafik max.384MB shared memory 
Bluetooth &#8226; SD-Card Slot &#8226; FingerPrint Reader &#8226; Web-/Videokamera (2.0 Megapixel) &#8226; 12.1" WXGA+ TFT (1280x800) &#8226; Wacom Tablet LCD &#8226; HS2300 HSDPA/UMTS/GPRS Modem, HP softmodem, 

Installation with (K)ubuntu Gutsy Gibbon 7.10
CPU - works out of the box
Sound - works out of the box  
WLAN - works out of the box with (k)networkmanager, (module iwl4965)  
LAN works out of the box
HSDPA Modem: is a Sierra Wireless, Inc. Model: MC8775 
sudo modprobe usbserial vendor=0x03f0 product=0x1e1d 
Bluetooth - works out of the box
Fingerprint Sensor - untested
Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter works after patching sdhci module
USB Ports work out of the box
Firewire works out of the box  
Webcam is a Chicony 04f2:b018 works with UVC driver
ACPI works out of the box, suspend and hibernate need a 'blacklist video'  in /etc/modprobe.d/blacklist 
Some special keys for the tablet mode are not accessible

---

### Post by CarolinaGirl on 2008-04-06
Hp Pavilion zd8000
CPU Intel P4 - 3.4GHz
Memory 2GB
Video ATI Mobility Radeon x600
Wireless Broadcam 802.11b/g WLAN

I think that's everything. Anyway, here's my delima: 
I downloaded the -iso- torrent file from unbuntu.com, as far as my computer knew, everything was good. I used MSFT's cdburn to make a bootable cd. It will load the browser when in Win Xp, BUT...

When I boot from the aforementioned CD, a couple of things happen:
1st- There flash on the screen three lines saying something about not being able to do something with "Region 6, 7 and 8" (one per line), but it goes on the the installer/check screen. 
2nd- When I do the CD check, I get 1 file bad, I've burned it twice, and I get the same thing. 
3rd- If I tell it to go ahead and install, it looks good, but it's asking for a UserName and PassWord, which, of course, I have no clue as to what it should be.

I tried downloading the files fromo GaTech and ANL, and both of THEM are hosed - Heck, I've even tried Kunbuntu (7.10) and my HP doesn't seem to loke that either

---

### Post by ardnetih on 2008-04-07
Please post the following things:
Model: Presario 2800
Processor: Pentium 4-M 1.4GHz
Wireless Card: DLINK DWL-G600 (Atheros chipset)
Graphics Card: Radeon Mobility 7500 (RV200)
Gutsy Tribe (Version): 7.10
Boot Parameters: (Only if extra boot options are needed in order to boot)

What works:

* Atheros WLAN (DLINK DWL-G600 PCMCIA card)
* volume up/down keys
* Headphone plug recognition (when activated in control panel)
* Info key (brings up help)
* fn+F8 (battery state key)
* fn+f9..f11 brightness 1/-, contrast
* Lid closed key
* Num Lock (with LED); embedded numeric keys
* Touchpad
* USB mouse

What does not work:

* I upgraded from 7.04 (Fiesty) to 7.10 (Gusty) and no matter what I tried, i couldn't get my screen resolution above 800x600. In Fiesty I had it working fine on 1024x768 but upgrading to Gusty broke that. I had a saved copy of xorg.conf and tried making the same changes to the file in Gusty but no go. I am still looking for a solution for this, so if anyone has figured it out please let me know. 
* The laptop gets too hot at times and I found a small solution for that which worked fine for me: Turn off the desktop tracker (System > Preferences > Indexing Preferences)

I will update this as I make more progress with this.

---

### Post by rahul_rocks on 2008-04-07
Hi Friends,

I am having HP Pavilion dv 2519 i have installed Ubuntu 7.10 on my machine
My graphic card is:
Mobile GM965/GL960 Integrated Graphics Controller


By mistake i have changed the graphic card driver. Now my machine is accepting only default vesa drivers. So i am not able to run compiz and all other visual effects in terminal compiz shows result:-

Checking for Xgl: not present. 
No whitelisted driver found
SKIP_CHECKS is yes, so continuing despite problems.
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: not present. 
SKIP_CHECKS is yes, so continuing despite problems.
Checking for nVidia: not present. 
Checking for FBConfig: Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
not present. 
SKIP_CHECKS is yes, so continuing despite problems.
Checking for Xgl: not present. 
Starting emerald
Xlib:  extension "GLX" missing on display ":0.0".
/usr/bin/compiz.real (core) - Fatal: Root visual is not a GL visual
/usr/bin/compiz.real (core) - Error: Failed to manage screen: 0
/usr/bin/compiz.real (core) - Fatal: No manageable screens found on display :0.0

Kindly help me to reload the Intel Drivers and run compiz
thanks

---

### Post by ryofire on 2008-04-09
Model: HP pavillion DV5120us laptop
Processor: AMD Turion 64bit
Wireless Card: BCM4318
Graphics Card: RADEON XPRESS 200M

The Good:
It works, is fast and stable.

The Bad:
Hibernate and Standby JUST DON'T WORK.

The Ugly:
Wireless is a confusing process to install but works perfectly with ndiswrapper. Use the following thread, but realize that if the script doesn't work for you (it didn't for me) you can still open it with a text editor and follow it step by step (worked every time I tried it).

[HOWTO/SCRIPT: Broadcom 4318 Wireless Cards]("http://ubuntuforums.org/showthread.php?t=197102")

---

### Post by Lazy-buntu on 2008-04-09
I'm having difficulties with my gutsy install, im currently downloading the iso for feisty, i think i'll try feisty if no one can help me with my current problem:


> **Lazy-buntu said:**
> I was reading [http://ubuntuforums.org/showthread.php?p=4684447&posted=1#post4684447](http://ubuntuforums.org/showthread.php?p=4684447&posted=1#post4684447)

Is feisty a better choice for HP laptops? I posted a reply on that thread:


my original problem: [http://ubuntuforums.org/showthread.php?p=4674415#post4674415](http://ubuntuforums.org/showthread.php?p=4674415#post4674415)

---

### Post by nnamdi on 2008-04-09
Model: HP Pavilion dv6000
Processor: intel centrino Duo 1.67Ghz
Wireless Card:  Intel Corporation PRO/Wireless 3945ABG Network
Graphics Card: Intel Corporation Mobile GM965/GL960 Graphics
Gutsy Tribe (Version): 4 32bit
Kernel Options: None

after installing it my sound was not working and graphics card was blacklisted but every other thing worked out of the box

---

### Post by CheshireMac on 2008-04-09
Exactly the same issue . . . worried that my lappy may be toast, but if it's a common thing, maybe there's a fix? I'm experiencing both problems, although I don't reboot the system to get back on. I only have to reconnect through my tray-manager.
The machine itself is always on though, as you said above. It gets pretty hot. Worried it may burn out soon . . . is this just an issue with age or malnutrition?

---

### Post by sharp65 on 2008-04-10
Model: HP Pavilion dv6500t
Processor: Intel Core 2 Duo T7300 @ 2.0GHZ
Wireless Card: Intel  PRO/Wireless 3945ABG Network
Graphics Card: NVIDIA 8400M GS
Gutsy Tribe (Version): 32bit

Install went very smoothly, I partitioned my vista ultimate drive using ubuntus installer and it was quick and painless. After installing everything was picked up in terms of drivers except for sound, I tried so many different things and couldn't get any sound. After hours of searching I got it working, I have a realtek acl268 card and you just need to go [here]("http://www.realtek.com.tw/Downloads/downloadsView.aspx?Langid=1&PNid=14&PFid=24&Level=4&Conn=3&DownTypeID=3&GetDown=false") and download the linux driver(2.4 or 2.6) and let that install. Now everything is working great

It does seem to be running pretty hot though, Ill have to keep an eye on it.

---

### Post by Ayuthia on 2008-04-10
> **sharp65 said:**
> Model: HP Pavilion dv6500t
Processor: Intel Core 2 Duo T7300 @ 2.0GHZ
Wireless Card: Intel  PRO/Wireless 3945ABG Network
Graphics Card: NVIDIA 8400M GS
Gutsy Tribe (Version): 32bit

It does seem to be running pretty hot though, Ill have to keep an eye on it.

I thought that I read somewhere that there was a BIOS update that helped fix the fan speed.  Not for sure if yours is up to date or not.  Also, can you post your temps?  There might be others here that might be able to tell you if yours is running too hot or not (or provide others an idea about if their laptops are running hot).

---

### Post by Elmer Fudd on 2008-04-13
In case it helps anyone.
Hp dv9000t
Running 7.10
Intel 3945ABG

No sound or wireless running 386 version (wireless shows UNCLAIMED)
Everything works fine with Generic version if I blacklist ipv6.

---

### Post by PeterWD on 2008-04-15
Model: dv6244eu
Processor: Turionx2 1.6Ghx
Wireless Card: (not sure, it's broken anyway)
Graphics Card: Nvidia 6100 integrated
Gutsy Tribe (Version): 7.10 amd64
Boot Parameters:

My key problem is an issue with the sound system, the only sound that comes through my speakers is a constant *ba-dunk ba-dunk ba-dunk* which I assume is the first fraction of the startup tone repeated ad infinitum. Given that this machine is:

a) Overwriting my buggy-as-hell Vista install because it locked me out as a pirate and wouldn't let me in again (and as such I am a Total newbie).
b) intended as my music store and internet browser only

it's something of a problem. Anyone know of a fix for this? I did a quick search but didn;t see anything.

The other problem I have is that I can't get Flash to install. Firefox repeatedly claims to have installed it but it doesn't actually WORK...

This is probably because I'm really new and haven't really got the hang of it yet (though I'm using the tutorials on this site) but if anyone knows some easy solutions that's be awesome.

Thanks in advance

---

### Post by Lazy-buntu on 2008-04-15
Gutsy was horrible for my HP Pavillion dv6308, messed around with wireless for a week, reformtatted many times, now I use PCLOS 2008 Gnome--which didn't even require manual installation of ndiswrapper or the bcmwl5.inf driver

just went to configure my computer, network/internet, wireless, ndiswrapper, chose bcmwl5.inf, popped in my WEP key and bam had wifi (didn't even had to reboot)

---

### Post by braveerudite on 2008-05-19
Ubuntu 8.04 64 bit

 Presario F756NR (laptop)

Wireless is not working (I hate you Atheros)

Everything else works

---

### Post by EXCiD3 on 2008-05-19
> **braveerudite said:**
> Wireless is not working (I hate you Atheros)

Everything else works

Which atheros card do you have? Glad to see everything else works though!

---

### Post by braveerudite on 2008-05-20
> **EXCiD3 said:**
> Which atheros card do you have? Glad to see everything else works though!

Been trying to get Atheros AR5007 802.11b/g internal wireless to work under Ubuntu 64-bit 8.04


No luck so far :(

[Here is a list of Vista 64 drivers for my Compaq Presario F756NR]("http://h10025.www1.hp.com/ewfrf/wc/softwareList?os=2100&lc=en&cc=us&dlc=en&product=3646836&lang=en#")

---

### Post by EXCiD3 on 2008-05-20
> **braveerudite said:**
> Been trying to get Atheros AR5007 802.11b/g internal wireless to work under Ubuntu 64-bit 8.04


No luck so far :(

[Here is a list of Vista 64 drivers for my Compaq Presario F756NR]("http://h10025.www1.hp.com/ewfrf/wc/softwareList?os=2100&lc=en&cc=us&dlc=en&product=3646836&lang=en#")

You might want to try out this tutorial: [http://www.ubuntugeek.com/atheros-ar5007-wireless-with-madwifi-on-ubuntu-804-hardy-heron.html](http://www.ubuntugeek.com/atheros-ar5007-wireless-with-madwifi-on-ubuntu-804-hardy-heron.html)

---

