---
title: "odd sound problem"
date: 2005-04-19
forum: Hardware &amp; Laptops
---

### Post by Liz on 2005-04-19
im using an sis onboard sound chip. 
it all works fine, on my login.... on my sons login, he has no sound whatso ever. no system sounds, no sounds in xmms or music player. 

it used to work on monday, it doesnt work on tuesday. 

he has access to the cdrom group, and the audio hardware group. i doubled checked just in case hes changed an option somewhere. ..
ive checked the settings on xmms to make sure it uses esd sound, and it does.
ive checked the multimedia systems selector in system ->preferences. they are set the same as mine. 

still no sound.
anyone got any ideas where i can look for an answer?

if its something ive installed recently?..could be..ive installed and then uninstalled amaya..ive installed mozilla web browser..and thats it. and niether of those should conflict with the sound on his side of things. 

ideas?

thanks.

---

### Post by kassetra on 2005-04-19
[QUOTE=Liz]im using an sis onboard sound chip. 
it all works fine, on my login.... on my sons login, he has no sound whatso ever. no system sounds, no sounds in xmms or music player.[/QUOTE]

The thought I had was to check the "PCM" sound volume when logged in as him:
Right click on the "Speaker" in the top panel.
Left click on "Open Volume Control" in the little pop-up menu.
PCM should not be muted, nor should the sliders be all the way at the bottom.

Make sure none of the sliders are at the bottom, and nothing is muted.

---

### Post by Liz on 2005-04-20
already did that too.
i had that in warty, and someone advised me to look in alsamixer.

i dont know what the problem was, but its been solved now. 
i rebooted the machine,a nd that seemed to clear the problem.

very odd.
but its working now.

---

