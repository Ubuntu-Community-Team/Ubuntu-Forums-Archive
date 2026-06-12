---
title: "Ubuntu 18.04 HUAWEI Mobile Broadband Module issue"
date: 2018-05-06
forum: Hardware
---

### Post by giuliorossetti on 2018-05-06
Hi,
I have some issue related to an internal 4G/LTE modem on my laptop: Ubuntu 18.04 recognizes it but it seems not willing to let me use it :)

Some additional info:

**lsusb**[B] | grep Huawei


[/B]```

Bus 001 Device 002: ID 12d1:15bb Huawei Technologies Co., Ltd. ME936 LTE/HSDPA+ 4G modem

```



**usb****-devices**

```


 T:  Bus=01 Lev=01 Prnt=01 Port=01 Cnt=01 Dev#=  2 Spd=480 MxCh= 0D:  Ver= 2.00 Cls=ef(misc ) Sub=02 Prot=01 MxPS=64 #Cfgs=  3
P:  Vendor=12d1 ProdID=15bb Rev=00.01
S:  Manufacturer=Huawei Technologies Co., Ltd.
S:  Product=HUAWEI Mobile Broadband Module
C:  #Ifs= 6 Cfg#= 2 Atr=a0 MxPwr=500mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=02(commc) Sub=0d Prot=00 Driver=cdc_ncm
I:  If#= 1 Alt= 1 #EPs= 2 Cls=0a(data ) Sub=00 Prot=00 Driver=cdc_ncm
I:  If#= 2 Alt= 0 #EPs= 3 Cls=ff(vend.) Sub=05 Prot=10 Driver=option
I:  If#= 3 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=05 Prot=13 Driver=option
I:  If#= 4 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=05 Prot=12 Driver=option
I:  If#= 5 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=05 Prot=14 Driver=option



```

 **mmcli**[B] -L

[/B]```

Found 1 modems:
    /org/freedesktop/ModemManager1/Modem/3 [Huawei Technologies Co., Ltd.] ME936

```
[B]mmcli -m 3 | grep -Ev "imei|equipment|Numbers"

[/B]```

/org/freedesktop/ModemManager1/Modem/3 (device id 'f29e60bfc899550c5df44ef69a64b012678fe7ae')
  -------------------------
  Hardware |   manufacturer: 'Huawei Technologies Co., Ltd.'
           |          model: 'ME936'
           |       revision: '11.350.20.01.00'
           |      supported: 'gsm-umts, lte'
           |        current: 'gsm-umts, lte'
  -------------------------
  System   |         device: '/sys/devices/pci0000:00/0000:00:14.0/usb1/1-2'
           |        drivers: 'option1, cdc_ncm'
           |         plugin: 'Huawei'
           |   primary port: 'ttyUSB1'
           |          ports: 'wwp0s20f0u2c2 (net), ttyUSB1 (at), ttyUSB3 (at), ttyUSB4 (at)'
  -------------------------
  -------------------------
  Status   |           lock: 'unknown'
           | unlock retries: 'unknown'
           |          state: 'failed'
           |  failed reason: 'sim-missing'
           |    power state: 'on'
           |    access tech: 'unknown'
           | signal quality: '0' (cached)
  -------------------------
  Modes    |      supported: 'allowed: any; preferred: none'
           |        current: 'allowed: any; preferred: none'
  -------------------------
  Bands    |      supported: 'unknown'
           |        current: 'unknown'
  -------------------------
  IP       |      supported: 'ipv4, ipv6, ipv4v6'
  -------------------------
  SIM      |           path: 'none'


  -------------------------
  Bearers  |          paths: 'none'



```


The SIM is inserted and unloked, however it seems to fail for 'sim-missing'. The same SIM perfectly works on a tablet.
Do you have any suggestions on how to make the modem work?

Thanks in advance!

---

### Post by ismaelteodoro on 2018-05-07
on ubuntu 18.04
check udev rules
check by ~#udevadm monitor (plug and unplug device several times)
check permissions on ~#ls -la /dev/bus/usb/xxx/xxx/
~#crw------- 1 root root 189, 19 mai  7 21:55 020

---

