---
title: "Good idea to upgrade my RAM?"
date: 2013-11-07
forum: Hardware
---

### Post by darian2 on 2013-11-07
So, I just got £40 and instead of going out and spending it on some games I'm trying to think of some things I can do to improve my crappy pc (anything I can do with £40 will probably improve it a little, so that's good lol)

My PC: [http://www.acer.co.uk/ac/en/GB/content/model-datasheet/PW.SGBE2.013](http://www.acer.co.uk/ac/en/GB/content/model-datasheet/PW.SGBE2.013)

Now, it claims its maximum memory is 16 GB (currently has 4 GB) it's also 64 bit.

Now, if I were to upgrade the RAM, is that all I'd need to upgrade? and how would I go about doing it, do I just grab a random DDR3 SDRAM from amazon and put it in (that's what she said).

All jokes aside, what else could I do with my PC if not to upgrade the RAM which could improve it?


Thanks :)

---

### Post by buzzingrobot on 2013-11-07
You'll likely see an improvement going from 4 to 16 gigs.  How much, and where, depends on how you use the machine.

As long as you buy compatible memory, installing should just be a matter of following instructions. The machine should recognize it when you power it back up. The most common problem here is probably failing to "seat" the chips correctly.

---

### Post by philinux on 2013-11-07
Unless the OP is doing  a lot of simultaneous VM's or large video transcoding I cant see how going beyond 4 gig would improve performance.

What does the output of this show. while running ubuntu.

```
free -m
```

---

### Post by ibjsb4 on 2013-11-07
You call that a crappy computer?  I got nothing that could touch it.

I have to agree, 4G is plenty for the everyday desktop machine.  This may help you understand.

[http://www.linuxatemyram.com/](http://www.linuxatemyram.com/)

---

### Post by Bucky Ball on 2013-11-07
> **philinux said:**
> Unless the OP is doing  a lot of simultaneous VM's or large video transcoding I cant see how going beyond 4 gig would improve performance.



+1.

Welcome. If the computer is not up to scratch it's not the RAM that's the problem, unless you are using it as philinux suggests. Unless you are, wouldn't waste the money. ;)

The majority of people that go over 4Gb (or even 2Gb) of RAM really don't need to. Must be some kind of status symbol, 'mine's bigger than yours' mentality, because generally it makes no sense. A lot of people with 16Gb of RAM check emails, surf the net, listen to music and watch some vids. That's it. What a waste of RAM that is. Bigger is not always better (the same goes for desktop power supplies).

Take someone out for lunch. ;)

---

### Post by darian2 on 2013-11-07
> **Bucky Ball said:**
> +1.

Welcome. If the computer is not up to scratch it's not the RAM that's the problem, unless you are using it as philinux suggests. Unless you are, wouldn't waste the money. ;)

The majority of people that go over 4Gb (or even 2Gb) of RAM really don't need to. Must be some kind of status symbol, 'mine's bigger than yours' mentality, because generally it makes no sense. A lot of people with 16Gb of RAM check emails, surf the net, listen to music and watch some vids. That's it. What a waste of RAM that is. Bigger is not always better (the same goes for desktop power supplies).

Take someone out for lunch. ;)

Well, I don't just mean upgrading the RAM, I mean if there's not really a point in upgrading it, is there anything else I could upgrade at all?

---

### Post by buzzingrobot on 2013-11-07
I have 16gigs in one machine and 32gigs in another, and use both for photo work.  That memory comes in very handy for that work, but, no, it isn't nececssary otherwise. 

So, if you aren't seeing swapping or other slowdowns while using your most memory intensive applications, then you likely won't see any subjectively noticeable improvement.  As I said, it depends on how you use a machine.

Avenues for other hardware upgrades depend on how open your machine is. Other than RAM, typical upgrades would be installing a new video card or adding an SSD or a bigger, faster hard drive. Again, though, unless you are trying to correct obvious weaknesses -- current video too weak to support games, drive is failing or running out of space -- nothing magic is likely to happen.

---

