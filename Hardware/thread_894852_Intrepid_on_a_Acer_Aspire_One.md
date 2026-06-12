---
title: "Intrepid on a Acer Aspire One"
date: 2008-08-19
forum: Hardware
---

### Post by jbernardo on 2008-08-19
Anyone else trying intrepid on a Acer Aspire One? I found that the [instructions for Hardy]("https://help.ubuntu.com/community/AspireOne") are no longer fully applicable under intrepid. I installed on a external USB HD, and it boots into kde4, but wifi won't work at all. With the madwifi drivers I can scan the neighbourhood, but network manager won't scan and won't connect to my wpa 802.11g network. The sound doesn't seem work and I haven't tried building the alsa drivers from source yet.
The "setpci -d 197b:2381 AE=47" line to enable the card reader doesn't work at all - there is no pci device with the specified id under intrepid.
Anyone else trying Intrepid on the one?

---

### Post by jbernardo on 2008-08-20
Well, since nobody else replies, here are my first tests, which I already posted[ here]("http://www.aspireoneuser.com/forum/viewtopic.php?f=28&t=1615"):
Sound - no chance until alsa is updated, 1.0.16 won't build under kernel 2.6.26. 1.0.17 is out, so maybe the ubuntu developers will update it soon.
Wireless - also no luck. Installing the madwifi drivers seems to work, and I can scan the network, but NetworkManager won't connect, with a strange error:


    NetworkManager: <WARN>  wait_for_connection_expired(): Connection (2) /org/freedesktop/NetworkManagerSettings/Connection/0 failed to activate (timeout): (0) Connection was not provided by any settings service

.
Also, there is no longer a pci device with ID 197b:2381, so the card reader doesn' t work at all.

---

### Post by dugald on 2008-08-22
Any idea on whether the newer ALSA and madwifi versions required to get audio and wireless working correctly will be incuded in Ibex?  I am setting up an Aspire One for my boss, and was considering holding off handing it over until Ibex comes out and things work a little better - perhaps this is wishful thinking (or an excuse to hang onto it for longer!). :D

---

### Post by aamukahvi on 2008-08-22
Have you tried these: [http://kernel.ubuntu.com/pub/next/](http://kernel.ubuntu.com/pub/next/)

---

### Post by plun on 2008-08-22
> **aamukahvi said:**
> Have you tried these: [http://kernel.ubuntu.com/pub/next/](http://kernel.ubuntu.com/pub/next/)

I think its important to read what Mr Collins writes about Kernel Next.

[http://blog.phunnypharm.org/2008/08/ubuntu-kernel-next.html](http://blog.phunnypharm.org/2008/08/ubuntu-kernel-next.html)

Hopefully there will be a "switch" to the 2.6.27 kernel.

---

### Post by Jitz0722 on 2008-09-26
I have installed, or upgraded to Intrepid Ibex Alpha 6 today on my acer aspire one. 1.6GHz 120GB harddrive. It appears networking and wireless are working. Need to try lgging onto a network later, but I can see the networks close to me.

The one thing I have not been able to do is get the wireless leds to work.

from dmesg I get the keycodes, 
[  165.270732] atkbd.c: Unknown key pressed (translated set 2, code 0xd5 on isa0060/serio0).
[  165.270754] atkbd.c: Use 'setkeycodes e055 <keycode>' to make it known.
[  165.277335] atkbd.c: Unknown key released (translated set 2, code 0xd5 on isa0060/serio0).
[  165.277354] atkbd.c: Use 'setkeycodes e055 <keycode>' to make it known.
[  171.148784] ath0: no IPv6 routers present
[ 1832.044041] atkbd.c: Unknown key pressed (translated set 2, code 0xd6 on isa0060/serio0).
[ 1832.044059] atkbd.c: Use 'setkeycodes e056 <keycode>' to make it known.
[ 1832.050631] atkbd.c: Unknown key released (translated set 2, code 0xd6 on isa0060/serio0).
[ 1832.050647] atkbd.c: Use 'setkeycodes e056 <keycode>' to make it known. 

I have added the following to rc.local and rebooted and still no luck.
( These are supposed to make them work on hardy 8.04 ). Note also using remix GUI

sysctl -w dev.wifi0.ledpin=3
sysctl -w dev.wifi0.softled=1

The wifi kill switch uses these keycodes (also to use in rc.local):

/usr/bin/setkeycodes e055 159
/usr/bin/setkeycodes e056 158

---

### Post by jbernardo on 2008-09-27
The wifi led only works with the madwifi drivers (ath_pci), not with the kernel included driver (ath5k).

---

### Post by Jitz0722 on 2008-09-29
So I verified I am using the latest Kernel: 2.6.27-4-generic
(previoulsy I had 2.6.24 loading )

I built and loaded the ath_pci as below

mkdir source
cd source
wget [http://snapshots.madwifi.org/madwifi-hal-0.10.5.6/madwifi-hal-0.10.5.6-r3835-20080801.tar.gz](http://snapshots.madwifi.org/madwifi-hal-0.10.5.6/madwifi-hal-0.10.5.6-r3835-20080801.tar.gz)
tar -xzvf madwifi-hal-0.10.5.6-r3835-20080801.tar.gz
cd madwifi-hal-0.10.5.6-r3835-20080801
sudo apt-get install build-essential linux-headers-$(uname -r)

make, make install.

The wireless comes up and works, but the leds on the unit still do not work.

I modified rc.local as per instructions above, wireless appears to trun on and off, but no led.

Regards

---

### Post by condez on 2008-10-03
I have installed Ubuntu Server Beta 1 on the Acer One.

I have followed the instructions on "https://help.ubuntu.com/community/AspireOne" regarding the wireless drivers.

Since i'm running the server i can simply go to "Hardware Drivers" to disable ath driver, because i have no graphic environment.

I followed step by step the procedure to compile drivers from source but thw wireless card still doesn't work.
Also, it seams the kernel drivers try to create a "wlan0" device, however i can't bring it up.
Tried to remove restricted modules from the system but still no luck.

This means, i can't use the wireless card in Ubuntu.

Does anyone have any clues?

---

### Post by Drano on 2008-10-03
Hi folks!

Just managed to get the aspire one wireless to work with ibex drivers. I have done the following:
1-installed ibex alpha6
2-got all updates
3-installed madwifi-tools
4-add the following to /etc/modprobe.d/blacklist.
blacklist ath_pci
5-add the following to /etc/rc.local.
modprobe ath5k

reboot and you will the wlan0 interface...

---

### Post by sigmabetatooth on 2008-10-04
Sweet success!  I was having trouble with the madwifi install on my compaq c700 (which was working fine before ibex).  Your directions were prefect.  Many thanx!

---

### Post by Drano on 2008-10-04
I just wanna share one more tweak that i have done to my aspire one. Adding "elevator=deadline loglevel=1 console=tty1 nolapic_timer" to the kernel line in /boot/grub/menu.lst made my system a lot more responsiveness.
I got these options from the menu.lst that cames with Linpus.

---

### Post by gcday on 2008-10-06
Hi - can someone talk me through install those "mad wifi" drivers I have an acer one and currently no wifi (having just installed 8.10).

---

### Post by aimpau on 2008-10-06
Go back to page one and read Drano's post.

Please don't tease me with your Acer Aspires...I want one so badly too...:(

---

### Post by gcday on 2008-10-06
I am stuck at the first stage - where do I get the software from?

---

### Post by aimpau on 2008-10-06
> **Drano said:**
> Hi folks!

Just managed to get the aspire one wireless to work with ibex drivers. I have done the following:
1-installed ibex alpha6
2-got all updates
3-installed madwifi-tools
4-add the following to /etc/modprobe.d/blacklist.
blacklist ath_pci
5-add the following to /etc/rc.local.
modprobe ath5k

reboot and you will the wlan0 interface...

#1 You said you've **just** installed 8.10 so I'm assuming it is already in the last stage of alpha (ibex alpha6).

#2 Go to Applications>>System>>Updates (I'm on xubuntu so try to adjust to your ubuntu)

#3 Open a terminal and:
```

sudo apt-get install madwifi-tools

```

#4 On the same terminal after the install
```

sudo gedit /etc/modprobe.d/blacklist

```

On the last line, add
```

blacklist ath_pci

```
and press save

#5 Terminal
```

sudo gedit /etc/rc.local

```
And add to the last line
```

modprobe ath5k

```


If anything is wrong here, please feel free to correct me.

---

### Post by Drano on 2008-10-06
Thanks aimpau! That's exactly what i've done, and you are right, i was using the alpha6.

---

### Post by gcday on 2008-10-06
tried it and nothing happened?

---

### Post by aimpau on 2008-10-07
Are you using ibex alpha 6? Update first.

---

### Post by gcday on 2008-10-07
> **aimpau said:**
> Are you using ibex alpha 6? Update first.


Thanks for your help with this - how would I check what I am running? I did the download and install yesterday so assumed I was running the most update.

---

### Post by aimpau on 2008-10-07
Go to applications>>System>>>system monitor

Check out the system tab. If you already have ibex alpha6. just follow the instructions above.

**Now:**

If by chance you already have the beta release, try to follow the instructions above as well. If everything goes fine, post back here. :)

---

### Post by gcday on 2008-10-08
> **aimpau said:**
> Go to applications>>System>>>system monitor

Check out the system tab. If you already have ibex alpha6. just follow the instructions above.

**Now:**

If by chance you already have the beta release, try to follow the instructions above as well. If everything goes fine, post back here. :)

It looks like I have the beta release:

> Release 8.10 (intrepid)
Kernel linux 2.6.27-5-generic
Gnome 2.24.0

I followed the instructions and nothing seems to happened.

---

### Post by craggsy on 2008-10-08
Well I have the beta running and its all fine, apart from two things. Sound doesn't work on youtube, though that may just be a firefox issue. Secondly when I try to run Open arena it just goes back to desktop all i can do is log out, However when I log back in it loads up, game runs fine. 

Going to try and get the 8.0.0 version see if that helps, other than that everything runs fine.

---

### Post by Davsdu on 2008-10-09
craggsy, did you make a fresh install or an upgrade from 8.4? Also, do video, sound (beside your Youtube experince without sound) and wifi ´just work´ without any tweaking at all? Too good to be true, but I wanna believe. :)

---

### Post by craggsy on 2008-10-09
> **Davsdu said:**
> craggsy, did you make a fresh install or an upgrade from 8.4? Also, do video, sound (beside your Youtube experince without sound) and wifi ´just work´ without any tweaking at all? Too good to be true, but I wanna believe. :)


Hey

I screwed up mu 8.04 install so i reinstalled that, then using my ethernet I ran the upgrade took about an hour I guess in total. Everything works, the wifi started up perfectly though it wasn't too happy about WEP for some reason but it runs using WPA-2. I haven't tweaked the wifi at all, it ran as soon as i rebooted after the upgrade. I fixed the Firefox sound issues ([[COLOR="Blue"]flash audio fix[/COLOR]]("http://www.derekhildreth.com/blog/how-to-fix-the-no-sound-issue-in-firefox-flash/")), I had a problem with Open Arena crashing though I fixed that by following [[COLOR="Blue"]THIS[/COLOR]]("http://ubuntuforums.org/showthread.php?t=866965"). 

The boot time is 44 seconds compared to 36/38 on  8.04 though when everything works straight up its easier. 

Two "issues" are 
- Card reader doesn't work, the fixes for 8.04 don't work
- Screen resolutions now are only 640 and 1024, which is lame for open arena, though Warsow can display other resolutions than the two listed. 

So yea the only tweaks are to run the pulse audio fix that takes about 2 mins max, and install the flashaudio thing for youtube, thats it. Everything else works out of the box.

---

### Post by Davsdu on 2008-10-09
Wow! Sounds amazingly good--can´t wait to get my hands on my own Aspire One.

Thanks for the heads up!

---

