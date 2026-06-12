---
title: "printer question"
date: 2006-03-23
forum: Hardware &amp; Laptops
---

### Post by Chuck_W on 2006-03-23
I've been cruising these forums for several days and have gotten a lot of good ideas. One problem still has be baffled. I have a Kyocera Mita FS-1010 laser printer. It is connected to my network via a Hawking Technologies print server. So far I haven't been able to print a test page much less anything else. It says it is printing but nothing happens. I don't think it is a driver issue as Ubuntu has a ppd file for this printer. There must be something with the settings. Should I be using CUPS or Unix? What should the settings be? I have 2 Mac's, OS X and an old OS 8.1 machine, that work fine using LPR. I tried using the same settings but no luck so far. Any ideas?
Thanks

---

### Post by kline on 2006-04-08
[QUOTE=Chuck_W]I've been cruising these forums for several days and have gotten a lot of good ideas. One problem still has be baffled. I have a Kyocera Mita FS-1010 laser printer. It is connected to my network via a Hawking Technologies print server. So far I haven't been able to print a test page much less anything else. It says it is printing but nothing happens. I don't think it is a driver issue as Ubuntu has a ppd file for this printer. There must be something with the settings. Should I be using CUPS or Unix? What should the settings be? I have 2 Mac's, OS X and an old OS 8.1 machine, that work fine using LPR. I tried using the same settings but no luck so far. Any ideas?
Thanks[/QUOTE]

Not too long ago I asked if it were possible to use CUPS on my Ubuntu servers to print on my Berkeley Unix printer server that runs lpr/lpd.   Zero replies.  Most new BSD people are using CUPS; it's primarily guys like me who have been unix users for *years* who stick to ye olden way.  When I moved to lpr I saw that I'm losing the Ubuntu desktop; that's the main reason I'd like to stick with CUPS.

But after some N weekends of headbanging, since everything else just-works, lpr is a good deal.  The trouble seems to be some kind of a network handshake  snafu; with CUPS it looked as tho the file was printing and wasn't.   Too bad there are no diagnostic tools for printer stuff.

gary kline

---

