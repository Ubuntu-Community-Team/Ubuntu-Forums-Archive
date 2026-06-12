---
title: "permissions help"
date: 2008-09-30
forum: General Help
---

### Post by shcKr- on 2008-09-30
i just installed ubuntu today, and am having problems with permissions.. when i go to edit some files in the text editor, and then save them (i'm following tutorials)
it says:
> 
You do not have the necessary permissions to save the file. Please, check that you typed the location correctly and try again

then when i, right click the file>properties>permissions
it says:
[img]http://i34.tinypic.com/5upniq.jpg[/img]

help :)
thanks

---

### Post by Sycron on 2008-09-30
Open a terminal and type: ```
gksudo nautilus
``` and change the permissions.

[COLOR="Red"]--OR--[/COLOR]

use cd to navigate to the index.html and type ```
sudo chmod 777 index.html
```

---

### Post by porchrat on 2008-09-30
what exactly are you trying to edit?

Another way of doing it is to change ownership to yourself, and you can do that with this command:

```
sudo chown username:username /path/to/file
```

However you don't want to change the user (and group in this case) that a file belongs to if it is something important.  If it just one of your documents under your home directory or something then I suggest you change its ownership anyway.

---

### Post by porchrat on 2008-09-30
also if you want to edit something and you don't have permission you can do this:

```
sudo gedit /path/to/file
```

where "path/to/file" is the pathway to the file you are trying to edit.

that way you don't have to alter the files permissions or ownership at all.  However once again I hope it isn't something important (considering it belongs to root)

---

### Post by Sycron on 2008-09-30
If you're trying to modify some files in paths like /var/www the best solution is with *sudo gedit*.

---

### Post by shcKr- on 2008-09-30
thanks for the quick replies,
its for xampp, some of the config files require editing and i dont have the permissions, thanks for the help! i will have a mess around with it :)

---

### Post by porchrat on 2008-09-30
then you must use this:

```
gksudo gedit /path/to/file
```

you don't want to be messing with its permission and especially not the ownership details as it may affect the functioning of the program.

use gksudo as it is better for graphical commands

---

### Post by Sycron on 2008-09-30
Good luck, and happy coding.

---

### Post by porchrat on 2008-09-30
HAH sycron that is an awesome avatar!:D

---

### Post by oldos2er on 2008-09-30
> **shcKr- said:**
> i just installed ubuntu today, and am having problems with permissions.. when i go to edit some files in the text editor, and then save them (i'm following tutorials)
it says:


then when i, right click the file>properties>permissions
it says:
[img]http://i34.tinypic.com/5upniq.jpg[/img]

help :)
thanks

 Be very careful changing permissions of any file outside of your /home directory, it's easy to break things.

 To edit a text configuration file, in the terminal use the command "gksudo gedit /etc/apt/sources.list", as an example. If you prefer nano, the command would be "sudo nano /etc/apt/sources.list".

---

### Post by Sigshane on 2008-12-30
Here's my question on this: we are supposed to save all of our PHP files to the /opt/lampp/htdocs folder, yeah?

But if you are not logged in as root, or if you don't have an active terminal open as root, you are not allowed to do it, *at least in the default Ubuntu configuration.*

How can I give myself, that is, my user account, read and write permissions on /opt/lampp/htdocs, and the folders within?

Thanks in advance!

Shane

---

