---
title: "Problem with brightness controls"
date: 2018-05-25
forum: Hardware
---

### Post by natgwil on 2018-05-25
I recently did an upgrade of my existing installation from Ubuntu 16.04 to Ubuntu 18.04. Because it resulted in the brightness problem detailed below, I decided to try again with a complete clean install, and thought I'd try Kubuntu while I was at it.

After installing Kubuntu 18.04 on my Fujitsu AH532 I still had problems with controlling the brightness of the display. Initially I had no brightness controls at all after installation. I edited /etc/default/grub and changed the line which read GRUB_CMDLINE_LINUX_DEFAULT="quiet splash" to GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_backlight=vendor". Now I have brightness controls again in "Battery and Brightness" and I can also control it with my function keys F6 and F7. 

However there is still strange behaviour. If I put the slider up to 100% it is not very bright, it's actually maybe 70%. But if I adjust the slider down, as expected it gets dimmer, and as I reach about 10% the screen is completely dark. However when I reach 0% the screen is suddenly at full brightness!

After each reboot the screen is on the very lowest brightness setting, and I can barely see anything. I can't immediately use the function key brightness controls, because at each boot I have a little request box which asks for my password. Until I enter my password in this box I can't do anything, including adjusting the brightness. But I can barely see the box that I have to click in to enter the password!

What can I do to make the brightness slider (or the function keys) operate as they should? Thanks in advance for any suggestions.

---

### Post by kerry_s on 2018-05-26
i think it's a hardware thing, it gets the info from the hardware/bios.

i use use scripts for mine, i run them from my sound boost launcher right click.

[ATTACH=CONFIG]279857[/ATTACH]

here's the command i use for full brightness, see if it does anything for ya.

```
xrandr --output LVDS-1 --brightness 1.0
```

---

### Post by natgwil on 2018-06-04
Yes, I can use the xrandr command. It is a useful workaround, thank you for the suggestion. However it is still only a work around. It's a shame because everything worked perfectly before in 16.04.

---

