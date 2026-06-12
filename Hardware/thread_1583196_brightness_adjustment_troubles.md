---
title: "brightness adjustment troubles"
date: 2010-09-27
forum: Hardware
---

### Post by buckley310 on 2010-09-27
i went through a lot of effort when i first got my laptop running linux to get the brightness keys working. i found shell scripts that run whenever i press the buttons and ended up scripting something that increments or decrements the brightnes by writing to /proc/ACPI/..[stuff]../brightness but this method does not display the brightness in the top right corner when adjusted. originally that script had some fakekey commands but i tried and wasnt able to get a fakekey command that would work. when i go into power settings and adjust the brightness slider the panel does change so i know the OS is talking correctly to my hardware...is there any way through scripting to tell the OS to change brightness besides fakekey?

---

