---
title: "Gateway MX3414 Laptop - AMD64 - Several Problems"
date: 2006-08-17
forum: Hardware &amp; Laptops
---

### Post by Gnuklear on 2006-08-17
Hey guys,

I recently purchased a [Gateway MX3414 Laptop]("http://www.bestbuy.com/site/olspage.jsp?skuId=7889065&type=product&id=1149206139777&ref=06&loc=01") on which I installed Ubuntu 6.06.1 AMD64 Edition and for the most part things have been pleasant. However, there are a couple pieces of hardware that either do not work at all, or only work partially. Here's a basic rundown:

What Worked Completely:
- Keyboard ;)
- Ethernet
- USB Ports

What Worked Partially:
- Video Card - Screen Resolution options are only 640x480, 800x600 and 1024x768, and the refresh rate listed in the drop down menu is 0Hz.
- Wireless - Chip is recognized and when properly configured can connect, but signal strength is always displayed as 0 when in reality it is much higher (so yes, the Wireless connection works).
- Mouse (Touchpad) - On the i386 version, it works completely. Only difference on AMD64 is that selecting text is not possible, and when attempting to move scrollbars, they only move after the first mouse button is released (aka, do not respond in realtime). Tested with another mouse to see if this was an GNOME-AMD64 issue, and the other mouse worked as expected, seems to just be an issue with the touchpad on AMD64.

What Doesn't Work:
- Sound - SigmaTel STAC 92xx. I've read that many other people have had problems, but that this was a bug in ALSA up to 1.0.11, and that with ALSA 1.0.11 only a single line need be added to a configuration file to get sound working on this card. ALSA 1.0.11 is available in Edgy, but I'd prefer not to upgrade my entire operating system to an experiment system in order to get sound working. I've also read that it is possible to use apt-source to download ALSA 1.0.11 from Edgy and get it working on Dapper, but I'm not familiar enough with apt or compiling from source to get it working. Any help on this issue would be greatly appreciated.

For those interested, here is the contents of an lsmod on my system:
```
ubuntu@ubuntu:~$ lsmod
Module                  Size  Used by
usbhid                 43040  0
rfcomm                 45600  0
l2cap                  30464  5 rfcomm
bluetooth              59268  4 rfcomm,l2cap
ipv6                  300416  10
ppdev                  11400  0
parport_pc             40816  0
lp                     15040  0
parport                44172  3 ppdev,parport_pc,lp
powernow_k8            12992  1
cpufreq_userspace       9184  1
cpufreq_stats           8264  0
freq_table              6464  2 powernow_k8,cpufreq_stats
cpufreq_powersave       3328  0
cpufreq_ondemand        9768  0
cpufreq_conservative    10984  0
video                  18824  0
tc1100_wmi              9096  0
sony_acpi               7188  0
pcc_acpi               16128  0
hotkey                 13768  0
dev_acpi               15364  0
container               6272  0
button                  8864  0
acpi_sbs               24600  0
battery                12296  1 acpi_sbs
i2c_acpi_ec             7040  1 acpi_sbs
ac                      7176  1 acpi_sbs
dm_mod                 63176  1
md_mod                 76792  0
joydev                 13184  0
tsdev                  10240  0
snd_hda_intel          21664  4
snd_hda_codec         190920  1 snd_hda_intel
snd_pcm_oss            59424  0
snd_mixer_oss          20608  1 snd_pcm_oss
snd_pcm               104584  4 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_timer              29064  2 snd_pcm
snd                    68576  12 snd_hda_intel,snd_hda_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
psmouse                40324  0
soundcore              13216  1 snd
snd_page_alloc         13968  2 snd_hda_intel,snd_pcm
pcspkr                  3592  0
serio_raw               9732  0
r818x                  97808  0
ieee80211_rtl          90384  1 r818x
i2c_core               26624  1 i2c_acpi_ec
shpchp                 51360  0
pci_hotplug            33168  1 shpchp
af_packet              28172  4
evdev                  14464  2
squashfs               44416  1
unionfs                94232  1
loop                   19216  2
nls_cp437               8320  1
isofs                  39808  1
ide_generic             2816  0
ohci_hcd               23684  0
forcedeth              34444  0
ehci_hcd               36232  0
usbcore               147004  4 usbhid,ohci_hcd,ehci_hcd
ide_cd                 35744  1
cdrom                  41144  1 ide_cd
ide_disk               19456  2
generic                 7300  0
amd74xx                17072  0 [permanent]
sata_nv                12548  0
libata                 85536  1 sata_nv
scsi_mod              160504  1 libata
thermal                16524  0
processor              29736  2 powernow_k8,thermal
fan                     6408  0
capability              7176  0
commoncap               9728  1 capability
vga16fb                15120  1
cfbcopyarea             5120  1 vga16fb
vgastate               10368  1 vga16fb
cfbimgblt               4224  1 vga16fb
cfbfillrect             5760  1 vga16fb
fbcon                  43136  72
tileblit                4096  1 fbcon
font                    9984  1 fbcon
bitblit                 7424  1 fbcon
softcursor              3712  1 bitblit
```

