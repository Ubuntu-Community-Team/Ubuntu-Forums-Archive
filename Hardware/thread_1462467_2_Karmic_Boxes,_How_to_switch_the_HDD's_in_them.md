---
title: "2 Karmic Boxes, How to switch the HDD's in them?"
date: 2010-04-25
forum: Hardware
---

### Post by Rasa1111 on 2010-04-25
Hey all,

 Im gonna throw this out there and see if I should even attempt it or not...:confused:

 I've two Ubuntu pc's, both with 9.10~
(both pcs are rather "old" next to most today) lol

my 'main PC' (Dell Dimension), which has 2.4GHz CPU, with 1 GB RAM~ and 40GB HDD

and my other, old PC (compaq presario) which has 1.8GHz CPU~ 512 RAM, and 100 GB HDD

I have external hard drives to use for storage and the like,

but I would really like to be able to have my 100GB HDD in my main PC...

  How much trouble would this be? 

  or a better question.... 

How much trouble would this be for a n00b who has only been using Ubuntu for 5 or 6 months? ... ( and who has never switched HDD's of two PC's?). lol  :confused:
  What steps would one take to do it properly? 

Would there be enough risk involved,
of killing something that i cant fix,
that i should just not even bother?  lol

 Thanks for your time, and any help you can provide. :KS

---

### Post by Mewshi on 2010-04-25
Don't quote me on this, but I think that, since Ubuntu does hardware detection at boot time (rather than being tied to the machine), you should be able to just swap out the drives.  This is, of course, barring anything you may have edited to differentiate it from the normal distro (such as installing ATI drivers which, last I checked, do still edit xorg.conf, which CAN be undone but can be a huge pain).

Also, you may be limited by the specs of the hard drives.  If one drive is SATA, and the other computer only accepts PATA, then you have a problem.  Barring any problems like that however...

Anyway, as to the actual procedure for the physical swap:
0)  Make sure the computer is fully off by switching off the switch in the back (or unplugging it from the wall).
1)  Remove the casing from both computers.  This varies from computer to computer, but generally, look for screws in the back of the case and remove them.  Slide the side of the case off.
2)  Locate the hard drives, disconnect the power and data cables, and remove the drives.  The drives should be toward the "front" of the computer (below or above the CD/DVD drive).  This process will either be very easy (just remove 4 screws holding in the drive) or moderately difficult (as is the case in certain machines with custom carriages for hard drive/CD drives.  If you run into a custom carriage (i.e., it won't just come out by removing screws) then post here and I'll do my best to help).
3)  Swap the drives (VERY carefully; avoid touching any of the circuitry), position them in the tower, and replace the screws.  Connect the power and data cables.  Replace the case.
4)  Boot computers.

If I'm right, then they should switch without a hitch.  Worst case, you have to unswap the drives so they're in the original computer again.  Again, be VERY careful inside the computer, and be SURE that you're properly grounded (either get a grounding bracelet and attach the clip to the tower or use the poor man's method of just holding the case with one hand).

If you follow these directions, there's minimal risk of anything going on; as long as you're properly grounded, the chances of frying anything are relatively slim, so I'd say it's worth it.

---

### Post by Rasa1111 on 2010-04-25
awesome! thank you Mewshi! :)

 i do know how to get into them and get the drives out , 
and the rest of your post is (surprising to me.... just what i wanted/needed to hear!) lol
I didnt think it would be so easy, though id hoped it might be. 

everything has been pretty easy so far so im not too surprised i guess, 
but i wasnt sure if disconnecting them and then reconnecting them would give me any 'beef'. lol

 so if it doesnt work for some reason,
just switch them back,  .. and they they should be working properly. 
good deal.. 

very helpful, :)
many thanks. 

i will get up the guts to give it a go, and report back when i do. lol :)
*deep bows*

---

### Post by conradin on 2010-04-25
Mewshi gives good advice. Just be sure to be grounded at all times. Either buy a grounding wrist strap or keep one hand on the metal part of the case at all times. 

Also be sure to properly shutdown you computer before working on it. 
Also, after unplugging the computers press the power button again, this will dissipate most of the residual stored voltages.

---

### Post by Rasa1111 on 2010-04-28
cool , thanks. :)

 well I did it..
 and it worked just as Mewshi said! :D

 very cool, thanks Mewshi! thanks conradin!

solved! lol :D

---

