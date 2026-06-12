---
title: "Critically low battery msg after  unplugging Netbook"
date: 2011-12-22
forum: Hardware
---

### Post by zahchronicler on 2011-12-22
New to Ubuntu and am liking it so far except for an issue with power/ battery management.  After unplugging my netbook I often but not always get a critically low batterylife message and ubuntu proceeds to shutdown.  This seems to happen most often after it has been plugged in for a while and the battery is definitely fully charged.   If I unplug when the indicator shows less than 100% it seems to be fine and runs down as normal.  

I have a Dell Inspiron 910 running Ubuntu 11.10

a friend helped me create a log of the events but I don't know how to interpret and he isn't familiar with ubuntu






Dec 22 00:23:43 Brian-Mini kernel: [124377.204733] [13875]     0 13875      491       24   0       0             0 anacron
Dec 22 00:23:43 Brian-Mini kernel: [124377.204747] [14047]     0 14047      684       71   0       0             0 dhclient
Dec 22 00:23:43 Brian-Mini kernel: [124377.204762] [14079]     0 14079      510       19   0       0             0 ntpdate
Dec 22 00:23:43 Brian-Mini kernel: [124377.204776] [14083]     0 14083      492       15   1       0             0 lockfile-touch
Dec 22 00:23:43 Brian-Mini kernel: [124377.204791] [14089]     0 14089      598       37   0       0             0 ntpdate
Dec 22 00:23:43 Brian-Mini kernel: [124377.204803] Out of memory: Kill process 3326 (firefox) score 605 or sacrifice child
Dec 22 00:23:43 Brian-Mini kernel: [124377.204823] Killed process 3326 (firefox) total-vm:1933588kB, anon-rss:637888kB, file-rss:0kB
Dec 22 00:24:07 Brian-Mini kernel: [124401.554434] init: anacron main process (13875) killed by TERM signal
Dec 22 00:24:07 Brian-Mini kernel: [124401.960715] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=600
Dec 22 00:24:13 Brian-Mini kernel: [124407.989361] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
Dec 22 00:25:28 Brian-Mini kernel: [124482.130110] init: anacron main process (14195) killed by TERM signal
Dec 22 00:25:28 Brian-Mini kernel: [124482.642959] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=600
Dec 22 00:26:18 Brian-Mini kernel: [124532.492373] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
Dec 22 01:05:41 Brian-Mini kernel: [126895.257968] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=600
Dec 22 01:06:05 Brian-Mini kernel: [126919.728495] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
Dec 22 01:07:11 Brian-Mini kernel: [126985.773094] [drm] Changing LVDS panel from (+hsync, -vsync) to (-hsync, -vsync)
Dec 22 01:39:51 Brian-Mini kernel: [128945.840899] [drm] Changing LVDS panel from (-hsync, -vsync) to (+hsync, -vsync)
Dec 22 01:40:06 Brian-Mini kernel: [128960.679116] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=600

---

### Post by zahchronicler on 2011-12-22
also forgot to mention that after restarting if I don't have it plugged in the battery indicates a full charge with hours of usage left

---

