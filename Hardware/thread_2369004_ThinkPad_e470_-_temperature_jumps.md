---
title: "ThinkPad e470 - temperature jumps"
date: 2017-08-17
forum: Hardware
---

### Post by microice on 2017-08-17
[COLOR=#333333][FONT=Ubuntu]Hello.
[/FONT][/COLOR]Few days ago I bought notebook Lenovo ThinkPad e470, without OS:
[COLOR=#333333][FONT=Ubuntu]-processor: i5 (2 cores)[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]-RAM: 8gb[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]-disk: 256 GB SSD SATA III[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]-graphic cards: NVIDIA GeForce 940MX, + Intel HD Graphics 620.
[/FONT][/COLOR]I installed ubuntu 16.04. It worked silent but sometimes i heard lourder work(not much, but it could be noticed, for example when i was using PyCharm or just watching the film). I thought that it is new notebook so it should work quietly. I did some research in web and found:
[https://askubuntu.com/questions/22108/h ... -fan-speed]("https://askubuntu.com/questions/22108/how-to-control-fan-speed")[COLOR=#333333][FONT=Ubuntu] (2 answer)[/FONT][/COLOR]
[https://putokaz.wordpress.com/2011/11/0 ... kpad-t520/]("https://putokaz.wordpress.com/2011/11/02/fixing-cpu-fan-on-lenovo-thinkpad-t520/")

I did what is written there, but it started to work really loud. I decided to install ubuntu all over again. Now it works quietly, but it sometimes has temperature jumps and works very loud.
Please could you give me some advices what to do, because i'd like to it works as new.

---

### Post by Autodave on 2017-08-17
Did you install a driver for the video card? If so, where did you get it from?

If you have not installed one yet, you may want to try that. According to Nvidia's site, the newest Linux driver will work.  You can go to Settings -> Additional Drivers. Let it search and install the recommended one. Reboot and see what the fan does then.

---

### Post by microice on 2017-08-17
I've installed driver from nvidia page but i couldn't login, eveytime i have to login again. So i install driver from here: [https://askubuntu.com/questions/851069/latest-nvidia-driver-on-ubuntu-16-04](https://askubuntu.com/questions/851069/latest-nvidia-driver-on-ubuntu-16-04) (second answer). But after that my fan runs 10000RPM. So i did this again [https://askubuntu.com/questions/22108/how-to-control-fan-speed](https://askubuntu.com/questions/22108/how-to-control-fan-speed) (2 answer) and after that my fan goes once loudly, once quietly. I've change in NVIDA X Server to use Intel graphic card and now sometimes goes loud.

---

### Post by microice on 2017-09-05
I'v change this notebook for the same but without nvidia card and it is running alike. I actualized BIOS and intel microcode.

---

