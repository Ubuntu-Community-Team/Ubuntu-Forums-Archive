---
title: "NVidia GTX 750 not working under Ubuntu 16.04"
date: 2017-05-11
forum: Hardware
---

### Post by King_of_Nomads on 2017-05-11
Hey people of this awesome forum,

I've got trouble getting my NVidia GTX 750 Ti to work on Ubuntu (on both 14.04 and 16.04).
My PC is a PowerEdge rack server.
After installing Ubuntu (I've tried 14.04 and 16.04, same problems) as dualboot with Windows 10 I can only use my motherboard's VGA port, not my NVidia GPU's connectors.
On the one screen that is connected to the motherboard's VGA port I can see the Ubuntu login screen. When I try to login, however, the screen turns black and the login screen opens again.
I can CTRL+ALT+F1 and login to the terminal.

During the installation of Ubuntu the screen connected to the motherboard's VGA port is displaying a single console line and the installation menu is dislayed on my other two monitors that are connected to my NVidia GPU (screens are duplicated, they both show the same), but after the installation Ubuntu doesn't use them anymore.

Things I have tried:
- Installing NVidia drivers from the PPA.
- Installing the drivers from the NVidia website via wget in terminal.
- Everything I could find that might be a solution from several forums.

Any help would be greatly appreciated.

---

### Post by howefield on 2017-05-11
Thread moved to the "*Hardware*" forum for a better fit.

---

### Post by King_of_Nomads on 2017-05-11
Thank you. I am new to this forum so I wasn't sure in which category to post this.

---

### Post by mte2 on 2017-05-11
Is it possible to disable the onboard graphics or init the external video as priority from the BIOS?

Mark

---

### Post by King_of_Nomads on 2017-05-12
@Mark thanks for your reply.
Unfortunately, if I would do this I wouldn't be able to access the BIOS anymore.
I'm running a PowerEdge R720XD and it has a lengthy startup procedure so without a screen I can't really time keys. It also has a custom BIOS so I can't lookup keys on the internet to blindly use the BIOS.
It officially has no support for external GPU's, so that's why I'd rather not try that. The external GPU works like a charm under Windows 10 though.
I will search for an option to give the external GPU priority.

---

### Post by King_of_Nomads on 2017-05-12
I decided to try disabling the internal GPU and it worked!
The startup screen is showing via my external GPU, I can access the BIOS via it, Ubuntu displays on all screens and I don't have the login loop anymore.
I've been messing with this for almost a week now.
Thanks a thousand times over!

---

### Post by SeijiSensei on 2017-05-13
[wrong thread]

---