### Post by giuliorossetti on 2018-05-08
> **ismaelteodoro said:**
> on ubuntu 18.04
check udev rules
check by ~#udevadm monitor (plug and unplug device several times)
check permissions on ~#ls -la /dev/bus/usb/xxx/xxx/
~#crw------- 1 root root 189, 19 mai 7 21:55 020

If I run udevadm monitor I get nothing inserting/removing the SIM card (as well as abilitating/disabilitating Broadband connection in networkmanager).
Or at least nothing more than this:


```

monitor will print the received events for:
UDEV - the event which udev sends out after rule processing
KERNEL - the kernel uevent




KERNEL[492.288139] add      /kernel/slab/:A-0000256/cgroup/filp(1826:NetworkManager-dispatcher.service) (cgroup)
KERNEL[492.288232] add      /kernel/slab/:aA-0000192/cgroup/dentry(1826:NetworkManager-dispatcher.service) (cgroup)
KERNEL[492.288247] add      /kernel/slab/inode_cache/cgroup/inode_cache(1826:NetworkManager-dispatcher.service) (cgroup)
KERNEL[492.288261] add      /kernel/slab/:A-0000192/cgroup/cred_jar(1826:NetworkManager-dispatcher.service) (cgroup)
KERNEL[492.288277] add      /kernel/slab/:A-0000208/cgroup/vm_area_struct(1826:NetworkManager-dispatcher.service) (cgroup)
KERNEL[492.288289] add      /kernel/slab/:A-0002112/cgroup/mm_struct(1826:NetworkManager-dispatcher.service) (cgroup)
KERNEL[492.288302] add      /kernel/slab/:A-0000064/cgroup/pid(1826:NetworkManager-dispatcher.service) (cgroup)
KERNEL[492.288314] add      /kernel/slab/anon_vma/cgroup/anon_vma(1826:NetworkManager-dispatcher.service) (cgroup)
KERNEL[492.288354] add      /kernel/slab/:A-0006016/cgroup/task_struct(1826:NetworkManager-dispatcher.service) (cgroup)
KERNEL[492.288443] add      /kernel/slab/proc_inode_cache/cgroup/proc_inode_cache(1826:NetworkManager-dispatcher.service) (cgroup)
KERNEL[492.289097] add      /kernel/slab/sock_inode_cache/cgroup/sock_inode_cache(1826:NetworkManager-dispatcher.service) (cgroup)
KERNEL[492.289470] add      /kernel/slab/:0000256/cgroup/kmalloc-256(1826:NetworkManager-dispatcher.service) (cgroup)
KERNEL[492.289585] add      /kernel/slab/:0000512/cgroup/kmalloc-512(1826:NetworkManager-dispatcher.service) (cgroup)
UDEV  [492.289671] add      /kernel/slab/:A-0000256/cgroup/filp(1826:NetworkManager-dispatcher.service) (cgroup)
UDEV  [492.289879] add      /kernel/slab/:aA-0000192/cgroup/dentry(1826:NetworkManager-dispatcher.service) (cgroup)
UDEV  [492.290759] add      /kernel/slab/anon_vma/cgroup/anon_vma(1826:NetworkManager-dispatcher.service) (cgroup)
UDEV  [492.291008] add      /kernel/slab/:A-0000064/cgroup/pid(1826:NetworkManager-dispatcher.service) (cgroup)
UDEV  [492.291044] add      /kernel/slab/:A-0002112/cgroup/mm_struct(1826:NetworkManager-dispatcher.service) (cgroup)
UDEV  [492.291578] add      /kernel/slab/:A-0006016/cgroup/task_struct(1826:NetworkManager-dispatcher.service) (cgroup)
UDEV  [492.291982] add      /kernel/slab/:0000512/cgroup/kmalloc-512(1826:NetworkManager-dispatcher.service) (cgroup)
UDEV  [492.292057] add      /kernel/slab/proc_inode_cache/cgroup/proc_inode_cache(1826:NetworkManager-dispatcher.service) (cgroup)
UDEV  [492.292341] add      /kernel/slab/:0000256/cgroup/kmalloc-256(1826:NetworkManager-dispatcher.service) (cgroup)
UDEV  [492.292442] add      /kernel/slab/:A-0000208/cgroup/vm_area_struct(1826:NetworkManager-dispatcher.service) (cgroup)
KERNEL[492.293116] add      /kernel/slab/:0000192/cgroup/kmalloc-192(1826:NetworkManager-dispatcher.service) (cgroup)
UDEV  [492.293146] add      /kernel/slab/sock_inode_cache/cgroup/sock_inode_cache(1826:NetworkManager-dispatcher.service) (cgroup)
KERNEL[492.293242] add      /kernel/slab/:0001024/cgroup/kmalloc-1024(1826:NetworkManager-dispatcher.service) (cgroup)
KERNEL[492.293303] add      /kernel/slab/:A-0000704/cgroup/files_cache(1826:NetworkManager-dispatcher.service) (cgroup)
KERNEL[492.293380] add      /kernel/slab/sighand_cache/cgroup/sighand_cache(1826:NetworkManager-dispatcher.service) (cgroup)
KERNEL[492.293459] add      /kernel/slab/:A-0001024/cgroup/signal_cache(1826:NetworkManager-dispatcher.service) (cgroup)
UDEV  [492.294228] add      /kernel/slab/:0000192/cgroup/kmalloc-192(1826:NetworkManager-dispatcher.service) (cgroup)
UDEV  [492.294319] add      /kernel/slab/:0001024/cgroup/kmalloc-1024(1826:NetworkManager-dispatcher.service) (cgroup)
UDEV  [492.294393] add      /kernel/slab/:A-0000192/cgroup/cred_jar(1826:NetworkManager-dispatcher.service) (cgroup)
UDEV  [492.294465] add      /kernel/slab/inode_cache/cgroup/inode_cache(1826:NetworkManager-dispatcher.service) (cgroup)
UDEV  [492.294530] add      /kernel/slab/sighand_cache/cgroup/sighand_cache(1826:NetworkManager-dispatcher.service) (cgroup)
UDEV  [492.294598] add      /kernel/slab/:A-0000704/cgroup/files_cache(1826:NetworkManager-dispatcher.service) (cgroup)
UDEV  [492.294906] add      /kernel/slab/:A-0001024/cgroup/signal_cache(1826:NetworkManager-dispatcher.service) (cgroup)
KERNEL[503.072215] remove   /kernel/slab/sock_inode_cache/cgroup/sock_inode_cache(1826:NetworkManager-dispatcher.service) (cgroup)
KERNEL[503.072258] remove   /kernel/slab/proc_inode_cache/cgroup/proc_inode_cache(1826:NetworkManager-dispatcher.service) (cgroup)
KERNEL[503.072289] remove   /kernel/slab/:A-0000256/cgroup/filp(1826:NetworkManager-dispatcher.service) (cgroup)
KERNEL[503.072305] remove   /kernel/slab/inode_cache/cgroup/inode_cache(1826:NetworkManager-dispatcher.service) (cgroup)
KERNEL[503.072327] remove   /kernel/slab/:aA-0000192/cgroup/dentry(1826:NetworkManager-dispatcher.service) (cgroup)
KERNEL[503.072404] remove   /kernel/slab/:A-0000208/cgroup/vm_area_struct(1826:NetworkManager-dispatcher.service) (cgroup)
KERNEL[503.072420] remove   /kernel/slab/:A-0002112/cgroup/mm_struct(1826:NetworkManager-dispatcher.service) (cgroup)
KERNEL[503.072430] remove   /kernel/slab/:A-0000704/cgroup/files_cache(1826:NetworkManager-dispatcher.service) (cgroup)
KERNEL[503.072454] remove   /kernel/slab/:A-0001024/cgroup/signal_cache(1826:NetworkManager-dispatcher.service) (cgroup)
KERNEL[503.072525] remove   /kernel/slab/sighand_cache/cgroup/sighand_cache(1826:NetworkManager-dispatcher.service) (cgroup)
KERNEL[503.072548] remove   /kernel/slab/:A-0006016/cgroup/task_struct(1826:NetworkManager-dispatcher.service) (cgroup)
KERNEL[503.072571] remove   /kernel/slab/:A-0000192/cgroup/cred_jar(1826:NetworkManager-dispatcher.service) (cgroup)
KERNEL[503.072600] remove   /kernel/slab/anon_vma/cgroup/anon_vma(1826:NetworkManager-dispatcher.service) (cgroup)
KERNEL[503.072632] remove   /kernel/slab/:A-0000064/cgroup/pid(1826:NetworkManager-dispatcher.service) (cgroup)
KERNEL[503.072657] remove   /kernel/slab/:0001024/cgroup/kmalloc-1024(1826:NetworkManager-dispatcher.service) (cgroup)
KERNEL[503.072688] remove   /kernel/slab/:0000512/cgroup/kmalloc-512(1826:NetworkManager-dispatcher.service) (cgroup)
KERNEL[503.072718] remove   /kernel/slab/:0000256/cgroup/kmalloc-256(1826:NetworkManager-dispatcher.service) (cgroup)
KERNEL[503.072748] remove   /kernel/slab/:0000192/cgroup/kmalloc-192(1826:NetworkManager-dispatcher.service) (cgroup)
UDEV  [503.073103] remove   /kernel/slab/sock_inode_cache/cgroup/sock_inode_cache(1826:NetworkManager-dispatcher.service) (cgroup)
UDEV  [503.073306] remove   /kernel/slab/proc_inode_cache/cgroup/proc_inode_cache(1826:NetworkManager-dispatcher.service) (cgroup)
UDEV  [503.073609] remove   /kernel/slab/:A-0000256/cgroup/filp(1826:NetworkManager-dispatcher.service) (cgroup)
UDEV  [503.073724] remove   /kernel/slab/:A-0000208/cgroup/vm_area_struct(1826:NetworkManager-dispatcher.service) (cgroup)
UDEV  [503.073855] remove   /kernel/slab/inode_cache/cgroup/inode_cache(1826:NetworkManager-dispatcher.service) (cgroup)
UDEV  [503.074332] remove   /kernel/slab/:A-0002112/cgroup/mm_struct(1826:NetworkManager-dispatcher.service) (cgroup)
UDEV  [503.074352] remove   /kernel/slab/:A-0001024/cgroup/signal_cache(1826:NetworkManager-dispatcher.service) (cgroup)
UDEV  [503.074369] remove   /kernel/slab/sighand_cache/cgroup/sighand_cache(1826:NetworkManager-dispatcher.service) (cgroup)
UDEV  [503.074385] remove   /kernel/slab/:A-0006016/cgroup/task_struct(1826:NetworkManager-dispatcher.service) (cgroup)
UDEV  [503.074409] remove   /kernel/slab/:A-0000704/cgroup/files_cache(1826:NetworkManager-dispatcher.service) (cgroup)
UDEV  [503.075163] remove   /kernel/slab/:A-0000192/cgroup/cred_jar(1826:NetworkManager-dispatcher.service) (cgroup)
UDEV  [503.075178] remove   /kernel/slab/:A-0000064/cgroup/pid(1826:NetworkManager-dispatcher.service) (cgroup)
UDEV  [503.075189] remove   /kernel/slab/:0001024/cgroup/kmalloc-1024(1826:NetworkManager-dispatcher.service) (cgroup)
UDEV  [503.075198] remove   /kernel/slab/:0000512/cgroup/kmalloc-512(1826:NetworkManager-dispatcher.service) (cgroup)
UDEV  [503.075207] remove   /kernel/slab/:aA-0000192/cgroup/dentry(1826:NetworkManager-dispatcher.service) (cgroup)
UDEV  [503.075217] remove   /kernel/slab/:0000256/cgroup/kmalloc-256(1826:NetworkManager-dispatcher.service) (cgroup)
UDEV  [503.075227] remove   /kernel/slab/anon_vma/cgroup/anon_vma(1826:NetworkManager-dispatcher.service) (cgroup)
UDEV  [503.075374] remove   /kernel/slab/:0000192/cgroup/kmalloc-192(1826:NetworkManager-dispatcher.service) (cgroup)



```

Consider that in the meantime I have the ethernet connection on, I guess the entry for Network-Manager dispatcher refer to that one...

All the permissions under /dev/bus/usb/xxx/xxx/ are

crw-rw-r-- 1 root root

---

