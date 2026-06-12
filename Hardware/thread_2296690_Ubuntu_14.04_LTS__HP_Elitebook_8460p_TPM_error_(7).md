---
title: "Ubuntu 14.04 LTS  HP Elitebook 8460p TPM error (7) boot error"
date: 2015-09-28
forum: Hardware
---

### Post by donnywood-studio on 2015-09-28
HI All

I am new to this forum , and recently have been running 14.04 LTS  now on my Elitebook 8460p .  In the last two or three 14.04 Software update I am getting TPM error at boot screen  .   Appreciate some pointers on how to get rid of this boot message at boot time

"A TPM error (7) occurred attempting to read a pcr value"

Searched the net and i manage to run these command below to get status of this process . I am not sure if the correct action  here is to fix it or to suppress the mesages .   It 

The laptop does boot fine and works ok though. 

------
alcatel@alcatel-[FONT=arial black]HP-EliteBook-8460p:/etc/modprobe.d$ sudo tcsd -f[/FONT]
[sudo] password for alcatel: 
TCSD TDDL ioctl: (25) Inappropriate ioctl for device
TCSD TDDL Falling back to Read/Write device support.
TCSD trousers 0.3.11.2: TCSD up and running.

------
alcatel@alcatel-[FONT=arial black]HP-EliteBook-8460p:/usr/sbin$ tpm_version[/FONT]
  TPM 1.2 Version Info:
  Chip Version:        1.2.3.17
  Spec Level:          2
  Errata Revision:     2
  TPM Vendor ID:       IFX
  Vendor Specific data: 03110008 00
  TPM Version:         01010000
  Manufacturer Info:   49465800
alcatel@alcatel-HP-EliteBook-8460p:/usr/sbin$ tpm_selftest
  TPM Test Results: bfbff5bf ff8f
alcatel@alcatel-HP-EliteBook-8460p:/usr/sbin$ tpm_nvinfo
NVRAM index   : 0x10000001 (268435457)
PCR read  selection:
 Localities   : ALL
PCR write selection:
 Localities   : ALL
Permissions   : 0x00001002 (WRITEALL|OWNERWRITE)
bReadSTClear  : FALSE
bWriteSTClear : FALSE
bWriteDefine  : FALSE
Size          : 20 (0x14)


--------

Syslog MSG

Sep 28 18:34:00 alcatel-HP-EliteBook-8460p AptDaemon.Worker: CRITICAL: tpm-tools: dependency problems - leaving unconfigured
Sep 28 18:34:02 alcatel-HP-EliteBook-8460p AptDaemon.Worker: CRITICAL: tpm-tools: dependency problems - leaving unconfigured

---

### Post by ajgreeny on 2015-09-28
There seems to be an old launchpad bug about this problem when using an HP 8560 which I will have to leave you to investigate further.  It looks as if there were some possible solutions to it with kernel updates, but they were older kernels than you are running, so that may be a wild goose chase, but have a good look through and see if you get any clues.
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/864739](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/864739)

---

### Post by tgalati4 on 2015-09-28
Syslog is telling you that you have a configuration/dependency problem.

Open a terminal:

```
apt-cache policy tpm-tools
```

There are debug versions in the repositories:

> tgalati4@Mint17 ~ $ apt-cache search tpm-tools
libtpm-unseal-dev - Management tools for the TPM hardware (development)
libtpm-unseal1 - Management tools for the TPM hardware (library)
tpm-tools - Management tools for the TPM hardware (tools)
tpm-tools-dbg - Management tools for the TPM hardware (debug)


You could install those and then run the debugger to capture the errors in real time.  Or simply reinstall and reboot.

Of course it could be one of the dependencies is broken:

> tgalati4@Mint17 ~ $ apt-cache depends tpm-tools
tpm-tools
  Depends: libc6
  Depends: libssl1.0.0
  Depends: libtpm-unseal1
  Depends: libtspi1
  Depends: opencryptoki
  Depends: trousers
  Conflicts: tpm-tools:i386


Try reinstalling first:

```
sudo apt-get purge tpm-tools
sudo apt-get install tpm-tools
```

Then reboot.

---

### Post by donnywood-studio on 2015-09-28
> **ajgreeny said:**
> There seems to be an old launchpad bug about this problem when using an HP 8560 which I will have to leave you to investigate further.  It looks as if there were some possible solutions to it with kernel updates, but they were older kernels than you are running, so that may be a wild goose chase, but have a good look through and see if you get any clues.
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/864739](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/864739)

thanks ajgreeny,  i have gone thru  the thread and looks like ended on ubuntu 12.04.   Will dig thru  ubuntu bug site for latest kernel fixes if any.

---

### Post by donnywood-studio on 2015-10-05
> **tgalati4 said:**
> Syslog is telling you that you have a configuration/dependency problem.

Open a terminal:

```
apt-cache policy tpm-tools
```

There are debug versions in the repositories:



You could install those and then run the debugger to capture the errors in real time.  Or simply reinstall and reboot.

Of course it could be one of the dependencies is broken:



Try reinstalling first:

```
sudo apt-get purge tpm-tools
sudo apt-get install tpm-tools
```

Then reboot.

thanks [COLOR=#000000]tgalati4 for the pointers.   I been away and since then i had two  SW  update.  Its not causing any harm at the moment and I also found these messages in the boot log i.e no TPM chip..   I have decided to just leave it alone .   I will mark the thread SOLVED for now.
[/COLOR]
 **alcatel@alcatel-HP-EliteBook-8460p:~$ dmesg|grep TPM**
[    1.083865] tpm_tis 00:01: 1.2 TPM (device-id 0xB, rev-id 16)
[    1.310437] tpm_tis 00:01: TPM is disabled/deactivated (0x7)
[    1.402642] tpm_tis 00:01: A TPM error (7) occurred attempting to read a pcr value
[    1.402683] ima: No TPM chip found, activating TPM-bypass!
alcatel@alcatel-HP-EliteBook-8460p:~$ uname -a
Linux alcatel-HP-EliteBook-8460p 3.16.0-50-generic #66~14.04.1-Ubuntu SMP Thu Sep 10 17:05:00 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux
alcatel@alcatel-HP-EliteBook-8460p:~$

---

### Post by tgalati4 on 2015-10-05
TPM is a complicated framework:  [http://resources.infosecinstitute.com/linux-tpm-encryption-initializing-and-using-the-tpm/](http://resources.infosecinstitute.com/linux-tpm-encryption-initializing-and-using-the-tpm/)

There are different versions and different ways of setting it up.  So it's possible that it is simply a configuration problem.  Be careful though, you don't want to lock yourself out of your machine.

More configuration:  [http://askubuntu.com/questions/414747/does-ubuntu-use-tpm-2-0-chip](http://askubuntu.com/questions/414747/does-ubuntu-use-tpm-2-0-chip)

---

