---
title: "intel 2200bg wireless card won't work."
date: 2009-08-30
forum: Hardware
---

### Post by gopaldawg on 2009-08-30
I am a complete newbie with ubuntu. i just installed it on my Sharp M4000 laptop and so far everything works except my wireless card doesnt get recognized and it is a intel 2200bg. what can i do to resolve this issue?

---

### Post by mikewhatever on 2009-08-30
Can you elaborate on why you think the wireless isn't recognized. What happens exactly when trying to connect?

---

### Post by gopaldawg on 2009-08-30
I don't think ubuntu recognizes the card. I always see the red x next to the grayed out bars that indicate signal strength. THen, when i right click that area, i see wireless is grayed out. So I think its mainly just a driver problem, but i dont know how to solve it.

---

### Post by lswb on 2009-08-30
The most common problem I have seen with the ipw2200 card is simply that it is not turned on. (dmesg or /var/syslog will often refer to a Kill Switch) 

Different laptops have different ways to turn on/off wireless. Some have a dedicated button, others use a Fn key combination. Does your laptop have something like that? 

There are also some load-time parameters that occasionally can be used to fix certain problems on particular systems.

---

### Post by lswb on 2009-08-30
A little googling told me that the Sharp M4000 uses Fn-F1 to toggle wireless on/off.

---

### Post by gopaldawg on 2009-08-30
Oh Wow... that worked! lol. Thank you SO MUCH. i cant believe i didn't think of that. I spent hours looking for other solutions. Thanks again!!!

---

### Post by mikewhatever on 2009-08-30
> **lswb said:**
> A little googling told me that the Sharp M4000 uses Fn-F1 to toggle wireless on/off.

Well done.

---

