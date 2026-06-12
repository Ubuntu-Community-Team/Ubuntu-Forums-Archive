---
title: "Very slow boot with error in dmesg"
date: 2014-05-14
forum: Hardware
---

### Post by mohamed-ali-mhenni on 2014-05-14
Hi all,
I upgrade my Ubuntu from 13.10 to 14.04 beta version and it work well
my laptop is Lenovo z510 with i7 cpu and solidestat hybride hard drive.
But after i upgrade to final version a have some error shown in dmesg output and the boot is verys slow ( about 1 minute or more)
also after the login unity take a log time to appere in desktop

ther is my dmesg output
```

[   25.648090] Console: switching to colour frame buffer device 170x48
[   25.650674] i915 0000:00:02.0: fb0: inteldrmfb frame buffer device
[   25.650675] i915 0000:00:02.0: registered panic notifier
[   25.651074] [Firmware Bug]: ACPI(PEGP) defines _DOD but not _DOS
[   25.651416] ACPI: Video Device [PEGP] (multi-head: yes  rom: yes  post: no)
[   25.651433] ACPI Error: [\_SB_.PCI0.GFX0.DD02._BCL] Namespace lookup failure, AE_NOT_FOUND (20131115/psargs-359)
[   25.651439] ACPI Error: Method parse/execution failed [\_SB_.PCI0.PEG1.PEGP.DD02._BCL] (Node ffff8802538ad5c8), AE_NOT_FOUND (20131115/psparse-536)
[   25.651484] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:40/LNXVIDEO:00/input/input12
[   25.661208] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[   25.661498] acpi device:5a: registered as cooling_device9
[   25.661558] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:01/input/input13
[   25.661627] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 1
[   27.169885] Linux video capture interface: v2.00
[   28.344157] uvcvideo: Found UVC 1.00 device Lenovo EasyCamera (13d3:5722)
[   28.350247] input: Lenovo EasyCamera as /devices/pci0000:00/0000:00:14.0/usb3/3-1/3-1:1.0/input/input14
[   28.350362] usbcore: registered new interface driver uvcvideo
[   28.350364] USB Video Class driver (1.1.1)
[   28.392738] EXT4-fs (sda7): re-mounted. Opts: errors=remount-ro
[   28.457937] type=1400 audit(1400065383.191:2): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/sbin/dhclient" pid=603 comm="apparmor_parser"
[   28.457943] type=1400 audit(1400065383.191:3): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=603 comm="apparmor_parser"
[   28.457946] type=1400 audit(1400065383.191:4): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=603 comm="apparmor_parser"
[   28.457954] type=1400 audit(1400065383.191:5): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/sbin/dhclient" pid=480 comm="apparmor_parser"
[   28.457961] type=1400 audit(1400065383.191:6): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=480 comm="apparmor_parser"
[   28.457964] type=1400 audit(1400065383.191:7): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=480 comm="apparmor_parser"
[   28.457973] type=1400 audit(1400065383.191:8): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/sbin/dhclient" pid=481 comm="apparmor_parser"
[   28.457979] type=1400 audit(1400065383.191:9): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=481 comm="apparmor_parser"
[   28.457983] type=1400 audit(1400065383.191:10): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=481 comm="apparmor_parser"
[   28.458314] type=1400 audit(1400065383.191:11): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=603 comm="apparmor_parser"
[   29.232702] EXT4-fs (sda8): mounted filesystem with ordered data mode. Opts: (null)
[   32.430061] FS-Cache: Loaded
[   32.563624] FS-Cache: Netfs 'cifs' registered for caching
[   32.563684] Key type cifs.spnego registered
[   32.563688] Key type cifs.idmap registered
[   32.932433] CIFS VFS: Error connecting to socket. Aborting operation.
[   32.932553] CIFS VFS: cifs_mount failed w/return code = -101
[   35.248768] init: failsafe main process (859) killed by TERM signal
[   35.252850] CIFS VFS: Error connecting to socket. Aborting operation.
[   35.252956] CIFS VFS: cifs_mount failed w/return code = -101
[   42.040971] audit_printk_skb: 24 callbacks suppressed
[   42.040974] type=1400 audit(1400065396.775:20): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/sbin/dhclient" pid=1003 comm="apparmor_parser"
[   42.040978] type=1400 audit(1400065396.775:21): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=1003 comm="apparmor_parser"
[   42.040981] type=1400 audit(1400065396.775:22): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=1003 comm="apparmor_parser"
[   42.041238] type=1400 audit(1400065396.775:23): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=1003 comm="apparmor_parser"
[   42.041240] type=1400 audit(1400065396.775:24): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=1003 comm="apparmor_parser"
[   42.041375] type=1400 audit(1400065396.775:25): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=1003 comm="apparmor_parser"
[   42.280477] type=1400 audit(1400065397.015:26): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/sbin/mysqld" pid=1009 comm="apparmor_parser"
[   42.304420] type=1400 audit(1400065397.039:27): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/sbin/tcpdump" pid=1011 comm="apparmor_parser"
[   42.317557] type=1400 audit(1400065397.051:28): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/sbin/cups-browsed" pid=1007 comm="apparmor_parser"
[   42.594847] type=1400 audit(1400065397.327:29): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/cups/backend/cups-pdf" pid=1008 comm="apparmor_parser"
[   44.626952] CIFS VFS: Error connecting to socket. Aborting operation.
[   44.627053] CIFS VFS: cifs_mount failed w/return code = -101
[   44.839752] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   44.839755] Bluetooth: BNEP filters: protocol multicast
[   44.839764] Bluetooth: BNEP socket layer initialized
[   44.854225] Bluetooth: RFCOMM TTY layer initialized
[   44.854232] Bluetooth: RFCOMM socket layer initialized
[   44.854237] Bluetooth: RFCOMM ver 1.11
[   44.881184] init: Failed to spawn atd main process: unable to execute: No such file or directory
[   46.470515] init: cups main process (1079) killed by HUP signal
[   46.470536] init: cups main process ended, respawning
[   47.635225] bbswitch: version 0.7
[   47.635232] bbswitch: Found integrated VGA device 0000:00:02.0: \_SB_.PCI0.GFX0
[   47.635237] bbswitch: Found discrete VGA device 0000:07:00.0: \_SB_.PCI0.PEG1.PEGP
[   47.635246] ACPI Warning: \_SB_.PCI0.PEG1.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20131115/nsarguments-95)
[   47.635313] bbswitch: detected an Optimus _DSM function
[   47.635320] bbswitch: Succesfully loaded. Discrete card 0000:07:00.0 is on
[   49.378586] init: samba-ad-dc main process (1000) terminated with status 1
[   54.073204] r8169 0000:08:00.0 eth0: link down
[   54.073226] r8169 0000:08:00.0 eth0: link down
[   54.073235] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   54.073504] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   54.075076] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   55.739702] r8169 0000:08:00.0 eth0: link up
[   55.739710] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   56.034994] init: nvidia-persistenced main process (1428) terminated with status 1
[   57.643460] init: nvidia-persistenced main process (1463) terminated with status 1
[   58.663596] Non-volatile memory driver v1.3
[   58.717008] thinkpad_acpi: ThinkPad ACPI Extras v0.25
[   58.717010] thinkpad_acpi: http://ibm-acpi.sf.net/
[   58.717011] thinkpad_acpi: ThinkPad BIOS 8DCN26WW, EC unknown
[   58.717012] thinkpad_acpi: Lenovo Lenovo IdeaPad Z510, model 20287
[   58.717492] ACPI Error: [\_SB_.PCI0.GFX0.DD02._BCL] Namespace lookup failure, AE_NOT_FOUND (20131115/psargs-359)
[   58.717497] ACPI Error: Method parse/execution failed [\_SB_.PCI0.PEG1.PEGP.DD02._BCL] (Node ffff8802538ad5c8), AE_NOT_FOUND (20131115/psparse-536)
[   58.717504] thinkpad_acpi: detected a 8-level brightness capable ThinkPad
[   58.717531] thinkpad_acpi: Standard ACPI backlight interface available, not loading native one
[   58.717593] thinkpad_acpi: Console audio control enabled, mode: monitor (read only)
[   58.719618] input: ThinkPad Extra Buttons as /devices/platform/thinkpad_acpi/input/input15
[   64.007420] iwlwifi 0000:09:00.0: L1 Disabled; Enabling L0S
[   64.007654] iwlwifi 0000:09:00.0: L1 Disabled; Enabling L0S
[   64.018726] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   68.373416] vgaarb: this pci device is not a vga device
[   68.395876] nvidia 0000:07:00.0: irq 51 for MSI/MSI-X
[   68.401655] ACPI Warning: \_SB_.PCI0.PEG1.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20131115/nsarguments-95)
[   68.401685] ACPI Warning: \_SB_.PCI0.PEG1.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20131115/nsarguments-95)
[   68.401699] ACPI Warning: \_SB_.PCI0.PEG1.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20131115/nsarguments-95)
[   68.401722] ACPI Warning: \_SB_.PCI0.PEG1.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20131115/nsarguments-95)
[   68.401735] ACPI Warning: \_SB_.PCI0.PEG1.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20131115/nsarguments-95)
[   68.401748] ACPI Warning: \_SB_.PCI0.PEG1.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20131115/nsarguments-95)
[   68.401775] ACPI Warning: \_SB_.PCI0.PEG1.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20131115/nsarguments-95)
[   68.401789] ACPI Warning: \_SB_.PCI0.PEG1.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20131115/nsarguments-95)
[   69.147487] ACPI Warning: \_SB_.PCI0.PEG1.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20131115/nsarguments-95)
[   70.312097] vgaarb: this pci device is not a vga device
[   70.677832] init: plymouth-upstart-bridge main process ended, respawning
[   70.695777] init: plymouth-upstart-bridge main process ended, respawning
[   74.632470] audit_printk_skb: 138 callbacks suppressed


```
  in attachment you will find the log of bootchart
if you need more information pleaze tell me.

thank you

---

### Post by keratos2 on 2014-05-14
you've got quite a few "errors" in your dmesg. which ones are you worried about/thinking about. in big handfuls I see:

- Multiple ACPI errors
- Video errors?
- Networking profiles not defined so are being guessed?
- Samba/Shares not setup correctly
- atd Job daemon not setup correctly
- Plymouth boot taking too long - operations timing out

There is a load of stuff here. I'd suggest the upgrade did not "work well" contrary to your statement. I'd propose wiping the hard drive and starting again with a fresh 14.04 install - if you must. I've had a lot of issues with 14.04 and went back to 13.10 which is a lot more stable for me and many of my collegaues. What precisely is in 14.04 that you need. As a general , if you dont need it why are you doing it?
-

---

### Post by mohamed-ali-mhenni on 2014-05-14
thank u for your response .
i'll try to reinstall it and why i use 14.04 because it's only in that distribution i can use my geforce card

