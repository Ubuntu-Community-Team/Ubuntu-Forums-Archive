---
title: "Vmware-player"
date: 2008-12-23
forum: Installation &amp; Upgrades
---

### Post by markomk on 2008-12-23
i can't uninstall vmware-player :S i have also problem with instalation :S
how can i uninstall ?

---

### Post by lemming465 on 2008-12-26
I haven't fiddled with vmware player much recently, as I mostly deal with vmware workstation and vmware server.  Normally vmware installs a link such as */usr/bin/vmware-uninstall* to its built-in uninstaller, but I'm assuming that **sudo vmware-uninstall** isn't working for you for some reason.  You should be able to eradicate it by hand doing something like```

sudo -i
rm -rf /etc/vmware /usr/lib/vmware ~/.vmware
cd /usr/bin
rm vmware* vmplayer vmnet* vmrun

```

---

