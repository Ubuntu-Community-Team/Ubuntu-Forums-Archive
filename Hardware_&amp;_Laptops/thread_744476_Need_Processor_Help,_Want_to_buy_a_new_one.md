---
title: "Need Processor Help, Want to buy a new one"
date: 2008-04-03
forum: Hardware &amp; Laptops
---

### Post by DeVonne on 2008-04-03
Hello, I am planning on getting a new processor since mine is currently at 800mhz

I am not very good at hardware, I am mostly software/windows and got ubuntu only a few days ago

My question is how do I know what Processor is compatible with my Motherboard and Ubuntu and costs around $100-150

And if you can recommend something that would also be available in a local store it would be fantastic!

I don't know what to type to check my system specs, I will gladly post them if someone tells me how

A main problem of mine is I don't want to plug it in burn it out, or something not work, I want it to go as smoothly and as safe as possible, and I know minimum about hardware not enough to have confidence in making a choice or knowing what is possible

Who better to ask then the ubuntu community? :)

Help is greatly appreciated!

---

### Post by em3raldxiii on 2008-04-03
The bad news:  Most likely, if you have a processor that only runs at 800mhz, it's probably something like a PIII or a Celeron (although there are others that it could be but the same problem occurs).  With these older processors, most likely your motherboard's processor socket is a Socket 370, or possibly a Socket 478.  If your processor is an AMD, most likely the socket will be a Socket A.  Now, with all this info (I know, probably seems kinda like technobabble to you), but the net result is this:  They don't manufacture processors for those sockets any more.  So you might be stuck trying to find a second-hand processor to fit your socket, and that will be even more difficult because there is no quality control in that situation.

So now you might say to me, "well, can I just get a new motherboard?" and the answer is, "well, yes, but there are going to be some other hitches ..."

A new motherboard will support the newer processors (and there are plenty of motherboard/processor combos that run in the <$200 range).  However, it will very likely not support the RAM that you have (probably PC1600 or PC3200).  The new boards will take a totally different beast (PC6400) which is DDR2.  Totally different animal.  This will tack on another $50 or so to your package.  And the worst part is, many of your existing expansion cards may not be compatible, and your hard drives will be IDE (as opposed to the SATA2 that dominates the market right now).

So ... I hate to say it, but you might be stuck.  Unless you can find someone like me who does a lot of hardware repairs.  I have quite a large supply "dump" of older hardware that I am loathe to chuck out.  If you can find someone who has a similar collection you might be able to upgrade for nothing.

With that said, if you happen to live somewhere in Northern Alberta, Canada, I could hook you up for free :D.

---

### Post by SoloSalsa on 2008-04-03
Don't get worried about what em3raldxiii said.  I'm sure you acknowledge your computer is old without being told so.  That just means that buying something secondhand (like from eBay) will be *that much* cheaper!

I don't know any terminal commands to identify a motherboard, but there is a very nice graphical way.
```
 Ubuntu Menu Bar > System > Preferences > Hardware Information
```In the Device Manager, look in the left column for ```
System Board
```.  Look at both "Device" and "Advanced" tabls for something that looks like a model number.

That should be simple enough, but for whatever reason, on my computer, all I get is "Unknown" in all fields.  The next easiest way to identify your board is to look at your BIOS.  Your BIOS will definitely report the board model, processor model, and a bunch more information.  The last way to identify your board is to open your computer and locate it's printed information.

---

### Post by acron1 on 2008-04-03
> **DeVonne said:**
> Hello, I am planning on getting a new processor since mine is currently at 800mhz

I am not very good at hardware, I am mostly software/windows and got ubuntu only a few days ago

My question is how do I know what Processor is compatible with my Motherboard and Ubuntu and costs around $100-150

And if you can recommend something that would also be available in a local store it would be fantastic!

I don't know what to type to check my system specs, I will gladly post them if someone tells me how

A main problem of mine is I don't want to plug it in burn it out, or something not work, I want it to go as smoothly and as safe as possible, and I know minimum about hardware not enough to have confidence in making a choice or knowing what is possible

Who better to ask then the ubuntu community? :)

Help is greatly appreciated!

I will be flamed for this but the best way I know to accurately identify your hardware configuration is with SiSoftware Sandra XII SP1 in W$. You can download it from here:
[http://www.download.com/SiSoftware-Sandra/3000-2086_4-10556571.html?tag=lst-1](http://www.download.com/SiSoftware-Sandra/3000-2086_4-10556571.html?tag=lst-1)
or google it for other choices. I have to question a- the logic of this upgrade since it appears that this is a very old system  and b- your ability to carry this out given your limited knowledge. Having said this if you would like to learn to tinker with computers(it's not hard at all) then this is the system to do it on.

---

