---
title: "issue with macbook pro sound (after kernel update)"
date: 2006-12-13
forum: Hardware &amp; Laptops
---

### Post by russellc on 2006-12-13
i had sound working on my macbook pro (15in) before the latest kernel update to 2.6.17-10. at that time, i had edited the alsa-base file to include the "options snd-intel-hda "position-fix=2" " line for the sound to work. i'm not sure what happened now, but i updated to the 2.6.17-10 kernel and now the sound does not work anymore. i have tried all the known fixes listed. so now i'm not too sure what to do. how can i go about reverting back to the previous kernel version? is there anyone else with this problem? i also tried installing the latest libasound2 versions and such, but no avail. i would appreciate any help possible and if reverting back to the previous kernel version is possible, then by all means a form of instruction on how to do that would be great. thanks in advance! if any more details are needed, i'll be glad to provide them.

oh also, when running the tests on the sound preferences, it gives the following error:
> audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Could not open resource for writing.

it did this before i updated to the latest libasound2 files and alsa-base files. 

also, when i run alsa configuration applications, they claim that there is no sound card.

---

### Post by cocoia on 2007-02-25
I have managed to fix the sound in that kernel once by simply uninstalling all alsa, reinstalling all of it, and opening alsa-mixer and checking the marks, then sliding all silders up.

---

