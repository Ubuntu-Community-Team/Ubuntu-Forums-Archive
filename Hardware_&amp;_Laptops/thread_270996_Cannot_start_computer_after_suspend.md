---
title: "Cannot start computer after suspend"
date: 2006-10-04
forum: Hardware &amp; Laptops
---

### Post by RafRaf on 2006-10-04
I have a serius problem that I do not know if it related to Ubuntu or the hardware itself. If anyone could help or give suggestion itwould be a great help.

Sometimes after suspend to RAM, the resume does not work: fan starts on max power but no screen or keyboard. After 10 seconds the computer goes dead.

Now to the strange part. After this happens, I cannot restart the computer! Every time I try I get the same 10 seconds of fan going nuts. AND this happens even after I remove the power source and the battery. :confused: 

After a few hours with the battery plugged out the computer starts again like normal.

Please help. I have a hp nc6000 laptop with ATI running fglrx driver (latest). No XGL or similar. I fear either the harddrive or RAM is broken..?

---

### Post by RafRaf on 2006-10-04
Anyone?

---

### Post by the_0ne on 2006-10-04
> **RafRaf said:**
> I have a serius problem that I do not know if it related to Ubuntu or the hardware itself. If anyone could help or give suggestion itwould be a great help.

Sometimes after suspend to RAM, the resume does not work: fan starts on max power but no screen or keyboard. After 10 seconds the computer goes dead.

Now to the strange part. After this happens, I cannot restart the computer! Every time I try I get the same 10 seconds of fan going nuts. AND this happens even after I remove the power source and the battery. :confused: 

After a few hours with the battery plugged out the computer starts again like normal.

Please help. I have a hp nc6000 laptop with ATI running fglrx driver (latest). No XGL or similar. I fear either the harddrive or RAM is broken..?

