---
title: "ATI X700 PRO and fglrx not working"
date: 2005-04-23
forum: Hardware &amp; Laptops
---

### Post by ranx on 2005-04-23
Hi

I know that the ATI fglrx driver has been covered in many posts. I read them all and still no luck. 

I have a ATI X700 PRO graphics card and Samsung SyncMaster 959NF monitor.

As the X700 is in the PCI-E slot i figured it's normal that during the install my X will not be configured. I did 'apt-get' on the 'xorg-driver-fglrx' and 'linux-restricted-modules'. 
Changed the xorg.conf from "ati" to "fglrx"

Now when I try to run '/etc/init.d/gdm start' I can briefly see that GNOME is starting and then a weird thing happens. My monitor just shuts down. As if it gets no more signal from the pc. It does exactly the same thing when i remove the VGA cable. 

The PC does no more thinking. Ctrl+Alt+Del or Ctrl+Alt+Backspace dont work. Only way to reboot is by pressing the restart button on the PC.

Before installing the fglrx driver I got the 'no screens found' error when starting X.
Now there is no error message in the log file. 

I tried attaching the xorg.conf and Xorg.0.log files.

---

### Post by alastair on 2005-04-23
There's nothing obviously wrong in the log file, or the conf file. 

It would be worth also taking a look in the system log /var/log/syslog, to see if it has any warnings or errors when X starts.

---

### Post by ranx on 2005-04-23
Here's the syslog. 

Apr 23 13:27:14 localhost kernel: [fglrx:firegl_addmap] *ERROR* mtrr allocation failed (-22)
Apr 23 13:27:14 localhost kernel: allocation failed: out of vmalloc space - use vmalloc=<size> to increase size.

Is that it?

---

### Post by alastair on 2005-04-23
I don't know. A Google search for : "out of vmalloc space" fglrx

Gives some hits. IT is also worth looking through the Rage3D forums e.g.

