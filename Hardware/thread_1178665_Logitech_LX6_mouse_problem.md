---
title: "Logitech LX6 mouse problem"
date: 2009-06-04
forum: Hardware
---

### Post by teejcee on 2009-06-04
I've recently installed a Logitech LX6 mouse. This is connected to a kvm switch which has a mix of systems connected...jaunty, vista, xp.

The mouse works fine on jaunty until I switch to, say, the vista box. When I switch back to jaunty, the mouse still works, sort of... ie the buttons work fine but I've lost scroll wheel functionality.

The previous mouse was a MS wireless and it did not encounter this problem.

Any help would be greatly appreciated.

---

### Post by teejcee on 2009-06-05
Bump...

---

### Post by teejcee on 2009-06-07
This issue is now SOLVED, however, I cannot find where/how I flag the thread as such. Nor can I find how to thank someone for the answer, so thanks to **stevux** for this answer

> October 24th, 2007, 06:33 AM

sudo rmmod psmouse
sudo modprobe psmouse rate=100 proto=imps



---

