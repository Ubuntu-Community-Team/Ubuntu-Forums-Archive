---
title: "Thousand questions before remove Ubuntu from a desperate 6.10 user"
date: 2007-07-11
forum: Hardware &amp; Laptops
---

### Post by redarmy on 2007-07-11
Hallo all,
I have installed Ubuntu 6.10 alternate next to my Windows2000, but this linux distro doesn't recognize my PCMCIA network card. When the command ./pcmciautils under /etc/init. is issued, the machine indicates:
* No PCMCIA bridge module specified

The other big problem is that during installation of this version Ubuntu, I didnot seen any prompt on asking for inputting password for the root. As a result, I have no way to enter linux as root. How could I retrieve the missing password.

If the problems are too difficult to tackled, I'd like to remove this version Ubuntu. I think I should go to Windows2000 to repartition this part of harddisk which is at this moment dedicated to Ubuntu, and make a boot disk, after restart, start Windows2000 with this boot disk. Is this scheme feasible? What kind of problems should I pay attention to?

Any help will be highly appreciated.

Redarmy

---

### Post by Stephen Howard on 2007-07-11
Ubuntu is set up without a root password.  Instead, log on as a normal user and use sudo to become root.

---

### Post by bernied on 2007-07-11
That's really only two questions, no reason to get down-hearted.

I don't know the answer to your PCMCIA network card issue, but as for root access...

Ubuntu doesn't use a root user by default. Instead you are encouraged to use the sudo application, or its graphical equivalents gksu and kdesu, to run inidividual commands with root privileges. During the install process, the user that you first specified will already have authority to use sudo for all commands.

[Here is some information](http://linux.about.com/od/ubuntu_doc/a/ubudg24t4.htm) that might explain things better. I'd suggest you read it and google some more before you think about any of the below.

You can configure the behaviour of sudo with the visudo command (be very careful).
You can get a root terminal with 'sudo su'.
You can enable the root user with 'sudo passwd' - you will be asked for a password three times, the first is your password (the first user setup during install), the second is the new root password, and the third is confirmation of the new root password.

Good luck with the PCMCIA card - I'd suggest you post something in the hardware section of the forum with a slightly more optimistic subject. And google can help as well.

---

### Post by redarmy on 2007-07-11
Thanks for your reply. Actually I have tried my hand with sudo, but upon running sudo start pcmciautils, an errror comes off saying: start need to be root (I cannot exactly recall the message). Anyways I shall try my luck in the hardware group as the last resort.

---

### Post by louieb on 2007-07-11
Before you uninstall Please read this. If you don't replace the MBR code before removing Ubuntu your computer will make a nice doorstop.  [Dual Boot Un-install Page]("http://www.users.bigpond.net.au/hermanzone/p18.htm")

---

