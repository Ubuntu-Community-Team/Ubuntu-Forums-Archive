---
title: "Keyboard is recognised, won't accept input"
date: 2015-04-19
forum: Hardware
---

### Post by Morgan_Lei on 2015-04-19
So I have a Corsair K70 RGB keyboard and it works fine in Windows, GRUB, and BIOS. However, it won't work in Linux.

Going into terminal and using the command ```
xinput list
``` I get:

```
 Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; Razer Razer Taipan                          id=9    [slave  pointer  (2)]
&#9116;   &#8627; Razer Razer Taipan                          id=10    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Razer Razer Taipan                          id=11    [slave  keyboard (3)]
    &#8627; Dell Dell USB Entry Keyboard                id=12    [slave  keyboard (3)]
    &#8627; Corsair Components, Inc. Corsair Vengeance 1500    id=8    [slave  keyboard (3)]
    &#8627; Power Button                                id=7    [slave  keyboard (3)]
    &#8627; Corsair Corsair K70 RGB Gaming Keyboard     id=13    [slave  keyboard (3)]



```

The last entry is the keyboard that I want to use. I've tried reinstalling the input drivers using ```
sudo apt-get install --reinstall xserver-xorg-input-all
``` but to no avail.

Any help would be very much appreciated :)

---

### Post by al14 on 2015-05-17
Try this--> [CKB 4 Linux]("https://github.com/ccMSC/ckb")  :mrgreen:

---

