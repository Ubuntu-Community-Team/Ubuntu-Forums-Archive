---
title: "don't work ubuntu7.10"
date: 2008-01-19
forum: Hardware &amp; Laptops
---

### Post by xxxYURAxxx on 2008-01-19
i am install ubuntu 7.10 in my laptop (hp compaq 6710)
ubuntu is frozen when i try login & pass
when i boot in recovery mod after command 'startx' i can see this message:
ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
ata1.00: (irq_stat 0x40000001)
ata1.00: cmd c8/00:08:cb:c2:75/00:00:00:00:00/e8 tag 0 cdb 0x0 data 4096 in

my filesystem is good, in live cd i can write/read in partition with ubuntu

google say me try this:
1) boot with options noapic acpi=off
no result :(

launchpad say this:
2) The quick workaround for this on an installed system is to add "piix" to /etc/initramfs-tools/modules, and run "sudo update-initramfs -u"
no result :(

maybe this problem with smartmontools
if we need logs please say me

please help me

---

