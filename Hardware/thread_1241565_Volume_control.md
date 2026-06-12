---
title: "Volume control"
date: 2009-08-16
forum: Hardware
---

### Post by AmerNewbieInDE on 2009-08-16
i have noticed that when a sound or video plays, it is very quiet. I have an Acer Aspire 8730 notebook with the nvidis HiDef sound and Realtek sound devises.. any ideas? I already went through the sound toolbar and all the slides are all the way to max. also this notebook keyboard has a touch volume control on the right side, the mute works, but the slide control makes no differeence.

---

### Post by kiridude on 2009-08-16
Have you had this problem since you installed Ubuntu, or did it happen "out of the blue?"

Also, are you double booting with Windows?

---

### Post by AmerNewbieInDE on 2009-08-16
i have had it since install.. been trying to fix it but cant, i installed the realtek drives already and didnt help. 

Maybe you can concider that i dual boot. Windows is on the internal drive. Ubuntu is on an external sata drive with its boot loader. My pc boots off USB first, so if the external is plugged in, it boots to linux, it the external is unplugged, it boots directly to windows.

---

### Post by kiridude on 2009-08-16
I asked because on some machines if the volume is turned down in Windows, it will stay down in Linux. Try turning all the volumes to max in Windows, then try again in Ubuntu.

---

### Post by Ing.M.V. on 2009-09-28
> **AmerNewbieInDE said:**
> i have noticed that when a sound or video plays, it is very quiet. I have an Acer Aspire 8730 notebook with the nvidis HiDef sound and Realtek sound devises.. any ideas? I already went through the sound toolbar and all the slides are all the way to max. also this notebook keyboard has a touch volume control on the right side, the mute works, but the slide control makes no differeence.

I have an ACER ASPIRE 8730, too. Same problem with volume touch control.

Any Idea to fix it??

---

### Post by mvalenti on 2009-11-06
Nice machine, I have one as well. I have yet to find a fix for the touch volume slider. Sound is awesome otherwise. What I mean by that is I have to use the volume control on the desktop.

---

### Post by Ing.M.V. on 2009-11-23
Any news about how to fix the volume keys problem????

---

### Post by alexfish on 2009-11-23
> **Ing.M.V. said:**
> Any news about how to fix the volume keys problem????
hi 
 thanks in advance / could you post your system with info/

laptop model/ ubuntu " version" 64 bit or 32 bit / / clean install or up grade

 also try this from the terminal and post the results if possible

from the terminal

aplay -l

also look here item 9  .... please read all