Hate to say it, I have on real help, but it has happened to me before. Many times actually.  I have the exact same symptoms also.  Strange thing, after many, many times of trying to start it up, I just let it go.  Let it sit for awhile and then try again and then it works.  Not sure why.  I definitely do not hibernate anymore, only ever shut down.  :(  I thought it was a hardware problem until I finally found somebody that has the exact same problem.

---

### Post by roger_doger on 2006-10-05
I have the same problems on my laptop. Looks a problem with the acpi manager, but I am new to linux and don't have much of clue as to how to fix it, yet.

---

### Post by xyz on 2006-10-05
Hi folks!
Check my sig for Suspend/Hibernate Laptops...It worked fantastic for me.
I suspend in less than 2 seconds and resume in about 5.
Hope it works for you too.

---

### Post by CallMeIke on 2006-10-05
Hey,
  I'm having a similar problem.  Something I've done recently has made it so that my Laptop (Alienware 5500) will no longer start after a suspend/hibernate (although it used to work, mostly).  Perhaps this section of the syslog is a clue?  It occurs every time that the restart fails.  eth0 is down, and eth1, the wireless card, should be up.  Note the " Uhhuh. NMI received. Dazed and confused..." message:

[SIZE="1"][FONT="Courier New"]Oct  5 07:45:56 localhost kernel: [17179812.292000] Restarting tasks... done
Oct  5 07:45:57 localhost kernel: [17179813.004000] hda: drive_cmd: status=0x51 { DriveReady SeekComplete Error }
Oct  5 07:45:57 localhost kernel: [17179813.004000] hda: drive_cmd: error=0x04 { AbortedCommand }
Oct  5 07:45:57 localhost kernel: [17179813.004000] ide: failed opcode was: 0xec
Oct  5 07:45:57 localhost kernel: [17179813.124000] r8169 Gigabit Ethernet driver 2.2LK loaded
Oct  5 07:45:57 localhost kernel: [17179813.124000] ACPI: PCI Interrupt 0000:05:05.0[A] -> GSI 19 (level, low) -> IRQ 225
Oct  5 07:45:57 localhost kernel: [17179813.124000] eth0: Identified chip type is 'RTL8169s/8110s'.
Oct  5 07:45:57 localhost kernel: [17179813.124000] eth0: RTL8169 at 0xf8a56800, 00:03:0d:4e:c1:15, IRQ 225
Oct  5 07:45:57 localhost kernel: [17179813.140000] ieee80211_1_1_13_crypt: registered algorithm 'NULL'
Oct  5 07:45:57 localhost kernel: [17179813.144000] ieee80211_1_1_13: 802.11 data/management/control stack, 1.1.13
Oct  5 07:45:57 localhost kernel: [17179813.144000] ieee80211_1_1_13: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
Oct  5 07:45:57 localhost kernel: [17179813.144000] ieee80211: 802.11 data/management/control stack, git-1.1.7
Oct  5 07:45:57 localhost kernel: [17179813.144000] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
Oct  5 07:45:57 localhost kernel: [17179813.156000] ipw3945: Intel(R) PRO/Wireless 3945 Network Connection driver for Linux, 1.0.5m
Oct  5 07:45:57 localhost kernel: [17179813.156000] ipw3945: Copyright(c) 2003-2006 Intel Corporation
Oct  5 07:45:57 localhost kernel: [17179813.156000] ACPI: PCI Interrupt 0000:04:00.0[A] -> GSI 18 (level, low) -> IRQ 185
Oct  5 07:45:57 localhost kernel: [17179813.160000] PCI: Setting latency timer of device 0000:04:00.0 to 64
Oct  5 07:45:57 localhost kernel: [17179813.160000] ipw3945: Detected Intel PRO/Wireless 3945ABG Network Connection
Oct  5 07:45:57 localhost dhclient: Internet Systems Consortium DHCP Client V3.0.3
Oct  5 07:45:57 localhost dhclient: Copyright 2004-2005 Internet Systems Consortium.
Oct  5 07:45:57 localhost dhclient: All rights reserved.
Oct  5 07:45:57 localhost dhclient: For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)
Oct  5 07:45:57 localhost dhclient: 
Oct  5 07:45:57 localhost kernel: [17179813.240000] r8169: eth0: link down
Oct  5 07:45:57 localhost kernel: [17179813.240000] ADDRCONF(NETDEV_UP): eth0: link is not ready
Oct  5 07:45:58 localhost dhclient: Listening on LPF/eth0/00:03:0d:4e:c1:15
Oct  5 07:45:58 localhost dhclient: Sending on   LPF/eth0/00:03:0d:4e:c1:15
Oct  5 07:45:58 localhost dhclient: Sending on   Socket/fallback
Oct  5 07:46:02 localhost dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
Oct  5 07:46:10 localhost dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
Oct  5 07:46:23 localhost dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 19
Oct  5 07:46:42 localhost dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
Oct  5 07:46:52 localhost dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
Oct  5 07:47:02 localhost dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 1
Oct  5 07:47:03 localhost dhclient: No DHCPOFFERS received.
Oct  5 07:47:03 localhost dhclient: No working leases in persistent database - sleeping.
Oct  5 07:54:19 localhost kernel: [17179814.016000] Uhhuh. NMI received. Dazed and confused, but trying to continue
Oct  5 07:54:19 localhost kernel: [17179814.016000] You probably have a hardware problem with your RAM chips
[/FONT][/SIZE]

Here's the log for the same interval, from messages:

