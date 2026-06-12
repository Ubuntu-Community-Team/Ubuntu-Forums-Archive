---
title: "Unplug USB keyboard and it stops working when replugged"
date: 2008-02-19
forum: Hardware &amp; Laptops
---

### Post by kweinert on 2008-02-19
I'm using a Microsoft Natural Keyboard, model 4000 and whenever it gets unplugged, replugging it in does not get it working again.

I had hoped to share the keyboard between two desktops (I'm at work, so the other box is my Windows laptop) but since it won't start working without restarting the box that's not a solution.

For now I have two keyboards, but that's a bit unwieldy since I need a keyboard tray.

A permanent fix would be good, a way to ssh in and run some sort of command would be acceptable.

Any thoughts?

Thanks.

---

### Post by kweinert on 2008-02-19
While trying to track down an issue where gphoto was no longer working, I found that I was stuck in the interim between the dropping of usbdevfs support and the tools catching up.

So I followed some instructions for re-enabling usbdevfs support and now both the camera and the keyboard are functioning as normal.

---

