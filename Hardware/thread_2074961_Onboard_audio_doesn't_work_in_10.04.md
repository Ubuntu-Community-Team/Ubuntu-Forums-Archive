---
title: "Onboard audio doesn't work in 10.04"
date: 2012-10-22
forum: Hardware
---

### Post by Linuxguy348 on 2012-10-22
Title says it all! I don't know what to do, I don't know my Motherboard's name either. Would upgrading to 12.04 help?

---

### Post by gordintoronto on 2012-10-23
Upgrading might help. Every recent version has improved the audio support, mostly due to improvements in the kernel.

If you posted the result from the terminal command lspci, it might help people to help you.

---

### Post by myromance123 on 2012-10-23
Changing to Ubuntu 12.04 may or may not help your situation. 12.04 is very stable in my personal experience.

Alright, first lets check what your onboard sound card is.
Go to the Ubuntu Dash (or press the Windows button). Search for Terminal.
Now in that terminal type this and hit Enter:
```
aplay -l
```

This will list your sound device(s).
Paste the outcome here so we can see it.
It's very likely that you have a Realtek sound card of some kind, but I could be wrong. If its Realtek,  then the current drivers on their website are pretty easy to install.

---

