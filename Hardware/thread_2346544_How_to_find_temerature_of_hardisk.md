---
title: "How to find temerature of hardisk ?"
date: 2016-12-16
forum: Hardware
---

### Post by 1ritesh on 2016-12-16
Hello,
 i get to know that there is temperature sensor in harddisk so, i want to know how to know in ubuntu??

---

### Post by a.c.m on 2016-12-16
Hello,

install hddtemp (sudo apt-get install hddtemp) and do: hddtemp /dev/sdX, where X is your device.

For example:

hddtemp /dev/sda
/dev/sda: WDC WD20EARS-00MVWB0: 43°C

---

### Post by 1ritesh on 2016-12-16
OK it is working what is the use of it?[ATTACH=CONFIG]272724[/ATTACH]

---

### Post by a.c.m on 2016-12-16
What do you mean "what is the use of it?" ?
If you want to know your HDD's temp, you do that :)
From your screen, it shows that your seagate HDD's temperature is 37 degrees celsius.

---

### Post by QIII on 2016-12-16
Hello!

Are you asking how to use hddtemp without using the terminal each time?

---

### Post by 1ritesh on 2016-12-17
how to check temperature in window 7??

---

### Post by QIII on 2016-12-17
Windows 7 is a different OS and any questions you may have regarding it should be asked [here]("https://ubuntuforums.org/forumdisplay.php?f=170").

---

