---
title: "Mouse not working"
date: 2019-01-03
forum: Hardware
---

### Post by buffsop on 2019-01-03
So, I'm pretty new to Linux and Ubuntu. I've played around with it before, but I never really used it enough to warrant keeping it on my computer. Times change. I decided I wanted to dual-boot Windows and Ubuntu again.

I created a bootable USB with Rufus and booted from it but my mouse doesn't work when I'm running that way. Using the same PC and the same USB port in Windows 10 instead of Linux works just fine, but the second I boot to Ubuntu from USB, I can't move it or click it. My keyboard works just fine, so I'm sure there's some hope because of that.

Ubuntu version is 18.04.1 desktop

The mouse (Corsair Glaive): [https://www.newegg.com/Product/Product.aspx?Item=N82E16826816075&Description=corsair%20glaive&cm_re=corsair_glaive-_-26-816-075-_-Product](https://www.newegg.com/Product/Product.aspx?Item=N82E16826816075&Description=corsair%20glaive&cm_re=corsair_glaive-_-26-816-075-_-Product)

---

### Post by CatKiller on 2019-01-04
Apparently it communicates in a non-standard way. I've found some references on the kernel mailing list to making some changes to allow for its quirks, so hopefully that will work its way through to the mainline kernel at some point. In the meantime, I've found [this project](https://github.com/ckb-next/ckb-next), which some people have reported as being useful.

I don't have that mouse, or anything like it, that's just what I've found from a search.

---

