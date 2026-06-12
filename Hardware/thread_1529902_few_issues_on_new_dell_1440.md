---
title: "few issues on new dell 1440"
date: 2010-07-12
forum: Hardware
---

### Post by ut40755 on 2010-07-12
so i got a new dell inspiron 1440 and of course whipped it clean the second i got it and dual booted win7 and ubuntu like all my pcs.  only problem is i have a few issues.  im running ubuntu 10.04 on the latest kernel (i update almost everyday):

screen brightness: iv seen this bug reported all over the place and no solutions, but i figure ill bring it up anyway.  video card is intel i950 mobile.  it pre-installed the intel graphics driver, but the acpi files all come up with <not supported> like noted elsewhere, and the brightness applet does nothing.  are there any work arounds to this?

wireless: another tough one, a broadcomm wireless chip.  it came up with a restricted driver after a while, but of course with no internet, i couldnt install it.  i went to another pc and manually downloaded it and installed it.  it works, but it does not auto load on boot.  i have to make, make install, modprobe lib80211, insmod wl.ko every time.  i then thought i could just install the restricted driver so it would be more stable.  i did, but that doesn't stay turned on either.  it comes up saying its enabled but not in use.  but after i install it manually, it says its turned on, and it seems like the wireless is now on twice.

id love to get the brightness fixed cause i mostly use ubuntu for programming and writing on a pure white screen is awful.  the wireless is a pain but it at least works.

any help is appreciated, and i can get any output u guys need (im a linux newbie so i have no idea where to even begin with what i need to report to u guys).  thanks everyone!

---

### Post by Sliiice on 2010-07-12
Alright  more info for those who care :P
 The following are known working components
Motherboard
RAM
Power adapter
DC Jack. 
Battery

I am not sure about the CPU, I think it is in working order but not sure
Or the fan.

So now my question is, does anyone think that a dead fan may be causing all of these issues?

---

### Post by Sliiice on 2010-07-12
woooooaaa. sorry, I so wasnt paying attention.

---

### Post by ut40755 on 2010-07-24
can anyone help on either of these issues?

edit:  here's whats really going on.  almost NONE of the hardware works.  ethernet, graphics driver, wireless driver needs to be installed manually on every boot, the keyboard mapping is all screwy...  can anyone help?  i understand this is new hardware but give me a break...  ill be on windows till i can fix this....

---

