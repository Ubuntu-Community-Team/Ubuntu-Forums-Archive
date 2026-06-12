---
title: "Sound on Toshiba A75"
date: 2004-12-04
forum: Hardware &amp; Laptops
---

### Post by vdubgeek on 2004-12-04
Hello - 
I'm in the process of installing Ubuntu on a new Toshiba A75.  I've managed to get the integrated wireless running, but can't quite figure out why sound is not functioning.  

The onboard audio is IXP150 AC'97 .  I've tried the pci=noacpi grub boot param with no luck.  I've also tried just noacpi , with no luck as well.    There is no /dev/dsp .

Interestingly, output from dmesg shows:

ATI IXP AC97 controller: probe of 0000:00:14.5 failed with error -13


Here is config info:

_lsmod:_
Module                  Size  Used by
wlan_tkip              11200  2
acpi                    6432  0
proc_intf               4128  0
freq_table              4512  1 acpi
cpufreq_userspace       7072  4
cpufreq_powersave       1952  0
ipv6                  273956  10
ds                     18756  2
button                  6808  0
ac                      5036  0
battery                 9612  0
af_packet              23496  6
yenta_socket           21248  0
pcmcia_core            69108  2 ds,yenta_socket
8139too                27008  0
8139cp                 21792  0
mii                     5280  2 8139too,8139cp
crc32                   4512  2 8139too,8139cp
ath_pci                57124  0
wlan                  119036  3 wlan_tkip,ath_pci
ath_hal               129520  2 ath_pci
ohci1394               36004  0
ehci_hcd               32068  0
ohci_hcd               21924  0

usbcore               119044  4 ehci_hcd,ohci_hcd
shpchp                100364  0
pciehp                 96908  0
pci_hotplug            34716  2 shpchp,pciehp
ati_agp                 8684  1
agpgart                34316  1 ati_agp
irtty_sir               9760  0
sir_dev                20092  1 irtty_sir
irda                  204480  2 irtty_sir,sir_dev
crc_ccitt               2336  1 irda
pcspkr                  3884  0
rtc                    14088  0
md                     50184  0
dm_mod                 58592  1
capability              4744  0
commoncap               7392  1 capability
snd_atiixp             22088  0
snd_ac97_codec         68772  1 snd_atiixp
snd_pcm_oss            53864  0
snd_mixer_oss          19744  1 snd_pcm_oss
snd_pcm                99552  2 snd_atiixp,snd_pcm_oss
snd_timer              26756  1 snd_pcm
snd                    57828  6 snd_atiixp,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore              10688  1 snd
snd_page_alloc         11688  2 snd_atiixp,snd_pcm
parport_pc             35680  1
lp                     11044  0
parport                42216  2 parport_pc,lp
sbp2                   24488  0
ieee1394              110744  2 ohci1394,sbp2
tsdev                   7488  0
evdev                   9696  0
ide_cd                 42180  0
mousedev               10480  1
psmouse                19976  0
sr_mod                 17316  0
scsi_mod              125412  2 sbp2,sr_mod
cdrom                  39808  2 ide_cd,sr_mod
ext3                  126344  1
jbd                    68952  1 ext3
mbcache                10148  1 ext3
ide_generic             1632  0
ide_disk               19136  3
atiixp                  9272  1
ide_core              138896  4 ide_cd,ide_generic,ide_disk,atiixp
unix                   30576  698
fan                     4204  0
thermal                13232  0
processor              18272  2 acpi,thermal
font                    8576  0
vesafb                  6784  0
cfbcopyarea             3936  1 vesafb
cfbimgblt               3296  1 vesafb
cfbfillrect             3840  1 vesafb

_lspci:_
0000:00:00.0 Host bridge: ATI Technologies Inc: Unknown device 5831 (rev 02)
0000:00:01.0 PCI bridge: ATI Technologies Inc: Unknown device 5838
0000:00:13.0 USB Controller: ATI Technologies Inc: Unknown device 4347 (rev 01)
0000:00:13.1 USB Controller: ATI Technologies Inc: Unknown device 4348 (rev 01)
0000:00:13.2 USB Controller: ATI Technologies Inc: Unknown device 4345 (rev 01)
0000:00:14.0 SMBus: ATI Technologies Inc ATI SMBus (rev 18)
0000:00:14.1 IDE interface: ATI Technologies Inc: Unknown device 4349
0000:00:14.3 ISA bridge: ATI Technologies Inc: Unknown device 434c
0000:00:14.4 PCI bridge: ATI Technologies Inc: Unknown device 4342
0000:00:14.5 Multimedia audio controller: ATI Technologies Inc IXP150 AC'97 Audio Controller
0000:00:14.6 Modem: ATI Technologies Inc: Unknown device 434d (rev 01)
0000:01:05.0 VGA compatible controller: ATI Technologies Inc: Unknown device 5835
0000:02:00.0 FireWire (IEEE 1394): Texas Instruments TSB43AB21 IEEE-1394a-2000 Controller (PHY/Link)
0000:02:02.0 Ethernet controller: Atheros Communications, Inc. AR5212 802.11abg NIC (rev 01)
0000:02:03.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
0000:02:04.0 CardBus bridge: ENE Technology Inc CB710 Cardbus Controller
0000:02:04.1 FLASH memory: ENE Technology Inc: Unknown device 0530
0000:02:04.2 Class 0805: ENE Technology Inc: Unknown device 0550
0000:02:04.3 FLASH memory: ENE Technology Inc: Unknown device 0520

