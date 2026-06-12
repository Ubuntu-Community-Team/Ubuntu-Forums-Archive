---
title: "Btusb creates high power consumption"
date: 2020-03-23
forum: Hardware
---

### Post by snowgepard on 2020-03-23
Hi, 

Im running a Dell Precision 5530 with Intel 9260 combined WiFI and Bluetooth cards. 
Lately I had the feeling that my battery runtime went really bad and indeed the fans where running quite often. With powertop I found out that the service ```
btusb
``` consumes almost 13-15 W constantly. 
I know that I could just kill the process, but this would not solve my issues, since I use Bluetooth for my mouse.
Is there a way to fix this issue? 

I guess btusb might be part of the kernel and there might not be an easy remove, reset and reinstall approach.

---

