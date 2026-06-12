---
title: "Exec script when Wacom is hot-plugged"
date: 2010-01-09
forum: Hardware
---

### Post by kkjaergaard on 2010-01-09
Is it possible to execute a script when hardware gets plugged into the computer?

In this case, I want to execute a script when my Wacom Bamboo One gets plugged into my computer, so is it a matter for x.org forums?

---

### Post by Favux on 2010-01-09
Hi kkjaergaard,

I think you should be able to do it by modifying the udev rule for your Bamboo in wacom.rules.  See:  [http://reactivated.net/writing_udev_rules.html#external-run](http://reactivated.net/writing_udev_rules.html#external-run)

You could also take a look at the HAL spec.:  [http://www.marcuscom.com/hal-spec/hal-spec.html](http://www.marcuscom.com/hal-spec/hal-spec.html)

---

### Post by kkjaergaard on 2010-01-09
I did edit the file /lib/udev/rules.d/40-xserver-xorg-input-wacom.rules. Here is the diff:

```
67c67
< ATTRS{idVendor}=="056a", ATTRS{idProduct}=="0069", SYMLINK+="input/tablet-bamboo1", RUN+="/usr/local/bin/set-wacom-ar"
---
> ATTRS{idVendor}=="056a", ATTRS{idProduct}=="0069", SYMLINK+="input/tablet-bamboo1"
```

Here is the script set-wacom-ar:

```
#!/bin/sh

xsetwacom set "Wacom Bamboo1" TopY 261
xsetwacom set "Wacom Bamboo1" BottomY 3451
xsetwacom set "Wacom Bamboo1 cursor" TopY 261
xsetwacom set "Wacom Bamboo1 cursor" BottomY 3451
xsetwacom set "Wacom Bamboo1 eraser" TopY 261
xsetwacom set "Wacom Bamboo1 eraser" BottomY 3451
xsetwacom set "Wacom Bamboo1 pad" TopY 261
xsetwacom set "Wacom Bamboo1 pad" BottomY 3451
```

This does not work. The script does run, but it has no effect. If I run the script manually after connecting the Wacom, it works as expected.

How can I make sure the input devices "Wacom Bamboo1{| cursor| eraser| pad}" are available when the script executes?

---

### Post by Favux on 2010-01-09
Hi kkjaergaard,

OK, I see.  You are using the default linuxwacom.fdi.  Have you configured through wacomcpl and it's .xinitrc script?

When using HAL/.fdi you have to use the info.callout to hal-setup-wacom to append the sub-devices.

See [post #176]("http://ubuntuforums.org/showpost.php?p=7234134&postcount=176") on the "Wacom tablets in Ubuntu guide/howto".  It has a modified linuxwacom.fdi so wacomcpl works and a link to setting up wacomcpl and it's .xinitrc.

---

### Post by kkjaergaard on 2010-01-09
> **Favux said:**
> Have you configured through wacomcpl and it's .xinitrc script?

No. I've made no permanent configuration changes.

> **Favux said:**
> See [post #176]("http://ubuntuforums.org/showpost.php?p=7234134&postcount=176") on the "Wacom tablets in Ubuntu guide/howto".  It has a modified linuxwacom.fdi so wacomcpl works and a link to setting up wacomcpl and it's .xinitrc.

Does that work if the tablet is not connected when Xorg starts?

---

