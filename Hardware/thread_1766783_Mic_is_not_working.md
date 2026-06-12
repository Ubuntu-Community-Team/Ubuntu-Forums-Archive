---
title: "Mic is not working"
date: 2011-05-24
forum: Hardware
---

### Post by RooFYzz on 2011-05-24
I have NoteBook Acer Aspire 5935G and i have recently updated to version 11.04 however my mic is not working neither on the current version nor the previous ones??

---

### Post by djpurity on 2011-05-24
I had Ubuntu 10.10 64-bit that I put on a new WD 500 GB HDD into my Acer aspipre 5251-1805, and my mic used to work, but at one point, stopped. I tried everything and installed all sorts of new packages and downloads and sudo'd my **** off. But the mic would show that it had a frequency detected, as the bar would go up and down, but when I tried Skype or Google Talk, it didn't work. I tried a basic Ubuntu Software Record program and it would not record, even while I watched in the sound preferences as the bar for the mic reading showed my voice was registering sound wavs being "heard" ... they just couldn't be recorded or sent over the Internet.

Have you tried using your mic built in, in addition to an external generic plug-in mic, too? I have tried both, same results. I don't know when it exaCTLY stopped WORKING, BUT IT did WORK ONCE BEFORE.

aLSO, THE EXTERNAL MIC HAS BEEN SET UP IN gOOGLE tALK AND SHOWS THAT IT WORKS AS WELL AS MY WEBCAM, BUT NO RECORDING OR PEOPLE HEARING ME CALL THEM. bUILT IN OR EXTERNAL.

wHAT HAVE YOU TRIED? 


:popcorn:

---

### Post by IWantFroyo on 2011-05-24
```
alsamixer
```

Hit f4, and make sure the capture is all the way up.

---

### Post by lidex on 2011-05-25
> **RooFYzz said:**
> I have NoteBook Acer Aspire 5935G and i have recently updated to version 11.04 however my mic is not working neither on the current version nor the previous ones??

Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.
[Terminal="Applications-> Accessories-> Terminal"]

---

### Post by phob0ss on 2011-07-12
I've got the same problem on acer 5738zg. Here's output of the script: [http://www.alsa-project.org/db/?f=b077d4de6bd2ec429d00556e9ca5bc289d693db2](http://www.alsa-project.org/db/?f=b077d4de6bd2ec429d00556e9ca5bc289d693db2)

---

### Post by lidex on 2011-07-12
> **phob0ss said:**
> I've got the same problem on acer 5738zg. Here's output of the script: [http://www.alsa-project.org/db/?f=b077d4de6bd2ec429d00556e9ca5bc289d693db2](http://www.alsa-project.org/db/?f=b077d4de6bd2ec429d00556e9ca5bc289d693db2)

Try this using a Terminal="Applications->Accessories->Terminal"
```
echo "options snd-hda-intel model=acer" | sudo tee -a /etc/modprobe.d/alsa-base.conf
``` **Reboot**

---

### Post by qwqwqwqwq on 2011-07-15
thank`s it`s working greate

---

### Post by Grez on 2011-07-15
> **lidex said:**
> Try this using a Terminal="Applications->Accessories->Terminal"
```
echo "options snd-hda-intel model=acer" | sudo tee -a /etc/modprobe.d/alsa-base.conf
``` **Reboot**

Any chance of a bit of help with mine, please? Similar problem, but it's a Realtek ALC888 internal sound on an ASRock M3A785GMH/128M motherboard (custom-built PC).

The output file is here: [http://www.alsa-project.org/db/?f=4a214a1a539498ce6908aafa5e8512186454e628](http://www.alsa-project.org/db/?f=4a214a1a539498ce6908aafa5e8512186454e628)

Thanks in advance!

:)

---

### Post by lidex on 2011-07-15
> **Grez said:**
> Any chance of a bit of help with mine, please? Similar problem, but it's a Realtek ALC888 internal sound on an ASRock M3A785GMH/128M motherboard (custom-built PC).

The output file is here: [http://www.alsa-project.org/db/?f=4a214a1a539498ce6908aafa5e8512186454e628](http://www.alsa-project.org/db/?f=4a214a1a539498ce6908aafa5e8512186454e628)

Thanks in advance!

:)

Your model name is using incorrect syntax of 6stack.dig
Change it to 6stack-dig and reboot

---

### Post by Grez on 2011-07-16
> **lidex said:**
> Your model name is using incorrect syntax of 6stack.dig
Change it to 6stack-dig and reboot

Hi, and a thousand thanks. It gave me a couple of new inputs, but still no recording from mic or line-in. It's taking input (I can hear it through the speakers) but no matter what settings I seem to use I can't get Sound Recorder or Audacity to record anything.

Any idea what I'm doing wrong?

:?

---

### Post by lidex on 2011-07-16
> **Grez said:**
> 
Any idea what I'm doing wrong?
:?

Turning it on ;)
I kid, post your amixer output:
```
amixer
```
This is the internal mic?

---

### Post by Grez on 2011-07-17
> **lidex said:**
> Turning it on ;)
I kid, post your amixer output:
```
amixer
```
This is the internal mic?

