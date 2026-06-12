---
title: "Ipod breaking USB connectivity on Kensington hub"
date: 2008-08-20
forum: Hardware
---

### Post by LucheLibre on 2008-08-20
I'm running Hardy on a Toshiba A215-S4747.

I have a 3g Ipod Nano. It will (finally, after much fiddling) connect to the laptop's usb port without problem.

However, I have a 7-port Kensington hub with a External Raptor HDD and a cruzer thumb connected to it. By themselves, they are fine and are recognized properly. However, as soon as I connect the Ipod to it (which is preferable to me), the Ipod's screen goes dark and the two components already connected to the hub lose connectivity and the thumb also loses power.

Even after disconnecting the iPod, no amount of current internet suggestions or plug/unplug combinations can get Ubuntu to use the hub. A reboot is required, and sometimes two.

Here is the dmesg after plugging in the Ipod.

```

 hub 6-1.4:1.0: hub_port_status failed (err = -110)
[ 4355.484731] hub 6-1.4:1.0: cannot reset port 1 (err = -110)
[ 4355.934261] hub 6-1.4:1.0: cannot reset port 1 (err = -110)
[ 4356.383791] hub 6-1.4:1.0: cannot reset port 1 (err = -110)
[ 4356.833321] hub 6-1.4:1.0: cannot reset port 1 (err = -110)
[ 4356.833328] hub 6-1.4:1.0: Cannot enable port 1.  Maybe the USB cable is bad?
[ 4357.282849] hub 6-1.4:1.0: cannot disable port 1 (err = -110)
[ 4357.732379] hub 6-1.4:1.0: cannot reset port 1 (err = -110)
[ 4358.181909] hub 6-1.4:1.0: cannot reset port 1 (err = -110)
[ 4358.631441] hub 6-1.4:1.0: cannot reset port 1 (err = -110)
[ 4359.080969] hub 6-1.4:1.0: cannot reset port 1 (err = -110)
[ 4359.530499] hub 6-1.4:1.0: cannot reset port 1 (err = -110)
[ 4359.530507] hub 6-1.4:1.0: Cannot enable port 1.  Maybe the USB cable is bad?
[ 4359.980029] hub 6-1.4:1.0: cannot disable port 1 (err = -110)
[ 4360.429557] hub 6-1.4:1.0: cannot reset port 1 (err = -110)
[ 4360.879089] hub 6-1.4:1.0: cannot reset port 1 (err = -110)
[ 4361.328620] hub 6-1.4:1.0: cannot reset port 1 (err = -110)
[ 4361.787308] hub 6-1.4:1.0: cannot reset port 1 (err = -110)
[ 4362.236330] hub 6-1.4:1.0: cannot reset port 1 (err = -110)
[ 4362.236336] hub 6-1.4:1.0: Cannot enable port 1.  Maybe the USB cable is bad?
[ 4362.685860] hub 6-1.4:1.0: cannot disable port 1 (err = -110)
[ 4363.135389] hub 6-1.4:1.0: cannot reset port 1 (err = -110)
[ 4363.584929] hub 6-1.4:1.0: cannot reset port 1 (err = -110)
[ 4364.034454] hub 6-1.4:1.0: cannot reset port 1 (err = -110)
[ 4364.672018] hub 6-1.4:1.0: cannot reset port 1 (err = -110)
[ 4365.288135] hub 6-1.4:1.0: cannot reset port 1 (err = -110)
[ 4365.288142] hub 6-1.4:1.0: Cannot enable port 1.  Maybe the USB cable is bad?
[ 4365.737663] hub 6-1.4:1.0: cannot disable port 1 (err = -110)
[ 4366.187254] hub 6-1.4:1.0: cannot disable port 1 (err = -110)
[ 4368.118055] hub 6-1:1.0: cannot reset port 2 (err = -110)
[ 4368.567589] hub 6-1:1.0: cannot reset port 2 (err = -110)
[ 4368.790975] hub 6-1.4:1.0: hub_port_status failed (err = -110)
[ 4369.017126] hub 6-1:1.0: cannot reset port 2 (err = -110)
[ 4369.466647] hub 6-1:1.0: cannot reset port 2 (err = -110)
[ 4369.916179] hub 6-1:1.0: cannot reset port 2 (err = -110)
[ 4369.916187] hub 6-1:1.0: Cannot enable port 2.  Maybe the USB cable is bad?
[ 4370.365711] hub 6-1:1.0: cannot disable port 2 (err = -110)
[ 4370.815238] hub 6-1:1.0: cannot reset port 2 (err = -110)
[ 4371.037107] hub 6-1.4:1.0: hub_port_status failed (err = -110)
[ 4371.264766] hub 6-1:1.0: cannot reset port 2 (err = -110)
[ 4371.714298] hub 6-1:1.0: cannot reset port 2 (err = -110)
[ 4372.163825] hub 6-1:1.0: cannot reset port 2 (err = -110)
[ 4372.613353] hub 6-1:1.0: cannot reset port 2 (err = -110)
[ 4372.613360] hub 6-1:1.0: Cannot enable port 2.  Maybe the USB cable is bad?
[ 4373.062885] hub 6-1:1.0: cannot disable port 2 (err = -110)
[ 4373.284760] hub 6-1.4:1.0: hub_port_status failed (err = -110)
[ 4373.800389] hub 6-1:1.0: cannot reset port 2 (err = -110)
[ 4374.316563] hub 6-1:1.0: cannot reset port 2 (err = -110)
[ 4374.766113] hub 6-1:1.0: cannot reset port 2 (err = -110)
[ 4375.222615] hub 6-1:1.0: cannot reset port 2 (err = -110)
[ 4375.672036] hub 6-1:1.0: cannot reset port 2 (err = -110)
[ 4375.672043] hub 6-1:1.0: Cannot enable port 2.  Maybe the USB cable is bad?
[ 4375.887037] hub 6-1.4:1.0: hub_port_status failed (err = -110)
[ 4376.121570] hub 6-1:1.0: cannot disable port 2 (err = -110)
[ 4376.571097] hub 6-1:1.0: cannot reset port 2 (err = -110)
[ 4377.020628] hub 6-1:1.0: cannot reset port 2 (err = -110)
[ 4377.470162] hub 6-1:1.0: cannot reset port 2 (err = -110)
[ 4377.919687] hub 6-1:1.0: cannot reset port 2 (err = -110)
[ 4378.369219] hub 6-1:1.0: cannot reset port 2 (err = -110)
[ 4378.369226] hub 6-1:1.0: Cannot enable port 2.  Maybe the USB cable is bad?
[ 4378.818758] hub 6-1:1.0: cannot disable port 2 (err = -110)
[ 4379.268279] hub 6-1:1.0: cannot reset port 3 (err = -110)
[ 4379.268293] hub 6-1:1.0: cannot disable port 2 (err = -110)
[ 4379.263412] sd 6:0:0:0: Device offlined - not ready after error recovery
[ 4379.717815] hub 6-1:1.0: cannot reset port 3 (err = -110)
[ 4380.167345] hub 6-1:1.0: cannot reset port 3 (err = -110)
[ 4380.616874] hub 6-1:1.0: cannot reset port 3 (err = -110)
[ 4381.066404] hub 6-1:1.0: cannot reset port 3 (err = -110)
[ 4381.066411] hub 6-1:1.0: Cannot enable port 3.  Maybe the USB cable is bad?
[ 4381.515930] hub 6-1:1.0: cannot disable port 3 (err = -110)
[ 4381.516160] hub 6-1:1.0: hub_port_status failed (err = -110)
[ 4381.965457] hub 6-1:1.0: cannot reset port 3 (err = -110)
[ 4382.414989] hub 6-1:1.0: cannot reset port 3 (err = -110)
[ 4382.864520] hub 6-1:1.0: cannot reset port 3 (err = -110)
[ 4383.314048] hub 6-1:1.0: cannot reset port 3 (err = -110)
[ 4383.763577] hub 6-1:1.0: cannot reset port 3 (err = -110)
[ 4383.763584] hub 6-1:1.0: Cannot enable port 3.  Maybe the USB cable is bad?
[ 4384.213111] hub 6-1:1.0: cannot disable port 3 (err = -110)
[ 4384.232648] hub 6-1.4:1.0: hub_port_status failed (err = -110)
[ 4384.662641] hub 6-1:1.0: cannot reset port 3 (err = -110)
[ 4385.112168] hub 6-1:1.0: cannot reset port 3 (err = -110)
[ 4385.561702] hub 6-1:1.0: cannot reset port 3 (err = -110)
[ 4386.011228] hub 6-1:1.0: cannot reset port 3 (err = -110)
[ 4386.493307] hub 6-1:1.0: cannot reset port 3 (err = -110)
[ 4386.493314] hub 6-1:1.0: Cannot enable port 3.  Maybe the USB cable is bad?
[ 4386.537280] hub 6-1.4:1.0: hub_port_status failed (err = -110)
[ 4387.264889] hub 6-1:1.0: cannot disable port 3 (err = -110)
[ 4387.714464] hub 6-1:1.0: cannot reset port 3 (err = -110)
[ 4388.163953] hub 6-1:1.0: cannot reset port 3 (err = -110)
[ 4388.615278] hub 6-1:1.0: cannot reset port 3 (err = -110)
[ 4389.066240] hub 6-1:1.0: cannot reset port 3 (err = -110)
[ 4389.106214] hub 6-1.4:1.0: hub_port_status failed (err = -110)
[ 4390.077673] hub 6-1:1.0: cannot reset port 3 (err = -110)
[ 4390.077680] hub 6-1:1.0: Cannot enable port 3.  Maybe the USB cable is bad?
[ 4390.673805] hub 6-1:1.0: cannot disable port 3 (err = -110)
[ 4391.123334] hub 6-1:1.0: cannot disable port 3 (err = -110)
[ 4391.123517] sd 7:0:0:0: Device offlined - not ready after error recovery
[ 4391.123532] sd 7:0:0:0: [sdb] Result: hostbyte=DID_ABORT driverbyte=DRIVER_OK,SUGGEST_OK
[ 4391.123536] end_request: I/O error, dev sdb, sector 12746855
[ 4391.123541] Buffer I/O error on device sdb1, logical block 1593349
[ 4391.123547] Buffer I/O error on device sdb1, logical block 1593350
[ 4391.123551] Buffer I/O error on device sdb1, logical block 1593351
[ 4391.123555] Buffer I/O error on device sdb1, logical block 1593352
[ 4391.123558] Buffer I/O error on device sdb1, logical block 1593353
[ 4391.123562] Buffer I/O error on device sdb1, logical block 1593354
[ 4391.123565] Buffer I/O error on device sdb1, logical block 1593355
[ 4391.123569] Buffer I/O error on device sdb1, logical block 1593356
[ 4391.123573] Buffer I/O error on device sdb1, logical block 1593357
[ 4391.123576] Buffer I/O error on device sdb1, logical block 1593358
[ 4391.123606] sd 7:0:0:0: rejecting I/O to offline device
[ 4391.123629] sd 7:0:0:0: rejecting I/O to offline device
[ 4391.123637] sd 7:0:0:0: [sdb] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
[ 4391.123641] end_request: I/O error, dev sdb, sector 12747095
[ 4391.137779] sd 7:0:0:0: rejecting I/O to offline device

[ 4391.137892] sd 7:0:0:0: rejecting I/O to offline device
[ 4391.138165] sd 7:0:0:0: rejecting I/O to offline device
[ 4392.040163] hub 6-1.4:1.0: hub_port_status failed (err = -110)
[ 4394.287793] hub 6-1:1.0: hub_port_status failed (err = -110)
[ 4397.529682] hub 6-1:1.0: hub_port_status failed (err = -110)
[ 4402.458832] hub 6-1.4:1.0: hub_port_status failed (err = -110)

```

---

### Post by warmrobot on 2008-08-22
I can confirm this problem. I have a USB hub in Dell 2007 WFP. I can detect iPOd in two cases:

1) when it was connected at the PC sturtup
2) when I connect it directly to PC, not to hub

---

