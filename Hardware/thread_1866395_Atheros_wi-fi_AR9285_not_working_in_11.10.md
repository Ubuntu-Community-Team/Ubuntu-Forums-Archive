---
title: "Atheros wi-fi AR9285 not working in 11.10"
date: 2011-10-21
forum: Hardware
---

### Post by asashnov on 2011-10-21
Atheros wi-fi AR9285 not working in 11.10 on HP 635 Notebook.

On Ubuntu 11.04 works fine, so I just install kernel from Ubuntu 11.04 natty release:

$ sudo nano /etc/apt/sources.list

add this line:

deb [http://ru.archive.ubuntu.com/ubuntu/](http://ru.archive.ubuntu.com/ubuntu/) natty main restricted

$ sudo apt-get update

$ apt-cache search linux-image-

(you need search in output linux-image-2.6.xxx version)

$ sudo apt-get install linux-image-2.6.38-8-generic

Reboot and select 3-th item from GRUB (previous kernel versions), then select just installed 2.6.xxx kernel from submenu.

Enjoy :)





The following solution I try and it is NOT working for me:

1. ###############

$ sudo rfkill unblock all
$ rfkill list               
In output still  
 hardware blocked: no
 software blocked: yes

2. ##############
  Pressing Fn+F12 (wi-fi button). This is switched 'hardware block' only, software block still 'on'.


3. ##############
   Via Network Manager applet, try to set 'Enable Wireless' checkbox via right button menu.
 Check box is flicks but resets immediately.


4. ##############
$ sudo nano /etc/modprobe.d/blacklist.conf

add line
blacklist acer_wmi

Not working for me too- situation is not changed.

5. ############
Go to System->Administration->Software Sources, Updates tab, check 'Proposed updates'.
Go to System->Administration->Update Manager, uncheck all, check only kernel-related packages (linux-image). Install, reboot 
This is update my kernel from 3.0.0-12 to 3.0.0-13 version.



After all of this cases I see 'soft blocked: yes' into `rfkill list` output and not checked 'wireless networking' into Network Manager applet.

---

### Post by lightwarrior on 2011-10-21
Try this:

Create a new file /etc/modprobe.d/ath9k.conf:

sudo nano /etc/modprobe.d/ath9k.conf

Add the following line to it:

options ath9k nohwcrypt=1

Save and reboot.

---

### Post by asashnov on 2011-10-31
> **lightwarrior said:**
> 
sudo nano /etc/modprobe.d/ath9k.conf

Add the following line to it:

options ath9k nohwcrypt=1


Big thanks! It works for me! Now I can use wi-fi on 3.0.0-13 kernel.

---

### Post by g21k5 on 2012-02-08
Hello!

For some reason, the approach with the approach with 

options ath9k nohwcrypt=1

is not working in my case. I still get the following output:


```

$ rfkill list
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: yes
1: hp-wifi: Wireless LAN
	Soft blocked: yes
	Hard blocked: no
2: hp-bluetooth: Bluetooth
	Soft blocked: yes
	Hard blocked: no
3: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no

```

other output that might be of interest:
```

$ cat /etc/modprobe.d/ath9k.conf 
options ath9k nohwcrypt=1

$ iwconfig 
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off

$ dmesg | grep ath9k
[   22.414039] ath9k 0000:07:00.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[   22.414060] ath9k 0000:07:00.0: setting latency timer to 64
[   22.550525] ieee80211 phy0: Selected rate control algorithm 'ath9k_rate_control'
[   22.551709] Registered led device: ath9k-phy0

```

would somebody be so kind to help me out with this? I already regret updating from 11.04 to 11.10 ...

Thanks!

---

