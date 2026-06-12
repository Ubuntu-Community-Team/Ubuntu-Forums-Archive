---
title: "Passwords in Grub?"
date: 2005-11-22
forum: General Help
---

### Post by bonzodog on 2005-11-22
Anybody here know if Grub can password protect a partition, as we want to put a dual boot machine that currently has 2 windows installs on ubuntu and windows, knocking out one of them which isn't needed. It currently uses a boot manager called 'GAG' which is graphical and claims to be able to boot linux, but actually only recognises ext2 filesystems. (we've already tried to get it to see an ubuntu install!) However, GAG can password protect a partition. I've not yet seen grub or lilo do this, so can they? If so, how?

---

### Post by SuSUntu on 2005-11-22
See the GRUB sections in the following links (lots more available via search I suppose):

[http://linsec.ca/syshardening/bootlock.php](http://linsec.ca/syshardening/bootlock.php)
[http://www.redhat.com/docs/manuals/linux/RHL-9-Manual/security-guide/s1-wstation-boot-sec.html](http://www.redhat.com/docs/manuals/linux/RHL-9-Manual/security-guide/s1-wstation-boot-sec.html)

If you still want to use an external boot manager, try BootIt NG. I have a machine with 2 XP Pro installations and 3 Linux installations. It's very powerful, stable and flexible.

---

### Post by bonzodog on 2005-11-22
thanks for that. It looks like it's simply a case of adding a couple of lines to grub.conf (or menu.lst?) from ubuntu.

---

