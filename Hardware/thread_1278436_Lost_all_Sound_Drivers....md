---
title: "Lost all Sound Drivers..."
date: 2009-09-29
forum: Hardware
---

### Post by NV FISH on 2009-09-29
(supposed to read "Devices"...not drivers)

Hello, 
I am new to the forums and somewhat new to Ubuntu and Linux. My first adventure in Linux was frustrating but I found myself wanting to try it again...so I did and not have 9.04 running...ABSOLUTELY LOVE IT!

However....once a gain a frustration has emerged:

I have an ASUS G50Vt with a 82801I (ICH9 Family) HD Audio Controller

Regular speakers worked decent at the start but seemed to be at 50% which I was trying to adapt to (checked all the sound volume locations and set to full but still low) when I attempted to use headphones and discovered that they dont work.

Google being a friend I went a looking and found ([http://www.linlap.com/wiki/asus+g50v](http://www.linlap.com/wiki/asus+g50v)) that this is a problem with this particular laptop. So I tried to follow the fix it instructions but had to google more stuff to be able to do what it says (I dont know where most things are in Ubuntu) and somewhere along the line i lost all of my sound devices in the Sound-Volume Control Area except for:

Capture: Monitor of Null Output (Pulse Audio Mixer)
and
Playback: Null Output (Pulse Audio Mixer)

Trying to use what I had I discovered that these failed....no sound though they seem to be turned up. Installing Pulse Audio Device Chooser showed me that they are muted...even though they are not selected as muted.

Anyway...I have tried adding Ubuntu Studio thing-a-ma-bobs to no avail.....PLEASE HELP!????

How do I get my sound devices back?

I am loving 9.04 and I spent some time setting it up like a like it and would hate to have to reinstall.

Thanks

FISH

---

### Post by lidex on 2009-09-29
First follow this guide using relevant steps:
[http://www.ubuntugeek.com/sound-solutions-for-ubuntu-904-jaunty-users.html]("http://www.ubuntugeek.com/sound-solutions-for-ubuntu-904-jaunty-users.html")
Reboot

Next I would suggest updating alsa. The latest version fixes a lot of compatibility issues.

---

### Post by lidex on 2009-09-29
To update alsa:
[http://ubuntuforums.org/showthread.php?p=6589810#post6589810]("http://ubuntuforums.org/showthread.php?p=6589810#post6589810")

Sound troubleshooting:
[https://help.ubuntu.com/community/SoundTroubleshooting]("https://help.ubuntu.com/community/SoundTroubleshooting")

---

### Post by NV FISH on 2009-09-29
Hello Lidex and thanks for replying.

I did visit this page and start the process prior to the problem of losing all my devices...in fact I believe this may have been what caused it? Anyway...I went through the steps again and everything loaded but I still have no devices to choose from other that the ones I mentioned above.

So basically when you click on the Sound Icon at top right and click on Volume Control and then the down arrow next to device....all I have to choose from is:

Capture: Monitor of Null Output (Pulse Audio Mixer)
and
Playback: Null Output (Pulse Audio Mixer)


 I also installed the new alsa drivers this morning and now show:

Advanced Linux Sound Architecture Driver Version 1.0.20.
Compiled on Sep 29 2009 for kernel 2.6.28-15-generic (SMP).

FISH

---

### Post by lidex on 2009-09-29
Try the sound troubleshooting link. So many things it could be - need to narrow it down.

---

### Post by NV FISH on 2009-09-29
working it....sound card is not recognized is what I have found so far.

also this:
Pulseaudio:
      Installed - Yes (/usr/bin/pulseaudio)
      Running - Yes

ESound Daemon:
      Installed - Yes (/usr/bin/esd)
      Running - No

Jack:
      Installed - Yes (/usr/bin/jackd)
      Running - No


!!Soundcards recognised by ALSA
!!-----------------------------

--- no soundcards ---

still troubleshooting

---

### Post by NV FISH on 2009-09-29
OK...when its asking me for my Module I have this too choose from:

!!All Loaded Modules
!!------------------

Module
binfmt_misc
ppdev
bridge
stp
bnep
input_polldev
lp
parport
snd_hda_codec
snd_hwdep
snd_pcm_oss
snd_mixer_oss
snd_pcm
snd_seq_oss
snd_seq_midi_event
snd_seq
arc4
uvcvideo
snd_timer
snd_seq_device
ecb
compat_ioctl32
video
snd
psmouse
asus_laptop
iwlagn
iwlcore
sdhci_pci
pcspkr
serio_raw
videodev
output
led_class
mac80211
soundcore
joydev
intel_agp
iTCO_wdt
iTCO_vendor_support
sdhci
nvidia
v4l1_compat
snd_page_alloc
cfg80211
usbhid
ohci1394
ieee1394
r8169
mii
fbcon
tileblit
font
bitblit
softcursor

---

### Post by NV FISH on 2009-09-29
Found this:

[   10.695143] synaptics was reset on resume, see synaptics_resume_reset if you have trouble on resume
[   10.723545] snd_hda_intel: Unknown parameter `G50V'
[   10.804861] lp: driver loaded but no devices found

the unknown parameter may be causing the issue?

---

### Post by NV FISH on 2009-09-29
OK. 

I am at an impasse with the Trouble Shooting....I have no ALSA Module loaded.

Tried reinstalling...nothing

How do we correct this?

---

### Post by NV FISH on 2009-09-29
well....it seems my sound card is not among the supported ones....it worked somewhat at first though.

oh well

---

### Post by lidex on 2009-09-29
That parameter is probably an issue. Did you find the correct driver for your soundcard? Try this using your driver name:> Manually starting the Audio driver

Open a terminal and type sudo modprobe snd-[NAME OF YOUR SOUNDCARD'S DRIVER]. For example, my driver is a via82xx so I would type, sudo modprobe snd-via82xx. 

Then check for sound.

Just saw your last post. What is your soundcard model?

---

### Post by lidex on 2009-09-29
Looked at that website you referenced. According to that alsa should be supported. You may need to manually load the driver using the /etc/modules file.Run the Audio Tester for more help.

[http://www.linwik.com/wiki/audio+tester]("http://www.linwik.com/wiki/audio+tester")

---

### Post by NV FISH on 2009-09-29
82801I (ICH9 Family) HD Audio Controller intel

i have tried using the "start over command" which is supposed to get you back to square 1....nothing

USB audio is working and speakers at start up are good prior to OS

---

### Post by lidex on 2009-09-29
Alright, this is going to take some work. Try this:
> "Just before I went to sleep last night, I found some Other settings by searching for "options snd-hda-intel"... and Someone else had some additional settings that I added to /etc/modprobe.d/alsa-base:

options snd-hda-intel model=3stack-dig
options snd-hda-intel enable_msi=1
options snd-hda-intel single_cmd=1

(add to the bottom, save and reboot)

If no joy check out these threads:
[http://ubuntuforums.org/showthread.php?t=940689]("http://ubuntuforums.org/showthread.php?t=940689")
[http://ubuntuforums.org/showthread.php?t=1199144]("http://ubuntuforums.org/showthread.php?t=1199144")
[http://ubuntuforums.org/showthread.php?t=1153030]("http://ubuntuforums.org/showthread.php?t=1153030")
[http://ubuntuforums.org/showthread.php?t=1101993]("http://ubuntuforums.org/showthread.php?t=1101993")

---

### Post by NV FISH on 2009-09-29
how do you save?

---

### Post by NV FISH on 2009-09-29
no avail

---

### Post by lidex on 2009-09-29
In terminal:
```
sudo gedit /etc/modprobe.d/alsa-base.conf
``` that opens file for editing. Add the following to the end of file
```
options snd-hda-intel model=3stack-dig
options snd-hda-intel enable_msi=1
options snd-hda-intel single_cmd=1
```
Click on save button in gedit. Close. Reboot.

---

### Post by NV FISH on 2009-09-29
Roger..its complete and verified that its in there...still nothing. I reviewed the other treads but nothing worked their as well. I will just reinstall. Sucks but oh well. Sound works on the CD Ubuntu still so I know its just a setting. I will have to be careful this time around.

---

