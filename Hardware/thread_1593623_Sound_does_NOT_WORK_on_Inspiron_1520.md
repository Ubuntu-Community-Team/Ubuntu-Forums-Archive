---
title: "Sound does NOT WORK on Inspiron 1520"
date: 2010-10-11
forum: Hardware
---

### Post by MrTripi on 2010-10-11
Ok, so I've been dealing with this issue since Ubuntu 8.0; but the sound simply does not work correctly on the Dell Inspiron 1520 even with the latest Ubuntu release.  

I understand that certain applications will try to access the sound card directly and that my laptop only has one channel, but this is ridiculous.  Everytime a new release is put out I cross my fingers and hope that they've somehow fixed pulseaudio, or rather how the OS implements it.

Certain applications will launch and play audio through pulseaudio correctly, I can have as many of these applications open at a time and won't experience any issues with sound.  But things like flash, even the latest version still DO NOT WORK.  

I've read countless threads about how alsa-utils is somehow missing some type of configuration in the latest Lucid release.  So I even tried updating my repository to jaunty and reinstalling it, still not good.  

So I reinstalled the latest version (Lucid) and this is what I get.

john@john-laptop:~$ asoundconf-gtk
sh: /usr/bin/asoundconf: not found
You need to make sure asoundconf is active!
By default, asoundconf's configuration file is ~/.asoundrc.asoundconf
and must be included in ~/.asoundrc. Open this file to make sure it is!

On the pulseaudio wiki is states that the latest version of adobe flash will use pulseaudio without any additional configuration, well I call BS; it still doesn't work.  

I even tried modifying the asound.conf file so that everything would be set to "type pulse".  Nothing, in fact I feel like I've done more harm than good.  Turning the volume down on my laptop no longer has any effect on the adobe flash plugin.

asound.conf
```

# Set default sound card
# Useful so that all settings can be changed to a different card here.
pcm.pulse {
    type pulse
}
ctl.pulse {
    type pulse
}
ctl.!default {
    type pulse
}

pcm.snd_card {
     #type hw
     type pulse
     card 0
}

# Allow mixing of multiple output streams to this device
pcm.dmixer {
     type dmix
     ipc_key 1024
     slave.pcm "snd_card"
     slave {
          # This stuff provides some fixes for latency issues.
          # buffer_size should be set for your audio chipset.
          period_time 0
          period_size 1024
          buffer_size 4096
          # rate 44100
     }

     bindings {
          0 0
          1 1
     }
}

# Allow reading from the default device.
# Also known as record or capture.
pcm.dsnooper {
     type dsnoop
     ipc_key 2048
     slave.pcm "snd_card"

     bindings {
          0 0
          1 1
     }
}

# This is what we want as our default device
# a fully duplex (read/write) audio device.
pcm.duplex {
     type asym
     playback.pcm "dmixer"
     capture.pcm "dsnooper"
}

###################
# CONVERSION PLUG #
###################
# Setting the default pcm device allows the conversion
# rate to be selected on the fly.
# duplex mode allows any alsa enabled app to read/write
# to the dmix plug (Fixes a problem with wine).

pcm.!default {
     #type asym
     #playback.pcm "dmixer"
     #capture.pcm "dsnooper"
	type pulse
}

########
# AOSS #
########
# OSS dsp0 device (OSS needs only output support, duplex will break some stuff)
pcm.dsp0 {
     type plug
     slave.pcm "dmixer"
}

# OSS control for dsp0 (needed?...this might not be useful)
ctl.dsp0 {
     type plug
     slave.pcm "snd_card"
}

# OSS control for dsp0 (default old OSS is mixer0)
ctl.mixer0 {
     type plug
     slave.pcm "snd_card"
}

```

Is there anyone out there who can help me out with this?  Getting tired of having to reboot my machine every time I visit youtube.

---

### Post by MrTripi on 2010-10-11
modified /etc/asound.conf

```

pcm.pulse {
    type pulse
}
ctl.pulse {
    type pulse
}
pcm.!default {
    type pulse
}
ctl.!default {
    type pulse
}

```

