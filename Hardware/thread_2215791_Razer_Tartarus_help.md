---
title: "Razer Tartarus help?"
date: 2014-04-08
forum: Hardware
---

### Post by Aaron_Sher on 2014-04-08
Can anyone suggest a way to get the Razer Tartarus working under Ubuntu 12.04? 

Thanks,
    Aaron

---

### Post by Kirboosy on 2014-04-09
I don't know if it will work properly without their proprietary software which is Windows and Mac only.

Perhaps running the following command in a terminal might give you some outputs and maybe allow you to create something that will handle the device.

```
xev
```

Just hover your mouse in the little window that appears. Then press a button on the Razer device. Hopefully it shows some output.

Hope that helps!
~Caboose

---

### Post by Aaron_Sher on 2014-04-15
> **Caboose885 said:**
> I don't know if it will work properly without their proprietary software which is Windows and Mac only.

Perhaps running the following command in a terminal might give you some outputs and maybe allow you to create something that will handle the device.

```
xev
```

Just hover your mouse in the little window that appears. Then press a button on the Razer device. Hopefully it shows some output.

Hope that helps!
~Caboose

Looks to me as if it behaves like the left half of the keyboard: Tab, Q, W, E, R on the top row, and so forth. In xev, I see no difference between pressing Q on the Tartarus and pressing Q on the main keyboard. I assume that means I won't be able to use xbindkeys (which I've also had no luck with in any other case, BTW) to make it do something different. 

So, without Razer getting their act together (which seems unlikely), I'm SOL?

Thanks,
    Aaron

---

### Post by Kirboosy on 2014-04-15
Most likely or unless there is a group of enthusiasts that create the drivers/software needed the hardware won't work to its full potential. I have a Saitek Cyborg keyboard and a RAT 7 mouse. Saitek never released any sort of drivers for the device so it works like a generic keyboard and I can't really use any of the more advanced features of the hardware under Ubuntu.

Hope that helps!
~Caboose

---

### Post by rjnicholson1591 on 2015-03-19
I understand that this is a very old thread, but this awesome guy has created a java based app called Keyboarding Master which supports several mice, keyboards and keypads recently including the Razer Tartarus along with the Orbweaver in the works! [http://sourceforge.net/projects/kbmaster/](http://sourceforge.net/projects/kbmaster/)

---

