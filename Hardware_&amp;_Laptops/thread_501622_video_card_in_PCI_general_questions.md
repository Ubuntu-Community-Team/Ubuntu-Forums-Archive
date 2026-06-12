---
title: "video card in PCI general questions"
date: 2007-07-15
forum: Hardware &amp; Laptops
---

### Post by ufugu on 2007-07-15
I have a couple of quick questions about upgrading to a new video card.  I come from 20 years of Macs where the only fussing I ever needed to do was swapping out a hard drive or adding RAM.  After running Ubuntu on a G4 for awhile I now have my first PC and despite reading my manual, Googling, and searching the forums a lot of stuff about video cards and PCI slots is still confusing to me.

The machine is an HP Slimline Pavilion s7600y ([details on components here]("http://h10025.www1.hp.com/ewfrf/wc/prodinfoCategory?lc=en&cc=us&dlc=en&product=3254062")).   The video card is an integrated Radeon Xpress 200M.  I have one available PCI slot and would really like to be using a better video card.  

I have a few questions but they are really all the same ball of wax:

Can I just get a new video card and pop it in the slot, or am I stuck with the "integrated" ATI card?  Do I have to somehow disable the ATI card? Would the two cards conflict? Would I disconnect the integrated ATI card physically?  Will I need to do a clean install of Ubuntu afterwards?

I'd also be up for any specific card recommendations.

I'd also appreciate any links you've found helpful where I can learn more on my own.  I've looked around but I'm kinda lost on this even though it seems to be basic knowledge to most PC tinkerers.

Thanks!

---

### Post by w4ett on 2007-07-15
Tall order.....But a seperate card will give you better operation.

Requirements (As I see'em)

1.  I recommend almost anything Nvidia over ATI because of the driver support.
2.  A slimline card and Bracket required (or does the case have full size car slots?
3.  At least 128MB VRam...the more the better
4.  Your motherboard SHOULD detect the new card, but might have to be configured manually or may even have a jumper...(Check Documentation)
5.  PCI Vid cards are getting thin on the ground, but can be found on EBAY and   
[www.pricewatch.com](www.pricewatch.com)

---

### Post by ufugu on 2007-07-15
Thanks for the assist!

The slot is low profile.

As I look around more at Nvidia cards it looks like I might be out of luck.  The manual for the computer says i can't install anything in the slot with more than 5 watt power consumption (probably due to the super compact size and cooling issues) and the cards that I can find that even bother to list power consumption seem to be substantially more than that.

Am I doomed to stick with the crappy Radeon Xpress 200M or are there other options to check out?  I wish I had done more homework and learned how much trouble I'd have with the ATI.

---

### Post by w4ett on 2007-07-15
What driver are you using , the xorg-ati or the restricted fglrx driver?
Is your 3D enabled?    in the terminal type:

glxgears

lets see what it's doing? Maybe we can tweak a little bit.

---

### Post by ufugu on 2007-07-16
thanks for the offer to assist, w4ett.  i have fglrx installed and average about 850 frames per sec.  i have (thanks to the Xpress 200M folks in the forums) set up a separate session for beryl and it works, although unfortunately it does not work well.   it is slow and jagged looking and not very usable.

oddly enough, i had beryl working well in PCLinuxOS (and i find it useful, not just "eye candy") , but i truly prefer Ubuntu.   i was really hoping there was some way to just get a better graphics card going, but maybe i just have to pass on that dream with this particular computer.  i feel a little ripped off but it was my own darn fault for not knowing about ATI driver issues...

---

