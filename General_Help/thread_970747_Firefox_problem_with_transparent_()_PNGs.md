---
title: "Firefox: problem with transparent (?) PNGs"
date: 2008-11-04
forum: General Help
---

### Post by generic-identity on 2008-11-04
Hi!

I observed strange artifacts in some images (transparent PNGs?) in Firefox. Please see the attached screenshot, esp. the Wikipedia logo and the images on the right.

I'd be really grateful if someone could tell me how to get rid of this annoying effect.

(This is on Ubuntu 8.10 with Firefox 3.0.3, both "standard" installations.)


Thanks in advance.

---

### Post by gmjs on 2008-11-04
It looks like the images are being stretched doesn't it?  Perhaps Firefox is not displaying at 100% but something over that value.

Try pressing **Ctrl+0** on the keyboard in Firefox to see if this improves the images (reset to default zoom).

Firefox is particularly good at displaying transparent PNGs (compared to Internet Explorer anyway) so I doubt it's a Firefox issue.

Hope this helps,

Graham

---

### Post by generic-identity on 2008-11-05
Thanks a lot, Graham!
The problem is indeed caused by the zoom level. However, it seems my default zoom level (what I get by Ctrl+0) is something higher than 100%, so that new pages are by default zoomed in, making the images look bad.
Unfortunately, I haven't found out yet how or where to adjust this default zoom level...

Edit: I managed to adjust things using the NoSquint-Addon. Problem solved.

---

