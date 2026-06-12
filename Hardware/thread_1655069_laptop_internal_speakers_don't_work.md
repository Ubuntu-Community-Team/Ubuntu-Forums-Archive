---
title: "laptop internal speakers don't work"
date: 2010-12-29
forum: Hardware
---

### Post by bngsudheer on 2010-12-29
The laptop model is HP Compaq CQ50.


Here's the output of lspci:

> 
00:00.0 RAM memory: nVidia Corporation MCP78S [GeForce 8200] Memory Controller (rev a2)
00:01.0 ISA bridge: nVidia Corporation Device 075e (rev a2)
00:01.1 SMBus: nVidia Corporation MCP78S [GeForce 8200] SMBus (rev a1)
00:01.3 Co-processor: nVidia Corporation MCP78S [GeForce 8200] Co-Processor (rev a2)
00:01.4 RAM memory: nVidia Corporation MCP78S [GeForce 8200] Memory Controller (rev a1)
00:02.0 USB Controller: nVidia Corporation MCP78S [GeForce 8200] OHCI USB 1.1 Controller (rev a1)
00:02.1 USB Controller: nVidia Corporation MCP78S [GeForce 8200] EHCI USB 2.0 Controller (rev a1)
00:04.0 USB Controller: nVidia Corporation MCP78S [GeForce 8200] OHCI USB 1.1 Controller (rev a1)
00:04.1 USB Controller: nVidia Corporation MCP78S [GeForce 8200] EHCI USB 2.0 Controller (rev a1)
00:06.0 IDE interface: nVidia Corporation MCP78S [GeForce 8200] IDE (rev a1)
00:07.0 Audio device: nVidia Corporation MCP72XE/MCP72P/MCP78U/MCP78S High Definition Audio (rev a1)
00:08.0 PCI bridge: nVidia Corporation MCP78S [GeForce 8200] PCI Bridge (rev a1)
00:09.0 IDE interface: nVidia Corporation MCP78S [GeForce 8200] SATA Controller (non-AHCI mode) (rev a2)
00:0a.0 Ethernet controller: nVidia Corporation MCP77 Ethernet (rev a2)
00:0b.0 PCI bridge: nVidia Corporation MCP78S [GeForce 8200] PCI Express Bridge (rev a1)
00:14.0 PCI bridge: nVidia Corporation MCP78S [GeForce 8200] PCI Bridge (rev a1)
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 11h Processor HyperTransport Configuration (rev 40)
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 11h Processor Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 11h Processor DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 11h Processor Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 11h Processor Link Control
02:00.0 VGA compatible controller: nVidia Corporation C77 [GeForce 8200M G] (rev a2)
07:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g LP-PHY (rev 01)

The sound works if I connect an external speaker to the jack. But the internal speakers don't work.

I have made sure sound is not muted and raised the controls in sound preferences, alsamixer and gnome-alsamixer.

This is on Ubuntu 10.10. Output of uname -a:

> 
Linux tilo 2.6.35-24-generic #42-Ubuntu SMP Thu Dec 2 01:41:57 UTC 2010 i686 GNU/Linux

How can I fix this problem?

---

### Post by lidex on 2010-12-29
Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]

---

### Post by bngsudheer on 2010-12-29
Here's the info:

