---
title: "New graphics card --&gt; no graphics!"
date: 2005-07-31
forum: Hardware &amp; Laptops
---

### Post by lusepuster on 2005-07-31
My old AGP graphics card burned down after a couple of months' illess the other day. I put in an old PCI graphics card, logged in, everything works fine, but it cannot start Xorg.

It's a dual boot machine, and graphics work fine in Win XP. But Xorg says it can't detect any monitor.

Does anyone have an idea how to convince Xorg that the monitors is actually there?  :???:

---

### Post by tucoz on 2005-07-31
I am very new to ubuntu, but I have fiddeled around with xorg.conf lateley. Try and generate a new xorg.conf file by typing:
```
sudo dpkg-reconfigure xserver-xorg
```
which will start the xorg.conf wizard.

If that fails, try and change the driver in the Device section in /etc/X11/xorg.conf to Driver  "vesa", to get a somewhat failsafe setting to get your x started. I do not know if this will work for you, but it might be worth a try.

---

### Post by Lord Illidan on 2005-07-31
First try the vesa thing..

Then make a new xorg server if it doesn't.

---

### Post by lusepuster on 2005-08-01
Thanks for the advise - 

I Got hands on another card, newer but a cheap crappy one, SIS PCI Card. Put it in, reconfigured X.org, and it worked... As long as no LAN cable was in; it refused to boot if i plugged in the net.

Afyter swaping the two cards a bit around in the 5 PCI Slots, I found a working combination - Graphics Card in 2, network card in 4 - an it booted fine again. The first couple of times.   ](*,) 

Now, after having tried to boot some times, it goes completely crazy. It refuses to boot, doesn't even do the POST 'beep'. Until the third try or so, where it boots just fine.

This looks unpleasantly much like the situation before the final burndown of the first graphics card; so I'd really much like it to get fixed somehow...   :|

Does anyone have suggestions? Is it some wrong BIOS settings or something like that?

---

