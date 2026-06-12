---
title: "Thinkpad x140e and wifi"
date: 2015-05-14
forum: Hardware
---

### Post by belanger on 2015-05-14
I recently bought a Thinkpadx140e to install Ubuntu.  (Actually, Lubuntu, but I'd be satisfied with either one.)

I had Ubuntu installed on a Thinkpad x100e, and it worked great.  I also heard that Ubuntu would run on the x140e, so I didn't expect any trouble.

I've installed Ubuntu 14.04.2, Lubuntu 14.04.2 and 15.04 on the x140e, and they all installed fine expect they didn't realize that I had a wifi card.  (I tried it on Windows before I installed Ubuntu, Windows had no problem with wifi.)  I replaced the wifi card in the x140e with the one from the x100e; the x140e complained about the card and wouldn't start.

Does anyone know how to get wifi working on the x140e with Ubuntu, either by getting Ubuntu to play nice with the card or suggesting a wifi card that both the x140e and Ubuntu work with?

Thanks,
Jay

---

### Post by tgalati4 on 2015-05-14
Thinkpads have a habit of "whitelisting" their hardware.  Changing a hard disk or wireless card will trigger an error in the BIOS.  

There is no x140e page at ThinkWiki, but there is an x100e page.  There are some suggestions on how to compile the RealTek wireless driver.  Perhaps try compiling the driver for your x140e.  [http://www.thinkwiki.org/wiki/Category:X100e](http://www.thinkwiki.org/wiki/Category:X100e)

What is the exact model of wireless card for each machine?

```
lspci
```

---

### Post by belanger on 2015-05-15
Thanks for the pointer to the x100e information, and even more, thanks for suggesting lspci.  The computer has a Broadcom card, it turns out, and there is a thread in the networking part of the forums telling what to do with a Broadcom card.  So now it's working.

Thanks again!

---

### Post by tgalati4 on 2015-05-15
You can mark the title of this thread with [SOLVED] in the thread tools and please post a link to the instructions that you followed so that others can find it quicker.  Also consider adding an x140e page with your setup experiences to the thinkwiki page.  Every little bit helps.

Thanks.

---

