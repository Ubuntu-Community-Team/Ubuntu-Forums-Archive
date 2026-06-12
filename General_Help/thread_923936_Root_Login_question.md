---
title: "Root Login question"
date: 2008-09-18
forum: General Help
---

### Post by GSDUDE on 2008-09-18
I was wondering if there's something special about logging in as root.

The reason I ask this is I remember with Fedora or Redhat I was asked to set a root password at installation.

During the install of Ubuntu I'm only asked to create a user account and password.

When I go to the user manager I see the root account.

When I log in and try the username root and put in the password I created for the username it says password is invalid.

Also if I try to get into I think it was /usr/bin/something about gnome desktop and setting the permission level to ....                  thinking it was 777 for root ...


This is to make it so people can not make changes to the desktop.

I have the email with the link at work.

But I can't change that with out being root.

Any tips on what I'm doing wrong here??


Thanks
Doug

---

### Post by jp73107 on 2008-09-18
logging in as root is dangerous. if you need to do things as root, use sudo in the terminal. if you need to run a graphical application as root, hit alt+f2 and type gksu nameofapplication (i.e. nautilus, gksu nautilus)

---

### Post by iaculallad on 2008-09-18
By default, the ROOT account is disabled in Ubuntu. And to have the 'root-like' privilege, you have to issue commands such as:

> sudo,gksudo,gksu,kdesu

```
sudo vi /etc/fstab
gksudo gedit /etc/fstab
kdesu kate /etc/fstab

```
or

> sudo -i, sudo su

```
sudo -i
sudo su

```
and using the commands above, you have to input your own password.

---

### Post by Iowan on 2008-09-18
Perhaps [this]("https://help.ubuntu.com/community/RootSudo") link can help explain it.

---

### Post by GSDUDE on 2008-09-18
Okay, that makes sense I guess. So, this is what sort of led me to this question. I need to make the desktop non changable to users. It's sort of a work place PC and I don't need the blithering twits to set some porn picture as a desktop...
No matter how cute she is somebody will complain..

I got these directions and I'm not familiar enought to do with a command line.

change mode of /usr/bin/gnome-appearance-properties fromi 755 to 744, so only root can akses this file to change the appearance of desktop

I'll now also search around in here on how to change permission levels.

Thanks

---

### Post by GSDUDE on 2008-09-18
Will this do it? chmod 744 /usr/bin/gnome-appearance-properties

---

### Post by aysiu on 2008-09-18
Maybe you want something like Pessulus?
[http://www.gnomefiles.org/app.php?soft_id=1082](http://www.gnomefiles.org/app.php?soft_id=1082)

---

