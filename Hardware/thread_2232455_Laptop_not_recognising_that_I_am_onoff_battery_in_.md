---
title: "Laptop not recognising that I am on/off battery in Trusty"
date: 2014-07-02
forum: Hardware
---

### Post by inameiname on 2014-07-02
[COLOR=#333333][FONT=Lucida Grande]This is a problem that I first noticed in Saucy. Anyway, what happens is my battery seems to be somewhat ignored when I try to use my laptop solely on battery power. It will still work just fine, but when I do go on battery power, my screen does not lower in brightness or anything else changes as a result, such as what settings I have in System Settings -> Power Management.[/FONT][/COLOR]

[COLOR=#333333][FONT=Lucida Grande]To note, I also have hardinfo installed, and noticed it does not recognise my laptop has a battery. It states there is no battery on my system. In past versions, hardinfo always found my battery, and also gave me info on its particulars.[/FONT][/COLOR]

[COLOR=#333333][FONT=Lucida Grande]In all, I would just love to be able to know the capacity of my battery, and especially would love my laptop to be able to dim as it should whenever I go on battery power.[/FONT][/COLOR]

---

### Post by xc3RnbFO8P on 2014-07-02
First check this:
> upower -e
> upower -i /org/freedesktop/UPower/devices/battery_BAT1

---

### Post by inameiname on 2014-07-02
Thanks for the suggestion. The commands you gave do show my battery is being recognised. Since it works off battery and does show me it is on battery, I figured something would say it is working. It's just the packages that determine if the battery is being solely used or not when it comes to lower the screen brightness and such is the problem.

Anyway, here is the output given for those above commands. Thanks.:

```

upower -e
/org/freedesktop/UPower/devices/battery_BAT1
/org/freedesktop/UPower/devices/line_power_ACAD

```

```

upower -i /org/freedesktop/UPower/devices/battery_BAT1
  native-path:          BAT1
  vendor:               SANYO
  model:                MAL32ab
  power supply:         yes
  updated:              Wed 02 Jul 2014 01:57:25 PM MDT (3 seconds ago)
  has history:          yes
  has statistics:       yes
  battery
    present:             yes
    rechargeable:        yes
    state:               fully-charged
    energy:              45.306 Wh
    energy-empty:        0 Wh
    energy-full:         45.36 Wh
    energy-full-design:  47.52 Wh
    energy-rate:         0 W
    voltage:             12.453 V
    percentage:          99%
    capacity:            95.4545%
    technology:          lithium-ion

```

---

### Post by xc3RnbFO8P on 2014-07-02
See if this helps:
[http://askubuntu.com/questions/7485/battery-not-detected]("http://askubuntu.com/questions/7485/battery-not-detected")

---

### Post by inameiname on 2014-07-03
Thanks for the suggestion, but running 'cat /proc/acpi/battery/BAT0/info' or even 'cat /proc/acpi/battery/BAT0/info' yields no results. 
I also tried adding acpi=force onto the line GRUB_CMDLINE_LINUX_DEFAULT="" in /etc/default/grub, and rebooted, and that did nothing either.

Oh well. It isn't that big of a deal. Thanks for the suggestions.

---

### Post by xc3RnbFO8P on 2014-07-03
Check if got this installed:
> sudo apt-get install indicator-power

---

### Post by inameiname on 2014-07-03
I do not have 'indicator-power' installed. However, is it for Unity? If so, I do not use Unity. 

To install that package, it requires the following to be installed as well:

unity-control-center gnome-control-center ubuntu-system-settings xfce4-power-manager

---

### Post by xc3RnbFO8P on 2014-07-03
What did you install , Xubuntu?
Otherwise it is no harm to install them.

---

### Post by inameiname on 2014-07-11
I see. I actually use Linux Mint. But I figured my issue is not necessarily a Linux Mint distro issue, but a Ubuntu and Ubuntu-distro one.

---

