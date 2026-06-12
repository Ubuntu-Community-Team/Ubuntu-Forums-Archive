---
title: "ttyl 1-6 is blank"
date: 2008-11-29
forum: General Help
---

### Post by cLtmstr on 2008-11-29
Hey, when I try to switch to ttyl 1-6 (CTRL+ALT+F1/F2/F3/etc) all I get is a blank screen. But when I change back to ttyl7 everything suddenly works again. And yes, I've tried rebooting my computer!

I run the newest Ubuntu version downloaded yesterday.

Thanks in advance,
cLtmstr

---

### Post by iponeverything on 2008-11-29
> **cLtmstr said:**
> Hey, when I try to switch to ttyl 1-6 (CTRL+ALT+F1/F2/F3/etc) all I get is a blank screen. But when I change back to ttyl7 everything suddenly works again. And yes, I've tried rebooting my computer!

I run the newest Ubuntu version downloaded yesterday.

Thanks in advance,
cLtmstr

tty7 is where your X session is.

8.10 might need the framebuffer driver (uvesafb/v86d) for you to see the consoles on your other vty's.

---

### Post by cLtmstr on 2008-11-29
I know that ttyl7 is my X session. But the curious thing is that all the other ttyl's has worked before. They just suddenly stopped working :S

---

### Post by cLtmstr on 2008-12-03
No one knows?

---

### Post by philinux on 2008-12-03
Hiya, just tried accessing tty 1-6. Same here, I get a blank screen with distorted colours at the top.

Must be a new bug from an update maybe.

[edit] Doh, I was on Jaunty testing and got carried away there.
Just rebooted to Intrepid and tty's are fine.

---

### Post by cLtmstr on 2008-12-05
How to switch to intrepid?

---

