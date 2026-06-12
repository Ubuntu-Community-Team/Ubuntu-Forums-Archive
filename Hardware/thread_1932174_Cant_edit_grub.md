---
title: "Cant edit grub"
date: 2012-02-27
forum: Hardware
---

### Post by Kardel on 2012-02-27
Hi guys i am new to Linux but decided to install it on my Toshiba satellite z830/00g. I am trying to edit the grub file located in /etc/default/grub in order to make changes suggested at [http://www.linlap.com/wiki/toshiba+portege+z830-10f](http://www.linlap.com/wiki/toshiba+portege+z830-10f). The problem I am having is I can not save the changes to the file as it is read only. Any help would be greatly appreciated.

---

### Post by ahallubuntu on 2012-02-27
You need to have administrator privileges to edit files like this in Linux.  Fortunately, it's pretty easy.

First, open a terminal window.  Search for "terminal" and then double-click to open.

In the terminal window, type

sudo gedit /etc/default/grub

If you put the word "sudo" in front of any command like this, you'll get administrative privileges to edit it.  You'll have to give your admin password to get the privileges.

---

### Post by Kardel on 2012-02-27
Thanks ahallubuntu that worked great.[URL="http://ubuntuforums.org/member.php?u=32392"]
[/URL]

---

### Post by Bucky Ball on 2012-02-27
sudo = super user do!

Please mark thread as solved from Thread Tools to help others. ;)

---

