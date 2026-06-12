---
title: "ATI radeon driver?"
date: 2010-02-22
forum: Hardware
---

### Post by volter on 2010-02-22
I want to buy a notebook with ATI Mobility Radeon HD 4570.

I would like to know if this video card supported in Ubuntu, I couldn't find driver.

---

### Post by tukuyomi on 2010-02-22
Not yet, but anytime soon, devs are working on it:
[http://www.x.org/wiki/radeonhd](http://www.x.org/wiki/radeonhd) (read "how to setup 3D for r6xx/r7xx (experimental)" -- but do not touch, unless you know what you're doing!)
For the time being, Ubuntu will surely let you install ATi's fglrx drivers :)

---

### Post by volter on 2010-02-22
So, if I get it right. I wouldn't be able to work correctly (video, some compiz ...) without doing this: 
-> [http://www.x.org/wiki/radeonhd](http://www.x.org/wiki/radeonhd) setup 3D for r6xx/r7xx <-

---

### Post by Yellow Pasque on 2010-02-22
You'll want to use the proprietary ATI Catalyst/fglrx driver because it has full "ATI PowerPlay" power management, and the open-source driver doesn't (at least for now).

> [http://www.x.org/wiki/radeonhd](http://www.x.org/wiki/radeonhd) (read "how to setup 3D for r6xx/r7xx (experimental)" -- but do not touch, unless you know what you're doing!)
That info's a bit outdated. 3D will work "out of the box" in Ubuntu Lucid/10.04 with the open-source driver. It's also doable in Karmic without compiling a bunch of stuff (though you do have to install a few .deb packages for a newer kernel). See: [https://help.ubuntu.com/community/RadeonHD](https://help.ubuntu.com/community/RadeonHD)

---

### Post by tukuyomi on 2010-02-22
> **Temüjin said:**
> That info's a bit outdated. 3D will work "out of the box" in Ubuntu Lucid/10.04 with the open-source driver. It's also doable in Karmic without compiling a bunch of stuff (though you do have to install a few .deb packages for a newer kernel). See: [https://help.ubuntu.com/community/RadeonHD](https://help.ubuntu.com/community/RadeonHD)

Thanks for the read (**expecting to come soon to Debian too** ^^) :)

---