---

### Post by John.Michael.Kane on 2006-08-18
Heres a guide for setting up the nvidia card [Latest_Nvidia_Dapper]("http://doc.gwos.org/index.php/Latest_Nvidia_Dapper") that should fix the resolution issues.

lsmod is showing that your sound device is seen. so i'm not sure why your not having sound.

---

### Post by jaybf11 on 2006-08-19
I am having similar problems with the mx3414.

for the video resolution modified the monitor section indicated below and was able to get the resolution up to the 1280x800 native resolution:

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
 	HorizSync       28-80         
	VertRefresh     43-60
EndSection

I also had to add "1280x800" to each display subsection as below:

	SubSection "Display"
		Depth		24
		Modes		"1280x800" "1024x768" "800x600" "640x480"
	EndSubSection

for the touchpad i commented out the synaptics entry under serverlayout as below:

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
#	InputDevice	"Synaptics Touchpad"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"
EndSection

only problem with this is that the scroll feature of the touchpad is not functioning.

still haven't found a resolution for the sound card.  i thought it was part of the nvidia chipset though.  i may be wrong but i think the sigmatel is for the modem.

the nvidia chipset is the geforce go 6100 which includes the network and sound card.

wireless card is realtek 8185 which i also have a problem with.  network manager only shows wep as an option.  i can't get it to support wpa or wpa2.

---

### Post by John.Michael.Kane on 2006-08-19
These may help with your wireless issues.
[realtek+8185]("http://www.ubuntuforums.org/showthread.php?t=191776&highlight=realtek+8185")

[**realtek+818**]("http://www.ubuntuforums.org/showthread.php?t=95879")

If you feel you need to file a bug report. **[COLOR="Red"]Please be as detailed as you can eg include all info/msg.[/COLOR]**
[**Realtek ubuntu/+bug/55905**]("https://launchpad.net/distros/ubuntu/+bug/55905")

---

### Post by Gnuklear on 2006-08-19
Thanks for the help, guys.

Jay: I tried what you suggested for the resolution, and for some odd reason the screen still displays at 1024x768. I'm rather vexed on this one. However, by commenting out the Touchpad, the "mouse" buttons suddenly became much more responsive, but I cannot use the scroll bar now either. I'm going to file a bug report on this. Also, I've started a LaptopTeam wiki page for this model, ( [http://wiki.ubuntu.com/LaptopTeam/GatewayMX3414]("http://wiki.ubuntu.com/LaptopTestingTeam/GatewayMX3414") ) and would appreciate your assistance in confirming the issues with this model.

SD: I'd prefer not to use the proprietary NVidia drivers, I'm one of those Free Software zealots you hear tell of.;) Thanks for the helpful links though. As a clarification, the Integrated Wireless works (at least for me) with the Free/Open Source drivers that are packaged with Ubuntu. The only issue with them is that signal strength is always displayed as 0. I haven't had the need to try to use WPA authentication with it, so I can't really help there.

I did some more research on the sound card, and the problem appears to be that the STAC92xx audio codec (which this card uses) is broken in Dapper and unfortunately also in Etchy. From what I've read, the issue appears to be fixed in ALSA 1.0.11-rc4 and above, which I believe Ubuntu will sadly not get into its repositories until November (since Etchy is upstream frozen). That said, there should be a way to compile the newer ALSA version manually, but my technical experience isn't up to par for that course. Any help whatsoever on that would be appreciated.

---

### Post by jaybf11 on 2006-08-19
i've attached a full copy of my xorg.conf.

---

### Post by Gnuklear on 2006-08-19
Completely fixed my resolution problems by replacing my xorg,conf file with yours. It seems that the driver was this source of the problem. I had been using vesa, but by switching to nv is recognized the new resolution. Thanks so much, Jay!

I tried compiling ALSA 1.0.12r3 from source, and can get it to compile successfully, but still no sound. This may very well be because I don't know what I'm doing as far as configurations after compiling. The install guide suggests using alsaconf, but... I can't get alsa-utils to compile - it can't find ncurses. Still working on that.

EDIT:

