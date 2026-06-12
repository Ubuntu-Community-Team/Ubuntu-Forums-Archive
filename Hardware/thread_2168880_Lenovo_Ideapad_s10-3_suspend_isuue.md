---
title: "Lenovo Ideapad s10-3 suspend isuue"
date: 2013-08-19
forum: Hardware
---

### Post by anastas2 on 2013-08-19
[SIZE=3][FONT=arial narrow]Hi folks

Another newbie in the Ubuntu family( xubuntu 13.04 to be precise). To be sort I installed Xubuntu 13.04 on my netbook( ideapad s10-3). Everything works great except suspend!
When I close the lid it suspends normal ( one LED is blinking) but when I  open the lid I get black screen( the LEDs are on as it should- hard drive make "on" noise etc...). 
I guess it something to do with the video drivers :/ 

I really liked this distro and I want to keep it( no laggy at all) but suspend is something importand for me :/
Thanks in advance 
Anastas[/FONT][/SIZE]

---

### Post by Toz on 2013-08-19
Hello and welcome to the forums.

Can you try the following kernel boot parameters:

**nohpet**

or

**hpet=disable highres=off nohz=off**

or

**intel_idle.max_cstate=0**

See the "Kernel Boot Parameters" link in my signature for information on how. More info on what those kernel parameters mean can be found [here]("https://www.kernel.org/doc/Documentation/kernel-parameters.txt").

---

### Post by anastas2 on 2013-08-19
You are a star mate ;) second parameter make it suspend. What is the cause of this issue? 
Thanks again :)

---

### Post by Toz on 2013-08-19
Glad to hear. 

As I understand it, while in suspend mode, the hpet timer is mis-firing or missing cycles causing this to happen. A more detailed explanation can be found in [this bug report]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/871891").

Can you please mark this thread as solved using the Thread Tools link above? Thanks.
Edit: I see you have marked it as solved. Thanks.

---

### Post by anastas2 on 2013-08-20
Got it...Thanks again mate ;)

---

### Post by Mr Zero One on 2013-10-17
fantastico!! thanks

---

