---
title: "Audio/Video/Power Management(acpi) problem after upgrading to Edgy"
date: 2006-11-01
forum: Hardware &amp; Laptops
---

### Post by Dutchy on 2006-11-01
FIXED, READ POST BELOW

Hello everyone,

After upgrading from Dapper to Edgy on my Toshiba Satellite P100-232 I have a little problem. Here's the deal:

Before, in Dapper, I had my sound working and my power management (acpi), however not at the same time. I'd like this fixed but it's no biggie, I didnt care much, I booted with acpi=off and I had sound.

After upgrading, my Xorg stopped working returning returning an error that it couldnt read /dev/nvidia0 ... even after reconfiguring xorg and reinstalling the nvidia drivers it wouldnt do anything, _until_ i turned on acpi again. Making the sound stop working ofcourse... So video but no sound...

I have no clue where to go from here, except one: Before the ubuntu loading bar at boot, I see some errors telling me something about failing to allocate memory for some pci bus id's or something, it goes too fast for me to read, is this logged somewhere? Though these are just the errors that i used to get when loading both sound and acpi, it's nothing new...

I'd love to get all three working, but just the video and audio, like i used to have, is just fine. Perhaps it's just a configuration problem for xorg/nvidia/gdm atm? I can post those .conf's later if necessairy, or any other info you may need.

I recon reinstalling ubuntu would fix it but thats the very last option, because i dont want to go through the trouble of reconfiguring the wireless again :>

I hope I made some sense up there... Who can help me?

the sound: snd_hda_intel (a bitch)
gfx card: nvidia go 7900
processor: intel T2600



~~Dutchy

---

### Post by Dutchy on 2006-11-01
Sorry for the shameless bump but my thread got to the second page with only 6 views, so i felt i could bump it :)

Any extra info I could supply that could be useful for solving my case?

---

### Post by Dutchy on 2006-11-01
pci=noacpi pci=biosirq noapic acpi=off seemed to fix my sound again

---

### Post by dactry on 2006-12-08
I have the exact same problem. did you ever find a solution?

---

### Post by Dutchy on 2007-06-03
I have found a solution after months

[http://www.linuxquestions.org/questions/showthread.php?p=2773589#post2773589](http://www.linuxquestions.org/questions/showthread.php?p=2773589#post2773589)

it's a guide for suse but i found out how to do it on Ubuntu and posted a small fix in that thread, it's the 11th post

This is a fix for the Toshiba Satellite P100 laptops

[http://gentoo-wiki.com/HARDWARE_Toshiba_Satellite_P100#Audio](http://gentoo-wiki.com/HARDWARE_Toshiba_Satellite_P100#Audio)

If a mod reads this, perhaps post a sticky or something? It's a quite common problem

---

