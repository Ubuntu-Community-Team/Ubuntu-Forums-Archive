---
title: "Install PCI wf-2113 wireless card"
date: 2013-04-13
forum: Hardware
---

### Post by UltimateCat on 2013-04-13
:KSHi:

I just purchased a Netis wf 2113 wireless PCI card for my Desktop.
I made sure to take a picture of my MSI motherboard to show the Tech what I have.

[http://www.netis-systems.com/en/products/Wired-Adapter/95.html](http://www.netis-systems.com/en/products/Wired-Adapter/95.html)

The tech took his tower apart and showed me how to install the card but I have a few questions.

I know I need to unplug the power cord to the tower--

Do I need to unplug all of the other cords's (mouse, keyboard and monitor) to the tower?

Should I insert the card first into the slot and than attatch the metal arm of the card to the removeable metal strip ? 
Than attach the antenna before or after I close the case?

---

### Post by UltimateCat on 2013-04-18
I successfully installed the new card! LOL!;)

I installed the driver for Win's XP and the wireless card works fine.

But I don't understand why Debian doesn't show me the wireless connection.
I installed the firmware and the wireless tools-

```
firmware-realtek-0.28+squeeze1_all.deb
wireless-tools_30~preq-d_amd64.deb

```

What can I do to get the wireless working?

---

### Post by UltimateCat on 2013-04-19
According to the Debian Wiki I would need at least kernel 2.3.38 for the new PCI card to be supported.

The documentation to upgrade to Wheezy is difficult so I think I'll be looking for another distribution.
But before I do go looking I have to at least try--

---

### Post by UltimateCat on 2013-04-22
Does anyone know how to install a newer version of the kernel and the headers + all of the details?

And do the headers and the additional pkgs (dependencies in Synaptic) have to be installed first before thel backport .deb pkg first?

I'm really not intrested in loosing the current OS I have.

---

### Post by UltimateCat on 2013-05-02
Installed the new PCI Wireless card with help.

After the first boot Debian saw my new wireless card but no wireless connection.
After 6-8 days of trying to install wireless-tools and getting errors I could not get the wireless to work regardless.

Couldn't upgrade becauase I couldn't get a internet connection on that Desktop to upgrade-

Had to throw the towel in on this project--

Looking at other distributions to install--

---

### Post by UltimateCat on 2013-05-05
Brand new distribution see's my new card!

I'm running Black Opal 64bit and wireless works great!

---