[http://www.alsa-project.org/db/?f=2afe972f889e0a84388990256ac71724ef8e21c6](http://www.alsa-project.org/db/?f=2afe972f889e0a84388990256ac71724ef8e21c6)

---

### Post by lidex on 2010-12-29
Try this. Using a Terminal="Applications->Accessories->Terminal"
Open this file for editing:
```
 gksudo gedit /etc/modprobe.d/alsa-base.conf 
```
Insert this line at the bottom:
```
 options snd-hda-intel model=laptop position_fix=1 enable=yes 
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

### Post by bngsudheer on 2010-12-29
I followed all the steps you mentioned.

After adding the line 
 options snd-hda-intel model=laptop position_fix=1 enable=yes 
in 

/etc/modprobe.d/alsa-base.conf

The jack also stopped working.

In alsamixer I have selected HDA NVidia as the sound card. 

In Sound Preferences, there's only one device listed. I have tested all the profiles in the Hardware tab.

Now, there's no sound output.

---

### Post by bngsudheer on 2010-12-29
Update:

In Sound Preferences, Hardware tab, when I select Analog Stereo Duplex or Analog Stereo Output, the jack works. But the internal speakers don't with any profile.

---

### Post by lidex on 2010-12-29
Gotcha. Replace that switch with this one:
```
options snd-hda-intel model=ideapad
```
Remember to reboot to initialize then check alsamixer.
Other models to try:
 ```

 laptop	
 dell-laptop	
 olpc-xo-1_5
```

---

### Post by Dthsapprntc on 2010-12-30
I am having the same problem with my internal laptop speakers not working. I've tried the solutions already listed. I get sound with a headset in the headset jack, but nothing through the internal speakers.

Alsa-info-script: [http://www.alsa-project.org/db/?f=05c17ba22525ce615f79a4594b12ee87fdfe6c79](http://www.alsa-project.org/db/?f=05c17ba22525ce615f79a4594b12ee87fdfe6c79)

---

### Post by lidex on 2010-12-30
> **Dthsapprntc said:**
> I am having the same problem with my internal laptop speakers not working. I've tried the solutions already listed. I get sound with a headset in the headset jack, but nothing through the internal speakers.


You have different hardware, so that will not work for you. I'll need you to revert any changes you've made. Remove any custom entries from this file:
```
gksudo gedit /etc/modprobe.d/alsa-base.conf
```
Update your install:
```
sudo apt-get update
sudo apt-get upgrade
sudo update-grub
```
Reboot. Now this to update alsa. Using a Terminal="Applications->Accessories->Terminal"
Add the ubuntu-audio-dev ppa:
```
sudo add-apt-repository ppa:ubuntu-audio-dev/ppa
sudo apt-get update
```
Now install:
```
sudo apt-get install linux-alsa-driver-modules-$(uname -r)
```
**Reboot**
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

### Post by bngsudheer on 2010-12-30
options snd-hda-intel model=ideapad
works. 

Thanks lidex.

---

### Post by Dthsapprntc on 2010-12-30
Thank you very much Lidex, that worked like a charm

---

### Post by Trevor4706 on 2010-12-30
I'm having similar problems with my new HP Compaq Mini CQ10-510CA netbook -- neither the internal speakers or the internal mic will work.  Internal web cam works just fine.  I tried the switch <<options snd-hda-intel model=ideapad>> without success.

Here's the result of lspci on my box:

trevor@trevor-netbook:~$ lspci
00:00.0 Host bridge: Intel Corporation N10 Family DMI Bridge
00:02.0 VGA compatible controller: Intel Corporation N10 Family Integrated Graphics Controller
00:02.1 Display controller: Intel Corporation N10 Family Integrated Graphics Controller
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 02)
00:1d.0 USB Controller: Intel Corporation N10/ICH7 Family USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation NM10 Family LPC Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation N10/ICH7 Family SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 02)
01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 04)
01:00.1 Class ff00: Realtek Semiconductor Co., Ltd. Device 5288 (rev 01)
02:00.0 Network controller: Broadcom Corporation Device 4727 (rev 01)

I'm running Ubuntu 10.04 netbook version with a clean install.

Any suggestions on a switch that might work for me?

---

### Post by lidex on 2010-12-30
@Trevor4706
I'll need some more info. 
Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]

---

### Post by Trevor4706 on 2010-12-30
Lidex

Here's the link:

[http://www.alsa-project.org/db/?f=b2ac3b83944ac20980681823c76aab2fed8e7973](http://www.alsa-project.org/db/?f=b2ac3b83944ac20980681823c76aab2fed8e7973)

Hope you can help.

Regards

Trevor

---

### Post by lidex on 2010-12-30
> **Trevor4706 said:**
> Lidex
Here's the link:
[http://www.alsa-project.org/db/?f=b2ac3b83944ac20980681823c76aab2fed8e7973](http://www.alsa-project.org/db/?f=b2ac3b83944ac20980681823c76aab2fed8e7973)
Hope you can help.
Regards
Trevor
Alsa is using a generic parser as it doesn't quite recognize your codec. Try updating your alsa-driver-modules.
Using a Terminal="Applications->Accessories->Terminal"
Add the ubuntu-audio-dev ppa:
```
sudo add-apt-repository ppa:ubuntu-audio-dev/ppa
sudo apt-get update
```
Now install:
```
sudo apt-get install linux-alsa-driver-modules-$(uname -r)
```
**Reboot**
Check your levels in alsamixer.
```
 alsamixer 
```
Press <F6> to select the correct soundcard.
Press <F3> to show playback levels. <F4> selects capture levels [or use <Tab>]
Use the left/right arrow keys to select and up/down arrow keys to change levels. <M> to mute/unmute.
Go to "System ->Preferences ->Sound" and make sure the correct soundcard is default and adjust your profile on the hardware tab. 
On the output tab choose the correct device.
Post your results and also this output please:
```

aplay -l
dpkg -l | grep "alsa"
head -n 1 /proc/asound/card*/codec#* 
```

---

### Post by Trevor4706 on 2010-12-30
Lidex

Excellent result.  On board speakers now work.  Here's the infor you requested:

trevor@trevor-netbook:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

trevor@trevor-netbook:~$ dpkg -l | grep "alsa"
ii  alsa-base                                      1.0.22.1+dfsg-0ubuntu3                          ALSA driver configuration files
ii  alsa-utils                                     1.0.22-0ubuntu5                                 ALSA utilities
ii  bluez-alsa                                     4.60-0ubuntu8                                   Bluetooth audio support
ii  gnome-alsamixer                                0.9.7~cvs.20060916.ds.1-2                       ALSA sound mixer for GNOME
ii  gstreamer0.10-alsa                             0.10.28-1                                       GStreamer plugin for ALSA
ii  linux-alsa-driver-modules-2.6.32-27-generic    2.6.32-27.201012291600                          Ubuntu-supplied Linux modules for version 2.

trevor@trevor-netbook:~$ head -n 1 /proc/asound/card*/codec#*
Codec: IDT 92HD88B1

Do you have expertise with getting internal microphones to work as well, or should I try another post?

---

### Post by lidex on 2010-12-30
Did you remove
```
options snd-hda-intel model=ideapad
```
from alsa-base.conf and reboot?

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

Then go to 'Sound Preferences' to select and unmute your mic in 'Input' tab.
Make sure you have selected a profile with 'duplex' or 'analog input' for the correct sound device on the 'Hardware' tab.
Use Pulse Audio Volume Control (pavucontrol) to unlock stereo sliders for the mic in 'Input Devices' tab. Drag the right slider down to zero. The mic is a mono device.

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

No joy? Please sign on to this bug report:
[https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/671814](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/671814)

---

### Post by Trevor4706 on 2010-12-31
Lidex

Thanks for your assistance in getting the internal speakers up and running.  Still no joy regarding the internal mic.  I've signed into the bug as you suggested, and will just have to wait and see if anything comes up to correct the problem.

Regards

Trevor

---

### Post by Trevor4706 on 2011-01-01
Probably should have tried this earlier, but this morning I decided to run the 10.04 netbook remix from a live USB stick to see if everything worked out-of-the-box in the live environment.  I was surprised to find that it did.  The internal mic worked as advertised. Altho sound quality was scratchy, it was certainly readable.  Checking the live set-up in sound preferences, there were no differences from the set-up I have in the installed version on my HD.

Curious.

---

### Post by lidex on 2011-01-01
At this point it may be helpful to run alsa-info script from usb version and also from dedicated install and check for differences.

---

### Post by Zoomy on 2011-01-02
> **lidex said:**
> You have different hardware, so that will not work for you. I'll need you to revert any changes you've made. Remove any custom entries from this file:
```
gksudo gedit /etc/modprobe.d/alsa-base.conf
```
Update your install:
```
sudo apt-get update
sudo apt-get upgrade
sudo update-grub
```
Reboot. Now this to update alsa. Using a Terminal="Applications->Accessories->Terminal"
Add the ubuntu-audio-dev ppa:
```
sudo add-apt-repository ppa:ubuntu-audio-dev/ppa
sudo apt-get update
```
Now install:
```
sudo apt-get install linux-alsa-driver-modules-$(uname -r)
```
**Reboot**
Check your levels in alsamixer.
```
 alsamixer 
```
Press <F6> to select the correct soundcard.
Press <F3> to show playback levels. <F4> selects capture levels [or use <Tab>]
Use the left/right arrow keys to select and up/down arrow keys to change levels. <M> to mute/unmute.
Go to "System ->Preferences ->Sound" and make sure the correct soundcard is default and adjust your profile on the hardware tab. 
On the output tab choose the correct device.

I followed all the instructions and now my internal speakers are working properly.  I have no understanding of how these commands work, but they do!  Also I notice in other posts some people having problems with simultaneous output from speakers and headphones, but when I plug in my headphones, internal speakers do turn off as expected.

Thanks!

---

### Post by Trevor4706 on 2011-01-02
Lidex

I did as you suggested and ran the alsa script in the live environment and compared the result with that I get from the installed version.  Lots of info there, as you know.  No difference jumped out at me, altho I have to be honest and say I did not do an exhaustive line-by-line comparison beyond the first part that same to contain most of the data relating to system hardware and software.

Regards

Trevor

---

### Post by Dthsapprntc on 2011-01-26
So I have to admit that I am brand new to using Linux, and don't really know what I am doing. My laptop just ran an update this morning and now my internal speakers no longer work. I tried rerunning the scripts that I used to make them work earlier but it is not working. i am only getting the following line:

E: Couldn't find package linux-alsa-driver-modules-2.6.32-28-generic

here is my information again:

[http://www.alsa-project.org/db/?f=d31a5bf573f7bc249f8f6e58fdc9c1561dbcabf7](http://www.alsa-project.org/db/?f=d31a5bf573f7bc249f8f6e58fdc9c1561dbcabf7)

thanks for your time

---

### Post by safarj on 2011-01-27
Same here .. fire up the terminal and run command to remove latest kernel, then go to the Sound preferences and choose appropriate profile:
```
sudo aptitude remove linux-image-2.6.32-28-generic

```
Next time, before you proceed with update, check via commandline, if the PPA Alsa modules are part of the system:

```
$apt-cache search 2.6.32-27|grep alsa
linux-backports-modules-alsa-2.6.32-27-generic - Ubuntu supplied Linux modules for version 2.6.32 ALSA snapshots.
linux-backports-modules-alsa-2.6.32-27-preempt - Ubuntu supplied Linux modules for version 2.6.32 ALSA snapshots.
linux-backports-modules-alsa-2.6.32-27-server - Ubuntu supplied Linux modules for version 2.6.32 ALSA snapshots.
linux-headers-alsa-driver-2.6.32-27-server - Header files related to linux-alsa-driver-modules-lucid version 2.6.32 server
linux-headers-alsa-driver-2.6.32-27-generic - Header files related to linux-alsa-driver-modules-lucid version 2.6.32 generic
linux-alsa-driver-modules-2.6.32-27-server - Ubuntu-supplied Linux modules for version 2.6.32-27-server ALSA snapshots
linux-alsa-driver-modules-2.6.32-27-generic - Ubuntu-supplied Linux modules for version 2.6.32-27-generic ALSA snapshots
```

.. as you can see, there are no modules for the latest kernel:
```
apt-cache search 2.6.32-28|grep alsa
```

---

### Post by m3n3chm0 on 2011-01-27
Waiting for !!

---

### Post by lidex on 2011-01-27
> **Dthsapprntc said:**
> So I have to admit that I am brand new to using Linux, and don't really know what I am doing. My laptop just ran an update this morning and now my internal speakers no longer work. I tried rerunning the scripts that I used to make them work earlier but it is not working. i am only getting the following line:

E: Couldn't find package linux-alsa-driver-modules-2.6.32-28-generic

here is my information again:

[http://www.alsa-project.org/db/?f=d31a5bf573f7bc249f8f6e58fdc9c1561dbcabf7](http://www.alsa-project.org/db/?f=d31a5bf573f7bc249f8f6e58fdc9c1561dbcabf7)

thanks for your time

This should be fixed in maverick, if you don't mind upgrading. That would free you from the work-arounds. Or try a newer kernel from here:
[https://wiki.ubuntu.com/Kernel/MainlineBuilds](https://wiki.ubuntu.com/Kernel/MainlineBuilds)

---

### Post by m3n3chm0 on 2011-02-01
linux-alsa-driver-modules-2.6.32-28-generic*

Was released. I just update my system today :guitar:

---

### Post by bngsudheer on 2011-02-16
Hello,

After installing Ubunto 10.10 on my laptop, sound was not working properly. Thanks to Ubuntu forums and lidex, I could get it working. I am the OP of this thread.

I recently found out the sound is broken again. It only works on jack, ie, headset. The laptop speakers don't work.

[http://www.alsa-project.org/db/?f=6a4969b1ad9f7f26d369b2c42524af54210a7348](http://www.alsa-project.org/db/?f=6a4969b1ad9f7f26d369b2c42524af54210a7348) has detailed information about the hardware.

At the end of /etc/modprobe.d/alsa-base.conf I have
options snd-hda-intel model=ideapad

How can I fix it again?

---

### Post by bngsudheer on 2011-02-16
I updated the packages today. After rebooting it worked.

---

### Post by m3n3chm0 on 2011-03-05
Hi all,

Waiting again for linux-alsa-driver-modules-2.6.32-29-generic-pae  :popcorn:

Regards¡¡

:guitar:




[B]linux-alsa-driver-modules-2.6.32-29-generic-pae        - Ubuntu-supplied Linux modules for version 2.6.32-29-generic-pae

[COLOR=Blue][U][I]Ready to update   :lolflag:
[/I][/U][/COLOR][/B]

---

