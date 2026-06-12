---
title: "HP Pavilion dv6 no sound issue"
date: 2009-10-20
forum: Hardware
---

### Post by x2chevelle09 on 2009-10-20
Okay so I know that there are hundreds of these similar posts concerning no sound and let me assure you...I've gone through most of them and at least 15 different methods of trying to obtain ANY sound.

I currently have Ubuntu 9.04 Jaunty dual installed with Vista on my Hp Pavilion Dv6 laptop.  everything works great except for the no sound issue.  This 'no sound issue' includes:

no system sounds
no media (movies/music) sounds 
and I believe, but am unsure, that there is no sound capturing occuring either

Here are my sound card hardware specs:

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: STAC92xx Digital [STAC92xx Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

I also have alsamixer v1.0.20 installed and this is what it looks like in the terminal:

Card: PulseAudio
Chip: PulseAudio
View:  Playback  Capture [All]
Item: Capture

when i run alsa mixer from the menu it says:
HDA Intel : IDT 92HD75B3X5
(with a bunch of volume options here)

and below that:
HDA ATI HDMI : ATI R6xx HDMI
with the option to un/select IEC958

I also have Pulse Audio Device chooser v0.9.14 installed and I am using the default values:
Default Sink         alsa_output.pci_8086_293e_sound_card_0_alsa_playback_0
Default Source     alsa_input.pci_8086_293e_sound_card_0_alsa_capture_0

I go into Volume Control of Pulse Audio and select the tab Output Devices and this is what is shown:
HDA Intel -STAC92xx Analog
(now when i have a music file or when a sound SHOULD play due to my system preferences running the volume bar moves, so it obviously registering the fact that audio is being played)

I also have a Virtual Device in this tab that follows this same pattern, but changes nothing

Also, when I go to the PulseAudio Manager and click the clients tab I have 
'ALSA plug-in [python 2.6]' flashing repeatedly
_________________________________________________________________________
Now when I open preferences in the volume control I have a lot of options:

HDA Intel (Alsa mixer) -devices: Master, PCM, Front, Surround

HDA ATI HDMI (Alsa mixer) -has no devices to control

IDT 92HD75b3X5 (OSS Mixer) -devices: Volume, In-gain, Digital

Playback: Simultaneous output to HDA Intel -STAC92xx Analog (PulseAudio Mixer) -devices: Master

Playback HDA Intel -STAC92xx Analog (PulseAudio Mixer) -devices: Master

Capture: Monitor Source of Simultaneous output to HDA Intel -STAC92xx Analog (PulseAudio Mixer) -devices: Master

Capture: Monitor of  HDA Intel -STAC92xx Analog (PulseAudio Mixer) -devices: Master

Capture: HDA Intel -STAC92xx Analog (PulseAudio Mixer) -devices: Master

I have no idea which one I should be using (if its necessary to even select any of these)
________________________________________________________________________
If more hardware/software info is needed please let me know and I will provide it

Now here is what I have done to try to get my audio working:

I have reinstalled Alsa Mixer numerous times and have tried multiple combinations in editing the alsa-base.conf, all which have done nothing (yes I rebooted the system ever time)

I have tried creating virtual devices using Pulse Audio.

Nothing is Muted...this is always mentioned in responses, let me assure you, I have checked and rechecked, and rechecked, and rechecked, and then checked again to make sure NOTHING is muted.

I have tried downloading alsa-driver-snapshot.tar.gz and installing it bc I read that my current sound card isn't compatible with Alsa and this would fix that (it didnt)

I have also tried alsa-driver-unstable-snapshot.tar.gz but to no avail

I have tried upgrading to alsa-driver-1.0.21.tar.bz2 (no sound still)

I have rewritten my alsa-base.conf file numerous times - (this is my current file)
options snd-pcsp index=-2
alias snd-card-0 snd-hda-intel
alias sound-slot-0 snd-hda-intel
options snd-hda-intel model=hp-m4
options snd-hda-intel enable_msi=1
options snd-hda-intel model=hp-m4 enable_msi=1

don't ask me what all these things are or how they relate to MY sound card...its gotten to the point where I'm copying and pasting from tutorials that may possibly help
_________________________________________________________________________

Anyways, thats pretty much the sum of everything...I've spent at least 14 hours in the past 2 days trying to solve this problem...I am obviously overlooking something.

Any and all help would be very much appreciated!

---

### Post by bryanagee on 2009-10-24
I had the same issue with 9.04 on my dv6-1230us. Upgrading to 9.10 beta fixed that, but I now have the issue where my speakers don't turn off when the headphones are plugged in (see [this thread]("http://ubuntuforums.org/showthread.php?t=806620")) and I haven't find the right model.

So if you can afford to upgrade, I guess only out-loud sound is better than none.

---

### Post by x2chevelle09 on 2009-10-27
> **bryanagee said:**
> I had the same issue with 9.04 on my dv6-1230us. Upgrading to 9.10 beta fixed that, but I now have the issue where my speakers don't turn off when the headphones are plugged in (see [this thread]("http://ubuntuforums.org/showthread.php?t=806620")) and I haven't find the right model.

So if you can afford to upgrade, I guess only out-loud sound is better than none.

...I love you...works exactly as you describe it! Thank you so much!  I will post a solution to the headphone/speaker problem if I can figure it out.

Once again, many thanks!

---

### Post by bryanagee on 2009-10-27
No worries. On the headphone issue, I've tried:
[LIST]
[*]hp-dv5
[*]hp-laptop
[*]dellm4-2
[/LIST]
and no joy. I'll post when I've found the right model, unless someone beats me to it. Good luck!

---

### Post by nah40 on 2009-10-27
this worked for me.

[http://www.ubuntugeek.com/sound-solutions-for-ubuntu-904-jaunty-users.html#more-1301](http://www.ubuntugeek.com/sound-solutions-for-ubuntu-904-jaunty-users.html#more-1301)

---

### Post by faderjockey on 2009-11-01
Well I has sound working in 9.04 now in 9.10 I have no sound...
HP Dv5...

I have to use a mouse. Because now I also lost the touchpad..and when I open an app to use the camera like Skype or cheese webcam.. The Laptop crashes and reboots. 

When I close the lid and go to bed.. Next morning it's rebooted for no reason,

And everything is sooooo Slow!!! Takes time to click on anything..
9.04 was running so much better... 

Why didn't I wait longer on this update??? Stupid!!!

---

