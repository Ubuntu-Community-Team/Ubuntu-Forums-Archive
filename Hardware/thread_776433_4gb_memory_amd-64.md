---
title: "4gb memory amd-64"
date: 2008-04-30
forum: Hardware
---

### Post by fbroce on 2008-04-30
I have had some trouble getting this to work but I finally found the cure! (at least on my system, Asus MV2-MX, 4gb ram, Nvidia 7600 GS).

I am running 8.04 with the nvidia driver and lilo. To correctly see the 4gb memory, enable the memory hole option in the bios. This allows you to boot without running Xorg and see 4gb memory. If  you run xorg you will get a large grainy cursor about 1" square.

To fix this add this to lilo.conf

append="iommu=65534,noagp,soft"

Actually, I had to also add:

append="noapic nolapic iommu=65534,noagp,soft"

since I was getting an annoying disk error.

run lilo and reboot. You should see this running the "free" command:

             total       used       free     shared    buffers     cached
Mem:       4054284     723224    3331060          0      15028     285352

---

