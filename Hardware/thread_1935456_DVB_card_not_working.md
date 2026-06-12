---
title: "DVB card not working"
date: 2012-03-04
forum: Hardware
---

### Post by earthwormgym on 2012-03-04
Hi,

I'm having trouble getting my DVB card to work on Ubuntu 11.10

Details of the card from an lspci -v are...
```
07:01.0 Multimedia controller: Philips Semiconductors SAA7146 (rev 01)
	Subsystem: Technotrend Systemtechnik GmbH DVB T-1500
	Flags: bus master, medium devsel, latency 64, IRQ 17
	Memory at fbeffc00 (32-bit, non-prefetchable) [size=512]
	Kernel driver in use: budget_ci dvb
	Kernel modules: budget-ci

```

The issue is that a frontend does not get created as you can see from
```
ls -l /dev/dvb/adapter0/
total 0
crw-rw----+ 1 root video 212, 0 2012-03-04 15:51 demux0
crw-rw----+ 1 root video 212, 1 2012-03-04 15:51 dvr0
crw-rw----+ 1 root video 212, 2 2012-03-04 15:51 net0

```

I have the following in dmesg
```
[   15.048902] saa7146: register extension 'budget_ci dvb'.
[   15.048922] budget_ci dvb 0000:07:01.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   15.048952] saa7146: found saa7146 @ mem ffffc90000c7ec00 (revision 1, irq 17) (0x13c2,0x1012).
[   15.048955] saa7146 (0): dma buffer size 192512
[   15.048956] DVB: registering new adapter (TT-Budget-T-CI PCI)
...
[   15.144837] Registered IR keymap rc-hauppauge
[   15.144961] input: Budget-CI dvb ir receiver saa7146 (0) as /devices/pci0000:00/0000:00:1e.0/0000:07:01.0/rc/rc0/input5
[   15.145000] rc0: Budget-CI dvb ir receiver saa7146 (0) as /devices/pci0000:00/0000:00:1e.0/0000:07:01.0/rc/rc0
[   15.175758] tda10046: chip is not answering. Giving up.
[   15.175763] budget-ci: A frontend driver was not found for device [1131:7146] subsystem [13c2:1012]

```

So this issue seems to be around the line
```
tda10046: chip is not answering. Giving up
```

I have searched around for a solution to this without much luck. I did find this post which may have something to do with it but I'm not sure how to confirm it.
[http://permalink.gmane.org/gmane.linux.drivers.dvb/42284]("http://permalink.gmane.org/gmane.linux.drivers.dvb/42284")

Any help is very much appreciated as I'm completely stuck now.

Thanks!

---

### Post by earthwormgym on 2012-03-10
I'm not sure what was going on but I seem to have it working now and the only thing I had to do above a vanilla install was to install linux-firmware-nonfree

---

