---
title: "Spontaneous reboots"
date: 2009-11-30
forum: Hardware
---

### Post by alex341 on 2009-11-30
I installed Mythbuntu 9.10, using the image from mythbuntu.org, as a front- & backend systemon. My motherboard is a Via Epia EX10000EG, with C7 processor an CX700M2 chipset. I use a Haupauge PVR 500 dual tuner card.
 
I get spontaneous reboots. Sometimes the system shows live tv, sometimes I can playback a recording, but often (usualy when I start using the tuner card, but not always) the system spontaneous reboots.
 
On the Myth Wiki description of the Hauppauge PVR 500, under the chapter Common Problems And Solutions I found: 
**Spontaneous Reboots **

Do *not* attempt to enable pre-emptive kernel locks in your kernel configuration--the ivtv modules do not get along with them and will cause *spontaneous reboots*. 
 
I am just a Linux beginner. What does "pre-emtive kernel locks" mean, how do I check for them and how do I disable them if they are enabled? Since I installed the "standard" version of Mythbuntu and the Mythbuntu version supports the Hauppauge card, I don't expect this to be the problem, but you never know... If not, what else could it be?

---

### Post by alex341 on 2009-12-15
Since my previous message, I've build a new kernel with Pre-emptive kernel locks disabled, but my spontaneous reboots remain. 
 
Who can help me?
 
As said:
Motherboard: Via Epia EX10000EG, 1 Gb, C7 processor an CX700M2 chipset
TV Tunercard: Hauppauge PRV 500

---

### Post by alex341 on 2009-12-29
Tnx to Jeroen Roos the reboots are over...

---

