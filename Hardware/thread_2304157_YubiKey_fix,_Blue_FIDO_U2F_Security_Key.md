---
title: "YubiKey fix, Blue FIDO U2F Security Key"
date: 2015-11-24
forum: Hardware
---

### Post by bathynomusBLUE on 2015-11-24
This is the Yubico Key that I am referring to:
[https://www.yubico.com/products/yubikey-hardware/fido-u2f-security-key/](https://www.yubico.com/products/yubikey-hardware/fido-u2f-security-key/)

I use Xubuntu 15.04 and 15.10. This key does not appear to work unless you add a special **.rules** file to /etc/udev/rules.d/ . The **.rules** file from Yubico's GitHub didn't work for me. The text below does.

1. Create the file:
sudo mousepad /etc/udev/rules.d/70-u2f-generic.rules
or
sudo gedit /etc/udev/rules.d/70-u2f-generic.rules

2. Paste code:
```
ACTION!="add|change", GOTO="u2f_end"


KERNEL=="hidraw*", SUBSYSTEM=="hidraw", ATTRS{idVendor}=="*", ATTRS{idProduct}=="*", TAG+="uaccess"


LABEL="u2f_end"
```

3. Save
4. Reboot 


Credit for this source goes to Easy Linux Tips Project.

[IMG]https://images-na.ssl-images-amazon.com/images/I/51D2-XOLkAL._SS300_.jpg[/IMG]

---

### Post by TheFu on 2015-11-25
Be careful using GUI editors with sudo. Much safer using **sudoedit** when editing system files.

The issue is that udev changed when systemd took over. On systemd OS installs, the rules are different from pre-systemd udev rules.

Plus folks need to know that only recent chrome and chromium browsers support U2F. Firefox does not, yet.

---

