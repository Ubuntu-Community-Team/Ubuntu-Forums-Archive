---
title: "ubuntu partition effecting windows recovery"
date: 2010-07-27
forum: Hardware
---

### Post by Femster88 on 2010-07-27
after failing to partition correctly to install ubuntu on my pc, i tried to recover my software and restore it to its original factory settings. In doing so, an error message 0xe0ef0003 popped up and now i can not even make it to the log in screen of windows...Assistance please****

---

### Post by Grenage on 2010-07-27
Did you remove the recovery partition?  If you boot up with a live CD and run Gparted - what is your structure?

---

### Post by Femster88 on 2010-07-27
I used a USB with Ubuntu on it to load it on my labtop...Last time i did it on my other labtop, it showed on the "prepared disk space" portion when i partitioned it that i could use side-by-side format and regulate how much i would share with Windows and ubuntu...Now on this labtop it only has the manual option or the entire disk option...when i did manual, i partitioned 160Gb from Windows to use for ubuntu...when i did that it created free space for 160Gb...once i did that i couldnt move on so i placed the 160gb back to the original Windows loader...set my boot order to its original settings and now i cant go into windows at all...i cant reset the software to it factory settings either...it gives me two codes of error...1 is 0xE0EF0009 Null input string...the other is error code 0xe0ef0003...Honestly i just want to get my labtop back to its normal settings and for everything to work properly

---

### Post by Grenage on 2010-07-28
Did you resize partitions during the Ubuntu install, or did you simply delete and recreate the partitions?  I wasn't aware it supported resizing.

---

