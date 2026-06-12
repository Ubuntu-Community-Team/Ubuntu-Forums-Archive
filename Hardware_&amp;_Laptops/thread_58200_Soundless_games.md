---
title: "Soundless games"
date: 2005-08-19
forum: Hardware &amp; Laptops
---

### Post by GrootBrak on 2005-08-19
Many of the games does not play with sound. Notably, Tuxracer, Bumprace, Frozen bubble and others.

In Volume control I can select. ALC880 (OSS) or Intel-HDA (Alsa)

In Multimidia system select I can get. ALSA, OSS and ESD.

That gives me 15 possibilities, I still can't get sound working. TuxKart  however play well with sound. Any ideas?

---

### Post by agro1986 on 2005-08-19
Same thing here. In device manager the audio hardware name is "82801BA/BAM AC'97 Audio".

In "multimedia systems selector", for audio default sink I can choose ESD (default), ALSA, Atrsd, and OSS. Pressing the "Test" button for ESD works, but for other choices it gives the error "Failed to construct test pipeline for '[chosen sink]'" (replace [chosen sink] with actual sink name).

Here's what works and don't on my system:
* sytem sounds like drumroll when login works
* Playing divx and wmv movie is OK. mp3 and wma is OK.
* playing quicktime movies don't produce any sound!
* in supertux and frozen-bubble, the option for enabling sound is greyed out (disabled).
* The Battle for Wesnoth don't output any sound

Any suggestions?

Thanks a lot

---

### Post by Toddy on 2005-08-19
Do the following:

sudo apt-get install libsdl1.2debian-all

---

### Post by agro1986 on 2005-08-19
[QUOTE=Toddy]Do the following:

sudo apt-get install libsdl1.2debian-all[/QUOTE]

Thanks for the info. After following your instructions, sound is working on frozen bubble and supertux, bud sadly still no sound for wesnoth and for playing quicktime files. How do I fix it?

Thanks a lot!

---

### Post by agro1986 on 2005-08-19
Some more info which hopefully will help. I tried the games mentioned by GrootBrak.

tuxracer: sound works OK (nice music!)
bumprace: sound works OK
tuxkart: no sound

When I run tuxkart from the console, it outputs various messages to the console. I think the relevant lines are:

slDSP: open: Device or resource busy
WARNING: slScheduler: soundcard init failed.

Any ideas?

---

### Post by Mustard on 2005-08-19
Hmm...cool.  libsdl1.2debian-all worked well for stratagus.  I've finally got some noise happening in the game. :)

---

### Post by gerbman on 2005-08-20
[QUOTE=agro1986]Some more info which hopefully will help. I tried the games mentioned by GrootBrak.

tuxracer: sound works OK (nice music!)
bumprace: sound works OK
tuxkart: no sound

When I run tuxkart from the console, it outputs various messages to the console. I think the relevant lines are:

slDSP: open: Device or resource busy
WARNING: slScheduler: soundcard init failed.

Any ideas?[/QUOTE]

Try disabling Ubuntu's sound server (it might be conflicting with the game's sound). Go to "System", "Preferences", "Sound Preferences", and uncheck "Enable sound server startup".

It's kind of a pain to have to do it any time you play a game, but I'm not sure of a better solution.

---

### Post by agro1986 on 2005-08-20
[QUOTE=gerbman]Try disabling Ubuntu's sound server (it might be conflicting with the game's sound). Go to "System", "Preferences", "Sound Preferences", and uncheck "Enable sound server startup".

It's kind of a pain to have to do it any time you play a game, but I'm not sure of a better solution.[/QUOTE]
 Cool, now tuxkart has sound! However still no quicktime and wesnoth sound. Here's the console ouput of wesnoth:
