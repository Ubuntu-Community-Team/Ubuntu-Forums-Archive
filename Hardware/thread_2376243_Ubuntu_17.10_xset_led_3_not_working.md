---
title: "Ubuntu 17.10 xset led 3 not working"
date: 2017-10-31
forum: Hardware
---

### Post by vetabz on 2017-10-31
Hi,

I just upgraded to the newest version as of today November 1, 2017.... Ubuntu 17.10.

I have a keyboard with backlights and I used to turn it on and off using the xset command, particualrly xset led 3. today, i just stopped working after the upgrade.

I already tried xset led (1 to 32) nothing has worked.

How do I resolve this?

---

### Post by TheFu on 2017-11-01
X11 isn't used by default in 17.10. Wayland is.   Could that have something to do with this problem?  To test that, on the login screen, click the "gear" and select the xorg option.  Did that help?

---

### Post by ohnonotscott on 2018-01-16
> **TheFu said:**
> X11 isn't used by default in 17.10. Wayland is.   Could that have something to do with this problem?  To test that, on the login screen, click the "gear" and select the xorg option.  Did that help?

That's the thing that worked for me. So thanks for bringing it up.

---

### Post by TheFu on 2018-01-16
> **ohnonotscott said:**
> That's the thing that worked for me. So thanks for bringing it up.

X11 has lots and lots of issues, but it has been around a very, very, very, very long time, so most programs work with it.  Wayland is relatively new and it will take years for things to catch up, especially things that most people don't do. Wayland doesn't address network-based displays, for example.  It isn't something they care about.

---

