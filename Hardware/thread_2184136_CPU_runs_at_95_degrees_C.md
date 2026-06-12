---
title: "CPU runs at 95 degrees C"
date: 2013-10-27
forum: Hardware
---

### Post by acodea on 2013-10-27
Is there a way to undervolt or slow down the cpus bus so that I don't harm my laptop? I have a l Core2 duo Intel 2.17 g. cpu with a single fan and running O/S Ubuntu Precise 12.04 LTS. I spend hours at the laptop sometimes and like this minute, the temperature therefore has the stress of just Chromium. Even if I could adjust the browser to run at 16bit could that help?

---

### Post by tgalati4 on 2013-10-27
95C will shorten the life of the CPU.  Shutdown will happen at 100 or 110C.  Your machine should probably run at 70C with maximum load.  I would suspect you have a loose heatsink or the heat paste is old and needs to be renewed.  There is a way to undervolt Intel CPU's, but that won't help in this case.  You have a mechanical problem that needs to be fixed right away.

Undervolting causes the current to increase which can actually increase the temperature for certain workloads, so it is not recommended for this problem.  Perhaps in the BIOS there is a way to declock (slow down) the processor.  Also *cpufreqd* and a panel application that allows you to select the processor speed (to 800 MHz) would be needed to get enough reduction.

---

### Post by acodea on 2013-10-27
>  Also *cpufreqd* and a panel application that allows you to select the processor speed (to 800 MHz) would be needed to get enough reduction.
!
I have installed cpufreqd and am looking in to building a gui. There is just so little in the way of programs I can use for this distro. Somehow, 12.04 has been slipped past on this subject without taking a chance on your own coding and (decoding) skills.

These outputs doesn't show anything suggesting what I may use to control cpu freq as cpufreqd install did hint at.

$ cpufreq-info
cpufrequtils 007: cpufreq-info (C) Dominik Brodowski 2004-2009
Report errors and bugs to [EMAIL="cpufreq@vger.kernel.org"]cpufreq@vger.kernel.org[/EMAIL], please.
analyzing CPU 0:
  driver: acpi-cpufreq
  CPUs which run at the same hardware frequency: 0 1
  CPUs which need to have their frequency coordinated by software: 0
  maximum transition latency: 10.0 us.
  hardware limits: 1000 MHz - 2.17 GHz
  available frequency steps: 2.17 GHz, 1.67 GHz, 1.33 GHz, 1000 MHz
  available cpufreq governors: conservative, ondemand, userspace, powersave, performance
  current policy: frequency should be within 2.17 GHz and 2.17 GHz.
                  The governor "performance" may decide which speed to use
                  within this range.
  current CPU frequency is 2.17 GHz.
  cpufreq stats: 2.17 GHz:92.37%, 1.67 GHz:7.51%, 1.33 GHz:0.01%, 1000 MHz:0.11%  (82)
analyzing CPU 1:
  driver: acpi-cpufreq
  CPUs which run at the same hardware frequency: 0 1
  CPUs which need to have their frequency coordinated by software: 1
  maximum transition latency: 10.0 us.
  hardware limits: 1000 MHz - 2.17 GHz
  available frequency steps: 2.17 GHz, 1.67 GHz, 1.33 GHz, 1000 MHz
  available cpufreq governors: conservative, ondemand, userspace, powersave, performance
  current policy: frequency should be within 2.17 GHz and 2.17 GHz.
                  The governor "performance" may decide which speed to use
                  within this range.
  current CPU frequency is 2.17 GHz.
  cpufreq stats: 2.17 GHz:92.47%, 1.67 GHz:7.50%, 1.33 GHz:0.00%, 1000 MHz:0.03%  (55)
