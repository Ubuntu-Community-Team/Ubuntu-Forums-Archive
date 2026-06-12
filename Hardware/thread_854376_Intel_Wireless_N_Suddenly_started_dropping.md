---
title: "Intel Wireless N Suddenly started dropping"
date: 2008-07-09
forum: Hardware
---

### Post by LeoSolaris on 2008-07-09
This is a strange issue, because it worked perfectly fine before I moved...

After getting DSL in my new apartment, I connected everything and I have a line that works when I plug in my laptop, but when I switch over to using my Linksys WRT300N (v1.1 with current firmware upgrade) My laptop will only intermittently connect. My wireless card is the Intel Wireless N in a Dell 1520.

I am pretty sure it is something in a recent update in Ubuntu, because there is no issue in Windows.

There are a lot more signals here, maybe it is getting confused?

Leo

---

### Post by pytheas22 on 2008-07-09
The next time it disconnects, can you open a terminal and immediately enter the command:
```

dmesg
```

and please post the output here (it will be a lot, but please post it all).

Also, when you say that the laptop will only intermittently connect, what do you mean?  Does the connection drop after a few minutes or are you unable to connect at all sometimes?

---

### Post by LeoSolaris on 2008-07-10
After a lot of poking, I figured out that it was actually the old phone that was attached to the line. It was ringing at the same time the DSL dropped, which was roughly every 30 seconds. No one was on the line, but it still rang.

Got a new phone and that solved it.

Thank ya though, pytheas!

Leo

---

### Post by LeoSolaris on 2008-07-10
> **pytheas22 said:**
> The next time it disconnects, can you open a terminal and immediately enter the command:
```

dmesg
```and please post the output here (it will be a lot, but please post it all).

Also, when you say that the laptop will only intermittently connect, what do you mean?  Does the connection drop after a few minutes or are you unable to connect at all sometimes?