```

Battle for Wesnoth v0.9.3
Started on Sat Aug 20 15:44:16 2005

started game: 3540992485
open /dev/sequencer: No such file or directory
Checking video mode: 1024x768x16...
32
setting mode to 1024x768x32
found valid cache at '/home/budi/.wesnoth/cache/game.cfg-cache-v0.9.3-MEDIUM-NORMAL' using it
started music
753976018
showing title screen...
753976023
Loading tips of day
title screen returned result
no valid cache found. Writing cache to '/home/budi/.wesnoth/cache/game.cfg-cache-v0.9.3-CAMPAIGN_EASTERN_INVASION-MEDIUM-NORMAL'
error display: could not open image ''
escape pressed..showing quit
found valid cache at '/home/budi/.wesnoth/cache/game.cfg-cache-v0.9.3-MEDIUM-NORMAL' using it
started music
754013506
showing title screen...
754013510
Loading tips of day
title screen returned result
quitting game...
closing audio...
final closing audio...
done closing audio...
exiting with code 0

```

I think the relevant line is

```
open /dev/sequencer: No such file or directory
```

Any more ideas :)?

Thanks a lot

---

### Post by gerbman on 2005-08-20
[QUOTE=agro1986]Cool, now tuxkart has sound! However still no quicktime and wesnoth sound. Here's the console ouput of wesnoth:
```

Battle for Wesnoth v0.9.3
Started on Sat Aug 20 15:44:16 2005

started game: 3540992485
open /dev/sequencer: No such file or directory
Checking video mode: 1024x768x16...
32
setting mode to 1024x768x32
found valid cache at '/home/budi/.wesnoth/cache/game.cfg-cache-v0.9.3-MEDIUM-NORMAL' using it
started music
753976018
showing title screen...
753976023
Loading tips of day
title screen returned result
no valid cache found. Writing cache to '/home/budi/.wesnoth/cache/game.cfg-cache-v0.9.3-CAMPAIGN_EASTERN_INVASION-MEDIUM-NORMAL'
error display: could not open image ''
escape pressed..showing quit
found valid cache at '/home/budi/.wesnoth/cache/game.cfg-cache-v0.9.3-MEDIUM-NORMAL' using it
started music
754013506
showing title screen...
754013510
Loading tips of day
title screen returned result
quitting game...
closing audio...
final closing audio...
done closing audio...
exiting with code 0

```

I think the relevant line is

```
open /dev/sequencer: No such file or directory
```

Any more ideas :)?

Thanks a lot[/QUOTE]

The /dev/sequencer device is missing.  [This](http://lists.freebsd.org/pipermail/freebsd-questions/2003-November/024518.html) post sounds like it's on the right track, and 'man MAKEDEV' explains more.  Though I couldn't get MAKEDEV to create the 'sequencer' device, so this may be the wrong approach.  I'll do a little more looking later.

EDIT:  ```
sudo modprobe snd-seq
``` should fix the problem ([reference](http://ubuntuforums.org/showthread.php?t=41812))

---

### Post by Delkster on 2005-08-21
[QUOTE=agro1986]* playing quicktime movies don't produce any sound![/QUOTE]
This probably isn't a hardware issue.

The audio track in the quicktime files has probably been encoded with a proprietary codec unsupported by the open source decoders included with Ubuntu. At least many movie trailers I've seen use QDesign Audio and I don't know of any open source implementation for decoding that. The Sorenson video codec often used for encoding the video data in quicktime files is, however, supported by open source components, so the video itself works. Sound may also work in some quicktime files if they use a different codec for the audio track (quicktime itself is just a container format after all, not a codec, so different codecs may be used for encoding the actual data).

You'd need the corresponding proprietary Windows codecs for decoding the audio. There's something about that in the [Unofficial Ubuntu 5.04 Starter Guide](http://ubuntuguide.org/) but I haven't tried it so I can't say much more.

---

### Post by GrootBrak on 2005-09-01
I allmost forgot about this post...

I'm still not having sound as in my original post. Same for stratagus. No sound.
Any help would be great.

---

### Post by excelsior on 2005-11-24
Have you installed the package wesnoth-music? The game won't have sound without it

---

### Post by GrootBrak on 2005-11-25
My problem has been solved. I'm using Breezy nowadays. Sound is still soft though, and no fix coming! Thanx

---

### Post by nix4me on 2006-01-01
Thanks for the post.

I have sound in ppracer now.

nix4me

---

### Post by GrootBrak on 2006-01-06
Got the Kubuntu Breezy install. Sound working right from the start, although it was muted after installation. Will have to check on my games, but I lost most since I can't get my back-ups up and running again.

---