Got alsa-utils to compile by apt-getting ncurses5-dev package. The good news: alsaconf recognizes the soundcard as "hda-intel nVidia Corporation MCP51 High Definition Audio (rev a2)". However, sound doesn't work... I haven't given up, I'm getting closer every minute.

---

### Post by jaybf11 on 2006-08-19
had similar results with compiling 1.0.12 rc2.  I'm considering trying another distro at this point although this is my second.  So far i've tried the 32bit and 64bit versions of ubuntu and novell suse enterprise desktop 10.1 and got similar results with the sound, video and wireless.  I may return this puppy to best buy tomorrow if i can't get this stuff working.

---

### Post by Rokcwlr on 2006-08-22
Hi guys, I found the driver problem for this computer for the AUDIO. Took me awhile but here it is, do a google search for this driver 'Realtek_HD_MI31006', install it (its a bus sys driver) and then u will see the audio and modem to install. hope this helps someone. My mx3414 is up and running great now.

Ah, Cant find it, heres a link to a download [http://rapidshare.de/files/30361739/Realtek_HD_MI31006.zip.html](http://rapidshare.de/files/30361739/Realtek_HD_MI31006.zip.html)

---

### Post by degel3030 on 2006-08-25
just want to thank you for starting the wiki, i bought my laptop about 2 weeks and do like it
one thing with that xorg.conf it takes away the ability to use the side scroll on the mouse pad, not sure if this happened to anyone else but my mouse works perfectly out of the default install. now if we could get nvidia drivers to work correctly

---

### Post by parkash on 2006-08-27
I have also the GeForce Go 6100... But I don't get nvidia-glx to work...  How did you do it?  What driver do I need?

---

### Post by parkash on 2006-08-27
haha, oops... Hadn't nvidia-kernel installed... :p

---

### Post by jaybf11 on 2006-08-27
On the nvidia drivers -- apparently nvidia identified a bug in the drivers that prevent it from working on the geforce go 6100 card and there's no bug fix in sight so no xgl.

[http://www.nvnews.net/vbulletin/showthread.php?t=75129&page=2](http://www.nvnews.net/vbulletin/showthread.php?t=75129&page=2)

---

### Post by rabbi1337 on 2006-08-30
Yes, thanks so much for the xorg jay, it works for me now without a funny looking wide picture :-) I also have the mouse scroll problem but I actually just modded your config a little bit. There is a line near the bottom of the file for Synaptics that was commented out for some reason. Now my gfx card/touchpad work great but still no sound.

---

### Post by degel3030 on 2006-09-08
can you explain what mouse problems you had/have? the only thing i have problems is that while im typing the mouse doesnt disable

o and i just upgraded to edgy, had a little problem with nautilis but now i seem to be working ok, still havent tested the sound though

---

### Post by degel3030 on 2006-10-05
was wondering if anyone has had any luck getting the sound to work on this, i have updated to 6.10 but the alsamixer is 1.0.11
if anyone has been able to get the audio to work, either headphones or speakers please repost with some hints, about the only thing thats keeping me from using this fulltime on my laptop

---

### Post by brandoncolorado on 2007-01-07
Still no luck for me!  I cannot get the sound to work, and I have not found a good post telling me how to get it working!](*,)

---

### Post by brandoncolorado on 2007-01-28
> **degel3030 said:**
> was wondering if anyone has had any luck getting the sound to work on this, i have updated to 6.10 but the alsamixer is 1.0.11
if anyone has been able to get the audio to work, either headphones or speakers please repost with some hints, about the only thing thats keeping me from using this fulltime on my laptop

What about you, any luck yet?

---

### Post by brandoncolorado on 2007-02-04
Have you tried ALSA 1.0.14 RC2?

---

### Post by brandoncolorado on 2007-02-12
I just read the 1.0.14rc2 change log at ALSA.  It looks like there is a partial fix already built in, and that they are working on this problem for 1.0.14 final release.  Hopefully my reading is right.

---

### Post by brandoncolorado on 2007-03-03
No luck.

Bump for help

---

### Post by rabbi1337 on 2007-03-05
Hello all.

Just an update. I'm on a MX3414 running Edgy and so far so good at this point except for the following:

Sound: Compiled latest ALSA Driver 1.0.14rc2 to no avail

Video: New NVidia 1.0-9746 Drivers working perfectly when built from nvidia-installer. Only issue is when doing CTRL+ALT+F1 etc for a TTY terminal the screen gets glitchy and blinks with artifacts.

Everything else is working well. I'll be happy to post an xorg.conf or whatever else anyone with this laptop needs.

---