```

[   35.182570] iTCO_wdt: Found a ICH8M TCO device (Version=2, TCOBASE=0x1060)
[   35.182615] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   35.339730] iwl4965: Intel(R) Wireless WiFi Link 4965AGN driver for Linux, 1.2.25
[   35.339734] iwl4965: Copyright(c) 2003-2007 Intel Corporation
[   35.339901] ACPI: PCI Interrupt 0000:0c:00.0[A] -> GSI 17 (level, low) -> IRQ 17
[   35.339921] PCI: Setting latency timer of device 0000:0c:00.0 to 64
[   35.340536] iwl4965: Detected Intel Wireless WiFi Link 4965AGN
[   35.484948] wmaster0: Selected rate control algorithm 'iwl-4965-rs'
[   35.554670] input: PC Speaker as /devices/platform/pcspkr/input/input8
[   35.661664] Linux video capture interface: v2.00
[   35.912686] uvcvideo: Found UVC 1.00 device Laptop Integrated Webcam (05a9:2640)
[   35.913707] uvcvideo: Failed to query (135) UVC control 1 (unit 0) : -32 (exp. 26).
[   35.925769] ACPI: PCI interrupt for device 0000:0c:00.0 disabled
[   35.970987] usbcore: registered new interface driver uvcvideo
[   35.970993] USB Video Class driver (v0.1.0)
[   36.051947] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 21 (level, low) -> IRQ 21
[   36.052590] PCI: Setting latency timer of device 0000:00:1b.0 to 64
[   36.118614] Synaptics Touchpad, model: 1, fw: 6.3, id: 0x1a0b1, caps: 0xa04793/0x300000
[   36.118619] serio: Synaptics pass-through port at isa0060/serio1/input0
[   36.167361] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input9
[   36.485693] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
[   37.122002] ALSA /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/sound/alsa-driver/pci/hda/../../alsa-kernel/pci/hda/hda_intel.c:593: hda_intel: azx_get_response timeout, switching to polling mode: last cmd=0x00af0900
[   38.257853] lp: driver loaded but no devices found
[   38.395584] Adding 3092472k swap on /dev/sda5.  Priority:-1 extents:1 across:3092472k
[   38.424576] EXT3 FS on sda6, internal journal
[   38.571164] kjournald starting.  Commit interval 5 seconds
[   38.571373] EXT3 FS on sda7, internal journal
[   38.571380] EXT3-fs: mounted filesystem with ordered data mode.
[   39.069896] ip_tables: (C) 2000-2006 Netfilter Core Team
[   39.103089] nf_conntrack version 0.5.0 (16384 buckets, 65536 max)
[   39.977489] No dock devices found.
[   41.171167] ppdev: user-space parallel port driver
[   41.233865] audit(1215717378.096:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=6702 profile="/usr/sbin/cupsd" namespace="default"
[   42.647343] vboxdrv: Trying to deactivate the NMI watchdog permanently...
[   42.647351] vboxdrv: Successfully done.
[   42.647354] vboxdrv: Found 2 processor cores.
[   42.647374] vboxdrv: fAsync=0 u64DiffCores=612.
[   42.647444] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
[   42.647447] vboxdrv: Successfully loaded version 1.6.0 (interface 0x00070001).
[   44.079873] ACPI: PCI Interrupt 0000:0c:00.0[A] -> GSI 17 (level, low) -> IRQ 17
[   44.080115] PM: Writing back config space on device 0000:0c:00.0 at offset 1 (was 100102, writing 100106)
[   44.191233] iwl4965: Tunable channels: 11 802.11bg, 13 802.11a channels
[   44.201555] Registered led device: iwl-phy0:RX
[   44.201589] Registered led device: iwl-phy0:TX
[   56.658562] NET: Registered protocol family 10
[   56.659016] lo: Disabled Privacy Extensions
[   56.660751] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   56.661608] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   62.349976] CPU0 attaching NULL sched-domain.
[   62.349986] CPU1 attaching NULL sched-domain.
[   62.371812] CPU0 attaching sched-domain:
[   62.371822]  domain 0: span 03
[   62.371826]   groups: 01 02
[   62.371832]   domain 1: span 03
[   62.371835]    groups: 03
[   62.371840]    domain 2: span 03
[   62.371843]     groups: 03
[   62.371848] CPU1 attaching sched-domain:
[   62.371851]  domain 0: span 03
[   62.371854]   groups: 02 01
[   62.371859]   domain 1: span 03
[   62.371862]    groups: 03
[   62.371866]    domain 2: span 03
[   62.371870]     groups: 03
[   62.745609] NET: Registered protocol family 17
[   64.558753] wlan0: Initial auth_alg=0
[   64.558764] wlan0: authenticate with AP 00:1a:70:fd:0b:7b
[   64.664973] wlan0: authenticate with AP 00:1a:70:fd:0b:7b
[   64.755219] wlan0: authenticate with AP 00:1a:70:fd:0b:7b
[   64.882088] wlan0: authentication with AP 00:1a:70:fd:0b:7b timed out
[   72.262345] wlan0: Initial auth_alg=0
[   72.262355] wlan0: authenticate with AP 00:1a:70:fd:0b:7b
[   72.265397] wlan0: Initial auth_alg=0
[   72.265407] wlan0: authenticate with AP 00:1a:70:fd:0b:7b
[   72.267435] wlan0: Initial auth_alg=0
[   72.267446] wlan0: authenticate with AP 00:1a:70:fd:0b:7b
[   72.296509] wlan0: authenticate with AP 00:1a:70:fd:0b:7b
[   72.333984] wlan0: authenticate with AP 00:1a:70:fd:0b:7b
[   72.419127] wlan0: authentication with AP 00:1a:70:fd:0b:7b timed out
[   72.634884] wlan0: authentication frame received from 00:1a:70:fd:0b:7b, but not in authenticate state - ignored
[   76.455145] wlan0: Initial auth_alg=0
[   76.455156] wlan0: authenticate with AP 00:1a:70:fd:0b:7b
[   76.457931] wlan0: Initial auth_alg=0
[   76.457940] wlan0: authenticate with AP 00:1a:70:fd:0b:7b
[   76.559573] wlan0: authenticate with AP 00:1a:70:fd:0b:7b
[   76.700243] wlan0: authenticate with AP 00:1a:70:fd:0b:7b
[   76.825254] wlan0: authentication with AP 00:1a:70:fd:0b:7b timed out
[   80.972027] wlan0: authentication frame received from 00:1a:70:fd:0b:7b, but not in authenticate state - ignored
[   80.974565] wlan0: Initial auth_alg=0
[   80.974574] wlan0: authenticate with AP 00:1a:70:fd:0b:7b
[   80.976950] wlan0: Initial auth_alg=0
[   80.976959] wlan0: authenticate with AP 00:1a:70:fd:0b:7b
[   80.979473] wlan0: Initial auth_alg=0
[   80.979484] wlan0: authenticate with AP 00:1a:70:fd:0b:7b
[   81.090814] wlan0: authenticate with AP 00:1a:70:fd:0b:7b
[   81.214744] wlan0: authenticate with AP 00:1a:70:fd:0b:7b
[   81.345683] wlan0: authentication with AP 00:1a:70:fd:0b:7b timed out
[   85.719573] wlan0: Initial auth_alg=0
[   85.719582] wlan0: authenticate with AP 00:1a:70:fd:0b:7b
[   85.721898] wlan0: Initial auth_alg=0
[   85.721907] wlan0: authenticate with AP 00:1a:70:fd:0b:7b
[   85.811899] wlan0: authenticate with AP 00:1a:70:fd:0b:7b
[   85.857213] wlan0: authenticate with AP 00:1a:70:fd:0b:7b
[   85.902786] wlan0: authentication with AP 00:1a:70:fd:0b:7b timed out
[   89.657034] wlan0: Initial auth_alg=0
[   89.657043] wlan0: authenticate with AP 00:1a:70:fd:0b:7b
[   89.659650] wlan0: Initial auth_alg=0
[   89.659657] wlan0: authenticate with AP 00:1a:70:fd:0b:7b
[   89.857866] wlan0: authenticate with AP 00:1a:70:fd:0b:7b
[   90.057702] wlan0: authenticate with AP 00:1a:70:fd:0b:7b
[   90.257486] wlan0: authentication with AP 00:1a:70:fd:0b:7b timed out
[   92.832778] wlan0: authentication frame received from 00:1a:70:fd:0b:7b, but not in authenticate state - ignored
[   92.835819] wlan0: Initial auth_alg=0
[   92.835830] wlan0: authenticate with AP 00:1a:70:fd:0b:7b
[   92.837578] wlan0: Initial auth_alg=0
[   92.837588] wlan0: authenticate with AP 00:1a:70:fd:0b:7b
[   92.874963] wlan0: authenticate with AP 00:1a:70:fd:0b:7b
[   92.910811] wlan0: authenticate with AP 00:1a:70:fd:0b:7b
[   92.947749] wlan0: authentication with AP 00:1a:70:fd:0b:7b timed out
[   94.598775] wlan0: authentication frame received from 00:1a:70:fd:0b:7b, but not in authenticate state - ignored
[   94.828451] wlan0: authentication frame received from 00:1a:70:fd:0b:7b, but not in authenticate state - ignored
[   95.456294] wlan0: Initial auth_alg=0
[   95.456304] wlan0: authenticate with AP 00:1a:70:fd:0b:7b
[   95.460000] wlan0: Initial auth_alg=0
[   95.460009] wlan0: authenticate with AP 00:1a:70:fd:0b:7b
[   95.460033] wlan0: RX authentication from 00:1a:70:fd:0b:7b (alg=0 transaction=2 status=0)
[   95.460037] wlan0: authenticated
[   95.460040] wlan0: associate with AP 00:1a:70:fd:0b:7b
[   95.460056] wlan0: authentication frame received from 00:1a:70:fd:0b:7b, but not in authenticate state - ignored
[   95.461868] wlan0: authentication frame received from 00:1a:70:fd:0b:7b, but not in authenticate state - ignored
[   95.464496] wlan0: RX AssocResp from 00:1a:70:fd:0b:7b (capab=0x411 status=0 aid=1)
[   95.464505] wlan0: associated
[   95.464620] wlan0: WMM queue=2 aci=0 acm=0 aifs=3 cWmin=15 cWmax=1023 burst=0
[   95.464626] wlan0: WMM queue=3 aci=1 acm=0 aifs=7 cWmin=15 cWmax=1023 burst=0
[   95.464631] wlan0: WMM queue=1 aci=2 acm=0 aifs=2 cWmin=7 cWmax=15 burst=30
[   95.464636] wlan0: WMM queue=0 aci=3 acm=0 aifs=2 cWmin=3 cWmax=7 burst=15
[   95.469877] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  100.295884] wlan0: no IPv6 routers present
[  105.334716] wlan0: No ProbeResp from current AP 00:1a:70:fd:0b:7b - assume out of range
[  108.716470] wlan0: Initial auth_alg=0
[  108.716484] wlan0: authenticate with AP 00:1a:70:fd:0b:7b
[  108.718266] wlan0: Initial auth_alg=0
[  108.718276] wlan0: authenticate with AP 00:1a:70:fd:0b:7b
[  108.900554] wlan0: authenticate with AP 00:1a:70:fd:0b:7b
[  109.099863] wlan0: authenticate with AP 00:1a:70:fd:0b:7b
[  109.290791] wlan0: authentication with AP 00:1a:70:fd:0b:7b timed out
[  109.568028] wlan0: authentication frame received from 00:1a:70:fd:0b:7b, but not in authenticate state - ignored
[  113.946840] wlan0: authentication frame received from 00:1a:70:fd:0b:7b, but not in authenticate state - ignored
[  116.465517] wlan0: authentication frame received from 00:1a:70:fd:0b:7b, but not in authenticate state - ignored
[  116.468648] wlan0: Initial auth_alg=0
[  116.468659] wlan0: authenticate with AP 00:1a:70:fd:0b:7b
[  116.471032] wlan0: Initial auth_alg=0
[  116.471043] wlan0: authenticate with AP 00:1a:70:fd:0b:7b
[  116.511471] wlan0: authenticate with AP 00:1a:70:fd:0b:7b
[  116.628664] wlan0: authenticate with AP 00:1a:70:fd:0b:7b
[  116.671660] wlan0: authentication with AP 00:1a:70:fd:0b:7b timed out
[  119.214871] wlan0: authentication frame received from 00:1a:70:fd:0b:7b, but not in authenticate state - ignored
[  119.218091] wlan0: Initial auth_alg=0
[  119.218099] wlan0: authenticate with AP 00:1a:70:fd:0b:7b
[  119.221174] wlan0: Initial auth_alg=0
[  119.221180] wlan0: authenticate with AP 00:1a:70:fd:0b:7b
[  119.225355] wlan0: Initial auth_alg=0
[  119.225362] wlan0: authenticate with AP 00:1a:70:fd:0b:7b
[  119.228435] wlan0: Initial auth_alg=0
[  119.228442] wlan0: authenticate with AP 00:1a:70:fd:0b:7b
[  119.426895] wlan0: authenticate with AP 00:1a:70:fd:0b:7b
[  119.626798] wlan0: authenticate with AP 00:1a:70:fd:0b:7b
[  119.826714] wlan0: authentication with AP 00:1a:70:fd:0b:7b timed out
[  122.964391] wlan0: authentication frame received from 00:1a:70:fd:0b:7b, but not in authenticate state - ignored
[  123.737110] wlan0: authentication frame received from 00:1a:70:fd:0b:7b, but not in authenticate state - ignored
[  124.457548] wlan0: Initial auth_alg=0
[  124.457558] wlan0: authenticate with AP 00:1a:70:fd:0b:7b
[  124.460351] wlan0: Initial auth_alg=0
[  124.460361] wlan0: authenticate with AP 00:1a:70:fd:0b:7b
[  124.576713] wlan0: authenticate with AP 00:1a:70:fd:0b:7b
[  124.638139] wlan0: authenticate with AP 00:1a:70:fd:0b:7b
[  124.677757] wlan0: authentication with AP 00:1a:70:fd:0b:7b timed out
[  126.653408] wlan0: Initial auth_alg=0
[  126.653419] wlan0: authenticate with AP 00:1a:70:fd:0b:7b
[  126.655340] wlan0: Initial auth_alg=0
[  126.655349] wlan0: authenticate with AP 00:1a:70:fd:0b:7b
[  126.658881] wlan0: Initial auth_alg=0
[  126.658891] wlan0: authenticate with AP 00:1a:70:fd:0b:7b
[  126.661108] wlan0: Initial auth_alg=0
[  126.661118] wlan0: authenticate with AP 00:1a:70:fd:0b:7b
[  126.801040] wlan0: authenticate with AP 00:1a:70:fd:0b:7b
[  126.900888] wlan0: authenticate with AP 00:1a:70:fd:0b:7b
[  126.981428] wlan0: authentication with AP 00:1a:70:fd:0b:7b timed out
[  131.561631] wlan0: Initial auth_alg=0
[  131.561641] wlan0: authenticate with AP 00:1a:70:fd:0b:7b
[  131.563710] wlan0: Initial auth_alg=0
[  131.563719] wlan0: authenticate with AP 00:1a:70:fd:0b:7b
[  131.586795] wlan0: authenticate with AP 00:1a:70:fd:0b:7b
[  131.625875] wlan0: authenticate with AP 00:1a:70:fd:0b:7b
[  131.660499] wlan0: authentication with AP 00:1a:70:fd:0b:7b timed out
[  135.866118] wlan0: authentication frame received from 00:1a:70:fd:0b:7b, but not in authenticate state - ignored
[  135.868740] wlan0: Initial auth_alg=0
[  135.868749] wlan0: authenticate with AP 00:1a:70:fd:0b:7b
[  135.871907] wlan0: Initial auth_alg=0
[  135.871915] wlan0: authenticate with AP 00:1a:70:fd:0b:7b
[  135.889251] wlan0: authenticate with AP 00:1a:70:fd:0b:7b
[  135.950468] wlan0: authenticate with AP 00:1a:70:fd:0b:7b
[  136.053219] wlan0: authentication with AP 00:1a:70:fd:0b:7b timed out
[  138.549840] wlan0: authentication frame received from 00:1a:70:fd:0b:7b, but not in authenticate state - ignored
[  143.381815] wlan0: authentication frame received from 00:1a:70:fd:0b:7b, but not in authenticate state - ignored
[  143.384932] wlan0: Initial auth_alg=0
[  143.384943] wlan0: authenticate with AP 00:1a:70:fd:0b:7b
[  143.388345] wlan0: Initial auth_alg=0
[  143.388354] wlan0: authenticate with AP 00:1a:70:fd:0b:7b
[  143.481232] wlan0: authenticate with AP 00:1a:70:fd:0b:7b
[  143.522293] wlan0: authenticate with AP 00:1a:70:fd:0b:7b
[  143.577926] wlan0: RX authentication from 00:1a:70:fd:0b:7b (alg=0 transaction=2 status=0)
[  143.577936] wlan0: authenticated
[  143.577940] wlan0: associate with AP 00:1a:70:fd:0b:7b
[  143.615380] wlan0: associate with AP 00:1a:70:fd:0b:7b
[  143.756192] wlan0: associate with AP 00:1a:70:fd:0b:7b
[  143.953138] wlan0: association with AP 00:1a:70:fd:0b:7b timed out
[  148.489640] wlan0: Initial auth_alg=0
[  148.489650] wlan0: authenticate with AP 00:1a:70:fd:0b:7b
[  148.491960] wlan0: Initial auth_alg=0
[  148.491971] wlan0: authenticate with AP 00:1a:70:fd:0b:7b
[  148.529407] wlan0: authenticate with AP 00:1a:70:fd:0b:7b
[  148.560835] wlan0: authenticate with AP 00:1a:70:fd:0b:7b
[  148.602075] wlan0: authentication with AP 00:1a:70:fd:0b:7b timed out
[  148.748766] wlan0: authentication frame received from 00:1a:70:fd:0b:7b, but not in authenticate state - ignored
[  152.058628] wlan0: Initial auth_alg=0
[  152.058639] wlan0: authenticate with AP 00:1a:70:fd:0b:7b
[  152.061795] wlan0: Initial auth_alg=0
[  152.061804] wlan0: authenticate with AP 00:1a:70:fd:0b:7b
[  152.104918] wlan0: authenticate with AP 00:1a:70:fd:0b:7b
[  152.130035] wlan0: authenticate with AP 00:1a:70:fd:0b:7b
[  152.179999] wlan0: authentication with AP 00:1a:70:fd:0b:7b timed out
[  154.809546] wlan0: authentication frame received from 00:1a:70:fd:0b:7b, but not in authenticate state - ignored
[  154.813511] wlan0: Initial auth_alg=0
[  154.813519] wlan0: authenticate with AP 00:1a:70:fd:0b:7b
[  154.815462] wlan0: Initial auth_alg=0
[  154.815471] wlan0: authenticate with AP 00:1a:70:fd:0b:7b
[  154.818671] wlan0: Initial auth_alg=0
[  154.818680] wlan0: authenticate with AP 00:1a:70:fd:0b:7b
[  154.821815] wlan0: Initial auth_alg=0
[  154.821823] wlan0: authenticate with AP 00:1a:70:fd:0b:7b
[  154.869980] wlan0: authenticate with AP 00:1a:70:fd:0b:7b
[  154.981970] wlan0: authenticate with AP 00:1a:70:fd:0b:7b
[  155.103575] wlan0: authentication with AP 00:1a:70:fd:0b:7b timed out
[  159.192671] wlan0: authentication frame received from 00:1a:70:fd:0b:7b, but not in authenticate state - ignored
[  161.102993] wlan0: Initial auth_alg=0
[  161.103004] wlan0: authenticate with AP 00:1a:70:fd:0b:7b
[  161.104763] wlan0: Initial auth_alg=0
[  161.104774] wlan0: authenticate with AP 00:1a:70:fd:0b:7b
[  161.196729] wlan0: authenticate with AP 00:1a:70:fd:0b:7b
[  161.302558] wlan0: authenticate with AP 00:1a:70:fd:0b:7b
[  161.408294] wlan0: authentication with AP 00:1a:70:fd:0b:7b timed out
[  162.321923] wlan0: authentication frame received from 00:1a:70:fd:0b:7b, but not in authenticate state - ignored
[  164.801008] wlan0: authentication frame received from 00:1a:70:fd:0b:7b, but not in authenticate state - ignored
[  166.548133] wlan0: Initial auth_alg=0
[  166.548143] wlan0: authenticate with AP 00:1a:70:fd:0b:7b
[  166.550655] wlan0: Initial auth_alg=0
[  166.550666] wlan0: authenticate with AP 00:1a:70:fd:0b:7b
[  166.673579] wlan0: authenticate with AP 00:1a:70:fd:0b:7b
[  166.744266] wlan0: authenticate with AP 00:1a:70:fd:0b:7b
[  166.827020] wlan0: authentication with AP 00:1a:70:fd:0b:7b timed out
[  170.126822] wlan0: Initial auth_alg=0
[  170.126832] wlan0: authenticate with AP 00:1a:70:fd:0b:7b
[  170.129957] wlan0: Initial auth_alg=0
[  170.129964] wlan0: authenticate with AP 00:1a:70:fd:0b:7b
[  170.207603] wlan0: authenticate with AP 00:1a:70:fd:0b:7b
[  170.238274] wlan0: authenticate with AP 00:1a:70:fd:0b:7b
[  170.254858] wlan0: authentication with AP 00:1a:70:fd:0b:7b timed out
[  174.560599] wlan0: authentication frame received from 00:1a:70:fd:0b:7b, but not in authenticate state - ignored
[  174.560614] wlan0: authentication frame received from 00:1a:70:fd:0b:7b, but not in authenticate state - ignored
[  174.562929] wlan0: Initial auth_alg=0
[  174.562940] wlan0: authenticate with AP 00:1a:70:fd:0b:7b
[  174.565023] wlan0: Initial auth_alg=0
[  174.565033] wlan0: authenticate with AP 00:1a:70:fd:0b:7b
[  174.567451] wlan0: Initial auth_alg=0
[  174.567461] wlan0: authenticate with AP 00:1a:70:fd:0b:7b
[  174.673843] wlan0: authenticate with AP 00:1a:70:fd:0b:7b
[  174.800443] wlan0: authenticate with AP 00:1a:70:fd:0b:7b
[  174.860081] wlan0: authentication with AP 00:1a:70:fd:0b:7b timed out
[  175.013644] wlan0: authentication frame received from 00:1a:70:fd:0b:7b, but not in authenticate state - ignored
[  175.050872] wlan0: authentication frame received from 00:1a:70:fd:0b:7b, but not in authenticate state - ignored
[  175.175906] wlan0: authentication frame received from 00:1a:70:fd:0b:7b, but not in authenticate state - ignored
[  175.176769] wlan0: authentication frame received from 00:1a:70:fd:0b:7b, but not in authenticate state - ignored
[  176.558771] wlan0: authentication frame received from 00:1a:70:fd:0b:7b, but not in authenticate state - ignored
[  176.559672] wlan0: authentication frame received from 00:1a:70:fd:0b:7b, but not in authenticate state - ignored
[  176.560588] wlan0: authentication frame received from 00:1a:70:fd:0b:7b, but not in authenticate state - ignored
[  176.561473] wlan0: authentication frame received from 00:1a:70:fd:0b:7b, but not in authenticate state - ignored
[  176.562384] wlan0: authentication frame received from 00:1a:70:fd:0b:7b, but not in authenticate state - ignored
[  176.563373] wlan0: authentication frame received from 00:1a:70:fd:0b:7b, but not in authenticate state - ignored
[  176.564245] wlan0: authentication frame received from 00:1a:70:fd:0b:7b, but not in authenticate state - ignored
[  176.565140] wlan0: authentication frame received from 00:1a:70:fd:0b:7b, but not in authenticate state - ignored
[  176.566088] wlan0: authentication frame received from 00:1a:70:fd:0b:7b, but not in authenticate state - ignored
[  176.567343] wlan0: association frame received from 00:1a:70:fd:0b:7b, but not in associate state - ignored
[  176.568561] wlan0: association frame received from 00:1a:70:fd:0b:7b, but not in associate state - ignored
[  176.570091] wlan0: RX deauthentication from 00:1a:70:fd:0b:7b (reason=15)
[  176.570096] wlan0: deauthenticated
[  176.571000] wlan0: authentication frame received from 00:1a:70:fd:0b:7b, but not in authenticate state - ignored
[  176.571895] wlan0: authentication frame received from 00:1a:70:fd:0b:7b, but not in authenticate state - ignored
[  176.572775] wlan0: authentication frame received from 00:1a:70:fd:0b:7b, but not in authenticate state - ignored
[  176.574607] wlan0: authentication frame received from 00:1a:70:fd:0b:7b, but not in authenticate state - ignored
[  176.575520] wlan0: authentication frame received from 00:1a:70:fd:0b:7b, but not in authenticate state - ignored
[  176.576416] wlan0: authentication frame received from 00:1a:70:fd:0b:7b, but not in authenticate state - ignored
[  176.577296] wlan0: authentication frame received from 00:1a:70:fd:0b:7b, but not in authenticate state - ignored
[  176.578209] wlan0: authentication frame received from 00:1a:70:fd:0b:7b, but not in authenticate state - ignored
[  176.579102] wlan0: authentication frame received from 00:1a:70:fd:0b:7b, but not in authenticate state - ignored
[  176.580917] wlan0: authentication frame received from 00:1a:70:fd:0b:7b, but not in authenticate state - ignored
[  176.581442] wlan0: authentication frame received from 00:1a:70:fd:0b:7b, but not in authenticate state - ignored
[  176.582248] wlan0: authentication frame received from 00:1a:70:fd:0b:7b, but not in authenticate state - ignored
[  176.583114] wlan0: authentication frame received from 00:1a:70:fd:0b:7b, but not in authenticate state - ignored
[  176.584925] wlan0: authentication frame received from 00:1a:70:fd:0b:7b, but not in authenticate state - ignored
[  176.585815] wlan0: authentication frame received from 00:1a:70:fd:0b:7b, but not in authenticate state - ignored
[  178.990984] wlan0: RX deauthentication from 00:1a:70:fd:0b:7b (reason=7)
[  178.990996] wlan0: RX deauthentication from 00:1a:70:fd:0b:7b (reason=7)
[  178.991003] wlan0: RX deauthentication from 00:1a:70:fd:0b:7b (reason=7)
[  178.991009] wlan0: RX deauthentication from 00:1a:70:fd:0b:7b (reason=7)
[  178.991015] wlan0: RX deauthentication from 00:1a:70:fd:0b:7b (reason=7)
[  178.991021] wlan0: RX deauthentication from 00:1a:70:fd:0b:7b (reason=7)
[  178.991027] wlan0: RX deauthentication from 00:1a:70:fd:0b:7b (reason=7)
[  178.991033] wlan0: RX deauthentication from 00:1a:70:fd:0b:7b (reason=7)
[  178.991038] wlan0: RX deauthentication from 00:1a:70:fd:0b:7b (reason=7)
[  178.991044] wlan0: RX deauthentication from 00:1a:70:fd:0b:7b (reason=7)
[  178.991050] wlan0: RX deauthentication from 00:1a:70:fd:0b:7b (reason=7)
[  178.991056] wlan0: RX deauthentication from 00:1a:70:fd:0b:7b (reason=7)
[  178.991061] wlan0: RX deauthentication from 00:1a:70:fd:0b:7b (reason=7)
[  178.991067] wlan0: RX deauthentication from 00:1a:70:fd:0b:7b (reason=7)
[  178.991073] wlan0: RX deauthentication from 00:1a:70:fd:0b:7b (reason=7)
[  178.991078] wlan0: RX deauthentication from 00:1a:70:fd:0b:7b (reason=7)
[  178.991084] wlan0: RX deauthentication from 00:1a:70:fd:0b:7b (reason=7)
[  178.991089] wlan0: RX deauthentication from 00:1a:70:fd:0b:7b (reason=7)
[  178.991095] wlan0: RX deauthentication from 00:1a:70:fd:0b:7b (reason=7)
[  178.991101] wlan0: RX deauthentication from 00:1a:70:fd:0b:7b (reason=7)
[  178.994307] wlan0: Initial auth_alg=0
[  178.994313] wlan0: authenticate with AP 00:1a:70:fd:0b:7b
[  178.996773] wlan0: Initial auth_alg=0
[  178.996784] wlan0: authenticate with AP 00:1a:70:fd:0b:7b
[  178.996810] wlan0: RX authentication from 00:1a:70:fd:0b:7b (alg=0 transaction=2 status=0)
[  178.996814] wlan0: authenticated
[  178.996818] wlan0: associate with AP 00:1a:70:fd:0b:7b
[  178.996835] wlan0: authentication frame received from 00:1a:70:fd:0b:7b, but not in authenticate state - ignored
[  179.000211] wlan0: authentication frame received from 00:1a:70:fd:0b:7b, but not in authenticate state - ignored
[  179.001381] wlan0: RX AssocResp from 00:1a:70:fd:0b:7b (capab=0x411 status=0 aid=1)
[  179.001387] wlan0: associated
[  179.001504] wlan0: WMM queue=2 aci=0 acm=0 aifs=3 cWmin=15 cWmax=1023 burst=0
[  179.001510] wlan0: WMM queue=3 aci=1 acm=0 aifs=7 cWmin=15 cWmax=1023 burst=0
[  179.001514] wlan0: WMM queue=1 aci=2 acm=0 aifs=2 cWmin=7 cWmax=15 burst=30
[  179.001519] wlan0: WMM queue=0 aci=3 acm=0 aifs=2 cWmin=3 cWmax=7 burst=15
[  179.006710] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  186.130361] wlan0: no IPv6 routers present
[  366.064594] wlan0: No ProbeResp from current AP 00:1a:70:fd:0b:7b - assume out of range
[  369.642147] wlan0: No STA entry for own AP 00:1a:70:fd:0b:7b
[  369.645561] wlan0: Initial auth_alg=0
[  369.645575] wlan0: authenticate with AP 00:1a:70:fd:0b:7b
[  369.647416] wlan0: Initial auth_alg=0
[  369.647428] wlan0: authenticate with AP 00:1a:70:fd:0b:7b
[  369.766136] wlan0: authenticate with AP 00:1a:70:fd:0b:7b
[  369.846312] wlan0: authenticate with AP 00:1a:70:fd:0b:7b
[  369.934182] wlan0: authentication with AP 00:1a:70:fd:0b:7b timed out
[  370.564269] wlan0: authentication frame received from 00:1a:70:fd:0b:7b, but not in authenticate state - ignored
[  371.648229] wlan0: authentication frame received from 00:1a:70:fd:0b:7b, but not in authenticate state - ignored
[  375.096397] wlan0: authentication frame received from 00:1a:70:fd:0b:7b, but not in authenticate state - ignored
[  375.099016] wlan0: Initial auth_alg=0
[  375.099028] wlan0: authenticate with AP 00:1a:70:fd:0b:7b
[  375.101783] wlan0: Initial auth_alg=0
[  375.101794] wlan0: authenticate with AP 00:1a:70:fd:0b:7b
[  375.199132] wlan0: authenticate with AP 00:1a:70:fd:0b:7b
[  375.271473] wlan0: authenticate with AP 00:1a:70:fd:0b:7b
[  375.353706] wlan0: authentication with AP 00:1a:70:fd:0b:7b timed out
[  378.323269] wlan0: authentication frame received from 00:1a:70:fd:0b:7b, but not in authenticate state - ignored
[  378.327689] wlan0: Initial auth_alg=0
[  378.327698] wlan0: authenticate with AP 00:1a:70:fd:0b:7b
[  378.329746] wlan0: Initial auth_alg=0
[  378.329755] wlan0: authenticate with AP 00:1a:70:fd:0b:7b
[  378.329784] wlan0: RX authentication from 00:1a:70:fd:0b:7b (alg=0 transaction=2 status=0)
[  378.329788] wlan0: authenticated
[  378.329792] wlan0: associate with AP 00:1a:70:fd:0b:7b
[  378.331628] wlan0: authentication frame received from 00:1a:70:fd:0b:7b, but not in authenticate state - ignored
[  378.340574] wlan0: RX AssocResp from 00:1a:70:fd:0b:7b (capab=0x411 status=0 aid=1)
[  378.340583] wlan0: associated
[  378.340696] wlan0: WMM queue=2 aci=0 acm=0 aifs=3 cWmin=15 cWmax=1023 burst=0
[  378.340702] wlan0: WMM queue=3 aci=1 acm=0 aifs=7 cWmin=15 cWmax=1023 burst=0
[  378.340706] wlan0: WMM queue=1 aci=2 acm=0 aifs=2 cWmin=7 cWmax=15 burst=30
[  378.340711] wlan0: WMM queue=0 aci=3 acm=0 aifs=2 cWmin=3 cWmax=7 burst=15
[  378.345904] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  389.068333] wlan0: no IPv6 routers present
[  486.307241] wlan0: No ProbeResp from current AP 00:1a:70:fd:0b:7b - assume out of range
[  489.160785] wlan0: Initial auth_alg=0
[  489.160799] wlan0: authenticate with AP 00:1a:70:fd:0b:7b
[  489.162761] wlan0: RX authentication from 00:1a:70:fd:0b:7b (alg=0 transaction=2 status=0)
[  489.162767] wlan0: authenticated
[  489.162771] wlan0: associate with AP 00:1a:70:fd:0b:7b
[  489.167837] wlan0: Initial auth_alg=0
[  489.167847] wlan0: authenticate with AP 00:1a:70:fd:0b:7b
[  489.167904] wlan0: RX authentication from 00:1a:70:fd:0b:7b (alg=0 transaction=2 status=0)
[  489.167907] wlan0: authenticated
[  489.167911] wlan0: associate with AP 00:1a:70:fd:0b:7b
[  489.168519] wlan0: RX ReassocResp from 00:1a:70:fd:0b:7b (capab=0x411 status=0 aid=1)
[  489.168525] wlan0: associated
[  489.168637] wlan0: WMM queue=2 aci=0 acm=0 aifs=3 cWmin=15 cWmax=1023 burst=0
[  489.184988] wlan0: WMM queue=3 aci=1 acm=0 aifs=7 cWmin=15 cWmax=1023 burst=0
[  489.185598] wlan0: WMM queue=1 aci=2 acm=0 aifs=2 cWmin=7 cWmax=15 burst=30
[  489.186204] wlan0: WMM queue=0 aci=3 acm=0 aifs=2 cWmin=3 cWmax=7 burst=15
[  545.085025] wlan0: CTS protection enabled (BSSID=00:1a:70:fd:0b:7b)
[  545.969488] wlan0: CTS protection disabled (BSSID=00:1a:70:fd:0b:7b)
[  641.695221] npviewer.bin[12275]: segfault at 74731400 rip 74731400 rsp ffdfc78c error 14
[  641.766236] [UFW BLOCK INPUT]: IN=wlan0 OUT= MAC=00:1d:e0:50:46:ed:00:1a:70:fd:0b:79:08:00 SRC=209.47.169.13 DST=192.168.1.2 LEN=52 TOS=0x00 PREC=0x00 TTL=45 ID=11934 PROTO=TCP SPT=80 DPT=49456 WINDOW=65535 RES=0x00 ACK URGP=0 
```

I'll say it's long! It chopped off the top of it in the scroll back.

