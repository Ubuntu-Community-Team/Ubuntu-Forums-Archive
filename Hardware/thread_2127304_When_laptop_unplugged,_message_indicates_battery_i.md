---
title: "When laptop unplugged, message indicates battery is critically low and hibernates"
date: 2013-03-19
forum: Hardware
---

### Post by Jason F on 2013-03-19
Running Ubuntu 12.04 LTS 64-bit on Lenovo Ideapad S400. New Install on a new computer. When the computer is unplugged and battery is fully charged the computer indicates a critically low battery and hibernates. It will run fine on the battery if i resume the computer without it plugged in. Does anyone know a fix for this. I cannot remember if it did this before i ran the update manager after the install. Thank you

---

### Post by Paulo_S._P._SIlveira on 2013-09-27
Same computer... same headache. I finally found what worked for me. Take a look at [http://askubuntu.com/questions/92794/how-to-change-critically-low-battery-value](http://askubuntu.com/questions/92794/how-to-change-critically-low-battery-value). It says:

Start dconf-editor.
Browse to org->gnome->settings-daemon->plugins->power.
Change the values of *percentage-critical* and *percentage-action* to the level you require.
And change *use-time-for-policy* to false

I just had to install dconf through Ubuntu Software Center to find the way. All the percentages were ok. I turned *use-time-for-policy* to false and restarted the session. Working fine now. Enjoy... it is always good to remove Windows from a computer. 

By the way, before I intended to remove Windows (it is my 77-year-old, mother-in-law computer) after it gets 1060 viruses of 15 different kinds in the first week of use, I called Lenovo in Brazil asking them about warranty. To my surprise, I was told that Windows removal voids warranty... I must return to windows if I need that. You know what? I don't mind. Ubuntu is already installed and, except for this small battery glitch, it seems to recognize all peripherals ok.

---