### Post by arfalconi on 2008-10-09
I had installed Hardy on my Aspire One (1Gb ram, 120 GB HD), i had some issues with the soundcard, it worked, but not very well, i tried all the options from the [https://help.ubuntu.com/community/AspireOne:](https://help.ubuntu.com/community/AspireOne:)

/etc/modprobe.d/alsa-base:options snd-hda-intel model=toshiba, acer, auto

I discover that when the wireless card module (ath_pci) was loaded, the sound card did not work (snd-hda-intel)

I recompiled the latest alsa modules with the AlsaUpgrade script and the madwifi ones, not success with the sound problem, if ath_pci module was loaded there was a sound problem, but if removed the modules from the kernel and i loaded both again the sound problem fixed.

so i decided to update to Intrepid, before the update i commented all the options i added from the above page, rc.local, modules, etc...  After the update everything was working ok, i did not have to compile anything for the wireless card to work, the sound worked perfect, etc. So, after that, i was adding the options i had before, one by one...

The options:
# As in the rc.last.ctrl of Linpus
#echo ondemand > /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor
#echo ondemand > /sys/devices/system/cpu/cpu1/cpufreq/scaling_governor
#cat /sys/devices/system/cpu/cpu0/cpufreq/ondemand/sampling_rate_max > /sys/devices/system/cpu/cpu0/cpufreq/ondemand/sampling_rate

Cause the automatic scaling not to work, so i commented it.

The option:
#echo 10 > /sys/module/snd_hda_intel/parameters/power_save

Cause the sound card not to work very well, cutted sound, for example, the login Gnome sound (maybe that option was causing problems on Hardy).

The wireless works ok but the wireless card led does not work.

The new kernel uses the ath5k module for the atheros card on the Aspire One, so the options:
sysctl -w dev.wifi0.ledpin=3
sysctl -w dev.wifi0.softled=1

will not work since there are not such variables on the sysctl system, and of course the wireless card is now wlan0:

the sysctl -A command show all the sysctl available variables, there is not anyone for turnon the led when using the ath5k module.

So far, the system is working ok with Intrepid, i have some issues related to the 3D performance, INTEL_BATH=1 enviroment variable does not seem to make any diference, and the other xorg.conf options ( Option "AccelMethod" "EXA", etc.) that should make better 3D performance did not work too.

I got a poor 340.827 FPS, when i had +- 800.000 whit Hardy.

I hope the xorg Intel driver gets updated on new kernel updates.

Excuseme for my bad english.

-Ariel
México

---

### Post by khaeru on 2008-10-13
Ariel, thanks for your reply.

I've been trying to reconcile [https://help.ubuntu.com/community/AspireOne](https://help.ubuntu.com/community/AspireOne) with what works under Intrepid, and you've confirmed a few things for me (frequency scaling, wireless LEDs)

I am going to try to clean up that wiki page once I get through a few more issues. Can you please clarify about the sound:

 * Do you still have "snd-hda-intel" in /etc/modules, or does it load automatically?
 * Do you have "options snd-hda-intel model=toshiba" or similar in /etc/modprobe.d/alsa-base or any other file?

Another thing is that usplash doesn't seem to be working under Intrepid...have you also experienced this?

---

### Post by bobnutfield on 2008-10-14
I am getting an Acer Aspire One on the 22nd, the 120gb HD version.  I had intended to install Intrepid straight away, since so much more of my Toshiba laptop worked right away with Intrepid.  But after reading several of these posts and the Community guide, looks like I need to rethink this.  It doesn't look like it is going to be easy to install over the default Linpus.

---

### Post by craggsy on 2008-10-14
Well it does install over linpus, and after yesterdays update everything now works, minus the wifi led's though I don't really care about them.

---

### Post by bobnutfield on 2008-10-14
> **craggsy said:**
> Well it does install over linpus, and after yesterdays update everything now works, minus the wifi led's though I don't really care about them.

Well, that gives me hope.  But I am not sure I want to spend the hours it looks like will be necessary to get all the hardware working.  I will only be using it for mobile internet and email away from home. I would much prefer to have Intrepid than Linpus.  Linpus is based on Fedora 8 as I understand it and I could not even get to a normal desktop when I demo'd it.  I will be wanting to do more than the default Linpus will allow me to do.

---

### Post by KenHagan on 2008-10-14
> Well, that gives me hope. But I am not sure I want to spend the hours it looks like will be necessary to get all the hardware working.

I grabbed the ISO last Thursday and installed it on Friday evening and spent Saturday morning going through the instructions posted hereabouts. My experience was that nearly everything does work out of the box. Today I lost my wireless for no obvious reason. (There's been a fairly steady stream of updates for Intrepid, unsurprisingly, so I have been moving the goalposts I suppose.) However, as I write this the problem has gone away again. I don't really know what did it, but I currently have ath_pci blacklisted and ath5k enabled and I've done a few power on/off restarts as opposed to simply choosing "restart".

I got the machine several weeks ago and stuck with Linpus for a while, but was increasingly frustrated by (a) the fact that the system seems to be tied to out-of-date versions of several libraries, causing me grief when I tried to install things like Amarok or Rhythmbox, and (b) there's almost no community support for Linpus at all. (I think there's one or two guys blogging about it somewhere. I couldn't find anything useful on the Acer or Linpus sites.) There's a strong argument for going with an out-of-the-box configuration of a mainstream distro.

---

### Post by bobnutfield on 2008-10-14
> **KenHagan said:**
> I grabbed the ISO last Thursday and installed it on Friday evening and spent Saturday morning going through the instructions posted hereabouts. My experience was that nearly everything does work out of the box. Today I lost my wireless for no obvious reason. (There's been a fairly steady stream of updates for Intrepid, unsurprisingly, so I have been moving the goalposts I suppose.) However, as I write this the problem has gone away again. I don't really know what did it, but I currently have ath_pci blacklisted and ath5k enabled and I've done a few power on/off restarts as opposed to simply choosing "restart".

I got the machine several weeks ago and stuck with Linpus for a while, but was increasingly frustrated by (a) the fact that the system seems to be tied to out-of-date versions of several libraries, causing me grief when I tried to install things like Amarok or Rhythmbox, and (b) there's almost no community support for Linpus at all. (I think there's one or two guys blogging about it somewhere. I couldn't find anything useful on the Acer or Linpus sites.) There's a strong argument for going with an out-of-the-box configuration of a mainstream distro.

Yes, thank you.  Linpus is based on Fedora 8 which will no longer be supported at all in December.  This Acer Aspire is going to be a gift, so I had always intended to install Intrepid anyway, it was just reading all the confi necessary was a little depressing, but if I have to I have to.  Can't be any worse than getting my volume wheel on the front of my laptop working in Slackware which I recently did.

---

### Post by Jitz0722 on 2008-10-14
@khaeru

The /etc/modules is mostly blank
two entries:
fuse
lp

The /etc/modprobe.d/alsa-base

# autoloader aliases
install sound-slot-0 /sbin/modprobe snd-card-0
install sound-slot-1 /sbin/modprobe snd-card-1
install sound-slot-2 /sbin/modprobe snd-card-2
install sound-slot-3 /sbin/modprobe snd-card-3
install sound-slot-4 /sbin/modprobe snd-card-4
install sound-slot-5 /sbin/modprobe snd-card-5
install sound-slot-6 /sbin/modprobe snd-card-6
install sound-slot-7 /sbin/modprobe snd-card-7

# Cause optional modules to be loaded above generic modules
install snd /sbin/modprobe --ignore-install snd && { /sbin/modprobe --quiet snd-ioctl32 ; : ; }
install snd /sbin/modprobe --ignore-install snd && { /sbin/modprobe -Qb snd-seq ; }
install snd-pcm /sbin/modprobe --ignore-install snd-pcm && { /sbin/modprobe --quiet snd-pcm-oss ; : ; }
install snd-mixer /sbin/modprobe --ignore-install snd-mixer && { /sbin/modprobe --quiet snd-mixer-oss ; : ; }
install snd-seq /sbin/modprobe --ignore-install snd-seq && { /sbin/modprobe --quiet snd-seq-midi ; /sbin/modprobe --quiet snd-seq-oss ; : ; }
install snd-rawmidi /sbin/modprobe --ignore-install snd-rawmidi && { /sbin/modprobe --quiet snd-seq-midi ; : ; }
# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-emu10k1-synth ; }
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-seq ; }

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe -Qb saa7134-alsa ; : ; }

# Load snd-seq for devices that don't have hardware midi;
#   Ubuntu #26283, #43682, #56005; works around Ubuntu #34831 for
#   non-Creative Labs PCI hardware
install snd /sbin/modprobe --ignore-install snd && { /sbin/modprobe -Qb snd-seq ; }
# Prevent abnormal drivers from grabbing index 0
options bt87x index=-2
options cx88_alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-usx2y index=-2
options snd-usb-caiaq index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
# Keep snd-pcsp from beeing loaded as first soundcard
options snd-pcsp index=-2

Overall, the machine is working better each day after doing updates.
Very usable and functional today ( I followed the netbook remix insstall for Intrepid ) 

[https://help.ubuntu.com/community/AspireOne](https://help.ubuntu.com/community/AspireOne)

regards

---

### Post by craggsy on 2008-10-14
One bug I had (no idea if it still happens), is if you restart the wifi doesn't load. But if you shut-down then power on its fine.

---

### Post by arfalconi on 2008-10-14
Hello khaeru,

No, i do not have "snd-hda-intel" in /etc/modules, it is loaded automatically.

# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

fuse
#lp

---------------------------------------------------------------------

I have not compiled the atheros madwifi, the wireless is working well with the ath5k module that is loaded automatically.

I commented and later deleted the options i previously added related to the sound card on /etc/modprobe.d/alsa-base before the hardy to intrepid upgrade:

there is not any of the following options:

options snd-hda-intel model=toshiba
options snd-hda-intel model=auto
options snd-hda-intel model=acer

- The /etc/modprobe.d/alsa-base i have now, is the default one that the upgrade installed.

I noticed the usplash problem, it had like two progress lines mixed or something like that, i do not remember very well, but what i remember is that after i saw that problem, i did a:

sudo update-initramfs -u

I am not sure if it fixed the problem

In resume, before the hardy to intrepid update, i deleted (or commented) all the previously added options on:

/etc/modules
/etc/modprobe.d/alsa-base

I did not commented the following options on /etc/rc.local

#Acer Aspire One fan control
/usr/local/bin/acerfand

echo 1500 > /proc/sys/vm/dirty_writeback_centisecs
echo 20 > /proc/sys/vm/dirty_ratio
echo 10 > /proc/sys/vm/dirty_background_ratio

echo 1 > /sys/devices/system/cpu/sched_smt_power_savings
echo 5 > /proc/sys/vm/laptop_mode

#Decrease power usage of USB while idle
[ -L /sys/bus/usb/devices/1-5/power/level ] && echo auto > /sys/bus/usb/devices/1-5/power/level
[ -L /sys/bus/usb/devices/5-5/power/level ] && echo auto > /sys/bus/usb/devices/5-5/power/level


If someone still using hardy and have sound problems, please try commenting (if you have it) the line:
#echo 10 > /sys/module/snd_hda_intel/parameters/power_save

on /etc/rc.local


The 3D performance problem stills there, i think i will be fixed on the next xorg-intel driver update.

Hasta pronto !!!

-Ariel

---

### Post by thor2002ro on 2008-10-15
hi there i got thease days a acer aspire one and put intrepid on it works great but i was looking for that fabulos messenger aplication that came with linpus cant even tell what program they used in about it just says 
```
Messenger 1.01.3015
G.722.1, licensed from Polycom(R)
Acer Communication Suite Development Team
```

and i was looking at limpus related sites and found this FTP [http://ftp.twaren.net/Linux/Linpus/Aspire_One_Linpus_Linux/]("http://ftp.twaren.net/Linux/Linpus/Aspire_One_Linpus_Linux/")

it seems to have acer aspire one related sources and in Aspire_One_Source directory there is "ACS_open_src_final.tar.gz" is it just me or it sounds like Acer Communication Suite(ACS) inside there semms to be various sources and then i saw Pidgin .... i'm thinking they modified pidgin for audio and video ... maybe :) other then this there are some manager source , firefox source , kernel source , and mplayerplugin , maybe now we can make a better compatibility for ubuntu hope someone with programer skills can look at thease , i know some c++ programing but im not there yet so please someone take a look :)

---

### Post by gcday on 2008-10-15
Odd how I cannot get my wifi to work..... :confused:

---

### Post by KenHagan on 2008-10-23
> **gcday said:**
> Odd how I cannot get my wifi to work..... :confused:

Still no joy? I haven't had any further wifi trouble since some fixes for the guidance power management software came down the pipe earlier this week (20th?). (I mention this not to gloat but in case people are finding this thread on google and wondering how things ended up. It would be all too easy to conclude that lots of us had trouble with the AA1 and nothing was ever resolved!)

Looking back over this thread, the only thing that caught my eye was the suggestion that the last line of /etc/rc.local should be "modprobe ath5k". That should be the second last line, of course, since the last line is "exit 0", but I don't suppose it can be that simple. :)

---

### Post by bobnutfield on 2008-10-23
Well, I have my AAO now, and working with the Linpus that it came with looked like it was going to be real crap.  And, actually it isn't that bad once I learned a couple of hacks to switch between the actual XFCE desktop and the default Linpus desktop.  It has a 2.6.23 kernel, which is about 7 months ago and, of course, it is based on Fedora 8, but I have found that once the full XFCE menus are unlocked, it is pretty usable.  As it is, all of the hardware is working, and, while I would prefer to have Intrepid, I am hesitant to install it now as most people still do not ALL of the hardware and functions working with Intrepeid. I will keep watching this thread to see if there are any further developments.

---

### Post by pjalegria on 2008-10-23
Yes, its ACER MESSENGER but but is tar.gz file, how can i install on Ubuntu?
Linpus messenger on Ubuntu, that ill be great...

---

### Post by arfalconi on 2008-10-23
I am not sure if i am the only one that had this problem, any way, i will share it:

The brightness Up key of my Aspire One was not working, i mean, i did up the brightness level but the image that usually appears on gnome, indicating that the brightness is increasing on gnome was not present.

What i did to fix this was to add the line:

```
setkeycodes e04e $KEY_BRIGHTNESSUP    # Acer Aspire One Brightness Up
```

to the file:

```
/usr/share/hotkey-setup/acer.hk
```

My acer.hk file looks now:

```
# Acer Laptops
setkeycodes     e025    $KEY_HELP       # Help key
setkeycodes     e074    $KEY_PROG1      # Misc 1
setkeycodes     e073    $KEY_PROG2      # Misc 2
setkeycodes     e04e    $KEY_BRIGHTNESSUP       # Acer Aspire One Brightness Up key
#setkeycodes    e057    $KEY_           # Blue          Bluetooth On (hardware, led, informational only)
#setkeycodes    e058    $KEY_           # Blue          Bluetooth Off (hardware, led, informational only)
#Also: PreviousTrack, NextTrack, Play, Stop, WWW, Email, VolumeUp, VolumeDown, Mute, BrightnessDown...

```

Or you could add:

```
setkeycodes     e04e    225
```

to the:

```
/etc/rc.local

```
file


-Ariel

---

### Post by KenHagan on 2008-10-25
Ugh. I think I've just been bitten by Bug #288148, or rather by its "resolution". It seems that the ath5k module has been withdrawn from the kernel entirely, so my wifi stopped working altogether. I grabbed linux-backports-modules-intrepid using apt-get and this has restored a module of that name, but I find it *very* hard to believe it is the same piece of software because I can't see my router despite being about 5 feet away from it.

I'm not complaining, since this is what beta testing is for, but I'm on a wired link to the outside world until I find a working wireless setup. Any other AA1 users with this problem today? Any suggestions?

---

### Post by arfalconi on 2008-10-25
As it was a duplicate post, i am editing it...


How many fps do you get in Intrepid?

Here: 

346.472 fps

-Ariel

---

### Post by arfalconi on 2008-10-25
Yes, i have noticed that, i had the same issue after yesterday updates  :(

Check this post:

[*[COLOR="Blue"]_Todays update killed my AR242x wireless card_[/COLOR]*]("http://ubuntuforums.org/showthread.php?t=957697")


-Ariel

---

### Post by khaeru on 2008-10-27
@KenHagan: I also stumbled on the solution you found (installing linux-backports-modules-intrepid).

One thing I note is that jockey (System > Administration > Hardware Drivers) now shows *two* wireless-related entries:
[list]
[*]Support for 5xxxx series of Atheros 802.11 wireless LAN cards.
[*]Support for Atheros 802.11 wireless LAN cards.
[/list]
...only the first one is activated in my case.

Can you check (this way, or via "lsmod | grep ath" in a terminal) which driver you're running? Depending on the order of installation, you may still be running the ath_pci driver that became the default (again) when ath5k was disabled.

---

### Post by Oni-san on 2008-10-27
I just updated my aspire one from ubuntu 8.04 where everything worked fine to ubuntu 8.10.

And I'm now also unable to use my wireless card.

The ath5k driver loads but it does not find any network (there are at least 10 reachable).

I quickly tried to compile ath_pci from svn and a solution with ndiswrapper but none worked. I probably did it wrong... I will retry but the best would be an out of the box support (in fact that's what I expected when I did this upgrade).

---

### Post by KenHagan on 2008-10-27
> **khaeru said:**
> Can you check (this way, or via "lsmod | grep ath" in a terminal) which driver you're running? Depending on the order of installation, you may still be running the ath_pci driver that became the default (again) when ath5k was disabled.

I checked, and it is the ath5k driver. Good idea, though, and thanks for the suggestion.

However ... the goalposts have moved. I take the view that if I'm going to run the beta I ought to pull the updates each day to minimise the chances that I'm complaining about a problem that has been fixed. This evening I dragged down some english translations and a few patches for SCIM (and possibly others that I've forgotten, but certainly nothing related to the kernel or to backports or to networking in general) and "as if by magic" my wireless is working again.

So I'm *absolutely* none the wiser, but it all works. Sigh!

---

### Post by inportb on 2008-10-27
Well, that's good in a way... I no longer have to blacklist ath5k to use madwifi; I feel queasy disabling a perfectly fine driver just so I could aircrack =p

---

### Post by arfalconi on 2008-10-28
Hello all,

i checked the video performance (fps) om my Aspire One with Intrepid and Hardy, and as i commented before, there is a performance issue in Intrepid, i get +- 346.472 FPS (Intrepid), vs +- 800.000 (Hardy), using all the recommendations for increase the video performance.

It seems that the xserver-xorg-video-intel does not has implemented the INTEL_BATCH option, so adding it to the /etc/profile is useless (i think)

Here more info:
[[COLOR="Blue"]https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/284082[/COLOR]]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/284082")

-Ariel

---

### Post by bobnutfield on 2008-10-30
> **KenHagan said:**
> I checked, and it is the ath5k driver. Good idea, though, and thanks for the suggestion.

However ... the goalposts have moved. I take the view that if I'm going to run the beta I ought to pull the updates each day to minimise the chances that I'm complaining about a problem that has been fixed. This evening I dragged down some english translations and a few patches for SCIM (and possibly others that I've forgotten, but certainly nothing related to the kernel or to backports or to networking in general) and "as if by magic" my wireless is working again.

So I'm *absolutely* none the wiser, but it all works. Sigh!

I quote this post because it seems to relate to my observation, rightly or wrongly.  I have waited to download an .iso for Intrepid to try it on my AAO until at or near release time.  So, last night at about midnight I downloaded the .iso (hours before the official release), created a live USB disk, and loaded it up to see how it would work out of the box as a live setup.

The whole system seems to work fine: sound, eth0, etc.  Graphics seem fine.  But the wireless does not work at all.  It isn't even recognized.  

Now, the reason I waited was because of all the posts in this thread about the ath5k module which supposedly would enable the wireless automatically.  Well, it does not seem to be present (does not show up in lsmod), but the Hardware Drivers shows a driver for the Atheros chipset which is enabled but not in use.  However, it does not offer a means of enabling it, only a choice to disable it.  Of course, I am using a live demo with the USB, so rmmod ath_pci and ath_hal and modprobe ath5k has no affect.  I made this bootably USB stick from my Intrepid install on my main laptop and I believe I can save my settings on shutdown, so I will try it again, saving the settings and rebooting.

The reason for my post is that it looks like even the final release of Intrepid is not going to work out of the box on the AAO for wireless without some reasonable reconfiguring of the wireless modules.  My AAO is the 120GB HD version with 1GB memory.  I am still hesitant to wipe the drive in favor of Intrepid (though obviously it is preferred to Linpus, which renders the machine to little than a PDA.)

Just a comment to those with a similar AAO considering an Intrepid install.

---

### Post by jbernardo on 2008-10-30
The ath5k was apparently pulled just before the final release. The solution is to use the madwifi drivers, which (at least for me) are a lot more stable and faster.

---

### Post by bobnutfield on 2008-10-30
> **jbernardo said:**
> The ath5k was apparently pulled just before the final release. The solution is to use the madwifi drivers, which (at least for me) are a lot more stable and faster.  

It may be better to use madwifi, but the ath5k module is in fact there, just doesn't work.  I enabled and disabled the driver listed in Hardware Drivers (which I assume is the ath_pci), but nothing.  Dissapointing, really.  Looks like I am going to have to continue to use Linpus for a while until I can figure this out because I really need wireless.  I might investigate a dual boot setup.

---

### Post by Crazy Jesus on 2008-10-30
I'm currently running Intrepid RC1 from my usb drive. Neither ALSA or the wifi card works. Alsa worked fine in Hardy, and the wifi card was perfect after installing the madwifi driver. 

I think I'll stick with hardy for now, I'm pretty disappointed less works in intrepid than hardy. Hopefully the official release will fix some things.

---

### Post by bobnutfield on 2008-10-30
Well, after some tweaking with a wired connection, I downloaded madwifi tools, and was finally able to get the wireless to work from the live session on the USB.  I am sure it would not be too difficult to get it going if I installed.  But, it is much slower to boot than the Linpus that is installed, and performs a little slower.  I will probably keep Linpus a little while longer.

---

### Post by gcday on 2008-10-30
Yeah, I've gone back to linpus for the moment. However, that now means my 3g modem doesn't work... :( so it's swings and roundabouts...

---

### Post by christian.paratschek on 2008-11-01
Hello!

This is the official thread for discussing Ubuntu 8.10 on the Acer Aspire One. 

There are currently two community sites for this netbook, a special guide for the 110L and Intrepid (might also be expanded to the other models)

[https://help.ubuntu.com/community/AspireOne110L]("https://help.ubuntu.com/community/AspireOne110L")

And the original one that also includes 8.04 but is a bit cluttered right now:

[https://help.ubuntu.com/community/AspireOne]("https://help.ubuntu.com/community/AspireOne")

To at least keep the first one clean, I opened this thread to discuss stuff before putting it into the documentation.

---

### Post by christian.paratschek on 2008-11-01
1. About the elevator=noop option in /boot/grub/menu.lst

I have read in the now closed development thread the following: 

> I just wanna share one more tweak that i have done to my aspire one. Adding "elevator=deadline loglevel=1 console=tty1 nolapic_timer" to the kernel line in /boot/grub/menu.lst made my system a lot more responsiveness.
I got these options from the menu.lst that cames with Linpus.

What experiences did you make? What should we recommend?

2. Are there solutions for the various Suspend/Resume issues?

Suspend/Resume breaks Audio and destroys partitions on SD-Cards. 

3. Regarding the SD-Cards:

Do we still need "options pciehp pciehp_force=1"? It works for me without this!

---

### Post by redbook4574 on 2008-11-01
Don't know if this is the right place but here goes

Aspire 150 - with umpc image loaded from usb stick.

I have tweaked the OS and got it the way I like it (added firefox - using ndiswrapper for wifi (led lit and better connection speed - 54mb vice 6mb).

My question is, is it possible to now recreate a usb image of my basic setup and if so HOW??

---

### Post by evengrift on 2008-11-02
redbook, try looking into dd, search for migration, backup, etc..
[https://help.ubuntu.com/community/BackupYourSystem]("https://help.ubuntu.com/community/BackupYourSystem") LVPM may also be an option [http://lubi.sourceforge.net/lvpm.html]("http://lubi.sourceforge.net/lvpm.html") This is not however a hardware specific issue, you'd have better luck posting a question like this in an appropriate forum..

Anyone else getting occasional random lockups with ibex? I'm getting a complete freeze after my upgrade every once in awhile, very frustrating. It's the same behavior as here: [http://ubuntuforums.org/showthread.php?t=450862]("http://ubuntuforums.org/showthread.php?t=450862") with the flashing caps lock light and the system completely locked and non-responsive to anything.

I do not believe this is a hardware issue as this has never happened with other OS's (incl. Hardy, XPsp3). That said my hardware **is** non-standard with an intel 4965 802.lln card, and upped to 1.5GB of ram.

However, everything works except video acceleration seems to be off (as discussed in other threads: [http://ubuntuforums.org/showpost.php?p=6031952&postcount=44]("http://ubuntuforums.org/showpost.php?p=6031952&postcount=44") ). However I haven't tried to re-institute the usual video hacks, not sure they're even working however based on that dev thread.

---

### Post by bapoumba on 2008-11-02
Moved to Hardware & Laptops.

---

### Post by Andyvan on 2008-11-02
Christian,

  The left-hand reader works fine for me without doing anything.  In fact, for me, a card does not have to be inserted at boot-time.  I have checked this numerous times.  

The right-hand reader, however, doesn't work the same.  I haven't remembered to have a card in there at boot-time to know whether having one in there works or not.

---

### Post by bapoumba on 2008-11-02
One thread merged.

---

### Post by Andyvan on 2008-11-02
Note for those of you wondering if it's worth it to move from the default linpus install:  Some things work now that didn't before:

[LIST=1]
[*]My bluetooth adaptor was recognized immediately when I plugged it in
[*]I have much better options for external monitor resolutions
[*]I was able to use my printer (shared on network via Linksys PSUS4)
[/LIST]

It really depends on what you're using your AAO for.

---

### Post by cake_or_death on 2008-11-02
Just a quick tip for those struggling with wireless drivers on the AAO:

All I had to do to get my wireless working well was install linux-backports-modules-intrepid BEFORE updating right after installation of 8.10, then disable the default driver in System->Administration->Hardware Drivers.  After a reboot wireless worked perfectly.  I had tried both following the instructions at [https://help.ubuntu.com/community/AspireOne110L](https://help.ubuntu.com/community/AspireOne110L), as well as the madwifi driver with no success before taking the more simplistic approach.
Hope this helps somebody.

---

### Post by BoyBlunder on 2008-11-02
I'm having a problem with my wireless card disappearing completely from the system. I'm unable to disable anything under my hardware drivers option, and ```
lspci | grep net
``` only shows my normal ethernet card.

Any suggestions??

---

### Post by khaeru on 2008-11-02
@bobnutfield and others: I just read the 8.10 release notes at [http://www.ubuntu.com/getubuntu/releasenotes/810#Atheros%20ath5k%20wireless%20driver%20not%20enabled%20by%20default](http://www.ubuntu.com/getubuntu/releasenotes/810#Atheros%20ath5k%20wireless%20driver%20not%20enabled%20by%20default). These always contain nuggets of wisdom and make worthwhile reading. In this case:

> While not installed by default, this linux-backports-modules-intrepid-generic package is included on the Ubuntu 8.10 CD and DVD images for ease of installation.

...thus if you create a bootable USB, it should include the package containing the ath5k driver. Find the appropriate package, install and go.

On an unrelated note, I have observed that wireless performance goes downhill over time. After a day of continuous use, Network Manager reports signal strengths much lower than actual. Powering down, removing the battery for a few seconds and then replacing it seems to fix the problem. I doubt this is a driver flaw; probably I smudged something with my (greasy?) fingers while doing a manual RAM upgrade and static accumulation or something is degrading the performance. However if anyone else is experiencing the same, I would appreciate knowing.

---

### Post by christian.paratschek on 2008-11-03
Hmmm... I read somewhere that there are slightly different versions of the AAO. If that's true, we do have a problem.

For instance, someone mentioned in the old wikipage that the internal mic is not working and even linked a launchpad bug for it. But the mic works for me and for others withput any problems.

Both card readers work for me without any tweaking.I just need to have them inserted before booting.

Regarding wireless: I have not stresstested the ath5k setup. I mostly do not use this machine for a complete day or longer, but I can try later.

---

### Post by Handssolow on 2008-11-03
I finally got my AAO (XP 1G 120Gb) running 8.10 persistent from a USB stick with updates/upgrades using a wired connection to my router. The bluetooth mouse often needs to be removed and reinstalled to get it to work- a known bug, also sometimes on bootup the ethernet hasn't connected. Possibly last time the following got it back- 
sudo ifconfig eth0 down
sudo ifconfig eth0 up

(I'll keep checking that my ethernet link works and edit this post if there's more news)

A couple of days ago, after checking out another Forum thread, I disabled the Atheros driver in System>Admin>Hardware Drivers and downloaded some madwifi stuff with no success. However,  System>Admin>Hardware Drivers showed a/the driver disabled but still active. Wlan(0) wasn't visible in ifconfig or iwconfig. Earlier today after reading this thread I blacklisted ath_pci as descibed earlier and inputed nothing else. A reboot and my Wlan(0) was working and initially recognising my neighbours router not mine! Perhaps related to broadcast of my router's essid being turned off? I'm currently posting from my AAO with wifi. 

The Network Applet in the top toolbar reports that I'm using the ath5k_pci driver and Hardware Drivers shows the Atheros driver is not activated. Can I assume that my driver came courtesy from the madwifi source?

Outstanding issues for me are getting a reliable connection to my Bluetooth mouse, password protection on my live USB stick, a way of backing it up to my desktop PC and why A package Manager icon is always active on the top toolbar.

---

### Post by ultra2033 on 2008-11-03
I found this on another thread, after getting the "Unable to change Visual Effects" error when trying to get Compiz working, the answer is:

type:
sudo dpkg-reconfigure xserver-xorg

and then reboot, and now you should be able to enable desktop effects and get compiz working.

Remember to add:
sudo apt-get install compizconfig-settings-manager

and follow this tutorial to get everything else working :D 
[https://help.ubuntu.com/community/AspireOne110L](https://help.ubuntu.com/community/AspireOne110L)

---

### Post by devzero on 2008-11-04
Hi,

I upgraded from 8.04 to 8.10 and installed the backport driver for my wlan but it cant connect to encrypted networks
The Driver Manager tells me that i Use the 5xxxx Driver.
Has anyone any suggestions how to get that work?

thanks in advance.

---

### Post by gmc on 2008-11-04
> **evengrift said:**
> 
Anyone else getting occasional random lockups with ibex? I'm getting a complete freeze after my upgrade every once in awhile, very frustrating. It's the same behavior as here: [http://ubuntuforums.org/showthread.php?t=450862](http://ubuntuforums.org/showthread.php?t=450862) with the flashing caps lock light and the system completely locked and non-responsive to anything.


Yes, I've had it happen a couple of times. I flashed the bios to 3304 a few days ago as it was supposted to fix the problem. I'm debating if I want to try 3305.

G.

---

### Post by Handssolow on 2008-11-04
I've no wifi this morning on my AA0 running with memory stick's 8.10 and the ethernet links comes and goes too. In contrast, I've no problem using my wifi router to upgrade a desktop pc to Intrepid whilst I'm working on my AA0. I got ethernet back after I removed the avahi-daemon and avahi-autoipd, not sure if these were the cause. Posting from my AA0 with ethernet, System>Preferences>Network Configuration shows Auto eth0 as never connected which isn't right.

By the way, considering the increasing interest in running Ubuntu from a USB memory stick I think a separate Forum category would be popular.


Edit: Since the above posting I've spend most of today locked out by me having a Gnome login window where I knew neither username or password. With my USB stick's 8.10 there's no grub or recovery mode that's easily accessible. Finally after Ctl+Alt+F6 to get a command line, I was able to sudo nano /etc/gdm/gdm.conf to alter the autologin settings plus I'd seen "ubuntu" was one of the items I needed to input. Finally getting back to a full Gnome desktop, on bootup both wifi and my bletooth mouse are both working. I've madwifi-tools, Intrepid's standard Atheros drivers disabled and no avahi packages loaded. I wonder if it will all work a next time after a reboot?  After two reboots wifi still works. Bluetooth mouse works on a cold reboot but needs binning and re-installing on a warm reboot.

---

### Post by iconolith on 2008-11-05
@khaeru
> **khaeru said:**
> On an unrelated note, I have observed that wireless performance goes downhill over time. After a day of continuous use, Network Manager reports signal strengths much lower than actual. Powering down, removing the battery for a few seconds and then replacing it seems to fix the problem. I doubt this is a driver flaw; probably I smudged something with my (greasy?) fingers while doing a manual RAM upgrade and static accumulation or something is degrading the performance. However if anyone else is experiencing the same, I would appreciate knowing.

I am experiencing the same issue with the wireless on the AAO 16GB SSD running Ibex. I tried removing the battery for a few moments and the wireless was working again after every loaded back up. You might be onto something.

---

### Post by noic on 2008-11-05
everything works in my Acer 1, even the wireless, but the wireless led don't work. 

does anyone made it work?

I use the ath5k drive.

---

### Post by anamorgan on 2008-11-05
so got an aspire user too. I use acer aspire 4715z, and i dont know why in my 2 mb connection, my resume of a downlaod take sliek 15 to 20 mins and sometimes 1 hour to start. any help ?

---

### Post by jbernardo on 2008-11-05
The leds will only work with the madwifi drivers. The ath5k kernel driver doesn't have the led interface.

---

### Post by bizkut on 2008-11-06
I am using the latest madwifi driver. Now, the wifi LED works! But only the right side wifi's LED works (flashing) not both LEDs with
```
/sbin/sysctl -w dev.wifi0.ledpin=3
/sbin/sysctl -w dev.wifi0.softled=1
```
on /etc/rc.local

The LED flashing slowly when searching for networks and goes faster when connecting to AP, flashing with a certain pattern when connected and light off when the wifi switch turned off.

The wifi switch also works to disconnect the wifi from AP. It doesn't turn off the device. So, ath0 is still up ready for connection. So, the problem is the nm-applet is always looking for available networks and trying to connect to them automatically, thus later ignores the wifi switch which early turned the wifi off.

I never have a chance to try to turn on the wifi through the switch because the nm-applets turns it on before me. So, I don't know if the switch working for connecting the wifi back.

Something to do with nm-applet handling, or the way the switch works.

:guitar:

---

### Post by jbernardo on 2008-11-06
I never saw the left led working, nor any reports of it working at all.

---

### Post by kluless on 2008-11-06
Hi, "new" (had it for a week) AAO owner here. I've installed Xubuntu 8.10 and the linux backports modules so I now have wifi working. Now the only thing I'm missing is MS-DUO support in the card reader.. SD seems to work great on both the left and right side, but my MS/MS-DUO isn't detected when I insert it.

Anyone else having this problem? Any idea on how to solve this?

---

### Post by jbernardo on 2008-11-06
The MS support isn't compiled in the ubuntu kernels. The module is still experimental. The only way I found to have it is to build the kernel from source, enabling the module.

---

### Post by Orestez on 2008-11-06
> **devzero said:**
> Hi,

I upgraded from 8.04 to 8.10 and installed the backport driver for my wlan but it cant connect to encrypted networks
The Driver Manager tells me that i Use the 5xxxx Driver.
Has anyone any suggestions how to get that work?

thanks in advance.


I had the same problem. In NM it said "Wireless Networks" but showed none. Turned out the network cards wireless is turned off by "default" and you have to turn it on with the switch, then it suddenly worked.

---

### Post by kluless on 2008-11-06
Ah, that would explain things. :)
thanks.

---

### Post by nray on 2008-11-07
Hi, I've had two big problems with Intrepid on my Aspire One that I haven't seen documented yet... one is with the gnome-power-manager [(my thread here)]("http://ubuntuforums.org/showthread.php?p=6072544") and the other is with sound [(my thread here)]("http://ubuntuforums.org/showthread.php?p=6112926").  Does anyone have any fixes for these problems, or should I report them as bugs?

---

### Post by darkwalt on 2008-11-08
Is the problem different from that in this guide?

[https://help.ubuntu.com/community/AspireOne#AUDIO:](https://help.ubuntu.com/community/AspireOne#AUDIO:)

---

### Post by mrcunninghamz on 2008-11-08
I am running ubuntu intrepid on my acer aspire one.

Everything seemed to work on the top half regarding installation and configuring your acer with ubuntu 8.04. 

I'm not quite sure if a solution for this has been addressed:
The only problem I had was with the wifi during suspend/resume. It would no longer connect to any wireless access points i was previously able to.

I searched around and found this entry from this site:
[https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules/+bug/272300](https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules/+bug/272300)

The fella Brian Harkness came up with this solution. 
(this is assuming you are using madwifi)
> 

FIX/workaround: If you have trouble with reconnection and when you do ifconfig you have my issue of wifi0 being present from boot but not resuming from suspend/hibernate,

open

/usr/lib/pm-utils/sleep.d/10NetworkManager

thaw|resume)
ifconfig wifi0 up <--
resume_nm

add that line assuming this is the virtual device (for you as it is for me) that madwifi creates along with ath0.

You don't need to add ath0 if that seems to show up after resume.

NM reconnects Wifi every time - so far for me anyway.


This has managed to work for me as well. I have not tested it from resume out of hibernation, but resume from suspend seems to work just fine.

Enjoys.

---

### Post by nray on 2008-11-09
> **darkwalt said:**
> Is the problem different from that in this guide?

[https://help.ubuntu.com/community/AspireOne#AUDIO:](https://help.ubuntu.com/community/AspireOne#AUDIO:)

Yes, it is different.  That guide is for 8.04, and is accurate for 8.04 (it worked for me in 8.04).  All the guides for 8.10 and audio were accurate for 8.10 beta and initial release, until a week ago.  Please [read my thread]("http://ubuntuforums.org/showthread.php?p=6138747") on the issue for more information on the symptoms and everything I've tried.

---

### Post by andrewsimpson on 2008-11-10
Cross-posting a post that I made on the Aspire One User Forum: I now have both card readers working perfectly in 8.10.

I mostly followed the instructions on the [Debian Aspire One Wiki]("http://wiki.debian.org/DebianAcerOne"). I can insert SD cards at any time, in any sequence, and hal will see the card, put an icon on my desktop (Xubuntu) and open a file manager. I tried an old MemoryStick in the righthand reader, but the kernel didn't seem to recognise this.

Here is what I did:

Created a file /etc/modprobe.d/aspireone with the following contents:

```

options pciehp pciehp_force=1
install sdhci for i in 2381 2382 2383 2384; do /usr/bin/setpci -d 197b:$i AE=47; done; /sbin/modprobe --ignore-install sdhci

```


Note there are only two lines in this file. On the original web page, the line wrap made it look like three lines - and I don't think that will work.

Added the following line to /etc/modules:

```

pciehp

```

Nothing else! Nothing changed in fstab - we let hal do this automagically....

Rebooted, and it just worked.

So far the fix has been confirmed by other users on the Aspire One User Forum.  With a bit of luck this might solve the long running problems with the card readers.:)

---

### Post by andrewsimpson on 2008-11-10
Cross-posting a post I've made on the Aspire One User Forum:

There is a small error in the file listings on the various community wiki's that prevents USB from suspending.  This means that the webcam stays on 100% of the time affecting battery life.

These lines in the Ubuntu wiki don't work:

```

# Decrease power usage of USB while idle
[ -L /sys/bus/usb/devices/1-5/power/level ] && echo auto > /sys/bus/usb/devices/1-5/power/level
[ -L /sys/bus/usb/devices/5-5/power/level ] && echo auto > /sys/bus/usb/devices/5-5/power/level

```

These equivalent lines in the A110 wiki don't work either:

```

# Decrease power usage of USB while idle
[ -x /sys/bus/usb/devices/1-5/power/level ] && echo auto > /sys/bus/usb/devices/1-5/power/level
[ -x /sys/bus/usb/devices/5-5/power/level ] && echo auto > /sys/bus/usb/devices/5-5/power/level

```

The problem is the test conditional; '-L' checks for symbolic link (it's not), while '-x' checks for executable (it's not). The second line ('5-5') controls the webcam, while the first line ('1-5') does not have any use?

Here is the fix:

```

# Decrease power usage of USB while idle
[ -w /sys/bus/usb/devices/1-5/power/level ] && echo auto > /sys/bus/usb/devices/1-5/power/level
[ -w /sys/bus/usb/devices/5-5/power/level ] && echo auto > /sys/bus/usb/devices/5-5/power/level 

```

I have already taken the liberty of fixing up the wiki's.;-)

---

### Post by devzero on 2008-11-10
Hi,

about my wlan problem:

i deactivated the ath5xxx driver and did this:

```

sudo apt-get install build-essential 
svn checkout http://svn.madwifi.org/madwifi/branches/madwifi-hal-0.10.5.6 
cd madwifi-hal-0.10.5.6 
make
sudo make install 

```

/etc/rc.local:
```

sysctl -w dev.wifi0.ledpin=3
sysctl -w dev.wifi0.softled=1

```

now it works again as before.
If you install a new kernel you have to reinstall the madwifi driver again

```

make clean
make
sudo make install 

```

HTH

---

### Post by jbernardo on 2008-11-10
That is exactly what I do, as the ath5k driver is too unstable for my taste (besides not supporting the led interface).

---

### Post by nray on 2008-11-10
> **jbernardo said:**
> That is exactly what I do, as the ath5k driver is too unstable for my taste (besides not supporting the led interface).

When you say the ath5k driver is too unstable, what are the symptoms?  I've been using ath5k since I upgraded to 8.10 beta (because the wiki guides told me ath5k 'just worked' in 8.10), and the only problems I've seen have been with gnome-power-manager periodically hanging every few minutes and recently sound ceasing to work, but wireless actually seems fine (though not with the performance I'd always expect).

---

### Post by thor2002ro on 2008-11-10
> **nray said:**
> When you say the ath5k driver is too unstable, what are the symptoms?  I've been using ath5k since I upgraded to 8.10 beta (because the wiki guides told me ath5k 'just worked' in 8.10), and the only problems I've seen have been with gnome-power-manager periodically hanging every few minutes and recently sound ceasing to work, but wireless actually seems fine (though not with the performance I'd always expect).

the problem is that its slow...not switching speeds correctly , no led , sometimes the wlan card gets stuck on boot and will not connect on any netowk unless you shutdown(as in halt) and boot again(dont remember the exact stuck error...i think is something about hardware reset...)

---

### Post by HonoredMule on 2008-11-11
devzero's instructions for compiling madwifi driver directly from source came the closest to fully functional for me, and is now the ONLY way that will work at all.

```

sudo apt-get install build-essential 
svn checkout http://svn.madwifi.org/madwifi/branches/madwifi-hal-0.10.5.6 
cd madwifi-hal-0.10.5.6 
make
sudo make install 

```

/etc/rc.local:
```

sysctl -w dev.wifi0.ledpin=3
sysctl -w dev.wifi0.softled=1

```
I had to add
```
modprobe ath_pci
```
to get it to work on boot, and the modprobe line only worked when it preceded the sysctl lines.  Also, the *working* madwifi driver creates an ath0 device, as well as a wifi0 device with "no wireless extensions."  But the LEDs do not work using either device name.

Also, I still cannot connect to hidden SSIDs (even when manually initiated), and after standby, my access point is not found and gives me the repeating password request if I manually force a connection (as if it were hidden).

_______________________________________________


I had started by following the Aspire One instructions on the wiki, which worked on the first day and never again thereafter.  After that I screwed around with every possible solution discussed in any related bug reports:

madwifi-tools from the repository, wicd, and ath9k did nothing at all.

ath5k recognized the hardware and appeared functional, but wouldn't successfully connect to my WPA access point...I got the repeating password request.  While trying to work with it, I also encountered various other discussed issues, such as needing a cold boot for the hardware to function, refusing to connect to hidden SSID (which it had successfully done at first as per the wiki setup), and finding no access points.

The only thing I didn't bother with was ndiswrapper, as I had no intention of dealing with that bag of hurt, and WPA support was an absolute necessity.

---

### Post by nray on 2008-11-11
> **HonoredMule said:**
> ath5k recognized the hardware and appeared functional, but wouldn't successfully connect to my WPA access point...I got the repeating password request.  While trying to work with it, I also encountered various other discussed issues, such as needing a cold boot for the hardware to function, refusing to connect to hidden SSID (which it had successfully done at first as per the wiki setup), and finding no access points.

Hmm, well I haven't used ath5k with WPA at all (or WEP), but I do use it extensively with a hidden SSID, and don't have any problems.  I also haven't seen any problems with ath5k during either warm or cold boots, it's always functional, and it's never had any trouble seeing all broadcast access points either.

---

### Post by FunEye on 2008-11-12
Anyone else having problems getting the sched_smt_power_savings to stick?

I've added:
```
# As in the rc.last.ctrl of Linpus
echo 1 > /sys/devices/system/cpu/sched_smt_power_savings
```

to my rc.local, but I still get:
```
>cat /sys/devices/system/cpu/sched_smt_power_savings
0
```

Trying to edit it from a terminal only gives "Permission denied", even running as su.

Might be a stupid question, but I'm just starting to learn how to run Linux.. :)

Another thing is the 

```
options pciehp pciehp_force=1
```

in /etc/modprobe.d/aspireone. This seems to make the card slot polling go haywire. Every second it reports card is present, then card not present, looping over and over, leading to spikes in CPU freq.. Anyone else seeing this?

---

### Post by HonoredMule on 2008-11-12
I got to test the madwifi-hal-0.10.5.6 install at a friend's house yesterday, where there were 13 different access points visible.  I had no trouble connecting to his WPA2 access point as well.

For the time being, I'm just not using hidden SSIDs or standby, and I still haven't gotten a peep out of the LEDs.

But I did notice today that the fn+right sends a '±' character, and out of the blue I started getting a brightness meter when adjusting brightness (hadn't shown up before, don't know why)--which only goes up because of this incorrect mapping.  I know someone else noticed and fixed this elsewhere, so I'll just have to find that post/page for the "brightness up" keycode.

I will say I'm quite happy, as this is the first linux-based machine I've managed to get working well enough to report no show stoppers and also be happy and comfortable using it in a graphical desktop environment.  Nautilus even works with samba shares and correctly launches VLC on remotely-stored files--will wonders never cease?  (I've had no end of hassles with this in the past.)

---

### Post by beow on 2008-11-12
> **nray said:**
> and the only problems I've seen have been with gnome-power-manager periodically hanging every few minutes 

I also experienced this. Any idea of how to fix it?

---

### Post by knudsen18 on 2008-11-12
I've just installed Ubuntu 8.10 intrepid on my AA1, and Ive followed the guide on [https://help.ubuntu.com/community/AspireOne](https://help.ubuntu.com/community/AspireOne) . Ive tried to get my wifi to work by follow the guide about "Wireless Module" and done eactly as described, but I can't find my wireless network in my house. Im unable to press both wireless and wired connection on my connection tab. Any suggestions?

---

### Post by Tk0680 on 2008-11-12
This is so very, very disappointing.

My AAO (with 8.10) works fine, with the exception of the WLAN. Unfortunately, the idea of an ultra-portable computer without wireless networking is pretty flawed, and wireless networking I am certainly without currently.

I don't think it's unfair to say that Ubuntu 8.10 does not work (yes, I'm suggesting that inoperable network interfaces count as a broken installation) reliably after significant tinkering and tweaking on an AAO, let alone "out of the box".

---

### Post by HonoredMule on 2008-11-12
Ok, seriously, WTF?  ath5k worked fine...at first, and died 24 hours later.  Now I've compiled and installed madwifi-hal (ath_pci) and it worked...for 24 hours.

Atheros cards are supposed to be awesome with Linux (a big reason why I bought this netbook) and yet drug dealers would treat me better than this ****.  What gives?  Each time a working install fails, nothing has changed at a system level.

---

### Post by upallnight on 2008-11-13
I just got WiFi working on my Acer Aspire One with 8gb ssd and 1.5gb ram (upgraded) and Ubuntu Intrepid 8.10 after the default Atheros 802.11 Hardware Drivers didn't work and the installed madwifi 5xxx series drivers didn't work either and heres how:

Install the latest version of the madwifi drivers from their website by building the source code.

First, go to System->Administration->Hardware Drivers
and de-activate all the Atheros wireless drivers (one by default and two if you installed madwifi).

Second, download the newest source code for madwifi from here:
[http://snapshots.madwifi-project.org/madwifi-hal-0.10.5.6/](http://snapshots.madwifi-project.org/madwifi-hal-0.10.5.6/)

Current version:
[http://snapshots.madwifi-project.org/madwifi-hal-0.10.5.6/madwifi-hal-0.10.5.6-r3875-20081105.tar.gz](http://snapshots.madwifi-project.org/madwifi-hal-0.10.5.6/madwifi-hal-0.10.5.6-r3875-20081105.tar.gz)

Then extract the archive using Archive Manager or use a terminal and create an extract directory, copy the archive there and untar it:
```

mkdir madwifi
cp madwifi-hal-0.10.5.6-r3875-20081105.tar.gz ./madwifi/
cd madwifi
tar -xzvf madwifi-hal-0.10.5.6-r3875-20081105.tar.gz
```

Then open a terminal and make sure you have the gnu compiler installed:
```

sudo apt-get install build-essential linux-headers-$(uname -r)
```

Now build the madwifi source code:
```

make
sudo make install
```

Now to add the madwifi module to the kernel every boot, add this line anywhere before the exit 0 in your /etc/rc.local file:
```

modprobe ath_pci
```

Now reboot and your wifi card will work!

The wireless toggle button at the front of the netbook also works, but the two LEDs won't ever turn on and the only feedback will be from the Network Monitor in the taskbar and because your internet connection has died :)
Toggling between WiFi on/off works without any extra modification.

This is a list of hardware that have issues after installing Intrepid:
built-in speakers - no sound until following the instructions found here:
[https://help.ubuntu.com/community/AspireOne110L#Audio](https://help.ubuntu.com/community/AspireOne110L#Audio) then it works fine
headphones - work fine without modification
built-in mic - works but has tons of static
external mic - doesn't work
all the usb ports work
I haven't tried the sd and hdsd card reader ports yet but I hear they don't work
The Function+Vol Up/Down buttons work by default!

---

### Post by mustang on 2008-11-13
> **upallnight said:**
> I just got WiFi working on my Acer Aspire One with 8gb ssd and 1.5gb ram (upgraded) and Ubuntu Intrepid 8.10 after the default Atheros 802.11 Hardware Drivers didn't work and the installed madwifi 5xxx series drivers didn't work either and heres how:

Install the latest version of the madwifi drivers from their website by building the source code.

First, go to System->Administration->Hardware Drivers
and de-activate all the Atheros wireless drivers (one by default and two if you installed madwifi).

Second, download the newest source code for madwifi from here:
[http://snapshots.madwifi-project.org/madwifi-hal-0.10.5.6/](http://snapshots.madwifi-project.org/madwifi-hal-0.10.5.6/)

Current version:
[http://snapshots.madwifi-project.org/madwifi-hal-0.10.5.6/madwifi-hal-0.10.5.6-r3875-20081105.tar.gz](http://snapshots.madwifi-project.org/madwifi-hal-0.10.5.6/madwifi-hal-0.10.5.6-r3875-20081105.tar.gz)

Then extract the archive using Archive Manager or use a terminal and create an extract directory, copy the archive there and untar it:
```

mkdir madwifi
cp madwifi-hal-0.10.5.6-r3875-20081105.tar.gz ./madwifi/
cd madwifi
tar -xzvf madwifi-hal-0.10.5.6-r3875-20081105.tar.gz
```

Then open a terminal and make sure you have the gnu compiler installed:
```

sudo apt-get install build-essential linux-headers-$(uname -r)
```

Now build the madwifi source code:
```

make
sudo make install
```

Now to add the madwifi module to the kernel every boot, add this line anywhere before the exit 0 in your /etc/rc.local file:
```

modprobe ath_pci
```

Now reboot and your wifi card will work!

The wireless toggle button at the front of the netbook also works, but the two LEDs won't ever turn on and the only feedback will be from the Network Monitor in the taskbar and because your internet connection has died :)
Toggling between WiFi on/off works without any extra modification.

This is a list of hardware that have issues after installing Intrepid:
built-in speakers - no sound until following the instructions found here:
[https://help.ubuntu.com/community/AspireOne110L#Audio](https://help.ubuntu.com/community/AspireOne110L#Audio) then it works fine
headphones - work fine without modification
built-in mic - works but has tons of static
external mic - doesn't work
all the usb ports work
I haven't tried the sd and hdsd card reader ports yet but I hear they don't work
The Function+Vol Up/Down buttons work by default!

Thanks upallnight. These instructions worked perfectly.

---

### Post by bobnutfield on 2008-11-13
I believe that the hard driver version (model 150) uses the same Atheros wireless chipset as the 8GB SD version.  I have Intrepid running on a USB stick and wireless is working with the ath5k module (no madwifi needed.)  You simply have to blacklist the ath_pci module.

---

### Post by Yumpin_Yimminie on 2008-11-15
[FONT="Arial"][SIZE="3"]I have an Acer Aspire One with 512 MB ram and the 8 GB SSD drive.  I've read various comments about SSD drives having a very limited life so it is advised to avoid putting a swap partition on the drive.  I believe SSD drives can be replaced in this computer.  Taking things apart and putting them back together so they work is not one of my strong points.

With only 512 MB ram, swap would be a pretty nice thing to have.  So I went out and bought a 8 GB sdhc card and put it into the left hand card reader.  Then started installing Ubuntu .... again.  When it came to partitioning I went ahead and made the SSD internal drive all 'ext2'.  I also went ahead and partitioned the sdhc card in the left card slot.  I set 1.5 GB for swap and the rest for 'ext2'.  I loaded it at the / level.  Which I don't have a clue what that is or means.

Now mostly I had done the initial installation of Ubuntu on the Aspire following the instructions of Christian Paratschek at:  [https://help.ubuntu.com/community/AspireOne110L]("https://help.ubuntu.com/community/AspireOne110L")

But as mentioned I am a neophyte in Ubuntu and Linux in general.  

I've got a bunch of questions and hopefully someone(s) will have the patience to help answer them.  

The very first is swap space on the sdhc card that is located in the left card reader position.  Would the operating system actually use the swap parition that is on this sdhc card?  When I did partition this sdhc card during a full install of the Intrepid Ibenix I devoted the remainder of the space not going to the swap area to 'ext2'.  Not being that familiar with the Ubuntu filing system.  Is 'ext2' the best file system for the partition that takes up the remainder of the space on the sdhc card or should I be using a different alternative such as NTFS or 'ext3'.  

Another area of questioning is about the package 'GParted'.  When I fire up 'GParted' the SSD drive can be worked with.  But there is no way to work with the partitions that I set up while installing 8.10 the Intrepid Ibenix on the sdhc card that is in the left hand card slot.   

The last area of questions is the amount of files that have been installed on the sdhc card in the left side card slot of the computer.  The sdhc card is 8 GB.  There is a 1.5 GB partition for the swap.  That left 6.5 GB for the 'ext2' partition that is currently on the card.  When I pull up properties it shows:

Name:       6.5 GB Media
Type:       folder (inode/directory)
Contents:   111,518 items, totalling 1.8 GB (some contents  unreadable)

Then a pie chart with the following detail

Free space:  3.6 GB

yellow portion of the pie chart says 2.3 GB used
blue portion of the pie chart denoted 3.6 GB free

Filesystem type:  ext3  [note when I partitioned this card I partitioned this with a file system of 'ext2'.  

When I click on the Volume Tab of the Media Properties Window it states:

File System ext2


When I browse the 6.5 GB disk I see file folders for 'bin', 'boot', 'dev', 'etc', 'home', and a bunch more files that all look like they are related to system operations.  I was going to ask how did they get there.  But silly question, I put them there.  I just don't know how I did it.  It doesn't seem like they really need to be on this sdhc card in the left hand slot of the computer. 

As an experiment I took and removed the partition on the internal SSD drive.  I then shut down the computer.  Removed the connection to CD drive that I was running the LiveDisk from.  I then tried rebooting the computer with the sdhc card configured as detailed above and the computer wouldn't boot to the Ubuntu system.  So I'm feeling pretty confident that all those system files that are on the sdhc card in the left hand slot of the computer aren't needed to be on that card. 

So what do I want to do?  Here is the list:

1) Install Ubuntu 8.10 on my Acer Aspire One.

2) Be able to have the internal SSD drive to be partitioned entirely in 'ext2' with no swap partition on the drive.  I want to avoid wearing out the SSD drive for as long as possible.
 
3) Have a swap on the sdhc card that is in the left hand slot of the computer.  Figuring it is much easier and cheaper for me to wear out and replace a sdhc card in the left slot of the computer then having to take the computer apart and replace the internal SSD drive.

4) Find out what the best type of partition to set up on the sdhc card that is in the left slot of the computer for the space left after a swap partition is allocated to that sdhc card.

5) Find out how to avoid getting all those system files that are on the sdhc card when I redo the partition.

6) Find out how to use 'GParted' to change the partitioning on that sdhc card.  Currently when I run 'GParted' it will see the internal SSD card and let me make changes to the partitions on it, but won't see the sdhc card that is the left hand slot of the computer.  If I can't use 'GParted' to change the partitioning on the sdhc card is there another program that I can use that will allow me to change the partitioning on the card?

7) Is it possible to get updates for the Bios on this computer?  

I thank you for your patience and any help you can provide.

Have a Great Day,
Jim



[/SIZE][/FONT]

---

### Post by Aearenda on 2008-11-15
I can answer a few of these, and pose more questions!

Question 2 - ext3 is a journalling version of ext2, and you're right to use ext2 on the SSD (at the risk of lost data on power loss). But I think you need to have '/' on the SSD - see below.

Question 3 - I would question the use of the sdhc card for swap. First, do you really need any swap space at all? This depends on what apps you plan to use. However, a swap partition is definitely needed if you want to use hibernation. Secondly, is it fast enough? There's no point in swapping if it makes the computer go slower than it would without swap. I hope others will chime in with comments on this - my Aspire One has a hard disk, so I haven't experimented with this. I guess the use of similar devices for Vista 'readyboost' suggests they are fast enough. My Aspire One running Hardy uses about 230Mb for the logged-on system, before running any applications. Don't forget that Linux uses the rest of the memory for disk caching, so it always 'seems' to be all in use.

Question 4 - Ext2 again, for the same reasons.

Question 5 - the files on your sdhc card are the operating system itself, because you placed '/' there. On Unix and Linux systems, '/' is the root of the filesystem. Windows uses drive letters instead, and has a separate filesystem within each partition. Linux 'mounts' additional partitions at empty folders in the root filesystem, so that all the partitions look like they are part of a single filesystem tree. The operating system files go in '/' by default. One of the folders that is created is called '/home', and corresponds to "Documents and Settings" on Windows. This folder is often used as the mount point for a separate home partition. It sounds to me as though you have your SSD mounted as '/home' and you are booting off the sdhc drive. I assume you've acted upon the recommendations to reduce logging - or you could usefully use the data partition on the sdhc card for /var, and keep logging as normal.

I don't know about Questions 6 and 7.

EDIT: On Q6, I just put a card in the left slot of my Hardy system, and rebooted. In GParted on Hardy, I *can* select the partition on that drive and work with it, using the drop-down list at the top right of the window. Maybe you can't because the partition is in use on your system and GParted is preventing disaster.

By the way, just for the record, you didn't need to re-install Ubuntu to add the swap partition. It may be harder because of being on the sdhc card, but there are normally four command-line steps involved: 1) use fdisk (or GParted) to create the partition 2) use mkswap to format the partition 3) use swapon to bring it into use on the running system (no reboot needed) 4) Modify /etc/fstab to make sure it is used on subsequent reboots. I haven't given details of the parameters here because I don't remember what the sdhc device was called (I've turned my AA1 off again).

Another afterthought: I think on reflection that your AA1 may be booting GRUB (the bootloader) initially from the internal SSD, but then loading Ubuntu from the sdhc card - unless you have changed the boot order in the BIOS. Also, maybe you have not mounted the SSD as /home after all, judging from your experiment about removing the partition. I'm a bit confused about exactly what you did there!

I hope this helps!

---

### Post by thor2002ro on 2008-11-15
anyone know how to boot off the sdhc? i know bios doesnt support it so you got to have grub on the hdd , but how do you boot it :|

---

### Post by mustang on 2008-11-15
> **mustang said:**
> Thanks upallnight. These instructions worked perfectly.

Hmmm I take this back. Wifi gets a little twitchy after multiple suspends and resumes. The access point list doesn't refresh sometimes.

And unrelated to wifi, suspend will not work sometimes.

---

### Post by jbernardo on 2008-11-16
> **nray said:**
> When you say the ath5k driver is too unstable, what are the symptoms?  I've been using ath5k since I upgraded to 8.10 beta (because the wiki guides told me ath5k 'just worked' in 8.10), and the only problems I've seen have been with gnome-power-manager periodically hanging every few minutes and recently sound ceasing to work, but wireless actually seems fine (though not with the performance I'd always expect).

Sorry for the long delay replying, but the last two weeks have been very busy.
When I say the ath5k driver is unstable, I mean not only that it shows a lower connection quality and has more trouble connecting than the madwifi driver, but also that it will hang my one (not even answering to alt-sysrq) if there is more than one AP with the same ssid in the neigbourhood. I've seen it happen in hotels and airports, where the APs have all the same SSID.

---

### Post by rudinger on 2008-11-17
Hi!

Remember that there is a switch below the wifi led to turn on/off the wifi. I didn't know and I became crazy!

Thanks

---

### Post by fallenclient on 2008-11-17
I have the 120Gb hdd with 1Gb memory AAO, that has some problems with the madwifi drivers. Following the community instructions for madwifi under hardy on my intrepid install it seemed to have worked fine. But it only intermittantly comes up after boot, sometimes three or four boots before it will show up and connect to my router. Flicking the wifi kill switch at these times doesnt make any difference other then switch the LED on/off.

---

### Post by damianusthesage on 2008-11-18
Sorry if I've missed this in the posts above, but this document is specific to the AAO with 8.10

[https://help.ubuntu.com/community/AspireOne110L](https://help.ubuntu.com/community/AspireOne110L)

Anyone else really, really hate that the wireless LED's don't work and wondering if the irritation is justified? It shouldn't bug me as much as it does...

Also, what is the issue with the fan control as mentioned in the above link?
I find my AAO to be super-quiet. I don't want to go through the modification unless I am actually improving something.

---

### Post by fogelfink on 2008-11-18
Most things seem to work OK on my Aspire One.

The one thing I struggle with is to get my internal mic working - neither skype, nor sound recorder will record any sound.

I am running a pure ALSA setup, no pulseaudio.
So my sound preferences are all set to autodetect, except sound capture is set to ALSA.
When I go to alsamixer I have all capture tabs on full, but can't get the thing recording.
Any advice?

---

### Post by cake_or_death on 2008-11-19
I'm having some of the same issues with my wireless now (this started happening only recently) that some have outlined in this thread.  I have tried both the ath5k driver and madwifi, but both fail to connect after suspend, and sometimes even fail on a cold boot.  I am repeatedly asked for my password, and no connection is made, though I can see all the networks in my area, including my own router.  Has anyone made any progress on this issue?  Also, does anyone know why this problem came up only recently, and not when I initially installed the driver?  I'm just looking for a little enlightenment.

---

### Post by djpandemonium on 2008-11-20
cake_or_death:
I'm seeing the same thing with 8.10 and ath5k.  I was contemplating the possibility of trying madwifi to see if it's any better, so I'm interested to know that you still had trouble.  Was it any better at all?

---

### Post by nray on 2008-11-20
> **cake_or_death said:**
> I'm having some of the same issues with my wireless now (this started happening only recently) that some have outlined in this thread.

I had been using ath5k since 8.10 beta, and then I was at a hotel recently and was surprised to find that during one bootup it could see the hotel network but gave me 0% signal.  Rebooted and it worked ok, but I was very unhappy with that flakiness, and it certainly was slow.

I have lots of experience with ndiswrapper (in Ubuntu 8.04 64-bit it was the *only* way I could get one particular Atheros PCIe wireless card to work, and on top of that I had to pre-up it in the config file with the card's MAC address), and it was very easy to use ndiswrapper on the Aspire One.  It's been both reliable and with improved signal strength and performance.  I think people should avoid ath5k, it's just not ready.

---

### Post by nray on 2008-11-20
I'm still having issues with sound in 8.10 - some update or dependency to some software I installed at some point appears to have caused ALSA to just produce crackles for output, whereas in 8.10 beta and the first couple weeks of release it worked great.

I've discovered that if I go into Sound Preferences and set playback to any OSS and test it, then I do get the proper test tone. If I set it to Autodetect, or any ALSA, I get crackles or I get an error message along the lines of "audotestsrc wave=sine freq=512 ! ..." So it looks like OSS works... and I do get functional audio in the Rhythmbox Music Player, but I get just crackles in Miro (I'm assuming this is because one uses OSS and the other ALSA?)

Anyone have any ideas what's going on, or how I can solve this?  I also have PulseAudio installed, if that matters.

---

### Post by cake_or_death on 2008-11-21
> **djpandemonium said:**
> cake_or_death:
I'm seeing the same thing with 8.10 and ath5k.  I was contemplating the possibility of trying madwifi to see if it's any better, so I'm interested to know that you still had trouble.  Was it any better at all?

I'm afraid I can't say the madwifi was any better.  The madwifi produced exactly the same result as the ath5k, with sketchy connections, and no connection after a suspend.  I'm now considering trying the ndiswrapper, because on a so-called "netbook" wireless is pretty essential.  I'm sorely disappointed with this issue in intrepid, since everything else is greatly improved, including graphics and boot time on my aspire one.  I'm finding now that the wireless on my sony vaio is also a little buggy, though I can always reconnect if I'm disconnected, even after a suspend.  I thought improved wireless was supposed to be a major focus of the intrepid release.  Boo... hiss...

PS:  Has anyone had a good experience with the ndiswrapper on their aspire one using intrepid?  Are these same issues a problem?

---

### Post by jbernardo on 2008-11-21
I have madwifi working well after suspend - but only because I added a file in /etc/pm/config.d with the line 'SUSPEND_MODULES="snd-hda-intel ath_pci"'. That fixes the madwifi problems with suspend/resume, but not the alsa ones (the headphones won't disable the speakers when plugged in  after a resume).
The madwifi drivers have worked well for me with this fix. Stable, decent signal, no lockups.

---

### Post by redbook4574 on 2008-11-21
> **cake_or_death said:**
> I'm afraid I can't say the madwifi was any better.  The madwifi produced exactly the same result as the ath5k, with sketchy connections, and no connection after a suspend.  I'm now considering trying the ndiswrapper, because on a so-called "netbook" wireless is pretty essential.  I'm sorely disappointed with this issue in intrepid, since everything else is greatly improved, including graphics and boot time on my aspire one.  I'm finding now that the wireless on my sony vaio is also a little buggy, though I can always reconnect if I'm disconnected, even after a suspend.  I thought improved wireless was supposed to be a major focus of the intrepid release.  Boo... hiss...

PS:  Has anyone had a good experience with the ndiswrapper on their aspire one using intrepid?  Are these same issues a problem?

I am happily using ndiswrapper with no problems, i travel all over the country and have connected everywhere i go

---

### Post by cake_or_death on 2008-11-21
> **jbernardo said:**
> I have madwifi working well after suspend - but only because I added a file in /etc/pm/config.d with the line 'SUSPEND_MODULES="snd-hda-intel ath_pci"'. That fixes the madwifi problems with suspend/resume, but not the alsa ones (the headphones won't disable the speakers when plugged in  after a resume).
The madwifi drivers have worked well for me with this fix. Stable, decent signal, no lockups.

Might this fix also work with the ath5k driver?  I'm reluctant to switch drivers yet again.

EDIT:  This fix does in fact work with the ath5k driver.  I have my wireless connecting consistently after suspend by adding a file in /etc/pm/config.d with the SUSPEND_MODULES line mentioned above.  On another note, I got the audio working after suspend by following the tweaks in the Aspire One ubuntu community documentation for installing Hardy (I went with the model=toshiba option).

---

### Post by LoSt180 on 2008-11-23
I've got an AOA-150 1.5GB Ram, 160GB hard drive Running Ubuntu 8.10 and Netbook-remix for about 2 weeks now, and I've been very satisfied. I followed most of the tweeks from the wiki. I'm using the ath5k driver for wireless and it works just fine most of the time, sometimes I can't connect to my network (it keeps prompting for a password, and clicking "show password" just has a bunch of gibberish and not my passphrase. it's happened both at home and at my parents). 

Video playback was a pain, because totem displays a narrow screen instead of filling up the full wide screen. I tried using xine backend, still didn't work. So now I'm using MPlayer, and the display is good. 

I've tried a few test calls on Ekiga softphone, and can't get the mic to work. Doesn't look like there's a complete fix yet. Camera worked out of the box.

I also commented out some of the CPU power saving setting that were in the Wiki, because it seemed to cause my One to run really slow, flash video in firefox was very jittery and jumpy. 

Created the config file for acerfand and reduced the temp by 10 degrees because it was getting too hot in my lap. Luckily the fan isn't too loud.

---

### Post by peterpall on 2008-11-23
The mic problem I can confirm, but at least I have answers for the wifi prompting for the passphrase again that seem to work for me:
[LIST]
[*]The Gibberish should actually be the passphrase --- only converted into a hexadecimal number --- at least in theory, since using this number for logging in to the network never works vor me.
[*]Why the network manager sometimes asks for the passphrase even if it should know it still is not clear to me. I have the impression it just panicks if the first attempt to log into the network failed. Pressing *cancel* instead of typing in anything normally results in a stable network connection in this case, as does clicking on the network manager icon and choosing the network the computer was trying to connect to again.
[/LIST]

---

### Post by brucealdridge on 2008-12-04
time for me to chime in i guess,
i've had my AAO (8GB SSD) for a few days now... i seem to have the same issues as everyone else.
 - wireless passwords not working.. (at work and at home after suspend) .. at work resetting the router has worked twice!? or just restarting the AAO
 - the wireless leds... grrr is the wireless being screwy or is it just off?
 - the mic. i can't seem to get the mic working... plugging one in works fine when i bump the volume way way up, but internal doesn't work at all.

implemented most of the fixes from the wiki, would be stuck without it!

also i;m keen to do a photo a day type thing everytime it boots, but cant find an easy way to grab one frame from thhe camera, any ideas?

-bruce

---

### Post by Cobi00 on 2008-12-04
For people with wireless issues at startup see here - confirmed bug. I see this issue when the network manager pops up asking me to re-enter details. 

You normally see something like this in your dmesg:

ath5k phy0: noise floor calibration failed (2412MHz)
ath5k phy0: can't reset hardware (-11)

[https://bugs.launchpad.net/ubuntu/+source/linux-backports-modules-2.6.27/+bug/290991]("https://bugs.launchpad.net/ubuntu/+source/linux-backports-modules-2.6.27/+bug/290991")

---

### Post by malmjako on 2008-12-04
> **brucealdridge said:**
> 
also i;m keen to do a photo a day type thing everytime it boots, but cant find an easy way to grab one frame from thhe camera, any ideas?

Ha! That's a good idea! It would be interesting to know how to do that.

---

### Post by dpod on 2008-12-05
Hi all,

I installed 8.10 on a new aspire one flawlessly using the backported ath5k dirver about two weeks ago. And then two days ago there was a new kernel update and my wireless vanished. I reinstalled had no luck then some luck and so have been trying to figure out what the issues is: I got the wireless working and decided to try reinstalling to trace step by step what was going on. And I can't figure out why it works sometimes and not others following essentially the same algorithm.

Here's what I've been doing:

1) Regular 8.10 desktop USB installation
2) Regular wired ethernet update and upgrade with all repositories open
3) Reboot as required
4) apt-getting the linux-backports-intrepid-generic
5) rebooting
6) rmmod ath_pci; modprobe ath5k; adding ath5k to /etc/modules
7) rebooting
8) adding the netbook remix
(each time I reboot after step 5, I also look at System>Administration>Hardware Drivers to see if the ath5k is showing up [if it does, I deactivate the original general driver and activate the ath5k rebooting as required) 

The problems are coming at step 6 and following (which I have also tried in various orders, and varying between reboots and powerdown-wait-powerup). I can't get ath5k to show up consistently at any one point in the process. This last time it hasn't shown up at all (i.e. if I sudo modprobe ath5k I get a fatal module not found error, even though my linux-backports-intrepid is up-to-date). Sometimes when it doesn't work, I give up, turn everything off--only to discover when I get back that it is working. This last time I tried powering down instead of rebooting each time, in case that was it. But to no avail. Once all I needed to do was pull the Wlan switch twice. 

I did some looking around at the modules on this last install, and note that the ath5k is there, but in an unusual place: all the other ath drivers are in /lib/modules/2.6.27-7-generic/volatile/; ath5k.ko is all by itself in /lib/modules/2.6.27-9-generic/updates/

Anybody know what the issues could be? I'm wondering if the powerdown vs. reboot issue suggests that there must be somekind of persistence in the card. But I can't figure out why sometimes ath5k modprobes fine and other times, like now seems to be uninstallable. As far as I can tell (and I'm keeping very detailed notes), I'm doing the same thing everytime.

---

### Post by 3rdalbum on 2008-12-05
Although the SD card slots are supposed to work out-of-the-box on Intrepid, I'm finding that neither of them work. Doesn't matter too much to me, I have a USB card reader that works fine.

I haven't tried the microphone.

The wireless switch is a bit of a dog on Ubuntu; Network Manager won't reconnect unless you turn the wireless on and then restart. Nothing else seems to work. Asking for a passphrase when it should know, and then still not connecting, is a quirk of Network Manager and is not specific to the Aspire One. It happens sometimes on my desktop.

I'm also finding I only get 2 hours battery life, when I was getting a reported 3 hours of battery life on Linpus. And could someone please try the Sonic The Hedgehog flash game on their One and tell me if it's meant to be slow? When playing this game I get speeds comparable to my old 333MHz iMac :-(

---

### Post by 3rdalbum on 2008-12-05
Although the SD card slots are supposed to work out-of-the-box on Intrepid, I'm finding that neither of them work. Doesn't matter too much to me, I have a USB card reader that works fine.

I haven't tried the microphone.

The wireless switch is a bit of a dog on Ubuntu; Network Manager won't reconnect unless you turn the wireless on and then restart. Nothing else seems to work. Asking for a passphrase when it should know, and then still not connecting, is a quirk of Network Manager and is not specific to the Aspire One. It happens sometimes on my desktop.

I'm also finding I only get 2 hours battery life, when I was getting a reported 3 hours of battery life on Linpus. And could someone please try the Sonic The Hedgehog flash game on their One and tell me if it's meant to be slow? When playing this game I get speeds comparable to my old 333MHz iMac :-(

---

### Post by c0da on 2008-12-05
AAO 150 Ubuntu 8.04

- the micro isn't working at all.
- right sd card slot works only with insert card while booting
- sound makes some strange noises from time to time

---

### Post by pjalegria on 2008-12-06
You can install this Kernel:

[http://www.aspireoneuser.com/forum/viewtopic.php?f=28&t=7560&st=0&sk=t&sd=a](http://www.aspireoneuser.com/forum/viewtopic.php?f=28&t=7560&st=0&sk=t&sd=a)

fully working for me...:D

---

### Post by dsm iv tr on 2008-12-06
Just confirming that the ALSA build mentioned on the ArchWiki, along with

options snd-hda-intel model=acer-aspire

in a file in modprobe.d/, makes my sound fully functional.

[ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.18a.tar.bz2](ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.18a.tar.bz2)

I had to completely disable ath5k/ath_pci and go back to ndiswrapper for the wireless, because I kept getting odd hardware reset messages. With ndiswrapper, the card works 100% for WEP and WPA, including LED status and full speed.

---

### Post by Supertoy on 2008-12-07
First of all I want to say thank you to everyone on this list.   By using all the notes here and on the wiki page I've now gotten Intrepid running successfully on an A110L (with 16GB SSD and 1.5GB RAM, latter upgraded from 1GB by me swapping in some old laptop memory; it was definitely worth the pain of opening the case to get the extra headroom...), with wireless and sound.

NOW what I want to do is get it to boot faster.  Linpus was limited but one thing it DID do was boot fast: about 15s vs about 60s for ubuntu (counting the time to get from power-off to a useful state with the desktop up).  
 
I would be useful to start discussing what can be turned off in the boot sequence to improve the boot times.   From what I've read, one boot time-waster is probing for hardware that can't possibly be there.   For example, looking at the boot logs I've noticed ubuntu probing for things like EIDE devices, and (what a surprise) not finding any.  I would be useful to look at some custom configurations for various netbooks.  Another more generic time-waster is, of course, starting unneeded services, but I *assume* that has already been reasonably optimized...

There's a tool called "bootchart" that might be useful to analyze what's going on.

The other thing I'm like to try is installing a Toshiba MK1231GAL, which is a 5m x 1.8" 120GB PATA drive.   That *should* physically fit in place of the SSD.  Anyone have any experience with that drive?

---

### Post by Shihan74 on 2008-12-07
Ok guys, i've tried to follow the instructions but with 8.10 im getting nowehere... 

for starters my xorg.conf file is blank (0 bytes long) so I cant seem to add the lines for X, secondly X is being started up as:

~$ ps -ef |grep X
root      7130  7106  0 15:57 tty9     00:00:05 /usr/X11R6/bin/X :0 -br -audit 0 -auth /var/lib/gdm/:0.Xauth -nolisten tcp vt9

which i assume has something to do with the problem... how did that happen? (/usr/X11R6/bin is just a symlink to /usr/bin but still, i cant believe this is "normal")?

---

### Post by Supertoy on 2008-12-07
Oh, and I'm using reiserfs, after having important system files mysteriously vanish on my SSD (about two reinstalls ago... and forcing one of those reinstalls.)

This is sort of in reply to the other post talking about seeing a zero-length xorg.conf file.  The SSD *could* be the problem: it's not very reliable.  With me it was important system programs in /usr/bin just vanishing!

That's the other reason I'm looking at the MK1231GAL.   I'm actually ok with only 16GB of storage but having files disappearing randomly is just too much.

On a related note: does anyone know how to do a full-system-image backup with partimage?  I've tried (using a SystemRescue CD and an external USB hard drive) but can't get it to boot after a restore.  I probably need to reinstall grub or something.   If anyone has a documented procedure that works it would be great to have in the wiki, especially as I start messing about with the boot sequence ;)

---

### Post by brucealdridge on 2008-12-08
> **malmjako said:**
> Ha! That's a good idea! It would be interesting to know how to do that.

okay, i've found out how...

```
sudo apt-get install streamer
```

then create snapshot.sh in your home directory (or where ever)

```
#!/bin/sh
streamer -o /home/user/Pictures/"$(date +%y%m%d%H%M%S)".jpeg -s 640x480

```

```
chmod +x snapshot.sh
sudo cp snapshot.sh /etc/acpi/resume.d/99-snapshot.sh
sudo nano /etc/rc.local
```

and add 
```
/home/user/snapshot.sh
```
to just before the last line (exit 0)

-bruce

---

### Post by japglish on 2008-12-08
> options snd-hda-intel model=acer-aspire

in a file in modprobe.d/, makes my sound fully functional.


Can confirm that this option (model=acer-aspire) is working with my alsa build 1.0.17 - am assuming that this is the build which came with Intrepid but since i upgraded from Hardy and had played with Alsa before, not too sure about this. Internal mike works, headphones mute front speakers properly.

I included the option in /etc/modprobe.d/aspireone and removed the model=toshiba option I had previously been using.

Also had to play around with sound settings.

The recording tab of the sound applet now has two capture devices - capture and capture 1.  Set both so that mike is muted.  In the options tab, there are now two input sources showing - the first, set to Input Source=mic, the second, input source=Front Mic.  Open up Applications>Sound and Video>Sound Recorder and make a test recording. The first recording sounded a little dodgy but subsequent recordings worked with no hassle at all.

Also managed to resolve skype settings for those who are interested, once I was sure the internal mike was working. Go to Options>Sound Devices.  Sound In I set to HDA Intel (hw:intel,0) and Sound Out to Pulse.  Test call works.

On another matter, has anybody had issues with VLC freezing intermittently during playback?  Annoying me so much, had to uninstall and install smplayer instead. Am running compiz and am guessing that it might be connected to this.  No problems with smplayer though.

---

### Post by binnian on 2008-12-08
I've installed Intrepid on 3 Aspire Ones.

On the first one I did (a couple of weeks ago), videos play fine.

On the the 2nd and 3rd, videos (mpg and wmv)
are horizontally squashed, both in stand-alone totem
and in the firefox plugin.

Anyone else having this problem?

---

### Post by Tom_T on 2008-12-10
I've just bought my acer one... not set it up yet.. but will want to install ubuntu 8.10.

Any 'simple' guides ? has the wifi / sound / mic issues been fixed ?

Many Thanks

---

### Post by solpuerto on 2008-12-10
):P   Hello first post on the forum.

I have the 8gb SSD version with Linpus which is great if you just want to run the applications on it. However I am a bit of a dabbler and liked the look of Ubuntu. I do not want to replace Linpus, well not just yet, so I have been looking at building a USB boot. I followed a lot of the advice in the Forums, and there is a lot, and eventually tried 8.1. I did get it to boot from the USB but could not get wireless to work and when I tried Terminal I could not use that as it kept asking for a password but I was never given an opportunity to create one.

I then tried 8.04.1 and as before that booted from the USB with no wireless. I upgraded through Terminal ( No password required this time?) but stopped at making the modifications to hardware and code to enable wireless, I hope.

My first question is if I make the mods to get wireless working from bootable USB will they impact on normal Linpus boot from SSD?

Second question, can I create a separate partition to boot Ubuntu from the SSD? i.e. I want to achieve a dual bootable system for Linpus and Ubuntu ideally from a menu. 

I am considering adding an SDHC card to the left slot to increase the memory possible to 24GB.

Before anybody states the obvious I have a PC with Vista, I just want to have an ultra portable with Linux on to see if I can learn more about the operating system.

Hope the above is all clear and many thanks for any response.

Great forum.

---

### Post by JohnFante on 2008-12-11
Forgive me if this has been answered before and for the long post.

I am running 8.10 and have used khaerus excellent guide to get wireless working nicely (installing backports, blacklisting ath_pci and load ath5k manually). But I have a very strange problem.

Suddenly, after a couple of the days of use with no problems, wireless stops working! It refuses to connect automaticly and when I click on the network logo to find the wireless network there is nothing there! 

Right click gives "enable networking", "enable wireless" (both enabled), "Connection information", "Edit connection" and "About". Right click (where the networks in range normally comes up) gives "wired network" greyed out "Auto eth0" (using it now), "wireless networks" greyed out, "VPN Connections", "connect to hidden wireless network" and "Create new wireless network".

When I try manually to connect to hidden wireless network it comes back and says no connection right away and no matter what I do (I also tried editing the auto wireless connection but nothing happens when I try to connect) I can't get it to find the wireless network and connect.

I have checked that the drivers are activated and rebooted several times but so far with no luck

The most strange problem is that I have had this problem two times before when I tried first eeeBuntu and the 8.10 when it was released. Both time I went back to Linpus because of this problem.

I can see that khearus have posted this tip today. 

"Note: The above solution didn't work for me. I have copied the 2.6.27-7 kernel image and the 2.6.27-7 backports-module from the Ubuntu 8.10 usbstick and installed them with dpkg -i. Reboot with kernel 2.6.27-7 and wireless worked again. To make sure the backports-module doesn't get updated the next time I put it on hold; echo "linux-backports-modules-2.6.27-7-generic hold" | dpkg --set-selections"

Since I am a ubuntu noob I am not sure how to do it. I have found "linux-backports-modules-2.6.27-7-generic_2.6.27-7.4_i386.deb" on the USB but I cant find the kernel image and how do I install them?

Big thanks in advance.

---

### Post by FountainDew on 2008-12-12
All I ever wanted was for my Aspire One to have Wireless on Ubuntu 8.10. But seeing as I'm a Linux newb and no one seems to answer these questions anymore (in the form of a guide), I'm going to switch back to Linpus Lite since wireless did work out of the box. Goodbye flashy Ubuntu. :(

---

### Post by solpuerto on 2008-12-12
> **FountainDew said:**
> All I ever wanted was for my Aspire One to have Wireless on Ubuntu 8.10. But seeing as I'm a Linux newb and no one seems to answer these questions anymore (in the form of a guide), I'm going to switch back to Linpus Lite since wireless did work out of the box. Goodbye flashy Ubuntu. :(

Hi

I know how you feel, look at my post just before yours. As you will see I managed to get 8.10 onto a USB stick and then to Boot the Aspire to run from the USB.

Because of some problems with getting access to Terminal I gave up on that version. I then tried the same with 8.04.1 and was able to access Terminal but I did not want to start making changes to the wireless set up incase I lost it through the normal Aspire system.

I found a very useful forum and I have pasted the link. 

[http://ubuntuforums.org/showthread.php?t=811397](http://ubuntuforums.org/showthread.php?t=811397)

I have a PC running XP and used that to download Unetbootin and Ubuntu-8.04.1-desktop-i386.

Unetbootin is an application that allows you to select the source where you saved your Ubuntu download on your PC and then create a diskimage onto your chosen USB drive. When you open Unetbootin it will be come clear. I used a 1GB USB that I have had for some time and it worked OK.

I hope you try the above as at least it will let you get a version of Ubuntu onto your Aspire.

Remember you need to change the boot order by pressing F2 at start up.

Very best wishes

---

### Post by FountainDew on 2008-12-12
> **solpuerto said:**
> Hi

I know how you feel, look at my post just before yours. As you will see I managed to get 8.10 onto a USB stick and then to Boot the Aspire to run from the USB.

Because of some problems with getting access to Terminal I gave up on that version. I then tried the same with 8.04.1 and was able to access Terminal but I did not want to start making changes to the wireless set up incase I lost it through the normal Aspire system.

I found a very useful forum and I have pasted the link. 

[http://ubuntuforums.org/showthread.php?t=811397](http://ubuntuforums.org/showthread.php?t=811397)

I have a PC running XP and used that to download Unetbootin and Ubuntu-8.04.1-desktop-i386.

Unetbootin is an application that allows you to select the source where you saved your Ubuntu download on your PC and then create a diskimage onto your chosen USB drive. When you open Unetbootin it will be come clear. I used a 1GB USB that I have had for some time and it worked OK.

I hope you try the above as at least it will let you get a version of Ubuntu onto your Aspire.

Remember you need to change the boot order by pressing F2 at start up.

Very best wishes

Hi, thanks for the tip. I actually already tried this, and Ubuntu is loaded off my SSD each time. My problem is that I hit the "Wireless kill switch" on my laptop and ever since then my wireless has never worked again! I don't know how to "un-kill" my wireless because theres no actual documentation on the switch other than "move switch."

[edit]
It looks like I have to boot up Linpus Lite and "un-kill" the wireless, and THEN boot up Ubuntu and NOT HIT THE SWITCH AGAIN.

---

### Post by Topsiho on 2008-12-12
The wireless kill switch is a toggle switch: moving it again will enable wireless. Until you do this you won't have wireless, whatever you try to do. Hope this will solve your problem...

Topsiho

---

### Post by Pooh22 on 2008-12-12
Hi All

I have a 150 model (1G+120GB hdd) and I installed ubuntu on a dual boot (took a bit of freaking :guitar: to get linpus to take up less space and make room for xubuntu 8.10). I managed to break the linpus install by removing firefox (due to the google toolbar issue) and subsequently removing xdesktop2 or some such package)

Anyway, back to intrepid + xfce4. I have trouble with most of the "normal" applications and xfce's configuration dialogues. They seem to be made for 768 height as a minimum and thus I get into trouble when I want to click on buttons located behind screen-bars or even further down, off screen.

Anyone else have this and found a solution?

I also tried KDE 4.2b1 and it's even less adapted to low-res screens apparently. I hope this will improve quickly...

Cheers

Simon

PS, I followed some more instructions from the community page and now my screen is a lot better (smaller, harder to read, but more space available)

---

### Post by solpuerto on 2008-12-13
> **FountainDew said:**
> Hi, thanks for the tip. I actually already tried this, and Ubuntu is loaded off my SSD each time. My problem is that I hit the "Wireless kill switch" on my laptop and ever since then my wireless has never worked again! I don't know how to "un-kill" my wireless because theres no actual documentation on the switch other than "move switch."

[edit]
It looks like I have to boot up Linpus Lite and "un-kill" the wireless, and THEN boot up Ubuntu and NOT HIT THE SWITCH AGAIN.

Hi again

I assume you used Unetbootin direct on the Aspire. The method I used was using the Netbootin on my Windows PC and create the Boot USB there. It sounds like you chose to install direct onto the Aspire and also the SSD.

As I understand Ubuntu disables the Wireless Switch unless you do some coding in Terminal. I should also have given you the following link that explains what needs to be done. I have not tried this as I was concerned how it may effect the use of Linpus, bearing in mind I was running Ubuntu from the USB stick and did not at this stage wish to loose Linpus.

[https://help.ubuntu.com/community/AspireOne](https://help.ubuntu.com/community/AspireOne)

If you have Ubuntu on the SSD you may wish to try this before restoring Linpus.

Hope you keep us informed of your progress.

Best wishes

---

### Post by chris.h on 2008-12-13
I got pretty much everything workin on my AOA (haven't tried the mic or SD slots, webcam works in luvcview but not cheese) but does anyone know of a way to have it suspend when the lid closes and wake when it opens back up?

From what I can tell hibernate is sketchy?

I have my power settings set to suspend when the lid is closed for AC and Battery power.



Other notes: my wifi works using ath5, 1 finger scrolling and tapping the bottom right for right clicking worked out of the box, my sound worked out of the box, I just had to switch the control from master to PCM so it would control the volume regardless of having my headphones connected or not, my wifi still works after suspend, my webcam works for luvcview but not cheese and i have the "clone" "true" option set, haven't tested the mic, and haven't tested either SD slot yet. I don't really use sd cards much...

Anyone know how to get suspending on lid close or the webcam to work in cheese? oh, also my youtube can be a lil jumpy, my only power settings in /etc/local.rc are two lines supposed to "decrease power usage of usb device while idle" that i got from the wiki.

wow, i ramble.

edit:
i tested a 4 gb microSD with an adapter and that worked in both slots as did a 512 card from my camera. (512, i know!)

---

### Post by gusman21 on 2008-12-14
> **JohnFante said:**
> Forgive me if this has been answered before and for the long post.

I am running 8.10 and have used khaerus excellent guide to get wireless working nicely (installing backports, blacklisting ath_pci and load ath5k manually). But I have a very strange problem.

Suddenly, after a couple of the days of use with no problems, wireless stops working! It refuses to connect automaticly and when I click on the network logo to find the wireless network there is nothing there! 

Right click gives "enable networking", "enable wireless" (both enabled), "Connection information", "Edit connection" and "About". Right click (where the networks in range normally comes up) gives "wired network" greyed out "Auto eth0" (using it now), "wireless networks" greyed out, "VPN Connections", "connect to hidden wireless network" and "Create new wireless network".

When I try manually to connect to hidden wireless network it comes back and says no connection right away and no matter what I do (I also tried editing the auto wireless connection but nothing happens when I try to connect) I can't get it to find the wireless network and connect.

I have checked that the drivers are activated and rebooted several times but so far with no luck

The most strange problem is that I have had this problem two times before when I tried first eeeBuntu and the 8.10 when it was released. Both time I went back to Linpus because of this problem.

I can see that khearus have posted this tip today. 

"Note: The above solution didn't work for me. I have copied the 2.6.27-7 kernel image and the 2.6.27-7 backports-module from the Ubuntu 8.10 usbstick and installed them with dpkg -i. Reboot with kernel 2.6.27-7 and wireless worked again. To make sure the backports-module doesn't get updated the next time I put it on hold; echo "linux-backports-modules-2.6.27-7-generic hold" | dpkg --set-selections"

Since I am a ubuntu noob I am not sure how to do it. I have found "linux-backports-modules-2.6.27-7-generic_2.6.27-7.4_i386.deb" on the USB but I cant find the kernel image and how do I install them?

Big thanks in advance.

Go to a wired connection and do the following:
```

sudo apt-get install linux-backports-modules-intrepid

```

should bring the wireless back.

---

### Post by JohnFante on 2008-12-14
Thank you for the reply.

I allready have the latest linux-backports-modules-intrepid installed. :-(

---

### Post by christian.paratschek on 2008-12-15
Which repositories do you use? If you enabled proposed updates and backports, you might encounter problems, because these are not that well tested (there's a reason why they call it "proposed"). 

Just run with the standard install and your wireless should be ok. Mine never broke in the last weeks, it just works...

---

### Post by xltrigger on 2008-12-15
For those having problems with WiFi. I have been fighting with mine since I got my Aspire One a few days ago. I wanted 8.10 installed on it. WiFi would not work. Following the backport instructions showed the adapter as present, but no networks would be detected. I updated the bios to 3309 that I got from here: [http://macles.blogspot.com/2008/12/acer-aspire-one-bios-3309.html](http://macles.blogspot.com/2008/12/acer-aspire-one-bios-3309.html)

I had bios 3305 when I received it. If anybody needs help updating the bios pm me. I can walk you through it. You have to make a freedos usb boot disk and place the bios update in a folder on the thumb drive and boot off of it. 

I have fully tested everything, but it at least sees wireless networks now. I post again after I get to test it more.

---

### Post by chris.h on 2008-12-15
hey, just wondering if anyone noticed anything magically becoming fixed with the pulseaudio updates today?

also, for the people with wireless coming in and out (not me) has anyone tried wicd?

---

### Post by darkwalt on 2008-12-16
> **JohnFante said:**
> Thank you for the reply.

I allready have the latest linux-backports-modules-intrepid installed. :-(

Well what I did is I updated,
```

sudo aptitude update

sudo aptitude safe-upgrade

``` then went to synaptic package manager, settings -> repositories -> updates and selected unsupported updates,  It says backports on it.  Then I ran the backports command.

```

sudo aptitude install linux-backports-modules-intrepid

```
  Also, remember in Administration -> Hardware Drivers to disable the default driver.  It should say "Support for Atheros 802.11 wireless LAN cards."  If there is another one listed, enable that one.  It should work after a reboot.

---

### Post by brucealdridge on 2008-12-16
just ran the latest batch of updates today, required a restart ... and wireless broke.

:(

---

### Post by chris.h on 2008-12-16
> **brucealdridge said:**
> just ran the latest batch of updates today, required a restart ... and wireless broke.

:(

what drivers are you using!?  

the updates work for me using ath5k.

---

### Post by brucealdridge on 2008-12-16
> **chris.h said:**
> what drivers are you using!?  

the updates work for me using ath5k.

sorry,
ignore me... wireless going down at work happened to coincide perfectly with my restart.

works now

---

### Post by darkwalt on 2008-12-16
Wow.  Had me a bit worried there.  I was in the middle of updating.

---

### Post by gmc on 2008-12-16
> **chris.h said:**
> hey, just wondering if anyone noticed anything magically becoming fixed with the pulseaudio updates today?

also, for the people with wireless coming in and out (not me) has anyone tried wicd?

Yes, I upgraded to Wicd. It works very well but for me it has the side effect of hanging the machine (flashing capslock crash) during moderate to heavy traffic over the wireless. This occured periodically under Network Manager so I know it's a machine/wireless problem and not Wicd.

I flashed the Bios to 3309 and am going to see if the problem still occurs later today.

G.

---

### Post by gaspodog on 2008-12-17
I've managed to get pretty much everything working on my Aspire One (160GB HD, 512MB RAM), but one thing that's still bugging me is the HD load cycling. On battery, it's been cycling around 100-120 times per hour, which is not filling me with confidence that this drive is going to last very long.

I've hunted around, looking at the bug reports on the subject, and came across the [PowerManagement]("https://wiki.ubuntu.com/PowerManagement") page on the Ubuntu wiki, which suggests that all you need to do in Intrepid is set the LAPTOP_MODE to true on battery in /etc/default/acpi-support

After doing that, I find that the HD spins down completely after 5-10 seconds of inactivity. It then spins up again straight away as the system wants the disc again, or I change workspace or do something in a file. This causes the load cycling to occur about 10 times per minute under normal (browsing, IRC etc) usage, which is much worse than before.

I tried setting the apm to 254 in hdparm, as per another tutorial I found, but that resulted in a slightly better situation, but still worse than initially with laptop mode off.

Does anybody know of a fix for this? I've come across various approaches on the bug report pages, but it's not entirely clear what I should do with 8.10, since the issue seems to be regarded as fixed by some people and not by others. I don't know if I'm being paranoid, but I'd quite like my HD to have a decent lifespan without me having to use the laptop on AC power the whole time to avoid load cycling.

---

### Post by figvam on 2008-12-19
> **chris.h said:**
> also, for the people with wireless coming in and out (not me) has anyone tried wicd?

I'm using wicd, it works a bit better than NetworkManager, though it's hard to say because of other apparent driver-related problems with WiFi.

> **gmc said:**
> Yes, I upgraded to Wicd. It works very well but for me it has the side effect of hanging the machine (flashing capslock crash) during moderate to heavy traffic over the wireless. This occured periodically under Network Manager so I know it's a machine/wireless problem and not Wicd.It's not because of wicd, it's a kernel panic most likely related to ath5k. I'm getting it when the traffic is heavy, too. In fact I'm considering using ndiswrapper as it seems to be the only flawlessly working solution for wireless on Aspire One.

---

### Post by doogiekd on 2008-12-19
Hi Friends, 

I have just purchased the Acer Aspire One hard drive version with windows XP installed. Currently, all of my PC's are using Ubuntu.

I would like to make my new AAO a dual boot machine.

The question: Will installing Ubuntu erase the XP installation?

Also, I am concerned about the post regarding the always on hard drive - anyone have an answer for that?

Thanks, 

doogie

---

### Post by RockDoctor on 2008-12-19
> **doogiekd said:**
> 
The question: Will installing Ubuntu erase the XP installation?

Only if you tell it to. My AA1 also came with WinXP. I kept the recovery partition, reduced the WinXP partition to 20GB, then created a 100 MB common Boot partition and a bunch of 8GB partitions for each distro/variant. The Boot partition is always mounted at /boot. No problems with one install clobbering anything on the HD, but I do update the common /boot/grub/menu.lst file manually.

Haven't tried messing with the HD and power-saving.

---

### Post by chris.h on 2008-12-19
Word of caution, the current proposed 2.6.27.11 kernel disables wifi (ath5). it can probably just be re set up but I'm too lazy to care.

---

### Post by Aearenda on 2008-12-19
> 
I've hunted around, looking at the bug reports on the subject, and came across the PowerManagement page on the Ubuntu wiki, which suggests that all you need to do in Intrepid is set the LAPTOP_MODE to true on battery in /etc/default/acpi-support

After doing that, I find that the HD spins down completely after 5-10 seconds of inactivity. It then spins up again straight away as the system wants the disc again, or I change workspace or do something in a file. This causes the load cycling to occur about 10 times per minute under normal (browsing, IRC etc) usage, which is much worse than before.

I tried setting the apm to 254 in hdparm, as per another tutorial I found, but that resulted in a slightly better situation, but still worse than initially with laptop mode off.

I don't have 8.10 on my AA1 yet, but on my other laptop with 8.10 I found that to prevent the hard drive problem, I had to set LAPTOP_MODE true as described, but also modify /etc/laptop-mode/laptop-mode.conf. This is necessary because by default laptop-mode only prevents the problem when on AC power, not when on battery. The relevant section is:```

#
# Should laptop mode tools control the hard drive idle timeout settings?
#
CONTROL_HD_IDLE_TIMEOUT=1
#
# Idle timeout values. (hdparm -S)
# Default is 2 hours on AC (NOLM_HD_IDLE_TIMEOUT_SECONDS=7200) and 20 seconds
# for battery and for AC with laptop mode on.
# 
LM_AC_HD_IDLE_TIMEOUT_SECONDS=60
LM_BATT_HD_IDLE_TIMEOUT_SECONDS=60
NOLM_HD_IDLE_TIMEOUT_SECONDS=7200


#
# Should laptop mode tools control the hard drive power management settings?
#
CONTROL_HD_POWERMGMT=1
#
# Power management for HD (hdparm -B values)
# That is, control it so as to disable it!
BATT_HD_POWERMGMT=254
LM_AC_HD_POWERMGMT=254
NOLM_AC_HD_POWERMGMT=254

```

Just setting it using hdparm won't stick. The logic used to determine the default behaviour favours protecting the drive when on battery, and the computer is more likely to be dropped then. I don't agree, which is why I disable the parking bahaviour always, and use the standby timeout to save power, which IS what I want when on battery.

The settings for hdparm -B are hardware-dependant. For my laptop drive (Hitachi) I found the manufacturers details and worked from there. I offer this as a guide, but it may not have the desired effect for you - I encourage you to do the research for your drive and choose accordingly.

---

### Post by capdog on 2008-12-20
Hi everyone, I managed to get 99% working using this thread and the wiki info! The only problem I'm having is with the ath5k driver. It works, but the signal is weak and if I run 

 sudo tail -f /var/log/syslog

I get the following every few minutes:

Dec 20 20:07:58 mark-netbook NetworkManager: <debug> [1229803678.234259] periodic_update(): Roamed from BSSID (none) ((none)) to 00:18:4D:F8:B7:C0 (SKY20685)

It's basically dropping the connection as far as I can tell, and re-connecting.

I'm thinking of trying out the ndiswrapper driver because apparently it works... any idea otherwise?

- [EDIT] 

I have installed the ndiswrapper as per the Aspire One Ubuntu docs, and now the wireless LED works, I get full signal and there are no more disconnects!

I think the ath5k driver is still a bit buggy, but it will probably move on and improve quickly.

---

### Post by the-madman on 2008-12-23
Hi all, is it just me?
After the last update session in the last days (something with a partial upgrade and it looked like a new kernel version) my AAO110 is not going back to the wired lan anymore. 

All I can see is that auto eth0 is not ticked.
Is this related to the latest update did they remove the driver?

Andreas

---

### Post by solpuerto on 2008-12-24
> **doogiekd said:**
> Hi Friends, 

I have just purchased the Acer Aspire One hard drive version with windows XP installed. Currently, all of my PC's are using Ubuntu.

I would like to make my new AAO a dual boot machine.

The question: Will installing Ubuntu erase the XP installation?

Also, I am concerned about the post regarding the always on hard drive - anyone have an answer for that?

Thanks, 

doogie

Hi doogie

I installed Ubuntu 8.10 on my XP desktop by downloading the ISO from the Ubuntu site and then running it. It will do some repartitioning of your HDD but the KEY thing is when it gets to the Prepare Disk Space screen use Guided Resize xxxx drive. This will give you the ability to adjust the size of the partition you want to create for Ubuntu. It is pretty fail safe on the basis that you can adjust the partitioning to what you want but it will not actually do it until you say you are sure.
The other point to mention, it automatically sets up a Dual Boot screen that will default to Ubuntu after a period of time but gives you an option to select Windows XP.
I am no techie but I found it pretty straight forward.

As is always said BACK UP FIRST

Best wishes

---

### Post by Mattia on 2008-12-24
> **the-madman said:**
> Hi all, is it just me?
After the last update session in the last days (something with a partial upgrade and it looked like a new kernel version) my AAO110 is not going back to the wired lan anymore. 

All I can see is that auto eth0 is not ticked.
Is this related to the latest update did they remove the driver?

Andreas

Hi, i've the same problem. Have you solved?

---

### Post by grandmaster on 2008-12-26
Without stating the obvious :) is there any way to tell what state my aao wireless switch is at, because the lights dont work..

My wireless was working but since a reboot its not. but i would love to know what status the switch is..

thanks

GM

---

### Post by grandmaster on 2008-12-26
My wireless is backup after I set my bios back to defaults coincidence? I dont know but it works now.. I still would love to how to determin the status of my wifi kill switch though..

GM

---

### Post by brucealdridge on 2008-12-29
anyone else having webcam issues?
i've only just noticed....
it used to spit out 640x480 fine
but now it can only do 160x120

i've managed to trace it back to 
sometime between Dec 10 & Dec 11

is there anyway to find out what caused the problem?
note: i can't check log files as they're just stored on a ramdisk

-bruce

---

### Post by darkwalt on 2008-12-29
Yeah, around that same timeframe cheese stopped working for me.  Everything works but cheese.

---

### Post by the-madman on 2008-12-29
> **Mattia said:**
>  Re: Intrepid on a Acer Aspire One
Quote:
Originally Posted by the-madman View Post
Hi all, is it just me?
After the last update session in the last days (something with a partial upgrade and it looked like a new kernel version) my AAO110 is not going back to the wired lan anymore.

All I can see is that auto eth0 is not ticked.
Is this related to the latest update did they remove the driver?

Andreas
Hi, i've the same problem. Have you solved?

Works now for me.
But I dont really know the full solution so those steps I did.

1. I reinstalled the gnome network manager package
2. updated to the BIOS 3309 [http://macles.blogspot.com/2008/12/acer-aspire-one-bios-3309.html](http://macles.blogspot.com/2008/12/acer-aspire-one-bios-3309.html)
3. went into the BIOS and reset all to default (in fact there was no visible change to the original values but just for joy I did it)
4. boot up the ubuntu and went into the network config (right click on network  manager and network connections) and (for any reason it dissapeard) reenabled in the auto eth0 interface the "connect automatically". whups after another reboot it worked again.
Andreas

---

### Post by Mattia on 2008-12-31
> **the-madman said:**
> Works now for me.
But I dont really know the full solution so those steps I did.

1. I reinstalled the gnome network manager package
2. updated to the BIOS 3309 [http://macles.blogspot.com/2008/12/acer-aspire-one-bios-3309.html](http://macles.blogspot.com/2008/12/acer-aspire-one-bios-3309.html)
3. went into the BIOS and reset all to default (in fact there was no visible change to the original values but just for joy I did it)
4. boot up the ubuntu and went into the network config (right click on network  manager and network connections) and (for any reason it dissapeard) reenabled in the auto eth0 interface the "connect automatically". whups after another reboot it worked again.
Andreas

Thanks, but i've the aa1 110 and 3309 is fo for 150.

---

### Post by solpuerto on 2009-01-01
I have Ubuntu 8.10 booting and running from a USB stick on my Aspireone. At present this suits me fine but I notice other posters are also booting from USB.
Can anyone tell me if it is possible to get rid of the multi language screen that displays at the start of the boot and last for 30 seconds. Is this something you have to live with on a USB boot?

I also have Ubuntu installed on a desktop PC and the language screen does not appear at boot

Many thanks for any advice.

---

### Post by trazalca on 2009-01-03
All is going on on my 150, but i need info about multitouch, with xp driver i can scroll with two finger, can i do the same with ubuntu?? Someone can tell me how? Thanks in advance.

---

### Post by darkwalt on 2009-01-04
> **trazalca said:**
> All is going on on my 150, but i need info about multitouch, with xp driver i can scroll with two finger, can i do the same with ubuntu?? Someone can tell me how? Thanks in advance.


I think that standard the right side of the pad is scroll, and if you tap the bottom right corner you the right click menu.  As for two finger scroll I have no clue.

---

### Post by damoisture on 2009-01-05
This is going to be a long post, as I have finally given this thread a thorough read in my quest to perfect my Xubuntu install on my AAO. I have had no wireless problems after following the instructions posted on the community wiki page.

However, I would definitely like this puppy to boot faster. While reading this thread, I came upon this:
> **christian.paratschek said:**
> 1. About the elevator=noop option in /boot/grub/menu.lst

I have read in the now closed development thread the following:
> I just wanna share one more tweak that i have done to my aspire one. Adding "elevator=deadline loglevel=1 console=tty1 nolapic_timer" to the kernel line in /boot/grub/menu.lst made my system a lot more responsiveness.
I got these options from the menu.lst that cames with Linpus.
What experiences did you make? What should we recommend?
What is the consensus on this? Valid suggestion? Also, it seems like Supertoy has some similar ideas:
> **Supertoy said:**
> ...NOW what I want to do is get it to boot faster.  Linpus was limited but one thing it DID do was boot fast: about 15s vs about 60s for ubuntu (counting the time to get from power-off to a useful state with the desktop up).  
 
I would be useful to start discussing what can be turned off in the boot sequence to improve the boot times.   From what I've read, one boot time-waster is probing for hardware that can't possibly be there.   For example, looking at the boot logs I've noticed ubuntu probing for things like EIDE devices, and (what a surprise) not finding any.  I would be useful to look at some custom configurations for various netbooks.  Another more generic time-waster is, of course, starting unneeded services, but I *assume* that has already been reasonably optimized...

There's a tool called "bootchart" that might be useful to analyze what's going on...
I can concur with his ~60s boot times which is a few seconds slower than when I boot into XP Home. Anybody have a fast ubuntu boot?

Also, I was having some problems with the card readers, until I came across this post:
> **christian.paratschek said:**
> 3. Regarding the SD-Cards:

Do we still need "options pciehp pciehp_force=1"? It works for me without this!
Thank you so much for posting this! I've been pulling my hair out for the last few days trying to get my right card reader to work. Deleting those three params, leaving just the one line, worked fairly well for me; the right card reader works and hot-swaps SD cards just fine.

However, I still cannot get the right card reader to read xD picture cards! Has anyone had any luck with this?

---

### Post by birkenkrahe on 2009-01-07
hi i hope this is the right thread for my problem: 

i am running ubuntu 8.10 on an acer aspire one 150 (1.6 GHZ, 120 GB) model; no problems whatsoever (apart from WLAN issues which i was able to sort out with madwifi) until i connected the notebook to an external monitor and connected a USB mouse. 

i received a system message at that point to reset the virtual resolution (or something) and reboot after which the monitor image was fine.

as i was disconnecting the monitor and the USB mouse this morning, i noticed that the touchpad & mouse keys on the acer were not responding anymore at all. i can login of course in pure-terminal mode, but i cannot figure out how to re-attach the touchpad (which i presume is still working OK).

my assumption is that the xorg.conf file somehow got corrupted in the course of the two interventions (ext monitor / USB mouse) - but then i read that the X11 controls were changed completely with 8.10 ... and i am out of my depth.

QUESTIONS: 

(1) any hints how i can proceed trying to identify the error and solve it (ie get the touchpad working again)?

(2) aby idea how i can operate the acer WITHOUT the touchpad and WITHOUT a mouse - ie e.g. how i can access the panel applications (or any applications apart from F1 = help)?

thanks in advance!

---

### Post by Koterpillar on 2009-01-08
> **birkenkrahe said:**
> (1) any hints how i can proceed trying to identify the error and solve it (ie get the touchpad working again)?
Have you tried Fn+F7?

> **birkenkrahe said:**
> (2) any idea how i can operate the acer WITHOUT the touchpad and WITHOUT a mouse - ie e.g. how i can access the panel applications (or any applications apart from F1 = help)?
Alt+F1 = system menu, Alt+F2 = Run dialog. From Run, gnome-terminal, konsole or xterm take you to the sweetest of *nix things - the console. From there, you can do everything.

---

### Post by rhy on 2009-01-14
This may seem obvious, but for anyone stuck with getting the madwifi driver to work, try changing Wicd preferences. 

I just installed the madwifi driver as per [https://help.ubuntu.com/community/AspireOne](https://help.ubuntu.com/community/AspireOne) as the ath5k driver was causing dropouts. 

Nothing worked until I changed the settings in Wicd --> Preferences --> wireless interface to ath0

Once I did that, networks detected and the traffic led started blinking when connected. Association led doesn't seem to be working yet.

---

### Post by Aearenda on 2009-01-15
Anyone using intrepid-proposed updates, note that kernel 2.6.27-11-generic presently fails to load the realtek driver for the wired interface in the AA1. 2.6.27-10-generic is ok. It's [bug 313866]("https://bugs.launchpad.net/ubuntu/+bug/313866") in Launchpad.

---

### Post by capdog on 2009-01-18
My wireless stopped working after I used the killswitch. Couldn't bring it back up again. Using ndiswrapper.

Removed Ubuntu and put on WinXP. I just can't afford to have shaky wireless when out on the road, travelling. I've tried all the wifi options and they all had different issues.

---

### Post by gsuveg on 2009-01-23
hi,

its a solution to fix if i plug in headphone to off the speaker ??
now with latest intrepid kernel ist works not :(
and soo funny on a train, everybody hear what i listen :D

thanks
G.

---

### Post by teaker1s on 2009-01-24
running acer model line and latest updates, internal,external mike works by switching in volume control.

my bug is that if audio is started with headphones connected it mutes speakers, if unplugged and replugged in it doesn't mute.

Anyone with clicking hdd 160gb model-acer and Western Digital are informed by me, it's a hdd firmware bug causing excessive load count.

Will post back as and when they suggest a solution

---

### Post by gsuveg on 2009-01-24
> **teaker1s said:**
> running acer model line and latest updates, internal,external mike works by switching in volume control.

my bug is that if audio is started with headphones connected it mutes speakers, if unplugged and replugged in it doesn't mute.

sorry, i havent radio button in volume control :( and dont mute.
ive lastest kernel and gnome, and modell=acer in modconf.d/options file.

i need see maybe if i boot witl headphone maybe mute the speaker ?

---

### Post by teaker1s on 2009-01-24
* Open /etc/modprobe.d/alsa-base with the following command: 

```
sudo nano /etc/modprobe.d/alsa-base
```

Then paste the following line at the end of the file (change MODEL with the type of sound card's model, in our example it should be "acer" (without quotation marks)):

```
options snd-hda-intel model=acer
```

save file 
    * Reboot

This is all I have done to have both external and internal mic working and headphones

---

### Post by gsuveg on 2009-01-24
> **teaker1s said:**
> 

```
sudo nano /etc/modprobe.d/alsa-base
```
```
options snd-hda-intel model=acer
```

This is all I have done to have both external and internal mic working and headphones

i realy sorry in alsa-base file im setup it before. and headphone dont switch off my speaker :(

kernel 2.6.27-9.

---

### Post by pjalegria on 2009-01-24
Maybe this can help for...

[http://www.ubuntuaone.com/content/slckb0ykuki-kernel-2628-v02-acer-aspire-oneundervolt](http://www.ubuntuaone.com/content/slckb0ykuki-kernel-2628-v02-acer-aspire-oneundervolt)

---

### Post by gsuveg on 2009-01-26
the wifi card is kill me :(
now come now with cant reset hardware bug :( ive realy bad moood :(
what can i do ? soundcard (headphone / speaker) and wifi (come the cant reset hw bug) dont works :( :(
intrepid with fresh upgrade, backposts and no 'extra' packages from source...

---

### Post by gusman21 on 2009-01-26
> **pjalegria said:**
> Maybe this can help for...

[http://www.ubuntuaone.com/content/slckb0ykuki-kernel-2628-v02-acer-aspire-oneundervolt](http://www.ubuntuaone.com/content/slckb0ykuki-kernel-2628-v02-acer-aspire-oneundervolt)

I wanna use sickboy, but kernel does not support /home on left media reader.

---

### Post by pjalegria on 2009-01-27
Yes it does, i have HOME at my SDHC 8GB on my left card reader....with resume/suspend also working :D

---

### Post by gusman21 on 2009-01-27
> **pjalegria said:**
> Yes it does, i have HOME at my SDHC 8GB on my left card reader....with resume/suspend also working :D


I downloaded and sudo dpkg -i --force-architecture kernel and sudo dpkg -i headers. setup my links.  rebooted and selected sickboy.  logged in at GDM and it said no /home.  dropped to tty1 and mount showed no device at mmkblk01 (or whatever the device is). it is in fstab to mount as uuid.

EDIT:
removed and reinserted card and dmesg:
```

mmc0: error -84 whilst initialising SD card

```

added the following to /etc/modprobe.d/aspireone
```

options sdhci debug_quirks=1

```
from: [https://kerneltrap.org/mailarchive/linux-kernel/2008/10/27/3820014](https://kerneltrap.org/mailarchive/linux-kernel/2008/10/27/3820014)

Update: Fixed by adding [https://kerneltrap.org/mailarchive/linux-kernel/2008/10/27/3820014](https://kerneltrap.org/mailarchive/linux-kernel/2008/10/27/3820014)

---

### Post by darkwalt on 2009-01-29
Ok.  Something weird just happened.  My networking just completely ceased to function.  Wireless and wired.  If I do an iwconfig, it shows that the wireless card is there, but it is not transmitting anything.  It does not show anything for the wired network.  Any ideas?

---

### Post by drlmg on 2009-01-29
I had Intrepid working on my AAO then it slowly began to mess up. I would repair everything and with updating things here and there began messing up all over again. The wireless would work sporadically. I went through the forums and tried everything I could to no avail. I eventually ended up re-formatting and re-installing 8.04 LTS and followed the directions here... [https://help.ubuntu.com/community/AspireOne#Install%20Ubuntu%20Hardy%20Heron%20(8.04.1)%20on%20the%20Acer%20Aspire%20One]("https://help.ubuntu.com/community/AspireOne#Install%20Ubuntu%20Hardy%20Heron%20(8.04.1)%20on%20the%20Acer%20Aspire%20One") and got everything working again. **BEWARE UPDATING**.... today (01_29_09) there is an update (I don't know which one yet) that has totally crashed it TWO times. I get a message **'kernel panic - not syncing - attempted to kill init'**. Afterwards I cannot boot, even recovery mode will not boot. I am now in the process of re-installing for the 2nd time today.

---

### Post by drlmg on 2009-01-29
After re-installing twice I have found what caused my two laptops to crash. It is one or all of the following updates..

[B]linux headers 2.6.24-23

linux headers 2.6.24-23-generic

linux-image-2.6.24-23-generic[/B]

All have to do with the Linux kernel.

When I re-installed for the second time I updated everything except these updates and it re-booted fine.

---

### Post by darkwalt on 2009-01-29
Ok, wireless started working by itself.  Might of been the wireless switch.  Someone needs to figure out the code for the wifi lights.  However, wired networking on mine still isnt working.

---

### Post by leifoelgaard on 2009-01-29
One way to get around the kernel problem is by using SICKBOY's kernel fr KUKI Linux (based on Ubuntu) - It's just amazing! :D

It ust works. There's a "How-to" on [www.kuki.me](www.kuki.me).

God Luck

---

### Post by stchman on 2009-01-29
I have a tutorial to get Intrepid working on the Acer Aspire One.

I have a script that installs the wireless using the madwifi drivers.

[http://www.stchman.com/aspire_one_intrepid.html](http://www.stchman.com/aspire_one_intrepid.html)

---

### Post by gusman21 on 2009-01-29
> **leifoelgaard said:**
> One way to get around the kernel problem is by using SICKBOY's kernel fr KUKI Linux (based on Ubuntu) - It's just amazing! :D

It ust works. There's a "How-to" on [www.kuki.me](www.kuki.me).

God Luck

seconded. very nice kernel. works VERY well.

---

### Post by anjilslaire on 2009-01-29
> **stchman said:**
> I have a tutorial to get Intrepid working on the Acer Aspire One.

I have a script that installs the wireless using the madwifi drivers.

[http://www.stchman.com/aspire_one_intrepid.html](http://www.stchman.com/aspire_one_intrepid.html)

Thanks :)

---

### Post by anjilslaire on 2009-01-30
Boot into 2.6.27.7 

Wired comes back.

---

### Post by MadEgg on 2009-02-01
> **gusman21 said:**
> seconded. very nice kernel. works VERY well.


Thirded (;-)),. I just installed this kernel on an Acer Aspire One 150 with 120 GB HD and finally both card readers work, wifi-led works, standby/resume works. Great kernel!

---

### Post by LunatikBUnnie on 2009-02-01
> **MadEgg said:**
> Thirded (;-)),. I just installed this kernel on an Acer Aspire One 150 with 120 GB HD and finally both card readers work, wifi-led works, standby/resume works. Great kernel!

Wait... how do you install it? O_o
All i have is the ISO image

---

### Post by theApokalypsis on 2009-02-01
Saw this had some action, if no one posted yet here is the wiki link.

[https://help.ubuntu.com/community/AspireOne#Install%20Ubuntu%20Intrepid%20Ibex%208.10%20on%20the%20Acer%20Aspire%20One]("https://help.ubuntu.com/community/AspireOne#Install%20Ubuntu%20Intrepid%20Ibex%208.10%20on%20the%20Acer%20Aspire%20One")


Also, check out the Moblin distro being developed for Atom based netbooks. its in alpha right now but it boots damn fast.

---

### Post by anjilslaire on 2009-02-01
Yes, I've looked at that, but used this to get the madwifi drivers going. Works great!:

[http://www.stchman.com/aspire_one_intrepid.html](http://www.stchman.com/aspire_one_intrepid.html)

---

### Post by Pooh22 on 2009-02-02
Hi

I'm running ubuntu on my A150 and after the updates today, I don't have wired working (until I rebooted with the previous kernel 2.6.27-9). I figure the update broke my wired interface driver in 2.6.27-11 kernel.

A symptom seems to be that I get continuous notices from pciehp about a Card being present in Slot(1) and then immediately that it's not present.

I've no idea whether this is related, but it might be if the ethernet card is connected through a PCI-e interface...

Can anyone confirm this?

Cheers

Simon

---

### Post by kevh on 2009-02-02
Yes, I have noticed the same problem. Wireless still working ok but getting about pairs of error messages per second stating "kernel: [18689.916972] pciehp: Card present on Slot(1)" followed by "kernel: [18689.965259] pciehp: Card not present on Slot(1)"

---

### Post by kevh on 2009-02-02
Sorry should have read:
Yes, I have noticed the same problem. Ethernet no longer working but wireless still working ok and getting about 15 pairs of error messages per second stating "kernel: [18689.916972] pciehp: Card present on Slot(1)" followed by "kernel: [18689.965259] pciehp: Card not present on Slot(1)"

---

### Post by kevh on 2009-02-02
Hello Pooh22,
Just found this, tried it and it solved the problem. Both card readers still working.
Kevh



[http://ubuntuforums.org/showthread.php?t=974525&highlight=pciehp]("http://ubuntuforums.org/showthread.php?t=974525&highlight=pciehp")

---

### Post by Pooh22 on 2009-02-02
Thanks for the link, but I´m not sure this is what causes my problems...

I noticed (no I'm not reading the kernel mailinglist every day ;-) that 2.6.27.14 fixes something related to pciehp:

[INDENT]Jiri Slaby (2):
      **PCI hotplug: fix lock imbalance in pciehp**
      relay: fix lock imbalance in relay_late_setup_files[/INDENT]

So it might be fixed soon if an update of the kernel is passed downstream via the ubuntu updates...

Meanwhile, I'll keep using the previous kernel

Cheers

Simon

---

### Post by dmfrey on 2009-02-02
i am having an issue with the fan on my acer aspire one using intrepid.  The bios was recently updated to 3309 and now the fan does not run constantly like it did under 3304.  However, about every 3 seconds the fan spins up and then spins down.  It kind of sounds like revving an engine.  Anyone else experience this and, if so, how did you fix it?

Thanks.

---

### Post by darkwalt on 2009-02-02
Ok, so installing the kuki kernel fixed all of my networking problems.  Did a full reinstall just to try it out.  Yes, I know that I didn't have to, but I wanted to see what it would do.  All it did for me was automatically install the wireless drivers.  Everything else in the aspire one install guide I had to do, including the code for getting both card readers to work and become hot-pluggable.  Also, @dmfrey, did you mean 3305?  I would try re-flashing the bios.  Use a different usb stick if you have one, or format the one you used.

---

### Post by dmfrey on 2009-02-02
> **darkwalt said:**
> Also, @dmfrey, did you mean 3305?  I would try re-flashing the bios.  Use a different usb stick if you have one, or format the one you used.

Darkwalt, 3309 is available as of January 9th or 19th (I forget which one).

---

### Post by darkwalt on 2009-02-02
> **dmfrey said:**
> Darkwalt, 3309 is available as of January 9th or 19th (I forget which one).

Really?  Where did you get it from?  The site I usually get mine from is 
[http://www.aspireoneuser.com/~staukcla/upload/microfile.php?path=./AA1_BIOS](http://www.aspireoneuser.com/~staukcla/upload/microfile.php?path=./AA1_BIOS)

---

### Post by doug1212 on 2009-02-03
Acer Aspire One 110 BIOS:

[HTML]ftp://ftp.acer-euro.com/netbook/aspire_one_110/bios/[/HTML]

---

### Post by darkwalt on 2009-02-03
Hm, well that's odd.  I see 3308 and 3309 on there, both of which aren't on the official acer "aspireoneuser.com" website.  Not to be condescending, but did you do the fan control part of the install guide?

[html]https://help.ubuntu.com/community/AspireOne110L#Fan%20Control[/html]

---

### Post by doug1212 on 2009-02-03
On the M/C I have the acerfan control script did not work properly with the later bios (not sure if it has been tweaked since) so I omitted it.
At idle it spins constantly very slowly but is very quiet.
Doug.

---

### Post by darkwalt on 2009-02-03
Hm.  Well i'll make a note to stay away from that firmware.  I would suggest flashing it back to the previous version of the bios then.  I remember when I first got my A1 that would happen until I installed the acerfand script, or when I got a kernel update.  Did you try using a sickboy kernel to see if that fixed it?

---

### Post by dmfrey on 2009-02-03
> **doug1212 said:**
> Acer Aspire One 110 BIOS:

[HTML]ftp://ftp.acer-euro.com/netbook/aspire_one_110/bios/[/HTML]

This was where I got it from as well.

---

### Post by dmfrey on 2009-02-03
> **darkwalt said:**
> Hm, well that's odd.  I see 3308 and 3309 on there, both of which aren't on the official acer "aspireoneuser.com" website.  Not to be condescending, but did you do the fan control part of the install guide?

[html]https://help.ubuntu.com/community/AspireOne110L#Fan%20Control[/html]

Yes, I configured it as stated on that page.  There were updated versions of the scripts as well that were needed to handle the specific bios version.

---

### Post by dmfrey on 2009-02-03
> **darkwalt said:**
> Hm.  Well i'll make a note to stay away from that firmware.  I would suggest flashing it back to the previous version of the bios then.  I remember when I first got my A1 that would happen until I installed the acerfand script, or when I got a kernel update.  Did you try using a sickboy kernel to see if that fixed it?

Which version is the recommended one at this point that supports the fan control correct?  3305?

---

### Post by darkwalt on 2009-02-03
Yeah, i'm using 3305 and I have no problem right now.

EDIT:  Forgot to mention that I didn't need the fan control script for firmware 3305.

---

### Post by mikespug on 2009-02-22
For those interested in two finger scroll...

[http://www.aspireoneuser.com/forum/viewtopic.php?f=28&t=10975](http://www.aspireoneuser.com/forum/viewtopic.php?f=28&t=10975)

---

### Post by darkwalt on 2009-02-23
> **mikespug said:**
> For those interested in two finger scroll...

[http://www.aspireoneuser.com/forum/viewtopic.php?f=28&t=10975](http://www.aspireoneuser.com/forum/viewtopic.php?f=28&t=10975)

Just a note.  If you put in just the additions that the author recommends on that page, you get a graphical error.  Instead, put this in your /etc/X11/xorg.conf

```
    
Section "InputDevice"
       Identifier     "Synaptics Touchpad"
       Driver         "synaptics"
       Option         "SendCoreEvents"      "true"
       Option         "Device"            "/dev/psaux"
       Option         "Protocol"         "auto-dev"
       Option         "HorizEdgeScroll"      "0"
       Option         "SHMConfig"         "true"
       Option         "VertTwoFingerScroll"   "1"
       Option         "EmulateTwoFingerMinW"   "7"
    EndSection

    Section "ServerLayout"
       Identifier    "Default Server Layout"
       Screen        "Default Screen"
       InputDevice   "Keyboard"      "Core Keyboard"
       InputDevice   "Synaptics Touchpad"   "Core Pointer"
    EndSection

Section "InputDevice"
   Identifier   "Keyboard"
   Driver      "kbd"
EndSection
```

That should be easier and save you some time and hassle.

---

### Post by Sockerdrickan on 2009-02-24
> **darkwalt said:**
> Hm, well that's odd.  I see 3308 and 3309 on there, **both of which aren't on the official acer "aspireoneuser.com" website.**
.........official my *** ):P

---

### Post by senor_smile on 2009-02-24
I just purchased an aspire one last friday, and went through all the directions I found via this thread and the related documentation referenced.  I must say, this is quite the coolest little toy I have come across in some time.  I got it for only 247.99 from Fry's, which is to date the cheapest full use computer I have ever purchased.  

The directions really got me up and running quickly(including just getting the two finger mouse working).  Thanks to all who have contributed.  

--shaun

p.s. Has anyone found the two button mouse scrolling a little quirky?  Whenever I let my fingers off of the mouse pad, it shifts a little from the section of the page I have scrolled to.

---

### Post by darkwalt on 2009-02-24
> **senor_smile said:**
> Has anyone found the two button mouse scrolling a little quirky?  Whenever I let my fingers off of the mouse pad, it shifts a little from the section of the page I have scrolled to.

Yeah, I have.  On the website the code is on, one of the posts details how to fix it.  I've just been too lazy to.  ;)

Btw tux0r, that is official for the aspire one.  It's run by acer, which is why they put a rebuttal to them having sent larger battery review units.

---

### Post by darkwalt on 2009-03-02
> **senor_smile said:**
> Has anyone found the two button mouse scrolling a little quirky?  Whenever I let my fingers off of the mouse pad, it shifts a little from the section of the page I have scrolled to.


Get this little gem.  In system under preferences it'll add a section called touchpad.  To get mine working I turned up the sensitivity.  That helped a bunch.  However, it doesn't help with the odd scrolling problem that is jumping up and down rapidly.  It does help with the small movements.  Acceleration is good too.
```
sudo apt-get install gsynaptics
```

---

### Post by hawkys on 2009-03-03
hello folks

thx for the AspireOne110L community doku :P ... to this:

yesterday i have tested and installed ubuntu 8.10 from usb-stick and after installation + reboot i can connect to the lan with eth0.

1.) the suggested new kernel *linux-image-2.6.28-6-generic_2.6.28-6.17_i386.deb* i don't found on *fr.archive.ubuntu.com*.

the kernel i found and tested was 2.6.28-8, but this one breaks with kernel panic.

2.) after the safe-upgrade and reboot the aao can't connect the lan with eth0 again.

bye,
hawkys

---

### Post by gmc on 2009-03-03
> **hawkys said:**
> hello folks

thx for the AspireOne110L community doku :P ... to this:

yesterday i have tested and installed ubuntu 8.10 from usb-stick and after installation + reboot i can connect to the lan with eth0.

1.) the suggested new kernel *linux-image-2.6.28-6-generic_2.6.28-6.17_i386.deb* i don't found on *fr.archive.ubuntu.com*.

the kernel i found and tested was 2.6.28-8, but this one breaks with kernel panic.

2.) after the safe-upgrade and reboot the aao can't connect the lan with eth0 again.

bye,
hawkys

Regarding (1) the 2.6.28-8 kernel. I maybe wrong but I think you'll find that kernel is under testing for the upcoming 9.04 version of Ubuntu and will not work with 8.10. I haven't run 8.10 for some time now. 

You may have better luck using the customized kernel found at [http://www.aspireonekernel.com/](http://www.aspireonekernel.com/)

Problem (2) is related to your current kernel problems.

Gord

---

### Post by hawkys on 2009-03-03
> **gmc said:**
> 

Problem (2) is related to your current kernel problems.

Gord

with kernel panic there is no chance to safe-upgrade i think ;-)

so i have do a new clean installation and after this, the aptitude safe-upgrade


ps: the location *[http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com)* and the kernel is named/recommended in the AspireOne110L-docu!

--hawkys

---

### Post by gmc on 2009-03-03
> **hawkys said:**
> with kernel panic there is no chance to safe-upgrade i think ;-)

so i have do a new clean installation and after this, the aptitude safe-upgrade


ps: the location *[http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com)* and the kernel is named/recommended in the AspireOne110L-docu!

--hawkys

Well I have to be honest, it probably wouldn't hurt to do a re-install, but before you do, you should be able boot up and press <esc> when the system offers you the option and select a previously installed kernel. 

Failing that, then a re-install will definitely sort things out for you. Best of luck...

Gord

---

### Post by hawkys on 2009-03-03
... ok, if i do press <esc> and select the old kernel 2.6.27-7, so i can re-connect the wired lan. good! now i do install *linux-backports-modules-intrepid*

after reboot with 2.6.27-7 there is no wireless-lan-interface, but if i boot into 2.6.27-11 (comes from safe-upgrade) now i can connect the wireless-lan and write here from aao 110l this message ;-)

### ### ###

HOWTO INSTALL UBUNTU 8.10 AT AAO 110L FOR GERMAN SPEAKERS:

=> [http://neo.magdeburg.de/AAO-110L-Ubuntu-8.10.txt](http://neo.magdeburg.de/AAO-110L-Ubuntu-8.10.txt) <=

### ### ###


thx,
hawkys

---

### Post by darkwalt on 2009-03-05
Hey, is anybody else having trouble with their wifi after the latest update that required a restart?  I'm using the latest sickboy kernel and still nothing.

---

### Post by grandmaster on 2009-03-07
I now have no wifi at all since the last update.
I have tried a few things but so far I have been unable to get it to work.:(

I'm gutted

---

### Post by darkwalt on 2009-03-07
> **grandmaster said:**
> I now have no wifi at all since the last update.
I have tried a few things but so far I have been unable to get it to work.:(

I'm gutted

Try the wifi switch, and leave it sitting there for five minutes.  It's happened to me more than once.  Also, I updated around 2145 PST and my wifi worked.

---

### Post by grandmaster on 2009-03-07
> **darkwalt said:**
> Try the wifi switch, and leave it sitting there for five minutes.  It's happened to me more than once.  Also, I updated around 2145 PST and my wifi worked.

Thanks for the reply!

I tried that but got nothing (wireless card was not even detected.
I tried some other drivers but still nothing.
Then I opened my etc/modules and added ath5k on the end.
Rebooted and managed to connect.

So i'm typing this reply on my beloved aspire one.

Excellent! :D

---

### Post by Jesterday on 2009-03-07
I have found that when my wifi Connection drops out and the card no longer gets detected, shut the computer off and then start it up and all will be fine.

---

### Post by grandmaster on 2009-03-07
> **Jesterday said:**
> I have found that when my wifi Connection drops out and the card no longer gets detected, shut the computer off and then start it up and all will be fine.

That has happened to me a few times and that has worked however since the update my wireless ceased to work, i have only managed to get time to look at it today as i used a usb 3G dongle most of the time when i'm at work and i have a larger laptop at home which I do most of my stuff on...

although as I was typing this reply my wireless has dropped out so I may need to spend a little more time on it doh!!

---

### Post by superJoel on 2009-03-07
> **grandmaster said:**
> That has happened to me a few times and that has worked however since the update my wireless ceased to work, i have only managed to get time to look at it today as i used a usb 3G dongle most of the time when i'm at work and i have a larger laptop at home which I do most of my stuff on...

although as I was typing this reply my wireless has dropped out so I may need to spend a little more time on it doh!!

If running with madwifi drivers, Did you try going to your madwifi folder and do a make than make install after the update.

I am running WiCd as my network manager with the Mad-wifi drivers on Intrepid off my SDHC card.

On Juanty I installed the jaunty linux-backports and the nm-applet on my Jaunty on my SSD drive and my wireless works on both.

---

### Post by londonali1010 on 2009-03-10
> **darkwalt said:**
> Hey, is anybody else having trouble with their wifi after the latest update that required a restart?  I'm using the latest sickboy kernel and still nothing.

I had a great time with the last update!  I'd left my 'puter on overnight downloading some videos, came back to it wanting to update, but my wireless was gone, couldn't figure it out and couldn't update!  So I went to use the wired connection and that didn't work either, read something about the latest kernel breaking the wired connection, reverted to a previous kernel, which then gave me black screen of death!!!  Did manual fsck, booted up, got ethernet to work, updated, reverted back to latest kernel *et voila!*  Everything works fine now.  I still have no idea what happened...?!?  But I now have a lot more experience, thanks mostly to y'all here :D

---

### Post by drlmg on 2009-03-13
I did it again, I figured that after a few months surely someone had fixed this problem but no. This is really pitiful. After hours of working on the laptop trying to restore my previous setup (have had barely any sleep in days - working, still no excuse) I got so aggravated I threw it in the trash.... really hard. I know that was very stupid and childish but it is done now but I regret it dearly, just please don't tell my mommy she will beat my a$$ regardless of my age!! I loved that little laptop. I am an idiot but I wanted to warn others of this ongoing problem. Read here....[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/322867](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/322867)

supposedly the newest version (still being tested I think) will not crash the machines, however in the forum listed above is this.. "Sorry Stefan, but the bug persists in 2.6.24-24.50."

---

### Post by darkwalt on 2009-03-13
Ok, so updated earlier this week and it did something out of the ordinary.  When I booted I got "could not start x graphical environment".  Did an update from the console and one of the updates was libpurple.  The other one was pidgin.  I'm fairly sure that pidgin didn't kill the display.

---

### Post by cirabisi2009 on 2009-03-13
> **gcday said:**
> It looks like I have the beta release:



I followed the instructions and nothing seems to happened.

i have everything the same except

kernel linux 2.6.27-7-generic

how do i get my wifi to work? and it wont read my sd card.. and i have absolutely NO idea how ubuntu works.. i just got it this morning. i downloaded it from [http://wubi-installer.org/](http://wubi-installer.org/)

please help.. get ahold of me on aim even.. that'd be alot more helpful. and is there a way for me to swap between xp and ubuntu besides shutting down everytime to switch

---

### Post by darkwalt on 2009-03-13
> **cirabisi2009 said:**
> how do i get my wifi to work?

Usually when I reinstall, which isn't that often anymore, I just install the sickboy kernel, which fixes the wifi and the tx/rx led.  They don't provide it at kuki.me anymore, which kinda blows, but they do provide it at another website that does have acer in the address.  Ah, found it [html]http://www.aspireonekernel.com/[/html].  Go there and download the sickboy kernel.  Let us know if that helps.

---

### Post by drlmg on 2009-03-13
Here is a great page for Acer Aspire One users. It tells in great detail how to get everything working. I wish I had found it sooner.

[https://help.ubuntu.com/community/AspireOne](https://help.ubuntu.com/community/AspireOne)

---

### Post by darkwalt on 2009-03-13
Isn't that the site that this thread is for?

---

### Post by cirabisi2009 on 2009-03-13
> **darkwalt said:**
> Usually when I reinstall, which isn't that often anymore, I just install the sickboy kernel, which fixes the wifi and the tx/rx led.  They don't provide it at kuki.me anymore, which kinda blows, but they do provide it at another website that does have acer in the address.  Ah, found it [html]http://www.aspireonekernel.com/[/html].  Go there and download the sickboy kernel.  Let us know if that helps.

the one thing im not grasping! how do i download that file into ubuntu when i can only download it from windows xp? maybe sd card? but then i dont know how to set that up to make something install from an sd card :( 

i know i know.. im kinda uber noobish...


and another thing. any info i recieve on fixing these problems will be posted in one of my blogs on myspace as well as a link to come here. So your typed in words are not going to any waste i promise that

---

### Post by darkwalt on 2009-03-13
> **cirabisi2009 said:**
> i know i know.. im kinda uber noobish...

Ah, well it comes in a .deb package, which is like a windows .exe file, but for ubuntu.  Also, wired networking works.  Just follow this guide right here [https://help.ubuntu.com/community/AspireOne](https://help.ubuntu.com/community/AspireOne) and you'll be on the right path.

---

### Post by cirabisi2009 on 2009-03-14
first off i cant get my wired connection to even work now? and. 

Wireless module
There has been some confusion as to which wireless driver provides the best performance and reliability. I have found the following: 


-madwifi from kernel (ath_pci) - does not attach to hardware. 
-ath5k from intrepid backports (ath5k) - connects to hardware, but experiences disconnects on medium to heavy wireless activity, and can not communicate with some AP's using WPA2 PSK. 
-madwifi-hal from [http://snapshots.madwifi-project.org/](http://snapshots.madwifi-project.org/) (ath_pci) - Everything works. 

I recommend using the most recent snapshot of madwifi-hal from [http://snapshots.madwifi-project.org/](http://snapshots.madwifi-project.org/) 



wget [http://snapshots.madwifi-project.org/madwifi-hal-0.10.5.6-current.tar.gz](http://snapshots.madwifi-project.org/madwifi-hal-0.10.5.6-current.tar.gz)
sudo apt-get install build-essential linux-headers-$(uname -r)
tar -xzf madwifi-hal-0.10.5.6-current.tar.gz
cd madwifi-hal-0.10.5.6*/
make
sudo make install
sudo modprobe ath_pci



i dont understand where to enter anything. 

and with the ethernet cable plugged in. all that comes up is auto eth0 and that does nothing. as soon as i plug in the internet it says disconnected with in a few seconds?

---

### Post by ludovich on 2009-03-14
I installed 8.10 on friday on mine... fought with the atheros wireless problem for quite a while until I was able to get it to work with the madwifi drivers. Saturday I fooled around for quite some time trying to get VNC to display a UBUNTU window on my MACBOOK Pro OS X laptop, no luck yet, I could use some help with this....

Late last night I installed all the recommended updates (251 of them)...
I got up this morning to play and the network stopped working... no wireless, no hardwire ethernet, nothing. I noticed that the upgrade included a newer ".11" kernel, I rolled back to the original ".7" kernel that was installed initially and now the network is back.

One of my most frustrating problems right now is that the entire screen needs to be shifted up, the information in the grey bar at the bottom is cut off by about 40%. I can't get "xvidtune" to work as described it keeps giving the error message "Unable to query montor info" and quits.

Anybody have any good suggestions?

---

### Post by skyer2000 on 2009-03-15
How do you revert back to an older kernel? Also, when reverting back to an old one, won't it ask to update everytime?

---

### Post by khaeru on 2009-03-15
Hi everyone,

I would highly recommend running the development version of Ubuntu [http://cdimage.ubuntu.com/releases/9.04/](http://cdimage.ubuntu.com/releases/9.04/). Choose the "UNR USB image".

I installed Alpha 4 and have been keeping it up to date (now Alpha 6). Because Jaunty is still under active development, this means downloading a large number of updates every couple of days, but I do this plugged in to Ethernet and it goes fairly quickly.

Some of the improvements I have noted:
[list]
[*]Ethernet works without issue ([https://bugs.launchpad.net/ubuntu/+source/linux/+bug/326891](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/326891) this bug has been fixed)
[*]Wireless performance is much improved over 8.10. Connections are made and renewed very quickly, whereas Signal strength (very subjectively) seems better.
[*]The display is better when outputting to both the VGA port and built-in display. Instead of a 640 × 480 screen stretched oddly over the 1024×600 LCD, there is a 800×600 screen centered in the middle of the LCD and letterboxed.
[*]I use an ext2-formatted SDHC card in the left slot, and while some bugs exist, the auto-mounting behaviour is better under Jaunty than in 8.10.
[/list]

At the very least, this means you don't have to do any mucking about with madwifi. Just install & go!

---

### Post by pjalegria on 2009-03-16
Hi

Do you use the SDHC card in the left slot as HOME? Can you Suspend/Resume without the SDHC in the slot?

Thanks

---

### Post by khaeru on 2009-03-16
> **pjalegria said:**
> Do you use the SDHC card in the left slot as HOME? Can you Suspend/Resume without the SDHC in the slot?

I don't use it as /home. It is automounted (i.e. without me having ever edited /etc/fstab) at /media/disk; for now I only have a music directory on it, and I have configured Rhythmbox to use /media/disk/Music instead of /home/khaeru/Music. This works fairly well.

Under jaunty-alpha, I can suspend and resume with or without the card in. Is "without" a typo? I can't see why you would want to put /home on the card, then remove the card, then suspend...that would seem like a recipe for trouble.

The bugs I referred to are:
[list]
[*]I see two items for "16.1 GB Media" in netbook-launcher, but only one is ever mounted. It seems one refers to /dev/mmcblk0 and the other to /dev/mmcblk0p1. The former is probably an error, because it is just the block device, while the latter is the actual filesystem.
[*]Occasionally my partition table on the SDHC card disappears. I have not pinned down when this happens; it may be on suspend/resume *and* on boot. In these instances, I have to "sudo cfdiskc /dev/mmcblk0" and recreate the partition. When I do, the card is automounted and all my data is present; so for now this is only an annoyance and not a data integrity problem.
[/list]

I wiped the fat32 filesystem from the card as soon as I bought it, so I have no clue how the SDHC performance is for fat32 cards under 8.10 vs. jaunty-alpha.

---

### Post by awy on 2009-03-16
Hi, 

I have just bought an AA1 but one of the new 10.1" versions. While much is similar to its smaller cousin, a few bits are clearly different. I'm having trouble getting it into a useful state (it came with WinXP :(.

I was able to install 8.04 easily enough from USB stick but neither fixed nor wireless networking works. I have read both the [https://help.ubuntu.com/community/AspireOne](https://help.ubuntu.com/community/AspireOne) & [https://help.ubuntu.com/community/AspireOne110L](https://help.ubuntu.com/community/AspireOne110L) threads but I get the impression that they are all talking about the 8.9" version.

I tried putting [http://kernelmirror.linxisp.com/releases/linux-image-2.6.28sickboy-kuki_0.4_i386.deb](http://kernelmirror.linxisp.com/releases/linux-image-2.6.28sickboy-kuki_0.4_i386.deb) (from [http://www.aspireonekernel.com/](http://www.aspireonekernel.com/)) on it but this hangs during boot, just after probing the USB devices.

My next plan is to try either 8.10 or even Xubuntu 9.04 Alpha 6. Before I spend lots of time thrashing around between versions, is there anyone who has successfully brought Ubuntu (or Xubuntu, UNR) up on this variant?

For the record, the various stickers on the bottom call it a D150-1165 or a KAV10.

Alan.

---

### Post by flatland2d on 2009-03-17
Alan, I feel your pain.  One of the reasons I bought the One was good support with Ubuntu since the laptop has been out for a while.  The 10" seems to be a slightly different beast though.  I've been having some problems with mine.  I tried starting another thread specifically for the 10" since it has separate issues.  So far that thread hasn't gone anywhere.  Here's a link:

[http://ubuntuforums.org/showthread.php?t=1095616](http://ubuntuforums.org/showthread.php?t=1095616)

The Sickboy kernel won't work on our 10" Ones.  Not sure why.  Different hardware?

Intrepid works well except for a few issues.  No sound, suspend/hibernate not working when the lid is closed (does work when selected manually), ACPI temp not reporting correctly, and significantly less battery life than WinXP (I get 5.5 hours with Ubuntu, 8 hours with Windows).  Once I upgraded to the madwifi-hal drivers, wireless worked perfectly

I am testing Jaunty right now and I like it better except my vertical scrolling is messed up somehow (might be my fault).  Sounds works fine.  Wifi works without installing extra drivers.  Still no suspend/hibernate when the lid is closed, and the ACPI temp is still wrong.  That makes me worry about overheating, but it doesn't feel especially hot.  I've been doing testing for the developer of acerhdf (fan control) but no success yet.

Whether we use this thread or start a new one, I really hope some more 10" people come aboard because I really love this laptop.  I want everything to work perfectly.

---

### Post by .:Justus:. on 2009-03-18
**For everyone who needs help reverting back to the older kernel visit this thread [http://ubuntuforums.org/showthread.php?t=1078602](http://ubuntuforums.org/showthread.php?t=1078602)  and follow ugm6hr´s instructions**

**Wifi only works in -7 or older kernels as of right now on the AAO**

---

### Post by abisdad on 2009-04-10
Hi, posted some of my experiences in [http://ubuntuforums.org/showthread.php?p=6975458#post6975458]("http://ubuntuforums.org/showthread.php?p=6975458#post6975458").

I've got 8.10 running fairly well, but managed to stuff my XP Pro boot up in the process.

Now 8.10 boots beautifully, but when I F12, select USB CD and stick my XP CD in to recover the XP, it comes up with the line:

Press any key to boot from the CD...

(which I do, then quickly flashes for an instant:

Setup is inspecting your computer's hardware configuration...

Before doing a black screen and staying there.

Any idea's how to recover an XP install from a USB? 

(or to make a USB bootable with the XP Pro disk on)?

(or why my CD ROM won't boot, but my USB will)?

Sorry - but it's my work's Acer One, and they insist it needs to run XP!

Abisdad.

---

### Post by darkwalt on 2009-04-10
Are you using an aspire one or another aspire model with an internal drive?  Either way, I would partition the drive you're using with the xp boot to have two partitions.  One for ubuntu and one for xp.  Thats the way I did it on a pc and it worked for me.

---

### Post by abisdad on 2009-04-10
An Acer Aspire One ZG5 - 1GB RAM, 160GB HDD. BIOS 35/3305.

Ah! Hindsight... I had used 1 partition as I'd had problems with my 1st live Ubuntu USB (fixed with "HP USB Disk Storage Format Tool" from WWW), then happily made my XP partition smaller without defragging first!

This morning removed my 8.10, and 1/2 killed grub.

Could then boot from my USB CD drive with XP Pro in.

Microsoft FIXBOOT and FIXMBR failed to help! 

"A disk error occurred" was the error message I had...

I then found this link, which gives a fantastic little app that sorted all my problems! 
[URL="http://www.cgsecurity.org/wiki/TestDisk"]
http://www.cgsecurity.org/wiki/TestDisk[/URL]

Fixed my MBR, and restored (I think) my deleted Ubuntu too!

Wow!

---

### Post by darkwalt on 2009-04-10
Ah, also, forgot to mention this. You mentioned that you wanted to put xp on a usb flash drive?  You can use [unetbootin](http://en.wikipedia.org/wiki/UNetbootin) to make a .iso file bootable from a thumb drive.  Now if you can find a *legal* method for making your xp cd into a .iso file everything should be gravy.

---

### Post by abisdad on 2009-04-11
Thanks for the reply.

Having fixed my booting issues with [http://www.cgsecurity.org/wiki/TestDisk]("http://www.cgsecurity.org/wiki/TestDisk"), I didn't need to reload my XP, and I could also boot from my USB CD drive again!

I didn't manage to recover my GRUB config - due to my inability to concentrate at that stage - so I just reinstalled (twice! - the first time it picked up on the original install and tried to fix it - I think, so I wiped the partitions again from XP and tried again successfully) :-).

I now have a fantastic duel boot Acer Aspire One ZG5, working beautifully! :-) I'm very happy! :-) Thank you for your help.

---

### Post by darkwalt on 2009-04-23
Jaunty breaks two-finger scroll in the last form that I posted.  Anybody know how to get around it or re-enable it?

Also breaks even seeing anything plugged into right card slot.

---

### Post by londonali1010 on 2009-04-27
Anyone upgraded to Jaunty yet?  And do you know if I'll have to redo all my settings specific to the AA1?  (e.g. wireless LAN, SD cards, etc.)

---

### Post by chris.h on 2009-04-27
> **londonali1010 said:**
> Anyone upgraded to Jaunty yet?  And do you know if I'll have to redo all my settings specific to the AA1?  (e.g. wireless LAN, SD cards, etc.)

I have the 160gb HDD version. I upgraded to the 9.04 UNR and it rocks. The only thing I had to do was the acerhdf module. wireless worked, the left hand sd reader was hot-pluggable, suspend worked, cheese worked, microphone worked. The upgrade went perfect for me.

---

### Post by darkwalt on 2009-04-27
Yeah, the left sd card is hot pluggable for me, but for some odd reason the right one isn't.  I have to leave a card in there from boot if I want to use it.

---

### Post by londonali1010 on 2009-04-28
Just an update: I bit the bullet and did the upgrade...Only problems so far is no fan control and my SD cards (both!) don't work.  I have yet to test all my other weird programs, sound, etc.

Wireless is absolutely fine out of the box (and I dig the new notification popup), but no LEDs.

That said, the whole process was very easy and went smoothly, and I'm liking at least one new feature: the disk janitor :)  Esp. since space is at a premium on my little jewel!

PS. Is there already a separate thread for Jaunty on the AA1?  I couldn't find one, and I'm thinking it's about time, since we're hijacking the 8.10 thread...

EDIT: Whoops, I'm an idiot.  Rebooted, and left SD card is fine.  Still haven't gotten the right one to work, tho.

EDIT #2 (sorry! Careful, there's a forum spammer on the loose!!!): I added the acerhdf module as per [here]("https://help.ubuntu.com/community/AA1/Fixes") and the fan is fine now.  All that's left to work fully is the right card reader and wireless LEDs.

---

### Post by Aearenda on 2009-04-28
Wireless LEDs work if you install linux-backports-jaunty - the right SD card is still a problem for everyone unless you boot with a card in it.

---

### Post by darkwalt on 2009-04-29
> **Aearenda said:**
> Wireless LEDs work if you install linux-backports-jaunty - the right SD card is still a problem for everyone unless you boot with a card in it.

I have backports enabled in the repositories menu, but the wifi led still isn't working.

---

### Post by Aearenda on 2009-04-29
Sorry, I got the package name wrong. It is 'linux-backports-modules-jaunty', and confusingly it is in the 'main' repository.

Edit - this is from the [community help page]("https://help.ubuntu.com/community/AspireOne#Notes%20about%20Ubuntu%209.04%20(Jaunty%20Jackalope)%20desktop%20and%20UNR%20(Netbook%20Remix)"), and working on my system.

---

### Post by londonali1010 on 2009-04-29
OMIGOD THANK YOU!!!

I haven't had the LEDs working EVER, not even when it was straight out of the box! (They were only ever: left off, right solid on.) 'Course, only the right one of the two is working, is that the same for everyone?

PS: I made a new Jaunty thread for the Acer Aspire One...[here]("http://ubuntuforums.org/showthread.php?p=7177918#post7177918")

---

### Post by rico1981 on 2009-04-29
> **londonali1010 said:**
> 
PS: I made a new Jaunty thread for the Acer Aspire One...[here]("http://ubuntuforums.org/showthread.php?p=7177918#post7177918")

OK, I joined the new thread and I wrote about my experience with Aspire One D150 and Ubuntu 9.04 Jaunty, feedbacks are welcome :)

---

### Post by teh603 on 2009-04-29
> **londonali1010 said:**
> OMIGOD THANK YOU!!!

I haven't had the LEDs working EVER, not even when it was straight out of the box! (They were only ever: left off, right solid on.) 'Course, only the right one of the two is working, is that the same for everyone?
That's how they were when I was using eeebuntu 8.10 and the NDISwrapper drivers.

---

### Post by felixfx on 2009-05-04
Hello...

i have installed [SIZE=1]Jaunty Jackalope on AAO150 and to get [/SIZE]hibernate working i have installed the TucOnIce PPA described in [AspireOne]("https://help.ubuntu.com/community/AspireOne?action=fullsearch&context=180&value=linkto%3A%22AspireOne%22")  Documentation. When booting with the 2.6.28-12 kernel from the TucOnIce-PPA the wireless-LED does not working anymore, maybe because there are no **linux-backports-modules** available for this kernel . Is there anyone who knows to fix that ?

greeting,
felix

---

### Post by TechnoBlunder on 2009-05-22
Hi Folks,

I came across this thread from the [community link on the Aspire One.]("https://help.ubuntu.com/community/AspireOne/")  I was having issues with suspending my Aspire One, where the wifi wouldn't come up.  There's a shell script mentioned to bring the Wifi0 down and up again, that with a minor tweak did the job for me.  I couldn't find an example anywhere else, so thought I'd offer it both here and there.  The file is located at

/etc/pm/sleep.d/00wireless

```

#
# Restart WiFi interface after suspension
#

case "$1" in
        resume|thaw)
[COLOR=Sienna]                /etc/init.d/networking restart[/COLOR]
        ;;
        *)
        ;;
esac

exit $?
```

Regards,

Stephan

---

### Post by londonali1010 on 2009-05-23
Can you post the type of Aspire One you have (e.g. 9", 10.5", SSD, HDD, what memory) and which WiFi method you're using?

For instance, I've always used ath5k and had no issues with suspend/resume (of course I'm running 9.04 Jaunty now, so it might be a moot point).

---

### Post by LewRockwell on 2009-07-10
Acer Aspire One AOA-150-1864 with the Dell mini-wlan 1390 card

Report:

Working fine triple-booting XP Professional SP3, Ubuntu 9.04 Jaunty(full version), Puppy Linux 4.2.1, and with five more logical partitions for five more *nix distros!

.

---

### Post by gloken on 2009-10-03
> **aimpau said:**
> #1 You said you've **just** installed 8.10 so I'm assuming it is already in the last stage of alpha (ibex alpha6).

#2 Go to Applications>>System>>Updates (I'm on xubuntu so try to adjust to your ubuntu)

#3 Open a terminal and:
```

sudo apt-get install madwifi-tools

```

#4 On the same terminal after the install
```

sudo gedit /etc/modprobe.d/blacklist

```

On the last line, add
```

blacklist ath_pci

```
and press save

#5 Terminal
```

sudo gedit /etc/rc.local

```
And add to the last line
```

modprobe ath5k

```


If anything is wrong here, please feel free to correct me.

I tried this on a fresh install of 8.10 and there's been no visible change.
Anyone know what could have gone wrong?

Nevermind! I solved it... somehow. I believe that I had to enable it in hardware drivers.

---