Ok it happened again, but it appears to not be as bad now. The intermittant loss of signal seems to happen slightly less often, but I am still getting a very low wireless signal, like 55% -65% when I am just 7-10 feet away though a thin closed door! (opening the door doesn't alter the strength)

So far as I have seen Windows hasn't had near the issues, nor a low, rapid fluxuation of signal like Ubuntu's. 

Interestingly, if I switched the router over to the N signal only rather than a mixed signal, Ubuntu could not connect. It is reading the signal as a wireless b, but the speed is the same, if not slightly faster in Ubuntu's connection, vrs. Windows.

Appearently all the change in the phone did was to allieviate the constant ringing and constant disconnection issues, while leaving the fluctuating signal issue.

I just did an update today and there was an update for the headers and other kernel updates, so maybe it will fix it. I have not restarted yet to see if that will work.

Thank you for your help! 

Leo

P.S It did it while I was typing here!   grrr   Here's the second dmesg:
```
not in authenticate state - ignored
[   95.461868] wlan0: authentication frame received from 00:1a:70:fd:0b:7b, but not in authenticate state - ignored
[   95.464496] wlan0: RX AssocResp from 00:1a:70:fd:0b:7b (capab=0x411 status=0 aid=1)
[   95.464505] wlan0: associated
[   95.464620] wlan0: WMM queue=2 aci=0 acm=0 aifs=3 cWmin=15 cWmax=1023 burst=0
[   95.464626] wlan0: WMM queue=3 aci=1 acm=0 aifs=7 cWmin=15 cWmax=1023 burst=0
[   95.464631] wlan0: WMM queue=1 aci=2 acm=0 aifs=2 cWmin=7 cWmax=15 burst=30
[   95.464636] wlan0: WMM queue=0 aci=3 acm=0 aifs=2 cWmin=3 cWmax=7 burst=15
[   95.469877] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  100.295884] wlan0: no IPv6 routers present
[  105.334716] wlan0: No ProbeResp from current AP 00:1a:70:fd:0b:7b - assume out of range
[  108.716470] wlan0: Initial auth_alg=0
[  108.716484] wlan0: authenticate with AP 00:1a:70:fd:0b:7b
[  108.718266] wlan0: Initial auth_alg=0
[  108.718276] wlan0: authenticate with AP 00:1a:70:fd:0b:7b
[  108.900554] wlan0: authenticate with AP 00:1a:70:fd:0b:7b
[  109.099863] wlan0: authenticate with AP 00:1a:70:fd:0b:7b
[  109.290791] wlan0: authentication with AP 00:1a:70:fd:0b:7b timed out
[  109.568028] wlan0: authentication frame received from 00:1a:70:fd:0b:7b, but not in authenticate state - ignored
[  113.946840] wlan0: authentication frame received from 00:1a:70:fd:0b:7b, but not in authenticate state - ignored
[  116.465517] wlan0: authentication frame received from 00:1a:70:fd:0b:7b, but not in authenticate state - ignored
[  116.468648] wlan0: Initial auth_alg=0
[  116.468659] wlan0: authenticate with AP 00:1a:70:fd:0b:7b
[  116.471032] wlan0: Initial auth_alg=0
[  116.471043] wlan0: authenticate with AP 00:1a:70:fd:0b:7b
[  116.511471] wlan0: authenticate with AP 00:1a:70:fd:0b:7b
[  116.628664] wlan0: authenticate with AP 00:1a:70:fd:0b:7b
[  116.671660] wlan0: authentication with AP 00:1a:70:fd:0b:7b timed out
[  119.214871] wlan0: authentication frame received from 00:1a:70:fd:0b:7b, but not in authenticate state - ignored
[  119.218091] wlan0: Initial auth_alg=0
[  119.218099] wlan0: authenticate with AP 00:1a:70:fd:0b:7b
[  119.221174] wlan0: Initial auth_alg=0
[  119.221180] wlan0: authenticate with AP 00:1a:70:fd:0b:7b
[  119.225355] wlan0: Initial auth_alg=0
[  119.225362] wlan0: authenticate with AP 00:1a:70:fd:0b:7b
[  119.228435] wlan0: Initial auth_alg=0
[  119.228442] wlan0: authenticate with AP 00:1a:70:fd:0b:7b
[  119.426895] wlan0: authenticate with AP 00:1a:70:fd:0b:7b
[  119.626798] wlan0: authenticate with AP 00:1a:70:fd:0b:7b
[  119.826714] wlan0: authentication with AP 00:1a:70:fd:0b:7b timed out
[  122.964391] wlan0: authentication frame received from 00:1a:70:fd:0b:7b, but not in authenticate state - ignored
[  123.737110] wlan0: authentication frame received from 00:1a:70:fd:0b:7b, but not in authenticate state - ignored
[  124.457548] wlan0: Initial auth_alg=0
[  124.457558] wlan0: authenticate with AP 00:1a:70:fd:0b:7b
[  124.460351] wlan0: Initial auth_alg=0
[  124.460361] wlan0: authenticate with AP 00:1a:70:fd:0b:7b
[  124.576713] wlan0: authenticate with AP 00:1a:70:fd:0b:7b
[  124.638139] wlan0: authenticate with AP 00:1a:70:fd:0b:7b
[  124.677757] wlan0: authentication with AP 00:1a:70:fd:0b:7b timed out
[  126.653408] wlan0: Initial auth_alg=0
[  126.653419] wlan0: authenticate with AP 00:1a:70:fd:0b:7b
[  126.655340] wlan0: Initial auth_alg=0
[  126.655349] wlan0: authenticate with AP 00:1a:70:fd:0b:7b
[  126.658881] wlan0: Initial auth_alg=0
[  126.658891] wlan0: authenticate with AP 00:1a:70:fd:0b:7b
[  126.661108] wlan0: Initial auth_alg=0
[  126.661118] wlan0: authenticate with AP 00:1a:70:fd:0b:7b
[  126.801040] wlan0: authenticate with AP 00:1a:70:fd:0b:7b
[  126.900888] wlan0: authenticate with AP 00:1a:70:fd:0b:7b
[  126.981428] wlan0: authentication with AP 00:1a:70:fd:0b:7b timed out
[  131.561631] wlan0: Initial auth_alg=0
[  131.561641] wlan0: authenticate with AP 00:1a:70:fd:0b:7b
[  131.563710] wlan0: Initial auth_alg=0
[  131.563719] wlan0: authenticate with AP 00:1a:70:fd:0b:7b
[  131.586795] wlan0: authenticate with AP 00:1a:70:fd:0b:7b
[  131.625875] wlan0: authenticate with AP 00:1a:70:fd:0b:7b
[  131.660499] wlan0: authentication with AP 00:1a:70:fd:0b:7b timed out
[  135.866118] wlan0: authentication frame received from 00:1a:70:fd:0b:7b, but not in authenticate state - ignored
[  135.868740] wlan0: Initial auth_alg=0
[  135.868749] wlan0: authenticate with AP 00:1a:70:fd:0b:7b
[  135.871907] wlan0: Initial auth_alg=0
[  135.871915] wlan0: authenticate with AP 00:1a:70:fd:0b:7b
[  135.889251] wlan0: authenticate with AP 00:1a:70:fd:0b:7b
[  135.950468] wlan0: authenticate with AP 00:1a:70:fd:0b:7b
[  136.053219] wlan0: authentication with AP 00:1a:70:fd:0b:7b timed out
[  138.549840] wlan0: authentication frame received from 00:1a:70:fd:0b:7b, but not in authenticate state - ignored
[  143.381815] wlan0: authentication frame received from 00:1a:70:fd:0b:7b, but not in authenticate state - ignored
[  143.384932] wlan0: Initial auth_alg=0
[  143.384943] wlan0: authenticate with AP 00:1a:70:fd:0b:7b
[  143.388345] wlan0: Initial auth_alg=0
[  143.388354] wlan0: authenticate with AP 00:1a:70:fd:0b:7b
[  143.481232] wlan0: authenticate with AP 00:1a:70:fd:0b:7b
[  143.522293] wlan0: authenticate with AP 00:1a:70:fd:0b:7b
[  143.577926] wlan0: RX authentication from 00:1a:70:fd:0b:7b (alg=0 transaction=2 status=0)
[  143.577936] wlan0: authenticated
[  143.577940] wlan0: associate with AP 00:1a:70:fd:0b:7b
[  143.615380] wlan0: associate with AP 00:1a:70:fd:0b:7b
[  143.756192] wlan0: associate with AP 00:1a:70:fd:0b:7b
[  143.953138] wlan0: association with AP 00:1a:70:fd:0b:7b timed out
[  148.489640] wlan0: Initial auth_alg=0
[  148.489650] wlan0: authenticate with AP 00:1a:70:fd:0b:7b
[  148.491960] wlan0: Initial auth_alg=0
[  148.491971] wlan0: authenticate with AP 00:1a:70:fd:0b:7b
[  148.529407] wlan0: authenticate with AP 00:1a:70:fd:0b:7b
[  148.560835] wlan0: authenticate with AP 00:1a:70:fd:0b:7b
[  148.602075] wlan0: authentication with AP 00:1a:70:fd:0b:7b timed out
[  148.748766] wlan0: authentication frame received from 00:1a:70:fd:0b:7b, but not in authenticate state - ignored
[  152.058628] wlan0: Initial auth_alg=0
[  152.058639] wlan0: authenticate with AP 00:1a:70:fd:0b:7b
[  152.061795] wlan0: Initial auth_alg=0
[  152.061804] wlan0: authenticate with AP 00:1a:70:fd:0b:7b
[  152.104918] wlan0: authenticate with AP 00:1a:70:fd:0b:7b
[  152.130035] wlan0: authenticate with AP 00:1a:70:fd:0b:7b
[  152.179999] wlan0: authentication with AP 00:1a:70:fd:0b:7b timed out
[  154.809546] wlan0: authentication frame received from 00:1a:70:fd:0b:7b, but not in authenticate state - ignored
[  154.813511] wlan0: Initial auth_alg=0
[  154.813519] wlan0: authenticate with AP 00:1a:70:fd:0b:7b
[  154.815462] wlan0: Initial auth_alg=0
[  154.815471] wlan0: authenticate with AP 00:1a:70:fd:0b:7b
[  154.818671] wlan0: Initial auth_alg=0
[  154.818680] wlan0: authenticate with AP 00:1a:70:fd:0b:7b
[  154.821815] wlan0: Initial auth_alg=0
[  154.821823] wlan0: authenticate with AP 00:1a:70:fd:0b:7b
[  154.869980] wlan0: authenticate with AP 00:1a:70:fd:0b:7b
[  154.981970] wlan0: authenticate with AP 00:1a:70:fd:0b:7b
[  155.103575] wlan0: authentication with AP 00:1a:70:fd:0b:7b timed out
[  159.192671] wlan0: authentication frame received from 00:1a:70:fd:0b:7b, but not in authenticate state - ignored
[  161.102993] wlan0: Initial auth_alg=0
[  161.103004] wlan0: authenticate with AP 00:1a:70:fd:0b:7b
[  161.104763] wlan0: Initial auth_alg=0
[  161.104774] wlan0: authenticate with AP 00:1a:70:fd:0b:7b
[  161.196729] wlan0: authenticate with AP 00:1a:70:fd:0b:7b
[  161.302558] wlan0: authenticate with AP 00:1a:70:fd:0b:7b
[  161.408294] wlan0: authentication with AP 00:1a:70:fd:0b:7b timed out
[  162.321923] wlan0: authentication frame received from 00:1a:70:fd:0b:7b, but not in authenticate state - ignored
[  164.801008] wlan0: authentication frame received from 00:1a:70:fd:0b:7b, but not in authenticate state - ignored
[  166.548133] wlan0: Initial auth_alg=0
[  166.548143] wlan0: authenticate with AP 00:1a:70:fd:0b:7b
[  166.550655] wlan0: Initial auth_alg=0
[  166.550666] wlan0: authenticate with AP 00:1a:70:fd:0b:7b
[  166.673579] wlan0: authenticate with AP 00:1a:70:fd:0b:7b
[  166.744266] wlan0: authenticate with AP 00:1a:70:fd:0b:7b
[  166.827020] wlan0: authentication with AP 00:1a:70:fd:0b:7b timed out
[  170.126822] wlan0: Initial auth_alg=0
[  170.126832] wlan0: authenticate with AP 00:1a:70:fd:0b:7b
[  170.129957] wlan0: Initial auth_alg=0
[  170.129964] wlan0: authenticate with AP 00:1a:70:fd:0b:7b
[  170.207603] wlan0: authenticate with AP 00:1a:70:fd:0b:7b
[  170.238274] wlan0: authenticate with AP 00:1a:70:fd:0b:7b
[  170.254858] wlan0: authentication with AP 00:1a:70:fd:0b:7b timed out
[  174.560599] wlan0: authentication frame received from 00:1a:70:fd:0b:7b, but not in authenticate state - ignored
[  174.560614] wlan0: authentication frame received from 00:1a:70:fd:0b:7b, but not in authenticate state - ignored
[  174.562929] wlan0: Initial auth_alg=0
[  174.562940] wlan0: authenticate with AP 00:1a:70:fd:0b:7b
[  174.565023] wlan0: Initial auth_alg=0
[  174.565033] wlan0: authenticate with AP 00:1a:70:fd:0b:7b
[  174.567451] wlan0: Initial auth_alg=0
[  174.567461] wlan0: authenticate with AP 00:1a:70:fd:0b:7b
[  174.673843] wlan0: authenticate with AP 00:1a:70:fd:0b:7b
[  174.800443] wlan0: authenticate with AP 00:1a:70:fd:0b:7b
[  174.860081] wlan0: authentication with AP 00:1a:70:fd:0b:7b timed out
[  175.013644] wlan0: authentication frame received from 00:1a:70:fd:0b:7b, but not in authenticate state - ignored
[  175.050872] wlan0: authentication frame received from 00:1a:70:fd:0b:7b, but not in authenticate state - ignored
[  175.175906] wlan0: authentication frame received from 00:1a:70:fd:0b:7b, but not in authenticate state - ignored
[  175.176769] wlan0: authentication frame received from 00:1a:70:fd:0b:7b, but not in authenticate state - ignored
[  176.558771] wlan0: authentication frame received from 00:1a:70:fd:0b:7b, but not in authenticate state - ignored
[  176.559672] wlan0: authentication frame received from 00:1a:70:fd:0b:7b, but not in authenticate state - ignored
[  176.560588] wlan0: authentication frame received from 00:1a:70:fd:0b:7b, but not in authenticate state - ignored
[  176.561473] wlan0: authentication frame received from 00:1a:70:fd:0b:7b, but not in authenticate state - ignored
[  176.562384] wlan0: authentication frame received from 00:1a:70:fd:0b:7b, but not in authenticate state - ignored
[  176.563373] wlan0: authentication frame received from 00:1a:70:fd:0b:7b, but not in authenticate state - ignored
[  176.564245] wlan0: authentication frame received from 00:1a:70:fd:0b:7b, but not in authenticate state - ignored
[  176.565140] wlan0: authentication frame received from 00:1a:70:fd:0b:7b, but not in authenticate state - ignored
[  176.566088] wlan0: authentication frame received from 00:1a:70:fd:0b:7b, but not in authenticate state - ignored
[  176.567343] wlan0: association frame received from 00:1a:70:fd:0b:7b, but not in associate state - ignored
[  176.568561] wlan0: association frame received from 00:1a:70:fd:0b:7b, but not in associate state - ignored
[  176.570091] wlan0: RX deauthentication from 00:1a:70:fd:0b:7b (reason=15)
[  176.570096] wlan0: deauthenticated
[  176.571000] wlan0: authentication frame received from 00:1a:70:fd:0b:7b, but not in authenticate state - ignored
[  176.571895] wlan0: authentication frame received from 00:1a:70:fd:0b:7b, but not in authenticate state - ignored
[  176.572775] wlan0: authentication frame received from 00:1a:70:fd:0b:7b, but not in authenticate state - ignored
[  176.574607] wlan0: authentication frame received from 00:1a:70:fd:0b:7b, but not in authenticate state - ignored
[  176.575520] wlan0: authentication frame received from 00:1a:70:fd:0b:7b, but not in authenticate state - ignored
[  176.576416] wlan0: authentication frame received from 00:1a:70:fd:0b:7b, but not in authenticate state - ignored
[  176.577296] wlan0: authentication frame received from 00:1a:70:fd:0b:7b, but not in authenticate state - ignored
[  176.578209] wlan0: authentication frame received from 00:1a:70:fd:0b:7b, but not in authenticate state - ignored
[  176.579102] wlan0: authentication frame received from 00:1a:70:fd:0b:7b, but not in authenticate state - ignored
[  176.580917] wlan0: authentication frame received from 00:1a:70:fd:0b:7b, but not in authenticate state - ignored
[  176.581442] wlan0: authentication frame received from 00:1a:70:fd:0b:7b, but not in authenticate state - ignored
[  176.582248] wlan0: authentication frame received from 00:1a:70:fd:0b:7b, but not in authenticate state - ignored
[  176.583114] wlan0: authentication frame received from 00:1a:70:fd:0b:7b, but not in authenticate state - ignored
[  176.584925] wlan0: authentication frame received from 00:1a:70:fd:0b:7b, but not in authenticate state - ignored
[  176.585815] wlan0: authentication frame received from 00:1a:70:fd:0b:7b, but not in authenticate state - ignored
[  178.990984] wlan0: RX deauthentication from 00:1a:70:fd:0b:7b (reason=7)
[  178.990996] wlan0: RX deauthentication from 00:1a:70:fd:0b:7b (reason=7)
[  178.991003] wlan0: RX deauthentication from 00:1a:70:fd:0b:7b (reason=7)
[  178.991009] wlan0: RX deauthentication from 00:1a:70:fd:0b:7b (reason=7)
[  178.991015] wlan0: RX deauthentication from 00:1a:70:fd:0b:7b (reason=7)
[  178.991021] wlan0: RX deauthentication from 00:1a:70:fd:0b:7b (reason=7)
[  178.991027] wlan0: RX deauthentication from 00:1a:70:fd:0b:7b (reason=7)
[  178.991033] wlan0: RX deauthentication from 00:1a:70:fd:0b:7b (reason=7)
[  178.991038] wlan0: RX deauthentication from 00:1a:70:fd:0b:7b (reason=7)
[  178.991044] wlan0: RX deauthentication from 00:1a:70:fd:0b:7b (reason=7)
[  178.991050] wlan0: RX deauthentication from 00:1a:70:fd:0b:7b (reason=7)
[  178.991056] wlan0: RX deauthentication from 00:1a:70:fd:0b:7b (reason=7)
[  178.991061] wlan0: RX deauthentication from 00:1a:70:fd:0b:7b (reason=7)
[  178.991067] wlan0: RX deauthentication from 00:1a:70:fd:0b:7b (reason=7)
[  178.991073] wlan0: RX deauthentication from 00:1a:70:fd:0b:7b (reason=7)
[  178.991078] wlan0: RX deauthentication from 00:1a:70:fd:0b:7b (reason=7)
[  178.991084] wlan0: RX deauthentication from 00:1a:70:fd:0b:7b (reason=7)
[  178.991089] wlan0: RX deauthentication from 00:1a:70:fd:0b:7b (reason=7)
[  178.991095] wlan0: RX deauthentication from 00:1a:70:fd:0b:7b (reason=7)
[  178.991101] wlan0: RX deauthentication from 00:1a:70:fd:0b:7b (reason=7)
[  178.994307] wlan0: Initial auth_alg=0
[  178.994313] wlan0: authenticate with AP 00:1a:70:fd:0b:7b
[  178.996773] wlan0: Initial auth_alg=0
[  178.996784] wlan0: authenticate with AP 00:1a:70:fd:0b:7b
[  178.996810] wlan0: RX authentication from 00:1a:70:fd:0b:7b (alg=0 transaction=2 status=0)
[  178.996814] wlan0: authenticated
[  178.996818] wlan0: associate with AP 00:1a:70:fd:0b:7b
[  178.996835] wlan0: authentication frame received from 00:1a:70:fd:0b:7b, but not in authenticate state - ignored
[  179.000211] wlan0: authentication frame received from 00:1a:70:fd:0b:7b, but not in authenticate state - ignored
[  179.001381] wlan0: RX AssocResp from 00:1a:70:fd:0b:7b (capab=0x411 status=0 aid=1)
[  179.001387] wlan0: associated
[  179.001504] wlan0: WMM queue=2 aci=0 acm=0 aifs=3 cWmin=15 cWmax=1023 burst=0
[  179.001510] wlan0: WMM queue=3 aci=1 acm=0 aifs=7 cWmin=15 cWmax=1023 burst=0
[  179.001514] wlan0: WMM queue=1 aci=2 acm=0 aifs=2 cWmin=7 cWmax=15 burst=30
[  179.001519] wlan0: WMM queue=0 aci=3 acm=0 aifs=2 cWmin=3 cWmax=7 burst=15
[  179.006710] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  186.130361] wlan0: no IPv6 routers present
[  366.064594] wlan0: No ProbeResp from current AP 00:1a:70:fd:0b:7b - assume out of range
[  369.642147] wlan0: No STA entry for own AP 00:1a:70:fd:0b:7b
[  369.645561] wlan0: Initial auth_alg=0
[  369.645575] wlan0: authenticate with AP 00:1a:70:fd:0b:7b
[  369.647416] wlan0: Initial auth_alg=0
[  369.647428] wlan0: authenticate with AP 00:1a:70:fd:0b:7b
[  369.766136] wlan0: authenticate with AP 00:1a:70:fd:0b:7b
[  369.846312] wlan0: authenticate with AP 00:1a:70:fd:0b:7b
[  369.934182] wlan0: authentication with AP 00:1a:70:fd:0b:7b timed out
[  370.564269] wlan0: authentication frame received from 00:1a:70:fd:0b:7b, but not in authenticate state - ignored
[  371.648229] wlan0: authentication frame received from 00:1a:70:fd:0b:7b, but not in authenticate state - ignored
[  375.096397] wlan0: authentication frame received from 00:1a:70:fd:0b:7b, but not in authenticate state - ignored
[  375.099016] wlan0: Initial auth_alg=0
[  375.099028] wlan0: authenticate with AP 00:1a:70:fd:0b:7b
[  375.101783] wlan0: Initial auth_alg=0
[  375.101794] wlan0: authenticate with AP 00:1a:70:fd:0b:7b
[  375.199132] wlan0: authenticate with AP 00:1a:70:fd:0b:7b
[  375.271473] wlan0: authenticate with AP 00:1a:70:fd:0b:7b
[  375.353706] wlan0: authentication with AP 00:1a:70:fd:0b:7b timed out
[  378.323269] wlan0: authentication frame received from 00:1a:70:fd:0b:7b, but not in authenticate state - ignored
[  378.327689] wlan0: Initial auth_alg=0
[  378.327698] wlan0: authenticate with AP 00:1a:70:fd:0b:7b
[  378.329746] wlan0: Initial auth_alg=0
[  378.329755] wlan0: authenticate with AP 00:1a:70:fd:0b:7b
[  378.329784] wlan0: RX authentication from 00:1a:70:fd:0b:7b (alg=0 transaction=2 status=0)
[  378.329788] wlan0: authenticated
[  378.329792] wlan0: associate with AP 00:1a:70:fd:0b:7b
[  378.331628] wlan0: authentication frame received from 00:1a:70:fd:0b:7b, but not in authenticate state - ignored
[  378.340574] wlan0: RX AssocResp from 00:1a:70:fd:0b:7b (capab=0x411 status=0 aid=1)
[  378.340583] wlan0: associated
[  378.340696] wlan0: WMM queue=2 aci=0 acm=0 aifs=3 cWmin=15 cWmax=1023 burst=0
[  378.340702] wlan0: WMM queue=3 aci=1 acm=0 aifs=7 cWmin=15 cWmax=1023 burst=0
[  378.340706] wlan0: WMM queue=1 aci=2 acm=0 aifs=2 cWmin=7 cWmax=15 burst=30
[  378.340711] wlan0: WMM queue=0 aci=3 acm=0 aifs=2 cWmin=3 cWmax=7 burst=15
[  378.345904] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  389.068333] wlan0: no IPv6 routers present
[  486.307241] wlan0: No ProbeResp from current AP 00:1a:70:fd:0b:7b - assume out of range
[  489.160785] wlan0: Initial auth_alg=0
[  489.160799] wlan0: authenticate with AP 00:1a:70:fd:0b:7b
[  489.162761] wlan0: RX authentication from 00:1a:70:fd:0b:7b (alg=0 transaction=2 status=0)
[  489.162767] wlan0: authenticated
[  489.162771] wlan0: associate with AP 00:1a:70:fd:0b:7b
[  489.167837] wlan0: Initial auth_alg=0
[  489.167847] wlan0: authenticate with AP 00:1a:70:fd:0b:7b
[  489.167904] wlan0: RX authentication from 00:1a:70:fd:0b:7b (alg=0 transaction=2 status=0)
[  489.167907] wlan0: authenticated
[  489.167911] wlan0: associate with AP 00:1a:70:fd:0b:7b
[  489.168519] wlan0: RX ReassocResp from 00:1a:70:fd:0b:7b (capab=0x411 status=0 aid=1)
[  489.168525] wlan0: associated
[  489.168637] wlan0: WMM queue=2 aci=0 acm=0 aifs=3 cWmin=15 cWmax=1023 burst=0
[  489.184988] wlan0: WMM queue=3 aci=1 acm=0 aifs=7 cWmin=15 cWmax=1023 burst=0
[  489.185598] wlan0: WMM queue=1 aci=2 acm=0 aifs=2 cWmin=7 cWmax=15 burst=30
[  489.186204] wlan0: WMM queue=0 aci=3 acm=0 aifs=2 cWmin=3 cWmax=7 burst=15
[  545.085025] wlan0: CTS protection enabled (BSSID=00:1a:70:fd:0b:7b)
[  545.969488] wlan0: CTS protection disabled (BSSID=00:1a:70:fd:0b:7b)
[  641.695221] npviewer.bin[12275]: segfault at 74731400 rip 74731400 rsp ffdfc78c error 14
[  641.766236] [UFW BLOCK INPUT]: IN=wlan0 OUT= MAC=00:1d:e0:50:46:ed:00:1a:70:fd:0b:79:08:00 SRC=209.47.169.13 DST=192.168.1.2 LEN=52 TOS=0x00 PREC=0x00 TTL=45 ID=11934 PROTO=TCP SPT=80 DPT=49456 WINDOW=65535 RES=0x00 ACK URGP=0 
[ 1102.995861] wlan0: No ProbeResp from current AP 00:1a:70:fd:0b:7b - assume out of range
[ 1105.526456] wlan0: No STA entry for own AP 00:1a:70:fd:0b:7b
[ 1105.532129] wlan0: Initial auth_alg=0
[ 1105.532139] wlan0: authenticate with AP 00:1a:70:fd:0b:7b
[ 1105.535280] wlan0: Initial auth_alg=0
[ 1105.535286] wlan0: authenticate with AP 00:1a:70:fd:0b:7b
[ 1105.537190] wlan0: RX authentication from 00:1a:70:fd:0b:7b (alg=0 transaction=2 status=0)
[ 1105.537196] wlan0: authenticated
[ 1105.537199] wlan0: associate with AP 00:1a:70:fd:0b:7b
[ 1105.538123] wlan0: authentication frame received from 00:1a:70:fd:0b:7b, but not in authenticate state - ignored
[ 1105.541450] wlan0: RX ReassocResp from 00:1a:70:fd:0b:7b (capab=0x411 status=0 aid=1)
[ 1105.541458] wlan0: associated
[ 1105.541572] wlan0: WMM queue=2 aci=0 acm=0 aifs=3 cWmin=15 cWmax=1023 burst=0
[ 1105.541577] wlan0: WMM queue=3 aci=1 acm=0 aifs=7 cWmin=15 cWmax=1023 burst=0
[ 1105.541582] wlan0: WMM queue=1 aci=2 acm=0 aifs=2 cWmin=7 cWmax=15 burst=30
[ 1105.541586] wlan0: WMM queue=0 aci=3 acm=0 aifs=2 cWmin=3 cWmax=7 burst=15
[ 1108.822592] wlan0: No ProbeResp from current AP 00:1a:70:fd:0b:7b - assume out of range
[ 1111.279072] wlan0: No STA entry for own AP 00:1a:70:fd:0b:7b
[ 1111.283748] wlan0: Initial auth_alg=0
[ 1111.283763] wlan0: authenticate with AP 00:1a:70:fd:0b:7b
[ 1111.285982] wlan0: Initial auth_alg=0
[ 1111.285993] wlan0: authenticate with AP 00:1a:70:fd:0b:7b
[ 1111.343235] wlan0: authenticate with AP 00:1a:70:fd:0b:7b
[ 1111.409572] wlan0: authenticate with AP 00:1a:70:fd:0b:7b
[ 1111.495387] wlan0: authentication with AP 00:1a:70:fd:0b:7b timed out
[ 1113.930268] wlan0: authentication frame received from 00:1a:70:fd:0b:7b, but not in authenticate state - ignored
[ 1115.296800] wlan0: Initial auth_alg=0
[ 1115.296812] wlan0: authenticate with AP 00:1a:70:fd:0b:7b
[ 1115.299586] wlan0: Initial auth_alg=0
[ 1115.299595] wlan0: authenticate with AP 00:1a:70:fd:0b:7b
[ 1115.373457] wlan0: authenticate with AP 00:1a:70:fd:0b:7b
[ 1115.487936] wlan0: authenticate with AP 00:1a:70:fd:0b:7b
[ 1115.546454] wlan0: authentication with AP 00:1a:70:fd:0b:7b timed out
[ 1117.774894] wlan0: authentication frame received from 00:1a:70:fd:0b:7b, but not in authenticate state - ignored
[ 1117.778251] wlan0: Initial auth_alg=0
[ 1117.778261] wlan0: authenticate with AP 00:1a:70:fd:0b:7b
[ 1117.780570] wlan0: Initial auth_alg=0
[ 1117.780580] wlan0: authenticate with AP 00:1a:70:fd:0b:7b
[ 1117.782911] wlan0: Initial auth_alg=0
[ 1117.782921] wlan0: authenticate with AP 00:1a:70:fd:0b:7b
[ 1117.864455] wlan0: authenticate with AP 00:1a:70:fd:0b:7b
[ 1117.985151] wlan0: authenticate with AP 00:1a:70:fd:0b:7b
[ 1118.078348] wlan0: authentication with AP 00:1a:70:fd:0b:7b timed out
[ 1122.999732] wlan0: Initial auth_alg=0
[ 1122.999742] wlan0: authenticate with AP 00:1a:70:fd:0b:7b
[ 1123.002067] wlan0: Initial auth_alg=0
[ 1123.002076] wlan0: authenticate with AP 00:1a:70:fd:0b:7b
[ 1123.100625] wlan0: authenticate with AP 00:1a:70:fd:0b:7b
[ 1123.172975] wlan0: authenticate with AP 00:1a:70:fd:0b:7b
[ 1123.248971] wlan0: authentication with AP 00:1a:70:fd:0b:7b timed out
[ 1126.477839] wlan0: authentication frame received from 00:1a:70:fd:0b:7b, but not in authenticate state - ignored
[ 1128.608723] wlan0: Initial auth_alg=0
[ 1128.608732] wlan0: authenticate with AP 00:1a:70:fd:0b:7b
[ 1128.611888] wlan0: Initial auth_alg=0
[ 1128.611893] wlan0: authenticate with AP 00:1a:70:fd:0b:7b
[ 1128.790439] wlan0: authenticate with AP 00:1a:70:fd:0b:7b
[ 1128.990280] wlan0: authenticate with AP 00:1a:70:fd:0b:7b
[ 1129.190103] wlan0: authentication with AP 00:1a:70:fd:0b:7b timed out
[ 1135.752338] wlan0: authentication frame received from 00:1a:70:fd:0b:7b, but not in authenticate state - ignored
[ 1135.754831] wlan0: Initial auth_alg=0
[ 1135.754842] wlan0: authenticate with AP 00:1a:70:fd:0b:7b
[ 1135.757630] wlan0: Initial auth_alg=0
[ 1135.757640] wlan0: authenticate with AP 00:1a:70:fd:0b:7b
[ 1135.759655] wlan0: Initial auth_alg=0
[ 1135.759666] wlan0: authenticate with AP 00:1a:70:fd:0b:7b
[ 1135.763008] wlan0: Initial auth_alg=0
[ 1135.763017] wlan0: authenticate with AP 00:1a:70:fd:0b:7b
[ 1135.842082] wlan0: authenticate with AP 00:1a:70:fd:0b:7b
[ 1135.962680] wlan0: authenticate with AP 00:1a:70:fd:0b:7b
[ 1136.162479] wlan0: authentication with AP 00:1a:70:fd:0b:7b timed out
[ 1136.462299] wlan0: authentication frame received from 00:1a:70:fd:0b:7b, but not in authenticate state - ignored
[ 1143.554797] wlan0: Initial auth_alg=0
[ 1143.554806] wlan0: authenticate with AP 00:1a:70:fd:0b:7b
[ 1143.560664] wlan0: Initial auth_alg=0
[ 1143.560672] wlan0: authenticate with AP 00:1a:70:fd:0b:7b
[ 1143.760683] wlan0: authenticate with AP 00:1a:70:fd:0b:7b
[ 1143.960516] wlan0: authenticate with AP 00:1a:70:fd:0b:7b
[ 1144.167346] wlan0: authentication with AP 00:1a:70:fd:0b:7b timed out
[ 1148.441128] wlan0: authentication frame received from 00:1a:70:fd:0b:7b, but not in authenticate state - ignored
[ 1148.444082] wlan0: authentication frame received from 00:1a:70:fd:0b:7b, but not in authenticate state - ignored
[ 1148.446912] wlan0: authentication frame received from 00:1a:70:fd:0b:7b, but not in authenticate state - ignored
[ 1150.218671] wlan0: Initial auth_alg=0
[ 1150.218683] wlan0: authenticate with AP 00:1a:70:fd:0b:7b
[ 1150.280281] wlan0: authenticate with AP 00:1a:70:fd:0b:7b
[ 1150.357501] wlan0: authenticate with AP 00:1a:70:fd:0b:7b
[ 1150.440459] wlan0: authentication with AP 00:1a:70:fd:0b:7b timed out
[ 1153.665352] wlan0: authentication frame received from 00:1a:70:fd:0b:7b, but not in authenticate state - ignored
[ 1154.720064] wlan0: authentication frame received from 00:1a:70:fd:0b:7b, but not in authenticate state - ignored
[ 1154.720075] wlan0: authentication frame received from 00:1a:70:fd:0b:7b, but not in authenticate state - ignored
[ 1154.720082] wlan0: authentication frame received from 00:1a:70:fd:0b:7b, but not in authenticate state - ignored
[ 1157.100063] wlan0: authentication frame received from 00:1a:70:fd:0b:7b, but not in authenticate state - ignored
[ 1159.268439] wlan0: authentication frame received from 00:1a:70:fd:0b:7b, but not in authenticate state - ignored
[ 1161.539066] wlan0: authentication frame received from 00:1a:70:fd:0b:7b, but not in authenticate state - ignored
[ 1163.727185] wlan0: authentication frame received from 00:1a:70:fd:0b:7b, but not in authenticate state - ignored
[ 1163.727213] wlan0: authentication frame received from 00:1a:70:fd:0b:7b, but not in authenticate state - ignored
[ 1165.908670] wlan0: authentication frame received from 00:1a:70:fd:0b:7b, but not in authenticate state - ignored
[ 1168.088481] wlan0: authentication frame received from 00:1a:70:fd:0b:7b, but not in authenticate state - ignored
[ 1168.220680] wlan0: authentication frame received from 00:1a:70:fd:0b:7b, but not in authenticate state - ignored
[ 1170.546430] wlan0: authentication frame received from 00:1a:70:fd:0b:7b, but not in authenticate state - ignored
[ 1171.341493] wlan0: authentication frame received from 00:1a:70:fd:0b:7b, but not in authenticate state - ignored
[ 1172.829694] wlan0: authentication frame received from 00:1a:70:fd:0b:7b, but not in authenticate state - ignored
[ 1180.321199] wlan0: authentication frame received from 00:1a:70:fd:0b:7b, but not in authenticate state - ignored
[ 1181.981160] wlan0: authentication frame received from 00:1a:70:fd:0b:7b, but not in authenticate state - ignored
[ 1182.489653] wlan0: authentication frame received from 00:1a:70:fd:0b:7b, but not in authenticate state - ignored
[ 1183.438820] wlan0: authentication frame received from 00:1a:70:fd:0b:7b, but not in authenticate state - ignored
[ 1191.395542] wlan0: authentication frame received from 00:1a:70:fd:0b:7b, but not in authenticate state - ignored
[ 1196.370373] wlan0: authentication frame received from 00:1a:70:fd:0b:7b, but not in authenticate state - ignored
[ 1201.232536] wlan0: authentication frame received from 00:1a:70:fd:0b:7b, but not in authenticate state - ignored
[ 1201.403096] wlan0: authentication frame received from 00:1a:70:fd:0b:7b, but not in authenticate state - ignored
[ 1201.532171] wlan0: authentication frame received from 00:1a:70:fd:0b:7b, but not in authenticate state - ignored
[ 1201.583431] wlan0: authentication frame received from 00:1a:70:fd:0b:7b, but not in authenticate state - ignored
[ 1202.365616] wlan0: authentication frame received from 00:1a:70:fd:0b:7b, but not in authenticate state - ignored
[ 1202.487379] wlan0: authentication frame received from 00:1a:70:fd:0b:7b, but not in authenticate state - ignored

```

---

### Post by pytheas22 on 2008-07-10
Sorry to hear it's breaking again.

There are several problems recorded in dmesg.  Lines like these are definitely related to the problem:
```

wlan0: No ProbeResp from current AP 00:1a:70:fd:0b:7b - assume out of range
wlan0: authentication frame received from 00:1a:70:fd:0b:7b, but not in authenticate state - ignored
```

It seems like your card thinks that it's moved out of range of your router, even though it presumably hasn't, and drops the connection as a result.  This seems to be happening reliably at fixed time intervals.

Lines like these that appear in the first dmesg are also interesting, although I'm not sure whether they're related to what's going on in the second dmesg:
```

wlan0: RX deauthentication from 00:1a:70:fd:0b:7b (reason=15)
```

There, it looks like your router is intentionally disconnecting you for some reason that I can't determine.  When it tries to reauthenticate you again, it fails with an error message like:
```

wlan0: authentication frame received from 00:1a:70:fd:0b:7b, but not in authenticate state - ignored
```

which makes it sound like your card doesn't think it should be reconnecting (aka reauthenticating) even though it knows it just got disconnected.  I think what we've got here is a failure to communicate.

As far as solutions, I googled for a while but couldn't find anything concrete.  There are a few things to try, however.  First, apply all of the updates.  Enabling the hardy-proposed repository will get you the very latest bug fixes (at the risk of downloading potentially unstable software as well, but the risk is low).  This problem is mostly likely a bug with your driver or firmware that should be fixed by an update.

If that doesn't help, try running these first thing commands after a fresh reboot of your computer:

```

sudo rmmod iwl4965
sudo modprobe iwl4965
```

There were a couple people who suggested that doing that may prevent the instability.  If it does, we can apply that fix permanently.

If that still doesn't help, you can use ndiswrapper (a utility to drive your card with Windows drivers instead of the native Linux iwl4965 driver), but hopefully that will be unnecessary.

My biggest suspicion after all of this, though, is that it's just a bug in the firmware that should be fixed by an update (and which was possibly also introduced by an update, which seems to happen too often with wireless cards).

---

### Post by Daelyn on 2008-07-11
> **LeoSolaris said:**
> This is a strange issue, because it worked perfectly fine before I moved...

After getting DSL in my new apartment, I connected everything and I have a line that works when I plug in my laptop, but when I switch over to using my Linksys WRT300N (v1.1 with current firmware upgrade) My laptop will only intermittently connect. My wireless card is the Intel Wireless N in a Dell 1520.

I am pretty sure it is something in a recent update in Ubuntu, because there is no issue in Windows.

There are a lot more signals here, maybe it is getting confused?

Leo


Try checking the following out.[http://ubuntuforums.org/showthread.php?t=764886](http://ubuntuforums.org/showthread.php?t=764886)

Maybe it helps? It's worth a shot :)

---

### Post by LeoSolaris on 2008-07-11
Thanks guys! (or gals, ya never know if on here really) After a lot of poking at it to make sure it wasn't damaged in the move (one of the antenna was loose) I accidentally discovered that if I moved what it was sitting on over just a bit it could project around some boxes that were set in the way. (it didn't have clear line of sight, but it was by no means buried either)

Add to that bit of renegotiation of space, I also applied a new update last night. With a restart, that seems to work better as well.

Daelyn: I'll have to look over what you put up more carefully, as the double encryption idea looks intriguing. 

Thank you both, and I think it was something in both the update and the cardboard that contributed to this one. It's stable for now, but I will report back in a day or two on it. Of course if it breaks I'll be back sooner ;)

