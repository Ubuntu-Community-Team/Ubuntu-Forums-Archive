---
title: "CPU speeds autodetect wrongly, cpufreqd spamming syslog"
date: 2015-02-18
forum: Hardware
---

### Post by Anakinholland on 2015-02-18
Working on a Lenovo X240  with Xubuntu 14.04

The laptop has a 1,9Ghz CPU I5-4300U, but autodetect insists it can do 2,5Ghz, so as a result cpufreqd wants to increase to that speed, which fails, spamming syslog...

I cannot find info on limiting frequency detection, and even so will likely need custom kernel compiling, so will probably have to alter cpufreqd, whoms config will be overwritten in the next update.

System info

```
System:    Host: schuldiner Kernel: 3.13.0-45-generic x86_64 (64 bit) Desktop: Xfce 4.11.8 Distro: Ubuntu 14.04 trusty
Machine:   System: LENOVO (portable) product: 20ALCTO1WW version: ThinkPad X240
           Mobo: LENOVO model: 20ALCTO1WW version: SDK0E50510 PRO Bios: LENOVO version: GIET75WW (2.25 ) date: 06/24/2014
CPU:       Dual core Intel Core i5-4300U CPU (-HT-MCP-) clocked at 1900.00 MHz 
Graphics:  Card: Intel Haswell-ULT Integrated Graphics Controller 
           X.Org: 1.15.1 drivers: intel (unloaded: fbdev,vesa) Resolution: 1920x1080@60.0hz 
           GLX Renderer: Mesa DRI Intel Haswell Mobile GLX Version: 3.0 Mesa 10.1.3
Network:   Card-1: Intel Ethernet Connection I218-LM driver: e1000e 
           Card-2: Intel Wireless 7260 driver: iwlwifi 
Drives:    HDD Total Size: 1180.3GB (4.2% used)
Info:      Processes: 267 Uptime: 1:52 Memory: 2595.5/7864.9MB Client: Shell (bash) inxi: 1.9.17 
```

CPU info

[http://ark.intel.com/products/76308/Intel-Core-i5-4300U-Processor-3M-Cache-up-to-2_90-GHz](http://ark.intel.com/products/76308/Intel-Core-i5-4300U-Processor-3M-Cache-up-to-2_90-GHz)

syslog:

```
Feb 17 07:35:15 schuldiner cpufreqd[1724]: cpufreqd_set_profile     : Couldn't set profile "Performance High" set for cpu0 (2501000-2501000-performance)
Feb 17 07:35:15 schuldiner cpufreqd[1724]: cpufreqd_loop            : Cannot set policy, Rule unchanged ("AC Off - Medium Battery").
```

This is showing when plugging A/C adapter in after working on battery.

Model detection

```
root@schuldiner:/var/log# cat /proc/cpuinfo |grep "model name" | sort -u
model name    : Intel(R) Core(TM) i5-4300U CPU @ 1.90GHz
```

available frequencies:

```
root@schuldiner:~# cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_available_frequencies 
2501000 2500000 2400000 2200000 2100000 1900000 1800000 1700000 1600000 1500000 1300000 1200000 1100000 1000000 800000 775000 
```

This should not exceed 1900000.

cpufreqd.conf

```
[Profile]
name=Performance High
minfreq=100%
maxfreq=100%
policy=performance
#exec_post=echo 8 > /proc/acpi/sony/brightness
[/Profile]
```

So, in the end, the autodetect is "wrong", resulting in cpufreqd not being able to actually set the speeds.

Changing "100%" to "1900000" solves the issue, but will be overwritten in future updates (unless it gets a ".d" directory as well, which has downsides or even dangers in itself)

Any thoughts on alternatives?&#65279;

---

