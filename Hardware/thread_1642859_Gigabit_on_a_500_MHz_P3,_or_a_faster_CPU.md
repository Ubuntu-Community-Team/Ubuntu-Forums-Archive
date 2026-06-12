---
title: "Gigabit on a 500 MHz P3, or a faster CPU?"
date: 2010-12-10
forum: Hardware
---

### Post by WA1DH on 2010-12-10
I'm currently running a 500 MHz Pentium 3 file server with ~400MB RAM. It runs Xubuntu and stays in command-line/terminal mode (~0 load at idle). It is used for nothing more than a file server. It currently has a 10/100 ethernet adapter and can serve files at about 10.5 MB/sec over NFS. While transferring a file, the CPU usage is about 90%. At idle, CPU usage is between 0-1% (minimal processes running).

I would like to upgrade to a gigabit ethernet adapter. Specifically, I am considering the Intel PRO-1000 for 32-bit PCI. I'm not exactly sure how the processing power for serving gigabit differs from 10/100. Is the processing done by the adapter itself, and I can expect a faster data transfer with the same CPU usage, or am I going to max the CPU out and have minimal increase in transfer speed?

If I'm overtaxing this system for gigabit, I have a 2 GHz AMD Athlon 3200+ chip and a socket 939 board laying around I could use. I was just thinking that would be overkill for a command-line only file server.

Thoughts?

---

### Post by Sam Lars on 2010-12-11
If you're putting a Gigabit card in the server, you'll also need a router that is capable of Gigabit speeds. And unless you tend to serve to multiple machines at the same time, the machine on the other end will also need a Gigabit card. It also favors higher-quality wiring (Cat-5e or Cat-6).
Also, with IDE disks you're not going to be able to get a whole lot out of Gigabit ethernet. The newer system would probably transfer data faster. SATA drives would be your best bet for throughput.

Found this here:
[http://www.dssnetworks.com/v3/FAQs.asp#CPUREQ](http://www.dssnetworks.com/v3/FAQs.asp#CPUREQ)
> The basic rule or formula in the industry applicable to TCP/IP protocol is 1 MHZ of CPU for each megabit of data and allowing for application processing. This equates to a 1-GHZ CPU for a wire speed transfer in one direction or a 2-GHZ CPU for a bi-directional transfer in full-duplex mode when using the TCP/IP protocol stack. Using other protocols including UDP/IP or direct-IP can provide better performance with lower CPU utilization.

---

### Post by WA1DH on 2010-12-12
Good info, that's exactly what I was looking for. I am actually running a SATA drive (Caviar Green 1TB) with a SATA PCI adapter. The drive benchmarks with a read speed around 80 MB/sec but is bottlenecked at ~10MB/sec by the current LAN. I'll go ahead with upgrading to a new system for gigabit.

---

### Post by Fafler on 2010-12-12
For what it's worth, i was able to get around 30-40 mbyte/s on my old fileserver (dual 550 mhz P3 and 4 bundled 100 mbit interfaces). Good network cards make a difference and the Intel Pro 1000 is one of the better.

---

### Post by WA1DH on 2010-12-12
Are PCI express gigabit cards worthwhile or should I just stick to the PRO-1000 PCI? PCI bus is maxed at 133 MB/sec and gigabit tops 125 MB/sec. My HDD benchmarks at 80 MB/sec read. My board has PCI X1 slots and PCI.

Am I missing something or is it pointless to bother buying a PCI express card for it?

---

### Post by pezed on 2010-12-12
you won't notice a great increase with gigabit in that machine.  I have a p3 800mhz with 1gb ram that i use for a backup storage device with 2x1tb drives.  it maxes at around 30meg/sec.  The old p3's busses just lack the bandwidth.  Best bet would be spend about $100 on a low end modern board/cpu.  Even the intel atom stuff will be much quicker than the p3.

---

### Post by WA1DH on 2010-12-12
> **pezed said:**
> you won't notice a great increase with gigabit in that machine.  I have a p3 800mhz with 1gb ram that i use for a backup storage device with 2x1tb drives.  it maxes at around 30meg/sec.  The old p3's busses just lack the bandwidth.  Best bet would be spend about $100 on a low end modern board/cpu.  Even the intel atom stuff will be much quicker than the p3.

Sorry, let me clarify. This is my current plan:

The P3 500 MHz system is going to be replaced by an AMD Athlon 4000+ (2.4 GHz) with a Mach Speed MSNV-939 board. The board has both PCI and PCI express X1 slots. Is there any advantage to going with a PCI express gigabit card on -this- system versus using a cheaper PCI card? The PCI express Intel adapters appear to run 3x more in cost over the PCI ones. The PCI Intel PRO-1000 is about $10.

I have the entire system ready to go - it was an old board and chip I had sitting unused in my garage. I only need to buy the gigabit adapter.

---

### Post by Fafler on 2010-12-13
In that case i'd go PCIe, as each PCIe slot has a separate connection to the chipset, where PCI share one connection across all slots.

But if the NIC is the only device on the PCI bus and have all the 133 mb/s for it self, it should be able to reach the 80 mb/s your drive can deliver.

---

