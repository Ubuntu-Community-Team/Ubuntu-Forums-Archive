---
title: "No wireless on HP G50-126NR"
date: 2009-03-26
forum: Hardware
---

### Post by sevensevens on 2009-03-26
I have been wrestling with this problem for a few weeks now.  I have a HP G50-126NR that I just installed Ubunut 8.10 on.  Everything works great except wireless.  I believe the issue is the hardware button isn't activated at startup, and Ubuntu does not know how to turn it on.  I've posed about this previously at [http://ubuntuforums.org/showthread.php?t=1076466&highlight=G50]("http://ubuntuforums.org/showthread.php?t=1076466&highlight=G50"), but after much investigating still have no answer.  Is there a way to detect a wifi hardware button in ubuntu, and proceed to enable it?

---

### Post by Dark_Stang on 2009-03-26
It looks like that device might not be supported natively. I would suggest trying to use ndiswrapper with one of the drivers for windows.

Here is a link to the driver downloads page.
[http://www.realtek.com/downloads/downloadsView.aspx?Langid=1&PNid=7&PFid=7&Level=5&Conn=4&DownTypeID=3&GetDown=false#RTL8100E/RTL8101E/RTL8102E-GR/RTL8103E(L)%3Cbr%3ERTL8102E(L)/RTL8101E](http://www.realtek.com/downloads/downloadsView.aspx?Langid=1&PNid=7&PFid=7&Level=5&Conn=4&DownTypeID=3&GetDown=false#RTL8100E/RTL8101E/RTL8102E-GR/RTL8103E(L)%3Cbr%3ERTL8102E(L)/RTL8101E)

---

