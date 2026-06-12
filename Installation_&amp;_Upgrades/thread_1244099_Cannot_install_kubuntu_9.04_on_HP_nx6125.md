---
title: "Cannot install kubuntu 9.04 on HP nx6125"
date: 2009-08-19
forum: Installation &amp; Upgrades
---

### Post by Kajin3k on 2009-08-19
Hello,
I have problem with installing new Kubuntu on my laptop (HP nx6125, Sempron 3100+ = 1.8GHz, 512 RAM, 60GB HDD,...). Firstly, laptop was not able to detect boot cd. I burned image on DVD and it's OK, instalation menu appeared. It's strange, that it needs DVD, but that's not main problem.

After pressing Install Kubuntu (I use alternative instalation CD, live does not work also), three messages appear on the screen for few seconds and then screen becomes black. 

powernow-k8: ph2 null fid transition 0xe
IO APIC resources could be not be allocated
Starting system log daemon: syslogd, klogd.

I googled and found that options noapic and nolapic can solve this problem. They didn't, problem persisted. I tried almost all combinations of install options, nothing worked. So I decided to switch of powernow and try all combinations of options again, but result was similar. Fisrtly few error messages about PnpBIOS (fatal error, set_dev_node: unexpected status 0x37, etc.), then
serial 00:0c: activation failed
and finaly
powernow-k8: BIOS error - no PSB or ACPI _PSS objects
IO APIC resources could be not be allocated

I flashed new bios (F13), still the same. It does not matter if I use live or alter CD/DVD. 

There were few older posts about similar problems, but no solution worked for me. Some people said, it was problem with VIA chipsets and bug in kernel, but I also found people, who used ubuntu/kubuntu without problems, so it must be possible. :) Few years back I used some old version of ubuntu on this laptop and it was all OK, then I installed debian, also without bigger problems. 

Does anybody know, what could solve this? Thx a lot and sorry for my english :)

---

