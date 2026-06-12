---
title: "Ubuntu Server or Desktop?"
date: 2008-10-21
forum: General Help
---

### Post by Aysah on 2008-10-21
At my company right now we are using a RedHat on a 1U Dual Core box for SFTP and would like to try Ubuntu out.  We definitely need a gui whether we choose Ubuntu Server or Desktop being that we are a mixed IT group and some just dont play nice with strict command line. So my bottom=line question is if either one better than the other for what we do?

Currently all we use on the redhat box is:
[LIST]
[*]VNC (internally)
[*]mastercommander
[*]samba
[*]openssh
[*]samba
[/LIST]

---

### Post by tCarls on 2008-10-21
My vote goes to using the ubuntu-server kernel. Among other things it turns off preemption and speeds up the timer interrupt, which seems like it would make some difference for you, see [http://www.ubuntu.com/products/whatisubuntu/serveredition/features/kernel](http://www.ubuntu.com/products/whatisubuntu/serveredition/features/kernel). The server edition doesn't come with a GUI, but you can install one with

```

sudo apt-get install ubuntu-desktop
sudo apt-get install gdm
sudo /etc/init.d/gdm start
sudo dpkg-reconfigure xserver-xorg

```

Another option would be to install the desktop edition then run ```
sudo apt-get install ubuntu-server
```

---

### Post by ghost_ryder35 on 2008-10-21
My vote goes for server edition... you can add on the other packages you need after install

---

