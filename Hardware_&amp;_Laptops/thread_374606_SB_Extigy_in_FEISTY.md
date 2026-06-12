---
title: "SB Extigy in FEISTY"
date: 2007-03-02
forum: Hardware &amp; Laptops
---

### Post by Mr Scipione on 2007-03-02
Ok, here's a tough one for you guys and gals!  I have surfed the forums for weeks now, and nothing I've found helped so I'm willing to try even the simplist fixes.  I have a SB Extigy and just installed FEISTY over EDGY in hopes that some of the updated features of FEISTY would solve my problem! NEIN.  Under both FEISTY and EDGY I have no sound from my soundcard.  My computer speakers do still beep.  I have previously used XP and Mandriva which both recognized and utilized my soundcard with absolutely no problems.  Allow me to start listing my various error messages starting now:  

alsamixer / sudo alsamixer : 
alsamixer: function snd_ctl_open failed for default: No such device  

rhythmbox playing a mp3: 
Could not open resource for writing.

multimedia systems selector "test" button error messages sorted by "plugin" selection:  
ESD:  ESD - Enlightenment Sound Daemon: Could not establish connection to sound server
ALSA:  ALSA - Advanced Linux Sound Architecture: Could not open resource for writing.
OSS: OSS - Open Sound System: Could not open resource for writing.
CUSTOM (pipeline OSSSINK): Custom: Could not open resource for writing.
AUTODETECT: Crashes application  

sudo alsaconf:  
sudo: alsaconf: command not found

Here is the output from trying to play a mp3 in mpg321:  
Title  : Breathing                       Artist: Yellowcard                    
Album  :                                 Year  :                               
Comment:                                 Genre :                               

Playing MPEG stream from Yellowcard - Breathing.mp3 ...
MPEG 1.0 layer III, 192 kbit/s, 44100 Hz joint-stereo
ALSA lib pcm_direct.c:1477:(_snd_pcm_direct_get_slave_ipc_offset) Invalid value for card
ALSA snd_pcm_open error: No such device
- using device -default
- using device -default
ALSA lib pcm.c:2145:(snd_pcm_open_noupdate) Unknown PCM -default
Can't find a suitable libao driver. (Is device in use?)


OK.  I'm pretty new to this stuff, but I guess the system is you send me a bunch of commands to run, and I paste the outputs.  So hold forth! My fingers await your command.  Oh, and please don't suggest buying new hardware that is a stupid suggestion that doesn't answer my question.

---

### Post by Mr Scipione on 2007-03-07
Problem resolved... extigy was being assigned to dev 1 instead of dev 0 .

---

### Post by kalunke on 2007-04-05
Same problem for me. How exactly did you solve it?

---

### Post by tscheepers on 2007-04-27
Same problem here. Please post the solution, I'm sure were not the only ones.

---

### Post by viralata00 on 2007-06-03
hello,

I have a SB extigy, Topcom voip phone and a  logitech webcam with a mic.
I use a 5.1 creative speaker set.

I can hear music (stereo) on xmms with ALSA driver -> audio device hw1,0
Totem can play audio (stereo) to....

but aMSN, system logon and logout doen't play any sound...

in the sound config i can hear the beep on sound events, Music and Movies and Audio Conferencing...

anyone can help me?

---

### Post by crimsun on 2007-06-03
> **viralata00 said:**
> I can hear music (stereo) on xmms with ALSA driver -> audio device hw1,0
Totem can play audio (stereo) to....

but aMSN, system logon and logout doen't play any sound...

If you specify a hardcoded hw: or plughw: device, that bypasses alsa-lib's dmix.  You need to use (i.e., type in) "plug:dmix:1" in the virtual device drop-down entry field, or simply use asoundconf(1) set-default-card then restart your sound apps.

---

### Post by viralata00 on 2007-06-07
Thanks crimsun, it work now.. :)

Can you put more than 1 aplication playing sound?

---

### Post by viralata00 on 2007-06-07
still can't hear amsn sound....how to play in 5.1 instead of stereo?

this don't work:

gedit ~/.asoundrc

    * Enter the following section: 

pcm.!default {
    type plug
    slave.pcm "surround51"
    slave.channels 6
    route_policy duplicate
}

---

### Post by viralata00 on 2007-06-07
I solved all the sound problems using ESD....now aMSN, xmms.totem,system plays sounds....

Now I just need to play it on 5.1 ...or  virtual 5.1 ....

---

### Post by nilord on 2007-09-12
I also have SB Extigy. It produces sound only in the FRONT Stereo Output.

Also, can you use the front panel (Volume Knobs, etc.) of your extigy in ubuntu?

I'm really having a hard time making it work.

Thanks in advance!

---

### Post by sonicsmooth on 2007-10-31
I was unable to get any exact specific instructions in this thread.

When I first installed 7.04 sound sometimes seemed to work through the SPDIF output, but I think things were confused since not all applications actually used the sound, only some streaming player which I don't remember.  Also I had the onboard audio enabled in the BIOS. Since then I've disabled the BIOS sound chip, installed an uninstalled a zillion multimedia things, including a pcHDTV card, and sound through my extigy is now mostly broken.  I've followed Comprehensive Sound Problem Solutions Guide v0.5e with some success.

