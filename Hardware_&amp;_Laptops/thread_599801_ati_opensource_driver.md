---
title: "ati opensource driver"
date: 2007-11-01
forum: Hardware &amp; Laptops
---

### Post by jtouso on 2007-11-01
Hi,
Simple few questions all of them about ATI-RADEON 9550 (RV350 AS) on agp:

1-Ati opensource free driver, ati, has 3d acceleration?
2-Need I write some orders on xorg.conf to run compiz or compizfusion?
3-Why I have "desktops effects" in Ubuntu 7.04 and I don't have with 7.10?
4-Why Beryl works ok and compizfusion no?
5-May I work with opensource ati driver (xorg-video-ati) who says Direct rendering:yes and compizfusion?
and resum question:
How can I use Ubuntu 7.10 with all the desktop effects with my chart and using the free opensource ati driver who has direct rendering:yes and it means 3d possibilities? I prefer don't install fglrx with xgl or wait for the new one with aiglx included without needing xgl.
Thanks a lot
Jose

---

### Post by marcantonio on 2007-11-01
I'll try to answer most of these.
> **jtouso said:**
> 
1-Ati opensource free driver, ati, has 3d acceleration?


Yes, but it's not rock solid for your card.  You'll have to try it out to see but I wouldn't be supprised if it doesn't work.

> 
2-Need I write some orders on xorg.conf to run compiz or compizfusion?


You shouldn't have to.  Try looking [here]("http://wiki.cchtml.com/index.php/Main_Page").  (This is for fglrx)

> 
3-Why I have "desktops effects" in Ubuntu 7.04 and I don't have with 7.10?


In Gutsy you need to go to System > Preferences > Appearance and click the Visual Effects tab.

> 
4-Why Beryl works ok and compizfusion no?


Not sure about this one.

> 
5-May I work with opensource ati driver (xorg-video-ati) who says Direct rendering:yes and compizfusion?


As long as AIGLX is enabled.

> 
and resum question:
How can I use Ubuntu 7.10 with all the desktop effects with my chart and using the free opensource ati driver who has direct rendering:yes and it means 3d possibilities? I prefer don't install fglrx with xgl or wait for the new one with aiglx included without needing xgl.


I've been using the newest fglrx on an HP nw8440 with a FireGL X1600 and it runs great.

Hope that helps.

---

### Post by airtonix on 2007-11-02
Just a warning...

I have a radeon 9600, rv350

Upon installing gutsy (7.10) desktop effects are enabled by default.

If were to install the fglrx....ala via the restricted drivers gui....then i wouldn't be able to get desktop effect back again by simply disabling restrcited drivers.

also, with fglrx i cant have my desktop across two screens as they both turn off when gutsy boots with the fglrx drivers.

---

