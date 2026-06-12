---
title: "Asus: IrDA hangs..."
date: 2006-11-29
forum: Hardware &amp; Laptops
---

### Post by adk on 2006-11-29
Hello. I installed Kubuntu 6.06 on Asus A6B00L notebook and I cannot make built-in IrDA working. Irda chipset is unknown (not listed in lspci/lshw/findchip). I found in Google, that in similar Asus laptops is installed chip controlled by nsc_ircc module. So I made as root:
> 
modprobe irda
modprobe ircomm
modprobe ircomm_tty
modprobe nsc_ircc
setserial /dev/ttyS1
irattach /dev/ttyS1

Last lines from dmesg:
> 
[4295321.440000] IrCOMM protocol (Dag Brattli) 
[4295349.807000] sirdev_get_instance - ttyS1 
[4295349.807000] irtty_open - ttyS1: irda line discipline opened 
[4295350.817000] irlap_change_speed(), setting speed to 9600

After that I started irdadump and tried to send file from mobile phone:
> 
11:07:00.490112 (14230.25 ms) xid:cmd ffffffff < 00210740 S=6 s=0 (14) 
11:07:00.577050 (0086.94 ms) xid:cmd ffffffff < 00210740 S=6 s=1 (14) 
11:07:00.665045 (0088.00 ms) xid:cmd ffffffff < 00210740 S=6 s=2 (14) 
11:07:00.753023 (0087.98 ms) xid:cmd ffffffff < 00210740 S=6 s=3 (14) 
11:07:00.753084 (0000.06 ms) xid:rsp 13eabc4b > 00210740 S=6 s=3 laptop hint=0400 [ Computer ] (22)

After receiving these packets, IrDA connection hangs. I cannot kill irattach daemon (system hangs at shutdown with "Deconfiguring network interfaces" message. 

Dmesg after hang:
> 
[4295482.704000] irlap_state_reply(), QUERY_TIMER_EXPIRED <515408>

This is two-way connection, because phone returns 'Error'. (when IrDA is dead, it returns 'No device'). 

I tried with different set of kernel modules, different modes, slowing down connection, using wizard (dpkg-reconfigure irda-utils) - the same result - connection hangs after receiving 4-6 packages.

What's wrong?

---

### Post by adk on 2006-12-02
Solved. There was an unknown problem with original Ubuntu kernel. Recompiled kernel works fine.

---