### Post by Bucky Ball on 2013-11-07
As buzzingrobot suggests, another hard drive is a good alternative upgrade, or SSD or upgrade the graphics if forty quid will cover it (in Australia so don't know the prices where you are). But unless you need this stuff ... ;)

---

### Post by ajgreeny on 2013-11-07
I presume from your link that the computer runs with the Intel integrated graphic chip only and has no independent graphic card.

If that is the case, I think that is probably the weakest link in the chain, as far as gaming is concerned, if you really are a game player, that is;  otherwise I would leave it as it is.

---

### Post by darian2 on 2013-11-07
> **buzzingrobot said:**
> I have 16gigs in one machine and 32gigs in another, and use both for photo work.  That memory comes in very handy for that work, but, no, it isn't nececssary otherwise. 

So, if you aren't seeing swapping or other slowdowns while using your most memory intensive applications, then you likely won't see any subjectively noticeable improvement.  As I said, it depends on how you use a machine.

Avenues for other hardware upgrades depend on how open your machine is. Other than RAM, typical upgrades would be installing a new video card or adding an SSD or a bigger, faster hard drive. Again, though, unless you are trying to correct obvious weaknesses -- current video too weak to support games, drive is failing or running out of space -- nothing magic is likely to happen.
What advantages does a SSD have over a normal HDD?

> **Bucky Ball said:**
> As buzzingrobot suggests, another hard drive is a good alternative upgrade, or SSD or upgrade the graphics if forty quid will cover it (in Australia so don't know the prices where you are). But unless you need this stuff ... ;)
Hm, I wasn't sure if I could upgrade the graphics card in an all-in-one
> **ajgreeny said:**
> I presume from your link that the computer runs with the Intel integrated graphic chip only and has no independent graphic card.

If that is the case, I think that is probably the weakest link in the chain, as far as gaming is concerned, if you really are a game player, that is;  otherwise I would leave it as it is.

So basically, if I can I should improve the graphics card (again, I've never upgraded anything in a computer before so I don't know if I need to upgrade the motherboard if I put in a new card)

---

### Post by Bucky Ball on 2013-11-07
SSD faster than HDD. You buy a graphics card that is going to work with the motherboard, naturally. ;)

---

### Post by bazsound on 2013-11-08
If your using an integrated graphics chipset, buy a graphics card. like others have said its the weak link in the chain. You can get some not too bad geforce cards for under £40 but research wether its going to work with your version of ubuntu. newer x servers dont work properly with some older cards, like the geforce fx 5500 though i doubt you would be buying something that old.

the great thing about having a dedicated graphics card is you now free up some of your system ram. integrated graphics use a portion of your system ram, also its generally slower than graphic card memory. integrated chipsets tend to be much slower than dedicated graphics card.

And my favourite part, even budget graphics cards these days usually have atleast 2 monitor outputs. so if you have a spare monitor lying around, you can have dual monitors which is pretty awesome.

make sure you get the right card for your motherboard, if your motherboard has PCI-E then PCI-E graphics card, if its slightly older its more likely AGP. Also remember that some graphics cards require extra power by being connected directly to the powersupply but not all.

Id prefer one that has its on power from the powersupply, ive read to many stories of pci-e slots burning out, happened to me aswell on my machine so im back to integrated graphics :/

---

### Post by buzzingrobot on 2013-11-08
If your machine is an all-in-one, its construction may well be much like a laptop and, so, difficult or impossible to upgrade.   You should check the unit's manual (which should be available online if you don't have it.)

An SSD is a Solid State Drive that uses technology much like that in a camera's data card. They move data faster than traditional hard drives. On the downside, they have a higher cost-per-byte-stored.  If your tasks include something that involves frequent moving of large amounts of data to and from storage, and you find yourself waiting idly for that to finish, then an SSD would likely make a noticeable improvement.

---

### Post by gordintoronto on 2013-11-08
This might consume half of your windfall: get a 32 GB USB 3.0 flash drive and copy your current data onto it. If you ever swap programs, music, videos or pictures with your friends, a big, fast flash drive is wonderful. I find that a USB 3.0 flash drive is faster than older ones, even when plugged into a USB 2.0 port.

---