Update : 
i just reinstalled ubuntu 14.04 but the probleme with error and bad performance stay
i tryed to turn off acpi but error in sda5 shown but it boot faster
and i turn on acpi again and all work
the acpi error stay but the boot was fast
there is my dmesg 
teh mountig problem with samba it's juste beacause i haven't install cifs-utils
```

[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Initializing cgroup subsys cpuacct
[    0.000000] Linux version 3.14.1-031401-generic (apw@gomeisa) (gcc version 4.6.3 (Ubuntu/Linaro 4.6.3-1ubuntu5) ) #201404141220 SMP Mon Apr 14 16:21:48 UTC 2014
[    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-3.14.1-031401-generic root=UUID=bef5bda4-93bb-479d-9994-5e0987da907e ro quiet splash vt.handoff=7
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] e820: BIOS-provided physical RAM map:
[    0.000000] BIOS-e820: [mem 0x0000000000000000-0x000000000006efff] usable
[    0.000000] BIOS-e820: [mem 0x000000000006f000-0x000000000006ffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000000070000-0x0000000000087fff] usable
[    0.000000] BIOS-e820: [mem 0x0000000000088000-0x00000000000bffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000000100000-0x000000008ccaffff] usable
[    0.000000] BIOS-e820: [mem 0x000000008ccb0000-0x000000008e0affff] reserved
[    0.000000] BIOS-e820: [mem 0x000000008e0b0000-0x00000000926befff] usable
[    0.000000] BIOS-e820: [mem 0x00000000926bf000-0x00000000928befff] type 20
[    0.000000] BIOS-e820: [mem 0x00000000928bf000-0x0000000092ebefff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000092ebf000-0x0000000092fbefff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x0000000092fbf000-0x0000000092ffefff] ACPI data
[    0.000000] BIOS-e820: [mem 0x0000000092fff000-0x0000000092ffffff] usable
[    0.000000] BIOS-e820: [mem 0x0000000093000000-0x000000009f9fffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000e0000000-0x00000000efffffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000feb00000-0x00000000feb0ffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fec00000-0x00000000fec00fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fed00000-0x00000000fee00fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000ffb80000-0x00000000ffffffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000100000000-0x000000025f5fffff] usable
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] efi: EFI v2.31 by INSYDE Corp.
[    0.000000] efi:  ACPI=0x92ffe000  ACPI 2.0=0x92ffe014  SMBIOS=0x92ebef98 
[    0.000000] efi: mem00: type=3, attr=0xf, range=[0x0000000000000000-0x0000000000001000) (0MB)
[    0.000000] efi: mem01: type=7, attr=0xf, range=[0x0000000000001000-0x000000000006f000) (0MB)
[    0.000000] efi: mem02: type=0, attr=0xf, range=[0x000000000006f000-0x0000000000070000) (0MB)
[    0.000000] efi: mem03: type=7, attr=0xf, range=[0x0000000000070000-0x0000000000080000) (0MB)
[    0.000000] efi: mem04: type=3, attr=0xf, range=[0x0000000000080000-0x0000000000082000) (0MB)
[    0.000000] efi: mem05: type=7, attr=0xf, range=[0x0000000000082000-0x0000000000088000) (0MB)
[    0.000000] efi: mem06: type=6, attr=0x800000000000000f, range=[0x0000000000088000-0x000000000009f000) (0MB)
[    0.000000] efi: mem07: type=0, attr=0xf, range=[0x000000000009f000-0x00000000000a0000) (0MB)
[    0.000000] efi: mem08: type=2, attr=0xf, range=[0x0000000000100000-0x00000000014fb000) (19MB)
[    0.000000] efi: mem09: type=7, attr=0xf, range=[0x00000000014fb000-0x0000000002000000) (11MB)
[    0.000000] efi: mem10: type=2, attr=0xf, range=[0x0000000002000000-0x00000000033fb000) (19MB)
[    0.000000] efi: mem11: type=7, attr=0xf, range=[0x00000000033fb000-0x0000000035cbe000) (808MB)
[    0.000000] efi: mem12: type=2, attr=0xf, range=[0x0000000035cbe000-0x0000000036e57000) (17MB)
[    0.000000] efi: mem13: type=7, attr=0xf, range=[0x0000000036e57000-0x0000000067e61000) (784MB)
[    0.000000] efi: mem14: type=2, attr=0xf, range=[0x0000000067e61000-0x000000008b0c0000) (562MB)
[    0.000000] efi: mem15: type=4, attr=0xf, range=[0x000000008b0c0000-0x000000008b0e0000) (0MB)
[    0.000000] efi: mem16: type=7, attr=0xf, range=[0x000000008b0e0000-0x000000008badb000) (9MB)
[    0.000000] efi: mem17: type=2, attr=0xf, range=[0x000000008badb000-0x000000008bcaf000) (1MB)
[    0.000000] efi: mem18: type=4, attr=0xf, range=[0x000000008bcaf000-0x000000008ccb0000) (16MB)
[    0.000000] efi: mem19: type=0, attr=0xf, range=[0x000000008ccb0000-0x000000008e0b0000) (20MB)
[    0.000000] efi: mem20: type=7, attr=0xf, range=[0x000000008e0b0000-0x000000008e0bd000) (0MB)
[    0.000000] efi: mem21: type=2, attr=0xf, range=[0x000000008e0bd000-0x000000008e0bf000) (0MB)
[    0.000000] efi: mem22: type=7, attr=0xf, range=[0x000000008e0bf000-0x000000008e18b000) (0MB)
[    0.000000] efi: mem23: type=1, attr=0xf, range=[0x000000008e18b000-0x000000008e2bf000) (1MB)
[    0.000000] efi: mem24: type=7, attr=0xf, range=[0x000000008e2bf000-0x000000008f190000) (14MB)
[    0.000000] efi: mem25: type=2, attr=0xf, range=[0x000000008f190000-0x000000008f19a000) (0MB)
[    0.000000] efi: mem26: type=4, attr=0xf, range=[0x000000008f19a000-0x00000000900aa000) (15MB)
[    0.000000] efi: mem27: type=7, attr=0xf, range=[0x00000000900aa000-0x00000000900ab000) (0MB)
[    0.000000] efi: mem28: type=4, attr=0xf, range=[0x00000000900ab000-0x00000000900ac000) (0MB)
[    0.000000] efi: mem29: type=7, attr=0xf, range=[0x00000000900ac000-0x00000000900af000) (0MB)
[    0.000000] efi: mem30: type=4, attr=0xf, range=[0x00000000900af000-0x00000000900be000) (0MB)
[    0.000000] efi: mem31: type=7, attr=0xf, range=[0x00000000900be000-0x00000000900bf000) (0MB)
[    0.000000] efi: mem32: type=4, attr=0xf, range=[0x00000000900bf000-0x00000000900e7000) (0MB)
[    0.000000] efi: mem33: type=7, attr=0xf, range=[0x00000000900e7000-0x00000000900e9000) (0MB)
[    0.000000] efi: mem34: type=4, attr=0xf, range=[0x00000000900e9000-0x0000000090227000) (1MB)
[    0.000000] efi: mem35: type=3, attr=0xf, range=[0x0000000090227000-0x0000000090234000) (0MB)
[    0.000000] efi: mem36: type=4, attr=0xf, range=[0x0000000090234000-0x0000000090241000) (0MB)
[    0.000000] efi: mem37: type=7, attr=0xf, range=[0x0000000090241000-0x0000000090242000) (0MB)
[    0.000000] efi: mem38: type=4, attr=0xf, range=[0x0000000090242000-0x000000009025a000) (0MB)
[    0.000000] efi: mem39: type=7, attr=0xf, range=[0x000000009025a000-0x000000009025d000) (0MB)
[    0.000000] efi: mem40: type=4, attr=0xf, range=[0x000000009025d000-0x0000000090262000) (0MB)
[    0.000000] efi: mem41: type=7, attr=0xf, range=[0x0000000090262000-0x0000000090265000) (0MB)
[    0.000000] efi: mem42: type=4, attr=0xf, range=[0x0000000090265000-0x0000000090268000) (0MB)
[    0.000000] efi: mem43: type=7, attr=0xf, range=[0x0000000090268000-0x000000009026a000) (0MB)
[    0.000000] efi: mem44: type=4, attr=0xf, range=[0x000000009026a000-0x0000000090290000) (0MB)
[    0.000000] efi: mem45: type=7, attr=0xf, range=[0x0000000090290000-0x0000000090291000) (0MB)
[    0.000000] efi: mem46: type=4, attr=0xf, range=[0x0000000090291000-0x00000000922bf000) (32MB)
[    0.000000] efi: mem47: type=7, attr=0xf, range=[0x00000000922bf000-0x00000000922c3000) (0MB)
[    0.000000] efi: mem48: type=3, attr=0xf, range=[0x00000000922c3000-0x00000000926bf000) (3MB)
[    0.000000] efi: mem49: type=5, attr=0x800000000000000f, range=[0x00000000926bf000-0x00000000928bf000) (2MB)
[    0.000000] efi: mem50: type=6, attr=0x800000000000000f, range=[0x00000000928bf000-0x0000000092abf000) (2MB)
[    0.000000] efi: mem51: type=0, attr=0xf, range=[0x0000000092abf000-0x0000000092ebf000) (4MB)
[    0.000000] efi: mem52: type=10, attr=0xf, range=[0x0000000092ebf000-0x0000000092fbf000) (1MB)
[    0.000000] efi: mem53: type=9, attr=0xf, range=[0x0000000092fbf000-0x0000000092fff000) (0MB)
[    0.000000] efi: mem54: type=4, attr=0xf, range=[0x0000000092fff000-0x0000000093000000) (0MB)
[    0.000000] efi: mem55: type=7, attr=0xf, range=[0x0000000100000000-0x000000025f600000) (5622MB)
[    0.000000] efi: mem56: type=0, attr=0x0, range=[0x00000000000a0000-0x00000000000c0000) (0MB)
[    0.000000] efi: mem57: type=0, attr=0x0, range=[0x0000000093000000-0x000000009fa00000) (202MB)
[    0.000000] efi: mem58: type=11, attr=0x8000000000000001, range=[0x00000000e0000000-0x00000000f0000000) (256MB)
[    0.000000] efi: mem59: type=11, attr=0x8000000000000001, range=[0x00000000feb00000-0x00000000feb10000) (0MB)
[    0.000000] efi: mem60: type=11, attr=0x8000000000000001, range=[0x00000000fec00000-0x00000000fec01000) (0MB)
[    0.000000] efi: mem61: type=11, attr=0x8000000000000001, range=[0x00000000fed00000-0x00000000fed1c000) (0MB)
[    0.000000] efi: mem62: type=11, attr=0x8000000000000000, range=[0x00000000fed1c000-0x00000000fed20000) (0MB)
[    0.000000] efi: mem63: type=11, attr=0x8000000000000001, range=[0x00000000fed20000-0x00000000fee01000) (0MB)
[    0.000000] efi: mem64: type=11, attr=0x8000000000000000, range=[0x00000000ffb80000-0x0000000100000000) (4MB)
[    0.000000] SMBIOS 2.7 present.
[    0.000000] DMI: LENOVO 20287/AILZAZBZC, BIOS 8DCN26WW 09/23/2013
[    0.000000] e820: update [mem 0x00000000-0x00000fff] usable ==> reserved
[    0.000000] e820: remove [mem 0x000a0000-0x000fffff] usable
[    0.000000] No AGP bridge found
[    0.000000] e820: last_pfn = 0x25f600 max_arch_pfn = 0x400000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-E7FFF write-protect
[    0.000000]   E8000-EFFFF write-combining
[    0.000000]   F0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 0000000000 mask 7F80000000 write-back
[    0.000000]   1 base 0080000000 mask 7FF0000000 write-back
[    0.000000]   2 base 0090000000 mask 7FFE000000 write-back
[    0.000000]   3 base 0092000000 mask 7FFF000000 write-back
[    0.000000]   4 base 00FFB80000 mask 7FFFF80000 write-protect
[    0.000000]   5 base 00FFC00000 mask 7FFFC00000 write-protect
[    0.000000]   6 base 0100000000 mask 7F00000000 write-back
[    0.000000]   7 base 0200000000 mask 7F80000000 write-back
[    0.000000]   8 base 025F600000 mask 7FFFE00000 uncachable
[    0.000000]   9 base 025F800000 mask 7FFF800000 uncachable
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] e820: last_pfn = 0x93000 max_arch_pfn = 0x400000000
[    0.000000] Scanning 1 areas for low memory corruption
[    0.000000] Base memory trampoline at [ffff880000082000] 82000 size 24576
[    0.000000] Using GB pages for direct mapping
[    0.000000] init_memory_mapping: [mem 0x00000000-0x000fffff]
[    0.000000]  [mem 0x00000000-0x000fffff] page 4k
[    0.000000] BRK [0x02fd9000, 0x02fd9fff] PGTABLE
[    0.000000] BRK [0x02fda000, 0x02fdafff] PGTABLE
[    0.000000] BRK [0x02fdb000, 0x02fdbfff] PGTABLE
[    0.000000] init_memory_mapping: [mem 0x25f400000-0x25f5fffff]
[    0.000000]  [mem 0x25f400000-0x25f5fffff] page 2M
[    0.000000] BRK [0x02fdc000, 0x02fdcfff] PGTABLE
[    0.000000] init_memory_mapping: [mem 0x25c000000-0x25f3fffff]
[    0.000000]  [mem 0x25c000000-0x25f3fffff] page 2M
[    0.000000] init_memory_mapping: [mem 0x200000000-0x25bffffff]
[    0.000000]  [mem 0x200000000-0x23fffffff] page 1G
[    0.000000]  [mem 0x240000000-0x25bffffff] page 2M
[    0.000000] init_memory_mapping: [mem 0x00100000-0x8ccaffff]
[    0.000000]  [mem 0x00100000-0x001fffff] page 4k
[    0.000000]  [mem 0x00200000-0x3fffffff] page 2M
[    0.000000]  [mem 0x40000000-0x7fffffff] page 1G
[    0.000000]  [mem 0x80000000-0x8cbfffff] page 2M
[    0.000000]  [mem 0x8cc00000-0x8ccaffff] page 4k
[    0.000000] init_memory_mapping: [mem 0x8e0b0000-0x926befff]
[    0.000000]  [mem 0x8e0b0000-0x8e1fffff] page 4k
[    0.000000]  [mem 0x8e200000-0x925fffff] page 2M
[    0.000000]  [mem 0x92600000-0x926befff] page 4k
[    0.000000] BRK [0x02fdd000, 0x02fddfff] PGTABLE
[    0.000000] BRK [0x02fde000, 0x02fdefff] PGTABLE
[    0.000000] init_memory_mapping: [mem 0x92fff000-0x92ffffff]
[    0.000000]  [mem 0x92fff000-0x92ffffff] page 4k
[    0.000000] init_memory_mapping: [mem 0x100000000-0x1ffffffff]
[    0.000000]  [mem 0x100000000-0x1ffffffff] page 1G
[    0.000000] RAMDISK: [mem 0x35cbe000-0x36e56fff]
[    0.000000] ACPI: RSDP 0000000092ffe014 000024 (v02 LENOVO)
[    0.000000] ACPI: XSDT 0000000092ffe210 0000BC (v01 LENOVO CB-01    00000001      01000013)
[    0.000000] ACPI: FACP 0000000092ff7000 00010C (v05 LENOVO CB-01    00000001 ACPI 00040000)
[    0.000000] ACPI: DSDT 0000000092fe7000 00C042 (v01 LENOVO CB-01    00000001 ACPI 00040000)
[    0.000000] ACPI: FACS 0000000092fba000 000040
[    0.000000] ACPI: SLIC 0000000092ffd000 000176 (v01 LENOVO CB-01    00000001 ACPI 00040000)
[    0.000000] ACPI: UEFI 0000000092ffc000 000236 (v01 LENOVO CB-01    00000001 ACPI 00040000)
[    0.000000] ACPI: FPDT 0000000092ffa000 000044 (v01 LENOVO CB-01    00000001 ACPI 00040000)
[    0.000000] ACPI: POAT 0000000092ff9000 000055 (v03 LENOVO CB-01    00000001 ACPI 00040000)
[    0.000000] ACPI: ASF! 0000000092ff8000 0000A5 (v32 LENOVO CB-01    00000001 ACPI 00040000)
[    0.000000] ACPI: HPET 0000000092ff6000 000038 (v01 LENOVO CB-01    00000001 ACPI 00040000)
[    0.000000] ACPI: APIC 0000000092ff5000 00008C (v03 LENOVO CB-01    00000001 ACPI 00040000)
[    0.000000] ACPI: MCFG 0000000092ff4000 00003C (v01 LENOVO CB-01    00000001 ACPI 00040000)
[    0.000000] ACPI: SSDT 0000000092fe6000 0007F9 (v01 LENOVO CB-01    00000001 ACPI 00040000)
[    0.000000] ACPI: BOOT 0000000092fe4000 000028 (v01 LENOVO CB-01    00000001 ACPI 00040000)
[    0.000000] ACPI: ASPT 0000000092fe2000 000034 (v07 LENOVO CB-01    00000001 ACPI 00040000)
[    0.000000] ACPI: DBGP 0000000092fe1000 000034 (v01 LENOVO CB-01    00000001 ACPI 00040000)
[    0.000000] ACPI: SSDT 0000000092fd8000 000539 (v01 LENOVO CB-01    00000001 ACPI 00040000)
[    0.000000] ACPI: SSDT 0000000092fd7000 000AD8 (v01 LENOVO CB-01    00000001 ACPI 00040000)
[    0.000000] ACPI: SSDT 0000000092fd3000 0032D2 (v01 LENOVO CB-01    00000001 ACPI 00040000)
[    0.000000] ACPI: SSDT 0000000092fcd000 003BF1 (v01 LENOVO CB-01    00000001 ACPI 00040000)
[    0.000000] ACPI: DMAR 0000000092fd1000 000090 (v01 LENOVO CB-01    00000001 ACPI 00040000)
[    0.000000] ACPI: BGRT 0000000092fd2000 000038 (v01 LENOVO CB-01    00000001 ACPI 00040000)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at [mem 0x0000000000000000-0x000000025f5fffff]
[    0.000000] Initmem setup node 0 [mem 0x00000000-0x25f5fffff]
[    0.000000]   NODE_DATA [mem 0x25f5f8000-0x25f5fcfff]
[    0.000000]  [ffffea0000000000-ffffea00097fffff] PMD -> [ffff880256e00000-ffff88025ebfffff] on node 0
[    0.000000] Zone ranges:
[    0.000000]   DMA      [mem 0x00001000-0x00ffffff]
[    0.000000]   DMA32    [mem 0x01000000-0xffffffff]
[    0.000000]   Normal   [mem 0x100000000-0x25f5fffff]
[    0.000000] Movable zone start for each node
[    0.000000] Early memory node ranges
[    0.000000]   node   0: [mem 0x00001000-0x0006efff]
[    0.000000]   node   0: [mem 0x00070000-0x00087fff]
[    0.000000]   node   0: [mem 0x00100000-0x8ccaffff]
[    0.000000]   node   0: [mem 0x8e0b0000-0x926befff]
[    0.000000]   node   0: [mem 0x92fff000-0x92ffffff]
[    0.000000]   node   0: [mem 0x100000000-0x25f5fffff]
[    0.000000] On node 0 totalpages: 2033734
[    0.000000]   DMA zone: 64 pages used for memmap
[    0.000000]   DMA zone: 24 pages reserved
[    0.000000]   DMA zone: 3974 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 9227 pages used for memmap
[    0.000000]   DMA32 zone: 590528 pages, LIFO batch:31
[    0.000000]   Normal zone: 22488 pages used for memmap
[    0.000000]   Normal zone: 1439232 pages, LIFO batch:31
[    0.000000] ACPI: PM-Timer IO Port: 0x1808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x02] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x03] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x05] lapic_id[0x04] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x06] lapic_id[0x05] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x07] lapic_id[0x06] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x08] lapic_id[0x07] enabled)
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.000000] smpboot: Allowing 8 CPUs, 0 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] PM: Registered nosave memory: [mem 0x0006f000-0x0006ffff]
[    0.000000] PM: Registered nosave memory: [mem 0x00088000-0x000bffff]
[    0.000000] PM: Registered nosave memory: [mem 0x000c0000-0x000fffff]
[    0.000000] PM: Registered nosave memory: [mem 0x8ccb0000-0x8e0affff]
[    0.000000] PM: Registered nosave memory: [mem 0x926bf000-0x928befff]
[    0.000000] PM: Registered nosave memory: [mem 0x928bf000-0x92ebefff]
[    0.000000] PM: Registered nosave memory: [mem 0x92ebf000-0x92fbefff]
[    0.000000] PM: Registered nosave memory: [mem 0x92fbf000-0x92ffefff]
[    0.000000] PM: Registered nosave memory: [mem 0x93000000-0x9f9fffff]
[    0.000000] PM: Registered nosave memory: [mem 0x9fa00000-0xdfffffff]
[    0.000000] PM: Registered nosave memory: [mem 0xe0000000-0xefffffff]
[    0.000000] PM: Registered nosave memory: [mem 0xf0000000-0xfeafffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfeb00000-0xfeb0ffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfeb10000-0xfebfffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfec00000-0xfec00fff]
[    0.000000] PM: Registered nosave memory: [mem 0xfec01000-0xfecfffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfed00000-0xfee00fff]
[    0.000000] PM: Registered nosave memory: [mem 0xfee01000-0xffb7ffff]
[    0.000000] PM: Registered nosave memory: [mem 0xffb80000-0xffffffff]
[    0.000000] e820: [mem 0x9fa00000-0xdfffffff] available for PCI devices
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:256 nr_cpumask_bits:256 nr_cpu_ids:8 nr_node_ids:1
[    0.000000] PERCPU: Embedded 29 pages/cpu @ffff88025f200000 s86528 r8192 d24064 u262144
[    0.000000] pcpu-alloc: s86528 r8192 d24064 u262144 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 0 1 2 3 4 5 6 7 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 2001931
[    0.000000] Policy zone: Normal
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.14.1-031401-generic root=UUID=bef5bda4-93bb-479d-9994-5e0987da907e ro quiet splash vt.handoff=7
[    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
[    0.000000] xsave: enabled xstate_bv 0x7, cntxt size 0x340
[    0.000000] Checking aperture...
[    0.000000] No AGP bridge found
[    0.000000] Calgary: detecting Calgary via BIOS EBDA area
[    0.000000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[    0.000000] ------------[ cut here ]------------
[    0.000000] WARNING: CPU: 0 PID: 0 at /home/apw/COD/linux/drivers/iommu/dmar.c:503 warn_invalid_dmar+0x80/0x90()
[    0.000000] Your BIOS is broken; DMAR reported at address 0!
[    0.000000] BIOS vendor: LENOVO; Ver: 8DCN26WW; Product Version: Lenovo IdeaPad Z510
[    0.000000] Modules linked in:
[    0.000000] CPU: 0 PID: 0 Comm: swapper Not tainted 3.14.1-031401-generic #201404141220
[    0.000000] Hardware name: LENOVO 20287/AILZAZBZC, BIOS 8DCN26WW 09/23/2013
[    0.000000]  00000000000001f7 ffffffff81c01da8 ffffffff8175bbf5 0000000000000d3e
[    0.000000]  ffffffff81c01df8 ffffffff81c01de8 ffffffff8106ac9c ffffffff81c01e38
[    0.000000]  ffffffff81fd8008 ffffffff81fd8030 0000ffffffff81d2 00000000ffffffff
[    0.000000] Call Trace:
[    0.000000]  [<ffffffff8175bbf5>] dump_stack+0x46/0x58
[    0.000000]  [<ffffffff8106ac9c>] warn_slowpath_common+0x8c/0xc0
[    0.000000]  [<ffffffff8106ad2f>] warn_slowpath_fmt_taint+0x3f/0x50
[    0.000000]  [<ffffffff81746ae2>] ? acpi_os_map_memory+0x28/0x156
[    0.000000]  [<ffffffff817610dd>] warn_invalid_dmar+0x80/0x90
[    0.000000]  [<ffffffff81d83a63>] check_zero_address+0x57/0xf7
[    0.000000]  [<ffffffff81d2d120>] ? early_idt_handlers+0x120/0x120
[    0.000000]  [<ffffffff81d83b17>] detect_intel_iommu+0x14/0x81
[    0.000000]  [<ffffffff81d38662>] pci_iommu_alloc+0x44/0x6e
[    0.000000]  [<ffffffff81d481c5>] mem_init+0x11/0xa2
[    0.000000]  [<ffffffff81d2d120>] ? early_idt_handlers+0x120/0x120
[    0.000000]  [<ffffffff81d2dd8d>] start_kernel+0x16d/0x3ac
[    0.000000]  [<ffffffff81d2dab2>] ? repair_env_string+0x5a/0x5a
[    0.000000]  [<ffffffff8174a81f>] ? memblock_reserve+0x49/0x4e
[    0.000000]  [<ffffffff81d2d5f8>] x86_64_start_reservations+0x2a/0x2c
[    0.000000]  [<ffffffff81d2d739>] x86_64_start_kernel+0x13f/0x14e
[    0.000000] ---[ end trace 6405b9ce732cb54f ]---
[    0.000000] Memory: 7833424K/8134936K available (7642K kernel code, 1109K rwdata, 3592K rodata, 1356K init, 1432K bss, 301512K reserved)
[    0.000000] SLUB: HWalign=64, Order=0-3, MinObjects=0, CPUs=8, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000]     RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000]     RCU restricting CPUs from NR_CPUS=256 to nr_cpu_ids=8.
[    0.000000]     Offload RCU callbacks from all CPUs
[    0.000000]     Offload RCU callbacks from CPUs: 0-7.
[    0.000000] RCU: Adjusting geometry for rcu_fanout_leaf=16, nr_cpu_ids=8
[    0.000000] NR_IRQS:16640 nr_irqs:744 16
[    0.000000] Console: colour dummy device 80x25
[    0.000000] console [tty0] enabled
[    0.000000] allocated 33030144 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] hpet clockevent registered
[    0.000000] tsc: Fast TSC calibration using PIT
[    0.000000] tsc: Detected 2194.903 MHz processor
[    0.000030] Calibrating delay loop (skipped), value calculated using timer frequency.. 4389.80 BogoMIPS (lpj=8779612)
[    0.000032] pid_max: default: 32768 minimum: 301
[    0.000039] ACPI: Core revision 20131218
[    0.009715] ACPI: All ACPI Tables successfully acquired
[    0.029016] Security Framework initialized
[    0.029029] AppArmor: AppArmor initialized
[    0.029030] Yama: becoming mindful.
[    0.029617] Dentry cache hash table entries: 1048576 (order: 11, 8388608 bytes)
[    0.031061] Inode-cache hash table entries: 524288 (order: 10, 4194304 bytes)
[    0.031651] Mount-cache hash table entries: 16384 (order: 5, 131072 bytes)
[    0.031661] Mountpoint-cache hash table entries: 16384 (order: 5, 131072 bytes)
[    0.031850] Initializing cgroup subsys memory
[    0.031855] Initializing cgroup subsys devices
[    0.031856] Initializing cgroup subsys freezer
[    0.031857] Initializing cgroup subsys net_cls
[    0.031859] Initializing cgroup subsys blkio
[    0.031860] Initializing cgroup subsys perf_event
[    0.031862] Initializing cgroup subsys hugetlb
[    0.031886] CPU: Physical Processor ID: 0
[    0.031887] CPU: Processor Core ID: 0
[    0.031891] ENERGY_PERF_BIAS: Set to 'normal', was 'performance'
[    0.031891] ENERGY_PERF_BIAS: View and update with x86_energy_perf_policy(8)
[    0.032836] mce: CPU supports 9 MCE banks
[    0.032851] CPU0: Thermal monitoring enabled (TM1)
[    0.032864] Last level iTLB entries: 4KB 1024, 2MB 1024, 4MB 1024
[    0.032864] Last level dTLB entries: 4KB 1024, 2MB 1024, 4MB 1024, 1GB 4
[    0.032864] tlb_flushall_shift: 6
[    0.032968] Freeing SMP alternatives memory: 28K (ffffffff81e6a000 - ffffffff81e71000)
[    0.036489] ftrace: allocating 31510 entries in 124 pages
[    0.049725] dmar: Host address width 39
[    0.049727] dmar: DRHD base: 0x00000000000000 flags: 0x1
[    0.049728] dmar: parse DMAR table failure.
[    0.050135] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.089859] smpboot: CPU0: Intel(R) Core(TM) i7-4702MQ CPU @ 2.20GHz (fam: 06, model: 3c, stepping: 03)
[    0.089867] TSC deadline timer enabled
[    0.091794] Performance Events: PEBS fmt2+, 16-deep LBR, Haswell events, full-width counters, Intel PMU driver.
[    0.091801] ... version:                3
[    0.091802] ... bit width:              48
[    0.091803] ... generic registers:      4
[    0.091804] ... value mask:             0000ffffffffffff
[    0.091805] ... max period:             0000ffffffffffff
[    0.091806] ... fixed-purpose events:   3
[    0.091807] ... event mask:             000000070000000f
[    0.093348] x86: Booting SMP configuration:
[    0.093350] .... node  #0, CPUs:      #1
[    0.107551] TSC synchronization [CPU#0 -> CPU#1]:
[    0.107554] Measured 761953297 cycles TSC warp between CPUs, turning off TSC clock.
[    0.107559] tsc: Marking TSC unstable due to check_tsc_sync_source failed
[    0.107680] NMI watchdog: enabled on all CPUs, permanently consumes one hw-PMU counter.
[    0.008000]  #2 #3 #4 #5 #6 #7
[    0.177384] x86: Booted up 1 node, 8 CPUs
[    0.177387] smpboot: Total of 8 processors activated (35118.44 BogoMIPS)
[    0.180118] devtmpfs: initialized
[    0.184433] EVM: security.selinux
[    0.184435] EVM: security.SMACK64
[    0.184436] EVM: security.ima
[    0.184437] EVM: security.capability
[    0.184451] PM: Registering ACPI NVS region [mem 0x92ebf000-0x92fbefff] (1048576 bytes)
[    0.184784] pinctrl core: initialized pinctrl subsystem
[    0.184845] regulator-dummy: no parameters
[    0.184876] RTC time: 16:02:47, date: 05/14/14
[    0.184907] NET: Registered protocol family 16
[    0.185020] cpuidle: using governor ladder
[    0.185021] cpuidle: using governor menu
[    0.185060] ACPI FADT declares the system doesn't support PCIe ASPM, so disable it
[    0.185062] ACPI: bus type PCI registered
[    0.185063] acpiphp: ACPI Hot Plug PCI Controller Driver version: 0.5
[    0.185124] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[    0.185127] PCI: MMCONFIG at [mem 0xe0000000-0xefffffff] reserved in E820
[    0.211456] PCI: Using configuration type 1 for base access
[    0.212529] bio: create slab <bio-0> at 0
[    0.212529] ACPI: Added _OSI(Module Device)
[    0.212529] ACPI: Added _OSI(Processor Device)
[    0.212529] ACPI: Added _OSI(3.0 _SCP Extensions)
[    0.212529] ACPI: Added _OSI(Processor Aggregator Device)
[    0.217900] ACPI: Executed 1 blocks of module-level executable AML code
[    0.221248] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
[    0.222582] ACPI: SSDT 0000000092e57c18 0003D3 (v01  PmRef  Cpu0Cst 00003001 INTL 20121220)
[    0.223223] ACPI: Dynamic OEM Table Load:
[    0.223225] ACPI: SSDT           (null) 0003D3 (v01  PmRef  Cpu0Cst 00003001 INTL 20121220)
[    0.224222] ACPI: SSDT 0000000092e57618 0005AA (v01  PmRef    ApIst 00003000 INTL 20121220)
[    0.224934] ACPI: Dynamic OEM Table Load:
[    0.224936] ACPI: SSDT           (null) 0005AA (v01  PmRef    ApIst 00003000 INTL 20121220)
[    0.228111] ACPI: SSDT 0000000092e61c18 000119 (v01  PmRef    ApCst 00003000 INTL 20121220)
[    0.228758] ACPI: Dynamic OEM Table Load:
[    0.228761] ACPI: SSDT           (null) 000119 (v01  PmRef    ApCst 00003000 INTL 20121220)
[    0.233397] ACPI: Interpreter enabled
[    0.233404] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S1_] (20131218/hwxface-580)
[    0.233410] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S2_] (20131218/hwxface-580)
[    0.233428] ACPI: (supports S0 S3 S4 S5)
[    0.233429] ACPI: Using IOAPIC for interrupt routing
[    0.233455] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.233660] ACPI: No dock devices found.
[    0.245476] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-fe])
[    0.245482] acpi PNP0A08:00: _OSC: OS supports [ExtendedConfig ASPM ClockPM Segments MSI]
[    0.245993] acpi PNP0A08:00: _OSC: OS now controls [PCIeHotplug PME AER PCIeCapability]
[    0.246571] PCI host bridge to bus 0000:00
[    0.246574] pci_bus 0000:00: root bus resource [bus 00-fe]
[    0.246576] pci_bus 0000:00: root bus resource [io  0x0000-0x0cf7]
[    0.246578] pci_bus 0000:00: root bus resource [io  0x0d00-0xffff]
[    0.246579] pci_bus 0000:00: root bus resource [mem 0x000a0000-0x000bffff]
[    0.246581] pci_bus 0000:00: root bus resource [mem 0x000c0000-0x000c3fff]
[    0.246582] pci_bus 0000:00: root bus resource [mem 0x000c4000-0x000c7fff]
[    0.246584] pci_bus 0000:00: root bus resource [mem 0x000c8000-0x000cbfff]
[    0.246585] pci_bus 0000:00: root bus resource [mem 0x000cc000-0x000cffff]
[    0.246587] pci_bus 0000:00: root bus resource [mem 0x000d0000-0x000d3fff]
[    0.246588] pci_bus 0000:00: root bus resource [mem 0x000d4000-0x000d7fff]
[    0.246590] pci_bus 0000:00: root bus resource [mem 0x000d8000-0x000dbfff]
[    0.246591] pci_bus 0000:00: root bus resource [mem 0x000dc000-0x000dffff]
[    0.246593] pci_bus 0000:00: root bus resource [mem 0x9fa00000-0xfeafffff]
[    0.246600] pci 0000:00:00.0: [8086:0c04] type 00 class 0x060000
[    0.246745] pci 0000:00:01.0: [8086:0c01] type 01 class 0x060400
[    0.246782] pci 0000:00:01.0: PME# supported from D0 D3hot D3cold
[    0.246887] pci 0000:00:01.0: System wakeup disabled by ACPI
[    0.246923] pci 0000:00:01.1: [8086:0c05] type 01 class 0x060400
[    0.246959] pci 0000:00:01.1: PME# supported from D0 D3hot D3cold
[    0.247062] pci 0000:00:01.1: System wakeup disabled by ACPI
[    0.247099] pci 0000:00:02.0: [8086:0416] type 00 class 0x030000
[    0.247111] pci 0000:00:02.0: reg 0x10: [mem 0xb5000000-0xb53fffff 64bit]
[    0.247118] pci 0000:00:02.0: reg 0x18: [mem 0xc0000000-0xcfffffff 64bit pref]
[    0.247123] pci 0000:00:02.0: reg 0x20: [io  0x6000-0x603f]
[    0.247260] pci 0000:00:03.0: [8086:0c0c] type 00 class 0x040300
[    0.247268] pci 0000:00:03.0: reg 0x10: [mem 0xb5710000-0xb5713fff 64bit]
[    0.247433] pci 0000:00:14.0: [8086:8c31] type 00 class 0x0c0330
[    0.247454] pci 0000:00:14.0: reg 0x10: [mem 0xb5700000-0xb570ffff 64bit]
[    0.247517] pci 0000:00:14.0: PME# supported from D3hot D3cold
[    0.247612] pci 0000:00:14.0: System wakeup disabled by ACPI
[    0.247650] pci 0000:00:16.0: [8086:8c3a] type 00 class 0x078000
[    0.247672] pci 0000:00:16.0: reg 0x10: [mem 0xb5718000-0xb571800f 64bit]
[    0.247740] pci 0000:00:16.0: PME# supported from D0 D3hot D3cold
[    0.247881] pci 0000:00:1a.0: [8086:8c2d] type 00 class 0x0c0320
[    0.247903] pci 0000:00:1a.0: reg 0x10: [mem 0xb571d000-0xb571d3ff]
[    0.247995] pci 0000:00:1a.0: PME# supported from D0 D3hot D3cold
[    0.248104] pci 0000:00:1a.0: System wakeup disabled by ACPI
[    0.248146] pci 0000:00:1b.0: [8086:8c20] type 00 class 0x040300
[    0.248162] pci 0000:00:1b.0: reg 0x10: [mem 0xb5714000-0xb5717fff 64bit]
[    0.248236] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.248365] pci 0000:00:1c.0: [8086:8c16] type 01 class 0x060400
[    0.248437] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.248535] pci 0000:00:1c.0: System wakeup disabled by ACPI
[    0.248577] pci 0000:00:1c.4: [8086:8c18] type 01 class 0x060400
[    0.248654] pci 0000:00:1c.4: PME# supported from D0 D3hot D3cold
[    0.248754] pci 0000:00:1c.4: System wakeup disabled by ACPI
[    0.248797] pci 0000:00:1d.0: [8086:8c26] type 00 class 0x0c0320
[    0.248820] pci 0000:00:1d.0: reg 0x10: [mem 0xb571c000-0xb571c3ff]
[    0.248912] pci 0000:00:1d.0: PME# supported from D0 D3hot D3cold
[    0.249020] pci 0000:00:1d.0: System wakeup disabled by ACPI
[    0.249060] pci 0000:00:1f.0: [8086:8c49] type 00 class 0x060100
[    0.249286] pci 0000:00:1f.2: [8086:8c03] type 00 class 0x010601
[    0.249303] pci 0000:00:1f.2: reg 0x10: [io  0x6088-0x608f]
[    0.249312] pci 0000:00:1f.2: reg 0x14: [io  0x6094-0x6097]
[    0.249321] pci 0000:00:1f.2: reg 0x18: [io  0x6080-0x6087]
[    0.249329] pci 0000:00:1f.2: reg 0x1c: [io  0x6090-0x6093]
[    0.249338] pci 0000:00:1f.2: reg 0x20: [io  0x6060-0x607f]
[    0.249348] pci 0000:00:1f.2: reg 0x24: [mem 0xb571b000-0xb571b7ff]
[    0.249389] pci 0000:00:1f.2: PME# supported from D3hot
[    0.249512] pci 0000:00:1f.3: [8086:8c22] type 00 class 0x0c0500
[    0.249529] pci 0000:00:1f.3: reg 0x10: [mem 0xb5719000-0xb57190ff 64bit]
[    0.249552] pci 0000:00:1f.3: reg 0x20: [io  0x6040-0x605f]
[    0.249727] pci 0000:00:01.0: PCI bridge to [bus 01-06]
[    0.249730] pci 0000:00:01.0:   bridge window [io  0x5000-0x5fff]
[    0.249733] pci 0000:00:01.0:   bridge window [mem 0xb4000000-0xb4ffffff]
[    0.249737] pci 0000:00:01.0:   bridge window [mem 0xb2000000-0xb2ffffff 64bit pref]
[    0.249791] pci 0000:07:00.0: [10de:1292] type 00 class 0x030200
[    0.249804] pci 0000:07:00.0: reg 0x10: [mem 0xb3000000-0xb3ffffff]
[    0.249819] pci 0000:07:00.0: reg 0x14: [mem 0xa0000000-0xafffffff 64bit pref]
[    0.249834] pci 0000:07:00.0: reg 0x1c: [mem 0xb0000000-0xb1ffffff 64bit pref]
[    0.249843] pci 0000:07:00.0: reg 0x24: [io  0x4000-0x407f]
[    0.249854] pci 0000:07:00.0: reg 0x30: [mem 0xfff80000-0xffffffff pref]
[    0.256013] pci 0000:00:01.1: PCI bridge to [bus 07]
[    0.256016] pci 0000:00:01.1:   bridge window [io  0x4000-0x4fff]
[    0.256018] pci 0000:00:01.1:   bridge window [mem 0xb3000000-0xb3ffffff]
[    0.256022] pci 0000:00:01.1:   bridge window [mem 0xa0000000-0xb1ffffff 64bit pref]
[    0.256168] pci 0000:08:00.0: [10ec:8136] type 00 class 0x020000
[    0.256234] pci 0000:08:00.0: reg 0x10: [io  0x3000-0x30ff]
[    0.256350] pci 0000:08:00.0: reg 0x18: [mem 0xb5600000-0xb5600fff 64bit]
[    0.256422] pci 0000:08:00.0: reg 0x20: [mem 0xb5400000-0xb5403fff 64bit pref]
[    0.256604] pci 0000:08:00.0: supports D1 D2
[    0.256606] pci 0000:08:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.256663] pci 0000:08:00.0: System wakeup disabled by ACPI
[    0.264036] pci 0000:00:1c.0: PCI bridge to [bus 08]
[    0.264040] pci 0000:00:1c.0:   bridge window [io  0x3000-0x3fff]
[    0.264044] pci 0000:00:1c.0:   bridge window [mem 0xb5600000-0xb56fffff]
[    0.264050] pci 0000:00:1c.0:   bridge window [mem 0xb5400000-0xb54fffff 64bit pref]
[    0.264180] pci 0000:09:00.0: [8086:08b2] type 00 class 0x028000
[    0.264239] pci 0000:09:00.0: reg 0x10: [mem 0xb5500000-0xb5501fff 64bit]
[    0.264481] pci 0000:09:00.0: PME# supported from D0 D3hot D3cold
[    0.264535] pci 0000:09:00.0: System wakeup disabled by ACPI
[    0.272031] pci 0000:00:1c.4: PCI bridge to [bus 09]
[    0.272037] pci 0000:00:1c.4:   bridge window [mem 0xb5500000-0xb55fffff]
[    0.272079] acpi PNP0A08:00: Disabling ASPM (FADT indicates it is unsupported)
[    0.272570] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 10 11 12 14 15) *0, disabled.
[    0.272617] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 10 11 12 14 15) *0, disabled.
[    0.272661] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 10 11 12 14 15) *0, disabled.
[    0.272705] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 10 11 12 14 15) *0, disabled.
[    0.272750] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 10 11 12 14 15) *0, disabled.
[    0.272793] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 10 11 12 14 15) *0, disabled.
[    0.272835] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 10 11 12 14 15) *0, disabled.
[    0.272879] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 10 11 12 14 15) *0, disabled.
[    0.273042] ACPI: Enabled 6 GPEs in block 00 to 3F
[    0.273077] ACPI : EC: GPE = 0x17, I/O: command/status = 0x66, data = 0x62
[    0.273155] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
[    0.273155] vgaarb: loaded
[    0.273155] vgaarb: bridge control possible 0000:00:02.0
[    0.273155] SCSI subsystem initialized
[    0.273155] libata version 3.00 loaded.
[    0.273155] ACPI: bus type USB registered
[    0.273155] usbcore: registered new interface driver usbfs
[    0.273155] usbcore: registered new interface driver hub
[    0.273155] usbcore: registered new device driver usb
[    0.273155] PCI: Using ACPI for IRQ routing
[    0.279510] PCI: pci_cache_line_size set to 64 bytes
[    0.279563] e820: reserve RAM buffer [mem 0x0006f000-0x0006ffff]
[    0.279565] e820: reserve RAM buffer [mem 0x00088000-0x0008ffff]
[    0.279566] e820: reserve RAM buffer [mem 0x8ccb0000-0x8fffffff]
[    0.279567] e820: reserve RAM buffer [mem 0x926bf000-0x93ffffff]
[    0.279569] e820: reserve RAM buffer [mem 0x93000000-0x93ffffff]
[    0.279570] e820: reserve RAM buffer [mem 0x25f600000-0x25fffffff]
[    0.279650] NetLabel: Initializing
[    0.279652] NetLabel:  domain hash size = 128
[    0.279652] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.279663] NetLabel:  unlabeled traffic allowed by default
[    0.279676] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0, 0, 0, 0, 0
[    0.279676] hpet0: 8 comparators, 64-bit 14.318180 MHz counter
[    0.281032] Switched to clocksource hpet
[    0.285247] AppArmor: AppArmor Filesystem Enabled
[    0.285270] pnp: PnP ACPI init
[    0.285283] ACPI: bus type PNP registered
[    0.285384] pnp 00:00: [dma 4]
[    0.285407] pnp 00:00: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.285428] pnp 00:01: Plug and Play ACPI device, IDs INT0800 (active)
[    0.285523] pnp 00:02: Plug and Play ACPI device, IDs PNP0103 (active)
[    0.285568] pnp 00:03: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.285612] system 00:04: [io  0x0680-0x069f] has been reserved
[    0.285615] system 00:04: [io  0xffff] has been reserved
[    0.285617] system 00:04: [io  0xffff] has been reserved
[    0.285619] system 00:04: [io  0xffff] has been reserved
[    0.285621] system 00:04: [io  0x1800-0x18fe] could not be reserved
[    0.285623] system 00:04: [io  0x164e-0x164f] has been reserved
[    0.285626] system 00:04: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.285670] system 00:05: [io  0x0800-0x087f] has been reserved
[    0.285672] system 00:05: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.285699] pnp 00:06: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.285743] system 00:07: [io  0x1854-0x1857] has been reserved
[    0.285746] system 00:07: Plug and Play ACPI device, IDs INT3f0d PNP0c02 (active)
[    0.285802] pnp 00:08: Plug and Play ACPI device, IDs PNP0303 (active)
[    0.285835] pnp 00:09: Plug and Play ACPI device, IDs SYN2b2a PNP0f13 (active)
[    0.285946] pnp 00:0a: disabling [mem 0xffffffff-0x100000ffe] because it overlaps 0000:07:00.0 BAR 6 [mem 0xfff80000-0xffffffff pref]
[    0.285968] system 00:0a: [mem 0xfed1c000-0xfed1ffff] has been reserved
[    0.285970] system 00:0a: [mem 0xfed10000-0xfed17fff] has been reserved
[    0.285972] system 00:0a: [mem 0xfed18000-0xfed18fff] has been reserved
[    0.285974] system 00:0a: [mem 0xfed19000-0xfed19fff] has been reserved
[    0.285977] system 00:0a: [mem 0xe0000000-0xefffffff] has been reserved
[    0.285979] system 00:0a: [mem 0xfed20000-0xfed3ffff] has been reserved
[    0.285981] system 00:0a: [mem 0xfed90000-0xfed93fff] has been reserved
[    0.285983] system 00:0a: [mem 0xff000000-0xffffffff] could not be reserved
[    0.285985] system 00:0a: [mem 0xfee00000-0xfeefffff] could not be reserved
[    0.285987] system 00:0a: [mem 0x9fa10000-0x9fa10fff] has been reserved
[    0.285990] system 00:0a: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.286543] pnp: PnP ACPI: found 11 devices
[    0.286544] ACPI: bus type PNP unregistered
[    0.293009] pci 0000:07:00.0: no compatible bridge window for [mem 0xfff80000-0xffffffff pref]
[    0.293037] pci 0000:00:01.0: PCI bridge to [bus 01-06]
[    0.293040] pci 0000:00:01.0:   bridge window [io  0x5000-0x5fff]
[    0.293043] pci 0000:00:01.0:   bridge window [mem 0xb4000000-0xb4ffffff]
[    0.293046] pci 0000:00:01.0:   bridge window [mem 0xb2000000-0xb2ffffff 64bit pref]
[    0.293052] pci 0000:07:00.0: BAR 6: can't assign mem pref (size 0x80000)
[    0.293055] pci 0000:00:01.1: PCI bridge to [bus 07]
[    0.293057] pci 0000:00:01.1:   bridge window [io  0x4000-0x4fff]
[    0.293059] pci 0000:00:01.1:   bridge window [mem 0xb3000000-0xb3ffffff]
[    0.293062] pci 0000:00:01.1:   bridge window [mem 0xa0000000-0xb1ffffff 64bit pref]
[    0.293066] pci 0000:00:1c.0: PCI bridge to [bus 08]
[    0.293069] pci 0000:00:1c.0:   bridge window [io  0x3000-0x3fff]
[    0.293074] pci 0000:00:1c.0:   bridge window [mem 0xb5600000-0xb56fffff]
[    0.293078] pci 0000:00:1c.0:   bridge window [mem 0xb5400000-0xb54fffff 64bit pref]
[    0.293084] pci 0000:00:1c.4: PCI bridge to [bus 09]
[    0.293089] pci 0000:00:1c.4:   bridge window [mem 0xb5500000-0xb55fffff]
[    0.293099] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    0.293101] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    0.293102] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    0.293104] pci_bus 0000:00: resource 7 [mem 0x000c0000-0x000c3fff]
[    0.293105] pci_bus 0000:00: resource 8 [mem 0x000c4000-0x000c7fff]
[    0.293107] pci_bus 0000:00: resource 9 [mem 0x000c8000-0x000cbfff]
[    0.293108] pci_bus 0000:00: resource 10 [mem 0x000cc000-0x000cffff]
[    0.293110] pci_bus 0000:00: resource 11 [mem 0x000d0000-0x000d3fff]
[    0.293111] pci_bus 0000:00: resource 12 [mem 0x000d4000-0x000d7fff]
[    0.293113] pci_bus 0000:00: resource 13 [mem 0x000d8000-0x000dbfff]
[    0.293114] pci_bus 0000:00: resource 14 [mem 0x000dc000-0x000dffff]
[    0.293116] pci_bus 0000:00: resource 15 [mem 0x9fa00000-0xfeafffff]
[    0.293118] pci_bus 0000:01: resource 0 [io  0x5000-0x5fff]
[    0.293119] pci_bus 0000:01: resource 1 [mem 0xb4000000-0xb4ffffff]
[    0.293121] pci_bus 0000:01: resource 2 [mem 0xb2000000-0xb2ffffff 64bit pref]
[    0.293122] pci_bus 0000:07: resource 0 [io  0x4000-0x4fff]
[    0.293124] pci_bus 0000:07: resource 1 [mem 0xb3000000-0xb3ffffff]
[    0.293125] pci_bus 0000:07: resource 2 [mem 0xa0000000-0xb1ffffff 64bit pref]
[    0.293127] pci_bus 0000:08: resource 0 [io  0x3000-0x3fff]
[    0.293129] pci_bus 0000:08: resource 1 [mem 0xb5600000-0xb56fffff]
[    0.293130] pci_bus 0000:08: resource 2 [mem 0xb5400000-0xb54fffff 64bit pref]
[    0.293132] pci_bus 0000:09: resource 1 [mem 0xb5500000-0xb55fffff]
[    0.293157] NET: Registered protocol family 2
[    0.293290] TCP established hash table entries: 65536 (order: 7, 524288 bytes)
[    0.293420] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.293543] TCP: Hash tables configured (established 65536 bind 65536)
[    0.293558] TCP: reno registered
[    0.293569] UDP hash table entries: 4096 (order: 5, 131072 bytes)
[    0.293596] UDP-Lite hash table entries: 4096 (order: 5, 131072 bytes)
[    0.293653] NET: Registered protocol family 1
[    0.293665] pci 0000:00:02.0: Boot video device
[    0.328128] PCI: CLS 64 bytes, default 64
[    0.328167] Trying to unpack rootfs image as initramfs...
[    0.624996] Freeing initrd memory: 18020K (ffff880035cbe000 - ffff880036e57000)
[    0.625001] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
[    0.625004] software IO TLB [mem 0x870c0000-0x8b0c0000] (64MB) mapped at [ffff8800870c0000-ffff88008b0bffff]
[    0.625066] Simple Boot Flag at 0x44 set to 0x1
[    0.625325] RAPL PMU detected, hw unit 2^-14 Joules, API unit is 2^-32 Joules, 3 fixed counters 655360 ms ovfl timer
[    0.625367] Scanning for low memory corruption every 60 seconds
[    0.625673] futex hash table entries: 2048 (order: 5, 131072 bytes)
[    0.625692] Initialise system trusted keyring
[    0.625728] audit: initializing netlink subsys (disabled)
[    0.625741] audit: type=2000 audit(1400083367.624:1): initialized
[    0.654133] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.655406] zbud: loaded
[    0.655547] VFS: Disk quotas dquot_6.5.2
[    0.655588] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    0.656028] fuse init (API version 7.22)
[    0.656108] msgmni has been set to 15473
[    0.656156] Key type big_key registered
[    0.656623] Key type asymmetric registered
[    0.656624] Asymmetric key parser 'x509' registered
[    0.656654] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 252)
[    0.656698] io scheduler noop registered
[    0.656699] io scheduler deadline registered (default)
[    0.656724] io scheduler cfq registered
[    0.656785] pcieport 0000:00:01.0: device [8086:0c01] has invalid IRQ; check vendor BIOS
[    0.656910] pcieport 0000:00:01.0: irq 40 for MSI/MSI-X
[    0.656960] pcieport 0000:00:01.1: device [8086:0c05] has invalid IRQ; check vendor BIOS
[    0.657045] pcieport 0000:00:01.1: irq 41 for MSI/MSI-X
[    0.657091] pcieport 0000:00:1c.0: device [8086:8c16] has invalid IRQ; check vendor BIOS
[    0.657185] pcieport 0000:00:1c.0: irq 42 for MSI/MSI-X
[    0.657238] pcieport 0000:00:1c.4: device [8086:8c18] has invalid IRQ; check vendor BIOS
[    0.657332] pcieport 0000:00:1c.4: irq 43 for MSI/MSI-X
[    0.657405] pcieport 0000:00:01.0: Signaling PME through PCIe PME interrupt
[    0.657408] pcie_pme 0000:00:01.0:pcie01: service driver pcie_pme loaded
[    0.657420] pcieport 0000:00:01.1: Signaling PME through PCIe PME interrupt
[    0.657421] pci 0000:07:00.0: Signaling PME through PCIe PME interrupt
[    0.657424] pcie_pme 0000:00:01.1:pcie01: service driver pcie_pme loaded
[    0.657439] pcieport 0000:00:1c.0: Signaling PME through PCIe PME interrupt
[    0.657441] pci 0000:08:00.0: Signaling PME through PCIe PME interrupt
[    0.657445] pcie_pme 0000:00:1c.0:pcie01: service driver pcie_pme loaded
[    0.657461] pcieport 0000:00:1c.4: Signaling PME through PCIe PME interrupt
[    0.657462] pci 0000:09:00.0: Signaling PME through PCIe PME interrupt
[    0.657466] pcie_pme 0000:00:1c.4:pcie01: service driver pcie_pme loaded
[    0.657477] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.657491] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.657532] efifb: probing for efifb
[    0.657979] efifb: framebuffer at 0xc0000000, mapped to 0xffffc90010f00000, using 4160k, total 4160k
[    0.657980] efifb: mode is 1366x768x32, linelength=5504, pages=1
[    0.657981] efifb: scrolling: redraw
[    0.657983] efifb: Truecolor: size=8:8:8:8, shift=24:16:8:0
[    0.660249] Console: switching to colour frame buffer device 170x48
[    0.662377] fb0: EFI VGA frame buffer device
[    0.662389] intel_idle: MWAIT substates: 0x42120
[    0.662390] intel_idle: v0.4 model 0x3C
[    0.662391] intel_idle: lapic_timer_reliable_states 0xffffffff
[    0.668135] ACPI: AC Adapter [ADP0] (on-line)
[    0.668276] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input0
[    0.668294] ACPI: Lid Switch [LID0]
[    0.668328] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[    0.668331] ACPI: Power Button [PWRB]
[    0.668363] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
[    0.668365] ACPI: Power Button [PWRF]
[    0.668777] GHES: HEST is not enabled!
[    0.668866] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    0.670382] Linux agpgart interface v0.103
[    0.671664] brd: module loaded
[    0.672326] loop: module loaded
[    0.672673] libphy: Fixed MDIO Bus: probed
[    0.672756] tun: Universal TUN/TAP device driver, 1.6
[    0.672757] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.672792] PPP generic driver version 2.4.2
[    0.672830] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.672833] ehci-pci: EHCI PCI platform driver
[    0.672946] ehci-pci 0000:00:1a.0: EHCI Host Controller
[    0.672951] ehci-pci 0000:00:1a.0: new USB bus registered, assigned bus number 1
[    0.672964] ehci-pci 0000:00:1a.0: debug port 2
[    0.676875] ehci-pci 0000:00:1a.0: cache line size of 64 is not supported
[    0.676896] ehci-pci 0000:00:1a.0: irq 16, io mem 0xb571d000
[    0.688013] ehci-pci 0000:00:1a.0: USB 2.0 started, EHCI 1.00
[    0.688051] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
[    0.688053] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.688055] usb usb1: Product: EHCI Host Controller
[    0.688056] usb usb1: Manufacturer: Linux 3.14.1-031401-generic ehci_hcd
[    0.688058] usb usb1: SerialNumber: 0000:00:1a.0
[    0.688229] hub 1-0:1.0: USB hub found
[    0.688236] hub 1-0:1.0: 2 ports detected
[    0.688451] ehci-pci 0000:00:1d.0: EHCI Host Controller
[    0.688456] ehci-pci 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    0.688467] ehci-pci 0000:00:1d.0: debug port 2
[    0.692376] ehci-pci 0000:00:1d.0: cache line size of 64 is not supported
[    0.692394] ehci-pci 0000:00:1d.0: irq 23, io mem 0xb571c000
[    0.704041] ehci-pci 0000:00:1d.0: USB 2.0 started, EHCI 1.00
[    0.704083] usb usb2: New USB device found, idVendor=1d6b, idProduct=0002
[    0.704085] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.704087] usb usb2: Product: EHCI Host Controller
[    0.704088] usb usb2: Manufacturer: Linux 3.14.1-031401-generic ehci_hcd
[    0.704090] usb usb2: SerialNumber: 0000:00:1d.0
[    0.704222] hub 2-0:1.0: USB hub found
[    0.704228] hub 2-0:1.0: 2 ports detected
[    0.704347] ehci-platform: EHCI generic platform driver
[    0.704354] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.704362] ohci-pci: OHCI PCI platform driver
[    0.704370] ohci-platform: OHCI generic platform driver
[    0.704376] uhci_hcd: USB Universal Host Controller Interface driver
[    0.704499] xhci_hcd 0000:00:14.0: xHCI Host Controller
[    0.704503] xhci_hcd 0000:00:14.0: new USB bus registered, assigned bus number 3
[    0.704599] xhci_hcd 0000:00:14.0: cache line size of 64 is not supported
[    0.704620] xhci_hcd 0000:00:14.0: irq 44 for MSI/MSI-X
[    0.704679] usb usb3: New USB device found, idVendor=1d6b, idProduct=0002
[    0.704681] usb usb3: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.704683] usb usb3: Product: xHCI Host Controller
[    0.704684] usb usb3: Manufacturer: Linux 3.14.1-031401-generic xhci_hcd
[    0.704685] usb usb3: SerialNumber: 0000:00:14.0
[    0.704804] hub 3-0:1.0: USB hub found
[    0.704821] hub 3-0:1.0: 14 ports detected
[    0.706974] xhci_hcd 0000:00:14.0: xHCI Host Controller
[    0.706979] xhci_hcd 0000:00:14.0: new USB bus registered, assigned bus number 4
[    0.707020] usb usb4: New USB device found, idVendor=1d6b, idProduct=0003
[    0.707022] usb usb4: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.707023] usb usb4: Product: xHCI Host Controller
[    0.707025] usb usb4: Manufacturer: Linux 3.14.1-031401-generic xhci_hcd
[    0.707026] usb usb4: SerialNumber: 0000:00:14.0
[    0.707144] hub 4-0:1.0: USB hub found
[    0.707156] hub 4-0:1.0: 4 ports detected
[    0.707850] i8042: PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    0.724201] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.724205] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.724412] mousedev: PS/2 mouse device common for all mice
[    0.724745] rtc_cmos 00:06: RTC can wake from S4
[    0.724912] rtc_cmos 00:06: rtc core: registered rtc_cmos as rtc0
[    0.724943] rtc_cmos 00:06: alarms up to one month, 242 bytes nvram, hpet irqs
[    0.725008] device-mapper: uevent: version 1.0.3
[    0.725109] device-mapper: ioctl: 4.27.0-ioctl (2013-10-30) initialised: dm-devel@redhat.com
[    0.725116] Intel P-state driver initializing.
[    0.725129] Intel pstate controlling: cpu 0
[    0.725144] Intel pstate controlling: cpu 1
[    0.725167] Intel pstate controlling: cpu 2
[    0.725176] Intel pstate controlling: cpu 3
[    0.725187] Intel pstate controlling: cpu 4
[    0.725196] Intel pstate controlling: cpu 5
[    0.725208] Intel pstate controlling: cpu 6
[    0.725221] Intel pstate controlling: cpu 7
[    0.725243] ledtrig-cpu: registered to indicate activity on CPUs
[    0.725244] EFI Variables Facility v0.08 2004-May-17
[    0.734155] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    0.750903] TCP: cubic registered
[    0.750977] NET: Registered protocol family 10
[    0.751215] NET: Registered protocol family 17
[    0.751235] Key type dns_resolver registered
[    0.751747] Loading compiled-in X.509 certificates
[    0.752343] Loaded X.509 cert 'Magrathea: Glacier signing key: 1c0f32e6fa24c2d8ee2657f2ffe090b5537204a6'
[    0.752352] registered taskstats version 1
[    0.754309] Key type trusted registered
[    0.756438] Key type encrypted registered
[    0.758480] AppArmor: AppArmor sha1 policy hashing enabled
[    0.758483] IMA: No TPM chip found, activating TPM-bypass!
[    0.758904] regulator-dummy: disabling
[    0.759092]   Magic number: 14:702:34
[    0.759172] memory memory70: hash matches
[    0.759242] rtc_cmos 00:06: setting system clock to 2014-05-14 16:02:48 UTC (1400083368)
[    0.759351] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.759353] EDD information not available.
[    0.759412] PM: Hibernation image not present or could not be loaded.
[    0.808148] ACPI: Battery Slot [BAT0] (battery present)
[    0.809295] Freeing unused kernel memory: 1356K (ffffffff81d17000 - ffffffff81e6a000)
[    0.809297] Write protecting the kernel read-only data: 12288k
[    0.810554] Freeing unused kernel memory: 540K (ffff880002779000 - ffff880002800000)
[    0.811441] Freeing unused kernel memory: 504K (ffff880002b82000 - ffff880002c00000)
[    0.823862] systemd-udevd[146]: starting version 204
[    0.842338] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    0.842346] r8169 0000:08:00.0: can't disable ASPM; OS doesn't have ASPM control
[    0.842539] r8169 0000:08:00.0: irq 45 for MSI/MSI-X
[    0.842664] r8169 0000:08:00.0 eth0: RTL8106e at 0xffffc90010c9a000, 28:d2:44:32:6a:9f, XID 04900000 IRQ 45
[    0.842876] ahci 0000:00:1f.2: version 3.0
[    0.842979] ahci 0000:00:1f.2: irq 46 for MSI/MSI-X
[    0.842995] ahci 0000:00:1f.2: SSS flag set, parallel bus scan disabled
[    0.843016] ahci 0000:00:1f.2: AHCI 0001.0300 32 slots 4 ports 6 Gbps 0x14 impl SATA mode
[    0.843018] ahci 0000:00:1f.2: flags: 64bit ncq stag pm led clo pio slum part ems apst 
[    0.848453] scsi0 : ahci
[    0.848565] scsi1 : ahci
[    0.848664] scsi2 : ahci
[    0.848763] scsi3 : ahci
[    0.848860] scsi4 : ahci
[    0.848895] ata1: DUMMY
[    0.848896] ata2: DUMMY
[    0.848898] ata3: SATA max UDMA/133 abar m2048@0xb571b000 port 0xb571b200 irq 46
[    0.848899] ata4: DUMMY
[    0.848901] ata5: SATA max UDMA/133 abar m2048@0xb571b000 port 0xb571b300 irq 46
[    1.000090] usb 1-1: new high-speed USB device number 2 using ehci-pci
[    1.132474] usb 1-1: New USB device found, idVendor=8087, idProduct=8008
[    1.132477] usb 1-1: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    1.132750] hub 1-1:1.0: USB hub found
[    1.132821] hub 1-1:1.0: 6 ports detected
[    1.168066] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    1.169721] ata3.00: ATAPI: HL-DT-ST DVDRAM GU70N, DE01, max UDMA/133
[    1.171578] ata3.00: configured for UDMA/133
[    1.172646] scsi 2:0:0:0: CD-ROM            HL-DT-ST DVDRAM GU70N     DE01 PQ: 0 ANSI: 5
[    1.181741] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    1.181744] cdrom: Uniform CD-ROM driver Revision: 3.20
[    1.181907] sr 2:0:0:0: Attached scsi CD-ROM sr0
[    1.181992] sr 2:0:0:0: Attached scsi generic sg0 type 5
[    1.244094] usb 2-1: new high-speed USB device number 2 using ehci-pci
[    1.376475] usb 2-1: New USB device found, idVendor=8087, idProduct=8000
[    1.376478] usb 2-1: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    1.376732] hub 2-1:1.0: USB hub found
[    1.376818] hub 2-1:1.0: 8 ports detected
[    1.500065] ata5: SATA link up 6.0 Gbps (SStatus 133 SControl 300)
[    1.544086] usb 3-1: new high-speed USB device number 2 using xhci_hcd
[    1.566106] ata5.00: ATA-9: ST1000LM014-1EJ164, LVD3, max UDMA/133
[    1.566109] ata5.00: 1953525168 sectors, multi 0: LBA48 NCQ (depth 31/32), AA
[    1.610485] ata5.00: configured for UDMA/133
[    1.610634] scsi 4:0:0:0: Direct-Access     ATA      ST1000LM014-1EJ1 LVD3 PQ: 0 ANSI: 5
[    1.610805] sd 4:0:0:0: [sda] 1953525168 512-byte logical blocks: (1.00 TB/931 GiB)
[    1.610808] sd 4:0:0:0: [sda] 4096-byte physical blocks
[    1.610824] sd 4:0:0:0: Attached scsi generic sg1 type 0
[    1.611016] sd 4:0:0:0: [sda] Write Protect is off
[    1.611020] sd 4:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.611104] sd 4:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.614870]  sda: sda1 sda2 sda3 sda4 sda5 sda6 sda7 sda8
[    1.615868] sd 4:0:0:0: [sda] Attached SCSI disk
[    1.718747] usb 3-1: New USB device found, idVendor=13d3, idProduct=5722
[    1.718752] usb 3-1: New USB device strings: Mfr=3, Product=1, SerialNumber=2
[    1.718754] usb 3-1: Product: Lenovo EasyCamera
[    1.718756] usb 3-1: Manufacturer: Azurewave
[    1.718758] usb 3-1: SerialNumber: NULL
[    1.888075] usb 3-2: new low-speed USB device number 3 using xhci_hcd
[    2.011000] EXT4-fs (sda7): INFO: recovery required on readonly filesystem
[    2.011002] EXT4-fs (sda7): write access will be enabled during recovery
[    2.075773] usb 3-2: New USB device found, idVendor=0566, idProduct=3002
[    2.075777] usb 3-2: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    2.075872] usb 3-2: ep 0x81 - rounding interval to 64 microframes, ep desc says 80 microframes
[    2.075875] usb 3-2: ep 0x82 - rounding interval to 64 microframes, ep desc says 80 microframes
[    2.078823] hidraw: raw HID events driver (C) Jiri Kosina
[    2.089924] usbcore: registered new interface driver usbhid
[    2.089926] usbhid: USB HID core driver
[    2.091291] input: HID 0566:3002 as /devices/pci0000:00/0000:00:14.0/usb3/3-2/3-2:1.0/0003:0566:3002.0001/input/input5
[    2.091381] hid-generic 0003:0566:3002.0001: input,hidraw0: USB HID v1.10 Keyboard [HID 0566:3002] on usb-0000:00:14.0-2/input0
[    2.092251] input: HID 0566:3002 as /devices/pci0000:00/0000:00:14.0/usb3/3-2/3-2:1.1/0003:0566:3002.0002/input/input6
[    2.092368] hid-generic 0003:0566:3002.0002: input,hiddev0,hidraw1: USB HID v1.10 Device [HID 0566:3002] on usb-0000:00:14.0-2/input1
[    2.188083] usb 3-7: new full-speed USB device number 4 using xhci_hcd
[    2.317156] usb 3-7: New USB device found, idVendor=8087, idProduct=07dc
[    2.317159] usb 3-7: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    2.484113] usb 3-10: new low-speed USB device number 5 using xhci_hcd
[    2.540936] EXT4-fs (sda7): recovery complete
[    2.550740] EXT4-fs (sda7): mounted filesystem with ordered data mode. Opts: (null)
[    2.616339] usb 3-10: New USB device found, idVendor=045e, idProduct=0040
[    2.616343] usb 3-10: New USB device strings: Mfr=1, Product=3, SerialNumber=0
[    2.616345] usb 3-10: Product: Microsoft 3-Button Mouse with IntelliEye(TM)
[    2.616346] usb 3-10: Manufacturer: Microsoft
[    2.616447] usb 3-10: ep 0x81 - rounding interval to 64 microframes, ep desc says 80 microframes
[    2.618586] input: Microsoft Microsoft 3-Button Mouse with IntelliEye(TM) as /devices/pci0000:00/0000:00:14.0/usb3/3-10/3-10:1.0/0003:045E:0040.0003/input/input7
[    2.618852] hid-generic 0003:045E:0040.0003: input,hidraw2: USB HID v1.10 Mouse [Microsoft Microsoft 3-Button Mouse with IntelliEye(TM)] on usb-0000:00:14.0-10/input0
[    5.271962] random: init urandom read with 113 bits of entropy available
[    5.969549] random: nonblocking pool is initialized
[    6.136023] init: plymouth-upstart-bridge main process (226) terminated with status 1
[    6.136035] init: plymouth-upstart-bridge main process ended, respawning
[    6.137828] init: plymouth-upstart-bridge main process (239) terminated with status 1
[    6.137837] init: plymouth-upstart-bridge main process ended, respawning
[    6.139265] init: plymouth-upstart-bridge main process (241) terminated with status 1
[    6.139277] init: plymouth-upstart-bridge main process ended, respawning
[    6.141106] init: plymouth-upstart-bridge main process (242) terminated with status 1
[    6.141117] init: plymouth-upstart-bridge main process ended, respawning
[    6.142635] init: plymouth-upstart-bridge main process (244) terminated with status 1
[    6.142645] init: plymouth-upstart-bridge main process ended, respawning
[    6.144383] init: plymouth-upstart-bridge main process (245) terminated with status 1
[    6.144394] init: plymouth-upstart-bridge main process ended, respawning
[    6.145786] init: plymouth-upstart-bridge main process (247) terminated with status 1
[    6.145797] init: plymouth-upstart-bridge main process ended, respawning
[    6.147635] init: plymouth-upstart-bridge main process (248) terminated with status 1
[    6.147647] init: plymouth-upstart-bridge main process ended, respawning
[    6.148827] init: plymouth-upstart-bridge main process (250) terminated with status 1
[    6.148836] init: plymouth-upstart-bridge main process ended, respawning
[    6.150325] init: plymouth-upstart-bridge main process (251) terminated with status 1
[    6.150336] init: plymouth-upstart-bridge main process ended, respawning
[    6.151848] init: plymouth-upstart-bridge main process (253) terminated with status 1
[    6.151859] init: plymouth-upstart-bridge respawning too fast, stopped
[   13.919814] Adding 8000508k swap on /dev/sda6.  Priority:-1 extents:1 across:8000508k FS
[   14.071573] systemd-udevd[357]: starting version 204
[   14.248290] wmi: Mapper loaded
[   14.263490] ACPI Warning: SystemIO range 0x0000000000001828-0x000000000000182f conflicts with OpRegion 0x0000000000001800-0x000000000000187f (\PMIO) (20131218/utaddress-258)
[   14.263495] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   14.263499] ACPI Warning: SystemIO range 0x0000000000000830-0x000000000000083f conflicts with OpRegion 0x0000000000000800-0x000000000000083f (\GPRL) (20131218/utaddress-258)
[   14.263501] ACPI Warning: SystemIO range 0x0000000000000830-0x000000000000083f conflicts with OpRegion 0x0000000000000800-0x0000000000000bff (\GPR_) (20131218/utaddress-258)
[   14.263504] ACPI Warning: SystemIO range 0x0000000000000830-0x000000000000083f conflicts with OpRegion 0x0000000000000800-0x000000000000085f (\_SB_.PCI0.PEG1.PEGP.GPIO) (20131218/utaddress-258)
[   14.263506] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   14.263507] ACPI Warning: SystemIO range 0x0000000000000800-0x000000000000082f conflicts with OpRegion 0x0000000000000800-0x000000000000083f (\GPRL) (20131218/utaddress-258)
[   14.263509] ACPI Warning: SystemIO range 0x0000000000000800-0x000000000000082f conflicts with OpRegion 0x0000000000000800-0x0000000000000bff (\GPR_) (20131218/utaddress-258)
[   14.263511] ACPI Warning: SystemIO range 0x0000000000000800-0x000000000000082f conflicts with OpRegion 0x0000000000000810-0x0000000000000813 (\IO_D) (20131218/utaddress-258)
[   14.263513] ACPI Warning: SystemIO range 0x0000000000000800-0x000000000000082f conflicts with OpRegion 0x0000000000000800-0x000000000000085f (\_SB_.PCI0.PEG1.PEGP.GPIO) (20131218/utaddress-258)
[   14.263515] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   14.263516] lpc_ich: Resource conflict(s) found affecting gpio_ich
[   14.280099] input: Ideapad extra buttons as /devices/platform/VPC2004:00/input/input18
[   14.558886] lp: driver loaded but no devices found
[   14.565660] ppdev: user-space parallel port driver
[   14.591949] microcode: CPU0 sig=0x306c3, pf=0x10, revision=0x9
[   14.593600] microcode: CPU1 sig=0x306c3, pf=0x10, revision=0x9
[   14.593614] microcode: CPU2 sig=0x306c3, pf=0x10, revision=0x9
[   14.593626] microcode: CPU3 sig=0x306c3, pf=0x10, revision=0x9
[   14.593639] microcode: CPU4 sig=0x306c3, pf=0x10, revision=0x9
[   14.593651] microcode: CPU5 sig=0x306c3, pf=0x10, revision=0x9
[   14.593663] microcode: CPU6 sig=0x306c3, pf=0x10, revision=0x9
[   14.593675] microcode: CPU7 sig=0x306c3, pf=0x10, revision=0x9
[   14.593744] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[   14.685927] mei_me 0000:00:16.0: irq 47 for MSI/MSI-X
[   14.738117] [drm] Initialized drm 1.1.0 20060810
[   14.838050] AVX2 version of gcm_enc/dec engaged.
[   14.849042] cfg80211: Calling CRDA to update world regulatory domain
[   14.860620] Bluetooth: Core ver 2.18
[   14.860631] NET: Registered protocol family 31
[   14.860632] Bluetooth: HCI device and connection manager initialized
[   14.860637] Bluetooth: HCI socket layer initialized
[   14.860639] Bluetooth: L2CAP socket layer initialized
[   14.860643] Bluetooth: SCO socket layer initialized
[   14.866499] usbcore: registered new interface driver btusb
[   14.879504] Bluetooth: hci0: read Intel version: 370710018002030d00
[   14.887705] Intel(R) Wireless WiFi driver for Linux, in-tree:
[   14.887708] Copyright(c) 2003- 2014 Intel Corporation
[   14.887844] iwlwifi 0000:09:00.0: irq 48 for MSI/MSI-X
[   14.889741] cfg80211: World regulatory domain updated:
[   14.889744] cfg80211:  DFS Master region: unset
[   14.889745] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   14.889747] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   14.889749] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   14.889750] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   14.889751] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   14.889753] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   14.936606] Bluetooth: hci0: Intel Bluetooth firmware file: intel/ibt-hw-37.7.10-fw-1.80.2.3.d.bseq
[   14.964472] iwlwifi 0000:09:00.0: loaded firmware version 22.24.8.0 op_mode iwlmvm
[   14.994151] [drm] Memory usable by graphics device = 2048M
[   14.994154] checking generic (c0000000 410000) vs hw (c0000000 10000000)
[   14.994155] fb: conflicting fb hw usage inteldrmfb vs EFI VGA - removing generic driver
[   14.994179] Console: switching to colour dummy device 80x25
[   15.035502] Bluetooth: hci0: Intel Bluetooth firmware patch completed and activated
[   15.040067] i915 0000:00:02.0: irq 49 for MSI/MSI-X
[   15.040075] [drm] Supports vblank timestamp caching Rev 2 (21.10.2013).
[   15.040076] [drm] Driver supports precise vblank timestamp query.
[   15.040146] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem
[   15.069986] Linux video capture interface: v2.00
[   15.081429] ACPI Warning: \_SB_.PCI0.GFX0._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20131218/nsarguments-95)
[   15.081470] ACPI Warning: \_SB_.PCI0.GFX0._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20131218/nsarguments-95)
[   15.081572] i915 0000:00:02.0: optimus capabilities: enabled, status dynamic power, hda bios codec supported
[   15.081591] ACPI Warning: \_SB_.PCI0.PEG1.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20131218/nsarguments-95)
[   15.081618] ACPI Warning: \_SB_.PCI0.PEG1.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20131218/nsarguments-95)
[   15.081702] pci 0000:07:00.0: optimus capabilities: enabled, status dynamic power, hda bios codec supported
[   15.081704] VGA switcheroo: detected Optimus DSM method \_SB_.PCI0.PEG1.PEGP handle
[   15.081727] nouveau 0000:07:00.0: enabling device (0006 -> 0007)
[   15.115492] uvcvideo: Found UVC 1.00 device Lenovo EasyCamera (13d3:5722)
[   15.121453] input: Lenovo EasyCamera as /devices/pci0000:00/0000:00:14.0/usb3/3-1/3-1:1.0/input/input20
[   15.121544] usbcore: registered new interface driver uvcvideo
[   15.121546] USB Video Class driver (1.1.1)
[   15.129597] fbcon: inteldrmfb (fb0) is primary device
[   15.162488] iwlwifi 0000:09:00.0: Detected Intel(R) Wireless N 7260, REV=0x144
[   15.162548] iwlwifi 0000:09:00.0: L1 Disabled; Enabling L0S
[   15.162818] iwlwifi 0000:09:00.0: L1 Disabled; Enabling L0S
[   15.166775] audit: type=1400 audit(1400079782.903:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=479 comm="apparmor_parser"
[   15.166778] audit: type=1400 audit(1400079782.903:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=479 comm="apparmor_parser"
[   15.166780] audit: type=1400 audit(1400079782.903:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=479 comm="apparmor_parser"
[   15.166788] audit: type=1400 audit(1400079782.903:5): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=478 comm="apparmor_parser"
[   15.166792] audit: type=1400 audit(1400079782.903:6): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=478 comm="apparmor_parser"
[   15.166794] audit: type=1400 audit(1400079782.903:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=478 comm="apparmor_parser"
[   15.167072] audit: type=1400 audit(1400079782.903:8): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=479 comm="apparmor_parser"
[   15.167074] audit: type=1400 audit(1400079782.903:9): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=479 comm="apparmor_parser"
[   15.167082] audit: type=1400 audit(1400079782.903:10): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=478 comm="apparmor_parser"
[   15.167084] audit: type=1400 audit(1400079782.903:11): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=478 comm="apparmor_parser"
[   15.289283] psmouse serio1: synaptics: Touchpad model: 1, fw: 8.1, id: 0x1e2b1, caps: 0xd00123/0x840300/0x127c00, board id: 2334, fw id: 1508589
[   15.346810] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input19
[   15.403595] ieee80211 phy0: Selected rate control algorithm 'iwl-mvm-rs'
[   16.247609] EXT4-fs (sda7): re-mounted. Opts: errors=remount-ro
[   16.590461] EXT4-fs (sda8): mounted filesystem with ordered data mode. Opts: (null)
[   16.747949] FS-Cache: Loaded
[   16.768097] Console: switching to colour frame buffer device 170x48
[   16.770203] i915 0000:00:02.0: fb0: inteldrmfb frame buffer device
[   16.770204] i915 0000:00:02.0: registered panic notifier
[   16.770568] [Firmware Bug]: ACPI(PEGP) defines _DOD but not _DOS
[   16.770873] ACPI: Video Device [PEGP] (multi-head: yes  rom: yes  post: no)
[   16.770876] ACPI Error: [\_SB_.PCI0.GFX0.DD02._BCL] Namespace lookup failure, AE_NOT_FOUND (20131218/psargs-359)
[   16.770880] ACPI Error: Method parse/execution failed [\_SB_.PCI0.PEG1.PEGP.DD02._BCL] (Node ffff88025686c5c8), AE_NOT_FOUND (20131218/psparse-536)
[   16.770926] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:4c/LNXVIDEO:00/input/input21
[   16.772128] [drm] Enabling RC6 states: RC6 on, RC6p off, RC6pp off
[   16.785245] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[   16.785571] acpi device:66: registered as cooling_device9
[   16.785646] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:01/input/input22
[   16.785743] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[   16.785905] [drm] hdmi device  not found 7 0 1
[   16.785965] HDA driver get symbol successfully from i915 module
[   16.786051] nouveau  [  DEVICE][0000:07:00.0] BOOT0  : 0x108120a1
[   16.786054] nouveau  [  DEVICE][0000:07:00.0] Chipset: GK208 (NV108)
[   16.786056] nouveau  [  DEVICE][0000:07:00.0] Family : NVE0
[   16.786504] snd_hda_intel 0000:00:1b.0: irq 50 for MSI/MSI-X
[   16.787774] nouveau  [   VBIOS][0000:07:00.0] checking PRAMIN for image...
[   16.788885] nouveau  [   VBIOS][0000:07:00.0] ... signature not found
[   16.788887] nouveau  [   VBIOS][0000:07:00.0] checking PROM for image...
[   16.788960] nouveau  [   VBIOS][0000:07:00.0] ... signature not found
[   16.788962] nouveau  [   VBIOS][0000:07:00.0] checking ACPI for image...
[   16.796055] snd_hda_intel 0000:00:03.0: irq 51 for MSI/MSI-X
[   16.814724] input: HDA Intel HDMI HDMI/DP,pcm=8 as /devices/pci0000:00/0000:00:03.0/sound/card0/input25
[   16.814829] input: HDA Intel HDMI HDMI/DP,pcm=7 as /devices/pci0000:00/0000:00:03.0/sound/card0/input24
[   16.814913] input: HDA Intel HDMI HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:03.0/sound/card0/input23
[   16.877510] SKU: Nid=0x0 sku_cfg=0x00003801
[   16.877512] SKU: port_connectivity=0x0
[   16.877513] SKU: enable_pcbeep=0x1
[   16.877514] SKU: check_sum=0x00000000
[   16.877515] SKU: customization=0x00000000
[   16.877515] SKU: external_amp=0x0
[   16.877516] SKU: platform_type=0x0
[   16.877517] SKU: swap=0x0
[   16.877518] SKU: override=0x1
[   16.877733] autoconfig: line_outs=1 (0x14/0x0/0x0/0x0/0x0) type:speaker
[   16.877735]    speaker_outs=0 (0x0/0x0/0x0/0x0/0x0)
[   16.877736]    hp_outs=1 (0x21/0x0/0x0/0x0/0x0)
[   16.877736]    mono: mono_out=0x0
[   16.877737]    inputs:
[   16.877738]      Mic=0x19
[   16.877739]      Internal Mic=0x12
[   16.877740] realtek: Enabling init ASM_ID=0x3801 CODEC_ID=10ec0282
[   16.882296] input: HDA Intel PCH Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card1/input27
[   16.882407] input: HDA Intel PCH Mic as /devices/pci0000:00/0000:00:1b.0/sound/card1/input26
[   16.888836] FS-Cache: Netfs 'cifs' registered for caching
[   16.888904] Key type cifs.spnego registered
[   16.888908] Key type cifs.idmap registered
[   16.889081] CIFS VFS: No username specified
[   17.527191] CIFS VFS: No username specified
[   17.530970] CIFS VFS: No username specified
[   17.544175] nouveau  [   VBIOS][0000:07:00.0] ... appears to be valid
[   17.544178] nouveau  [   VBIOS][0000:07:00.0] using image from ACPI
[   17.544271] nouveau  [   VBIOS][0000:07:00.0] BIT signature found
[   17.544274] nouveau  [   VBIOS][0000:07:00.0] version 80.28.2c.00.08
[   17.544703] nouveau  [ DEVINIT][0000:07:00.0] adaptor not initialised
[   17.544712] nouveau  [   VBIOS][0000:07:00.0] running init tables
[   17.609720] nouveau 0000:07:00.0: irq 52 for MSI/MSI-X
[   17.609728] nouveau  [     PMC][0000:07:00.0] MSI interrupts enabled
[   17.609780] nouveau  [     PFB][0000:07:00.0] RAM type: DDR3
[   17.609781] nouveau  [     PFB][0000:07:00.0] RAM size: 2048 MiB
[   17.609782] nouveau  [     PFB][0000:07:00.0]    ZCOMP: 0 tags
[   17.609861] nouveau E[   PIBUS][0000:07:00.0] HUB0: 0x6013d4 0x00005702 (0x1a708200)
[   17.609898] nouveau E[   PIBUS][0000:07:00.0] GPC0: 0x4188ac 0x00000001 (0x1970822e)
[   17.613869] nouveau  [    VOLT][0000:07:00.0] GPU voltage: 600000uv
[   17.636749] nouveau  [  PTHERM][0000:07:00.0] FAN control: none / external
[   17.636754] nouveau  [  PTHERM][0000:07:00.0] fan management: automatic
[   17.636756] nouveau  [  PTHERM][0000:07:00.0] internal sensor: yes
[   17.636775] nouveau  [     CLK][0000:07:00.0] 07: core 405 MHz memory 810 MHz 
[   17.636828] nouveau  [     CLK][0000:07:00.0] 0a: core 405-1058 MHz memory 1620 MHz 
[   17.636895] nouveau  [     CLK][0000:07:00.0] 0f: core 405-1058 MHz memory 2002 MHz 
[   17.636956] nouveau  [     CLK][0000:07:00.0] --: core 405 MHz memory 810 MHz 
[   17.672487] vga_switcheroo: enabled
[   17.672633] [TTM] Zone  kernel: Available graphics memory: 3962368 kiB
[   17.672634] [TTM] Zone   dma32: Available graphics memory: 2097152 kiB
[   17.672635] [TTM] Initializing pool allocator
[   17.672638] [TTM] Initializing DMA pool allocator
[   17.672645] nouveau  [     DRM] VRAM: 2048 MiB
[   17.672646] nouveau  [     DRM] GART: 1048576 MiB
[   17.672649] nouveau E[     DRM] Pointer to TMDS table invalid
[   17.672666] nouveau  [     DRM] DCB version 4.0
[   17.672668] nouveau E[     DRM] Pointer to flat panel table invalid
[   17.672693] nouveau  [     DRM] ACPI backlight interface available, not registering our own
[   17.680443] nouveau  [     DRM] MM: using COPY for buffer copies
[   17.680451] [drm] Initialized nouveau 1.1.1 20120801 for 0000:07:00.0 on minor 1
[   19.064145] init: failsafe main process (737) killed by TERM signal
[   19.066706] CIFS VFS: No username specified
[   19.226244] init: avahi-cups-reload main process (852) terminated with status 1
[   19.229889] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   19.229892] Bluetooth: BNEP filters: protocol multicast
[   19.229899] Bluetooth: BNEP socket layer initialized
[   19.554310] CIFS VFS: No username specified
[   19.687214] Bluetooth: RFCOMM TTY layer initialized
[   19.687223] Bluetooth: RFCOMM socket layer initialized
[   19.687227] Bluetooth: RFCOMM ver 1.11
[   19.921210] r8169 0000:08:00.0 eth0: link down
[   19.921231] r8169 0000:08:00.0 eth0: link down
[   19.921247] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   19.922839] iwlwifi 0000:09:00.0: L1 Disabled; Enabling L0S
[   19.923068] iwlwifi 0000:09:00.0: L1 Disabled; Enabling L0S
[   19.936651] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   20.180143] audit_printk_skb: 72 callbacks suppressed
[   20.180147] audit: type=1400 audit(1400079787.919:36): apparmor="STATUS" operation="profile_replace" name="pxgsettings" pid=944 comm="apparmor_parser"
[   20.180152] audit: type=1400 audit(1400079787.919:37): apparmor="STATUS" operation="profile_replace" name="sanitized_helper" pid=944 comm="apparmor_parser"
[   20.180155] audit: type=1400 audit(1400079787.919:38): apparmor="STATUS" operation="profile_replace" name="/usr/lib/telepathy/telepathy-ofono" pid=944 comm="apparmor_parser"
[   20.180199] audit: type=1400 audit(1400079787.919:39): apparmor="STATUS" operation="profile_load" name="/usr/sbin/tcpdump" pid=948 comm="apparmor_parser"
[   20.180256] audit: type=1400 audit(1400079787.919:40): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince" pid=942 comm="apparmor_parser"
[   20.180261] audit: type=1400 audit(1400079787.919:41): apparmor="STATUS" operation="profile_load" name="sanitized_helper" pid=942 comm="apparmor_parser"
[   20.180264] audit: type=1400 audit(1400079787.919:42): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince-previewer" pid=942 comm="apparmor_parser"
[   20.180267] audit: type=1400 audit(1400079787.919:43): apparmor="STATUS" operation="profile_load" name="sanitized_helper" pid=942 comm="apparmor_parser"
[   20.180270] audit: type=1400 audit(1400079787.919:44): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince-thumbnailer" pid=942 comm="apparmor_parser"
[   20.180272] audit: type=1400 audit(1400079787.919:45): apparmor="STATUS" operation="profile_load" name="sanitized_helper" pid=942 comm="apparmor_parser"
[   20.721614] nouveau E[    PBUS][0000:07:00.0] MMIO read of 0x00000000 FAULT at 0x122130 [ TIMEOUT ]
[   20.721960] nouveau E[    PBUS][0000:07:00.0] MMIO write of 0xbad0011f FAULT at 0x000260 [ TIMEOUT ]
[   20.730966] nouveau E[    PBUS][0000:07:00.0] MMIO read of 0x00000000 FAULT at 0x000260 [ TIMEOUT ]
[   20.731796] nouveau E[    PBUS][0000:07:00.0] MMIO read of 0x00000000 FAULT at 0x000260 [ TIMEOUT ]
[   21.154629] CIFS VFS: No username specified
[   21.530659] r8169 0000:08:00.0 eth0: link up
[   21.530669] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   23.586471] CIFS VFS: No username specified
[   25.864078] ACPI Warning: \_SB_.PCI0.PEG1.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20131218/nsarguments-95)
[   25.864209] ACPI: \_SB_.PCI0.PEG1.PEGP: failed to evaluate _DSM
[   25.864213] ACPI Warning: \_SB_.PCI0.PEG1.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20131218/nsarguments-95)
[   26.732047] CIFS VFS: No username specified
[  254.472955] systemd-hostnamed[2996]: Warning: nss-myhostname is not installed. Changing the local hostname might make it unresolveable. Please install nss-myhostname!
[  256.238539] CIFS VFS: Autodisabling the use of server inode numbers on \\192.168.1.103\pi. This server doesn't seem to support them properly. Hardlinks will not be recognized on this mount. Consider mounting with the "noserverino" option to silence this message.

```

---

