---
title: "No wireless after waking from suspension"
date: 2009-11-15
forum: Hardware
---

### Post by sparklingspecks on 2009-11-15
Hi, since suspend-to-RAM under Karmic is now working rather reliably on my (Medion) MD95400, the old bug (I've even had it under Windows XP, which came pre-installed) that wi-fi¹ won't work afterwards bites me again.
Under Jaunty, I used to be able to run
> [FONT="Courier New"]> sudo modprobe acerhk force_series=95400 autowlan=1
> echo 1 | sudo tee > /proc/driver/acerhk/wirelessled[/FONT]
Now, acerhk doesn't build² anymore on Karmic, so I need a replacement... Does anyone know anything I could do?


---
¹ The card is this (output of lspci --nn):
> [FONT="Courier New"]02:05.0 Ethernet controller [0200]: Broadcom Corporation BCM4401 100Base-T [14e4:4401] (rev 01)
02:06.0 Network controller [0280]: Intel Corporation PRO/Wireless 2200BG [Calexico2] Network Connection [8086:4220] (rev 05)[/FONT]


² I know, there is [456123]("https://bugs.launchpad.net/ubuntu/+source/acerhk/+bug/456123"), where people seemed to have gotten it working on Fujitsus. I somehow can't build it (that said, I am not the most technical person there is and if I can't build straightforwardly with ./configure, make, make install I generally don't know enough to still go on).
Fox states that you could try with acer-wmi, but my notebook is [apparently not supported]("http://code.google.com/p/aceracpi/wiki/SupportedHardware").

---

