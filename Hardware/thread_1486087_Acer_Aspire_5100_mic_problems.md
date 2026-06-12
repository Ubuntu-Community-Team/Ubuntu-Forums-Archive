---
title: "Acer Aspire 5100 mic problems"
date: 2010-05-17
forum: Hardware
---

### Post by warriorofchaos20 on 2010-05-17
hey guys, so i just installed the new Lucid Lynx (10.04) and am really liking it so far with the little i've done, but i installed skype and my built-in microphone isn't working. in fact, i went to check stuff and it doesn't appear to be working at all...any advice? and please include easy to follow steps. thank you!

---

### Post by lidex on 2010-05-17
For Skype:
Try this. Use a terminal="Applications->Accessories->Terminal"
Enter these commands, one line at a time:
```
sudo add-apt-repository ppa:ubuntu-audio-dev/ppa
sudo apt-get update
sudo apt-get install linux-alsa-driver-modules-$(uname -r)
```
Reboot.

Get to know your mixers. 
**Alsamixer**
Using a Terminal="Applications->Accessories->Terminal"
```
 alsamixer 
```
Press <F6> to select the correct soundcard.
Press <F3> to show playback levels. <F4> selects capture levels [or use <Tab>]
Use the left/right arrow keys to select and up/down arrow keys to change levels. <M> to mute/unmute.

**Gnome-alsamixer**
Using Alt+F2 run dialog
```
 gnome-alsamixer 
```
Use 'Edit -> Sound Card Properties' menu to enable elements.
Soundcard tab to select / adjust levels.

---

### Post by warriorofchaos20 on 2010-05-20
i did all that and it doesn't seem to have helped at all...i tried using sound recorder and it didn't seem to work and i tried Skype but that doesn't work, and the only Audio options available are PulseAudio...any other suggestions?

---

