---
title: "[SOLVED] ATI to Nvidia installation advice"
date: 2008-05-29
forum: Hardware
---

### Post by pfwd.tech on 2008-05-29
Hi I have just bought an XFX 8600GT XXX Edition 256MB DDR3 card to replace my ATI Sapphire X1550 512MB DDR2 card.
What is the process of uninstalling my ATI card and installing my Nvidia card?
I take it there I don't have to do anything drastic like rebuild my system in order to  remove the ATI proprietary driver.

Im using Hardy on an Intel core 2 6400 with 2GB of Ram

---

### Post by overdrank on 2008-05-29
> **pfwd.tech said:**
> Hi I have just bought an XFX 8600GT XXX Edition 256MB DDR3 card to replace my ATI Sapphire X1550 512MB DDR2 card.
What is the process of uninstalling my ATI card and installing my Nvidia card?
I take it there I don't have to do anything drastic like rebuild my system in order to  remove the ATI proprietary driver.

Im using Hardy on an Intel core 2 6400 with 2GB of Ram

Hi and you should uninstall the ATI driver then reboot, install nvidia card and then reconfigure you xorg on boot. Then install the nvidia drivers.

---

### Post by pfwd.tech on 2008-05-29
Hi Overdrank,
Do you know of any guides/walkthroughs that I could use to assist me?

---

### Post by pfwd.tech on 2008-05-30
I managed it. Done a bit of research and got the Nvidia card working.
I wrote a guide on how I removed the ATI drivers and installed Envy drivers for my Nvidia card on my [blog]("http://www.blog.peterfisher.me.uk/linux/uninstalling-ati-installing-nvidia-drivers/").
Thanks for your help

---

