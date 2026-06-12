---
title: "Long Heat sink fan fro Thinpad question"
date: 2010-02-14
forum: Hardware
---

### Post by skiphk on 2010-02-14
I replaced my motherboard on my T40 Thinkpad and it is now a T42. The board number is 93p4156. I have had a a history of motherboards going bad where the Raedon 7500 video chip fails... due to heat as I have been told. 
 
Can anyone comment on the effectiveness of the long heat sink fan (verses tghe standard short one) which covers the video chip? When installing is grease used for the processor chip required?
 
Skip

---

### Post by tgalati4 on 2010-02-14
The long fan is supposed to be better.  Yes, use heat sink paste.  Don't use too much, you want a THIN layer that is evenly spread.

Make sure the heat sink lays flat against the CPU and GPU.  Some machines require a copper shim because of the height differences between the CPU and GPU.  If you notice that the long fan heat sink doesn't sit flat, then look for some thin copper stock to make up the difference.

Thermal cycles in the GPU cause the small solder balls to crack and lose contact.  Anything that keeps the temperatures more consistent and lower than 70C is helpful.  Load tpfand and run tpfan-admin to set your fan speed trigger points.  You can fine tune your fan's behavior to keep the GPU at a constant temperature regardless of load.  

Because the CPU and GPU share one fan and heat sink, playing 3D games on it in Windows can really cook it.  The machines were designed for Excel and Word, not Open Arena and Neverball.  Although they handle 3d pretty well, my T43p heats up and gets weird after an hour of play, so beware.

---

### Post by skiphk on 2010-02-14
m

---

### Post by skiphk on 2010-02-14
Where can I get the loads (tpfand and run tpfan-admin) you refer too?

---

### Post by tgalati4 on 2010-02-15
What is the output of:

apt-cache search tpfan

---

