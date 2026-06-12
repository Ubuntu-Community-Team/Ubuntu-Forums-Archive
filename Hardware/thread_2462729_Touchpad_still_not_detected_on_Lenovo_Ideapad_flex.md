---
title: "Touchpad still not detected on Lenovo Ideapad flex 5 14are05"
date: 2021-05-26
forum: Hardware
---

### Post by 0x54 on 2021-05-26
The touchpad on my Laptop has never worked, however the issue has persisted throughout several kernel updates, now 5.11.
According to the spec sheet, the touchpad is supposed to be a "Buttonless Mylar® touchpad" but in the error messages it is called MSFT0001:00.
The note app Xournalpp can detect it although the rest of the system can't and calles it "MSFT0001:00 04F3:3140"

Many sources claim the issue has been fixed, however since it does not work in ubuntu, manjaro, fedora and openSUSE (live boots), I do not really know what to do here. 
Since it didn't work in the live boots I think it should not be any false configuration on my part.

It is not visible in libinput, xinput, lshw, lsusb and lspci.
The touchpad gets claimed by the i2c_hid diver and I can't seem to be able to bind it elsewhere.

Has anyone got any idea why this is happening?

---