Hi - no internal mic - it's a desktop so I have front & rear mic sockets and a rear line-in socket all of which will play through the speakers but won't record!

Here's the amixer output:

```
Simple mixer control 'Master',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined penum
  Playback channels: Mono
  Limits: Playback 0 - 31
  Mono: Playback 27 [87%] [-6.00dB] [on]
Simple mixer control 'Headphone',0
  Capabilities: pswitch penum
  Playback channels: Front Left - Front Right
  Mono:
  Front Left: Playback [on]
  Front Right: Playback [on]
Simple mixer control 'PCM',0
  Capabilities: pvolume penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 255
  Mono:
  Front Left: Playback 249 [98%] [-1.20dB]
  Front Right: Playback 249 [98%] [-1.20dB]
Simple mixer control 'Front',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 31 [100%] [0.00dB] [on]
  Front Right: Playback 31 [100%] [0.00dB] [on]
Simple mixer control 'Front Mic',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 20 [65%] [-4.50dB] [on]
  Front Right: Playback 20 [65%] [-4.50dB] [on]
Simple mixer control 'Front Mic Boost',0
  Capabilities: volume penum
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: 0 - 3
  Front Left: 2 [67%]
  Front Right: 2 [67%]
Simple mixer control 'Surround',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 31 [100%] [0.00dB] [on]
  Front Right: Playback 31 [100%] [0.00dB] [on]
Simple mixer control 'Center',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined penum
  Playback channels: Mono
  Limits: Playback 0 - 31
  Mono: Playback 31 [100%] [0.00dB] [on]
Simple mixer control 'LFE',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined penum
  Playback channels: Mono
  Limits: Playback 0 - 31
  Mono: Playback 31 [100%] [0.00dB] [on]
Simple mixer control 'Side',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 31 [100%] [0.00dB] [on]
  Front Right: Playback 31 [100%] [0.00dB] [on]
Simple mixer control 'Line',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 31 [100%] [12.00dB] [on]
  Front Right: Playback 31 [100%] [12.00dB] [on]
Simple mixer control 'CD',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 18 [58%] [-7.50dB] [on]
  Front Right: Playback 18 [58%] [-7.50dB] [on]
Simple mixer control 'Mic',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 18 [58%] [-7.50dB] [on]
  Front Right: Playback 18 [58%] [-7.50dB] [on]
Simple mixer control 'Mic Boost',0
  Capabilities: volume penum
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: 0 - 3
  Front Left: 2 [67%]
  Front Right: 2 [67%]
Simple mixer control 'IEC958',0
  Capabilities: pswitch pswitch-joined cswitch cswitch-joined penum
  Playback channels: Mono
  Capture channels: Mono
  Mono: Playback [on] Capture [off]
Simple mixer control 'IEC958 Default PCM',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'Beep',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 21 [68%] [-3.00dB] [on]
  Front Right: Playback 21 [68%] [-3.00dB] [on]
Simple mixer control 'Capture',0
  Capabilities: cvolume cswitch penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 31
  Front Left: Capture 27 [87%] [24.00dB] [on]
  Front Right: Capture 27 [87%] [24.00dB] [on]
Simple mixer control 'Capture',1
  Capabilities: cvolume cswitch penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 31
  Front Left: Capture 21 [68%] [15.00dB] [on]
  Front Right: Capture 21 [68%] [15.00dB] [on]
Simple mixer control 'Channel Mode',0
  Capabilities: enum
  Items: '6ch' '8ch'
  Item0: '6ch'
Simple mixer control 'Input Source',0
  Capabilities: cenum
  Items: 'Mic' 'Front Mic' 'Line' 'CD'
  Item0: 'Line'
Simple mixer control 'Input Source',1
  Capabilities: cenum
  Items: 'Mic' 'Front Mic' 'Line' 'CD'
  Item0: 'Front Mic'

```