-----------------------------------------------------------------------------------------------------------------------------------------------------------
$ pstree 
init-+-NetworkManager-+-dhclient
     |                |-dnsmasq
     |                `-2*[{NetworkManager}]
     |-accounts-daemon---{accounts-daemon}
     |-acpid
     |-and
     |-atd
     |-atop
     |-avahi-daemon---avahi-daemon
     |-bluetoothd
     |-chromium-browse-+-chromium-browse
     |                 |-chromium-browse---chromium-browse---chromium-browse---+
     |                 |-chromium-browse---5*[{chromium-browse}]
     |                 `-32*[{chromium-browse}]
     |-clamd---{clamd}
     |-colord---2*[{colord}]
     |-console-kit-dae---64*[{console-kit-dae}]
     |-cpufreqd---{cpufreqd}
     |-cron
     |-cupsd
     |-3*[dbus-daemon]
     |-2*[dbus-launch]
     |-2*[dconf-service---2*[{dconf-*********]]
     |-e-addressbook-f---2*[{e-addressbook-f}]
     |-freshclam
     |-2*[gconfd-2]
     |-geoclue-master
     |-6*[getty]
     |-gnome-keyring-d---8*[{gnome-keyring-d}]
     |-gnome-shell-cal---2*[{gnome-shell-cal}]
     |-gnome-terminal-+-bash---pstree
     |                |-gnome-pty-helpe
     |                `-4*[{gnome-terminal}]
     |-goa-daemon---{goa-daemon}
     |-gsd-printer---{gsd-printer}
     |-gvfs-afc-volume---{gvfs-afc-volume}
     |-2*[gvfs-fuse-daemo---3*[{gvfs-fuse-daemo}]]
     |-gvfs-gdu-volume
     |-gvfs-gphoto2-vo
     |-2*[gvfsd]
     |-gvfsd-burn
     |-gvfsd-http---2*[{gvfsd-http}]
     |-gvfsd-metadata
     |-gvfsd-trash
     |-hddtemp
     |-irqbalance
     |-lightdm-+-Xorg---2*[{Xorg}]
     |         |-lightdm-+-gnome-session-+-deja-dup-monito---2*[{deja-dup-monit+
     |         |         |               |-gdu-notificatio---2*[{gdu-notificati+
     |         |         |               |-gnome-screensav---2*[{gnome-screensa+
     |         |         |               |-gnome-settings--+-syndaemon
     |         |         |               |                 `-3*[{gnome-settings+
     |         |         |               |-gnome-shell---5*[{gnome-shell}]
     |         |         |               |-indicator-multi---2*[{indicator-mult+
     |         |         |               |-nautilus---2*[{nautilus}]
     |         |         |               |-nm-applet---2*[{nm-applet}]
     |         |         |               |-psensor---3*[{psensor}]
     |         |         |               |-ssh-agent
     |         |         |               |-synapse---2*[{synapse}]
     |         |         |               |-update-notifier---2*[{update-notifie+
     |         |         |               |-vino-server---2*[{vino-server}]
     |         |         |               `-3*[{gnome-session}]
     |         |         `-{lightdm}
     |         `-2*[{lightdm}]
     |-master-+-pickup
     |        `-qmgr
     |-mission-control---2*[{mission-control}]
     |-modem-manager
     |-3*[mount.ntfs]
     |-mousetweaks---2*[{mousetweaks}]
     |-polkitd---{polkitd}
     |-pulseaudio-+-gconf-helper
     |            `-2*[{pulseaudio}]
     |-rsyslogd---3*[{rsyslogd}]
     |-rtkit-daemon---2*[{rtkit-daemon}]
     |-timidity
     |-ubuntu-geoip-pr---2*[{ubuntu-geoip-pr}]
     |-ubuntuone-syncd---3*[{ubuntuone-syncd}]
     |-udevd---2*[udevd]
     |-udisks-daemon-+-udisks-daemon
     |               `-2*[{udisks-daemon}]
     |-upowerd---2*[{upowerd}]
     |-upstart-socket-
     |-upstart-udev-br
     |-whoopsie---{whoopsie}
     |-zeitgeist-daemo---{zeitgeist-daemo}
     |-zeitgeist-datah---{zeitgeist-datah}
     `-zeitgeist-fts-+-cat
                     `-{zeitgeist-fts}
-----------------------------------------------------------------------------------------------------------------------------------------------------------

---

### Post by tgalati4 on 2013-10-27
There are several indicator/selectors for cpufreqd.  Choose one that works with your environment.

tgalati4@Mint14-Extensa ~ $ apt-cache search cpufreq
mate-applets - Various applets for the MATE panel
mate-applets-common - Various applets for the MATE panel (common files)
collectd-core - statistics collection and monitoring daemon (core system)
cpufreqd - fully configurable daemon for dynamic frequency and voltage scaling
cpufrequtils - utilities to deal with the cpufreq Linux kernel feature
gnome-applets - Various applets for the GNOME panel - binary files
indicator-cpufreq - CPU frequency scaling indicator
libcpufreq-dev - development files to deal with the cpufreq Linux kernel feature
libcpufreq0 - shared library to deal with the cpufreq Linux kernel feature
xfce4-cpufreq-plugin - cpufreq information plugin for the Xfce4 panel
xfce4-goodies - enhancements for the Xfce4 Desktop Environment

---

### Post by coldraven on 2013-10-28
If your laptop is several years old you probably need to clean the fan. I found a tutorial online for my HP* and the fan was half chocked with fluff. Now it runs cool.
* In my case you remove three screws underneath and then remove the keyboard to access the fan.

---

### Post by Yellow Pasque on 2013-10-28
> The governor "performance" may decide which speed to use
That's not what you want:
```
sudo cpufreq-set -g ondemand
```

Also, you want to make sure 3D is working properly for Unity, so the CPU isn't being used for graphics accel:
```
/usr/lib/nux/unity_support_test -p
```

---

### Post by acodea on 2013-10-28
> **Temüjin said:**
> That's not what you want:
```
sudo cpufreq-set -g ondemand
```

Also, you want to make sure 3D is working properly for Unity, so the CPU isn't being used for graphics accel:
```
/usr/lib/nux/unity_support_test -p
```

I checked to make sure  that hasn't changed.

The cpufreq GUI reset whenever I used it. I still use the gui, and it shows the cpufreq setting took.  
```
sudo cpufreq-set -g ondemand
```
```
/usr/lib/nux/unity_support_test -p
```[/QUOTE]

[PHP]Not software rendered:    yes
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes


Unity 3D supported:       yes[/PHP]

---

### Post by acodea on 2013-10-28
> **tgalati4 said:**
> There are several indicator/selectors for cpufreqd.  Choose one that works with your environment.

tgalati4@Mint14-Extensa ~ ```
$ apt-cache search cpufreq
mate-applets - Various applets for the MATE panel
mate-applets-common - Various applets for the MATE panel (common files)
collectd-core - statistics collection and monitoring daemon (core system)
cpufreqd - fully configurable daemon for dynamic frequency and voltage scaling
cpufrequtils - utilities to deal with the cpufreq Linux kernel feature
gnome-applets - Various applets for the GNOME panel - binary files
indicator-cpufreq - CPU frequency scaling indicator
libcpufreq-dev - development files to deal with the cpufreq Linux kernel feature
libcpufreq0 - shared library to deal with the cpufreq Linux kernel feature
xfce4-cpufreq-plugin - cpufreq information plugin for the Xfce4 panel
xfce4-goodies - enhancements for the Xfce4 Desktop Environment
```

'Tis a good list and the day is young

---

### Post by Yellow Pasque on 2013-10-28
Well, check to see what's using the CPU when it gets that hot:
```
sudo apt-get install htop
htop
```

If nothing is pegging the CPU, then you may be looking at the wrong sensor output, or the sensor's output may be suspect (or as others have suggested, it may be a dust or heatsink issue).

---

### Post by acodea on 2013-10-28
> **Temüjin said:**
> Well, check to see what's using the CPU when it gets that hot:
```
sudo apt-get install htop
htop
```

If nothing is pegging the CPU, then you may be looking at the wrong sensor output, or the sensor's output may be suspect (or as others have suggested, it may be a dust or heatsink issue).


Why is chromium and all browsers running as root? This was the first question I ask. Why is something like this close to the internet running with privileges elevated?

---

### Post by pqwoerituytrueiwoq on 2013-10-28
```
echo powersave | sudo tee /sys/devices/system/cpu/cpu*/cpufreq/scaling_governor
```
will lower temps but make the system slow
clean out the dust bunnies and make sure your cpu fan is working

---

### Post by acodea on 2013-10-28
Trying to get VM to access physical memory sooner

Testing swap file parameter: swappiness

sudo sysctl vm.swappiness=40


Adding the parameter to .sysctl.conf

gksu gedit /etc/sysctl.conf

vm.swappiness=40

---

### Post by acodea on 2013-10-28
> **pqwoerituytrueiwoq said:**
> ```
echo powersave | sudo tee /sys/devices/system/cpu/cpu*/cpufreq/scaling_governor
```
will lower temps but make the system slow
clean out the dust bunnies and make sure your cpu fan is working

How would I undo in case I need to?

---

### Post by acodea on 2013-10-28
I have installed cpufreqd but it will revert back from other settings and be running at performance settings when I check.



cat /sys/devices/system/cpu/cpu0/cpufreq/cpuinfo_cur_freq 
266000

ls /lib/modules/$(uname -r)/kernel/drivers/cpufreq/
p4-clockmod.ko speedstep-lib.ko

cat /sys/devices/system/cpu/cpu0/cpufreq/cpuinfo_cur_freq 
266000

ls /lib/modules/$(uname -r)/kernel/drivers/cpufreq/
p4-clockmod.ko speedstep-lib.ko

watch grep \"cpu MHz\" /proc/cpuinfo
Every 2.0s: grep "cpu MHz" /proc/cpuinfo                Mon Oct 28 14:34:05 2013


cpu MHz         : 2166.000
cpu MHz         : 2166.000

---

### Post by Iowan on 2013-10-28
> **acodea said:**
> Another sage with Dust Bunny advice, thanks. How would I undo in case I need to?With that kind of comment, you'll be lucky to get any more help.

---

### Post by pqwoerituytrueiwoq on 2013-10-28
> **acodea said:**
> Another sage with Dust Bunny advice, thanks. How would I undo in case I need to?

change [FONT=courier new]powersave[/FONT] to [FONT=courier new]ondemand[/FONT] or reboot

---

### Post by acodea on 2013-10-28
> **Iowan said:**
> With that kind of comment, you'll be lucky to get any more help.

lowan, I meant it friendly, really. This is not the place for comment so I'll remove it.

---

### Post by acodea on 2013-10-28
> **pqwoerituytrueiwoq said:**
> change [FONT=courier new]powersave[/FONT] to [FONT=courier new]ondemand[/FONT] or reboot

Ok.

---

### Post by acodea on 2013-10-28
> **Iowan said:**
> With that kind of comment, you'll be lucky to get any more help.

It still returns to performance after several minutes.

---

### Post by tgalati4 on 2013-10-28
Unless you logged in as root, both Firefox and Chrome will run as User:

```
whoami
```

---

### Post by tgalati4 on 2013-10-28
The workload governor will resort to performance if you have a high load.  What is the output of:

```
w
```

Your system does not seem to be running normally.

tgalati4@tpad-Gloria7 ~/Desktop $ w
 17:42:44 up 40 days,  8:21,  3 users,  load average: 0.06, 0.23, 0.18
USER     TTY      FROM              LOGIN@   IDLE   JCPU   PCPU WHAT
tgalati4 tty7     :0               18Sep13 40days  3:22m  5.25s x-session-manager
tgalati4 pts/0    :0.0             21Oct13  5:22   0.79s  0.79s bash
tgalati4 pts/1    :0.0             Thu20    0.00s  0.40s 18.63s gnome-terminal

---

### Post by acodea on 2013-10-28
> **tgalati4 said:**
> Unless you logged in as root, both Firefox and Chrome will run as User:

```
whoami
```

 ```
    me@ubuntu
```

---

### Post by acodea on 2013-10-28
> **tgalati4 said:**
> The workload governor will resort to performance if you have a high load.  What is the output of:

```
w
```

Your system does not seem to be running normally.

tgalati4@tpad-Gloria7 ~/Desktop $ w
 17:42:44 up 40 days,  8:21,  3 users,  load average: 0.06, 0.23, 0.18
USER     TTY      FROM              LOGIN@   IDLE   JCPU   PCPU WHAT
tgalati4 tty7     :0               18Sep13 40days  3:22m  5.25s x-session-manager
tgalati4 pts/0    :0.0             21Oct13  5:22   0.79s  0.79s bash
tgalati4 pts/1    :0.0             Thu20    0.00s  0.40s 18.63s gnome-terminal

```
    ~$ w
 19:40:16 up  4:55,  2 users,  load average: 1.72, 1.37, 1.30
USER     TTY      FROM              LOGIN@   IDLE   JCPU   PCPU WHAT
ooboo    tty7                      16:14    4:54m 17:20   0.40s gnome-session -
ooboo    pts/0    :0.0             19:40    0.00s  0.24s  0.00s w
ooboo@ubuntu:~$ 



```

oh, ok. then the performance resets when cpu peaks.

---

### Post by tgalati4 on 2013-10-29
If this is a dual-core system, then you are running 1 core at 100% and the other at between 30 and 70%, which will cause your system to heat up and cause the governors to react accordingly.  I don't know if the governors reset, you will have to do some more research into how they are programmed to react to CPU load.

---

### Post by acodea on 2013-10-29
I'm doing that. 

When I get another computer I will be prepared.

---

### Post by acodea on 2013-10-29
Here is the screen of my system monitor, Looks good to me. Could the swap be bigger, bigger=better?

And the PSensor. Running @ 74 deg now.

So thanks everyone. I cleared up this without the can of air, but the air comes next.

---

### Post by tgalati4 on 2013-10-30
Swap should at least equal the size of RAM (~3 GB in this case) if you want to hibernate.  Hibernate copies the RAM to disk (on the swap partition or file) then reads it back when rebooting so you get back to your work session.  It is quite a slow way to boot, so I never use it.  Swap won't improve performance.  When you use swap, you will notice a slow-down like molassas.  

Without swap (or small swap) processes will get shut down with low-memory warnings.

---

