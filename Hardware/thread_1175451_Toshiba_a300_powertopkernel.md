---
title: "Toshiba a300 powertop/kernel"
date: 2009-06-01
forum: Hardware
---

### Post by qbasasa on 2009-06-01
Hello i have a problem my toshuba a300 1eg works on battery only 1,5h when using ubuntu while on window i had almost 3h on max energy saving, 
I read i can get more batttery time when i make custom kernel but each time i try it my xorg server wont boot ore some stuffs doesnt work.
Could i request your help in this matter?

#lspci
```
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: ATI Technologies Inc Mobility Radeon HD 3400 Series
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
03:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)
06:06.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
06:06.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
06:06.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
06:06.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)

```

#lsusb
```
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 002: ID 046d:c043 Logitech, Inc. MX320 Laser Mouse
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 04f2:b008 Chicony Electronics Co., Ltd 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```

#Powertop
```
  47,1% (728,9)            deluge : schedule_hrtimeout_range (hrtimer_wakeup) 
  25,5% (395,0)       <interrupt> : extra timer interrupt 
   8,5% (131,1)      <kernel IPI> : Rescheduling interrupts 
   4,2% ( 64,7)   USB device  6-1 : USB-PS/2 Optical Mouse (Logitech) 
   3,9% ( 60,0)       <interrupt> : fglrx[0]@PCI:1:0:0 
   3,5% ( 54,7)       <interrupt> : uhci_hcd:usb6 
   1,4% ( 21,5)       <interrupt> : eth0 
   1,3% ( 20,6)           deluged : schedule_hrtimeout_range (hrtimer_wakeup) 
   1,0% ( 16,1)           firefox : futex_wait (hrtimer_wakeup) 
   0,6% ( 10,0)        skype.real : do_nanosleep (hrtimer_wakeup) 
   0,6% ( 10,0)        skype.real : schedule_hrtimeout_range (hrtimer_wakeup) 
   0,5% (  7,4)       <interrupt> : PS/2 keyboard/mouse/touchpad
   0,3% (  4,0)     <kernel core> : usb_hcd_poll_rh_status (rh_timer_func)
   0,2% (  3,7)    scim-panel-gtk : schedule_hrtimeout_range (hrtimer_wakeup)
   0,2% (  3,5)     <kernel core> : neigh_table_init_no_netlink (neigh_periodic_timer)
   0,2% (  2,5)           deluged : schedule_timeout (process_timeout)
   0,1% (  1,7)     <kernel core> : hrtimer_start (tick_sched_timer)
   0,1% (  1,3)             conky : schedule_hrtimeout_range (hrtimer_wakeup)
   0,1% (  1,3)             tilda : schedule_hrtimeout_range (hrtimer_wakeup)
   0,1% (  1,1)    cpufreq-applet : schedule_hrtimeout_range (hrtimer_wakeup)
   0,1% (  1,0)            python : schedule_hrtimeout_range (hrtimer_wakeup)
   0,1% (  1,0)            exaile : schedule_hrtimeout_range (hrtimer_wakeup)
   0,1% (  1,0)        atieventsd : schedule_hrtimeout_range (hrtimer_wakeup)
   0,1% (  0,9)       <interrupt> : ahci
   0,0% (  0,5)      <kernel IPI> : Function call interrupts
   0,0% (  0,5)             conky : do_nanosleep (hrtimer_wakeup)
   0,0% (  0,5)   <kernel module> : queue_delayed_work (delayed_work_timer_fn)
   0,0% (  0,5)   hald-addon-stor : schedule_hrtimeout_range (hrtimer_wakeup)
   0,0% (  0,4)       gnome-panel : schedule_hrtimeout_range (hrtimer_wakeup)
   0,0% (  0,3)   gnome-power-man : schedule_hrtimeout_range (hrtimer_wakeup)
   0,0% (  0,2)     <kernel core> : page_writeback_init (wb_timer_fn)
   0,0% (  0,2)           pdflush : blk_plug_device (blk_unplug_timeout)
   0,0% (  0,2)           firefox : schedule_hrtimeout_range (hrtimer_wakeup)
   0,0% (  0,2)    NetworkManager : __netdev_watchdog_up (dev_watchdog)
   0,0% (  0,2)              Xorg : hrtimer_start (it_real_fn)
   0,0% (  0,2)    NetworkManager : schedule_hrtimeout_range (hrtimer_wakeup)
   0,0% (  0,2)   gnome-settings- : schedule_hrtimeout_range (hrtimer_wakeup)

```

I usually close deluge when on battery.

---

