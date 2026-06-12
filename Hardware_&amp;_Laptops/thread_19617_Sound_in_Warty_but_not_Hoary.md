---
title: "Sound in Warty but not Hoary"
date: 2005-03-12
forum: Hardware &amp; Laptops
---

### Post by Joh_ on 2005-03-12
I just updated my Ubuntu version today from Warty to Hoary. In Warty everything worked fine (except for the ATI drivers but that's another story). I had sound right out of the box through both Alsa and OSS. Now, when I run Hoary I have no sound at all.

My soundcard is a [CMedia](http://www.cmedia.com.tw) CMI9739 chipset integrated on my ASRock K7S8X motherboard. I've tried installing the drivers from their web page but I can't get them to work either.

Since I'm practically new to linux (been using it on and off for a few years) and especially Ubuntu or Debian, I don't know what information you need but I'm guessing it's atleast my lsmod output:

```
proc_intf               3908  0
freq_table              4004  0
cpufreq_userspace       4348  0
cpufreq_ondemand        6140  0
cpufreq_powersave       1632  0
video                  15972  0
sony_acpi               5928  0
pcc_acpi               11008  0
button                  6480  0
battery                 9988  0
container               4320  0
ac                      4676  0
ipv6                  257824  9
af_packet              21992  2
joydev                  9664  0
snd_usb_audio          65216  0
snd_usb_lib            12480  1 snd_usb_audio
snd_rawmidi            24480  1 snd_usb_lib
snd_seq_device          8460  1 snd_rawmidi
tsdev                   7520  0
8139cp                 20416  0
8139too                25856  0
mii                     4896  2 8139cp,8139too
sis900                 20068  0
usbhid                 31936  0
ehci_hcd               32676  0
ohci_hcd               21512  0
usbcore               118968  6 snd_usb_audio,snd_usb_lib,usbhid,ehci_hcd,ohci_hcd
cmaudio                57996  0
snd_intel8x0           32352  2
snd_ac97_codec         74144  1 snd_intel8x0
snd_pcm_oss            52132  1
snd_mixer_oss          19680  1 snd_pcm_oss
snd_pcm                94696  4 snd_usb_audio,snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              25060  1 snd_pcm
snd                    55012  11 snd_usb_audio,snd_rawmidi,snd_seq_device,snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore              10016  3 cmaudio,snd
snd_page_alloc          9732  2 snd_intel8x0,snd_pcm
i2c_sis96x              5252  0
i2c_core               22320  1 i2c_sis96x
shpchp                 99172  0
pci_hotplug            33488  1 shpchp
sis_agp                 8036  1
agpgart                33608  2 sis_agp
analog                 11584  0
gameport                4448  1 analog
floppy                 58864  0
pcspkr                  3496  0
rtc                    12472  0
md                     47280  0
dm_mod                 59420  1
evdev                   9344  0
capability              4648  0
commoncap               7712  1 capability
fglrx                 237088  7
psmouse                21320  0
mousedev               11288  1
parport_pc             37252  1
lp                     11144  0
parport                36744  2 parport_pc,lp
ide_cd                 41700  0
cdrom                  40220  1 ide_cd
ext3                  136424  1
jbd                    60216  1 ext3
mbcache                 8356  1 ext3
ide_generic             1312  0
sis5513                16328  1
ide_disk               20416  4
ide_core              129356  4 ide_cd,ide_generic,sis5513,ide_disk
unix                   28276  725
thermal                13320  0
processor              22452  1 thermal
fan                     4388  0
fbcon                  37504  0
font                    8192  1 fbcon
bitblit                 5472  1 fbcon
vesafb                  6724  0
cfbcopyarea             3808  1 vesafb
cfbimgblt               2912  1 vesafb
cfbfillrect             3488  1 vesafb

```

And I also assume you want my lspci output:
```
0000:00:00.0 Host bridge: Silicon Integrated Systems [SiS] 746 Host (rev 10)
0000:00:01.0 PCI bridge: Silicon Integrated Systems [SiS] SG86C202
0000:00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS963 [MuTIOL Media IO] (rev 25)
0000:00:02.1 SMBus: Silicon Integrated Systems [SiS]: Unknown device 0016
0000:00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE]
0000:00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] Sound Controller (rev a0)
0000:00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
0000:00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
0000:00:03.2 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
0000:00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 90)
0000:00:0b.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
0000:01:00.0 VGA compatible controller: ATI Technologies Inc RV280 [Radeon 9200 SE] (rev 01)
0000:01:00.1 Display controller: ATI Technologies Inc RV280 [Radeon 9200 SE] (Secondary) (rev 01)

```
If you need to know anything else to be able to help, please ask as I really need to get sound working to move from Windows to Linux.

Thanks in advance!

**EDIT:** The cmaudio module is actually the official drivers from CMedia. It seems to be loaded but I still have no sound and no users are using it. 8-[

**EDIT AGAIN:** The snd_usb_audio is my microphone integrated into my webcam.

---

### Post by bman08 on 2005-03-12
Same problem different hardware.  Warty worked perfectly, hoary nothing.  I have the Realtek ALC655 on my motherboard and the audigy2 and want to use the audigy.  Everything seems to be working as far as no error messages and the volume control slides up and down and stuff, but no sounds come out.  ](*,)

---

### Post by Eskokk on 2005-03-13
[QUOTE=Joh_]I just updated my Ubuntu version today from Warty to Hoary. In Warty everything worked fine (except for the ATI drivers but that's another story). I had sound right out of the box through both Alsa and OSS. Now, when I run Hoary I have no sound at all.

My soundcard is a [CMedia](http://www.cmedia.com.tw) CMI9739 chipset integrated on my ASRock K7S8X motherboard. I've tried installing the drivers from their web page but I can't get them to work either.

Since I'm practically new to linux (been using it on and off for a few years) and especially Ubuntu or Debian, I don't know what information you need but I'm guessing it's atleast my lsmod output:

```
proc_intf               3908  0
freq_table              4004  0
cpufreq_userspace       4348  0
cpufreq_ondemand        6140  0
cpufreq_powersave       1632  0
video                  15972  0
sony_acpi               5928  0
pcc_acpi               11008  0
button                  6480  0
battery                 9988  0
container               4320  0
ac                      4676  0
ipv6                  257824  9
af_packet              21992  2
joydev                  9664  0
snd_usb_audio          65216  0
snd_usb_lib            12480  1 snd_usb_audio
snd_rawmidi            24480  1 snd_usb_lib
snd_seq_device          8460  1 snd_rawmidi
tsdev                   7520  0
8139cp                 20416  0
8139too                25856  0
mii                     4896  2 8139cp,8139too
sis900                 20068  0
usbhid                 31936  0
ehci_hcd               32676  0
ohci_hcd               21512  0
usbcore               118968  6 snd_usb_audio,snd_usb_lib,usbhid,ehci_hcd,ohci_hcd
cmaudio                57996  0
snd_intel8x0           32352  2
snd_ac97_codec         74144  1 snd_intel8x0
snd_pcm_oss            52132  1
snd_mixer_oss          19680  1 snd_pcm_oss
snd_pcm                94696  4 snd_usb_audio,snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              25060  1 snd_pcm
snd                    55012  11 snd_usb_audio,snd_rawmidi,snd_seq_device,snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore              10016  3 cmaudio,snd
snd_page_alloc          9732  2 snd_intel8x0,snd_pcm
i2c_sis96x              5252  0
i2c_core               22320  1 i2c_sis96x
shpchp                 99172  0
pci_hotplug            33488  1 shpchp
sis_agp                 8036  1
agpgart                33608  2 sis_agp
analog                 11584  0
gameport                4448  1 analog
floppy                 58864  0
pcspkr                  3496  0
rtc                    12472  0
md                     47280  0
dm_mod                 59420  1
evdev                   9344  0
capability              4648  0
commoncap               7712  1 capability
fglrx                 237088  7
psmouse                21320  0
mousedev               11288  1
parport_pc             37252  1
lp                     11144  0
parport                36744  2 parport_pc,lp
ide_cd                 41700  0
cdrom                  40220  1 ide_cd
ext3                  136424  1
jbd                    60216  1 ext3
mbcache                 8356  1 ext3
ide_generic             1312  0
sis5513                16328  1
ide_disk               20416  4
ide_core              129356  4 ide_cd,ide_generic,sis5513,ide_disk
unix                   28276  725
thermal                13320  0
processor              22452  1 thermal
fan                     4388  0
fbcon                  37504  0
font                    8192  1 fbcon
bitblit                 5472  1 fbcon
vesafb                  6724  0
cfbcopyarea             3808  1 vesafb
cfbimgblt               2912  1 vesafb
cfbfillrect             3488  1 vesafb

```

And I also assume you want my lspci output:
```
0000:00:00.0 Host bridge: Silicon Integrated Systems [SiS] 746 Host (rev 10)
0000:00:01.0 PCI bridge: Silicon Integrated Systems [SiS] SG86C202
0000:00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS963 [MuTIOL Media IO] (rev 25)
0000:00:02.1 SMBus: Silicon Integrated Systems [SiS]: Unknown device 0016
0000:00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE]
0000:00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] Sound Controller (rev a0)
0000:00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
0000:00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
0000:00:03.2 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
0000:00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 90)
0000:00:0b.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
0000:01:00.0 VGA compatible controller: ATI Technologies Inc RV280 [Radeon 9200 SE] (rev 01)
0000:01:00.1 Display controller: ATI Technologies Inc RV280 [Radeon 9200 SE] (Secondary) (rev 01)

```
If you need to know anything else to be able to help, please ask as I really need to get sound working to move from Windows to Linux.

Thanks in advance!

**EDIT:** The cmaudio module is actually the official drivers from CMedia. It seems to be loaded but I still have no sound and no users are using it. 8-[

**EDIT AGAIN:** The snd_usb_audio is my microphone integrated into my webcam.[/QUOTE]
 I have the same problem. No sound in Hoary, Warty and Mandrake ok. I have a tv-card in my computer and it seems that it tries to use it as sound card and doesn't see the actual sound card at all.

---

### Post by trigg on 2005-03-13
Okay,
  I had a similar problem with an Audigy 2 Value card - though I was coming from suse to  ubuntu . . .  
  Apparently the ALSA version from apt-get didn't support my card, even though it was the most recent version ("1.0.8").  I just ran this

```
apt-get alsa-source linux-headers-(insert your kernel version here)
cd /usr/src
sudo tar -xvjf alsa-driver.tar.gz
cd modules/alsa-driver
sudo ./configure --with-cards=emu10k1 (or whatever card you have) --with-sequencer=yes
sudo make
sudo make install
``` 

added the appropriate modules to my /etc/modules files, rebooted so udev would create the appropriate devices, unmuted the channels and all was good.

---

### Post by Joh_ on 2005-03-13
[QUOTE=trigg]added the appropriate modules to my /etc/modules files, rebooted so udev would create the appropriate devices, unmuted the channels and all was good.[/QUOTE]
Excuse me for asking, but what exactly are the appropriate modules to add? I've never compiled ALSA before. Always came pre-installed.

---

### Post by bman08 on 2005-03-13
lsmod is showing snd_emu10k1 is loaded and happily running.  Alsa volume control shows the card and lets me adjust the volume.  Why would they support this card w/ built-in drivers in Warty but not Hoary?  I don't think this is the problem, but if you're sure I'll get to compiling.

---

### Post by trigg on 2005-03-13
[QUOTE=bman08]lsmod is showing snd_emu10k1 is loaded and happily running.  Alsa volume control shows the card and lets me adjust the volume.  Why would they support this card w/ built-in drivers in Warty but not Hoary?  I don't think this is the problem, but if you're sure I'll get to compiling.[/QUOTE]


I think it depends on the card.  I know that in earlier versions of alsa (pre 1.0.7) the emu10k1 supported the original Audigy and Audigy 2 chipsets.  With 1.0.8 they changed the driver to also support the Audigy 2 Value and the Audigy LS chipsets - I think the problem has something to do with the varying versions of the emu10k1 driver. . .

When I initiall install the alsa-base through apt-get, the modules seemed to load fine, but I was unable to access the card, change the volume (unmute), etc.  Once I compiled it myself, it worked fine.

---

### Post by trigg on 2005-03-13
[QUOTE=Joh_]Excuse me for asking, but what exactly are the appropriate modules to add? I've never compiled ALSA before. Always came pre-installed.[/QUOTE]


Sorry for not being more specific.  In my case  - these were the modules I added.

snd-pcm-oss 
snd-emu10k1
snd-mixer-oss


the modules that end in oss are for oss emulation so that software that doesn't necessarily support ALSA is fooled into thinking that is still using OSS.

to get a better idea of what modules you need take a look at this website

[http://www.alsa-project.org/alsa-doc/](http://www.alsa-project.org/alsa-doc/)

at the bottom of the page you can select the sound card manufacturer, then select the card you have and it will take you to the "how-to" documentation for the card - which should list the modules that pertain to the card

---

### Post by DougZ on 2005-03-13
Trigg,  tried your advice as I have an Audigy 2 Value that worked flawlessly under Warty, but is no longer works with Hoary.

recompiled, edited modules, rebooted. Nada. Still no sound

---

### Post by telmo on 2005-03-13
Same problem here with a ATI IXP AC'97... Warty was the only distro i tried where the sound worked flawlessly.

Someone HELP please!  [-o<

---

### Post by Joh_ on 2005-03-14
FINALLY! After hours of testing, reinstallations and coffee ( ;) ) i got it working! The problem was easier to solve than i thought. There was a sound channel i had to mute using alsamixer for some reason. So now i got sound working. :)

In case someone else has this problem, try muting and unmuting a couple of sound channels in alsamixer (run in terminal), and please note that you can scroll to the right amongst the channels (didn't know there was more than what was listed at the first screen).

The channel i had to mute was called "IEC958 Capture Monitor".


Thanks all who has tried to help. :)

---

### Post by haaglin on 2005-03-14
I have the same motherboard, but i'm not able to Control the volume. it don't respond to master volume, and the PCM snaps to either full or off. Does this work to you?  and i cant get alsa or OSS to work with the soundcard, i have to use ESD.

---

### Post by DougZ on 2005-03-14
Found the workaround solution for my Audigy 2 listed in the BugZilla discussion for Bug #6303.  Had to unmute the "Audigy Analog/Digital Output Jack" using alsamixer and voila I had sound.  (Gnome's mixer crashes if you try this - use alsamixer)

I would never have ever come up with this in a million years. I'd still be searching.

But I have sound now !!!  :D  :D  :D

---

### Post by bman08 on 2005-03-14
DougZ it is official, you are the man.   I had the speakers almost all the way up when the test tone came on.  I nearly had a heart attack :D.  Sound!  Sweet sweet sound!

---

### Post by Joh_ on 2005-03-14
[QUOTE=haaglin]I have the same motherboard, but i'm not able to Control the volume. it don't respond to master volume, and the PCM snaps to either full or off. Does this work to you?  and i cant get alsa or OSS to work with the soundcard, i have to use ESD.[/QUOTE]
No, i cannot. But that's only since the cmi9739 chipset doesn't support hardware volume. You have to do it with software (haven't figured out how yet but i'll look at it tomorrow). And actually, you should be able to use Alsa at the very least. Just run "killall esd" (without the quotes) and all Alsa apps will hopefully run fine, until you restart the computer that is. ;)

Got some work arounds to look at tomorrow. I've already activated a software mixer so i can play more than one sound at a time using Alsa.

---

### Post by trigg on 2005-03-15
[QUOTE=DougZ]Found the workaround solution for my Audigy 2 listed in the BugZilla discussion for Bug #6303.  Had to unmute the "Audigy Analog/Digital Output Jack" using alsamixer and voila I had sound.  (Gnome's mixer crashes if you try this - use alsamixer)

I would never have ever come up with this in a million years. I'd still be searching.

But I have sound now !!!  :D  :D  :D[/QUOTE]
 DougZ glad you got it working!  I just updated Alsa via apt-get and it looks like they have the modules fixed because I still have sound - (yes I have reloaded the new ones) so if anyone is having the same problem - you may not have to compile - just update repositories and upgrade packages.

EDIT: And of course, make sure you have the sound channels unmuted! ;)

---

### Post by haaglin on 2005-03-15
[QUOTE=Joh_]No, i cannot. But that's only since the cmi9739 chipset doesn't support hardware volume. You have to do it with software (haven't figured out how yet but i'll look at it tomorrow). And actually, you should be able to use Alsa at the very least. Just run "killall esd" (without the quotes) and all Alsa apps will hopefully run fine, until you restart the computer that is. ;)

Got some work arounds to look at tomorrow. I've already activated a software mixer so i can play more than one sound at a time using Alsa.[/QUOTE]

But i can control the volume in media apps like xmms, vlc and so on, just not the main volume. so there has to be some way to control the volume by software.

---

### Post by Joh_ on 2005-03-15
[QUOTE=haaglin]But i can control the volume in media apps like xmms, vlc and so on, just not the main volume. so there has to be some way to control the volume by software.[/QUOTE]
 Esd is a software mixer and might contain this ability, and since xmms has the ability to use esd, you can change the volume there. If you're not running esd (e.g killed it) and are using alsa or oss, xmms has the ability to use a software volume control. Either way, it's controlled by software. To get it working on the entire system you first need to get alsa to do it for you.

I'll have to get back on this though when I've figured out how. ;)

---

### Post by haaglin on 2005-03-15
How did you get alsa to work anyways? In multimedia systems selector, ESD is the only on that is working, all others gives me the output error: Failed to construct test pipeline.

---

### Post by heribou on 2005-03-15
Same from Warty to Hoary onto mac powerbook G3 pismo. No OSS nore ALSA working.
when running a sound app, got following error message :

ALSA lib seq_hw.c:446:(snd_seq_hw_open) open /dev/snd/seq failed: No such file or directory
Segmentation fault

everything was OK on Warty or Debian.

I have the last release from apt-get

---

### Post by kirkhayes on 2005-03-16
I think I am suffering from the same problem.

However, I have only been trying linux for the past couple of weeks, and I am really stuck.  I don't understand much of what people are saying or doing to solve this problem.

I have done the lspci and found out I have an Intel i810 soundcard.  I went to the alsa website to download the driver and info, but I got confused reading their directions.

I don't understand the part where it starts talking about editing out stuff and then adding in stuff.  It isn't specific enough for me to comprehend what version they are referring to.

Does someone have an example of what they did to get their card working?  I would then be able to mimic the same steps, but substitute for my card.

I am using BeatrIX distro.  I have attached lspci and dmesg

Thanks,

Kirk  :shock:

---

### Post by cabu on 2005-03-16
[QUOTE=Joh_]
The channel i had to mute was called "IEC958 Capture Monitor".
[/QUOTE]

Thanks for this bit of info. I am finally running Hoary with sound from onboard AC '97.

---

### Post by teevee on 2005-03-16
[QUOTE=Joh_]FINALLY! After hours of testing, reinstallations and coffee ( ;) ) i got it working! The problem was easier to solve than i thought. There was a sound channel i had to mute using alsamixer for some reason. So now i got sound working. :)

