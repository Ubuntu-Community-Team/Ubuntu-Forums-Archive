---
title: "Blurry text on LCD of Acer Aspire 1640"
date: 2007-10-29
forum: Hardware &amp; Laptops
---

### Post by coelho on 2007-10-29
Hello,

I have Ubuntu 7.10 on an Acer Aspire 1640 but the fonts/characters are blurry and really straining on the eyes. Had the same problem with 7.04.

Some screen grabs are attached.

Screen resolution is 1024x768
Sub pixel smoothing (LCDs) is on
Full Hinting
RGB subpixel order

I've tried searching for fixes and using MS fonts, but nothing works. Does anyone know how to fix this?

Thanks heaps in advance for your help :)

---

### Post by hugmenot on 2007-10-29
Your real screen resolution must be something else. Simple.
Your screenshots show very sharp black-and-white letters on my screen.

Did you try 1280x800 already (that&#8217;s wide-screen).

---

### Post by hugmenot on 2007-10-29
And I think you littered your font config with stuff, because on your screenshot no antialias whatsoever is used.

---

### Post by openaddict on 2007-10-29
Maybe I'm not seeing it either, but your screenshots looked fine to me.

---

### Post by coelho on 2007-10-29
Thanks guys for suggestions and feedback.

I couldn't change my screen resolution via System > Preferences >Screen Resolution or via System > Administration > Screens and Graphics

I think this is because I have the Intel i915GM onboard graphics chipset and Ubuntu is not detecting the native resolution.

So had to run
sudo dpkg-reconfigure xserver-xorg

and now I can switch to 1280x800 and it's looking a lot better. But I'm still getting some crappy fonts in Firefox e.g. "Quick Reply" heading in attached screenshot. Ubuntu fonts set to Sans 11.

---

### Post by hugmenot on 2007-10-29
The "Quick Reply" looks crappy because of your earlier modifications.
Get rid of those first.

---