When I try aplay -l I get:
```
card 1: Extigy [Sound Blaster Extigy], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Extigy [Sound Blaster Extigy], device 1: USB Audio [USB Audio #1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Extigy [Sound Blaster Extigy], device 2: USB Audio [USB Audio #2]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

This is a USB external audio card so nothing relevant shows up when I do lspci.


When I do lsmod | grep snd I get:

```
snd_usb_audio          81024  0 
snd_usb_lib            17920  1 snd_usb_audio
snd_rawmidi            25728  1 snd_usb_lib
snd_seq_device          9228  1 snd_rawmidi
snd_hwdep              10244  1 snd_usb_audio
snd_pcm                80388  2 cx88_alsa,snd_usb_audio
snd_timer              24324  1 snd_pcm
snd                    54660  7 cx88_alsa,snd_usb_audio,snd_rawmidi,snd_seq_device,snd_hwdep,snd_pcm,snd_timer
soundcore               8800  1 snd
snd_page_alloc         11400  1 snd_pcm
usbcore               138632  8 usbhid,xpad,snd_usb_audio,snd_usb_lib,uhci_hcd,ehci_hcd,ohci_hcd

```

my /etc/modules file contains:
```
fuse
lp
cx88-dvb

```

The last entry is because my pcHDTV card has an audio output I think, which I don't intend to use right now.

I have removed (purged) and reinstalled linux-sound-base alsa-base alsa-utils gdm ubuntu-desktop and rebooted.

Running alsa mixer *gave* me only the mixer for the cx88 device.
When I modprobe -r removed the cx88 device then alsamixer said something about snd_ctl not found or something.  I thought it would automatically pick up the extigy device since that module was already loaded.

At this point no sound of any sort came out, and the mixer did not show anything useful.

Then I ran asoundconf set-default-card Extigy without a lot of feedback or anything in the man pages.  It left this file .asoundrc
```
# ALSA library configuration file

# Include settings that are under the control of asoundconf(1).
# (To disable these settings, comment out this line.)
</home/sonic/.asoundrc.asoundconf>

```

Then as I was typing this post I reran alsamixer and the extigy mixer came up.  Also whereas before I had a bunch of "audiotestsrc wave=sine freq=512 ! audioconvert" errors when trying a test sound, I now only have that when I try running a test sound with oss and/or esd, which I don't think I have installed.

Anyway, after unmuting stuff, I can now get *analog* sound out the front of the card.  Yay.

So I'm wondering, "What happened"?  Does asoundconf do stuff other than write the .asoundrc file?

How do I enable SPDIF again?  I've seen some unsresolved posts regarding that question.  I see there is an AC3 passthrough instruction someplace here for audigy.  Should that work with my extigy?

Thanks
Michael

---

### Post by sonicsmooth on 2007-10-31
So I followed the instructions here: [http://ubuntuforums.org/showthread.php?p=1269056]("http://ubuntuforums.org/showthread.php?p=1269056")

to no avail.  I tried changing the card number to 1 from 0 but that didn't help.  Yes, I restarted alsa-utils from /etc/init.d.  The metallica I was playing through analog went quiet then came back on.

The only references to any hardware seemed pretty generic, leading me to believe this file is not audigy specific.

Anyway, I did a little probing.  aplay -l gives me this:
```
sonic@Sophos:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 1: Extigy [Sound Blaster Extigy], device 0: USB Audio [USB Audio]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 1: Extigy [Sound Blaster Extigy], device 1: USB Audio [USB Audio #1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Extigy [Sound Blaster Extigy], device 2: USB Audio [USB Audio #2]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

and aplay -L give me this:
```
sonic@Sophos:~$ aplay -L
null
    Discard all samples (playback) or generate zero samples (capture)
front:CARD=Extigy,DEV=0
    Sound Blaster Extigy, USB Audio
    Front speakers
surround40:CARD=Extigy,DEV=0
    Sound Blaster Extigy, USB Audio
    4.0 Surround output to Front and Rear speakers
surround41:CARD=Extigy,DEV=0
    Sound Blaster Extigy, USB Audio
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=Extigy,DEV=0
    Sound Blaster Extigy, USB Audio
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=Extigy,DEV=0
    Sound Blaster Extigy, USB Audio
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=Extigy,DEV=0
    Sound Blaster Extigy, USB Audio
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
iec958:CARD=Extigy,DEV=0
    Sound Blaster Extigy, USB Audio
    IEC958 (S/PDIF) Digital Audio Output
```


How can I use this with my .asoundrc file to get Alsa to do SPDIF out, AC3 pass through, etc.?

Thanks
Michael

---

### Post by friskaddict on 2007-11-22
Hi, I'm having same type of problem. I did a clean install of Gutsy.
I was able to get my Extigy to work in Analog mode, (via setting all sound options in preferences menu to ALSA, after that running 'asoundconf set-default-card Extigy'). Unfortunately, this doesn't make SPDIF available; when i try to enable that in VLC i'm getting nothing good.
Another problem i'm facing is that when i shutdown my pc; Ubuntu automatically mutes anything in the extigy. I connected my Xbox via an optical cable to the Extigy, so i'm not able to use my Xbox if my pc's not running. Also, if i reboot into windows, Windows isn't able to unmute the thing. If i disconnect the Extigy before shutting down Ubuntu the volume stays the same.
Anyone having some idea to fix this, or the SPDIF issue?

---

### Post by Blastomorpha on 2008-04-18
Believe or not, I'm looking for a solution to the "Extigy Problem" for about 2 years... have you ever tried [this]("http://exaudio.sourceforge.net/")?
I tried this about a year ago (on 6.06LST), but I wasn't lucky :(
Maybe now that i moved to 7.10...

---

