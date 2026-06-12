---
title: "Kworld Video Magician TV Tuner card"
date: 2008-10-31
forum: Hardware
---

### Post by Fir3chi3f on 2008-10-31
I cant seem to get this capture card working right.

Tvtime gives the error:
```

videoinput: Cannot open capture device /dev/video0: No such file or directory
```

It looks like at least one person got it working here

Here is what I got so far:

for "dmesg":

```
[   54.513292] Linux video capture interface: v2.00
[   54.584260] Linux agpgart interface v0.102
[   54.756658] cx8800: Unknown parameter `card'
```

and for "lspci | grep -i cx | more":
Code:
```

02:08.0 Multimedia video controller: Conexant CX23880/1/2/3 PCI Video and Audio 
Decoder (rev 05)
```

for "lsmod | grep "cx""

```
cx88xx                 65960  0 
ir_common              36100  1 cx88xx
i2c_algo_bit            7300  1 cx88xx
tveeprom               16656  1 cx88xx
videodev               29440  2 sn9c102,cx88xx
v4l2_common            18304  3 sn9c102,cx88xx,videodev
videobuf_dma_sg        14980  1 cx88xx
videobuf_core          18820  2 cx88xx,videobuf_dma_sg
btcx_risc               5896  1 cx88xx
i2c_core               24832  5 nvidia,cx88xx,i2c_algo_bit,tveeprom,i2c_nforce2
```

I have not been able to try 64bit ubuntu yet, but unless Im mistaken this should work regardless.
As always, any help, suggestions or questions are greatly appreciated

---

### Post by Fir3chi3f on 2008-11-01
Desperate bump

---

