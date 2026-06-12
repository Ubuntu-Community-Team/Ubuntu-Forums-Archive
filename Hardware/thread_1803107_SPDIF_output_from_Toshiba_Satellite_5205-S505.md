---
title: "S/PDIF output from Toshiba Satellite 5205-S505"
date: 2011-07-12
forum: Hardware
---

### Post by Old Toshiba on 2011-07-12
Hello again,

I have an aging Toshiba laptop and recently made the switch from Windows XP to Ubuntu 10.04. Most features have worked out-of-the-box with Ubuntu. However, the optical output (aka IEC958 or SPDIF) does not work. I have roamed the forums looking for a fix. Most people seem to have solved it simply by installing GNOME Alsamixer. I have the application installed and fiddled with all the settings, but cannot seem to get sound through the digital output. I can see that light is being passed through the TOSLINK cable, but no sound is coming from my stereo receiver. Using alsamixer from the terminal does not work either. 

Can anyone point me in the right direction?

Thanks!

Here's some outputs which may help...

```
uname -a
Linux Toshiba 2.6.35-25-generic #44~lucid1-Ubuntu SMP Tue Jan 25 19:19:31 UTC 2011 i686 GNU/Linux
``````
aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: I82801CAICH3 [Intel 82801CA-ICH3], device 0: Intel ICH [Intel 82801CA-ICH3]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
``````
aplay -L
pulse
    Playback/recording through the PulseAudio sound server
front:CARD=I82801CAICH3,DEV=0
    Intel 82801CA-ICH3, Intel 82801CA-ICH3
    Front speakers
surround40:CARD=I82801CAICH3,DEV=0
    Intel 82801CA-ICH3, Intel 82801CA-ICH3
    4.0 Surround output to Front and Rear speakers
surround41:CARD=I82801CAICH3,DEV=0
    Intel 82801CA-ICH3, Intel 82801CA-ICH3
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=I82801CAICH3,DEV=0
    Intel 82801CA-ICH3, Intel 82801CA-ICH3
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=I82801CAICH3,DEV=0
    Intel 82801CA-ICH3, Intel 82801CA-ICH3
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
iec958:CARD=I82801CAICH3,DEV=0
    Intel 82801CA-ICH3, Intel 82801CA-ICH3
    IEC958 (S/PDIF) Digital Audio Output
``````
cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.23.
```

---

### Post by lidex on 2011-07-15
Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]

---

### Post by Old Toshiba on 2011-07-15
Here is the terminal output:
```

wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh
--2011-07-15 17:05:29--  http://www.alsa-project.org/alsa-info.sh
Resolving www.alsa-project.org... 77.48.224.243
Connecting to www.alsa-project.org|77.48.224.243|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: http://git.alsa-project.org/?p=alsa-driver.git;a=blob_plain;f=utils/alsa-info.sh [following]
--2011-07-15 17:05:30--  http://git.alsa-project.org/?p=alsa-driver.git;a=blob_plain;f=utils/alsa-info.sh
Resolving git.alsa-project.org... 77.48.224.243
Reusing existing connection to www.alsa-project.org:80.
HTTP request sent, awaiting response... 200 OK
Length: unspecified [text/plain]
Saving to: `alsa-info.sh'

    [  <=>                                  ] 27,247      56.0K/s   in 0.5s    

2011-07-15 17:05:32 (56.0 KB/s) - `alsa-info.sh' saved [27247]

ALSA Information Script v 0.4.60
--------------------------------

This script visits the following commands/files to collect diagnostic
information about your ALSA installation and sound related hardware.

  dmesg
  lspci
  lsmod
  aplay
  amixer
  alsactl
  /proc/asound/
  /sys/class/sound/
  ~/.asoundrc (etc.)

See 'alsa-info.sh --help' for command line options.

Automatically upload ALSA information to www.alsa-project.org? [y/N] : y
Uploading information to www.alsa-project.org ...  Done!

Your ALSA information is located at 
Please inform the person helping you.
```One thing I find odd is that it says "Your ALSA information is located at [blank]"

---

