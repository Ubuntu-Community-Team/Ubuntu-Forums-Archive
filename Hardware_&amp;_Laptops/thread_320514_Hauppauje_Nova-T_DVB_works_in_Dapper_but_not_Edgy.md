---
title: "Hauppauje Nova-T DVB works in Dapper but not Edgy"
date: 2006-12-17
forum: Hardware &amp; Laptops
---

### Post by mikeje99 on 2006-12-17
Help

I've change to Edgy and now my Nova-T DVB doesn't work. 

I've read this is a bug in Edgy. Does anyone now how to it working?

Mike

---

### Post by nmsmith on 2007-01-31
This appears to be the only post that describes the symptoms I'm getting, and yet there are no replies! Where did you hear about this supposed bug, and have you found any solutions?

I am trying to get a Hauppauge DVB-T card (connexant cx23880 chip) working in Edgy on a Pentium III 500 MHz with 384 Mb RAM. I recall Knoppmyth working (i..e. displaying live TV but not having the horsepower to encode) on this machine a few months ago when it only had 128 Mb of RAM, but Dapper (I guess Gnome in particular) was too slow. So now I've stuck some more memory in and Edgy boots and looks fine. Except I get the following when I try the scan utility:

```
root@praxidike:~# scan /usr/share/doc/dvb-utils/examples/scan/dvb-t/uk-Oxford > /root/.tzap/channels.conf
scanning /usr/share/doc/dvb-utils/examples/scan/dvb-t/uk-Oxford
using '/dev/dvb/adapter0/frontend0' and '/dev/dvb/adapter0/demux0'
initial transponder 578000000 0 2 9 3 0 0 0
>>> tune to: 578000000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_2_3:FEC_AUTO:QAM_64:TRANSMISSION_MODE_2K:GUARD_INTERVAL_1_32:HIERARCHY_NONE
WARNING: >>> tuning failed!!!
>>> tune to: 578000000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_2_3:FEC_AUTO:QAM_64:TRANSMISSION_MODE_2K:GUARD_INTERVAL_1_32:HIERARCHY_NONE (tuning failed)
WARNING: >>> tuning failed!!!
ERROR: initial tuning failed
dumping lists (0 services)
Done.
```

dmesg and lspci produce (what I would consider to be) the expected  outputs:

```
root@praxidike:~# dmesg | grep cx2388
[   78.818390] cx2388x v4l2 driver version 0.0.5 loaded
[   78.920329] cx2388x dvb driver version 0.0.5 loaded
[   79.039813] cx88[0]/2: cx2388x based dvb card
[   79.097725] cx2388x blackbird driver version 0.0.5 loaded
```

```
root@praxidike:~# lspci
00:00.0 Host bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (rev 03)
00:01.0 PCI bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge (rev 03)
00:07.0 ISA bridge: Intel Corporation 82371AB/EB/MB PIIX4 ISA (rev 02)
00:07.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01)
00:07.2 USB Controller: Intel Corporation 82371AB/EB/MB PIIX4 USB (rev 01)
00:07.3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 02)
00:10.0 Multimedia video controller: Conexant CX23880/1/2/3 PCI Video and Audio Decoder (rev 05)
00:10.2 Multimedia controller: Conexant CX23880/1/2/3 PCI Video and Audio Decoder [MPEG Port] (rev 05)
00:10.4 Multimedia controller: Conexant CX23880/1/2/3 PCI Video and Audio Decoder [IR Port] (rev 05)
00:12.0 Ethernet controller: NetVin NV5000SC
00:14.0 Multimedia audio controller: Ensoniq ES1371 [AudioPCI-97] (rev 06)
01:00.0 VGA compatible controller: nVidia Corporation NV5M64 [RIVA TNT2 Model 64/Model 64 Pro] (rev 11)
```



I get plenty signal strength to run a cheapo set-top box, and I've tried other transmitters than uk-Oxford (though 23km to the Stanton St. John transmitter sounds like the most likely location) , so I'm guessing this is a driver or kernel issue. Can anyone help?

---

### Post by nmsmith on 2007-02-01
bump

---

### Post by patrickfromspain on 2007-02-01
I also have a hauppage nova-t.. I think in edgy, it worked for me. Anyway, you could try: sudo modprobe cx88-dvb That's the problem I had in feisty.

If it doesn't work, you could try compiling the following:

go here [http://linuxtv.org/hg/v4l-dvb?ca=df3605a24a04;type=gz](http://linuxtv.org/hg/v4l-dvb?ca=df3605a24a04;type=gz)

Download and unpakage the file. cd to the folder, then make, sudo make install and reboot. Try if it works. To uninstall: sudo apt-get install --reinstall kernel-you're-runningç

Hope it helps!

---

### Post by nmsmith on 2007-02-01
Thanks patrickfromspain for your advice. After tinkering more this evening I think I might have to back down from my position and humbly apologise.

I reinstalled Dapper to check whether it would tune there, and had similar issues. So instead of tuning to the uk-Oxford config file settings I tried all of the channels in order. Eventually I got a signal from the uk-Craigkelly settings. Now I'm fairly certain that Craigkelly is not actually sending me the signal, but its config file seemed to work. I can just about tzap to a couple of crappy quality streams.

So the problem seems to be signal-strength and in-PC-radio-noise related, probably coupled with the difficulties that the Pentium III has in loading things like mplayer.

Perhaps my aerial is at fault.

Sorry!

---

