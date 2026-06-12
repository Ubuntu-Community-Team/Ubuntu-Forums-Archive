---
title: "Preventing USB disks auto-mounting"
date: 2013-07-06
forum: Hardware
---

### Post by parish on 2013-07-06
I'm running OS X in VMWare Player on Ubuntu 12.04LTS and have a couple of USB disks (one with two partitions) attached, formatted HFS+.

When I boot the machine - or exit/reboot OS X - Ubuntu mounts the disks. When OS X starts it "steals" them from Ubuntu. I want to stop Ubuntu auto-mounting them (but with the ability to manually mount them should I wish).

I've been looking into how to do this and think I've got it figured out but would like confirmation that I understand it correctly.

I reckon I should follow the instructions [here]("http://www.tuxradar.com/answers/500") to ensure the disks always get assigned the same block device names (/dev/xxx), then I add entires for the devices to /etc/fstab with the `noauto' option.

Have I got that right?

Thanks.

---

### Post by ohnonot on 2013-07-09
i think the link you gave does not apply.
comment out everything in your fstab that is related to those external drives (whether you added it or it was already there), reboot and see if you get the desired behavior.
if they still mount automatically, it must be an automount setting usually accessible through the file managers preferences.

if you're not sure, post your /etc/fstab here.

cheers,
o.

---

### Post by parish on 2013-07-10
> **ohnonot said:**
> i think the link you gave does not apply.
comment out everything in your fstab that is related to those external drives (whether you added it or it was already there), reboot and see if you get the desired behavior.

There are no entries in /etc/fstab for these drives (which is what I'd expect).

---

### Post by steeldriver on 2013-07-10
Have you checked that (launcher -->) Removable Drives and Media --> Storage tab --> 'Mount removable drives when hotplugged' is unchecked?

If that doesn't do it, try

```
gsettings set org.gnome.desktop.media-handling automount false
```

(or equivalently with dconf if you have the dconf-tools package)

```
dconf write /org/gnome/desktop/media-handling/automount false
```

---

### Post by parish on 2013-07-10
> **steeldriver said:**
> Have you checked that (launcher -->) Removable Drives and Media --> Storage tab --> 'Mount removable drives when hotplugged' is unchecked?

If that doesn't do it, try

```
gsettings set org.gnome.desktop.media-handling automount false
```

(or equivalently with dconf if you have the dconf-tools package)

```
dconf write /org/gnome/desktop/media-handling/automount false
```

It seems that I'd already done what I wanted to do without realising.

I'd set automount and automount-open to false (using dconf-editor) but the drives still appeared in Nautilus under devices when OS X wasn't running. What I hadn't noticed was that there was no eject button next to them so although Ubuntu could see the drives it hadn't actually mounted them. I hadn't expected them to appear in Nautilus unless they were mounted.

What further confused me is that VMWare Player was still popping up a dialogue saying the drives were in use by the host.

So, it seems it is now working as I want.

Thanks for all the help guys :D

---

### Post by parish on 2013-07-10
.

---

