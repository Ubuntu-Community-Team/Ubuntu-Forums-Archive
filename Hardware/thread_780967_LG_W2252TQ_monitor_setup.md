---
title: "LG W2252TQ monitor setup"
date: 2008-05-03
forum: Hardware
---

### Post by sofasurfer on 2008-05-03
Hardy 64bit.

I just bought a LG W2252TQ monitor. Holy cow!! I was worried it wouldn't be big enough. Its HUGE!!!

On first power up the resolution was low. Video on [www.nbc.com](www.nbc.com) was jerky. I couldn't understand that.

The instructions are kinda meager so I just puttered with it.
I went to desktop>change desktop background>visual effects.
I clicked on the "normal" button and rebooted. Resolution was improved.
I went to system>preferences>screen resolution and I see that resolution is at 1680X1050. But the refresh rate is at 50 Hz with the only other option being 51 Hz. Rotation is "normal" whatever that means.

My question is about refresh rate. Shouldn't that be 60 Hz? Does it make a differance? Video is not jerky anymore. Don't know what changed there.

Is there anything else I need to know or do?

And as for my review, this monitor is huge, very bright, vivid. Its pretty stable on the stand. I looked at a samsung and it wobbled really bad. Not the LG though.

It has a connection for both an analog and a dvi cable. The dvi cable was not included. So I am running on analog yet. Don't know what improvement dvi will make over analog. 

Question. When I get the dvi cable, do I leave them both, the analog and the dvi, connected or only the dvi?

I'll write more about this monitor after I learn more bout the controls and use it longer.

---

### Post by jedimasterk on 2008-06-27
Well any answers to this guys question. I also am looking into this monitor for my Ubuntu system. And have the same question?.

---

### Post by tchalvakspam on 2008-10-06
Just got the same monitor, after a lot of fiddling with the screen resolution, it's now showing in all its 1680x1050 glory.

This is in Hardy Heron, Gnome, on a Dell Dimension C521.

My recommendation when first setting up an LG Flatron W2252TQ and probably other similar LG Flatron monitors with ubuntu is:  
Make sure to install the driver (someThing.inf) from the cd that came with it.  You can install it by running displayconfig-gtk on the command line to get to a gui to work with. 

Restart after installing the driver, then try to change your resolution to the appropriate value (I'm using 1680x1050 right now).

If your default user's desktop doesn't adjust the first time around, use the "switch user" option to view a blank user's desktop to see if the default xorg.conf file is actually handling the new monitor and resolution fine, and it's just the current configuration that isn't adjusting.  That'll at least tell you whether it's some user-specific setting or whether the default ubuntu configuration isn't handling it either.

Most important is the install of the driver, though, I think.

---

### Post by AFarris01 on 2008-12-06
I actually got this monitor for my birthday this year, I'm running ubuntu Hardy, 32 bit, ATI HD 2600xt graphics, on a custom computer.  I didnt bother with the .inf driver thingy, and it works great.  the only issue i have with it is that the text in some programs is really hard to read for some reason.  perhaps it's because i didnt install that .inf...
oh well.  all in all though, i love this monitor, and i will purchase a second one soon so i can fully exploit the unused power of my desktop :)

---

