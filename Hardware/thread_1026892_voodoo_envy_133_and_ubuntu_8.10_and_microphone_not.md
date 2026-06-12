---
title: "voodoo envy 133 and ubuntu 8.10 and microphone not working"
date: 2008-12-31
forum: Hardware
---

### Post by .primus on 2008-12-31
hi all,

i am running ubuntu 8.10 on a voodoo envy 133.

alsamixer reports
card: hda intel
chip: silicon image SiI1392 hdmi

the problem is i cannot seem to record any sound via the microphone.

i have checked in alsamixer that capture is capturing and i have tried recording with the following input sources: mic, front mic, and line. 

the mic boost, front mic boost, line boost, and capture channels are at maximum volume.

i dont know if anyone is familiar with the voodoo envy 133 hardware, but my understanding is that the headphone output doubles as a microphone input. however, i could be way off base with this (i dont currently have the manual handy).

any help or pointers would be great!

thanks in advance.

---

### Post by .primus on 2009-03-01
for those interested, the resolution was to add

options snd-hda-intel model=dell-m6

to the file

/etc/modprobe.d/alsa-base

---

### Post by inverser on 2010-12-28
> **.primus said:**
> for those interested, the resolution was to add

options snd-hda-intel model=dell-m6

to the file

/etc/modprobe.d/alsa-base
Hi Primus, I'm trying to get the builtin microphone working on my Envy133 and found your thread. I've tried the instructions above but don't notice any change. Can you add any details to the instructions? Do I have to change any alsa mixer settings also?

---

### Post by .primus on 2010-12-29
hi Inverser,

i admit this was quite a while ago, so i don't recall the precise details of the fix.

are you running 8.10 or are you running a higher version of ubuntu? in the version after 8.10 i did not have to apply the fix described above. i am running 10.04 on my envy now and did not have to do this.

most likely there is something with your alsamixer settings, that is usually the culprit for me. if you run the command "alsamixer" in the terminal, i have the capture selected on the Capture. you do this by hitting F4 and then you should see something like:

```

     x                x       
     x                x           x
     x                x           x
Front Mic Boost     Capture    Digital

```

and i have the Capture selected and see a red CAPTURE on it. i think the space bar selects.

hope this helps

---

