---
title: "HP Probook 4250s driver issue"
date: 2011-07-12
forum: Hardware
---

### Post by StuffSauce on 2011-07-12
I recently installed Ubuntu 11.04 on my HP Probook 4250s, I need to get ahold of some proper drivers for the wireless card and the synaptics touchpad. The wireless on-off button on the keyboard flashes from white to orange and I can't connect to the internet. And the touchpad wont do hardly anything right. I'll appreciate the help!

---

### Post by StuffSauce on 2011-07-12
Anyone??

---

### Post by StuffSauce on 2011-07-13
For anyone else with this problem, I figured it out. The wireless card on the laptop is an rt3090PCIe, by Ralink. To fix the issue you need to add rt2800pci to the end of the blacklist.conf file.

---

