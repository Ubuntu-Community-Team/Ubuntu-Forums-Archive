---
title: "no measurable reduction in power consumption/cpu-freq"
date: 2009-03-31
forum: Hardware
---

### Post by graysky on 2009-03-31
I have a Kill-a-watt that measures a power draw in Watts. I was curious to see what sort of real energy reduction the acpi in my kernel was affording to me so I measured the idle system under the two available multipliers both at the stock level for my system, and the overclocked level.

The bottom line is that there was no difference!

Hardware Details:
CPU: Intel X3360 (Xeon version of the 45nm quad-core Q9550)
Memory: 2x2 Gb DDR2
Motherboard: DFI LT LP P35-T2R
HDD: 2x Seagate 7200.11 (640 Gb)
Fans: 5x120mm 1500 RPM fans
Videocard: PCI-E 16X 8400GS

The stock setting was a FSB of 333 MHz under both the 6.0x and 8.5x multiplier w/ the RAM running @ 1,066 MHz. The low idle was 2.00 GHz and the full idle was 2.83 GHz. The overclocked setting was a FSB of 400 MHz under both the 6.0x and 8.5x multiplier w/ the RAM running @ 1,000 MHz. The low idle was 2.40 GHz and the full idle was 3.40 GHz.

Under stock conditions, the power consumption idle (just logged into Gnome with nothing running) was 92 Watts @ 2.00 GHz and also 92 Watts @ 2.83 GHz. Under overclocked conditions, the power consumption idle (just logged into Gnome with nothing running was 98 Watts @ 2.40 GHz and also 98 Watts @ 3.40 GHz.

What gives? I was led to believe that adjusting the CPU frequency saved power on idle. According to these readings, there is no difference between the two multipliers.

---

### Post by Dark_Stang on 2009-03-31
There is going to be very little difference in power consumption. If it was a laptop, it would be a different story. The processor on my laptop clocks between 800mhz and 1.9ghz.

---

