---
title: "Laptop crashes during memtest86 @ 30%, every time"
date: 2010-11-21
forum: Hardware
---

### Post by ming0 on 2010-11-21
I have 8 gigs of dual channel RAM (2x4gb). I have been getting a lot of crashes (computer shuts down abruptly -- often flashes shutdown screen as it's shutting down), especially when encoding video or running a virtual machine w/ windows.

I just tried running memtest86 with both sticks, and then each stick singly, then a single stick in an opposite RAM slot--memtest fails at around 30% every time and the computer just abruptly turns off.

It's a thinkpad T410s with an intel I5 processor.

I'm wondering if this is memory itself (I could see both sticks failing at same time, because it's dual channel and maybe has an identical error, tho this is totally a guess) OR possibly the memory controller or something else on the mobo.

---

### Post by squaregoldfish on 2010-11-21
My guess would be a dud motherboard. The only way to be sure though is to try some different RAM in it. Or try your RAM in a different motherboard.

Of course, if you don't have the alternative hardware, you're kind of stumped...

Steve.

---

### Post by ming0 on 2010-11-21
Hmmm that's what I was thinking (but hoping wasn't the case). I don't have alt hardware, so I guess I'll start w/ the RAM since it's easier to send back. Oh, actually maybe I have an original stick that I can test... I upgraded to the 8gb.

Thanks for the advice.

---

### Post by ming0 on 2010-12-01
This has gotten strange -- I just pulled 2 sticks of ram out of my old macbook pro and slotted one into the lenovo, ran memtest86 and it ran through 3 times without failing. So I figured it was my mushkin ram that was bad and got it wrapped up to send back, leaving the macbook ram in the lenovo.

Out of curiosity, I ran the video compression software that had been reliably crashing my machine and after 10 minutes it crashed again. I noticed that it didn't just crash instantly -- I saw the ubuntu shutdown screen go on just as it turned the computer off (thought I may have seen that before, but figured I was imagining it).

So then I tried memtesting the mac memory again and it failed at 30%. Now that there seems to be some inconsistency I can't tell if it's a defect the motherboard or maybe just a bug in the i-5 processor or something. 

Also, the fact that the video compression crash usually happens around the same time and actually goes through the shutdown screen is totally puzzling to me. Not sure what to do :|

---

### Post by squaregoldfish on 2010-12-01
I'm going to go with the motherboard being faulty. Two lots of RAM have been found to be bad at the same point, which indicates a likely dodgy pin in your RAM slot or similar.

It could be that your motherboard is actively killing the RAM :eek:

Steve.

---

