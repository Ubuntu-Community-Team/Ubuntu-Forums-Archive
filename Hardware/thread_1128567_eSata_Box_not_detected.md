---
title: "eSata Box not detected"
date: 2009-04-17
forum: Hardware
---

### Post by StanleyKowalsky on 2009-04-17
Hello there

I have a Sata-Box with 4x2.5 drives in there (box: [http://www.raidsonic.de/de/pages/products/external_cases.php?we_objectID=5240]("http://www.raidsonic.de/de/pages/products/external_cases.php?we_objectID=5240"))

When I try to connect the Box via eSata to the PC (latest ubuntu - 2.6.28.11-generic) the 4 disks won't get detected:

dmesg delivers:

```
[ 3702.470499] ata6.15: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[ 3702.792054] ata6.00: hard resetting link
[ 3703.111520] ata6.00: SATA link down (SStatus 0 SControl 310)
[ 3703.111523] ata6.02: hard resetting link
[ 3706.428879] ata6.15: qc timeout (cmd 0xe8)
[ 3706.428891] ata6.02: failed to write SCR 1 (Emask=0x4)
[ 3706.428893] ata6.02: failed to read SCR 0 (Emask=0x40)
[ 3706.428895] ata6.03: hard resetting link
[ 3706.428897] ata6.03: failed to read SCR 2 (Emask=0x40)
[ 3706.428898] ata6.03: failed to read SCR 2 (Emask=0x40)
[ 3706.428900] ata6.03: COMRESET failed (errno=-5)
[ 3706.428902] ata6.03: failed to read SCR 0 (Emask=0x40)
[ 3706.428904] ata6.03: reset failed, giving up
[ 3706.428906] ata6.15: hard resetting link
[ 3711.956010] ata6.15: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[ 3712.276037] ata6.01: failed to read SCR 0 (Emask=0x40)
[ 3712.276039] ata6.01: failed to write SCR 1 (Emask=0x40)
[ 3712.276041] ata6.01: failed to clear SError.N (errno=-5)
[ 3712.276043] ata6.15: hard resetting link
[ 3717.797066] ata6.15: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[ 3718.120042] ata6.01: failed to read SCR 0 (Emask=0x100)
[ 3718.120044] ata6.01: failed to write SCR 1 (Emask=0x40)
[ 3718.120046] ata6.01: failed to clear SError.N (errno=-5)
[ 3718.120048] ata6.15: hard resetting link
[ 3723.644027] ata6.15: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[ 3723.961875] ata6.01: failed to read SCR 0 (Emask=0x40)
[ 3723.961877] ata6.01: failed to write SCR 1 (Emask=0x40)
[ 3723.961878] ata6.01: failed to clear SError.N (errno=-5)
[ 3723.961881] ata6.15: hard resetting link
[ 3729.488010] ata6.15: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[ 3729.808041] ata6.01: failed to read SCR 0 (Emask=0x100)
[ 3729.808043] ata6.01: failed to write SCR 1 (Emask=0x40)
[ 3729.808045] ata6.01: failed to clear SError.N (errno=-5)
[ 3729.808047] ata6: failed to recover PMP after 5 tries, giving up
[ 3729.808048] ata6.15: Port Multiplier detaching
[ 3729.808071] ata6.00: disabled
[ 3729.808075] ata6: exception Emask 0x42 SAct 0x0 SErr 0x80800 action 0x6 frozen t4
[ 3729.808076] ata6: irq_stat 0x00800000, incorrect PMP
[ 3729.808078] ata6: SError: { HostInt 10B8B }
[ 3729.808081] ata6: hard resetting link
[ 3735.328594] ata6: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[ 3735.328599] ata6: EH complete
[ 3861.630698] ata6: exception Emask 0x50 SAct 0x0 SErr 0x4090800 action 0xe frozen
[ 3861.630701] ata6: irq_stat 0x00400040, connection status changed
[ 3861.630703] ata6: SError: { HostInt PHYRdyChg 10B8B DevExch }
[ 3861.630708] ata6: hard resetting link
[ 3862.356011] ata6: SATA link down (SStatus 0 SControl 300)
[ 3862.356015] ata6: EH complete
[ 3910.243485] ata6: exception Emask 0x10 SAct 0x0 SErr 0x4050002 action 0xe frozen
[ 3910.243490] ata6: irq_stat 0x00000040, connection status changed
[ 3910.243492] ata6: SError: { RecovComm PHYRdyChg CommWake DevExch }
[ 3910.243499] ata6: hard resetting link
[ 3911.130557] ata6: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[ 3911.130632] ata6.15: Port Multiplier 1.1, 0x1095:0x3726 r23, 6 ports, feat 0x1/0x9
[ 3911.130755] ata6.01: hard resetting link
[ 3911.448977] ata6.01: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[ 3911.448979] ata6.02: hard resetting link
[ 3911.771591] ata6.02: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[ 3911.771594] ata6.03: hard resetting link
[ 3912.092107] ata6.03: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[ 3912.092110] ata6.04: hard resetting link
[ 3912.412214] ata6.04: SATA link down (SStatus 0 SControl 320)
[ 3912.412217] ata6.05: hard resetting link
[ 3912.732104] ata6.05: SATA link up 1.5 Gbps (SStatus 113 SControl 320)
[ 3912.732126] ata6.01: failed to IDENTIFY (I/O error, err_mask=0x100)
[ 3912.732128] ata6.15: hard resetting link
[ 3913.440009] ata6.15: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[ 3913.440084] ata6.00: hard resetting link
[ 3913.757244] ata6.00: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[ 3916.448556] ata6.01: hard resetting link
[ 3919.772006] ata6.15: qc timeout (cmd 0xe4)
[ 3919.772012] ata6.01: failed to read SCR 0 (Emask=0x4)
[ 3919.772014] ata6.01: COMRESET failed (errno=-5)
[ 3919.772016] ata6.01: failed to read SCR 0 (Emask=0x40)
[ 3919.772018] ata6.01: reset failed, giving up
[ 3919.772021] ata6.15: hard resetting link
[ 3920.477838] ata6.15: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[ 3920.477928] ata6.00: hard resetting link
[ 3920.798809] ata6.00: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[ 3921.452005] ata6.01: hard resetting link
[ 3921.772106] ata6.01: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[ 3921.772109] ata6.02: hard resetting link
[ 3922.092102] ata6.02: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[ 3922.092104] ata6.03: hard resetting link
[ 3925.099183] ata6.15: qc timeout (cmd 0xe8)
[ 3925.099189] ata6.03: failed to write SCR 2 (Emask=0x4)
[ 3925.099191] ata6.03: COMRESET failed (errno=-5)
[ 3925.099193] ata6.03: failed to read SCR 0 (Emask=0x40)
[ 3925.099194] ata6.03: reset failed, giving up
[ 3925.099197] ata6.15: hard resetting link
[ 3925.808009] ata6.15: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[ 3925.808083] ata6.00: hard resetting link
[ 3928.816009] ata6.15: qc timeout (cmd 0xe4)
[ 3928.816015] ata6.00: failed to read SCR 2 (Emask=0x4)
[ 3928.816017] ata6.00: COMRESET failed (errno=-5)
[ 3928.816019] ata6.00: failed to read SCR 0 (Emask=0x40)
[ 3928.816020] ata6.00: reset failed, giving up
[ 3928.816023] ata6.15: hard resetting link
[ 3929.524009] ata6.15: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[ 3930.808005] ata6.00: hard resetting link
[ 3931.125747] ata6.00: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[ 3931.125750] ata6.01: hard resetting link
[ 3931.448105] ata6.01: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[ 3931.448108] ata6.02: hard resetting link
[ 3931.768105] ata6.02: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[ 3931.768108] ata6.03: hard resetting link
[ 3932.087491] ata6.03: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[ 3932.087494] ata6.04: hard resetting link
[ 3932.408102] ata6.04: SATA link down (SStatus 0 SControl 320)
[ 3932.408105] ata6.05: hard resetting link
[ 3932.728105] ata6.05: SATA link up 1.5 Gbps (SStatus 113 SControl 320)
[ 3932.728128] ata6.00: failed to IDENTIFY (I/O error, err_mask=0x100)
[ 3932.728130] ata6.15: hard resetting link
[ 3933.824763] ata6.15: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[ 3936.128023] ata6.00: hard resetting link
[ 3939.448006] ata6.15: qc timeout (cmd 0xe4)
[ 3939.448012] ata6.00: failed to read SCR 1 (Emask=0x4)
[ 3939.448014] ata6.00: failed to read SCR 0 (Emask=0x40)
[ 3939.448017] ata6.01: hard resetting link
[ 3939.448019] ata6.01: failed to read SCR 2 (Emask=0x40)
[ 3939.448020] ata6.01: failed to read SCR 2 (Emask=0x40)
[ 3939.448022] ata6.01: COMRESET failed (errno=-5)
[ 3939.448024] ata6.01: failed to read SCR 0 (Emask=0x40)
[ 3939.448025] ata6.01: reset failed, giving up
[ 3939.448027] ata6.01: failed to recover link after 3 tries, disabling
[ 3939.448030] ata6.15: hard resetting link
[ 3940.153384] ata6.15: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[ 3940.472555] ata6.01: failed to write SCR 1 (Emask=0x100)
[ 3940.472558] ata6.01: COMRESET failed (errno=-5)
[ 3940.472561] ata6.01: failed to write SCR 1 (Emask=0x40)
[ 3940.472562] ata6.01: failed to clear SError.N (errno=-5)
[ 3940.472566] ata6.15: hard resetting link
[ 3941.184009] ata6.15: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[ 3941.502773] ata6.01: failed to read SCR 0 (Emask=0x100)
[ 3941.502775] ata6.01: failed to write SCR 1 (Emask=0x40)
[ 3941.502776] ata6.01: failed to clear SError.N (errno=-5)
[ 3941.502779] ata6.15: hard resetting link
[ 3942.212009] ata6.15: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[ 3942.532041] ata6.01: failed to read SCR 0 (Emask=0x100)
[ 3942.532043] ata6.01: failed to write SCR 1 (Emask=0x40)
[ 3942.532044] ata6.01: failed to clear SError.N (errno=-5)
[ 3942.532047] ata6.15: hard resetting link
[ 3943.237718] ata6.15: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[ 3943.560039] ata6.01: failed to read SCR 0 (Emask=0x100)
[ 3943.560041] ata6.01: failed to write SCR 1 (Emask=0x40)
[ 3943.560042] ata6.01: failed to clear SError.N (errno=-5)
[ 3943.560044] ata6: failed to recover PMP after 5 tries, giving up
[ 3943.560045] ata6.15: Port Multiplier detaching
[ 3943.560068] ata6.00: disabled
[ 3943.560072] ata6: exception Emask 0x42 SAct 0x0 SErr 0x80800 action 0x6 frozen t4
[ 3943.560073] ata6: irq_stat 0x00800000, incorrect PMP
[ 3943.560075] ata6: SError: { HostInt 10B8B }
[ 3943.560077] ata6: hard resetting link
[ 3944.266271] ata6: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[ 3944.266275] ata6: EH complete
[ 4014.958450] ata6: exception Emask 0x50 SAct 0x0 SErr 0x4090800 action 0xe frozen
[ 4014.958454] ata6: irq_stat 0x00400040, connection status changed
[ 4014.958456] ata6: SError: { HostInt PHYRdyChg 10B8B DevExch }
[ 4014.958461] ata6: hard resetting link
[ 4015.684011] ata6: SATA link down (SStatus 0 SControl 300)
[ 4015.684015] ata6: EH complete

```

Right now I don't know if there is a Hardware-Problem on the box or maybe the sata driver has a Problem. When I connect the box via usb to the pc, the disks get detected and everything is fine - and slower ;-)

lspci -vnn
```
00:1f.2 SATA controller [0106]: Intel Corporation 82801IR/IO/IH (ICH9R/DO/DH) 6 port SATA AHCI Controller [8086:2922] (rev 02) (prog-if 01)
        Subsystem: Holco Enterprise Co, Ltd/Shuttle Computer Device [1297:3106]
        Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 2301
        I/O ports at f800 [size=8]
        I/O ports at f700 [size=4]
        I/O ports at f600 [size=8]
        I/O ports at f500 [size=4]
        I/O ports at f400 [size=32]
        Memory at fdffd000 (32-bit, non-prefetchable) [size=2K]
        Capabilities: <access denied>
        Kernel driver in use: ahci

```

Any help is really appreciated. I googled around but found unfortunately nothing helpfull regarding this specific problem

tnx n greetz

---

### Post by kayex on 2009-08-05
did you ever figure this out? :confused: I have the exact same issue.

---

