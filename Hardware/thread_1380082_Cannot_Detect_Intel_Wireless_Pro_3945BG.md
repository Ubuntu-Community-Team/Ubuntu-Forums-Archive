---
title: "Cannot Detect Intel Wireless Pro 3945BG"
date: 2010-01-13
forum: Hardware
---

### Post by nomad05 on 2010-01-13
Ok, so as a gift to a friend I picked up a Hasee MJ125 Netbook while I was in China last week.  It's a crappy Chinese brand, but it seems to do the job.

It didn't come with a wireless adapter so I manually installed an Intel Pro 3945BG card.  Despite not being familiar with linux operating systems in general, I picked Ubuntu Netbook Remix for the OS for my friend's preferences.

The problem is that Ubuntu cannot recognize the card or even detect that is there.  It's firmly plugged in correctly, but beyond that I'm stumped.  I've spent considerable time researching the 3945BG's history with linux, and I've noted several unofficial driver projects (ipw3945) which have later been morphed into other broader projects (iwlwifi).

Not knowing much about command lines, my overall apparent conclusion is that the most recent build of Ubuntu that I have (9.10) has drivers integrated.  I've tried using 3rd party network programs (Wicd) to remedy the problem but still cannot be detected.

I'm at a loss.  Ubuntu and Linux in general isn't a world I'm intimately familar with.  If anyone has any advice or suggestions on where to proceed from here, I'd greatly appreciate it.

Thanks,
Chris

---

### Post by labinnsw on 2010-01-20
You will need to have the windows driver for the adapter in question.

From Synaptic, install ndisgtk, ndiswrapper-common and ndiswrapper-utils-* (On Hardy, it is ndiswrapper-utils-1.9)

Navigate the menus to System >> Administration >> Windows Wireless Drivers.

Click "install new driver"

Browse to the location where the driver is located (it will be an .inf file)

Click "Configure Network" and follow the prompts to configure the network settings. When you are done you should be able to detect the device and connect to the network.

---

