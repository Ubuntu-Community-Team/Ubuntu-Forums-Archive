---
title: "Brother printer do not work on xubuntu 20.04 but it does on ubuntu 20.04, ¿why?"
date: 2020-12-31
forum: Hardware
---

### Post by mranon2 on 2020-12-31
hi!

I have a Brother DCP-J152W working fine on _Ubuntu 20.04 LTS _

Brother packages installed:

[INDENT]dcpj152wlpr-3.0.0-1.i386.deb
dcpj152wcupswrapper-3.0.0-1.i386.deb
[/INDENT]

settings:

[INDENT](device URI) ipp://[PRINTER IP]
[/INDENT]
[INDENT](driver )Brother DCP-J152W CUPS 
[/INDENT]

Same config and setup in _xubuntu 20.04 LTS_ with following result:

- "Print Self-Test Page" is working fine BUT "Print Test Page" do NOT
- Any document sent to the printer gives no error but nothing happens...
- with cups driverless is working fine BUT lose advanced settings from brother driver

**what is the problem? **a difference that I see between xubuntu & ubuntu is that in xubuntu I do not have the _libcups2: i386_ package installed nor does it exist in the repositories, I have tried to install it but then it breaks my dependencies

Any help is appreciated.
Thank you very much and sorry for my bad English.

---

### Post by brian_p on 2020-12-31
> - with cups driverless is working fine BUT lose advanced settings from brother driver

What advanced settings are lost? Which ones are very important to you?

---

### Post by mranon2 on 2020-12-31
theese settings

[IMG]https://i.imgur.com/7xUsw1u.png[/IMG]

anyway, I would like to know the reason why it works in ubuntu and not in xubuntu

thanks!!

---

### Post by brian_p on 2020-12-31
> - with cups driverless is working fine...

There you are; you are set up to print. Why not be satisfied and go with this? What do any of the advanced settings have to offer you that you would use on a regular basis? How do they enhance your printing experience?

---

