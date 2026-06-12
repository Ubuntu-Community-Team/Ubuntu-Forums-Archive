---
title: "Power saving in Hardy on Laptop (powertop)"
date: 2008-04-27
forum: Hardware
---

### Post by quantumkit on 2008-04-27
So basically i am not having any real problem with Hardy, but the power consumption seems to have less improvement than expected.

When I was using Gusty, the powertop always complained there is no CONFIG_NO_HZ option for the kernel (2.6.22). While I have upgraded to Hardy, I also found many options (e.g. laptop mode, etc) are not showing up...

Here are the power usage for different OS on my thinkpad

Hardy: 19~21W (powertop)
Gusty: 17~19W (powertop)
Windows Vista: 14~16W (thinkpad powermanager + undervolting)

Overall battery life is around 3~3.5 hours

Just wonder where does the options in the powertop goes? are they all implicitly enabled in Hardy now?

I was expecting the new ubuntu has great improvement on battery life since using the new kernel (according to lesswatts.org). But this is not the case (yet).

---

### Post by acron1 on 2008-04-27
> **quantumkit said:**
> So basically i am not having any real problem with Hardy, but the power consumption seems to have less improvement than expected.

When I was using Gusty, the powertop always complained there is no CONFIG_NO_HZ option for the kernel (2.6.22). While I have upgraded to Hardy, I also found many options (e.g. laptop mode, etc) are not showing up...

Here are the power usage for different OS on my thinkpad

Hardy: 19~21W (powertop)
Gusty: 17~19W (powertop)
Windows Vista: 14~16W (thinkpad powermanager + undervolting)

Overall battery life is around 3~3.5 hours

Just wonder where does the options in the powertop goes? are they all implicitly enabled in Hardy now?

I was expecting the new ubuntu has great improvement on battery life since using the new kernel (according to lesswatts.org). But this is not the case (yet).

How do you determine how many watts you are using with powertop?
Thanks

---

### Post by quantumkit on 2008-04-27
If you are using battery, powertop will show the power consumption and the remained battery life, i.e.
```
sudo powertop
```

---

### Post by ethanay on 2008-05-03
I believe that the Ubuntu team has implemented some of powertop's suggestions.  It's also been reported (don't have the links handy) that at least a few of powertop's suggestions are bogus or irrelevant.

I'm just getting into power optimization, but I'm finding oddly that powertop is reporting MORE cpu wakeups from idle in Hardy, yet less overall power consumption and longer times in deeper sleep states.  Weird.

---

### Post by schmolch on 2008-05-03
Are you guys getting the usb informations from powertop?
I dont and i dont know why.

I also have trouble with usb (uhci_hcd), since Hardy one of my 2 cores is always in C2 unless i unload uhci_hcd manually.

---