Leo

---

### Post by LeoSolaris on 2008-07-13
Alright, the dropping issue is still there.

It isn't as bad in Windows, but still happens.

Just today Ubuntu started dropping at the first attempt at activity after it "connected" with a 100% signal. It drops to a 0% signal, then drops the connection.

Here's the dmesg:
```

[  424.762062] wlan0: RX authentication from 00:1a:70:fd:0b:7b (alg=0 transaction=2 status=0)
[  424.762070] wlan0: authenticated
[  424.762074] wlan0: associate with AP 00:1a:70:fd:0b:7b
[  424.777634] wlan0: RX ReassocResp from 00:1a:70:fd:0b:7b (capab=0x411 status=0 aid=1)
[  424.777644] wlan0: associated
[  424.777723] wlan0: WMM queue=2 aci=0 acm=0 aifs=3 cWmin=15 cWmax=1023 burst=0
[  424.777728] wlan0: WMM queue=3 aci=1 acm=0 aifs=7 cWmin=15 cWmax=1023 burst=0
[  424.777733] wlan0: WMM queue=1 aci=2 acm=0 aifs=2 cWmin=7 cWmax=15 burst=30
[  424.777738] wlan0: WMM queue=0 aci=3 acm=0 aifs=2 cWmin=3 cWmax=7 burst=15
[  429.015738] wlan0: No ProbeResp from current AP 00:1a:70:fd:0b:7b - assume out of range
[  429.336806] wlan0: no IPv6 routers present
[  429.858841] wlan0: No STA entry for own AP 00:1a:70:fd:0b:7b
[  432.036282] wlan0: Initial auth_alg=0
[  432.036295] wlan0: authenticate with AP 00:1a:70:fd:0b:7b
[  432.038650] wlan0: Initial auth_alg=0
[  432.038661] wlan0: authenticate with AP 00:1a:70:fd:0b:7b
[  432.060263] wlan0: authenticate with AP 00:1a:70:fd:0b:7b
[  432.078810] wlan0: authenticate with AP 00:1a:70:fd:0b:7b
[  432.093760] wlan0: RX authentication from 00:1a:70:fd:0b:7b (alg=0 transaction=2 status=0)
[  432.093768] wlan0: authenticated
[  432.093772] wlan0: associate with AP 00:1a:70:fd:0b:7b
[  432.281240] wlan0: associate with AP 00:1a:70:fd:0b:7b
[  432.296876] wlan0: associate with AP 00:1a:70:fd:0b:7b
[  432.306868] wlan0: authentication frame received from 00:1a:70:fd:0b:7b, but not in authenticate state - ignored
[  432.359728] wlan0: authentication frame received from 00:1a:70:fd:0b:7b, but not in authenticate state - ignored
[  432.417864] wlan0: association with AP 00:1a:70:fd:0b:7b timed out
[  432.518296] wlan0: authentication frame received from 00:1a:70:fd:0b:7b, but not in authenticate state - ignored
[  432.636229] wlan0: association frame received from 00:1a:70:fd:0b:7b, but not in associate state - ignored
[  432.641881] wlan0: association frame received from 00:1a:70:fd:0b:7b, but not in associate state - ignored
[  432.706086] wlan0: association frame received from 00:1a:70:fd:0b:7b, but not in associate state - ignored
[  432.810817] wlan0: association frame received from 00:1a:70:fd:0b:7b, but not in associate state - ignored
[  432.933274] wlan0: association frame received from 00:1a:70:fd:0b:7b, but not in associate state - ignored
[  432.953237] wlan0: association frame received from 00:1a:70:fd:0b:7b, but not in associate state - ignored
[  433.004015] wlan0: association frame received from 00:1a:70:fd:0b:7b, but not in associate state - ignored
[  433.435527] wlan0: association frame received from 00:1a:70:fd:0b:7b, but not in associate state - ignored
[  433.444530] wlan0: Initial auth_alg=0
[  433.444541] wlan0: authenticate with AP 00:1a:70:fd:0b:7b
[  433.490426] wlan0: authenticate with AP 00:1a:70:fd:0b:7b
[  433.522541] wlan0: association frame received from 00:1a:70:fd:0b:7b, but not in associate state - ignored
[  433.524066] wlan0: authenticate with AP 00:1a:70:fd:0b:7b
[  433.692645] wlan0: association frame received from 00:1a:70:fd:0b:7b, but not in associate state - ignored
[  433.694214] wlan0: authentication with AP 00:1a:70:fd:0b:7b timed out
[  433.730006] wlan0: association frame received from 00:1a:70:fd:0b:7b, but not in associate state - ignored
[  433.775500] wlan0: association frame received from 00:1a:70:fd:0b:7b, but not in associate state - ignored
[  433.786798] wlan0: association frame received from 00:1a:70:fd:0b:7b, but not in associate state - ignored
[  433.867102] wlan0: association frame received from 00:1a:70:fd:0b:7b, but not in associate state - ignored
[  433.922873] wlan0: association frame received from 00:1a:70:fd:0b:7b, but not in associate state - ignored
[  433.929097] wlan0: authentication frame received from 00:1a:70:fd:0b:7b, but not in authenticate state - ignored
[  433.941950] wlan0: authentication frame received from 00:1a:70:fd:0b:7b, but not in authenticate state - ignored
[  433.992804] wlan0: authentication frame received from 00:1a:70:fd:0b:7b, but not in authenticate state - ignored
[  434.013201] wlan0: authentication frame received from 00:1a:70:fd:0b:7b, but not in authenticate state - ignored
[  434.079105] wlan0: authentication frame received from 00:1a:70:fd:0b:7b, but not in authenticate state - ignored
[  434.112358] wlan0: authentication frame received from 00:1a:70:fd:0b:7b, but not in authenticate state - ignored
[  434.188987] wlan0: Initial auth_alg=0
[  434.188997] wlan0: authenticate with AP 00:1a:70:fd:0b:7b
[  434.192149] wlan0: Initial auth_alg=0
[  434.192157] wlan0: authenticate with AP 00:1a:70:fd:0b:7b
[  434.214344] wlan0: RX authentication from 00:1a:70:fd:0b:7b (alg=0 transaction=2 status=0)
[  434.214352] wlan0: authenticated
[  434.214356] wlan0: associate with AP 00:1a:70:fd:0b:7b
[  434.261055] wlan0: associate with AP 00:1a:70:fd:0b:7b
[  434.278229] wlan0: authentication frame received from 00:1a:70:fd:0b:7b, but not in authenticate state - ignored
[  434.324546] wlan0: authentication frame received from 00:1a:70:fd:0b:7b, but not in authenticate state - ignored
[  434.360529] wlan0: associate with AP 00:1a:70:fd:0b:7b
[  434.492129] wlan0: association with AP 00:1a:70:fd:0b:7b timed out
[  434.639798] wlan0: authentication frame received from 00:1a:70:fd:0b:7b, but not in authenticate state - ignored
[  434.731993] wlan0: authentication frame received from 00:1a:70:fd:0b:7b, but not in authenticate state - ignored
[  434.800347] wlan0: authentication frame received from 00:1a:70:fd:0b:7b, but not in authenticate state - ignored
[  435.140032] wlan0: authentication frame received from 00:1a:70:fd:0b:7b, but not in authenticate state - ignored
[  435.256782] wlan0: authentication frame received from 00:1a:70:fd:0b:7b, but not in authenticate state - ignored
[  435.275713] wlan0: authentication frame received from 00:1a:70:fd:0b:7b, but not in authenticate state - ignored
[  435.540517] wlan0: authentication frame received from 00:1a:70:fd:0b:7b, but not in authenticate state - ignored
[  435.935041] wlan0: authentication frame received from 00:1a:70:fd:0b:7b, but not in authenticate state - ignored
[  436.038334] wlan0: authentication frame received from 00:1a:70:fd:0b:7b, but not in authenticate state - ignored
[  436.082724] wlan0: authentication frame received from 00:1a:70:fd:0b:7b, but not in authenticate state - ignored
[  436.147076] wlan0: authentication frame received from 00:1a:70:fd:0b:7b, but not in authenticate state - ignored
[  436.148292] wlan0: association frame received from 00:1a:70:fd:0b:7b, but not in associate state - ignored
[  436.237387] wlan0: association frame received from 00:1a:70:fd:0b:7b, but not in associate state - ignored
[  436.243910] wlan0: association frame received from 00:1a:70:fd:0b:7b, but not in associate state - ignored
[  436.437427] wlan0: association frame received from 00:1a:70:fd:0b:7b, but not in associate state - ignored
[  436.520363] wlan0: association frame received from 00:1a:70:fd:0b:7b, but not in associate state - ignored
[  437.043775] wlan0: association frame received from 00:1a:70:fd:0b:7b, but not in associate state - ignored
[  438.088201] wlan0: Initial auth_alg=0
[  438.088211] wlan0: authenticate with AP 00:1a:70:fd:0b:7b
[  438.130178] wlan0: RX authentication from 00:1a:70:fd:0b:7b (alg=0 transaction=2 status=0)
[  438.130184] wlan0: authenticated
[  438.130188] wlan0: associate with AP 00:1a:70:fd:0b:7b
[  438.175742] wlan0: authentication frame received from 00:1a:70:fd:0b:7b, but not in authenticate state - ignored
[  438.186685] wlan0: RX AssocResp from 00:1a:70:fd:0b:7b (capab=0x411 status=0 aid=1)
[  438.186695] wlan0: associated
[  438.186820] wlan0: WMM queue=2 aci=0 acm=0 aifs=3 cWmin=15 cWmax=1023 burst=0
[  438.192190] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  438.194715] wlan0: WMM queue=3 aci=1 acm=0 aifs=7 cWmin=15 cWmax=1023 burst=0
[  438.195318] wlan0: WMM queue=1 aci=2 acm=0 aifs=2 cWmin=7 cWmax=15 burst=30
[  438.195924] wlan0: WMM queue=0 aci=3 acm=0 aifs=2 cWmin=3 cWmax=7 burst=15
[  438.367080] wlan0: association frame received from 00:1a:70:fd:0b:7b, but not in associate state - ignored
[  439.464505] wlan0: Initial auth_alg=0
[  439.464518] wlan0: authenticate with AP 00:1a:70:fd:0b:7b
[  439.467387] wlan0: Initial auth_alg=0
[  439.467399] wlan0: authenticate with AP 00:1a:70:fd:0b:7b
[  439.538651] wlan0: RX authentication from 00:1a:70:fd:0b:7b (alg=0 transaction=2 status=0)
[  439.538660] wlan0: authenticated
[  439.538664] wlan0: associate with AP 00:1a:70:fd:0b:7b
[  439.734440] wlan0: associate with AP 00:1a:70:fd:0b:7b
[  439.805607] wlan0: RX ReassocResp from 00:1a:70:fd:0b:7b (capab=0x411 status=0 aid=1)
[  439.805614] wlan0: associated
[  439.805691] wlan0: WMM queue=2 aci=0 acm=0 aifs=3 cWmin=15 cWmax=1023 burst=0
[  439.813632] wlan0: WMM queue=3 aci=1 acm=0 aifs=7 cWmin=15 cWmax=1023 burst=0
[  439.814241] wlan0: WMM queue=1 aci=2 acm=0 aifs=2 cWmin=7 cWmax=15 burst=30
[  439.815474] wlan0: WMM queue=0 aci=3 acm=0 aifs=2 cWmin=3 cWmax=7 burst=15
[  439.816084] wlan0: association frame received from 00:1a:70:fd:0b:7b, but not in associate state - ignored
[  441.744366] wlan0: no IPv6 routers present
[  441.813109] wlan0: RX deauthentication from 00:1a:70:fd:0b:7b (reason=15)
[  441.813119] wlan0: deauthenticated
[  442.047171] wlan0: authenticate with AP 00:1a:70:fd:0b:7b
[  442.049259] wlan0: RX authentication from 00:1a:70:fd:0b:7b (alg=0 transaction=2 status=0)
[  442.049268] wlan0: authenticated
[  442.049272] wlan0: associate with AP 00:1a:70:fd:0b:7b
[  442.052494] wlan0: RX ReassocResp from 00:1a:70:fd:0b:7b (capab=0x411 status=0 aid=1)
[  442.052502] wlan0: associated
[  447.920509] wlan0: no IPv6 routers present
[  455.492598] wlan0: No ProbeResp from current AP 00:1a:70:fd:0b:7b - assume out of range
[  456.381862] wlan0: No STA entry for own AP 00:1a:70:fd:0b:7b
[  456.385930] wlan0: Initial auth_alg=0
[  456.385946] wlan0: authenticate with AP 00:1a:70:fd:0b:7b
[  456.387826] wlan0: Initial auth_alg=0
[  456.387834] wlan0: authenticate with AP 00:1a:70:fd:0b:7b
[  456.398152] wlan0: RX authentication from 00:1a:70:fd:0b:7b (alg=0 transaction=2 status=0)
[  456.398160] wlan0: authenticated
[  456.398164] wlan0: associate with AP 00:1a:70:fd:0b:7b
[  456.432976] wlan0: authentication frame received from 00:1a:70:fd:0b:7b, but not in authenticate state - ignored
[  456.440773] wlan0: authentication frame received from 00:1a:70:fd:0b:7b, but not in authenticate state - ignored
[  456.447990] wlan0: associate with AP 00:1a:70:fd:0b:7b
[  456.459975] wlan0: authentication frame received from 00:1a:70:fd:0b:7b, but not in authenticate state - ignored
[  456.464768] wlan0: authentication frame received from 00:1a:70:fd:0b:7b, but not in authenticate state - ignored
[  456.470645] wlan0: RX ReassocResp from 00:1a:70:fd:0b:7b (capab=0x411 status=0 aid=1)
[  456.470652] wlan0: associated
[  456.470778] wlan0: WMM queue=2 aci=0 acm=0 aifs=3 cWmin=15 cWmax=1023 burst=0
[  456.480260] wlan0: WMM queue=3 aci=1 acm=0 aifs=7 cWmin=15 cWmax=1023 burst=0
[  456.480875] wlan0: WMM queue=1 aci=2 acm=0 aifs=2 cWmin=7 cWmax=15 burst=30
[  456.481497] wlan0: WMM queue=0 aci=3 acm=0 aifs=2 cWmin=3 cWmax=7 burst=15
[  456.488463] wlan0: association frame received from 00:1a:70:fd:0b:7b, but not in associate state - ignored
[  456.518439] wlan0: association frame received from 00:1a:70:fd:0b:7b, but not in associate state - ignored
[  457.893918] wlan0: No ProbeResp from current AP 00:1a:70:fd:0b:7b - assume out of range
[  461.937388] wlan0: RX deauthentication from 00:1a:70:fd:0b:7b (reason=15)
[  461.937395] wlan0: deauthenticated
[  461.937409] wlan0: RX deauthentication from 00:1a:70:fd:0b:7b (reason=15)
[  461.937415] wlan0: RX deauthentication from 00:1a:70:fd:0b:7b (reason=15)
[  461.937422] wlan0: RX deauthentication from 00:1a:70:fd:0b:7b (reason=7)
[  461.937427] wlan0: RX deauthentication from 00:1a:70:fd:0b:7b (reason=7)
[  461.937433] wlan0: RX deauthentication from 00:1a:70:fd:0b:7b (reason=7)
[  461.937439] wlan0: RX deauthentication from 00:1a:70:fd:0b:7b (reason=7)
[  461.937444] wlan0: RX deauthentication from 00:1a:70:fd:0b:7b (reason=7)
[  461.937450] wlan0: RX deauthentication from 00:1a:70:fd:0b:7b (reason=7)
[  461.937456] wlan0: RX deauthentication from 00:1a:70:fd:0b:7b (reason=7)
[  461.937462] wlan0: RX deauthentication from 00:1a:70:fd:0b:7b (reason=7)
[  461.937482] wlan0: RX deauthentication from 00:1a:70:fd:0b:7b (reason=7)
[  461.937487] wlan0: RX deauthentication from 00:1a:70:fd:0b:7b (reason=7)
[  461.937493] wlan0: RX deauthentication from 00:1a:70:fd:0b:7b (reason=7)
[  461.937499] wlan0: RX deauthentication from 00:1a:70:fd:0b:7b (reason=7)
[  461.937504] wlan0: RX deauthentication from 00:1a:70:fd:0b:7b (reason=7)
[  461.937510] wlan0: RX deauthentication from 00:1a:70:fd:0b:7b (reason=7)
[  461.941848] wlan0: Initial auth_alg=0
[  461.941857] wlan0: authenticate with AP 00:1a:70:fd:0b:7b
[  461.946525] wlan0: Initial auth_alg=0
[  461.946537] wlan0: authenticate with AP 00:1a:70:fd:0b:7b
[  461.963841] wlan0: RX authentication from 00:1a:70:fd:0b:7b (alg=0 transaction=2 status=0)
[  461.963850] wlan0: authenticated
[  461.963854] wlan0: associate with AP 00:1a:70:fd:0b:7b
[  462.010741] wlan0: RX ReassocResp from 00:1a:70:fd:0b:7b (capab=0x411 status=0 aid=1)
[  462.010749] wlan0: associated
[  462.010864] wlan0: WMM queue=2 aci=0 acm=0 aifs=3 cWmin=15 cWmax=1023 burst=0
[  462.018166] wlan0: WMM queue=3 aci=1 acm=0 aifs=7 cWmin=15 cWmax=1023 burst=0
[  462.018766] wlan0: WMM queue=1 aci=2 acm=0 aifs=2 cWmin=7 cWmax=15 burst=30
[  462.019360] wlan0: WMM queue=0 aci=3 acm=0 aifs=2 cWmin=3 cWmax=7 burst=15
[  462.970005] wlan0: Initial auth_alg=0
[  462.970020] wlan0: authenticate with AP 00:1a:70:fd:0b:7b
[  462.980457] wlan0: RX authentication from 00:1a:70:fd:0b:7b (alg=0 transaction=2 status=0)
[  462.980465] wlan0: authenticated
[  462.980469] wlan0: associate with AP 00:1a:70:fd:0b:7b
[  462.987906] wlan0: RX AssocResp from 00:1a:70:fd:0b:7b (capab=0x411 status=0 aid=1)
[  462.987913] wlan0: associated
[  462.987993] wlan0: WMM queue=2 aci=0 acm=0 aifs=3 cWmin=15 cWmax=1023 burst=0
[  462.993022] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  462.997799] wlan0: WMM queue=3 aci=1 acm=0 aifs=7 cWmin=15 cWmax=1023 burst=0
[  462.998418] wlan0: WMM queue=1 aci=2 acm=0 aifs=2 cWmin=7 cWmax=15 burst=30
[  462.999047] wlan0: WMM queue=0 aci=3 acm=0 aifs=2 cWmin=3 cWmax=7 burst=15
[  464.662100] wlan0: Initial auth_alg=0
[  464.662114] wlan0: authenticate with AP 00:1a:70:fd:0b:7b
[  464.664350] wlan0: Initial auth_alg=0
[  464.664360] wlan0: authenticate with AP 00:1a:70:fd:0b:7b
[  464.682341] wlan0: RX authentication from 00:1a:70:fd:0b:7b (alg=0 transaction=2 status=0)
[  464.682349] wlan0: authenticated
[  464.682353] wlan0: associate with AP 00:1a:70:fd:0b:7b
[  464.700879] wlan0: authentication frame received from 00:1a:70:fd:0b:7b, but not in authenticate state - ignored
[  464.702114] wlan0: RX ReassocResp from 00:1a:70:fd:0b:7b (capab=0x411 status=0 aid=1)
[  464.702121] wlan0: associated
[  464.702197] wlan0: WMM queue=2 aci=0 acm=0 aifs=3 cWmin=15 cWmax=1023 burst=0
[  464.714560] wlan0: WMM queue=3 aci=1 acm=0 aifs=7 cWmin=15 cWmax=1023 burst=0
[  464.715515] wlan0: WMM queue=1 aci=2 acm=0 aifs=2 cWmin=7 cWmax=15 burst=30
[  464.716109] wlan0: WMM queue=0 aci=3 acm=0 aifs=2 cWmin=3 cWmax=7 burst=15
[  467.351995] wlan0: no IPv6 routers present
[  467.770331] wlan0: RX deauthentication from 00:1a:70:fd:0b:7b (reason=15)
[  467.770339] wlan0: deauthenticated
[  468.214087] wlan0: authenticate with AP 00:1a:70:fd:0b:7b
[  468.215487] wlan0: RX authentication from 00:1a:70:fd:0b:7b (alg=0 transaction=2 status=0)
[  468.215496] wlan0: authenticated
[  468.215499] wlan0: associate with AP 00:1a:70:fd:0b:7b
[  468.217815] wlan0: RX ReassocResp from 00:1a:70:fd:0b:7b (capab=0x411 status=0 aid=1)
[  468.217824] wlan0: associated
[  479.860111] wlan0: no IPv6 routers present
[  482.454849] wlan0: No ProbeResp from current AP 00:1a:70:fd:0b:7b - assume out of range
[  486.692697] wlan0: No STA entry for own AP 00:1a:70:fd:0b:7b
[  490.997520] wlan0: No STA entry for own AP 00:1a:70:fd:0b:7b
[  491.003242] wlan0: Initial auth_alg=0
[  491.003252] wlan0: authenticate with AP 00:1a:70:fd:0b:7b
[  491.006390] wlan0: Initial auth_alg=0
[  491.006395] wlan0: authenticate with AP 00:1a:70:fd:0b:7b
[  491.100088] wlan0: authenticate with AP 00:1a:70:fd:0b:7b
[  491.106397] wlan0: RX authentication from 00:1a:70:fd:0b:7b (alg=0 transaction=2 status=0)
[  491.106405] wlan0: authenticated
[  491.106409] wlan0: associate with AP 00:1a:70:fd:0b:7b
[  491.138146] wlan0: authentication frame received from 00:1a:70:fd:0b:7b, but not in authenticate state - ignored
[  491.140665] wlan0: authentication frame received from 00:1a:70:fd:0b:7b, but not in authenticate state - ignored
[  491.141889] wlan0: RX ReassocResp from 00:1a:70:fd:0b:7b (capab=0x411 status=0 aid=1)
[  491.141895] wlan0: associated
[  491.142009] wlan0: WMM queue=2 aci=0 acm=0 aifs=3 cWmin=15 cWmax=1023 burst=0
[  491.151634] wlan0: WMM queue=3 aci=1 acm=0 aifs=7 cWmin=15 cWmax=1023 burst=0
[  491.152237] wlan0: WMM queue=1 aci=2 acm=0 aifs=2 cWmin=7 cWmax=15 burst=30
[  491.165706] wlan0: WMM queue=0 aci=3 acm=0 aifs=2 cWmin=3 cWmax=7 burst=15
[  491.166322] wlan0: association frame received from 00:1a:70:fd:0b:7b, but not in associate state - ignored
[  491.543329] wlan0: deauthenticate(reason=3)
[  492.466153] CPU0 attaching NULL sched-domain.
[  492.466167] CPU1 attaching NULL sched-domain.
[  492.492332] CPU0 attaching sched-domain:
[  492.492348]  domain 0: span 03
[  492.492354]   groups: 01 02
[  492.492362]   domain 1: span 03
[  492.492365]    groups: 03
[  492.492372]    domain 2: span 03
[  492.492378]     groups: 03
[  492.492382] CPU1 attaching sched-domain:
[  492.492388]  domain 0: span 03
[  492.492394]   groups: 02 01
[  492.492398]   domain 1: span 03
[  492.492404]    groups: 03
[  492.492410]    domain 2: span 03
[  492.492414]     groups: 03
[  496.110701] wlan0: RX deauthentication from 00:1a:70:fd:0b:7b (reason=7)
[  496.110711] wlan0: deauthenticated
[  496.110721] wlan0: RX deauthentication from 00:1a:70:fd:0b:7b (reason=7)
[  496.110730] wlan0: RX deauthentication from 00:1a:70:fd:0b:7b (reason=7)
[  496.110738] wlan0: RX deauthentication from 00:1a:70:fd:0b:7b (reason=7)
[  496.116049] wlan0: Initial auth_alg=0
[  496.116065] wlan0: authenticate with AP 00:1a:70:fd:0b:7b
[  496.117944] wlan0: Initial auth_alg=0
[  496.117960] wlan0: authenticate with AP 00:1a:70:fd:0b:7b
[  496.124971] wlan0: RX authentication from 00:1a:70:fd:0b:7b (alg=0 transaction=2 status=0)
[  496.124985] wlan0: authenticated
[  496.124992] wlan0: associate with AP 00:1a:70:fd:0b:7b
[  496.130065] wlan0: RX AssocResp from 00:1a:70:fd:0b:7b (capab=0x411 status=0 aid=1)
[  496.130076] wlan0: associated
[  496.130188] wlan0: WMM queue=2 aci=0 acm=0 aifs=3 cWmin=15 cWmax=1023 burst=0
[  496.137510] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  496.144842] wlan0: WMM queue=3 aci=1 acm=0 aifs=7 cWmin=15 cWmax=1023 burst=0
[  496.145471] wlan0: WMM queue=1 aci=2 acm=0 aifs=2 cWmin=7 cWmax=15 burst=30
[  496.146115] wlan0: WMM queue=0 aci=3 acm=0 aifs=2 cWmin=3 cWmax=7 burst=15
[  497.651752] wlan0: No ProbeResp from current AP 00:1a:70:fd:0b:7b - assume out of range
[  498.680272] wlan0: no IPv6 routers present
[  499.247599] wlan0: No STA entry for own AP 00:1a:70:fd:0b:7b
[  499.251947] wlan0: Initial auth_alg=0
[  499.251961] wlan0: authenticate with AP 00:1a:70:fd:0b:7b
[  499.254511] wlan0: Initial auth_alg=0
[  499.254520] wlan0: authenticate with AP 00:1a:70:fd:0b:7b
[  499.267630] wlan0: RX authentication from 00:1a:70:fd:0b:7b (alg=0 transaction=2 status=0)
[  499.267639] wlan0: authenticated
[  499.267643] wlan0: associate with AP 00:1a:70:fd:0b:7b
[  499.271340] wlan0: authentication frame received from 00:1a:70:fd:0b:7b, but not in authenticate state - ignored
[  499.277651] wlan0: RX ReassocResp from 00:1a:70:fd:0b:7b (capab=0x411 status=0 aid=1)
[  499.277659] wlan0: associated
[  499.277781] wlan0: WMM queue=2 aci=0 acm=0 aifs=3 cWmin=15 cWmax=1023 burst=0
[  499.287473] wlan0: WMM queue=3 aci=1 acm=0 aifs=7 cWmin=15 cWmax=1023 burst=0
[  499.288078] wlan0: WMM queue=1 aci=2 acm=0 aifs=2 cWmin=7 cWmax=15 burst=30
[  499.288712] wlan0: WMM queue=0 aci=3 acm=0 aifs=2 cWmin=3 cWmax=7 burst=15
[  506.329066] wlan0: no IPv6 routers present
[  508.597210] wlan0: No ProbeResp from current AP 00:1a:70:fd:0b:7b - assume out of range
[  511.918356] wlan0: Initial auth_alg=0
[  511.918371] wlan0: authenticate with AP 00:1a:70:fd:0b:7b
[  511.920940] wlan0: Initial auth_alg=0
[  511.920949] wlan0: authenticate with AP 00:1a:70:fd:0b:7b
[  511.948088] wlan0: RX authentication from 00:1a:70:fd:0b:7b (alg=0 transaction=2 status=0)
[  511.948097] wlan0: authenticated
[  511.948101] wlan0: associate with AP 00:1a:70:fd:0b:7b
[  512.028627] wlan0: associate with AP 00:1a:70:fd:0b:7b
[  512.036510] wlan0: authentication frame received from 00:1a:70:fd:0b:7b, but not in authenticate state - ignored
[  512.145828] wlan0: associate with AP 00:1a:70:fd:0b:7b
[  512.169838] wlan0: authentication frame received from 00:1a:70:fd:0b:7b, but not in authenticate state - ignored
[  512.191029] wlan0: authentication frame received from 00:1a:70:fd:0b:7b, but not in authenticate state - ignored
[  512.228218] wlan0: authentication frame received from 00:1a:70:fd:0b:7b, but not in authenticate state - ignored
[  512.243796] wlan0: association with AP 00:1a:70:fd:0b:7b timed out
[  512.306755] wlan0: authentication frame received from 00:1a:70:fd:0b:7b, but not in authenticate state - ignored
[  512.328061] wlan0: authentication frame received from 00:1a:70:fd:0b:7b, but not in authenticate state - ignored
[  512.337232] wlan0: association frame received from 00:1a:70:fd:0b:7b, but not in associate state - ignored
[  512.357241] wlan0: association frame received from 00:1a:70:fd:0b:7b, but not in associate state - ignored
[  512.406332] wlan0: association frame received from 00:1a:70:fd:0b:7b, but not in associate state - ignored
[  516.213015] wlan0: RX deauthentication from 00:1a:70:fd:0b:7b (reason=15)
[  516.213024] wlan0: deauthenticated
[  516.288232] wlan0: RX deauthentication from 00:1a:70:fd:0b:7b (reason=15)
[  516.579767] wlan0: RX deauthentication from 00:1a:70:fd:0b:7b (reason=15)
[  516.616748] wlan0: RX deauthentication from 00:1a:70:fd:0b:7b (reason=15)
[  520.483068] wlan0: Initial auth_alg=0
[  520.483076] wlan0: authenticate with AP 00:1a:70:fd:0b:7b
[  520.486177] wlan0: Initial auth_alg=0
[  520.486183] wlan0: authenticate with AP 00:1a:70:fd:0b:7b
[  520.490421] wlan0: Initial auth_alg=0
[  520.490431] wlan0: authenticate with AP 00:1a:70:fd:0b:7b
[  520.496154] wlan0: RX authentication from 00:1a:70:fd:0b:7b (alg=0 transaction=2 status=0)
[  520.496161] wlan0: authenticated
[  520.496165] wlan0: associate with AP 00:1a:70:fd:0b:7b
[  520.508730] wlan0: authentication frame received from 00:1a:70:fd:0b:7b, but not in authenticate state - ignored
[  520.513136] wlan0: RX AssocResp from 00:1a:70:fd:0b:7b (capab=0x411 status=0 aid=1)
[  520.513145] wlan0: associated
[  520.513265] wlan0: WMM queue=2 aci=0 acm=0 aifs=3 cWmin=15 cWmax=1023 burst=0
[  520.518405] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  520.520746] wlan0: WMM queue=3 aci=1 acm=0 aifs=7 cWmin=15 cWmax=1023 burst=0
[  520.521347] wlan0: WMM queue=1 aci=2 acm=0 aifs=2 cWmin=7 cWmax=15 burst=30
[  520.521962] wlan0: WMM queue=0 aci=3 acm=0 aifs=2 cWmin=3 cWmax=7 burst=15
[  521.422657] CPU0 attaching NULL sched-domain.
[  521.422666] CPU1 attaching NULL sched-domain.
[  521.431401] CPU0 attaching sched-domain:
[  521.431411]  domain 0: span 03
[  521.431414]   groups: 01 02
[  521.431420]   domain 1: span 03
[  521.431423]    groups: 03
[  521.431427] CPU1 attaching sched-domain:
[  521.431431]  domain 0: span 03
[  521.431434]   groups: 02 01
[  521.431439]   domain 1: span 03
[  521.431442]    groups: 03
[  525.925074] wlan0: RX deauthentication from 00:1a:70:fd:0b:7b (reason=15)
[  525.925082] wlan0: deauthenticated
[  526.446887] wlan0: authenticate with AP 00:1a:70:fd:0b:7b
[  526.486034] wlan0: RX authentication from 00:1a:70:fd:0b:7b (alg=0 transaction=2 status=0)
[  526.486042] wlan0: authenticated
[  526.486046] wlan0: associate with AP 00:1a:70:fd:0b:7b
[  526.514461] wlan0: RX ReassocResp from 00:1a:70:fd:0b:7b (capab=0x411 status=0 aid=1)
[  526.514469] wlan0: associated
[  527.223048] b44: eth0: Link is up at 100 Mbps, full duplex.
[  527.223055] b44: eth0: Flow control is off for TX and off for RX.
[  527.228397] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[  527.406260] wlan0: no IPv6 routers present
[  534.526042] wlan0: deauthenticate(reason=3)
[  541.254887] wlan0: RX deauthentication from 00:1a:70:fd:0b:7b (reason=7)
[  541.254895] wlan0: deauthenticated
[  541.254903] wlan0: RX deauthentication from 00:1a:70:fd:0b:7b (reason=7)
[  541.254909] wlan0: authenticate with AP 00:1a:70:fd:0b:7b
[  541.304108] wlan0: RX authentication from 00:1a:70:fd:0b:7b (alg=0 transaction=2 status=0)
[  541.304117] wlan0: authenticated
[  541.304121] wlan0: associate with AP 00:1a:70:fd:0b:7b
[  541.332560] wlan0: invalid aid value 0; bits 15:14 not set
[  541.332570] wlan0: RX AssocResp from 00:1a:70:fd:0b:7b (capab=0x411 status=12 aid=0)
[  541.332574] wlan0: AP denied association (code=12)
[  541.429819] wlan0: associate with AP 00:1a:70:fd:0b:7b
[  541.481770] wlan0: invalid aid value 0; bits 15:14 not set
[  541.481781] wlan0: RX AssocResp from 00:1a:70:fd:0b:7b (capab=0x411 status=12 aid=0)
[  541.481785] wlan0: AP denied association (code=12)
[  541.628742] wlan0: associate with AP 00:1a:70:fd:0b:7b
[  541.650320] wlan0: invalid aid value 0; bits 15:14 not set
[  541.650330] wlan0: RX AssocResp from 00:1a:70:fd:0b:7b (capab=0x411 status=12 aid=0)
[  541.650334] wlan0: AP denied association (code=12)
[  541.733847] wlan0: association with AP 00:1a:70:fd:0b:7b timed out
[  545.282240] eth0: no IPv6 routers present
[  550.422447] wlan0: RX disassociation from 00:1a:70:fd:0b:7b (reason=7)
[  550.422455] wlan0: RX disassociation from 00:1a:70:fd:0b:7b (reason=7)
[  550.422459] wlan0: RX disassociation from 00:1a:70:fd:0b:7b (reason=7)
[  550.422463] wlan0: RX disassociation from 00:1a:70:fd:0b:7b (reason=7)
[  565.864688] wlan0: RX disassociation from 00:1a:70:fd:0b:7b (reason=7)
[  565.864699] wlan0: RX disassociation from 00:1a:70:fd:0b:7b (reason=7)
[  565.864705] wlan0: RX disassociation from 00:1a:70:fd:0b:7b (reason=7)
[  565.864711] wlan0: RX disassociation from 00:1a:70:fd:0b:7b (reason=7)
[  587.101564] wlan0: RX disassociation from 00:1a:70:fd:0b:7b (reason=7)
[  587.101575] wlan0: RX disassociation from 00:1a:70:fd:0b:7b (reason=7)
[  587.101582] wlan0: RX disassociation from 00:1a:70:fd:0b:7b (reason=7)
[  587.101588] wlan0: RX disassociation from 00:1a:70:fd:0b:7b (reason=7)
[  587.101593] wlan0: RX disassociation from 00:1a:70:fd:0b:7b (reason=7)
[  594.265941] wlan0: RX disassociation from 00:1a:70:fd:0b:7b (reason=7)
[  594.265953] wlan0: RX disassociation from 00:1a:70:fd:0b:7b (reason=7)
[  594.313320] wlan0: RX disassociation from 00:1a:70:fd:0b:7b (reason=7)
[  594.324244] wlan0: RX disassociation from 00:1a:70:fd:0b:7b (reason=7)
[  594.362210] wlan0: RX disassociation from 00:1a:70:fd:0b:7b (reason=7)
[  594.362948] wlan0: RX disassociation from 00:1a:70:fd:0b:7b (reason=7)

```

