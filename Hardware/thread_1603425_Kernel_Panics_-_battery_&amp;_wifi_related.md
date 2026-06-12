---
title: "Kernel Panics - battery &amp; wifi related"
date: 2010-10-22
forum: Hardware
---

### Post by pea-brane on 2010-10-22
Hi all,

I have been running my ancient HP Omnibook 6000 on Xubuntu for quite a few years. This month I upgraded xubuntu 10.04 to 10.10 and have encountered some problems with kernel panics (frozen screen, keyboard and cursor; caps lock and num lock flashing).

The problem seems to be connected to the wifi card and running on battery. On mains, I don't see any panics at all. If I boot on battery, the panic happens when the wifi network is attempting to connect after log-in. Strangely, if I boot on battery without the wifi card and hot plug it some time after log-in, the system runs OK. If I boot on mains, complete log-in and network connect and then disconnect the mains, I get the panic. If I boot and log-in on battery with the wifi modem router switched off, there is no kernel panic.

If it makes any odds, the battery is a recent replacement and has plenty of grunt.

I can't see anything in syslog that tells me what the panic was.

I have Googled this to the best of my ability. Acpi seems a possible cause (although this was no problem in earlier xubuntu releases). Updating /etc/default/grub with noacpi acpi=off stopped the panics but has caused other problems - the battery indicator in the top toolbar vanishes and adding one is useless - it only ever reads 50%% (and why 2 % signs?) and also the laptop will not power off on shutdown - although it does with acpi enabled. I have tried every combination of apm commands I can find including updating S90halt to comment out some lines, adding various combinations of apm commands in /etc/modules and /etc/default/grub according to various threads but the power off problem will not go away.

I would prefer to reinstate acpi as this worked before and I did not have battery indicator or poweroff probs. Chasing the power off problem is treating the effects of a bad fix and not the problem itself.

The wifi card, according to lspci, is an RT61.

Can anyone help me with this please?

---

