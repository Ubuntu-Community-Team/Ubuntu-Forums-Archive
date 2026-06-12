---
title: "eSATA Card - Does Sonnet work in Ubuntu?"
date: 2010-02-22
forum: Hardware
---

### Post by plaine on 2010-02-22
I've been looking for an eSATA card that will work in Ubuntu and also with my new Drobo S.  Options are limited due to Drobo's current issues with eSATA support, but I wanted to see if anyone here has either a Sonnet E2P or E4P card and can confirm it works with the latest version of Ubuntu?  Can anyone confirm that it does or does not work?

According to their tech support:

Possibly. We don't support Linux with most of our products. Doesn't mean they don't work, it just means we don't have the resources to support Linux.

The E2P card is based on a Silicon Image 3132 chipset and their website does have Linux drivers posted but they're 4 years old so I'm not sure they're needed.

The E4P card is based on a Marvell 7042 chipset and I'm pretty sure there are Open Source drivers out there for that chipset.

---

### Post by Objekt on 2010-02-22
I don't know about those particular cards.  Is there some reason you must use one of those two models?  If I understand you correctly, you already have the Drobo.  You want to add an eSATA port to a machine so you can hook up the Drobo by eSATA, but aren't sure which eSATA expansion cards will work under Ubuntu.

If all you need is to add an eSATA port, there are several options.  Some are way cheaper than either of those cards, depending on the machine you're adding eSATA to.

---

### Post by plaine on 2010-02-22
Drobo S only supports a very select few eSATA cards at this point.  Really sucks, but is what it is, so that's why I asked about those.  My on-board eSATA won't even work which would really be the ideal solution, just plug it in to the port that's already there.

---

### Post by Objekt on 2010-02-22
Odd.  I don't understand how the Drobo would know - or care - what kind of eSATA port it's connected by.  I would have thought any eSATA connection would be as good as any other.

Given that constraint, I can only offer educated guesses.  I know that at least one Silicon Image 3114-based card, the Rosewill EC-209-EX, worked fine for me under both Kubuntu 8.04.1 and Ubuntu 8.04.3, in 2 different machines.  One might infer that the Silicon Image 3132 would be similarly Linux-friendly, especially since you only need it to provide an eSATA port, not provide any of its RAID features (if I understand you correctly).

Beyond that, I did find a page suggesting the Si 3132 has been well-supported under Linux since at least 2007.  You might give it a look:
[http://linuxmafia.com/faq/Hardware/sata.html#addonics-sil24%22]("http://linuxmafia.com/faq/Hardware/sata.html#addonics-sil24%22")

Also, Silicon Image offers Red Hat Linux drivers for its 3132 chip: [http://www.siliconimage.com/support/searchresults.aspx?pid=32&cat=3]("http://www.siliconimage.com/support/searchresults.aspx?pid=32&cat=3")

Putting that all together, and given the circa 2006 debut of the Si 3132 chip, I'd say it's highly likely that the card using it would work for you under Ubuntu.

Unfortunately, educated guesses and "highly likely" is probably the best answer you'll get, absent an owner of one or the other card happening by these forums.

---

### Post by plaine on 2010-02-22
Thanks for taking the time to write such a detailed response.  Based on this, its at least worth the trouble of ordering and worst case, having to return it.  Thanks.  And yeah, not sure why Drobo is so fickle, but I've been going back and forth with their tech support for 2 months now waiting for them to fix things.  It's pretty annoying to say the least.  They swear they're getting close to a E4P fix (which Sonnet's site always seems to state in regards to Drobo S compatibility), but its been 2 months now of Firewire 800 speeds for me.  Luckily, its just a backup and I don't rely on it for anything else, but nevertheless, eSATA would be much more ideal for the large video files I have to transfer from time to time.

---

### Post by Objekt on 2010-02-22
What kind of transfer rates are you seeing with Firewire 800?  I know Firewire kicks the pants off USB 2.0 in general, but have never had anything that used Firewire so have not been able to test it myself.

For comparison: reading files from my external HDD connected by eSATA, I get a maximum of around 70 megabytes/second (560 megabits/second).  That is way faster than USB 2.0, but doesn't come close to maxing out eSATA (maximum of 375 megabytes/second).  The hard drive itself is the limiting factor.

---

