---
title: "Microphone does not work on 10.04 on Dell e6410"
date: 2010-06-08
forum: Hardware
---

### Post by waliu on 2010-06-08
Hi all,

I installed 10.04 64-bit on my Dell E6410. My microphone is not working and none of the solutions I found on the internet works for me :(
Please tell my if you need any input from me, for example my lspci output or anything else that could be helpful.

Thanks!

---

### Post by lidex on 2010-06-09
Internal or external? All other sound OK?
Can you post the output of these terminal commands for me please:
```
uname -a
aplay -l
cat /proc/asound/version
head -n 1 /proc/asound/card*/codec#* 
```
Terminal="Applications->Accessories->Terminal"
**Please also include the make/model of your PC/Laptop.**
Please post text output using code tags (the # in toolbar)

---

### Post by olegsmall on 2010-06-09
Try this:
Left button on the dynamics in the system tray
select audio settings
Go to the tab input
Power on microphone
and select the microphone2 (this works on my laptop)

---

### Post by lostthetrail on 2010-06-11
I have the same problem and same machine.

@lidex:
Here are the requested outputs.

$ uname -a
Linux lostfocus 2.6.32-22-generic #36-Ubuntu SMP Thu Jun 3 22:02:19 UTC 2010 i686 GNU/Linux

$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

$ cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.21.

$ head -n 1 /proc/asound/card*/codec#*
==> /proc/asound/card0/codec#0 <==
Codec: IDT 92HD81B1C5

==> /proc/asound/card1/codec#0 <==
Codec: Nvidia ID b

==> /proc/asound/card1/codec#1 <==
Codec: Nvidia ID b

==> /proc/asound/card1/codec#2 <==
Codec: Nvidia ID b

==> /proc/asound/card1/codec#3 <==
Codec: Nvidia ID b

@olegsmall
Good suggestion, no sadly no dice.

---

### Post by lidex on 2010-06-11
Using a Terminal="Applications->Accessories->Terminal"
Open this file for editing:
```
 gksudo gedit /etc/modprobe.d/alsa-base.conf 
```
Insert this line at the bottom:
```
 options snd-hda-intel model=dell-s14 
```
Save. Close. Reboot. Check your levels in alsamixer.
```
 alsamixer 
```
Press <F6> to select the correct soundcard.
Press <F3> to show playback levels. <F4> selects capture levels [or use <Tab>]
Use the left/right arrow keys to select and up/down arrow keys to change levels. <M> to mute/unmute.
Go to "System ->Preferences ->Sound" and make sure the correct soundcard is default and adjust your profile on the hardware tab.

Now if that doesn't work, upgrade your alsa install using the alsa-upgrade link in my sig.

---

### Post by tgm on 2010-06-17
I have a Dell E6410 running 10.04 and that works for me. Thank you very much. Now I just need to wait for the touchpad issues to make it through into the kernel.

---

### Post by lostthetrail on 2010-06-19
@lidex: That worked perfectly. Could you explain what that line I just added does for us that makes it work?

Thanks in advance.

---

### Post by lisar915 on 2010-07-09
Hi,

My internal microphone doesn't work either.  I have a Sony Vaio PCG-K33 laptop.  My sound card is ALI 5451.  The chip is Realtek ALC203.  And I'm using Ubuntu version 10.04.  

I tried installing the gnome alsamixer.  Also when I type alsamixer in the terminal, there are no bars showing up for the microphone.  

Any suggestions will be greatly appreciated.

Thanks.
Lisa

---

### Post by lidex on 2010-07-10
> **lostthetrail said:**
> @lidex: That worked perfectly. Could you explain what that line I just added does for us that makes it work?

Thanks in advance.
It tells alsa that the codec implementation is non-standard, so configure for that model not the default.

---

### Post by anrange on 2010-07-17
Hi, I have a dell latitude e6410 too with nvidia graphics.

I follow this tutorial.
I ran the alsamixer, but when I talk to the mic, I don see it moving.
What app can I use to test it?

my settings: 

I modified the file /etc/modprobe.d/alsa-base.conf 

as show here:


tail /etc/modprobe.d/alsa-base.conf
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-us122l index=-2
options snd-usb-usx2y index=-2
options snd-usb-caiaq index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
# Keep snd-pcsp from being loaded as first soundcard
options snd-pcsp index=-2
options snd-hda-intel model=dell-s14


Info requested:

uname -a
Linux andres-ubuntu 2.6.32-23-generic #37-Ubuntu SMP Fri Jun 11 08:03:28 UTC 2010 x86_64 GNU/Linux

aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 3: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 7: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 8: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 9: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.23.
Compiled on Jul 17 2010 for kernel 2.6.32-23-generic (SMP).

head -n 1 /proc/asound/card*/codec#*

==> /proc/asound/card0/codec#0 <==
Codec: IDT 92HD81B1C5

==> /proc/asound/card1/codec#0 <==
Codec: Nvidia GT21x HDMI

==> /proc/asound/card1/codec#1 <==
Codec: Nvidia GT21x HDMI

==> /proc/asound/card1/codec#2 <==
Codec: Nvidia GT21x HDMI

==> /proc/asound/card1/codec#3 <==
Codec: Nvidia GT21x HDMI

---

### Post by lidex on 2010-07-18
First, for mic problem, check this.
**Gnome-alsamixer**
Using Alt+F2 run dialog
```
 gnome-alsamixer 
```
**Use 'Edit -> Sound Card Properties' menu to enable elements.**
Soundcard tab to select / adjust levels.
To install:
```
sudo apt-get install gnome-alsamixer
```

Then use pulseaudio volume control (pavucontrol) or 'Sound Preferences' to select and unmute your mic in 'Input Devices' tab.

From alsa documentation:
> Capture Problems
~~~~~~~~~~~~~~~~
The capture problems are often because of missing setups of mixers.
Thus, before submitting a bug report, make sure that you set up the
mixer correctly.  For example, both "Capture Volume" and "Capture
Switch" have to be set properly in addition to the right "Capture
Source" or "Input Source" selection.  Some devices have "Mic Boost"
volume or switch.

When the PCM device is opened via "default" PCM (without pulse-audio
plugin), you'll likely have "Digital Capture Volume" control as well.
This is provided for the extra gain/attenuation of the signal in
software, especially for the inputs without the hardware volume
control such as digital microphones.  Unless really needed, this
should be set to exactly 50%, corresponding to 0dB -- neither extra
gain nor attenuation.  When you use "hw" PCM, i.e., a raw access PCM,
this control will have no influence, though.

You can use 'Sound Recorder' to test.

---

### Post by djtarki on 2010-07-20
> **lidex said:**
> First, for mic problem, check this.
**Gnome-alsamixer**
Using Alt+F2 run dialog
```
 gnome-alsamixer 
```**Use 'Edit -> Sound Card Properties' menu to enable elements.**
Soundcard tab to select / adjust levels.
To install:
```
sudo apt-get install gnome-alsamixer
```Then use pulseaudio volume control (pavucontrol) or 'Sound Preferences' to select and unmute your mic in 'Input Devices' tab.

From alsa documentation:


You can use 'Sound Recorder' to test.


Solved! Thanks very much!

---

### Post by margni on 2010-08-23
[QUOTE]Hi, I have a dell latitude e6410 too with nvidia graphics.[QUOTE]

Does your dell have the nVidia NSM 3100M video card?  If it's working for you, what did you do to get that to happen>

My install is permanently stuck in 800x600 video resolution...

Any insight would be much appreciated!

---

### Post by empie on 2010-08-30
Thanks a lot, this solved my problem! Have a nice day, so do I now :D
Max

---

### Post by sloppyjimbob on 2010-09-05
My microphone does not work either.  I have a Dell Adamo 13 and the microphone worked fine with 9.10. I've searched and tried some of the "fixes."  I tried lidex's alsa script but i'm unsure of what "model" to use (mine says STAC92XX, not sure what the last 2 digits should be).

Here is lidex's requested code:
```

justin@jc-laptop:~$ uname -a
Linux jc-laptop 2.6.32-24-generic #39-Ubuntu SMP Wed Jul 28 05:14:15 UTC 2010 x86_64 GNU/Linux
justin@jc-laptop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 3: INTEL HDMI [INTEL HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
justin@jc-laptop:~$ cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.21.
justin@jc-laptop:~$ head -n 1 /proc/asound/card*/codec#*
==> /proc/asound/card0/codec#0 <==
Codec: IDT 92HD73C1X5

==> /proc/asound/card0/codec#1 <==
Codec: Intel G45 DEVCTG
justin@jc-laptop:~$ 


```


I've also noticed that there are quite a few less control bars in alsamixer than I had in 9.10, not sure if that matters.

Note: I just did a fresh install of 10.04 as I'm switching between 9.10 to trouble shoot this. Thats why it may look (from the code) that I haven't tried the alsa script.


Any help would be much appreciated.

I attached my alsa-base.conf if that would help at all.

---

### Post by zazootheparrot on 2010-09-05
I have an issue with both my microphone and webcam :(
I've gone through many of the threads but haven't found any solutions yet!
Typing lsusb in the terminal, it gives me the following message: 
```
Bus 007 Device 002: ID 044e:3017 Alps Electric Co., Ltd 
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 003: ID 147e:2016 Upek Biometric Touchchip/Touchstrip Fingerprint Sensor
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 054c:0281 Sony Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 05ca:183a Ricoh Co., Ltd Visual Communication Camera VGP-VCC7 [R5U870]
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

``` 

Computer model: Sony Vaio VGN-SZ740 
Operating system: Ubuntu 10.04 Lucid Lynx 

Could you please help me?

---

### Post by lidex on 2010-09-06
*sloppyjimbob:*
Using a Terminal="Applications->Accessories->Terminal"
Open this file for editing:
```
 gksudo gedit /etc/modprobe.d/alsa-base.conf 
```
Insert this line at the bottom:
```
 options snd-hda-intel model=dell-eq 
```
Save. Close. Reboot. 
Check your levels in alsamixer.
```
 alsamixer 
```
Press <F6> to select the correct soundcard.
Press <F3> to show playback levels. <F4> selects capture levels [or use <Tab>]
Use the left/right arrow keys to select and up/down arrow keys to change levels. <M> to mute/unmute.
Go to "System ->Preferences ->Sound" and make sure the correct soundcard is default and adjust your profile on the hardware tab. 
On the output tab choose the correct device.

---

### Post by lidex on 2010-09-06
> **zazootheparrot said:**
> I have an issue with both my microphone and webcam :(
I've gone through many of the threads but haven't found any solutions yet!
Typing lsusb in the terminal, it gives me the following message: 
```
Bus 007 Device 002: ID 044e:3017 Alps Electric Co., Ltd 
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 003: ID 147e:2016 Upek Biometric Touchchip/Touchstrip Fingerprint Sensor
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 054c:0281 Sony Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 05ca:183a Ricoh Co., Ltd Visual Communication Camera VGP-VCC7 [R5U870]
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

``` 

Computer model: Sony Vaio VGN-SZ740 
Operating system: Ubuntu 10.04 Lucid Lynx 

Could you please help me?
Does this help:
[http://www.linlap.com/wiki/sony+vaio+vgn-sz+series](http://www.linlap.com/wiki/sony+vaio+vgn-sz+series)

---

### Post by zazootheparrot on 2010-09-06
Thank you so much!!!! Now, The microphone is working perfectly well :D:D

---

### Post by zazootheparrot on 2010-09-06
> **lidex said:**
> Does this help:
[http://www.linlap.com/wiki/sony+vaio+vgn-sz+series](http://www.linlap.com/wiki/sony+vaio+vgn-sz+series)

I checked this link and in the downloads part I downloaded the driver for SZ. Then I extracted the file but when I try to configure it, the following appears in the terminal :
```
root@ava-laptop:~/Downloads/r5u870-0.10.0# ./configure
bash: ./configure: No such file or directory

```So I can't "make" and "make install" it because it can't be configured!

Would you be so kind to tell me what to do next? :confused:

Thanks

---

### Post by sloppyjimbob on 2010-09-06
> **lidex said:**
> *sloppyjimbob:*
Using a Terminal="Applications->Accessories->Terminal"
Open this file for editing:
```
 gksudo gedit /etc/modprobe.d/alsa-base.conf 
```
Insert this line at the bottom:
```
 options snd-hda-intel model=dell-eq 
```
Save. Close. Reboot. 
Check your levels in alsamixer.
```
 alsamixer 
```
Press <F6> to select the correct soundcard.
Press <F3> to show playback levels. <F4> selects capture levels [or use <Tab>]
Use the left/right arrow keys to select and up/down arrow keys to change levels. <M> to mute/unmute.
Go to "System ->Preferences ->Sound" and make sure the correct soundcard is default and adjust your profile on the hardware tab. 
On the output tab choose the correct device.

Thanks. I gave it a shot but it didn't work.  It did give me some different "controls" in the alsamixer, the the mic still isn't working.

---

### Post by sloppyjimbob on 2010-09-06
@lidex, thank you so much for your help and info, not just in this thread but in others as well.  I used "model=dell-m6-dmic" and that worked fine.  Thanks again.

---

### Post by lidex on 2010-09-15
Yah! Sorry I didn't follow up sooner - was on vacation and away from internet access.

---

### Post by zazootheparrot on 2010-09-18
Any ideas how to configure? 



> **zazootheparrot said:**
> I checked this link and in the downloads part I downloaded the driver for SZ. Then I extracted the file but when I try to configure it, the following appears in the terminal :
```
root@ava-laptop:~/Downloads/r5u870-0.10.0# ./configure
bash: ./configure: No such file or directory

```So I can't "make" and "make install" it because it can't be configured!

Would you be so kind to tell me what to do next? :confused:

Thanks

---

### Post by ivanz on 2010-09-29
I've used model dell-s14 for my Dell E6410, according instructions, thanks for them
The internal mic now works well. However the external mic is not working now.
In alsamixer I see two imputs - "Front mic" and "Mic",   but in pulse input preferences, I do not have any options to chose,  the input seems to be connected to "Mic", which is build in mic, and no other option to choose.  Before changing model for intel sound driver, I had 4 options in pulse input configuration (Mic, Mic-line in, Front mic, Front mic - line-in).

Any ideas how to get both mics working?

---

### Post by rakete on 2010-10-08
Thank you, works for Dell Latitude E5400 with 10.10 (Maverick), too...

---

### Post by mvega on 2010-10-14
Hi,

I have been working on my DELL E6510 for 2 days trying to solve this problem, and I finally made it !!!!

The key information I used came from [https://patchwork.kernel.org/patch/216322/]("https://patchwork.kernel.org/patch/216322/") where I found that there is a kernel patch to solve this problem, but since I was not planning to compile my kernel .... I just modified the file: ```
/etc/modprobe.d/alsa-base.conf
```to use: ```
options snd-hda-intel model=ref
```
In the function ***stac92hd83xxx_models**, in the kernel patch, you can see the different models for this soundcard.  The first one worked for me.

---

### Post by mrbean_pfiev on 2010-10-29
> **lidex said:**
> Using a Terminal="Applications->Accessories->Terminal"
Open this file for editing:
```
 gksudo gedit /etc/modprobe.d/alsa-base.conf 
```Insert this line at the bottom:
```
 options snd-hda-intel model=dell-s14 
```Save. Close. Reboot. Check your levels in alsamixer.
```
 alsamixer 
```Press <F6> to select the correct soundcard.
Press <F3> to show playback levels. <F4> selects capture levels [or use <Tab>]
Use the left/right arrow keys to select and up/down arrow keys to change levels. <M> to mute/unmute.
Go to "System ->Preferences ->Sound" and make sure the correct soundcard is default and adjust your profile on the hardware tab.

Now if that doesn't work, upgrade your alsa install using the alsa-upgrade link in my sig.

Hello,
   I used Dell Latitude E6410 with the same problem with these other guys here and I had followed your instruction but the sound doesn't work on my headphone. Can you help me? And how can I know my Alsa driver is up to date? I'm using Ubuntu 10.10 , I don't know if it is different to solve with Ubuntu 10.04?
Thank you very much.

---

### Post by fallenshadow on 2010-10-30
Ubuntu 10.10 has the latest ALSA I think. Just make sure that your headphones are selected as the output device in your "Sound Preferences".

---

### Post by mrbean_pfiev on 2010-10-30
Hi,
  My headphone has worked today. But after that when I restart my computer, it doesn't work. I don't understand why. And now, after turn off my computer for about 2 hours, my headphone go to work again. Very strange. 
Can you help me in this case?

---

### Post by lidex on 2010-10-30
> **mrbean_pfiev said:**
> Hi,
  My headphone has worked today. But after that when I restart my computer, it doesn't work. I don't understand why. And now, after turn off my computer for about 2 hours, my headphone go to work again. Very strange. 
Can you help me in this case?

Not sure - try this. Using a Terminal="Applications->Accessories->Terminal"
```

rm -r ~/.pulse ~/.asound* ~/.pulse-cookie 
sudo rm /etc/asound.conf
```
**Logout/in.**

---

### Post by mrbean_pfiev on 2010-10-31
Hi,
  After several times restart, turn off, turn on the computer, I have found that when I restart from Win 7 to Ubuntu (that means I boot on Win 7, after that I restart to boot to Ubuntu), there is no sound in my headphone (the headphone works for win 7, of course). But when I boot direct to Ubuntu (that means the computer is turned off before), my headphone works. That is my problem.
I had tried with your command, but it said that there is no such file or directory. Thanks very much

---

### Post by lidex on 2010-10-31
> **mrbean_pfiev said:**
> Hi,
  After several times restart, turn off, turn on the computer, I have found that when I restart from Win 7 to Ubuntu (that means I boot on Win 7, after that I restart to boot to Ubuntu), there is no sound in my headphone (the headphone works for win 7, of course). But when I boot direct to Ubuntu (that means the computer is turned off before), my headphone works. That is my problem.
I had tried with your command, but it said that there is no such file or directory. Thanks very much

Can you post these outputs please:
```
dmesg | grep firmware
sudo dmidecode -t bios
sudo dmidecode -t baseboard
```

---

### Post by mrbean_pfiev on 2010-11-01
Here is my portable's output:
**$ dmesg | grep firmware**
[   10.442034] iwlagn 0000:03:00.0: loaded firmware version 9.221.4.1 build 25532

**$ sudo dmidecode -t bios**
# dmidecode 2.9
SMBIOS 2.6 present.

Handle 0x0000, DMI type 0, 24 bytes
BIOS Information
    Vendor: Dell Inc.
    Version: A05
    Release Date: 08/10/2010
    Address: 0xF0000
    Runtime Size: 64 kB
    ROM Size: 1024 kB
    Characteristics:
        PCI is supported
        BIOS is upgradeable
        BIOS shadowing is allowed
        ESCD support is available
        Boot from CD is supported
        Selectable boot is supported
        BIOS ROM is socketed
        EDD is supported
        5.25"/1.2 MB floppy services are supported (int 13h)
        3.5"/720 KB floppy services are supported (int 13h)
        3.5"/2.88 MB floppy services are supported (int 13h)
        Print screen service is supported (int 5h)
        8042 keyboard services are supported (int 9h)
        Serial services are supported (int 14h)
        Printer services are supported (int 17h)
        CGA/mono video services are supported (int 10h)
        ACPI is supported
        USB legacy is supported
        LS-120 boot is supported
        ATAPI Zip drive boot is supported
        BIOS boot specification is supported
        Targeted content distribution is supported
    BIOS Revision: 4.6

Handle 0x0018, DMI type 13, 22 bytes
BIOS Language Information
    Installable Languages: 1
        en|US|iso8859-1
    Currently Installed Language: en|US|iso8859-1

**$ sudo dmidecode -t baseboard**
# dmidecode 2.9
SMBIOS 2.6 present.

Handle 0x0002, DMI type 2, 15 bytes
Base Board Information
    Manufacturer: Dell Inc.
    Product Name: 0K42JR
    Version: A01
    Serial Number: /34C6WM1/CN1296109T0228/
    Asset Tag:  
    Features:
        Board is a hosting board
        Board is replaceable
    Location In Chassis: Not Specified
    Chassis Handle: 0x0003
    Type: Motherboard
    Contained Object Handles: 0

Handle 0x0014, DMI type 10, 6 bytes
On Board Device Information
    Type: Video
    Status: Disabled
    Description: "Intel GM45 Graphics"

Handle 0x0015, DMI type 10, 6 bytes
On Board Device Information
    Type: Ethernet
    Status: Enabled
    Description: NETWORK_NAME_STRING


**And,** another information, my computer uses the card graphic: Nvidia Quadro 3100M

---

### Post by lidex on 2010-11-02
> **mrbean_pfiev said:**
> Here is my portable's output:
**$ dmesg | grep firmware**
[   10.442034] iwlagn 0000:03:00.0: loaded firmware version 9.221.4.1 build 25532

**$ sudo dmidecode -t bios**
# dmidecode 2.9
SMBIOS 2.6 present.

Handle 0x0000, DMI type 0, 24 bytes
BIOS Information
    Vendor: Dell Inc.
    Version: A05
    Release Date: 08/10/2010
    Address: 0xF0000
    Runtime Size: 64 kB
    ROM Size: 1024 kB
    Characteristics:
        PCI is supported
        BIOS is upgradeable
        BIOS shadowing is allowed
        ESCD support is available
        Boot from CD is supported
        Selectable boot is supported
        BIOS ROM is socketed
        EDD is supported
        5.25"/1.2 MB floppy services are supported (int 13h)
        3.5"/720 KB floppy services are supported (int 13h)
        3.5"/2.88 MB floppy services are supported (int 13h)
        Print screen service is supported (int 5h)
        8042 keyboard services are supported (int 9h)
        Serial services are supported (int 14h)
        Printer services are supported (int 17h)
        CGA/mono video services are supported (int 10h)
        ACPI is supported
        USB legacy is supported
        LS-120 boot is supported
        ATAPI Zip drive boot is supported
        BIOS boot specification is supported
        Targeted content distribution is supported
    BIOS Revision: 4.6

Handle 0x0018, DMI type 13, 22 bytes
BIOS Language Information
    Installable Languages: 1
        en|US|iso8859-1
    Currently Installed Language: en|US|iso8859-1

**$ sudo dmidecode -t baseboard**
# dmidecode 2.9
SMBIOS 2.6 present.

Handle 0x0002, DMI type 2, 15 bytes
Base Board Information
    Manufacturer: Dell Inc.
    Product Name: 0K42JR
    Version: A01
    Serial Number: /34C6WM1/CN1296109T0228/
    Asset Tag:  
    Features:
        Board is a hosting board
        Board is replaceable
    Location In Chassis: Not Specified
    Chassis Handle: 0x0003
    Type: Motherboard
    Contained Object Handles: 0

Handle 0x0014, DMI type 10, 6 bytes
On Board Device Information
    Type: Video
    Status: Disabled
    Description: "Intel GM45 Graphics"

Handle 0x0015, DMI type 10, 6 bytes
On Board Device Information
    Type: Ethernet
    Status: Enabled
    Description: NETWORK_NAME_STRING


**And,** another information, my computer uses the card graphic: Nvidia Quadro 3100M

Could be as simple as the settings (being reset) in Sound Preferences as mentioned in a previous post. Have you tried toggling the connector option on the output tab?

---

### Post by mrbean_pfiev on 2010-11-08
Hi,
  I have changed the output to Analog Headphones and Analog Output, but it's still doen't work. Can't understand. Maybe I should boot direct to ubuntu so that I can use my headphone.
Thanks very much for your help!

---

### Post by lidex on 2010-11-10
> **mrbean_pfiev said:**
> Hi,
  I have changed the output to Analog Headphones and Analog Output, but it's still doen't work. Can't understand. Maybe I should boot direct to ubuntu so that I can use my headphone.
Thanks very much for your help!

I doubt this is an issue with ubuntu. More likely windows is causing the problem.

---

### Post by go4linux on 2010-11-12
lidex, you rock. I had tried the model dell-s14 before, but somehow it didn't work. I think I was missing the alsamixer part. Now I have my microphone working. Thanks a lot.
The only thing I'm missing now is: why do I have to do all this work with the alsamixer if I use pulseaudio? I know that pulseaudio can use alsa, but the impression is that alsa actually does everything. What's pulseaudio's added value?

Thanks again

edit: for the record, I see that this thread is about 10.04. I'm using 10.10, 64 bit

---

### Post by earlycj5 on 2010-12-01
> **sloppyjimbob said:**
> @lidex, thank you so much for your help and info, not just in this thread but in others as well.  I used "model=dell-m6-dmic" and that worked fine.  Thanks again.

Thank YOU, sloppyjimbob, your "model=dell-m6-dmic" fixed the mic on my Adamo13.  Fully functional now!

---

### Post by Kivrin on 2010-12-23
I recently upgraded to 10.04 (via fresh install) on my Toshiba U305-S2804. Under sound preferences, I have no way to toggle between input options, so my external mic isn't working. (My internal mic isn't working either, but I don't care as much.) 

I've upgraded Alsamixer (compiled from the source), I've looked at my Alsamixer (nothing muted), I've modified my alsa-base.conf (I must have the wrong codec, none that I've tried have worked). However, I must still have pulseaudio working, since Skype sound preferences show puseaudio server as the only sound option. 

I'm going nuts, any suggestions?

The results to the inputs:

> uname -a
Linux Oliver 2.6.32-26-generic #48-Ubuntu SMP Wed Nov 24 09:00:03 UTC 2010 i686 GNU/Linux

> aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC268 Analog [ALC268 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0


> cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.23.
Compiled on Dec 19 2010 for kernel 2.6.32-26-generic (SMP). 

> head -n 1 /proc/asound/card*/codec#*
==> /proc/asound/card0/codec#0 <==
Codec: Realtek ALC268

==> /proc/asound/card0/codec#1 <==
Codec: LSI ID 1040


---

### Post by lidex on 2010-12-24
@Kivrin
You're not able to toggle the input in alsamixer, as in, it won't work, or you don't know how to access it? Can you do this for me please? Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]

---

### Post by wvandael on 2011-03-18
I'm having the same problems as mrbean_pfiev: no sound in headphones on Dell Latitude E6410.
I have a dual boot config. Sound in Windows works ok, but even when booting straight into Ubuntu I have no sound. I tried all suggestions in this whole tread.

Can someone help me? I ran the alsa-info script. The output can be found at

[http://www.alsa-project.org/db/?f=0060fc975b252ba5899beb06834fbbf2b742d2e4](http://www.alsa-project.org/db/?f=0060fc975b252ba5899beb06834fbbf2b742d2e4)

Thanks in advance

---

### Post by lidex on 2011-03-18
> **wvandael said:**
> I'm having the same problems as mrbean_pfiev: no sound in headphones on Dell Latitude E6410.
I have a dual boot config. Sound in Windows works ok, but even when booting straight into Ubuntu I have no sound. I tried all suggestions in this whole tread.

Can someone help me? I ran the alsa-info script. The output can be found at

[http://www.alsa-project.org/db/?f=0060fc975b252ba5899beb06834fbbf2b742d2e4](http://www.alsa-project.org/db/?f=0060fc975b252ba5899beb06834fbbf2b742d2e4)

Thanks in advance
Bear in mind this is a thread about the microphone.

Have you checked the levels in alsa mixer and 'Sound Preferences'? What are these outputs:
```
cat /etc/modprobe.d/alsa-base.conf
ls /etc/modprobe.d

```

---

### Post by gkout on 2011-05-03
Thnx lidex,

I ve been searching for a long time to solutions to my internal mic not working and the setting you suggested in alsa conf file did the trick. My mic now is working like a charm. 

thnx again.

---

### Post by gkout on 2011-05-03
> **ivanz said:**
> I've used model dell-s14 for my Dell E6410, according instructions, thanks for them
The internal mic now works well. However the external mic is not working now.
In alsamixer I see two imputs - "Front mic" and "Mic",   but in pulse input preferences, I do not have any options to chose,  the input seems to be connected to "Mic", which is build in mic, and no other option to choose.  Before changing model for intel sound driver, I had 4 options in pulse input configuration (Mic, Mic-line in, Front mic, Front mic - line-in).

Any ideas how to get both mics working?

Alsa "speaks" with the h/w, so u need to change the settings in alsamixer.

Run alsamixer
Press F3 and in the mic column change the 'Mic in' to 'Line in' using <Page Up> or <Page Down>. This will switch to the external mic.
Following that go to "Capture" mode with <F4> and set you volume controls for you external mic there.

I could not find a way to have both "Mic in" and "Line in" enabled at the same time as capture devices in alsa, but the above should do the job.

---

### Post by marvin1969 on 2011-09-02
Thanks, Lidex.  Your mod configuration worked perfectly for me.

---

### Post by lidex on 2011-09-02
> **marvin1969 said:**
> Thanks, Lidex.  Your mod configuration worked perfectly for me.

You're welcome. Good to get positive feedback when so many issues unsolved but more important is knowing what works so it can help others. Enjoy.

---

