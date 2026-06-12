---
title: "Geforce 6800 and Ubuntu 9.04"
date: 2009-05-01
forum: Hardware
---

### Post by laxmidd50 on 2009-05-01
So I just installed ubuntu 9.04 on my computer and it doesnt seem to be detecting my video card at all. It is a GeForce 6800 agp, and it doesnt even show up in the hardware drivers manager.  I reinstalled already, and still nothing.  This is the first time i've installed any form of linux on this comp, so I'm not sure if it would work with an older version. Any suggestions?

---

### Post by laxmidd50 on 2009-05-04
Anyone know how to get it to recognize my video card?

---

### Post by taurus on 2009-05-04
What's the output of this command from a terminal?

```
lspci | grep VGA
```

Do you have an onboard integrated graphic controller?

---

### Post by Insomniac20k on 2009-05-04
The nVidia drivers are proprietary so they won't be installed automatically. Try going to system>administration>Hardware Drivers and see if you can enable the restricted drivers there.

EDIT: Nevermind, you indicated that you tried that.

---

### Post by laxmidd50 on 2009-05-06
typing 'lspci | grep VGA' outputs
01:00.0 VGA compatible controller: nVidia Corporation NV40 [GeForce 6800 GT] (rev a1)
So apparently it is recognizing it, but why doesnt it show up in the hardware drivers section? And it doesn't seem that its being used because i can't enable compiz effects.  Oh, and I do have an onboard graphics controller, could it be using that instead of the graphics card?

---

