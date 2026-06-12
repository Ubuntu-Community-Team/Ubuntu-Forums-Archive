---
title: "Running out of memory and crashing :("
date: 2008-11-22
forum: General Help
---

### Post by fiddler616 on 2008-11-22
Hello,
Twice so far, I've been doing normal things on my computer--browsing the internet, coding, etc. Nothing too system intensive, when suddenly my processor goes crazy, and nothing moves. Not even the mouse. The first time, I pressed Ctrl-Alt-F1 to get a tty to reboot off of, and after a *long* time, I managed to log in, and then it said something along the lines of how I didn't have enough memory ( I have 512MB of RAM, and ~512MB of swap, so I don't know what to think about that!) I ended up hardbooting. This happened again this morning, but I couldn't even get the tty up (and Ctrl-Alt-Backspace was useless too) so I hardbooted. This can't be healthy, and I'm very sorry to see the dependable, reliable, solid Ubuntu having these BSOD-like moments. Is there anything I can do?
Thank you very much.

---

### Post by oldos2er on 2008-11-22
Run memtest overnight to check the health of your RAM.

---

### Post by Kain000 on 2008-11-22
sounds like a problem I have experenced from time to time.... I've only had this happen on my laptop, is yours a desktop or laptop?   


anyway  when it happens to me under the terminal I type
```
top
```

this will give you a system monitor view of what processes are takeing place and using what resources.... without using that much more (like system monitor does)    

in addition it also lists your ROOT processes running. 
Each time this problem has been caused by some process called somthing like kapid or somehing like that, using two processes always # 50 and 51 and using together 100% of the processer.

once I kill those two things go back to normal w/o any trouble.   
use top and see what's hogging your RAM and CPU and you may want to google search before you go killing off any processes but see if doing so helps.

---

### Post by fiddler616 on 2008-11-22
Thanks to both of you, but:
My system was kind of falling apart at the seams--so I just reinstalled (I had a separate /home partition)
I couldn't run any commands in the terminal or anything--it was completely jammed up. Otherwise I just would've run 'halt'

---

