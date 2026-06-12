---
title: "Networking problems"
date: 2005-12-05
forum: General Help
---

### Post by Thunk on 2005-12-05
After installing Ubuntu for the first time and not being able to get internet access (DSL) I deleted the hostname from DHCP config panel and now whenever I log in it gives me this error messege:

"Could not look up internet address for . This will prevent GNOME from operating correctly. It may be possible to correct the problem by adding to the file /etc/hosts."

Now when I press on system->admin.->networking it says:

"starting networking" and then shuts down without even opening the networking window...

Any ideas of what I should add to etc/hosts or how I can roll back to the previous stable setup?

---

### Post by adwait on 2005-12-05
Do you use some kind of client to start your connection in windows?? Try running this:
```
sudo pppoeconf
```

---

### Post by Thunk on 2005-12-05
The problem is that at the surrent state I can't even load any of the config windows...

---

### Post by adwait on 2005-12-05
umm.....huh? What config windows? I am not getting what you are trying to say.......

Try typing the command I suggested in a terminal window (look at my signature for where to find that).

---

### Post by Thunk on 2005-12-05
[QUOTE=adwait]umm.....huh? What config windows? .[/QUOTE]

Yeah, sorry, I guess that's my own lingo...

Anyways, whenever I **sudo** it gives me this error messege:

"sudo: unable to lookup via gethostbyname()"

Thanks a lot, I really appreciate it.

---

### Post by aclaunch on 2005-12-05
It sounds like your /etc/hosts file is messed up. This is what it should look like:

127.0.0.1 localhost.localdomain localhost moria
# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

Note that "moria" is my local computer's hostname. Replace it with your computer's hostname. Basically, your computer needs a hostname-it can be anything- but it should be something. Lots of things, especially networking, depend on it.

Just do "sudo gedit /etc/hosts" ; if sudo does not work, try "sudo su" which make you actual root.

Good Luck,
Alan

---

### Post by Thunk on 2005-12-05
Thanks a lot! I'll try that.
:D

---

