---
title: "Install Ubuntu from a Network Server without using PXE"
date: 2009-01-30
forum: Installation &amp; Upgrades
---

### Post by ussvoyager74656 on 2009-01-30
Ok,  I went to the IRC and someone kept through unetbootin at me, which WILL NOT do what I want to do.

Anyways, heres the skinny.

I want to be able to boot a computer to the network and pull the ubuntu install from another machine.

BUT

I CANNOT use a PXE/DHCP server.  So I have to use a CD or a flash drive to begin the bootup process. So after, it has boot up I can remove the media and walk away, while ubuntu installs itself on that machine.

Thanks for you help in advance

---

### Post by cariboo on 2009-01-30
Use the [mini.iso]("http://help.ubuntu.com/community/Installation/MinimalCD"). this just installs enough to start up the network and allow you to setup where you want to download packages from. Be aware that you will have to setup a mirror of the repositories first.

The mini.iso will also allow you to do the type of setup you want, server, desktop or cli.

Jim

---

