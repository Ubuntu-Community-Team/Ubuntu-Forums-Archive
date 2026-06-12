---
title: "openssl support via padlock"
date: 2014-05-01
forum: Hardware
---

### Post by lepetit on 2014-05-01
hi, i want to patch openssl for support via padlock from my via nano ?
how doing that ?

the patch 
[http://git.alpinelinux.org/cgit/aports/plain/main/openssl/](http://git.alpinelinux.org/cgit/aports/plain/main/openssl/)
0001-crypto-hmac-support-EVP_MD_CTX_FLAG_ONESHOT-and-set-.patch 
0002-engines-e_padlock-backport-cvs-head-changes.patch 
0003-engines-e_padlock-implement-sha1-sha224-sha256-accel.patch 
0004-crypto-engine-autoload-padlock-dynamic-engine.patch

```

lsmod | grep padlock
padlock_sha            13557  0 
padlock_aes            13052  0

```

```

openssl engine padlock
139655346542240:error:260B606D:engine routines:DYNAMIC_LOAD:init failed:eng_dyn.c:521:
139655346542240:error:2606A074:engine routines:ENGINE_by_id:no such engine:eng_list.c:417:id=padlock

```

```

uname -a
Linux lubuntu 3.13.0-24-generic #46-Ubuntu SMP Thu Apr 10 19:11:08 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux

```

```

lspci
00:00.0 Host bridge: VIA Technologies, Inc. VX900 Host Bridge: Host Control (rev 80)
00:00.1 Host bridge: VIA Technologies, Inc. VX900 Error Reporting
00:00.2 Host bridge: VIA Technologies, Inc. VX900 CPU Bus Controller
00:00.3 Host bridge: VIA Technologies, Inc. VX900 DRAM Bus Control
00:00.4 Host bridge: VIA Technologies, Inc. VX900 Power Management and Chip Testing Control
00:00.5 Host bridge: VIA Technologies, Inc. VX900 APIC and Central Traffic Control
00:00.6 Host bridge: VIA Technologies, Inc. VX900 Scratch Registers
00:00.7 Host bridge: VIA Technologies, Inc. VX900 North-South Module Interface Control
00:01.0 VGA compatible controller: VIA Technologies, Inc. VX900 Graphics [Chrome9 HD]
00:01.1 Audio device: VIA Technologies, Inc. Device 9170
00:03.0 PCI bridge: VIA Technologies, Inc. VX900 PCI Express Root Port 0
00:03.1 PCI bridge: VIA Technologies, Inc. VX900 PCI Express Root Port 1
00:03.2 PCI bridge: VIA Technologies, Inc. VX900 PCI Express Root Port 2
00:03.3 PCI bridge: VIA Technologies, Inc. VX900 PCI Express Root Port 3
00:03.4 Host bridge: VIA Technologies, Inc. Device e410
00:0f.0 IDE interface: VIA Technologies, Inc. VX900 Serial ATA Controller
00:10.0 USB controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.1 USB controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.2 USB controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.3 USB controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.4 USB controller: VIA Technologies, Inc. USB 2.0 (rev 90)
00:11.0 ISA bridge: VIA Technologies, Inc. VX900 Bus Control and Power Management
00:11.7 Host bridge: VIA Technologies, Inc. VX8xx South-North Module Interface Control
00:13.0 PCI bridge: VIA Technologies, Inc. VX855/VX875/VX900 PCI to PCI Bridge
00:14.0 Audio device: VIA Technologies, Inc. VT8237A/VT8251 HDA Controller (rev 20)
05:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 06)

```

---

### Post by lepetit on 2014-05-01
up

---

