---
title: "wireless internet problem."
date: 2008-07-20
forum: General Help
---

### Post by mudassar on 2008-07-20
I'm having trouble connecting to the internet using ubuntu.

I've just installed it or the first time.

If i go to system > administration > hardware testing


Under network controllers it says 'Realtek ... wireless controller..." (... = un-needed text)

So it is recognised, unless i'm confused.

But under System> administration > hardware drivers there is nothing. Absolutely nothing.

When i click the network connection icon in the top right i get two list options 'wired network' which is greyed out and unselectable and 'manual configuration...'

If i click manual i get the 'network settings' box which has 'wired connection and point to point connections listed under the 'connections' section. But no wireless network.

Any advice?

---

### Post by pauper on 2008-07-20
[https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide)
[http://www.hpl.hp.com/personal/Jean_Tourrilhes/Linux/Tools.html#debug](http://www.hpl.hp.com/personal/Jean_Tourrilhes/Linux/Tools.html#debug)

---

### Post by Lori700698 on 2008-07-20
If you can get a connection (maybe hard wired?) It's pretty simple to fix.
Go to applications, add/remove, system tools, and select windows wireless driver. Then you need to download the driver files (I'm not sure which one you are using) We can get you a link if you let us know which one you have.  I put this folder on my desktop and it can be moved later when you get this resolved.  After all is in go to systems, administration, and select the windows wireless driver and add (point to the driver folder on your desktop and that's it)  If you can't get online you can download everything to a disk and then put the files on that way too.

---

### Post by mudassar on 2008-07-21
Lori, it is a Realtek 8185, what it says under device manager.

[here is the link]("http://www.novatech.co.uk/novatech/specpage.html?NOV-54GPCI")

Although, i just read in the comment section that drivers for linux are hard to find, something about not knowing what chipset it uses. That means nothing to me. :-|


So linux recognises the wireless card but cant use it? that's the bit that confused me.

---

