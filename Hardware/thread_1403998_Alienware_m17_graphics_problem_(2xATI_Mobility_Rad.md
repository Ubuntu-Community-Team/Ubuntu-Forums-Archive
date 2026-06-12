---
title: "Alienware m17 graphics problem (2xATI Mobility Radeon HD 3870 )"
date: 2010-02-10
forum: Hardware
---

### Post by joelwhrs on 2010-02-10
I have just installed Ubuntu on this laptop and everything seemed to be working fine until I tried to install a driver so that it supports desktop effects, etc. After I have installed that and boot up Ubuntu it boots to a terminal instead of the desktop. The screen flickers a few times when it is in the terminal. I have followed every tutorial that I could find to at least get it back so that I can use the gui and no luck so far. When I run the startx command I get the error that no screens were detected. I have gone through the recovery menu and ran the fix X command and it made no change. I have dual ATI Mobility Radeon HD 3870 video cards. I have it dual booted with windows 7 if that helps anything. Basically what I want to know is how to get the driver properly working or at least get it back to the original state.

---

### Post by markbuntu on 2010-02-12
What driver are you using and how did you install it?
Are these gpus for crossfire or do they run separate displays?
Did you run

aticonfig --initial

after installing the driver?

You can try

aticonfig --help

for options for setting up crossfire chains and everything else about setting up the driver/cards.

---

