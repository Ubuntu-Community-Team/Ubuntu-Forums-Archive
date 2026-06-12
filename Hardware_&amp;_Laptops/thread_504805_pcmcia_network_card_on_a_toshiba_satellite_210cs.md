---
title: "pcmcia network card on a toshiba satellite 210cs"
date: 2007-07-19
forum: Hardware &amp; Laptops
---

### Post by chicoperico on 2007-07-19
hello all,

this is my first posting on an ubuntu forum -  i changed to ubuntu from suse linux about half a year ago and have done four complete installs by now.

i am busy writing a lamp based project for acid-base analysis data, this is meant to be run on a server accessible from the internet some day.

recently i managed to install an ubuntu 7.06 on an old toshiba satellite 210cs (which i hope to be able to use as the server for my project), without a working floppy drive, and the machine can't boot from the cdrom. so if anybody needs help with this - feel free to ask, it was many hours of work. the essential step was simple (when i had found it ...): tell the initramfs prompt to load the ide module: modprobe ide-generic.

my problem now is, that i can't get the system to see my pcmcia network card, it is a d-link gigaexpress dge-660td.

i loaded the modules pcmcia, pcmcia_core, yenta_socket, rsrc_nonstatic and i82365.

when restarting the network i still get:
eth0: ERROR while getting interface flags: No such device

is this network card simply incompatible with such an old machine?


regards,
Rainer

---

### Post by fredj on 2007-07-20
You should check what sort of pcmcia slot you have on your old notebook. Is it a 32 bit slot or the earlier
16 bit type. The later type is sometimes called cardbus.

---

### Post by chicoperico on 2007-07-21
thank you for your answer!

looking at <http://ferdyx.org/~ferdy/laptops/ri-linux/ri-linux_howto_es.html> via tuxmobil.org, it seems to be the cardbus type.

what is the consequence, if it is?

going to sleep now, i shall be looking at this again tomorrow evening.

bye for now!
Rainer

---

