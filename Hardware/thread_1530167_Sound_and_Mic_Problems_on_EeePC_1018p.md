---
title: "Sound and Mic Problems on EeePC 1018p"
date: 2010-07-13
forum: Hardware
---

### Post by cspollard on 2010-07-13
I have an Asus EeePC 1018p and I'm having trouble debugging an audio problem in Lucid.  The internal microphone does not work, nor does the headphone jack or external mic input.  I've tried fiddling with alsamixer, pavucontrol (some fixes involve setting turning down the left or right capture channels), etc., but haven't had any success.

It seems that many people with EeePCs (other models) have fixed the problems with what I mentioned above, but it's no use for me.  I've also booted into UNR to see if the modified kernel that it ships with fixes any problems, but nothing changed.

Any ideas?  I don't even know which logs to look in to find the issue.

Here is some information on my system if it helps.

```

ALSA Audio Debug v0.1.0 - Tue Jul 13 14:02:40 CEST 2010
http://alsa.opensrc.org/aadebug
http://www.gnu.org/licenses/gpl.txt

Kernel ----------------------------------------------------
Linux ####### 2.6.32-23-generic #37-Ubuntu SMP Fri Jun 11 08:03:28 UTC 2010 x86_64 GNU/Linux

Loaded Modules --------------------------------------------
snd_hda_codec_realtek   279040  1 
snd_hda_intel          25677  6 
snd_hda_codec          85759  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               6924  1 snd_hda_codec
snd_pcm_oss            41394  0 
snd_mixer_oss          16299  1 snd_pcm_oss
snd_pcm                87882  5 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1782  0 
snd_seq_oss            31219  0 
snd_seq_midi            5829  0 
snd_rawmidi            23420  1 snd_seq_midi
snd_seq_midi_event      7267  2 snd_seq_oss,snd_seq_midi
snd_seq                57481  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              23649  2 snd_pcm,snd_seq
snd_seq_device          6888  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    71106  22 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
snd_page_alloc          8500  2 snd_hda_intel,snd_pcm

Dev Snd ---------------------------------------------------
by-path  controlC0  hwC0D0  pcmC0D0c  pcmC0D0p	seq  timer

CPU -------------------------------------------------------
model name	: Intel(R) Atom(TM) CPU N450   @ 1.66GHz
cpu MHz		: 1667.000
model name	: Intel(R) Atom(TM) CPU N450   @ 1.66GHz
cpu MHz		: 1667.000

RAM -------------------------------------------------------
MemTotal:        1014136 kB
SwapTotal:       1033208 kB

Hardware --------------------------------------------------
00:00.0 Host bridge: Intel Corporation N10 Family DMI Bridge

```

---

### Post by cspollard on 2010-07-15
Bump bump...Is this in the right forum?

---

### Post by cspollard on 2010-07-25
OK, well I've submitted this information to the launchpad bug found here:

