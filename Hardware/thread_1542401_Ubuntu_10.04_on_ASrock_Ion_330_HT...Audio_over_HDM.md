---
title: "Ubuntu 10.04 on ASrock Ion 330 HT...Audio over HDMI issue..."
date: 2010-07-30
forum: Hardware
---

### Post by gballard on 2010-07-30
Apparently I just cannot figure out what to search for this problem I am having.  I have Ubuntu 10.04 64-bit installed on my ASrock ION 330 HT box and I cannot figure how to enable Audio over HDMI on it...would one of you kind souls please point me to any documentation on this please?  Even my normally strong Google-fu is failing me on this.

---

### Post by jouzts on 2010-07-31
Have you tried the instructions in: 
[http://ptspts.blogspot.com/2009/08/asrock-ion-330-nettop-with-jaunty.html](http://ptspts.blogspot.com/2009/08/asrock-ion-330-nettop-with-jaunty.html)

I am also trying the Toslink s/pdif out.

John

---

### Post by gballard on 2010-07-31
This looks promising....thanks....will let ya know how it goes.

---

### Post by jouzts on 2010-07-31
I succeeded in getting S/PDIF optical working with:

mplayer -ao alsa:device=iec958=NVidia [http://www.wdav.org/streams/WDAV-128k.m3u](http://www.wdav.org/streams/WDAV-128k.m3u)

(That's all on one line, of course.)

I did not disable pulseaudio, which hopefully is better behaved these days. I am running Kubuntu lucid. 

Are you using mythtv as an input?

John

---

### Post by gballard on 2010-07-31
Just trying to get the HDMI audio working in plain ole Ubuntu 10.04 64 bit...I may add XBMC to it as well.

---

### Post by wedsxcrfv on 2010-07-31
Hi guys,
I'm having the same problem after installing Lucid, I had to reinstall because I messed something up, but before I had Lucid as well WITH HDMI SOUND WORKING
The problem being, I have no idea how I got it working...
On my previous setup I had the latest proprietary nVidia drivers (I think they were neccesary), and I removed Pulseaudio but I am not sure if that is necesary, as it started working after I used something from some site that I completely forgot that caused ALSA (I think) to find the soundcard and use it (It was something like that, but I completely don't remember where I found it :( )
So, I will follow this topic closely and help if I can, because I am in the same boat as you guys :( lets get this working!

---

### Post by gballard on 2010-07-31
ok...doing aplay -L gives this...

ben@bedroom:~$ aplay -L
pulse
    Playback/recording through the PulseAudio sound server
front:CARD=NVidia,DEV=0
    HDA NVidia, ALC889A Analog
    Front speakers
surround40:CARD=NVidia,DEV=0
    HDA NVidia, ALC889A Analog
    4.0 Surround output to Front and Rear speakers
surround41:CARD=NVidia,DEV=0
    HDA NVidia, ALC889A Analog
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=NVidia,DEV=0
    HDA NVidia, ALC889A Analog
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=NVidia,DEV=0
    HDA NVidia, ALC889A Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=NVidia,DEV=0
    HDA NVidia, ALC889A Analog
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
iec958:CARD=NVidia,DEV=0
    HDA NVidia, ALC889A Digital
    IEC958 (S/PDIF) Digital Audio Output
hdmi:CARD=NVidia,DEV=0
    HDA NVidia, NVIDIA HDMI
    HDMI Audio Output

Will creating a .asoundrc with the following make audio over HDMI work?

defaults.pcm.!card NVidia
defaults.ctl.!card NVidia
defaults.pcm.!device 0
defaults.ctl.!device 0

---

### Post by wedsxcrfv on 2010-07-31
Ok, this is worth a read: [http://alsa.opensrc.org/.asoundrc](http://alsa.opensrc.org/.asoundrc)
Also, I think updating Alsa to the latest and greatest might help, see these instructions: [http://ubuntuforums.org/showthread.php?p=6589810#post6589810](http://ubuntuforums.org/showthread.php?p=6589810#post6589810)
Ill update and try an .asoundrc config file to see if it works then...

---

### Post by jouzts on 2010-07-31
I have a non-ASRock machine that is running the maverick alpha. Recently I lost sound on mythfrontend, but it has mysteriously returned, although I have now lost sound on mplayer but not on vlc. In this case, the kubuntu 64bit install spontaneously found the coax s/pdif output on an RME card. Although I tried several "fixes" to get sound back for mythfrontend, none seemed to work. 

This has the effect of making me a little paranoid about messing around with the sound on the fully working ASRock box right now, so sadly I still have mythtv pointed at the analog output until I get another stable machine as a backup. 

John

---

### Post by jouzts on 2010-07-31
gballard,

I am not sure. aplay -l (note little L) gives me 3 devices:
0: analog
1: s/pdif
3: hdmi

If you want to keep your HDMI output, I think the device number has to be 3, since 0 is analog.

John

---

### Post by gballard on 2010-07-31
ahh...the blog referenced earlier in the thread says to run aplay -L....when I ran -l I see what you are talking about about the device numbers....thanks.


ben@bedroom:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC889A Analog [ALC889A Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: ALC889A Digital [ALC889A Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 3: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

Does pulseaudio need to be killed for this to work properly?

---

### Post by gballard on 2010-07-31
OK...I upgraded Alsa and still no go on HDMI Audio...:(

---

### Post by lidex on 2010-07-31
[http://alsa.opensrc.org/DigitalOut](http://alsa.opensrc.org/DigitalOut)
[http://ubuntuforums.org/showthread.php?t=1466111](http://ubuntuforums.org/showthread.php?t=1466111)
[http://wiki.xbmc.org/index.php?title=HOW-TO_set_up_HDMI_audio_on_nVidia_GeForce_G210,_GT220,_or_GT240](http://wiki.xbmc.org/index.php?title=HOW-TO_set_up_HDMI_audio_on_nVidia_GeForce_G210,_GT220,_or_GT240)
[http://forum.xbmc.org/showthread.php?t=59877](http://forum.xbmc.org/showthread.php?t=59877)
[http://ubuntuforums.org/showthread.php?t=1532355](http://ubuntuforums.org/showthread.php?t=1532355)

---

### Post by jouzts on 2010-08-01
gballard,

What does this give you:

mplayer -ao alsa:device=hdmi=NVidia [http://www.wdav.org/streams/WDAV-128k.m3u](http://www.wdav.org/streams/WDAV-128k.m3u)

The optical s/pdif equivalent works for me. The biggest problem I had was figuring out which optical input connected to which input setting on my Panasonic receiver. With both video and audio on the same input, it should be easier to setup, although my streaming example is probably audio only. Just substitute a video file or source.

John

---

### Post by wedsxcrfv on 2010-08-01
Guess what, I got half-baked sound :)
I removed pulseaudio, used the proprietary NVidia drivers, put this in my .asoundrc:
[HTML]pcm.!default {
        type hw
        card 0
        device 3
}
[/HTML]
And set the XBMC sound settings to default, HDMI and I got sound!
But it is not, however system-wide yet

EDIT:
OK, it is system wide! Just add above to your .asoundrc and it should work

---

### Post by miki4242 on 2010-08-10
No need to ditch Pulseaudio!

Here's my setup: Asrock ION 330HT-BD (assume it works with 330HT also) connected to Sony KDL-32V4220 HD-Ready TV via HDMI only.
(Note: I've read somewhere that some chipsets require that a video signal be sent along with audio for HDMI audio to work, so test with a TV or monitor first!)

This is what I did, assuming you have the GNOME desktop (*some texts translated from Dutch):

- Click speaker on top menubar, select "Sound Preferences"*
- Click tab "Hardware"
- Select profile "HDMI Output" from the list

This should change default audio device to HDMI, but I had no sound from the TV yet.

So I did the following:
- Open a terminal window and run:
```
alsamixer
```
- Then, using the right cursor key, navigate all the way to the right to the setting "S/PDIF 1"
- Unmute this by hitting the M key
- Exit alsamixer by hitting the Escape key

That's it, immediately after hitting M, sound came from the TV!

Now, to make this stick across system reboots...
Do the following:

- Still in the terminal window, run:
```
sudo alsactl store
```

That's it!

---

### Post by miki4242 on 2010-08-10
Another note: the setting "S/PDIF 1" is horribly misnamed, and may be the cause of many people not finding a solution on their own or using HOWTO's and such.

When you check what setting actually changes using `amixer contents`, you will notice that the changed setting is actually called "IEC958 Playback Switch". Go figure...
Not much improvement some would say, but at least some HOWTOs will point you to changing this very setting to get any digital output working at all.

After all this, I can only conclude that the problem with getting HDMI audio to work really is with the profile setting in Sound Preferences.
A profile is supposed to be a convenient collection of settings to perform a task (as is well-known in video transcoding). So the "HDMI Output" profile is simply missing an important setting.

I agree with jouzts post #4: nuking Pulseaudio as the first step for every sound problem isn't going to make things better, Pulseaudio is here to stay. Finding the root cause of the problem and fixing that is much better.

---

### Post by wedsxcrfv on 2010-08-11
> **miki4242 said:**
> No need to ditch Pulseaudio!

Here's my setup: Asrock ION 330HT-BD (assume it works with 330HT also) connected to Sony KDL-32V4220 HD-Ready TV via HDMI only.
(Note: I've read somewhere that some chipsets require that a video signal be sent along with audio for HDMI audio to work, so test with a TV or monitor first!)

This is what I did, assuming you have the GNOME desktop (*some texts translated from Dutch):

- Click speaker on top menubar, select "Sound Preferences"*
- Click tab "Hardware"
- Select profile "HDMI Output" from the list

This should change default audio device to HDMI, but I had no sound from the TV yet.

So I did the following:
- Open a terminal window and run:
```
alsamixer
```
- Then, using the right cursor key, navigate all the way to the right to the setting "S/PDIF 1"
- Unmute this by hitting the M key
- Exit alsamixer by hitting the Escape key

That's it, immediately after hitting M, sound came from the TV!

Now, to make this stick across system reboots...
Do the following:

- Still in the terminal window, run:
```
sudo alsactl store
```

That's it!

OK, this is totally weird awesome
I tested some more, and found out I could only play files with a Sample rate of 48Khz
This has probably something to do with my TV totally sucking, but after I changed my .asoundrc to 
```
pcm.!default {
        type hw
        card 0
        device 3
        rate 48000
}
```
It worked!
So, I looked at Pulseaudio, and found out that the Sample Rate is 44100 Hz by default.
Then I edited /etc/pulse/daemon.conf and set default-sample-rate = 48000 ... and everything worked perfectly
So thanks for making me try Pulse again, and this might help someone :)

---

### Post by miki4242 on 2010-08-11
@wedsxcrfv: why do you need to use an .asoundrc at all? Won't this complicate things when you add new soundcards (e.g. USB headsets and such)? The beauty (if I may call it that) of Pulseaudio is that it should handle dynamic reconfiguration of your audio hardware (it gets udev events for this).

Also, in my (unmodified) /etc/pulse/daemon.conf the default-sample-rate line is commented out, so I think that unless you uncomment it, Pulseaudio will use whatever default it finds is best.

According to this [article]("http://www.audioholics.com/education/display-formats-technology/hdmi-interface-a-beginners-guide"), HDMI is supposed to use some kind of "link intelligence" to negotiate playback format capabilities between devices, so isn't ALSA/Pulseaudio supposed to pick these up?

As far as I can recall testing this, I had no problems playing audio with different sample rates, even mixing players like YouTube (flashplayer), Totem, MPlayer, Audacious, Rhythmbox, aplay all playing at once (helluva cacophony I can tell you!) with no problems whatsoever. Pulseaudio, not ALSA, is supposed to do the sample rate conversion and final mixdown, and at least in my case it seems to be doing so just fine..

---

### Post by wedsxcrfv on 2010-08-11
> **miki4242 said:**
> @wedsxcrfv: why do you need to use an .asoundrc at all? Won't this complicate things when you add new soundcards (e.g. USB headsets and such)? The beauty (if I may call it that) of Pulseaudio is that it should handle dynamic reconfiguration of your audio hardware (it gets udev events for this).

Also, in my (unmodified) /etc/pulse/daemon.conf the default-sample-rate line is commented out, so I think that unless you uncomment it, Pulseaudio will use whatever default it finds is best.

According to this [article]("http://www.audioholics.com/education/display-formats-technology/hdmi-interface-a-beginners-guide"), HDMI is supposed to use some kind of "link intelligence" to negotiate playback format capabilities between devices, so isn't ALSA/Pulseaudio supposed to pick these up?

As far as I can recall testing this, I had no problems playing audio with different sample rates, even mixing players like YouTube (flashplayer), Totem, MPlayer, Audacious, Rhythmbox, aplay all playing at once (helluva cacophony I can tell you!) with no problems whatsoever. Pulseaudio, not ALSA, is supposed to do the sample rate conversion and final mixdown, and at least in my case it seems to be doing so just fine..
Ofcourse I uncommented the line :)
What I think is that my television (where it is connected to) does not accept any other sample rate than 48Khz (it is a cheap brand) so after changing that setting it did work...
I know it is totally weird but thats just the truth :)
Also, all my apps now work with sound (I am gonna test multiple at the same time later) except for Flashplayer! I can only play a few flash videos on youtube but not all of them, and games do not have sound. Got any tips on that?

---

### Post by lidex on 2010-08-11
> **wedsxcrfv said:**
> and games do not have sound. Got any tips on that?

See this section 'No sound or stuttering sound in SDL-based games' of this page:
[https://wiki.ubuntu.com/DebuggingSoundProblems/KarmicCaveats](https://wiki.ubuntu.com/DebuggingSoundProblems/KarmicCaveats)

---

### Post by miki4242 on 2010-08-11
> **wedsxcrfv said:**
> Ofcourse I uncommented the line :)
What I think is that my television (where it is connected to) does not accept any other sample rate than 48Khz (it is a cheap brand) so after changing that setting it did work...
Ok, I see. I'm glad you found the .asoundrc and Pulseaudio settings that do work with your TV. The good news is that the ALSA people know about the problem ([link]("http://www.spinics.net/lists/alsa-devel/msg36270.html")), the bad news is that there is no fix yet to set things right automatically.

Now, Flashplayer problems are often a whole different ballgame, with entirely different issues.
Does your Flashplayer work OK with plain ALSA and analog audio? Does it work with Pulseaudio (analog or digital) at all?
If it works OK with plain ALSA but not with Pulseaudio, you might try deleting the .pulse directory in your home directory, then logging out and back in (it will be recreated with defaults).
I've noticed that Pulseaudio can get confused if you change lots of settings like redirecting the output for individual applications, then change your soundcard setup (like adding then removing USB headsets and such.)

Also, which version of Ubuntu, 32bit or 64bit, and which version of Flashplayer are you using? There are known issues with Flashplayer on 64bit systems, which may not get fixed anytime soon sadly, as Adobe has put development of the 64bit version on hold indefinitely ([link]("http://www.bit-tech.net/news/bits/2010/06/16/adobe-kills-64-bit-flash-player/1")).

Please tell me more about it, I'll try to help.

---

### Post by wedsxcrfv on 2010-08-12
> **miki4242 said:**
> Ok, I see. I'm glad you found the .asoundrc and Pulseaudio settings that do work with your TV. The good news is that the ALSA people know about the problem ([link]("http://www.spinics.net/lists/alsa-devel/msg36270.html")), the bad news is that there is no fix yet to set things right automatically.

Now, Flashplayer problems are often a whole different ballgame, with entirely different issues.
Does your Flashplayer work OK with plain ALSA and analog audio? Does it work with Pulseaudio (analog or digital) at all?
If it works OK with plain ALSA but not with Pulseaudio, you might try deleting the .pulse directory in your home directory, then logging out and back in (it will be recreated with defaults).
I've noticed that Pulseaudio can get confused if you change lots of settings like redirecting the output for individual applications, then change your soundcard setup (like adding then removing USB headsets and such.)

Also, which version of Ubuntu, 32bit or 64bit, and which version of Flashplayer are you using? There are known issues with Flashplayer on 64bit systems, which may not get fixed anytime soon sadly, as Adobe has put development of the 64bit version on hold indefinitely ([link]("http://www.bit-tech.net/news/bits/2010/06/16/adobe-kills-64-bit-flash-player/1")).

Please tell me more about it, I'll try to help.
I am running Ubuntu 10.04 32-bit on an AsRock ION 330
It is connected to my television using a HDMI cable.
I only use the audio over HDMI, no other soundcards.
About what works and what not, I will post again sometime today :)
I can now only tell you that this video did have audio for me: [http://www.youtube.com/watch?v=OfH38VrecH8](http://www.youtube.com/watch?v=OfH38VrecH8)
While I could not find another video that also had video and flash games on kongregate did not gave sound either.
I think I might also try put the " rate 48000 " in my .asoundrc file to try if that might help, but first I'll try your tip with deleting the .pulse directory.
Thanks for helping me out on this!

---

### Post by 88fingerslukee on 2010-08-23
Can anybody help me out with this as well?  I've tried all of these suggestions and nothing works.  I have an ASrock ION 330 HT and Windows 7 had everything working just fine.  I have never had sound in any flavour of Linux.  I've run Ubuntu 10.04 and 9.10 as well as Fedora 13 without success.

I have updated Nvidia drivers to the latest, ran the ALSA upgrade scripts, changed my asound.conf file (AND  .asoundrc file for that matter), daemon.conf file, defaults.pa file, alsa-base.conf file and whatever else I can get my greedy, text-editing paws on in vain attempts to subdue the audio d(a)emons.

Somebody please offer some guidance, but I fear I've done all there is to do.  What am I doing wrong?

---

### Post by jouzts on 2010-08-24
88,

I don't remember any difficulty get analog sound out of the green mini-phone jack on the back of any ASRock Ion 330, HT or not, with every Linux Live CD I tried. 

Getting spdif or hdmi sound is more complicated. 

Do you have analog sound?

John

---

### Post by 88fingerslukee on 2010-08-25
> **jouzts said:**
> 
Do you have analog sound?

John


Thanks for replying John.  I do have analog sound.  I've followed the instructions all over the place and can't get it to work.

Alsamixer has all channels unmuted.

I cannot get anything more than 2 channels however, even with 5.1 plugged into my receiver.

---

### Post by jouzts on 2010-08-25
88,

First I would double check that the digital audio outputs are turned on in the bios. 

Then, if it is not too much trouble, I would do a fresh install.

And finally, I would start testing with a command like:

mplayer -ao alsa:device=hdmi=NVidia [http://www.wdav.org/streams/WDAV-128k.m3u](http://www.wdav.org/streams/WDAV-128k.m3u)

without changing any other settings first. The optical s/pdif alternative may be subject to fewer modes of failure than hdmi, if you have trouble getting hdmi to work. 

Frankly, I had very little trouble getting this to work, although I had the machine running in analog for quite a while before I started trying, so I could have made other changes that I don't remember. Once you have either s/pdif or hdmi working in digital stereo, it is easy to set Mythtv or whatever source to 5.1 output. 

Good luck!

John

---

### Post by 88fingerslukee on 2010-08-26
> **jouzts said:**
> 88,

First I would double check that the digital audio outputs are turned on in the bios. 

Then, if it is not too much trouble, I would do a fresh install.

And finally, I would start testing with a command like:

mplayer -ao alsa:device=hdmi=NVidia [http://www.wdav.org/streams/WDAV-128k.m3u](http://www.wdav.org/streams/WDAV-128k.m3u)

without changing any other settings first. The optical s/pdif alternative may be subject to fewer modes of failure than hdmi, if you have trouble getting hdmi to work. 

Frankly, I had very little trouble getting this to work, although I had the machine running in analog for quite a while before I started trying, so I could have made other changes that I don't remember. Once you have either s/pdif or hdmi working in digital stereo, it is easy to set Mythtv or whatever source to 5.1 output. 

Good luck!

John

John,

I've done several fresh installs already with the same results.  Since you have this working, would you please do me a favour and paste your asound.conf (or .asoundrc) or both as well as anything relating to nvidia or snd-hda-intel in your /etc/modprobe.d/alsa-base.conf file?

the mplayer command runs but predictable plays no sound.  This seems to be a driver initialization issue because only 2.0 audio works.

---

### Post by Pwyll123 on 2010-08-28
I had the same issue with a home made HTPC based on a asus AT3ION, which has the same Nvidia chipset than the ASRock. I tryed many things without success. Could not get any HDMI sound output.

The I simply did a```
speaker-test
``` command in a terminal. I heard a small background sound in my TV speakers, and then the Speaker Test succeded to output the R+L channels sounds of my TV through HDMI.

When back into Ubuntu, played a music with RythmBox with success, then started XBMC and got my HDMI sound output ....

Seems like the ```
speaker-test
``` actually initialsed the sound output ?

---

### Post by jouzts on 2010-08-28
I did a "find / -name " for both .asoundrc and asound.conf and came up with nothing. Here is the entire alsa-base.conf file:

> # autoloader aliases
install sound-slot-0 /sbin/modprobe snd-card-0
install sound-slot-1 /sbin/modprobe snd-card-1
install sound-slot-2 /sbin/modprobe snd-card-2
install sound-slot-3 /sbin/modprobe snd-card-3
install sound-slot-4 /sbin/modprobe snd-card-4
install sound-slot-5 /sbin/modprobe snd-card-5
install sound-slot-6 /sbin/modprobe snd-card-6
install sound-slot-7 /sbin/modprobe snd-card-7

# Cause optional modules to be loaded above generic modules
install snd /sbin/modprobe --ignore-install snd $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-ioctl32 ; /sbin/modprobe --quiet --use-blacklist snd-seq ; }
#
# Workaround at bug #499695 (reverted in Ubuntu see LP #319505)
install snd-pcm /sbin/modprobe --ignore-install snd-pcm $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-pcm-oss ; : ; }
install snd-mixer /sbin/modprobe --ignore-install snd-mixer $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-mixer-oss ; : ; }
install snd-seq /sbin/modprobe --ignore-install snd-seq $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; /sbin/modprobe --quiet --use-blacklist snd-seq-oss ; : ; }
#
install snd-rawmidi /sbin/modprobe --ignore-install snd-rawmidi $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; : ; }
# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-emu10k1-synth ; }
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq ; }

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist saa7134-alsa ; : ; }
# Prevent abnormal drivers from grabbing index 0
options bt87x index=-2
options cx88_alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-us122l index=-2
options snd-usb-usx2y index=-2
options snd-usb-caiaq index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
# Keep snd-pcsp from being loaded as first soundcard
options snd-pcsp index=-2

It has been a while since I did the original install, but I don't remember doing anything special. Keep in mind that what I set up in the course of this thread is the optical s/pdif with 5.1 surround, since my hdmi cable is going in a different direction to monitor/projector without audio capabilities. 

John

---

### Post by 88fingerslukee on 2010-08-28
> **Pwyll123 said:**
> Seems like the ```
speaker-test
``` actually initialsed the sound output ?

> **jouzts said:**
> I did a "find / -name " for both .asoundrc and asound.conf and came up with nothing. Here is the entire alsa-base.conf file:

It has been a while since I did the original install, but I don't remember doing anything special. Keep in mind that what I set up in the course of this thread is the optical s/pdif with 5.1 surround, since my hdmi cable is going in a different direction to monitor/projector without audio capabilities. 

John


Thanks for the suggestions guys, but something REALLY weird is going on here.

As I've mentioned, analog works but only in 2.0 even when I have all the jacks plugged into my receiver (I can receive 5.1 by this method normally).  Because John said he had optical working I gave that a go and it sorta works.  When I run speaker-test on the optical port with more than 2.0 it starts playing those extra channels in the Front L and R speakers.  It's also 2.0!

So that's two of three outputs that are only half working.  This really seems to be a driver problem but I've tried all the drivers.  My alsa-base.conf file matches John's exactly as well (diff command turns up nothing).

Thoughts on the state of my output?

---

### Post by 88fingerslukee on 2010-08-30
Just to update this, I did a fresh install of Kubuntu 10.04 just to see if PulseAudio was this issue.  This is not the case.  I ran the Alsa upgrade script and enabled all SPDIF devices.  No dice.

Analog is still 2.0 only and HDMI is silent.  I'm depressed.  If I hadn't seen and heard with my own head-holes the thing working with Windows 7 I would have RMA'd this thing a long time ago.  The fact is, the port works and nothing that has been previously done is helping.  I'm stumped.  

What BIOS versions are people running?

---

### Post by jouzts on 2010-09-01
My bios is v02.64.

After I managed to get s/pdif output in stereo, correctly setting up mythtv for surround sound was all I did to get multichannel working. I vaguely recollect allowing HDMI and s/pdif in the BIOS settings, though.

John

---

### Post by 88fingerslukee on 2010-09-01
> **jouzts said:**
> My bios is v02.64.

After I managed to get s/pdif output in stereo, correctly setting up mythtv for surround sound was all I did to get multichannel working. I vaguely recollect allowing HDMI and s/pdif in the BIOS settings, though.

John


2.64?  Do you have an ASRock Ion 330 HT?  you might be looking at the wrong number...see here:

[http://www.avforums.com/forums/home-entertainment-pcs/1024281-asrock-ion-330-a-9.html](http://www.avforums.com/forums/home-entertainment-pcs/1024281-asrock-ion-330-a-9.html)

---

### Post by rugbyman on 2010-09-06
> **miki4242 said:**
> Another note: the setting "S/PDIF 1" is horribly misnamed, and may be the cause of many people not finding a solution on their own or using HOWTO's and such.

When you check what setting actually changes using `amixer contents`, you will notice that the changed setting is actually called "IEC958 Playback Switch". Go figure...
Not much improvement some would say, but at least some HOWTOs will point you to changing this very setting to get any digital output working at all.

After all this, I can only conclude that the problem with getting HDMI audio to work really is with the profile setting in Sound Preferences.
A profile is supposed to be a convenient collection of settings to perform a task (as is well-known in video transcoding). So the "HDMI Output" profile is simply missing an important setting.

I agree with jouzts post #4: nuking Pulseaudio as the first step for every sound problem isn't going to make things better, Pulseaudio is here to stay. Finding the root cause of the problem and fixing that is much better.
_[U]_[/U]Miki4242 - thanks, that was it - had to unmute the SPDIF in alsamixer to get sound! It *is* horribly named. 

I've been through several iterations of installs and about a thousand forum posts, but I've finally got sound.

Not sure if it would have worked with earlier versions of alsa or NVIDIA drivers, but here's what I've got now and I'm not touching anything :-)

Acer Revo 3610 w/ION
Kubuntu 10.04 32bit
NVIDIA 256.44 drivers
Alsa 1.0.23 installed from backports
XBMC

---

### Post by 88fingerslukee on 2010-09-08
> **rugbyman said:**
> Miki4242 - thanks, that was it - had to unmute the SPDIF in alsamixer to get sound! It *is* horribly named. 

I've been through several iterations of installs and about a thousand forum posts, but I've finally got sound.

Not sure if it would have worked with earlier versions of alsa or NVIDIA drivers, but here's what I've got now and I'm not touching anything :-)

Acer Revo 3610 w/ION
Kubuntu 10.04 32bit
NVIDIA 256.44 drivers
Alsa 1.0.23 installed from backports
XBMC


This simply doesn't work for me.  The most frustrating thing in the world.

---

### Post by perevera on 2010-10-30
Thanks, miki4242, your recipe solved the issue in my ASRock ION 300HT!

I had been struggling with it since I purchased the box, several months ago (I installed Karmic Koala in the beginning).

Now I just upgraded to Lucid Lynx (for no special reason, everything was working ok for me, MythTV, Spotify, XBMC... except sound through HDMI), and decided to browse the web for solutions again, so I am happy I discovered this link.

A question arise, though...

Since I was using analog stereo output to feed my Hi-Fi system (which is really cool for Spotify or Amarock, but less fancy for MythTV or XBMC), now I face the problem: or I use sound through HDMI or through Analog Stereo, but not both at a time (I don't see any profile that uses both in Sound Preferences).

I guess this is possible to configure a program or another to use an ALSA profile or another though...

If yes, please give me some hint.

Thanks again.

---

### Post by kaegee on 2010-11-16
> **88fingerslukee said:**
> This simply doesn't work for me. The most frustrating thing in the world.
 
88, you're not alone. I have the ASRock ION 330HT-BD linked to a Panasonic TV via HDMI. After following pretty much every link on this forum and others, all I managed to do was to reduce my screen size when updating the nVidia drivers and could not get the screen to fit the television anymore.
 
I am a complete noob when it comes to Linux so I eventually got fed up and installed Windows Vista. No HDMI sound (and, interestingly, no change in screen size).
 
I then installed Windows 7 and guess what, full screen TV with, more importantly, HDMI sound.
 
I can only guess it is a driver issue.
 
Does anyone have any further ideas?
 
One further bit of info: when I navigate to SPDIF1 using alsamixer, all it allows me to do is to mute/unmute the channel but there is no option to increase the sound from "00". Could that be the problem?
 
Thanks in advance.

---

### Post by sydbat on 2010-11-18
> **kaegee said:**
> I can only guess it is a driver issue.
 
Does anyone have any further ideas?
 
One further bit of info: when I navigate to SPDIF1 using alsamixer, all it allows me to do is to mute/unmute the channel but there is no option to increase the sound from "00". Could that be the problem?
 
Thanks in advance.I have the same problem, except with my desktop. Is there any way of increasing the volume on S/PDIF 1??

---

