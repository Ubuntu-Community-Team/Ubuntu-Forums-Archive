---
title: "Wireless doesn't works"
date: 2009-09-18
forum: Hardware
---

### Post by Cebonet on 2009-09-18
I had problems since I upgraded to jaunty. The wireless device is recognized, but I think i wouldn't start.
  I installed wicd hoping it would work, but when I opened I got this massage:
"trådløs nødafbryder aktiveret" translated from danish to english "wireless emergency cutout activated"
Any ideas to solve this problem?

I have a Intel PRO/Wireless 2200BG 

When I type iwconfig:

> lo        no wireless extensions.

eth0      no wireless extensions.

eth1      radio off  ESSID:off/any  
          Mode:Managed  Channel:0  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power=off   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

And when I type dmesg in terminal I get this:
>  low) -> IRQ 10
[   13.373495] mmc0: SDHCI controller on PCI [0000:02:04.4] using PIO
[   13.373556] mmc1: SDHCI controller on PCI [0000:02:04.4] using PIO
[   13.373616] mmc2: SDHCI controller on PCI [0000:02:04.4] using PIO
[   13.373998] ipw2200 0000:02:06.0: enabling device (0000 -> 0002)
[   13.374291] ACPI: PCI Interrupt Link [LNKE] enabled at IRQ 11
[   13.374295] ipw2200 0000:02:06.0: PCI INT A -> Link[LNKE] -> GSI 11 (level, low) -> IRQ 11
[   13.377175] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
[   13.377220] ipw2200 0000:02:06.0: firmware: requesting ipw2200-bss.fw
[   13.613773] ipw2200: Radio Frequency Kill Switch is On:
[   13.613775] Kill switch must be turned off for wireless networking to work.
[   13.615845] ipw2200: Detected geography ZZM (11 802.11bg channels, 0 802.11a 

notice: Kill switch must be turned off for wireless networking to work

---

