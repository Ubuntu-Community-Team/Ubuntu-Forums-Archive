---
title: "Lenovo Ideapad y510 Sound"
date: 2011-03-18
forum: Hardware
---

### Post by KaiSkylerBliss on 2011-03-18
Ok, I have found a way to make it real easy to fix the sound in a Lenovo y510 laptop. You get the sub working and headphones, and mutes when headphones are plugged in.

First, browse to /ect/modprobe.d/ 
Then open alsa-base.conf

At the bottom of the file, add

options snd-hda-intel model=lenovo-sky

Then reboot.

After, open terminal and type

alsamixer

And find where it says 

Channel

After you have found that, change it to 6 instead of 2.
You will now have excellent sound and headphones will now work perfectly!

Hope this helps.

---

