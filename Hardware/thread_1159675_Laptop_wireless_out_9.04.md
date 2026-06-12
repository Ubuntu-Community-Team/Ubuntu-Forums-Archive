---
title: "Laptop wireless out 9.04"
date: 2009-05-14
forum: Hardware
---

### Post by don_quixote on 2009-05-14
Hi all,

Not sure what happened, as I didn't (at least I don't remember) install any updates, but all of a sudden my wireless is broken (an atheros card).  I've tried activating the madwifi, but that doesn't do anything.  It's odd that wireless would just cut out (seemingly) randomly.  When I try to click on the wireless panel, all the wireless options are now suddenly grayed out.

---

### Post by don_quixote on 2009-05-14
For all you Acer 5720Z owners (and I'm sure many others), this behaviour seems to have occurred because I pressed the wireless connect button on the laptop accidentally.  Pressing it again will NOT enable it again!  The only solution was to shut down (not reboot) the computer.  It works fine once again now.

---

### Post by malarie on 2009-05-15
sudo ifdown ath0;
sudo ifup ath0 would have probably worled as well..

---

