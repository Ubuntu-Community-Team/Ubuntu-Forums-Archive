---
title: "Intel® Core™2 Duo CPU P7350 problem with cpufreq-tools"
date: 2012-01-09
forum: Hardware
---

### Post by Cappy Fruit on 2012-01-09
Hi all,

I have a laptop with an Intel® Core™2 Duo CPU P7350 processor in it. This is the link to see its properties: [http://ark.intel.com/products/36750/Intel-Core2-Duo-Processor-P7350-%283M-Cache-2_00-GHz-1066-MHz-FSB%29](http://ark.intel.com/products/36750/Intel-Core2-Duo-Processor-P7350-%283M-Cache-2_00-GHz-1066-MHz-FSB%29)
I have installed Ubuntu 11.10 and it works well but i have a little problem.
My CPU's max freq should be 2 GHz but i cannot set it up.

cpufreq-info said:

cpufrequtils 007: cpufreq-info (C) Dominik Brodowski 2004-2009
Report errors and bugs to [email]cpufreq@vger.kernel.org[/email], please.
analyzing CPU 0:
  driver: acpi-cpufreq
  CPUs which run at the same hardware frequency: 0
  CPUs which need to have their frequency coordinated by software: 0
  maximum transition latency: 10.0 us.
  hardware limits: 1.34 GHz - 1.60 GHz
  available frequency steps: 1.60 GHz, 1.34 GHz
  available cpufreq governors: conservative, ondemand, userspace, powersave, performance
  current policy: frequency should be within 1.34 GHz and 1.60 GHz.
                  The governor "ondemand" may decide which speed to use
                  within this range.
  current CPU frequency is 1.34 GHz.
  cpufreq stats: 1.60 GHz:5,96%, 1.34 GHz:94,04%  (127859)
analyzing CPU 1:
  driver: acpi-cpufreq
  CPUs which run at the same hardware frequency: 1
  CPUs which need to have their frequency coordinated by software: 1
  maximum transition latency: 10.0 us.
  hardware limits: 1.34 GHz - 1.60 GHz
  available frequency steps: 1.60 GHz, 1.34 GHz
  available cpufreq governors: conservative, ondemand, userspace, powersave, performance
  current policy: frequency should be within 1.34 GHz and 1.60 GHz.
                  The governor "ondemand" may decide which speed to use
                  within this range.
  current CPU frequency is 1.34 GHz.
  cpufreq stats: 1.60 GHz:5,65%, 1.34 GHz:94,35%  (104853)

I think this some kind of driver problem but i cannot find any driver. I downloaded one datasheet from the intel's homepage but i don't really know how to use it.
Is there anyone who can help me with this issue?

Thx for the replies already:p

---

