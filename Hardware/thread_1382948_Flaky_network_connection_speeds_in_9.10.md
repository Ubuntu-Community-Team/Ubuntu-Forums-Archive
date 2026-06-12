---
title: "Flaky network connection speeds in 9.10"
date: 2010-01-16
forum: Hardware
---

### Post by Sporkman on 2010-01-16
I just got a machine to use as a server - it's a HP Compaq dc7900. I have installed Ubuntu 9.10 server.

Unfortunately the ethernet behavior is flaky. The connection speed sporadically drops dramatically, measured by downloading from the server a large file. Normally the download speed is around 11 mb/s, but occasionally something happens and the speeds drops to around 200 kb/s, and doesn't go back up until I reboot (restarting /etc/init.d/network doesn't work). This happened recently, and the only unusual thing that showed up in /var/log/messages (between the times when the connection was good & when it was not):
 
```
Jan 16 13:42:17 athena kernel: [98270.990132] e1000e: eth0 NIC Link is Down
Jan 16 13:42:18 athena kernel: [98272.670775] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
Jan 16 13:42:18 athena kernel: [98272.670778] 0000:00:19.0: eth0: 10/100 speed: disabling TSO

```

Does anybody know what's going on? Is this a 9.10 issue? Here is some info:

uname -a:

```
Linux athena 2.6.31-17-server #54-Ubuntu SMP Thu Dec 10 18:06:56 UTC 2009 x86_64 GNU/Linux
```


lsmod:

```
Module                  Size  Used by
ipt_REJECT              3584  0 
xt_limit                3236  0 
xt_tcpudp               3616  0 
nf_conntrack_ipv4      16376  0 
nf_defrag_ipv4          2400  1 nf_conntrack_ipv4
xt_state                2432  0 
nf_conntrack           80832  2 nf_conntrack_ipv4,xt_state
snd_hda_codec_analog    79680  1 
iptable_filter          3872  0 
ip_tables              21168  1 iptable_filter
snd_hda_intel          31880  0 
x_tables               25768  5 ipt_REJECT,xt_limit,xt_tcpudp,xt_state,ip_tables
snd_hda_codec          87424  2 snd_hda_codec_analog,snd_hda_intel
i915                  247112  0 
tpm_infineon           10044  0 
tpm                    18464  1 tpm_infineon
snd_hwdep               9128  1 snd_hda_codec
tpm_bios                7680  1 tpm
drm                   193280  1 i915
snd_pcm                92296  2 snd_hda_intel,snd_hda_codec
psmouse                57124  0 
serio_raw               6596  0 
i2c_algo_bit            7076  1 i915
snd_timer              26928  1 snd_pcm
snd                    76808  6 snd_hda_codec_analog,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_timer
intel_agp              32752  2 i915
soundcore               9088  1 snd
heci                   64580  0 
snd_page_alloc         10928  2 snd_hda_intel,snd_pcm
video                  23612  1 i915
lp                     11908  0 
output                  3680  1 video
parport                40528  1 lp
floppy                 65192  0 
e1000e                138640  0 

```


lspci:

```
00:00.0 Host bridge: Intel Corporation 4 Series Chipset DRAM Controller (rev 03)
00:02.0 VGA compatible controller: Intel Corporation 4 Series Chipset Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation 4 Series Chipset Integrated Graphics Controller (rev 03)
00:03.0 Communication controller: Intel Corporation 4 Series Chipset HECI Controller (rev 03)
00:03.2 IDE interface: Intel Corporation 4 Series Chipset PT IDER Controller (rev 03)
00:03.3 Serial controller: Intel Corporation 4 Series Chipset Serial KT Controller (rev 03)
00:19.0 Ethernet controller: Intel Corporation 82567LM-3 Gigabit Network Connection (rev 02)
00:1a.0 USB Controller: Intel Corporation 82801JD/DO (ICH10 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801JD/DO (ICH10 Family) USB UHCI Controller #5 (rev 02)
00:1a.2 USB Controller: Intel Corporation 82801JD/DO (ICH10 Family) USB UHCI Controller #6 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801JD/DO (ICH10 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801JD/DO (ICH10 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801JD/DO (ICH10 Family) PCI Express Port 1 (rev 02)
00:1c.4 PCI bridge: Intel Corporation 82801JD/DO (ICH10 Family) PCI Express Port 5 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801JD/DO (ICH10 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801JD/DO (ICH10 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801JD/DO (ICH10 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801JD/DO (ICH10 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev a2)
00:1f.0 ISA bridge: Intel Corporation 82801JDO (ICH10DO) LPC Interface Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801JD/DO (ICH10 Family) 4-port SATA IDE Controller (rev 02)
00:1f.5 IDE interface: Intel Corporation 82801JD/DO (ICH10 Family) 2-port SATA IDE Controller (rev 02)

```


sudo lshw -C Network:

```
  *-network               
       description: Ethernet interface
       product: 82567LM-3 Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth0
       version: 02
       serial: 00:24:81:11:16:32
       size: 100MB/s
       capacity: 1GB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=1.0.2-k2 duplex=full firmware=0.4-3 ip=192.168.1.12 latency=0 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: irq:30 memory:f0500000-f051ffff memory:f0525000-f0525fff ioport:1100(size=32)

```

---

### Post by Sporkman on 2010-01-16
Looks like it might have simply been the ethernet cable..? I swapped it out & have since been unable to reproduce the slowdown...

---

### Post by lev-unr on 2010-01-16
Glad it was a hardware issue. Easy fix! I had a similar problem with wifi speed when i upgraded to 9.10. 

It works fine for me now. 

Hope it was just the chord! I know how annoying it can be when your speed is not up to par.

---