[https://help.ubuntu.com/community/SoundTroubleshootingProcedure](https://help.ubuntu.com/community/SoundTroubleshootingProcedure)

---

### Post by mvalenti on 2009-11-23
Intel® Core™2 Duo Processor T6500 
(2MB L2 cache, 2.10GHz, 800MHz FSB) 
or
Intel® Core™2 Duo Processor P8600 
(3MB L2 Cache, 2.40GHz, 1066MHz FSB) 
or
Intel® Core™2 Duo Processor T6400 


 
Chipset  Mobile Intel® PM45 Express 


 
Memory  4GB (2GB installed in each of two memory slots) DDR2 667 SDRAM 


 
Storage  Up to 320GB* hard disk drive 

Integrated variable-speed Super-Multi drive: 
-Read - 24X CD-ROM, 24X CD-R, 24X CD-RW, 8X DVD-ROM, 8X DVD-R, 8X DVD+R, 6X DVD-ROM DL (double-layer), 6X DVD-R DL (double-layer), 6X DVD+R DL (double-layer), 6X DVD-RW, 6X DVD+RW, 5X DVD-RAM 
-Write - 24X CD-R, 16X CD-RW, 8X DVD-R, 8X DVD+R, 4X DVD-R DL (double-layer), 4X DVD+R DL (double-layer), 6X DVD-RW, 8X DVD+RW, 5X DVD-RAM 

6-in-1 card reader supports optional MultiMediaCard™, MMCplus™, Secure Digital card, Memory Stick®, Memory Stick PRO™ or xD-Picture Card™ 

Optional external USB 1.44MB* diskette drive 

*When referring to storage capacity, GB stands for one billion bytes and MB stands for one million bytes. Some utilities may indicate varying storage capacities. Total user-accessible capacity may vary depending on operating environments. 


 
Video  Acer® CineCrystal HD+ 18.4" WXGA+ (1680 x 945) TFT LCD 

16:9 aspect ratio, 8ms high-definition response time 

Discrete NVIDIA® GeForce® 9600M GT (512MB dedicated GDDR3 VRAM memory, up to 1791MB shared system memory) 
or
Integrated Intel® Graphics Media Accelerator 4500MHD 

Windows® Media Video 9 (VC-1 standard) and H.264 support 

MPEG-2 DVD decoding 

Acer® Video Conference with integrated high-definition Acer® Crystal Eye webcam supporting Acer® PrimaLite technology, which consists of a premium sensor, firmware and lenses to provide superior video performance under low-light conditions 

VGA, HDMI™ (High-Definition Multimedia Interface™) with HDCP (high-bandwidth digital-content protection) support ports 

Up to 16.7 million colors 

Support for simultaneous display on notebook LCD and external monitor 


 
Audio  Dolby®-optimized surround-sound system with two integrated stereo speakers and one subwoofer supporting low-frequency effects 

Integrated microphone 

Optimized second-generation Dolby® Home Theater audio enhancement 

True 5.1-channel surround-sound output 

Headphones/speaker/line-out with SPDIF support, microphone-in and line-in ports 

Microsoft® DirectSound® compatibility 

Acer® MediaTouch volume meter 

Interface Ports  DC-in 
RJ-11 modem 
RJ-45 LAN 
VGA 
Headphones/speaker/line-out with SPDIF support 
Microphone 
Line-in 
HDMI™ (High-Definition Multimedia Interface™) with HDCP (high-bandwidth digital-content protection) support 
CIR (consumer infrared) 
Four USB 2.0 


 
Card Slots  ExpressCard™/54 slot 

6-in-1 card reader supports optional MultiMediaCard™, MMCplus™, Secure Digital card, Memory Stick®, Memory Stick PRO™ or xD-Picture Card™ 


 
Communications  Intel® Wireless WiFi Link network connection supporting 802.11a/b/g/Draft-N wireless LAN, Acer® SignalUp technology for enhanced antenna efficiency, WI-FI CERTIFIED™ 

Bluetooth® 2.0 + EDR (enhanced data rate) wireless PAN (select models only) 

Gigabit LAN, Wake-on-LAN ready 

V.92 56Kbps* data/fax modem, PTT (postal, telegraph, telephone) certified in select countries, Wake-on-Ring ready 


At least with my system, I am running Ubunti 9.04 (64 bit), clean install. Dual boot with Windows xp64.

---

### Post by alexfish on 2009-11-23
hi 

re item 9 from last post

extract

If you are using a dual boot system (even with Windows and Ubuntu installed on separate partitions), then make sure to set the sound volume in Windows to a high level before booting into Ubuntu. Also make sure to use the special function keys in Windows to make sure the loudspeakers are physically switched ON and working properly in Windows before installing and testing Ubuntu. This step is necessary with certain Toshiba Tecra laptops.

may be same problem 
 also 

try this
from the terminal

aplay -l 

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 6: Si3054 Modem [Si3054 Modem] <--------This one
   Subdevices: 0/1
  Subdevice #0: subdevice #0


 if looks something like this 

you may be able to disable the driver 
or
 try to disable the software modem in the bios 

      also search site with the info it  gives

 there is a link here for laptops with hardware problems

[http://ubuntuforums.org/showthread.php?t=361237](http://ubuntuforums.org/showthread.php?t=361237)

---

### Post by mvalenti on 2009-11-23
Will try that when I get home, will post results! Thanks!


-Mark

---

### Post by mvalenti on 2009-11-23
mark@mark-laptop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC888 Analog [ALC888 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
mark@mark-laptop:~$

---

