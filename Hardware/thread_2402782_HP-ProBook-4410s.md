---
title: "HP-ProBook-4410s"
date: 2018-10-04
forum: Hardware
---

### Post by kagashe on 2018-10-04
This Laptop was provided to me by my employer in 2010
HP-ProBook-4410s
Memory 2,9 GB
Processor Intel® Core™2 Duo CPU T6570 @ 2.10GHz × 2
Graphics Mobile Intel® GM45 Express Chipset

It came with Windows XP but I prefer Linux even on Hardware provided by employers (although they never liked it) and I installed Ubuntu 10.04 in dual boot and subsequently Ubuntu 12.04 and both worked well. I quit regular office work in 2016 and the Laptop was lying unused.

Meanwhile I purchased personal Laptop Lenovo G50-45 and was running subsequent LTS versions of Ubuntu but the Laptop is broken now.

I took out the HP ProBook which had Ubuntu 12.04 working well but now unsupported.

I installed Ubuntu 18.04-1 on it now but I am having random freezes particularly if I leave it for couple of minutes. After freeze it is not responding to touchpad, mouse or keyboard even to ctrl alt F keys or any other key combinations.

I am posting now from the same system and I hope it won't freeze till I complete the post.

Any help would be greatly appreciated.

Kamalakar

---

### Post by Autodave on 2018-10-04
First thing that comes to mind is that it could be overheating.  Running Ubuntu on those specs would be really pushing it.  You could also have dirt / dust built up inside the unit.  Have you tried blowing canned air through it?  You could also try sucking out the dirt with a vacuum, but use extreme caution that you do it very quickly: holding a strong vacuum on it for even a few seconds could cause damage to the fan itself from over-revving.

If cleaning it doesn't help, you may want to consider a lighter desktop like Xubuntu.

---

### Post by kagashe on 2018-10-08
After reading about crashes on askubuntu and elsewhere I did the following:
```
sudo gedit /etc/default/grub
Replace following line
GRUB_CMDLINE_LINUX_DEFAULT=”quiet splash”
with
GRUB_CMDLINE_LINUX_DEFAULT=”quiet splash intel_idle.max_cstate=1&#8243;
sudo update-grub

```

I hope it works for a few days then I will mark the thread as solved.

Kamalakar

---

