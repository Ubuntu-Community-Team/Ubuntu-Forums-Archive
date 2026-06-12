---
title: "sending a command to windows via ssh??"
date: 2008-10-12
forum: General Help
---

### Post by el_ricardo on 2008-10-12
ok so here's the deal: I have windows XP installed on virtualbox, with the intention of using it for photoshop illustrator and dreamweaver. Wine isn't an option because support for CS3 is non-existent at present. I want to configure kde to autoload a snapshot of the VM, without the taskbar, this isn't the hard part...

...what i want to know is whether it's possible to send a command to the VM over the virtual network to load my apps, can this be done with ssh?

cheers for any responses :)

---

### Post by spiderbatdad on 2008-10-12
I have not tried this, but i would think ssh would be ideal for this on a local network...not behind a nat. Have you tried? Are you wondering whether it's worth the trouble to install openssh-server? You will need putty on the xp vm.
[https://help.ubuntu.com/community/SSHHowto](https://help.ubuntu.com/community/SSHHowto)

---

### Post by bodhi.zazen on 2008-10-12
You can do it if you install cygwin on windows, you can install an openssh server via cygwin.

[http://www.cygwin.com/](http://www.cygwin.com/)

---

### Post by el_ricardo on 2008-10-12
that sounds complicated lol, anyway I'm having a big problem getting the virtual network actually working now, I've tried all the different interfaces and i can't seem to access the VM from ubuntu, for example if i try navigating to smb://ipaddressofVM it times out, and i can't ping it either, does anyone have any tips that i'm missing?

spiderbatdad suggested putty, can putty recieve ssh commands as well as send them?

---

