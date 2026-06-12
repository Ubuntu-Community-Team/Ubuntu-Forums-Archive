---
title: "mic does not work on my asus eeepc 1001px"
date: 2010-10-27
forum: Hardware
---

### Post by Raimon on 2010-10-27
I just instal ubuntu netbook edition 10.10 on my asus eeepc 1001px and my mic does'nt work. when i click on sound preference there is not waves. Can you help me. sorry for my english, I'm french :).

---

### Post by Raimon on 2010-10-28
I ever try solution for Eeepc 1001HA but it still does'nt work.

---

### Post by plastoid-ru on 2010-11-04
What I deed with Asus eeepc 1001PX and Ubuntu 10.10.

To switch built-in microphone on:
1. Download and build **hda-verb**.
Set hda-verb **executable** and copy to **/usr/local/bin/**

2. No need to modify /etc/modprobe.d/alsa-base.conf

3. Add hda-verb call to /etc/rc.local

> [B]sudo pico /etc/rc.local
[/B]
enter before **exit**:
...

**/usr/local/bin/hda-verb /dev/snd/hwC0D0 0x023 SET_CONNECT_SEL 0x5**

exit 0


4. reboot

5. mic shoud work now.


P.S. After 
install of Ubuntu 10.10, audio playback works ok via EEEPC speakers and automatically switches to HEADPHONES when I plug them in EEEPC. So no need to other tricks. My audio works fine.

---

### Post by phillsky on 2010-11-05
> **plastoid-ru said:**
> What I deed with Asus eeepc 1001PX and Ubuntu 10.10.

To switch built-in microphone on:
1. Download and build **hda-verb**.
Set hda-verb **executable** and copy to **/usr/local/bin/**

2. No need to modify /etc/modprobe.d/alsa-base.conf

3. Add hda-verb call to /etc/rc.local

> [B]sudo pico /etc/rc.local
[/B]
enter before **exit**:
...

**/usr/local/bin/hda-verb /dev/snd/hwC0D0 0x023 SET_CONNECT_SEL 0x5**

exit 0


4. reboot

5. mic shoud work now.


P.S. After 
install of Ubuntu 10.10, audio playback works ok via EEEPC speakers and automatically switches to HEADPHONES when I plug them in EEEPC. So no need to other tricks. My audio works fine.

Did a fresh install of Ubuntu 10.10 on my EEE PC 1001px and tried your solution above, but it didn't work, mic is still dead.

---

### Post by dead8088 on 2010-11-05
I have the same problem and this solution haven't helped me too...

---

### Post by EowynCarter on 2010-11-07
hey, other 1001px users :)

Right now, i'm having problme with battery life. 
how long does the battery hold for you ?

---

### Post by dead8088 on 2010-11-07
About 6 hours. Do you have problems with built-in mic too?

---

### Post by rgstrator on 2010-11-07
Check out this post:

