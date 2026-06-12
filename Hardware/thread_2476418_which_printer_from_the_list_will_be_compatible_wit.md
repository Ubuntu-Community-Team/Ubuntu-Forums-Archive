---
title: "which printer from the list will be compatible with linux?"
date: 2022-06-25
forum: Hardware
---

### Post by ronjjjg8885 on 2022-06-25
here is the [list]("https://www.zap.co.il/models.aspx?sog=c-printer&db179738=179739&db6754951=6755030").
i need a lazer one that is relatively cheap. preferably not made in china if possible.

here is a [list]("https://www.openprinting.org/printers/manufacturer/Brother") of printers that work on linux. i'm not sure if i've found any of the printers available to be compatible.

better if it can work with cups but even if i need additional driver it might be fine.

i live in israel so i can't buy from a shop of used printers from other countries.

let me know if you found anything that may work.

i don't use much printing so i want it quite cheap [the prices are indicated]
tnx

---

### Post by ronjjjg8885 on 2022-06-25
i think this one might be ok....
Brother HL2130

---

### Post by mIk3_08 on 2022-06-26
I have this brother printer/scanner works smoothly with my Linux Ubuntu Operating System. I have this setup for 6 years now so far so good and haven't encountered any errors. Regards and cheers.

---

### Post by ronjjjg8885 on 2022-07-02
the Brother HL2130?

---

### Post by yancek on 2022-07-03
I see in your links that you only have Brother printers.  HP printers are generally known as being more compatible with Linux.  The link below has a list of HP ;printers as well as others including some Brother printers.

[https://haydenjames.io/finding-linux-compatible-printers/](https://haydenjames.io/finding-linux-compatible-printers/)

---

### Post by mIk3_08 on 2022-07-04
Brother DCP-8040
[Click Here]("https://support.brother.com/g/b/downloadtop.aspx?c=us&lang=en&prod=dcp8040_all") for more info and driver.
[HTML]https://support.brother.com/g/b/downloadtop.aspx?c=us&lang=en&prod=dcp8040_all[/HTML]

---

### Post by TheFu on 2022-07-04
If it were me, I'd look for driver-less printers. Basically, printers that accept raw PS or PDF input over IPP and will print those files correctly.
Eventually, any printer that uses proprietary drivers will end support.  I have a brother printer that was supported about 10 yrs, then they stopped updating.

OTOH, a Samsung laser printer (Samsung doesn't make printers anymore) with FLOSS driver support has been plug-n-play this entire time.  With 20.04, it was even pre-setup by the Ubuntu desktop, so when I went to configure it (which was 30 seconds in 18;.04), it was 5 seconds just to confirm it saw the printer and configured everything in advance.

Look for driver-less printers.   [https://openprinting.github.io/driverless/](https://openprinting.github.io/driverless/)
[https://openprinting.github.io/printers/](https://openprinting.github.io/printers/) has a list that can be filtered by make, model, or partial query "all-in-one".

---

### Post by kurt18947 on 2022-07-04
I'd expect new Brother printers to work and shouldn't require driver installation. Printers right now are not inexpensive I guess due to supply chain issues.  I recently purchased a Brother MFC-J4535 Inkjet all-in-one. Printer and scanner worked out of the box. If for some reason a Brother printer doesn't work fully out of the box there is an installer script run from a terminal that I've had excellent luck with. HP printers have an excellent reputation for Linux compatibility but do your homework about 'expiring' supplies. That may not be an issue with HP lasers but it is with inkjets. Canon makes very good lasers - Canon made the print engines in the legendary HP laserjets - but I don't know about Linux support.

---

