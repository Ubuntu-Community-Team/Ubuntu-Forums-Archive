---
title: "Help with Hardware Management (Ubuntu 8.10)"
date: 2008-11-20
forum: General Help
---

### Post by tslawinski on 2008-11-20
I've installed Ubuntu 8.10 and love it. I got rid of my windows partitions finally. It's been a bit of an adjustment though. I messed up a previous installation by trying to manually install a driver for the modem on my laptop. I ended up killing the sound on my machine. I ended up wiping the machine and doing a clean re-install. I can live without the modem. The benefits of Ubuntu far outweigh the use of that device. Nevertheless, I was wondering about a device manager utility.

I've done a bit of a search regarding a hardware manager. I'm assuming this release does not have one. ie. I don't see one under system -> preferences.

Is there a reason for this. I would like to install one using package manager. Is there one recommended... or will one be forthcoming in a future update?

Sincerely,

Ted

---

### Post by Yellow Pasque on 2008-11-20
You can install the gnome-device-manager package, but to be honest, it's not very useful for actually configuring hardware, though it does provide a lot of good information.
```
sudo apt-get install gnome-device-manager
```

---

### Post by tslawinski on 2008-11-20
Ok, thanks. I was thinking about doing that. It would be helpful just to identify how devices are configured and their associated drivers in trying to get things working. I'm a little leery now of manually installing drivers because of what happened last time. I was very impressed with the initial Ubuntu 8.10 install. Virtually everything set up seamlessly on my Acer laptop machine with the exception of the modem. Like I said previously, my modem is not a mission critical device for me. I recognise that in our windows centric world, driver issues can be a problem. Hopefully this will get better with time as people see the benefits of alternative OS's such as Ubuntu.

Thanks,

Ted

---

### Post by Yellow Pasque on 2008-11-20
If you want to identify what drivers are in use in Linux, nothing beats the command line. Between lspci, lshw, and dmidecode, you'll have way too much info on your hardware.
```
sudo lshw
sudo lspci -vv
sudo dmidecode
```

---

