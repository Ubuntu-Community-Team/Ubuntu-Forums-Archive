---
title: "Canon MP190 printing problem on Ubuntu 14.04 LTS"
date: 2014-08-25
forum: Hardware
---

### Post by fidelis2 on 2014-08-25
Good day,

I'm running a fresh installation of Xubuntu 14.04 LTS (64bit) including all updates available so far. It should behave identical to Ubuntu 14.04 LTS when it comes to non-desktop things like printers and so on, I think.
So far everything works very well with my new Linux installation -- except for my printer...

My Canon Pixma MP190 Inkjet printer connceted via USB to the PC, worked fine under Windows which I  just replaced with Linux. Now the very nice (X-)Ubuntu printer configuration  (program "system-config-printer") detected my Canon printer instantly,  and I was happy when the test page started to print -- but then it only  prints half of of the page (roughly), and then starts to pause. After  some minutes it printes one raster line more, and sometimes after 5  minutes or so it prints the rest, but mostly it doesn't print anymore,  so mostly you're ending with half a page or so.
When I look in the task manager it says that some cupsd is using the  CPU, so there's something working in the background, just that it  doesn't print, 

When I cancel the print job (in the print queque window) and try again,  the driver or printer soon gets very angry and then the printer can't  even be switched off with his soft power button...


Now in this forum I read that the MP190 printer would have worked with  Ubuntu 13 or older, but since I can't say, I'm asking you readers what about Ubuntu 14? I've no  luck so far and am pretty lost. Not being able to print is pretty bad, when all the rest works so well.

The system-config-printer program lists this as driver properties:
Canon MP190 series - CUPS+Gutenprint v5.2.10-pre2


Any help much appreciated!


P.P.S. The MP190's built-in scanner behaves similar: when I try to scan, the first  raster lines are scanned correctly but then no further lines are shown.  However, this may be something different (driver? No idea), so I'll  stick to the printing problem in this thread.

---

### Post by fidelis2 on 2014-08-27
Or maybe some users are using another Canon (Pixma) MP-xx printer model but too can't print from within Ubuntu 14.04 ?

Any hints on how to solve this problem would be much appreciated, since I'm now printer-less...

Would I have to buy an Ubuntu-/Linux-compatible printer like the HP ones? But my Canon MP190 works fine (under Windows it did), so I'd rather like to keep it...

---

### Post by fidelis2 on 2014-08-28
Well, I just can't get that Canon MP190 to print from within my new  (X-)Ubuntu 14.04 but need that printer; so I took the next step and tried to print with Virtualbox (from the software centre) and a  Windows guest, because the latter comes with working Canon printer drivers.

First, the Win7 guest doesn't like my host's USB3 ports -- no matter if I tell the Virtualbox to enable USB1 or USB2 to its guest. The Win7 guest  says that something isn't correct with the printer USB  device, well it sees the  Canon printer but doesn't properly communicate with it.
Since this "Ubuntu 14.04 + Virtualbox + USB" problem has been reported  several times here on the forum, I think there's indeed some software  problem.

Second, a WinXP guest does like the host's USB3 ports -- but only if I tell the Virtualbox to "use USB1" for the guest. The other option "use  USB2" for the guest won't work and result in the same errors as does the Win7 guest.

So I let the WinXP guest install the Canon MP190 driver coming with  WinXP and everything works nicely fropm within the WinXP guest.
I also network-share the virtual Canon printer in the guest, and enable"bridge"  network mode in Virtualbox for this guest. This way I can use (X-) Ubuntu's  printer GUI tool to add a network printer (the virtual one inside the  WinXP guest), so finally even (X-) Ubuntu prints to the Canon printer!

P.S.  The WinXP guest is happy with "just" 256 MB assigned to in  Virtualbox, and by using the "save snapshot" feature of Virtualbox to  start and end the guest is very fast.


Just reporting all this in case somebody experiences similar problems with his new Ubuntu 14.04 and a Canon MP printer.

---

