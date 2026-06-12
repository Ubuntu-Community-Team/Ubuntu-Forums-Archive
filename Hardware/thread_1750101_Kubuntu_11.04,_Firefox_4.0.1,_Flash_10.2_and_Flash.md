---
title: "Kubuntu 11.04, Firefox 4.0.1, Flash 10.2 and Flash Charts"
date: 2011-05-05
forum: Hardware
---

### Post by thomi_ch on 2011-05-05
Hey all

Does anybody also have this Problem, see here:
Firefox 4.0.1 and Flash Chart
[http://dl.dropbox.com/u/5636258/flash-chart-ff401.ogv](http://dl.dropbox.com/u/5636258/flash-chart-ff401.ogv)

Chrome 11.0.696.57 and Flash Chart
[http://dl.dropbox.com/u/5636258/flash-chart-chrome.ogv](http://dl.dropbox.com/u/5636258/flash-chart-chrome.ogv)

My System information:
```
lsb_release -a
LSB Version:    core-2.0-amd64:core-2.0-noarch:core-3.0-amd64:core-3.0-noarch:core-3.1-amd64:core-3.1-noarch:core-3.2-amd64:core-3.2-noarch:core-4.0-amd64:core-4.0-noarch:cxx-3.0-amd64:cxx-3.0-noarch:cxx-3.1-amd64:cxx-3.1-noarch:cxx-3.2-amd64:cxx-3.2-noarch:cxx-4.0-amd64:cxx-4.0-noarch:desktop-3.1-amd64:desktop-3.1-noarch:desktop-3.2-amd64:desktop-3.2-noarch:desktop-4.0-amd64:desktop-4.0-noarch:graphics-2.0-amd64:graphics-2.0-noarch:graphics-3.0-amd64:graphics-3.0-noarch:graphics-3.1-amd64:graphics-3.1-noarch:graphics-3.2-amd64:graphics-3.2-noarch:graphics-4.0-amd64:graphics-4.0-noarch:printing-3.2-amd64:printing-3.2-noarch:printing-4.0-amd64:printing-4.0-noarch:qt4-3.1-amd64:qt4-3.1-noarch
Distributor ID: Ubuntu
Description:    Ubuntu 11.04
Release:        11.04
Codename:       natty


lspci | grep -i nvidia
01:00.0 VGA compatible controller: nVidia Corporation GT216 [GeForce GT 240M] (rev a2)


xorg.conf
[http://paste.ubuntu.com/603670/](http://paste.ubuntu.com/603670/)


uname -a
Linux poseidon 2.6.38-9-generic #43-Ubuntu SMP Thu Apr 28 15:23:06 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux
```


If more information are needed, just inform me...

Thanks for response
thomi

---

### Post by lovinglinux on 2011-05-05
Get my [Flash-Aid]("https://addons.mozilla.org/en-US/firefox/addon/161939/") extension for Firefox. It will install the latest beta version of flash 64bit and apply some tweaks that will probably solve your problem.

---

### Post by PapaGary on 2011-05-05
> **lovinglinux said:**
> Get my [Flash-Aid]("https://addons.mozilla.org/en-US/firefox/addon/161939/") extension for Firefox. It will install the latest beta version of flash 64bit and apply some tweaks that will probably solve your problem.
I'm not the OP but...

Thank you! Flash-Aid worked like a charm for me.

Gawd, I love this place.:D

---

### Post by lovinglinux on 2011-05-05
> **PapaGary said:**
> I'm not the OP but...

Thank you! Flash-Aid worked like a charm for me.

Gawd, I love this place.:D

You are welcome.

---

### Post by Jontom on 2011-05-19
Hey thanks, solved my issues as well, although I could have just installed the beta myself, the automation is nice, now I can play word twist properly again :)

Donated btw.

Jontom

---

### Post by lovinglinux on 2011-05-19
> **Jontom said:**
> Hey thanks, solved my issues as well, although I could have just installed the beta myself, the automation is nice, now I can play word twist properly again :)

Donated btw.

Jontom

Thank you very much. In case you have version 2.0.8, version 2.1.1 released yesterday has a new wizard and new quick installation methods.

---

