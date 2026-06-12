---
title: "Sound on resume distorted (Sony Vaio w/intel sound card)"
date: 2007-06-25
forum: Hardware &amp; Laptops
---

### Post by gregorygreg on 2007-06-25
I posted a problem that I was having awhile ago where my sound upon resuming from suspend would crackle and echo.  Someone told me that I had to restart my sound driver but did not explain how to do this and I was unable to find a solution online.
Any suggestions?

Thanks,
Greg

---

### Post by gregorygreg on 2007-07-09
Jump!

(snd_hda_intel / snd_hda_codec)

---

### Post by Depressed Man on 2007-07-09
I don't know much (struggling with a similar problem on a Sony VAIO FE series too). But if you use ALSA this should work. 

In the terminal

/etc/init.d/alsa-utils restart

or

alsa-utils restart

Though I think the "fix" for now is to somehow unload the sound module by editing this 

/etc/default/acpi-support

and adding in the sound module to this list. Though I don't know which module to add myself..(where I'm stuck)

# Add modules to this list to have them removed before suspend and reloaded
# on resume. An example would be MODULES="em8300 yenta_socket"
#
# Note that network cards and USB controllers will automatically be unloaded
# unless they're listed in MODULES_WHITELIST
MODULES="module name here"

Hope that helps!

---

