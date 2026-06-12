---
title: "Wierd samba and gedit problem O_O"
date: 2005-11-28
forum: General Help
---

### Post by sapo on 2005-11-28
i ve installed Ubuntu at my job, and here we have a file server runing fedora and samba, everyone have write permission on the samba server, there is no username/password.

The wierd thing is:

I can mount and read the files, vi, and other text editors can write in the server.. but gedit doesnt write on it.. it says "permission denied".

here are my configs, i tried a lot of stuff, nothing seens to work:

My fstab:
```

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
//LINUX/trab	/home/fabio/trab	smbfs	username=nobody,password=,uid=500,gid=100,umask=0002	0	0

```

here the server share smb config:

```
[trab]
      comment =
      path = /home/trab
      browseable = yes
      public = yes
      writable = yes
      write list =
      valid users =
      inherit permissions = yes
      createmask = 0777
      directorymask = 0777
      printable = no
      invalid users = root

```

Please, any help is welcome, i dont know what more to do.. i need to make it work any any cost :(

thanx in advance

---

### Post by kosmic on 2005-11-28
just a hint try to start gedit as a superuser (root) and see if you can write to the samba share

---

### Post by jaa1180 on 2005-11-28
[QUOTE=kosmic]just a hint try to start gedit as a superuser (root) and see if you can write to the samba share[/QUOTE]


What I would suggest. How are you accessing the files? 
As a user and doing a gedit to the file? 

How are you accessing the files using VI?

---

### Post by sapo on 2005-11-28
[QUOTE=jaa1180]What I would suggest. How are you accessing the files? 
As a user and doing a gedit to the file? 

How are you accessing the files using VI?[/QUOTE]
i open the gedit, browse the mounted dir and open the file.. and with vi i acess it with the terminal.

But if i use that mousepad that came with xfce it opens and saves the file normally O_O

---

### Post by jaa1180 on 2005-11-28
Ok, nothing special then. 
Hmmm... did opening with root work?

---

### Post by sapo on 2005-11-28
[QUOTE=jaa1180]Ok, nothing special then. 
Hmmm... did opening with root work?[/QUOTE]
i didnt try yet, cause that box is at my work.. i ll try tomorrow morning.

---

### Post by sapo on 2005-11-29
I tried with gksudo gedit, and it worked, with sudo i can write in the samba folder, how can i fix it so i can write on it without sudo?

thanx

---

### Post by kosmic on 2005-11-29
Now I don't know because if the permisions are correct and VI, nano etc can write to the samba share without root acess...the only thing i can say is for you to submit a bug about gedit and writing in samba partitions :(

---

