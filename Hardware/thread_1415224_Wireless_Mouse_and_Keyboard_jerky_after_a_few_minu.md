---
title: "Wireless Mouse and Keyboard jerky after a few minutes"
date: 2010-02-24
forum: Hardware
---

### Post by Jeztastic on 2010-02-24
My wireless mouse and keyboard (labtec) pretty quickly get jerky and become unusable on 8.04, and 9.10. Someone suggested that the computer was repeatedly checking for new devices, and that I should add:

```
Section "ServerFlags"
option  "AutoAddDevices" "off"
EndSection

```

to my xorg.conf. Tried that, didn't work. Any other ideas?

Cheers,

Jez

edit - I hate my other keyboard, it's driving me mad and I have to write a 4000 word essay by Monday, so please help!

---

### Post by mörgæs on 2010-02-25
Have you tried other versions, for example 9.04?

---

### Post by Jeztastic on 2010-02-25
> **mörgæs said:**
> Have you tried other versions, for example 9.04?

As I mentioned on the OP, I replicated the problem in 8.04 and 9.10. Do you have a particular reason for thinking 9.04 will work?

---

### Post by mörgæs on 2010-02-25
In general 9.04 is the most bug-free release of them all, but I don't know about wirefree keyboard and mouse in particular.

Trying a 9.04 live CD could be a quick test.

---

### Post by Jeztastic on 2010-02-25
> **mörgæs said:**
> In general 9.04 is the most bug-free release of them all, but I don't know about wirefree keyboard and mouse in particular.

Trying a 9.04 live CD could be a quick test.

Yes, good plan. Bit of a faff having to reinstall by Monday though!

---

