---
title: "Mic is not recognized using card [HDA NVidia] VT1708S Analog in ubuntu 10.04 or 8.04"
date: 2010-06-08
forum: Hardware
---

### Post by ignacio69 on 2010-06-08
Mic is not recognized using card [HDA NVidia] VT1708S Analog in ubuntu 10.04 either in 8.04 (gnome) no help upgrading ALSA.
Hello,
I have already read most of the posts in internet related to: ubuntu sound problem, trubleshootings, ekiga sound problem, mic sound problem, capture audio problem, pulseaudio (already killed and removed), ALSA, gnome-volume-control (evrything is red, nothing is unmuted), alsamixer: see my .png
This are the output of the commands that are normally required for people being able to help you:

Tried the following:
[https://help.ubuntu.com/community/SoundTroubleshootingProcedure](https://help.ubuntu.com/community/SoundTroubleshootingProcedure)
[http://monespaceperso.org/blog-en/2010/05/02/upgrade-alsa-1-0-23-on-ubuntu-lucid-lynx-10-04/](http://monespaceperso.org/blog-en/2010/05/02/upgrade-alsa-1-0-23-on-ubuntu-lucid-lynx-10-04/)
cat /proc/asound/version:
Advanced Linux Sound Architecture Driver Version 1.0.23.
Compiled on Jun  5 2010 for kernel 2.6.32-22-generic (SMP).
sudo alsaconf
error no card supported, want to try an ISA, No
!!Aplay/Arecord output
!!------------

APLAY

**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: VT1708S Analog [VT1708S Analog]
  Subdevices: 2/2
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1

ARECORD

**** List of CAPTURE Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: VT1708S Analog [VT1708S Analog]
  Subdevices: 2/2
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1

cat /proc/asound/card*/codec* | grep Codec:
Codec: VIA VT1708S
sudo which alsactl:
/usr/sbin/alsactl
[http://www.mjmwired.net/kernel/Documentation/search?cx=partner-pub-5258443501063629%3Aj1dm2i-kn8t&cof=FORID%3A9&ie=ISO-8859-1&q=VIA+VT1708S&sa=Search#222](http://www.mjmwired.net/kernel/Documentation/search?cx=partner-pub-5258443501063629%3Aj1dm2i-kn8t&cof=FORID%3A9&ie=ISO-8859-1&q=VIA+VT1708S&sa=Search#222)
Your search - VIA VT1708S - did not match any documents.

I just cannot use my mic either in ekiga, either in sound recorder, either in audacity.
My mic is a SPEEDLINK headphones with mic that I plugged in with a jack.
these programs will behave different; ekiga and audicity will not register anything; sound recorder will register a high pitch beep.
uname -r:
2.6.32-22-generic

can you tell me what information I can post to try it further.
thank you in advance

---

### Post by lidex on 2010-06-09
I would suggest upgrading alsa again. This time follow the upgrade link in my sig and if you have alsa-backports installed, uninstall it and reboot first. Have you tried toggling the 'input source' in alsamixer?

---

### Post by ignacio69 on 2010-06-10
Dear Lidex,
Thnk you for your time in advance:
what I did, I followed the link in your sig, that is: [http://ubuntuforums.org/showthread.php?p=6589810#post6589810](http://ubuntuforums.org/showthread.php?p=6589810#post6589810) 
step 1,
I tried to toggle the 'input source' in alsamixer:
see my .png
I have two options:
Front mic and Line,
tried to select Line and check it using sound recorder; result: beep
toggled again to 'Front mic' and check it using sound recorder; result: beep

step 2,
uninstall alsa-backports; I do not know if I have them, either how to chek it, but I tried the following in terminal:
sudo apt-get purge linux-backports-modules-alsa-lucid-generic:
Sudo says is not installed so it cannot be removed, so trying again with the upgrading.

Closing all programs that can need the alsa (ekiga, sound recorder, pidgin, leaving only openoffice, firefox (without music for your post) omegaT) and running the script

step 3,
download the script and save it somewhere
2. cd <your-download-dir>
3. tar xvf AlsaUpgrade-1.0.23-2.tar
4. sudo ./AlsaUpgrade-1.0.23-2.sh -d
5. sudo ./AlsaUpgrade-1.0.23-2.sh -c
6. sudo ./AlsaUpgrade-1.0.23-2.sh -i
7. sudo shutdown -r 0

step 4 checking the version
cat /proc/asound/version:
Advanced Linux Sound Architecture Driver Version 1.0.23.
Compiled on Jun 10 2010 for kernel 2.6.32-22-generic (SMP).

step5 testing aplay
speaker-test -Dplughw:0,0 -c2: test OK

step 6, multiples checking:
check if your alsamixer-channels are activated and unmuted (gnome-mixer/volume-control/preferences)!! :
see in my .png that nothing is unmuted


step 7, /etc/modprobe.d/alsa-base.conf:

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
install snd /sbin/modprobe --ignore-install snd $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-ioctl32 ; /sbi$
#
# Workaround at bug #499695 (reverted in Ubuntu see LP #319505)
install snd-pcm /sbin/modprobe --ignore-install snd-pcm $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-pcm-os$
install snd-mixer /sbin/modprobe --ignore-install snd-mixer $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-mi$
install snd-seq /sbin/modprobe --ignore-install snd-seq $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-mi$
#
install snd-rawmidi /sbin/modprobe --ignore-install snd-rawmidi $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist sn$
# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist sn$
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist sn$

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist saa7134-al$
# Prevent abnormal drivers from grabbing index 0
options bt87x index=-2
options cx88_alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-us122l index=-2
options snd-usb-usx2y index=-2
options snd-usb-caiaq index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
# Keep snd-pcsp from being loaded as first soundcard
options snd-pcsp index=-2

step 8, as it seems that the line options snd-hda is missing I will added manually

step 9, searching model hda using the following command:
cat /proc/asound/card0/codec#* | grep Codec:
Codec: VIA VT1708S

cat /proc/asound/card0/pcm0c/info:
card: 0
device: 0
subdevice: 0
stream: CAPTURE
id: VT1708S Analog
name: VT1708S Analog
subname: subdevice #0
class: 0
subclass: 0
subdevices_count: 2
subdevices_avail: 2

step 10, waiting for help:
As this model "VIA VT1708S" is not present in HD-Audio-Models.txt do not know what to add and I am stopped,
please, can you help me further to find out which model should add to my /etc/modprobe.d/alsa-base.conf.
Thanks in advance,

---

### Post by lidex on 2010-06-11
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

Then use pulseaudio volume control (pavucontrol) to select your mic in 'Input Devices' tab.

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

### Post by ignacio69 on 2010-06-12
Dear Lidex:
thank you again for your help.
It seems I have already installed gnome-alsamixer.
I tried the following
in terminal typed gnome-alsamixer: see gnomealsamutefrontmic.png
the front mic is muted, and the input source is blank
so I tried to check the input source with this result:
** (gnome-alsamixer:4028): WARNING **: gam_toggle_get_state (). No idea what to do for mixer element "Independent HP"!

** (gnome-alsamixer:4028): WARNING **: gam_toggle_get_state (). No idea what to do for mixer element "Input Source"!

** (gnome-alsamixer:4028): WARNING **: gam_toggle_get_state (). No idea what to do for mixer element "Input Source"!

** (gnome-alsamixer:4028): WARNING **: gam_toggle_set_state (). No idea what to do for mixer element "Input Source"!

and tried to unmute the front mic (see my gnomealsacapture.png:
tryed with sound recorder and ... after recording, the result is only a beep.
checked also pavucontrol: It seems that my mic was already selected see my pavucontrolinput.png

I am including another 2 .png:
1) pavucontrolnotdetectinginputsoundrecorder.png
2) pavucontroldetectingoutputsoundrecorder.png

When I record usign sound recorder, the seconds move and everything looks as it were recorded, but the output is a beep. 

Please, can you give me more hints?

---

### Post by lidex on 2010-06-12
In your first screen, is it showing two sliders (L + R) for the mic? If so, try turning one down all the way. Mic should be mono.

---

### Post by ignacio69 on 2010-06-13
Dear LIdex:
once again, thank you for your help.
I am going to try the following:
1. the frist screen, I assume is the alsamixer, I am going to try the closer to left turn down and try sound recorder, here is the result: **beep** see (lefslideturneddownbutfrontmicmuted.png); 

2. I realized that front mic is muted for reproduction, I try to unmute and the result in soundrecorder is: 
**beep** see (leftslideturneddownfrontmicunmuted.png)

3. I tried both the right and left slide to turn down. The result with sound recorder is: **beep** (see bothleftandrightslideturneddown.png)

4. Last I try the right slide turned down and the left up tp 100. The result with sound recorder is: **beep** (see (rightslideturneddownfrontmicunmuted.png)

I am sure you have more important things to do, but I feel that we are closing to get the mic working, please, can you give me more hints. Ask me for more ouput of my system.
Thank you in advance,

---

### Post by lidex on 2010-06-13
No, I was referring to the previous post. It looks like pulseaudio volume control. In the first screenshot there are two sliders. It looks like a stereo pair. Turn one of them down in the volume control, not alsamixer.

---

### Post by ignacio69 on 2010-06-13
Dear Lidex,
so once more, thank you for your help.
I try the pulse audio volume control (typed pavucontrol in terminal) to turn down one of the slides.
Unfortunatelly the 2 slides are sicked is not possible to separate them, I include a twoslidestogetherisnotpossibletoseparatethem.png, so you see that I tried but the slides are together is not left and right slide.
the result with sound recorder is: still beep
So, please, can you still give any more hints?

---

### Post by lidex on 2010-06-13
Yeah, that button with the little shield icon controls that. Click on it once to disable channel locking.

---

### Post by ignacio69 on 2010-12-11
Dear Lidex,
I finally understood waht you meant when you said:
> **lidex said:**
> Yeah, that button with the little shield icon controls that. Click on it once to disable channel locking.

Now that the slides are separated I have turned down the right one in the Volume control; tab > capture.
I have tried sound-recorder and still the output is beep.

However I have tried: these commandes: [PHP]arecord -d 5 test-mic.wav
Grabación WAVE 'test-mic.wav' : Unsigned 8 bit, Ratio 8000 Hz, Mono
ignacio@ignacio-desktop:~$ aplay test-mic.wav
Sonando WAVE 'test-mic.wav' : Unsigned 8 bit, Ratio 8000 Hz, Mono[/PHP]
and the output was some kind of buzz, which means that some mic is recording.

However I would like to use the mic in my headphones which is plugged in the front part of the PC at the right side, there are 2 holes: the first is rose where I plugged the "mic"; bellow it, there is a green one, where I have plugged the headphones "sound output". 
The headphones are working perfectly, only the mic is not worling.

Here is the output of [PHP]amixer[/PHP]
imple mixer control 'Master Front',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 31 [100%] [12.00dB] [on]
  Front Right: Playback 31 [100%] [12.00dB] [on]
Simple mixer control 'PCM',0
  Capabilities: pvolume penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 255
  Mono:
  Front Left: Playback 255 [100%] [0.00dB]
  Front Right: Playback 255 [100%] [0.00dB]
Simple mixer control 'Front',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 42
  Mono:
  Front Left: Playback 42 [100%] [0.00dB] [on]
  Front Right: Playback 42 [100%] [0.00dB] [on]
Simple mixer control 'Front Mic',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 26 [84%] [4.50dB] [on]
  Front Right: Playback 26 [84%] [4.50dB] [on]
Simple mixer control 'Front Mic Boost',0
  Capabilities: cvolume penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 3
  Front Left: Capture 1 [33%] [10.25dB]
  Front Right: Capture 1 [33%] [10.25dB]
Simple mixer control 'Line',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 31 [100%] [12.00dB] [on]
  Front Right: Playback 31 [100%] [12.00dB] [on]
Simple mixer control 'Mic',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 31 [100%] [12.00dB] [on]
  Front Right: Playback 31 [100%] [12.00dB] [on]
Simple mixer control 'Mic Boost',0
  Capabilities: cvolume penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 3
  Front Left: Capture 3 [100%] [30.75dB]
  Front Right: Capture 0 [0%] [0.00dB]
Simple mixer control 'Capture',0
  Capabilities: cvolume cswitch penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 31
  Front Left: Capture 31 [100%] [30.00dB] [on]
  Front Right: Capture 0 [0%] [-16.50dB] [on]
Simple mixer control 'Capture',1
  Capabilities: cvolume cswitch penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 31
  Front Left: Capture 31 [100%] [30.00dB] [on]
  Front Right: Capture 31 [100%] [30.00dB] [on]
Simple mixer control 'Digital',0
  Capabilities: cvolume penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 120
  Front Left: Capture 98 [82%] [19.00dB]
  Front Right: Capture 98 [82%] [19.00dB]
Simple mixer control 'Independent HP',0
  Capabilities: enum
  Items: 'OFF' 'ON'
  Item0: 'OFF'
Simple mixer control 'Input Source',0
  Capabilities: cenum
  Items: 'Stereo Mixer' 'Mic' 'Front Mic' 'Line'
  Item0: 'Front Mic'
Simple mixer control 'Smart 5.1',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [off]

So, can you still help me to get the record working?, My goal is being able of using a VoIP like Ekiga

---

### Post by lidex on 2010-12-12
It's been awhile. Can you update me?
Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]

---

### Post by ignacio69 on 2010-12-16
Dear LIdex,
Thank you in advance for your help. 
I did what you said, I put the command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
and here is the link for the output.: [http://www.alsa-project.org/db/?f=52fa8051612920820f87eab05b8fabf62a9dbe5f](http://www.alsa-project.org/db/?f=52fa8051612920820f87eab05b8fabf62a9dbe5f)
With this information can you make my Ubuntu to be able of recording using sound recorder and being able of using Ekiga?
Thank again for your time and effort.

---

### Post by lidex on 2010-12-16
@ignacio69
Try this. Using a Terminal="Applications->Accessories->Terminal"
Open this file for editing:
```
 gksudo gedit /etc/modprobe.d/alsa-base.conf 
```
Insert this line at the bottom:
```
 options snd-hda-intel model=auto 
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

### Post by ignacio69 on 2010-12-17
Dear Lidex,
thank you once more for your advice.
I did what you said. I went to a Terminal="Applications->Accessories->Terminal"
Opened this file for editing:
```
 gksudo gedit /etc/modprobe.d/alsa-base.conf 
```
Inserted this line at the bottom:
```
 options snd-hda-intel model=auto 
```
Save. Close. Reboot. 
I opened again a Terminal="Applications->Accessories->Terminal
```
 alsamixer 
```
Press <F6> to select the correct soundcard.
There is only one card to choose HDA NVidia;
```

&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472; Tarjeta de sonido &#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;&#9618;&#9474;               >
&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;-  (predeterminado)                       &#9474;&#9618;&#9474;               >
&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;0  HDA NVidia                             &#9474;&#9618;&#9474;               >
&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;   introduzca el nombre del dispositivo...&#9474;&#9618;&#9474;               >
&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9492;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9496;&#9618;
```
> Press <F3> to show playback levels. 
All at are the maximum (with output I have no problems)
> Press <F4> to select capture levels [or use <Tab>]
Using the left/right arrow keys to select and up/down arrow keys to change levels. and the <M> to mute/unmute.
Here is the output in my .png, 
Can you check if this is correct?:capture171210.png

I went to "System ->Preferences ->Sound" and make sure the correct soundcard is default
[PHP]There is only one:
see my soundpreferences17122010.png
[/PHP]
can you check if everything is correct until now?
I have run the script once more with the changes so you can check if this is OK now. Here is the link: [http://www.alsa-project.org/db/?f=b5fb2787d995baf023eccb1f60b0992e33ce775b](http://www.alsa-project.org/db/?f=b5fb2787d995baf023eccb1f60b0992e33ce775b) 
Thank you again for your time.

---

### Post by lidex on 2010-12-17
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

Then go to 'Sound Preferences' to select and unmute your mic in 'Input' tab.
Make sure you have selected a profile with 'duplex' or 'analog input' for the correct sound device on the 'Hardware' tab.
Use Pulse Audio Volume Control (pavucontrol) to unlock stereo sliders for the mic in 'Input Devices' tab. Drag the right slider down to zero. The mic is a mono device.

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

### Post by gradinaruvasile on 2010-12-17
You have VIA VT1708S ?
I encountered a somewhat similar problem on a Asus M4A78-LT-M motherboard. That had AMD chipset, but it did identify as VIA VT1708S chip.

Anyway the fix to this issue was to append to the 

/etc/modprobe.d/alsa-base.conf

file the following lines:

options snd_hda_intel model=asus
options snd_hda_intel position_fix=1

After reboot i had working capture (the options snd_hda_intel model=auto line is the default behaviour anyway).


Watch out for the high capture levels because they can distort sound - the digital was at 50% on that comp. Also i had 33% boost and 90-100% capture set.

Make sure your capture microphone is the right one - Front Mic is the one connected to the front of the case, Mic is the back one. This can be selected from the sound preferences gui aswell (Microphone 1 or 2, test them to see the which one has movement on the capture bar when tapped).

Also, in the sound preferences -> output tab select the "Analog Output" connector because for some reason the front case output is not separated in the internal mixer correctly (it is greyed out in Alsamixer - it is the "Headphones" connector there). Otherwise you might not get sound playback through the front connector.
In Alsamixer Set the Independent HP (or jack switching) to OFF. It may cut the sound sometimes if it is set to ON.

---

### Post by ignacio69 on 2010-12-18
Dear Lidex,
once more thank you for your time.
Let's focus in the mic problem.
```
 gnome-alsamixer 
```
see my png, where all the switchs are activated and enabled on:gnomealsamixer18122010.png

> Then go to 'Sound Preferences' to select and unmute your mic in 'Input' tab.

the mic is unmute in 'Input' tab.
see png: soundpreferences18122010.png
> Make sure you have selected a profile with 'duplex' or 'analog input' for the correct sound device on the 'Hardware' tab.
see my png. the correct sound device on the 'Hardware' tab is "Analog stereo duplex": soundpreferenceshardware18122010.png
Last step:
> Use Pulse Audio Volume Control (pavucontrol) to unlock stereo sliders for the mic in 'Input Devices' tab. Drag the right slider down to zero. The mic is a mono device.

In pavucontrol I have the slider for the mic in 'Input Devices' tab. on the right slider down to zero  ('frente derecho'). See my .png: pavucontrolimput18122010.png
So, can you check if something else need to be set up?

---

### Post by ignacio69 on 2010-12-18
Dear gradinaruvasile,
thank you for your time in advance
> Anyway the fix to this issue was to append to the 

/etc/modprobe.d/alsa-base.conf

file the following lines:

options snd_hda_intel model=asus
options snd_hda_intel position_fix=1

I had included these 2 lines and nothing has changed, except maybe that using Audacity for recording gives a more strong signal, but still buzz only


> Watch out for the high capture levels because they can distort sound - the digital was at 50% on that comp. Also i had 33% boost and 90-100% capture set.


Can you check if this levels are ok?: see my .png: capture18122010.png

> Make sure your capture microphone is the right one - Front Mic is the one connected to the front of the case, Mic is the back one.

It took me a while to figure out, but finally I got to the same statement that you are pointing:
I am using now the 'front mic', which it is the one that is in the front part of my computer closer to me  and this is the one in the input capture. 
The 'mic' is the one at the rear, that is where all the other "holes" are, for the electricity, for the monitor, for the mice, for the keyboard, for the LAN ...

> This can be selected from the sound preferences gui aswell (Microphone 1 or 2, test them to see the which one has movement on the capture bar when tapped).

I believe that the mic 2 is the 'front mic'. Am I right?

> Also, in the sound preferences -> output tab select the "Analog Output" 
It is set to 'Analog Output', see my .png: soundpreferencesoutput18122010.png

> In Alsamixer Set the Independent HP (or jack switching) to OFF. It may cut the sound sometimes if it is set to ON.
It is setted to OFF. see my .png: alsamixerindependtoff18122010.png

Can you checked if everything is correctly settled up?

---

### Post by gradinaruvasile on 2010-12-18
Ok. The capture tab:

I never had any problems with feft/right channel recording. So ypu should turn them up to the same level.
My settings were:
Capture: 33% boost, 100% capture, 50% digital (might be as high as 70%, but at this level it already interferes with recording)

Playback:

It seems to me that you have no surround? In the mobo used i had quite a few surround-related controls.
What mobo (or computer/laptop) do you have?

Anyway, the rule of the thumb is to disable all mics in the Playback tab. Leave them only for the capture tab.

---

### Post by ignacio69 on 2010-12-19
Dear gradinaruvasile,
thank you for your time,
> Ok. The capture tab:

I never had any problems with left/right channel recording. So you should turn them up to the same level.

The reason I had them like that, it is because Lidex (one of the other user who was helping me in this thread) warned me that the mic is mono so it should have one channel only. Nevertheless there is no difference to turn them up to the same level 100%
> My settings were:
Capture: 33% boost, 100% capture, 50% digital (might be as high as 70%, but at this level it already interferes with recording)

I have now the same settings that you have: see my .png: capturealsamixer19122010.png

> Playback:

It seems to me that you have no surround? In the mobo used i had quite a few surround-related controls.
What mobo (or computer/laptop) do you have?
I am not sure what do you ask: I have introduced this command in the terminal 
```
cat /proc/cpuinfo
```
and I have found this: AMD Athlon(tm) II X2 240 Processor


> Anyway, the rule of the thumb is to disable all mics in the Playback tab. Leave them only for the capture tab.
Now I have disabled all mics in the Playback tab
so here is my png. playbackalsamixer19122010.png

Is it everything already set up? do I have to change anything else?

---

### Post by gradinaruvasile on 2010-12-19
> 
and I have found this: AMD Athlon(tm) II X2 240 Processor


Not the processor, the motherboard is i am interested on. Typically you can find it with:

```

sudo lshw | grep product

```

Usually it is the line above the processor.

This is my output (the red text is the motherboard model)

```


product: System Product Name
       product: [COLOR="Red"]M3N78-VM[/COLOR]
          product: AMD Athlon(tm) II X2 250 Processor
             product: PartNum0
             product: PartNum1
             product: PartNum2
             product: PartNum3
          product: MCP78S [GeForce 8200] Memory Controller
          product: MCP78S [GeForce 8200] LPC Bridge
          product: MCP78S [GeForce 8200] SMBus
          product: MCP78S [GeForce 8200] Memory Controller
          product: MCP78S [GeForce 8200] Co-Processor
          product: MCP78S [GeForce 8200] Memory Controller
          product: MCP78S [GeForce 8200] OHCI USB 1.1 Controller
          product: MCP78S [GeForce 8200] EHCI USB 2.0 Controller
          product: MCP78S [GeForce 8200] OHCI USB 1.1 Controller
          product: MCP78S [GeForce 8200] EHCI USB 2.0 Controller
          product: MCP78S [GeForce 8200] IDE
             product: DRW-1608P3S
          product: MCP72XE/MCP72P/MCP78U/MCP78S High Definition Audio
          product: MCP78S [GeForce 8200] PCI Bridge
          product: MCP78S [GeForce 8200] AHCI Controller
             product: Hitachi HDT72502
             product: WDC WD1600AAJS-6
          product: MCP77 Ethernet
          product: MCP78S [GeForce 8200] PCI Express Bridge
             product: C77 [GeForce 8200]
          product: MCP78S [GeForce 8200] PCI Express Bridge
          product: MCP78S [GeForce 8200] PCI Express Bridge
          product: Family 10h Processor HyperTransport Configuration
          product: Family 10h Processor Address Map
          product: Family 10h Processor DRAM Controller
          product: Family 10h Processor Miscellaneous Control
          product: Family 10h Processor Link Control


```

The idea is to identify the motherboard in order to look at its specifications.


First i would advise to get rid of the custom modprobe lines (if any) except the ones i told you.
Comment out the rest by putting a # character at the beginning of the line (those lines will be ignored).

Also install back the alsa version from the repos because sometimes components compiled behave differently than those provided by the repositories. The VIA VT1708S chip is a surround chip and should have many controls you dont have there (front left, front right, rear left, rear right, lfe and whatnot).
Reset the card:

sudo service alsa-utils reset

Reboot.

Connect the mic to the pink jack connector back of the computer and the headphones to the green connector. This is to eliminate the problem that might be caused by faulty front connectors (if any).

Check the alsamixer settings.
Set the captured device as "mic" and do the "arecord | aplay" test.

---

### Post by ignacio69 on 2010-12-19
Dear gradinaruvasile,
so, again thank you for your time:
> The idea is to identify the motherboard in order to look at its specifications.

```
sudo lshw | grep product
```
Output is product: N68-S
```
product: To Be Filled By O.E.M.
       [COLOR="Red"]product: N68-S[/COLOR]
          product: AMD Athlon(tm) II X2 240 Processor
             product: PartNum0
             product: PartNum
```


> First i would advise to get rid of the custom modprobe lines (if any) except the ones i told you.
Comment out the rest by putting a # character at the beginning of the line (those lines will be ignored).
I will wait for your orders in order to get rid of the custom modprobe lines. which command do I need in order to get the output?

> Also install back the alsa version from the repos because sometimes components compiled behave differently than those provided by the repositories. The VIA VT1708S chip is a surround chip and should have many controls you don't have there (front left, front right, rear left, rear right, lfe and whatnot).

I install the 1.0.23 because Lidex was trying to help me to get more controls, I remember that when having 1.0.21 i did not have 'smart 5.1' 
Nevertheless, I will wait for your orders in order to do this step also
> Reset the card:

sudo service alsa-utils reset 

Reboot. 
I will wait for your orders in order to do this step also
> Connect the mic to the pink jack connector back of the computer and the headphones to the green connector. This is to eliminate the problem that might be caused by faulty front connectors (if any).

I have changed it now
> Check the alsamixer settings.
Set the captured device as "mic" and do the "arecord | aplay" test. 
here is the output:It works!!!!
```
arecord -f dat -d 20 -D hw:0,0 test.wav
```
Grabación WAVE 'test.wav' : Signed 16 bit Little Endian, Ratio 48000 Hz, Estéreo
^CAbortado por la señal Interrupción... 
```
aplay -f dat test.wav
```

Sonando WAVE 'test.wav' : Signed 16 bit Little Endian, Ratio 48000 Hz, Estéreo


**I can here myself when I use the 'arecord' command using the 'mic' in the rear part of my computer, Also I can here myself when I record my voice using 'Audacity', Also I can here myself when I try the 'Echo call' in 'Skype'**.
[COLOR="Red"]The only thing that are not working are the gnome-sound-recorder' and 'Ekiga'[/COLOR].

So I will marked this post as SOLVED and also all the other post where I was asking for solutions.
Thank you LIDEX and gradinaruvasile for your wonderful advices, your patience, your time and your unbelievable helpful tips.

I will open a new post in order to make it work also for 'Ekiga', 'sound-recorder' and 'front mic', but this latter, I am going to enjoy that I can use my CAPTURE after a year searching.

---

### Post by gradinaruvasile on 2010-12-19
Glad it worked.
Dont change system settings if they work now.

Check ekigas sound settings and set everything to default/alsa.

---

### Post by Graham A on 2011-01-14
I'd like to re-open this if possible. I have a similar issue with recording with my analogue microphone. It's connected to the following device:

```
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
    Subsystem: ASUSTeK Computer Inc. M4A785TD Motherboard
    Flags: bus master, slow devsel, latency 64, IRQ 16
    Memory at fe8f4000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel
```

Using the command **$ arecord -f dat -d 20 -D hw:0,0 test.wav** I'm able to record my voice into the .WAV file which I can hear clearly. Using the command **$ arecord -l** I'm able to get this output.
```
**** List of CAPTURE Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: VT1708S Analog [VT1708S Analog]
  Subdevices: 2/2
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1

```

What perplexes me however is that PulseAudio seems unable to find my input. The mixer program does not recognise any input devices at all! I'm wanting to use my microphone in Skype but *PulseAudio (local)* is the only sound input option available and does not work. Output is fine! Clearly it's not a compatibility issue as I can hear myself when I record with the microphone as stated above but I don't know anything about how PulseAudio works so I've no idea where to start with the issue.

---

### Post by Graham A on 2011-01-16
Prodding with ALSA output. My machine is a desktop PC for the pedantic but I imagine it's similar hardware.

[http://www.alsa-project.org/db/?f=5efe65dfd4ae6a64030745347a532a9d75ec54b2](http://www.alsa-project.org/db/?f=5efe65dfd4ae6a64030745347a532a9d75ec54b2)

---

### Post by lidex on 2011-01-18
Try changing position fix from 1 to 0

---

### Post by Graham A on 2011-01-18
> **lidex said:**
> Try changing position fix from 1 to 0
No effect.

Let me be clear, my microphone works with ALSA. I'm able to use **arecord** to record sound from my microphone. I can hear this! This works! But mic input seems unavailable in PulseAudio and, as such, unavailable in Skype.

---

### Post by lidex on 2011-01-18
What about sound recorder, audacity, etc?

---

### Post by Graham A on 2011-01-18
Audacity works fine. Sound recorder does not.

---

### Post by lidex on 2011-01-18
So audacity is using alsa input then? If you open pavucontrol, on the 'input devices' tab, what options do you have for 'port'?

---

### Post by Graham A on 2011-01-18
Correct, Audacity skips PA and uses ALSA directly.

pavucontrol gives me nothing on the input tab. "No input devices available". If I select "All Input Devices" in the corner, I can get an "internal monitor" but nothing useful. Not sure what you mean by "port".

---

### Post by lidex on 2011-01-18
Also in pavucontrol, on the 'configuration' tab, what profile do you have selected for internal audio?

---

### Post by Graham A on 2011-01-18
"Analogue Stereo Output" amongst a variable multitude of Analogue Surround, there's an Analogue Duplex... which when selected has allowed me to enable my Mic on the "Input" tab which does seem to be responding to my sound from the Microphone. I believe that's a step in the right direction although still getting nothing from Skype or Sound recorder - perhaps a reboot might seal the deal.

---

### Post by Graham A on 2011-01-18
[Might as well use this space-saving post for vital information]

The "duplex" change seemed able to do the trick, I'm getting positive results from both Skype and Sound Recorder.

Champion! Thanks for your input into my input.

---

### Post by Graham A on 2011-01-18
[Sorry, connection issue, reposted twice - ignore this or delete]

---

