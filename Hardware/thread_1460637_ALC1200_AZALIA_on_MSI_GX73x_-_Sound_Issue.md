---
title: "ALC1200 AZALIA on MSI GX73x - Sound Issue"
date: 2010-04-23
forum: Hardware
---

### Post by LittleJakub on 2010-04-23
Dear forumers,

first of all- greetings from Poland! Now, to business...

I have to start with the note that, in my society, OS other than Windows  is really, really under-appreciated... Mainly it is because Windows is  simply everywhere- and such a situation really makes me sad... Anyway,  back to the topic: I am a music producer, also, I am in a band in my  city, and we (referring to the band) use laptops and computers in  general a lot in our music composition and production process. For now,  everything happened in the environment of Win, I must say- if You want  to go the legal way, it is not the cheapest and affordable option of  all. Therefore, as the only person in my group of musical environment  that came up with an idea to start using Open Source software, because I  have been using UBUNTU a lot on my older PCs, and remembered it as a  great system.

BUT, there came a very sad surprise- when I setup it on my laptop (my  sweet-music-studio-miracle, MSI GX 733) I was sadly surprised- the only  sound I can get out of it is through subwoofer (out of 5 speakers in  general). First I searched through all the forums, all the solutions,  and- maximum that I got was to make all the speakers work, (through  configuration of alsa-base.conf in modprobe.d folder) but then, when the  outside AMPLIFIER and speakers were plugged in, there would be no  sound, or randomly, both on external speakers and the ones from laptop  (and no, alsamixer doesn't let me mute JUST the laptop, it mutes  everything, like all the regulators were bound together).

And that is why, my dear fellow inhabitants of UBUNTU Land of Glory and  Fast Performance, I came to You to ask for help. I really am into the  idea of spreading the word about Open Source in the Music World, and I  am talking big here- but as long as I cannot prove that a system put to  any random machine works just "out of the box", I will never convince  the "elders", who with their patronizing looks just shake their heads  and point to Windows- it really pis**es me off...

Help me show that UBUNTU can do it, any outcomes from terminal needed,  just let me know!

P.S. I am using the Beta 2 version 10.04 LTS right now, but the same  error appeared on 9.04 and 9.10, I guess the ALC1200 "Azalia" is really  hated :P

---

### Post by lidex on 2010-04-23
Open this file for editing:
```
 gksudo gedit /etc/modprobe.d/alsa-base.conf 
```
Insert this line at the bottom:
```
 options snd-hda-intel probe_mask=1  
```
Save. Close. Reboot. Check your levels in alsamixer.
```
 alsamixer 
```
Press F6 to select the correct soundcard.
Press F3 to show playback levels. F4 selects capture levels [or use <Tab>]
Use the left/right arrow keys to select and up/down arrow keys to change levels.
Go to "System>Preferences>Sound" and make sure the correct soundcard is default

---

### Post by LittleJakub on 2010-04-25
Just to be clear- the line in the alsa-base.conf You suggested- should I put only it at the end of the default alsa-base.conf file, or put it after the lines I added for the working of all the speakers?

cheers ;)

---

### Post by dino99 on 2010-04-25
Is your sound chipset well identified into system- pref -sound ?

If therte is problem with pulseaudio, delete .pulse

install gnome-alsamixer to tweak mute and volume .
In case you can run into console:

sudo dpkg-reconfigure alsa