It kept asking for a password, but rejecting the password when I know it was correct. It also tried using LEAP once rather than WPA2 and the password was in WPA2.

I asked AT&T to send me a new modem to see if that fixes the issue, but I am still not sure that will do it. I learned yesterday that the service I signed up for has a "Wireless signal" or something like that built in and it could be the cause, since my old modem is not new enough to work with that signal. 

I am going to be really ticked if this nearly new Wireless N Router is broken...   blasted thing is expensive, and I don't have the cash to replace it. It was bought at a Best Buy, but I doubt they will replace it for free.

Leo

---

### Post by LeoSolaris on 2008-07-13
Ok...   I feel all sorts of stupid.

I removed wifi-radar

I enabled the Proposed updates (I had some bad experiences with proposed updates really screwing up my system, so I disabled it, then forgot about them)

I changed my password to something simpler (from a really secure one with @ and numbers and various capped and uncapped letters, to one with just lower case and numbers)

Then I updated the system.

Then I restarted.

Now it works perfectly and I am picking up wireless signals that I had never seen around here before.

These are things I should have done at the start of this fiasco...

Sorry bout that guys (or gals) and thank y'all for your help!

Leo

Grrr...  Blasted thing lied to me...    lasted for all of ten minutes.

latest dmesg:

```

not in authenticate state - ignored
[  141.007429] wlan0: Initial auth_alg=0
[  141.007439] wlan0: authenticate with AP 00:1a:70:fd:0b:7b
[  141.009312] wlan0: RX authentication from 00:1a:70:fd:0b:7b (alg=0 transaction=2 status=0)
[  141.009318] wlan0: authenticated
[  141.009322] wlan0: associate with AP 00:1a:70:fd:0b:7b
[  141.012355] wlan0: RX ReassocResp from 00:1a:70:fd:0b:7b (capab=0x411 status=0 aid=1)
[  141.012364] wlan0: associated
[  141.012371] wlan0: CTS protection enabled (BSSID=00:1a:70:fd:0b:7b)
[  141.012443] wlan0: WMM queue=2 aci=0 acm=0 aifs=3 cWmin=15 cWmax=1023 burst=0
[  141.012449] wlan0: WMM queue=3 aci=1 acm=0 aifs=7 cWmin=15 cWmax=1023 burst=0
[  141.012454] wlan0: WMM queue=1 aci=2 acm=0 aifs=2 cWmin=7 cWmax=15 burst=30
[  141.012458] wlan0: WMM queue=0 aci=3 acm=0 aifs=2 cWmin=3 cWmax=7 burst=15
[  141.555119] wlan0: CTS protection disabled (BSSID=00:1a:70:fd:0b:7b)
[  145.855896] wlan0: no IPv6 routers present
[  145.917250] wlan0: CTS protection enabled (BSSID=00:1a:70:fd:0b:7b)
[  146.557056] wlan0: CTS protection disabled (BSSID=00:1a:70:fd:0b:7b)
[  146.621485] wlan0: CTS protection enabled (BSSID=00:1a:70:fd:0b:7b)
[  160.138467] wlan0: CTS protection disabled (BSSID=00:1a:70:fd:0b:7b)
[  162.000692] wlan0: CTS protection enabled (BSSID=00:1a:70:fd:0b:7b)
[  181.623061] CPU0 attaching NULL sched-domain.
[  181.623076] CPU1 attaching NULL sched-domain.
[  181.635695] CPU0 attaching sched-domain:
[  181.635710]  domain 0: span 03
[  181.635716]   groups: 01 02
[  181.635725]   domain 1: span 03
[  181.635730]    groups: 03
[  181.635735]    domain 2: span 03
[  181.635741]     groups: 03
[  181.635748] CPU1 attaching sched-domain:
[  181.635751]  domain 0: span 03
[  181.635757]   groups: 02 01
[  181.635764]   domain 1: span 03
[  181.635767]    groups: 03
[  181.635774]    domain 2: span 03
[  181.635780]     groups: 03
[  182.264302] wlan0: CTS protection disabled (BSSID=00:1a:70:fd:0b:7b)
[  182.783153] wlan0: CTS protection enabled (BSSID=00:1a:70:fd:0b:7b)
[  184.352742] wlan0: CTS protection disabled (BSSID=00:1a:70:fd:0b:7b)
[  184.458223] wlan0: CTS protection enabled (BSSID=00:1a:70:fd:0b:7b)
[  185.151993] wlan0: CTS protection disabled (BSSID=00:1a:70:fd:0b:7b)
[  188.131263] wlan0: CTS protection enabled (BSSID=00:1a:70:fd:0b:7b)
[  188.442813] wlan0: CTS protection disabled (BSSID=00:1a:70:fd:0b:7b)
[  189.485386] wlan0: CTS protection enabled (BSSID=00:1a:70:fd:0b:7b)
[  189.842322] wlan0: CTS protection disabled (BSSID=00:1a:70:fd:0b:7b)
[  195.998189] wlan0: CTS protection enabled (BSSID=00:1a:70:fd:0b:7b)
[  196.358391] wlan0: CTS protection disabled (BSSID=00:1a:70:fd:0b:7b)
[  196.795502] wlan0: CTS protection enabled (BSSID=00:1a:70:fd:0b:7b)
[  197.429153] wlan0: CTS protection disabled (BSSID=00:1a:70:fd:0b:7b)
[  197.463932] wlan0: CTS protection enabled (BSSID=00:1a:70:fd:0b:7b)
[  198.108879] wlan0: CTS protection disabled (BSSID=00:1a:70:fd:0b:7b)
[  198.228031] wlan0: CTS protection enabled (BSSID=00:1a:70:fd:0b:7b)
[  199.590520] wlan0: CTS protection disabled (BSSID=00:1a:70:fd:0b:7b)
[  201.041931] wlan0: CTS protection enabled (BSSID=00:1a:70:fd:0b:7b)
[  201.387777] wlan0: CTS protection disabled (BSSID=00:1a:70:fd:0b:7b)
[  207.702993] wlan0: CTS protection enabled (BSSID=00:1a:70:fd:0b:7b)
[  208.025228] wlan0: CTS protection disabled (BSSID=00:1a:70:fd:0b:7b)
[  208.330755] wlan0: CTS protection enabled (BSSID=00:1a:70:fd:0b:7b)
[  210.801511] wlan0: CTS protection disabled (BSSID=00:1a:70:fd:0b:7b)
[  212.997991] wlan0: CTS protection enabled (BSSID=00:1a:70:fd:0b:7b)
[  220.578320] wlan0: CTS protection disabled (BSSID=00:1a:70:fd:0b:7b)
[  220.975695] wlan0: CTS protection enabled (BSSID=00:1a:70:fd:0b:7b)
[  224.869684] wlan0: CTS protection disabled (BSSID=00:1a:70:fd:0b:7b)
[  226.021792] wlan0: CTS protection enabled (BSSID=00:1a:70:fd:0b:7b)
[  232.482877] wlan0: CTS protection disabled (BSSID=00:1a:70:fd:0b:7b)
[  234.134613] wlan0: CTS protection enabled (BSSID=00:1a:70:fd:0b:7b)
[  236.493010] wlan0: CTS protection disabled (BSSID=00:1a:70:fd:0b:7b)
[  236.660077] wlan0: CTS protection enabled (BSSID=00:1a:70:fd:0b:7b)
[  239.219377] wlan0: CTS protection disabled (BSSID=00:1a:70:fd:0b:7b)
[  244.234600] wlan0: CTS protection enabled (BSSID=00:1a:70:fd:0b:7b)
[  245.556923] wlan0: CTS protection disabled (BSSID=00:1a:70:fd:0b:7b)
[  267.332468] wlan0: CTS protection enabled (BSSID=00:1a:70:fd:0b:7b)
[  270.674606] wlan0: CTS protection disabled (BSSID=00:1a:70:fd:0b:7b)
[  274.134610] wlan0: CTS protection enabled (BSSID=00:1a:70:fd:0b:7b)
[  275.135969] wlan0: CTS protection disabled (BSSID=00:1a:70:fd:0b:7b)
[  275.171765] wlan0: CTS protection enabled (BSSID=00:1a:70:fd:0b:7b)
[  286.682977] wlan0: CTS protection disabled (BSSID=00:1a:70:fd:0b:7b)
[  315.549422] wlan0: CTS protection enabled (BSSID=00:1a:70:fd:0b:7b)
[  330.758830] wlan0: CTS protection disabled (BSSID=00:1a:70:fd:0b:7b)
[  333.403335] wlan0: CTS protection enabled (BSSID=00:1a:70:fd:0b:7b)
[  342.660275] wlan0: CTS protection disabled (BSSID=00:1a:70:fd:0b:7b)
[  382.499815] wlan0: deauthenticate(reason=3)
[  387.845214] wlan0: Initial auth_alg=0
[  387.845222] wlan0: authenticate with AP 00:1a:70:fd:0b:7b
[  387.846990] wlan0: Initial auth_alg=0
[  387.846998] wlan0: authenticate with AP 00:1a:70:fd:0b:7b
[  387.850973] wlan0: Initial auth_alg=0
[  387.850984] wlan0: authenticate with AP 00:1a:70:fd:0b:7b
[  387.960934] wlan0: authenticate with AP 00:1a:70:fd:0b:7b
[  388.067998] wlan0: authenticate with AP 00:1a:70:fd:0b:7b
[  388.158551] wlan0: authentication with AP 00:1a:70:fd:0b:7b timed out
[  388.624035] wlan0: authentication frame received from 00:1a:70:fd:0b:7b, but not in authenticate state - ignored
[  389.136919] wlan0: authentication frame received from 00:1a:70:fd:0b:7b, but not in authenticate state - ignored
[  422.917328] wlan0: Initial auth_alg=0
[  422.917337] wlan0: authenticate with AP 00:1a:70:fd:0b:7b
[  422.921011] wlan0: Initial auth_alg=0
[  422.921019] wlan0: authenticate with AP 00:1a:70:fd:0b:7b
[  422.921043] wlan0: RX authentication from 00:1a:70:fd:0b:7b (alg=0 transaction=2 status=0)
[  422.921047] wlan0: authenticated
[  422.921051] wlan0: associate with AP 00:1a:70:fd:0b:7b
[  422.923490] wlan0: authentication frame received from 00:1a:70:fd:0b:7b, but not in authenticate state - ignored
[  422.925971] wlan0: RX AssocResp from 00:1a:70:fd:0b:7b (capab=0x411 status=0 aid=1)
[  422.925981] wlan0: associated
[  422.925988] wlan0: CTS protection enabled (BSSID=00:1a:70:fd:0b:7b)
[  422.926068] wlan0: WMM queue=2 aci=0 acm=0 aifs=3 cWmin=15 cWmax=1023 burst=0
[  422.926073] wlan0: WMM queue=3 aci=1 acm=0 aifs=7 cWmin=15 cWmax=1023 burst=0
[  422.926078] wlan0: WMM queue=1 aci=2 acm=0 aifs=2 cWmin=7 cWmax=15 burst=30
[  422.926083] wlan0: WMM queue=0 aci=3 acm=0 aifs=2 cWmin=3 cWmax=7 burst=15
[  422.931384] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  428.651143] wlan0: RX deauthentication from 00:1a:70:fd:0b:7b (reason=15)
[  428.651150] wlan0: deauthenticated
[  428.651165] wlan0: RX deauthentication from 00:1a:70:fd:0b:7b (reason=7)
[  428.651171] wlan0: RX deauthentication from 00:1a:70:fd:0b:7b (reason=7)
[  428.651177] wlan0: RX deauthentication from 00:1a:70:fd:0b:7b (reason=7)
[  428.651182] wlan0: RX deauthentication from 00:1a:70:fd:0b:7b (reason=7)
[  428.651188] wlan0: RX deauthentication from 00:1a:70:fd:0b:7b (reason=7)
[  428.651193] wlan0: RX deauthentication from 00:1a:70:fd:0b:7b (reason=7)
[  428.651199] wlan0: RX deauthentication from 00:1a:70:fd:0b:7b (reason=7)
[  428.651204] wlan0: RX deauthentication from 00:1a:70:fd:0b:7b (reason=7)
[  428.651210] wlan0: RX deauthentication from 00:1a:70:fd:0b:7b (reason=7)
[  428.651233] wlan0: RX deauthentication from 00:1a:70:fd:0b:7b (reason=7)
[  428.651238] wlan0: RX deauthentication from 00:1a:70:fd:0b:7b (reason=7)
[  428.651244] wlan0: RX deauthentication from 00:1a:70:fd:0b:7b (reason=7)
[  428.658013] wlan0: Initial auth_alg=0
[  428.658022] wlan0: authenticate with AP 00:1a:70:fd:0b:7b
[  428.658050] wlan0: RX deauthentication from 00:1a:70:fd:0b:7b (reason=7)
[  428.658056] wlan0: RX deauthentication from 00:1a:70:fd:0b:7b (reason=7)
[  428.661592] wlan0: Initial auth_alg=0
[  428.661602] wlan0: authenticate with AP 00:1a:70:fd:0b:7b
[  428.663690] wlan0: RX authentication from 00:1a:70:fd:0b:7b (alg=0 transaction=2 status=0)
[  428.663698] wlan0: authenticated
[  428.663701] wlan0: associate with AP 00:1a:70:fd:0b:7b
[  428.666364] wlan0: RX AssocResp from 00:1a:70:fd:0b:7b (capab=0x411 status=0 aid=1)
[  428.666371] wlan0: associated
[  428.666376] wlan0: CTS protection enabled (BSSID=00:1a:70:fd:0b:7b)
[  428.666444] wlan0: WMM queue=2 aci=0 acm=0 aifs=3 cWmin=15 cWmax=1023 burst=0
[  428.666449] wlan0: WMM queue=3 aci=1 acm=0 aifs=7 cWmin=15 cWmax=1023 burst=0
[  428.666454] wlan0: WMM queue=1 aci=2 acm=0 aifs=2 cWmin=7 cWmax=15 burst=30
[  428.666458] wlan0: WMM queue=0 aci=3 acm=0 aifs=2 cWmin=3 cWmax=7 burst=15
[  428.673577] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  429.831628] wlan0: deauthenticate(reason=3)
[  432.452904] wlan0: RX deauthentication from 00:1a:70:fd:0b:7b (reason=7)
[  432.452911] wlan0: deauthenticated
[  432.452918] wlan0: RX deauthentication from 00:1a:70:fd:0b:7b (reason=7)
[  432.452924] wlan0: RX deauthentication from 00:1a:70:fd:0b:7b (reason=7)
[  432.452930] wlan0: RX deauthentication from 00:1a:70:fd:0b:7b (reason=7)
[  432.452936] wlan0: RX deauthentication from 00:1a:70:fd:0b:7b (reason=7)
[  432.452941] wlan0: RX deauthentication from 00:1a:70:fd:0b:7b (reason=7)
[  432.452946] wlan0: RX deauthentication from 00:1a:70:fd:0b:7b (reason=7)
[  432.452952] wlan0: RX deauthentication from 00:1a:70:fd:0b:7b (reason=7)
[  432.452958] wlan0: RX deauthentication from 00:1a:70:fd:0b:7b (reason=7)
[  432.452964] wlan0: RX deauthentication from 00:1a:70:fd:0b:7b (reason=7)
[  432.452970] wlan0: RX deauthentication from 00:1a:70:fd:0b:7b (reason=7)
[  432.452975] wlan0: RX deauthentication from 00:1a:70:fd:0b:7b (reason=7)
[  432.452980] wlan0: RX deauthentication from 00:1a:70:fd:0b:7b (reason=7)
[  432.452986] wlan0: RX deauthentication from 00:1a:70:fd:0b:7b (reason=7)
[  432.456769] wlan0: Initial auth_alg=0
[  432.456777] wlan0: authenticate with AP 00:1a:70:fd:0b:7b
[  432.456805] wlan0: RX deauthentication from 00:1a:70:fd:0b:7b (reason=7)
[  432.460060] wlan0: Initial auth_alg=0
[  432.460069] wlan0: authenticate with AP 00:1a:70:fd:0b:7b
[  432.462347] wlan0: Initial auth_alg=0
[  432.462357] wlan0: authenticate with AP 00:1a:70:fd:0b:7b
[  432.464364] wlan0: Initial auth_alg=0
[  432.464374] wlan0: authenticate with AP 00:1a:70:fd:0b:7b
[  432.464403] wlan0: RX authentication from 00:1a:70:fd:0b:7b (alg=0 transaction=2 status=0)
[  432.464407] wlan0: authenticated
[  432.464410] wlan0: associate with AP 00:1a:70:fd:0b:7b
[  432.466239] wlan0: authentication frame received from 00:1a:70:fd:0b:7b, but not in authenticate state - ignored
[  432.467009] wlan0: RX AssocResp from 00:1a:70:fd:0b:7b (capab=0x411 status=0 aid=1)
[  432.467018] wlan0: associated
[  432.467025] wlan0: CTS protection enabled (BSSID=00:1a:70:fd:0b:7b)
[  432.467099] wlan0: WMM queue=2 aci=0 acm=0 aifs=3 cWmin=15 cWmax=1023 burst=0
[  432.467105] wlan0: WMM queue=3 aci=1 acm=0 aifs=7 cWmin=15 cWmax=1023 burst=0
[  432.467109] wlan0: WMM queue=1 aci=2 acm=0 aifs=2 cWmin=7 cWmax=15 burst=30
[  432.467114] wlan0: WMM queue=0 aci=3 acm=0 aifs=2 cWmin=3 cWmax=7 burst=15
[  432.472222] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  435.678584] wlan0: CTS protection disabled (BSSID=00:1a:70:fd:0b:7b)
[  436.899659] wlan0: CTS protection enabled (BSSID=00:1a:70:fd:0b:7b)
[  444.311888] wlan0: no IPv6 routers present
[  453.752032] wlan0: CTS protection disabled (BSSID=00:1a:70:fd:0b:7b)
[  455.500554] wlan0: CTS protection enabled (BSSID=00:1a:70:fd:0b:7b)
[  456.946004] wlan0: CTS protection disabled (BSSID=00:1a:70:fd:0b:7b)
[  467.418552] wlan0: CTS protection enabled (BSSID=00:1a:70:fd:0b:7b)
[  470.231156] wlan0: CTS protection disabled (BSSID=00:1a:70:fd:0b:7b)
[  505.469781] wlan0: CTS protection enabled (BSSID=00:1a:70:fd:0b:7b)
[  506.642908] wlan0: CTS protection disabled (BSSID=00:1a:70:fd:0b:7b)
[  513.027105] wlan0: CTS protection enabled (BSSID=00:1a:70:fd:0b:7b)
[  514.285793] wlan0: CTS protection disabled (BSSID=00:1a:70:fd:0b:7b)
[  516.888859] wlan0: CTS protection enabled (BSSID=00:1a:70:fd:0b:7b)
[  518.455100] wlan0: CTS protection disabled (BSSID=00:1a:70:fd:0b:7b)
[  519.015823] wlan0: CTS protection enabled (BSSID=00:1a:70:fd:0b:7b)
[  521.820282] wlan0: CTS protection disabled (BSSID=00:1a:70:fd:0b:7b)
[  521.993547] wlan0: CTS protection enabled (BSSID=00:1a:70:fd:0b:7b)
[  522.721878] wlan0: CTS protection disabled (BSSID=00:1a:70:fd:0b:7b)
[  525.430737] wlan0: CTS protection enabled (BSSID=00:1a:70:fd:0b:7b)
[  527.686855] wlan0: CTS protection disabled (BSSID=00:1a:70:fd:0b:7b)
[  528.095882] wlan0: CTS protection enabled (BSSID=00:1a:70:fd:0b:7b)
[  529.516887] wlan0: CTS protection disabled (BSSID=00:1a:70:fd:0b:7b)
[  541.781568] wlan0: CTS protection enabled (BSSID=00:1a:70:fd:0b:7b)
[  557.613897] wlan0: CTS protection disabled (BSSID=00:1a:70:fd:0b:7b)
[  563.587363] wlan0: CTS protection enabled (BSSID=00:1a:70:fd:0b:7b)
[  564.283738] wlan0: CTS protection disabled (BSSID=00:1a:70:fd:0b:7b)
[  568.677035] wlan0: No ProbeResp from current AP 00:1a:70:fd:0b:7b - assume out of range
[  570.307780] wlan0: No STA entry for own AP 00:1a:70:fd:0b:7b
[  570.312103] wlan0: Initial auth_alg=0
[  570.312119] wlan0: authenticate with AP 00:1a:70:fd:0b:7b
[  570.314838] wlan0: Initial auth_alg=0
[  570.314848] wlan0: authenticate with AP 00:1a:70:fd:0b:7b
[  570.363483] wlan0: authenticate with AP 00:1a:70:fd:0b:7b
[  570.412657] wlan0: authenticate with AP 00:1a:70:fd:0b:7b
[  570.454796] wlan0: RX authentication from 00:1a:70:fd:0b:7b (alg=0 transaction=2 status=0)
[  570.454806] wlan0: authenticated
[  570.454810] wlan0: associate with AP 00:1a:70:fd:0b:7b
[  570.504138] wlan0: associate with AP 00:1a:70:fd:0b:7b
[  570.565662] wlan0: associate with AP 00:1a:70:fd:0b:7b
[  570.604775] wlan0: association with AP 00:1a:70:fd:0b:7b timed out
[  570.854659] wlan0: authentication frame received from 00:1a:70:fd:0b:7b, but not in authenticate state - ignored
[  571.074919] wlan0: authentication frame received from 00:1a:70:fd:0b:7b, but not in authenticate state - ignored
[  571.075788] wlan0: authentication frame received from 00:1a:70:fd:0b:7b, but not in authenticate state - ignored
[  571.136005] wlan0: authentication frame received from 00:1a:70:fd:0b:7b, but not in authenticate state - ignored
[  571.282476] wlan0: authentication frame received from 00:1a:70:fd:0b:7b, but not in authenticate state - ignored
[  571.302196] wlan0: authentication frame received from 00:1a:70:fd:0b:7b, but not in authenticate state - ignored
[  571.303346] wlan0: association frame received from 00:1a:70:fd:0b:7b, but not in associate state - ignored
[  571.305347] wlan0: association frame received from 00:1a:70:fd:0b:7b, but not in associate state - ignored
[  571.532063] wlan0: association frame received from 00:1a:70:fd:0b:7b, but not in associate state - ignored
[  571.690870] wlan0: association frame received from 00:1a:70:fd:0b:7b, but not in associate state - ignored
[  571.693269] wlan0: association frame received from 00:1a:70:fd:0b:7b, but not in associate state - ignored
[  572.281500] wlan0: association frame received from 00:1a:70:fd:0b:7b, but not in associate state - ignored
[  572.651204] wlan0: association frame received from 00:1a:70:fd:0b:7b, but not in associate state - ignored
[  572.866467] wlan0: association frame received from 00:1a:70:fd:0b:7b, but not in associate state - ignored
[  572.997027] wlan0: association frame received from 00:1a:70:fd:0b:7b, but not in associate state - ignored
[  573.039787] wlan0: RX deauthentication from 00:1a:70:fd:0b:7b (reason=15)
[  573.039796] wlan0: deauthenticated
[  573.042253] wlan0: RX deauthentication from 00:1a:70:fd:0b:7b (reason=15)
[  577.721487] wlan0: RX deauthentication from 00:1a:70:fd:0b:7b (reason=7)
[  577.721497] wlan0: RX deauthentication from 00:1a:70:fd:0b:7b (reason=7)
[  577.721503] wlan0: RX deauthentication from 00:1a:70:fd:0b:7b (reason=7)
[  577.721509] wlan0: RX deauthentication from 00:1a:70:fd:0b:7b (reason=7)
[  577.724856] wlan0: Initial auth_alg=0
[  577.724864] wlan0: authenticate with AP 00:1a:70:fd:0b:7b
[  577.842137] wlan0: authenticate with AP 00:1a:70:fd:0b:7b
[  577.981593] wlan0: authenticate with AP 00:1a:70:fd:0b:7b
[  578.087246] wlan0: authentication with AP 00:1a:70:fd:0b:7b timed out
[  578.544126] wlan0: Initial auth_alg=0
[  578.544136] wlan0: authenticate with AP 00:1a:70:fd:0b:7b
[  578.607832] wlan0: authenticate with AP 00:1a:70:fd:0b:7b
[  578.673613] wlan0: authenticate with AP 00:1a:70:fd:0b:7b
[  578.744831] wlan0: authentication with AP 00:1a:70:fd:0b:7b timed out
[  578.776257] wlan0: authentication frame received from 00:1a:70:fd:0b:7b, but not in authenticate state - ignored
[  578.777034] wlan0: authentication frame received from 00:1a:70:fd:0b:7b, but not in authenticate state - ignored
[  578.782492] wlan0: authentication frame received from 00:1a:70:fd:0b:7b, but not in authenticate state - ignored
[  578.957919] wlan0: authentication frame received from 00:1a:70:fd:0b:7b, but not in authenticate state - ignored
[  579.064004] wlan0: authentication frame received from 00:1a:70:fd:0b:7b, but not in authenticate state - ignored
[  579.178951] wlan0: authentication frame received from 00:1a:70:fd:0b:7b, but not in authenticate state - ignored
[  579.189116] wlan0: authentication frame received from 00:1a:70:fd:0b:7b, but not in authenticate state - ignored
[  579.487070] wlan0: authentication frame received from 00:1a:70:fd:0b:7b, but not in authenticate state - ignored
[  590.783472] wlan0: Initial auth_alg=0
[  590.783483] wlan0: authenticate with AP 00:1a:70:fd:0b:7b
[  590.858599] wlan0: authenticate with AP 00:1a:70:fd:0b:7b
[  590.983535] wlan0: authenticate with AP 00:1a:70:fd:0b:7b
[  591.061421] wlan0: authentication with AP 00:1a:70:fd:0b:7b timed out
[  593.476647] wlan0: Initial auth_alg=0
[  593.476657] wlan0: authenticate with AP 00:1a:70:fd:0b:7b
[  593.479439] wlan0: Initial auth_alg=0
[  593.479449] wlan0: authenticate with AP 00:1a:70:fd:0b:7b
[  593.492426] wlan0: RX authentication from 00:1a:70:fd:0b:7b (alg=0 transaction=2 status=0)
[  593.492436] wlan0: authenticated
[  593.492440] wlan0: associate with AP 00:1a:70:fd:0b:7b
[  593.550725] wlan0: associate with AP 00:1a:70:fd:0b:7b
[  593.578753] wlan0: authentication frame received from 00:1a:70:fd:0b:7b, but not in authenticate state - ignored
[  593.581677] wlan0: authentication frame received from 00:1a:70:fd:0b:7b, but not in authenticate state - ignored
[  593.604536] wlan0: associate with AP 00:1a:70:fd:0b:7b
[  593.661556] wlan0: association with AP 00:1a:70:fd:0b:7b timed out
[  593.672943] wlan0: authentication frame received from 00:1a:70:fd:0b:7b, but not in authenticate state - ignored
[  596.173906] wlan0: authentication frame received from 00:1a:70:fd:0b:7b, but not in authenticate state - ignored
[  596.290127] wlan0: authentication frame received from 00:1a:70:fd:0b:7b, but not in authenticate state - ignored
[  596.291011] wlan0: authentication frame received from 00:1a:70:fd:0b:7b, but not in authenticate state - ignored
[  596.317054] wlan0: authentication frame received from 00:1a:70:fd:0b:7b, but not in authenticate state - ignored
[  596.343275] wlan0: authentication frame received from 00:1a:70:fd:0b:7b, but not in authenticate state - ignored
[  598.029290] wlan0: authentication frame received from 00:1a:70:fd:0b:7b, but not in authenticate state - ignored
[  598.033654] wlan0: authentication frame received from 00:1a:70:fd:0b:7b, but not in authenticate state - ignored
[  598.867439] wlan0: authentication frame received from 00:1a:70:fd:0b:7b, but not in authenticate state - ignored
[  599.491371] wlan0: authentication frame received from 00:1a:70:fd:0b:7b, but not in authenticate state - ignored
[  600.012011] wlan0: authentication frame received from 00:1a:70:fd:0b:7b, but not in authenticate state - ignored
[  600.412153] wlan0: authentication frame received from 00:1a:70:fd:0b:7b, but not in authenticate state - ignored
[  600.528652] wlan0: authentication frame received from 00:1a:70:fd:0b:7b, but not in authenticate state - ignored
[  600.561652] wlan0: authentication frame received from 00:1a:70:fd:0b:7b, but not in authenticate state - ignored
[  600.752446] wlan0: authentication frame received from 00:1a:70:fd:0b:7b, but not in authenticate state - ignored
[  600.842382] wlan0: association frame received from 00:1a:70:fd:0b:7b, but not in associate state - ignored
[  601.501344] wlan0: association frame received from 00:1a:70:fd:0b:7b, but not in associate state - ignored
[  601.900827] wlan0: association frame received from 00:1a:70:fd:0b:7b, but not in associate state - ignored
[  602.353135] wlan0: association frame received from 00:1a:70:fd:0b:7b, but not in associate state - ignored
[  602.835285] wlan0: association frame received from 00:1a:70:fd:0b:7b, but not in associate state - ignored
[  603.011191] wlan0: association frame received from 00:1a:70:fd:0b:7b, but not in associate state - ignored
[  603.122981] wlan0: association frame received from 00:1a:70:fd:0b:7b, but not in associate state - ignored
[  603.387189] wlan0: association frame received from 00:1a:70:fd:0b:7b, but not in associate state - ignored
[  603.707434] wlan0: Initial auth_alg=0
[  603.707444] wlan0: authenticate with AP 00:1a:70:fd:0b:7b
[  603.817743] wlan0: authenticate with AP 00:1a:70:fd:0b:7b
[  603.894218] wlan0: authenticate with AP 00:1a:70:fd:0b:7b
[  603.981848] wlan0: authentication with AP 00:1a:70:fd:0b:7b timed out
[  604.096830] wlan0: RX deauthentication from 00:1a:70:fd:0b:7b (reason=15)
[  604.096839] wlan0: deauthenticated
[  605.018143] wlan0: authentication frame received from 00:1a:70:fd:0b:7b, but not in authenticate state - ignored
[  605.127863] wlan0: authentication frame received from 00:1a:70:fd:0b:7b, but not in authenticate state - ignored
[  606.092950] wlan0: Initial auth_alg=0
[  606.092961] wlan0: authenticate with AP 00:1a:70:fd:0b:7b
[  606.095453] wlan0: Initial auth_alg=0
[  606.095462] wlan0: authenticate with AP 00:1a:70:fd:0b:7b
[  606.147233] wlan0: authenticate with AP 00:1a:70:fd:0b:7b
[  606.173715] wlan0: authenticate with AP 00:1a:70:fd:0b:7b
[  606.204598] wlan0: authentication with AP 00:1a:70:fd:0b:7b timed out
[  607.119277] wlan0: authentication frame received from 00:1a:70:fd:0b:7b, but not in authenticate state - ignored
[  607.461171] wlan0: authentication frame received from 00:1a:70:fd:0b:7b, but not in authenticate state - ignored
[  607.836506] wlan0: authentication frame received from 00:1a:70:fd:0b:7b, but not in authenticate state - ignored
[  608.005791] wlan0: authentication frame received from 00:1a:70:fd:0b:7b, but not in authenticate state - ignored
[  608.011667] wlan0: authentication frame received from 00:1a:70:fd:0b:7b, but not in authenticate state - ignored
[  608.128325] wlan0: authentication frame received from 00:1a:70:fd:0b:7b, but not in authenticate state - ignored
[  608.173076] wlan0: authentication frame received from 00:1a:70:fd:0b:7b, but not in authenticate state - ignored
[  608.173886] wlan0: authentication frame received from 00:1a:70:fd:0b:7b, but not in authenticate state - ignored
[  608.547665] wlan0: Initial auth_alg=0
[  608.547674] wlan0: authenticate with AP 00:1a:70:fd:0b:7b
[  608.550041] wlan0: Initial auth_alg=0
[  608.550049] wlan0: authenticate with AP 00:1a:70:fd:0b:7b
[  608.589086] wlan0: authenticate with AP 00:1a:70:fd:0b:7b
[  608.624321] wlan0: authenticate with AP 00:1a:70:fd:0b:7b
[  608.665795] wlan0: RX authentication from 00:1a:70:fd:0b:7b (alg=0 transaction=2 status=0)
[  608.665804] wlan0: authenticated
[  608.665808] wlan0: associate with AP 00:1a:70:fd:0b:7b
[  608.726557] wlan0: associate with AP 00:1a:70:fd:0b:7b
[  608.735408] wlan0: authentication frame received from 00:1a:70:fd:0b:7b, but not in authenticate state - ignored
[  608.764870] wlan0: associate with AP 00:1a:70:fd:0b:7b
[  608.797090] wlan0: association with AP 00:1a:70:fd:0b:7b timed out
[  608.965930] wlan0: authentication frame received from 00:1a:70:fd:0b:7b, but not in authenticate state - ignored
[  609.052342] wlan0: authentication frame received from 00:1a:70:fd:0b:7b, but not in authenticate state - ignored
[  609.709612] wlan0: authentication frame received from 00:1a:70:fd:0b:7b, but not in authenticate state - ignored
[  609.802095] wlan0: authentication frame received from 00:1a:70:fd:0b:7b, but not in authenticate state - ignored
[  609.817406] wlan0: authentication frame received from 00:1a:70:fd:0b:7b, but not in authenticate state - ignored
[  609.818173] wlan0: authentication frame received from 00:1a:70:fd:0b:7b, but not in authenticate state - ignored
[  609.823163] wlan0: authentication frame received from 00:1a:70:fd:0b:7b, but not in authenticate state - ignored
[  609.887692] wlan0: authentication frame received from 00:1a:70:fd:0b:7b, but not in authenticate state - ignored
[  609.888851] wlan0: association frame received from 00:1a:70:fd:0b:7b, but not in associate state - ignored
[  609.890447] wlan0: association frame received from 00:1a:70:fd:0b:7b, but not in associate state - ignored
[  609.904871] wlan0: association frame received from 00:1a:70:fd:0b:7b, but not in associate state - ignored
[  609.920293] wlan0: association frame received from 00:1a:70:fd:0b:7b, but not in associate state - ignored
[  609.942208] wlan0: association frame received from 00:1a:70:fd:0b:7b, but not in associate state - ignored
[  610.009308] wlan0: association frame received from 00:1a:70:fd:0b:7b, but not in associate state - ignored
[  610.140309] wlan0: association frame received from 00:1a:70:fd:0b:7b, but not in associate state - ignored
[  610.167739] wlan0: association frame received from 00:1a:70:fd:0b:7b, but not in associate state - ignored
[  610.182088] wlan0: association frame received from 00:1a:70:fd:0b:7b, but not in associate state - ignored
[  610.251839] wlan0: association frame received from 00:1a:70:fd:0b:7b, but not in associate state - ignored
[  610.608508] wlan0: RX deauthentication from 00:1a:70:fd:0b:7b (reason=15)
[  610.608517] wlan0: deauthenticated
[  612.303103] wlan0: RX deauthentication from 00:1a:70:fd:0b:7b (reason=7)
[  612.303116] wlan0: RX deauthentication from 00:1a:70:fd:0b:7b (reason=7)
[  612.303122] wlan0: RX deauthentication from 00:1a:70:fd:0b:7b (reason=7)
[  612.303128] wlan0: RX deauthentication from 00:1a:70:fd:0b:7b (reason=7)
[  612.303134] wlan0: RX deauthentication from 00:1a:70:fd:0b:7b (reason=7)
[  612.303139] wlan0: RX deauthentication from 00:1a:70:fd:0b:7b (reason=7)
[  612.303145] wlan0: RX deauthentication from 00:1a:70:fd:0b:7b (reason=7)
[  614.956194] wlan0: RX deauthentication from 00:1a:70:fd:0b:7b (reason=7)
[  614.960327] wlan0: Initial auth_alg=0
[  614.960337] wlan0: authenticate with AP 00:1a:70:fd:0b:7b
[  614.962881] wlan0: Initial auth_alg=0
[  614.962893] wlan0: authenticate with AP 00:1a:70:fd:0b:7b
[  614.998581] wlan0: authenticate with AP 00:1a:70:fd:0b:7b
[  615.088087] wlan0: authenticate with AP 00:1a:70:fd:0b:7b
[  615.127529] wlan0: authentication with AP 00:1a:70:fd:0b:7b timed out
[  615.536588] wlan0: authentication frame received from 00:1a:70:fd:0b:7b, but not in authenticate state - ignored
[  615.539826] wlan0: authentication frame received from 00:1a:70:fd:0b:7b, but not in authenticate state - ignored
[  615.544850] wlan0: authentication frame received from 00:1a:70:fd:0b:7b, but not in authenticate state - ignored
[  615.605681] wlan0: authentication frame received from 00:1a:70:fd:0b:7b, but not in authenticate state - ignored
[  615.606506] wlan0: authentication frame received from 00:1a:70:fd:0b:7b, but not in authenticate state - ignored
[  615.609207] wlan0: authentication frame received from 00:1a:70:fd:0b:7b, but not in authenticate state - ignored
[  615.627233] wlan0: authentication frame received from 00:1a:70:fd:0b:7b, but not in authenticate state - ignored
[  619.959890] b44: eth0: Link is up at 100 Mbps, full duplex.
[  619.959897] b44: eth0: Flow control is off for TX and off for RX.
[  619.965528] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[  620.006052] wlan0: Initial auth_alg=0
[  620.006062] wlan0: authenticate with AP 00:1a:70:fd:0b:7b
[  620.008357] wlan0: Initial auth_alg=0
[  620.008366] wlan0: authenticate with AP 00:1a:70:fd:0b:7b
[  620.057711] wlan0: authenticate with AP 00:1a:70:fd:0b:7b
[  620.087555] wlan0: authenticate with AP 00:1a:70:fd:0b:7b
[  620.153406] wlan0: authentication with AP 00:1a:70:fd:0b:7b timed out
[  626.732542] eth0: no IPv6 routers present
[  630.651766] wlan0: authentication frame received from 00:1a:70:fd:0b:7b, but not in authenticate state - ignored
[  630.730834] wlan0: authentication frame received from 00:1a:70:fd:0b:7b, but not in authenticate state - ignored
[  630.835206] wlan0: authentication frame received from 00:1a:70:fd:0b:7b, but not in authenticate state - ignored
[  631.544876] wlan0: authentication frame received from 00:1a:70:fd:0b:7b, but not in authenticate state - ignored
[  631.559973] wlan0: authentication frame received from 00:1a:70:fd:0b:7b, but not in authenticate state - ignored
[  633.068418] wlan0: authentication frame received from 00:1a:70:fd:0b:7b, but not in authenticate state - ignored

```