In case someone else has this problem, try muting and unmuting a couple of sound channels in alsamixer (run in terminal), and please note that you can scroll to the right amongst the channels (didn't know there was more than what was listed at the first screen).

The channel i had to mute was called "IEC958 Capture Monitor".


Thanks all who has tried to help. :)[/QUOTE]
Thanks Joh, I fiddled around with the same problem since upgrading to Hoary earlier today, I had to unmute exactly the same channel. It's late at night here and the speaker volume was quite high when I muted the channel - I think I heard one of my neighbors falling out of the bed. ;-)

---

### Post by Joh_ on 2005-03-17
[QUOTE=haaglin]How did you get alsa to work anyways? In multimedia systems selector, ESD is the only on that is working, all others gives me the output error: Failed to construct test pipeline.[/QUOTE]
As i stated previously, I just ran "killall esd", started a terminal and ran alsamixer. There I had to MUTE a channel called "IEC958 Capture Monitor". After that ALSA ran fine even if it told me that it couldn't create a test pipeline to ALSA.

So to get alsa to work permanently (**instead** of esd which means no esd applications will work), I did this:

[list=1]
[*]Opened a terminal window
[*]Ran the command **killall esd**
[*]Ran the command **alsamixer**
[*]Pressed the right arrow key on my keyboard past the edge of the terminal window until I reached the "IEC958 Capture Monitor" channel
[*]Pressed the **M** button to *MUTE* it and then the **escape** key
[*]Tested with xmms to see that I had sound (needed to change output to use ALSA under **Options -> Settings -> choose libALSA.so in the dropdown box** [note that I'm using swedish xmms and that the text could be different in an english xmms version]).
[*]Sound verified working. Time to save changes. In the open console window, I typed **alsactl store** (don't remember if you need to sudo this) to store the setting made in **alsamixer**
[*]Also went into **System -> Settings -> Sound** and unticked the box telling ubuntu to start the sound server at startup
[*]Rebooted machine to verify it was working, which it was :)
[/list]

Please note that this is what I did using the intel8x0 chipset. It might not work for you and I am not responsible if it doesn't.


I have actually came a bit further in making alsa work the way I want it to. I can now play many different sounds from both ALSA and ESD at the same time but ESD sounds pretty bad! I can also play sound from OSS if I kill ESD and don't play any other sound. I'm still working on it though and when I finally get it to work it is supposed to, with the ability to play many sounds from ESD, ALSA and OSS at the same time, plus ability to change the volume using software (since my soundcard doesn't support it using hardware), I'll probably post a HOWTO aimed at linux newbies with very descriptive step by step instructions. :)


Later... /Joh

---

### Post by bman08 on 2005-03-17
How do I get alsamixer to save the changes?  Everytime I reboot I've got to re-unmute the Analog/Digital output jack, also I have to start esd by hand every time I reboot.

---

### Post by oracledarren on 2005-03-17
to get alsamixer to save the changes

drop to a terminal
su
[password]
alsactl store

thats all there is to it  :smile:

---

### Post by trigg on 2005-03-18
[QUOTE=oracledarren]to get alsamixer to save the changes

drop to a terminal
su
[password]
alsactl store

thats all there is to it  :smile:[/QUOTE]

or if in ubuntu:
```
sudo dpkg-reconfigure alsa-base
```

---

### Post by haaglin on 2005-03-18
Thanx Joh_ , Let me know if you get the volume control to work, i'm running alsa now :-)

---

### Post by Joh_ on 2005-03-22
Well, to be honest, I did find the software volume plugin. But I didn't get it to work. =/

But I've got my computer to play multiple sounds at a time using both alsa and esd now (haven't tried oss but I'm sure it works using aoss). Do this to get both working:

[list=1]
[*]Open a console window
[*]Run the command **alsamixer**
[*]Press the right arrow key past the edge of the window until you reach the channel named *IEC958 Capture Monitor*, then press the **M** key to mute it
[*]Press the **escape** key to exit alsamixer and run **sudo alsactl store** to store the settings
[*]Open the file **/etc/apt/sources.list** with your favorite text editor and uncomment this line by removing the **#** in front of it: ```
# deb http://se.archive.ubuntu.com/ubuntu hoary universe
```
[*]Run the command **sudo apt-get update** and when that's finished, the command **sudo apt-get install libesd-alsa0 libsdl1.2debian-alsa**. This will make esd and sdl use alsa for sound output
[*]Create the file **/etc/asound.conf** (or the file **~/.asoundrc** depending on your needs) and give it the following contents: ```
pcm.!default {
    type plug
    slave.pcm "ossmix"
}
pcm.dsp0 {
    type plug
    slave.pcm "ossmix"
}
pcm.ossmix  {
    type dmix
    ipc_key 1024
    slave {
        pcm "hw:0,0"
        period_time 0
        period_size 2048
        buffer_size 32768
        #periods 128
        #rate 48000
    }
    bindings {
        0 0
        1 1
    }
}
ctl.mixer0 {
    type hw
    card 0
}

```
[*]Edit the file **/etc/esound/esd.conf** so it looks like this: ```
[esd]
auto_spawn=1
spawn_options=-terminate -nobeeps -as 2 -d default
spawn_wait_ms=100
```
[*]That should be it. :)
[/list]

Note that I do NOT guarantee that this will work with your soundcard or configuration. It worked for me with the intel8x0 module but that does not mean it will work with your configuration. I am not responsible if your computer breaks down to pieces.

I will keep looking for software volume changing. :)

**EDIT:** Why has this thread been placed in Warty troubles when it is relating to Hoary troubles?

---

### Post by haaglin on 2005-03-25
Nice, hope you find anything about the software volume. i'm still looking, but havent found anything yet. since we have the same mainboard, i will post it as soon as i find anything.

---

### Post by Joh_ on 2005-03-25
[QUOTE=haaglin]Nice, hope you find anything about the software volume. i'm still looking, but havent found anything yet. since we have the same mainboard, i will post it as soon as i find anything.[/QUOTE]
I actually did find something just today. The CVS version (1.1) of alsa-lib seems to support this for the C-Media chipsets (which our motherboards are using). Only problem is, I can't seem to get the CVS version for it. I've tried with the way they tell me to on their web page but cvs complaints over -z3 not being a valid parameter. 

I'm not giving up that easily though. Still trying. :p

---

### Post by haaglin on 2005-03-27
I also found something at alsa's pages. i haven't tried it yet, but i found it on another page ( [http://www.sabi.co.uk/Notes/linuxSoundALSA.html](http://www.sabi.co.uk/Notes/linuxSoundALSA.html) ), saying this would give us the ability to control the volume. But i have no idea what i'm suppose to do with this, i'm a linux newbie, so hopefully, you understand more of this. 

> 
CMI9739
This chipset is increasingly popular on various motherboards, and has some significant limitations, for example it the digital output can only be at 48000Hz. 
More importantly, the chip seems not to have the ability to change sound volume, and one needs a software volume control, like the newly introduced softvol plugin for /etc/asound.conf.
 

end of page: [http://www.alsa-project.org/alsa-doc/alsa-lib/pcm_plugins.html](http://www.alsa-project.org/alsa-doc/alsa-lib/pcm_plugins.html)
[http://www.alsa-project.org/alsa-doc/alsa-lib/pcm__softvol_8c.html#_details](http://www.alsa-project.org/alsa-doc/alsa-lib/pcm__softvol_8c.html#_details)

---

### Post by tsalem on 2005-04-02
[QUOTE=haaglin]I also found something at alsa's pages. i haven't tried it yet, but i found it on another page ( [http://www.sabi.co.uk/Notes/linuxSoundALSA.html](http://www.sabi.co.uk/Notes/linuxSoundALSA.html) ), saying this would give us the ability to control the volume. But i have no idea what i'm suppose to do with this, i'm a linux newbie, so hopefully, you understand more of this. 

 

end of page: [http://www.alsa-project.org/alsa-doc/alsa-lib/pcm_plugins.html](http://www.alsa-project.org/alsa-doc/alsa-lib/pcm_plugins.html)
[http://www.alsa-project.org/alsa-doc/alsa-lib/pcm__softvol_8c.html#_details](http://www.alsa-project.org/alsa-doc/alsa-lib/pcm__softvol_8c.html#_details)[/QUOTE]
 I believe I have the same motherboard, it's an ASRock, I'm not too sure on the model, but I had the same problem as those in this thread and umuting one of the volumes in alsamixer got me my audio back, but I was unable to control the volume. I kept scrolling to the right in alsamixer, and came across 4 different volumes, trying to adjust them to see if it would affect my volume at all. One of them did, it was labelled "VIA DSX 0"

So great, I could change my volume, but I needed to be able to control it without running alsamixer everytime, so I just right-clicked on the volume control in the system tray and hit Preferences. I set the device to Via and chose the Via DSX channel.

So now I have audio and I'm able to control it. I hope this helps. :)

---

### Post by La_PaRCa on 2005-04-02
[QUOTE=tsalem]I believe I have the same motherboard, it's an ASRock, I'm not too sure on the model, but I had the same problem as those in this thread and umuting one of the volumes in alsamixer got me my audio back, but I was unable to control the volume. I kept scrolling to the right in alsamixer, and came across 4 different volumes, trying to adjust them to see if it would affect my volume at all. One of them did, it was labelled "VIA DSX 0"

So great, I could change my volume, but I needed to be able to control it without running alsamixer everytime, so I just right-clicked on the volume control in the system tray and hit Preferences. I set the device to Via and chose the Via DSX channel.

So now I have audio and I'm able to control it. I hope this helps. :)[/QUOTE]
 Um, I still dont know how to change my sound daemon from esd to ALSA, anyone that can tell me exactly how to do it would be appreciated.

---

### Post by Joh_ on 2005-04-07
Okay! Now I've finally got it to work with the PCM volume, not Master. All i did was update my alsa-driver, alsa-lib, alsa-oss, alsa-plugins and alsa-utils to version 1.0.9rc2 (newest at this time, can be downloaded from [www.alsa-project.org)](www.alsa-project.org)). I compiled alsa-driver like this:
```
tar xvjf alsa-driver-1.0.9rc2.tar.bz2
cd alsa-driver-1.0.9rc2
./configure --with-cards=intel8x0
make
sudo make install
```
The rest i compiled the same way except i ran only ./configure (without arguments).

After compiling everything and restarting my computer, i changed my /etc/asound.conf into this:
```
pcm.!default {
    type plug
    slave.pcm {
        type softvol
        slave.pcm "ossmix"
        control {
             card 0
             name "PCM Playback Volume"
        }
    }
}
pcm.dsp0 {
    type plug
    slave.pcm "ossmix"
}
pcm.ossmix  {
    type dmix
    ipc_key 1024
    slave {
        pcm "hw:0,0"
        period_time 0
        period_size 2048
        buffer_size 16384
        #periods 128
        #rate 48000
    }
    bindings {
        0 0
        1 1
    }
}
ctl.mixer0 {
    type hw
    card 0
}

```
And then I could change the volume with alsamixer (I'm using kubuntu so I haven't tried GMix, KMix didn't work since my PCM channel wasn't listed).

Hope this helps :)

---

### Post by haaglin on 2005-04-07
Nice work!

---

### Post by Martin Witte on 2005-04-09
[QUOTE=Joh_]FINALLY! After hours of testing, reinstallations and coffee ( ;) ) i got it working! The problem was easier to solve than i thought. There was a sound channel i had to mute using alsamixer for some reason. So now i got sound working. :)

In case someone else has this problem, try muting and unmuting a couple of sound channels in alsamixer (run in terminal), and please note that you can scroll to the right amongst the channels (didn't know there was more than what was listed at the first screen).

The channel i had to mute was called "IEC958 Capture Monitor".


Thanks all who has tried to help. :)[/QUOTE]
Thanks - I fixed it exactly like this on my asrock motherboard

---

