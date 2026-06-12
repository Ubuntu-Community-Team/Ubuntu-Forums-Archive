---
title: "How to mount network drive at boot"
date: 2008-09-12
forum: General Help
---

### Post by theedudenator on 2008-09-12
I have a few directories on my winXP machine I want to mount when I use my laptop(Ubuntu)

How do I do this?

---

### Post by ajmorris on 2008-09-12
hi there,
to mount your samba shares, you can do the following:
```
mount //winserver/share /mnt/mount_point -t smbfs -o username=user,password=pswd -o gid=users,dmask=777,fmask=777,rw
```and you can add a line to /etc/fstab to make it mount on boot:

```
//winserver/share  /mnt/mount_point     smbfs  rw,user,username=user,password=pswd       0       0
```AJ

---

### Post by theedudenator on 2008-09-12
I am not sure how I can edit that file, it will not let me save it.

I am not sure how to change to the directory in the terminal either to use sudo.

For winserver do I need to have my IP address?

---

### Post by cariboo on 2008-09-13
To edit your /etc/fstab press Alt-F2 and enter:

```
gksu gedit /etc/fstab
```

Enter your password when asked then add the entries.

If you can access your windows computer by name, use the name eg:

```
ping windows_computer
```

You don't need the ip address. If you cant access the windows computer by name you can edit your /etc/hosts file to alias a name to the ip address eg:

```
192.168.1.202	minibuntu
```

Where the ip address would be your windows computer's ip address and minibuntu would be your windows computer's name.

jim

---

### Post by fmartinez on 2008-09-13
What I did to reduce network traffic was install autofs and created a sym link from the shared file to a file on the client. I did this because when you add shared files in fstab you always have a link to that file on the network. 
When you use autofs the link isn't established until to attempt to acess that directory. 

It's been working pretty well for me.

---

### Post by theedudenator on 2008-09-13
This is the error that I get

mount: mount point /media/D does not exist


This is the line I am trying to use in terminal

sudo mount //BASEMENT/D /media/D -t smbfs -o username=XXXX,password=XX -o gid=users,dmask=777,fmask=777,rw


I am able to ping BASEMENT with no problems.

---

### Post by ajmorris on 2008-09-18
> **theedudenator said:**
> This is the error that I get

mount: mount point /media/D does not exist


This is the line I am trying to use in terminal

sudo mount //BASEMENT/D /media/D -t smbfs -o username=XXXX,password=XX -o gid=users,dmask=777,fmask=777,rw


I am able to ping BASEMENT with no problems.

make sure you do sudo mkdir /media/D first

AJ

---

### Post by Ateo on 2008-09-19
I suggest using autofs. There is a bug with current Ubuntu (possibly others) in which network drives (during shut down) are unmounted AFTER the network is shut down which causes the system to hang during shutdown until it figures out what it needs to do.

Just do 'apt-get install autofs'. After installed, the file to edit is /etc/auto.master.

Autofs mounts as needed and unmounts drive at specified time (in auto.master).

---

### Post by theedudenator on 2008-09-20
Any suggestion on the parameters for the auto.master file?

---

### Post by idledecz on 2008-09-24
> **theedudenator said:**
> Any suggestion on the parameters for the auto.master file?

I would love to have this information as well. Can't find much in search and I have no idea what I'm looking at in the auto.master file as the format looks very different than //server/share //mount/mount etc etc

Also, is it possible to mount a servers root share as in //192.168.1.100/ but not put in a share name? (Windows XP as server)

---

