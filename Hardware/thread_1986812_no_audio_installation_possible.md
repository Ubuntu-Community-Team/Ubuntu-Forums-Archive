---
title: "no audio installation possible"
date: 2012-05-25
forum: Hardware
---

### Post by dorennee on 2012-05-25
Hi,

I have ubuntu 12.04 on a Lenovo W520 installed. I am glad everything is fine except the Sound: suddenly there wasn't any (I guess due to some update).
Here are some In- and Outputs:

```
 cat /proc/asond/cards 

--- no soundcards --- 
``````
 lspci | grep -i audio 

00:1b.0 Audio device: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller (rev 04)
01:00.1 Audio device: NVIDIA Corporation GF106 High Definition Audio Controller (rev a1)

```What can I do?

Greetings,
René

---

