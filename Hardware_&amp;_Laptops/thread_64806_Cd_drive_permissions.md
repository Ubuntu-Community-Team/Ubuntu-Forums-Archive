---
title: "Cd drive permissions"
date: 2005-09-12
forum: Hardware &amp; Laptops
---

### Post by cbudden on 2005-09-12
So that i can burn a CD, i need to change the permissions on the cd drive, as i can only read it.  I do this and it works fine, but after a reboot Ubuntu "forgets" the setting and i need to change the permission again.  Why is it doing this?  How can i keep the setting?

---

### Post by Bruce3000 on 2005-09-12
[QUOTE=cbudden]So that i can burn a CD, i need to change the permissions on the cd drive, as i can only read it.  I do this and it works fine, but after a reboot Ubuntu "forgets" the setting and i need to change the permission again.  Why is it doing this?  How can i keep the setting?[/QUOTE]
 You may want to have a peek at your /etc/fstab file I'm guessing...

In a terminal:

sudo nano /etc/fstab

Under the options section for the drive you are talking about, if there is an "ro" change it to a "rw".

ctrl+x and choose yes for writing changes

ro= read-only, rw=read-write.

This is of course a bit of a guess, based on what info you have provided ;) Making these changes to /etc/fstab won't kill your computer and are reversible.

Hope this helps!

Cheers

Bruce

---

### Post by cbudden on 2005-09-12
[QUOTE=Bruce3000]You may want to have a peek at your /etc/fstab file I'm guessing...

In a terminal:

sudo nano /etc/fstab

Under the options section for the drive you are talking about, if there is an "ro" change it to a "rw".

ctrl+x and choose yes for writing changes

ro= read-only, rw=read-write.

This is of course a bit of a guess, based on what info you have provided ;) Making these changes to /etc/fstab won't kill your computer and are reversible.

Hope this helps!

Cheers

Bruce[/QUOTE]
 Thanks for your help, i will give it a go when im back on linix.

---

### Post by cbudden on 2005-09-12
[QUOTE=cbudden]Thanks for your help, i will give it a go when im back on linix.[/QUOTE]
 Ok i tried that but still no luck.  I need to keep changing the permissions on the hdc device in /dev/hdc and change it to write.

---

### Post by cbudden on 2005-09-12
[QUOTE=cbudden]Ok i tried that but still no luck.  I need to keep changing the permissions on the hdc device in /dev/hdc and change it to write.[/QUOTE]
 Ok, now everything works.  The drive is now saying i can write to the drive.  Don't know how though, but i set the fstab file to ro, and not rw.

---

### Post by Bruce3000 on 2005-09-13
that is bizarre!

---

