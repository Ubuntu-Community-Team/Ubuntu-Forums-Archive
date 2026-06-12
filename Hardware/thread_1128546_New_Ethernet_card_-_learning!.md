---
title: "New Ethernet card - learning!"
date: 2009-04-17
forum: Hardware
---

### Post by momist on 2009-04-17
Hi everyone,

I have just installed a new high speed Ethernet card.  There's no brand on the box, but it's labelled as "Plug and Play 10/100 Mbps Fast Ethernet PCI Adapter".  The main chip on board carries the Belkin name.  This replaces a *very* old 3Com EtherLink III PCI device which only supported 10Mbps half duplex.

I simply swapped the new board for the old one.  Now, it didn't work straight off, and after some digging I discovered that the network connection uses Eth0, while the new card has been labelled as Eth1.  Why?  Further digging lead me to use the Network Manager for the first time - and after command line in the terminal discovered the MAC address of the new card, I have managed to set it up as a wired connection dedicated to that board, still on Eth1.  Immediate connection!  Wow, it's fast! :D

So now the questions.
1. Why did the new board take Eth1 instead of Eth0, when it is the only ethernet device in the machine?
2. Having taken Eth1, why did Ubuntu not automatically try to use it for a network connection?
3. Why did I not have to set up the old board using Network Manager, but I did with the new one?

I'm not complaining, I now have a working connection (or you wouldn't be seeing this).  But I'd love to know how it ought to have worked, and why it didn't.  Plug and Play? I don't think so!

---

### Post by kidders on 2009-04-19
Hi there,

> **momist said:**
> 1. Why did the new board take Eth1 instead of Eth0, when it is the only ethernet device in the machine?Ubuntu has no way of knowing you don't intend to plug the old network card back in again, so eth0 is kept free for it. For example ...[LIST]
[*]Rather than taking your old card out, suppose you had plugged both cards in at the same time. You would expect your network configuration to remain unaffected. This is achieved by reserving eth0 for your old card, so there is no way your new card could ever steal it (eg by being detected before the old one).
[*]Suppose you had hot-pluggable or USB network adapters ... say, for example, a couple of phones. Life would get very confusing if your phones' GSM network connections kept being assigned different names, every time you plugged them in. Imagine, for the sake of argument, you have a laptop, and internet access is only available through your Nokia on eth7, which took you half an hour to manually configure. It would be pretty annoying if your configuration fell apart the next time you rebooted, simply because eth6 and eth5 weren't plugged in at the time.
[*]Let's say your machine had 3 network connections, one of which was very heavily firewalled. Suppose eth0 disappears (either because it fried & stopped working, or because you plugged it out). In a way, your question pre-supposes that the default behaviour should be to shuffle eth1 and eth2 down to eth0 and eth1 at the next boot, so that any firewall rules or servers you might have are now bound to the wrong networks.
[/LIST]

> **momist said:**
> 2. Having taken Eth1, why did Ubuntu not automatically try to use it for a network connection?You didn't tell it you wanted it to do that. You see, Ubuntu's only option would be to apply a network configuration intended to work with a completely different card on (possibly) a completely different network, which might not work ... or even be safe.

> **momist said:**
> 3. Why did I not have to set up the old board using Network Manager, but I did with the new one?Ubuntu will do a certain amount of configuration for you at the beginning, based on some reasonable assumptions about how new users want their computers to work. Trying to second-guess you like that six months later is more likely to be annoying than helpful, imo! In networking terms, plug and play takes you as far as automagically loading the appropriate driver for a newly-discovered network card, and making it ready for use on the next available "ethX" slot. At the time, typing **ifconfig -a** would have shown you your new network interface, ready & waiting to be configured. Nine times out of ten, going as far as discarding a pre-existing network configuration & probing the new network connection for DHCP servers & internet access would be a step too far. For all Ubuntu knows, you temporarily disabled eth0 in your BIOS configuration, so that your could run your computer without a network connection for a few hours.

Anyhow, you'll find the configuration setting that's keeping you from re-using eth0 in /etc/udev/rules.d/70-persistent-net.rules. It's basically a list of every network interface you've ever had, and what it should be called, the next time Ubuntu sees it. Alternatively, the directives for how to treat detected network interfaces are in /etc/network/interfaces. Interfaces not listed here are ignored ... basically treated as unconfigured spares. In your situation, If I intended for one network adapter to replace another (rather than work alongside it), I would probably have edited one of these, to get better control of what happened when I booted my box back up with the new card.

I hope that helps.

---

### Post by SnaveDogg on 2009-04-25
> **kidders said:**
> Hi there,

Ubuntu has no way of knowing you don't intend to plug the old network card back in again, so eth0 is kept free for it. For example ...
[LIST]
[*]Rather than taking your old card out, suppose you had plugged both cards in at the same time. You would expect your network configuration to remain unaffected. This is achieved by reserving eth0 for your old card, so there is no way your new card could ever steal it (eg by being detected before the old one).
[*]Suppose you had hot-pluggable or USB network adapters ... say, for example, a couple of phones. Life would get very confusing if your phones' GSM network connections kept being assigned different names, every time you plugged them in. Imagine, for the sake of argument, you have a laptop, and internet access is only available through your Nokia on eth7, which took you half an hour to manually configure. It would be pretty annoying if your configuration fell apart the next time you rebooted, simply because eth6 and eth5 weren't plugged in at the time.
[*]Let's say your machine had 3 network connections, one of which was very heavily firewalled. Suppose eth0 disappears (either because it fried & stopped working, or because you plugged it out). In a way, your question pre-supposes that the default behaviour should be to shuffle eth1 and eth2 down to eth0 and eth1 at the next boot, so that any firewall rules or servers you might have are now bound to the wrong networks.
[/LIST]

You didn't tell it you wanted it to do that. You see, Ubuntu's only option would be to apply a network configuration intended to work with a completely different card on (possibly) a completely different network, which might not work ... or even be safe.

Ubuntu will do a certain amount of configuration for you at the beginning, based on some reasonable assumptions about how new users want their computers to work. Trying to second-guess you like that six months later is more likely to be annoying than helpful, imo! In networking terms, plug and play takes you as far as automagically loading the appropriate driver for a newly-discovered network card, and making it ready for use on the next available "ethX" slot. At the time, typing **ifconfig -a** would have shown you your new network interface, ready & waiting to be configured. Nine times out of ten, going as far as discarding a pre-existing network configuration & probing the new network connection for DHCP servers & internet access would be a step too far. For all Ubuntu knows, you temporarily disabled eth0 in your BIOS configuration, so that your could run your computer without a network connection for a few hours.

Anyhow, you'll find the configuration setting that's keeping you from re-using eth0 in /etc/udev/rules.d/70-persistent-net.rules. It's basically a list of every network interface you've ever had, and what it should be called, the next time Ubuntu sees it. Alternatively, the directives for how to treat detected network interfaces are in /etc/network/interfaces. Interfaces not listed here are ignored ... basically treated as unconfigured spares. In your situation, If I intended for one network adapter to replace another (rather than work alongside it), I would probably have edited one of these, to get better control of what happened when I booted my box back up with the new card.

I hope that helps.

sounds like you are very knowledgeable as to how to set one of these up. I am having massive problems getting my internet up and running. Could you help me out??

I'm having lots of trouble finding anyone to help in any amount of detail. Many thanks ahead of time..

---

