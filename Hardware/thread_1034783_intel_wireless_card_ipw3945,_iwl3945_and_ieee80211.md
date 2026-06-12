---
title: "intel wireless card ipw3945, iwl3945 and ieee80211"
date: 2009-01-09
forum: Hardware
---

### Post by linderox on 2009-01-09
I have laptop hp6720s with ubuntu. There is a wireless card intel 3945ABG, but it's doesn't work under Linux, on winxp everything is Ok(Wifi button is switch ON).Before writing i have googling for some months. Can u help me to solve this problem?
What i have done:

1) ndiswrapper and my windows driver said me that "bcmwl5.inf invalid driver" and it doesn't work.
2) i downloaded ipw3945d and ipw3945-1.2.2  driver, but compiling give me error:
```

make
Makefile:53:
Makefile:54: WARNING: $SHELL not set to bash.
Makefile:55: If you experience build errors, try
Makefile:56: 'make SHELL=/bin/bash'.
Makefile:57:
/bin/sh: Syntax error: "(" unexpected
/bin/sh: Syntax error: "(" unexpected
-e
 WARNING: Your kernel contains ieee80211 symbol definitions and you
are not using the kernel's default ieee80211 subsystem.  (Perhaps you
used the out-of-tree ieee80211 subsystem's 'make install' or have
provided a path to the ieee80211 subsystem via IEEE80211_INC.)

If you wish to use the out-of-tree ieee80211 subsystem then it is
recommended to use that projects' "make patch_kernel" facility
and rebuild your kernel to update the Module symbol version information.

Failure to do this may result in build warnings and unexpected
behavior when running modules which rely on the ieee80211 subsystem.


-e  Aborting the build.  You can force the build to continue by adding:

        IEEE80211_IGNORE_DUPLICATE=y

to your make command line.


make: *** [check_inc] Error 1

```
3) I downloaded ieee80211-1.2.18 stack driver, but at compiling it is ask to replace some files in modules dir and I said "yes" and now I have troubles with it too. 
4)is it
```

$ lspci | grep Wire
10:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)

```

```

$ modprobe iwlwifi_mac8021
FATAL: Module iwlwifi_mac8021 not found.

```
```
$ sudo modprobe cfg80211
FATAL: Error inserting cfg80211 (/lib/modules/2.6.24-22-generic/kernel/net/wireless/cfg80211.ko): Unknown symbol in module, or unknown parameter (see dmesg)

```
```

$ sudo modprobe iwlwifi_mac8021
FATAL: Module iwlwifi_mac8021 not found.

```

here is my uname
```
$ uname -a
Linux ulaptop 2.6.24-22-generic #1 SMP Mon Nov 24 18:32:42 UTC 2008 i686 GNU/Linux

```

I decided to add all modules to the blacklist and load it manually
```
cat /etc/modprobe.d/blacklist
blacklist bcm43xx
blacklist iwl3945
blacklist iwlwifi_mac8021
blacklist cfg80211

```

```

$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11abg  ESSID:""
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated
          Tx-Power=0 dBm
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

```

$ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1a:4b:84:84:dc
          inet addr:192.168.1.34  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21a:4bff:fe84:84dc/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3052 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3306 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100
          RX bytes:2809690 (2.6 MB)  TX bytes:633850 (618.9 KB)
          Base address:0x4020 Memory:e4600000-e4620000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1356 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1356 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:68720 (67.1 KB)  TX bytes:68720 (67.1 KB)

```

```


```

---

### Post by linderox on 2009-01-09
up

---

### Post by mikewhatever on 2009-01-09
That wireless card works out of the box, no ndiswrapper needed.

---

### Post by dadozgb on 2009-01-09
Install package linux-backports-modules for your running kernel.

---

### Post by linderox on 2009-01-09
> Install package linux-backports-modules for your running kernel.
I did it, but my wicd didn't see anything...

---

### Post by linderox on 2009-01-09
```

master@ulaptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11abg  ESSID:""
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated
          Tx-Power=0 dBm
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

master@ulaptop:~$ sudo ifconfig wlan0 up
SIOCSIFFLAGS: No such device

```

---

### Post by dadozgb on 2009-01-09
> **linderox said:**
> I did it, but my wicd didn't see anything...

Ok. First remove those modules which you blacklisted. I have a file named iwl3945 in /etc/modprobe.d/ which contains following 
alias wlan0 iwl3945
options iwl3945 disable_hw_scan=0

unload you wireless moudles and load them again.

---

### Post by linderox on 2009-01-09
hm...
I did ...SIOCSIFFLAGS: No such device
```

$ sudo vim /etc/modprobe.d/blacklist
[sudo] password for master:
$ modprobe iw
iw_c2                   iwl3945                 iwlwifi_mac80211
iw_cm                   iwl4965                 iwlwifi_rc80211_simple
iw_cxgb3                iwlcore
master@ulaptop:~$ modprobe iw
iw_c2                   iwl3945                 iwlwifi_mac80211
iw_cm                   iwl4965                 iwlwifi_rc80211_simple
iw_cxgb3                iwlcore
master@ulaptop:~$ modprobe iwl
iwl3945                 iwlcore                 iwlwifi_rc80211_simple
iwl4965                 iwlwifi_mac80211
$ modprobe iwl3945
$ sudo modprobe iwl3945
$ sudo vim /etc/modprobe.d/iwl3945
$ sudo modprobe iwl3945
$ sudo modprobe -r iwl3945
$ sudo modprobe iwl3945
$ sudo ifconfig wlan0 up
SIOCSIFFLAGS: No such device

```

---

### Post by dadozgb on 2009-01-09
this is my lsmod | grep iwl3945 output
iwl3945                98804  0 
rfkill                 17176  2 iwl3945
mac80211              216820  1 iwl3945
led_class              12164  1 iwl3945
cfg80211               32392  2 iwl3945,mac80211

and what you get when you wrote ifconfig?

---

### Post by linderox on 2009-01-09
I crashed my cfg80211 by manual making it at my home dir with ieee80211. Any ideas how to repair it?
```

$ sudo modprobe cfg80211
FATAL: Error inserting cfg80211 (/lib/modules/2.6.24-22-generic/kernel/net/wireless/cfg80211.ko): Unknown symbol in module, or unknown parameter (see dmesg)

```

```
$ lsmod | grep iwl3945       
iwl3945                96244  0 
lbm_iwl_mac80211      242420  1 iwl3945
rfkill                  8596  2 iwl3945
led_class               6020  1 iwl3945
lbm_iwl_cfg80211       33248  2 iwl3945,lbm_iwl_mac80211

```

---

### Post by dadozgb on 2009-01-09
try to install kernel image linux-image-2.6.27-7-generic along with backports modules and than reboot in your new kernel.

---

### Post by linderox on 2009-01-09
my aptitude doesn't has this package... the last one image is 2.6.24-22, how can I update it to the 2.6.24-27?

---

### Post by linderox on 2009-01-09
up

---

### Post by dadozgb on 2009-01-10
> **linderox said:**
> my aptitude doesn't has this package... the last one image is 2.6.24-22, how can I update it to the 2.6.24-27?

You can upgrade your kernel easy. Do in term apt-cache search linux-image to see list of availabe kernel images in repo. Than pick image which has backports modules and do apt-get install linux-image whatever his name is.But if you do not install backports modules for that kernel wifi will not work.It's important to install image with a backports modules for it from repo.

---

