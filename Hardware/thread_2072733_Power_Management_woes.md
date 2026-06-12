---
title: "Power Management woes"
date: 2012-10-18
forum: Hardware
---

### Post by Firepowerforfreedom on 2012-10-18
I'm having a struggle with both of my T40-series (T42 and T43, to be exact) ThinkPads: when I check PowerTop, I get this list (on my T43; the T42 is similar but has a Radeon Mobility 9600 rather than GMA900):

>> Bad           Wireless Power Saving for interface wlan0                                                
   Bad           VM writeback timeout
   Bad           NMI watchdog should be turned off
   Bad           Autosuspend for USB device EHCI Host Controller [usb1]
   Bad           Autosuspend for USB device UHCI Host Controller [usb2]
   Bad           Autosuspend for USB device UHCI Host Controller [usb3]
   Bad           Autosuspend for USB device UHCI Host Controller [usb4]
   Bad           Autosuspend for USB device UHCI Host Controller [usb5]
   Bad           Runtime PM for PCI Device Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor
   Bad           Runtime PM for PCI Device Atheros Communications Inc. AR5212/AR5213 Wireless Network Adap
   Bad           Runtime PM for PCI Device Broadcom Corporation NetXtreme BCM5751M Gigabit Ethernet PCI Ex
   Bad           Wake-on-lan status for device eth0
   Good          Runtime PM for PCI Device Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge
   Good          Runtime PM for PCI Device Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI
   Good          Runtime PM for PCI Device Intel Corporation 82801FBM (ICH6M) SATA Controller
   Good          Runtime PM for PCI Device Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI
   Good          Runtime PM for PCI Device Texas Instruments PCI1510 PC card Cardbus Controller
   Good          Runtime PM for PCI Device Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Aud
   Good          Runtime PM for PCI Device Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI
   Good          Runtime PM for PCI Device Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI
   Good          Runtime PM for PCI Device Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI
   Good          Runtime PM for PCI Device Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Expre
   Good          Runtime PM for PCI Device Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Expre
   Good          Runtime PM for PCI Device Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Cont
   Good          Wake-on-lan status for device wlan0
   Good          Wake-on-lan status for device irda0
   Good          Using 'ondemand' cpufreq governor

The "Wireless power saving" entry is a driver issue with Ath5k (power management apparently isn't quite working yet), but I'm at my wit's end trying to diagnose what's the deal with the other "Bad" entries. 

Help?

---

