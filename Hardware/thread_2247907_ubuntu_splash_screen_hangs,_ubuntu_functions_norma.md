---
title: "ubuntu splash screen hangs, ubuntu functions normally"
date: 2014-10-11
forum: Hardware
---

### Post by rvanlaar on 2014-10-11
My laptop screen keeps on displaying the purple ubuntu splash screen and won't display the 'login' screen.
This started happening in the last month or so. 

The login screen is displayed just fine on an external monitor. 
Going to settings -> displays, setting the internal monitor to off, select apply, and click 'Restore previous configuration'
lets me use the internal display just fine.

This happens when I enable optimus support in the bios and have the nvidia card selected in 'PRIME Profiles'.
When I select the intel card I don't have this problem.

I've reinstalled the nvidia-331.38 from nvidia, and also tried  nviaia-331-updates, this didn't solve my problem.

Any ideas on how to solve this problem?

My Specs:
dell latitude E6520
lspci |grep -i vga
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
01:00.0 VGA compatible controller: NVIDIA Corporation GF119M [NVS 4200M] (rev a1)

---

