---
title: "x64 Wireless driver for server"
date: 2008-10-01
forum: General Help
---

### Post by Gannon8 on 2008-10-01
Hi. I have an x64 version of Ubuntu Server installed to a computer with a wireless card. Unfortunately, Ubuntu server does not come with a driver for it, but Ubuntu Desktop does.

I managed to install ndiswrapper via a x64 Desktop CD, but my card's manufacturer does not provide x64 bit drivers for windows XP. Can anyone help me get the driver?

I have a USB drive I can use. Ubuntu Desktop says that I have an Atheros card from the restricted drivers menu. I have a D-Link WDA-1320, in case you need to know.

Thanks :popcorn:

---

### Post by Gannon8 on 2008-10-01
I tried looking on the cd. Would the package "drdsl_1.2.0-1_amd64.deb" happen to be it?

---

### Post by Yellow Pasque on 2008-10-01
No, drdsl looks to be something totally different. What kind of Atheros controller does it use?
```
sudo lshw -C network
```

---

### Post by Gannon8 on 2008-10-02
AR2143

Cannot really cut and paste since I am doing this on my laptop, so let me know if there is any other info you need.

---

### Post by Gannon8 on 2008-10-02
Hey I really need this driver working. Any and all help appreciated.

Would this be it? avm-fritz-firmware-2.6.24-19_3.11+2.6.24.13-19.44_amd64.deb

---

### Post by Gannon8 on 2008-10-02
Ok. It is madwifi-tools. Only problem is that it has a chain of dependencies and I cannot download them all...

---

### Post by Yellow Pasque on 2008-10-02
Edit: nvm

---

### Post by Gannon8 on 2008-10-02
Too late... I can't work on it now...

---

### Post by Gannon8 on 2008-10-09
Ok, I know I am double posting a lot, but this one is to bump it up.
Anyway, I will have my computer back by tomorrow( 10/10 ) evening. If anyone will suggest something, I will try it out tomorrow. I am thinking about trying to cross compile the madwifi driver.

---

