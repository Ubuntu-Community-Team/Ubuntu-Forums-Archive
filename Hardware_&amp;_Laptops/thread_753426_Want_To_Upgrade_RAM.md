---
title: "Want To Upgrade RAM"
date: 2008-04-12
forum: Hardware &amp; Laptops
---

### Post by Literati on 2008-04-12
Hi all.
I'm trying to make my computer run as fast as I possibly can for a reasonable amount of money.

RIght now, I have a 2.4Ghz P4 with a P4P800 mobo, and only 512 MB of RAM.

Now, I notice that in my system monitor, my CPU is getting used way more than I feel it should for what I'm doing (Browsing, listening to music, messaging etc) and think that upgrading the ram should help.

My questions are:

Is there a limit as to how much RAM Ubuntu would even recognize (Like 3.4 I believe on XP)?

What is a good BRAND of RAM, or does it really matter?

My mobo can support 4GB of RAM (1 GB in a slot) It's made for PC-2700, but I heard it doesn't exactly matter, and can accept PC-3200 is that right? It can accept a max of a 400mHz stick.

Do you guys know of any good sticks or a place to buy them? 
How good is it to buy from eBay? (I'm comfortable with eBay as a whole, just, is there a lot of scamming on RAM sticks?)

Thanks in advance!

---

### Post by tamoneya on 2008-04-12
the default 32 bit kernel of ubuntu al;so has the 3.4 GB restriction on it but i see no reason to go that high.  As for speed of the RAM it makes no sense to buy faster than your motherboard supports because it will just be more expensive.  
I would stay away from ebay since it is so susceptible to scamming.  I would get it from newegg.  Here is what I would get [http://www.newegg.com/Product/Product.aspx?Item=N82E16820141429](http://www.newegg.com/Product/Product.aspx?Item=N82E16820141429) or [http://www.newegg.com/Product/Product.aspx?Item=N82E16820141214](http://www.newegg.com/Product/Product.aspx?Item=N82E16820141214) depending how much ram you want.

---

### Post by Tomatz on 2008-04-12
Just do this:

**sudo apt-get install ddr_ram**

---

### Post by Literati on 2008-04-12
> **tamoneya said:**
> the default 32 bit kernel of ubuntu al;so has the 3.4 GB restriction on it but i see no reason to go that high.  As for speed of the RAM it makes no sense to buy faster than your motherboard supports because it will just be more expensive.  
I would stay away from ebay since it is so susceptible to scamming.  I would get it from newegg.  Here is what I would get [http://www.newegg.com/Product/Product.aspx?Item=N82E16820141429](http://www.newegg.com/Product/Product.aspx?Item=N82E16820141429) or [http://www.newegg.com/Product/Product.aspx?Item=N82E16820141214](http://www.newegg.com/Product/Product.aspx?Item=N82E16820141214) depending how much ram you want.

Hm,

How much of a difference would I notice from 333mhz to 400mhz?
Also, how much difference would I notice from CL2 to CL2.5 to CL3 latency speeds?

And Tomatz, I'm assuming that was a joke? :P

---

### Post by Tomatz on 2008-04-12
> **Literati said:**
> Hm,

How much of a difference would I notice from 333mhz to 400mhz?
Also, how much difference would I notice from CL2 to CL2.5 to CL3 latency speeds?

And Tomatz, I'm assuming that was a joke? :P


LOL

If your board only supports 333 you should (depending on the board/ram) be able to put a 400 module in it but it will only run at 333 mhz NOT 400 mhz.

---

### Post by tamoneya on 2008-04-12
these are PC-2700 sticks of ram.  Since you said your motherboard only supports PC-2700 you will notice ZERO difference since your motherboard will just underclock the sticks.  As for CAS latency you will notice some difference between 2 and 2.5 and 3 since it is a fairly large % difference.  I wouldnt worry about it.  These sticks are 2.5 CAS and it gets kind of expensive if you want to get CAS 2.

---

### Post by Literati on 2008-04-12
> **Tomatz said:**
> LOL

If your board only supports 333 you should (depending on the board/ram) be able to put a 400 module in it but it will only run at 333 mhz NOT 400 mhz.

Well, it can accept up to 400mhz. So that's why I'm asking, how much of a difference would I notice? Because I plan on buying RAM once, and really, never again (at least, not for a long time) so I may as well splurge the extra and get the best my mobo can handle. Just, if it doesn't make a noticeable difference, then screw it y'know? :)

---

### Post by Literati on 2008-04-12
Sorry for the double post. But I misread.

My mobo CAN accept PC-3200, 400mhz.

So between say:

PC-3200, 400mhz and PC-2700, 333mhz, how much difference would I notice?

---

### Post by tamoneya on 2008-04-12
that you will notice.  You should definately try and get 400 MHz instead of 333 Mhz especially since they are very similar in cost.

1 GB: [http://www.newegg.com/Product/Product.aspx?Item=N82E16820145440](http://www.newegg.com/Product/Product.aspx?Item=N82E16820145440)
2 GB: [http://www.newegg.com/Product/Product.aspx?Item=N82E16820231047](http://www.newegg.com/Product/Product.aspx?Item=N82E16820231047)

---

### Post by Literati on 2008-04-12
Alright, thank you very much.
Now, just to find a website that can ship to Canada :P
Thanks everyone! :)

---

### Post by ben@layer on 2008-04-12
> **Tomatz said:**
> Just do this:

**sudo apt-get install ddr_ram**

it didint work lol.:lolflag:


Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package ddr_ram

---

### Post by Tomatz on 2008-04-12
> **ben@layer said:**
> it didint work lol.:lolflag:


Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package ddr_ram

HeHe

Damn Hardy its so buggy!

:lolflag:

---

### Post by RTrev on 2008-04-13
Seems like 512 is a bit low.  You might want to check the system monitor to see how much you are actually swapping.  If you aren't swapping at all, then more memory won't help.  If you are swapping, it will.  I think that sums it up in a nutshell.  Swapping occurs when there isn't enough physical memory, and the swap areas of the disk need to be used to simulate real memory.  Disks are of course slow.  So get to the point where no or minimal swapping is taking place, and probably adding more memory beyond that point will have no effect on performance.

At least that's how I understand it.

bob

---

### Post by Literati on 2008-04-13
> **RTrev said:**
> Seems like 512 is a bit low.  You might want to check the system monitor to see how much you are actually swapping.  If you aren't swapping at all, then more memory won't help.  If you are swapping, it will.  I think that sums it up in a nutshell.  Swapping occurs when there isn't enough physical memory, and the swap areas of the disk need to be used to simulate real memory.  Disks are of course slow.  So get to the point where no or minimal swapping is taking place, and probably adding more memory beyond that point will have no effect on performance.

At least that's how I understand it.

bob

Well, right now, when I have JUST FireFox and uTorrent open (running through Wine) I'm using half my "503MB" of memory, and 310.8MB of Swap. 
Bah.

I'm definitely going to upgrade it then :P

---

