---
title: "No sound over HDMI on Asus P8H77-M Pro Motherboard"
date: 2013-08-01
forum: Hardware
---

### Post by aaronandlouise on 2013-08-01
Hi.  I have tried the last few versions of  Ubuntu (as well as several other flavors of Linux) and am only able to get certain sounds to work.  I don't get any sounds from aplay, XBMC, Firefox, or the Sounds panel in Dash.  However, Mupen64 produces very good sound.  I have tried every  suggestion I've been able to find online (check wires/amp, check volume  with alsamixer, several different settings inside alsa-base.conf) and  have had no luck.  I do get audio over the analog outputs (rear and  front headphones), just not over HDMI (although Mupen's audio is working over HDMI).  From what I can tell, HDMI is  supposed to be routed through the Panther Point chip and analog audio  goes through the Realtek ALC892 on the motherboard, but I could be wrong  about this.  I have just reinstalled Raring and updated Alsa.  Here is  my Alsa information:
      [http://www.alsa-project.org/db/?f=2e6945f66b998d3563b10ede39d4d5a075f13efc](http://www.alsa-project.org/db/?f=2e6945f66b998d3563b10ede39d4d5a075f13efc)

 Thanks in advance for any help!
-Aaron

---

### Post by TheFu on 2013-08-01
```

APLAY

**** List of PLAYBACK Hardware Devices ****
card 0: PCH [HDA Intel PCH], device 0: ALC892 Analog [ALC892 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 3: ALC892 Digital [ALC892 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 7: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 8: HDMI 1 [HDMI 1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```
This tells me that for HDMI audio to work, you need to specify that card 0, devide 7 or 8 be active.  If you use alsamixer, can you do that?

---

### Post by aaronandlouise on 2013-08-01
I have verified with alsamixer that the proper output card is selected, but I don't know how to select devices in alsamixer.  Can you explain that?

---

### Post by TheFu on 2013-08-01
> **aaronandlouise said:**
> I have verified with alsamixer that the proper output card is selected, but I don't know how to select devices in alsamixer.  Can you explain that?

Sorry, I cannot. The only system I have with HDMI audio uses XBMC and in the XMBC GUI, I use a custom audio device and simply point to the exact card with a: **hw:0,7**  That is not the device used on my box, just as a reference for you - should you be trying this with XBMC. ;)

Most of my systems are virtual machines, not connected to any audio at all. Each runs on a server - so no audio there either.

If I recall correctly, inside alsamixer, changing cards is F6. Don't recall. Make certain that the output levels are not turned down too far in the mixer too.  You might want to setup a ~/.asoundrc file to force a default device.  I've never needed to do that.  I'd expect that the alsamixer man page has all the information available.  The good news is that since **aplay** sees the HDMI, you have drivers loaded that SHOULD work. That is really good news.

Saw that ALSA includes a testing tool, **speaker-test**, that might be helpful too. I've never used it.

I hope someone smarter than me responds with better ideas.

---

### Post by aaronandlouise on 2013-08-02
Actually, xbmc is one of my main goals here since mupen's sound is working.  I tried playing around with the settings in xbmc and it's not making any difference.  I tried a bit with .asound.rc, but I'm not quite sure what I'm doing there.  I tried this:
    defaults.pcm.card 0
    defaults.pcm.device 8
    defaults.ctl.card 0
I tried device=7, too.  I'm really at a loss here for where to look next.

---

### Post by TheFu on 2013-08-02
If you named the file ".asound.rc" - then that is the 1st issue. Use the correct filename. I can only suggest google for more information about it - I've never used it myself.

XBMC audio was not easy to setup.  Besides the specific hardware, the other audio settings must be correct too or you get nothing.

---

### Post by Yellow Pasque on 2013-08-02
> **aaronandlouise said:**
> I tried a bit with .asound.rc, but I'm not quite sure what I'm doing there.  I tried this:
    defaults.pcm.card 0
    defaults.pcm.device 8
    defaults.ctl.card 0
I tried device=7, too.

No, that's not going to help on a pulseaudio system. Delete any asound.rc or asound.conf you made. Check out this thread: [http://ubuntuforums.org/showthread.php?t=2164490](http://ubuntuforums.org/showthread.php?t=2164490)

---

### Post by TheFu on 2013-08-02
> **Temüjin said:**
> No, that's not going to help on a pulseaudio system. Delete any asound.rc or asound.conf you made. Check out this thread: [http://ubuntuforums.org/showthread.php?t=2164490](http://ubuntuforums.org/showthread.php?t=2164490)

The 2nd thing I do on every desktop here - after purging nano - is to remove pulse*. It has been so long that I can't remember why, just that I had issues with pulse audio in my usage patterns. Other people will have different needs, so don't just remove pulse because I did, though my uses are low-end needs - no complex mixing, no specialized audio devices.  Just music, TV, and normal HDMI, SPIDF and analog outputs.


.asoundrc is the correct filename, BTW.

---

### Post by aaronandlouise on 2013-08-03
TheFu, thanks for the help, it did show me that it was a Pulse problem, not Alsa.

Temujin, I followed your post and was able to get audio working over optical, but not HDMI.  That's definitely a usable solution!  I was then able to undo the changes to /etc/pulse/defaults.pa and instead run through the long list of Built-in Audio profiles in pavucontrol's Configuration page and get it to work that way, too.  It was non-obvious which option to select, but it worked once I had the right selection.

Thanks guys!

---

