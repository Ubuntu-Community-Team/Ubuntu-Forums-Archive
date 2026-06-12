---
title: "How to open the samba server?"
date: 2008-08-18
forum: General Help
---

### Post by farmdve on 2008-08-18
My ISP has a samba server(or that was its name) the link was \\1.1.1.2 but in ubuntu it does not open but in windows it does
How to open that server?

---

### Post by prince_niceguy on 2008-08-19
smb://1.1.1.2 should open it.

hope you have samba installed from synaptic.

---

### Post by farmdve on 2008-08-20
Doesnt work

P.S
The samba server is made so that when u open a movie or anything infact u can watch it witout having to download it or buffer as i fit was on ur pc

---

### Post by prince_niceguy on 2008-08-20
smb: should work. I have samba server setup on my desktop and i access it through my laptop and am able to do so. 

run the following command to make sure you have required files

```
sudo aptitude install smb-fs samba
```

if it still not working after this then we can try mounting your samba share to one of the directory of your computer something like creating a mapped drives in windows world. let me know if you want to do that.

---

### Post by farmdve on 2008-08-20
Now "smb://1.1.1.2" says no such file or directory :(

---

### Post by prince_niceguy on 2008-08-20
lets see if the mounting is working. if yes then you can make it permanenent

create a directory where you want to mount the folder on the shared drive.

Open a terminal and do the following

```

cd /
sudo mkdir shared

```

Now let us mount the shared folder. 

```
sudo mount -t cifs -o username=xxx,password=xxx,file_mode=0777,dir_mode=0777,iocharset=utf8 //1.1.1.2/[the_Shared_folder] /shared
```

replace xxx with your user id and password if any. if not, then delete them from the command.

replace [the_Shared_folder] with the folder shared on your drive. 

Once done, go to /shared. it should show the content of your shared drive.

---

### Post by prince_niceguy on 2008-08-20
Also, one more question. Is the shared server a linux/unix server or windows server?

---

### Post by farmdve on 2008-08-20
Its not mine its my ISP sort of like an FTP but the name was Samba Server and i think that its a Unix one or so my terminal said

---

