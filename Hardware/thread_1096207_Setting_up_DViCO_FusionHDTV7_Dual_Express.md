---
title: "Setting up DViCO FusionHDTV7 Dual Express"
date: 2009-03-14
forum: Hardware
---

### Post by daveisfera on 2009-03-14
I just installed Mythbuntu 8.10 for the first time and I'm not sure how to setup the DViCO FusionHDTV7 Dual Express. It appears to be supported ( http://www.linuxtv.org/wiki/index.php/DViCO_FusionHDTV7_Dual_Express ) and there is a success story out there ( http://www.mythtv.org/pipermail/mythtv-users/2008-August/229796.html ), but being new at this, I don't see it as an option in the Capture Card section of the setup in MythTV and I'm not sure what I need to do to get it to work.

Any help would be VERY appreciated.

Thanks,
Dave

---

### Post by daveisfera on 2009-03-20
I extracted the firmware and put it in the /lib/firmware directory. Here's the output from dmesg:

```
[   15.413305] cx23885 driver version 0.0.1 loaded
[   16.520245] cx23885 0000:03:00.0: PCI INT A -> Link[LN0A] -> GSI 19 (level, low) -> IRQ 19
[   16.520343] CORE cx23885[0]: subsystem: 18ac:d618, board: DViCO FusionHDTV7 Dual Express [card=10,autodetected]
[   16.659937] cx23885[0]: i2c bus 0 registered
[   16.659976] cx23885[0]: i2c bus 1 registered
[   16.660009] cx23885[0]: i2c bus 2 registered
[   16.687174] cx23885[0]: cx23885 based dvb card
[   17.298189] xc5000: Successfully identified at address 0x64
[   17.298192] xc5000: Firmware has not been loaded previously
[   17.298215] DVB: registering new adapter (cx23885[0])
[   17.298218] DVB: registering frontend 0 (Samsung S5H1411 QAM/8VSB Frontend)...
[   17.298648] cx23885[0]: cx23885 based dvb card
[   17.344886] xc5000: Successfully identified at address 0x64
[   17.344888] xc5000: Firmware has not been loaded previously
[   17.344891] DVB: registering new adapter (cx23885[0])
[   17.344894] DVB: registering frontend 1 (Samsung S5H1411 QAM/8VSB Frontend)...
[   17.345272] cx23885_dev_checkrevision() Hardware revision = 0xb0
[   17.345278] cx23885[0]/0: found at 0000:03:00.0, rev: 2, irq: 19, latency: 0, mmio: 0xfe800000
[   17.345284] cx23885 0000:03:00.0: setting latency timer to 64
```

I don't see any errors, so I assume that it's all setup correctly. What can I do to test that it's working correctly?

Thanks,
Dave

---

### Post by daveisfera on 2009-03-21
I added what I believe to be the card as a DVB Tuner card in MythTV setup, but it didn't tune any channels. Any suggestions on what I can check to see why it can't tune channels?

---

### Post by daveisfera on 2009-03-25
According to the advice from [this post](http://www.mythtvtalk.com/forum/hardware/11102-setting-up-dvico-fusionhdtv7-dual-express.html), I installed the dvb-utils package and ran the scan utility but it had the same problem (couldn't tune any channels). Here is the specific output:

```
scan /usr/share/doc/dvb-utils/examples/scan/atsc/us-ATSC-center-frequencies-8VSB 
scanning /usr/share/doc/dvb-utils/examples/scan/atsc/us-ATSC-center-frequencies-8VSB
using '/dev/dvb/adapter0/frontend0' and '/dev/dvb/adapter0/demux0'
>>> tune to: 57028615:8VSB
WARNING: >>> tuning failed!!!
>>> tune to: 57028615:8VSB (tuning failed)
...
```

If anyone has any suggestions, then I'm willing to give them a try, but it appears that this is the straw that broke the camel's back and I am forced to give up on MythTV/Linux and just switch to Windows.

---

### Post by daveisfera on 2009-03-27
Thanks to the help on [this post](http://www.mythtvtalk.com/forum/hardware/11102-setting-up-dvico-fusionhdtv7-dual-express.html), I have been able to get my DViCO FusionHDTV7 Dual Express to tune channels. I'm still working on getting MythTV to tune all the channels that I can get manually, but at least it's working.

---

