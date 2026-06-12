---
title: "Dell Inspiron 8100 won't Suspend or Hibernate"
date: 2012-05-18
forum: Hardware
---

### Post by daemoncycler on 2012-05-18
Hi,
have a Dell Inspiron 8100 running Lubuntu 11.10 & doing it very well with one exception.  Will not enter Suspend or Hibernate.  Would really like it to suspend when the lid is closed.

First - I read the hardware most likely did not support suspend.


Then I found in the Hardware Compatibility section:
I will you advise to change the driver in xorg.conf to the 3d acceleration driver from ati. There for change the Driver under Device to fglrx but first pleace install the ati-drivers from the restricted deb repository. 


Lastly I found this thread: [http://askubuntu.com/questions/7552/cannot-suspend-dell-inspiron](http://askubuntu.com/questions/7552/cannot-suspend-dell-inspiron)
which might indicate running the following from Terminal:

**gksudo gedit /etc/pm/config.d/unload_modules**

And then add **SUSPEND_MODULES="xhci-hcd"**

save & reboot.

Your basic newbie here & perhaps have enough info to @ least give one of these a shot but was hoping someone could shed some light or point me in the right direction.

thanks,
Daemoncycler

---

### Post by daemoncycler on 2012-11-01
Hi,
thought I might post some more info - perhaps someone might be able to isolate a problem.  Does this thread belong in the "Ubuntu Specialised Support" Forum?

I did create files : /etc/pm/config.d/00sleep_module and /etc/pm/config.d/unload_module
add line to files : SUSPEND_MODULES="xhci-hcd"
This did not help.

Found a thread that addresses my issue however I need some help diagnosing.  Here is the thread:
[[COLOR="Navy"]Ubuntu won't resume from suspend mode[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1831541")

Before I proceed with modifying & editing /etc/pm/sleep.d/20_custom-xhci_hcd
maybe someone can look @ the extremely long winded log posting below & see if anything jumps out at them?

My video card is a Nvidia GeForce2 Go.

Below is a posting of the contents of **/var/log/pm-suspend.log** and **/var/log/syslog**.

I disabled & removed the Wireless Panda USB card before suspending because some of the msgs pointed towards the NetworkManager wake up as a failure.  That did not help.  Still got the NetworkManager wake up failure msgs with Panda wireless removed.

This line:
**Oct 31 23:17:39 ???-Inspiron-8100 kernel: [ 4592.533714] usb usb1: root hub lost power or was reset** 
looks suspicious.


This is while waking - sorry for pasting the whole log:

[COLOR="DarkGreen"]****************************************************************[/COLOR]

***From Suspend.log***
```

Wed Oct 31 23:17:39 MDT 2012: Awake. 
Wed Oct 31 23:17:39 MDT 2012: Running hooks for resume 
Running hook /usr/lib/pm-utils/sleep.d/99video resume suspend: 

/usr/lib/pm-utils/sleep.d/99video resume suspend: success. 
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend: 

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend: success. 
Running hook /usr/lib/pm-utils/sleep.d/95led resume suspend: 
 
/usr/lib/pm-utils/sleep.d/95led resume suspend: not applicable. 
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend: 

/dev/sda: 
 setting Advanced Power Management level to 0xfe (254) 
 APM_level	= 254 

/dev/sda: 
 setting Advanced Power Management level to 0xfe (254) 
 APM_level	= 254 

/usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend: success. 
Running hook /usr/lib/pm-utils/sleep.d/95anacron resume suspend: 

/usr/lib/pm-utils/sleep.d/95anacron resume suspend: success. 
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq resume suspend: 

/usr/lib/pm-utils/sleep.d/94cpufreq resume suspend: success. 
Running hook /usr/lib/pm-utils/sleep.d/90clock resume suspend: 

/usr/lib/pm-utils/sleep.d/90clock resume suspend: not applicable. 
Running hook /usr/lib/pm-utils/sleep.d/75modules resume suspend: 
Reloaded unloaded modules. 

/usr/lib/pm-utils/sleep.d/75modules resume suspend: success. 
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend: 
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory 

/usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend: success. 
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager resume suspend: 
**[COLOR="Purple"]Having NetworkManager wake interfaces back up...Failed.[/COLOR]** 

/usr/lib/pm-utils/sleep.d/55NetworkManager resume suspend: success. 
Running hook /usr/lib/pm-utils/sleep.d/49bluetooth resume suspend: 

/usr/lib/pm-utils/sleep.d/49bluetooth resume suspend: not applicable. 
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend: 

/etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend: success. 
Running hook /etc/pm/sleep.d/10_grub-common resume suspend: 

/etc/pm/sleep.d/10_grub-common resume suspend: success. 
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio resume suspend: 
Welcome to PulseAudio! Use "help" for usage information. 
>>> >>> Welcome to PulseAudio! Use "help" for usage information. 
>>> >>> Welcome to PulseAudio! Use "help" for usage information. 
>>> >>> 
/usr/lib/pm-utils/sleep.d/01PulseAudio resume suspend: success. 
Running hook /usr/lib/pm-utils/sleep.d/00powersave resume suspend: 

/usr/lib/pm-utils/sleep.d/00powersave resume suspend: success. 
Running hook /usr/lib/pm-utils/sleep.d/00logging resume suspend: 

/usr/lib/pm-utils/sleep.d/00logging resume suspend: success. 
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change resume suspend: 

/usr/lib/pm-utils/sleep.d/000kernel-change resume suspend: success. 
Wed Oct 31 23:17:43 MDT 2012: Finished.

```


***From Syslog: @ same time frame***
```

Nov  1 05:17:39 ???-Inspiron-8100 rtkit-daemon[1202]: The canary thread is apparently starving. Taking action. 
Nov  1 05:17:39 ???-Inspiron-8100 rtkit-daemon[1202]: Demoting known real-time threads. 
Nov  1 05:17:39 ???-Inspiron-8100 rtkit-daemon[1202]: Successfully demoted thread 1212 of process 1200 (n/a). 
Nov  1 05:17:39 ???-Inspiron-8100 rtkit-daemon[1202]: Successfully demoted thread 1207 of process 1200 (n/a). 
Nov  1 05:17:39 ???-Inspiron-8100 rtkit-daemon[1202]: Successfully demoted thread 1200 of process 1200 (n/a). 
Nov  1 05:17:39 ???-Inspiron-8100 rtkit-daemon[1202]: Demoted 3 threads. 
Oct 31 23:17:39 ???-Inspiron-8100 kernel: [ 4591.670841] PM: Syncing filesystems ... done. 
Oct 31 23:17:39 ???-Inspiron-8100 kernel: [ 4591.674829] PM: Preparing system for mem sleep 
Oct 31 23:17:39 ???-Inspiron-8100 kernel: [ 4591.674864] Freezing user space processes ... (elapsed 0.01 seconds) done. 
Oct 31 23:17:39 ???-Inspiron-8100 kernel: [ 4591.688128] Freezing remaining freezable tasks ... (elapsed 0.01 seconds) done. 
Oct 31 23:17:39 ???-Inspiron-8100 kernel: [ 4591.704090] PM: Entering mem sleep 
Oct 31 23:17:39 ???-Inspiron-8100 kernel: [ 4591.704124] Suspending console(s) (use no_console_suspend to debug) 
Oct 31 23:17:39 ???-Inspiron-8100 kernel: [ 4591.870353] PM: suspend of drv:psmouse dev:serio2 complete after 165.687 msecs 
Oct 31 23:17:39 ???-Inspiron-8100 kernel: [ 4591.870524] sd 0:0:0:0: [sda] Synchronizing SCSI cache 
Oct 31 23:17:39 ???-Inspiron-8100 kernel: [ 4591.870938] sd 0:0:0:0: [sda] Stopping disk 
Oct 31 23:17:39 ???-Inspiron-8100 kernel: [ 4591.922150] parport_pc 00:0e: disabled 
Oct 31 23:17:39 ???-Inspiron-8100 kernel: [ 4591.925845] serial 00:0d: disabled 
Oct 31 23:17:39 ???-Inspiron-8100 kernel: [ 4591.930100] serial 00:0d: wake-up capability disabled by ACPI 
Oct 31 23:17:39 ???-Inspiron-8100 kernel: [ 4591.930527] ACPI handle has no context! 
Oct 31 23:17:39 ???-Inspiron-8100 kernel: [ 4592.061234] PM: suspend of drv:nvidia dev:0000:01:00.0 complete after 130.303 msecs 
Oct 31 23:17:39 ???-Inspiron-8100 kernel: [ 4592.061329] Maestro3 0000:02:03.0: PCI INT A disabled 
Oct 31 23:17:39 ???-Inspiron-8100 kernel: [ 4592.061369] ACPI handle has no context! 
Oct 31 23:17:39 ???-Inspiron-8100 kernel: [ 4592.061407] uhci_hcd 0000:00:1f.2: PCI INT D disabled 
Oct 31 23:17:39 ???-Inspiron-8100 kernel: [ 4592.076079] PM: suspend of drv:Maestro3 dev:0000:02:03.0 complete after 145.452 msecs 
Oct 31 23:17:39 ???-Inspiron-8100 kernel: [ 4592.477111] PM: suspend of drv:sd dev:0:0:0:0 complete after 606.596 msecs 
Oct 31 23:17:39 ???-Inspiron-8100 kernel: [ 4592.477134] PM: suspend of drv:scsi dev:target0:0:0 complete after 606.508 msecs 
Oct 31 23:17:39 ???-Inspiron-8100 kernel: [ 4592.477154] PM: suspend of drv:scsi dev:host0 complete after 553.069 msecs 
Oct 31 23:17:39 ???-Inspiron-8100 kernel: [ 4592.477329] PM: suspend of drv:ata_piix dev:0000:00:1f.1 complete after 470.228 msecs 
Oct 31 23:17:39 ???-Inspiron-8100 kernel: [ 4592.477348] PM: suspend of drv: dev:pci0000:00 complete after 470.079 msecs 
Oct 31 23:17:39 ???-Inspiron-8100 kernel: [ 4592.477360] PM: suspend of devices complete after 772.767 msecs 
Oct 31 23:17:39 ???-Inspiron-8100 kernel: [ 4592.477367] PM: suspend devices took 0.772 seconds 
Oct 31 23:17:39 ???-Inspiron-8100 kernel: [ 4592.478227] PM: late suspend of devices complete after 0.852 msecs 
Oct 31 23:17:39 ???-Inspiron-8100 kernel: [ 4592.478379] ACPI: Preparing to enter system sleep state S3 
Oct 31 23:17:39 ???-Inspiron-8100 kernel: [ 4592.487793] PM: Saving platform NVS memory 
Oct 31 23:17:39 ???-Inspiron-8100 kernel: [ 4592.487800] Disabling non-boot CPUs ... 
Oct 31 23:17:39 ???-Inspiron-8100 kernel: [ 4592.487800] ACPI: Low-level resume complete 
Oct 31 23:17:39 ???-Inspiron-8100 kernel: [ 4592.487800] PM: Restoring platform NVS memory 
Oct 31 23:17:39 ???-Inspiron-8100 kernel: [ 4592.489958] ACPI: Waking up from system sleep state S3 
Oct 31 23:17:39 ???-Inspiron-8100 kernel: [ 4592.501994] agpgart-intel 0000:00:00.0: restoring config space at offset 0x1 (was 0x20900006, writing 0x20900106) 
Oct 31 23:17:39 ???-Inspiron-8100 kernel: [ 4592.502024] pci 0000:00:01.0: restoring config space at offset 0x7 (was 0x2a0c0c0, writing 0x22a0c0c0) 
Oct 31 23:17:39 ???-Inspiron-8100 kernel: [ 4592.502054] pci 0000:00:1e.0: restoring config space at offset 0x9 (was 0xfff0, writing 0x27f02000) 
Oct 31 23:17:39 ???-Inspiron-8100 kernel: [ 4592.502151] uhci_hcd 0000:00:1f.2: restoring config space at offset 0x1 (was 0x2800005, writing 0x2800001) 
Oct 31 23:17:39 ???-Inspiron-8100 kernel: [ 4592.516056] nvidia 0000:01:00.0: BAR 0: set to [mem 0xfc000000-0xfcffffff] (PCI address [0xfc000000-0xfcffffff]) 
Oct 31 23:17:39 ???-Inspiron-8100 kernel: [ 4592.516068] nvidia 0000:01:00.0: BAR 1: set to [mem 0xe0000000-0xe7ffffff pref] (PCI address [0xe0000000-0xe7ffffff]) 
Oct 31 23:17:39 ???-Inspiron-8100 kernel: [ 4592.516097] nvidia 0000:01:00.0: restoring config space at offset 0x3 (was 0x2000, writing 0xf800) 
Oct 31 23:17:39 ???-Inspiron-8100 kernel: [ 4592.516168] pci 0000:02:06.0: restoring config space at offset 0xf (was 0xefc0100, writing 0xefc010a) 
Oct 31 23:17:39 ???-Inspiron-8100 kernel: [ 4592.516188] pci 0000:02:06.0: restoring config space at offset 0x6 (was 0x1, writing 0xe401) 
Oct 31 23:17:39 ???-Inspiron-8100 kernel: [ 4592.516197] pci 0000:02:06.0: restoring config space at offset 0x5 (was 0x1, writing 0xe8f9) 
Oct 31 23:17:39 ???-Inspiron-8100 kernel: [ 4592.516206] pci 0000:02:06.0: restoring config space at offset 0x4 (was 0x0, writing 0xf8ffdc00) 
Oct 31 23:17:39 ???-Inspiron-8100 kernel: [ 4592.516218] pci 0000:02:06.0: restoring config space at offset 0x1 (was 0x2900000, writing 0x2900007) 
Oct 31 23:17:39 ???-Inspiron-8100 kernel: [ 4592.532048] firewire_ohci 0000:02:0f.2: BAR 0: set to [mem 0xf8ffd000-0xf8ffd7ff] (PCI address [0xf8ffd000-0xf8ffd7ff]) 
Oct 31 23:17:39 ???-Inspiron-8100 kernel: [ 4592.532060] firewire_ohci 0000:02:0f.2: BAR 1: set to [mem 0xf8ff8000-0xf8ffbfff] (PCI address [0xf8ff8000-0xf8ffbfff]) 
Oct 31 23:17:39 ???-Inspiron-8100 kernel: [ 4592.532076] firewire_ohci 0000:02:0f.2: restoring config space at offset 0xf (was 0x4020100, writing 0x402010a) 
Oct 31 23:17:39 ???-Inspiron-8100 kernel: [ 4592.532099] firewire_ohci 0000:02:0f.2: restoring config space at offset 0x3 (was 0x800000, writing 0x802008) 
Oct 31 23:17:39 ???-Inspiron-8100 kernel: [ 4592.532111] firewire_ohci 0000:02:0f.2: restoring config space at offset 0x1 (was 0x2100000, writing 0x2100116) 
Oct 31 23:17:39 ???-Inspiron-8100 kernel: [ 4592.532722] PM: early resume of devices complete after 30.840 msecs 
Oct 31 23:17:39 ???-Inspiron-8100 kernel: [ 4592.533611] pci 0000:00:1e.0: setting latency timer to 64 
Oct 31 23:17:39 ???-Inspiron-8100 kernel: [ 4592.533636] ata_piix 0000:00:1f.1: setting latency timer to 64 
Oct 31 23:17:39 ???-Inspiron-8100 kernel: [ 4592.533677] uhci_hcd 0000:00:1f.2: PCI INT D -> Link[LNKD] -> GSI 10 (level, low) -> IRQ 10 
Oct 31 23:17:39 ???-Inspiron-8100 kernel: [ 4592.533688] uhci_hcd 0000:00:1f.2: setting latency timer to 64 
**[COLOR="purple"]Oct 31 23:17:39 ???-Inspiron-8100 kernel: [ 4592.533714] usb usb1: root hub lost power or was reset [/COLOR]**
Oct 31 23:17:39 ???-Inspiron-8100 kernel: [ 4592.537515] Maestro3 0000:02:03.0: PCI INT A -> Link[LNKB] -> GSI 5 (level, low) -> IRQ 5 
Oct 31 23:17:39 ???-Inspiron-8100 kernel: [ 4592.540993] sd 0:0:0:0: [sda] Starting disk 
Oct 31 23:17:39 ???-Inspiron-8100 kernel: [ 4592.616683] firewire_core: skipped bus generations, destroying all nodes 
Oct 31 23:17:39 ???-Inspiron-8100 kernel: [ 4592.688102] PM: resume of drv:hub dev:1-0:1.0 complete after 147.130 msecs 
Oct 31 23:17:39 ???-Inspiron-8100 kernel: [ 4592.688123] PM: resume of drv: dev:ep_00 complete after 147.145 msecs 
Oct 31 23:17:39 ???-Inspiron-8100 kernel: [ 4592.688137] PM: resume of drv: dev:ep_81 complete after 147.168 msecs 
Oct 31 23:17:39 ???-Inspiron-8100 kernel: [ 4592.733631] PM: resume of drv:battery dev:PNP0C0A:01 complete after 191.683 msecs 
Oct 31 23:17:39 ???-Inspiron-8100 kernel: [ 4592.795540] serial 00:0d: activated 
Oct 31 23:17:39 ???-Inspiron-8100 kernel: [ 4592.875660] parport_pc 00:0e: activated 
Oct 31 23:17:39 ???-Inspiron-8100 kernel: [ 4592.998191] PM: resume of drv:i8042 dev:i8042 complete after 121.924 msecs 
Oct 31 23:17:39 ???-Inspiron-8100 kernel: [ 4593.138378] PM: resume of drv:Maestro3 dev:0000:02:03.0 complete after 600.902 msecs 
Oct 31 23:17:39 ???-Inspiron-8100 kernel: [ 4593.138449] firewire_core: rediscovered device fw0 
Oct 31 23:17:39 ???-Inspiron-8100 kernel: [ 4593.361144] PM: resume of drv:nvidia dev:0000:01:00.0 complete after 827.405 msecs 
Oct 31 23:17:39 ???-Inspiron-8100 kernel: [ 4595.616371] ata1.00: configured for UDMA/100 
Oct 31 23:17:39 ???-Inspiron-8100 kernel: [ 4595.632407] ata1.01: configured for MWDMA2 
Oct 31 23:17:39 ???-Inspiron-8100 kernel: [ 4595.642278] PM: resume of drv:sd dev:0:0:0:0 complete after 3101.285 msecs 
Oct 31 23:17:39 ???-Inspiron-8100 kernel: [ 4595.642305] PM: resume of drv:scsi_device dev:0:0:0:0 complete after 3101.257 msecs 
Oct 31 23:17:39 ???-Inspiron-8100 kernel: [ 4595.642321] PM: resume of drv:scsi_disk dev:0:0:0:0 complete after 2643.880 msecs 
Oct 31 23:17:39 ???-Inspiron-8100 kernel: [ 4598.648033] 
Oct 31 23:17:39 ???-Inspiron-8100 kernel: [ 4598.648041] floppy driver state 
Oct 31 23:17:39 ???-Inspiron-8100 kernel: [ 4598.648044] ------------------- 
Oct 31 23:17:39 ???-Inspiron-8100 kernel: [ 4598.648078] now=1074662 last interrupt=4294892918 diff=1149040 last called handler=reset_interrupt 
Oct 31 23:17:39 ???-Inspiron-8100 kernel: [ 4598.648083] timeout_message=lock fdc 
Oct 31 23:17:39 ???-Inspiron-8100 kernel: [ 4598.648086] last output bytes: 
Oct 31 23:17:39 ???-Inspiron-8100 kernel: [ 4598.648090]  0  0 0 
Oct 31 23:17:39 ???-Inspiron-8100 kernel: [ 4598.648094]  0  0 0 
Oct 31 23:17:39 ???-Inspiron-8100 kernel: [ 4598.648098]  8 80 4294892913 
Oct 31 23:17:39 ???-Inspiron-8100 kernel: [ 4598.648102]  8 80 4294892917 
Oct 31 23:17:39 ???-Inspiron-8100 kernel: [ 4598.648106]  8 80 4294892917 
Oct 31 23:17:39 ???-Inspiron-8100 kernel: [ 4598.648110]  8 80 4294892917 
Oct 31 23:17:39 ???-Inspiron-8100 kernel: [ 4598.648114]  8 80 4294892917 
Oct 31 23:17:39 ???-Inspiron-8100 kernel: [ 4598.648118]  e 80 4294892917 
Oct 31 23:17:39 ???-Inspiron-8100 kernel: [ 4598.648122] 13 80 4294892917 
Oct 31 23:17:39 ???-Inspiron-8100 kernel: [ 4598.648126]  0 90 4294892917 
Oct 31 23:17:39 ???-Inspiron-8100 kernel: [ 4598.648130] 1a 90 4294892917 
Oct 31 23:17:39 ???-Inspiron-8100 kernel: [ 4598.648133]  0 90 4294892917 
Oct 31 23:17:39 ???-Inspiron-8100 kernel: [ 4598.648137] 12 90 4294892917 
Oct 31 23:17:39 ???-Inspiron-8100 kernel: [ 4598.648141]  0 90 4294892917 
Oct 31 23:17:39 ???-Inspiron-8100 kernel: [ 4598.648145] 14 90 4294892917 
Oct 31 23:17:39 ???-Inspiron-8100 kernel: [ 4598.648149] 18 80 4294892917 
Oct 31 23:17:39 ???-Inspiron-8100 kernel: [ 4598.648153]  8 80 4294892918 
Oct 31 23:17:39 ???-Inspiron-8100 kernel: [ 4598.648157]  8 80 4294892918 
Oct 31 23:17:39 ???-Inspiron-8100 kernel: [ 4598.648161]  8 80 4294892918 
Oct 31 23:17:39 ???-Inspiron-8100 kernel: [ 4598.648165]  8 80 4294892918 
Oct 31 23:17:39 ???-Inspiron-8100 kernel: [ 4598.648168] last result at 4294892918 
Oct 31 23:17:39 ???-Inspiron-8100 acpid: client 1027[0:0] has disconnected 
Oct 31 23:17:39 ???-Inspiron-8100 kernel: [ 4598.648172] last redo_fd_request at 4294892918 
Oct 31 23:17:39 ???-Inspiron-8100 kernel: [ 4598.648180] status=0 
Oct 31 23:17:39 ???-Inspiron-8100 kernel: [ 4598.648183] fdc_busy=1 
Oct 31 23:17:39 ???-Inspiron-8100 kernel: [ 4598.648193] do_floppy=reset_interrupt 
Oct 31 23:17:39 ???-Inspiron-8100 kernel: [ 4598.648197] cont=e0812290 
Oct 31 23:17:39 ???-Inspiron-8100 kernel: [ 4598.648200] current_req=  (null) 
Oct 31 23:17:39 ???-Inspiron-8100 kernel: [ 4598.648204] command_status=-1 
Oct 31 23:17:39 ???-Inspiron-8100 kernel: [ 4598.648207] 
Oct 31 23:17:39 ???-Inspiron-8100 kernel: [ 4598.648212] floppy0: floppy timeout called 
Oct 31 23:17:39 ???-Inspiron-8100 kernel: [ 4598.648251] PM: resume of drv:floppy dev:floppy.0 complete after 3005.888 msecs 
Oct 31 23:17:39 ???-Inspiron-8100 kernel: [ 4598.928137] PM: resume of devices complete after 6395.360 msecs 
Oct 31 23:17:39 ???-Inspiron-8100 kernel: [ 4598.928320] PM: resume devices took 6.396 seconds 
Oct 31 23:17:39 ???-Inspiron-8100 kernel: [ 4598.928369] PM: Finishing wakeup. 
Oct 31 23:17:39 ???-Inspiron-8100 kernel: [ 4598.928373] Restarting tasks ... done. 
Oct 31 23:17:39 ???-Inspiron-8100 kernel: [ 4598.974932] video LNXVIDEO:00: Restoring backlight state 
Oct 31 23:17:39 ???-Inspiron-8100 acpid: client connected from 1027[0:0] 
Oct 31 23:17:39 ???-Inspiron-8100 acpid: 1 client rule loaded 
Oct 31 23:17:40 ???-Inspiron-8100 anacron[2343]: Anacron 2.3 started on 2012-10-31 
Oct 31 23:17:40 ???-Inspiron-8100 anacron[2343]: Normal exit (0 jobs run) 
Oct 31 23:17:42 ???-Inspiron-8100 anacron[2495]: Anacron 2.3 started on 2012-10-31 
Oct 31 23:17:42 ???-Inspiron-8100 anacron[2495]: Normal exit (0 jobs run) 
Oct 31 23:17:42 ???-Inspiron-8100 kernel: [ 4602.308149] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0 
Oct 31 23:17:43 ???-Inspiron-8100 NetworkManager[480]: <info> wake requested (sleeping: yes  enabled: yes) 
Oct 31 23:17:43 ???-Inspiron-8100 NetworkManager[480]: <info> waking up and re-enabling... 
Oct 31 23:17:43 ???-Inspiron-8100 NetworkManager[480]: <info> WWAN now enabled by management service 
Oct 31 23:17:52 ???-Inspiron-8100 kernel: [ 4608.200100] NVRM: Xid (0001:00): 8, Channel 00000000

```

[COLOR="DarkGreen"]***********************************************************[/COLOR]


Any help is much appreciated,

thank you

daemoncycler

---

### Post by Toz on 2012-11-01
Can you try the following to create an enhanced debugging log? 

Open a terminal window and type in the following command:
```
sudo bash
mv /var/log/pm-suspend.log /var/log/pm-suspend.log.BAK
export PM_DEBUG=true
pm-suspend
```

Your system should hang again on resume. Restart the system, then post back the full contents of the /var/log/pm-suspend.log file like this:
```
pastebinit /var/log/pm-suspend.log
```
...and post back the link that is generated.

And also, can we get some more info about your video card?
```
sudo lspci -vnn  |grep -A12 VGA
```

---

### Post by daemoncycler on 2012-11-02
Thanks for helping & for placing my logs into those clean windows above. :)

[http://paste.ubuntu.com/1325557/](http://paste.ubuntu.com/1325557/)

3300 lines of text.


& video card info:

01:00.0 VGA compatible controller [0300]: nVidia Corporation NV11 [GeForce2 Go] [10de:0112] (rev b2) (prog-if 00 [VGA controller])
	Subsystem: Dell Device [1028:00e6]
	Flags: bus master, VGA palette snoop, 66MHz, medium devsel, latency 248, IRQ 11
	Memory at fc000000 (32-bit, non-prefetchable) [size=16M]
	Memory at e0000000 (32-bit, prefetchable) [size=128M]
	[virtual] Expansion ROM at fd000000 [disabled] [size=64K]
	Capabilities: [60] Power Management version 2
	Capabilities: [44] AGP version 2.0
	Kernel driver in use: nvidia
	Kernel modules: nvidia_96_updates, nvidia_96, nouveau, nvidiafb, rivafb

02:03.0 Multimedia audio controller [0401]: ESS Technology ES1983S Maestro-3i PCI Audio Accelerator [125d:1998] (rev 10)
	Subsystem: Dell ES1983S Maestro-3i (Dell Inspiron 8100) [1028:00e6]
	Flags: bus master, medium devsel, latency 32, IRQ 5
	I/O ports at ec00 [size=256]

---

### Post by Toz on 2012-11-02
The log file doesn't seem complete. I'm not seeing the closing resume statements. Can you try again, but this time just a non-debugged version (just to make sure):
```
sudo bash
mv /var/log/pm-suspend.log /var/log/pm-suspend.log.BAK
pm-suspend
```
...then:
```
pastebinit /var/log/pm-suspend.log
```

And, since the log file stops at the resume of pulseaudio, can you show more info about your sound card:
```
sudo lspci -vnn  |grep -A12 audio
```

---

### Post by daemoncycler on 2012-11-02
Sure, thank you.

[http://paste.ubuntu.com/1326420/](http://paste.ubuntu.com/1326420/)


&  Audio

2:03.0 Multimedia audio controller [0401]: ESS Technology ES1983S Maestro-3i PCI Audio Accelerator [125d:1998] (rev 10)
	Subsystem: Dell ES1983S Maestro-3i (Dell Inspiron 8100) [1028:00e6]
	Flags: bus master, medium devsel, latency 32, IRQ 5
	I/O ports at ec00 [size=256]
	Memory at f8ffe000 (32-bit, non-prefetchable) [size=8K]
	Capabilities: [c0] Power Management version 2
	Kernel driver in use: Maestro3
	Kernel modules: snd-maestro3

02:06.0 Communication controller [0780]: Agere Systems WinModem 56k [11c1:0448] (rev 01)
	Subsystem: Actiontec Electronics Inc Device [1668:2000]
	Flags: bus master, medium devsel, latency 0, IRQ 10
	Memory at f8ffdc00 (32-bit, non-prefetchable) [size=256]


Since I do not have an internal wireless card here is some info on that. Scanned the log but I did not see Wifi.
Panda Mini Wifi (b/g/n) 150Mbps Wirelss-N 2.4Ghz USB Adapter

thanks,
daemoncycler

---

### Post by Toz on 2012-11-02
Yep, it looks like its hanging when trying to get the sound re-initialized. Try unloading the sound module then trying suspend/resume:

```
sudo bash
mv /var/log/pm-suspend.log /var/log/pm-suspend.log.BAK
modprobe -r snd_maestro3
pm-suspend
```

As usual, post back the the contents of the pm-suspend.log file.

In the event that it does resume, you won't have a sound driver. You can reload it via:
```
sudo modprobe snd_maestro3
```

---

### Post by daemoncycler on 2012-11-02
Hi, sorry for the delay.

[http://paste.ubuntu.com/1327280/](http://paste.ubuntu.com/1327280/)

I did not get the sound module to unload so suspend did not work. Received this msg = FATAL: Module snd_maestro3 is in use.


Do you mind if I ask how you were able to determine that the sound card was at fault?

---

### Post by Toz on 2012-11-02
I think its related to the sound card because the last statements in your log file are related to restarting pulseaudio, and it doesn't complete.

A couple of suggestions:

1. Do you have s2ram installed? If so, try suspending using it to see if it works:
```
s2ram -f
```

2. Lets try blacklisting the sound card (so it doesn't start and the modules don't load), then trying a suspend/resume cycle to see if it works. To do this, add:
```
blacklist snd_maestro3
```
...to the end of **/etc/modprobe.d/blacklist.conf** and reboot. On reboot, there should be no sound and no sound module loaded. Try suspend/resume. 
You can restore the sound driver by removing this entry and rebooting.

If neither of these work, we can try a lower level debug. See: [https://wiki.ubuntu.com/DebuggingKernelSuspend]("https://wiki.ubuntu.com/DebuggingKernelSuspend"). Hopefully this method will identify the offending device.

---

### Post by daemoncycler on 2012-11-02
s2ram is not installed & definitely no sound after blacklisting maestro3.  However PC still failing to resume from suspend.

Have been reviewing the debuggingkernelsuspend wiki & that is a bit over my head but I'm willing to give it a try.  This old PC is just for purposes like this. Do I need to worry about mainline kernel?

after issuing
```
sudo sh -c "sync; echo 1 > /sys/power/pm_trace; pm-suspend"
```
I have 3 mins before the real time clock gets corrupted.

These two sentences concern me a bit.
> If resume fails to complete, then press the power button until the computer turns off. Power on your computer making sure that it loads the same kernel that exhibited the resume problem.

How would I know which kernel exhibited the resume problem?

thanks


I did create another pastebinit after blacklist of maestro3.
[http://paste.ubuntu.com/1327590/](http://paste.ubuntu.com/1327590/)

---

### Post by Toz on 2012-11-02
Lets try one more thing before the kernel suspend test. I notice in 12.10, the Pulseaudio suspend script no longer exists. Lets try removing it from your system to see if it works. With the snd_maestro3 module loaded (not blacklisted), issue the following command:
```
sudo mv /usr/lib/pm-utils/sleep.d/01PulseAudio /usr/lib/pm-utils/
```

Then try again. (post back log file).

---

### Post by daemoncycler on 2012-11-02
Still stalling on awake.  Do I want to put 01PulseAudio back into the sleep.d folder?

[http://paste.ubuntu.com/1327753/](http://paste.ubuntu.com/1327753/)

Have now read the kernel suspend test several times & it is making more sense.  Remember reading somewhere fixing the RTC by removing & replacing the coin cell battery?  

thank you again for all your effort on this.

---

### Post by Toz on 2012-11-02
According to that log, resume completed! What happened on the screen? Was it black? Was there any activity on the laptop lights?

Can you try adjusting the brightness and going to tty1 and back to see if you can get the screen to display?

---

### Post by daemoncycler on 2012-11-02
Hi, sorry Linux beginner here.  Have been researching *fsck* & *tune2fs* so I could get the current interval setting.  In prep for debugging.

During resume it throws up some white hieroglyphics for a split second then black & turns light blue where it remains.  There is no disc activity after that & a minute later I force power off.  

Not familiar with tty1 - quick Google search indicates virtual terminals.  Is it Ctrl+Alt+F1?

---

### Post by Toz on 2012-11-02
Try adjusting the brightness using the brightness keys.

Yes, tty1 is Ctrl+Alt+F1 - do you get a visible screen there?

---

### Post by daemoncycler on 2012-11-02
The brightness keys are working.  tty1 was very difficult to read, even after I logged in the text & everything I type is overwritten by symbols.  Guess Ctrl+Alt+F7 returns me to normal console.  Hit a bunch of them until got back.

Do you mean for me to use tty1 while waiting for the PC to recover from resume?  Will adjusting the brightness help?

---

### Post by Toz on 2012-11-02
Did adjusting the brightness make the gui sceen (Ctrl+Alt+F7) visible again?

If so, can you post back the results of:
```
for file in /sys/class/backlight/*; do echo $file; cat $file/actual_brightness; cat $file/max_brightness; cat $file/brightness; done
```
...(lets see what brightness interfaces you have)

---

### Post by daemoncycler on 2012-11-02
No, adjusting the brightness did not make the gui reappear.

Not really sure what I am doing in /sys/class/backlight/*.  Was pretty proud I figured out gksudo & gedit.

---

### Post by Toz on 2012-11-02
Hold off on the kernel debug for a bit.

From your last few posts, I got the impression that after a suspend/resume cycle, when the system looked like it was unresponsive, you could go to TTY1 and see a screen to type in (indicating that the system was live). Is this correct? If so, then the resume worked but the graphic screen is not visible.

In that case, open a terminal window and copy/paste the command and run it (no gksudo or gedit required). It will simply post back info about your backlight interfaces. If the system is in fact resuming but the screen display is black, resetting the brightness value may bring it back to life.

If not, then we are back to our original thread.

---

### Post by daemoncycler on 2012-11-02
No - sorry.  Haven't yet tried to access tty1 after suspend.  Will do that now & see what happens.

---

### Post by daemoncycler on 2012-11-02
Ctrl+Alt+F1 after stalled resume caused a flicker of disc activity but that's it.  No other change & I guess you could really call it a black screen, looked like it had a slight blueish hue but black is more like it.

I must be doing something wrong.
There are no folders/files in **/sys/class/backlight** & from there issuing  "echo $file" produces a blank line.
"cat $file/actual_brightness" produced "cat: /actual_brightness: No such file or directory"

I know the ">" (greater than) places *whatever* in the file after the ">"  but not sure what "/" does?   We are echoing $file to the screen in an effort to identify brightness interfaces & the cat command places those in a file named actual & max brightness?  Is that what we're trying to do?

Anyway yes we are back to the original thread.

---

### Post by Toz on 2012-11-03
> **daemoncycler said:**
> When you tire of me please let me know. 

Ctrl+Alt+F1 after stalled resume caused a flicker of disc activity but that's it.  No other change & I guess you could really call it a black screen, looked like it had a slight blueish hue but black is more like it.
Based on the log file that you provided after you removed the PulseAudio sleep script, it showed that your system resumed completely. Yet, you had no evidence of the system returning from sleep. I believe that your system has completed a successful sleep/resume but that the screen is completely dimmed so that you can't see anything.

> I must be doing something wrong.
There are no folders/files in **/sys/class/backlight** & from there issuing  "echo $file" produces a blank line.
"cat $file/actual_brightness" produced "cat: /actual_brightness: No such file or directory"
It is possible that you do not have any backlight interfaces. If you did, you would have a directory in /sys/class/backlight that would be your backlight interface.

> I know the ">" (greater than) places *whatever* in the file after the ">"  but not sure what "/" does?   We are echoing $file to the screen in an effort to identify brightness interfaces & the cat command places those in a file named actual & max brightness?  Is that what we're trying to do?
This script was simply querying the contents of some files to get the brightness values. "$file/brightness" was referring to each interface's brightness file. For example, here is the result of the command on my system:
> $ for file in /sys/class/backlight/*; do echo $file; cat $file/actual_brightness; cat $file/max_brightness; cat $file/brightness; done
/sys/class/backlight/acpi_video0
24
24
24
/sys/class/backlight/intel_backlight
3274965
3274965
3274965

...I have 2 backlight interfaces, the acpi_video0 one being the correct active one.

> Anyway yes we are back to the original thread.
If I am right and your system is returning from sleep (but not visible), I'm not sure the kernel debug will help. We really should determine whether the system is in fact awake.

--------

Can you install the ssh server on this laptop and then after a resume, try to ssh in from another computer to see if you can connect?
```
sudo apt-get install openssh-server
```
...then after a sleep/resume, try connecting via ssh from another computer to see if you get a connection.

More information:
Here is a link on the ssh server: [https://help.ubuntu.com/12.04/serverguide/openssh-server.html]("https://help.ubuntu.com/12.04/serverguide/openssh-server.html") (though all you really need to do for this test is install it using the command above)

Here is a link on how to connect to an ssh server using various other systems: [https://help.ubuntu.com/community/SSH/OpenSSH/ConnectingTo]("https://help.ubuntu.com/community/SSH/OpenSSH/ConnectingTo").

Lets determine whether this laptop is really awake after a sleep/resume cycle.

--------

EDIT: Can you also post back your dmesg and syslog files after a sleep/resume cycle? I want to see if there is anything there that might help.
```
pastebinit /var/log/syslog
pastebinit /var/log/dmesg
```

---

### Post by daemoncycler on 2012-11-03
Only have (L)Ubuntu running in one place right now.  Did have Ubuntu running under Virtual Box on the desktop.  Shall put it back.
Will post back later today with ssh results.

thanks

---

### Post by daemoncycler on 2012-11-03
Toz - your diagnosis was spot on.  I can ssh my way into the Inspiron 8100 from another computer.  All this time the PC has been up.  If it could talk would probably say something like "*why doesn't that stupid human realize I'm awake?*".

That means something up with the backlight interface?

syslog = [http://paste.ubuntu.com/1330377/](http://paste.ubuntu.com/1330377/)

dmesg = [http://paste.ubuntu.com/1330379/](http://paste.ubuntu.com/1330379/)

thanks

---

### Post by Toz on 2012-11-03
So the question is, how to re-initialize the nvidia driver on resume. A quick google shows plenty of black screen problems on resume from suspend with nvidia drivers.
 
What version of the nvidia driver are you using?
```
glxinfo | grep "OpenGL version"
```

--------------

And. can you try the following:
```
sudo setpci -s 01:00.0 F4.B=80
sudo setpci -s 01:00.0 F4.B=c8
sudo setpci -s 01:00.0 F4.B=ff
sudo setpci -s 01:00.0 F4.B=00
```

These codes will directly manipulate the video card to try to adjust brightness. With each command, you should see the brightness change. If it does, can you let me know which command gives you the best brightness value? Maybe we can just force this on resume.

Note: the last 2 digits after the = sign are hexidecimal values between 0 and 255.

---

### Post by daemoncycler on 2012-11-04
nvidia driver version
> OpenGL version string: 1.5.8 NVIDIA 96.43.20

I have tried both these drivers-currently on recommended:
> NVIDIA accelerated graphics driver(version 96)[recommended]
NVIDIA accelerated graphics driver(post-release updates)(version 96-updates)
Perhaps I should check NVIDIA.com for drivers?


I  saw no change in brightness from any setpci command.  Tried it with the brightness turned down too.  Is there a reason you chose decimal values 128(80), 200(c8), 255(ff) & 00(0)?  Tried several others at random with no change as well.

---

### Post by Toz on 2012-11-04
Can you post your X11 configuration file:
```
pastebinit /etc/X11/xorg.conf
```
...and X log file:
```
pastebinit /var/log/Xorg.0.log
```

---

### Post by daemoncycler on 2012-11-04
Hi Toz,

Was just looking @ the NVIDIA X Server Settings.

Found newer version of driver @ nvidia.com
> NVIDIA Driver Version: 96.43.23 dated Fri, Sept 14, 2012


xorg.conf = [http://paste.ubuntu.com/1331854/](http://paste.ubuntu.com/1331854/)

Xorg.0.log = [http://paste.ubuntu.com/1331852/](http://paste.ubuntu.com/1331852/)

thanks

Pretty soon I'll be able to put up my own Avatar.

---

### Post by Toz on 2012-11-04
Lets try this one first:

1. Add **Option         "NvAGP" "1"** to the "Device" section so that it reads like this:
```
Section "Screen"
	Identifier	"Default Screen"
	Option	"AddARGBGLXVisuals"	"True"
EndSection

Section "Device"
	Identifier	"Default Device"
	Option	"NoLogo"	"True"
        Option          "NvAGP" "1"
EndSection
```
...(you'll need to "gksu leafpad /etc/X11/xorg.conf").

2. Blacklist the intel_agp module by adding:
```
blacklist intel_agp
```
...to the end of **/etc/modprobe.d/blacklist.conf** via "gksu leafpad /etc/modprobe.d/blacklist.conf"

3. Save both files and reboot.

---

### Post by daemoncycler on 2012-11-04
Well my friend you fixed it. Hibernate is working too.

Can you tell me what we just did?

---

### Post by Toz on 2012-11-04
Glad to hear we got it. Your system had a couple of problems. 

First, the resume was hanging when trying to re-initialize PulseAudio. We fixed that by removing the pulseaudio sleep script (on a related note, does audio work after resume?).

Second, the system was resuming, but the screen was blank. I haven't had much experience with nvidia cards, but came across a couple of references about older nvidia cards and the NvAGP setting. The last set of configuration entries enabled the nvidia agp driver and disabled the default driver. Looks like that was the final ingredient.

I think you can remove those **SUSPEND_MODULES="xhci-hcd"** entries that you made - I don't believe they are relevant to your system (though they shouldn't cause any harm if you leave them in).

---

### Post by daemoncycler on 2012-11-04
Yes the sound is working.

This was a great learning experience for me.  Perhaps I will break it again later this week for practice with the terminal.  Will fix it myself next time.


Found a driver update on nvidia.com.  NVIDIA Driver **Version: 96.43.23 **dated Fri, Sept 14, 2012.  Should I consider installing it & will that reset the agp driver settings?

> Release Highlights for version 96.43.23
*Added support for X.Org xserver versions 1.11 and 1.12.
*Improved compatibility with recent Linux kernels.

It looks like xserver setting 1.12 does apply - from NVIDIA X Server Settings
> NV-CONTROL Version: 1.12

Thanks very much!:)

daemoncycler

---

### Post by Toz on 2012-11-04
> **daemoncycler said:**
> Found a driver update on nvidia.com.  NVIDIA Driver **Version: 96.43.23 **dated Fri, Sept 14, 2012.  Should I consider installing it & will that reset the agp driver settings?
I belong to the "if it ain't broke, don't fix it" camp. But if you want to try as a learning experience...

Since this thread may be of help to others, can you mark it as Solved using the "Thread Tools" link in the top right of this page?

---

### Post by daemoncycler on 2012-11-04
Absolutely & I hope this thread does help someone else.

Thanks for everything.

---

### Post by daemoncycler on 2013-09-07
Thanks again Toz,

have referred to this thread on more than one occasion to assist family, friends & friends of family with suspend & blacklist issues.

L / Ubuntu are absolutely the way to go for older machines with the eventual retirement of XP.

---