[grouch]
Blasted piece of @#$5& #&*&%!!
[/grouch]

It seems to drop more often if there are other wireless networks in range.

Leo

---

### Post by LeoSolaris on 2008-07-13
I had (to quote Fry) one of those headaches with pictures!

I recalled one of the settings I could change in my web-settings for the router, about standard or wide channel and standard channel frequencies...

Well...   it was on auto. The wide channel Ubuntu just doesn't pick up, so I switched it to standard. It has been on the first channel of standard, so I swapped it to one of the alternates. It connected a good deal faster this time.

I am going to keep playing with it if I find that it continues to disconnect...   It may just be that the over lapping signals are causing interference. 

At least the signal strength is appropriate.

---

### Post by pytheas22 on 2008-07-13
Sorry to see it getting your hopes up and letting you down time and again.

The things you're doing seem good and, for now at least, I don't have much advice beyond what I've already given.  The only thing I will suggest is changing the channel that your router operates on.  If interference from other networks is contributing to the problem, that would help resolve it.

If you want to see which other channels are operating around you, the command:
```

iwlist scan
```

will list all the networks in range and their operating channels (you may need to run it a few times because it doesn't always pick up every network in one try).  It might help to look for the networks with the strongest signals, note their channels, and switch your router to operate on a channel as far away as possible.  In the United States I think you use channels 1 to 11.

Otherwise, please let us know how things go.

---

