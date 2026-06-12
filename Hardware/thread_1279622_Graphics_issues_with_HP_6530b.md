---
title: "Graphics issues with HP 6530b"
date: 2009-10-01
forum: Hardware
---

### Post by pwagen on 2009-10-01
I recently (a month or two ago) installed Kubuntu on my laptop. Yesterday, I made a switch to "normal" Ubuntu. Both distros had the same issue.

The problem I've had since day 1 is that sometimes (definitely not always) when booting, the resolution is set to 1024x768, which looks really bad on a widescreen laptop made for 1280x800. Sometimes it works going to the display settings and detect monitors, other times the only working thing is to reboot again (I guess just restarting X would do the trick as well, but I'm pretty fresh from Windows so bear with me).

Another problem which might or might not be related is that I started tinkering with the Allegro game library in C++. Sometimes when exiting a program (normally), the graphics gets "stuck" at 640x480 (which is the resolution I've used so far). Again, going to the display settings and detecting monitors work most of the time. I assume this could also be some problem with Allegro, but since it's a similar problem I thought I should mention it.

My xorg.conf looks like this:

```
Section "Device"
    Identifier    "Configured Video Device"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
EndSection
```I've tried making a SubSection in "Screen" called "Display" (I think, memory is a bit fuzzy), setting up resolution and stuff going by what I saw in some other post, but that didn't help either. I would try more, but not really sure what I would be doing...

Could anyone shed some light on this, or tell me where to look? I don't feel like having a link to the display settings on my desktop anymore, just to make it faster changing the  resolution at boot-up...

Anything I missed, just ask.

---

### Post by Yellow Pasque on 2009-10-01
When you get stuck with 1024x768, post/pastebin the /var/log/Xorg.0.log file.

---

### Post by pwagen on 2009-10-08
Thanks for the reply. Sorry it took a while to get back to you - the computer har behaved for quite some time.

The file you asked for is a long one, and I'm not sure which part it is you want, so here it is in all its glory:
[http://pastebin.com/m55c00dbc](http://pastebin.com/m55c00dbc)

---

### Post by pwagen on 2009-10-13
Sorry for the bump, but I'm getting a bit desperate for a solution. It seems it happens more and more often lately. Any suggestion where to look would be very appreciated.

---

### Post by Lord Stig on 2009-10-13
I am no expert but I had a problem with a game leaving my desktop in 640x480 resolution after it exits and my way of solving it was to type "xrandr -s 1024x768" into a text file, save it on my desktop and set the properties of that file to run in terminal (or wording to that effect - different with different file managers and I don't have access to a Linux machine at the moment).
That way, when it happens I just double click my file and it runs the command and switches the screen res immediately.

If you do use try this idea it's best to keep the icon for your script in the top left of the desktop because it's the top left that's always visible regardless of your current resolution.

Hope that helps.

---

### Post by Yellow Pasque on 2009-10-13
Helpful info: [https://wiki.ubuntu.com/X/Troubleshooting/Resolution#Problem:%20%20Autodetection%20results%20in%20reduced%20resolutions%20available](https://wiki.ubuntu.com/X/Troubleshooting/Resolution#Problem:%20%20Autodetection%20results%20in%20reduced%20resolutions%20available)

I don't have too much experience with intel graphics, but I think this is the crux of your problem:
> (II) intel(0): Output VGA using monitor section Configured Monitor
(II) intel(0): Output LVDS has no monitor section
Even if you made a custom Screen/Display section, it was probably trying to verify those modes on your VGA output.

Hopefully, another intel laptop user can give you a good xorg.conf if you can't figure out how to turn off the VGA, like here: [http://www.thinkwiki.org/wiki/Xorg_RandR_1.2](http://www.thinkwiki.org/wiki/Xorg_RandR_1.2)

---

### Post by pwagen on 2009-10-15
> **Lord Stig said:**
> I am no expert but I had a problem with a game leaving my desktop in 640x480 resolution after it exits and my way of solving it was to type "xrandr -s 1024x768" into a text file, save it on my desktop and set the properties of that file to run in terminal (or wording to that effect - different with different file managers and I don't have access to a Linux machine at the moment).
That way, when it happens I just double click my file and it runs the command and switches the screen res immediately.

If you do use try this idea it's best to keep the icon for your script in the top left of the desktop because it's the top left that's always visible regardless of your current resolution.
Yeah, that's what I've done so far. I kept an icon in the top left corner to the display manager, just in case. Got sick of it though :P

Thanks for the tips and links! Will dig into them ASAP and then come back and tell the story of how it turned out. Much appreciated :)

---

### Post by pwagen on 2009-11-13
Now I've done pretty much everything that's been described in the links posted above, and I'm now permanently stuck in 1024x768. Not because of changes I made though. I fired it up earlier today, and couldn't for the life of me get back to normal resolution, so went through all of the above. But to no avail so far :(

One thing I've noted now though, is that when on the login screen (still using 9.04 btw), the resolution is normal and the screen stretches to all edges of the monitor. All the time before, the login screen was lower resoluted as well. My guess is that this means only my main account (only account except for root) has graphic issues. It's way too late now, but tomorrow I guess I will try creating an additional account and see if the problem persists unless someone else has a really classy idea.

I still can't wrap my head around how it happened though - whether it works or not, it should be consistent every time I start my computer, not randomly work or not when I haven't changed a single setting or done anything at all except boot it.

---

