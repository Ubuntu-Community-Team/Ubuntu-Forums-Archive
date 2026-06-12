---
title: "Troubleshooting my laptop, need help"
date: 2014-07-21
forum: Hardware
---

### Post by kieeps2 on 2014-07-21
Hi
I recently switched laptop from my Asus g73jw to a asus g750
The old g73 never really worked 100% since there where some weird "spontaneous freeze" bug that i always blamed windows for. but now i installed ubuntu 14.04 server on it and hosted a friends minecraft server on it.

Problem now is that even though the performance/Hardware is way more then it needs to be i tend to get those "spontaneous freezes" yet again... so it has to be hardware related.

I have no idea how to troubleshoot this, i started looking in the logs to see if there where some problems with the kernel or something but didn't find anything.

Frankly i'd love it if there where a software of some kind out there that worked similar to the logcat software on android. Does anyone know any good ways to troubleshoot the laptop? or if there is any good softwares that monitor the communication between hardware and OS?

PS: i managed to work arround the spontaneous freezes with windows by lowering the "maximum CPU freq" to 80%. so something tells me it's something mobo related :mad: that "workaround" didn't work perfectly but it sure helped a lot.

---

### Post by mikewhatever on 2014-07-21
Troubleshooting hardware problems is difficult, I've no suggestions. You could try cpufrequtils to change the cpu governor from ondemand to powersave, as a workaround.

---

### Post by Yellow Pasque on 2014-07-21
It's probably overheating (especially if reducing CPU speed helps).

BTW, are you talking about the g73 or g750 here?

---

### Post by GrouchyGaijin on 2014-07-21
Yeah - I had an old Dell Inspiron 1520 that was constantly getting too hot.  Using CPUfreq solved the problem.  Once the laptop stopped getting so hot a lot of performance problems disappeared.

---

### Post by kieeps2 on 2014-07-21
thanks guys for the quick responses.

This is the g73 i'm talking about, the g750 works perfecly
I did suspect heat problems first aswell since thats usualy always the case with laptops. i opened it and gave it a good clean and repaste. found a software to write the temps to a file so that i could look at it after the computer froze and it was freezing at temps as low as 40C.

I will try the gov switch though :)

---

### Post by Yellow Pasque on 2014-07-21
I see some very similar complaints about this GPU, but those are under Windows, so who knows if they're related. [https://forums.geforce.com/default/topic/509337/geforce-mobile-gpus/nvidia-geforce-gtx-460m-crashes-blackscreen-bsod-crashing-during-gaming-/](https://forums.geforce.com/default/topic/509337/geforce-mobile-gpus/nvidia-geforce-gtx-460m-crashes-blackscreen-bsod-crashing-during-gaming-/)

---

### Post by kieeps2 on 2014-07-22
think it's the GPU? not sure how that would affect ubuntu server 14.04 :P
But still... if the GPU is faulty i guess it could bug the system by just being there. i'll look in to it

---

### Post by Yellow Pasque on 2014-07-22
Hmm, I saw Minecraft and assumed you were playing it.

Anyway, the two easy things I can think of here are memtest and making sure BIOS is updated. Unfortunately, Asus can't be bothered to give detailed changelogs, so we have no idea what changes in the latest BIOS...

---

### Post by kieeps2 on 2014-07-22
Well i do play ;-) just discovered this childishly addictive game  :-D and thats what triggered me to pull out my old g73 again :-)

I did try the govenour workaround but since it's a quadcore with HT i have to switch on all 8 "cores", the cores are numbered from 0-7 as expected... But what cores are actual physical cores? Anyone has a clue? Figured i might even combine different gouvenors... Who knows right? :-)

But putting them all in powersave gave a dramatic perfomance drop and still gave me freezes, i'll look in to using the same software to lower the cpu freq instead.

Cant belive a "simple" game like this is so damn perfomance demanding... Kinda why i never liked java :-P

Anyway, back to an earlier question.
Not sure if you guys even know what logcat is, but are there any equivalent to linux? That way i could keep it running and look at it when the problems occur.


Oh and about the bios, i have the latest asus released for the model i have... Not sure if i have the balls to try another one :-P

---

### Post by felly2 on 2014-07-23
[COLOR=#333333][FONT=HelveticaNeue-Light]most of the G73Jh stuff will apply to a Jw, except for the exact layout of the heatsink and the temps[/FONT][/COLOR]

---

### Post by kieeps2 on 2014-07-23
Well i guess i have nothing to loose :-) exept for the laptop i guess :-P but might be wort it!

---

