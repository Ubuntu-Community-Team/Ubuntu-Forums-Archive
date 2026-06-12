---
title: "X Display not detected?"
date: 2005-06-11
forum: Hardware &amp; Laptops
---

### Post by Pancakes on 2005-06-11
Just got the newest version of Ubuntu, but when I tried installing it on my computer (specs down below) it seemed to be installing fine, but near the end when it prompted me to restart and load up, it didnt detect my display for some reason.. It gave me some sort of weird error message that I dont remember right now -sorry- Ill try getting it in full soon, I'm about to just try and installing it again, anything else I should know before I do this?

UPdate: 
It says that my X Server Interface cannot be started, It is likely that it is not set up correctly 

Thanks
- Pancakes

System Specs:
Intel Celeron 1.6
Geforce FX5500 PCI
Sound Blaster Audigy
640 mb ram

All in an emachines T1720 case

---

### Post by Pancakes on 2005-06-11
Apparently itll bring me to some sort of dos screen, it just wont load the gui, but still I dont know any commands whatsoever... Is there anything i can do from here?

---

### Post by voidlogic on 2005-06-11
yeah, from there you can use vi or vim to edit you X11 config file. If youre stuck, try changing your driver from whatever it is set as to 'vesa'. Since you don't feel comfortable at the shell prompt, being a graphical mode will make it easier for you to find out why your cards specific drivers are being flaky. When you have the actual error message, let us know, I'll try to help you.  ;-) 

voidlogic

P.S. If you need to figure out vi or vim, or the command prompt in general, there are many examples online  ;-) 
-----------------
someone HELP!
[http://www.ubuntuforums.org/showthread.php?p=202288#post202288](http://www.ubuntuforums.org/showthread.php?p=202288#post202288)
 ](*,)  ](*,)  ](*,)

---

### Post by Pancakes on 2005-06-11
Thanks, I checked again, and I noticed that it actually gives me three error messages: 

Cannot read V_BIOS
VBE initialization failed
Screen(s) found, but none have a usable configuration.

Anything else I should try?

---

### Post by Pancakes on 2005-06-11
Anyone have any idea?

---

