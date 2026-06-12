---
title: "Nvidia GTS 250 not working correctly in 10.04"
date: 2010-06-13
forum: Hardware
---

### Post by Porpoise on 2010-06-13
Have searched through numerous posts and forums but haven't yet come up with a fix for this one! 

Just updated to 10.04 but can't get xorg to give me any meaningful resolutions (monitor is a Samsung 225 MW with 1680 x 1050 res.) I seem to be stuck with 640 x 480!

Have tried all the methods I have found so far (including downloaded latest drivers from Nvidia site and installed directly) but still no fix. It seems that 10.04 has a slightly different structure to previous versions?!? I haven't managed to find menu.lst yet either (another subject).

Wondering if there is a similar sort of issue going on with regards to video drivers...

HELP!:confused:

---

### Post by mikewhatever on 2010-06-13
Indeed, much has changed since Gutsy Gibbon, 7.10. I am not quite sure what you mean by 'just updated to 10.04', can you elaborate on that. Speaking of xorg, do you mean the xorg.conf config file? If that's the case, try removing it altogether, after making a backup copy.

---

### Post by SeePU on 2010-06-14
> **Porpoise said:**
> Have searched through numerous posts and forums but haven't yet come up with a fix for this one! 

Just updated to 10.04 but can't get xorg to give me any meaningful resolutions (monitor is a Samsung 225 MW with 1680 x 1050 res.) I seem to be stuck with 640 x 480!

Have tried all the methods I have found so far (including downloaded latest drivers from Nvidia site and installed directly) but still no fix. It seems that 10.04 has a slightly different structure to previous versions?!? I haven't managed to find menu.lst yet either (another subject).

Wondering if there is a similar sort of issue going on with regards to video drivers...

HELP!:confused:
Is it a fresh install of 10.04 or did you upgrade to it?

I haven't tried 10.04 yet but I'll be installing it on my desktop eventually.  I think Nvidia drivers have to be a 'brand new' install.  The installer has to purge the 'old stuff' so anything nvidia glx and older kernel headers need to be removed so that new ones are installed instead.   Kernel headers have to correspond with the new driver version and so forth.  When the code is replacing old stuff, there's new 'bits' to replace the old stuff so if something is there, that shouldn't, it will probably go back to VESA drivers.  The other possibility is that something is missing and/or didn't get installed correctly, so it's reverting back to VESA Drivers.

Try checking 'nvidia' in Synaptic and see what's installed.  It's a good visual cue.  Then look in xorg.conf and see what's there.  I think you need to re-install the drivers.  But, maybe purge the old stuff and start over.  I'm not sure if the Nvidia driver installer does a better job at removing the older stuff and re-installing the current driver or the driver you want.

---

### Post by SeePU on 2010-06-14
Search the Lucid section for 'nvidia' and check this link to get a better idea?:

[http://www.ubuntugeek.com/howto-install-nvidia-drivers-manually-on-ubuntu-10-04-lucid-lynx.html](http://www.ubuntugeek.com/howto-install-nvidia-drivers-manually-on-ubuntu-10-04-lucid-lynx.html)

---

