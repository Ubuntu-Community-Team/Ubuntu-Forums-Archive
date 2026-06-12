---
title: "update to 2.6.28-13 failed"
date: 2009-06-21
forum: Installation &amp; Upgrades
---

### Post by Mr Bean on 2009-06-21
I just used ubuntus automatic update to do all the recommended updates and now all 4 of the below boot options give the following error:

[IMG]http://img13.imageshack.us/img13/6628/error1c.jpg[/IMG]

[IMG]http://img13.imageshack.us/img13/2511/errorbpm.jpg[/IMG]

What the fudge? All hardware is the same as before the update but something has gone badly wrong. 

How to I fix my system?

:edit:

Also I noticed after the update (and before restarting) my sound stopped working.

:edit:

changed "kopt=" in menu.lst from the UUID to /dev/sda1 and that's fixed it.

*phew*

---

### Post by master_kernel on 2009-06-21
Boot into the old kernel and run '$ dpkg --configure -a

---

### Post by Mr Bean on 2009-06-21
I'm given a prompt with a 'greater than' symbol and a blinking cursor.

What now?

---

### Post by ajgreeny on 2009-06-21
I was very surprised when I did this update yersterday, to find that I was offered an option to either keep my old or, presumably, use a new /boot/grub/menu.lst file.  This is something that I have never seen before with the kernel update always automatically editing the file.  I chose keep the old version, as I knew that worked, but then updated it myself as the new -13 kernel, obviously, was not in the list.

Does anyone know why this happened for this kernel update?  My menu.lst file has been manually edited by me to add a grub splash graphic, but that is something I always did in previous ubuntu versions, so perhaps it is something to do with jaunty's grub that is new.

My system is working great with the manual edit, but I also wonder if this situation may have something to do with Mr Bean's problem.  Any thoughts, anyone?

Sorry, Mr Bean, I don't think I can actually solve your problem, but I thought it was worth making my point about this "unusual" update.

---

### Post by Mr Bean on 2009-06-21
I got the exact same option, and I chose to use the package managers version (that wasn't the axact option but it was something along those lines)

I've just booted with a live CD to edit the menu.lst file myself and it looks fine but I've changed all the UUIDs to /dev/sda1 but I get the same problem.

---

### Post by running_rabbit07 on 2009-06-21
I havent' had any problems with the update but, how do I get rid of the options to boot the old kernel?

---

### Post by Mr Bean on 2009-06-21
> **running_rabbit07 said:**
> I havent' had any problems with the update but, how do I get rid of the options to boot the old kernel?

You could comment them out in the menu.lst file (in /boot/grub) 

It should just use the first entry as the default though.

---

### Post by raymondh on 2009-06-21
> **running_rabbit07 said:**
> I havent' had any problems with the update but, how do I get rid of the options to boot the old kernel?

Or,  you can download/install (thru synaptic or terminal) startup manager which is a GUI app that gives you options which kernel or OS to default-boot into.  It also presents you with other options as well.  This GUI writes to your menu.lst as well per options you chose.

Just wanted to share just in case anyone's too lazy to do some manual editing :)

Happy Ubuntu-ing (and Father's day as well).

---

### Post by running_rabbit07 on 2009-06-21
> **raymondhenson said:**
> Or,  you can download/install (thru synaptic or terminal) startup manager which is a GUI app that gives you options which kernel or OS to default-boot into.  It also presents you with other options as well.  This GUI writes to your menu.lst as well per options you chose.

Just wanted to share just in case anyone's too lazy to do some manual editing :)

Happy Ubuntu-ing (and Father's day as well).

Thanx, that worked. I have Ubuntu 9.04 on here twice. Once on EXT3 and once on EXT4 so with the double kernel option my boot selection screen was packed. I just loaded the EXT4 today and I have the feeling the EXT3 will go away very soon with how well the EXT4 is working.

And happy Father's day back at ya!

---

