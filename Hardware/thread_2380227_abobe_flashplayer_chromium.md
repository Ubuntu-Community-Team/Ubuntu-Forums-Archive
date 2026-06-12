---
title: "abobe flashplayer chromium"
date: 2017-12-14
forum: Hardware
---

### Post by eagleftvp-co on 2017-12-14
hi 
Ihave the latest version of ad/flash/pl Ubuntu 16.04 32bit,but chromium ask to update to the latest version fl/pl..and cant open pages ..How to fix this problem..
Thank you

---

### Post by SeijiSensei on 2017-12-14
```
sudo apt install pepperflashplugin-nonfree
```

---

### Post by ajgreeny on 2017-12-14
What version do you actually have installed?

To tell us you have the "latest version of ad/flash/pl Ubuntu 16.04 32bit" does not really help us much.

How did you install the version you have at present?  Is it a problem on all pages with flash animation or just on some?

---

### Post by Yellow Pasque on 2017-12-14
If you already have pepperflash installed as SeijiSensei suggested, check the version, and if there is a newer version available, get it.
```
sudo update-pepperflashplugin-nonfree --status
sudo update-pepperflashplugin-nonfree --install
```

---

### Post by eagleftvp-co on 2017-12-14
thk you for your  Help...Now it looks ok...

---

