---
title: "Switching Video cards"
date: 2006-10-18
forum: Hardware &amp; Laptops
---

### Post by raeb on 2006-10-18
Hello all.  I've installed dapper about a week ago, and so far it has been running fantastic for me.  Any questions or problem I ran into was a quick search through the forums and someone had the answer.  I'm switching my video cards from an ATi to an nvidia card.  I didn't install any drivers for ati's card and i'm running on vesa graphics (since I knew the ati wouldn't be staying in the system long.)  Do I need to do anything as far as drivers or any special preperations to the system before I take out the ati card and attempt to install the nvidia card / drivers?  Thanks for any replies  :D

---

### Post by taurus on 2006-10-18
Boot it up after you've replaced the card and see if X would start.  If it gives you an error message, kicking you out to a console, then reconfigure your X again with

```
sudo dpkg-reconfigure xserver-xorg
```

---

