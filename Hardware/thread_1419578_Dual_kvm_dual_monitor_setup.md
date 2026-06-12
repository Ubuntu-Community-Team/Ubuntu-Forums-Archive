---
title: "Dual kvm dual monitor setup"
date: 2010-03-02
forum: Hardware
---

### Post by dajashby on 2010-03-02
This is a little weird. I have been using a dual monitor setup in Windows 7 for a while, and would like to share the same two monitors with my linux (kubuntu 9.10) box.  I have a couple of kvm switches, and have successfully shared one of the monitors with linux via a kvm switch (both PCs have video cards with two ports).  I decided to try using two kvm switches, with each one sharing a monitor with the two pcs.  The Windows 7 PC had no problem with this setup, but the linux pc refused to recognise that there were two monitors connected to it.  Is there any arcane configuration procedure needed to persuade linux that there are two kvm switches connected to it?  I have ordered a dual head kvm switch, but it'll probably take a while to arrive...

---

### Post by KeLa on 2010-03-02
Have you tested that both of those kvm switches works ok individually.
It may be that one of them don't work ok at all with ubuntu (all needed signals doesn't go through the switch).

---

### Post by dajashby on 2010-03-03
Yes, both switches worked with ubuntu when I used them as the only kvm in the setup. I am now using yet a third kvm which I haven't previously used with karmic but which worked with previous versions of ubuntu - this one is a Terra View model, the other two are Belkins.

---

