---
title: "Built In Webcam not working"
date: 2024-09-06
forum: Hardware
---

### Post by matterybattery on 2024-09-06
Hello!

I have been looking for a fix to my webcam not showing up in Cheese and the default camera app. I checked via lsusb, and it's showing up in there, however neither program can detect it. I likely am missing something, as I am very new to Linux as a whole. Any ideas on how to fix this?

---

### Post by matterybattery on 2024-09-06
I just figured it out. The command 
sudo apt install linux-headers- generic
fixed my problems for anyone experiencing something similar.

---

