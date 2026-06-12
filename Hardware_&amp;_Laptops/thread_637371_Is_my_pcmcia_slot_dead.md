---
title: "Is my pcmcia slot dead?"
date: 2007-12-10
forum: Hardware &amp; Laptops
---

### Post by ireneybean on 2007-12-10
I just posted this over in Absolute Beginners and was directed over here, so I'm hoping somebody will have some more input:

I suspect that my pcmcia slot may be kaput. I have never really used it before so I don't know if this issue just started when I moved to ubuntu.

I am plugging a Netgear wg511T network adapter card into the slot. the /var/log/messages shows no output at all when I plug in the card. The lights on the card do not come on. there is no ath0 device anywhere on the system that I can find.

however,
find /sys/class/pcmcia_socket/

does give me
/sys/class/pcmcia_socket/
/sys/class/pcmcia_socket/pcmcia_socket0
/sys/class/pcmcia_socket/pcmcia_socket0/available_ resources_mem
/sys/class/pcmcia_socket/pcmcia_socket0/available_ resources_io
/sys/class/pcmcia_socket/pcmcia_socket0/cis
/sys/class/pcmcia_socket/pcmcia_socket0/available_ resources_setup_done
/sys/class/pcmcia_socket/pcmcia_socket0/card_irq_m ask
/sys/class/pcmcia_socket/pcmcia_socket0/card_eject
/sys/class/pcmcia_socket/pcmcia_socket0/card_pm_st ate
/sys/class/pcmcia_socket/pcmcia_socket0/card_inser t
/sys/class/pcmcia_socket/pcmcia_socket0/card_vcc
/sys/class/pcmcia_socket/pcmcia_socket0/card_vpp
/sys/class/pcmcia_socket/pcmcia_socket0/card_volta ge
/sys/class/pcmcia_socket/pcmcia_socket0/card_type
/sys/class/pcmcia_socket/pcmcia_socket0/power
/sys/class/pcmcia_socket/pcmcia_socket0/power/wake up
/sys/class/pcmcia_socket/pcmcia_socket0/power/stat e
/sys/class/pcmcia_socket/pcmcia_socket0/device
/sys/class/pcmcia_socket/pcmcia_socket0/subsystem
/sys/class/pcmcia_socket/pcmcia_socket0/uevent

and
sudo ./etc/init.d/pcmciautils

gives me:

* PCMCIA bridge driver already present in kernel

I did see this:[http://ubuntuforums.org/showthread.php?t=570061](http://ubuntuforums.org/showthread.php?t=570061)
and worked through the info there as well as I can and am not coming up with anything much more. I did install pcimcia-cs. I tried the cardctl insert and the pccardctl insert (neither gave an error, but subsequently running pccardctl status said "no card found" I also tried rebooting my laptop with the card installed, no change.

not looking good for my pcmcia slot eh? all the other threads I have read on similiar issues have at least had some level of recognition of a card being inserted ... in my case there is just no evidence of any card existing at all.
...
I'm thinking that it could be the card too (I do not have another one to test with) but it is new so I'm hoping it's not that...

can anyone help me figure out what is going on?

---

### Post by ireneybean on 2007-12-11
bump

---

### Post by ilrudie on 2007-12-12
I am not an expert on this and have not tried it personally however I do hope to purchase a new laptop for Gutsy so I have been reading up on the subject. The issue may be that the kernel already has pcmcia compiled in and this must be absent for pcmcia-cs to function. 
> 8.3. Third-party modules
"Third-party modules" is the term I use for kernel modules with source code outside the kernel source tree. An example is "pcmcia-cs", which many laptop users need for the latest PCMCIA support. 

To use pcmcia-cs, apt-get the "pcmcia-source" package; the source tarball should be in /usr/src. As a normal user, expand the source tarball to /usr/src/modules/pcmcia-cs. If you don't already have a modules directory one will be created. 

When you configure your kernel, disable PCMCIA support. (If you have PCMCIA support enabled, pcmcia-cs won't build drivers.) If you want to use wireless LAN, enable it under "Network device support" but don't select any devices.

The entire kernel building tutorial can be found in the link below.  It's for Debian but since Ubuntu is derived from Debian you can likely use most of not all of the information in it.  It's also fairly old but IMHO it's worth reading before you try compiling a custom kernel since it will help you understand what you are in for.
[http://newbiedoc.sourceforge.net/system/kernel-pkg.html]("http://newbiedoc.sourceforge.net/system/kernel-pkg.html")

 I hope this helps and goodluck.

---

### Post by ireneybean on 2007-12-12
wow.  Recompiling the kernel is probably more than I want to take on right now.  I did manage to get my onboard wireless card working well enough that I don't need to rely on the PCMICIA one.  (In fact, I just returned it about an hour ago).

I'd like to get my pcmicia slot working if it is possible though so it's entirely possible that I may undertake this project in the future.  Thanks for the advice.

Every time that I used any of the pcmicia-cs commands I got basically a deprecation message pointing me at the pcmciautils package.  So everything that I tried I tried with both modules.  (Forgive me if I'm using the 'package' and 'modules' terms in the wrong context).

For instance I tried both "cardctl insert" and "pccardctl insert".  So even if pcmcia-cs is not working correctly because of the built in kernel support, then wouldn't the pcmciautils commands work?  (Or maybe pcmciautils <i>is</i> the kernel support that you are talking about? ([ugh, I'm such a n00b! :lolflag:)

Thanks though!

---

### Post by ilrudie on 2007-12-13
My guess would be that the standard pcmcia support that is built into the kernel does not support all pcmcia hardware that is available (and apparently your hardware is not supported). If that is not the case I don't know what the pcmcia-cs patch was created for.
 
[http://pcmcia-cs.sourceforge.net/](http://pcmcia-cs.sourceforge.net/)

---

### Post by turtles on 2007-12-13
Pcmcia-cs is long outdated. 
Although I am more experienced in Gentoo than Ubuntu I have admined a Ubuntu machine being a sony laptop that got traveled around with the pcmcia card inserted. And now the slot is dead.

I can tell you in my experience if you insert a card and if you open a terminal as root (or sudo as ubuntu does it) and ```
lspci -vvv
``` does not show your card's chipset but a card bus bridge then [list=A][*]Your card is broken try another. [*] Or your card slot is broken.[/list]

If you can borrow a pcmcia card try this script and post the output here:

```
#/bin/bash
echo "list everything we know about this card"
pccardctl status 
pccardctl ls
pccardctl info
pccardctl ident
echo "dmesg:"
dmesg | grep pci
dmesg | grep pcmcia && dmesg | grep Yenta 
echo "memory from /etc/pcmcia/config.opts"
less /etc/pcmcia/config.opts | grep memory
echo "lspci":
lspci | grep CardBus    
lspci -v | grep subordinate

```


Cheers

---

### Post by ireneybean on 2007-12-14
Thank you.   that's correct lshw does show the cardbus bridge and not the card itself.  So... when I get a hold of a known working card I will try what you have posted.  I appreciate it!

---

