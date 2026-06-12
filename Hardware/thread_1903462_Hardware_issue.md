---
title: "Hardware issue"
date: 2012-01-02
forum: Hardware
---

### Post by JAM3SoN on 2012-01-02
Hello guys, I revived my old desktop PC after not using it for about 8 months(guy in service said I got wrong RAM, so he changed both of them) + I bought new Intel SSD Disk. This is error I get sometimes(really randomly): [http://www.jam3son.sk/error.png]("http://www.jam3son.sk/error.png").

I really don't know how to google any possible problem with that - hope you can tell my which hardware part is causing problems? I had to uninstall additional drivers to see this message(otherwise it would freeze on "desktop"). I am using newest 11.10 + Gnome 3. On my laptop this combination works well.

Maybe related, I have some weird behavior of windows in gnome - sometimes they cant be dragged(like there is some transparent window with bigger z-index that blocks clikcing on it). It usually happen in chromium. Not having this on notebook.

Thank you for any help!

---

### Post by drdos2006 on 2012-01-02
Go back to an earlier version of Ubuntu, eg Version 10.4 LTS and see if the same problem persists.

regards

---

### Post by JAM3SoN on 2012-01-02
So I have to uninstall 11.10 and install let's say 10.04 from scratch as I assume there is no downgrade possible? I have made some customizations to this Ubuntu(custom DNS server, custom Apache stack setup etc) and this is one of the last things I would like to do just to test where is the problem. If there will be nothing better, I'll try it. Thanks for response!

---

### Post by drdos2006 on 2012-01-02
Sorry, I forgot to add : Use a Live CD.

regards

---

### Post by JAM3SoN on 2012-01-02
Thank you, will give it a shot!

---

### Post by librechick on 2012-01-03
Live CDs are great at testing hardware problems. You can figure out between 10.04 and 11.04 if a bug was introduced without messing up your setup. If it is a hardware problem then you can replace it. If it is a software problem (bug) then you can try selecting an earlier kernel version from the grub menu or possibly upgrading to a newer kernel/driver package.

---

