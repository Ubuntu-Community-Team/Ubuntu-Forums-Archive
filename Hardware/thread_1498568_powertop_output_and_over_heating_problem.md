---
title: "powertop output and over heating problem"
date: 2010-05-31
forum: Hardware
---

### Post by Bezi on 2010-05-31
my laptop gets over heated, even when it is almost idle.

Below is the output of powertop, 
If anyone can get anything out of this or has any general suggestion I would like to hear

thanks


$ powertop -d
PowerTOP 1.11   (C) 2007, 2008 Intel Corporation 

Collecting data for 15 seconds 


Cn	          Avg residency
C0 (cpu running)        ( 0.9%)
polling		  0.0ms ( 0.0%)
C1 halt		  0.0ms ( 0.0%)
C2		  0.3ms ( 1.0%)
C3		 11.8ms (98.1%)
P-states (frequencies)
  2.21 Ghz     0.1%
  2.21 Ghz     0.0%
  1.60 Ghz     0.0%
  1200 Mhz     0.0%
   800 Mhz    99.9%
Wakeups-from-idle per second : 111.4	interval: 15.0s
no ACPI power usage estimate available
Top causes for wakeups:
  35.3% ( 64.6)      <kernel IPI> : Rescheduling interrupts 
  19.5% ( 35.7)     <kernel core> : hrtimer_start_range_ns (tick_sched_timer) 
   8.8% ( 16.2)       <interrupt> : ata_piix 
   6.8% ( 12.5)       <interrupt> : extra timer interrupt 
   6.2% ( 11.3)     <kernel core> : hrtimer_start (tick_sched_timer) 
   5.5% ( 10.0)          nautilus : hrtimer_start_range_ns (hrtimer_wakeup) 
   3.1% (  5.6)              hald : __mod_timer (process_timeout) 
   2.7% (  4.9)       <interrupt> : ahci 
   2.2% (  4.0)     <kernel core> : __mod_timer (rh_timer_func) 
   2.1% (  3.9)        parcellite : hrtimer_start_range_ns (hrtimer_wakeup) 
   1.3% (  2.4)    sensors-applet : __mod_timer (process_timeout) 
   0.6% (  1.1)      npviewer.bin : __mod_timer (nv_kern_rc_timer) 
   0.5% (  1.0)       <interrupt> : uhci_hcd:usb3, firewire_ohci, nvidia 
   0.5% (  1.0)        checkgmail : hrtimer_start_range_ns (hrtimer_wakeup) 
   0.5% (  1.0)          metacity : __mod_timer (sky2_watchdog) 
   0.5% (  1.0)   gvfs-afc-volume : hrtimer_start_range_ns (hrtimer_wakeup) 
   0.5% (  0.9)       <interrupt> : sky2@pci:0000:05:00.0 
   0.3% (  0.5)     udisks-daemon : hrtimer_start_range_ns (hrtimer_wakeup) 
   0.3% (  0.5)   hald-addon-stor : hrtimer_start_range_ns (hrtimer_wakeup) 
   0.3% (  0.5)           iwl3945 : queue_delayed_work (delayed_work_timer_fn) 
   0.3% (  0.5)           dropbox : hrtimer_start_range_ns (hrtimer_wakeup) 
   0.3% (  0.5)               gpm : hrtimer_start_range_ns (hrtimer_wakeup) 
   0.1% (  0.3)     <kernel core> : __enqueue_rt_entity (sched_rt_period_timer) 
   0.1% (  0.3)       gnome-panel : hrtimer_start_range_ns (hrtimer_wakeup) 
   0.1% (  0.2)     <kernel core> : __mod_timer (dev_watchdog) 
   0.1% (  0.2)   hald-addon-acpi : hrtimer_start_range_ns (hrtimer_wakeup) 
   0.1% (  0.2)      rtkit-daemon : hrtimer_start_range_ns (hrtimer_wakeup) 
   0.1% (  0.2)            python : hrtimer_start_range_ns (hrtimer_wakeup) 
   0.1% (  0.2)    sensors-applet : hrtimer_start_range_ns (hrtimer_wakeup) 
   0.1% (  0.1)    gnome-terminal : hrtimer_start_range_ns (hrtimer_wakeup) 
   0.1% (  0.1)   gnome-power-man : hrtimer_start_range_ns (hrtimer_wakeup) 
   0.1% (  0.1)      npviewer.bin : __mod_timer (sta_info_cleanup) 
   0.1% (  0.1)        goldendict : hrtimer_start_range_ns (hrtimer_wakeup) 
   0.1% (  0.1)     <kernel core> : __mod_timer (sync_supers_timer_fn) 
   0.1% (  0.1)       bdi-default : __mod_timer (process_timeout) 
   0.1% (  0.1)         flush-8:0 : __mod_timer (process_timeout) 
   0.0% (  0.1)       <interrupt> : PS/2 keyboard/mouse/touchpad 
   0.0% (  0.1)      <kernel IPI> : Function call interrupts 
   0.0% (  0.1)              Xorg : hrtimer_start_range_ns (hrtimer_wakeup) 
   0.0% (  0.1)          gconfd-2 : __mod_timer (commit_timeout) 
   0.0% (  0.1)   gnome-settings- : hrtimer_start_range_ns (hrtimer_wakeup) 
   0.0% (  0.1)          events/0 : queue_delayed_work (delayed_work_timer_fn) 
   0.0% (  0.1)              hald : hrtimer_start_range_ns (hrtimer_wakeup) 
   0.0% (  0.1)     <kernel core> : __mod_timer (neigh_timer_handler) 
   0.0% (  0.1)           firefox : __mod_timer (blk_rq_timed_out_timer) 
   0.0% (  0.1)           audispd : hrtimer_start_range_ns (hrtimer_wakeup) 
   0.0% (  0.1)     udisks-daemon : __mod_timer (blk_rq_timed_out_timer) 
   0.0% (  0.1)           rpcbind : hrtimer_start_range_ns (hrtimer_wakeup) 
   0.0% (  0.1)              ntpd : __mod_timer (death_by_timeout) 
   0.0% (  0.1)          gconfd-2 : hrtimer_start_range_ns (hrtimer_wakeup) 

