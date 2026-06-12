---
title: "setting brightness via command line"
date: 2007-07-09
forum: Hardware &amp; Laptops
---

### Post by -emory- on 2007-07-09
Hey everyone, I'm running xubuntu on my dell inspiron 8600 laptop and, while I absolutely adore xubuntu, I've found that the battery life is less than par. In fact, if I close the screen, which should theoretically put it in standby, the battery continues to run down until it dies, usually within a few hours.  I just realized that under the battery icon properties on my toolbar it allwos me to run a command when the battery level begins to get low, and I was wondering if there is someway I can run a command that will dim my screen 50% or so when my battery begins to get lower. Thanks everyone!

---

### Post by statman88 on 2008-07-09
```
sudo echo -n "some number here" > /proc/acpi/video/VID/LCD/brightness
```

Might need to change VID to VGA if the VID directory doesn't work.

100 is the max (brightness)

---

