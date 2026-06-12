---
title: "Totally lost sound on Ubuntu 16.04"
date: 2018-06-29
forum: Hardware
---

### Post by yancek on 2018-06-29
I totally lost the sound on my HP Notebook which had been working for the past year when I purchased it.  I'm not sure if this is a hardware failure or some other problem but I have 3 Linux systems plus windows 10 and there is no sound on any of them and sound previously worked on all systems.  I haven't changed (deliberately) any sound settings and haven't made any changes that I would expect to have an effect on sound.  The only thing I've done recently which was different from standard use was connecting via HDMI to a TV.  Don't know if that would affect anything.

Currently, I have Ubuntu 16.04 installed

On windows, going into Control Panel, Sound I get a message that no audio devices are installed and the troubleshooter fails to identify the problem.

On Ubuntu, running aplay -l shows no soundcards found.
Running:  pactl stat
Currently in use: 2 blocks containing 125.0 KiB bytes total.
Allocated during whole lifetime: 92 blocks containing 3.4 MiB bytes total.
Sample cache size: 0 B

Not sure what the above means.  The following commands output no such file or directory which looks problematic:

/usr/sbin/lsmod | grep snd
/usr/sbin/fuser -v /dev/snd/pcm* /dev/dsp

The lspci command shows the below output

lspci -v | grep -A7 -i "audio"  
Shows info including:
Capabilities: <access denied> (this shows run as user, not with sudo)
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd_hda_intel
    
Running the alsa script also showed no sound cards found.
Running pulseaudio -k just goes back to the prompt with no output.

If anyone has any suggestions on further information I could post from specific commands I can do that.  Any other suggestions toward a possible solution would be appreciated.  Since sound fails on 4 different systems, I tend to think it is hardware or some unknown manual action with Action keys I might have used accidentally to turn off sound but I dont see anything in the BIOS or any keys that would do this.

---

### Post by Unkraut on 2018-07-08
> **yancek said:**
> I totally lost the sound on my HP Notebook which had been working for the past year when I purchased it.  I'm not sure if this is a hardware failure or some other problem but I have 3 Linux systems plus windows 10 and there is no sound on any of them and sound previously worked on all systems.

Just on a hunch: I had a similarly mysterious problem of that sort just now. After trying all sorts of Voodoo I finally fiddled with my BIOS settings. Turned out I just had to switch some setting for the sound card in BIOS from "{{don't remember}}" to "AC97".

No clue why I had to change that setting now suddenly. I had not changed it ever before and it was just a last desparate act to try and change what I could in the BIOS. But it got my sound back working as it did before.

---

