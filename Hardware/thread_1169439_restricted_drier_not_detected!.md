---
title: "restricted drier not detected!"
date: 2009-05-25
forum: Hardware
---

### Post by jmagick07 on 2009-05-25
on older versions of ubuntu when I went to "administration -> hardware drivers" it would detect my wi-fi card and install the driver for it.  I just did a fresh install of the newest version of ubuntu, and when I go there, it doesn't detect anything.  I currently can only use the internet from a wired connection, which sucks because the only wired connection in the house is at the router, which is in my sisters room!

How do I get the driver I need to go wireless?

---

### Post by jmagick07 on 2009-05-25
I really need to get this working by today.  Anyone?

---

### Post by 73ckn797 on 2009-05-25
Are all available sources selected in System/Administration/Software Sources/Third-Party Sources? Also make sure you have restricted and multiverse sources selected.

You may also try "ndisgtk" from repositories. You can install the Windows driver through that. It worked for me on a Trendnet wireless card. The card worked "out of the box" in Ubuntu but was showing a very weak signal even though it was only 10 feet from the router.

What wireless card do you have?

Post results from terminal of:
```
lspci -v
```

You may have to disable onboard ethernet in BIOS as one option to try. If you have onboard wired connection that is.

---

### Post by jmagick07 on 2009-05-25
> **73ckn797 said:**
> Are all available sources selected in System/Administration/Software Sources/Third-Party Sources?

That worked, thanks.  After I checked both boxes, it updated the source list, then when I went back to "Hardware Drivers", it was detected, and now the wireless works :)

---

### Post by 73ckn797 on 2009-05-25
> **jmagick07 said:**
> That worked, thanks.  After I checked both boxes, it updated the source list, then when I went back to "Hardware Drivers", it was detected, and now the wireless works :)

Good deal.

---

