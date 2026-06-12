---
title: "[SOLVED] Konsole scroll bar not working, doesn't move."
date: 2008-10-17
forum: General Help
---

### Post by HousieMousie2 on 2008-10-17
Hi,

I talked my Mom into upgrading from Dapper Drake LTS to Hardy Heron LTS... now her scroll bar in Konsole is not working.  Set to Left, Right, Hide, nothing makes it work.

How to go about trouble shooting the Konsole?

---

### Post by ellgor on 2008-10-18
Hi,

If that version of konsole came with Dapper it might be a bit outdated for Hardy, my version (self loaded in from their site) is 2.8.1 and as we speak their could even be a newer one.
Anyway I would recommend getting the newer version and either remove the old one or let the new one overwrite it, hope this helps.

Regards, Ellgor.

---

### Post by HousieMousie2 on 2008-10-18
> **ellgor said:**
> Hi,

If that version of konsole came with Dapper it might be a bit outdated for Hardy, my version (self loaded in from their site) is 2.8.1 and as we speak their could even be a newer one.
Anyway I would recommend getting the newer version and either remove the old one or let the new one overwrite it, hope this helps.

Regards, Ellgor.

Wouldn't it have automatically been upgraded and then updated?  I noticed an update to Konsole yesterday.

Anyway, I will call her and find out the version number.

Thank you for your post.

EDIT: She has the same version of Konsole I do, 1.6.6 (Installed with Hardy from a Live CD on mine.) KDE version 3.5.10  Mine is not broken.

---

### Post by HousieMousie2 on 2008-10-18
She gets this EVERY time she opens a Konsole:

```
Screen version 4.00.03 (FAU) 23-Oct-06

Copyright (c) 1993-2002 Juergen Weigert, Michael Schroeder
Copyright (c) 1987 Oliver Laumann

This program is free software; you can redistribute it and/or modify it under the terms of the
GNU General Public License as published by the Free Software Foundation; either version 2, or (at
your option) any later version.

This program is distributed in the hope that it will be useful, but WITHOUT ANY WARRANTY; without
even the implied warranty of MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE. See the GNU
General Public License for more details.

You should have received a copy of the GNU General Public License along with this program (see
the file COPYING); if not, write to the Free Software Foundation, Inc., 51 Franklin Street, Fifth
Floor, Boston, MA 02110-1301 USA.

Send bugreports, fixes, enhancements, t-shirts, money, beer & pizza to screen@uni-erlangen.de










                                 [Press Space or Return to end.]
```

This is what is different... mine has never shown this message.  It is written IN the Konsole, not as a separate window like the Tips are.

---

### Post by HousieMousie2 on 2008-10-18
Okay, we commented out the line in screenrc that was producing the message... but still the scroll doesn't work.

Just to frame the issue...  My Mom is definitely NOT a bleeding edge user, so she is not interested in going outside of the default repositories to fix what should just work.

Her Konsole scroll bar should work, that version, in Hardy.

---

### Post by HousieMousie2 on 2008-10-18
It's fixed.

All files & directories in the directory ~/.kde that were related to Konsole, were deleted.

Set/Reset all wanted setting in Konsole, Saved As Default and Saved Session.

Restarted.

Worked.

---

### Post by ellgor on 2008-10-19
Hi again,

Glad to see you got it fixed, and as to that error/information bit I must admit I've never seen that before, good thing is, its fixed, well done.

Regards, Ellgor

---

