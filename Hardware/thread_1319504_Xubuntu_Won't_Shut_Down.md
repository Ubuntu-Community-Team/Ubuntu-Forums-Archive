---
title: "Xubuntu Won't Shut Down"
date: 2009-11-08
forum: Hardware
---

### Post by Agurken on 2009-11-08
Hi, im new in this forum.

If my english, not always is correct, im sorry :roll:

My problem is, when i wanna shut down my old laptop, which i just installed xubuntu on, it won't completly shut down.

When i try i can do 2 things.

1: Go to a black screen, and write:
```
(Some lines i don't remember)
Niclas-Laptop login: 
```And just stand there, till it write something about 120 seconds, and then it just stand there again untill the 120 seconds come again, and so on. Untill i push the start buttom to shut it down.

2: Again go to a black screen, and write:
```
* Asking all remaining processes to terminate...
* Deconfiguring network interfaces...
* Deactivating swap...
* Will now halt
```But it won't halt, just stand there again.

It do's either one of those, no matter if i just shut it down normally or enter either one of these in console:
```
sudo nohup shutdown -h now
sudo shutdown -h now
sudo shutdown -P now
```I have xubuntu 9.10

Hope you can help me :D

---

### Post by Ganymedes on 2009-11-08
I have seemingly the same problem with Ubuntu 9.10 64-bit (I have had a tread open since yesterday).

In my case, the next boot takes a long time, perhaps (I am not certain, because I have never seen the normal situation with this newly installed 9.10) because I need to turn off the power from the computer while Ubuntu is still running. Is this your case as well?

---

### Post by Agurken on 2009-11-08
Well i can't say if its a slow boot or not, because i haven't had a real boot, without using the power button to turn off the pc.

---

### Post by Ganymedes on 2009-11-09
> **Agurken said:**
> Well i can't say if its a slow boot or not, because i haven't had a real boot, without using the power button to turn off the pc.

Same here, but I can compare to other computers with previous versions. If your computer is relatively fast:
- login time under 10 s (not MINUTES)
- boot time until login screen 30 s (not MINUTES), if there is no disk checking going on

---

