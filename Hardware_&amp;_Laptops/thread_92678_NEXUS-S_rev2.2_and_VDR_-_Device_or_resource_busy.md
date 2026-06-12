---
title: "NEXUS-S rev2.2 and VDR - Device or resource busy"
date: 2005-11-20
forum: Hardware &amp; Laptops
---

### Post by art2003 on 2005-11-20
I have a nexus-s DVB rev2.2 sat card
works fine under windows so I know the hardware is fine.
This card is similar to the Skystar1

I compile vdr without problems
run it
then run tvtime
and no signal. Doesn't allow me to select a different video source.

tvtime shows:
videoinput: Cannot open capture device /dev/dvb/adapter0/frontend0: Device or resource busy
Thank you for using tvtime.

lsof /dev/dvb/adapter0/frontend0
shows that only the vdr process is using frontend0

dmesg shows:
[4294702.521000] saa7146: register extension 'dvb'.
[4294702.526000] ACPI: PCI Interrupt 0000:00:0a.0[A] -> GSI 18 (level, low) -> IRQ 18
[4294702.527000] saa7146: found saa7146 @ mem e0b7ee00 (revision 1, irq 18) (0x13c2,0x0003).
[4294703.038000] DVB: registering new adapter (Technotrend/Hauppauge WinTV Nexus-S rev2.X).
[4294703.061000] adapter has MAC addr = 00:d0:5c:23:85:86
[4294703.264000] dvb-ttpci: gpioirq unknown type=0 len=0
[4294703.271000] dvb-ttpci: info @ card 0: firm f0240009, rtsl b0250018, vid 71010068, app 8000261f
[4294703.271000] dvb-ttpci: firmware @ card 0 supports CI link layer interface
[4294703.275000] dvb-ttpci: Crystal audio DAC @ card 0 detected
[4294703.286000] saa7146_vv: saa7146 (0): registered device video0 [v4l2]
[4294703.651000] DVB: registering frontend 0 (ST STV0299 DVB-S)...
[4294703.655000] dvb-ttpci: found av7110-0.

lspci shows:

 lspci
0000:00:00.0 Host bridge: Silicon Integrated Systems [SiS] 741/741GX/M741 Host (rev 03)
0000:00:01.0 PCI bridge: Silicon Integrated Systems [SiS]: Unknown device 0003
0000:00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS963 [MuTIOL Media IO] (rev 25)
0000:00:02.1 SMBus: Silicon Integrated Systems [SiS]: Unknown device 0016
0000:00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE]
0000:00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] Sound Controller (rev a0)
0000:00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
0000:00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
0000:00:03.2 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller0000:00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 90)
0000:00:0a.0 Multimedia controller: Philips Semiconductors SAA7146 (rev 01)
0000:01:00.0 VGA compatible controller: nVidia Corporation NV17 [GeForce4 MX 440] (rev a3)


 lsmod | grep dvb shows:

dvb_ttpci              97384  6
l64781                  7556  1 dvb_ttpci
saa7146_vv             49856  1 dvb_ttpci
saa7146                18056  2 dvb_ttpci,saa7146_vv
ves1820                 6020  1 dvb_ttpci
stv0299                11656  1 dvb_ttpci
tda8083                 6468  1 dvb_ttpci
stv0297                 9408  1 dvb_ttpci
sp8870                  7756  1 dvb_ttpci
ves1x93                 6980  1 dvb_ttpci
ttpci_eeprom            2624  1 dvb_ttpci
dvb_bt8xx              12676  0
nxt6000                 7876  1 dvb_bt8xx
mt352                   6788  1 dvb_bt8xx
sp887x                  8324  1 dvb_bt8xx
dst_ca                 16576  1 dvb_bt8xx
dst                    19588  2 dvb_bt8xx,dst_ca
bt878                  10296  2 dvb_bt8xx,dst
dvb_core               82088  3 dvb_ttpci,dvb_bt8xx,dst_ca
cx24110                 8516  1 dvb_bt8xx
or51211                 9796  1 dvb_bt8xx
bttv                  154384  2 dvb_bt8xx,bt878
firmware_class         10240  6 dvb_ttpci,sp8870,dvb_bt8xx,sp887x,or51211,bttv
i2c_core               21328  21 i2c_acpi_ec,dvb_ttpci,l64781,ves1820,stv0299,tda8083,stv0297,sp8870,ves1x93,ttpci_eeprom,i2c_sis96x,dvb_bt8xx,nxt6000,mt352,sp887x,dst,cx24110,or51211,bttv,i2c_algo_bit,tveeprom

---