[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)
[http://alsa.opensrc.org/index.php/Main_Page](http://alsa.opensrc.org/index.php/Main_Page)

---

### Post by dino99 on 2010-04-25
got this answer from realtek:

.. 	Search: alc1200
.... 	Sorry! There is no data found. Please try another keyword.
 
so this chip have an other name

what give aplay -l

look at:
[http://alsa.opensrc.org/index.php/RealtekALC](http://alsa.opensrc.org/index.php/RealtekALC)
[http://alsa.opensrc.org/index.php/SquisherAsoundRc](http://alsa.opensrc.org/index.php/SquisherAsoundRc)
[http://digamma.cs.unm.edu/trac.dmohr/wiki/DotAsoundrc](http://digamma.cs.unm.edu/trac.dmohr/wiki/DotAsoundrc)

[https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/365411](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/365411)

---

### Post by lidex on 2010-04-25
> **LittleJakub said:**
> Just to be clear- the line in the alsa-base.conf You suggested- should I put only it at the end of the default alsa-base.conf file, or put it after the lines I added for the working of all the speakers?

cheers ;)

For now just add it and reboot.

---

### Post by LittleJakub on 2010-04-25
[COLOR=Gray][I]**lidex: **When I put the line You suggested, the sound comes only from the headphone plug, and when I unplug the speakers/headphones (whatever is in the jack) there's no sound at all. My alsa-base.conf looks like this, maybe sth would help You:

```
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
install snd /sbin/modprobe --ignore-install snd $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-ioctl32 ; /sbin/modprobe --quiet --use-blacklist snd-seq ; }
#
# Workaround at bug #499695 (reverted in Ubuntu see LP #319505)
install snd-pcm /sbin/modprobe --ignore-install snd-pcm $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-pcm-oss ; : ; }
install snd-mixer /sbin/modprobe --ignore-install snd-mixer $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-mixer-oss ; : ; }
install snd-seq /sbin/modprobe --ignore-install snd-seq $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; /sbin/modprobe --quiet --use-blacklist snd-seq-oss ; : ; }
#
install snd-rawmidi /sbin/modprobe --ignore-install snd-rawmidi $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; : ; }
# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-emu10k1-synth ; }
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq ; }

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist saa7134-alsa ; : ; }
# Prevent abnormal drivers from grabbing index 0
options bt87x index=-2
options cx88_alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-us122l index=-2
options snd-usb-usx2y index=-2
options snd-usb-caiaq index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
# Keep snd-pcsp from being loaded as first soundcard
options snd-pcsp index=-2
```**dino99:** when I enter the command about reconfiguring You suggested, I get sth like this:

```
kuba@UBUNTU-PC:~$ sudo dpkg-reconfigure alsa
Package `alsa' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
/usr/sbin/dpkg-reconfigure: alsa is not installed
```Which seems kind of funny, because... well, I **have** alsa :P

And the command aplay -l gives the result:

```
kuba@UBUNTU-PC:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: ALC1200 Analog [ALC1200 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 1: ALC1200 Digital [ALC1200 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```So, as You can see, it **is** ALC1200, even though it's not listed in any of the docs You pointed out. I must say- I did my homework well before posting this topic about help ;)

I still have my hopes THIS high *pointing in the air somewhere above the head* for UBUNTU- I love this system and I believe that together we could sort it out :)

Waiting for another guidelines from You dear forumers!

[/I][B][COLOR=Black][SIZE=4]_[COLOR=Red]FIX OF POST![/COLOR]_[/SIZE] That's what happens, when You write with another reach for help without moving Your grey cells and trying out something else by Yourself ^^

[/COLOR][/B][COLOR=Black]Dear **lidex**, dear **dino99**- first of all, I have to thank You for Your help- without Your hints, I would simply never combine the ideas into one, solid solution. This is what happened to be the "crack".

As I said, I had my alsa-base.conf edited earlier, so that I could choose 5 channel output- let's call it that I enabled some features of the alsa driver on my sound card. BUT, when I added the line that **lidex** suggested, the card still thought it had those 5 channels to play, so it didn't let me change the single volume panels- it was sort of "all play or all mute"- which meant that the speakers of laptop were still playing, even with headphones plugged in.

So what had to be done, was simply to use another tweak into the sound card driver, so that it would think (probably) it has a variable channel. That is why I needed to make it (the driver) think I have a different card, so... I added in the end of alsa-base.conf those 5 lines:

[/COLOR][/COLOR]```
options snd-hda-intel model=targa-dig
options snd slots=snd-hda-intel
# u1Nb.u_BNWJ+LvyF:82801I (ICH9 Family) HD Audio Controller
alias snd-card-0 snd-hda-intel
options snd-hda-intel probe_mask=1
```[COLOR=Gray][COLOR=Black]

I would really suggest to post it somewhere on tops, cause as I searched the forums over the whole net, noone actually found the solution that would enable all the speakers on ALC1200 (which is subwoofer, front and rear left and right- total five of them), which would go mute when the sound would be played through the headphones jack.

Once more I want to thank You for help, and wish me luck with my mission of Open Source in the music world in Poland ^^ I'll keep You informed ;)

Cheers, Kuba G.
[/COLOR][/COLOR]

---

### Post by lidex on 2010-04-25
Good work! This ALC1200 codec has been a big pain. Please mark the thread as solved using the 'Thread Tools' link at top. Oh, and just to clarify, the additions to alsa-base.conf were the only changes you made?

---

### Post by LittleJakub on 2010-04-25
I am not 100% sure, maybe (cause I do not remember) I updated ALSA, or something of this sort... But, to make it certain- I am waiting for the Lynx to be officially released, and as soon as it happens I have planned a format of my hard drive and an install of fresh system- so then I will make sure that the change in alsa-base.conf is the only thing required for the fix.

Just one thing is a bit cranky, I will look into it when the official release is out- the mic proper settings and the general control of subwoofer volume. But for now- it's far better than it was ;) I'll keep You posted! :guitar:

---

### Post by LittleJakub on 2011-01-19
It's me again! Unfortunately, the problem returned in the new ubuntu 10.10- but this time, the trick I discovered doesn't do it's work... So my question is- isn't there anybody in Canonical itself to help us? :P

---

### Post by LittleJakub on 2011-01-19
It's me again! Unfortunately, the problem returned in the new ubuntu 10.10- but this time, the trick I discovered doesn't do it's work... So my question is- isn't there anybody in Canonical itself to help us? :P

---

### Post by lidex on 2011-01-19
Looks like a regression. You should file a bug.
Try running this command in a terminal for 10.04 or later:
```
ubuntu-bug audio
```
Reference the Ubuntu-Bug Audio link in my sig.

---

### Post by LittleJakub on 2011-02-18
K, something happened- and after applying my well working changes for 10.04, they started working for 10.10 after kernel update :) cheers!

---

