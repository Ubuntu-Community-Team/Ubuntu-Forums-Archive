---
title: "ChangeKeyb - change keyboard layouts easily in Xubuntu"
date: 2008-10-13
forum: General Help
---

### Post by wendigo10 on 2008-10-13
A program made by me. I had a difficulty adding Hebrew on my machine, so I decided to make a program to solve this issue. Just download it to your desktop, unpack it using file-roller, enter the terminal, and type:
```
sudo changekeyb [layout1, layout2] [key1_key2]
```

For example, to use the layouts US and IL, and bind the key combination alt+shift, type 
```
sudo changekeyb us,il alt_shift
```

To see your available layouts, type **changekeyb -i** .

Then you can add the Keyboard Layout Switcher applet to the Xfce panel, and you're done. Enjoy!

_***Note 1***_ : changekeyb doesn't **ADD** layouts, it **CHANGES** them. If you have US and want *both* US and IL, you need to change to **us,il** , **NOT** just il.

_***Note 2***_ :  to see Asian/Arabic/Hebrew fonts correctly, you may need to install the packagse culmus and/or msttcorefonts.

---

