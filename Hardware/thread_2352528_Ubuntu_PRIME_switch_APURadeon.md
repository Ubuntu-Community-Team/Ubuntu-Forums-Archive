---
title: "Ubuntu PRIME: switch APU/Radeon"
date: 2017-02-13
forum: Hardware
---

### Post by camelking96 on 2017-02-13
Good morning
  I had that problem on Ubuntu 14.04, and I never have been able to  resolve it. Now, on Ubuntu 16.04, I think I would find a solution: i  can't switch from APU A4-6210 to the dedicated graphic card AMD Radeon  HD 8570M. Using PRIME as described on the italian community guide. i put the  command

  ```
xrandr --listproviders
```
  and it gives to me that:
  ```
Providers: number : 3
Provider 0: id: 0x74 cap: 0x9, Source Output, Sink Offload crtcs: 2 outputs: 3 associated providers: 2 name:MULLINS @ pci:0000:00:01.0
Provider 1: id: 0x3f cap: 0x6, Sink Output, Source Offload crtcs: 0 outputs: 0 associated providers: 2 name:HAINAN @ pci:0000:01:00.0
Provider 2: id: 0x3f cap: 0x6, Sink Output, Source Offload crtcs: 0 outputs: 0 associated providers: 2 name:HAINAN @ pci:0000:01:00.0
```
  So I can see my APU (Mullins) but TWO (?) Radeon (Hainan)  Goning on with the guide, i put the IDs of the two graphic cards (0x74 e  0x3f) and I tried to start some programs  with the Radeon. Giving the  command
  ```
DRI_PRIME=1 0ad
```
  To try it on the famous linux videogame 0 A.D., but I had a black screen with this message
  [URL="http://www.imagestime.com/imageshow.php/1100381_IMG20170210144420.jpg"]http://www.imagestime.com/imageshow.php/1100381_IMG20170210144420.jpg
[/URL]  I have no idea of what it could be, the only thing I remember is that  on Ubuntu 14.04 I had to fix a brightness problem, which I resolved  changing something in that folder (I think). 

I also tried to give this command

