---
title: "Thinkpad T60 2007-CTO bluetooth not working"
date: 2008-08-01
forum: Hardware
---

### Post by L0stm4n on 2008-08-01
I've been fighting this for 2 days now. From what I gather the hardware is supported. I'm using Hardy 8.04. I keep it updated every day.

Here is the steps I've tried/what my stuff looks like. 

I cannot get bluetooth to work. I've tried hitting Fn + F5 trying to toggle. I've tried hitting it a bunch of times incase its setup to toggle all the state of on/off for bluetooth and wireless. All this does is toggle wireless network on and off. 

/proc/acpi/ibm/bluetooth doesn't exist. I cannot echo enable to it. 


```
root@joshm-laptop:~# echo enable > /proc/acpi/ibm/bluetooth
bash: /proc/acpi/ibm/bluetooth: No such file or directory
root@joshm-laptop:~# ls -al /proc/acpi/ibm/
total 0
dr-xr-xr-x  2 root root 0 2008-08-01 14:41 .
dr-xr-xr-x 12 root root 0 2008-08-01 13:22 ..
-rw-r--r--  1 root root 0 2008-08-01 14:41 beep
-rw-r--r--  1 root root 0 2008-08-01 14:41 cmos
-rw-r--r--  1 root root 0 2008-08-01 14:41 driver
-rw-r--r--  1 root root 0 2008-08-01 14:41 fan
-rw-r--r--  1 root root 0 2008-08-01 14:41 hotkey
-rw-r--r--  1 root root 0 2008-08-01 14:41 led
-rw-r--r--  1 root root 0 2008-08-01 14:41 light
-rw-r--r--  1 root root 0 2008-08-01 14:41 thermal
-rw-r--r--  1 root root 0 2008-08-01 14:41 video
-rw-r--r--  1 root root 0 2008-08-01 14:41 volume
root@joshm-laptop:~# 


```

It appears to me the correct modules are loaded:

```
root@joshm-laptop:~# lsmod | grep bluetooth
bluetooth              61156  4 rfcomm,l2cap
root@joshm-laptop:~# lsmod | grep hci
ehci_hcd               37900  0 
uhci_hcd               27024  0 
usbcore               146028  4 usbhid,ehci_hcd,uhci_hcd
root@joshm-laptop:~# lsmod | grep acpi
acpi_cpufreq           10796  2 
freq_table              5536  3 acpi_cpufreq,cpufreq_stats,cpufreq_ondemand
thinkpad_acpi          51836  0 
nvram                   9992  2 thinkpad_acpi
pata_acpi               8320  0 
libata                159344  3 ata_generic,ata_piix,pata_acpi
processor              36872  4 acpi_cpufreq,thermal
root@joshm-laptop:~#

```

Bluetooth IS enabled in the BIOS.

I am the administrator at a school with a laptop program so I have lots of spare machines to test with. I tossed my HDD in another laptop that bluetooth was working in windows in and it doesn't work on my linux drive. If I toss a windows HDD in my laptop bluetooth works. So it isn't dead hardware.


hcitool and lsusb do not show a bluetooth device.

```
root@joshm-laptop:~# hcitool dev
Devices:
root@joshm-laptop:~# lsusb
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 002: ID 0483:2016 SGS Thomson Microelectronics Fingerprint Reader
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 004: ID 045e:0040 Microsoft Corp. Wheel Mouse Optical
Bus 001 Device 001: ID 0000:0000  
root@joshm-laptop:~# 
```


I'm stuck, I'de really like to get this working so I can move pictures off my phone without the damn cord. I just moved to this laptop from a T60 model 1951-C2U and bluetooth worked fine. I only upgraded for a better graphics card. Bluetooth is the last thing to get working and I'll be happy as hell.

I'm beginning to think it is a bug with either Hardy, or the thinkpad_acpi module. I've ran into a few posts around the net from people who seem to have the same issues but no resolution. I'de like to get all the information in one big post like this one.

---