### Post by brandoncolorado on 2007-03-05
Hey, awesome you got everything working.  I have everything working too, I have used Envy to get the Nvidia drivers installed.  My touchpad is a little off because there is the arrow part on the right, but the right part of the touchpad still scrolls so there are two scrolling parts.

My real frustrations:

1) No sound.  I too have installed 1.0.14RC2.  This is a bug, and as confirmed by ALSA people, it is a known bug and they are working on it.

2) My wireless is real spotty at school.  I cannot figure it out.  Which wireless driver are you using?  Default?  Ndiswrapper with windows driver?

---

### Post by rabbi1337 on 2007-03-11
> **brandoncolorado said:**
> 2) My wireless is real spotty at school.  I cannot figure it out.  Which wireless driver are you using?  Default?  Ndiswrapper with windows driver?

I did a clean re-install of edgy and the card was detected automatically. :)

I also updated to the latest 1.0-9755 NVidia Drivers and it fixed the screen glitches I was having.

Now the only remaining issue is that there is still no sound, and because I often play music, this is the only thing keeping me from switching 100% linux.

---

### Post by alty29 on 2007-03-21
> **rabbi1337 said:**
> I did a clean re-install of edgy and the card was detected automatically. :)

I also updated to the latest 1.0-9755 NVidia Drivers and it fixed the screen glitches I was having.

Now the only remaining issue is that there is still no sound, and because I often play music, this is the only thing keeping me from switching 100% linux.


So I downloaded those Nvidia drivers, but I do not know how to install them. "Could not open the file /home/alex/Desktop/NVIDI…-x86_64-1.0-9755-pkg2.run."


How can I install it?

---

### Post by brandoncolorado on 2007-03-21
Google "Envy Ubuntu" use that.

---

### Post by alty29 on 2007-03-21
That worked. Anyone figure out sound problem yet?

---

### Post by brandoncolorado on 2007-03-21
> **alty29 said:**
> That worked. Anyone figure out sound problem yet?

There is no quick fix or anything.  The ALSA programmers are aware of it.  Hopefully we will see a change with 1.0.14rc4.

---

### Post by rabbi1337 on 2007-04-05
For all you MX3410 / MX3414 /MX3416, I found out something recently!

I basically uninstalled everything I could that had to do with alsa (sudo apt-get remove alsa*, sudo  make uninstall in rc3 source directory) and installed the latest version of OSS 

