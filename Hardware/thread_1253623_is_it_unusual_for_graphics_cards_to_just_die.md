---
title: "is it unusual for graphics cards to just die?"
date: 2009-08-30
forum: Hardware
---

### Post by badperson on 2009-08-30
I have an amd dual core machine that  a friend built for me a couple of years ago. I have ubuntu server installed on it, I've been using it to get some experience with servers in general. 

I've been unable to get any monitor output on it...I had two machines hooked together with a kvm switch; I tried hooking the suspect machine to the monitor; nothing...I tried using a a VGA/whatever adapter that I knew worked...nothing. 

I suppose I can just get a new graphics card...I figure that's the problem, but wanted to run it by here to see if anyone else had had a similar issue. 
bp

---

### Post by darco on 2009-08-30
Card specs please...
Also a bios setting maybe using the onboard video rather than the card itself...

darco

---

### Post by badperson on 2009-08-30
Sorry, I don't have any of the docs for the card...I think it's some kind of Nvidia...the mobo is asus a8n-e...there is no logo on the card itself. 

The reason I'm pretty sure it's the card is that those inputs used to work, and I ruled out all the cables/adapters/connections, etc...and I was plugging the monitor into one of the inputs on the card and it used to work...

thanks, 
bp

---

### Post by darco on 2009-08-30
run lspci in the terminal....

can you try a different card and see what the result is?
darco

---

### Post by badperson on 2009-08-30
Hi,
I can't run lspci because I don't have any monitor output at all...I don't see any onboard graphics on the mobo...

going to buy a new graphics card adn see if it works. 
bp

---

### Post by PatrickVogeli on 2009-08-30
Yes, it can. Actually most of electronic equipment which breaks, does it that way: one day works, the next it won't. That's my experience.

---

### Post by tgalati4 on 2009-08-30
GPU's run hotter and sometimes the heat paste wears out or the heat sink slips off of the GPU.  That will kill it quickly.  Also the boards that the GPU sit on wear out because of the excessive heat.  The heat warps the board and breaks the connections--no video.

---

### Post by badperson on 2009-09-02
got a cheap graphics card...that did the trick. 
bp

---

### Post by linux_tech on 2009-09-02
Glad to hear your graphics are working again

---

