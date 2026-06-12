---
title: "can a mini-pci card be changed?"
date: 2007-06-12
forum: Hardware &amp; Laptops
---

### Post by friendly2004 on 2007-06-12
hi!

can i easily without any risks change the mini-pci card of my notebook?
it's a HP/Compaq nx6125 and runs a bcm4318-module.

i wan to start using airsnort, aircrack-ng, ... 

the best would be a card with an atheros chip.

i'd like to buy one and build it in.

but i'm not sure whether this is such a good idea and if it works (possible bios probs?? mainboard won't accept it??)

so..
are there any risks? what do you recommend? or are there even alternatives that enable me to have the monitor with that module and the ndiswrapper?

cheers!

---

### Post by stchman on 2007-06-12
> **friendly2004 said:**
> hi!

can i easily without any risks change the mini-pci card of my notebook?
it's a HP/Compaq nx6125 and runs a bcm4318-module.

i wan to start using airsnort, aircrack-ng, ... 

the best would be a card with an atheros chip.

i'd like to buy one and build it in.

but i'm not sure whether this is such a good idea and if it works (possible bios probs?? mainboard won't accept it??)

so..
are there any risks? what do you recommend? or are there even alternatives that enable me to have the monitor with that module and the ndiswrapper?

cheers!

As long as the card fits, uses the same antenna connectors and uses the same bus it should work.

---

### Post by friendly2004 on 2007-06-13
hm..

but should is not a definitive "yes"..

how can i check the bus?

what else might make it not work?

i want to play safe..

---

### Post by stchman on 2007-06-13
> **friendly2004 said:**
> hm..

but should is not a definitive "yes"..

how can i check the bus?

what else might make it not work?

i want to play safe..

The laptop is not going to explode.  It is like this.  If you have a Turtle Beach PCI sound card you can remove that card and install an Audigy 2 sound card.

As long as the interface is the same and there is room for the card then you are fine.

---

### Post by friendly2004 on 2007-06-13
lol, glad 2 hear my notebook not gna xplode ;-)

don't wanna change a sound card but a wifi card/module... and don't want 2 buy one which won't work then.

---

### Post by moosesoom on 2007-06-14
Be careful,
I know some HP model had BIOS limitations to use only certain wifi cards (think the HP branded ones).

The safest way is to try some no-HP card.
I quote the no-explosion statement :)

---

### Post by CrazyGuy123 on 2007-06-14
I've never had any trouble changing a wifi card.  To play it safe follow the usual rules - eg. don't spill cofee in the minipci slot...  If it's for use with ubuntu, check drivers exist for the new one youre buying.  Changing the card is fairly easy in most systems.  Some you can change without undoing any screws.

I personally have an nx6125, and I can say changing the card is easy, but I havn't changed it for anything, just took it out to see what was in there.

If by some wierd coincidence it doesn't work, you can always send the card back as faulty (since there is nore chance of it being dead out of the box than a compaibility issue I'd say) , but I doubt very much that would be the case.

---

### Post by friendly2004 on 2007-06-15
thx, 4 all ur comments.

in the computer my bro uses is a mini-pci card built in- by prism.

here things like airsnort etc. work and it doesn't break down...

i think i'll change that first to see whether it works. if my bro's not gna experience probs with my one i'll keep his and he got to keep my..

will inform you about the result.

only thing that i now must have a look at is how to open my notebook ;)

---

### Post by Dan Still on 2007-06-15
Having inly installed MiniPCi cards and not having an HP I can say even from a beginners stand-point (which I am) that the process is simple and painless. 
A simple matter of popping off the keyboard and turning a few screws to expose the board in my case. From there the greatest difficulty was setting the antenna wires to the card itself without crushing it with my super human strength. :p If you already have a card in place, I find it hard to believe that changing it will have any UNdesired effects.

Noobie Dan Still LOVES THIS OS
Clevo 5600DS (AKA Alienware)
Ubuntu 7.04 SE

---

### Post by whayong on 2007-06-15
My experience with changing mPCI cards leads me to believe it is an easy job, not because of the number I've done but because it's a straight forward process.  Best way I can describe it is, if you can change/upgrade your RAM in your laptop then this is something you can definitely do.  The only difference is there will be more diassemble involved (depending on the laptop model).  I've replaced many, although I'm not to familiar with the BIOS that HP uses and it's limitations.  

If I can suggest one thing, DO NOT FORGET TO DISCHARGE ALL STATIC YOUR BODY IS STORING.  Do it a few times too, unless you're wearing an anti static strap, discharge often, you'll regret it that one time it fries everything. lol!

---

### Post by chili555 on 2007-06-17
Please check here: [http://www.dagarlas.org/stuff/computing/article0001.php](http://www.dagarlas.org/stuff/computing/article0001.php)

This is your exact laptop. You can install the card easily, but it will not run. > With my great surprise and a little bit of anger I read: "Error 104 - Unsupported network device..."The fix he describes is a bit complex.

---

### Post by koffiejunkie on 2007-10-30
> **friendly2004 said:**
> hi!

can i easily without any risks change the mini-pci card of my notebook?

No, you can't.  I have the nx6125 high-end model (with the 1400x1050 screen).  The first thing I did was looking on HP's website to see if there are any Intel cards available.  Found one that was listsed as compatible with this particular notebook.  Paid about three times as much for it as it should cost (thanks to that HP logo).  Got the error described in another post.   I also have an Atheros mini-PCI card which gave the same result.

This HP's BIOs has all sorts of booby traps.  The wireless is one.  Another one is the hard disc.  Mine failed, and I had a Hitaschi drive handy.  Put it in, and to my great surprise and disappointment, I could not make it switch on DMA.  Installing linux took hours.  Installing windows took more hours.  It was unusably slow.

That very same Hitaschi disc is still running 100% in an older notebook.    Earlier this year I bought a 100GB 7200rpm Seagate disc for my Mac Mini.  Before putting it in, I decided to try it in the HP, just for kicks.  It worked! So the 120GB 5400rpm Seagate disc that came out of the Mini is now in the HP, and works just fine.  The Hitaschi still doesn't.  So I guess the BIOS just checks to see if it's a Seagate disc (the original is a Seagate), and plays nasty if it isn't.

It's a pity that did such horrible things to such a great notebook.

---

