---
title: "headphones and speakers"
date: 2006-11-18
forum: Hardware &amp; Laptops
---

### Post by .alpeffers. on 2006-11-18
I've just discovered that when i plug in some headphones into my laptop's headphone jack, the sound keeps coming out of the speakers as well as my headphones :???: 

I cannot remember if that happened in drapper, but its happenning now that I'm using Edgy.

is there a fix for this?

laptop is a dell 640m or 1401(i think)... its the smaller dual core laptop.

Thanks :)

---

### Post by drinkingbird on 2006-11-19
I don't want to be the bearer of bad news, but to the best of my knowledge this is probably a hardware problem (albeit a simple one), and a switch in the headphone jack isn't working as it normally does to cut out the speakers when a plug is inserted.

You may want to check if this happens under another OS (try a live CD, or some such) to check if it's a persistent problem, but I don't like the chance that it's a software issue.

---

### Post by Portable_Jim on 2006-11-19
I don't know much about laptops or sound in Ubuntu, but here is a possible solution to your problem:

Ubuntu might have picked up the difference between the speakers and the headphones, and so the headphones might be controlled seperatly.


Try (this works in Dapper + gnome):
```
gnome-volume-control
```then mute 'headphone' and see (actually hear) what happens

PS. This is just a guess.

---

### Post by aspro on 2006-11-19
Well my old Apple PowerBook G4 had the same problem under Ubuntu back when I last tried it (over a year ago) it wouldn't cut the speakers when I was using Ubuntu, but would under OS X. So there is a possibility it is software.

BTW, you should be glad you found out about that now, rather than in an embarrassing situation (my friend didn't realize the same thing happened on his laptop, and he started playing music in the silent study area of the library, though I couldn't help but laugh :))

---

### Post by .alpeffers. on 2006-11-21
Thanks for the suggestions, and I discovered this almost in the middle of a lecture hehe...

anyway, when i run 'gnome-volume-control' I don't get any options for speakers, headphones, etc.

the only options i have are for the 'Master', 'PCM', and 'Capture Mix'

then there is a capture tab, and an options tab... there appears nothing else to enable, or disable...


am going to play around with it, and possibly pop in a different live CD to see if a different distro works...

!new progress!
I'm very sure now that it is just a software issue, i rebooted my laptop with headphones plugged in, then tried to play any sound file, and nothing came out of the speakers, just my headphones... so now I'm stumped on what/where to go.

---

### Post by .alpeffers. on 2007-01-02
might as well bump this, to see if anyone else has encountered this

and also to add that the issue still exsits.  Also I'm not sure if it is either a priority upon setting up the desktop environment or not.

IE if i plug in before booting up, speakers are quiet, however if i then unplug the headphones no sound continues to emanate from the laptop's speakers.  whereas if i start up with the headphones unplugged, login, and then plug them in, sound comes out of both.  Soo is there anyway that i could either...
A - have some signal be sent when i plug in the headphones, and unplug them.
or
B - not make me have to restart the desktop session every time i wish to use my headphones.


btw, theres some issues with doing the ctrl-alt-backspace.
but then again i've had nothing but issues with 6.10 :(

---

### Post by eggdeng on 2007-01-02
Sounds familiar (no pun intended). Can you post the output of ```
lspci
``` to see what soundcard you are using. Also any of these```
cat /proc/asounds/version
cat /proc/asound/cards
cat /proc/asound/modules
```
to see which version of alsa you have installed.

---

### Post by eitan_a on 2007-01-02
I had the same problem.  I solved it by downloading GNOME ALSA Mixer program from "add/remove" programs.  It let's you mute the internal speakers by muting "Front" and control the headphone volume using "PCM".  Hope that works.

---

### Post by .alpeffers. on 2007-01-08
lspci generated:
```
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 01)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) Serial ATA Storage Controller IDE (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
02:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
02:01.0 FireWire (IEEE 1394): Ricoh Co Ltd Unknown device 0832
02:01.1 Class 0805: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
02:01.2 System peripheral: Ricoh Co Ltd Unknown device 0843 (rev 01)
02:01.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)
02:01.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 05)
0c:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
```

cat /proc/asound/version...
```
Advanced Linux Sound Architecture Driver Version 1.0.12rc1 (Thu Jun 22 13:55:50 2006 UTC).
```

cat /proc/asound/cards...
```
 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xdfebc000 irq 233

```

cat /proc/asound/modules...
```
 0 snd_hda_intel

```

I will also have a look-see for the Gnome ALSA mixer, hopefully i can get some sort of resolution to this... if not i'll keep going with no sound :-#

---

### Post by skeeterflea on 2007-01-08
I'm having the same problem I haven't tried to reboot yet with the headphones plugged in however.  I'll do that afterwards.

lspci

```

0000:00:00.0 Host bridge: Intel Corporation 82845 845 (Brookdale) Chipset Host Bridge (rev 03)
0000:00:01.0 PCI bridge: Intel Corporation 82845 845 (Brookdale) Chipset AGP Bridge (rev 03)
0000:00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 12)
0000:00:1f.0 ISA bridge: Intel Corporation 82801BA ISA Bridge (LPC) (rev 12)
0000:00:1f.1 IDE interface: Intel Corporation 82801BA IDE U100 (rev 12)
0000:00:1f.2 USB Controller: Intel Corporation 82801BA/BAM USB (Hub #1) (rev 12)0000:00:1f.3 SMBus: Intel Corporation 82801BA/BAM SMBus (rev 12)
0000:00:1f.4 USB Controller: Intel Corporation 82801BA/BAM USB (Hub #2) (rev 12)0000:01:00.0 VGA compatible controller: ATI Technologies Inc Radeon RV200 QW [Radeon 7500]
0000:02:08.0 Multimedia audio controller: C-Media Electronics Inc CM8738 (rev 10)
0000:02:09.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

```

