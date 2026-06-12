---
title: "Symbolic link to run CD Player doesn't stick"
date: 2005-05-03
forum: Hardware &amp; Laptops
---

### Post by David Haas on 2005-05-03
I'm running 5.10. On opening the CD Player, I get a "drive error" message. Claus Cyrny, who had the same problem, said he solved it by making a symbolic link to /dev/hdc: ln -s /dev/hdc /dev/cdrom. With this made, the CD Player works fine. But this link disappears when the computer is turned off. So, on re-starting, this link must be re-written. I see that in /.dev there is a symbolic link to /dev/hdc:  cdrom -> /dev/hdc. This, however, does not seem to be the proper connection for the CDROM. Can anyone explain this situation and offer a permanent fix?   
David

---

### Post by David Haas on 2005-05-04
Woops--To give credit where it's due, it was Wulf Forrester-Barker who recommended the symlink to get the CD Player working. So, now it works, but as stated above, the link doesn't stick, but disappears when the computer is turned off. So, why is this, and what can be done to correct it? Wulf, are you there? Do you too have this problem. It's not a big deal, but it's worth correcting.
David

---

