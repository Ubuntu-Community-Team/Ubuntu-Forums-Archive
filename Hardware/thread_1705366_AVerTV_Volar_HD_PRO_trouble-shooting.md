---
title: "AVerTV Volar HD PRO trouble-shooting"
date: 2011-03-12
forum: Hardware
---

### Post by gambang07 on 2011-03-12
I just bought a USB TV tuner - AVerTV Volar HD PRO. I found a solved trouble-shoot from:[http://forum.ubuntu-it.org/index.php/topic,384436.msg3370690.html#msg3370690](http://forum.ubuntu-it.org/index.php/topic,384436.msg3370690.html#msg3370690)
However, I got two errors:

gambang07@gambang07-System-name:~$ sudo apt-get install linux-headers-'uname -r'[sudo] password for gambang07: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package linux-headers-uname -r

[Comment: I remember I deleted some old headers...]

so I skipped that to continue but I got stuck at Step 4:

gambang07@gambang07-System-name:~/tda18218$ wget [http://xgazza.altervista.org/Linux/DVB/Drivers/patch_af9035_tda18218.diff](http://xgazza.altervista.org/Linux/DVB/Drivers/patch_af9035_tda18218.diff)
Error parsing proxy URL [http://localhost:4001](http://localhost:4001) : Bad port number.

====
I am using Ubuntu10.10 on AMD dual core 64bit 2.0GHz. 2 GRam

---

### Post by rleck on 2011-05-19
Kia ora Gambang07

run 
$uname -r 

as a separate command first to find out what kernel you are running, then use that number in place of 'uname -r' in the command on the italian site. I'm about to have a go with that myself. :P

Cheers
R

---

### Post by rleck on 2011-05-27
I finally got my AVERTV Volar HD PRo working in 10.10, using these translated ubuntu.it.org (italian) instructions at comment # 178. Grazie mille a Xgax and Nico.Laus! 

I have used bit.ly because the google-translate url is so long. (It's clean, I promise)  [http://bit.ly/lBdQKM](http://bit.ly/lBdQKM)

The following linuxtv.org page was invaluable to understanding the process, with links to the testing and set up pages, etc. It's instructions are more up to date than the older italian ones I used, but I'm still on an older distro. I used the scan utility to find my transponders, as w_scan can't cope with New Zealand's weird h264 and acc broadcast combination, apparently. (It didn't work in any case)

All other readers on Natty 11.04 and above should probably start here:

[http://www.linuxtv.org/wiki/index.php/How_to_Obtain,_Build_and_Install_V4L-DVB_Device_Drivers](http://www.linuxtv.org/wiki/index.php/How_to_Obtain,_Build_and_Install_V4L-DVB_Device_Drivers)

It uses the more up to date git media_build rather than the deprecated v4l-dvb build.

Good hunting. I'm off to watch Freeview - finally!:popcorn:

---

