---
title: "Support for Intel 945GM chipset !?!?"
date: 2006-08-26
forum: Hardware &amp; Laptops
---

### Post by el3ktro on 2006-08-26
I'm pulling my hair out with this. I've got a new laptop with an Intel 945GM chipset, a RealTek 8139 onboard NIC, Intel WLAN chip & Intel GMA 950 VGA card. I'm reading every- and anywhere that this chipset is supported in Linux, but I can't get any distribution to work on my system. Ubuntu, Gentoo, OpenSUSE, Arch, Knoppix - they all hang during hardware detection. I found out while being in Gentoo that modprobing the 8139too driver for the onboard NIC causes a hard freeze - so I have no network there. Please can anybody help me??? I've done so much reading about which mobile chipset to use, and the Intel 945GM has always been recommended to me - and now I don't get past booting an install CD, this really sucks. Any tips or hints would really be appreciated. Does somebody know which modules I have to load exactly to get the chipset working? Any of those modules causes an error, but I don't know which one.

Thanks!
Tom

---

### Post by alan53 on 2006-08-26
I'm going around the same circles, have a "Dell Inspiron | 640m", Intel Centrino dual 945gm express chipsets.  I see reference to linux drivers in all my searches, but no links to downloads. Wrong move to become a linux newb with the latest and greatest hardware to learn with.

Naturally, I have my monitor working, due to fiddling with an Xcfg file if I'm not mistaken.  After running with VESA (?) I came upon the configuration manual for X and played with it until it recognized my graphic set up. I honestly don't remember what sequence of events or disasters I incurred before, during or after that, but I still have a picture on my screen.

Any updated info will be appreciated.

Alan

EDIT:

[This]("http://tinyurl.com/kcvln") could be the end of the Rainbow  An Intel page offering a download with the usual, "It's up to you to make it work" legalese.

More on this going on [here]("http://tinyurl.com/efp2j")

Seems to be a popular topic and I'm no closer to finding cures.

---

### Post by tsberry901 on 2006-10-19
You can download the drivers now from the Intel website.

---

### Post by onux16 on 2007-10-20
I used to have the same problem with my Toshiba A105-S4284 laptop. My Windows partition was all screwy, so I made an Ubuntu partition, and it froze on me -- the video was completely out of whack. When I finally got the Windows Quick Restore CD replacements, I restored Windows completely, and retried to make am Ubuntu partition. Surprisingly, it worked.

Dunno if that helps; just adding my $.02

---