[http://www.opensound.com/download.cgi](http://www.opensound.com/download.cgi)

After installing this from .tar in the / directory, I deleted some file it told me to called "starting." 

Then I rebooted, and ran sudo soundon and played with ossmix
I ran osstest and got nothing. I played around some more then tried osstest again but this time I figure i'd try to use my headphones.

Here's the catch: I plugged my headphones into the MICROPHONE jack and running osstest, suprise, suprise, I had some sound! It was coming in fine volume wise, in stereo, a little staticy... 

...but there WAS SOUND! :guitar: 

Consequently, plugging my headphones into the headphone jack did nothing, and the front-end for X would not detect that OSS had installed it. :mad: 

Hopefully some of you can try this and get some partially working sound on your MX34XX.

---

### Post by degel3030 on 2007-04-27
wtf are you serious? in the mic port you got sound? is this possible?

i wanted to post just to say that i did a clean install on the latest 4.07 ubuntu install and now my wifi doesnt work....anyone else have this issue?

---

### Post by igpf on 2007-05-27
I just click on the link but its broken.  I'm tryingto figure out the audio issue as well. i have a mx3414 i got everything working execpt audio.  Any help here would be great. i'm a bit new with ubuntu, altough I've always been a fan.

---

### Post by Andrewie on 2007-06-03
> **igpf said:**
> I just click on the link but its broken.  I'm tryingto figure out the audio issue as well. i have a mx3414 i got everything working execpt audio.  Any help here would be great. i'm a bit new with ubuntu, altough I've always been a fan.

I've also got a Gateway mx3410, can you tell me how you got your laptop to sleep?

---

### Post by indianajones123 on 2007-07-30
I'm a complete Linux newbie and I've been messing around with it for the past few days now.  cool stuff.  I have a gateway MX3414 and have been running into all the issues everyone is posting about.  I got wireless to work on my own... looks like the video issue will be easy enough to do tomorrow when i have more time and get the NVidia 1.0-9746 drivers.

Has there been any progress on the sound issue with this machine?  I was hoping with the release of Feisty there'd be a solution.  I'm dying to use Ubuntu more, but having no music is seriously killing my mood.

---

### Post by JustBrowsing on 2007-07-30
Wow, someone is actually posting in this topic.

I just followed "rabbi1337"'s advice and it does work. Sound does come out the microphone jack, I think that's what I'm plugging it into.

If you use the OSS drivers it will give you the sound if you extract the files into the "/" folder of your "filesystem" portion.

While the speakers don't currently work, having the sound coming out of headphone/microphone port is actually much better than nothing. I usually listen to music through headphones if I use my laptop in the library, and when my notebook at my desk it's hooked up to my Klipsch speakers .... so while this isn't perfect, it does allow you to listen to music.

The speakers suck on these laptops anyway.... however I got a feeling this issue will be fixed pretty soon, atleast I can now listen to music while playing around in Ubuntu.

---

### Post by indianajones123 on 2007-08-27
I may have found something helpful to everyone that still has sound issues.  I haven't had a chance to follow the steps as I'm at work, but if anyone wants to try this or experiment, please let me know if you have any success.

[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/117246](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/117246)

---

### Post by Andrewie on 2007-08-28
> **indianajones123 said:**
> I may have found something helpful to everyone that still has sound issues.  I haven't had a chance to follow the steps as I'm at work, but if anyone wants to try this or experiment, please let me know if you have any success.

[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/117246](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/117246)

the guy with the MX3414 said that it didn't work for his laptop.

---

### Post by brandoncolorado on 2007-09-11
[https://bugtrack.alsa-project.org/alsa-bug/view.php?id=2948](https://bugtrack.alsa-project.org/alsa-bug/view.php?id=2948)

---

### Post by rabbi1337 on 2007-09-24
Victory is ours!!! MX3414 now has working sound here. :-)

[https://bugtrack.alsa-project.org/alsa-bug/view.php?id=3036](https://bugtrack.alsa-project.org/alsa-bug/view.php?id=3036)

This page has these files:
 patch_sigmatel.c.patch-1.0.15rc1-simple [^] (462 bytes) 09-09-07 22:58
 15rc1_patch_install [^] (449 bytes) 09-09-07 22:59

Downloaded the three RC1 tars from alsa, typed in each individual command listed in 15rc1_patch_install. I manually stopped alsa before running alsaconf by doing /etc/init.d/alsasound stop. ran the alsactl store, removed the file /etc/asound.state then restarted alsasound and ran alsamixer.

As soon as I did sudo rm /etc/asound.state file and /etc/init.d/alsasound start, then ran mixer, that seems like the thing I was missing before. Hope this helps!

Here's the official thread on Alsa: [https://bugtrack.alsa-project.org/alsa-bug/view.php?id=2948](https://bugtrack.alsa-project.org/alsa-bug/view.php?id=2948)

---

### Post by julianmh on 2007-12-10
Does this solution work? Has anyone tried it? I'm on Windows right now, because I don't know the key to my wireless network, so I would like to know if it works before I try it.

---

### Post by brandoncolorado on 2007-12-10
The sound works by default in in the latest release of ALSA, wireless is still broken for WEP encrypted.  If you install and try to use the default wireless, your computer will freeze.

---

### Post by julianmh on 2007-12-10
What will I need to do for the wireless?

---

### Post by brandoncolorado on 2007-12-10
[https://bugs.launchpad.net/ubuntu/+bug/152522](https://bugs.launchpad.net/ubuntu/+bug/152522)

You could open up your wireless (no WEP) and I think that would work.

---

### Post by julianmh on 2007-12-10
I won't be able to do it without encryption, but it seems that ndiswrapper works. Thanks!

---

### Post by brandoncolorado on 2007-12-31
To clarify for anyone subscribed to this thread:

1)  The sound issue has been fixed by default in ALSA 1.0.15.  Ubuntu 7.10 has 1.0.14 by default, so to get working sound you must download and install the latest driver, library and utils from ALSA.

2)  The wireless freeze is still a problem, and a bug has been filed.

---

### Post by igpf on 2008-01-10
I also got the sound working.  I found this info somewhere in this forum:
> I got it all working! Thanks to plun in the swedish Ubuntu forum.

1. Download the latest alsa package from here: [ftp://ftp.suse.com/pub/projects/alsa/snapshot/driver](ftp://ftp.suse.com/pub/projects/alsa/snapshot/driver)

2. Extract it where ever you like and use cd in a terminal to get there.

3. Do: ./configure --with-oss=yes --with-sequencer=yes --with-cards=hda-intel ; make

4. sudo make install

I did it step for step, and it works perfectly.  Thanks to whoever put this up.

I also had the problem with the wifi freezing... ndiswrapper worked, but I'm not worried.  Sound was more important for me.

---