cat /proc/asounds/version

```

cat: /proc/asounds/version: No such file or directory

```

cat /proc/asound/cards

```
0 [CMI8738MC6     ]: CMI8738-MC6 - C-Media PCI CMI8738-MC6
                     C-Media PCI CMI8738-MC6 (model 55) at 0xdc00, irq 193

```

cat /proc/asound/modules
```
0 snd_cmipci
```

---

### Post by eggdeng on 2007-01-08
A lot of us using Intel High Definition Audio have had the same problem as .alpffers. To get things to work correctly, you need a recent version of alsa, in this case the version listed, 1.0.12rc1 should be OK (note to skeeterflea,: that's cat: /proc/asound/version & not 'asounds') and the correct snd_hda_intel module is listed. 

So you just need to add the correct option  at the end of /etc/modprobe.d/alsa-base along the lines of ```
options snd-hda-intel model= xyz
```
The problem is that xyz varies from maker to maker and from model to model. See this thread for a few of the options [http://www.ubuntuforums.org/showthread.php?t=314383](http://www.ubuntuforums.org/showthread.php?t=314383) or post the model of your laptop here. I'm not sure but installing the latest version of alsa 1.0.14 may make this addition unnecessary.

Skeeterflea is using a different chip which, sorry, I have no experience of.

---

### Post by .alpeffers. on 2007-01-10
This is a Dell 640m laptop
integrated intel graphics, sound, wireless..
I cannot tell you exactly what rev the firmware is on all this as I am not a hardware guru, so that is about the best description I can give... if i could find my part listing i got from dell when i ordered it i will list it.

other than that I know it has a Sata HD, DVD burner... "true bright" screen... aka high res(which i got working 1440x900)...

you'll hafta forgive me, working this in-depth with drivers is new to me, as i've been a windows person all my computing life(a small exception with the use of the apple classic in grade school) and i've never had to deal with driver issues like this, they just worked(or at least appeared to)

---

### Post by eggdeng on 2007-01-10
Your output from the lspci command (which basically lists hardware installed on the motherboard (pci bus) in your system) lists your soundcard as ```
Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01) 
```
Ubuntu uses a driver called alsa to interface with soundcards. Your system has a recent version of alsa - 1.0.12. Updating to the latest version might or might not solve your problem, if you want to go that way, google for a how-to.

The module alsa uses for Intel HDA cards is called snd-hda-intel. But you probably need to  configure it with a specific option for it to work on your laptop. You do this by opening the appropriate configuration file with root privileges in your text editor, if you are using gedit -
```
sudo gedit /etc/modprobe.d/alsa-base
```
- adding something like ```
options snd-hda-intel model=dell
```
or ```
options snd-hda-intel model=dell-laptop
```
at the end of the file  (google for more options), and rebooting. This has worked for others, it may or may not work for you but it shouldn't take you more than a couple of minutes to try.

---

### Post by lifeempowered.com on 2007-01-18
Thanks for this post, I have a dell 6400 and it worked to add the ...model=dell line to my file.  Appreciate it!;)

---

### Post by noworry on 2007-02-22
Thanx eggdeng, it got resolved in my dell e1505 by adding the line "options snd-hda-intel model=dell".

---

### Post by deadowl on 2007-03-05
Wow, I have the same effin problem.

And to add, the headphone/internal thing will happen when I come out of standby.

---

### Post by eggdeng on 2007-03-05
Check out this thread [http://www.ubuntuforums.org/showthread.php?t=314383](http://www.ubuntuforums.org/showthread.php?t=314383). What make / model is your laptop? What soundcard have you got? if you aren't sure, you can find out with ```
cat /proc/asound/cards
```

---

### Post by DishBreak on 2007-07-01
i've added the aforementioned line to alsa-base(used option "auto" and "3stack"), and wound up with sound working. but the headphones/speaker issue still remains. 

I'm at a loss. Is there anything i can do to fix this?

---

### Post by eggdeng on 2007-07-01
If you post the output of ```
aplay -l
``` it might be possible to narrow it down. I got mine working following
[http://ubuntuforums.org/showthread.php?t=342681](http://ubuntuforums.org/showthread.php?t=342681)
There are other fixes in
[http://ubuntuforums.org/showthread.php?p=1720522&highlight=Z70V#post1720522](http://ubuntuforums.org/showthread.php?p=1720522&highlight=Z70V#post1720522)

---

### Post by Orivel on 2007-11-24
I am having the same problem. When i use  ```
aplay -l
``` this is the output i get:


**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC883 Analog [ALC883 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC883 Digital [ALC883 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 6: Si3054 Modem [Si3054 Modem]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

Any help would be greatly appreciated.

---

### Post by eggdeng on 2007-11-24
You should be able to get this working by following [http://ubuntuforums.org/showthread.php?t=314383]("http://ubuntuforums.org/showthread.php?t=314383")

---

