---
title: "Not even seeing BIOS when computer boots"
date: 2011-01-22
forum: Hardware
---

### Post by Amablue on 2011-01-22
About a week or two ago I was playing Minecraft on my Ubuntu desktop when the screen went black and I couldn't do anything, so I reboot. This had happened in the past. Googling around a bit it turned out this was a known issue under certain conditions. 

Anyway, after I rebooted I saw nothing on my screen. Not even a BIOS screen. At this point it looks like some piece of hardware is just broken. (I'm not sure that Minecraft's bug caused this, but I included that part of the story just in case). I have two monitors plugged into an Nvidia graphics card, so my first step was to see if the graphics card died. I tried swapping it out with the card from another computer, but no dice. I also tried plugging a monitor directly into the 15-pin monitor out instead of one of the DVI outs on the graphics car. Still nothing. 

So it looks like the graphics card is not the problem. My next suspect is either the motherboard or the CPU. Is there anything I can do to figure out which one is the culprit? Or is there something I'm overlooking?

If I do end up replacing one or the other, will I have to do anything to my Ubuntu set up to get it back up and running again?

If you guys need any more information on any of my hardware just ask. It's all under a year old.

---

### Post by htmlland on 2011-01-22
Does your computer make any unusual beeps when it first powers on? Most motherboards have a beep pattern associated with a certain erro (e.g. [http://www.helpwithpcs.com/upgrading/post-beep-codes.htm](http://www.helpwithpcs.com/upgrading/post-beep-codes.htm)) if you just get the normal 1 beep then it could be something else im afraid but that would be beond me :(. On a side note if your hardrive was swapped out into any other computer (with your hardrive being the only one in the computer or say you bought a new motherboard etc.. ) ubuntu would boot just like normal.

---

### Post by Amablue on 2011-01-23
There are no interesting sounds coming from my computer when I turn it on. Does that mean it's safe to say the CPU has gone bad?

---

### Post by eentonig on 2011-01-23
Or your PSU unit as gone to pieces.

---

### Post by dandnsmith on 2011-01-23
With a bad CPU, there should be beeps.
With a failed motherboard you won't get any(or with failed PSU).

---

### Post by Amablue on 2011-01-23
So then my motherboard or PSU... is there a way to tell which is shot?

Edit: also, I should point out that my motherboard doesn't beep at all. I have an ASUS motherboard (and since I can't see the screen I don't know what BIOS version) but I think no beeps is the default? It's hard to tell since I don't know what error code list I should be reading, but I don't see any mention of no beeps on them.

---

### Post by dandnsmith on 2011-01-24
> **Amablue said:**
> So then my motherboard or PSU... is there a way to tell which is shot?

Edit: also, I should point out that my motherboard doesn't beep at all. I have an ASUS motherboard (and since I can't see the screen I don't know what BIOS version) but I think no beeps is the default? It's hard to tell since I don't know what error code list I should be reading, but I don't see any mention of no beeps on them.

Best I can suggest is to meter the outputs of the PSU, but you might have to short a couple of pins to get it active.

I've a couple of ASUS boards which either beep or can give a verbal message (no beep or message would be no problem)
[here](http://www.bioscentral.com/beepcodes/awardbeep.htm) is a list of the beeps.

---

