---
title: "Errors Attempting to log in to ubuntu"
date: 2005-11-28
forum: General Help
---

### Post by asad112 on 2005-11-28
First error after I enter my login information:

> Your home directory is listed as:
'/home/asad'
but it does not appear to exist.  Do you want to log in with the / (root) directory as your home directory?

It is unlikely anything will work unless you use a failsafe session.
"No" or "Yes"

When you select no, it takes your back to re-logon. When you press yes, it give you this error:

> Your $HOME/.dmrc file has incorrect permissions and is being ignored.  This prevens the default session and language from being saved.  File should be owned by user and have 644 permissions.
"OK"

And then this error comes up:
> Your session only lasted less than 10 seconds.  If you have not loged out yourself, this could mean that there is some installation problem or that you may be out of diskspace.  Try logging in with one of the failsafe sessions to see if you can fix this problem.

*Selects *View details (~/.xsession-errors file)*

/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp

/etc/gdm/PreSession/Default: running: /usr/bin/X11/sessreg -a -w    /car/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h " " -l ":0" "asad"

/etc/gdm/Xsession: Beginning session setup. . .

(gnome-session:8215): libgnomevfs-WARNING **: Unable to create ~/.gnome 2 directory: No such file or directory

Could not create per-user gnome configuration directory `/home/sad/.gnome2/'" No such file or directory

"OK" 

You select ok, and it takes you back to the log on, can anyone help me? :)

---

### Post by asad112 on 2005-11-28
*bump*

---

### Post by oldlucky on 2005-11-28
Hi you could try this , log in in failsafe session then

sudo chown (Yourname) .ICEauthority

this has worked before for me i hope it helps you.

Cheers

---

### Post by jj26 on 2005-11-29
Hi I had this problem too... I think i got it after trying to solve the $HOME/.dmrc problem on my own. This is what I did, though I'm sure someone who has used Linux more than the two days I have can give you a much better answer. To fix both this and the other problem I "chown"ed all of these files and folders under my name and "chmod"ed them to 777. Mind you this leaves your computer waaaaaay open and is prolly a bad idea. I'm gonna scale that back when i get more of a chance. 

starting from the base directory (just do "cd .." until it stops changing) I chowned and chmoded:

v("chmod 777 ~" and "chown yourname ~" is the style for all of these)v
~
home
home/yourname
home/yourname/.dmrc
home/yourname/.ICEauthority

i also edited a line in /etc/gdm/gdm.conf
it defines the variable RelaxPermissions
I changed the value from 0 to 2. Prolly another not-so-secure adjustment... 

ok, the fun part... If you have the same problem as me, you can't get into any form of gnome, not even with the failsafe. when the grub screen comes on at the beginning of the bootup, select recovery mode for ubuntu. This boots up outside of gnome, though you'll need to know your root password. Once you sign in, do the chown and chmod stuff listed above. To edit gdm.conf, type "sensible-editor /etc/gdm/gdm.conf" change the line and hit Ctrl+o to save it.

Reboot and good luck!


JJ out

---

