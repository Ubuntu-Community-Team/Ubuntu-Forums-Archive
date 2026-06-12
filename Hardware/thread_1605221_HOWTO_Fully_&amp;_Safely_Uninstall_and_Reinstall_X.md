---
title: "HOWTO: Fully &amp; Safely Uninstall and Reinstall Xorg?"
date: 2010-10-25
forum: Hardware
---

### Post by Calorus on 2010-10-25
How do I un/reinstall Xorg in Maverick? I'm having a nightmare on my Lenovo X200 with an Intel Mobile Chipset 4 Graphics Card which is refusing to do acceleration or let me start OpenGL.

I've seen some Kubuntu threads which circled around overriding security permissions, but there aren't equivalent files that I can find in Gnome.

Some seem to imply that this is an issue arising from the new kernel structure with it exerting more control on the Video Card which the current drivers aren't supporting.

So I though a good start might be to remove all of the old drivers I've had which have worked fine Lucid, but Synaptic tells me to remove them I'd have to remove Xorg itself - which seems odd - although reinstalling Xorg within Synaptic seemingly does nothing.

Any information on my 'little problem' gratefully appreciated.

---

### Post by IcarusR on 2010-10-25
Not guaranteeing 'safety' of any of this as I've never done it.

Need to boot into single user mode, ie command line.
Follow instructions here

[http://www.cyberciti.biz/faq/grub-boot-into-single-user-mode/]("http://www.cyberciti.biz/faq/grub-boot-into-single-user-mode/")

Login then become sudo

```
sudo su
```

Enter password

Remove xorg

```
apt-get purge xserver-xorg
```

Install xorg

```
apt-get install xserver-xorg
```

Configure xorg

```
dpkg-reconfigure xserver-xorg
```

xserver-xorg is part of a meta package with ubuntu-desktop, ie remove one removes them both.

So you will also have to reinstall ubuntu-desktop

```
apt-get install ubuntu-desktop
```

Please bear in mind this may break more of your system & not gain any thing.

As stated at top I've not done this myself, but is how I would approach it should I ever need to. 
Maybe simpler to go back to 10.04.

---

### Post by Calorus on 2010-10-25
Hi, massive thanks for responding - out of interest were one to have been so daft as to have not backed up one's system prior to upgrading, would there be an easy way to 'downgrade'?

I'd checked this out too, but it seems to be a case of restarting from scratch.

---

