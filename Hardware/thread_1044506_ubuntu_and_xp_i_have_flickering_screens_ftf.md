---
title: "ubuntu and xp i have flickering screens ftf"
date: 2009-01-19
forum: Hardware
---

### Post by erdal123 on 2009-01-19
i have this problem when i open I.E and scroll down a page with letters or pictures it flickers 

in ubuntu video files flickers and webbrowser too

I NOTICED WHEN CANCELLING VIDEOEFFECT IN UBUNTU THIS PROBLEM DISSAPEARS but i want to cure it not dodge it 

its so annoying because i dont know the cause

my speculation is: direct X or java 
but i tried everything to fix it (reinstalled and all the stuff)

i will be happy if some of you guys give me helpful feedback

--
some symptoms:

*it happens in standard ubuntu player IF i shut grapiceffect down, it doesnt flicker anymore

*this flickering happens in I.E in windows WITH TEXT AND PICTURES

*this flickering happens in FIREFOX in ubuntu WITH YOUTUBE VIDEOS
in firefox text and pictures doesnt flicker!

---

### Post by cariboo on 2009-01-19
I would suggest it is a driver problem in both Windows and Ubuntu. If you are using the default drivers in both OS's you will get the problems you are describing. Could paste the output in your next post:

```
sudo lshw -C video
```

THe above command must be run in a Applications-->Accessories-->Terminal.

Jim

---

