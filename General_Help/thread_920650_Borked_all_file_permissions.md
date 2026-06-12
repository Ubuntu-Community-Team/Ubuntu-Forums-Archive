---
title: "Borked all file permissions"
date: 2008-09-15
forum: General Help
---

### Post by jonnythan on 2008-09-15
Yes, I am a dolt.

I accidentally ran:

sudo chown -R www-data /

Instead of:

sudo chown -R www-data ./

Doh.

Is there any way at all to reset the file permissions on a fairly default 8.04 server install + LAMP without erasing the partition and starting over?

---

### Post by forger on 2008-09-15
Fat finger eh? :D Unfortunately there's no real way of recovering the permissions. By the way, you did **chown**, not chmod, you didn't change file permissions, you changed the owner.

You could also start using "." instead of "./", or "cd .." and then "sudo chown -R thefolder"

You should've made a backup :\

---

### Post by jonnythan on 2008-09-15
There's nothing really to back up. I only have two databases and a handful of config files that I need, and they are all backed up already. And /home is on its own partition so the restore process is minimal.

The only problem is that I don't really want a day and a half of downtime right now.

I've made root the owner of everything not on the /home partition and ssh and apache2 seem to be working. Maybe that'll get me by til Tuesday.

---

### Post by whizbaby on 2008-09-15
Btw a good thing to have is not only a backup, but a 
second system you could boot to if you broke your main system (again). Simply install the same thing in a second partition/drive and edit /boot/grub/menu.list to change the default if you want to boot into it (or write a little script that does it ;))
That way you can eventually reboot the computer into a running system.

---

### Post by koenn on 2008-09-15
There have been questions like these before, and one of the solutions was to boot from a live CD, mount the borked filesystem, compare it to the (obviouslu default) filesystem of the live CD system, and modify permissions (or ownership) where needed.
Maybe if you search the forums, you'll find some scripts to do such stuff.

Having everythinh owned by root is not a bad idea. I suppose some things will break, but if you can afford to just wait for the trouble, and fix it when it occurs, you can probably risk just leaving it like that for the time being.

---

### Post by jonnythan on 2008-09-15
OK, thanks for the advice guys. I like the Live CD idea.

---

### Post by whizbaby on 2008-09-15
> **koenn said:**
> Having everythinh owned by root is not a bad idea.
I'm not quite sure about that. Some things might stop working or even worse an exploit could be opened if a file is owned by root which isnt meant to. Anyways, in this particular case the risk might be low if you look at the software thats running and at the time it will be in that state...

---

### Post by bodhi.zazen on 2008-09-17
Alright, lets get back to finding solutions. We may not agree with each other, and that is fine. Lets agree to disagree on some issues or solutions and move on.

---

### Post by northern lights on 2008-09-17
Back to topic & @ the OP:

Boot into Recovery Mode, i.e. select it from the GRUB menu. If the menu does not show by default during boot, hit 'ESC' when it says "GRUB loading - stage 1.5".

Drop to a root shell and run```
chown -R root /
```and```
chown -R USER /home/USER/
```where USER is your username.

[EDIT]
If the install has multiple users, you obviously have to repeat the latter step.
[/EDIT]

---

### Post by LaRoza on 2008-09-17
Closed for review.

I see the last page at least hasn't focused on the issue. Will review and deal with any off topic posts.

---

### Post by Sef on 2008-09-17
Thread reopened after removing posts which either violated the Ubuntu Code of Conduct or were replies to them.  I removed the replies since it detracts from the OP's problems.

---

