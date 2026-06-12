---
title: "Plug in a headphone... sound still comes out laptop speakers"
date: 2007-06-27
forum: Hardware &amp; Laptops
---

### Post by bohsocks on 2007-06-27
Hey guys.  I was using Gutsy earlier today and all of a sudden when I tried to plug in a headset, and the sound continued to come out of the speakers..... 

If it's of any significance... I was installing the xine-ui package for DVD playback at the time.... I don't think it makes any difference

This is quite annoying.

Thank you!

---

### Post by scrooge_74 on 2007-06-27
On Feisty I did:

open a terminal type alsamixer

move arrow to headphone

on top,  on Item it says Headphone Jack Sense [Off]

type m 

plug headset, it should work now

---

### Post by garamas on 2007-10-10
i dont get the headphone option 
all i get is.....


**MASTER**   **PCM**   **IEC958**   **EXT MIC**   **INT MIC**

no headphone option :confused:

---

### Post by gubemton on 2007-10-14
Try:
 $ amixer controls

Get the numid and then:

$ amixer cset numid=... '0%'

Give a try :)

---

### Post by johnnybaconbits on 2007-10-20
same problem gave it a try this is what i get tho

 amixer controls
numid=3,iface=MIXER,name='Master Playback Volume'
numid=4,iface=MIXER,name='PCM Playback Volume'
numid=2,iface=MIXER,name='Caller ID Switch'
numid=1,iface=MIXER,name='Off-hook Switch'

no option for headphones either?

---

### Post by marcantonio on 2007-10-22
Exact same issue...

---

### Post by kyphi on 2007-10-22
On laptops, what should happen is that when you plug your headphones into the headphone socket, the circuit to the loudspeakers is interrupted and diverted to the headphones.

If this is not happening then your switch is faulty and needs to be replaced or adjusted.

---

### Post by CromagDK on 2007-10-22
I do not believe that is totaly true.
I installed ubuntu feisty on another laptop some time ago and had the same issue.
I was comming from windows XP with no issue like this. And when i changed back to windows xp it worked fine again.

---

### Post by scrooge_74 on 2007-10-22
> **kyphi said:**
> On laptops, what should happen is that when you plug your headphones into the headphone socket, the circuit to the loudspeakers is interrupted and diverted to the headphones.

If this is not happening then your switch is faulty and needs to be replaced or adjusted.

I doubt it because it happens to me from time to time, mostly after a suspend to disk. I then go to my sound control (or use alsamixer from the command line) and enable or disable (depends on the mood of my laptop) the headphone  jack sense

---

### Post by brancheb on 2007-10-22
Are the headphones by any chance powered? I have some USB-powered headphones and I had the same problem with them in "that operating system which must not be named".

---

### Post by manro on 2007-10-28
Hi!

I manage to resolve this issue following **[THIS]("http://forums.nvidia.com/index.php?showtopic=43715&st=0&p=265678&#entry265678")** link (the answer is in the last post)

Basically is very simple, just add the following line in /etc/modprobe.d/alsa-base

```
options snd-hda-intel model=laptop
```Hope it helps!

Regards,
MaNRo

---

### Post by marcantonio on 2007-10-29
Hey all,

I followed this [post]("http://ubuntuforums.org/showthread.php?p=3501600#post3501600") which is similar to MaNRo's above.  Interesting thing is that I didn't have to check off the missing option "headphone jack sense".

Marc

---

