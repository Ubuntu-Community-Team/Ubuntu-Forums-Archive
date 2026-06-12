---
title: "Switch driver for prism wlan"
date: 2007-01-14
forum: Hardware &amp; Laptops
---

### Post by graaah on 2007-01-14
I've been trying to get a old ThinkPad T30 to work with WPA2 authentification for wlans, but with no success.

The card is a PCI card with the Prism 2.5 chipset. It works fine for WEP or no auth, but there is no option to use WPA.

The machine is running Ubuntu 6.06, and originally the orinoco-driver is being used. Some research showed that the hostap-driver supports WPA, so I installed the package for that, along with some tools for it to flash the firmware etc.

But I can't get the machine to use hostap instead of orinoco. I tried blacklisting orinoco in modprobe config, but the result of that was that the machine wouldn't boot. I tried recovery-bootup and there I can read that hostap now is controlling the card, but then I get a few more lines of text before the boot halts again. So I had to boot from a live-cd and remove the blacklisting to get the machine working.

Some more research showed that the install of hostap added a few lines in /etc/hotplug/blacklist.d/hostap-utils and /etc/discover.d/hostap-utils that is supposed to stop the orinoco driver from loading. Apparently this doesn't work.

Any ideas on what to do?

---

### Post by discord on 2007-01-16
if not installed install the pcmcia-cs package. Then try ~$ sudo carctl ident in the terminal. Once you have the manf id you will need to add it to a config file for the hostap driver. It's been awhile since i did that but it worked before...

---

### Post by graaah on 2007-01-17
But it's not a PCMCIA card, it's PCI.

---

