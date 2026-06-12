---
title: "White screen after boot"
date: 2008-11-03
forum: Hardware
---

### Post by RADHAD on 2008-11-03
Hi foks 

i am new to the forum i search for a topic that can help me white this problemem .

i get a White screen after boot Ubuntu 8.10. Screen is freezing and white. 

can somebody help me  ?

hardware specs : 

Abit ip35 pro

Ati 4780 (1gb memory)

3Gb cross air memory

no raid config 

intel 8400 core

Sorry for my bad English

---

### Post by the lush on 2008-11-03
Yet another case of ATI problems. There are a lot of posts on this topic, most reference a black or blank screen, but as far as I can tell the problem is the same, only the display's response to a lack of signal is different.

If you can get to a command line, you can try to remove Compiz, this should give you a workable system, but none of the visual effects that are so popular. 

If not, you can re-install 8.04. The same applies if you want the Compiz effects, re-install 8.04.

Was 8.10 ever tested on ATI hardware? No idea.

---

### Post by skidaddy on 2008-11-04
could be that x server is using a video format that isnt compatible with your screen.  if you can get a terminal up then use

Xorg -configure

that should help get it working.

---

### Post by RADHAD on 2008-11-04
> **skidaddy said:**
> could be that x server is using a video format that isnt compatible with your screen.  if you can get a terminal up then use

Xorg -configure

that should help get it working.

How can i get the terminal screen ? 

sorry i am a newbie to the linux

---