[SIZE="1"][FONT="Courier New"]Oct  5 07:45:56 localhost kernel: [17179811.288000] ACPI: PCI Interrupt 0000:05:04.0[A] -> GSI 18 (level, low) -> IRQ 185
Oct  5 07:45:56 localhost kernel: [17179812.044000] ata1: dev 0 configured for UDMA/133
Oct  5 07:45:56 localhost kernel: [17179812.292000] Restarting tasks... done
Oct  5 07:45:57 localhost kernel: [17179813.004000] hda: drive_cmd: status=0x51 { DriveReady SeekComplete Error }
Oct  5 07:45:57 localhost kernel: [17179813.004000] hda: drive_cmd: error=0x04 { AbortedCommand }
Oct  5 07:45:57 localhost kernel: [17179813.004000] ide: failed opcode was: 0xec
Oct  5 07:45:57 localhost kernel: [17179813.124000] r8169 Gigabit Ethernet driver 2.2LK loaded
Oct  5 07:45:57 localhost kernel: [17179813.124000] ACPI: PCI Interrupt 0000:05:05.0[A] -> GSI 19 (level, low) -> IRQ 225
Oct  5 07:45:57 localhost kernel: [17179813.124000] eth0: RTL8169 at 0xf8a56800, 00:03:0d:4e:c1:15, IRQ 225
Oct  5 07:45:57 localhost kernel: [17179813.144000] ieee80211_1_1_13: 802.11 data/management/control stack, 1.1.13
Oct  5 07:45:57 localhost kernel: [17179813.144000] ieee80211_1_1_13: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
Oct  5 07:45:57 localhost kernel: [17179813.144000] ieee80211: 802.11 data/management/control stack, git-1.1.7
Oct  5 07:45:57 localhost kernel: [17179813.144000] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
Oct  5 07:45:57 localhost kernel: [17179813.156000] ipw3945: Intel(R) PRO/Wireless 3945 Network Connection driver for Linux, 1.0.5m
Oct  5 07:45:57 localhost kernel: [17179813.156000] ipw3945: Copyright(c) 2003-2006 Intel Corporation
Oct  5 07:45:57 localhost kernel: [17179813.156000] ACPI: PCI Interrupt 0000:04:00.0[A] -> GSI 18 (level, low) -> IRQ 185
Oct  5 07:45:57 localhost kernel: [17179813.160000] ipw3945: Detected Intel PRO/Wireless 3945ABG Network Connection
Oct  5 07:45:57 localhost kernel: [17179813.240000] r8169: eth0: link down
Oct  5 07:45:57 localhost kernel: [17179813.240000] ADDRCONF(NETDEV_UP): eth0: link is not ready
Oct  5 07:54:19 localhost kernel: [17179814.016000] Uhhuh. NMI received. Dazed and confused, but trying to continue
Oct  5 07:54:19 localhost kernel: [17179814.016000] You probably have a hardware problem with your RAM chips
Oct  5 07:54:19 localhost kernel: [17179814.148000] ipw3945: Detected geography ABG (11 802.11bg channels, 13 802.11a channels)
Oct  5 07:54:59 localhost kernel: [17180354.528000] ACPI: Power Button (FF) [PWRF]
[/FONT][/SIZE]

---

### Post by RafRaf on 2006-10-06
Hi again,

I found a workaround for my suspend problem.
Using the script described in [http://www.linux.com/article.pl?sid=06/05/24/1716222](http://www.linux.com/article.pl?sid=06/05/24/1716222) works. The laptop resumes just fine. Every time. 

However, I have not yet figured out how to execute this script when the laptop lid closes. I have changed the action of /etc/acpi/event/lid to run my script but that did not work (i.e. I get the same problem as described in my first post).

Anyway..Im sorta happy even though this means going around the problem instead of fixing what is wrong.

---

### Post by RafRaf on 2006-10-06
By the way, thanks xyz for the tip! :)

---

### Post by xyz on 2006-10-06
> **RafRaf said:**
> By the way, thanks xyz for the tip! :)
No problem RafRaf...glad I could pass on something I learned and that it worked. Good day!

---

### Post by jjhart on 2006-10-25
I have the nc6000 also and the exact same problem happened to me when I had WinXP installed.  It turns out that the motherboard/bios might also be defective.  I sent it in for warranty repair twice for the same problem in three months.  After the second fix it has worked flawlessly.  Unfortunately, if you are running linux, they might blame it on that and not fix it, or at they would at least wipe your drive.  I had two partitions on mine, but not with linux at the time, just WinXP and then a documents partition.  Because that wasn't the way it came from the factory, they wiped it and reinstalled the factory branded OEM windows onto it. (Which I promptly removed).  You might look into seeing if it isn't a hardware issue also.

---

### Post by RafRaf on 2006-10-25
ok, thanks. 

It still happens. Allthough not so often anymore using the suspend script.

---

### Post by xyz on 2006-10-26
> **RafRaf said:**
> ok, thanks. 

