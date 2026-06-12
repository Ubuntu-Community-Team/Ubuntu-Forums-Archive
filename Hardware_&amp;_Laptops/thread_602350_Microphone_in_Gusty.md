---
title: "Microphone in Gusty"
date: 2007-11-04
forum: Hardware &amp; Laptops
---

### Post by picosam on 2007-11-04
I did everything I can ever do. I read all the threads that have to deal with this issue (literally, all of them!). I still couldn't get my microphone to work. Final question (trial): how do I go about re-installing the ALSA drivers in Gusty? Maybe, as a last hope, that would make it work, I have found no direct and clear information that explains how to do this anywhere. Or maybe I haven't searched good enough? Please guide me.

Thank you,
Sammy

P.S. I have a Fujitsu Amilo laptop. Please do not point me to threads explaining how to increase mic/capture volume or unmute it etc. because I've done all this already.

---

### Post by rogirwin on 2007-11-04
I was the same until I installed gnome-alsamixer and ticked the Rec. tick box under capture. alsamixer etc didn't have that option.

Most likely it's muted if the sound works and reinstalling won't help.

---

### Post by picosam on 2007-11-04
Done that already with no success :(

---

### Post by 1/0 on 2007-11-08
Well you could start by unmuting all outputs in alsamixer by hitting “m”. Then hit tab to enter the capture settings. Use the arrow keys to highlight the “Mic” setting and hit space to enable the microphone. Now, use the arrow keys again to  highlight the Capture setting and hit space again to enable capture. Press escape to exit.

Maybe that will work for you?
/ 1/0

---

### Post by cuboconojos on 2008-01-22
I used gnome-alsamixer and it worked!!
Now I can talk in Skype!!!

Thanks

---

