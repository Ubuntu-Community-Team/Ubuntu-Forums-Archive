---
title: "scanner is missing in hplip-3.21.2"
date: 2021-03-16
forum: Hardware
---

### Post by wht-crl on 2021-03-16
I installed  hplip-3.21.2 on ubuntu 20.4 and now, I discovered that can't run scanner from hp-manager as the driver plugin installation is required.

[ATTACH=CONFIG]288143[/ATTACH]

but when I choose to install from a hp server, 

[ATTACH=CONFIG]288142[/ATTACH]
the waiting time is so long that I have to force quit.

[ATTACH=CONFIG]288144[/ATTACH]

Why can the hp-manager not connect to the server and find the driver plugin ?

Should I do it manually and where to find this plugin?

should I send the hplip-3.21.2 log installation file?

---

### Post by brian_p on 2021-03-17
> Should I do it manually and where to find this plugin?

Missing information:

[LIST]
[*]Device model.
[*]
[/LIST]
[LIST]
[*]USB or network?
[*]
[/LIST]
[https://www.openprinting.org/download/printdriver/auxfiles/HP/plugins/](https://www.openprinting.org/download/printdriver/auxfiles/HP/plugins/)

Install with ```
sudo sh PLUGIN_VERSION.run
```

---

### Post by rsteinmetz70112 on 2021-03-18
You may be able to run it would out the plugin try some of the scanned apps and see if it's recognized.

---