It still happens. Allthough not so often anymore using the suspend script.
I still happened to me as well from time to time when I pressed ANY key to resume. It has never happened again (so far) when I press the power button to resume. (fingers crossed).

---

### Post by RafRaf on 2006-10-29
Hi all again. The problems have gotten far worse lately. I presume it is a hardware problem or it is related to upgrading to edgy. 

The suspend script now does not help. Almost every time I suspend the computer now comes to this state that it not possible to start it. It also happens now after shut downs. :( 

Can anybody help? Is it Hardware related or software? Shall I do a clean install? Buy a new computer?

---

### Post by xyz on 2006-10-30
Hi-
Did you by any chance do a backing up of your system which you could restore to a time back when it worked 'better'?
That could also help see if it is hardware or not.

---

### Post by RafRaf on 2006-10-31
Hi, I tried to reinstall acpi-support but it did not help. I have found though that it only happens when not connected to AC.

Here is a log print out shortly after suspend:

Oct 31 17:41:57 localhost gnome-power-manager: (martin) Suspending computer because the power button has been pressed
Oct 31 17:41:59 localhost kernel: [17210127.968000] ACPI: PCI interrupt for device 0000:02:04.0 disabled
Oct 31 17:41:59 localhost kernel: [17210127.968000] ath_pci: driver unloaded
Oct 31 17:41:59 localhost kernel: [17210127.972000] ath_rate_sample: unloaded
Oct 31 17:41:59 localhost kernel: [17210127.972000] ath_hal: driver unloaded
Oct 31 17:41:59 localhost kernel: [17210128.004000] ACPI: PCI interrupt for device 0000:02:0e.0 disabled

There is no logs from when the computer is started and hangs.

---

### Post by RafRaf on 2006-10-31
Here is the log from when it works (resume from AC):


Oct 31 18:52:07 localhost gnome-power-manager: (martin) Suspending computer because the power button has been pressed
Oct 31 18:52:09 localhost kernel: [17182032.100000] ACPI: PCI interrupt for device 0000:02:04.0 disabled
Oct 31 18:52:09 localhost kernel: [17182032.100000] ath_pci: driver unloaded
Oct 31 18:52:09 localhost kernel: [17182032.104000] ath_rate_sample: unloaded
Oct 31 18:52:09 localhost kernel: [17182032.104000] ath_hal: driver unloaded
Oct 31 18:52:09 localhost kernel: [17182032.136000] ACPI: PCI interrupt for device 0000:02:0e.0 disabled
Oct 31 18:52:30 localhost kernel: [17182036.032000] Stopping tasks: ==============================================================================================|
Oct 31 18:52:30 localhost kernel: [17182037.132000] pnp: Device 00:05 disabled.
Oct 31 18:52:30 localhost kernel: [17182037.136000] pnp: Device 00:02 disabled.
Oct 31 18:52:30 localhost kernel: [17182037.136000] ACPI: PCI interrupt for device 0000:02:06.3 disabled
Oct 31 18:52:30 localhost kernel: [17182037.136000] ACPI: PCI interrupt for device 0000:02:06.1 disabled
Oct 31 18:52:30 localhost kernel: [17182037.136000] ACPI: PCI interrupt for device 0000:02:06.0 disabled
Oct 31 18:52:30 localhost kernel: [17182038.380000] ACPI: PCI interrupt for device 0000:01:00.0 disabled
Oct 31 18:52:30 localhost kernel: [17182038.380000] ACPI: PCI interrupt for device 0000:00:1f.5 disabled
Oct 31 18:52:30 localhost kernel: [17182038.380000] ACPI: PCI interrupt for device 0000:00:1d.7 disabled
Oct 31 18:52:30 localhost kernel: [17182038.396000] ACPI: PCI interrupt for device 0000:00:1d.2 disabled
Oct 31 18:52:30 localhost kernel: [17182038.396000] ACPI: PCI interrupt for device 0000:00:1d.1 disabled
Oct 31 18:52:30 localhost kernel: [17182038.396000] ACPI: PCI interrupt for device 0000:00:1d.0 disabled
Oct 31 18:52:30 localhost kernel: [17182046.396000] ACPI: Transitioning device [C20F] to D3
Oct 31 18:52:30 localhost kernel: [17182046.396000] ACPI: Transitioning device [C20F] to D3
Oct 31 18:52:30 localhost kernel: [17182046.396000] ACPI: Transitioning device [C210] to D3
Oct 31 18:52:30 localhost kernel: [17182046.396000] ACPI: Transitioning device [C210] to D3
Oct 31 18:52:30 localhost kernel: [17182046.396000] ACPI: Transitioning device [C211] to D3
Oct 31 18:52:30 localhost kernel: [17182046.396000] ACPI: Transitioning device [C211] to D3
Oct 31 18:52:30 localhost kernel: [17182046.396000] ACPI: Transitioning device [C212] to D3
Oct 31 18:52:30 localhost kernel: [17182046.396000] ACPI: Transitioning device [C212] to D3
Oct 31 18:52:30 localhost kernel: [17182046.824000] PCI: Enabling device 0000:00:1d.0 (0000 -> 0001)
Oct 31 18:52:30 localhost kernel: [17182046.824000] ACPI: PCI Interrupt 0000:00:1d.0[A] -> Link [C0C1] -> GSI 10 (level, low) -> IRQ 10
Oct 31 18:52:30 localhost kernel: [17182046.824000] usb usb1: root hub lost power or was reset
Oct 31 18:52:30 localhost kernel: [17182046.824000] PCI: Enabling device 0000:00:1d.1 (0000 -> 0001)
Oct 31 18:52:30 localhost kernel: [17182046.824000] ACPI: PCI Interrupt 0000:00:1d.1[B] -> Link [C0C4] -> GSI 10 (level, low) -> IRQ 10
Oct 31 18:52:30 localhost kernel: [17182046.824000] usb usb2: root hub lost power or was reset
Oct 31 18:52:30 localhost kernel: [17182046.824000] PCI: Enabling device 0000:00:1d.2 (0000 -> 0001)
Oct 31 18:52:30 localhost kernel: [17182046.824000] ACPI: PCI Interrupt 0000:00:1d.2[C] -> Link [C0C3] -> GSI 10 (level, low) -> IRQ 10
Oct 31 18:52:30 localhost kernel: [17182046.824000] usb usb3: root hub lost power or was reset
Oct 31 18:52:30 localhost kernel: [17182046.840000] PCI: Enabling device 0000:00:1d.7 (0000 -> 0002)
Oct 31 18:52:30 localhost kernel: [17182046.840000] ACPI: PCI Interrupt 0000:00:1d.7[D] -> Link [C0C8] -> GSI 10 (level, low) -> IRQ 10
Oct 31 18:52:30 localhost kernel: [17182046.840000] usb usb4: root hub lost power or was reset
Oct 31 18:52:30 localhost kernel: [17182046.840000] ehci_hcd 0000:00:1d.7: debug port 1
Oct 31 18:52:30 localhost kernel: [17182046.844000] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
Oct 31 18:52:30 localhost kernel: [17182046.848000] ACPI: PCI Interrupt 0000:00:1f.1[A] -> Link [C0C3] -> GSI 10 (level, low) -> IRQ 10
Oct 31 18:52:30 localhost kernel: [17182046.848000] ACPI: PCI Interrupt 0000:00:1f.5[B] -> Link [C0C2] -> GSI 11 (level, low) -> IRQ 11
Oct 31 18:52:30 localhost kernel: [17182047.104000] ACPI: PCI Interrupt 0000:01:00.0[A] -> Link [C0C1] -> GSI 10 (level, low) -> IRQ 10
Oct 31 18:52:30 localhost kernel: [17182047.248000] ACPI: PCI Interrupt 0000:02:06.0[A] -> Link [C0C3] -> GSI 10 (level, low) -> IRQ 10
Oct 31 18:52:30 localhost kernel: [17182047.248000] Yenta O2: res at 0x94/0xD4: ea/00
Oct 31 18:52:30 localhost kernel: [17182047.248000] Yenta O2: enabling read prefetch/write burst
Oct 31 18:52:30 localhost kernel: [17182047.248000] ACPI: PCI Interrupt 0000:02:06.1[A] -> Link [C0C3] -> GSI 10 (level, low) -> IRQ 10
Oct 31 18:52:30 localhost kernel: [17182047.248000] ACPI: PCI Interrupt 0000:02:06.3[A] -> Link [C0C3] -> GSI 10 (level, low) -> IRQ 10
Oct 31 18:52:30 localhost kernel: [17182047.260000] pnp: Device 00:02 activated.
Oct 31 18:52:30 localhost kernel: [17182047.260000] pnp: Device 00:05 activated.
Oct 31 18:52:30 localhost kernel: [17182047.260000] pnp: Device 00:0a does not support activation.
Oct 31 18:52:30 localhost kernel: [17182047.260000] pnp: Device 00:0b does not support activation.
Oct 31 18:52:30 localhost kernel: [17182054.240000] Restarting tasks...<6>usb 3-1: USB disconnect, address 2
Oct 31 18:52:30 localhost kernel: [17182054.300000]  done
Oct 31 18:52:31 localhost kernel: [17182055.140000] ath_hal: 0.9.17.2 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2413, RF5413)
Oct 31 18:52:31 localhost kernel: [17182055.140000] ath_rate_sample: 1.2 (0.9.2)
Oct 31 18:52:31 localhost kernel: [17182055.152000] ath_pci: 0.9.4.5 (0.9.2)
Oct 31 18:52:31 localhost kernel: [17182055.152000] ACPI: PCI Interrupt 0000:02:04.0[A] -> Link [C0C6] -> GSI 11 (level, low) -> IRQ 11
Oct 31 18:52:32 localhost kernel: [17182055.428000] usb 3-1: new full speed USB device using uhci_hcd and address 3
Oct 31 18:52:32 localhost kernel: [17182055.508000] wifi0: 11b rates: 1Mbps 2Mbps 5.5Mbps 11Mbps
Oct 31 18:52:32 localhost kernel: [17182055.508000] wifi0: 11g rates: 1Mbps 2Mbps 5.5Mbps 11Mbps 6Mbps 9Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps
Oct 31 18:52:32 localhost kernel: [17182055.508000] wifi0: H/W encryption support: WEP AES AES_CCM TKIP
Oct 31 18:52:32 localhost kernel: [17182055.508000] wifi0: mac 5.6 phy 4.1 radio 1.7
Oct 31 18:52:32 localhost kernel: [17182055.508000] wifi0: Use hw queue 1 for WME_AC_BE traffic
Oct 31 18:52:32 localhost kernel: [17182055.508000] wifi0: Use hw queue 0 for WME_AC_BK traffic
Oct 31 18:52:32 localhost kernel: [17182055.508000] wifi0: Use hw queue 2 for WME_AC_VI traffic
Oct 31 18:52:32 localhost kernel: [17182055.508000] wifi0: Use hw queue 3 for WME_AC_VO traffic
Oct 31 18:52:32 localhost kernel: [17182055.508000] wifi0: Use hw queue 8 for CAB traffic
Oct 31 18:52:32 localhost kernel: [17182055.508000] wifi0: Use hw queue 9 for beacons
Oct 31 18:52:32 localhost kernel: [17182055.564000] wifi0: Atheros 5212: mem=0x90080000, irq=11
Oct 31 18:52:32 localhost kernel: [17182055.580000] tg3.c:v3.59.1 (August 25, 2006)
Oct 31 18:52:32 localhost kernel: [17182055.580000] ACPI: PCI Interrupt 0000:02:0e.0[A] -> Link [C0C5] -> GSI 11 (level, low) -> IRQ 11
Oct 31 18:52:32 localhost kernel: [17182055.656000] usb 3-1: configuration #1 chosen from 1 choice
Oct 31 18:52:32 localhost kernel: [17182056.004000] tg3: eth0: Link is down.
Oct 31 18:52:32 localhost kernel: [17182056.028000] ADDRCONF(NETDEV_UP): eth0: link is not ready
Oct 31 18:52:32 localhost kernel: [17182056.168000] eth0: Tigon3 [partno(BMC5705mA3) rev 3003 PHY(5705)] (PCI:33MHz:32-bit) 10/100/1000BaseT Ethernet 00:0d:9d:90:50:85
Oct 31 18:52:32 localhost kernel: [17182056.168000] eth0: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[0] Split[0] WireSpeed[0] TSOcap[1] 
Oct 31 18:52:32 localhost kernel: [17182056.168000] eth0: dma_rwctrl[763f0000] dma_mask[64-bit]
Oct 31 18:52:32 localhost gnome-power-manager: (martin) Resuming computer