A USB device is active 100.0% of the time:
USB device  6-2 : USB OPTICAL MOUSE (PIXART)

Suggestion: Enable USB autosuspend by pressing the U key or adding 
usbcore.autosuspend=1 to the kernel command line in the grub config

Suggestion: increase the VM dirty writeback time from 5.00 to 15 seconds with:
  echo 1500 > /proc/sys/vm/dirty_writeback_centisecs 
This wakes the disk up less frequently for background VM activity

Suggestion: Enable SATA ALPM link power management via: 
  echo min_power > /sys/class/scsi_host/host0/link_power_management_policy
or press the S key.

Suggestion: Disable 'hal' from polling your cdrom with:  
hal-disable-polling --device /dev/cdrom 'hal' is the component that auto-opens a
window if you plug in a CD but disables SATA power saving from kicking in.

Recent USB suspend statistics
Active  Device name
100.0%	USB device  6-2 : USB OPTICAL MOUSE (PIXART)
  0.0%	USB device  2-5 : HP Webcam (Chicony Electronics Co., Ltd.)
  0.0%	USB device usb7 : UHCI Host Controller (Linux 2.6.33.5-112.fc13.x86_64 uhci_hcd)
100.0%	USB device usb6 : UHCI Host Controller (Linux 2.6.33.5-112.fc13.x86_64 uhci_hcd)
  0.0%	USB device usb5 : UHCI Host Controller (Linux 2.6.33.5-112.fc13.x86_64 uhci_hcd)
  0.0%	USB device usb4 : UHCI Host Controller (Linux 2.6.33.5-112.fc13.x86_64 uhci_hcd)
  0.0%	USB device usb3 : UHCI Host Controller (Linux 2.6.33.5-112.fc13.x86_64 uhci_hcd)
  0.0%	USB device usb2 : EHCI Host Controller (Linux 2.6.33.5-112.fc13.x86_64 ehci_hcd)
  0.0%	USB device usb1 : EHCI Host Controller (Linux 2.6.33.5-112.fc13.x86_64 ehci_hcd)

---

