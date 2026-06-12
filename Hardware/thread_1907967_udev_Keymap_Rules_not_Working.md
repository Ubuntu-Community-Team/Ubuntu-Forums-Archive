---
title: "udev Keymap Rules not Working"
date: 2012-01-12
forum: Hardware
---

### Post by Forte125 on 2012-01-12
Due to a problem with the keymaping on my Lenovo Ideapad, I created a custom keymap for udev.  The problem is that changing the rules in the 95-keymap.rules doesn't seem to do anything.  

The rule in question is: 
```
ENV{DMI_VENDOR}=="LENOVO*", ATTR{[dmi/id]product_name}=="*08862AU*", RUN+="keymap $name lenovo-ideapad-v460"
```
posted after the:
```
LABEL="keyboard_vendorcheck"

```
I am fairly sure I did everything correctly (this worked in ubuntu 10.04 LTS), but every time I log in I need to run this code in the terminal to get the correct keymap.
```
sudo /lib/udev/keymap input/event3 /lib/udev/keymaps/lenovo-ideapad-v460
```


If I understand udev correctly, the keymap should be applied at boot.

(Edit: I think that is the correct make/model)
```


cat /sys/class/dmi/id/sys_vendor
LENOVO
cat /sys/class/dmi/id/product_name
08862AU

```

---