---

### Post by RafRaf on 2006-10-31
This [https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.17/+bug/63967]("https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.17/+bug/63967") might be related

---

### Post by rrwo on 2006-11-01
I have the same problem on my ThinkPad Z60m, running Edgy: I am unable to restore from a suspend. The computer seems to power up, but nothing happens.

I also had a similar problem on the same laptop running Dapper, although strangely one of the kernel updates of Dapper fixed it (though I'm told it broke it for other people).

However, Hibernate does work. It takes a long time (20 seconds), but it shuts down and restores with no problem.

---

### Post by rrwo on 2006-11-01
> Now to the strange part. After this happens, I cannot restart the computer! Every time I try I get the same 10 seconds of fan going nuts. AND this happens even after I remove the power source and the battery.

After a few hours with the battery plugged out the computer starts again like normal.


On most laptops, you need only hold the power button for 10 seconds to force it to power down and then up again.  No need to remove the battery.

---

### Post by RafRaf on 2006-11-01
Yeah, I know. The strange thing here is that the computer does not start up after this happens..even though I remove all power sources. Im guessing that there is some bios battery that keeps the computer alive and in this bad state.

---

### Post by rrwo on 2006-11-02
> I found a workaround for my suspend problem.
Using the script described in [http://www.linux.com/article.pl?sid=06/05/24/1716222](http://www.linux.com/article.pl?sid=06/05/24/1716222) works

That script does not work for me.

---

### Post by hardyn on 2006-11-02
try removing the fglrx driver... my machine would not even shutdown with the ATI drivers installed.  moving to the radeon drivers allowed everything to work natively.  and im really quite happy with it... yes im not keen about losing the video performance, but im not much of a gamer so im really okey about it... it looks like we are going to have to sit tight until ATI can get a us a driver that works.

arlen.

---

### Post by rrwo on 2006-11-02
That didn't help. The system still crashes. (I'm using the i810 driver anyhow.)

---

### Post by Kira-cjd on 2006-11-02
i thinik it would be ur ram but take ur ram chips out and put them in some 1 elase laptop

---

### Post by Kira-cjd on 2006-11-02
well i think u should re install ubuntu other than that i dont know what 2 do

---

### Post by hardyn on 2006-11-02
I agree that the reinstall cant hurt... how old what type of notebook is it? it may be an acpi related problem.  i think that blaming the ram right away is a big agressive, esp. if it hasn't been giving you trouble before. (plus removing ram on some machines can be a real pain)

---

### Post by rrwo on 2006-11-03
It's not a problem with the RAM. Everything worked in Dapper.

---

### Post by fetus on 2007-06-18
I have the same problem as well. I tried to suspend, it seemed to work (except that my fan didn't turn off). I tried to resume, nothing happened. So I powered down by holding the power button. Now, I can't boot Windows XP or Ubuntu. Ubuntu freezes on startup screen with the progress bar and Windows goes black/inactive after the initial loading screen. I'm on a Vaio SZ with Ubuntu Studio installed via Wubi. Is the only solution to wait? What happens that fixes it after waiting?

Forgot to add: I can start Windows in safe mode - (wtf!)

---

### Post by fetus on 2007-06-18
I left the battery out for about 3 hours and now I finally booted successfully. Does anyone have any insight into *why* that worked? I'm looking for a more concrete solution here - not feeling too comfortable with the ol' wait-a-while solution..

---

