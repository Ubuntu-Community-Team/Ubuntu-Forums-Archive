---
title: "Nothing loads after fresh install"
date: 2006-06-22
forum: Hardware &amp; Laptops
---

### Post by corstar on 2006-06-22
I'm in a real pickle here.

I had a installation of fc5 on my second hdd and decided to install ubuntu on the master hdd. The install went fine as usual, then I got the login screen, no worries there.

That's where it stops dead. I do get the startup sound and x curser. But no right click menu, no desktop image, no menus, every key seems dead after the login screen.
Even ctl alt bkspce does nothing at all, as does ctl alt 1 or 2 or 3 and so on...

I have done a rescue kernel from grub, but the same results. edited  and reconfigured xorg from there and Nothing ......again.

I've taken every bit of non-essential hardware out individualy to single out the problem, nothing helps.

All my live disros work perfectly, gentoo, mepis, open solaris......

What on earth could it be....FC5 worked perfectly too (till I stuffed the LVG up)

PLEASE HELP.....oh, what is the default root password right after install ](*,)

---

### Post by corstar on 2006-06-22
When I enter rescue mode, logs in as root. All good there. But it won't let me switch consoles  even from there. How can I narrow this problem down?

I have a newish vidio card. But it worked fine previously under ubuntu (i've got breezy on now) The card is a Nvida6600.

---

### Post by user1397 on 2006-06-22
[quote=corstar]I'm in a real pickle here.

I had a installation of fc5 on my second hdd and decided to install ubuntu on the master hdd. The install went fine as usual, then I got the login screen, no worries there.

That's where it stops dead. I do get the startup sound and x curser. But no right click menu, no desktop image, no menus, every key seems dead after the login screen.
Even ctl alt bkspce does nothing at all, as does ctl alt 1 or 2 or 3 and so on...

I have done a rescue kernel from grub, but the same results. edited  and reconfigured xorg from there and Nothing ......again.

I've taken every bit of non-essential hardware out individualy to single out the problem, nothing helps.

All my live disros work perfectly, gentoo, mepis, open solaris......

What on earth could it be....FC5 worked perfectly too (till I stuffed the LVG up)

PLEASE HELP.....oh, what is the default root password right after install ](*,)[/quote]i am not sure about your problem, but I think your install cd might have been corrupted or burned too fast.  did you do the "check cd for defects" option at the first screen of the ubuntu-cd?  also, you should burn your iso images at 8x perhaps even 4x to make sure there are no errors.  the perfect guide for all of this is here: [http://www.psychocats.net/ubuntu/iso.html]("http://www.psychocats.net/ubuntu/iso.html")

by the way, thr root account is disabled by default in  ubuntu.  instead, sudo is used.  read here for more info: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by corstar on 2006-06-22
Thanks, it's strange though. I will download a new image from the net. I've used the same cd in the past to do fresh installs.

---

### Post by corstar on 2006-06-22
One other question though,

I have a bunch of stuff I need to back-up from the toasted FC5 partition. I have access to my laptop via ssh, but how do I mount that partition from the command line?
I try mount /dev/hda1 
But how to i add it to fstab without frying the other partition?

---

### Post by user1397 on 2006-06-22
[quote=corstar]One other question though,

I have a bunch of stuff I need to back-up from the toasted FC5 partition. I have access to my laptop via ssh, but how do I mount that partition from the command line?
I try mount /dev/hda1 
But how to i add it to fstab without frying the other partition?[/quote]that's an easy fix, just paste this in a terminal: ```
sudo mkdir /media/fedora
``` and then ```
sudo mount /dev/hda1 /media/fedora
```

---

### Post by user1397 on 2006-06-22
did that work for you, or not?

---