### Post by lidex on 2011-07-15
> **Old Toshiba said:**
> Here is the terminal output:
```

wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh
--2011-07-15 17:05:29--  http://www.alsa-project.org/alsa-info.sh
Resolving www.alsa-project.org... 77.48.224.243
Connecting to www.alsa-project.org|77.48.224.243|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: http://git.alsa-project.org/?p=alsa-driver.git;a=blob_plain;f=utils/alsa-info.sh [following]
--2011-07-15 17:05:30--  http://git.alsa-project.org/?p=alsa-driver.git;a=blob_plain;f=utils/alsa-info.sh
Resolving git.alsa-project.org... 77.48.224.243
Reusing existing connection to www.alsa-project.org:80.
HTTP request sent, awaiting response... 200 OK
Length: unspecified [text/plain]
Saving to: `alsa-info.sh'

    [  <=>                                  ] 27,247      56.0K/s   in 0.5s    

2011-07-15 17:05:32 (56.0 KB/s) - `alsa-info.sh' saved [27247]

ALSA Information Script v 0.4.60
--------------------------------

This script visits the following commands/files to collect diagnostic
information about your ALSA installation and sound related hardware.

  dmesg
  lspci
  lsmod
  aplay
  amixer
  alsactl
  /proc/asound/
  /sys/class/sound/
  ~/.asoundrc (etc.)

See 'alsa-info.sh --help' for command line options.

Automatically upload ALSA information to www.alsa-project.org? [y/N] : y
Uploading information to www.alsa-project.org ...  Done!

Your ALSA information is located at 
Please inform the person helping you.
```One thing I find odd is that it says "Your ALSA information is located at [blank]"

Yeah, its been doing that lately, not sure why. Try running with the --no-upload flag:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh --no-upload
```

---

### Post by Old Toshiba on 2011-07-16
Ok. The script output is attached. ;-)

---

### Post by lidex on 2011-07-16
> **Old Toshiba said:**
> Ok. The script output is attached. ;-)

Dude, you made me open Libre Office :rolleyes:
Familiar with alsamixer? 
**Alsamixer**
Using a Terminal="Applications->Accessories->Terminal"
```
 alsamixer 
```
Press <F6> to select the correct soundcard.
Press <F3> to show playback levels. <F4> selects capture levels [or use <Tab>]
Use the left/right arrow keys to select and up/down arrow keys to change levels. <M> to mute/unmute.

Can you post screenshots of the playback levels?

---

### Post by Old Toshiba on 2011-07-17
> **lidex said:**
> Dude, you made me open Libre Office :rolleyes:

I was hoping I could get you to use MS Word. :P

> **lidex said:**
>  
Familiar with alsamixer? 

Can you post screenshots of the playback levels?

Yup. The screenshots are attached. Now before you say anything about the S/PDIF playback levels, I have increased them to max before with no success. Once playback begins, the S/PDIF output level drops back to zero. When playback is stopped, the output level resumes to the max setting or the setting it was originally set to.

The GNOME Alsamixer does not seem to have this behavior, but the result are the same. I have tried just about every combination of toggles and sliders to try to get sound. I even played with the output device types in System -> Preferences -> Sound. :confused:

---

### Post by lidex on 2011-07-17
I'm sure its something simple. Have you tried unmuting spdifM and changing masterM level? Make sure all spdif elements are unmuted. Go ahead and enable spdifP as well and try toggling AC-link.

[http://alsa.opensrc.org/DigitalOut](http://alsa.opensrc.org/DigitalOut)

---

### Post by Old Toshiba on 2011-07-17
> **lidex said:**
> I'm sure its something simple. Have you tried unmuting spdifM and changing masterM level? Make sure all spdif elements are unmuted. Go ahead and enable spdifP as well and try toggling AC-link.

[http://alsa.opensrc.org/DigitalOut](http://alsa.opensrc.org/DigitalOut)

I wish it was. I have unmuted Master Mono along with enabling every S/PDIF option except for mute. I've tried both AC-link and A/D converter. I've tried enabling S/PDIF pins 43 and 48 with no success. (Pin 43 does make the output light dim a bit though.) Believe me, I've tried just about every possible combination that can be done in alsamixer.

What I find odd is that whenever the hardware in System -> Preferences -> Sound is set to any option with a digital output, alsamixer will not let me turn up the volume of the S/PDIF during playback. Like I was saying before, that output always drops to zero. However, if I change the hardware to "analog output" or "analog duplex" I can set and keep the S/PDIF volume wherever I want. Still, no sound comes out of the thing.:confused:

---

### Post by lidex on 2011-07-17
Yeah, nothing comes to mind. Did you try the link?

EDIT: try the link in my sig to update your alsa install. These versions don't look right:
```
!!ALSA Version
!!------------

