---
title: "help configuring xfree86 in hoary 5.04"
date: 2005-07-06
forum: Hardware &amp; Laptops
---

### Post by stanwebber on 2005-07-06
after reverting back to xfree86 in hoary 5.04, running *dpkg-reconfigure xserver-xfree86* does not generate a *XF86Config-4* file in */etc/X11*.  the config file must be generated somewhere since *dpkg-reconfigure xserver-xfree86* remembers my selections the next time it is run whenever i change any of the options.  i've tried *find / -name XF86Config-4 -print* to no avail

my question is how do i go about finding the config file & copy it to */etc/X11* or fix *dpkg-reconfigure xserver-xfree86* so it writes to the correct folder?  thanks

---

### Post by Xian on 2005-07-06
[QUOTE=stanwebber]my question is how do i go about finding the config file & copy it to */etc/X11* or fix *dpkg-reconfigure xserver-xfree86* so it writes to the correct folder?  thanks[/QUOTE]
If it exists it can be found. :)
Be sure to update your database first then use locate:
```
$ sudo updatedb
$ locate filename
```

---

### Post by WildTangent on 2005-07-06
slightly OT, but why did you revert to xfree86?

-Wild

---

### Post by stanwebber on 2005-07-06
i've searched extensively for *XF86Config-4* & *XF86Config* now.  if a config file is being written (doubting even more) it's under a different name.  at this point i'm guessing the xfree86 package is just plain broken & will probably never be fixed

the reason for xfree86 is xorg doesn't support my video card, period.  never has, never will

---

### Post by az on 2005-07-06
The reason it remembers your selections is that it uses debconf.  All your information is stored there so that you do not have to reenter it when you update the package.

Where did you get the xfree86 packages, and which ones did you install?  What is you card?

Also, did you use sudo or run dpkg-reconfigure as root?

---

### Post by stanwebber on 2005-07-07
i installed the *xserver-xfree86* package available from synaptic/apt-get after adding all the extra repositories in */etc/apt/sources.list*

point-of-fact i did run *dpkg-reconfigure xserver-xfree86* under the root account.  i sure as hell hope this wasn't the cause of the failure because it occurred to me to try it with sudo, but i dismissed the idea as sheer desperation

my card is a very odd ati all-in-wonder 128 pro pci.  it has a rage 128 pro ultra tf chip that is supposed to have only been on agp cards.  consequently, the card is detected as agp by the stock drivers (it even tries to use a 8mb agp aperture).  it works if i disable loading the dri module or use the vesa drivers; otherwise it's hopeless.  i use an experimental driver for xfree86 4.3.0 that allows me to enable accelleration

in any case i ended up using a knoppix cd to generate my *XF86Config-4*

---

