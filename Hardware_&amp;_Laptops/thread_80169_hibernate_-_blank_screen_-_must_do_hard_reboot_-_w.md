---
title: "hibernate - blank screen - must do hard reboot - why?"
date: 2005-10-21
forum: Hardware &amp; Laptops
---

### Post by towsonu2003 on 2005-10-21
On a hp pavilion zv5120us,
when I choose System>Log out>Hibernate
system closes everything, than a black blank screen appears, and nothing further. I have to hard reboot, and I have no idea what's going on.
Anyone have any ideas where to look for a meaningful error log for this? 
I looked through the forum, but did not see anything relevant.

---

### Post by Ventajou on 2005-10-21
Hi,

I have the same problem with my Dell Latitude D505... It's a Centrino if that makes any difference.

---

### Post by Joe_lurker on 2005-10-21
Try looking in the /var/log/acpid log if you have it otherwise in /var/log/messages.  Also try disabling pcmcia (sudo /etc/init.d/pcmcia stop) before you hibernate.  Does sleep work?

-Joe

---

### Post by Gandalf on 2005-10-21
Have you tried Hibernate on RAM? ( to enable it, edit /etc/default/acpi-support, uncomment the Second line "ACPI_SLEEP=true" ), i think it may work, on my HP pavilion 1071EA both hibernating works, but on RAM is more :roll: clean i think...

---

### Post by towsonu2003 on 2005-10-21
[QUOTE=Gandalf]Have you tried Hibernate on RAM? ( to enable it, edit /etc/default/acpi-support, uncomment the Second line "ACPI_SLEEP=true" ), i think it may work, on my HP pavilion 1071EA both hibernating works, but on RAM is more :roll: clean i think...[/QUOTE]

couldn't find specific info in /var/log/messages... it says something like signal 15 received exiting - and that's all... 

will try ACPI_SLEEP but I would prefer suspend to disk (hibernate)

will also try pcmcia stop

I will report back if I'm alive :)

---

### Post by Gandalf on 2005-10-21
[QUOTE=towsonu2003]couldn't find specific info in /var/log/messages... it says something like signal 15 received exiting - and that's all... 

will try ACPI_SLEEP but I would prefer suspend to disk (hibernate)

will also try pcmcia stop
[/QUOTE]Ok good luck then
[QUOTE=towsonu2003]
I will report back if I'm alive :)[/QUOTE]and if your pc alive too :lol:

---

### Post by towsonu2003 on 2005-10-22
[QUOTE=Gandalf]Ok good luck then
and if your pc alive too :lol:[/QUOTE]

hmmmm
okay I'll be honest... I was too scared to do them - right after I wrote that. Well, may be in 6.04? ehehe
I'll save the lucky wishes till then.
although I did not try the result, I changed the SLEEP option, though. just in case I go gung-ho one day... :rolleyes:

[EDIT] PS. I would still welcome any ideas on what to do. I seem to be unable to find anything in wiki... At least I'd like to understand the machinery of hibernate specifically in ubuntu.

---

### Post by hedge on 2005-10-23
[quote=towsonu2003]hmmmm
okay I'll be honest... I was too scared to do them - right after I wrote that. Well, may be in 6.04? ehehe
I'll save the lucky wishes till then.
although I did not try the result, I changed the SLEEP option, though. just in case I go gung-ho one day... :rolleyes:

[EDIT] PS. I would still welcome any ideas on what to do. I seem to be unable to find anything in wiki... At least I'd like to understand the machinery of hibernate specifically in ubuntu.[/quote]

Here a real way to to suspend to disk [http://www.ubuntuforums.org/showthread.php?t=75443](http://www.ubuntuforums.org/showthread.php?t=75443)

---

