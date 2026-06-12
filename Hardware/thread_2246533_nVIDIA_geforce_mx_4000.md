---
title: "nVIDIA geforce mx 4000"
date: 2014-10-01
forum: Hardware
---

### Post by carlcamp89 on 2014-10-01
Hey Everyone, i'm still kind of new with ubuntu but i have installed ubuntu 14.04.1 LTS multiple times with my nvidia geforce mx 4000 video card. Each time when i try to plug in the on-board along side the video card to have dual monitors it gets to the log in screen. After i log in the screen scrambles and goes completely yellow with some green lines with it. I have tried purging all nvidia updates and re-update. I'm at my wits end with this. is there anyone out there who has any idea what i can do to get this to work. Thank You

---

### Post by gifford on 2014-10-01
I am unsure of what you are trying to indicate. Do you mean that you are plugging the second monitor into the on motherboard video instead of the mx 4000?

---

### Post by carlcamp89 on 2014-10-01
I am plugging in two monitors into my computer. One of them is in the on-board, and the other is in the video card.

---

### Post by Vladlenin5000 on 2014-10-01
Who told you you can do that?

---

### Post by mörgæs on 2014-10-02
Let's forget dual monitors for a moment. 

Are you able to get a working system using Lubuntu 14.04.1?

---

### Post by carlcamp89 on 2014-10-02
Yes it works fine. If i use the on-board it comes up and i can use it, same goes for the mx 4000. The problem starts when you try to use both monitors

---

### Post by Vladlenin5000 on 2014-10-02
Wasn't my post enough as a hint?
You can't use both, not with that old hardware anyway. The problem most likely is caused by an AUTO setting at BIOS for the graphics device and things go awry when it notices active signal (connected) for both VGAs.
Keeping in mind you can use one or the other, not both - you probably want to use the addon card instead of the integrated chip -, you better setup the BIOS with a explicit option for PCI instead of AUTO and never boot it with any other cable connected to the onboard VGA.

---

### Post by gifford on 2014-10-02
To do what you want you might think about upgrading the video card. The memory amount and card is really outdated so it may not be possible for 
you to run two monitors.

---

### Post by Vladlenin5000 on 2014-10-03
There were a few "dual-head" cards contemporary of that MX4000 and it was possible back then to have at least two monitors, _connected to the same card_.
The MX4000 is an old PCI - not PCIe - graphics card release at a time where everybody was already moving to AGP. The MX4000, since its inception, was designed to fulfill the needs of a legacy niche market, ie, old boards without AGP.

---

