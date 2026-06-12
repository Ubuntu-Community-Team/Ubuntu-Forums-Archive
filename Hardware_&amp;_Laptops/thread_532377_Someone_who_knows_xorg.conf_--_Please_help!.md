---
title: "Someone who knows xorg.conf -- Please help!"
date: 2007-08-22
forum: Hardware &amp; Laptops
---

### Post by porcorosso on 2007-08-22
So close, and yet so far...

I have a Dell Precision M70 laptop with an nVidia Quadro FX Go1400 video subsystem.

If I use the Open Source drivers it does exactly what I want it to do -- which is, use my laptop's own built-in display when undocked, and use the external display when docked.

Internal display is a Seiko 1920x1200. External display is a Dell 2005fpw 1680x1050.

When I installed the restricted drivers on the system undocked, everything worked perfectly. Suddenly the system was a LOT faster and more responsive. OpenGL / 3D worked very well.

I had been down this road a couple of times. I followed the advice at this location:

[http://www.ublug.org/howtos/ubuntu/twinview/twinview-howto-laptop.html]("http://www.ublug.org/howtos/ubuntu/twinview/twinview-howto-laptop.html")

-- to see if I could get this system to just work the way it did with the standard Open Source drivers.

I'm attaching a file containing the error messages I get when running nvidia-settings, and a copy of my xorg.conf file. I've hammered at this until I'm blue in the face, and have gotten a lot farther this time around than ever before. But I'm thinking that the knowledge I still lack must be pretty arcane.

Here's how the system behaves now. If I dock it and start it up (with the lid closed) the external screen works fine right through the usplash screen, and then goes blank. I hear the logon screen sound. I open the lid, and there the screen is, in all its glory. I log on. The only way I can switch to the external screen (only) is to start nvidia-settings as root and choose Metamode3 which turns off the built-in screen and turns on the external screen. Resolutions are fine. If I choose Metamode2 I get both screens active with 1680x1050 resolution, clones of each other. If I choose Metamode1 I'm right back on the built-in screen with the external screen turned off.

This situation is workable, but I'd like it to just come up on the external screen alone when the system is docked.

Can someone here tell me what I've done wrong? I'd really love to solve this little problem, but a couple of weeks' worth of research have left me scratching my head on this one.

Thanks.

----

PS: Okay, I decided that the original xorg.txt (xorg.conf) file I posted was a real Frankenstein. I eliminated as much superfluous stuff as possible last evening -- killing everything I could then seeing if xserver would still start. After a lot of trial and error I've attached what's left.

It still behaves the same. No matter what configuration I boot up in -- undocked,  docked with the lid closed, docked with the lid open -- the login screen is going to come up on the built-in LCD. The ONLY way I can switch to having both monitors active or having just the external monitor active is to use nvidia-settings to apply a different metamode.

I want it to just "know" which screen to use, depending upon the docking / lid configuration -- just like it automatically does with the VESA driver.

Can someone help me -- please?

---

### Post by porcorosso on 2007-08-23
C'mon, throw me a bone, here!

;)

Surely someone has some direct experience with this issue?

Okay, I promise not to call you Shirley. Just help me. Someone?

Buhler?

---

### Post by tseliot on 2007-08-23
did you try asking here?
[http://www.nvnews.net/vbulletin/forumdisplay.php?s=&forumid=14](http://www.nvnews.net/vbulletin/forumdisplay.php?s=&forumid=14)

---

### Post by porcorosso on 2007-08-23
> **tseliot said:**
> did you try asking here?
[http://www.nvnews.net/vbulletin/forumdisplay.php?s=&forumid=14](http://www.nvnews.net/vbulletin/forumdisplay.php?s=&forumid=14)

I'll give it a shot. I searched there before and didn't think anyone seemed to be covering issues with configuring xorg.conf at all. They seem more interested in the driver installation process than anything else.

I think it's weird that nvidia-settings (run under root) simply cannot write to my xorg.conf file. Not that I'm really sure I want it to -- if you know what I mean.

The way I see it -- either I'm flaky, or nvidia-settings is flaky, or both of us are flaky. Really, really flaky.

:confused:

---

### Post by porcorosso on 2007-08-24
Well, I never got a response at all over in the other forum (nvnews). They appear to be almost entirely focused in that Linux section on just getting the drivers installed. That was never the problem for me. Every method I tried for installing the binary drivers worked. It was just trying to get the dual head configuration working properly that was stumping me.

In the end, it turns out that I was trying to make it too hard -- or expecting too much, I guess. With the binary drivers installed on this notebook it appears that automatic reconfiguration to use the built-in vs. the external monitor just ain't gonna happen -- at least at this juncture. But I did get it configured so that I don't have to start the danged thing with the lid open when I want to use the external monitor. When I hear the logon sound, I just hit Ctrl+Alt+- on the external keyboard, and the video output switches over to the external monitor. I am also able to use both monitors if I wish, with the desktop spanning them.

Ubuntu / Gnome wil lbe doing well if they can make this an "intuitive" process. Heck, I've seen people who knew virtually nothing about this sort of thing stumble into getting a multi-monitor configuration working with Windows XP or Vista. That's not really going to happen right now with Linux.

But for me, this is just a bunch of new toys to play with. I'm tickled by the nitty-gritty controls on most features available to users of this OS, and then flabbergasted by the lack of pretty basic controls on some other features. But I guess it will get there.

---

### Post by porcorosso on 2007-08-25
While I'm talking to myself, I'll make one last note in this thread...

I decided to heck with the restricted drivers. I finally got it all (almost) working just the way I wanted it to work, and then discovered that I couldn't play multimedia files on the system any more. I tried removing and reinstalling codecs and software, different codecs and software, reverting the hal to an earlier version -- none of it to any avail.

Know what worked? Yeah, removing the danged restricted drivers. So I've got a fancy notebook with a Quadro FX Go1400 video card in it, and all I'm going to get under Feisty for OpenGL support is what the Open Source drivers provide. Sad. But at least everything else besides OpenGL works very well.

---

