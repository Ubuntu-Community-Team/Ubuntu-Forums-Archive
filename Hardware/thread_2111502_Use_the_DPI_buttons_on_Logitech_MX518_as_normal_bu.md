---
title: "Use the DPI buttons on Logitech MX518 as normal buttons"
date: 2013-02-02
forum: Hardware
---

### Post by Horbo on 2013-02-02
The MX518 has two "special" buttons on either end of the scroll wheel that change the dpi setting of the mouse on the fly.
If you run xev, these two buttons don't register as input at all.

Their dpi feature works perfectly well in Ubuntu, but frankly it's not a very useful, and I want to use them as normal buttons, like I do in Windows.

I've checked many solutions, and there seems to be only one that will work: HiDPoint.
Lomoco has the correct feature but doesn't support the MX518.
It sounds like perhaps (I don't know) the evdev driver would make it happen, but I wasn't able to get it working.

Does anyone know any other possible way to make these buttons act "normally" instead of changing dpi? (Asking because there are some serious hurdles getting HiDPoint to work...)

---

### Post by Horbo on 2013-02-02
I finally got hidpoint to work, but it just crashes at runtime.

Does anyone else have an mx518 that they've successfully done this with?

---

