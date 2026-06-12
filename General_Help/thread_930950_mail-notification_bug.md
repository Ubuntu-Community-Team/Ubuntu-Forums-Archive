---
title: "mail-notification bug"
date: 2008-09-26
forum: General Help
---

### Post by rozbarwinek on 2008-09-26
Hello

I have installed mail-notification 5.4.0 and it works very well until I reboot my PC.
After the reboot mail-notification is blinking and showing error.
But when I click "refresh" It work good again :|
How to fix this so I won't have to press refresh every reboot?

---

### Post by sdpimpy on 2008-09-27
I have this same problem and it´s due to mail notification checking for mail before my wireless kicks in. I would think maybe a bash script to delay the start of mail notification by 10 or 15 seconds would due the trick. I´m very new to Linux so maybe someone with more experience could explain how to do that.

---

### Post by rozbarwinek on 2008-09-27
Ok, I managed this by disabling icon blinking on errors and changing checking to 1 minute :|
I think it's a best solution for now...

---

