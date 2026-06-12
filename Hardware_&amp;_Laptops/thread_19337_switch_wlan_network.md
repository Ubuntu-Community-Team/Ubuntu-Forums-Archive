---
title: "switch wlan network"
date: 2005-03-11
forum: Hardware &amp; Laptops
---

### Post by aracataca on 2005-03-11
hi to everybody,

this problem is quite a tough one for me since i'm after it for some time now and still didn't get closer to any success.

i'm an absolute linux-newby, and installing ubuntu was really smooth, regarding that my wlan-connection (at home) was automatically detected and used for downloading the necessary packages.

as i took my laptop (ibm T42) to the university, i'm facing the problem that the wlan-network is detected, for its intensity is shown (wireless link monitor applet), but i can do what i want, i can't get any connection.

there is quite a similar threat here in this forum, but the command

#>iwlist <wlan0 or whatever> scan

will only result in

ath0    Failed to read scan data : Resource temporarily unavailable


in the network-setup-gui, the ath0-device is active, and he is also accepting the command     iwconfig ath0
since i spent years on google to find any help, i am posting this already desperately, i can say.        [-o< 

thanks.

:::aracataca:::

---

### Post by ming0 on 2005-03-11
[QUOTE=aracataca]as i took my laptop (ibm T42) to the university, i'm facing the problem that the wlan-network is detected, for its intensity is shown (wireless link monitor applet), but i can do what i want, i can't get any connection.[/QUOTE]

Okay, have you connected to the university network with this computer before (like with windows)? Have you connected to the network on any other wireless computer (that you set up)?

They might have MAC filtering set up, so that you just need to register your wireless adapter, or maybe some other form of authentication that needs to be set up. That's the first thing to check.

After that, maybe you just need to re-dhcp for an address (or maybe you need to specify an address that the school gives you).

So contact the computer services desk, and find out what it takes to get onto the campus network (or maybe you have already done this)?

---

### Post by aracataca on 2005-03-11
ME CANT BELIEVE IT!

the university uses an authentification-system; only one site is available, login there and init!

thanks for answering!

and i go, circling in...

... rings around the wwworld... !

---

