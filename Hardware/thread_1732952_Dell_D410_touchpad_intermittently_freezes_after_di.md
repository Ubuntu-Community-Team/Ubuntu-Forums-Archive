---
title: "Dell D410 touchpad intermittently freezes after disabling track stick/pointing stick"
date: 2011-04-18
forum: Hardware
---

### Post by roddie on 2011-04-18
Okay, this problem is driving me absolutely crazy! My girlfriend's laptop developed a track stick fault that caused the mouse to fly across the screen.

Under Windows XP there is a Dell utility that simply allows me to disable it independent of the touch pad. In Ubuntu, I am able to disable it with xinput, but after a non-specific period of time the touchpad will freeze (including its mouse buttons). I discovered that this seems to happen at the same time as if the track stick was having its hissy fit, because if I touch the nub (after disabling it), I cannot use the pad at the same time.

Yesterday, after some digging on these forums, I came across a potential solution that involved creating an options.conf file in /etc/modprobe.d/ that would cause the touchpad and trackstick to be seen as a single, basic, PS/2 mouse. I thought it was working but, after a while, the trackstick wreaked havoc and the mouse went crazy again.

Just for clarity, I've installed the gpointing packages and made sure that there is no palm detection or disable touchpad while typing options enabled. I was running the 32 bit version of 10.10 and recently upgraded to 11.04 with no difference to the problem.

My girlfriend has now returned to the Windows partition on her laptop so I need your help to get her back to using Ubuntu!

---

### Post by wlee618 on 2011-08-15
i have the same problem with my recent D410.  drove me nuts!!!  have you find the fix yet?:(

---

