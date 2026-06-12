---
title: "Problems with hplip"
date: 2014-06-21
forum: Hardware
---

### Post by kencamargo on 2014-06-21
I was installing a new multi-functional printer under Ubuntu 14.04 64  bits, and downloaded and ran hplip v. 3.14.6. At one point, it asks for a plugin file, which says it will download from the internet. At that point, it gets stuck doing nothing. If the process is interrupted at this point, the installer leaves a lock file under  /var that simply halts any new attemtp tp install.

I managed to work around this issue following this steps:
1. deleted as SU the lock file under /var/
2. downloaded  the necessary plugin file  from [https://www.openprinting.org/download/printdriver/auxfiles/HP/plugins/](https://www.openprinting.org/download/printdriver/auxfiles/HP/plugins/) -- both hplip-3.14.6-plugin.run and hplip-3.14.6-plugin.run.asc are necessary
3. ran hp-setup and  when the installer asked for the plugin file, I pointed to hplip-3.14.6-plugin.run

Et voilà!

---

### Post by oldfred on 2014-06-22
Good info.

Please post as solved and perhaps add 14.04 to title so others searching forum or with Google will find it.

---

