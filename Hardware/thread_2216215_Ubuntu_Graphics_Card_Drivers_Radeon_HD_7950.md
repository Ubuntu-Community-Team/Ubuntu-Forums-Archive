---
title: "Ubuntu Graphics Card Drivers Radeon HD 7950"
date: 2014-04-10
forum: Hardware
---

### Post by Robert_Bailey on 2014-04-10
I'm looking to see if I can find drivers for my graphics card. I'm currently taking a cmp college course and am a IT tech that has never really dabbled in Linux but it was required in my class so i've grown to enjoy Ubuntu. I'm looking to see if there is a site to find compatible grahpics card or if my graphics card works

---

### Post by Mark Phelps on 2014-04-10
> I'm looking to see if there is a site to find compatible grahpics card or if my graphics card works 

If you're able to see a desktop, then by definitions, your graphics card "works".  Ubuntu scans the hardware during install and loads the needed drivers, in this case, the default Radeon driver.

Linux is not like Windows, where the first thing you do after installing is start hunting around for drivers.

---

### Post by grahammechanical on 2014-04-10
Ubuntu comes with a utility that will find and install proprietary video drivers for our graphic adapter if we feel we can get better quality than that provided by the open source video driver that is used by default. The utility is called Additional Drivers. I exists as a separate utility in Ubuntu 12.04 but in Ubuntu 13.10 we find it in System Settings>Software and Updates>Additional Drivers tab.

And then there is the IT tech method. :) I am sorry. I just could not resist. :)

Open a terminal and run

```
ubuntu-drivers devices
```

To see all the devices that need drivers.

```
ubuntu-drivers list
```

to see all available drivers. These commands take a while to run.

```
ubuntu-drivers autoinstall
```

to install the standard available proprietary video driver. Have fun.

Regards.

---

