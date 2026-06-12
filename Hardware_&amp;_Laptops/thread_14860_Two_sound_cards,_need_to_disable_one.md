---
title: "Two sound cards, need to disable one"
date: 2005-02-10
forum: Hardware &amp; Laptops
---

### Post by telex4 on 2005-02-10
Ahoy,

I'm having a problem with a friends' PC that has both an on board sound card and a separate card. The onboard one isn't used, but the modules are still being loaded for it, which appear to screw up the sound.

If I manually unload all of the modules, then load the ones the working sound card wants, we have sound. But when the computer boots, ubuntu loads all the modules again.

How can I disable the loading of these excess modules? I nosed around in the alsa, modprobe and hotplug configuration files to no avail.

---

### Post by Cindux on 2005-02-10
I'm not sure about disabling the modules, but make sure 100% you've disabled your friends Onboard sound in the BIOS on his computer.

---

### Post by WillCooke on 2005-02-10
Hi,

The way I did it was to blacklist the modules in hotplug.

For example, if the On Board card was a C Media, then:

[INDENT]sudo nano /etc/hotplug/blacklist[/INDENT]

Then add the module (you clearly know which modules, but for those that don't do an "lsmod" and see if one matches roughly what your looking for, in the case of a C Media sound card the module name is "snd_cmipci") to the end of the list perhaps with a comment to remind yourself why you put it there.

Reboot - job done.


HTH,

Will

---

### Post by telex4 on 2005-02-10
Thanks for the ideas. I'll try them out tomorrow and get back to you if there are any problems, which there shouldn't be.

I didn't know about the hotplug blacklist... handy :)

---

