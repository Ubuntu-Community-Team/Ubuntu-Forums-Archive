---
title: "Sound problem on GIGABYTE GA-PH67-UD3-B3"
date: 2012-02-22
forum: Hardware
---

### Post by RitualMast3r on 2012-02-22
Hello guys!
For sometime now I'm having problem with sound in Ubuntu 11.04. It's seems that the sound card isn't recognized at all. I've tryed both Alsa (PulseAudio) and OSS but doesn't work, neither. Here is what **lscpi** returns for me:
[PHP]00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)
00:01.0 PCI bridge: Intel Corporation 2nd Generation Core Processor Family PCI Express Root Port (rev 09)
00:16.0 Communication controller: Intel Corporation 6 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB Controller: Intel Corporation 6 Series Chipset Family USB Enhanced Host Controller #2 (rev 05)
00:1b.0 Audio device: Intel Corporation 6 Series Chipset Family High Definition Audio Controller (rev 05)
00:1c.0 PCI bridge: Intel Corporation 6 Series Chipset Family PCI Express Root Port 1 (rev b5)
00:1c.2 PCI bridge: Intel Corporation 6 Series Chipset Family PCI Express Root Port 3 (rev b5)
00:1c.3 PCI bridge: Intel Corporation 6 Series Chipset Family PCI Express Root Port 4 (rev b5)
00:1d.0 USB Controller: Intel Corporation 6 Series Chipset Family USB Enhanced Host Controller #1 (rev 05)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev a5)
00:1f.0 ISA bridge: Intel Corporation H67 Express Chipset Family LPC Controller (rev 05)
00:1f.2 IDE interface: Intel Corporation 6 Series Chipset Family 4 port SATA IDE Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 6 Series Chipset Family SMBus Controller (rev 05)
00:1f.5 IDE interface: Intel Corporation 6 Series Chipset Family 2 port SATA IDE Controller (rev 05)
01:00.0 VGA compatible controller: ATI Technologies Inc Device 68ba
01:00.1 Audio device: ATI Technologies Inc Juniper HDMI Audio [Radeon HD 5700 Series]
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 06)
04:00.0 PCI bridge: Integrated Technology Express, Inc. Device 8892 (rev 10)[/PHP]
also from **alsamixer**
[PHP]
&#1089;&#1084;&#1077;&#1089;&#1080;&#1090;&#1077;&#1083;&#1103;&#1090; &#1085;&#1077; &#1084;&#1086;&#1078;&#1077; &#1076;&#1072; &#1073;&#1098;&#1076;&#1077; &#1086;&#1090;&#1074;&#1086;&#1088;&#1077;&#1085;: &#1053;&#1103;&#1084;&#1072; &#1090;&#1072;&#1082;&#1098;&#1074; &#1092;&#1072;&#1081;&#1083; &#1080;&#1083;&#1080; &#1076;&#1080;&#1088;&#1077;&#1082;&#1090;&#1086;&#1088;&#1080;&#1103; (couldn't open the mixer: no such file or directory)
[/PHP]
Sorry for the bulgarian... :redface: 
I hope you can help! Thanks!

---

### Post by beceraful on 2012-02-23
I have the same problem too. Please people help. What we have to do to fix the problem. What we have to write in the terminal to fix the problem.?

I want to added that i have also no sound at all. For example in cs , listening to music and at all . This problem he have and i and we want to fix the problem at all.. Help and Thanks

---

### Post by gldearman on 2012-02-25
I don't know much about audio (or Bulgarian), but I can point out a few things that may benefit from further investigation.

First, your lspci output lists two audio devices: an Intel and a Radeon for output via HDMI.  The second one is probably a reference to your video card  I'm assuming you're using the first one? Can you check to see if audio output is working via HDMI?

By any chance, is this a dual-boot system, and you could check to see if the sound is working in another OS? That would rule out hardware issues.

Also, can you give us the output from these two commands, please:
```
$ lspci -v -s 00:1b.0
$ lsmod
```

---

### Post by gordintoronto on 2012-02-25
Also, when you run Sound Preferences and click on the Hardware tab, which device is selected? Then look at the Output tab and confirm that it's not muted.

---

### Post by PayPaul on 2012-02-28
I have a similar problem with a RealTek soundcard on an HP a1610n. PulseAudio seems to be installed but there is no sound. I checked devices and the volume is up and not muted. Why no sound. Output device shows "Internal Audio Analog Stereo" as the device. I can record with the microphone but get no playback.

---

### Post by beceraful on 2012-03-02
> **PayPaul said:**
> I have a similar problem with a RealTek soundcard on an HP a1610n. PulseAudio seems to be installed but there is no sound. I checked devices and the volume is up and not muted. Why no sound. Output device shows "Internal Audio Analog Stereo" as the device. I can record with the microphone but get no playback.

On windows I'm not having internet , but sound i have .. , i don't know why I don't have sound on linux and Internet (browsering) on windows..
Audio pulse was been stopped. i Stated it but no sound again , if audio pulse is off no sound or on again no sound.. 
Comands doesn't work , the command is not found , please peopel help me , i am not listing to music in 4-5 months.. since octomber.. I need to listen music i need it.. I am on Intel core , everythink is working but the sound on linux.. something is or stopped , or delete. 
Help people with decideting.

I am ritualmaster

Now pls help.

---

### Post by 23dornot23d on 2012-03-03
Not sure .... sound is not my thing .... but as you asked ....

Try installing alsamixer and see what it shows .... if you do these one after the other in a terminal
then post a screen shot of what you see ..... please .....

[B]sudo apt-get update

sudo apt-get install aptitude

sudo aptitude install gnome-alsamixer alsamixergui

alsamixergui


To find more information so others can help ..... do the following ..... then post the results ..... back here ....

[/B][B]sudo cat /proc/asound/card0/codec* | grep Codec

[/B]**sudo cat /proc/asound/card0/pcm0c/info**

**sudo cat /proc/asound/card0/codec***
[B]

here are mine as an example .....

[/B]> 
keith@keith-Aspire-7730ZG:~$ **sudo cat /proc/asound/card0/codec* | grep Codec**
[sudo] password for keith: 
Codec: Realtek ALC888
Codec: LSI ID 1040
Codec: Nvidia MCP77/78 HDMI
keith@keith-Aspire-7730ZG:~$ 


keith@keith-Aspire-7730ZG:~$ [B]sudo cat /proc/asound/card0/pcm0c/info
[/B]card: 0
device: 0
subdevice: 0
stream: CAPTURE
id: ALC888 Analog
name: ALC888 Analog
subname: subdevice #0
class: 0
subclass: 0
subdevices_count: 1
subdevices_avail: 1
keith@keith-Aspire-7730ZG:~$ 




---

