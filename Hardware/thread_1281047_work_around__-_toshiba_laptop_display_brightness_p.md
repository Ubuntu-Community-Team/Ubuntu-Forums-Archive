---
title: "work around  - toshiba laptop display brightness problem"
date: 2009-10-02
forum: Hardware
---

### Post by vijayckk on 2009-10-02
Hi All,

I have been playing around with various linux distro's over the years and quit due to some or the other problem, looks like ubuntu 9.04 fixed most of my h/w s/w issues except 1...  I have a toshiba satellite laptop and the brightness is blinding. After screaching thru countless posting i finally gave up till i accidently found a work aorund.

This work around needs a dual boot capability into windows. So start your laptop and boot into windows then reduce the brightness and restart the machine ( make sure to restart and not a complete shut down). Now boot into ubuntu and the brightness should stay to the level set in windows. 

Note: this needs to be performed every time the machine is completely shutdown and restarts. Hope it works for you guys. I know a lot of you are struggling with this issue.

vijay

P.S: Ubuntu Rocks :)

---

### Post by bradshawd on 2009-10-04
You need to try

sudo toshset -inten (0-7)

choose the number which will suit you best.

Hope this helps

---

