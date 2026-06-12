---
title: "[SOLVED] Sound gone in Intrepid (ATI sound hardware)"
date: 2008-11-02
forum: Hardware
---

### Post by Foster Grant on 2008-11-02
Installed Intrepid and rebooted. Happy. Fired up Songbird to listen to music ... no profit. Tried every multimedia program I have installed and got the same non-result.

I've tried the advice given by Everthon Valadão [on his MobileVS blog](http://mobilevs.blogspot.com/2008/11/how-to-quick-fix-no-sound-issue-in.html) to nuke Pulseaudio and switch everything to ALSA with no luck. I've also tried switching everything over to both the ALSO drivers and the Open Source Soundsystem drivers for the hardware (which is recognized because it's listed in the Sound Preferences control panel ... again, no profit.

I have no sound. This sucks. It's the first major problem I've had with Ubuntu, and I'm not happy.

Grepping lspci for audio references produces this:

```
00:14.2 Audio device: ATI Technologies Inc IXP SB4x0 High Definition Audio Controller (rev 01)
```

So how do I fix it?

---

### Post by ..::benjamin::.. on 2008-11-03
I have a similar problem on a Toshiba laptop with ATI hardware, after installing Intrepid.  First the sound was fine and on another startup the sound is gone.  In Alsamixer the Master-channel was muted and volume at zero (I didn't put it that way), but changing that doesn't help so far.

The question is why the other sound channels don't show up anymore in the alsamixer (only Master shows; this is the same on another Intredpid machine); maybe the PCM channel is muted, which might cause the lack of sound, but how to fix this?

Any help would be much appreciated!

---

### Post by Foster Grant on 2008-11-03
Well, you're not going to get much help from me, I'm afraid. Because of multiple issues I decided to back up my Home folder and re-install Intrepid from scratch as a test (I had upgraded thru Update Manager the first time around). Voila! I have working sound again and the $HOME/.dmrc warning is also gone.

Not really helpful, I know, but it worked.

---

### Post by ..::benjamin::.. on 2008-11-04
But do you still have sound, because at first I also had sound.  I lost sound all together after first/seconde reboot, cause still unknown.

I'll post as soon as I find a solution.

---

### Post by Foster Grant on 2008-11-04
Still have sound. Might have been a dependency issue in my case.

---

### Post by mike22 on 2008-11-06
same thing is happening to me. the advice I hear is to save important doc and folders and reinstall?

---

### Post by Foster Grant on 2008-11-07
> **mike22 said:**
> same thing is happening to me. the advice I hear is to save important doc and folders and reinstall?

I can only say one thing for sure: the nuclear option worked for me. :lolflag:

---

### Post by PMDirac on 2008-11-09
I am having similiar problems on ATI hardware (lspci output):

01:00.1 Audio device: ATI Technologies Inc RV635 Audio device [Radeon HD 3600 Series]

I already reinstalled once because my hardware requires 64 bit (and I tried the beta/alpha for months without knowing ATI video requires special drivers), so I'm a bit reluctant to try the 'nuclear option.'

Any other suggestions would be greatly appreciated.

---

