---
title: "Mounting volumes on demand"
date: 2008-07-18
forum: General Help
---

### Post by Mark Phelps on 2008-07-18
I'm trying to create a bunch of menu items by which I can mount individual volumes on demand.

I'm mounting NTFS volumes, and I want to be able to specify read-only, or read-write for each of the mounts.  So, I tried each one in a terminal using a command similar to the following:

sudo  mount -t ntfs-3g /dev/sda5 /media/DataVol -o ro,locale=en_US.utf8

And they work great!

So, I then edited the menus and added a single item for each mount.  Tried them and they worked.  Then, I logged off.

But now, the next day, when I try them (from the menu), nothing happens.   So, I tweaked one of them to be "gksudo" -- and it popped up a window where I entered the root password -- and it worked.  So, I changed ALL of them.

I then unmounted the volume I was using (also through a menu entry). And I went off to do other things.

Now, a couple of hours later, when I click the same menu entry, nothing happens again!!

OK, so I understand that when, in a terminal, I do "sudo", that "sticks" for some period of time such that I don't have to keep entering the root password.  So, is this the same problem with the menu entries?

I've got several of these volumes and I really don't want to have to type the mount command from a terminal every time -- because I'm trying to use this to prototype a way to setup other machines to do this from menu entries.  So, I need this to work from a menu.

Can anyone help?

---

### Post by Mark Phelps on 2008-07-24
WOW  5 days and absolutely no responses!  Good thing I stumbled upon XDialog and figured out a solution using shell scripts.

---

