---
title: "extra buttons on my mouse- yes I've read the other threads"
date: 2005-06-27
forum: Hardware &amp; Laptops
---

### Post by dancnpete on 2005-06-27
okay I have what I believe is a 7 button mouse based on the information I've read here. 1 left, 2 right, middle 3-4-5, and two more buttons 6-7.

I have no use for web functions on my mouse since I use mouse geustures instead. What would be really helpful is if I could get copy and paste functions on the mouse.
I thought I had it figured out by following the tutorials but apparently no go. 

this was my imwheelrc file code:

".*"
None,Up,ctrl_L|c
None,Down,Ctrl_L|v


and my 57xmodmap code

#/bin/bash
xmodmap -e "pointer = 1 2 3 4 5 6 7" --- Note: when I had 6 and 7 before 4 and 5 my scroll wheel acted like back and forward commands in firefox

---

