---
title: "chronic pauses with x399 and 1950x ryzen theadripper"
date: 2018-03-27
forum: Hardware
---

### Post by auburn on 2018-03-27
We've done 3 installations so far with ubuntu 16.04, ubuntu-mate-16.04, and lastly with ubuntu-mate17.10.
We have what look like network pauses but I'm suspicious it's bigger.

If I leave ping google.com in a terminal, it will pause for 15 seconds or so, every 3 or so minutes.
But simultaneously, if I leave a session pinging a local ip address and or doing an apt upgrade, those [processes will NOT pause.
It feels like it's a dns issue. I've tried stock NetworkManager settings and NetworkManager disabled/resolvconf removed/static resolv.conf

Here are the results of journalctl -p3:
```

-- Reboot --                     
Mar 27 10:04:19 mypc kernel: Couldn't get size: 0x800000000000000e
Mar 27 10:04:19 mypc kernel: MODSIGN: Couldn't get UEFI db list
Mar 27 10:04:19 mypc kernel: Couldn't get size: 0x800000000000000e
Mar 27 10:04:19 mypc kernel: Couldn't get size: 0x800000000000000e
Mar 27 10:04:20 mypc avahi-daemon[1185]: chroot.c: open() failed: No such file or directory
Mar 27 10:04:20 mypc NetworkManager[1193]: ((src/devices/nm-device.c:1452)): assertion '<dropped>' failed 
Mar 27 10:04:21 mypc wpa_supplicant[1389]: dbus: wpa_dbus_get_object_properties: failed to get object properties: (none) none
Mar 27 10:04:21 mypc wpa_supplicant[1389]: dbus: Failed to construct signal 
Mar 27 10:04:21 mypc wpa_supplicant[1389]: Could not read interface p2p-dev-wlp5s0 flags: No such device 
Mar 27 10:04:22 mypc lightdm[1444]: PAM unable to dlopen(pam_kwallet.so): /lib/security/pam_kwallet.so: cannot open shared objec
Mar 27 10:04:22 mypc lightdm[1444]: PAM adding faulty module: pam_kwallet.so
Mar 27 10:04:22 mypc lightdm[1444]: PAM unable to dlopen(pam_kwallet5.so): /lib/security/pam_kwallet5.so: cannot open shared obj
Mar 27 10:04:22 mypc lightdm[1444]: PAM adding faulty module: pam_kwallet5.so
Mar 27 10:04:23 mypc lightdm[1534]: PAM unable to dlopen(pam_kwallet.so): /lib/security/pam_kwallet.so: cannot open shared objec
Mar 27 10:04:23 mypc lightdm[1534]: PAM adding faulty module: pam_kwallet.so
Mar 27 10:04:23 mypc lightdm[1534]: PAM unable to dlopen(pam_kwallet5.so): /lib/security/pam_kwallet5.so: cannot open shared obj
Mar 27 10:04:23 mypc lightdm[1534]: PAM adding faulty module: pam_kwallet5.so
Mar 27 10:04:35 mypc pulseaudio[2135]: [pulseaudio] pid.c: Daemon already running.
Mar 27 10:04:35 mypc pulseaudio[2146]: [pulseaudio] pid.c: Daemon already running.
Mar 27 10:04:35 mypc pulseaudio[2149]: [pulseaudio] pid.c: Daemon already running.                                                     
Mar 27 10:04:50 mypc systemd[1]: Failed to start Network Manager Wait Online. 
```

some lines that stuck out to me from journalctl -p4:
```

-- Reboot --                                        
Mar 27 10:04:19 mypc kernel:    #2   #3   #4   #5   #6   #7   #8   #9  #10  #11  #12  #13  #14  #15  #16  #17  #18  #19  #20  #21  #22  #23  #24  #25  #26  #27  #28  #29  #30  #31
Mar 27 10:04:19 mypc kernel: PCCT header not found. 

(repeated 20 or so times:)
Mar 27 10:04:19 mypc kernel: [Firmware Bug]: ACPI MWAIT C-state 0x0 not supported by HW (0x0)

(these just one time)
Mar 27 10:04:19 mypc kernel: Couldn't get size: 0x800000000000000e       
Mar 27 10:04:19 mypc kernel: MODSIGN: Couldn't get UEFI db list       
Mar 27 10:04:19 mypc kernel: Couldn't get size: 0x800000000000000e       
Mar 27 10:04:19 mypc kernel: Couldn't get size: 0x800000000000000e 

```

SPECS:
Micro-Star X399 GAMING PRO CARBON AC (MS-7B09)     
American Megatrends firmware 1.7 
AMD Ryzen Threadripper 1950X 16-Core 1.9ghz
128gb ram
Intel Corporation I211 Gigabit Network Connection (rev 03)         
Host bridge: Advanced Micro Devices, Inc. [AMD] Device 1450       
Host bridge: Advanced Micro Devices, Inc. [AMD] Device 1452                                                                    

xGeForce GTX 1080 Ti] (rev a1)
ubuntu-mate 17.10.1

nvidia proprietary driver: 390.25 from:
[http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu](http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu)

Any suggestions are appreciated!

---

### Post by auburn on 2018-03-27
correction, it's a  2.2ghz cpu

---

