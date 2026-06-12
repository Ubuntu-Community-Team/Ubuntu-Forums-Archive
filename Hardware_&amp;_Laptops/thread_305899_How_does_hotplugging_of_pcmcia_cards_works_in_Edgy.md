---
title: "How does hotplugging of pcmcia cards works in Edgy 6.10?"
date: 2006-11-24
forum: Hardware &amp; Laptops
---

### Post by ronaldv on 2006-11-24
Hi,

Ubuntu 6.10 Edgy.

I have an rt2400-wireless card (pcmcia). Driver etc, works fine.

Last problem I have with it is that on my Mandrake system I had before, I could unplug&re-plug the card without problem. The hotplug system would call ifdown&ifup at the right moment. Now with my Ubuntu-edgy install the card comes up OK after boot but fails after I unplug& replug. How come?

I believe that Ubuntu 6.06 still used the hotplug-package to manage this but 6.10 comes without this package?

How does Edgy handle hotplugging of pcmcia (wireless) cards?
Where can I find the config-files for this system?
Where can I find the docs for this?
I really did a very good search for this but found nothing.

Cheers, Ronald

---

### Post by spd106 on 2006-11-24
As far as I know Dapper and Edgy both use Udev for all devices as a replacement for dev-fs and hotplug. Have a look around the web there's lots of information.

/etc/udev is where most of the config files for udev are kept.

Look in /etc/network for the ifupdown scripts and interfaces files.

---

