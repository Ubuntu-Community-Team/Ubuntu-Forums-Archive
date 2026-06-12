---
title: "installation"
date: 2008-07-16
forum: General Help
---

### Post by ilplinux_tester on 2008-07-16
hi, i already install ubuntu to 2 pc which is desktop i386 and laptop amd64.for desktop i installed from windows xp and for laptop i install to free space hard disk. after install i found that for desktop it cant detect windows partition automatically rather than laptop which is already have a shortcut in Places panel. is this effect from how i install the distro?

---

### Post by maddog39 on 2008-07-16
Well if you made a mistake during the installation on your desktop (i think it was) and overwrote everything instead of installing beside windows then your not going to see a windows partition anymore because there isnt one. I haven't heard of the installer not detecting other bootable partitions before.

---

### Post by halitech on 2008-07-16
> **ilplinux_tester said:**
> hi, i already install ubuntu to 2 pc which is desktop i386 and laptop amd64.for desktop i installed from windows xp and for laptop i install to free space hard disk. after install i found that for desktop it cant detect windows partition automatically rather than laptop which is already have a shortcut in Places panel. is this effect from how i install the distro?

on the desktop, can you still boot into windows?

---

### Post by ilplinux_tester on 2008-07-16
everything ok about booting windows and ubuntu. i just wonder why in desktop i not find windows partition shortcut in "Places" panel like in laptop

---

### Post by kansasnoob on 2008-07-16
OK, you said: > for desktop i installed from windows xp and for laptop i install to free space hard disk. after install i found that for desktop it cant detect windows partition automatically rather than laptop which is already have a shortcut in Places panel. is this effect from how i install the distro?

Now, "for desktop i installed from windows xp" sort of sounds like that may have been a Wubi install like this:

[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)

Whereas, "for laptop i install to free space hard disk", which sounds like a typical dual boot setup something like this:

[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

That's the first thing we need to clear up.

BTW, I gave Wubi a test drive but know very little about it if that's what we're dealing with.

---

### Post by ilplinux_tester on 2008-07-17
for desktop i mounted the partition manually, but in laptop already have a shortcut in "Places" panel

---

### Post by kansasnoob on 2008-07-17
So when you restart (or start) either computer you get the GRUB screen where you can choose which operating system to boot?

And if so, in both computers, you can successfully boot both Windows and Ubuntu, eh? 

Bear with me, I'm dense:confused:

---

### Post by Sef on 2008-07-17
Moved to Wubi Forum.

---

### Post by kansasnoob on 2008-07-17
> **Sef said:**
> Moved to Wubi Forum.

Are you certain this is a Wubi install:confused:

---

### Post by ilplinux_tester on 2008-07-17
> Now, "for desktop i installed from windows xp" sort of sounds like that may have been a Wubi install like this:

[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)

Whereas, "for laptop i install to free space hard disk", which sounds like a typical dual boot setup something like this:

[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

yes that's the way i installed it

> So when you restart (or start) either computer you get the GRUB screen where you can choose which operating system to boot?

And if so, in both computers, you can successfully boot both Windows and Ubuntu, eh?

yes just like you said

---

### Post by ago on 2008-07-17
windows files are available under /host. In 8.04 other partitions are no longer mounted automatically.

---

