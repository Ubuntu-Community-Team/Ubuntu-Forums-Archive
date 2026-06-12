---
title: "update error"
date: 2008-09-22
forum: General Help
---

### Post by Gdschaf on 2008-09-22
after migrating ubuntu to a new hard drive and working out MOST of the kinks (thank u great ubuntu community) this is the only one that remains (that i know of)
[IMG]http://i113.photobucket.com/albums/n229/ghalodog/error.png[/IMG]
this is weird does ne one know whats wrong here?

---

### Post by ajmorris on 2008-09-23
hi there,
try running ```
sudo dpkg-reconfigure -a
```

Also, what are the permissions on your /boot directory? (ls -l /)

AJ

---

### Post by Gdschaf on 2008-09-24
i have no idea...
and what u told me to run is pretty overwhelming... help with that?

---

### Post by wfp on 2008-09-24
just open a terminal and copy and paste command in terminal  sudo dpkg-reconfigure -a

---

### Post by Shazaam on 2008-09-24
Go to Applications>Accessories>Terminal. When it opens copy/paste (or type it in) this code...
```
sudo dpkg --configure -a
```
Sudo gives you temporary admin rights, the rest of the code means you are telling the program "dpkg" to configure unconfigured apps (with the -a option/argument). You will be asked for your user (login) password, go ahead and enter it. As a security feature whenever you enter your password in terminal you won't see anything printed out. Hit enter. You may or may not get any feedback from the command.
If you enter this in terminal later....
```
ls -l /
```
it will print out the permissions for the / directory. This is mine for the /boot directory...
```
drwxr-xr-x
```

---

### Post by Gdschaf on 2008-10-06
yeah i got the whole terminal thing im not that new at this, its the this that RUNS that is overwhelming

---

