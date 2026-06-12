---
title: "error: hd0,msdos1 read error"
date: 2010-11-05
forum: Hardware
---

### Post by drklump on 2010-11-05
So... I upgraded to Ubuntu 10.10 Netbook Remix. It worked just fine for a week or so. But yesterday when I tried to boot it stated this message:

"error: hd0,msdos1 read error"

so I decided to locate my drives, and this is what I got:

"grub rescue> ls
(hd0) (hd0,msdos1)
grub rescue>"

After that I tried to locate the grub folder:
"grub rescue> ls (hd0,msds1)/boot/grub"

waited a while

"error: hd0,msdos1 read error
grub rescue>"

Ehm, I kinda new to commands in Ubuntu, but not the actual OS.
It would be awesome if there's someone out there who knows how to solve this problem.

By the way, I haven't installed any new programmes for a while, nor upgrades. But I do let my computer go to sleep mode quite often and sometimes for a very long time.

It's a Asus Eee PC 1000h 1GB RAM. Its original OS was Windows XP, but I've been running Ubuntu for about a year or so.

Thanks! ^^

edit:
Right now is the screen looking something like this:

"error: hd0,msdos1 read error
grub rescue> ls
(hd0) (hd0,msdos1)
grub rescue> ls (hd0,msdos1)/boot/grub
error: hd0,msdos1 read error.
grub rescue>"

and the underlining "blinking"...

---

### Post by jdownes on 2010-12-21
I am getting the same error message.

Have installed 10.10 on a new hd  as sole partition.

10.10 eventaully loads but so slow

Any ideas???:mad:

---

### Post by Yearim on 2010-12-22
i have the same problem hd0 msdos1 read error, after several times trying to do something with commands when i reboot my pc it was like ubuntu start normal but it was very slow and never start, i am sorry if my grammar is bad the english is my second lenguage. if someone can fix that problem would be great

---

### Post by jdownes on 2011-01-02
Hi

Not sure this helps?

But I reinstalled Ubuntu Maverick onto new clean HD, allowing Ubuntu to format & partition this disk.

This stopped the error"hd0,msdos1" msg

However the boot loader is a bit flaky - needs CTRL-ALT-DEL to fire up Ubuntu?

Not sure this helps?

---

