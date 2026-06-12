---
title: "My laptop is going way too slow and geekbench result is too low"
date: 2016-08-24
forum: Hardware
---

### Post by Wanas on 2016-08-24
Last month my laptop gone way to slow in a sudden and didnt get hot as usual again, before that It always gets very hot and maybe shutdown on its own when it gets way too hot, but now my laptop it going so slow and not getting hot like before or even close when I tried geekbench to test my laptop speed the results was like in a half compared to other laptops with the same specifications anyone have any suggestions what going wrong with my laptop and how to fix it? 
Hint: My laptop fan maybe getting weak by the time.
My laptop geekbench results link: [http://browser.primatelabs.com/geekbench3/7896437](http://browser.primatelabs.com/geekbench3/7896437)
Other same laptops results: [http://browser.primatelabs.com/geekbench3/search?utf8=%E2%9C%93&q=TOSHIBA+Satellite+A500+430m](http://browser.primatelabs.com/geekbench3/search?utf8=%E2%9C%93&q=TOSHIBA+Satellite+A500+430m)

---

### Post by TheFu on 2016-08-24
Check the log files for issues.
* Fan not spinning
* loose cables
* failing components like HDDs, SSDs, USB devices, GPUs, 
* blow out the laptop to remove all dust sucked in over the years.

IF all that checks out, look for network issues. A slow DNS can cause very slow performance. Disable networking and test again is the easy way to see if DNS issues are happening.

BTW, Ubuntu 11.04 has been unsupported since 2012.

---

### Post by Wanas on 2016-08-24
how to check the log files ? can you help me ? can the log files tell me if any faulty things I have in the laptop ?
im using ubuntu mate 16.04 LTS

---

### Post by TheFu on 2016-08-24
[https://help.ubuntu.com/community/LinuxLogFiles](https://help.ubuntu.com/community/LinuxLogFiles)
[https://askubuntu.com/questions/186276/where-are-all-the-major-log-files-located](https://askubuntu.com/questions/186276/where-are-all-the-major-log-files-located)
[http://www.cyberciti.biz/faq/ubuntu-linux-gnome-system-log-viewer/](http://www.cyberciti.biz/faq/ubuntu-linux-gnome-system-log-viewer/)

That should get you started.

Log files have all the available information about the running system. It may be possible to increase or decrease the logging for each specific program, but this is usually not necessary to figure out an issue.

In short - always start with the log files for any issue on Linux/Unix.  Period.

---

