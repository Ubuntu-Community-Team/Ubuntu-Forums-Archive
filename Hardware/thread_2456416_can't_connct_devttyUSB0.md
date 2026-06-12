---
title: "can't connct /dev/ttyUSB0"
date: 2021-01-11
forum: Hardware
---

### Post by fredy50 on 2021-01-11
Hello,

Can someone tell me why i can't connect Barcode scanner ?
i use Python3.

My python code:
```
import sys
import os, time 
import usb.core
import usb.util

f = open('/dev/ttyUSB0')
print(f.read(13))
```

But then i try to run my code it says:
FileNotFoundError: [Errno 2] No such file or directory: '/dev/ttyUSB0'


I can cd /dev/ (ls there)
```
crw-r--r--   1 root root       10,   235 Jan 11 14:58 autofs
drwxr-xr-x   2 root root             340 Jan 11 14:58 block/
crw-------   1 root root       10,   234 Jan 11 14:58 btrfs-control
drwxr-xr-x   3 root root              60 Jan 11 14:58 bus/
drwxr-xr-x   2 root root            4200 Jan 11 14:59 char/
crw-------   1 root root        5,     1 Jan 11 14:58 console
lrwxrwxrwx   1 root root              11 Jan 11 14:58 core -> /proc/kcore
drwxr-xr-x   2 root root              60 Jan 11 14:58 cpu/
crw-------   1 root root       10,    60 Jan 11 14:58 cpu_dma_latency
crw-------   1 root root       10,   203 Jan 11 14:58 cuse
drwxr-xr-x   6 root root             120 Jan 11 14:58 disk/
crw-------   1 root root       10,    62 Jan 11 14:58 ecryptfs
crw-rw----   1 root video      29,     0 Jan 11 14:58 fb0
lrwxrwxrwx   1 root root              13 Jan 11 14:58 fd -> /proc/self/fd/
crw-rw-rw-   1 root root        1,     7 Jan 11 14:58 full
crw-rw-rw-   1 root root       10,   229 Jan 11 14:58 fuse
crw-------   1 root root      254,     0 Jan 11 14:58 gpiochip0
crw-------   1 root root      243,     0 Jan 11 14:58 hidraw0
crw-------   1 root root      243,     1 Jan 11 14:58 hidraw1
crw-------   1 root root      243,     2 Jan 11 14:58 hidraw2
crw-------   1 root root      243,     3 Jan 11 14:58 hidraw3
crw-------   1 root root      243,     4 Jan 11 14:59 hidraw4
crw-------   1 root root       10,   228 Jan 11 14:58 hpet
drwxr-xr-x   2 root root               0 Jan 11 14:58 hugepages/
crw-------   1 root root       10,   183 Jan 11 14:58 hwrng
crw-------   1 root root       89,     0 Jan 11 14:58 i2c-0
crw-------   1 root root       89,     1 Jan 11 14:58 i2c-1
crw-------   1 root root       89,     2 Jan 11 14:58 i2c-2
crw-------   1 root root       89,     3 Jan 11 14:58 i2c-3
crw-------   1 root root       89,     4 Jan 11 14:58 i2c-4
crw-------   1 root root       89,     5 Jan 11 14:58 i2c-5
lrwxrwxrwx   1 root root              25 Jan 11 14:58 initctl -> /run/systemd/initctl/fifo|
drwxr-xr-x   4 root root             480 Jan 11 14:59 input/
crw-r--r--   1 root root        1,    11 Jan 11 14:58 kmsg
crw-rw----+  1 root root       10,   232 Jan 11 14:58 kvm
drwxr-xr-x   2 root root              60 Jan 11 14:58 lightnvm/
lrwxrwxrwx   1 root root              28 Jan 11 14:58 log -> /run/systemd/journal/dev-log=
brw-rw----   1 root disk        7,     0 Jan 11 14:58 loop0
brw-rw----   1 root disk        7,     1 Jan 11 14:58 loop1
brw-rw----   1 root disk        7,     2 Jan 11 14:58 loop2
brw-rw----   1 root disk        7,     3 Jan 11 14:58 loop3
brw-rw----   1 root disk        7,     4 Jan 11 14:58 loop4
brw-rw----   1 root disk        7,     5 Jan 11 14:58 loop5
brw-rw----   1 root disk        7,     6 Jan 11 14:58 loop6
brw-rw----   1 root disk        7,     7 Jan 11 14:58 loop7
brw-rw----   1 root disk        7,     8 Jan 11 14:58 loop8
crw-rw----   1 root disk       10,   237 Jan 11 14:58 loop-control
drwxr-xr-x   2 root root              60 Jan 11 14:58 mapper/
crw-------   1 root root       10,   227 Jan 11 14:58 mcelog
crw-------   1 root root      240,     0 Jan 11 14:58 media0
crw-r-----   1 root kmem        1,     1 Jan 11 14:58 mem
crw-------   1 root root       10,    57 Jan 11 14:58 memory_bandwidth
drwxrwxrwt   2 root root              40 Jan 11 14:58 mqueue/
drwxr-xr-x   2 root root              60 Jan 11 14:58 net/
crw-------   1 root root       10,    59 Jan 11 14:58 network_latency
crw-------   1 root root       10,    58 Jan 11 14:58 network_throughput
crw-rw-rw-   1 root root        1,     3 Jan 11 14:58 null
crw-------   1 root root      242,     0 Jan 11 14:58 nvme0
brw-rw----   1 root disk      259,     0 Jan 11 14:58 nvme0n1
brw-rw----   1 root disk      259,     1 Jan 11 14:58 nvme0n1p1
brw-rw----   1 root disk      259,     2 Jan 11 14:58 nvme0n1p2
brw-rw----   1 root disk      259,     3 Jan 11 14:58 nvme0n1p3
brw-rw----   1 root disk      259,     4 Jan 11 14:58 nvme0n1p4
brw-rw----   1 root disk      259,     5 Jan 11 14:58 nvme0n1p5
crw-r-----   1 root kmem        1,     4 Jan 11 14:58 port
crw-------   1 root root      108,     0 Jan 11 14:58 ppp
crw-------   1 root root       10,     1 Jan 11 14:58 psaux
crw-rw-rw-   1 root tty         5,     2 Jan 11 15:07 ptmx
drwxr-xr-x   2 root root               0 Jan 11 14:58 pts/
crw-rw-rw-   1 root root        1,     8 Jan 11 14:58 random
crw-rw-r--+  1 root netdev     10,   242 Jan 11 14:58 rfkill
lrwxrwxrwx   1 root root               4 Jan 11 14:58 rtc -> rtc0
crw-------   1 root root      249,     0 Jan 11 14:58 rtc0
drwxrwxrwt   2 root root             300 Jan 11 15:07 shm/
crw-------   1 root root       10,   231 Jan 11 14:58 snapshot
drwxr-xr-x   3 root root             300 Jan 11 14:58 snd/
lrwxrwxrwx   1 root root              15 Jan 11 14:58 stderr -> /proc/self/fd/2
lrwxrwxrwx   1 root root              15 Jan 11 14:58 stdin -> /proc/self/fd/0
lrwxrwxrwx   1 root root              15 Jan 11 14:58 stdout -> /proc/self/fd/1
crw-------   1 root root       10,   224 Jan 11 14:58 tpm0
crw-------   1 root root      253, 65536 Jan 11 14:58 tpmrm0
crw-rw-rw-   1 root tty         5,     0 Jan 11 15:07 tty
crw--w----   1 root tty         4,     0 Jan 11 14:58 tty0
crw--w----   1 root tty         4,     1 Jan 11 14:58 tty1
crw--w----   1 root tty         4,    10 Jan 11 14:58 tty10
crw--w----   1 root tty         4,    11 Jan 11 14:58 tty11
crw--w----   1 root tty         4,    12 Jan 11 14:58 tty12
crw--w----   1 root tty         4,    13 Jan 11 14:58 tty13
crw--w----   1 root tty         4,    14 Jan 11 14:58 tty14
crw--w----   1 root tty         4,    15 Jan 11 14:58 tty15
crw--w----   1 root tty         4,    16 Jan 11 14:58 tty16
crw--w----   1 root tty         4,    17 Jan 11 14:58 tty17
crw--w----   1 root tty         4,    18 Jan 11 14:58 tty18
crw--w----   1 root tty         4,    19 Jan 11 14:58 tty19
crw--w----   1 root tty         4,     2 Jan 11 14:58 tty2
crw--w----   1 root tty         4,    20 Jan 11 14:58 tty20
crw--w----   1 root tty         4,    21 Jan 11 14:58 tty21
crw--w----   1 root tty         4,    22 Jan 11 14:58 tty22
crw--w----   1 root tty         4,    23 Jan 11 14:58 tty23
crw--w----   1 root tty         4,    24 Jan 11 14:58 tty24
crw--w----   1 root tty         4,    25 Jan 11 14:58 tty25
crw--w----   1 root tty         4,    26 Jan 11 14:58 tty26
crw--w----   1 root tty         4,    27 Jan 11 14:58 tty27
crw--w----   1 root tty         4,    28 Jan 11 14:58 tty28
crw--w----   1 root tty         4,    29 Jan 11 14:58 tty29
crw--w----   1 root tty         4,     3 Jan 11 14:58 tty3
crw--w----   1 root tty         4,    30 Jan 11 14:58 tty30
crw--w----   1 root tty         4,    31 Jan 11 14:58 tty31
crw--w----   1 root tty         4,    32 Jan 11 14:58 tty32
crw--w----   1 root tty         4,    33 Jan 11 14:58 tty33
crw--w----   1 root tty         4,    34 Jan 11 14:58 tty34
crw--w----   1 root tty         4,    35 Jan 11 14:58 tty35
crw--w----   1 root tty         4,    36 Jan 11 14:58 tty36
crw--w----   1 root tty         4,    37 Jan 11 14:58 tty37
crw--w----   1 root tty         4,    38 Jan 11 14:58 tty38
crw--w----   1 root tty         4,    39 Jan 11 14:58 tty39
crw--w----   1 root tty         4,     4 Jan 11 14:58 tty4
crw--w----   1 root tty         4,    40 Jan 11 14:58 tty40
crw--w----   1 root tty         4,    41 Jan 11 14:58 tty41
crw--w----   1 root tty         4,    42 Jan 11 14:58 tty42
crw--w----   1 root tty         4,    43 Jan 11 14:58 tty43
crw--w----   1 root tty         4,    44 Jan 11 14:58 tty44
crw--w----   1 root tty         4,    45 Jan 11 14:58 tty45
crw--w----   1 root tty         4,    46 Jan 11 14:58 tty46
crw--w----   1 root tty         4,    47 Jan 11 14:58 tty47
crw--w----   1 root tty         4,    48 Jan 11 14:58 tty48
crw--w----   1 root tty         4,    49 Jan 11 14:58 tty49
crw--w----   1 root tty         4,     5 Jan 11 14:58 tty5
crw--w----   1 root tty         4,    50 Jan 11 14:58 tty50
crw--w----   1 root tty         4,    51 Jan 11 14:58 tty51
crw--w----   1 root tty         4,    52 Jan 11 14:58 tty52
crw--w----   1 root tty         4,    53 Jan 11 14:58 tty53
crw--w----   1 root tty         4,    54 Jan 11 14:58 tty54
crw--w----   1 root tty         4,    55 Jan 11 14:58 tty55
crw--w----   1 root tty         4,    56 Jan 11 14:58 tty56
crw--w----   1 root tty         4,    57 Jan 11 14:58 tty57
crw--w----   1 root tty         4,    58 Jan 11 14:58 tty58
crw--w----   1 root tty         4,    59 Jan 11 14:58 tty59
crw--w----   1 root tty         4,     6 Jan 11 14:58 tty6
crw--w----   1 root tty         4,    60 Jan 11 14:58 tty60
crw--w----   1 root tty         4,    61 Jan 11 14:58 tty61
crw--w----   1 root tty         4,    62 Jan 11 14:58 tty62
crw--w----   1 root tty         4,    63 Jan 11 14:58 tty63
crw--w----   1 root tty         4,     7 Jan 11 14:58 tty7
crw--w----   1 root tty         4,     8 Jan 11 14:58 tty8
crw--w----   1 root tty         4,     9 Jan 11 14:58 tty9
crw-------   1 root root        5,     3 Jan 11 14:58 ttyprintk
crw-rw----   1 root dialout     4,    64 Jan 11 14:58 ttyS0
crw-rw----   1 root dialout     4,    65 Jan 11 14:58 ttyS1
crw-rw----   1 root dialout     4,    74 Jan 11 14:58 ttyS10
crw-rw----   1 root dialout     4,    75 Jan 11 14:58 ttyS11
crw-rw----   1 root dialout     4,    76 Jan 11 14:58 ttyS12
crw-rw----   1 root dialout     4,    77 Jan 11 14:58 ttyS13
crw-rw----   1 root dialout     4,    78 Jan 11 14:58 ttyS14
crw-rw----   1 root dialout     4,    79 Jan 11 14:58 ttyS15
crw-rw----   1 root dialout     4,    80 Jan 11 14:58 ttyS16
crw-rw----   1 root dialout     4,    81 Jan 11 14:58 ttyS17
crw-rw----   1 root dialout     4,    82 Jan 11 14:58 ttyS18
crw-rw----   1 root dialout     4,    83 Jan 11 14:58 ttyS19
crw-rw----   1 root dialout     4,    66 Jan 11 14:58 ttyS2
crw-rw----   1 root dialout     4,    84 Jan 11 14:58 ttyS20
crw-rw----   1 root dialout     4,    85 Jan 11 14:58 ttyS21
crw-rw----   1 root dialout     4,    86 Jan 11 14:58 ttyS22
crw-rw----   1 root dialout     4,    87 Jan 11 14:58 ttyS23
crw-rw----   1 root dialout     4,    88 Jan 11 14:58 ttyS24
crw-rw----   1 root dialout     4,    89 Jan 11 14:58 ttyS25
crw-rw----   1 root dialout     4,    90 Jan 11 14:58 ttyS26
crw-rw----   1 root dialout     4,    91 Jan 11 14:58 ttyS27
crw-rw----   1 root dialout     4,    92 Jan 11 14:58 ttyS28
crw-rw----   1 root dialout     4,    93 Jan 11 14:58 ttyS29
crw-rw----   1 root dialout     4,    67 Jan 11 14:58 ttyS3
crw-rw----   1 root dialout     4,    94 Jan 11 14:58 ttyS30
crw-rw----   1 root dialout     4,    95 Jan 11 14:58 ttyS31
crw-rw----   1 root dialout     4,    68 Jan 11 14:58 ttyS4
crw-rw----   1 root dialout     4,    69 Jan 11 14:58 ttyS5
crw-rw----   1 root dialout     4,    70 Jan 11 14:58 ttyS6
crw-rw----   1 root dialout     4,    71 Jan 11 14:58 ttyS7
crw-rw----   1 root dialout     4,    72 Jan 11 14:58 ttyS8
crw-rw----   1 root dialout     4,    73 Jan 11 14:58 ttyS9
crw-------   1 root root       10,   239 Jan 11 14:58 uhid
crw-rw----+  1 root root       10,   223 Jan 11 14:58 uinput
crw-rw-rw-   1 root root        1,     9 Jan 11 14:58 urandom
crw-------   1 root root       10,   240 Jan 11 14:58 userio
drwxr-xr-x   4 root root              80 Jan 11 14:58 v4l/
crw-rw----   1 root vboxusers  10,    56 Jan 11 14:58 vboxdrv
crw-rw-rw-   1 root root       10,    55 Jan 11 14:58 vboxdrvu
crw-rw----   1 root vboxusers  10,    54 Jan 11 14:58 vboxnetctl
drwxr-x---   4 root vboxusers         80 Jan 11 14:58 vboxusb/
crw-rw----   1 root tty         7,     0 Jan 11 14:58 vcs
crw-rw----   1 root tty         7,     1 Jan 11 14:58 vcs1
crw-rw----   1 root tty         7,     2 Jan 11 14:58 vcs2
crw-rw----   1 root tty         7,     3 Jan 11 14:58 vcs3
crw-rw----   1 root tty         7,     4 Jan 11 14:58 vcs4
crw-rw----   1 root tty         7,     5 Jan 11 14:58 vcs5
crw-rw----   1 root tty         7,     6 Jan 11 14:58 vcs6
crw-rw----   1 root tty         7,   128 Jan 11 14:58 vcsa
crw-rw----   1 root tty         7,   129 Jan 11 14:58 vcsa1
crw-rw----   1 root tty         7,   130 Jan 11 14:58 vcsa2
crw-rw----   1 root tty         7,   131 Jan 11 14:58 vcsa3
crw-rw----   1 root tty         7,   132 Jan 11 14:58 vcsa4
crw-rw----   1 root tty         7,   133 Jan 11 14:58 vcsa5
crw-rw----   1 root tty         7,   134 Jan 11 14:58 vcsa6
drwxr-xr-x   2 root root              60 Jan 11 14:58 vfio/
crw-------   1 root root       10,    63 Jan 11 14:58 vga_arbiter
crw-------   1 root root       10,   137 Jan 11 14:58 vhci
crw-------   1 root root       10,   238 Jan 11 14:58 vhost-net
crw-------   1 root root       10,   241 Jan 11 14:58 vhost-vsock
crw-rw----+  1 root video      81,     0 Jan 11 14:58 video0
crw-rw-rw-   1 root root        1,     5 Jan 11 14:58 zero
```