### Post by lidex on 2010-05-20
Is this an upgrade? 
Can you post the output of these terminal commands for me please:
```
uname -a
aplay -l
cat /proc/asound/version
head -n 1 /proc/asound/card*/codec#* 
```
Terminal="Applications->Accessories->Terminal"
**Also helpful is the make/model of your PC/Laptop.**
Please post text output using code tags (the # in toolbar)

---

### Post by warriorofchaos20 on 2010-05-21
I'm using the Acer Aspire 5100 and here's the code in the order you asked for them:
```
atwilly@musical-bumJR:~$ uname -a
Linux musical-bumJR 2.6.32-22-generic #33-Ubuntu SMP Wed Apr 28 13:28:05 UTC 2010 x86_64 GNU/Linux

```

```
twilly@musical-bumJR:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: ALC883 Analog [ALC883 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 1: ALC883 Digital [ALC883 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

```
twilly@musical-bumJR:~$ cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.23.
Compiled on May 19 2010 for kernel 2.6.32-22-generic (SMP).

```

```
twilly@musical-bumJR:~$ head -n 1 /proc/asound/card*/codec#*
==> /proc/asound/card0/codec#0 <==
Codec: Realtek ALC883

==> /proc/asound/card0/codec#1 <==
Codec: Conexant ID 2c06

```

hope this helps...

---

### Post by lidex on 2010-05-21
Using a Terminal="Applications->Accessories->Terminal"
Open this file for editing:
```
 gksudo gedit /etc/modprobe.d/alsa-base.conf 
```
Insert this line at the bottom:
```
 options snd-hda-intel model=acer 
```
Save. Close. Reboot. Check your levels in alsamixer.
```
 alsamixer 
```
Press <F6> to select the correct soundcard.
Press <F3> to show playback levels. <F4> selects capture levels [or use <Tab>]
Use the left/right arrow keys to select and up/down arrow keys to change levels. <M> to mute/unmute.
Go to "System ->Preferences ->Sound" and make sure the correct soundcard is default.

---

### Post by phillips321 on 2010-05-21
The machine got a GMA500 chipset? Mic input doesn't work on these chipsets yet...

---

### Post by aqua03 on 2010-11-05
For those looking for the solution to getting your Acer Aspire 5100 mic to work, this is the thread that solved the problem for me.  After looking through 3 or 4 threads I found this thread.  I followed lidex's directions and my mic now works!

---

### Post by DutchieR on 2011-02-04
Exact same machine, Aspire 5100, Ubuntu 10.10 latest build.
Latest version Skype (Beta) 2.1.0.81

Did all the things above, no result
Still same problem, Skype test call records nothing.

But also cannot change any setting in Skype Sound Devices options which are all set to PulseAudio Server (local).

All the settings above seem to use ALSA as sound server so I guess I have to convince Skype to use ALSA, but how? (BTW, sound output is OK, even if Skype is configured for PulseAudio).

Suggestions?

---

### Post by lidex on 2011-02-04
> **DutchieR said:**
> Exact same machine, Aspire 5100, Ubuntu 10.10 latest build.
Latest version Skype (Beta) 2.1.0.81

Did all the things above, no result
Still same problem, Skype test call records nothing.

But also cannot change any setting in Skype Sound Devices options which are all set to PulseAudio Server (local).

All the settings above seem to use ALSA as sound server so I guess I have to convince Skype to use ALSA, but how? (BTW, sound output is OK, even if Skype is configured for PulseAudio).

Suggestions?

You did this:
[http://ubuntuforums.org/showpost.php?p=10427507&postcount=30](http://ubuntuforums.org/showpost.php?p=10427507&postcount=30)

---

### Post by DutchieR on 2011-03-29
> **lidex said:**
> You did this:
[http://ubuntuforums.org/showpost.php?p=10427507&postcount=30](http://ubuntuforums.org/showpost.php?p=10427507&postcount=30)
Still nothing. 
In Pulse I seem to have 3 microphones (Mic1, Mic 2, LineIn). Mic1 and 2 both don't seem to pick up any sound. I haven tried LineIn since that is an external mic which I don have/want.

---

### Post by lidex on 2011-03-31
> **DutchieR said:**
> Still nothing. 
In Pulse I seem to have 3 microphones (Mic1, Mic 2, LineIn). Mic1 and 2 both don't seem to pick up any sound. I haven tried LineIn since that is an external mic which I don have/want.
Do you get mic input in 'Sound Recorder'?

Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]

---

### Post by DutchieR on 2011-04-01
> **lidex said:**
> Do you get mic input in 'Sound Recorder'?

Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]
Hi Lidex
No signs of sound in Sound Recorder whatsoever.
The link to the ALSA info is [http://www.alsa-project.org/db/?f=145245c4ff04eec2fdc40eaf0d104f9a4fb7a58c]("http://www.alsa-project.org/db/?f=145245c4ff04eec2fdc40eaf0d104f9a4fb7a58c")

Test call in Skype also records nothing (obviously)

Thanks for the help in advance. This bug is bugging me for ages now ;)

---

### Post by lidex on 2011-04-01
Your alsa install is screwy. Let's re-install. First remove the switch you added to alsa-base.conf. Next:
```
sudo aptitude --purge reinstall linux-sound-base alsa-base alsa-utils linux-image-`uname -r` linux-ubuntu-modules-`uname -r` libasound2
```
**Reboot.**

For a 'command not found' error simply install aptitude:
```
sudo apt-get install aptitude
```

---

### Post by DutchieR on 2011-04-04
> **lidex said:**
> Your alsa install is screwy. Let's re-install. First remove the switch you added to alsa-base.conf. Next:
```
sudo aptitude --purge reinstall linux-sound-base alsa-base alsa-utils linux-image-`uname -r` linux-ubuntu-modules-`uname -r` libasound2
```
**Reboot.**

For a 'command not found' error simply install aptitude:
```
sudo apt-get install aptitude
```
Hi Lidex, 
Done that, no audible change so far.
New ALSA info is here: [http://www.alsa-project.org/db/?f=f6b6bb45a8ddd846150afd224356ca6ac26a8247]("http://www.alsa-project.org/db/?f=f6b6bb45a8ddd846150afd224356ca6ac26a8247")

Next steps?
Something I don grasp is that I thought PulseAudio replaced ALSA in Ubuntu 10.10 or are these two separate mechanisms?

---

### Post by lidex on 2011-04-04
You're missing something:
```
sudo aptitude install alsa-utils
```

---

### Post by DutchieR on 2011-04-04
> **lidex said:**
> You're missing something:
```
sudo aptitude install alsa-utils
```
Never had such a quick reply, great!!!
Here is the new script output. [Your ALSA information is located at http://www.alsa-project.org/db/?f=6dfad9ea28850fa8726f34b74f30485d048ae539]("Your ALSA information is located at http://www.alsa-project.org/db/?f=6dfad9ea28850fa8726f34b74f30485d048ae539")
Or should I reboot first? Ubuntu didn tell me to do so, so I didn't.

And now?

---

### Post by lidex on 2011-04-04
Edit this file:
```
 gksudo gedit /etc/modprobe.d/alsa-base.conf 
```
Change this line:
```
options snd-hda-intel model=acer
```
To this:
```
options snd-hda-intel probe_mask=1
```
Reboot and post these outputs:
```
aplay -l
```
```
dmesg | grep -C1 -E 'ALSA|HDA|HDMI|sound|hda.codec|hda.intel'
```

---

### Post by DutchieR on 2011-04-05
> **lidex said:**
> Edit this file:
```
 gksudo gedit /etc/modprobe.d/alsa-base.conf 
```
Change this line:
```
options snd-hda-intel model=acer
```
To this:
```
options snd-hda-intel probe_mask=1
```
Reboot and post these outputs:
```
aplay -l
```
```
dmesg | grep -C1 -E 'ALSA|HDA|HDMI|sound|hda.codec|hda.intel'
```
Here is the output (sorry for dutch interface language, I assume you'll understand what it should be:

**** Lijst van PLAYBACK hardware-apparaten ****
kaart 0: SB [HDA ATI SB], apparaat 0: ALC883 Analog [ALC883 Analog]
  Sub-apparaten: 0/1
  Sub-apparaat #0: subdevice #0
kaart 0: SB [HDA ATI SB], apparaat 1: ALC883 Digital [ALC883 Digital]
  Sub-apparaten: 1/1
  Sub-apparaat #0: subdevice #0
rob@UBU-Aspire-5100:~$ dmesg | grep -C1 -E 'ALSA|HDA|HDMI|sound|hda.codec|hda.intel'
[   18.808463] piix4_smbus 0000:00:14.0: SMBus Host Controller at 0x8410, revision 0
[   18.808625] HDA Intel 0000:00:14.2: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   18.823637] [drm] radeon: ring at 0x00000000AE000000
--
[   19.054337] sr 2:0:0:0: Attached scsi generic sg1 type 5
[   19.056165] hda_codec: ALC883: BIOS auto-probing.
[   19.073751] [drm] fb mappable at 0xD0040000

---

### Post by lidex on 2011-04-05
OK, that made a difference. Check your mixer settings, sound preferences, profile, etc.

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

Then go to 'Sound Preferences' to select the correct device and mic ('Connector' option) and unmute your mic in 'Input' tab.
Make sure you have selected a profile with 'duplex' or 'analog input' for the correct sound device on the 'Hardware' tab.
Use Pulse Audio Volume Control (pavucontrol) to unlock stereo sliders for the mic in 'Input Devices' tab. Drag the right slider down to zero. 

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

---

### Post by DutchieR on 2011-04-11
Done everything .... still no result with the internal mic, getting desperate. Starting to doubt that I may misunderstand something. Nonetheless.. there seem to be many more users strugling with similar problems. So, therefore I also attached a USB micro microphone which works like a charm in both Ubuntu as well as with Skype. For the purpose of bugfixing (and using Skype when I have no USB mic available) however I removed it again.
 
Skype seems to get in touch with PulseAudio but doesn't get any sound. Testcalls playback without having recorded anything. Als PA-volume meter doesn't get any input.
Attached are some screendumps. Maybe that helps?

---

### Post by lidex on 2011-04-13
@DutchieR
Have you tried enabling the other capture?
What profile do you have selected in 'Sound Preferences'?
What is your amixer output:
```
amixer
```

---