---

### Post by lidex on 2011-07-17
Probably best to focus on the first (0) input. 
```
Simple mixer control 'Input Source',0
  Capabilities: cenum
  Items: 'Mic' 'Front Mic' 'Line' 'CD'
  Item0: 'Line'
```
Set that to the mic input you're trying to use.

---

### Post by Grez on 2011-07-17
Ok, I've done that, but still no joy. I also tried using the line-in socket having switched it to line-in and still no capture.

Switching the input from the GUI is causing the  input in alsamixer to change correctly, so they seem to be working with each other.

Any other suggestions?

---

### Post by lidex on 2011-07-17
Everything needs to line up correctly.

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

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

From ubuntu wiki:
> Changing default subdevice configuration

Some sound devices have multiple capture subdevices (eg. hda-intel), 
but pulseaudio only seems to detect the parent device, and only listens to subdevice #0. 
ALSA may not be configured to use your preferred device as subdevice #0 by default.

Open the pulseaudio record meter (pavumeter --record)
Talk into your chosen device while you carry out the process and watch the meter.
Some channels are quite noisy even with no input (especially on integrated chipsets), 
so we are watching for movements that correspond to our voice. 

Use alsamixer -c n (where n is your sound card number, probably 0)
Press F4 to get to the capture console
Make sure the first capture channel is enabled ("CAPTUR" in red, press space to toggle), 
and the volume turned up.
Check the first input source is switched to your chosen plug (Mic, in my case) 
At this point, you should see the record meter bouncing in response to your voice.
I found that I had to repeat this procedure each time I wanted to use the Mic, 
even though the settings "stuck" in the mixer, something in the soundcard wasn't initialized 
until it was repeated. This also works if you use the "Options" tab in the standard mixer app to do the same thing.

---

### Post by Grez on 2011-07-17
OK, I tried that. Still no recording :(

The alsamixer and pulse programs do appear to be talking to each other, as selecting different options in one is seeming to have an effect on the other.

Winding down the mic and line sliders in gnome-alsamixer (and also plain alsamixer) causes the mic and line inputs to attenuate (as can be heard) but there's still no ability to record. Altering the capture slider causes a similar alteration in the input slider on the pulse dialog but it just doesn't seem to be connected to anything.

I checked the recording volume meter and got absolutely no response. However, playing back a track on audacity through the pulse server gave me a nice juicy response on the playback meter.

Thanks so much for your help so far. Do you have any more suggestions, please?

---

### Post by lidex on 2011-07-17
Try an alsa upgrade via the link in my sig.

---

### Post by Grez on 2011-07-19
> **lidex said:**
> Try an alsa upgrade via the link in my sig.

Thanks.

Still not working.

Do you think I'm using the wrong "model" spec for the driver?

I've tried to fond some specific info on this, but can't. I've used the one 6stack-dig simply because it's got 6 jacks on the mobo, one of which is optical digital. Is this right, do you know?

---

### Post by lidex on 2011-07-22
You're using outboard mic via front panel input, correct? Is it a mono or stereo mic? Can you post updated alsa-info please?

---

### Post by jopeto on 2011-09-06
Hello,

I am using an old Thinkpad T22 and I am also having trouble with the internal mic. I played around with the alsamixer and pulsed volume control values and I can hear the sound captured in the microphone directly in the speakers, however when I use the Gnome sound recorder I get nothing.

Following previous posts, here's what I get from the alsa script:
[http://www.alsa-project.org/db/?f=fe8ab76e8676bed91430848a9421d031309aec7a](http://www.alsa-project.org/db/?f=fe8ab76e8676bed91430848a9421d031309aec7a)

If I could get some help on this, it would be really appreciated.

Thanks a lot in advance and let me know if you need any further info.

---

### Post by jopeto on 2011-09-06
Forgot to mention that I'm using mint 9, which I guess is the same as ubuntu 10.04...

---