do i missing driver for ubuntu ?

Best Regards
Frederik Frandsen

---

### Post by simon-webb on 2021-01-21
Hi. Have you tried modprobe usbserial? Normally I'd have expected the usbserial module to load automatically when you plug in the related device, but maybe this isn't happening (unless you just forgot to plug in the device before testing your code!)...in which case, you could try inserting the module manually (actually the exact instruction will be "sudo modprobe usbserial" as you won't have permission to do it as a regular user). The device file you need (/dev/ttyUSB0) clearly isn't there in your /dev so that is indeed the problem...and the usbserial kernel module is responsible for creating that device, so just typing modprobe usbserial might fix the issue.

---

### Post by SeijiSensei on 2021-01-22
Actually you'll need to use "sudo modprobe usbserial".

---

### Post by fredy50 on 2021-01-22
what will happen then i use sudo modprobe usbserial ?? nothing happen. do i do it wrong?

---

### Post by The Cog on 2021-01-22
If no error message then the module has been (or was) already installed. Unplug and re-plug the scanner.
It is entirely possible that the scanner is not recognised by the standard usbserial driver - if the makers choose to keep their driver code secret then it won't be in the standard kernel.

---

### Post by fredy50 on 2021-01-22
First use this sudo modprobe usbserial

and i try to reconnect the device / scanner. but nothing happen.

and no /dev/ttyUSB0


bash: /dev/ttyUSB0: No such file or directory

---

### Post by The Cog on 2021-01-23
Then it seems that the usbserial driver does not recognise the scanner, I suggest you look up the make of the scanner to find out what driver, if any, is available for Linux.

---

