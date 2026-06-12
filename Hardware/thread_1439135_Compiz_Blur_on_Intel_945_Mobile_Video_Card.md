---
title: "Compiz Blur on Intel 945 Mobile Video Card"
date: 2010-03-25
forum: Hardware
---

### Post by somethingkindawierd on 2010-03-25
Hello,
I have a laptop with an Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03) video card.

When I go to the CompizConfig Settings Manager -> Effects -> Blur Windows plugin and enable it, my computer comes to a screeching halt.

Is this due to limitations in the card? Or are there settings I can tweak to get Blur working?

Thanks!

---

### Post by somethingkindawierd on 2010-03-28
I have to admit that for something as superfluous as the blur eye-candy I spent far to much time looking into this.

Turns out that my laptop does not support Open GL 2.0 so Gaussian blur does not work...this crashes Compiz. But Mipmaps do work. The problem was when I chose the mipmap option everything turned black. That was because I needed to check the mipmap option in CompizConfig Settings Manager -> Effects -> Window decorations.

---

### Post by zebrattt on 2010-10-24
> **somethingkindawierd said:**
> I have to admit that for something as superfluous as the blur eye-candy I spent far to much time looking into this.

Turns out that my laptop does not support Open GL 2.0 so Gaussian blur does not work...this crashes Compiz. But Mipmaps do work. The problem was when I chose the mipmap option everything turned black. That was because I needed to check the mipmap option in CompizConfig Settings Manager -> Effects -> Window decorations.


can you explain it in details?    Is your problem fixed?  Have you got Blur Windows effect finally?

I enabled Window Decorations.    Whenever Blur Windows is enabled,  my ubuntu 10.10 becomes observable slower.    All of Gaussion or Mipmaps or 4xBilinear work, but all causes the system slower.

---

### Post by somethingkindawierd on 2010-10-24
I never got it to work without bringing the system to a halt...it became so slow it was unusable.

---