```
francesco@Francesco:~$ dmesg | egrep 'drm|radeon'
[    2.093014] [drm] Initialized drm 1.1.0 20060810
[    2.162969] [drm] radeon kernel modesetting enabled.
[    2.175086] fb: switching to radeondrmfb from EFI VGA
[    2.175767] [drm] initializing kernel modesetting (MULLINS 0x1002:0x9850 0x103C:0x22CE).
[    2.175791] [drm] register mmio base: 0xF0F00000
[    2.175793] [drm] register mmio size: 262144
[    2.175803] [drm] doorbell mmio base: 0xF0000000
[    2.175806] [drm] doorbell mmio size: 8388608
[    2.175814] [drm] ACPI VFCT contains a BIOS for 00:01.0 1002:9850, size 60416
[    2.175978] radeon 0000:00:01.0: VRAM: 512M 0x0000000000000000 - 0x000000001FFFFFFF (512M used)
[    2.175983] radeon 0000:00:01.0: GTT: 2048M 0x0000000020000000 - 0x000000009FFFFFFF
[    2.175986] [drm] Detected VRAM RAM=512M, BAR=256M
[    2.175989] [drm] RAM width 128bits DDR
[    2.176415] [drm] radeon: 512M of VRAM memory ready
[    2.176418] [drm] radeon: 2048M of GTT memory ready.
[    2.176443] [drm] Loading mullins Microcode
[    2.178545] [drm] Internal thermal controller without fan control
[    2.179442] [drm] radeon: dpm initialized
[    2.181906] [drm] Found VCE firmware/feedback version 40.2.2 / 15!
[    2.184388] [drm] GART: num cpu pages 524288, num gpu pages 524288
[    2.218985] [drm] PCIE GART of 2048M enabled (table at 0x0000000000324000).
[    2.219202] radeon 0000:00:01.0: WB enabled
[    2.219222] radeon 0000:00:01.0: fence driver on ring 0 use gpu addr 0x0000000020000c00 and cpu addr 0xffff880035765c00
[    2.219227] radeon 0000:00:01.0: fence driver on ring 1 use gpu addr 0x0000000020000c04 and cpu addr 0xffff880035765c04
[    2.219232] radeon 0000:00:01.0: fence driver on ring 2 use gpu addr 0x0000000020000c08 and cpu addr 0xffff880035765c08
[    2.219236] radeon 0000:00:01.0: fence driver on ring 3 use gpu addr 0x0000000020000c0c and cpu addr 0xffff880035765c0c
[    2.219240] radeon 0000:00:01.0: fence driver on ring 4 use gpu addr 0x0000000020000c10 and cpu addr 0xffff880035765c10
[    2.219743] radeon 0000:00:01.0: fence driver on ring 5 use gpu addr 0x0000000000076c98 and cpu addr 0xffffc90001036c98
[    2.219940] radeon 0000:00:01.0: fence driver on ring 6 use gpu addr 0x0000000020000c18 and cpu addr 0xffff880035765c18
[    2.219945] radeon 0000:00:01.0: fence driver on ring 7 use gpu addr 0x0000000020000c1c and cpu addr 0xffff880035765c1c
[    2.219950] [drm] Supports vblank timestamp caching Rev 2 (21.10.2013).
[    2.219952] [drm] Driver supports precise vblank timestamp query.
[    2.220012] radeon 0000:00:01.0: radeon: using MSI.
[    2.220052] [drm] radeon: irq initialized.
[    2.224128] [drm] ring test on 0 succeeded in 3 usecs
[    2.224225] [drm] ring test on 1 succeeded in 2 usecs
[    2.224244] [drm] ring test on 2 succeeded in 2 usecs
[    2.224464] [drm] ring test on 3 succeeded in 4 usecs
[    2.224473] [drm] ring test on 4 succeeded in 4 usecs
[    2.250323] [drm] ring test on 5 succeeded in 2 usecs
[    2.250339] [drm] UVD initialized successfully.
[    2.359548] [drm] ring test on 6 succeeded in 12 usecs
[    2.359560] [drm] ring test on 7 succeeded in 2 usecs
[    2.359562] [drm] VCE initialized successfully.
[    2.362787] [drm] ib test on ring 0 succeeded in 0 usecs
[    2.362827] [drm] ib test on ring 1 succeeded in 0 usecs
[    2.862202] [drm] ib test on ring 2 succeeded in 0 usecs
[    2.862284] [drm] ib test on ring 3 succeeded in 0 usecs
[    2.862348] [drm] ib test on ring 4 succeeded in 0 usecs
[    3.362225] [drm] ib test on ring 5 succeeded
[    3.362800] [drm] ib test on ring 6 succeeded
[    3.363310] [drm] ib test on ring 7 succeeded
[    3.366425] [drm] radeon atom DIG backlight initialized
[    3.366430] [drm] Radeon Display Connectors
[    3.366432] [drm] Connector 0:
[    3.366434] [drm]   eDP-1
[    3.366436] [drm]   HPD1
[    3.366440] [drm]   DDC: 0x6530 0x6530 0x6534 0x6534 0x6538 0x6538 0x653c 0x653c
[    3.366442] [drm]   Encoders:
[    3.366444] [drm]     LCD1: INTERNAL_UNIPHY
[    3.366446] [drm] Connector 1:
[    3.366448] [drm]   HDMI-A-1
[    3.366449] [drm]   HPD2
[    3.366452] [drm]   DDC: 0x6540 0x6540 0x6544 0x6544 0x6548 0x6548 0x654c 0x654c
[    3.366454] [drm]   Encoders:
[    3.366455] [drm]     DFP1: INTERNAL_UNIPHY
[    3.366457] [drm] Connector 2:
[    3.366459] [drm]   VGA-1
[    3.366462] [drm]   DDC: 0x65c0 0x65c0 0x65c4 0x65c4 0x65c8 0x65c8 0x65cc 0x65cc
[    3.366463] [drm]   Encoders:
[    3.366465] [drm]     CRT1: INTERNAL_KLDSCP_DAC1
[    3.668202] [drm] fb mappable at 0xE0728000
[    3.668210] [drm] vram apper at 0xE0000000
[    3.668213] [drm] size 4325376
[    3.668216] [drm] fb depth is 24
[    3.668219] [drm]    pitch is 5632
[    3.668451] fbcon: radeondrmfb (fb0) is primary device
[    3.668685] radeon 0000:00:01.0: fb0: radeondrmfb frame buffer device
[    3.694838] [drm] Initialized radeon 2.43.0 20080528 for 0000:00:01.0 on minor 0
[    3.695027] radeon 0000:01:00.0: enabling device (0002 -> 0003)
[    3.695500] [drm] initializing kernel modesetting (HAINAN 0x1002:0x666F 0x103C:0x22CE).
[    3.695530] [drm] register mmio base: 0xF0E00000
[    3.695532] [drm] register mmio size: 262144
[    3.767122] [drm] GPU not posted. posting now...
[    3.772878] radeon 0000:01:00.0: VRAM: 1024M 0x0000000000000000 - 0x000000003FFFFFFF (1024M used)
[    3.772884] radeon 0000:01:00.0: GTT: 2048M 0x0000000040000000 - 0x00000000BFFFFFFF
[    3.772888] [drm] Detected VRAM RAM=1024M, BAR=256M
[    3.772891] [drm] RAM width 64bits DDR
[    3.772920] [drm] radeon: 1024M of VRAM memory ready
[    3.772923] [drm] radeon: 2048M of GTT memory ready.
[    3.772949] [drm] Loading hainan Microcode
[    3.773226] [drm] External GPIO thermal controller with fan control
[    3.773277] [drm] probing gen 2 caps for device 1022:1439 = 733c41/6
[    3.784858] [drm] radeon: dpm initialized
[    3.784872] [drm] GART: num cpu pages 524288, num gpu pages 524288
[    3.788276] [drm] probing gen 2 caps for device 1022:1439 = 733c41/6
[    3.788287] [drm] enabling PCIE gen 2 link speeds, disable with radeon.pcie_gen2=0
[    4.249100] [drm] PCIE GART of 2048M enabled (table at 0x0000000000040000).
[    4.249319] radeon 0000:01:00.0: WB enabled
[    4.249326] radeon 0000:01:00.0: fence driver on ring 0 use gpu addr 0x0000000040000c00 and cpu addr 0xffff880033fa0c00
[    4.249331] radeon 0000:01:00.0: fence driver on ring 1 use gpu addr 0x0000000040000c04 and cpu addr 0xffff880033fa0c04
[    4.249335] radeon 0000:01:00.0: fence driver on ring 2 use gpu addr 0x0000000040000c08 and cpu addr 0xffff880033fa0c08
[    4.249339] radeon 0000:01:00.0: fence driver on ring 3 use gpu addr 0x0000000040000c0c and cpu addr 0xffff880033fa0c0c
[    4.249343] radeon 0000:01:00.0: fence driver on ring 4 use gpu addr 0x0000000040000c10 and cpu addr 0xffff880033fa0c10
[    4.249348] radeon 0000:01:00.0: VCE init error (-22).
[    4.249352] [drm] Supports vblank timestamp caching Rev 2 (21.10.2013).
[    4.249355] [drm] Driver supports precise vblank timestamp query.
[    4.249358] radeon 0000:01:00.0: radeon: MSI limited to 32-bit
[    4.249435] radeon 0000:01:00.0: radeon: using MSI.
[    4.249482] [drm] radeon: irq initialized.
[    4.665976] [drm] ring test on 0 succeeded in 1 usecs
[    4.665989] [drm] ring test on 1 succeeded in 1 usecs
[    4.665999] [drm] ring test on 2 succeeded in 1 usecs
[    4.666013] [drm] ring test on 3 succeeded in 4 usecs
[    4.666023] [drm] ring test on 4 succeeded in 4 usecs
[    4.666701] [drm] ib test on ring 0 succeeded in 0 usecs
[    4.666744] [drm] ib test on ring 1 succeeded in 0 usecs
[    4.666794] [drm] ib test on ring 2 succeeded in 0 usecs
[    4.666820] [drm] ib test on ring 3 succeeded in 0 usecs
[    4.666842] [drm] ib test on ring 4 succeeded in 0 usecs
[    4.667987] [drm] Radeon Display Connectors
[    4.670375] [drm:radeon_acpi_init [radeon]] *ERROR* Cannot find a backlight controller
[    4.670538] [drm] Initialized radeon 2.43.0 20080528 for 0000:01:00.0 on minor 1
[   18.469340] [drm] probing gen 2 caps for device 1022:1439 = 733c41/6
[   18.469350] [drm] enabling PCIE gen 2 link speeds, disable with radeon.pcie_gen2=0
[   18.940666] [drm] PCIE GART of 2048M enabled (table at 0x0000000000040000).
[   18.940910] radeon 0000:01:00.0: WB enabled
[   18.940917] radeon 0000:01:00.0: fence driver on ring 0 use gpu addr 0x0000000040000c00 and cpu addr 0xffff880033fa0c00
[   18.940922] radeon 0000:01:00.0: fence driver on ring 1 use gpu addr 0x0000000040000c04 and cpu addr 0xffff880033fa0c04
[   18.940927] radeon 0000:01:00.0: fence driver on ring 2 use gpu addr 0x0000000040000c08 and cpu addr 0xffff880033fa0c08
[   18.940931] radeon 0000:01:00.0: fence driver on ring 3 use gpu addr 0x0000000040000c0c and cpu addr 0xffff880033fa0c0c
[   18.940935] radeon 0000:01:00.0: fence driver on ring 4 use gpu addr 0x0000000040000c10 and cpu addr 0xffff880033fa0c10
[   18.940939] radeon 0000:01:00.0: VCE init error (-22).
[   19.359047] [drm] ring test on 0 succeeded in 1 usecs
[   19.359064] [drm] ring test on 1 succeeded in 1 usecs
[   19.359073] [drm] ring test on 2 succeeded in 1 usecs
[   19.359090] [drm] ring test on 3 succeeded in 5 usecs
[   19.359100] [drm] ring test on 4 succeeded in 4 usecs
[   19.359154] [drm] ib test on ring 0 succeeded in 0 usecs
[   19.359194] [drm] ib test on ring 1 succeeded in 0 usecs
[   19.359240] [drm] ib test on ring 2 succeeded in 0 usecs
[   19.359269] [drm] ib test on ring 3 succeeded in 0 usecs
[   19.359292] [drm] ib test on ring 4 succeeded in 0 usecs
[   35.875820] [drm] probing gen 2 caps for device 1022:1439 = 733c41/6
[   35.875830] [drm] enabling PCIE gen 2 link speeds, disable with radeon.pcie_gen2=0
[   36.345069] [drm] PCIE GART of 2048M enabled (table at 0x0000000000040000).
[   36.345254] radeon 0000:01:00.0: WB enabled
[   36.345261] radeon 0000:01:00.0: fence driver on ring 0 use gpu addr 0x0000000040000c00 and cpu addr 0xffff880033fa0c00
[   36.345266] radeon 0000:01:00.0: fence driver on ring 1 use gpu addr 0x0000000040000c04 and cpu addr 0xffff880033fa0c04
[   36.345271] radeon 0000:01:00.0: fence driver on ring 2 use gpu addr 0x0000000040000c08 and cpu addr 0xffff880033fa0c08
[   36.345276] radeon 0000:01:00.0: fence driver on ring 3 use gpu addr 0x0000000040000c0c and cpu addr 0xffff880033fa0c0c
[   36.345280] radeon 0000:01:00.0: fence driver on ring 4 use gpu addr 0x0000000040000c10 and cpu addr 0xffff880033fa0c10
[   36.345285] radeon 0000:01:00.0: VCE init error (-22).
[   36.761081] [drm] ring test on 0 succeeded in 1 usecs
[   36.761094] [drm] ring test on 1 succeeded in 1 usecs
[   36.761104] [drm] ring test on 2 succeeded in 1 usecs
[   36.761118] [drm] ring test on 3 succeeded in 4 usecs
[   36.761128] [drm] ring test on 4 succeeded in 4 usecs
[   36.761176] [drm] ib test on ring 0 succeeded in 0 usecs
[   36.761245] [drm] ib test on ring 1 succeeded in 0 usecs
[   36.761285] [drm] ib test on ring 2 succeeded in 0 usecs
[   36.761312] [drm] ib test on ring 3 succeeded in 0 usecs
[   36.761332] [drm] ib test on ring 4 succeeded in 0 usecs
[   53.257493] [drm] probing gen 2 caps for device 1022:1439 = 733c41/6
[   53.257505] [drm] enabling PCIE gen 2 link speeds, disable with radeon.pcie_gen2=0
[   53.727179] [drm] PCIE GART of 2048M enabled (table at 0x0000000000040000).
[   53.727358] radeon 0000:01:00.0: WB enabled
[   53.727365] radeon 0000:01:00.0: fence driver on ring 0 use gpu addr 0x0000000040000c00 and cpu addr 0xffff880033fa0c00
[   53.727371] radeon 0000:01:00.0: fence driver on ring 1 use gpu addr 0x0000000040000c04 and cpu addr 0xffff880033fa0c04
[   53.727376] radeon 0000:01:00.0: fence driver on ring 2 use gpu addr 0x0000000040000c08 and cpu addr 0xffff880033fa0c08
[   53.727380] radeon 0000:01:00.0: fence driver on ring 3 use gpu addr 0x0000000040000c0c and cpu addr 0xffff880033fa0c0c
[   53.727385] radeon 0000:01:00.0: fence driver on ring 4 use gpu addr 0x0000000040000c10 and cpu addr 0xffff880033fa0c10
[   53.727390] radeon 0000:01:00.0: VCE init error (-22).
[   54.143793] [drm] ring test on 0 succeeded in 1 usecs
[   54.143807] [drm] ring test on 1 succeeded in 1 usecs
[   54.143816] [drm] ring test on 2 succeeded in 1 usecs
[   54.143833] [drm] ring test on 3 succeeded in 4 usecs
[   54.143843] [drm] ring test on 4 succeeded in 4 usecs
[   54.143887] [drm] ib test on ring 0 succeeded in 0 usecs
[   54.143968] [drm] ib test on ring 1 succeeded in 0 usecs
[   54.144008] [drm] ib test on ring 2 succeeded in 0 usecs
[   54.144033] [drm] ib test on ring 3 succeeded in 0 usecs
[   54.144054] [drm] ib test on ring 4 succeeded in 0 usecs
[   74.693286] [drm] probing gen 2 caps for device 1022:1439 = 733c41/6
[   74.693298] [drm] enabling PCIE gen 2 link speeds, disable with radeon.pcie_gen2=0
[   75.162641] [drm] PCIE GART of 2048M enabled (table at 0x0000000000040000).
[   75.162817] radeon 0000:01:00.0: WB enabled
[   75.162824] radeon 0000:01:00.0: fence driver on ring 0 use gpu addr 0x0000000040000c00 and cpu addr 0xffff880033fa0c00
[   75.162829] radeon 0000:01:00.0: fence driver on ring 1 use gpu addr 0x0000000040000c04 and cpu addr 0xffff880033fa0c04
[   75.162834] radeon 0000:01:00.0: fence driver on ring 2 use gpu addr 0x0000000040000c08 and cpu addr 0xffff880033fa0c08
[   75.162839] radeon 0000:01:00.0: fence driver on ring 3 use gpu addr 0x0000000040000c0c and cpu addr 0xffff880033fa0c0c
[   75.162843] radeon 0000:01:00.0: fence driver on ring 4 use gpu addr 0x0000000040000c10 and cpu addr 0xffff880033fa0c10
[   75.162849] radeon 0000:01:00.0: VCE init error (-22).
[   75.578019] [drm] ring test on 0 succeeded in 1 usecs
[   75.578033] [drm] ring test on 1 succeeded in 1 usecs
[   75.578042] [drm] ring test on 2 succeeded in 1 usecs
[   75.578058] [drm] ring test on 3 succeeded in 5 usecs
[   75.578069] [drm] ring test on 4 succeeded in 4 usecs
[   75.578113] [drm] ib test on ring 0 succeeded in 0 usecs
[   75.578200] [drm] ib test on ring 1 succeeded in 0 usecs
[   75.578242] [drm] ib test on ring 2 succeeded in 0 usecs
[   75.578295] [drm] ib test on ring 3 succeeded in 0 usecs
[   75.578317] [drm] ib test on ring 4 succeeded in 0 usecs
francesco@Francesco:~$ 
```

And you can see two error point: " VCE init error (-22)" and the other "*ERROR* Cannot find a backlight controller"
  Can you help me please? :)

---

