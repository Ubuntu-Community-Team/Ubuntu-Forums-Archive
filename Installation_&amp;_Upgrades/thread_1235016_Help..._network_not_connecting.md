---
title: "Help... network not connecting"
date: 2009-08-08
forum: Installation &amp; Upgrades
---

### Post by AmerNewbieInDE on 2009-08-08
help, i just installed Ubuntu 9.04, i have a intel wireless 5100agn, out of the box i see te correct card, correct network ssid and security. I put in the network key but it does not connect... any ideas??? Yes, i reentered the key a number of times...but still no go.

---

### Post by gabry79Italy on 2009-08-09
have you tried to put in your key before to turn on the pc?

---

### Post by P4man on 2009-08-09
What kind of security are you using ? 
If possible, try turning it off on your wifi router and see if everything works then.

---

### Post by seven7seven on 2009-08-12
Hi,

Here's what you should do.

1. Download this: [http://intellinuxwireless.org/iwlwifi/downloads/iwlwifi-5000-ucode-8.24.2.12.tgz](http://intellinuxwireless.org/iwlwifi/downloads/iwlwifi-5000-ucode-8.24.2.12.tgz) and untar it (tar -zxvf iwlwifi-5000-ucode-8.24.2.12.tgz)

2. Copy iwlwifi-5000-2.ucode to /usr/lib/firmware (you might have to create the folder yourself)

3. Reboot

It worked for me with a WiFi 5100AGN. :)

---

