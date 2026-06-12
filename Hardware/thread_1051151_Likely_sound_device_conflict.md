---
title: "Likely sound device conflict"
date: 2009-01-26
forum: Hardware
---

### Post by jgmsys on 2009-01-26
I'm running an AMD Athlon 64 system with an ASUS A8V Deluxe system board that has a VIA 8237 AC97 sound controller onboard that I've disabled in the BIOS in favor of my SoundBlaster Audigy 2 Value card.  I am trying to understand why Ubuntu sees fit to attempt to configure a device that is disabled in the BIOS, and it is also trying to load the Audigy card, with the result that no sound files get played except in the very beginning when the login screen shows.  Once I've logged in, I can't get sound files played.  

The strange thing about this is that when I force usage of the Audigy card through Preferences/Sound and click the "Test" button, I get a sinewave sound coming through, which suggests that it somehow can see the card, but yet no sound files can be played.

In case anyone needs to see further details, here is the output of sudo lshw -C sound....

[FONT="Fixedsys"]  *-multimedia:0          
       description: Multimedia audio controller
       product: SB0400 Audigy2 Value
       vendor: Creative Labs
       physical id: c
       bus info: pci@0000:00:0c.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: driver=EMU10K1_Audigy latency=64 maxlatency=20 mingnt=2 module=snd_emu10k1
  *-multimedia:1
       description: Multimedia audio controller
       product: VT8233/A/8235/8237 AC97 Audio Controller
       vendor: VIA Technologies, Inc.
       physical id: 11.5
       bus info: pci@0000:00:11.5
       version: 60
       width: 32 bits
       clock: 33MHz
       capabilities: pm cap_list
       configuration: driver=VIA 82xx Audio latency=0 module=snd_via82xx
[/FONT]

Note, when I attempt to remove the module for the onboard sound controller, the system informs me that the operation is not permitted.  So how is one to prevent Ubuntu from recognizing and attempting to load this driver?  Admittedly, I've a few things to learn about the locations of config files in Ubuntu, as they're a little different from what I've been used to in the Fedora environment.

Any assistance anyone can give with this will be appreciated.

---

### Post by kostkon on 2009-01-26
> **jgmsys said:**
> I'm running an AMD Athlon 64 system with an ASUS A8V Deluxe system board that has a VIA 8237 AC97 sound controller onboard that I've disabled in the BIOS in favor of my SoundBlaster Audigy 2 Value card.  I am trying to understand why Ubuntu sees fit to attempt to configure a device that is disabled in the BIOS, and it is also trying to load the Audigy card, with the result that no sound files get played except in the very beginning when the login screen shows.  Once I've logged in, I can't get sound files played.  

The strange thing about this is that when I force usage of the Audigy card through Preferences/Sound and click the "Test" button, I get a sinewave sound coming through, which suggests that it somehow can see the card, but yet no sound files can be played.

In case anyone needs to see further details, here is the output of sudo lshw -C sound....

[FONT="Fixedsys"]  *-multimedia:0          
       description: Multimedia audio controller
       product: SB0400 Audigy2 Value
       vendor: Creative Labs
       physical id: c
       bus info: pci@0000:00:0c.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: driver=EMU10K1_Audigy latency=64 maxlatency=20 mingnt=2 module=snd_emu10k1
  *-multimedia:1
       description: Multimedia audio controller
       product: VT8233/A/8235/8237 AC97 Audio Controller
       vendor: VIA Technologies, Inc.
       physical id: 11.5
       bus info: pci@0000:00:11.5
       version: 60
       width: 32 bits
       clock: 33MHz
       capabilities: pm cap_list
       configuration: driver=VIA 82xx Audio latency=0 module=snd_via82xx
[/FONT]

Note, when I attempt to remove the module for the onboard sound controller, the system informs me that the operation is not permitted.  So how is one to prevent Ubuntu from recognizing and attempting to load this driver?  Admittedly, I've a few things to learn about the locations of config files in Ubuntu, as they're a little different from what I've been used to in the Fedora environment.

Any assistance anyone can give with this will be appreciated.
What version of Ubuntu do you have?

---

### Post by jgmsys on 2009-01-26
8.04

---

### Post by kostkon on 2009-01-26
You don't need to care if Ubuntu continues to see your onboard card or not.

Set your sound playback in your sound preferences to *Autodetect* and then install the *PulseAudio Device Chooser*. Run it (*Applications &#8594; Sound & Video &#8594; PulseAudio Device Chooser*) and it will its icon in your taskbar. Left-click on its icon and select *Volume Control*.

Select the *Output Devices* tab and you should see both of your sound cards listed. Right-click on your Audigy and enable the *Default* option to set it as the default card.

This will work for the applications that work with *PulseAudio* directly (i.e. all of the *Gstreamer* based applications, like *Totem*, *Rhythmbox* and others, if they are setup to use *PulseAudio*, like *VLC* and *Mplayer*).

But, the problem is that in 8.04 *PulseAudio* is not setup by default in the best way, unfortunately. Applications that use *ALSA* don't send their sound through *PulseAudio*.

This is only happening in 8.04. *Ubuntu* 8.10 and newer versions work as expected.

Thus, the above settings will not work for some applications. But in general you should be fine. Applications will use your Audigy.

If some applications continue to use the on-board card, the thing you should try is to open the *PulseAudio* volume control again and select the *Playback* tab. There you should see the audio streams of your applications. Right-click on the application that refuses to use the Audigy and right-click on it and select *Move Stream...* In the list that will appear select your Audigy card. This will make this application to send its sound to this card. *PulseAudio* will remember your choice from now on.

I would recommend you to try to setup *PulseAudio* the right way by following [this very good how-to]("http://ubuntuforums.org/showthread.php?t=789578").

For any questions or problems don't hesitate to ask here.

Hope that helps.

---

### Post by jgmsys on 2009-01-27
That did it. Awesome. Thanks. :)

---