Still no luck :(

---

### Post by MrTripi on 2010-10-25
Is there anyway I can at least submit a bug report for this specific sound card?

---

### Post by lidex on 2010-10-25
Can you provide some more info please? First rename your '/etc/asound.conf' file so it isn't recognized. Now reboot and use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]

---

### Post by MrTripi on 2010-10-25
Bareword "asound" not allowed while "strict subs" in use at (eval 1) line 1.
Bareword "conf" not allowed while "strict subs" in use at (eval 1) line 1.
john@john-laptop:/etc$ rename asound.conf asound_bak.conf
Bareword "asound" not allowed while "strict subs" in use at (eval 1) line 1.
Bareword "conf" not allowed while "strict subs" in use at (eval 1) line 1.
john@john-laptop:/etc$ wget [http://www.alsa-project.org/alsa-info.sh](http://www.alsa-project.org/alsa-info.sh) -O alsa-info.sh && bash alsa-info.sh
alsa-info.sh: Permission denied
john@john-laptop:/etc$ sudo wget [http://www.alsa-project.org/alsa-info.sh](http://www.alsa-project.org/alsa-info.sh) -O alsa-info.sh && bash alsa-info.sh
--2010-10-25 22:56:41--  [http://www.alsa-project.org/alsa-info.sh](http://www.alsa-project.org/alsa-info.sh)
Resolving [www.alsa-project.org](www.alsa-project.org)... 212.20.107.51
Connecting to [www.alsa-project.org|212.20.107.51|:80](www.alsa-project.org|212.20.107.51|:80)... connected.
HTTP request sent, awaiting response... 302 Found
Location: [http://git.alsa-project.org/?p=alsa-driver.git;a=blob_plain;f=utils/alsa-info.sh](http://git.alsa-project.org/?p=alsa-driver.git;a=blob_plain;f=utils/alsa-info.sh) [following]
--2010-10-25 22:56:43--  [http://git.alsa-project.org/?p=alsa-driver.git;a=blob_plain;f=utils/alsa-info.sh](http://git.alsa-project.org/?p=alsa-driver.git;a=blob_plain;f=utils/alsa-info.sh)
Resolving git.alsa-project.org... 212.20.107.51
Reusing existing connection to [www.alsa-project.org:80](www.alsa-project.org:80).
HTTP request sent, awaiting response... 200 OK
Length: unspecified [text/plain]
Saving to: `alsa-info.sh'

    [   <=>                                 ] 27,026      39.2K/s   in 0.7s    

2010-10-25 22:56:45 (39.2 KB/s) - `alsa-info.sh' saved [27026]

ALSA Information Script v 0.4.59
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

Automatically upload ALSA information to [www.alsa-project.org?](www.alsa-project.org?) [y/N] : y
Uploading information to [www.alsa-project.org](www.alsa-project.org) ...  Done!

Your ALSA information is located at [http://www.alsa-project.org/db/?f=3504bee67a3a802d5071e57c204e75c8828f8f9a](http://www.alsa-project.org/db/?f=3504bee67a3a802d5071e57c204e75c8828f8f9a)

Please inform the person helping you.

john@john-laptop:/etc$

---

### Post by lidex on 2010-10-26
Interesting. Please rename/remove this file also:
```
!!User specific config file (~/.asoundrc)

 pcm.!default
 {
   type oss
   device /dev/dsp
 }
 mixer.!default
 {
   type oss
   device /dev/dsp
 }

```
Next go here and upgrade your alsa install:
[http://ubuntuforums.org/showthread.php?p=6589810#post6589810](http://ubuntuforums.org/showthread.php?p=6589810#post6589810)
Once done run the info script again.

---

### Post by MrTripi on 2010-10-27
Ok, this is after I had run the upgrade script, etc.  

john@john-laptop:~$ wget [http://www.alsa-project.org/alsa-info.sh](http://www.alsa-project.org/alsa-info.sh) -O alsa-info.sh && bash alsa-info.sh
--2010-10-27 02:25:53--  [http://www.alsa-project.org/alsa-info.sh](http://www.alsa-project.org/alsa-info.sh)
Resolving [www.alsa-project.org](www.alsa-project.org)... 212.20.107.51
Connecting to [www.alsa-project.org|212.20.107.51|:80](www.alsa-project.org|212.20.107.51|:80)... connected.
HTTP request sent, awaiting response... 302 Found
Location: [http://git.alsa-project.org/?p=alsa-driver.git;a=blob_plain;f=utils/alsa-info.sh](http://git.alsa-project.org/?p=alsa-driver.git;a=blob_plain;f=utils/alsa-info.sh) [following]
--2010-10-27 02:25:53--  [http://git.alsa-project.org/?p=alsa-driver.git;a=blob_plain;f=utils/alsa-info.sh](http://git.alsa-project.org/?p=alsa-driver.git;a=blob_plain;f=utils/alsa-info.sh)
Resolving git.alsa-project.org... 212.20.107.51
Reusing existing connection to [www.alsa-project.org:80](www.alsa-project.org:80).
HTTP request sent, awaiting response... 200 OK
Length: 27026 (26K) [text/plain]
Saving to: `alsa-info.sh'

100%[======================================>] 27,026      64.0K/s   in 0.4s    

2010-10-27 02:25:54 (64.0 KB/s) - `alsa-info.sh' saved [27026/27026]

ALSA Information Script v 0.4.59
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

Automatically upload ALSA information to [www.alsa-project.org?](www.alsa-project.org?) [y/N] : y
Uploading information to [www.alsa-project.org](www.alsa-project.org) ...  Done!

Your ALSA information is located at [http://www.alsa-project.org/db/?f=8b6e384b6f71cab3c5397da71650dc2fdb2ce865](http://www.alsa-project.org/db/?f=8b6e384b6f71cab3c5397da71650dc2fdb2ce865)

Please inform the person helping you.

john@john-laptop:~$

---

### Post by lidex on 2010-10-27
You still have a config file in effect:
```
!!ALSA configuration files
!!------------------------

!!asoundconf-generated config file

 pcm.!default
 {
   type oss
   device /dev/dsp
 }
 mixer.!default
 {
   type oss
   device /dev/dsp
 }

```
Please remove for the purposes of testing.

---

### Post by MrTripi on 2010-10-27
I've already removed the two files you mentioned.  where can this one be located?

Assumed that this just meant it was reverting to some kind of default setting:

"!!asoundconf-generated config file"

---

### Post by MrTripi on 2010-10-27
ok, nevermind I found it.  The 3rd file was called asoundrc.asoundconf within the home/{user} directory



john@john-laptop:~$ sudo mv .asoundrc.asoundconf .asoundrc_old.asoundconf
[sudo] password for john: 
john@john-laptop:~$ wget [http://www.alsa-project.org/alsa-info.sh](http://www.alsa-project.org/alsa-info.sh) -O alsa-info.sh && bash alsa-info.sh
--2010-10-27 17:56:07--  [http://www.alsa-project.org/alsa-info.sh](http://www.alsa-project.org/alsa-info.sh)
Resolving [www.alsa-project.org](www.alsa-project.org)... 212.20.107.51
Connecting to [www.alsa-project.org|212.20.107.51|:80](www.alsa-project.org|212.20.107.51|:80)... connected.
HTTP request sent, awaiting response... 302 Found
Location: [http://git.alsa-project.org/?p=alsa-driver.git;a=blob_plain;f=utils/alsa-info.sh](http://git.alsa-project.org/?p=alsa-driver.git;a=blob_plain;f=utils/alsa-info.sh) [following]
--2010-10-27 17:56:08--  [http://git.alsa-project.org/?p=alsa-driver.git;a=blob_plain;f=utils/alsa-info.sh](http://git.alsa-project.org/?p=alsa-driver.git;a=blob_plain;f=utils/alsa-info.sh)
Resolving git.alsa-project.org... 212.20.107.51
Reusing existing connection to [www.alsa-project.org:80](www.alsa-project.org:80).
HTTP request sent, awaiting response... 200 OK
Length: unspecified [text/plain]
Saving to: `alsa-info.sh'

    [  <=>                                  ] 27,026      94.3K/s   in 0.3s    

2010-10-27 17:56:10 (94.3 KB/s) - `alsa-info.sh' saved [27026]

ALSA Information Script v 0.4.59
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

Automatically upload ALSA information to [www.alsa-project.org?](www.alsa-project.org?) [y/N] : y
Uploading information to [www.alsa-project.org](www.alsa-project.org) ...  Done!

Your ALSA information is located at [http://www.alsa-project.org/db/?f=daf4d5bc88507a62e7650cca3e17c85bbdda9ffc](http://www.alsa-project.org/db/?f=daf4d5bc88507a62e7650cca3e17c85bbdda9ffc)

Please inform the person helping you.

john@john-laptop:~$

---

### Post by lidex on 2010-10-27
Good question. Maybe:
```
/var/lib/alsa/
/usr/lib/alsa-lib/
/usr/lib32/alsa-lib/
/etc/
```

---

### Post by lidex on 2010-10-27
Good, nice and clean. Next I would like you to try adding some options to alsa-base.conf
Using a Terminal="Applications->Accessories->Terminal"
Open this file for editing:
```
 gksudo gedit /etc/modprobe.d/alsa-base.conf 
```
Insert this line at the bottom:
```
 options snd-hda-intel model=ref 
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

### Post by MrTripi on 2010-10-27
HoooooOOooly crap.  I think I got it working.  


it looks like the ".asoundrc.asoundconf" file in my /home/(user) directory was over riding /etc/asound.conf; forcing the new adobe flash plugin to use oss(i guess).  

After I renamed that file

"sudo mv .asoundrc.asoundconf .asoundrc_old.asoundconf"

I recreated the /etc/asound.conf file with the usual

```

pcm.pulse {
    type pulse
}
ctl.pulse {
    type pulse
}
pcm.!default {
    type pulse
}
ctl.!default {
    type pulse
}

```

IT WORKS.  WTF, damn! YESsss
:guitar::guitar::guitar::guitar::guitar::guitar::guitar::guitar::guitar:


Thanks for your help dude.  Would not have figured this out otherwise.

---

### Post by lidex on 2010-10-27
Nice. Please mark the thread solved using 'Thread Tools' up top.

---

