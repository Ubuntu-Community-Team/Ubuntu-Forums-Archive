---
title: "ubuntu 19.04 profile error"
date: 2019-09-24
forum: Hardware
---

### Post by sarto76 on 2019-09-24
[COLOR=#242729][FONT=Arial]When I start my computer this message appears:[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]Error found when loading /etc/profile: Find: '/usr/lib/modules/5.0.0-25-generic/kernel/drivers/thermal': File or directory not found[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]I controlled and I don't have the 5.0.0-25-generic module folder, I have the 13, 15, 16, 17, 20, 25, 27 and 27, but not the 25.[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]when I put this command:dpkg -l | grep -E 'linux-image-[0-9]+' | grep -Fv $(uname -r) i get also this line:[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]rc linux-image-5.0.0-25-generic 5.0.0-25.26 amd64 Signed kernel image generic[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]I read that means that the kernel has already been removed.[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]SO how can I correct the problem?[/FONT][/COLOR]

---

