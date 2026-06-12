---
title: "is it possible: minimum install over wireless"
date: 2009-08-19
forum: Installation &amp; Upgrades
---

### Post by keratos on 2009-08-19
Seeking to load a minimal install of ubuntu.

Welcome responses to the following, please:

1. Searching the threads it appears that at boot time if I select "custom" as the kernel, then I get dropped to a command line with base system.
Is this correct?

2. It is not practical for me to connect via wired LAN. I do have a wifi connection that works perfectly when running ubuntu liveCD in normal mode and when dual booting to windoze. I'd like to build on the base install using retrieved packages from the net over wireless. The AP is WPA2 secured with DHCP off. This cannot be changed! I have the passphrase key and IP address of AP.
Is this possible, what is the HOWTO procedure/linux commands. No 'man' pages please, I've looked at wlconfig and ifconfig - I genuinely need help please and not references to man pages.

Many thanks.

---

### Post by dstew on 2009-08-19
I am not sure what you are trying to do. Do you want to install a minimal Ubuntu from the Live CD? And then later, add packages over the internet? If so, do a **server** install. That gives you a minimal command-line interface, with software needed to install more packages by the internet.

---

### Post by vikjon0 on 2009-08-19
I am guessing he wants to use the minimal CD.
Anyway, using the server CD instead is probably a good idea.
I am pretty sure the result will be the same is if use used minimal.

Possbly the alt CD, havent tried it.

---

### Post by keratos on 2009-08-19
I'm trying to do a minimal install using  a CD and which CD do I need (i.e. a link to it please)

Also

The question was can I use wireless after the minimal install and if so then HOW do I do this - i.e.  what are the set of commands required to connect my laptop to the WAP.

p.s. I CERTAINLY DO NOT want to install a Server or anything to do with Server.

---

### Post by dstew on 2009-08-20
"Server install" is just the name Ubuntu uses for a command-line interface install. You don't have to install server software, or create a file server on a server install. It is essentially the same a regular Ubuntu, only without the gnome graphical user interface, also known as the desktop.

Later, if you want to install the full desktop, you can do ```
sudo apt-get install ubuntu-desktop
```and your server install will become a desktop install.

EDIT: Here is the server download page: [http://www.ubuntu.com/getubuntu/download-server](http://www.ubuntu.com/getubuntu/download-server)
You can also install a server system from an Alternate Install CD: [http://www.ubuntu.com/getubuntu/downloadmirrors#alternate](http://www.ubuntu.com/getubuntu/downloadmirrors#alternate)

---

### Post by keratos on 2009-08-23
thanks. done it with server install, no desktop because I wanted minimal base + icewm. Icebuntu too bloated!
cheers

---

