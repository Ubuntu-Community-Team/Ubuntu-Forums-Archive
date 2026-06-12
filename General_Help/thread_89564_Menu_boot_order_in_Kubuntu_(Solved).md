---
title: "Menu boot order in Kubuntu (Solved)"
date: 2005-11-12
forum: General Help
---

### Post by Marcussen on 2005-11-12
I have a dual boot system and need to make windows the default system

I have tried to access the grub menu.lst like this

sudo cp /boot/grub/menu.lst /boot/grub/menu.lst_backup

then 

sudo gedit /boot/grub/menu.lst

nothing happens 

I can open the file with konqueror and Kate and edit the file but I can't save it.

For some reason sudo don't seem to work, my root password don't work.

Any ideas?

---

### Post by sunrex on 2005-11-12
hmm...

if your root password doesnt work..go here

[http://ubuntuguide.org/#gainrootmodifykernel](http://ubuntuguide.org/#gainrootmodifykernel)

then just change your root password..

---

### Post by aysiu on 2005-11-12
*gedit* is a Gnome command.
Since you're using KDE, you should use ```
sudo kwrite /boot/grub/menu.lst
```

---

### Post by Marcussen on 2005-11-14
I booted into recovery mode and entered my root password, I then changed
the user password with this command
# passwd user
entered my new password twice it was accepted.

I then booted into normal Kubuntu
user password worked.

but I can not get my menu.lst edited

I tried 
sudo kwrite /boot/grub/menu.lst
I don't get asked for a password nothing happens 
here is a cut and paste from the console

ray@kubuntu:~$ sudo kwrite /boot/grub/menu.lst
ray@kubuntu:~$ su kwrite /boot/grub/menu.lst
Unknown id: kwrite
ray@kubuntu:~$ kwrite /boot/grub/menu.lst

the last one opens the menu.lst in kwrite but I am unable to save my changes.

I believe there is something wrong with the sudo subsystem 
how can I repair it.

---

### Post by aysiu on 2005-11-14
Why did you boot into recovery mode?
Can you also try this? ```
sudo nano /boot/grub/menu.lst
```

---

### Post by Marcussen on 2005-11-16
OK this is a cut and paste from console
ray@kubuntu:~$ sudo nano /boot/grub/menu.lst 
Password:
nothing happens

I then tried

ray@kubuntu:~$ su
Password:
root@kubuntu:/home/ray# nano /boot/grub/menu.lst

could not figure out how to edit using nano

tried
root@kubuntu:/home/ray# kwrite /boot/grub/menu.lstXlib:
connection to ":0.0" refused by serverXlib: No protocol pecifiedray@kubuntu:~$

How do I change so Kwrite is default text editor

---

### Post by aysiu on 2005-11-16
[QUOTE=Marcussen]
Nothing, what should happen?[/QUOTE] This is what should happen. And even though I've "prettified" my terminal, you shouldn't need X (a graphical interface) to be able to use Nano (unlike Gedit and KWrite, which both need a graphical environment to operate).

---

### Post by Marcussen on 2005-11-16
OK thanks I figured out the nano editor, boot order fixed.
sodo still don't work I have to log in as su to change anything.

---

### Post by awalesminfo on 2006-03-18
hi am using the kubuntu 5.10 and on my comp sudo is working fine , but i faced same problem on another machine , solution for that is su to root
then on terminal type visudo then it wil open /etc/sudoers 
then edit as follows it should work .best of luck ,if u want take backup of orig. file ;) 



# /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
#

# Host alias specification

# User alias specification

# Cmnd alias specification

# Defaults

Defaults        !lecture,tty_tickets,!fqdn

# User privilege specification
root    ALL=(ALL) ALL
\\:D/ USRNAME ALL=(ALL)ALL \\:D/ 
# Members of the admin group may gain root privileges
%admin  ALL=(ALL) ALL

---

