---
title: "New to Ubuntu - some questions..."
date: 2005-11-27
forum: General Help
---

### Post by Ted_Smith on 2005-11-27
hI

Just installed Ubuntu for the first time (quite excited) and trying to get used to my new environment. 

I have a few questions though :

1) I can't login as root using the GUI it seems, but I can't shell to command prompt from there either unless I login as a standard user then switch user to root. So how do I login as root from boot up without having to login as a user first? In other words, from the GUI login screen how do I shell out to console?

2) How do I switch to using KDE instead of Gnome? I have installed 'Ubuntu' which appears to be the GNOME version which I didn't realise before. Should I have installed KUbuntu instead? If not, how do I run KDE using Ubuntu? Is GNOME better than KDE?

3) I have enabled access to a slave drive (NTFS filesystem) via 'System' --> 'Administration' --> 'Disks' --> but I can only see it while I am su to root (which seems to expire after a few minutes). But it still says I cannot change the settings because I am not the owner. How do I set the permissions so that my standard 'Ted' user account can access the disk? 

Thanks for your help, and sorry for for being a dummy. 

Ted

---

### Post by Gustav on 2005-11-27
1) I you want to go to the console, just press alt+ctrl+F1 (you can press alt+ctrl+F7 to get back to the GUI)

2) Just install kubuntu-desktop via synaptic or apt

---

### Post by parktownprawn on 2005-11-27
1) You would have to enable the root account. type 
```
sudo passwd root
```
and enter a passwd for root. this may not be wise since it may break some of the gui admin tools. see [https://wiki.ubuntu.com/RootSudo]("https://wiki.ubuntu.com/RootSudo")
for more info

2) to install kde type ```
sudo apt-get install kubuntu-desktop
```

3) check out [https://wiki.ubuntu.com/AutomaticallyMountMSWindowsPartitions]("https://wiki.ubuntu.com/AutomaticallyMountMSWindowsPartitions")

---

### Post by atoponce on 2005-11-27
[QUOTE=Ted_Smith]hI

Just installed Ubuntu for the first time (quite excited) and trying to get used to my new environment. 

I have a few questions though :

1) I can't login as root using the GUI it seems, but I can't shell to command prompt from there either unless I login as a standard user then switch user to root. So how do I login as root from boot up without having to login as a user first? In other words, from the GUI login screen how do I shell out to console?[/quote]

Root is disabled by default, and there is really no need to turn it on.  Rather, Ubuntu makes admin access to the OS through the 'sudo' command.  Also, logging in as root is disabled, but can be enabled from System -> Administration -> Login Screen Setup.  Click the 'Security' tab, and check the box "Allow root to login with GDM".

[QUOTE=Ted_Smith]2) How do I switch to using KDE instead of Gnome? I have installed 'Ubuntu' which appears to be the GNOME version which I didn't realise before. Should I have installed KUbuntu instead? If not, how do I run KDE using Ubuntu? Is GNOME better than KDE?[/quote]

You first need to install KDE.  Pull up a terminal and type:

```
sudo apt-get install kubuntu-desktop
```

After which, just reboot and select 'KDE' from the session menu.

[QUOTE=Ted_Smith]3) I have enabled access to a slave drive (NTFS filesystem) via 'System' --> 'Administration' --> 'Disks' --> but I can only see it while I am su to root (which seems to expire after a few minutes). But it still says I cannot change the settings because I am not the owner. How do I set the permissions so that my standard 'Ted' user account can access the disk?[/quote]

Accessing an NTFS drive as a normal user is not recommended.  At least I wouldn't recommend it anyway.  However, if you would like to change the owner on the directory, pull up a terminal, and type:

```
sudo chown -R ted /media/windows
```

Assuming that /media/windows is the location of your NTFS drive.

---

### Post by Joey French on 2005-11-27
I think the key here is to understand first and foremost that ubuntu uses "sudo" (which means "superuser do") to give limited root access to the user. The developers have tried to make it so that one does not stay root. that is why you are sorta "kicked out" after a period of time.

---

### Post by jliedeka on 2005-11-27
This may be a dumb question, but have you set a root password?  There shouldn't be any need to actually log in as root but if you really want to, it should be do-able.  Assuming you have set a password, I'd poke around the GDM configuation stuff to see if something is excluding root logins.

You can probably install the KDE stuff through Synaptic.  As for which is better, that's very subjective.  I don't find either Gnome or KDE to meet my needs so I added XFCE fo my Ubuntu.  Gnome is fairly user-friendly and powerful but has a really crappy window manager.  KDE has a better window manager but the apps aren't as good and that Arts sound daemon always gives me headaches.

You should be able to edit the options for your NTFS mount in /etc/fstab.  Either add the "user" option or set uid and gid to your user account (usually 1000, the number in "grep yourlogin /etc/passwd")

---

### Post by Ted_Smith on 2005-11-27
Good grief...so many replies in such a small amount of time! You guys rock. Thanks very much.

I have successfully installed KDE (the console installation takes some getting used to, but I kinda like it!) and adjusted my permissions to my NTFS data disk. 

Thanks for actually explaining what 'sudo' actually means - it makes much more sense now. I didn't realise that root was disabled by default. It certainly makes sense just to log in and use that pwoer when you need to. 

Cheers guys...right, now onto sussing out where the firewall is! 

Ted

---

### Post by atoponce on 2005-11-27
'su' does not mean "superuser", but "switch user". This is one of the big misnomers in the UNIX/Linux community. By default, 'su' with no commands assumes you want to "switch user" as root. If an arguement is applied, say 'su john', then you will "switch user" as john.

So, 'sudo' does not mean "superuser do", but "switch user do". A list of users and groups are listed in the sudoers file, and what permissions they are granted. They are accessed through the 'sudo' command. By default, 'sudo' executes commands as root, however, 'sudo', just like 'su' can take user arguments. For example, to edit *index.html* in vi as the "www" user, the command would be:

```
sudo -u www vi index.html
``` 
Of course, the user "www" would have to be listed in the sudoers file, and what permissions he has.

---

### Post by Ted_Smith on 2005-11-27
The sudo chown -R ted /media/windows command executed, but it hasn't worked. I thought it had worked, but then when I went to access the files nothing had changed. So I ran it again, and then realised that  because the files are on an NTFS drive, every file it reads "Read-Only File System" beneath it.  So I think it tries to change the ownership but fails due to it being NTFS. 

Any toher way around this? 

Ted

---

### Post by atoponce on 2005-11-27
[quote=Ted_Smith]The sudo chown -R ted /media/windows command executed, but it hasn't worked. I thought it had worked, but then when I went to access the files nothing had changed. So I ran it again, and then realised that because the files are on an NTFS drive, every file it reads "Read-Only File System" beneath it. So I think it tries to change the ownership but fails due to it being NTFS. 

Any toher way around this? 

Ted[/quote] 
You could download the kernel sources, and enable the ability to write to an NTFS partition, but this is heavily NOT recommended. Linux has very little support writing to NTFS partitions, and doing so could corrupt the partition, and you would lose all your data. Thus, it is turned off in the kernel by default.

I had forgotten that you cannot change the ownership of an NTFS. :oops: I remember trying to do it myself, and had no luck. Other than recompiling the kernel with the ability to read and write to NTFS, I know no other way.

Sorry.

---

