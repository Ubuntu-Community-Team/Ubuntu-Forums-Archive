---
title: "Msi S262"
date: 2007-05-28
forum: Hardware &amp; Laptops
---

### Post by Gelu on 2007-05-28
I tried as I bought it with Kubuntu 6, and everything worked fine and detected all devices and hardware. Now I tried with Ubuntu 7, and it did not detect everything. How is that possible?

---

### Post by FerhatBingol on 2007-05-28
Can it be Kernel? Because they are different. 

What is your Kernel?

---

### Post by Gelu on 2007-05-29
> **FerhatBingol said:**
> Can it be Kernel? Because they are different. 

What is your Kernel?

What do you mean with "what is my kernel?" :confused:

---

### Post by FerhatBingol on 2007-05-29
try the command

```
uname -a
```

It should tell you what is your kernel... like below reply...

ferhat@lp:~$ uname -a
Linux lp-10894 2.6.20-15-generic #2 SMP Sun Apr 15 07:36:31 UTC 2007 i686 GNU/Linux

I bet you will come back with something saying it is i586

---

### Post by Gelu on 2007-06-01
Yeah. Your right....it's something i586. What can I do in this chase? :idea:
*Shall I grab the whole kernel name for you?

---

### Post by FerhatBingol on 2007-06-01
I think you should upgrade.

Try to use synaptic package manager. 

serach for kernel and the latest one is 2.6.20-16-generic, works fine with me. But it is new. 

If you want to secure yourself with a previous version try 2.6.20-15-generic and use i686...

---

### Post by Gelu on 2007-06-02
> **FerhatBingol said:**
> I think you should upgrade.

Try to use synaptic package manager. 

serach for kernel and the latest one is 2.6.20-16-generic, works fine with me. But it is new. 

If you want to secure yourself with a previous version try 2.6.20-15-generic and use i686...

Okay, I will go with that. But it's anyway funny, because I used Ubuntu free shipit service, and send me Ubuntu 7, one for 64bit and two for for 32bit pc. Well I tried just one, but is it possible that the other one is the i686 version?

---

