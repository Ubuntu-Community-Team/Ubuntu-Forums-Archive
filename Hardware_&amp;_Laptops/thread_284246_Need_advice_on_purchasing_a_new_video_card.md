---
title: "Need advice on purchasing a new video card"
date: 2006-10-25
forum: Hardware &amp; Laptops
---

### Post by RKCole on 2006-10-25
Hello, everyone.

I have decided to get a new video card for my Dell Dimension 4600 desktop PC.  When I first ordered the computer, I did not know much about computers at all, but now that I do I regret not making a better decision.

This system uses an integrated Intel 82865G Graphics controller with 128MB shared RAM.  This has really taken a toll on my OS performance in both Linux and Windows due to the fact that I use a screen magnifier.  This computer only has 256MB of RAM installed...I cannot afford extra RAM right now, and so I think that a video card would be more economic at this time.

I was looking at purchasing [this video card]("http://www.newegg.com/Product/Product.asp?Item=N82E16814150107"), but I am unsure of whether or not it will work with Ubuntu.

I am not much of a gamer (except for standalone games, but nothing too graphically intense), but I want to find a card that has at least 128MB onboard RAM, and something not too expensive.  That is why I am looking at the card described at the site posted above.

Any suggestions would be greatly appreciated.

Thanks guys.

Take care.

---

### Post by ReaderRat on 2006-10-25
I have not read of any problems with XFX cards, but you may want to check out the Hardware Compatibility List below in my signature. Good Luck, I am visaully impaired also. I know how hard it is to read all the stuff you need to research. Have a Good Day...ReaderRat (Ben)

---

### Post by RKCole on 2006-10-25
Thanks, ReaderRat.

You know...it's very ironic...All these years I had been using Windows, and while online looking for people to relate with being visually impaired, I never found anyone until I started using Ubuntu/the Ubuntu Forums.  I am very grateful for all the support and glad to be in such a great place.

Thanks again and take care.

---

### Post by RKCole on 2006-10-25
Hello, again.

Well, I was in luck with the video card as a friend fo mine was selling a barely used XFX video card which uses the nVidia GeForce 5500 GPU and has 256MB onboard RAM; it is an AGP card.

I am not sure if this is normal or not, but I thought that using an expansion card would free up some RAM...but I'm not sure if I was right in my theory.  I am attaching my report from doing the free -m command in the terminal so that you can see my memory usage statistics.  I'm not sure if it is just because I am using the beta release of Edgy or what it could be, but is this memory reading normal?

Hopefully one of these days I can afford to upgrade this machine to 512MB over the current 256MB.

Thanks for any input provided.

Take care.

---

### Post by RKCole on 2006-10-25
Guess it would help if I included the memory statistics, eh?  Sorry about that.

```

             total       used       free     shared    buffers     cached
Mem:           249        234         15          0          7         93
-/+ buffers/cache:        133        116
Swap:          855          0        855

```

---

### Post by hikaricore on 2006-10-25
LOL yea I think a video card (with ram) will take a decent chunk off the system ram usage you've got going there. Especially if you're using a graphicly intense (bloated) UI such as gnome.  :)

I was actually about to post a similar thread to what you posted, using an intel 845g built-in video chipset running the i810 driver in dri mode, somehow months ago I was able to compile a driver that allowed me to get direct rendering working.  Since then I can't find the damn source for the correct one again, so I'm finally about to say screw it and buy a real video card.  :)  Sadly I'm worse off than you are, I don't have an AGP slot so I'm looking into the small selection of PCI cards out there, oddly enough I found (almost) the pci version of what you're looking at [XFX GeForce FX 5200 (PCI)]("http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=633850&CatId=0") ... like I said, almost.  Please let us know how yours works out so I know if it's safe to spend money on one.  =)

---

### Post by hikaricore on 2006-10-25
btw just out of curiousity.  why do you have over 3 times as much swap space as you have physical memory?

---

### Post by RKCole on 2006-10-26
Hello, hikaricore.

Well, unfortunately, the RAM report above was taken after I installed the new video card.  The only thing I can say, though, is that this is while running the Edgy Beta which came out on September 29 or so.  I haven't checked to see if the final release of Edgy has come out yet, but once I get ahold of it (if it's out today I am going to download it) I'm going to test again.

As for the swap space...I made a bit of an oversight during the beta installation.  When the final release of Edgy comes out, I'm going to do a fresh install and correct that.

By the way, which desktop do you recommend?  I was thinking of just using the Xubuntu/Xfce Desktop because there is some accessibility support there.  Do you have any other suggestions?

Take care, and once I do a fresh install of the final Edgy release, I'll report back.  Looking forward to it.

---

### Post by hikaricore on 2006-10-26
Ah, i didn't realize that's what the memory report was from :)  was this while X was running and did you have the correct video drivers installed?  This has an impact on system memory usage.

I personally wasn't complaining about or recommending any desktop persay, I was just trying to reenforce the point that while nice looking and useful, gnome itself uses a ton of resources.  If you're wanting accessibility support you're probably stuck with either gnome or xfce.  Each have thier pros and cons, and they certainly look and feel different.  I guess it's just up to personal choice.  :)  If you can handle having a less than beautiful interface in favor of swiftness you may want to try the new Xubuntu release.

---

### Post by RKCole on 2006-10-26
OH, no offense or anythign taken at all, hikaricore.

I may not have had the correct drivers installed.  When I installed the cideo card, I just went into a terminal and did
```

sudo dpkg-reconfigure xserver-xorg

```

But I basically just did this to get the GUI working as I intended on doing a fresh install of the Edgy final release, anyhow.  I'm going to have to find where to get the correct nVidia drivers, though, as I have never really had to deal with that.

As far as the desktops, though, I do like GNOME, although it is bloated a bit.  But on the plus side...it's Linux...so I can just install the xubuntu-desktop, too, and use whichever one I am in the mood for. :)

I have Edgy final downloading via a Bittorrent client right now, so in an hour or so I will have it installed...in about 15 minutes it will be downloaded.

I'll write back after a bit.

Take care.

---

### Post by jhenager on 2006-10-27
[https://consolutiontechnology.com](https://consolutiontechnology.com)
Date Ordered: Tuesday 10 October, 2006

Products
------------------------------------------------------
1 x Palit GeForce 6200 256Mb AGP-8X - Retail Pack (P6200AGP256) = 
$44.99
------------------------------------------------------
Sub-Total: $44.99
Total: $44.99

Very happy with this card. Great value, and it performs nicely for me.

---

### Post by RKCole on 2006-10-29
Sorry it took me so long to post back, guys.  College has been keeping me busy.  I am taking a M$ Visual Basic class (required :( ) which seems to take up a lot of my time...

It seems that the new video card has made a difference.  Here is my current memory report:

             total       used       free     shared    buffers     cached
Mem:           249        184         65          0         63         45
-/+ buffers/cache:         75        174
Swap:          486         53        432


My question is...how accurate is the free -m command?  At one point it showed 14MB free.  Regardless, the system runs much better.

Now...if someone could point me in the direction of a low-priced pack of 256MB DDR PC2700 RAM, this machine would truly be flying...

---

