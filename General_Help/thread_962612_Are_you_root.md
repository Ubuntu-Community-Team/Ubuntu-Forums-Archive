---
title: "Are you root?"
date: 2008-10-29
forum: General Help
---

### Post by Jayhawker on 2008-10-29
What's the meaning of "are you root?" I read on Terminal when something is denied to go on?

---

### Post by Idefix82 on 2008-10-29
It means that you tried to do something that required administrator rights. Ubuntu doesn't grant them to you by default. Instead, when you need to run a command as admin (superuser or root in Linux language) you precede it with 'sudo'. If you want to start a graphical program with superuser rights you precede the command as 'gksudo'. For example
```
gksudo nautilus
```
will open the file browser with superuser rights so you can change the contents of the hard drive and not just of your home directory.
Or to copy a file (in this example menu.lst) you do
```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.bac
```

This prevents viruses from doing damage since they don't know your password and thus can't execute any command which could potentially harm your system (apart from deleting your home directory).

---

### Post by Wayne_V on 2008-10-29
"root" is the system administrator user name.  If you are running a command that requires root access you must do it via sudo (e.g. # sudo reboot).  You can also do "sudo -s" to switch yourself to root and then do "exit" or "^d" to switch back to your normal user.

---

### Post by oldos2er on 2008-10-29
> **Jayhawker said:**
> What's the meaning of "are you root?" I read on Terminal when something is denied to go on?

 You're trying to run a program that requires admin privileges. Use "sudo" for CLI programs or "gksu" for graphical ones ("kdesu" if you're running KDE).

 See [http://psychocats.net/ubuntu/permissions](http://psychocats.net/ubuntu/permissions)

---

### Post by Jayhawker on 2008-10-29
> **Idefix82 said:**
> It means that you tried to do something that required administrator rights. Ubuntu doesn't grant them to you by default. Instead, when you need to run a command as admin (superuser or root in Linux language) you precede it with 'sudo'. If you want to start a graphical program with superuser rights you precede the command as 'gksudo'. For example
```
gksudo nautilus
```
will open the file browser with superuser rights so you can change the contents of the hard drive and not just of your home directory.
Or to copy a file (in this example menu.lst) you do
```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.bac
```

This prevents viruses from doing damage since they don't know your password and thus can't execute any command which could potentially harm your system (apart from deleting your home directory).

I think it's quite interesting it in order to protect the computer from viruses and attacks. Please, I'm not an expert at all, so would you be so kind as to extent your explanation with some instances in order I quite get the idea? Of course if that doesn't mean a lot of time. 

Thank You

---

### Post by bodhi.zazen on 2008-10-29
[uwiki]RootSudo[/uwiki]

[Ubuntu Security - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=510812")

---

### Post by Idefix82 on 2008-10-29
Basically, every file and folder in Ubuntu has an owner. If you are the owner then you can change the content as much as you like without requesting superuser rights. For example you can do anything that only affects your own home folder without 'sudo'. If on the other hand the files are not owned by you, but either by some other user or by root then you need 'sudo' to change them. This applies to all folders and files outside your home folder. Here are a few examples:
```
cd ~/Documents
rm *.txt~
```
first goes into your Documents folder and then deletes all files which end with 'txt~'. In this context ~ is a sign that gedit appends to backup files. But if you tried to delete files outside your home directory it wouldn't work like that:
```
rm -r /var/cache/apt/archives
```
attempts to delete all temporary files downloaded by Synaptic. It won't let you do it because you are not their owner. Instead, this would work:
```
sudo rm -r /var/cache/apt/archives
```

Another example: if you want to open a file with gedit you can just do
```
gedit /boot/grub/menu.lst
```
but if you then try to save it, gedit will refuse to do so. If you want to change it's content then you need to open it as superuser:
```
gksudo gedit /boot/grub/menu.lst
```
Now you can change it and save the changes.

DISCLAIMER: These were just examples. Don't do any of it, unless you know what you are doing.

---

### Post by Jayhawker on 2008-10-29
> **bodhi.zazen said:**
> [uwiki]RootSudo[/uwiki]

[Ubuntu Security - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=510812")


Really grateful.

---

### Post by Jayhawker on 2008-10-29
> **Idefix82 said:**
> Basically, every file and folder in Ubuntu has an owner. If you are the owner then you can change the content as much as you like without requesting superuser rights. For example you can do anything that only affects your own home folder without 'sudo'. If on the other hand the files are not owned by you, but either by some other user or by root then you need 'sudo' to change them. This applies to all folders and files outside your home folder. Here are a few examples:
```
cd ~/Documents
rm *.txt~
```
first goes into your Documents folder and then deletes all files which end with 'txt~'. In this context ~ is a sign that gedit appends to backup files. But if you tried to delete files outside your home directory it wouldn't work like that:
```
rm -r /var/cache/apt/archives
```
attempts to delete all temporary files downloaded by Synaptic. It won't let you do it because you are not their owner. Instead, this would work:
```
sudo rm -r /var/cache/apt/archives
```

Another example: if you want to open a file with gedit you can just do
```
gedit /boot/grub/menu.lst
```
but if you then try to save it, gedit will refuse to do so. If you want to change it's content then you need to open it as superuser:
```
gksudo gedit /boot/grub/menu.lst
```
Now you can change it and save the changes.

DISCLAIMER: These were just examples. Don't do any of it, unless you know what you are doing.

Thank You very much; a useful information I've have to practice.

---

### Post by pluckypigeon on 2008-10-29
If you want to use root without typing sudo or gksudo before then type 

```
su
```

this will put you in root prompt

you need to set the root password before hand though 
System >Administration > Users and Groups

---

### Post by the8thstar on 2008-10-29
No, I'm not. I'm the8thstar, not root. You must have mistaken me for someone else with different privileges.

---

### Post by bodhi.zazen on 2008-10-29
> **pluckypigeon said:**
> If you want to use root without typing sudo or gksudo before then type 

```
su
```this will put you in root prompt

you need to set the root password before hand though 
System >Administration > Users and Groups

This is not how Ubuntu works and setting a root password is not advised.

If you need a root terminal use:

```
sudo -i
```

See the link I gave earlier on Root/sudo ;)

---

