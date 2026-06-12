---
title: "Wireless internet on hp tx2z laptop"
date: 2010-03-14
forum: Hardware
---

### Post by vizzle on 2010-03-14
Hello

I have a hp tx2z laptop.  I was able to get wired internet to work but im having issues having my wireless to work.  Can any help find a way to get the wireless internet to work?

Thank you

---

### Post by Ayuthia on 2010-03-14
Have you tried going into System->Administration->Hardware Drivers and activating the Broadcom STA driver?

---

### Post by dyslexia on 2010-03-14
That works for the live CD, for some reason it fails in the installed version.

Was a little bit tricky:

(1) in administration -> software sources
    make sure the "Installable from CD ROM" option is check-marked
(2) in administration -> synaptic
     type bcmwl in the search box
     and then check the available matching items "for install" .
(3) click 'apply', wait till finished.   Wireless should be available on reboot.

---