[http://ubuntuforums.org/showthread.php?p=6589810](http://ubuntuforums.org/showthread.php?p=6589810)

It made it work for me (eee 1001PX) - I still face several issues, but  basic audio IO works now and I guess the rest will be set when I  finetune the configuration.

Post a reply to this if you need more details

---

### Post by frankbooth on 2010-11-09
> **rgstrator said:**
> Check out this post:

[http://ubuntuforums.org/showthread.php?p=6589810](http://ubuntuforums.org/showthread.php?p=6589810)

It made it work for me (eee 1001PX) - I still face several issues, but  basic audio IO works now and I guess the rest will be set when I  finetune the configuration.

Post a reply to this if you need more details

So this solved the microphone problem but you still face several other issues? What kind?

I got my 1001PX yesterday and did a fresh Ubuntu Netbook Remix 10.10 install.
The problems I'm having are:


[LIST]
[*]Internal microphone doesn't work.
[*]In/Out jack only works for headphones. (explained below)
[/LIST]
Plugging in an external microphone disables the speakers, and the external microphone does not seem to work either. I can't explain why an external microphone wouldn't work... It feels  like something is muted, but alsamixer says everything is alright.

I've tried getting the internal microphone to work by trying the solution(s) [in this post] and also the suggestions on Launchpad without success. 

Is there a proper solution for the microphone problem? If not, does anyone know how long it took for the older versions of EEE PC to get their fix? (if they ever got fixed...)

---

### Post by retr0virus on 2010-11-10
> **frankbooth said:**
> 
[LIST]
[*]Internal microphone doesn't work.
[*]In/Out jack only works for headphones. (explained below)
[/LIST]
Exactly the problems I have with my 1005px. I tried several "solutions" but nothing worked for me.
If it is only an alsa-driver problem I would be happy. I think I will try an alsa upgrade soon.

---

### Post by lisamae on 2010-11-18
Hi I have an asus eeepc 1005px and my mic is also not working. I have tried all the solutions that I could find on the Ubuntu forums. Has anyone any other suggestions? Thanks

---

### Post by rgstrator on 2010-11-23
Sorry for the delay- there is an update; 

@frankbooth : basically I suspend the computer a lot, and unfortunately I noticed that after a reboot (several days later) the sound is again non-functional. Since I was setting it up as mainly a skype device, I was satisfied by it half-working. By 'half-working' I mean that 

a) built-in microphones never worked,
b) speakers always on, and 
c) plugged-in mic works. 

I managed the above by following instructions for installing the 'developer-grade' (? I do not know if this is the correct expression) ALSA drivers I mentioned in my previous post, following plasmoid-ru 's settings and trial-and-error combinations with the desktop's volume control- (I literally had a piece of scrap paper next to me and was eradicating combinations). The first sign that 'the trick worked' was that, after installing the newest ALSA drivers and rebooting, I got an external mic to work with audacity (with ridiculous amounts of static). Further fine-tuning got skype to work fine (webcam works out-of-the-box too), but even *thinking* of changing volume settings from the desktop's volume control messed up the picture again.
  
Obviously this is a half-measure setup, but at least gives you some functionality- 

I don't have much time to give it right now; I thought of either waiting for the ALSA people to do their magic, or try to see if there is a way to ndiswrap windows' driver (like I did for the WiFi chip). 

A note: I use WUBI, and I've still kept the windowze installation- when one plugs a device on the *unique* jack port, the driver daemon pops up and queries on what 'mode' to set itsself into (mic, speakers, mic+speaker headset and some other crap)

Another a bit off-topic note (on WUBI): Be very VERY careful when you install/upgrade kernels and/or grub!! It bricked my eee and I spent an hour trying to figure out what went wrong and fix it (by making bootable USBs from another system and the like). Seriously, if you're new, DO NOT JUST CLICK ON EVERY UPGRADE SUGGESTION YOU SEE- I assume the security ones are fine, but NOT the kernel or grub/boot related ones. Sorry, Ubuntu developers, but this is how it is- others have had this problem as well. 

Hope this helps-

PS> I activated instant mail notifications, so I'll probably be more fast getting back to you =)

---

### Post by irpsit on 2010-12-02
This solution worked for me:

Remove pulseaudio:
sudo apt-get remove --purge pulseaudio

Install alsamixer:
apt-get install alsamixer

Go to the new alsamixer volume control (applications, sound and video, mixer). Look for entry or capture, and set your microphone to digital and turn one channel down (0%), one channel up (100%).

This has worked for me. You can use the microphone to record your voice or skype. The only thing it didn't work was that I lost the volume tray.

EDIT: this post was written when I was trying a WUBI installation of Ubuntu 10.04, then I managed with this having the internal microphone. Now I did a separate and independent Ubuntu 10.10 install and no solution has work for the internal microphone!

---

### Post by lidex on 2010-12-02
> **irpsit said:**
> This solution worked for me:

Remove pulseaudio:
sudo apt-get remove --purge pulseaudio

Install alsamixer:
apt-get install alsamixer

Go to the new alsamixer volume control (applications, sound and video, mixer). Look for entry or capture, and set your microphone to digital and turn one channel down (0%), one channel up (100%).

This has worked for me. You can use the microphone to record your voice or skype. The only thing it didn't work was that I lost the volume tray.

