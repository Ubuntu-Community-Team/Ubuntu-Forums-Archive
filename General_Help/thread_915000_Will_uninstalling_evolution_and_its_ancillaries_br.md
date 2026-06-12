---
title: "Will uninstalling evolution and its ancillaries break Ubuntu?"
date: 2008-09-09
forum: General Help
---

### Post by brjoon1021 on 2008-09-09
Hi,

I want Thunderbird instead. There is no real harm in leaving evolution, but I want to remove it if there is no harm to other Gnome based applications or the OS itself by removing it.

Thanks,

B.

---

### Post by Sycron on 2008-09-09
When you uninstall evoulution [COLOR="Red"]BE SURE to NOT remove[/COLOR] *evolution-data-server-common* too.

---

### Post by Thingymebob on 2008-09-09
I think if you attempt to remove Evolution then you will also be forced to remove gnome-desktop-environment (depends on evolution) which will break Gnome
[http://packages.ubuntu.com/hardy/gnome-desktop-environment]("http://packages.ubuntu.com/hardy/gnome-desktop-environment")

---

### Post by brjoon1021 on 2008-09-09
Sh*t. I am glad I asked. I think I will leave it alone.

---

### Post by Sycron on 2008-09-10
> **brjoon1021 said:**
> Sh*t. I am glad I asked. I think I will leave it alone.

Yes... This was a lucky one.

---

### Post by L8erG8er on 2008-09-11
I've removed Evolution, I just added gnome-desktop-environment back in afterward.  But it is a risk.

---

### Post by Nepherte on 2008-09-11
I had no problems removing evolution. You will have to keep evolution-data-server-common though or you will loose a lot more too. You can safely remove everything else with apt-get. Note that apt-get will likely remove the virtual package ubuntu-desktop as well. This will not remove every package linked to it but only the virtual package.

---

