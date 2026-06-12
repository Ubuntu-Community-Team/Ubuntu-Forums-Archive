---
title: "Possible solution to HDD overheating without raise your Load_Cycle_Count"
date: 2010-09-05
forum: Hardware
---

### Post by CRAZY_PALADIN on 2010-09-05
Hi, all!

I suffered from an HDD overheating with my laptop. After a whole day search, I fianlly find a solution that will prevent my HDD from oveerheating by set APM to 128(hdparm -B 128 /dev/sda), while NOT raise the Load_Cycle_Count.

The original post is here(in Chinese though) :
[http://www.linuxsir.org/bbs/thread337135.html](http://www.linuxsir.org/bbs/thread337135.html)

The idea is to write something into your HDD every 5 sec, so your HDD won't unload, thus not raise Load_Cycle_Count. Kinda nasty, but it sure works.

*Warning*  If you do not understand what this topic is about, do read this thread:[http://ubuntuforums.org/showthread.php?t=805570]("http://ubuntuforums.org/showthread.php?t=805570"), and maybe use google for more info.
The following method is only tested on Ubuntu 10.04.1 LTS.

Write a script: /usr/bin/wdisk
```
#!/bin/bash
while :
do
        echo a > /tmp/.wdisk
        sleep 5
done  

```
chmod +x the script,  and test if it works. ```
sudo hdparm -B 128 /dev/sda
``` to set your APM to 128 and run the script.

If all fine, you may add it to /etc/rc.local so it will startup.Edit /etc/rc.local and add the following line:
```
/usr/bin/wdisk &

hdparm -B 128 /dev/sda
# you may  want to change the value here. 

```

(There is a 99-hdd-ugly-fix way to change the APM permanently, but it's complicated, and it doesn't work with 10.04 anymore. I wander why not add it to the /etc/rc.local file. If you have a good reason, please DO tell me, as I'm still very new to the Linux world, and  I'm afraid to mess something up :D)

Reboot and you should be fine. DO check your Load_Cycle_Count though, in case you mess something up. Enjoy!

---