Not sure how that worked for you as there is no install package named 'alsamixer'. Alsamixer is actually installed with the 'alsa-utils' package. Further, I don't see how removing pulseaudio accomplishes anything here. 
IMO, this procedure is more appropriate:
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

### Post by irpsit on 2010-12-04
Hi lidex,

thanks for noticing my mistake.
i am really a linux beginner :)
and my version is a portuguese, so sometimes I have to translate the packages names

1. What I did first was removing pulseaudio (I don't know if this is the cause for the microphone not working but many users in other threads suggested this and it worked for me)

sudo apt-get remove --purge pulseaudio

2. I also went to the package manager and remove the pulseaudio control volume (I guess this is the correct name, if my translation is ok)

3. Then, I installed alsamixer, as a sound control software alternative to pulseaudio:
apt-get install alsa-utils

4. in Alsamixer volume control, I chose microphone as digital and set one channel to zero, another to max, if the volume was makign noice I reduced the volume of the microphone, or also the volume of the microphone booster

This took me several hours to grasp, but worked. Let me know if you have already solved your microphone problem too

---

### Post by irpsit on 2010-12-12
Ok, yesterday I lost my sound again and had to reinstall the soundcard again. I recovered the sound but was without microphone again.

I tried again to follow my previous tricks, but to my astonishing the microphone does not work at all. With or without pulseaudio. Lidex, I also tried your gnome-alsamixer suggestion it didn't work.

Do you think I have to add some line to etc/modprobe.d/alsa-base.conf ?
Still no solution for this bug

---

### Post by irpsit on 2010-12-12
How do you download and build hda-verb?
How to do you set it as executable?

I'm sorry to ask; I am a Ubuntu beginner
I'm also looking to solve this microphone bug
(Asus eeePc 1001px, Ubuntu 10.04, soundcard "RealTek ALC269VB")


> **plastoid-ru said:**
> What I deed with Asus eeepc 1001PX and Ubuntu 10.10.

[B][COLOR="Blue"]To switch built-in microphone on:
1. Download and build **hda-verb**.
Set hda-verb **executable** and copy to **/usr/local/bin/**[/COLOR][/B]

2. No need to modify /etc/modprobe.d/alsa-base.conf

3. Add hda-verb call to /etc/rc.local

> [B]sudo pico /etc/rc.local
[/B]
enter before **exit**:
...

**/usr/local/bin/hda-verb /dev/snd/hwC0D0 0x023 SET_CONNECT_SEL 0x5**

exit 0


4. reboot

5. mic shoud work now.


P.S. After 
install of Ubuntu 10.10, audio playback works ok via EEEPC speakers and automatically switches to HEADPHONES when I plug them in EEEPC. So no need to other tricks. My audio works fine.

---

### Post by lidex on 2010-12-12
Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]

---

### Post by irpsit on 2010-12-15
OI installed today a fresh Ubuntu 10.10 installation.

Sound works perfect but Microphone does not work out of the box.

This is the result you asked for detailed information.
[http://www.alsa-project.org/db/?f=1d6c2a73abe6cd5cfb1a9b635faa944826434b54](http://www.alsa-project.org/db/?f=1d6c2a73abe6cd5cfb1a9b635faa944826434b54)

I haven't tried to remove pulseaudio this time nor edit the alsabase.conf file.
But I have set the microphone, left channel to 70%, right channel to 0%.

Do you have a solution?
I do I try the hda-verb solution?


QUOTE=lidex;10231747]Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"][/QUOTE]

---

### Post by lidex on 2010-12-16
@irpsit
Try this. 
Using a Terminal="Applications->Accessories->Terminal"
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

And if you don't have pulse audio volume control, install it and use to tweak mic settings.

---

### Post by irpsit on 2010-12-24
I tried with every different option, by editing the alsa-base.conf file
options snd-hda-intel model=auto
options snd-hda-intel model=fujitsu
options snd-hda-intel model=lifebook

In all of them, tried one by one and after rebooting every time, set all the capture devices to only the left (or right) channel, and also tried playing with choosing different microphones types, and still no recording sound with my microphone in my Asus eeePC 1001px (Maverick) with Alsa 1.0.23 (as seen by cat /proc/asound/version)

