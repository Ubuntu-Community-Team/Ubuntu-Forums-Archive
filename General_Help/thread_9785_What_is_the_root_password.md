---
title: "What is the root password?"
date: 2005-01-01
forum: General Help
---

### Post by MrKrabs on 2005-01-01
Hi.
I am new to Ubunto. and I did see something when I was setting the OS up that said if you need root priviliges to use the sudo command but now that I have the OS installed sudo does not get me to Super User status.

What is the defalt root pass word?

---

### Post by Hezekiah on 2005-01-01
There are some details on this here:

[http://www.ubuntulinux.org/support/documentation/faq/root](http://www.ubuntulinux.org/support/documentation/faq/root)

To sum things up, the root account is disabled by default.   You can use sudo to run single commands as root, or use 'sudo -s' to get a root console.

When you are prompted for a password by sudo, enter your own password, and everything should work from there.

Hope this helps.
Hez

---

### Post by Chokableu on 2005-01-08
root password strange behavior
here is what i noticed on my system. for instance, when i activate the network configuration (applications menu) , the system asks me for my root password, which i don't have, because according to Ubuntu's policy, i created a user account and gain root privileges to do some specific tasks (sudo ...). But in this particular case,  my user password is not accepted.
then i put the network monitor on the task bar and click on configuration, and there my user password gives me access to the ethernet configuration.
Same behavior with firestarter. 
that's not a problem in itself , but perhaps a question of polishing the all thing in the future  :-) or may be there is a rationale to it that i missed

---

### Post by jazzorist on 2005-01-08
Chokableu:

The command in the launcher is probably wrong. Right-click the firestarter (or network conf.) entry in the applications menu and take a look at the properties. If the command is "gksu /usr/sbin/firestarter" you have to change "gksu" to "gksudo" and it should work with your password.

.j.

---

### Post by xsos on 2005-01-08
[QUOTE=jazzorist]Chokableu:

The command in the launcher is probably wrong. Right-click the firestarter (or network conf.) entry in the applications menu and take a look at the properties. If the command is "gksu /usr/sbin/firestarter" you have to change "gksu" to "gksudo" and it should work with your password.

.j.[/QUOTE]
 helo you could setup the roor password using command: passwd  , and then type your new password. use the command under sudo (applications - system tools - root terminal) i hope this could help u.

---

### Post by Sensebend on 2005-01-10
To enable root, type sudo passwd root in a terminal, you'll be prompted for your user password and then followed by the new password for root.

---

### Post by lukem on 2005-01-10
just curious

what's the difference between sudo and gksudo

thanks
luke

---

