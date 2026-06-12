---
title: "Laptop backlight buttons"
date: 2008-07-26
forum: Hardware
---

### Post by TheAlmightyCthulhu on 2008-07-26
> **mjg59 said:**
> That's an entirely separate issue. Your system is designed to use the new Intel IGD OpRegion specification. This isn't supported in versions of Windows before Vista, so with your change to the DSDT it's falling back to the old-fashioned code. I've added support for this to Linux, which should be shipping in 2.6.27.

(I didn't want to hijack the other thread.)

Will this be ported back to Intrepid?

I have a Compaq laptop that could use this.

---

### Post by mjg59 on 2008-07-27
> **TheAlmightyCthulhu said:**
> (I didn't want to hijack the other thread.)

Will this be ported back to Intrepid?

I have a Compaq laptop that could use this.

I'd expect so, but I'm no longer involved in Ubuntu kernel development.

---

