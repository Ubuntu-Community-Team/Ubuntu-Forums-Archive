---
title: "Sapphire hd 2600 xt no display"
date: 2007-11-14
forum: Hardware &amp; Laptops
---

### Post by oneporter on 2007-11-14
Alright, I've been using ubuntu for about a year now, and while I'm no expert, I can usually figure out my issues.

I recently bought a new ati card (hd 2600 xt) to replace an old ati card.  I popped it in, tried to boot ubuntu, no dice, went into recovery mode, did a dpkg-reconfigure xserver-xorg or w/e it is and changed the driver.. still no dice.  Anyway, I have all my files on another partition, so I just formatted my ubuntu install and replaced it with kubuntu 7.10.  It installed and booted fine, and then it told me to install the restricted driver, I installed it, attempted to reboot, and we're hung at running local scripts (local.rc, I think)...  Can anyone help?

---

### Post by Naya on 2007-11-26
The problem being here is that the fglrx (ATI) driver in the restricted drivers manger is old and out of date, I'd say you'll need to install the new fglrx drivers for your card at the time of writing this it is 8.42.3 heres a great wiki helped me set up my card:): [http://wiki.cchtml.com/index.php/Main_Page]("http://wiki.cchtml.com/index.php/Main_Page")

Hope this helps. Good Luck to ya

---

