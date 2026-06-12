---
title: "Video colors inverted after upgrade"
date: 2009-06-26
forum: Installation &amp; Upgrades
---

### Post by Nick3193 on 2009-06-26
A few days ago I let the Upgrade Manager install a new kernel (2.6.28-13-generic) as well as some other patches.  Since it was rebuilding the kernel, I also upgraded the NVIDIA video driver to a newer version I had previously downloaded (185.18.04).  Since that time, the color of every video I try to watch has been inverted.  Blues have become yellow, green is magenta, etc.  It doesn't affect anything but videos, but it's doesn't matter what type of video it is: DIVX, WMV, MPEG, pretty much everything except Flash Video is screwy.  This is true in every player I've tried: gxine, mplayer, and players embedded in Firefox.  MythTV is having the same problem.  I've updated the NVIDIA driver to the latest version (185.18.14) without any difference.  I've downloaded, compiled, and installed the latest ffmpeg, no help there either.  I'm guessing it's something in gstreamer or maybe Totem?  I really don't know, and it's gotten very annoying.

:confused:

Is anyone else having a problem like this, and does anyone have any suggestions on fixing it?  Is there an easy way to roll back patches that have been applied using Update Manager?  Thanks in advance for any suggestions!

---

### Post by starcraft.man on 2009-06-26
> **Nick3193 said:**
> 
Is anyone else having a problem like this, and does anyone have any suggestions on fixing it?  Is there an easy way to roll back patches that have been applied using Update Manager?  Thanks in advance for any suggestions!

No, not really. Upgrading is pretty much one way. One day we should get a quick roll back program, or maybe there is such a thing and I don't know it.

I want to isolate this problem and make sure it's just a video acceleration issue. Can you install VLC from the repos please, open any video and confirm the problem still there. Then go to the preferences, under video and turn off acceleration (leave the pipe to default output). See if that fixes it? Then, turn it back on and try different piping/output for the video, with both X11 and openGL, see if either return a different result. Report results after of each test, whether or not you still got color inflection.

From the suddenness, I'm a bit suspicious. I've had no trouble with the latest bleeding edge driver nor am I aware of any regressions like this. What card is it btw? Is it old? It could be dying maybe? A thought, hopefully not.

Report back and I will see if I can think of any more diagnostics.

How did you install the driver btw? Manually by dropping the GDM and running the bin/.run file? Another means?

---

### Post by Nick3193 on 2009-06-27
I installed VLC to try the suggestions you had.  The videos played fine, no color problems at all.  I went back to the players I was using that had the problem, it's fine now.  The color looks great.  I can't say WHAT it was that fixed it; this morning I was trying to get Audacious to work and didn't do **anything** with video or video drivers.  I think my system isn't properly scared of me and it's acting up.  I need to get out the sledgehammer and set it next to the monitor to keep it in line. :P

Thank you very much for your help!

---

### Post by starcraft.man on 2009-06-27
You give too little credit to the great VLC. It fixes things just by being installed :P.

Glad your all fixed up, enjoy.

---

### Post by Nick3193 on 2009-07-01
Well, perhaps I spoke too soon.  It's acting up again but at least I know it's something that can be resolved.  Now all I need to do is figure out what it is that's changing.  :)

I did what you suggested in VLC (sweet little app there!).  Turning off acceleration didn't make a difference, nor did turning it back on.  Changing the output did though.  I first tried OpenGL and the color was fine again.  Same for X11.  I have some ideas about what may be triggering the problem though, based on how I've used the computer today.  I'm confident that it's not going to be a problem much longer.  Thanks again, and thank you to VLC!

---

