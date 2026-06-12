---
title: "U2F Security Keys Not Detected After Ubgrade to 23.04"
date: 2023-08-09
forum: Hardware
---

### Post by chiashurb on 2023-08-09
I recently upgraded from Ubuntu 22.10 Kinetic Kudu to Ubuntu 23.04 Lunar Lobster.  Since the upgrade, neither of my U2F hardware tokens are working.  They don't show up on `lsusb` or `yklist`, they don't register in the browser... it's as if they're not there.  They are a Feitian ePass and a Yubikey 5 nano, both of which work fine on other machines and on live images of other linux distros on this machine.  

I'm at a complete loss for how to approach this and would appreciate any help.

---

### Post by #&amp;thj^% on 2023-08-09
back in 2021 I had the same my fix was:[https://github.com/dani-garcia/vaultwarden/discussions/2147](https://github.com/dani-garcia/vaultwarden/discussions/2147)
Hope that helps, "yubikey"

---

### Post by chiashurb on 2023-08-09
Looks like your issue had to do with Vaultwarden not having the keys properly registered to your account.  My issue has to do with the OS not recognizing that the hardware is even there.

---

