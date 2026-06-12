---
title: "NDISWRAPPER WOES - belkin 56g wi-fi card does not work"
date: 2005-03-23
forum: Hardware &amp; Laptops
---

### Post by robtotheb on 2005-03-23
I have been trying to convert my brother-in-law to Ubuntu (he is not too impressed so far!  :evil: ).  I installed it on his VAIO laptop and his belkin 56g wi-fi card does not work.  I followed the tutorials on setting it up (wiki and the GID forums).  The weird thing is when I typed "ndiswrapper -l" after installing and it said "driver present, hardware present" BUT nothing show up in Networking except the Ethernet connection and I cant see any "add" options.  
Any ideas?

ps the belkin DOES shows up in Device manager.

---

### Post by Polymira on 2005-03-24
you're almost there...

as root (or sudo .. or whatever), run (without quotes): "ndiswrapper -m" ... that installs the module's & configurations...

congrats, a quick iwconfig should show your new hardware under wlan0 ... and if not, try a quick "ifconfig wlan0 up"

---

### Post by robtotheb on 2005-03-24
Still doesnt work.
When I type "ifconfig wlan0 up" its says
"Error while getting interface flags - no such device."

---

### Post by Polymira on 2005-03-24
alright, show me the output of ifconfig without any flags / options. And also, if possible, after a reboot .... give me the output of dmesg

---

