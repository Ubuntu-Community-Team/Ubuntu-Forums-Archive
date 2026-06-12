---
title: "Send faxes with USR USR5637 faxmodem"
date: 2020-09-04
forum: Hardware
---

### Post by wellbox on 2020-09-04
Hi Ubuntu community,

I bought a faxmodem U.S. Robotics USR5637 56K and want to make it run under Ubuntu 18.04.4 LTS.
As the documentation of USR tells, the modem should work out of the box. But unfortunately it does not.

E.g. I do miss the serial device in /dev/tty [1]. Even if lsusb [2] sees it.

Maybe I'm missing a Kernel module? But I'm not sure how to proceed.
Any hints of how to make it visible under /dev/tty*

My System: [3]


Thanks in advance

[1]
```
ls /dev/ttyU* /dev/ttyA* /dev/ttyH*
ls: cannot access '/dev/ttyU*': No such file or directory
ls: cannot access '/dev/ttyA*': No such file or directory
ls: cannot access '/dev/ttyH': No such file or directory
```

[2]
```
lsusb
Bus 002 Device 002: ID 8087:8000 Intel Corp.
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:8008 Intel Corp.
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 002: ID 0baf:0303 U.S. Robotics USR5637 56K Faxmodem
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

[3]
```
uname -a
Linux dabdabdab 4.15.0-108-generic #109-Ubuntu SMP Fri Jun 19 11:33:10 UTC 2020 x86_64 x86_64 x86_64 GNU/Linux
```
```
cat /etc/issue
Ubuntu 18.04.4 LTS \n \l
```
```
lsmod
Module                  Size  Used by
vboxpci                24576  0
vboxnetadp             28672  0
vboxnetflt             28672  0
vboxdrv               471040  3 vboxpci,vboxnetadp,vboxnetflt
xt_conntrack           16384  1
ipt_MASQUERADE         16384  1
nf_nat_masquerade_ipv4    16384  1 ipt_MASQUERADE
nfnetlink              16384  1
xfrm_user              32768  1
xfrm_algo              16384  1 xfrm_user
xt_addrtype            16384  2
iptable_nat            16384  1
nf_conntrack_ipv4      16384  3
nf_defrag_ipv4         16384  1 nf_conntrack_ipv4
nf_nat_ipv4            16384  1 iptable_nat
nf_nat                 32768  2 nf_nat_masquerade_ipv4,nf_nat_ipv4
nf_conntrack          131072  6 xt_conntrack,nf_nat_masquerade_ipv4,nf_conntrack_ipv4,nf_nat,ipt_MASQUERADE,nf_nat_ipv4
overlay                77824  0
aufs                  241664  0
binfmt_misc            20480  1
nls_iso8859_1          16384  1
kvm_intel             217088  0
kvm                   614400  1 kvm_intel
irqbypass              16384  1 kvm
video                  45056  0
sch_fq_codel           20480  2
iptable_filter         16384  1
ip6table_filter        16384  0
ip6_tables             28672  1 ip6table_filter
br_netfilter           24576  0
bridge                155648  1 br_netfilter
stp                    16384  1 bridge
llc                    16384  2 bridge,stp
arp_tables             24576  0
ib_iser                49152  0
rdma_cm                61440  1 ib_iser
iw_cm                  45056  1 rdma_cm
ib_cm                  53248  1 rdma_cm
ib_core               221184  4 rdma_cm,iw_cm,ib_iser,ib_cm
iscsi_tcp              20480  0
libiscsi_tcp           20480  1 iscsi_tcp
libiscsi               53248  3 libiscsi_tcp,iscsi_tcp,ib_iser
scsi_transport_iscsi    98304  3 iscsi_tcp,ib_iser,libiscsi
parport_pc             32768  0
ppdev                  20480  0
lp                     20480  0
parport                49152  3 parport_pc,lp,ppdev
ip_tables              28672  2 iptable_filter,iptable_nat
x_tables               40960  8 ip6table_filter,xt_conntrack,iptable_filter,ipt_MASQUERADE,xt_addrtype,ip6_tables,ip_tables,arp_tables
autofs4                40960  2
btrfs                1138688  1
zstd_compress         163840  1 btrfs
raid10                 53248  0
raid456               147456  0
async_raid6_recov      20480  1 raid456
async_memcpy           16384  2 raid456,async_raid6_recov
async_pq               16384  2 raid456,async_raid6_recov
async_xor              16384  3 async_pq,raid456,async_raid6_recov
async_tx               16384  5 async_pq,async_memcpy,async_xor,raid456,async_raid6_recov
xor                    24576  2 async_xor,btrfs
raid6_pq              114688  4 async_pq,btrfs,raid456,async_raid6_recov
libcrc32c              16384  3 nf_conntrack,nf_nat,raid456
raid1                  40960  0
raid0                  20480  0
multipath              16384  0
linear                 16384  0
crct10dif_pclmul       16384  0
crc32_pclmul           16384  0
ghash_clmulni_intel    16384  0
pcbc                   16384  0
aesni_intel           188416  0
aes_x86_64             20480  1 aesni_intel
crypto_simd            16384  1 aesni_intel
glue_helper            16384  1 aesni_intel
cryptd                 24576  3 crypto_simd,ghash_clmulni_intel,aesni_intel
e1000e                249856  0
ahci                   40960  4
ptp                    20480  1 e1000e
libahci                32768  1 ahci
pps_core               20480  1 ptp
```

---

### Post by SeijiSensei on 2020-09-04
Maybe this will help:

[https://legacy.hylafax.org/archive/2010-11/msg00141.php](https://legacy.hylafax.org/archive/2010-11/msg00141.php)

[https://help.ubuntu.com/community/Minicom](https://help.ubuntu.com/community/Minicom)

That document suggests using ttyUSB0 instead of ttyS0.

I've only ever used modems with traditional serial ports so I can't be more help.

---

