---
title: "Karmic on Toshiba A305-S6196, problem with ATI/AMD proprietary FGLRX graphics driver"
date: 2009-12-12
forum: Hardware
---

### Post by bartonski on 2009-12-12
I just installed Karmic on a Toshiba Satellite A305. I tried the live CD first, everything seemed to work correctly (sound, correct screen resolution, wireless connection all good).

I went ahead and let Synaptic install 105 updates, then requested install of ATI/AMD FGLRX graphics driver. After reboot, the white ubuntu logo (new feature for Karmic, apparantly) showed up for a few seconds. The logo disappeared, and the light on my caps lock key started flashing. At this point, the computer is competely hung.

So... two questions:

1) Has anyone seen this happen before? I've been googling around, and haven't found any references to it, but perhaps I've just been using the wrong search terms.

2) I would like to boot into safe mode and un-install this graphics driver, but I never get a GRUB menu. I'm sure that there's a key or key combo to hit to make grub stop and display the kernels to boot from, but I don't know what that is.

OBTW, I rebooted in to the live cd and poked around in /var/log. The machine crashed at 2009-12-13 05:36, here are all the log entries at that time...

```
-r-----  1 root              adm   50023 2009-12-13 05:35 dmesg.0
[   12.380795] 	(5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   12.380797] 	(5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)

-rw-r--  1 root              utmp  16384 2009-12-13 05:36 wtmp
[binary file... ]

-r-----  1 root              adm       0 2009-12-13 05:36 dmesg

-r--r--  1 root              root      0 2009-12-13 05:36 udev

-r--r--  1 root              root    251 2009-12-13 05:36 dkms_autoinstaller

fglrx (8.660): Already installed on this kernel.

-r-----  1 syslog            adm  376024 2009-12-13 05:36 messages
Dec 13 00:36:55 tiger-laptop kernel: [   16.796839] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Dec 13 00:36:55 tiger-laptop kernel: [   17.160859] ppdev: user-space parallel port driver

drwxrwx--T  2 root              gdm    4096 2009-12-13 05:36 gdm

-r-----  1 syslog            adm   24576 2009-12-13 05:36 lpr.log
Dec 13 00:35:57 tiger-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1d.7/usb2/2-0:1.0
Dec 13 00:35:57 tiger-laptop udev-configure-printer: invalid or -rw-r-----  1 syslog            adm   61440 2009-12-13 05:36 daemon.log
Dec 13 00:36:52 tiger-laptop avahi-daemon[918]: Successfully called chroot().
Dec 13 00:36:52 tiger-laptop avahi-daemon[918]: Successfully dropped remaining capabiliti-rw-r--r--  1 root              root   3859 2009-12-13 05:36 pm-powersave.log
/usr/lib/pm-utils/power.d/sched-powersave false: **sched policy powersave OFF
success.

-r-----  1 syslog            adm  376024 2009-12-13 05:36 messages

-r-----  1 syslog            adm   24576 2009-12-13 05:36 lpr.log

-r-----  1 syslog            adm   61440 2009-12-13 05:36 daemon.log

-r-----  1 syslog            adm  581632 2009-12-13 05:36 syslog

-r-----  1 syslog            adm  494936 2009-12-13 05:36 kern.log

-r-----  1 syslog            adm  135168 2009-12-13 05:36 debug
Dec 13 00:36:54 tiger-laptop NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/lo, iface: lo): no ifupdown configuration found.
Dec 13 00:3-rw-r-----  1 syslog            adm  494936 2009-12-13 05:36 kern.log
Dec 13 00:36:58 tiger-laptop kernel: [   19.456643]  domain 0: span 0-1 level MC
Dec 13 00:36:58 tiger-laptop kernel: [   19.456647]   groups: 1 0

-r-----  1 syslog            adm  135168 2009-12-13 05:36 debug
Dec 13 00:36:57 tiger-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1d.0/usb5/5-0:1.0
Dec 13 00:36:57 tiger-laptop udev-configure-printer: add /device

-rw-r--r--  1 root              root      0 2009-12-13 05:36 Xorg.0.log

```

Most signifigant, I would say, are the following:

```
-r--r--  1 root              root    251 2009-12-13 05:36 dkms_autoinstaller

fglrx (8.660): Already installed on this kernel.

```

```

-rw-r--r--  1 root              root      0 2009-12-13 05:36 Xorg.0.log

```

Also, there are a number of log files for X.org in ./gdm/
which are all empty. As far as I can tell, it looks like the fglrx driver barfed because it was conflicting with something already in the kernel (?? barton makes vague mumbling sounds, indicating that he has no idea how video drivers are actually loaded by the kernel, or what that message **actually** means ??). Anyway, it seems that this happens just about the time that X.org wants to start (x.org at least manages to get all of its log files open...) then kernel panic.

---

### Post by bartonski on 2009-12-12
This seems very similar to this bug report:

[https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/464525](https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/464525)

...everyone on that thread seems to be talking about 64 bit Ubuntu install, other than that, it describes the problem that I'm having exactly.

---

### Post by bartonski on 2009-12-13
I threw in the towel and re-installed the OS; I had less invested in the old install than motivation to fix. I tried hitting 'esc' while GRUB was loading, to force a boot menu, but it never stopped to give me any boot options.

After re-install, the trackpad on the Laptop doesn't respond... That didn't happen after the inital install, and it works just fine under live CD boot.

Out of the frying pan, and into the fire. :(

I'm off to trouble-shoot, I'll start a new thread if I have any particular questions. :x

---

### Post by fuego on 2009-12-13
Hope you are still reading this thread. Hold the shift key down on boot to see the grub menu.
I'm running Karmic on a Toshiba L305D and installed the FGLRX driver under System>Administration>HardwareDrivers. Really don't know if that makes a difference, as opposed to synaptic, but hey....ya never know.

And fyi:
$ dmesg | grep fglrx

[INDENT][   14.707982] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[   14.777561] [fglrx] Maximum main memory to use for locked dma buffers: 2622 MBytes.
[   14.777592] [fglrx]   vendor: 1002 device: 9613 count: 1
[   14.777906] [fglrx] ioport: bar 1, base 0x6000, size: 0x100
[   14.778248] [fglrx] Kernel PAT support is enabled
[   14.778280] [fglrx] module loaded - fglrx 8.66.10 [Sep  3 2009] with 1 minors
[   33.321597] [fglrx] GART Table is not in FRAME_BUFFER range 
[   33.347203] fglrx_pci 0000:01:05.0: irq 30 for MSI/MSI-X
[   33.347779] [fglrx] Firegl kernel thread PID: 1543
[   33.560036] [fglrx] Gart USWC size:862 M.
[   33.560041] [fglrx] Gart cacheable size:341 M.
[   33.560047] [fglrx] Reserved FB block: Shared offset:0, size:1000000 
[   33.560051] [fglrx] Reserved FB block: Unshared offset:fffb000, size:5000 
[/INDENT]

Also, I never did anything with 'aticonfig', which doesn't even reside on my computer, e.g., /etc/.

---

### Post by bartonski on 2009-12-13
Fuego,

Thanks for the reply. I already threw in the towel on the FGLRX driver, and simply re-installed Karmic... but now I'm having trouble with the touchpad (as I think that I mentioned in my previous post). I'll definitely remember how to get the grub menu, the next time I need it though.

---

### Post by bartonski on 2009-12-13
The problem seems to have been solved [here]("http://ubuntuforums.org/showthread.php?t=1323880&highlight=Problem+with+ATI+graphics+driver")

I haven't tried this, but I'm willing to mark the thread as solved.

---

