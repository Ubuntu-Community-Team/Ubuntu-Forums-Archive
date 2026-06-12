---
title: "Should I connect to internet while installing Ubuntu"
date: 2006-01-13
forum: Installation &amp; Upgrades
---

### Post by geniusvicks on 2006-01-13
Should I connect to internet while installing Ubuntu? i.e. after I download the cd image, and burn it to a cd. I reboot my computer with the cd in and when I'm installing it will the data come out from the cd like windows or should i connect to the internet?

---

### Post by Gustav on 2006-01-13
Most data will come from the CD but if you are connected to the internet you will download security updates as well during the install.

---

### Post by Kipper on 2006-01-13
Unless you are confident that your system cannot be hacked, for example you connect to the Internet via a router which has a configured firewall, I would say definitely not, it's not secure. 

In anycase, you don't need to consider updating/adding software until post-install. Even then strictly speaking you should not connect your system to the Internet before you perfomed a few basic security tasks on you rmachine.

Running the LiveCD on your machine should show you if your hardware is compatible.

---

### Post by kaamos on 2006-01-13
[QUOTE=Kipper]Even then strictly speaking you should not connect your system to the Internet before you perfomed a few basic security tasks on you rmachine.[/QUOTE]

As ubuntu ships with all ports closed, I don't really see the problem here. In your opinion, what would these tasks be?

---

### Post by Kipper on 2006-01-13
Really, all ports are closed? So if I just had a dial-up modem it is Ok just to connect straight away to the Internet? I don't need to worry about a firewall of any kind? Is this true for both a standard and server install? And if you did a port scan on it, absolutely nothing would turn up?

Perhaps I'm just being paranoid, or too use to using Mandrake. I haven't used Ubuntu/Debian much but I might make the switch. But I did notice immediately after installing Ubuntu, I could ping from another machine, connect to an ssh server, a cups server, and a samba server, so surely some ports must be open. 

Of course, I suppose there has to be something running on Ubuntu to connect to, or make it visible, for there to be a risk. But is that the only way the machine could be at risk? I did notice hosts.allow and hosts.deny were empty, at least on 5.04 they are. 

As far as security tasks are concerned, I was thinking about running Bastille to start with. But perhaps this all completely unnecessary.

---

### Post by Sef on 2006-01-13
>  I don't need to worry about a firewall of any kind?

You should have a firewall.  Linux is much harder to crack than Windows, but it is still possible to crack it.  There is a firewall that comes with Ubuntu.

Applications ----> Add Applications ----->System Tools ----> click on the arrow for the submenu -----> click on firestarter.

If it asks about opening multiverse say yes, and just click on apply to start the install.

---

### Post by kaamos on 2006-01-13
[QUOTE=Kipper]But I did notice immediately after installing Ubuntu, I could ping from another machine, connect to an ssh server, a cups server, and a samba server, so surely some ports must be open.[/QUOTE]
Then you have installed these services. Ubuntu out-of-the-box has no ssh-server, no samba-server and cups only listens to localhost.
[quote=Sef]
You should have a firewall. Linux is much harder to crack than Windows, but it is still possible to crack it. There is a firewall that comes with Ubuntu.

Applications ----> Add Applications ----->System Tools ----> click on the arrow for the submenu -----> click on firestarter.

If it asks about opening multiverse say yes, and just click on apply to start the install.[/quote]
Firestarter is just a tool to configure the firewall. The firewall is running and the configs can be done from the command line without installing anything as well. The point being that ubuntu has a pretty safe setup to begin with without installing anything. Installing firestarter is a very good idea though..

---

### Post by Kipper on 2006-01-13
Kaamos, you mis-read my post. Ubuntu "out-of-the-box" connected to servers running on another machine. Exactly how does it do this if all ports are closed? But then I release I'm talking about 5.04 which certainly has no firewall running after the first boot. Would the same happen in 5.10?

If iptables is installed with some pre-confgiured rules in 5.10 which block incoming connections and is up and running on first boot, that's good. 

Personally, I would like to see 5.10 have some sort of firewall software included rather than having to go look for it and install it. 

I would prefer the firewall to have a visible frontend (firestarter, guarddog etc.)  and not just run in the background and as a new user never realise it was there. As such, you wouldn't know if it was functioning or not. 

That's one thing I didn't like about Ubuntu 5.04, it was not easy to see what services were installed and running.  Correct me if I'm wrong, but there is no simple command like "service xxx stop|start|restart"  as in red-hat based distros.

Has something been added in 5.10 to help administer services?

---

### Post by Gustav on 2006-01-14
There is a quite minimalistic servicehandler (system->administration->services).

Ubuntu have a ssh *client* and so on from the start but no ssh *server*. This means that it's quite safe from attacks even without a firewall but to be on the safe side there are no reasons **not** to have a firewall.

---

### Post by kosmic on 2006-01-14
example
sudo /etc/init.d/mysql stop | start
sudo etc/init.d/gdm restart
 
simple :)

---

### Post by Kipper on 2006-01-14
Simple, maybe. But debian's equivalent of redhat's chkconfig command is update-rc.d and there apears to be no simple way of showing all active serivces as in chkconfig --list. Anyway, its time I downloaded the debian reference card.

---

### Post by Gowator on 2006-01-14
Either way ubuntu comes complete with pre-installed rootkit in the form of ALL:ALL in sudoers

---

