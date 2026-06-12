---
title: "no sound from head phone jack"
date: 2008-12-05
forum: Hardware
---

### Post by SCHWARTZMC on 2008-12-05
i have sound from the built in laptop speakers, but nothing from the headphone jack. unfortunately, i have no idea where to begin with this issue. any help would be greatly appreciated. thank you

---

### Post by milkwood on 2008-12-05
If you have the short cut of the sound control in the panel,try right click it.
And choose "open volume control",then confirm "switches" to see if "headphone detecion" is checked.
Take care:p.

---

### Post by Zorael on 2008-12-05
If milkwood's suggestion doesn't help, enter the following in a terminal.
```
$ aplay -l
```
If it says you have an Intel HDA sound chipset, chances are you need to pass a *model* to the driver to make it behave.
```
**** List of PLAYBACK Hardware Devices ****
card 0: **[COLOR="Red"]Intel [HDA Intel][/COLOR]**, device 0: ALC888 Analog [ALC888 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
```

Instructions to get you started: [http://ubuntuforums.org/showpost.php?p=5017453](http://ubuntuforums.org/showpost.php?p=5017453).

---

