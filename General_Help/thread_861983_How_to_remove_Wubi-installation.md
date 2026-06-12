---
title: "How to remove Wubi-installation?"
date: 2008-07-17
forum: General Help
---

### Post by pointyblue on 2008-07-17
I installed Ubuntu with Wubi from Vista on my laptop.

Can anyone tell me how to remove it?

There's no "uninstall Wubi" in Add/Remove programs in the Vista control panel...

---

### Post by ago on 2008-07-17
There should be Uninstall "Ubuntu" not "Wubi". And in any case there should be an uninstaller in c:\ubuntu. Note that if you used Wubi rev 505 you will need the uninstaller in [https://wiki.ubuntu.com/WubiGuide#head-61fe7beb6f9507b384ce19642d3dcb697b19aeb1](https://wiki.ubuntu.com/WubiGuide#head-61fe7beb6f9507b384ce19642d3dcb697b19aeb1)

---

### Post by pointyblue on 2008-07-17
There was no Uninstall Ubuntu either, but I found an uninstaller in the computer's d: partition - and that fixed it.

Thanks for helping out! ):P

---

### Post by pointyblue on 2008-07-17
OOPS!

Guess I didn't quite fix this problem after all... :(

Even though the uninstaller has removed all the ubuntu files from the computer I'm still asked if I want to boot Vista or Ubuntu when I start the computer .. pretty weird.

Do you know how to fix this?

---

### Post by ago on 2008-07-17
You can use EasyBCD for that. There should be a wubi log in your user temp folder, please post it.

---

### Post by pointyblue on 2008-08-18
Finally found the time to look at this problem again.

Installed and used EasyBCD to fix the problem. Thanks again.

:-)

---

### Post by azurehi on 2010-05-02
How will EasyBCD work with windows XP in removing wubi?

---

### Post by nichos on 2011-07-16
Thanx for that,

unfortunately they did not answer the Question if it works on XP.

---

