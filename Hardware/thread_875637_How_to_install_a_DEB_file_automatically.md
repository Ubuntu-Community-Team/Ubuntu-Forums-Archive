---
title: "How to install a DEB file automatically?"
date: 2008-07-31
forum: Hardware
---

### Post by owen_cao on 2008-07-31
When I insert a U-disk, I want to install a DEB file automatically. During this procedure, how to resolve the problem of inputting super user's password. 

thanks

---

### Post by imronak on 2008-07-31
If the file is file-name.deb, try double clicking it, a package manager should start and lead to install. 

You need to put in the root password to install packages. Its not a problem :)

---

### Post by Vishal Agarwal on 2008-07-31
> **owen_cao said:**
> how to resolve the problem of inputting super user's password.

The root password is for full security purpose only. Once u are being asked for super user password, u have to think more carefully, what u are going to do.

---

### Post by owen_cao on 2008-07-31
On the auto installation scenario, there is no prompt for inputting password. It is because a new terminal will be open to run the installation. How to go on with it?
thanks

---

### Post by forger on 2008-07-31
Correct, the super user is not a "problem", it's a wisely-used feature that prevents other people from installing bad software on other computers :)

About autorun, this might help:
[http://gnomejournal.org/article/6/cddvd-creation-with-nautilus](http://gnomejournal.org/article/6/cddvd-creation-with-nautilus)
> 
Here is another little tip. To create an autorun script, create a plain text file named &#8220;autorun&#8221;, something like this:

#!/bin/sh
dir=$(echo $0 |sed 's/autorun//')
cd $dir
fullpath=$(pwd)
exec /usr/bin/nautilus $fullpath

To make it executable, right click on the autorun script and set it to executable.

Keep in mind that:
1) the user can select to autorun the stuff or not from Nautilus' Edit > Preferences menu.
2) if you want to install it system-wise, you'll need to use that "problematic" user password :D
3) if you want to just run the program as a user, you could extract the deb package somewhere temporarily and execute it for that user only

---

### Post by forger on 2008-07-31
> **owen_cao said:**
> On the auto installation scenario, there is no prompt for inputting password. It is because a new terminal will be open to run the installation. How to go on with it?
thanks

you mean you want a GUI for user password?
```
gksu echo "moo."
```

---

### Post by owen_cao on 2008-08-01
When I insert the U-Disk to make the file autorun.sh run automatically for installing the DEB files,there always is a dialog box to prompt inputting password, but after input it, no actions can be found. So the DEB files can not be installed successfully.
PS: The file autorun.sh can run successfully when I type the command in the terminal.

---

### Post by owen_cao on 2008-08-01
The problem was solved, I missed the "" of the command dpkg -i xxx.deb. Thank you very much. The gksu is very helpful:)

---

