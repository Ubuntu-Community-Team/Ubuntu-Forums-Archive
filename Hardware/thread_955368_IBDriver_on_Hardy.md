---
title: "IBDriver on Hardy"
date: 2008-10-22
forum: Hardware
---

### Post by joe180 on 2008-10-22
Hi

I hope someone can help me out, i have PCMCIA iburst card which I tying to get to work on my Ubuntu hardy laptop. 

I have followed most of the readme's found on google. The driver compile works fine. 

Just when I insert the card I get:

cs: pcmcia_socket0: time out after reset

Which is pretty cryptic.

Please can someone tell me thet hell that means.

Ryan

---

### Post by joe180 on 2008-10-23
Anybody ?

---

### Post by joe180 on 2008-10-24
Hi 

I have solved the issue with some help from the guys at IBDRIVER. Also not I think this is for Hardy Only. As i have not used the the others.

see original post here; 

[https://sourceforge.net/forum/forum.php](https://sourceforge.net/forum/forum.php)

Ok quick fix is the following:

add below to "/etc/modprobe.d/options"

```
options pcmcia_core unreset_check=20 unreset_delay=100 unreset_limit=100
```

Joe

---

