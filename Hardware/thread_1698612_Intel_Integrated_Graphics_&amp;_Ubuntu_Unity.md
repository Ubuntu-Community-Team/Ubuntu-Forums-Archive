---
title: "Intel Integrated Graphics &amp; Ubuntu Unity?"
date: 2011-03-02
forum: Hardware
---

### Post by Shepherd X on 2011-03-02
Will the Unity Shell work fine with Intel i3 integrated graphics? I'm talking about the core i3 (pre-sandy bridge).

Also, do 3d graphics work in Ubuntu with the Intel i3 integrated graphics?

---

### Post by nLinked on 2011-04-21
I'm using Core i3 Sandy Bridge and 11.04 Beta 2, and find Unity very sluggish, especially when opening the menu and typing to search for an application. It tends to freeze while I'm typing for a few seconds, and then displays the results to choose from.

Also, while watching YouTube and other sites, they tend to pause every 10 seconds for about 3 seconds. It happens even with 3D screensavers like the built in GLBlur. In fact, it seems fine at first boot, but begins happening after resuming from suspend. I can't use Unity because of this.

Wish this was fixed. Works fine on my laptop with non-Sandy Bridge graphics.

---

### Post by Yellow Pasque on 2011-04-21
> **Shepherd X said:**
> Also, do 3d graphics work in Ubuntu with the Intel i3 integrated graphics?
Yes.

> I'm using Core i3 Sandy Bridge and 11.04 Beta 2, and find Unity very sluggish
It would be interesting to see if Mesa 7.11 fixes your issues (Ubuntu 11.04 uses 7.10).

---

### Post by nLinked on 2011-04-21
Is it possible to get that now? I made a new post here with more detail: [https://answers.launchpad.net/ubuntu/+question/153774](https://answers.launchpad.net/ubuntu/+question/153774)

---

### Post by Yellow Pasque on 2011-04-21
> **nLinked said:**
> Is it possible to get that now?

[https://launchpad.net/~xorg-edgers/+archive/ppa?field.series_filter=natty](https://launchpad.net/~xorg-edgers/+archive/ppa?field.series_filter=natty)

---

### Post by nLinked on 2011-04-21
> **Temüjin said:**
> [https://launchpad.net/~xorg-edgers/+archive/ppa?field.series_filter=natty](https://launchpad.net/~xorg-edgers/+archive/ppa?field.series_filter=natty)

It worked! I added their PPA, and no more freezing. I can finally use Unity, thank you!

It's a little buggy. The 3D screensaver is a lot faster, but also breaks a bit, like graphics mess up some times. But the freezing issue is gone.

Once the original Ubuntu rep gets a version higher than this edgers one, I should be able to remove this PPA for more stability. Thanks again!

---

