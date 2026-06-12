---
title: "Desktop does not load Ubuntu automatically but loads windows well"
date: 2010-10-07
forum: Hardware
---

### Post by tatsat on 2010-10-07
Hi,
 Please excuse me if there is something wrong about me posting my query in this section. 

My problem- I have Windows 7 and Ubuntu 10.04 running on my desktop but there is a strange problem that i am facing since the first day I got Ubuntu on the system. Whenever I try to log on to Ubuntu from the grub list, it goes blank for 15 seconds and restarts- just like that. If ,however, Windows is chosen, it loads normally. Now comes the *tricky part* :- If I take out my mouse after powering on the computer and plug it back in before selecting Ubuntu from the grub, it loads normally after the blank screen. 

I do not think there is some hardware issues as such because windows loads up with ease and Ubuntu once loaded, runs well. What is bugging me that I have to plug out and plug in mouse everytime I want to load Ubuntu and I primarily use Ubuntu.

Kindly suggest something ... 

TIA

---

### Post by quixote on 2010-10-09
It sounds like there might be some sort of driver conflict, but a) I'm not sure how to troubleshoot that, and b) let's start with the simple stuff.  Maybe grub just has a glitch. Open a Terminal (Application > Accessories > Terminal), and at the prompt type```
sudo update-grub
```It will ask for your password and then re-setup grub.  Be nice if that was all it needed. :D

---

