---
title: "Problems booting Ubuntu with nVidia and TiMidity"
date: 2008-01-29
forum: Hardware &amp; Laptops
---

### Post by Archyis on 2008-01-29
Oookay, here it goes:
I just installed my new GeForce 7600 GT nVidia graphics. Now it booted up into terminal with no graphics interface. I used envy to install the drivers in the terminal, it didn't seem to have any problems, but when I rebooted it showed a *very* quick error after grub, something about memory allotting, but it flys by too quick to read, then it goes through the Ubuntu loading screen, there doesn't seem to be a problem (I was about to jump for joy at this point... I've been with a cruddy vid card for awhile now), buuut, after the loading screen it shows a few messages and it ends with:

*Starting timidity...                                          [ OK ]
*Starting TiMidity++ ALSA midi emulation...       [ Ok ]

and now (right now actually, I'm posting on a lappy) I'm staring at a blinking cursor right under those lines... I'm pretty sure it's mocking me. I can ctrl+alt+del to shut down (just did that as well to make sure), but that's about it unless I go into recovery mode. Oh , it also blinks three times when it displays the messages at the end then stops.

If I need to keep rebooting to read the memory thins I will. Please help, I can't really afford to get another card, I've already sent one back due to motherboard problems.

---

### Post by HalfLifer on 2008-01-29
I'm getting exactly the same problem on my T61 7664. I've tried a couple of the suggested fixes including setting video to VESA but no love.

---

### Post by Archyis on 2008-01-29
I've found one or two threads with similar problems (old threads slightly difference but... eh I don't even know at this point) but the only post I've seen that even started to give a solution involved "I had to edit the kernel." and that was about it. 

I have a old radeon 9200 that refuses to work too, the loading screen comes up then stops with the bar about an inch in, if anyone's heard of a fix for that it'd be awesome. I'd prefer to get the new good card up, but I'll take anything at this point.

---

### Post by Archyis on 2008-02-02
Hurrah!

Okay, I managed to fix it myself... easier then I figured. Halflifer, I hope you're still checking this cause this might help you. First off I installed my nvidia drivers with envy, but apparently there was a problem when it tried to edit my config files, so go into terminal and type:

sudo nvidia-config

make sure to back up your current conf file... I hope that helps.

(it might still show the memory allotment message, but that doesn't mean it's not working. Mine does it too, but boots right up.

---

