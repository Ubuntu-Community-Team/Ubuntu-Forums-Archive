---
title: "Fumbling toward Linspire (Fujitsu P5010D wireless)"
date: 2006-09-13
forum: Hardware &amp; Laptops
---

### Post by Mize on 2006-09-13
I have a Fujitsu Lifebook P-5010D with Broadcom Wireless. The Linspire Live CD works with it flawlessly, but I cannot get Ubuntu to do likewise. I've tried numerous walkthroughs using ndiswrapper all to no avail (probably mucking things up in the process). If anyone has any great ideas I'd be grateful as I don't really want to put XP back on this machine and Linspire is $50 and much uglier than Ubuntu (which I have running great on another laptop).

Thanks in advance.

---

### Post by Neobuntu on 2006-09-13
Once ubuntu is installed to hard drive, you have to put the broadcom driver/module name into the blacklist configuration text file, add "ndiswrapper" to the top of your modules file (to load at boot time,) set ndiswrapper to install the correct and matching Windows XP broadcom drivers (in a short named folder directory, preferably off your "/home/*you*" folder for ease or use and REBOOT.

I prefer to hook up the Internet by hardwired Ethernet CAT5 cable temporarily, and install the GUI for ndiswrapper...hold on...yes it's "ndisgtk" (Install with the easy Synaptic package manager after enabling the Ubuntu sources in it; for new installs.) It will load all other packages and dependentcies.

Then it's just point and click (and do this point and click using the menu choice "Install Windows Drivers" every time the core kernel automatically updates.) Easy peasy.

Overall, much easier than installing a driver in XP.

Of course one could spend $10 and get a real wireless device that is reported to just work (zero driver setup just wireless name.)

In summary, ndiswrapper has worked better for me with the super crappy Broadcom stuff. (Dell even sent us a mini-PCI Intel Wifi to replace a Broadcom processor hog for free.) It's not like these devices with good supportive chipsets are expensive. It's truly anti-competitive Microsoft alignment corruption for these companies to shun open software. Most of them have been made to work (reverse engineered) by now anyway. Broadcom is in the process.

So I guess we need need some better quality control with these new reverse engineered devices. Espesicially in light of the rest of massive but new and stable code that is Ubuntu. Maybe it would be better NOT to have the fledgling Broadcom modules included until hardened. That way, people would go straight for ndiswrapper. But then they'd claim no support, I guess. 

In any case, about $10 can fix any wireless device problem so remember that, and don't everyone go beating your head against the wall becuse it only works with now unsupported Win 98. "Works" is a relative term. Stability matters.

Example: I bought a PCMCIA PCARD 802.11 Wirless card with known working chipset (researched it) for $9.99 US; NO tax and FREE shipping online included and all I had to do was insert it and enter my wireless "SSID" name! I can move it to any notebook with current (K)Ubuntu and it just works. Great for updates, especially since it's a faster pipe than available cable braodband speeds.

So If you want to save time, spend $10 and insert it when it's delivered. 

If you want what you have to work, whose fault is it that we were sold unsuported Windows only (originally) crap? It was a road block for open software and they darn well know it. If you know better, it's not a problem or in rare cases, one that $10 best solves with zero time wasted, IMHO.

---

### Post by Mize on 2006-09-13
I reinstalled and got it!

---

### Post by Neobuntu on 2006-09-13
Don't forget, although Windows is patently unsafe online with no remedy (but you'd better try,) one DOES NOT generally have to pick between XP and Ubuntu (I recommend Kubuntu but it doesn't matter much depending on space to do both KDE and GNOME.)

This way one can compare how things work in XP (on exact same hardware), you can run your old Windows programs in Windows and if you break one you have the other to help. Still, if you go online with Windows, you have a lot of work to do and you're still not as safe as Kubuntu. 

I just wanted to point out to newbies that your first; best step, is to add Kubuntu (after backup of everything you can't live without) not replace Windows.

Of couse then, Windows practically requires a clean install and due to it's nature and is best clean installed first, before Kubuntu. This way you can compare installing (building up and customizing to your likeing) the two. Said in another way, preinstalled systems are not in fact good because experts know it's better to install it yourself, most importantly after any Windows attack. Else you just never know for sure even if it reports clean.

---

### Post by Mize on 2006-09-13
KDE just seems slower and more kludgey than gnome.
I used to be an HP-UX/Nextstep person (11 years ago!) and linux seems the way to go. I have SUSE 10.1 at home on the desktop.

Does Kubuntu have any other advantages over gnome? Also, I still have to use XP and office since OO.o won't read some excel sheets :(

---

