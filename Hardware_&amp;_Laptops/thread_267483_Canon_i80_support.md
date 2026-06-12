---
title: "Canon i80 support"
date: 2006-09-28
forum: Hardware &amp; Laptops
---

### Post by headshrinker on 2006-09-28
I've installed 6.06 on my laptop and am rtying to get this Canon i80 printer working.

When installing using "System->Administration->Printing" and clicking on "New Printer", the printer seems to be successfully detected. It is connected to a USB port and "Canon i80" appears in the "Use a detected printer" box.

When selecting this and hitting "Forward", the exact model doesn't appear in the list - it defaults to the "imageRunner 330s". Selecting this model doesn't work - the test page does not print at all. Selecting a different model, such as the BJC-80, manages to print the testpage incorrectly (the magenta row comes out completely white).

This is annoying. I did find this driver on the internet called turboprint. There is a free version available for download (the full version costs 30 euros). This driver seems to work, the only problem being that when I printed out a full A4 picture of my daughter she had a great big "TurboPrint for Linux" logo plastered right across her face#-o . Is it just me that thinks charging money for a linux printer driver it total bananas?

Anybody have any other suggestions?

---

### Post by mgmiller on 2006-10-02
I have a canon i960 that I finally got working with Turboprint.  What is bananas, is the lack of linux support from the hardware manufacturer.  They refuse to release the specs to the open source community, so it is very hard to reverse engineer a driver for it.  The Turboprint people spent a lot of time and effort to create drivers that work as well as or better than the windows drivers.  I don't begrudge them 30 Euros for their work.  I am upset that Canon won't provide Linux support.  Before buying any piece of hardware, you should make sure it's supported by your operating system.  A quick forum check can tell you what's compatible or not.  As it happens, even with the cost of the Turboprint driver, the Canon printers are still very cost effective.  If you buy your ink cartridges from inkgrabber.com for about US 3$ each, it costs almost nothing to feed.  The inks are custom blended for each brand and model of printer and will not cause problems.  The carts for Epsons and HP's are much more expensive.  So a Canon printer + Turboprint + inkgrabber ink is cheaper in the long run than Epson or HP + no turboprint + inkgrabber ink.  I don't know where you live, but if there is a Costco (Price Club) near you, then you should buy their Kirkland Professional Glossy inkjet Photo Paper.  It is very inexpensive and is the equal of any brand name paper I have ever used.  It's much better than Kodak.  I believe it's made by Ilford in Switzerland for them.

Good Luck.

---

### Post by headshrinker on 2006-10-06
Thanks for the reply. I totally agree with you that it is a real pain that the hardware manufacturer doesn't have the foresight to support linux. I have recently moved over from Windows to Ubuntu so I am currently trying to get all my existing bits of hardware to work - most things (such as wireless, ipod, webcam) couldn't have made the transition any smoother. The printer seems to be the sticking point.

I think you may have slightly misunderstood my comment though, for which I take entire responsibility and send my apologies. I should not really post ambiguous statements such as "Is it just me that thinks charging money for a linux printer driver it total bananas?". The whole reason why I moved away from Windows and to Ubuntu was for the free software - by this I don't just mean software that costs nothing but software that has freedom (in the way promoted by the Free Software Foundation). So my objection was not over the cost of the driver in the sense that it was something I couldn't afford (although I dare say there are many in this world who would not be able to afford this).

I do appreciate, though, that people have to pay the bills but I think these guys at Turboprint are treading on very dodgy ground, especially if this printer driver is their core business. If this is the case, they could easily be put out of business overnight by the following 2 scenarios:

a) Since they are operating in open source territory, someone could conceivably come along with a free open source version - this, I think, is very likely
b) Canon, Epson and HP may all decide that they do want to support linux and release the appropriate drivers. This I also think is inevitable. Linux based systems such as Ubuntu are becoming increasingly popular and it is only a matter of time before these companies realise that they are missing out on a potentially large market. It is probably also that case that, as soon as one of them supports linux, the rest will follow.

It is true that if the hardware manufacturers supported linux in the first place then this clearly wouldn't be an issue and the guys at Turboprint would undoubtedly invest their time and, I'm sure, considerable energy into something equally as useful.
I do have to say, though, that I found it extremely annoying when I printed my photo out and got the great big Turboprint logo splashed across the middle of the page. This is the sort of tactic that I came to expect from software running on Windows which is why I have eradicated it from my life.

All that said, thanks very much for the tips they will come in very handy.

---

### Post by carusoswi on 2007-06-23
> **headshrinker said:**
> I do have to say, though, that I found it extremely annoying when I printed my photo out and got the great big Turboprint logo splashed across the middle of the page. This is the sort of tactic that I came to expect from software running on Windows which is why I have eradicated it from my life.


Well, obviously, if they gave you unlimited use in the trial version, you would never pay them whatever they are charging for the solution.  I don't know how much this TuboPrint will cost in US dollars (not up on Euros), but, if it's reasonable, I'm going to get it.  I have an I960 and an I860, both excellent little printers that do fantastic jobs.  I also bought an Epson for my wife during the holidays - it can print directly onto the surface of music CD's that we produce - I have not even begun to explore how to get it to work with Ubuntu.

Although I cannot agree totally with some of your statements, I do share your frustration about getting your printer to work.  This problem shows what happens when one manufacturer (MS) gets a stranglehold on a market segment.  Additionally, I believe, big printer manufacturers built their business model around the razor blade instead of the razor, and now are probably starting to feel some heat (or at least become aware of the real possibility of fire) as alternatives to their expensive inks become available and incentives that justify their proprietary support of MS become threatened by open source alternatives.

In this country (US) we have all benefited by this arrangement to some degree.  The printers (and MS-based software to run them) offer tremendous capabilities at almost no initial cost at all.  Pick your firewater and label the bottle a potion or poison as you will.

The whole situation is complex beyond my understanding.

Caruso

---

### Post by stadt on 2007-06-23
Canon has linux driver for many models have a look  here:

[ftp://download.canon.jp/pub/driver/bj/linux/](ftp://download.canon.jp/pub/driver/bj/linux/)

For easier installation (the canon drvers need several symlinks to work properly) you might try these (the drawback is a slighty reduced fuctionality)

[http://mambo.kuhp.kyoto-u.ac.jp/~takushi](http://mambo.kuhp.kyoto-u.ac.jp/~takushi)

Unfortunately the Canon IP 80 is not on the list.

---

### Post by carusoswi on 2007-06-24
I bit the bullet and purchased a three key license from  Turboprint.  Works like a charm - all functionality seems to be present for my I960.  

I'll have to install Turboprint on the Mrs' computer and see how it works with the Epson.

Now, I'm just thinkin' out loud.  How did the folks at Turboprint manage to develop drivers for all these printers, while, at the same time, all the folks out in distro development world have not yet developed them.  I understand that the info isn't provided by the manufacturer's, but, how did Turboprint manage to get the info if mfrs are not releasing?

Just curious.

One thing I love best about Ubuntu - you come to this board and do a little searching (not much) for a solution, you get a solution.  It may not always be perfect, and it isn't always free, but this board is the place to come to solve problems.

Thanks!!

Caruso

---

