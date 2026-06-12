---
title: "Webcam and mic wont work!"
date: 2008-10-18
forum: Hardware
---

### Post by egregory on 2008-10-18
Hi guys,

I am very new to Ubuntu, so pardon my ignorance, i am having problems using skype neither the web cam nor the mic work. 

I have a toshiba satellite A300-A300D, i have no idea what the make of my webcam is, i also tried the toshiba's site for latest drivers but there is very little for Linux/Ubuntu.

Can anyone help?

thanks

ed

---

### Post by Seti on 2008-10-18
see what ```
lsusb
```
tells you.
You should see something about your webcam's manufacturer there.
Try also:```
dmesg | grep webcam
``` ..
You should post the output back here and then we can help you better.
Also, as a rule you're not going to find linux drivers on your hardware maker's site. The drivers you want to be using are the ones already in the kernel.

---

### Post by egregory on 2008-10-18
Hello mate, thanks for a quick reply, as advised please see below.

edwardgregory@edwardgregory-laptop:~$ lsusb
Bus 007 Device 001: ID 0000:0000  
Bus 006 Device 002: ID 04f2:b008 Chicony Electronics Co., Ltd 
Bus 006 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000

---

### Post by rinishak on 2008-10-18
Hey, there. I don't really know much about hardware, but you can try checking out this thread. I think they may have found a solution:

[http://ubuntuforums.org/showthread.php?t=498571](http://ubuntuforums.org/showthread.php?t=498571)

Good luck.

---

### Post by egregory on 2008-10-26
no luck guys i am till having the webcam problem, to add insult to injury my keyboard short cuts dont work, i think it happened after i tried to install russian keys and it went tits up! any luck anyone? the webcam issue is an emergency now as my gf is giving me grief!! my webcam is chicony electronics, i have checked their website but there is nothing, i am very new to ubuntu and i need some TLC!!

---

### Post by egregory on 2008-10-26
Seti! where did you go mate? come back!! you started off so enthusiastically and then disappeared!!

---

### Post by egregory on 2008-10-26
ok i have managed to sort out the mic and webcam issue! Only the keyboard shortcuts remain!

---

### Post by rinishak on 2008-10-26
Is that a keyboard layout problem or what?

---

### Post by rinishak on 2008-10-26
I've read somewhere that Ubuntu assigns shortcuts to the keys symbols and not the keys code, so if you use a different input language your previous keyboard shortcut settings won't work, so it may only work with your previous input language.

---

### Post by 10ghost on 2009-04-08
sorry brother
am a victim of the webcam problem 
i read in one of your messages that you where able to solve it.
can you put me through because i am having the same problem and the maker of our webcam is the same
thanx for your anticipated cooperation

---

### Post by 10ghost on 2009-04-08
sorry brother
am a victim of the webcam problem
i read in one of your messages that you where able to solve it.
can you put me through because i am having the same problem and the maker of our webcam is the same
thanx for your anticipated cooperation

---

