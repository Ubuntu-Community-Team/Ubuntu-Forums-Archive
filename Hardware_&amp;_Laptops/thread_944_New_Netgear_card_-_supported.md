---
title: "New Netgear card - supported?"
date: 2004-10-16
forum: Hardware &amp; Laptops
---

### Post by tmccartney on 2004-10-16
I have a new Netgear WG511U, which is a laptop wireless network adapter that runs on G and A networks (also B, presumably).

Is this card too bleeding-edge to be supported in Ubuntu?  Any idea what I need to do to get it working?

I'm a complete n00b, so please be gentle...


Thanks,

Tracey

---

### Post by FLeiXiuS on 2004-10-16
You may have to download the driver for that specific card.  NetGear wireless G drivers can usually be foundled with at [http://www.prism54.org/](http://www.prism54.org/) .  Give this a shot.  It worked for me in the past but I haven't used wi-fi in a while.

---

### Post by tmccartney on 2004-10-16
Thanks!  That should get me started.  The Netgear WG511 is listed as a supported card; surely it has the same chipset as the WG511U.  Or so one would think.

---

### Post by neo on 2004-10-21
Actually the WG511 is a prism54 chipset while the WG511T and it appears now the WG511U are both Atheros based.

I am still hashing out my first Ubuntu install, but for Fedora and other distros you can either ndiswrapper it.. or the madwifi driver set is actually rather stable and good.

---

### Post by chet on 2004-11-11
Are there any instructions on how to install the drivers, I'm new to all this but trying to learn

Thanks

Chet

[QUOTE=FLeiXiuS]You may have to download the driver for that specific card.  NetGear wireless G drivers can usually be foundled with at [http://www.prism54.org/](http://www.prism54.org/) .  Give this a shot.  It worked for me in the past but I haven't used wi-fi in a while.[/QUOTE]

---

### Post by chambery on 2004-12-28
I just got this working on my wife's Netgear WG511T.   The instructions are here:

[http://www.marlow.dk/site.php/tech/madwifi](http://www.marlow.dk/site.php/tech/madwifi)

I should say that I _had_ it working, but a recent update (to Hoary) seems to have wiped it out.   It shows up under the Network Settings tool, and my router is detected under the Wireless settings section, but I can't get an IP.  The two lights on the card flip back and forth (instead of blinking together).

I should mention that I used the pre-built debs from the repository listed on the page.  It may be things are changing too fast and I'll have to build my own debs (the instructions for that are pretty detailed).

Good luck!

---- update ----

I don't know why it wasn't working, but I started over and it works now:

1) install Warty, not fetching Internet packages during the install
2) change Synaptic repositories to point to "hoary" instead of "warty"
3) grab the latest from hoary, the madwifi deb, build tools
4) build the driver according Martin List-Petersen's instructions
5) reboot

I wish I knew how I broke it before, but it works now.

---- update 2 ----

It appears that [netapplet](http://nermal.org/old/?entryid=297) may be the culprit.  It's a very useful tool, but as soon as I installed it and added it to the panel, my wireless shutdown (and doesn't want to come back).  It worked briefly, showing my current statistics, then went to an 'X', and my connection went down.  There were problems uninstalling it, though Synaptic says it's not installed.

---

### Post by 323k13l on 2008-05-05
So I was having this same issue with the NETGEAR WG511T.  It shows as ath0 in ifconfig but I noticed I had an IPv6 address.  I work for the computer support help desk at my university and we have been told that IPv6 is screwing things up.  So I deleted all IP6 entries in my hosts tab in network manager. It worked and I am writing this using that very interface.  This may be just due to the IPv6 issues with my school network but hey if it works it works.

---

### Post by 323k13l on 2008-05-06
I stand corrected.  It seemed to work for a while but has since ceased to work.  If anyone knows how to actually fix this problem that would be awesome.  I would love to switch to ubuntu entirely but I need to have wireless internet on my laptop and my windows partition is surviving because I have a card that works on windows but not on ubuntu.  I now have a WG511 and a WG511T and neither of them work (correctly) with linux natively.

UPDATE

so i just installed 8.04 and the WG511t works perfectly.  i am again writing this edit from that very card

---

