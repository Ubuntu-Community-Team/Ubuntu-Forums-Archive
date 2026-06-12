---
title: "Issues enabling AMDGPU-PRO on 16.04"
date: 2017-05-03
forum: Hardware
---

### Post by mm144 on 2017-05-03
I believe i'm having issues enabling the proprietary AMD driver on my system.
I followed : [http://support.amd.com/en-us/kb-articles/Pages/AMDGPU-PRO-Install.aspx](http://support.amd.com/en-us/kb-articles/Pages/AMDGPU-PRO-Install.aspx)
I have an RX580 card and it is my first AMD card i've had in years.
When i run this command:
```
dpkg -l amdgpu-pro
```

i get:
```
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version      Architecture Description
+++-==============-============-============-=================================
ii  amdgpu-pro     17.10-414273 amd64        Meta package to install amdgpu Pr

```

So it appears to be installed.

However, i do not believe it's enabled, unless i'm completely out to lunch.
When i run:
```
lspci -nnk | grep -i vga -A3 | grep 'in use'
```
i get:
```
	Kernel driver in use: amdgpu

```
I'm under the impression that amdgpu is the open/non proprietary driver.  If so, how do i enable amdgpu-pro?
I've rebooted and i added myself to the video group.

Am i missing something?

---

### Post by QIII on 2017-05-03
amdgpu will be listed because the AMDGPU driver is the base for the AMDGPU-PRO driver, which is just AMDGPU with a proprietary overlay for some of the goodies.

Here's a quick and dirty little trick:  The load sensor value is only available through AMDGPU-PRO.  If you can call it and get a reading (it might be 0%), AMDGPU-PRO is running.

```
sudo cat /sys/kernel/debug/dri/64/amdgpu_pm_info | grep GPU\ Load
```

---

### Post by mm144 on 2017-05-03
Oh, ok!
 i do get a load value so i presume it is correct then.
Thank you,

---

