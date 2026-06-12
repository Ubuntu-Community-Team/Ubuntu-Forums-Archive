---
title: "xubuntu and dial-up"
date: 2008-09-16
forum: General Help
---

### Post by clevelands on 2008-09-16
I've xubuntu on an old HP (pII,124M) and a serial modem. Need a dialer application. I have pppdialer.gz  sitting on desktop. Unable to get into Consol to install the CL way. More on this later.
Any prefered apps for Xubuntu??
Cleveland

---

### Post by rraj.be on 2008-09-16
> **clevelands said:**
> I've xubuntu on an old HP (pII,124M) and a serial modem. Need a dialer application. I have pppdialer.gz  sitting on desktop. Unable to get into Consol to install the CL way. More on this later.
Any prefered apps for Xubuntu??
Cleveland

Connect your modem and Try this in terminal

```
sudo wvdialconf
```

then edit the file /etc/wvdial.conf for specifying your user name and password of the internet account

---