Driver version:     1.0.23
Library version:    1.0.22
Utilities version:  1.0.22
```

---

### Post by Old Toshiba on 2011-07-18
Ok. I've updated my alsa version and still have the same troubles. 
 
```
 
!!ALSA Version
!!------------
 
Driver version:     1.0.24
Library version:    1.0.24-1
Utilities version:  1.0.24-2

```
 
I've also read through that entire alsa wiki article several times. There are few portions of the troubleshooting section which apply. I am working with only one soundcard (that can be found anyway) and have never had sound through it since Ubuntu.
 
I think as a sanity check, I am going to try another computer's S/PDIF output into the same receiver just to make sure the thing still works.

---

### Post by lidex on 2011-07-18
Try this:
```
sudo rmmod snd-intel8x0
```
```
sudo modprobe snd-ymfpci
```

---

### Post by Old Toshiba on 2011-07-22
Well, I tried the S/PDIF on the receiver with a different computer and it works. 
 
I couldn't remove the snd_intel8x0 module. Instead, I just put it on the blacklist. When I restart, there was no sound. I loaded the snd_ymfpci module and there is still no sound after restarting again.

---

### Post by lidex on 2011-07-22
> **Old Toshiba said:**
> Well, I tried the S/PDIF on the receiver with a different computer and it works. 
 
I couldn't remove the snd_intel8x0 module. Instead, I just put it on the blacklist. When I restart, there was no sound. I loaded the snd_ymfpci module and there is still no sound after restarting again.

Those commands are not permanent, only for the session. Run the commands as written and then run the alsa-info script.

---

### Post by Old Toshiba on 2011-07-22
I must be missing something. If I don't blacklist the current sound driver, I cannot remove it because it will always be in use. ](*,)

```

sudo rmmod snd-intel8x0
ERROR: Module snd_intel8x0 is in use
```

The script says nothing different--the snd_intel8x0 driver is being used.

---

### Post by lidex on 2011-07-22
Gotcha. Run the script after blacklisting snd-intel8x0 and modprobing snd-ymfpci

---

### Post by Old Toshiba on 2011-07-22
Doesn't look good.:(

---

### Post by Old Toshiba on 2011-07-26
Hi lidex,

I have come across the work of someone else, David Shust, who has run in to the same problem as myself. According to him, the YMF753 is non-standard when it comes to the S/PDIF output. With that, he's gone to far as to write a patch for the chip. I have the patch, but I do not know what to do with it. Here's the link:

[http://marcbug.scc-dc.com/svn/repository/tags/Linuxkernel_V1.1.0/linux-2.6.16-mcemu/sound/pci/ac97/ac97_patch.c](http://marcbug.scc-dc.com/svn/repository/tags/Linuxkernel_V1.1.0/linux-2.6.16-mcemu/sound/pci/ac97/ac97_patch.c)

Do you know if this patch has been baked into the newer ALSA drivers? If not, is there still a chance I could get it the digital out to work with this? If so, how do I do it?

Thanks.

---

### Post by Old Toshiba on 2012-03-19
I got it working and would like to share in case anyone else has the same problem.

My problem was that I had 10.04 installed with the 2.6.35 (Maverick) kernel. The patch for the sound card had been already implemented into the ALSA version which comes with 10.04. Once I reverted to the Lucid kernel and reinstalled ALSA, the optical output worked with only one modification. By default, the S/PDIF is set to disabled and needs to be set to pin 43 to work. Everything else, S/PDIF unmuted, volume at 0, set to AC-link, should be left alone. 

Sonic bliss has been restored.
:guitar:

---

