---
title: "Rediculously slow repositories"
date: 2008-11-05
forum: General Help
---

### Post by Afkpuz on 2008-11-05
Like the title says, my repos are unbearably slow.  My internet is normal speed and gets about 500kb/s on regular downloads.  However, when I use synaptic, the download speed doesn't even register.  It estimates that it will take over 4 days to download 100 megs.  

Also, I've checked other ubuntu computers on my network and they could download the exact same packages at normal speeds.  So, anyone have any ideas?

Internet is normal, repos are sluggish.

---

### Post by HyperHacker on 2008-11-05
Yeah, the servers are way overloaded. I'm averaging about 10k/s. (Holds steady about 20k/s for a few minutes, then disconnects for several seconds and/or drops to less than 1k/s for several minutes.) The system is not very smart as I understand it; it just connects to the closest server every time. As I mentioned elsewhere, there really ought to be a way for it to determine which servers are less crowded or distribute packages via P2P.

---

### Post by Afkpuz on 2008-11-05
But another ubuntu 8.10 computer on my network got normal download speeds in synaptic

---

### Post by shazbut on 2008-11-05
I was under the impression it only downloads from the server listed in System->Administration->Software Sources, under 'download from'.  After install I normally go there and choose the mirror my ISP provides.  If I leave it at the default server for my country it is always slow around release time.  Bonus for me is besides being faster, the ISP download is unmetered.

---

### Post by DougieFresh4U on 2008-11-06
> **shazbut said:**
> I was under the impression it only downloads from the server listed in System->Administration->Software Sources, under 'download from'. 
When you get to the "download from" choose "other" then click "select best server" and it will do a "ping" of 201 servers and highlight the fastest one it found and then click "choose", you will be downloading good

---

### Post by shazbut on 2008-11-06
I never noticed that there before.  I guess it never mattered since the quickest one for me will always be my ISP's mirror.  Maybe it the scan (or manual selection) should be a choice during initial installation.

---