[https://bugs.launchpad.net/ubuntu/+bug/601518](https://bugs.launchpad.net/ubuntu/+bug/601518)

Is there anything else I should do?

---

### Post by lidex on 2010-07-25
asus models seem to require more fiddling than any other. It's probably workable.
Can you post the output of these terminal commands for me please:
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

### Post by cspollard on 2010-07-25
Thanks for the help!

```

uname -a
------------------
Linux 2.6.32-24-generic #38-Ubuntu SMP Mon Jul 5 09:20:59 UTC 2010 x86_64 GNU/Linux


aplay -l
------------------
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC269 Analog [ALC269 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0


dpkg -l | grep "alsa"
------------------
ii  alsa-base                                                       1.0.22.1+dfsg-0ubuntu3                          ALSA driver configuration files
ii  alsa-utils                                                      1.0.22-0ubuntu5                                 ALSA utilities
ii  bluez-alsa                                                      4.60-0ubuntu8                                   Bluetooth audio support
ii  gstreamer0.10-alsa                                              0.10.28-1                                       GStreamer plugin for ALSA


head -n 1 /proc/asound/card*/codec#*
------------------
Codec: Realtek ALC269

```

---

### Post by lidex on 2010-07-25
Using a Terminal="Applications->Accessories->Terminal"
Open this file for editing:
```
 gksudo gedit /etc/modprobe.d/alsa-base.conf 
```
Insert this line at the bottom:
```
 options snd-hda-intel model=auto 
```
Save. Close. Reboot. Check your levels in alsamixer.
```
 alsamixer 
```
Press <F6> to select the correct soundcard.
Press <F3> to show playback levels. <F4> selects capture levels [or use <Tab>]
Use the left/right arrow keys to select and up/down arrow keys to change levels. <M> to mute/unmute.
Go to "System ->Preferences ->Sound" and make sure the correct soundcard is default and adjust your profile on the hardware tab.

---

### Post by cspollard on 2010-07-25
No change as far as I can tell.  Internal speakers still work.  Still no output via headphone jack, nor is there any response from the internal microphone.

Any other ideas?

---

### Post by lidex on 2010-07-25
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

Then use pulseaudio volume control (pavucontrol) or 'Sound Preferences' to select and unmute your mic in 'Input Devices' tab.

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

### Post by cspollard on 2010-07-25
hmm.  All devices are on in alsamixer, gnome-alsamixer, and pavucontrol.  Mic Boost, Capture, and Front Mic are all at 100%, as are Speaker, PCM, and Master.

Something funny though--the input in pavucontrol has a non-zero signal when the output slider level is set to something other than zero--even when output is muted.  If the output slider is at zero, there is never any input signal.

Also, pavucontrol seems to think that I have a stereo mic, but it's mono.  I've read that setting one slider to ~90 and the other to ~10 will fix the problem, but I haven't had any luck.  Every time I restart pavucontrol, the two channels are locked to one another again.

Cheers.

---

### Post by lidex on 2010-07-25
Try removing your pulse settings:
```

rm -r ~/.pulse ~/.asound* 
sudo rm /etc/asound.conf
```
**Logout/in.**
Now try again. The stereo mic is an issue. Turn the right channel all the way down.

---

### Post by cspollard on 2010-07-26
no luck.  I can't tell any difference.  The right and left mic input channels are still "locked" (i.e. the shield button is depressed) every time I restart pavucontrol, but the right input channel will stay at 0, and the left at 100.

Any other ideas?  Again, thanks for looking into this.

---

### Post by lidex on 2010-07-26
Open alsamixer, press <F4> and take a screenshot. Then post here if you would please.

---

### Post by cspollard on 2010-07-27
no problem.

---

### Post by Shakz on 2010-08-05
I have the exact same issue on the exact same netbook. Anyone have any ideas on this? It works on ubuntu 9.10 but not on 10.04.

---

### Post by lidex on 2010-08-05
```
Getting Line Input to work (Microphone, etc)

Changing default subdevice configuration

    * Some sound devices have multiple capture subdevices (eg. hda-intel), but pulseaudio only seems to detect the parent device, and only listens to subdevice #0. ALSA may not be configured to use your preferred device as subdevice #0 by default.
          o

            Open the pulseaudio record meter (pavumeter --record)
          o Talk into your chosen device while you carry out the process and watch the meter.
                + Some channels are quite noisy even with no input (especially on integrated chipsets), so we are watching for movements that correspond to our voice. 
          o

            Use alsamixer -c n (where n is your sound card number, probably 0)
                + Press F4 to get to the capture console
                + Make sure the first capture channel is enabled ("CAPTUR" in red, press space to toggle), and the volume turned up.
                + Check the first input source is switched to your chosen plug (Mic, in my case) 
          o At this point, you should see the record meter bouncing in response to your voice.
          o I found that I had to repeat this procedure each time I wanted to use the Mic, even though the settings "stuck" in the mixer, something in the soundcard wasn't initialized until it was repeated.
          o This also works if you use the "Options" tab in the standard mixer app to do the same thing. 
```

---

### Post by cspollard on 2010-08-05
Still the same old story.  I've used a USB mic successfully, so it's not the high level software that's an issue.  Funny.  I see a very regular ~1 Hz pulse in the mic channel--both actually (it's still stereo).

---

### Post by lidex on 2010-08-05
There must be something I'm not seeing - probably something basic. 
Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Enter your user password when prompted. Choose the upload option and provide a link for the output.

---

### Post by cspollard on 2010-08-06
Here's the link:

[http://www.alsa-project.org/db/?f=2bd476661ea41722ce9a36400681e5c762073d60](http://www.alsa-project.org/db/?f=2bd476661ea41722ce9a36400681e5c762073d60)

Hope it helps.

---

### Post by lidex on 2010-08-06
Try upgrading your alsa install. Use the link in my sig. But first remove any custom entries from alsa-base.conf

---

### Post by addicted68098 on 2010-08-08
> **lidex said:**
> Try upgrading your alsa install. Use the link in my sig. But first remove any custom entries from alsa-base.conf

Thanks, this solved all my problems

---

### Post by mikaellarson on 2010-08-10
Sorry for being somewhat naive. I have the same problem on my brand new eee pc 1018p (I don't understand why you can't buy the machine clean to begin with, and not just built for win).

Anyway. I understand the problem is solved. Can anyone summarize the logical sequence of the necessary steps:
Do I only have to upgrade the alsa install, or
do I have to go through any of the other steps in the thread?

Many thanks
Mikael

---

### Post by Aranha on 2010-08-16
If you didn't change the Kernel it is enough to just run the Alsa upgrade skript. I did with my new EeePc 1018P and it worked perfect.

---

### Post by mikaellarson on 2010-08-16
Thanks. Works now.
Mikael

---

### Post by Blindraven on 2010-09-23
Confirmed, worked perfectly for the Asus eeepc 1015p.

---

### Post by lkjoel on 2010-09-24
Try Fix your sound! in my signature.
Then use Post-Fix your sound! in my signature.

---

### Post by cspollard on 2010-10-10
This problem is fixed in Ubuntu 10.10, at least on a fresh install, so if you're willing to reinstall for sound working out of the box, I recommend it.

---

