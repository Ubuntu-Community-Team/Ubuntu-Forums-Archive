---
title: "Can't su, need to edit hosts"
date: 2005-11-14
forum: General Help
---

### Post by everdred on 2005-11-14
Hi, I edited my hosts file and now every time I log in to my account I get

> "Could not look up internet address for [computer name]. This will prevent GNOME from operating correctly. It may be possible to correct the problem by adding [name] to the file /etc/hosts."

That seems like a logical enough solution (and I do have a backup of my old hosts), but I *can't actually edit* my hosts file. When I try to sudo su, it says "unable to lookup [computer] via gethostbyname()". In fact, I can't launch anything with admin privileges. And it's not just a GNOME thing; I'm just as stuck with the plain terminal desktop.


So I'm pretty much stuck. Help? Please?

**Update:** Thanks for all the help, though I solved the problem!

Solution:

At the Grub menu, choose recovery mode.
At the root@[whatever]:~# prompt:
```
vi
:edit /etc/hosts~
```
(hosts~) was my backup. Make necessary changes to it.
```
:saveas! /etc/hosts
:q
exit
```

---

### Post by invalid on 2005-11-14
Does this just happen with "sudo su" ? Can you edit as your own user with sudo privledges (without su)?
```
sudo nano /etc/hosts
```

Cb

---

### Post by Zwack on 2005-11-14
As an aside sudo -s does much the same as sudo su - 

Z.

---

### Post by cdsboy on 2005-11-14
you can also do
> $ su <username>
for any user name other than host

---

### Post by everdred on 2005-11-14
[QUOTE=invalid]Does this just happen with "sudo su" ? Can you edit as your own user with sudo privledges (without su)?[/QUOTE]

Yes, this also happens when I sudo as me (ie sudo gedit /etc/fstab).

---

### Post by invalid on 2005-11-14
[QUOTE=everdred]Yes, this also happens when I sudo as me (ie sudo gedit /etc/fstab).[/QUOTE]
If this is the case, I can only make a couple suggestions..

a) You could try to boot in a failsafe terminal, though it is very possible that this will result in the same errors.

b) You could boot a recovery tool (like a knoppix cd), edit the file through this, and return to Ubuntu.

Maybe someone else has some other suggestions.

Cb

---

### Post by everdred on 2005-11-14
> **invalid]a) You could try to boot in a failsafe terminal, though it is very possible that this will result in the same errors.[/QUOTE]

This does. I mentioned it in the intial post, but I used the wrong wording for it  said:**
> b) You could boot a recovery tool (like a knoppix cd), edit the file through this, and return to Ubuntu.

I tried this, but was unable to mount the partition as writeable. That may have just been my fault, so I'll try it again.

---

### Post by everdred on 2005-11-14
Yeah, I mounted the partition in Knoppix as

/UNIONFS/dev/hda5 on /mnt/hda5 type ext3 (rw,nosuid,nodev)

and it still wouldn't let me write to the hosts file.

---

### Post by razorbuzz on 2005-11-14
Instead of trying to su, are you able to initially login as root?

---

### Post by everdred on 2005-11-14
[QUOTE=razorbuzz]Instead of trying to su, are you able to initially login as root?[/QUOTE]

'ey stranger :)

Not sure. Is there a default root password? Because I can't remember ever having to set any one aside from my user one.

*edit:* Heh... sorry, that was a dumb question.

---

### Post by everdred on 2005-11-14
Nah, when I 

sudo passwd root

I get the same 'unable to lookup ubuntu via gethostbyname()' error.

---

