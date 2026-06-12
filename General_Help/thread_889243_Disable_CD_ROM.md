---
title: "Disable CD ROM"
date: 2008-08-13
forum: General Help
---

### Post by niccholaspage on 2008-08-13
Can anyone tell me how to disable and enable my CD ROM.I want to do this so when I am on the road I will juice more power out of my battery.

---

### Post by Crafty Kisses on 2008-08-13
> **niccholaspage said:**
> Can anyone tell me how to disable and enable my CD ROM.I want to do this so when I am on the road I will juice more power out of my battery.

```
sudo apt-get install sysv-rc-conf
sudo sysv-rc-conf
```

Remove the X for all of the hardware you want disabled.

I also want to see the output of the following:
```
lsmod | grep cd
```

---

### Post by niccholaspage on 2008-08-13
Thanks.The output of lsmod | grep cd is:
```

cdrom                  43808  1 sr_mod
ehci_hcd               42892  0 
uhci_hcd               30224  0 
usbcore               145520  5 ndiswrapper,usbhid,ehci_hcd,uhci_hcd

```

---

### Post by Mister.Vash on 2008-08-14
It is easy to jump pull the CD ROM drive out of the machine and plugging it in when you need it?  Some laptop you can easily pop them in and out

---

