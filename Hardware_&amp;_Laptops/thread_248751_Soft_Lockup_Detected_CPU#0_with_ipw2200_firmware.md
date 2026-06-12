---
title: "Soft Lockup Detected CPU#0 with ipw2200 firmware"
date: 2006-09-01
forum: Hardware &amp; Laptops
---

### Post by Game_Ender on 2006-09-01
I have a Dell Inspiron 600M with the standard centrino wireless card.  I having trouble with my laptop "freezing" for about 15 seconds and then becoming responsive for about 2 seconds and doing this till I manage to shut it down.  During this time the NetworkManager indicates a loss of signal.  Sometimes it does it make it the through shutdown, just sitting there with a black screen doing nothing.

In order to shutdown down sometimes I have to go the command line "Ctrl+Alt+F5", and I get lots of "[17179758.236000] BUG: soft lockup detected on CPU#0!" coming to the console.  This just happening within the last week.

I have not detected a pattern yet, but it seems to happen most when I am doing heavy wireless work.  These crashing while downloading the xplane demo (700 megs).

uname -a:```
Linux jlisee-laptop 2.6.15-26-386 #1 PREEMPT Thu Aug 3 02:52:00 UTC 2006 i686 GNU/Linux
```

I am running the binary fglrx drivers from AIT (8.28.8 ), fglrxinfo:```
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: MOBILITY/RADEON 9000 DDR Generic
OpenGL version string: 1.3.1091 (X4.3.0-8.28.8)
```

