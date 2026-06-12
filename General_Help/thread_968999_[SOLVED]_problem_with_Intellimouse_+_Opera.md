---
title: "[SOLVED] problem with Intellimouse + Opera"
date: 2008-11-03
forum: General Help
---

### Post by Grrblt on 2008-11-03
I'm not sure where to post this because I'm not sure where the problem lies.

I have a Microsoft Intellimouse Explorer 3.0 mouse. The thumb's mouse buttons for forward and backward have historically never worked without implementing a fix in xorg.conf (in 8.04, that fix stopped working for me too). Supposedly, Ubuntu 8.10 has some updated xorg so that these buttons now work by default.

However, **they do not**. At least not in Opera. I see them working in Firefox though so I'm not sure whether the problem lies in Opera or in whatever is handling the mouse driver. Anyone have any ideas?

---

### Post by Grrblt on 2008-11-03
Opera forums helped me get a fix (Opera was listening for Button6 and 7, changing them to 8 and 9 worked) and I suppose it was Opera's fault all along.

---

