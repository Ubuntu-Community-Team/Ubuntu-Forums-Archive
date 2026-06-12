---
title: "You're gonna love this HDA-Intel bug"
date: 2008-05-15
forum: Hardware
---

### Post by marius311 on 2008-05-15
Installed Hardy and everything went flawlessly. My HDA-Intel sound card got configured perfectly (i.e. I have sliders for Center, and LFE volumes). Now here's the bug. If I boot into Windows XP on my other drive, then when I come back to Hardy, those volume sliders are gone! Happens EVERY single time. And the way to get them back? The best I've found so far is to suspend Hardy, resume, then restart. Then when it boots up again they're back. 

So yeah, this is a pretty weird one I think. I don't really know where to start. Any thoughts?

---

### Post by ivze on 2008-05-15
I have heard about such bugs. 
Don't have much to say, but feel curious.
Please, make an experiment: 
1)raise the bug (make the sliders disappear)
2)turn off the computer
3)unplug power socket and waint 2-3 mins
4)launch ubuntu again and see, whether the sliders are back without suspend->resume->restart.

---

### Post by prshah on 2008-05-15
> **marius311 said:**
> Now here's the bug. If I boot into Windows XP on my other drive, then when I come back to Hardy, those volume sliders are gone! Happens EVERY single time.
So yeah, this is a pretty weird one I think. I don't really know where to start. Any thoughts?

I'd think that the UAA (Microsoft's attempt for a Universal Audio Architecture) is responsible.

While I have not had this problem ever occur before, I know that on Windows (XP) I should install UAA _first_. before installing audio drivers. Failing to do this, or having a bad UAA install, means that I get no audio slider and as good as no high-level audio functions (mixers, et al). Note that I'm _still_ talking about Windows.

Even if UAA install is bad, you will get sound, and the dinky little speaker icon (probably red in color), so just playing an MP3 or hearing the startup sound is not a test.

Maybe you should try this in Windows:

a) First, create a restore point
b) 2nd Uninstall audio drivers
c) Uninstall UAA (this is a pain and very difficult; please refer MS knowledge base, do not have links at hand)
d) Reboot (non-sequitur)
e) Install UAA (Cancel _all_ "New Hardware Found" dialogs)
f) Reinstall audio drivers
g) restart

Then check if this Hardy error crops up again.

When I review this, it sounds like a lot of work to me, especially for an uncertain result; maybe first you should check in Windows if you have any mixers. Start-Run-```
sndvol32
``` If you do, then the above may not really be helpful.

---

### Post by marius311 on 2008-05-15
ivze- yep sure enough that worked

prshah- i was thinking it might have something to do windows drivers (you know its a bad bug when it affects OTHER operating systems). thanks for the advice but i figured out another solution, see below...


i got the output of dmesg after a good boot (i.e. sound works), and a bad one. the problem appears to be that the BIOS autoprobe fails, so it never gets set to 3-stack. 

good boot:

```
[   50.013568] hda_codec: Unknown model for ALC880, trying auto-probe from BIOS...
[   50.014215] hda_codec: Cannot set up configuration from BIOS.  Using 3-stack mode...
```

bad boot:

```
[   47.713028] hda_codec: Unknown model for ALC880, trying auto-probe from BIOS...
```

so basically, its just the autodetection that gets killed by windows. if i manually add "options snd-hda-intel model=3stack" to /etc/modprobe.d/alsa-base, then they don't dissapear after a windows boot. the only issue is the volumes are all set to 0, but i can deal with that for now. 

problem solved, time to stop procrastinating and get back to studying for finals.. ;)

---

