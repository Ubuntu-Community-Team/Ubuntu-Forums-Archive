---
title: "how to diagnose intermittent freeze"
date: 2021-03-13
forum: Hardware
---

### Post by bitrat2 on 2021-03-13
hi, 

I wonder if anybody has some advice as to where to look for clues to solve an intermittent freeze of the ubuntu os on a desktop.  it sometimes but not always reboots w/ alt-sysreq-u/alt-sysreq-b (not that I consider that a solution).  otherwise a power cycle is reqd.

it's probably to do with memory, expecially the memory hogging firefox with too many tabs open.  if anyone has a way of running firefox so that it is denied alloc over a limit, that would be good too.

[SIZE=2][SIZE=2]I tried this on firefox...
```
systemd-run --user --no-block -p MemoryHigh=1G /home/xxxx/opt/firefox-77.0.1/firefox/firefox 
```
but it doesn't have any effect.  should it?

last time I ran it, [/SIZE]Memtest86+ didn't show any memory faults.[/SIZE]

I tried wayland and xorg, doesn't seem to make a difference.

also, can't log in from another machine, so I assume it's not just the UI.

I'm about to reinstall the os, and might use debian  and xfce instead.  questions, comments, criticisms?

also, I don't like snap.  I like AppImage.

Sorry for this portmanteau post.  my real question is, might there be any logs that could offer a clue as to what's freezing my machine?  nothing in dmesg.


```

~$ inxi -F
System:    Host: xxxx Kernel: 4.15.0-136-generic x86_64 bits: 64 Desktop: Gnome 3.28.4
           Distro: Ubuntu 18.04.5 LTS
Machine:   Device: desktop Mobo: Gigabyte model: Z97-HD3 v: x.x serial: N/A BIOS: American Megatrends v: F6 date: 06/11/2014
CPU:       Quad core Intel Core i7-4790 (-MT-MCP-) cache: 8192 KB
           clock speeds: max: 4000 MHz 1: 1780 MHz 2: 1479 MHz 3: 1514 MHz 4: 1299 MHz 5: 1278 MHz 6: 1376 MHz
           7: 1559 MHz 8: 1459 MHz
Graphics:  Card: NVIDIA GM107GL [Quadro K2200]
           Display Server: x11 (X.Org 1.19.6 ) driver: nvidia Resolution: 1920x1080@60.00hz
           OpenGL: renderer: Quadro K2200/PCIe/SSE2 version: 4.6.0 NVIDIA 390.141
Audio:     Card-1 Intel 9 Series Family HD Audio Controller driver: snd_hda_intel
           Card-2 NVIDIA Device 0fbc driver: snd_hda_intel
           Sound: Advanced Linux Sound Architecture v: k4.15.0-136-generic
Network:   Card-1: Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller driver: r8169
           IF: enp3s0 state: up speed: 100 Mbps duplex: full mac: fc:aa:14:57:6d:9e
           Card-2: Qualcomm Atheros AR2417 Wireless Network Adapter [AR5007G 802.11bg] driver: ath5k
           IF: wlp5s0 state: down mac: 64:70:02:93:62:53
Drives:    HDD Total Size: 4500.8GB (28.8% used)
           ID-1: /dev/sda model: ST3250318AS size: 250.1GB
           ID-2: /dev/sdb model: ST3250318AS size: 250.1GB
           ID-3: USB /dev/sdc model: Elements_SE_2623 size: 2000.4GB
           ID-4: USB /dev/sdd model: Elements_SE_2623 size: 2000.4GB
Partition: ID-1: / size: 229G used: 167G (77%) fs: ext4 dev: /dev/sdb1
RAID:      No RAID devices: /proc/mdstat, md_mod kernel module present
Sensors:   System Temperatures: cpu: 29.8C mobo: 27.8C gpu: 40C
           Fan Speeds (in rpm): cpu: N/A
Info:      Processes: 382 Uptime: 4:24 Memory: 6139.1/15990.9MB Client: Shell (bash) inxi: 2.3.56 

```

---

### Post by guiverc on 2021-03-13
If it's not rebooting with SysRq commands (*direct to the kernel*), I'd starting thinking of blaming your hardware, and check your PSU, motherboard (*cap scan*) etc. as I doubt switching OS would change anything (*not to another GNU/Linux anyway after all the kernel is not responding*).

I have issues too with firefox, but it's extensions that cause ram leaks (*if I run firefox without the extensions no issues arise, but I want those extensions*).  I usually leave a `htop` active so I can detect the issue, and shutdown `firefox` (& `chromium` as it has the same issue with those same extensions) before it gets too bad. I wait until the OS has cleared the RAM & then restart the browser(s).

I would validate your motherboard using *live* media using another OS, different kernel stack at a minimum, but I'd likely use a non-Ubuntu (ie. something very different is my normal choice).

Issues where SysRq respond, and don't respond have likely a different cause in my experience, unless that inconsistency is the common denominator,  ie your hardware (*at least how I read it right now*).

FYI:  *If it's your UI/GUI, the SysRq keys will always work.  The normal REISUB command used to safely reboot a system includes taking back control over X*

---

### Post by TheFu on 2021-03-13
guiverc has some good ideas above.

Logs are in /var/log/.  Check those.  If they are wiped between reboots, there's a setting to keep them in the journald.conf file.

Running out of RAM will lock up any Unix system, so don't let that happen.  Pay attention to the system. If it starts getting sluggish, close at least 1 large application - probably one of the AppImages, since those are likely to use much more RAM than normal installed applications. If you can't "feel" the system getting slower, you'll need more swap. Put it on slower storage, so the feel can happen.  Too much swap is bad, so only use the amount you need to get the feel.

If you didn't run memtest for over 12 hrs, you didn't really test it.

If it has been awhile since the system was built, it could be a cooling issue. Watch the temperatures.  Intel CPUs should just throttle before locking up.  I've had this with a 1st-gen Core i7. It would slow the hot cores as needed. Never crashed.

All sorts of hardware issues can cause lockups. A failing PSU is common, but it could be a spec of dust causing a short on the motherboard, so clean it out.  Once I had lock ups that seemed like a bad PSU - replacing it didn't help.  Turned out the GPU was failing.  

Hummmm.  Besides HDDs, I've had more discrete GPUs cause problems than anything else.  We always talk about PSUs, but that hasn't been something I see unless it totally failed, which only happened 1 time the last 30 yrs. About 10 yrs ago, there was an 50% off sale on some Seasonic PSUs, so I bought a few. Still have 1 spare. None of the others have failed. Before that, even come-with-the-case PSUs worked fine.  The Seasonic model I got is more efficient and quieter, so that is good.

---

### Post by bitrat2 on 2021-03-13
Thanks guiverc and TheFu.  I'll take all those suggestions.  :-)

I had the idea of logging some system stats (cpu temp, cpu load, free mem, etc) on a timer, then checking the logs after a freeze.  is there a tool for this?

I also wondered about following the system journal with journalctl -f and looking for alerts.  would there be any warnings there for low memory, failed requests etc?

---