Any tips would be appreciated greatly, thanks!

---

### Post by zoso on 2004-12-04
I'm also running Ubuntu on an A75 and have the same problem. After doing some searching on Google I came up with only one reference to running Linux on an A75.

[http://jmccoy.sdf-us.org/slackware10/toshiba-a75.php](http://jmccoy.sdf-us.org/slackware10/toshiba-a75.php)

According to the writer hotplug is incorrectly loading the snd-atiixp-modem module in addition to the snd-atiixp module. Ubuntu doesn't appear to be doing this, according to the output of lsmod. Still, I gave it a shot but no joy.

If I make any progress with this I'll post about it here. However, any insight would be appreciated.

---

### Post by jdong on 2004-12-04
atiixp 9272 1

Both OSS and ALSA drivers are loaded. Try rmmodding the above module.

---

### Post by vdubgeek on 2004-12-04
[QUOTE=jdong]atiixp 9272 1mm

Both OSS and ALSA drivers are loaded. Try rmmodding the above module.[/QUOTE]

Hmmm, I tried removing the module, using both rmmod, and modprobe.  I'm still not able to get any audio.  Plus, if I reboot, atiixp is auto loaded.  How can I ensure this module isn't auto loaded?

---

### Post by zoso on 2004-12-04
I'd test this myself but I had to boot into XP for a moment. I'm guessing that hotplug is loading the atiixp module itself so if you at it to /etc/hotplug/blacklist then that will prevent the module from loading. Otherwise I'd have to poke around in /etc/modules to figure out what the deal is.

I'll test this in a few minutes, just as soon as my GF is finished printing some stuff out.

---

### Post by vdubgeek on 2004-12-04
[QUOTE=zoso]... I'm guessing that hotplug is loading the atiixp module itself so if you at it to /etc/hotplug/blacklist then that will prevent the module from loading. Otherwise I'd have to poke around in /etc/modules to figure out what the deal is.
...[/QUOTE]

I just tried adding it to the blacklist as you suggested, and it's still getting loaded.  Will need to keep digging.  Just out of curiousity, where is alsaconf?  I've got alsa-utils installed, but alsaconf appears to be missing.

---

### Post by zoso on 2004-12-04
I noticed that myself. I'm not sure what's going on there, when I do 'apt-cache search alsaconf' it returns alsa-utils.

When I do an rmmod atiixp all I get is 'module in use' so I'm stumped on that as well.

---

### Post by zoso on 2004-12-04
Ok, progress of a sort. Or at least an informative lack of progress.

atiixp is no longer loaded, but when I do /etc/init.d/alsa restart I get 'load_state:1134: No soundcards found...'

---

### Post by vdubgeek on 2004-12-04
[QUOTE=zoso]Ok, progress of a sort. Or at least an informative lack of progress.

atiixp is no longer loaded, but when I do /etc/init.d/alsa restart I get 'load_state:1134: No soundcards found...'[/QUOTE]

I'm getting the same error as well.  Very odd.  Thanks for helping troubleshoot this!

---

### Post by zoso on 2004-12-04
[QUOTE=vdubgeek]I'm getting the same error as well.  Very odd.  Thanks for helping troubleshoot this![/QUOTE]
 No problem. Just trying to get this one figured out. At this point I'm starting to think that this is an  ALSA problem more than anything else. 

I never was a huge GNOME fan so I'm going to install KDE and see how things go.

---

### Post by vdubgeek on 2004-12-04
[QUOTE=jdong]atiixp 9272 1

Both OSS and ALSA drivers are loaded. Try rmmodding the above module.[/QUOTE]

I pulled down the source for ALSA, and have been looking it over.  Are you saying atiixp is the OSS driver that should be removed?  Looking at the ALSA source, it looks like both snd_atiixp and atiixp are part of ALSA, with atiixp being an IDE driver?

---

### Post by vdubgeek on 2004-12-04
After some trial and error, I've managed to get audio working.  I ended up doing the following:

1.  Download ALSA 1.07 driver, build and installed.
2.  Download alsa utils 1.07 

After upgrading, I noticed that snd-atiixp-modem is now auto running.  I added that module to the blacklist file, and ran alsaconf and configured sound.  After doing this, sound is  running.

---

### Post by zoso on 2004-12-05
[QUOTE=vdubgeek]After some trial and error, I've managed to get audio working.  I ended up doing the following:

1.  Download ALSA 1.07 driver, build and installed.
2.  Download alsa utils 1.07 

After upgrading, I noticed that snd-atiixp-modem is now auto running.  I added that module to the blacklist file, and ran alsaconf and configured sound.  After doing this, sound is  running.[/QUOTE]
 I attempted to do the same, with no success. alsaconf appears to correctly configure the sound card but alsa fails to start with 'no sound cards found' error. Perhaps I'll attempt a clean install and then go through installing ALSA 1.07 once again.

---

### Post by zoso on 2004-12-05
[QUOTE=zoso]I attempted to do the same, with no success. alsaconf appears to correctly configure the sound card but alsa fails to start with 'no sound cards found' error. Perhaps I'll attempt a clean install and then go through installing ALSA 1.07 once again.[/QUOTE]
 Maybe I haven't had enough coffee, but this is kicking my butt. I downloaded the Alsa drivers 1.7 package and followed the installation instructions on the alsa-project.org website. When I do:

./configure --with-cards=atiixp --with-sequencer=yes

I get:

checking for which soundcards to compile driver for... configure: error: Unsupported soundcard atiixp

At this point I'm mystified.

---

### Post by vdubgeek on 2004-12-05
[QUOTE=zoso]I attempted to do the same, with no success. alsaconf appears to correctly configure the sound card but alsa fails to start with 'no sound cards found' error. Perhaps I'll attempt a clean install and then go through installing ALSA 1.07 once again.[/QUOTE]

Hmm, I'm trying to remember if there might have been anything else that I did that I left out.  I continued to get this error with alsaconf for a while as well.  Did you run the snddevices script to create the /dev files?

---

### Post by zoso on 2004-12-05
[QUOTE=vdubgeek]Hmm, I'm trying to remember if there might have been anything else that I did that I left out.  I continued to get this error with alsaconf for a while as well.  Did you run the snddevices script to create the /dev files?[/QUOTE]
 I did run the snddevices script and it made the proper files in /dev, but that was before I ran into the unsupported soundcard error. That was a result of following the instructions for installing the modules for the atiixp on the alsa website explicitly. I'm going to bash my head against this some more this evening to see if I can get anywhere.

---

### Post by zoso on 2004-12-06
I tried again last night without success. At this point I'm still confused as to why I'm having this problem. 

If you could post the steps you took to get this done I would really appreciate it.

---

### Post by vdubgeek on 2004-12-06
[QUOTE=zoso]I tried again last night without success. At this point I'm still confused as to why I'm having this problem. 

If you could post the steps you took to get this done I would really appreciate it.[/QUOTE]

Sure thing, sorry you haven't been able to get sound running.  I'll try to recreate the steps this evening after work.

---

### Post by vdubgeek on 2004-12-06
[QUOTE=zoso]I tried again last night without success. At this point I'm still confused as to why I'm having this problem. 

If you could post the steps you took to get this done I would really appreciate it.[/QUOTE]

Sure thing, sorry you haven't been able to get sound running.  I'll try to recreate the steps this evening after work.

---

### Post by vdubgeek on 2004-12-07
Well, I installed ubuntu into an empty partition, and reconfigured sound on the fresh install.   Worked again as before.  As before, I did the following:


1.  Downloaded ALSA 1.07 driver & ALSA Utils 1.07 .  Compiled and installed.  
2.  Added snd-atiixp-modem to blacklist file
3.  Restarted ubuntu
4.  ran alsaconf

At this point, I was able to play audio.   Hope this is of some help, if you have any questions let me know.

---

### Post by vdubgeek on 2004-12-08
[QUOTE=zoso]Maybe I haven't had enough coffee, but this is kicking my butt. I downloaded the Alsa drivers 1.7 package and followed the installation instructions on the alsa-project.org website. When I do:

./configure --with-cards=atiixp --with-sequencer=yes

I get:

checking for which soundcards to compile driver for... configure: error: Unsupported soundcard atiixp

At this point I'm mystified.[/QUOTE]

When I configured my build, I didn't use any switches, I just configured and compiled the default build.    Does your configure behave any differently without the switches?

---

### Post by snaga on 2004-12-10
Well, Tchaikovsky is coming from the speakers, so it must have worked for me too. Thank you.

Zoso, I hope you can get yours going as well. Let me know if I can help. 

Now if I could get the touchpad and wireless to work, I'll be pretty much totally up and running.

dm

---

### Post by zoso on 2004-12-10
[QUOTE=snaga]Well, Tchaikovsky is coming from the speakers, so it must have worked for me too. Thank you.

Zoso, I hope you can get yours going as well. Let me know if I can help. 

Now if I could get the touchpad and wireless to work, I'll be pretty much totally up and running.

dm[/QUOTE]
 I never did get sound to work, but the built-in wireless worked without a problem. Hotplug detected it and loaded the proper module, and then I just had to configure it using the Network manager in GNOME. 

I'm still running Ubuntu on my desktop but I had to turn to Kanotix in order to get the laptop up and running. With Kanotix everything just works on the laptop.

---

### Post by maxpower on 2004-12-14
[QUOTE=vdubgeek]Well, I installed ubuntu into an empty partition, and reconfigured sound on the fresh install.   Worked again as before.  As before, I did the following:


1.  Downloaded ALSA 1.07 driver & ALSA Utils 1.07 .  Compiled and installed.  
2.  Added snd-atiixp-modem to blacklist file
3.  Restarted ubuntu
4.  ran alsaconf

At this point, I was able to play audio.   Hope this is of some help, if you have any questions let me know.[/QUOTE]

When I first install Ubuntu I get sound on the GDM screen but the sound repeats and I have to kill aplay for it to stop.  After login ESD does the same thing but locks up the login process. So I kill ESD and turn it off.  When I try to play music using totem, no sound is emitted and totem locks up.  If I use XMMS with ALSA, the music plays fine but when I close XMMS it locks up and has to be forcefully killed.  If I use OSS with XMMS everything works fine.  This suggests to me that sound works with linux but not for totem, rythymbox, or xine as they all lock up.  I tried installing ALSA 1.07 but nothing changed. I also tried upgrading my Warty install to use Hoary's 2.6.9 kernel since I read somewhere that it includes bug fixes specfifc to the IXP but this did not work either.  Any suggestions?

mAx

---

### Post by maxpower on 2004-12-15
To answer my own question:
   I tried adding "noapic" to my kernel options and then I actually got sound!  Having done too many things to my install, I did a fresh install with both noapic and pci=noacpi added.  After install alsa cound not detect a sound card. So I removed noapic and I got the same lockups as before.  So I once again upgraded to the 2.6.9 hoary kernel, re-added noapic, and sound worked flawlessly.

mAx

---

### Post by duboz on 2004-12-20
[QUOTE=vdubgeek]I'm getting the same error as well.  Very odd.  Thanks for helping troubleshoot this![/QUOTE]

I am getting the same error too... it is very enoying... somebody from Unbuntu team to help us. Is somebody  can cotact developpers team ?

---

### Post by telmo on 2004-12-31
I'm going nuts!!!
How do i install Alsa Drivers 1.07?
It says:

[B]checking for gcc... no
checking for cc... no
checking for cc... no
checking for cl... no
configure: error: no acceptable C compiler found in $PATH[/B]

What do i do??? I'm not to keen on linux... 
 :oops:

---

### Post by telmo on 2005-01-08
Solved it...  (installed the driver...)
...but no sound!

---

### Post by dreamminder on 2005-03-03
Ok boys is really simple to add the sound to the Toshiba A75 just do the following

1.- in /etc/hotplug/blacklist add the modules snd-atiixp and snd-atiixp-modem
2.- in /etc/modules at the end add the line snd-atiixp

Thats it u'll have sound working including after reboots and the alsa config will be restore, well at least it worked for me.

By baby boys gl hf.

---

### Post by snaga on 2005-03-07
I am having a lingering problem with sound on my A75. This thread, as noted above, has been very useful in getting sound working.

The weird thing is that sound works on about 50% of my boot-ups. It worked fine yesterday, but this morning when I start up, I have no sound, and the volume control says 

> No mixer elements and/or devices found

If I restart, chances are good that it will find the device and all will be well.

Is this happening to anyone else?

dm

---

### Post by snaga on 2005-03-07
[QUOTE=dreamminder]Ok boys is really simple to add the sound to the Toshiba A75 [/QUOTE]

Are you using Warty or Hoary? If you are using Hoary, then maybe the problem has been fixed.

dm

---

### Post by moeser on 2005-03-23
Got it working on Toshiba A65.  All I had to do was install hoary's new kernel and modules, then reboot.  Sound worked fine after that, no goofing around with blacklists or module files required.
Unfortunately it also seems to install an "upgraded" touchpad driver that irritatingly hits "back" for me in firefox.  I guess it could have been like that before and I just never ran into that little glitch, but it seems new.

---