First instance of the lockup on a fresh restart (sorry for the log log file, but it shows and ipw2220 firmware restart followed by the bug again:
```

Sep  1 12:05:03 localhost kernel: [17179746.856000] BUG: soft lockup detected on CPU#0!
Sep  1 12:05:03 localhost kernel: [17179746.856000] 
Sep  1 12:05:03 localhost kernel: [17179746.856000] Pid: 0, comm:              swapper
Sep  1 12:05:03 localhost kernel: [17179746.856000] EIP: 0060:[delay_pmtmr+20/32] CPU: 0
Sep  1 12:05:03 localhost kernel: [17179746.856000] EIP is at delay_pmtmr+0x14/0x20
Sep  1 12:05:03 localhost kernel: [17179746.856000]  EFLAGS: 00000287    Tainted: P       (2.6.15-26-386)
Sep  1 12:05:03 localhost kernel: [17179746.856000] EAX: 198d14a1 EBX: 00001733 ECX: 198d0b4a EDX: 0000002e
Sep  1 12:05:03 localhost kernel: [17179746.856000] ESI: f6171260 EDI: c0387f04 EBP: c0387ef8 DS: 007b ES: 007b
Sep  1 12:05:03 localhost kernel: [17179746.856000] CR0: 8005003b CR2: 00591000 CR3: 35d59000 CR4: 00000690
Sep  1 12:05:03 localhost kernel: [17179746.856000]  [pg0+945526589/1069368320] tg3_readphy+0x5d/0xf0 [tg3]
Sep  1 12:05:03 localhost kernel: [17179746.856000]  [pg0+945533188/1069368320] tg3_setup_copper_phy+0x184/0x820 [tg3]
Sep  1 12:05:03 localhost kernel: [17179746.856000]  [pg0+945558368/1069368320] tg3_timer+0x0/0x2e0 [tg3]
Sep  1 12:05:03 localhost kernel: [17179746.856000]  [pg0+945539751/1069368320] tg3_setup_phy+0x87/0xe0 [tg3]
Sep  1 12:05:03 localhost kernel: [17179746.856000]  [pg0+945558795/1069368320] tg3_timer+0x1ab/0x2e0 [tg3]
Sep  1 12:05:03 localhost kernel: [17179746.856000]  [run_timer_softirq+182/464] run_timer_softirq+0xb6/0x1d0
Sep  1 12:05:03 localhost kernel: [17179746.856000]  [__do_softirq+79/176] __do_softirq+0x4f/0xb0
Sep  1 12:05:03 localhost kernel: [17179746.856000]  [do_softirq+53/64] do_softirq+0x35/0x40
Sep  1 12:05:03 localhost kernel: [17179746.856000]  [irq_exit+53/64] irq_exit+0x35/0x40
Sep  1 12:05:03 localhost kernel: [17179746.856000]  [do_IRQ+31/48] do_IRQ+0x1f/0x30
Sep  1 12:05:03 localhost kernel: [17179746.856000]  [common_interrupt+26/32] common_interrupt+0x1a/0x20
Sep  1 12:05:03 localhost kernel: [17179746.856000]  [pg0+944012146/1069368320] acpi_processor_idle+0x155/0x2bc [processor]
Sep  1 12:05:03 localhost kernel: [17179746.856000]  [cpu_idle+28/96] cpu_idle+0x1c/0x60
Sep  1 12:05:03 localhost kernel: [17179746.856000]  [start_kernel+374/464] start_kernel+0x176/0x1d0
Sep  1 12:05:03 localhost kernel: [17179748.232000] ipw2200: Firmware error detected.  Restarting.
Sep  1 12:05:15 localhost kernel: [17179758.236000] BUG: soft lockup detected on CPU#0!
Sep  1 12:05:15 localhost kernel: [17179758.236000] 
Sep  1 12:05:15 localhost kernel: [17179758.236000] Pid: 0, comm:              swapper
Sep  1 12:05:15 localhost kernel: [17179758.236000] EIP: 0060:[delay_pmtmr+20/32] CPU: 0
Sep  1 12:05:15 localhost kernel: [17179758.236000] EIP is at delay_pmtmr+0x14/0x20
Sep  1 12:05:15 localhost kernel: [17179758.236000]  EFLAGS: 00000297    Tainted: P       (2.6.15-26-386)
Sep  1 12:05:15 localhost kernel: [17179758.236000] EAX: f7a7c161 EBX: 00003ddc ECX: f7a79006 EDX: 00000031
Sep  1 12:05:15 localhost kernel: [17179758.236000] ESI: f6171260 EDI: c0387f04 EBP: c0387ef8 DS: 007b ES: 007b
Sep  1 12:05:15 localhost kernel: [17179758.236000] CR0: 8005003b CR2: b7f34000 CR3: 34b8b000 CR4: 00000690
Sep  1 12:05:15 localhost kernel: [17179758.236000]  [pg0+945526589/1069368320] tg3_readphy+0x5d/0xf0 [tg3]
Sep  1 12:05:15 localhost kernel: [17179758.236000]  [pg0+945533179/1069368320] tg3_setup_copper_phy+0x17b/0x820 [tg3]
Sep  1 12:05:15 localhost kernel: [17179758.236000]  [pg0+945558368/1069368320] tg3_timer+0x0/0x2e0 [tg3]
Sep  1 12:05:15 localhost kernel: [17179758.236000]  [pg0+945539751/1069368320] tg3_setup_phy+0x87/0xe0 [tg3]
Sep  1 12:05:15 localhost kernel: [17179758.236000]  [pg0+945558795/1069368320] tg3_timer+0x1ab/0x2e0 [tg3]
Sep  1 12:05:15 localhost kernel: [17179758.236000]  [run_timer_softirq+182/464] run_timer_softirq+0xb6/0x1d0
Sep  1 12:05:15 localhost kernel: [17179758.236000]  [__do_softirq+79/176] __do_softirq+0x4f/0xb0
Sep  1 12:05:15 localhost kernel: [17179758.236000]  [do_softirq+53/64] do_softirq+0x35/0x40
Sep  1 12:05:15 localhost kernel: [17179758.236000]  [irq_exit+53/64] irq_exit+0x35/0x40
Sep  1 12:05:15 localhost kernel: [17179758.236000]  [do_IRQ+31/48] do_IRQ+0x1f/0x30
Sep  1 12:05:15 localhost kernel: [17179758.236000]  [common_interrupt+26/32] common_interrupt+0x1a/0x20
Sep  1 12:05:15 localhost kernel: [17179758.236000]  [pg0+944012146/1069368320] acpi_processor_idle+0x155/0x2bc [processor]
Sep  1 12:05:15 localhost kernel: [17179758.236000]  [cpu_idle+28/96] cpu_idle+0x1c/0x60
Sep  1 12:05:15 localhost kernel: [17179758.236000]  [start_kernel+374/464] start_kernel+0x176/0x1d0
Sep  1 12:05:15 localhost kernel: [17179760.396000] ipw2200: Firmware error detected.  Restarting.
Sep  1 12:05:16 localhost NetworkManager: <information>^Iwpa_supplicant(4938): 7 65 72 2f 77 70 61 5f 63 74 72 6c 5f 34 34 39 34 2d 31 00 00 00 
Sep  1 12:05:16 localhost NetworkManager: <information>^Iwpa_supplicant(4938): Cancelling scan request 
Sep  1 12:05:16 localhost NetworkManager: <information>^Iwpa_supplicant(4938): WPA: clearing own WPA/RSN IE 
Sep  1 12:05:16 localhost NetworkManager: <information>^Iwpa_supplicant(4938): Automatic auth_alg selection: 0x1 
Sep  1 12:05:16 localhost NetworkManager: <information>^Iwpa_supplicant(4938): WPA: clearing AP WPA IE 
Sep  1 12:05:16 localhost NetworkManager: <information>^Iwpa_supplicant(4938): WPA: clearing AP RSN IE 
Sep  1 12:05:16 localhost NetworkManager: <information>^Iwpa_supplicant(4938): WPA: clearing own WPA/RSN IE 
Sep  1 12:05:16 localhost NetworkManager: <information>^Iwpa_supplicant(4938): No keys have been configured - skip key clearing 
Sep  1 12:05:16 localhost NetworkManager: <information>^Iwpa_supplicant(4938): wpa_driver_wext_set_drop_unencrypted 
Sep  1 12:05:16 localhost NetworkManager: <information>^Iwpa_supplicant(4938): State: SCANNING -> ASSOCIATING 
Sep  1 12:05:16 localhost NetworkManager: <information>^Iwpa_supplicant(4938): wpa_driver_wext_associate 
Sep  1 12:05:16 localhost NetworkManager: <information>^Iwpa_supplicant(4938): Setting authentication timeout: 10 sec 0 usec 
Sep  1 12:05:16 localhost NetworkManager: <information>^Iwpa_supplicant(4938): EAPOL: External notification - portControl=ForceAuthorized 
Sep  1 12:05:16 localhost NetworkManager: <information>^Iwpa_supplicant(4938): Wireless event: cmd=0x8b06 len=8 
Sep  1 12:05:16 localhost NetworkManager: <information>^Iwpa_supplicant(4938): Wireless event: cmd=0x8b1a len=12 
Sep  1 12:05:16 localhost NetworkManager: <information>^Iwpa_supplicant(4938): Wireless event: cmd=0x8b15 len=20 
Sep  1 12:05:16 localhost NetworkManager: <information>^Iwpa_supplicant(4938): Wireless event: new AP: 00:00:00:00:00:00 
Sep  1 12:05:16 localhost NetworkManager: <information>^Iwpa_supplicant(4938): Added BSSID 00:00:00:00:00:00 into blacklist 
Sep  1 12:05:16 localhost NetworkManager: <information>^Iwpa_supplicant(4938): State: ASSOCIATING -> DISCONNECTED 
Sep  1 12:05:16 localhost NetworkManager: <information>^Iwpa_supplicant(4938): EAPOL: External notification - portEnabled=0 
Sep  1 12:05:16 localhost NetworkManager: <information>^Iwpa_supplicant(4938): EAPOL: External notification - portValid=0 
Sep  1 12:05:16 localhost NetworkManager: <information>^Iwpa_supplicant(4938): CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys 
Sep  1 12:05:16 localhost NetworkManager: <information>^Iwpa_supplicant(4938): CTRL_IFACE monitor send - hexdump(len=42): 2f 76 61 72 2f 72 75 6e 2f 4e 65 74 77 6f 72 6b 4d 61 6e 61 67 65 72 2f 77 70 61 5f 63 74 72 6c 5f 34 34 39 34 2d 31 00 00 00 
Sep  1 12:05:16 localhost NetworkManager: <information>^Iwpa_supplicant(4938): NK, IFLA_IFNAME: Interface 'eth1' added 
Sep  1 12:05:16 localhost NetworkManager: <information>^Iwpa_supplicant(4938): Wireless event: cmd=0x8b15 len=20 
Sep  1 12:05:16 localhost NetworkManager: <information>^Iwpa_supplicant(4938): Wireless event: new AP: 00:00:00:00:00:00 
Sep  1 12:05:16 localhost NetworkManager: <information>^Iwpa_supplicant(4938): BSSID 00:00:00:00:00:00 blacklist count incremented to 2 
Sep  1 12:05:16 localhost NetworkManager: <information>^Iwpa_supplicant(4938): State: DISCONNECTED -> DISCONNECTED 
Sep  1 12:05:16 localhost NetworkManager: <information>^Iwpa_supplicant(4938): EAPOL: External notification - portEnabled=0 
Sep  1 12:05:16 localhost NetworkManager: <information>^Iwpa_supplicant(4938): EAPOL: External notification - portValid=0 
Sep  1 12:05:16 localhost NetworkManager: <information>^Iwpa_supplicant(4938): CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys 
Sep  1 12:05:16 localhost NetworkManager: <information>^Iwpa_supplicant(4938): CTRL_IFACE monitor send - hexdump(len=42): 2f 76 61 72 2f 72 75 6e 2f 4e 65 74 77 6f 72 6b 4d 61 6e 61 67 65 72 2f 77 70 61 5f 63 74 72 6c 5f 34 34 39 34 2d 31 00 00 00 
Sep  1 12:05:16 localhost NetworkManager: <information>^Iwpa_supplicant(4938): Wireless event: cmd=0x8b15 len=20 
Sep  1 12:05:16 localhost NetworkManager: <information>^Iwpa_supplicant(4938): Wireless event: new AP: 00:12:44:b1:e8:b0 
Sep  1 12:05:16 localhost NetworkManager: <information>^Iwpa_supplicant(4938): State: DISCONNECTED -> ASSOCIATED 
Sep  1 12:05:16 localhost NetworkManager: <information>^Iwpa_supplicant(4938): Associated to a new BSS: BSSID=00:12:44:b1:e8:b0 
Sep  1 12:05:16 localhost NetworkManager: <information>^Iwpa_supplicant(4938): Associated with 00:12:44:b1:e8:b0 
Sep  1 12:05:16 localhost NetworkManager: <information>^Iwpa_supplicant(4938): CTRL_IFACE monitor send - hexdump(len=42): 2f 76 61 72 2f 72 75 6e 2f 4e 65 74 77 6f 72 6b 4d 61 6e 61 67 65 72 2f 77 70 61 5f 63 74 72 6c 5f 34 34 39 34 2d 31 00 00 00 
Sep  1 12:05:16 localhost NetworkManager: <information>^Iwpa_supplicant(4938): WPA: Association event - clear replay counter 
Sep  1 12:05:16 localhost NetworkManager: <information>^Iwpa_supplicant(4938): EAPOL: External notification - portEnabled=0 
Sep  1 12:05:16 localhost NetworkManager: <information>^Iwpa_supplicant(4938): EAPOL: External notification - portValid=0 
Sep  1 12:05:16 localhost NetworkManager: <information>^Iwpa_supplicant(4938): L: External notification - portEnabled=1 
Sep  1 12:05:16 localhost NetworkManager: <information>^Iwpa_supplicant(4938): EAPOL: SUPP_PAE entering state S_FORCE_AUTH 
Sep  1 12:05:16 localhost NetworkManager: <information>^Iwpa_supplicant(4938): EAPOL: SUPP_BE entering state IDLE 
Sep  1 12:05:16 localhost NetworkManager: <information>^Iwpa_supplicant(4938): Cancelling authentication timeout 
Sep  1 12:05:16 localhost NetworkManager: <information>^Iwpa_supplicant(4938): State: ASSOCIATED -> COMPLETED 
Sep  1 12:05:16 localhost NetworkManager: <information>^Iwpa_supplicant(4938): CTRL-EVENT-CONNECTED - Connection to 00:12:44:b1:e8:b0 completed (auth) 
Sep  1 12:05:16 localhost NetworkManager: <information>^Iwpa_supplicant(4938): CTRL_IFACE monitor send - hexdump(len=42): 2f 76 61 72 2f 72 75 6e 2f 4e 65 74 77 6f 72 6b 4d 61 6e 61 67 65 72 2f 77 70 61 5f 63 74 72 6c 5f 34 34 39 34 2d 31 00 00 00 
Sep  1 12:05:16 localhost NetworkManager: <information>^Iwpa_supplicant(4938): RTM_NEWLINK, IFLA_IFNAME: Interface 'eth1' added 
Sep  1 12:05:16 localhost NetworkManager: <information>^Iwpa_supplicant(4938): RTM_NEWLINK, IFLA_IFNAME: Interface 'eth1' added 
Sep  1 12:05:16 localhost NetworkManager: <information>^Iwpa_supplicant(4938): Wireless event: cmd=0x8b15 len=20 
Sep  1 12:05:16 localhost NetworkManager: <information>^Iwpa_supplicant(4938): Wireless event: new AP: 00:12:44:b1:e8:b0 
Sep  1 12:05:16 localhost NetworkManager: <information>^Iwpa_supplicant(4938): State: COMPLETED -> ASSOCIATED 
Sep  1 12:05:16 localhost NetworkManager: <information>^Iwpa_supplicant(4938): Associated with 00:12:44:b1:e8:b0 
Sep  1 12:05:16 localhost NetworkManager: <information>^Iwpa_supplicant(4938): CTRL_IFACE monitor send - hexdump(len=42): 2f 76 61 72 2f 72 75 6e 2f 4e 65 74 77 6f 72 6b 4d 61 6e 61 67 65 72 2f 77 70 61 5f 63 74 72 6c 5f 34 34 39 34 2d 31 00 00 00 
Sep  1 12:05:16 localhost NetworkManager: <information>^Iwpa_supplicant(4938): WPA: Association event - clear replay counter 
Sep  1 12:05:16 localhost NetworkManager: <information>^Iwpa_supplicant(4938): EAPOL: External notification - portEnabled=0 
Sep  1 12:05:16 localhost NetworkManager: <information>^Iwpa_supplicant(4938): EAPOL: SUPP_PAE entering state DISCONNECTED 
Sep  1 12:05:16 localhost NetworkManager: <information>^Iwpa_supplicant(4938): EAPOL: SUPP_BE entering state INITIALIZE 
Sep  1 12:05:16 localhost NetworkManager: <information>^Iwpa_supplicant(4938): al notification - portValid=0 
Sep  1 12:05:16 localhost NetworkManager: <information>^Iwpa_supplicant(4938): EAPOL: External notification - portEnabled=1 
Sep  1 12:05:16 localhost NetworkManager: <information>^Iwpa_supplicant(4938): EAPOL: SUPP_PAE entering state S_FORCE_AUTH 
Sep  1 12:05:16 localhost NetworkManager: <information>^Iwpa_supplicant(4938): EAPOL: SUPP_BE entering state IDLE 
Sep  1 12:05:16 localhost NetworkManager: <information>^Iwpa_supplicant(4938): Cancelling authentication timeout 
Sep  1 12:05:16 localhost NetworkManager: <information>^Iwpa_supplicant(4938): State: ASSOCIATED -> COMPLETED 
Sep  1 12:05:16 localhost NetworkManager: <information>^Iwpa_supplicant(4938): CTRL-EVENT-CONNECTED - Connection to 00:12:44:b1:e8:b0 completed (reauth) 
Sep  1 12:05:16 localhost NetworkManager: <information>^Iwpa_supplicant(4938): CTRL_IFACE monitor send - hexdump(len=42): 2f 76 61 72 2f 72 75 6e 2f 4e 65 74 77 6f 72 6b 4d 61 6e 61 67 65 72 2f 77 70 61 5f 63 74 72 6c 5f 34 34 39 34 2d 31 00 00 00 
Sep  1 12:05:16 localhost NetworkManager: <information>^Iwpa_supplicant(4938): RTM_NEWLINK, IFLA_IFNAME: Interface 'eth1' added 
Sep  1 12:05:16 localhost NetworkManager: <information>^Iwpa_supplicant(4938): Wireless event: cmd=0x8b15 len=20 
Sep  1 12:05:16 localhost NetworkManager: <information>^Iwpa_supplicant(4938): Wireless event: new AP: 00:12:44:b1:e8:b0 
Sep  1 12:05:16 localhost NetworkManager: <information>^Iwpa_supplicant(4938): State: COMPLETED -> ASSOCIATED 
Sep  1 12:05:16 localhost NetworkManager: <information>^Iwpa_supplicant(4938): Associated with 00:12:44:b1:e8:b0 
Sep  1 12:05:16 localhost NetworkManager: <information>^Iwpa_supplicant(4938): CTRL_IFACE monitor send - hexdump(len=42): 2f 76 61 72 2f 72 75 6e 2f 4e 65 74 77 6f 72 6b 4d 61 6e 61 67 65 72 2f 77 70 61 5f 63 74 72 6c 5f 34 34 39 34 2d 31 00 00 00 
Sep  1 12:05:16 localhost NetworkManager: <information>^Iwpa_supplicant(4938): WPA: Association event - clear replay counter 
Sep  1 12:05:16 localhost NetworkManager: <information>^Iwpa_supplicant(4938): EAPOL: External notification - portEnabled=0 
Sep  1 12:05:16 localhost NetworkManager: <information>^Iwpa_supplicant(4938): EAPOL: SUPP_PAE entering state DISCONNECTED 
Sep  1 12:05:16 localhost NetworkManager: <information>^Iwpa_supplicant(4938): EAPOL: SUPP_BE entering state INITIALIZE 
Sep  1 12:05:28 localhost kernel: [17179770.400000] BUG: soft lockup detected on CPU#0!
```

---

### Post by Game_Ender on 2006-09-01
This appears to be bug [37773]("https://launchpad.net/distros/ubuntu/+source/linux-restricted-modules-2.6.15/+bug/37773") in ubuntu.  Just to confirm it appears that changing from madwifi-old to madwifi-ng fixes the problem, is true, and if so how do I go about doing that?

---

