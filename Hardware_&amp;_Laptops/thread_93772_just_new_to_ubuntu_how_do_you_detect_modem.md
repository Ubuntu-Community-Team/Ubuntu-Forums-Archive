---
title: "just new to ubuntu how do you detect modem"
date: 2005-11-22
forum: Hardware &amp; Laptops
---

### Post by jersey on 2005-11-22
i would kie to know howto detect modem,also configure it so i can get online

---

### Post by migueljacq on 2005-11-22
This is a useful option:
[http://www.ubuntuguide.org/#identifymodemchipset](http://www.ubuntuguide.org/#identifymodemchipset)

It will also tell you if your modem is compatible or not with Ubuntu. A lot of people with internal winmodems cannot get compatible drivers to use. Are you using a winmodem or a serial (external COM port) modem?

---

### Post by migueljacq on 2005-11-22
For configuration: if it all works well and you know what port your modem is on, you can run 'sudo pppconfig' from the terminal if you are on dialup and follow the steps to configure your details.

---

