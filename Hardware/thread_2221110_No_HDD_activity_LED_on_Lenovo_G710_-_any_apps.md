---
title: "No HDD activity LED on Lenovo G710 - any apps?"
date: 2014-04-30
forum: Hardware
---

### Post by NTL2009 on 2014-04-30
Like the title says, my new  Lenovo G710 has no HDD activity LED. Is there an app that will provide this in a panel (I'm running Xubuntu trusty if it matters)?

I'm talking about the software equivalent of the hard drive activity LED - something that would always be running, and display activity in near real time. So if I notice things running slow, I want to just glance up and see if the HDD activity 'LED' is on/flashing. Or if I see it flashing when I don't think there should be any drive activity, I know to look into it.

I did a fair amount of searching, and didn't seem to come up with anything.

TIA - NTL2009

---

### Post by ajgreeny on 2014-04-30
You can do this with conky but it's on the desktop not the panel by using the configuration that will show you cpu% and the processes using the cpu at any moment.  Here's what I use for that information along with a lot of other configuration for other info.
```
CPU1 ${color #FFA500}${cpu cpu0}% ${cpubar cpu0}${color #FFFFFF}
CPU2 ${color #FFA500}${cpu cpu1}% ${cpubar cpu1}${color #FFFFFF}
CPU3 ${color #FFA500}${cpu cpu2}% ${cpubar cpu2}${color #FFFFFF}
CPU4 ${color #FFA500}${cpu cpu3}% ${cpubar cpu3}
${cpugraph 20,320}${color #FFFFFF}
#Process CPU & MEM Usage${hr 2}        
Processes $alignr CPU%   MEM%   PID
 ${top name 1}  $alignr ${top cpu 1}  ${top mem 1}  ${top pid 1}
 ${top name 2}  $alignr ${top cpu 2}  ${top mem 1}  ${top pid 2}
 ${top name 3}  $alignr ${top cpu 3}  ${top mem 1}  ${top pid 3}
 ${top name 4}  $alignr ${top cpu 4}  ${top mem 1}  ${top pid 4}
```
It is not the easiest job to make a configuration file for conky that fits your requirements, but there are lots of examples around the web that show different desktop info being shown.  The simplest way to learn is to get one of those examples and see what it produces, then play around and edit that file bit-by-bit to see what changes it makes to what's displayed.  There is even a huge conky thread on this forum but it is almost unsearchable in my opinion; nevertheless have a look to see if it helps.
[http://ubuntuforums.org/showthread.php?t=281865&highlight=conky+thread](http://ubuntuforums.org/showthread.php?t=281865&highlight=conky+thread)

---