Later, I tried to install HDA-Analyser ([link]("http://www.alsa-project.org/main/index.php/HDA_Analyzer")) or also tried the alternative HDA-verb and played with different settings, suggested here ([link]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/580183")), including /usr/local/bin/hda-verb /dev/snd/hwC0D0 0x023 SET_CONNECT_SEL 0x5 and **[COLOR="Red"]nothing still makes the internal microphone work[/COLOR]**!

I am trying this with the gnome-sound-recorder (because I know of some other issues with Skype).

Could someone find a solution for this never-ending problem?

---

### Post by lidex on 2010-12-25
OK. Have a look at these:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/580183](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/580183)
[http://translate.google.com/translate?js=n&prev=_t&hl=en&ie=UTF-8&layout=2&eotf=1&sl=es&tl=en&u=http%3A%2F%2Fwww.ubuntu-es.org%2Fnode%2F137762](http://translate.google.com/translate?js=n&prev=_t&hl=en&ie=UTF-8&layout=2&eotf=1&sl=es&tl=en&u=http%3A%2F%2Fwww.ubuntu-es.org%2Fnode%2F137762)
[http://translate.google.com/translate?js=n&prev=_t&hl=en&ie=UTF-8&layout=2&eotf=1&sl=es&tl=en&u=http%3A%2F%2Faprendiendoconubuntu.blogspot.com%2F2010%2F10%2Fprimeros-pasos-con-ubuntu-lucid-lynx-en.html](http://translate.google.com/translate?js=n&prev=_t&hl=en&ie=UTF-8&layout=2&eotf=1&sl=es&tl=en&u=http%3A%2F%2Faprendiendoconubuntu.blogspot.com%2F2010%2F10%2Fprimeros-pasos-con-ubuntu-lucid-lynx-en.html)
[http://ubuntuforums.org/showthread.php?t=1607552](http://ubuntuforums.org/showthread.php?t=1607552)
[http://ubuntuforums.org/showthread.php?t=1574105](http://ubuntuforums.org/showthread.php?t=1574105)

---

### Post by irpsit on 2010-12-27
Thanks a lot.

I tried everything from the links below.
But nothing worked.

No alsa-base.conf modification (I tried all).
No hda-verb (tried several of suggestions before).
No alsa-driver problems, because they are the latest (1.0.23) and neither sudo apt-get install linux-alsa-driver-modules-$(uname -r).
No pulseaudio removal with model=fujitsu, and also with editing the rc.local file

Nothing works. And it's a fresh install.

Is there someone with the internal microphone working???

> **lidex said:**
> OK. Have a look at these:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/580183](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/580183)
[http://translate.google.com/translate?js=n&prev=_t&hl=en&ie=UTF-8&layout=2&eotf=1&sl=es&tl=en&u=http%3A%2F%2Fwww.ubuntu-es.org%2Fnode%2F137762](http://translate.google.com/translate?js=n&prev=_t&hl=en&ie=UTF-8&layout=2&eotf=1&sl=es&tl=en&u=http%3A%2F%2Fwww.ubuntu-es.org%2Fnode%2F137762)
[http://translate.google.com/translate?js=n&prev=_t&hl=en&ie=UTF-8&layout=2&eotf=1&sl=es&tl=en&u=http%3A%2F%2Faprendiendoconubuntu.blogspot.com%2F2010%2F10%2Fprimeros-pasos-con-ubuntu-lucid-lynx-en.html](http://translate.google.com/translate?js=n&prev=_t&hl=en&ie=UTF-8&layout=2&eotf=1&sl=es&tl=en&u=http%3A%2F%2Faprendiendoconubuntu.blogspot.com%2F2010%2F10%2Fprimeros-pasos-con-ubuntu-lucid-lynx-en.html)
[http://ubuntuforums.org/showthread.php?t=1607552](http://ubuntuforums.org/showthread.php?t=1607552)
[http://ubuntuforums.org/showthread.php?t=1574105](http://ubuntuforums.org/showthread.php?t=1574105)

---

### Post by lidex on 2010-12-29
Time to file a bug report. 
Try running this command in a terminal for 10.04 or later:
```
ubuntu-bug audio
```
Reference the Ubuntu-Bug Audio link in my sig.

---

### Post by ansgar1 on 2010-12-29
mine works after installing** pavucontrol** and changing the stereosetting for the microphone. It &#347; set as a strero mic, but it isn't. So i set one chanel to 0% and everything works. (see [http://wiki.ubuntuusers.de/Asus_Eee_PC](http://wiki.ubuntuusers.de/Asus_Eee_PC))

---

### Post by irpsit on 2010-12-31
I have filled for a bug, no reply yet!!
[https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/689258](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/689258)

Of course I set the microphone to mono, no recording ever worked so far

---

### Post by lidex on 2011-01-01
> **irpsit said:**
> I have filled for a bug, no reply yet!!
[https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/689258](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/689258)

Of course I set the microphone to mono, no recording ever worked so far
I see your original bug report was against:
```
DistroRelease: Ubuntu 10.04
Package: alsa-base 1.0.22.1+dfsg-0ubuntu3
ProcVersionSignature: Ubuntu 2.6.32-26.48-generic 2.6.32.24+drm33.11
Uname: Linux 2.6.32-26-generic x86_64
AlsaVersion:
 Advanced Linux Sound Architecture Driver Version 1.0.23.
 Compiled on Dec 12 2010 for kernel 2.6.32-26-generic (SMP).
AplayDevices:
 **** List of PLAYBACK Hardware Devices ****
 card 0: Intel [HDA Intel], device 0: ALC269VB Analog [ALC269VB Analog]
```
But you're now using maverick and it's showing your codec as ALC259. There may be a clue there. You may want to update the bug filing and include alsa-info. In this case save it locally and upload as an attachment to launchpad.

---

### Post by datokakava on 2011-01-07
Hey!
well, i am new with UBUNTU, but i really wanna have have,
installed it on my 1001PX, but i cant record sound, and make skype calls, well, mic simply doesnt work.
is there any possible way to fix it.
well, i have tried everything. still doesn't work!
best!
D.

---

### Post by lidex on 2011-01-07
> **datokakava said:**
> Hey!
well, i am new with UBUNTU, but i really wanna have have,
installed it on my 1001PX, but i cant record sound, and make skype calls, well, mic simply doesnt work.
is there any possible way to fix it.
well, i have tried everything. still doesn't work!
best!
D.

[https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/689258](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/689258)
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/580183](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/580183)
[http://www.ubuntu-es.org/node/137762](http://www.ubuntu-es.org/node/137762)

---

### Post by datokakava on 2011-01-08
> **lidex said:**
> [https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/689258](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/689258)
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/580183](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/580183)
[http://www.ubuntu-es.org/node/137762](http://www.ubuntu-es.org/node/137762)

well, i tried all this with ubuntu 10.10 desktop editon,
deosnt work

---

### Post by lidex on 2011-01-08
> **datokakava said:**
> well, i tried all this with ubuntu 10.10 desktop editon,
deosnt work
Exactly. You should sign onto one of those bugs.

---

### Post by GalacticHitch on 2011-01-19
I've recently bought an EEE PC 1001px and installed Ubuntu 10.10 netbook remix. 
Upon installation I discovered that the internal mic was not working.

I was primarily buying this machine to communicate with my wife via Skype. So getting the mic to work is pretty critical.

I tried almost every solution suggested in the forums:
-installing pavucontrol and balancing mic input fully to the left in both pulse audio and alsamixer.
-changing setting in /etc/modpbrobe.d/alsa-base.conf to 'lifebook', 'fujitsu', and 'auto'.
-installing the newest alsa drivers

the only thing I didn't try was solution with hda-verb.

while trying different combinations of mic balance vs. alsa-base.conf settings I noticed that my mic started working after a suspend and restore. This happened with options snd-hda-intel model=auto and mic balance pushed almost all the way to the left. All I had to do is reduce mic boost to get acceptable sound level.
I also had to turn off auto volume adjustment in Skype settings and it worked like a miracle.

I enfjoyed playing with the machine for a while, even added desktop edition of Ubuntu, and the behavior persisted. I just had to cycle through suspend/restore to make the mic work. 

After a while I decided to ditch the netbook edition altogether and to do a fresh desktop edition install/repartition the harddrive. Upon a fresh install of Ubuntu 10.10 desktop edition (32 bit) I've managed to replicate this behaviour. Here's what I did:

1. I added 'options snd-hda-intel model=auto' to alsa-base.conf
2. Installed pavucontrol (Pulse Audio Control) and set mic input balance to the left channel
3. Updated to the latest alsa drivers as described in [https://wiki.ubuntu.com/Audio/InstallingLinuxAlsaDriverModules.]("https://wiki.ubuntu.com/Audio/InstallingLinuxAlsaDriverModules")

After completing installation and rebooting the system, the suspend/restore enabled the mic again!
Not sure step 1 is really needed, above, but this is the way I did it.

Hope this temporary solution will work for you.  
[URL="https://wiki.ubuntu.com/Audio/InstallingLinuxAlsaDriverModules"]
[/URL]

---

### Post by frankbooth on 2011-01-19
> **GalacticHitch said:**
> I've recently bought an EEE PC 1001px and installed Ubuntu 10.10 netbook remix. 
Upon installation I discovered that the internal mic was not working.

I was primarily buying this machine to communicate with my wife via Skype. So getting the mic to work is pretty critical.

I tried almost every solution suggested in the forums:
-installing pavucontrol and balancing mic input fully to the left in both pulse audio and alsamixer.
-changing setting in /etc/modpbrobe.d/alsa-base.conf to 'lifebook', 'fujitsu', and 'auto'.
-installing the newest alsa drivers

the only thing I didn't try was solution with hda-verb.

while trying different combinations of mic balance vs. alsa-base.conf settings I noticed that my mic started working after a suspend and restore. This happened with options snd-hda-intel model=auto and mic balance pushed almost all the way to the left. All I had to do is reduce mic boost to get acceptable sound level.
I also had to turn off auto volume adjustment in Skype settings and it worked like a miracle.

I enfjoyed playing with the machine for a while, even added desktop edition of Ubuntu, and the behavior persisted. I just had to cycle through suspend/restore to make the mic work. 

After a while I decided to ditch the netbook edition altogether and to do a fresh desktop edition install/repartition the harddrive. Upon a fresh install of Ubuntu 10.10 desktop edition (32 bit) I've managed to replicate this behaviour. Here's what I did:

1. I added 'options snd-hda-intel model=auto' to alsa-base.conf
2. Installed pavucontrol (Pulse Audio Control) and set mic input balance to the left channel
3. Updated to the latest alsa drivers as described in [https://wiki.ubuntu.com/Audio/InstallingLinuxAlsaDriverModules.]("https://wiki.ubuntu.com/Audio/InstallingLinuxAlsaDriverModules")

After completing installation and rebooting the system, the suspend/restore enabled the mic again!
Not sure step 1 is really needed, above, but this is the way I did it.

Hope this temporary solution will work for you.  
[URL="https://wiki.ubuntu.com/Audio/InstallingLinuxAlsaDriverModules"]
[/URL]

Yeah, suspend & restore seems to work for some. What model do you have? (should be a sticker on the bottom of the laptop) and what BIOS version do you have?

---

### Post by GalacticHitch on 2011-01-19
> **frankbooth said:**
> Yeah, suspend & restore seems to work for some. What model do you have? (should be a sticker on the bottom of the laptop) and what BIOS version do you have?

The sticker on the bottom says '1001PX-BLK015X MB rev 1001PX 12'

Again, I notice that this suspend/restore trick only works aftre updating alsa drivers to the latest version. The ones included into 10.10 distro don't work this way.

---

### Post by yavor1912 on 2011-01-21
How do you make "suspend and restore". I did everything except that

---

### Post by just_another_user on 2011-01-21
> **yavor1912 said:**
> How do you make "suspend and restore". I did everything except that
Click on 'power' menu, which you use to restart or shutdown your pc, and there you can find also 'suspend'. So do it and then wake it up.

Just tried this method with suspention, and built-in mic is working now. That's great! And in 10.10 it's much easier to update alsa drivers comparing to for example 9.04.

I have Asus 1005PX netbook.

---

### Post by frankbooth on 2011-02-20
For those that didn't know, the issue is being discussed here: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/580183](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/580183)

I think we've found a solution that will work for everyone, we can't be sure unless more people try it though. At least it works for me and another fellow and we both have different models (model# can be found under the laptop, mine is: ASUS 1001PX-BLK044S).

**Anyway, this might work for everyone, please try if previous solutions haven't worked:**

**1)** Update BIOS to 1102
**2)** Follow these instructions for the latest drivers: [https://wiki.ubuntu.com/Audio/InstallingLinuxAlsaDriverModules](https://wiki.ubuntu.com/Audio/InstallingLinuxAlsaDriverModules)
**3)** Reboot, the microphone should now work after a suspend & resume.

**PLEASE NOTE:**
This worked for me on Lubuntu 10.10, _I DON'T USE PULSEAUDIO_.
That means it should work fine on Ubuntu 10.10 without PulseAudio. _If it works with PulseAudio? I have no idea..._ Try :).

---

### Post by garok89 on 2011-02-21
> **frankbooth said:**
> For those that didn't know, the issue is being discussed here: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/580183](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/580183)

I think we've found a solution that will work for everyone, we can't be sure unless more people try it though. At least it works for me and another fellow and we both have different models (model# can be found under the laptop, mine is: ASUS 1001PX-BLK044S).

**Anyway, this might work for everyone, please try if previous solutions haven't worked:**

**1)** Update BIOS to 1102
**2)** Follow these instructions for the latest drivers: [https://wiki.ubuntu.com/Audio/InstallingLinuxAlsaDriverModules](https://wiki.ubuntu.com/Audio/InstallingLinuxAlsaDriverModules)
**3)** Reboot, the microphone should now work after a suspend & resume.

**PLEASE NOTE:**
This worked for me on Lubuntu 10.10, _I DON'T USE PULSEAUDIO_.
That means it should work fine on Ubuntu 10.10 without PulseAudio. _If it works with PulseAudio? I have no idea..._ Try :).

worked for me on a fresh install
now i just need to figure out how to get it working on boot instead of on resume

---

### Post by spoiled-tv on 2011-02-22
> **frankbooth said:**
> For those that didn't know, the issue is being discussed here: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/580183](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/580183)

I think we've found a solution that will work for everyone, we can't be sure unless more people try it though. At least it works for me and another fellow and we both have different models (model# can be found under the laptop, mine is: ASUS 1001PX-BLK044S).

**Anyway, this might work for everyone, please try if previous solutions haven't worked:**

**1)** Update BIOS to 1102
**2)** Follow these instructions for the latest drivers: [https://wiki.ubuntu.com/Audio/InstallingLinuxAlsaDriverModules](https://wiki.ubuntu.com/Audio/InstallingLinuxAlsaDriverModules)
**3)** Reboot, the microphone should now work after a suspend & resume.

**PLEASE NOTE:**
This worked for me on Lubuntu 10.10, _I DON'T USE PULSEAUDIO_.
That means it should work fine on Ubuntu 10.10 without PulseAudio. _If it works with PulseAudio? I have no idea..._ Try :).
I have a 1215t, HDA verb stopped sound from working and did not fix my mic, I did the above and sound works but still no mic. 


[http://www.alsa-project.org/db/?f=eeef43c7d9526a185765211e6555a5bfe4b6c5f3](http://www.alsa-project.org/db/?f=eeef43c7d9526a185765211e6555a5bfe4b6c5f3)

Any ideas?

---

### Post by frankbooth on 2011-02-22
> **garok89 said:**
> worked for me on a fresh install
now i just need to figure out how to get it working on boot instead of on resume

Cool! Could you please check and tell us what model you've got? We need to figure out what specific process wakes up and makes the microphone work. After that maybe we can autorun a script so we don't need to suspend/resume.

---

### Post by angryswede on 2011-03-10
I can confirm the suspend and resume works on ubuntu 10.10 desktop edition with my asus eee pc 1001px-eu17-bk.  This was after I had update to the latest kernel and installed the upstream pulseaudio dev packages to get the speakers working. Is there anyone who is more knowledgeable who can explain what kind of impact suspend has on the audio subsystem?

---

### Post by Yellow Pasque on 2011-03-10
> **spoiled-tv said:**
> I have a 1215t, HDA verb stopped sound from working and did not fix my mic, I did the above and sound works but still no mic.
[http://www.alsa-project.org/db/?f=eeef43c7d9526a185765211e6555a5bfe4b6c5f3](http://www.alsa-project.org/db/?f=eeef43c7d9526a185765211e6555a5bfe4b6c5f3)
Any ideas?

Try some keywords in /etc/modprobe/alsa-base.conf using 'options snd-hda-intel model=<model>'

```
ALC269
======
  basic		Basic preset
  quanta	Quanta FL1
  laptop-amic	Laptops with analog-mic input
  laptop-dmic	Laptops with digital-mic input
  fujitsu	FSC Amilo
  lifebook	Fujitsu Lifebook S6420
  auto		auto-config reading BIOS (default)

```

---

### Post by mario_26 on 2011-04-10
Hello, I am new to the forum, I'm French and do not coprend much English. I come to your meeting because I also have a problem with my microphone assus 1001px "Ubuntu 10.10" and I want to know if anyone has solved the problem? I tested your solution but it works yet 

 Bye

---

### Post by lidex on 2011-04-13
> **mario_26 said:**
> Hello, I am new to the forum, I'm French and do not coprend much English. I come to your meeting because I also have a problem with my microphone assus 1001px "Ubuntu 10.10" and I want to know if anyone has solved the problem? I tested your solution but it works yet 

 Bye

You tried this solution:
[http://ubuntuforums.org/showpost.php?p=10374439&postcount=33](http://ubuntuforums.org/showpost.php?p=10374439&postcount=33)

---

### Post by mario_26 on 2011-04-14
Thank you, it's great !! But it works only with the ubuntu 10.10 kernel.

 Bye

---

### Post by ManishChiniwalar on 2011-04-17
> **EowynCarter said:**
> hey, other 1001px users :)

Right now, i'm having problme with battery life. 
how long does the battery hold for you ?
try using jupiter to extend battery life :)
[http://www.jupiterapplet.org/]("http://www.jupiterapplet.org/")

---

### Post by rgstrator on 2011-06-03
[FONT=Verdana]Well, no need for this thread anymore- everybody take a look at this: 

[http://www.extremetech.com/article2/0,2845,2386355,00.asp](http://www.extremetech.com/article2/0,2845,2386355,00.asp)

In short, ASUS is returning to Linux. Even more so, to Ubuntu. 

No word on releasing new machines, it will rather retrofit the eee 1001PXD, 1011PX and 1015PX with Ubuntu 10.10. The hardware is not that different, so hopefully most eee+Ubuntu problems will be gone.



[/FONT]

---

### Post by arttymi on 2012-12-23
> **rgstrator said:**
> [FONT=Verdana]Well, no need for this thread anymore- everybody take a look at this: 

[http://www.extremetech.com/article2/0,2845,2386355,00.asp](http://www.extremetech.com/article2/0,2845,2386355,00.asp)

In short, ASUS is returning to Linux. Even more so, to Ubuntu. 

No word on releasing new machines, it will rather retrofit the eee 1001PXD, 1011PX and 1015PX with Ubuntu 10.10. The hardware is not that different, so hopefully most eee+Ubuntu problems will be gone.

[/FONT]

OK another way to quickly solve all sound problems is to get a headphone + a USB Sound Adapter (should be $10 - $ 15 or so). In Sound Settings choose the USB Audio Adapter as input and/or output source, depending on your problem. Never mind the crossed red circle driver sign, everything's ok. Easy!

---

### Post by overdrank on 2012-12-23
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/index.php?page=policy")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---

