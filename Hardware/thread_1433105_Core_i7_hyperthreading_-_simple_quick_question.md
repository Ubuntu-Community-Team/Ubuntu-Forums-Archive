---
title: "Core i7 hyperthreading - simple quick question"
date: 2010-03-18
forum: Hardware
---

### Post by slockton on 2010-03-18
Hello,

I have a machine running 9.10 64-bit with the 2.6.31-14-generic kernel. I built it myself, choosing a Core i7 CPU. When I first configured the BIOS I turned hyperthreading off.

I'd now like to turn it back on. Will Ubuntu complain or crash? Is there anything I have to configure before it will work? Or is it just a case of going into the BIOS and selecting "hyperthreading on" and letting the OS figure it out?

Thanks!

S

---

### Post by TitanusEramius on 2010-03-18
I would definitely just turn it on and see how Ubuntu reacts :p
Worst case scenario is you have to reboot and turn it off again

Please post the results btw

---

### Post by slockton on 2010-03-18
Thanks for the reply,

It's a server in a lab, so I don't have that much opportunity to turn it off. It's under a pretty heavy load right now, and I thought hyperthreading might help the multiple jobs that end up running for days at a time.

S

---

### Post by TitanusEramius on 2010-03-18
Oh, thats pretty cool :p

After a little reading in the forums it's seems like hyper-threading not always is available in Ubuntu. I found several reported bugs where people couldn't turn HT on, but none of them was harmful to the system, so you should be safe in trying it, but it might not work. 

Apparently only time will show ;)

---

