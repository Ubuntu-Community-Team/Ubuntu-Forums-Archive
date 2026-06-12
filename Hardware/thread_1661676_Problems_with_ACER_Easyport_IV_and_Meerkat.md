---
title: "Problems with ACER Easyport IV and Meerkat"
date: 2011-01-07
forum: Hardware
---

### Post by grumrick on 2011-01-07
I have an ACER 8572G dual-booting Windows 7 Pro 64 bits and Ubuntu 10.10 64 bits. Ubuntu worked reasonably well (after a bit of fiddling) until I added an ACER Easyport IV. Win 7 performs perfectly with it, but when running Ubuntu the Ethernet and VGA ports don't work. The sound and USB ports are ok. I updated the BIOS to V1.20 and disabled the firewall, all to no avail. Does anyone have a suggestion?

---

### Post by grumrick on 2011-01-09
The problem definitely lies with Ubuntu 10.10. I installed openSUSE 11.3 64 bits (triple-boot) and the ACER Easyport IV works perfectly with it. Only Meerkat is recalcitrant.

Incidentally, I have found openSUSE to be much faster and responsive than Ubuntu 10.10 64 bits on the Travelmate, but I still like the Ubuntu UI and ease of use. I still want to make Meerkat my main OS, but this problem could push me to use something else.

---

### Post by grumrick on 2011-01-16
After a clean re-install of 10.10, the problem remains. What is the difference between openSUSE 11.3 Gnome and Ubutu 10.10 Gnome?

Should I report this as a bug?

---

### Post by grumrick on 2011-02-03
Bump!

---

### Post by grumrick on 2011-02-20
Bump! Anyone? Help!

---

### Post by h0nIg on 2011-03-11
> **grumrick said:**
> Should I report this as a bug?

yes! same problem here!

---

### Post by ramaza on 2011-03-28
Hi,

any news on this topic?

I also want to buy an Acer Easyport IV and use it with Ubuntu 10.10. Would be very good if Ethernet on Easyport is working. Thew problem seems to be resolvable.

Did someone already file a bugreport?

Perhaps the problem disappears with Ubuntu 11.04. There will be a first beta version in a few days. Is someone willing to test it? I don't have my Travelmate notebook and the Easyport IV yet.

Also interesting would be Ubuntu 10.04. The problem could be related to kernel 2.6.35. OpenSUSE 11.3 uses 2.6.34 for example.

Regards,
Franz

---

### Post by grumrick on 2011-04-02
I haven't reported this as a bug because it would be of such low priority because not many users have this problem and Ubuntu 10.10 has many more urgent problems compared with 10.04, such as with openvnp. I don't know if Easyport works with 10.04 and I won't be reinstalling it to find out. I'm hoping that Ubuntu 11 will fix the problem, whatever it is. There must be a fix, it's just that nobody, so far, has suggested what it might be.

---

### Post by ramaza on 2011-04-06
Does only VGA or also DVI don't work with the Easyport IV?

Please also post after you have tested with Ubuntu 11.04. Should be released in four weeks.

---

### Post by grumrick on 2011-04-11
I have tested Easyport IV with everything except the DMI output and the only connections that don't work are theVGA and Ethernet. I will probably do a clean install of 11.04 in a separate partition, being wary of updating from 10.10. I will post what happens. Meerkat seems to have many problems. I hope Natty is better.

---

### Post by hamst3rl3 on 2011-04-29
Hello,

still no luck on Ubuntu 11.04 at least for the ethernet port of the acer easyport 4. 

Any news here?

@grumrick: if you have OpenSUSE with a working easyport network it would be very kind of you if you could test some things there.

First of all: how many network interfaces do you have on SUSE?

On Ubuntu 11.04 I have three (eth0, eth1, lo). Maybe there is a forth port for the easyport in SUSE?

btw. you can list your network interfaces by using the command "ifconfig -a" on the shell.

Thanks and bye,
Peter

---

### Post by grumrick on 2011-05-04
Sorry, hamst3rl3, but I uninstalled Suse 11.3 to make way for Natty. As you have noted, Easyport IV is the same on 11.04 as it is on 10.10: no ethernet or VGA. So no resolution there. I will now report this as a bug, but I do not expect it will receive much attention.

---

### Post by grumrick on 2011-05-29
I have reported this as a bug. It is [https://bugs.launchpad.net/ubuntu/+bug/784985](https://bugs.launchpad.net/ubuntu/+bug/784985).

---

### Post by budo on 2012-02-02
I commented the BUG too, since I'm affected. I'm using a Travelmate 8372 and ubuntu 11.10.
No problems with VGA, but LAN and USB doen't work.
The "strange" part is that the first time i connected the dock, hotplugging it, the USB worked out of the box, without any problem!
After a reboot it didn't work anymore... tried several times but no way...
In windows Seven it works without any problem and without the need to install anything...

Is there a way to debug anything? Any information i can gather to help solve the problem?

---

