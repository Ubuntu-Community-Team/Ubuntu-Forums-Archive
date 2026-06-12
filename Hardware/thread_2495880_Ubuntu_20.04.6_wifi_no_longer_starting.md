---
title: "Ubuntu 20.04.6 wifi no longer starting"
date: 2024-03-05
forum: Hardware
---

### Post by xian555 on 2024-03-05
Ubuntu 20.04.6 with Ubuntu Pro, Mate 1.26 Kernel 5.15, Marco and lightdm  (all fully up to date) running on Dell Precision M6800 (with latest  firmware) Laptop i7-4600M with 16GB RAM and 250GB Kingston SA400S3 SSD

Kernels installed:  5.15.0-97 with wifi no longer starting
                             5.15.0-94 with no issues
both kernels running on same ssd with common iwlwifi (and associated:  dvm, mvm, ) driver files present and working under the -94 kernel  version, but not getting loaded by the -97 boot.

While running off my usual -97 kernel, problem started while  investigating issues with regular Tilda crashes and some modules like  the desktop selector crashing occasionally.  Examination of logs  indicated issues with the generic 'nouveau' driver with the nvidia card,  and further investigation pointed to incompatibility with a recent  Ubuntu or Kernel update?  A disastrous and very long attempt to go to  latest Nvidia driver lead to computer freezing and forced power down.   All Nvidia drivers were purged and configuration re-established to use  problem 'nouveau' driver, and was able to boot again into X.  However a  new problem appeared:  the wifi no longer works.  Investigation shows  that the driver does not load anymore, but is present and correct  version, as it works on exactly same computer with -94 kernel, and was  working on the -97 kernel.

I'm an advanced user of Ubuntu (15 years) but not an expert or  programmer.  Hacked at this little problem for 4 days with chatGPT4 to  see if I could solve it on my own.  Likely real experts hear will find  this amount of time rediculous, but I don't quite know the innards of  the the os, like details of the boot sequence between a GRUB 2 menu  choice and the process of booting all the modules and kernels, etc. and  what's amiss for the wifi module to be loaded.  Amoung things tried:[INDENT]a) manually loading iwlwifi with modprobe
b) purging the -97 kernel, re-installing kernel
c) assumed a mystical reason why the iwlwifi driver would work with one  kernel version and not the other so reloaded the latest version of the  driver from Intel[/INDENT]

Attached in an archive are 3 files:
1) system profile using the script system-info, with some details not  pertinent removed (list of all software, ...) removed, but complete  otherwise
2) using the script wireless-info the results with the -94 and those for the -97 kernels;

Likely the results of the following tests will also help:

** >>> tests run with -94 kernel **

~$ lspci -nnk | grep -A2 0280
03:00.0 Network controller [0280]: Intel Corporation Wireless 7260 [8086:08b1] (rev 73)
    Subsystem: Intel Corporation Dual Band Wireless-AC 7260 [8086:4470]
    Kernel driver in use: iwlwifi

~$ lspci -nnk | grep -A2 0280
03:00.0 Network controller [0280]: Intel Corporation Wireless 7260 [8086:08b1] (rev 73)
    Subsystem: Intel Corporation Dual Band Wireless-AC 7260 [8086:4470]
11:00.0 SD Host controller [0805]: O2 Micro, Inc. SD/MMC Card Reader Controller [1217:8520] (rev 01)


**>>> tests run with -97 kernel**~$ sudo modprobe -v iwlwifi
modprobe: ERROR: ../libkmod/libkmod-module.c:838 kmod_module_insert_module() could not find module by name='iwlwifi'
modprobe: ERROR: could not insert 'iwlwifi': Unknown symbol in module, or unknown parameter (see dmesg)

      	 	 	 	  modinfo iwlwifi | grep depends
~$ modinfo iwlwifi | grep depends
modinfo: ERROR: Module iwlwifi not found.

grep -r iwlwifi /etc/modprobe.d/ /usr/lib/modprobe.d/
/etc/modprobe.d/iwlwifi.conf:# /etc/modprobe.d/iwlwifi.conf
/etc/modprobe.d/iwlwifi.conf:# iwlwifi will dyamically load either iwldvm or iwlmvm depending on the
/etc/modprobe.d/iwlwifi.conf:# microcode file installed on the system.  When removing iwlwifi, first
/etc/modprobe.d/iwlwifi.conf:# remove the iwl?vm module and then iwlwifi.
/etc/modprobe.d/iwlwifi.conf:remove iwlwifi \

 >>> in Summary:
A) both kernel versions had wifi working, and the -97 wifi stopped  working after a severe computer crash associated with an nvidia driver  updated.
B) the drivers are the latest correct versions and in the right place  but the -97 kernel reports not finding them, yet they have not moved  since it was previously working with the same kernel
C) something in the boot process does not seem to be detecting the intel wifi card and triggering the driver(s) to load

Now the commands above to generate those test results are from chatGPT4,  as they are beyond my experience at this time.  I've gone as far as I  can go on my own and any help would be appreciated.  Thanks very much.

xian555

---

