---
title: "No sound from laptop speaker, after some troubleshooting no sound at all"
date: 2010-09-27
forum: Hardware
---

### Post by usmanhalalit on 2010-09-27
Hi,
This forum seems very helpful.

I am using Ubuntu 10.04 LTS in HP Compaq Presario CQ42. When I first installed there was no sound from my laptop's speaker but headphones worked fine. I googled for solution and found this thread [http://ubuntuforums.org/showthread.php?t=1073090](http://ubuntuforums.org/showthread.php?t=1073090) . I did accordingly as first post of the thread says, but after doing this I totally lost sound, System > Preferences > Sound > Hardware shows empty list. Volume icon near clock changed and shows Speaker and 3 dashes--- (I have attached screenshot). Laptop speakers and soundcard work fine on windows. 

Please help me, I am really stuck for few days.

---

### Post by quixote on 2010-09-29
I'm not sure what you did, but my guess would be that reinstalling sound might fix it.  However doing that is not simple :(.  There are issues between alsa and pulseaudio and all sorts of complications.  One of the sound gurus is "lidex".  Search for that name on the forums together with "presario" and see what comes up.  Hopefully the solution! :D

---

### Post by P4man on 2010-09-30
Im just guessing here, that you dont know vim and you accidentally removed or created an empty alsa-base file?  Vim is an advanced (and at the same time archaic) text editor. If you are not familiar with it, just use gedit (like notepad).

Also, in 10.04 at least,  the file to edit is actually called 
/etc/modprobe.d/alsa-base**.conf**

Just edit it with gedit, but you need sudo privilidges so run

> sudo gedit /etc/modprobe.d/alsa-base.conf


There try adding the "options snd_hda_intel model=hp-dv5" line. If you created an empty "/etc/modprobe.d/alsa-base" file, you probably want to remove it.

---

### Post by usmanhalalit on 2010-10-03
> **quixote said:**
> I'm not sure what you did, but my guess would be that reinstalling sound might fix it.  However doing that is not simple :(.  There are issues between alsa and pulseaudio and all sorts of complications.  One of the sound gurus is "lidex".  Search for that name on the forums together with "presario" and see what comes up.  Hopefully the solution! :D

Thanks, I am searching for it, I will let you know of any progress.

---

### Post by usmanhalalit on 2010-10-03
> **P4man said:**
> Im just guessing here, that you dont know vim and you accidentally removed or created an empty alsa-base file?  Vim is an advanced (and at the same time archaic) text editor. If you are not familiar with it, just use gedit (like notepad).

Also, in 10.04 at least,  the file to edit is actually called 
/etc/modprobe.d/alsa-base**.conf**

Just edit it with gedit, but you need sudo privilidges so run




There try adding the "options snd_hda_intel model=hp-dv5" line. If you created an empty "/etc/modprobe.d/alsa-base" file, you probably want to remove it.

Thanks for your response. I did it with gedit.

