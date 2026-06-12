---
title: "cursor jumps between dual monitors"
date: 2013-07-09
forum: Hardware
---

### Post by planarian on 2013-07-09
My Xubuntu machine has an nvidia card and dual monitors set to display  separate X sessions. Unlike in twinview (where moving the cursor to the  edge of one monitor causes it to appear on the corresponding edge of the  other) in this mode, the cursor jumps from the edge of the first  monitor to (roughly) the center of the second monitor. This isn't just  distracting -- it makes the setup almost unusable. I know there are  utilities out there that will lock the cursor onto one monitor or the  other, but what I'd really like is to find some way of controlling the  way the cursor translates between screens. I assume this would involve  the nvidia driver, but I'm not sure where to look. Thanks.

---

### Post by planarian on 2013-07-10
I managed to fix it by upgrading my Nvidia drivers from ver 313 to 319. In 319, the settings panel showed an overlap between the two screens. Once I made the two frames contiguous, the cursor jumps stopped.

---

