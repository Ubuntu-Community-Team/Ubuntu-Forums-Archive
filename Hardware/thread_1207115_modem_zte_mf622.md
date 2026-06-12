---
title: "modem zte mf622"
date: 2009-07-07
forum: Hardware
---

### Post by Cherpas on 2009-07-07
Hi everyone, i have a problem with my internet connection on Ubuntu 9.04. I'm using a zte mf622 wireless modem which is recognizable also as an usb storage device as a modem, so my problem is that y have to reboot in order to get my device as an effective modem. On the first boot there is no internet connection available, when i reboot i got them.

I've tried using usb_modeswitch but it tells me that there is no device connected, after that i execute lsusb and nothing, i also have a scrypt that tells the modem to change itself to the modem configuration added on the //etc/udev directory, but it doesn't work. I can get connected with a modification to the //etc/ppp/options file, by adding "ipcp-max-failure 30" on the space just before the end of the document. I'm guessing that it might be a problem on the usb management of the laptop (i'm using an HP Pavilion dv1000), i don't know if i have to boot with a command line edition from the GRUB or if i have to compile a new kernel...

Thankfully expecting that you'll find the solution, goodbye.

---

### Post by GeorgeVita on 2009-07-14
Hi **Cherpas**, just some ideas:
usually a laptop when is powered from the AC outlet supplies power to USB port all the time (to charge external peripherals). If this happens at your case, while in mobile use a reboot will power down your modem and power it up again (true h/w reset). If you are using the AC outlet this is possibly different, check it.

I think that the line you have added ("ipcp-max-failure 30") helps because your provider delays to give you IP and DNS numbers.

Basic tests you can do is to check before and after reboot/attach of the modem and review the results:
```
lsusb
```
```
dmesg
```
```
ls /dev/ttyU*
```

Post here any new info to follow up.

Regards,
George

---

