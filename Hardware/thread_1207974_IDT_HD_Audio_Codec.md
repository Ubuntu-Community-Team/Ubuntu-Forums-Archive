---
title: "IDT HD Audio Codec"
date: 2009-07-08
forum: Hardware
---

### Post by Sim-I-Am :} on 2009-07-08
Hey, I'm relatively new to UbuntuForums, and Ubuntu for that matter (but lovin it!). I just installed Jaunty on my second machine (Gateway P-6860FX Laptop), and I just have a few questions.
First of all, I have IDT HD Audio speakers on my lappy, and I can't seem to get them to work, or find any Linux drivers for them either. Does anyone else have any experience with this?
Also, what's a good audio converter for Linux?
And lastly, is there any way to enable AA on compiz animations? (dragging and desktop wall, for example)

Thanks,
    Sim-I-Am

---

### Post by jenkinbr on 2009-07-08
[size=4]Sound Problem[/size]

You might also want to try this:
[list=1]
[*]Open gnome-sound-proporties (System => Prefs => Sound)
[*]Set everything to autodetect and set Default mixer track to your IDT card and choose the appropriate option below the device setting
[*]Try playing sound - no luck, continue on.

.

[*]Click the Volume Control Icon on the Notification area (sys tray)
[*]Click Volume Control Button
[*]Check the PCM volume setting - make sure it is unmuted and set to a decent level. Also make sure other appropriate settings are unmuted and at appropriate levels.
[*]Try playing sound again - Still no luck, continue.

.

[*]With the Volume control still open, click 'Preferences'.
[*]Locate the option called 'External Amplifier (Switches)" and enable it.
[*]Close the preferences and click the 'Switches' tab in gnome-volume-control
[*]Ensure that External Amplifier is UNchecked - for some reason, this happens sometime.
[*]Play some sound - Still no luck? Contine.

.

[*]Post the output of the commands ```
aplay -l
``````
lshw -C multimedia
```
[/list]

[size=4]Audio Converter[/size]
I have had good luck with ffmpeg using a winff frontend. I use the medibuntu version, which seems to work better.

[size=4]Compiz[/size]

What do you mean by AA?

---

### Post by Sim-I-Am :} on 2009-07-09
Ok, nothing worked and there was no option for "External Amplifier (Switches)". So, here's my results:

1.
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: STAC92xx Digital [STAC92xx Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

2.
  *-multimedia            
       description: Audio device
       product: 82801H (ICH8 Family) HD Audio Controller
       vendor: Intel Corporation
       physical id: 1b
       bus info: pci@0000:00:1b.0
       version: 03
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=HDA Intel latency=0 module=snd_hda_intel

---

### Post by jenkinbr on 2009-07-09
You may need to try configuring PulseAudio correctly.

psyke83 set up a very nice guide over at [HOWTO: PulseAudio Fixes & System-Wide Equalizer Support ](http://ubuntuforums.org/showthread.php?t=789578) That may help out a bit.

Not sure why you don't have the external amplifier option in gnome-volume-control, though - I think it should be there regardless of hardware capabilities - half the stuff on that list has nothing to do with my hardware.

---

### Post by Yellow Pasque on 2009-07-09
Are they USB speakers or something? I wasn't aware you needed drivers for speakers.

As for AA (anti-aliasing), I know nvidia cards can do it. Wat kind of video do you have?

---

### Post by jenkinbr on 2009-07-09
> **Temüjin said:**
> Are they USB speakers or something? I wasn't aware you needed drivers for speakers.

As for AA (anti-aliasing), I know nvidia cards can do it. Wat kind of video do you have?
The speakers are the laptop built-in.

I know he has an nVidia card, I think its an 8600, but I'm not sure.

(no, I'm not psychic or anything - I know this user personally :))

---

### Post by Yellow Pasque on 2009-07-09
[http://forum.foresightlinux.org/index.php?topic=381.0](http://forum.foresightlinux.org/index.php?topic=381.0)

For sound: [http://bbs.archlinux.org/viewtopic.php?pid=565471](http://bbs.archlinux.org/viewtopic.php?pid=565471)

---

### Post by Sim-I-Am :} on 2009-07-11
Ok, I got the sound working! I followed one of the links Temujin posted, and by way of browsing multiple forums, I stumbled upon this: [http://ubuntuforums.org/showthread.php?t=1073090]("http://ubuntuforums.org/showthread.php?t=1073090") Followed the instructions, rebooted, and voila! Sound!

As for the Compiz AA (Anti-Aliasing) question, I haven't found a solution yet. The solutions in the link Temujin posted didn't work for me... Any other ideas?

---

