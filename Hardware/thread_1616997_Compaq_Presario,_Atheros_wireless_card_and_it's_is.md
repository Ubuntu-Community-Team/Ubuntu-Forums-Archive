---
title: "Compaq Presario, Atheros wireless card and it's issues.."
date: 2010-11-08
forum: Hardware
---

### Post by JohnnyMalakian on 2010-11-08
Hey everyone!
Before I start, I'd like to apologize in case this is not the correct section to post this issue. And I have done tons of searches for the same issue if already posted by someone else, but I can't get nowhere.

Here's the situation:
My laptop is a Compaq Presario CQ60-215ep, my wireless card is an Atheros AR5001 (kernel module: ath5k), and I'm using Ubuntu 10.10.

First things first: There's some kind of bug/conflict with my wireless switch.. it's blue (which supposedly means it's on), but the network manager has the "enable wireless" option disabled.. And when I press the wireless switch, it should change to orange (off) but it doesn't, and yet in the network manager the "enable wireless" is now available.

I enable that, but the 'wireless network' keeps showing as 'device not ready'. The only fix I get for my wireless is by going to the Terminal and use "rfkill unblock all". But I'm forced to do that everytime I boot on Ubuntu..

Furthermore, I can tell you that I have tried various possible fixes regarding madwifi, ndiswrapper, "blacklist ath5k" or not from the modprobe files and so on, but in the end I mess up with so much that I get confused and I don't know what I'm working or doing anymore lol. 
And another thing: the "Additional Drivers" doesn't show up any drivers for the wireless either.


In the end, what I wish to know is if there's any fix to get this wireless AND this wireless button thingy to work correctly.

Any help and feedback is really appreciated. :)
Any other info you need from me, feel free to ask.

Cheers! :guitar:

---

### Post by JohnnyMalakian on 2010-11-09
Anyone? :(

---

