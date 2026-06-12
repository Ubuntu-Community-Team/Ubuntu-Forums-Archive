---
title: "Slow booting time"
date: 2007-10-15
forum: Hardware &amp; Laptops
---

### Post by heha on 2007-10-15
My Laptop is with a very slow booting time. Attached is my bootchart log.

Below is my system information:
Hardward:  IBM T43 (CPU1.73G 512MBRAM 120GHDD)
OS:               ubuntu7.04 (kernel-2.6.20-16)

System freezes very long time here(Bold font):

Oct 14 09:26:01 ubuntu kernel: [   16.528000] cs: IO port probe 0xa00-0xaff: clean.
Oct 14 09:26:01 ubuntu kernel: [   17.012000] intel8x0_measure_ac97_clock: measured 55524 usecs
Oct 14 09:26:01 ubuntu kernel: [   17.012000] intel8x0: clocking to 48000
Oct 14 09:26:01 ubuntu kernel: [   20.996000] IBM TrackPoint firmware: 0x0e, buttons: 3/3
**Oct 14 09:26:01 ubuntu kernel: [   21.240000] input: TPPS/2 IBM TrackPoint as /class/input/input5**
Oct 14 09:26:01 ubuntu kernel: [   75.672000] NET: Registered protocol family 10
Oct 14 09:26:01 ubuntu kernel: [   75.672000] lo: Disabled Privacy Extensions
Oct 14 09:26:01 ubuntu kernel: [   75.672000] ADDRCONF(NETDEV_UP): eth0: link is not ready
Oct 14 09:26:01 ubuntu kernel: [   75.804000] fuse init (API version 7.8)
Oct 14 09:26:01 ubuntu kernel: [   75.828000] lp0: using parport0 (interrupt-driven).
Oct 14 09:26:01 ubuntu kernel: [   75.864000] usbcore: registered new interface driver usbserial

Any idea? Thanks so much!!

---

### Post by heha on 2007-10-16
Can anybody help me to solve it? Thanks!:(:(:(

---

### Post by heha on 2007-10-18
??? any comments?

---

### Post by kvonb on 2007-10-18
How do you get that bootchart thing?  That would be useful :).

I can't really help you though, but I would maybe look at /etc/X11/xorg.conf
, and especially the mouse input devices.

I added a Synaptics touchpad section to mine, but I don't have an IBM.

I attached my xorg.conf just in case it helps.

---

### Post by heha on 2007-10-18
Thanks for your reply!

> **kvonb said:**
> How do you get that bootchart thing?  That would be useful :).

See here: [http://www.bootchart.org/](http://www.bootchart.org/)
> **kvonb said:**
> 
I can't really help you though, but I would maybe look at /etc/X11/xorg.conf
, and especially the mouse input devices.

I added a Synaptics touchpad section to mine, but I don't have an IBM.

I attached my xorg.conf just in case it helps.

I dont think it's tracepoint(mouse) problem, because It works fine when I just installed ubuntu. But after I updated some packages or installed some softwares, it becomes slow. I guess some drivers probably load fail, so system freeze here for a timeout. But I just dont know how to trace where causes this issue. 
Can anybody give me some tips? Thanks!

---

### Post by Cannaregio on 2007-10-18
Did you check dsmeg?
Did you check  the relevant files in /var/log?
Did you check if the iptables have rules that are slowing the boot down?

```
iptables -L
```

---

### Post by heha on 2007-10-18
> **Cannaregio said:**
> Did you check dsmeg?
Did you check  the relevant files in /var/log?

Yes, I did, but dont know what causes this issue. :)

> **Cannaregio said:**
> 
Did you check if the iptables have rules that are slowing the boot down?

```
iptables -L
```
alex@ubuntu:/work/rootfs/szsmartphone$ sudo iptables -L
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination

---

