---
title: "Installing ATi drivers on a IBM T60 ThinkPad"
date: 2008-09-28
forum: Hardware
---

### Post by johnswb on 2008-09-28
Hello, I've reinstalled 3 times now trying to get my ATi settings to work.  I've looked for a way to go back to the default settings and had no luck.  After doing the installation everything seems to be working until I try and get the ATi control console to work.  I go to [ati.amd.com]("https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-8-9-x86.x86_64.run") and down load the driver and do the following.

```
sudo chmod +x ati-driver-installer-8-9-x86.x86_64.run
```
```
sudo ./ati-driver-installer-8-9-x86.x86_64.run
```

I've noticed after installing the module kernel my display settings are all out of sync.  I was running 7.10 and now I'm trying to upgrade to 8.04.1.

The reason why I'm trying to install the ATi control console is for my dual monitors. 

Please help

---

### Post by binbash on 2008-09-28
What about using Envyng?

---

### Post by johnswb on 2008-09-28
I have not heard about Envyng...

But I just got it to work, I think.  This time I didn't install the module kernel during the ATi driver install and when I rebooted I got a white screen only.  I then did booted to the recovery option and did a fix on X server.  After doing that I continued to the normal boot and reinstalled the drivers again without the "Hardware enabled".  I then rebooted and now it is looking good other then my dual monitors working correctly.  I guess I can give Envyng a try, do you know if I can configure my monitors with it?

---