I tried ad options snd_hda_intel model=hp-dv5 in alsa-base.conf but no luck yet :(

Is there any other solution?

Thanks...

---

### Post by quixote on 2010-10-03
It's probably a good idea to make sure your alsa-base.conf file is good, so you may want to add an attachment here with the whole file.  Just to make sure there isn't something obvious there tripping you up.

There's a lot of info in [this ubuntu wiki]("https://help.ubuntu.com/community/HdaIntelSoundHowto"), but I'm not familiar enough with sound issues to be sure any of it applies to you.  It might be worth a read, though.

---

### Post by lidex on 2010-10-03
Can you bring me up to speed please?
Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.

---

### Post by usmanhalalit on 2010-10-04
Thank you Lidex,
I am amazed by the way Ubuntians are helping me.

Here is the link
[http://www.alsa-project.org/db/?f=688aa3b2e330b40ad160e677f152a1ba03d02673](http://www.alsa-project.org/db/?f=688aa3b2e330b40ad160e677f152a1ba03d02673)

---

### Post by lidex on 2010-10-05
> **usmanhalalit said:**
> Thank you Lidex,
I am amazed by the way Ubuntians are helping me.

Here is the link
[http://www.alsa-project.org/db/?f=688aa3b2e330b40ad160e677f152a1ba03d02673](http://www.alsa-project.org/db/?f=688aa3b2e330b40ad160e677f152a1ba03d02673)

I'm not surprised you lost audio, your alsa install is borked. Try a re-install. Using a Terminal="Applications->Accessories->Terminal"
```
sudo apt-get update
sudo apt-get upgrade
```
```
sudo apt-get purge linux-sound-base alsa-base alsa-utils

```
```
sudo apt-get install linux-sound-base alsa-base alsa-utils gdm ubuntu-desktop

```
**Reboot.**
**gdm and ubuntu-desktop usually get taken out in the process, so we add them back**

---

### Post by usmanhalalit on 2010-10-06
> **lidex said:**
> I'm not surprised you lost audio, your alsa install is borked. Try a re-install. Using a Terminal="Applications->Accessories->Terminal"
```
sudo apt-get update
sudo apt-get upgrade
```
```
sudo apt-get purge linux-sound-base alsa-base alsa-utils

```
```
sudo apt-get install linux-sound-base alsa-base alsa-utils gdm ubuntu-desktop

```
**Reboot.**
**gdm and ubuntu-desktop usually get taken out in the process, so we add them back**

Hi,
Thanks for your support.
I tried this, but no luck yet. Now another problem; system gets fully hanged very often, even the mouse pointer doesn't move. :(

Regard,
Usman.

---

### Post by lidex on 2010-10-06
*usmanhalalit*
Can you run the alsa-info script again so we can see the changes?

---

### Post by starleaf1 on 2010-10-07
> **P4man said:**
> Im just guessing here, that you dont know vim and you accidentally removed or created an empty alsa-base file?  Vim is an advanced (and at the same time archaic) text editor. If you are not familiar with it, just use gedit (like notepad).

Also, in 10.04 at least,  the file to edit is actually called 
/etc/modprobe.d/alsa-base**.conf**

Just edit it with gedit, but you need sudo privilidges so run




There try adding the "options snd_hda_intel model=hp-dv5" line. If you created an empty "/etc/modprobe.d/alsa-base" file, you probably want to remove it.


Hello, I have similar problem here. No sound, not from the internal speaker, not from external speaker.
I tried this solution, and it DID give me sound, but only on the login screen. It seems like the solution didn't apply to any user but root.
Here's my complete content of the file, in case it helps:

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
#This is the line you suggest to add
options snd_hda_intel model=hp-dv5
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
# Keep snd-pcsp from being loaded as first soundcard
options snd-pcsp index=-2
```

---

### Post by lidex on 2010-10-07
> **starleaf1 said:**
> Hello, I have similar problem here. No sound, not from the internal speaker, not from external speaker.
I tried this solution, and it DID give me sound, but only on the login screen. It seems like the solution didn't apply to any user but root.
Here's my complete content of the file, in case it helps:


These options going to alsa-base.conf are hardware specific.Need your info. Can you post the output of these terminal commands for me please:
```
uname -a
aplay -l
dpkg -l | grep "alsa"
head -n 1 /proc/asound/card*/codec#* 
```
Terminal="Applications->Accessories->Terminal"
**Please also include the make/model of your PC/Laptop.**
Please post text output using code tags (the # in toolbar)

---

### Post by usmanhalalit on 2010-10-08
> **lidex said:**
> *usmanhalalit*
Can you run the alsa-info script again so we can see the changes?

I am sorry I had to re-install Ubuntu as it used to stop responding frequently. Now I have my sound OK with headphone or external speaker but no sound from laptop speaker.

Thanks,
Usman

---

### Post by lidex on 2010-10-08
> **usmanhalalit said:**
> I am sorry I had to re-install Ubuntu as it used to stop responding frequently. Now I have my sound OK with headphone or external speaker but no sound from laptop speaker.

Thanks,
Usman
OK. Same request. Please run the alsa-info script.

---

### Post by usmanhalalit on 2010-10-08
> **lidex said:**
> OK. Same request. Please run the alsa-info script.

OK, here is the link:

[http://www.alsa-project.org/db/?f=43f73daeae1a2391be91b2547ab68108a9d353dc](http://www.alsa-project.org/db/?f=43f73daeae1a2391be91b2547ab68108a9d353dc)

---

### Post by lidex on 2010-10-08
OK, let's see if this helps. I want you to add four lines to alsa-base.conf. 
Using a Terminal="Applications->Accessories->Terminal"
Open this file for editing:
```
 gksudo gedit /etc/modprobe.d/alsa-base.conf 
```
Insert these lines at the bottom:
```
options snd slots=snd-hda-intel
options snd-hda-intel model=hp-hdx
alias snd-card-0 snd-hda-intel
options snd-hda-intel enable_msi=1  
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

### Post by usmanhalalit on 2010-10-10
Thanks for your continuous support.
But its not working yet.

---

### Post by lidex on 2010-10-10
> **usmanhalalit said:**
> Thanks for your continuous support.
But its not working yet.

Time to upgrade your alsa install. Use the link in my sig.
First remove the 4 lines added to alsa-base.conf

If that doesn't help, add these lines:
```
alias snd-card-0 snd-hda-intel
alias sound-slot-0 snd-hda-intel
options snd-hda-intel model=m51va
options snd-hda-intel enable-msi=1
```

Save & Reboot.

---

### Post by ngaio on 2010-10-11
> **lidex said:**
> 
```
options snd slots=snd-hda-intel
options snd-hda-intel model=hp-hdx
alias snd-card-0 snd-hda-intel
options snd-hda-intel enable_msi=1  
```


I had no sound output via the external speakers on my Thinkpad T400s (with Intel ICH9M / Conexant CX20585), on my fresh install of 10.10 (Maverick). Sound worked ok in 10.04. I added the following:

```
options snd slots=snd-hda-intel
options snd-hda-intel model=thinkpad
alias snd-card-0 snd-hda-intel
options snd-hda-intel enable_msi=1
```

The sound now works - thanks! I think a bug should be filed, but I don't have the knowledge necessary to file a proper bug report. This alsa stuff can be pretty complex! If you think I should go ahead and submit something, let me know.

---

### Post by lidex on 2010-10-11
> **ngaio said:**
> I had no sound output via the external speakers on my Thinkpad T400s (with Intel ICH9M / Conexant CX20585), on my fresh install of 10.10 (Maverick). Sound worked ok in 10.04. I added the following:

```
options snd slots=snd-hda-intel
options snd-hda-intel model=thinkpad
alias snd-card-0 snd-hda-intel
options snd-hda-intel enable_msi=1
```

The sound now works - thanks! I think a bug should be filed, but I don't have the knowledge necessary to file a proper bug report. This alsa stuff can be pretty complex! If you think I should go ahead and submit something, let me know.

A regression should absolutely be reported. First return your system to the default (non-working) state. Try running this command in a terminal for 10.04 or later:
```
ubuntu-bug audio
```
Follow the prompts to file a bug report. Once that's done post back to the bug report what you did to get it to work so they can fix it upstream. The devs will ask you for any other info they might need.

---

### Post by starleaf1 on 2010-10-12
> **lidex said:**
> These options going to alsa-base.conf are hardware specific.Need your info. Can you post the output of these terminal commands for me please:
```
uname -a
aplay -l
dpkg -l | grep "alsa"
head -n 1 /proc/asound/card*/codec#* 
```Terminal="Applications->Accessories->Terminal"
**Please also include the make/model of your PC/Laptop.**
Please post text output using code tags (the # in toolbar)

Thank you for your response. Here's what you've requested.

```
riocark@riocark-laptop:~$ uname -a
Linux riocark-laptop 2.6.32-25-generic #44-Ubuntu SMP Fri Sep 17 20:26:08 UTC 2010 i686 GNU/Linux
riocark@riocark-laptop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC259 Analog [ALC259 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Generic [HD-Audio Generic], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
riocark@riocark-laptop:~$ dpkg -l | grep "alsa"
ii  alsa-base                                      1.0.22.1+dfsg-0ubuntu3                          ALSA driver configuration files
ii  alsa-utils                                     1.0.22-0ubuntu5                                 ALSA utilities
ii  bluez-alsa                                     4.60-0ubuntu8                                   Bluetooth audio support
ii  gstreamer0.10-alsa                             0.10.28-1                                       GStreamer plugin for ALSA
ii  linux-alsa-driver-modules-2.6.32-25-generic    2.6.32-25.201010051600                          Ubuntu-supplied Linux modules for version 2.
riocark@riocark-laptop:~$ head -n 1 /proc/asound/card*/codec#*
==> /proc/asound/card0/codec#0 <==
Codec: Realtek ALC259

==> /proc/asound/card1/codec#0 <==
Codec: ATI R6xx HDMI

```

---

### Post by usmanhalalit on 2010-10-13
OK lidex.

Thanks everyone for your help. The opensource community really rocks.

---

### Post by trailerkn on 2010-10-13
Got the same problem, and i had the same problem on win7, dosent seem to help in ubuntu either. Cant fix it either.

---

### Post by ccwillrun on 2011-12-17
> **lidex said:**
> OK, let's see if this helps. I want you to add four lines to alsa-base.conf. 
Using a Terminal="Applications->Accessories->Terminal"
Open this file for editing:
```
 gksudo gedit /etc/modprobe.d/alsa-base.conf 
```
Insert these lines at the bottom:
```
options snd slots=snd-hda-intel
options snd-hda-intel model=hp-hdx
alias snd-card-0 snd-hda-intel
options snd-hda-intel enable_msi=1  
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

Worked like a charm. Thanks Lidex.

---

