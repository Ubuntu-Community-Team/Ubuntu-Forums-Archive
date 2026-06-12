---
title: "root"
date: 2006-01-30
forum: Installation &amp; Upgrades
---

### Post by iAlta on 2006-01-30
Was planning on compieling a program.
But the frst problem I encounterd was I don't knw how to logon as root, can anyone help me with this?

---

### Post by Jakanden on 2006-01-30
[http://easylinux.info/wiki/Ubuntu#How_to_allow_root_user_to_login_into_GNOME](http://easylinux.info/wiki/Ubuntu#How_to_allow_root_user_to_login_into_GNOME)

Worked for me =)

---

### Post by Ysanne on 2006-01-30
Hi,
to compile a program, you don't necessarily have to be root. In fact, usually compiling a program is best done as a normal user, and the installation is the step where you may need to be root.
That said, the root account isn't activated by default in ubuntu, i.e. the password field is blank so you can't log in. So you have to change the root password:
```
sudo passwd root

```
This will prompt you for your user password (so that the "sudo" thing is done), and then it will ask you to specify the new root passwort.
After this is done, you can become root with:
```
su
```
or
```
su - root
```

---

### Post by mcduck on 2006-01-30
You don't need to set root password. Most people don't really ever need root account on Ubuntu. You should use sudo instead. (so, every time you enter a command that would need you to be root, you write sudo in front of the command, and then enter your own password.)

So, normal commands needed for compiling are:

./configure
make
sudo make install

By the way, you may want to install checkinstall (sudo apt-get install checkinstall), and use that instead of 'make install'. Checkinstall will create a .deb package of your program and install that. This way compiled programs will show in Synaptic, and you can also easily remove them.

./configure
make
sudo checkinstall

You should read this about root account in Ubuntu: [https://wiki.ubuntu.com/RootSudo?highlight=%28rootsudo%29]("https://wiki.ubuntu.com/RootSudo?highlight=%28rootsudo%29")

edit: if you don't want to type 'sudo every time, you can just use 'sudo su -', but remember to 'exit' when you are ready. And if you want to use graphical file manager as root, 'sudo nautilus' will open you nautilus file manager as root.

---

### Post by iAlta on 2006-02-01
Thanks, all of you. This really helped.\\:D/

---

