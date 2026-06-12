---
title: "External HD loses disc space everytime I delete sth with xubuntu"
date: 2007-09-03
forum: Hardware &amp; Laptops
---

### Post by ivofoe on 2007-09-03
Hello

I have an external hard disk (80Gb).
Unfortunately everytime I delete something on it, the disk space "disappears".

What's the problem here?

I have the same strange thing with my Sony cybershot digital camera. I can mount it via USB and transfer the whole pictures on my computer and I empty the sandisc card (in thunar file manager (using xubuntu)). On my camera it says:
either there is no disc space left, if I want to take a photograph
or the disc is full, if I want to see my pictures

so I first have to do some formatting manually on the camera.

I've no clue what it could be, because on Windows these to things worked awesomely well.

Thank you, Ivo

---

### Post by Iehova on 2007-09-03
Hi,

Open the disk in nautilus*, and click View > Show Hidden Files. You should see a hidden folder ./.Trash-yourusername.**

If you just select a file on that disk and hit delete, it isn't actually deleted but, as with your hard drive, moved to the trash folder, hence why your disk space appears to shrink.

If you go into ./.Trash-username, you can select to 'delete from deleted items folder'.**

If you want to save yourself the hassle, when deleting stuff hit Shift+Del rather than just Del when you delete stuff, that way it's permanently deleted.

Thanks,
[B]
* EDIT: Sorry, you're in Xubuntu not Ubuntu, you can do the same with Thunar. My bad. ;)
** EDIT 2: Actually, in Thunar I see a .trash-1000 file, which is where deleted files seem to go, still, delete away and use Shift-Del in future, if you're willing to take the risk... :P[/B]

---

