---
title: "Dell Laptop BIOS or Firmware Problem"
date: 2008-08-09
forum: Hardware
---

### Post by kneiliebob on 2008-08-09
I'm trying my first Ubuntu(8.04) install on a Dell Inspiron 2200. After I boot from CD and the Kernal loads, I get some message about a missing file and intstruction to go to a website for a BIOS or Firmware update. It all goes by too fast for me to read. Can someone please give me this info at a speed I can handle?

---

### Post by sdennie on 2008-08-09
Try seeing if you can find the message via System->Administration->System Log.  Also, Dell offers BIOS updates via apt (so, they appear as just normal software updates) but, it can be slightly complicated to setup.

---

### Post by kbrill on 2008-08-09
> **vor said:**
> Try seeing if you can find the message via System->Administration->System Log.  Also, Dell offers BIOS updates via apt (so, they appear as just normal software updates) but, it can be slightly complicated to setup.

Is there somewhere that explains this complicated setup that you know of?

---

### Post by sdennie on 2008-08-09
The "official" directions are here: [http://direct2dell.com/one2one/archive/2007/12/05/37446.aspx](http://direct2dell.com/one2one/archive/2007/12/05/37446.aspx)

However, they didn't completely work for me and I believe that after I ran the commands they listed, I needed to go to System->Administration->Synaptic Package Manager and find the firmware for my specific laptop model.

---

