---
title: "Ubuntu Boot Sequence"
date: 2005-07-31
forum: Hardware &amp; Laptops
---

### Post by SuperMike on 2005-07-31
On a normal Ubuntu bootup, does anyone know the boot sequence? It's quite a bit different than my RH9 and doesn't seem to match my average Linux boot sequence as specified in some of my older manuals.

I'm trying to see what Bash script that I can typically edit on bootup on this and future Ubuntu installs to add in my custom iptables statements, mapped remote smbfs shares, and so on.

I thought that most distros were supposed to do this boot sequence, but not Ubuntu:

/boot/grub stuff
/etc/inittab
/etc/rc.sysinit script
/etc/init.d stuff

I'm also pleased, however, that xinetd doesn't seem to be utilized in Ubuntu. I feel that init.d is so much easier to understand.

Since no rc.sysinit script is used, I guess I'm going to have to create my own service called "custom", stick it in /etc/init.d by following the /etc/init.d/skeleton example file, and fire it up, although I don't know the technique to make my custom service run by default on bootup.

---

### Post by varunus on 2005-07-31
Ubuntu uses a "system V" style init (you can google that for more info if you want).  There have to be corresponding symlinks in /etc/rc#.d, where # is the runlevel.  These symlinks must be named properly to run the script at that runlevel.

You can use the update-rc.d script to generate symlinks for a runlevel for a custom script you want in /etc/init.d.

---