[http://www.rage3d.com/board/showthread.php?t=33800068&highlight=vmalloc](http://www.rage3d.com/board/showthread.php?t=33800068&highlight=vmalloc)

You might try adding a "vmalloc=256m" to your kernel boot line as some say - but this seems a bit horrible to me.

Look through the logs again (Xorg.0.log/syslog) and make sure there is no other message/error.

---

### Post by ranx on 2005-04-24
Added the vmalloc=256m to kernel boot line and got rid of the error but nothing changes. I'm trying to investigate what this mtrr allocation error means.

```
Apr 24 09:05:58 localhost kernel: ACPI: Power Button (FF) [PWRF]
Apr 24 09:05:58 localhost kernel: ibm_acpi: ec object not found
Apr 24 09:05:59 localhost kernel: apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
Apr 24 09:05:59 localhost kernel: apm: overridden by ACPI.
Apr 24 09:06:00 localhost kernel: fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
Apr 24 09:06:00 localhost kernel: [fglrx] Maximum main memory to use for locked dma buffers: 681 MBytes.
Apr 24 09:06:00 localhost kernel: ACPI: PCI interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 16
Apr 24 09:06:00 localhost kernel: [fglrx] module loaded - fglrx 8.8.25 [Jan 14 2005] on minor 0
Apr 24 09:06:00 localhost kernel: mtrr: base(0xb0000000) is not aligned on a size(0x7ff0000) boundary
Apr 24 09:06:00 localhost kernel: [fglrx:firegl_addmap] *ERROR* mtrr allocation failed (-22)
Apr 24 09:06:00 localhost kernel: [fglrx] free  PCIe = 51118080
Apr 24 09:06:00 localhost kernel: [fglrx] max   PCIe = 51118080
Apr 24 09:06:00 localhost kernel: [fglrx] free  LFB = 122613760
Apr 24 09:06:00 localhost kernel: [fglrx] max   LFB = 122613760
Apr 24 09:06:00 localhost kernel: [fglrx] free  Inv = 134217728
Apr 24 09:06:00 localhost kernel: [fglrx] max   Inv = 134217728
Apr 24 09:06:00 localhost kernel: [fglrx] total Inv = 134217728
Apr 24 09:06:00 localhost kernel: [fglrx] total TIM = 0
Apr 24 09:06:00 localhost kernel: [fglrx] total FB  = 0
Apr 24 09:06:00 localhost kernel: [fglrx] total PCIe = 16384
Apr 24 09:06:01 localhost postfix/master[6592]: daemon started -- version 2.1.5
Apr 24 09:06:02 localhost anacron[6770]: Anacron 2.3 started on 2005-04-24
Apr 24 09:06:02 localhost anacron[6770]: Will run job `cron.daily' in 5 min.
Apr 24 09:06:02 localhost anacron[6770]: Jobs will be executed sequentially
Apr 24 09:06:02 localhost /usr/sbin/cron[6791]: (CRON) INFO (pidfile fd = 3)
Apr 24 09:06:02 localhost /usr/sbin/cron[6792]: (CRON) STARTUP (fork ok)
Apr 24 09:06:02 localhost /usr/sbin/cron[6792]: (CRON) INFO (Running @reboot jobs)
Apr 24 09:06:03 localhost udev[6821]: creating device node '/dev/vcs2'
Apr 24 09:06:03 localhost udev[6823]: creating device node '/dev/vcs3'
Apr 24 09:06:03 localhost udev[6825]: creating device node '/dev/vcsa2'
Apr 24 09:06:03 localhost udev[6829]: creating device node '/dev/vcsa3'
Apr 24 09:06:03 localhost udev[6827]: creating device node '/dev/vcs4'
Apr 24 09:06:03 localhost udev[6833]: creating device node '/dev/vcs6'
Apr 24 09:06:03 localhost udev[6831]: creating device node '/dev/vcsa4'
Apr 24 09:06:03 localhost udev[6835]: creating device node '/dev/vcs5'
Apr 24 09:06:03 localhost udev[6837]: creating device node '/dev/vcsa6'
Apr 24 09:06:03 localhost udev[6839]: creating device node '/dev/vcsa5'
Apr 24 09:06:07 localhost kernel: eth0: no IPv6 routers present
```

---

### Post by ranx on 2005-04-24
I've made some progress. Once again I downloaded the fglrx drivers from ati website. I got X running and I was happy. I did it all under failsafe. I started and stopped gdm for many times. 

But now when I rebooted and X loaded the screen just staid black but not like before. This time the monitor was receiving signals from the PC. But I was still unable to CTRL+ALT+DEL or BACKSPACE. And the "funny" thing is that it will not run under failsaif anymore. There are absolutely no error messages anywhere.

---

### Post by zwaardmeester on 2005-04-24
I'm not sure, but in the description of my driver X700 it not mentioned. Perhaps you need another driver than fglrx?

```

Video driver for ATI graphics accelerators
Video driver for the ATI Radeon and FireGL graphics accelerators.

This version of the ATI driver officially supports:
 * ATI Radeon 8500, 9000, 9100, 9200, 9250 (R2xx)
 * ATI Radeon 9500, 9550, 9600, 9700, 9800, X300, X400, X600 (R3xx)
 * ATI Radeon X700, X800 (R4xx)
 * ATI Mobility 9000, 9600, 9800
 * ATI FireGL 8700, 8800, E1, E2, X1, X2, X3, Z1, T2, 5100, 7100, 7200
 * ATI Mobility FireGL 9000, T2, T2e

This package provides 2D display drivers and hardware accelerated OpenGL.

```

---

### Post by alastair on 2005-04-24
It might be worth re-checking the :

/var/log/Xorg.conf
/var/log/syslog

log files - perhaps posting them again.

Also, maybe worth researching the /exact/ specs on your "Samsung SyncMaster 959NF" monitor, and manually adding the proper Horiz/Vert sync rates (MHz/Hz) to the config file.

Maybe the ATI drivers are b0rked on your configuration. It would not be the first time ...

---

