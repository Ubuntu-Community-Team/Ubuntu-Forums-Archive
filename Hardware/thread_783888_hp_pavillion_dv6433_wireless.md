---
title: "hp pavillion dv6433 wireless"
date: 2008-05-06
forum: Hardware
---

### Post by wilkerlucio on 2008-05-06
Hi,

i installed Ubuntu 8.04 in my laptop and all is working so fine except the wireless...

i searched over the internet and tried many tutorials to enable my wireless but nothing works...

anyone knows how to enable my laptop wireless?

---

### Post by instant on 2008-05-06
What tutorials have you tried this far? What model is the WLAN card? Do you know if there are native drivers for it?

//instant

---

### Post by wilkerlucio on 2008-05-06
Hi, the wireless is one Broadcom.

I tried to install the Vista driver (in HP website there is wireless driver only for vista...) using ndiswrapper and tried using b43-fwcutter too

but doesnt woks :(

---

### Post by Ayuthia on 2008-05-06
Can you post your lspci -nn?  There are various types of Broadcom cards and some work with b43 and a couple don't.  This command will allow us to see your card name and the chipset id so that we can tell which you may use.

Also, Vista drivers do not work with NDISwrapper yet.  Do you recall which guide you used for this?

Here is one that might help.  It does provide some drivers that might work also: [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)

---

