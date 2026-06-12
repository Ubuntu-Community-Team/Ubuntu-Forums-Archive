---
title: "How does Dell Inspiron 15 7000 response with Ubuntu?"
date: 2013-10-27
forum: Hardware
---

### Post by maqtanim on 2013-10-27
Hi everyone. I am planning to buy a new laptop. My older one is "Dell Inspiron 6400", which works smoothly with any versions of Ubuntu (really!!). I am planning to buy [Dell Inspiron 15 7000]("http://www.dell.com/us/p/inspiron-15-7537/pd"). Can anyone tell me how is the performance of this specific laptop in Ubuntu? 

Thanks in advance! :)

---

### Post by greatorety on 2014-10-13
As far as I can tell after testing Ubuntu 14.10 on my 7537 for over a week I'd say it works well in general but not without some issues. The first thing I noticed after the installation was a missing battery indicator (solved here: [http://dennis2society.de/main/ubuntu-14-04-doesnt-recognize-laptop-battery-dell-inspiron-15-7537](http://dennis2society.de/main/ubuntu-14-04-doesnt-recognize-laptop-battery-dell-inspiron-15-7537)), then the first time I tried suspend it didn't work but from then on no issues apart from enabling WiFi after suspend once (it was hardware-switched off). I've seen people reporting suspend works 95% of the time. Networking seems to be area for most problems as apart from that WiFi issue I had two times when a wired connection refused to work and got itself automagically straightened out after a few reboots. If one wants decent times on battery installing Bumblebee asap is a priority. 

Keyboard works (including the media keys (and there's an option in BIOS to revert to the sane Function Keys mode)) out of the box, the same with touchpad and sound. I bought a version with platter disk replaced with SSD by a vendor so I've got a hdd in a case connected through USB3 and it works fine, ditto a Logitech wireless mouse. No issues in that department.

I tested systemd but had to reconsider because it seems to incur and old Dell laptops bug where Ubuntu launches with the screen brightness set to minimum. Not user experiance breaking but irritating nonetheless.

---

