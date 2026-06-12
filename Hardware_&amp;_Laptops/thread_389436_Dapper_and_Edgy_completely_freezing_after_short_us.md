---
title: "Dapper and Edgy completely freezing after short use"
date: 2007-03-20
forum: Hardware &amp; Laptops
---

### Post by Lightspeed on 2007-03-20
Hi. I really, *really* want to install Ubuntu on my home PC. But at the moment I'm not having much luck. I'm currently using the LiveCD of Edgy, although I was experiencing the same problems with the Dapper LiveCD, too. I can successfully boot into Ubuntu with no issues, and go ahead and browse the web, open OpenOffice or whatever.

Anywhere between five to twenty minutes into the session, Ubuntu absolutely, completely, utterly freezes. The mouse cursor and keyboard refuse to respond, and the clock is frozen too so it's not just them. Also, the CD drive stops spinning quite suddenly. (Using my second CD drive makes no difference, so it's not that.)

I tried using Ctrl+Alt+Backspace which I believe is the interrupt combination (?) but no luck. (I tried others for good measure!)

The LiveCD itself checks out okay. I don't have the nerve to actually attempt installing the thing, until I've found some kind of solution. (I suspect Ubuntu would crash mid-install anyway.)

System specs:
[LIST]
[*]Motherboard: **ASUS P4C800-E Deluxe**
[*]Processor: **Intel Pentium 4, 3.20GHz**
[*]Memory: **512MB**
[*]Video card: **ATI Radeon 9700 PRO**
[/LIST]

Looking about myself, I can find horror stories from people using my motherboard. But none that match the symptoms I've experienced. And it's not like the board itself is faulty - it runs Windows XP flawlessly.

I can give more information if you want it -- but I'm really not sure where to start. The bug is reproducible in the fact that it happens every single time I try to use the OS, but not reproducible in the sense that I have no way of predicting when it'll happen.

Help wanted! :?

(p.s. I'll try a Feisty LiveCD later on today, when I have got the whole CD image, but I wanted to know if you guys had any leads.)

---

### Post by ciscosurfer on 2007-03-20
> **Lightspeed said:**
> Hi. I really, *really* want to install Ubuntu on my home PC. But at the moment I'm not having much luck. I'm currently using the LiveCD of Edgy, although I was experiencing the same problems with the Dapper LiveCD, too. I can successfully boot into Ubuntu with no issues, and go ahead and browse the web, open OpenOffice or whatever.

Anywhere between five to twenty minutes into the session, Ubuntu absolutely, completely, utterly freezes. The mouse cursor and keyboard refuse to respond, and the clock is frozen too so it's not just them. Also, the CD drive stops spinning quite suddenly. (Using my second CD drive makes no difference, so it's not that.)

I tried using Ctrl+Alt+Backspace which I believe is the interrupt combination (?) but no luck. (I tried others for good measure!)

The LiveCD itself checks out okay. I don't have the nerve to actually attempt installing the thing, until I've found some kind of solution. (I suspect Ubuntu would crash mid-install anyway.)

System specs:[LIST]
[*]Motherboard: **ASUS P4C800-E Deluxe**
[*]Processor: **Intel Pentium 4, 3.20GHz**
[*]Memory: **512MB**
[*]Video card: **ATI Radeon 9700 PRO**[/LIST]
Looking about myself, I can find horror stories from people using my motherboard. But none that match the symptoms I've experienced. And it's not like the board itself is faulty - it runs Windows XP flawlessly.

I can give more information if you want it -- but I'm really not sure where to start. The bug is reproducible in the fact that it happens every single time I try to use the OS, but not reproducible in the sense that I have no way of predicting when it'll happen.

Help wanted! :?

(p.s. I'll try a Feisty LiveCD later on today, when I have got the whole CD image, but I wanted to know if you guys had any leads.)So this freeze up never occurs when you run XP?  It still sounds to me like a motherboard issue / incompatability issue.  You might also want to check to make sure you haven't blown any capacitors on the board (open up the case and inspect the mobo if you can -- if you don't know how to do this, ask someone with more experience to have a look for you).  Another thought on your issue: you may be having power supply issues.  Also, how old is the computer?  And you might want to consider adding some additional memory (though I can't see why the amount you have currently would be affecting your computer in a negative way).

---

### Post by mojobromley on 2007-03-20
Being my first post, I can say its your video card!
I had same issue with my 9700 ATI.
Fooled around with the driver and it stopped but can't get any games to run.

Running fine on an old overclocked system though! 
Dave

Your motherboard is a solid one, still have a lot of systems I've built running strong on that board!

---

### Post by Devius on 2007-03-21
I have completely different hardware but also had that problem. After some research I found that in my case addind the "nolapic" parameter at boot solved the issue. To type it in you just press F6 when the boot process shows the initial ubuntu boot menu and add it to the end of the line before the "--". There are also some other boot parameters that solved this issue to others, like "acpi=off", "noapic" or "pci=bios" if I remember correctly.

---

