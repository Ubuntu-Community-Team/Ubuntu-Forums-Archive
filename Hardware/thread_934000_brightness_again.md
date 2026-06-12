---
title: "brightness again"
date: 2008-09-30
forum: Hardware
---

### Post by mrau on 2008-09-30
Hello,

I've visited various pages about 'setting the brightness' but it does not work. Any help or experiences very much appreciated (because the battery of my notebook is really not acceptable).

further comments:

brightness control ...
1) ... does not work with kpowersave
2) ... does not work with the (default) powermanager
3) ... does not work wth echo 30 > /proc/acpi/video/IGFX/DD01/brightness
       even though a cat /proc/acpi/video/IGFX/DD01/brightness displays the set parameter

I'm using Kubuntu 8.04: the Hardy Heron Release

and
  * 2 CPUs: CPU1 = Intel(R) Pentium(R) Dual  CPU  T2390  @ 1.86GHz @ 800.000MHz; CPU2 = Intel(R) Pentium(R) Dual  CPU  T2390  @ 1.86GHz @ 800.000MHz
  * Kernel: 2.6.24-19-generic #1 SMP Wed Aug 20 22:56:21 UTC 2008
  * Memory total: 1025272kB
  * Hostname: notebook @ 192.168.0.20
  * Network Interfaces:
        lo: 127.0.0.1
        wlan0: 192.168.0.20
  * Graphics card: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
  * Network controller: Intel Corporation 82566MC Gigabit Network Connection (rev 03)

  Attached SCSI disks:
    * Disk sdb:   (Channel: 00 ID: 00 Lun: 00)
    *   (Channel: 00 ID: 00 Lun: 00)
root@notebook:/home/mrau/inventory#    

Does anybody have any ideas?

Michael.

---

### Post by sergiom99 on 2008-09-30
Hi. try this command to set it to 50% brightness, type in Konsole:
```
xbacklight -set 50
```
(original thread: [http://ubuntuforums.org/showthread.php?t=838741&highlight=change+screen+brightness](http://ubuntuforums.org/showthread.php?t=838741&highlight=change+screen+brightness))

---

### Post by mrau on 2008-10-01
Thanks. I tried it but nothing happens. Any idea?

---

### Post by sergiom99 on 2008-10-01
what do you mean by nothing happens?
is xblacklight installed?
```
sudo apt-get install xbacklight
```

I set mine using the battery icon in the lower right corner, and set brightness level for AC and for mains powered.
Works just fine.
Good luck.

---

### Post by mrau on 2008-10-02
Sorry. I was not clear enough. I installed it but using it nothing happens.

---

### Post by sergiom99 on 2008-10-02
wow, sorry dude, I dont know what else to tell you.
I just configure it from Kpowermanager or whatever the 'battery-icon' is called.

---

### Post by mrau on 2008-10-02
thank you anyhow. maybe I will figure out at some day.

---

### Post by advisor on 2009-03-08
you should try other number when you type in the code xbacklight -set 50. try xbacklight -set 30 or xbacklight -set 40, and you should you the difference. but be careful not to make the number so lower that you maybe unable to see the screen.

---

