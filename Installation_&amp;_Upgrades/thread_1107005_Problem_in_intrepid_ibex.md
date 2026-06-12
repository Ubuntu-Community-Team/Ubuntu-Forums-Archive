---
title: "Problem in intrepid ibex"
date: 2009-03-26
forum: Installation &amp; Upgrades
---

### Post by swampdude on 2009-03-26
Hey, 

Ok so i am sort of new to the Linux world but since i installed hardy heron me and my computer have lived happily ever after. 

My problem is that the nvidia 177 proprietary driver which is recommended to use in intrepid ibex doesn't like my computer and once installed, when i restart a text thing come up instead of the operating system, which make me believe there is some sort of clash between the driver and my graphics card. 

My question is it possible to use the nvidia driver from hardy heron on intrepid ibex? and is it relatively easy to install.

---

### Post by coffeecat on 2009-03-26
> **swampdude said:**
> when i restart a text thing come up instead of the operating system, which make me believe there is some sort of clash between the driver and my graphics card.

More or less. What you're getting is a failure of the xserver (which is the underpinnings of the GUI) and you're being dumped into the command line. I'm not sure of all the details, but I believe this issue is more to do with the nvidia driver being partly incompatible with the later version of xorg (used in 8.10) rather than a driver/card issue. Whatever, there are issues, some big, some small, and it depends on your particular graphics chipset.

First question: which nvidia chipset have you got? Try searching the forum for this - others may have found a fix.

Second: When I go to System > Administration > Hardware Drivers, I'm offered three different versions of the nvidia driver. The latest driver won't work with earlier cards, but I don't know the details. You might want to try one of the other drivers, but first you need to get a GUI. try this:

At the command line, log in and:

```
sudo nano -w /etc/X11/xorg.conf
```You get the xorg config file in a simple text editor. Scroll down to the section "Device" and change the line

```
    Driver    "nvidia"
```to

```
    Driver    "nv"
```Now ctrl-O to save and ctrl-X to exit the text editor. Then:
```
sudo reboot
```and you should get a GUI using the open source 'nv' driver. Which works fine but you won't get hardware acceleration. Now you can try one of the other nvidia drivers.

---

