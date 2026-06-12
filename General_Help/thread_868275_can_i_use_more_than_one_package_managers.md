---
title: "can i use more than one package managers?"
date: 2008-07-23
forum: General Help
---

### Post by chriskin on 2008-07-23
i'd like to be able to use more than one packake management applications at the same time
for example i am using the terminal to restore the packages of my previous hardy, and i wanted to know the name of the gnome desktop environment on synaptic package management and i get an error message while oppening the latter, saying that "cannot get exclusive lock"

is there a workaround?

---

### Post by spupy on 2008-07-23
You cannot have two package managers running at the same time. The point of this is to prevent corrupting your packages by handling them with two programs in the same moment.

---

### Post by brian_p on 2008-07-23
> **chriskin said:**
> i'd like to be able to use more than one packake management applications at the same time
for example i am using the terminal to restore the packages of my previous hardy, and i wanted to know the name of the gnome desktop environment on synaptic package management and i get an error message while oppening the latter, saying that "cannot get exclusive lock"

is there a workaround?

```
apt-cache search <regex>
```

or

```
apt-cache show <pkg>
```

---

### Post by bodhi.zazen on 2008-07-23
Boot your old installation, make a list of installed packages, use that list on the new.

First, make the list. Open a terminal and enter these commands:

    ```
dpkg --get-selections | grep -v deinstall > ubuntu-files
```

Now you have got a list of all of your installed debs in a fairly small file. Transfer "ubuntu-files" to the insstallation you want to update (flash drive, email it to yourself, backup partition, etc).

Install Ubuntu on the new system.

Once Ubuntu is up and running, copy your ubuntu-files back into your home directory and do the following:

    sudo apt-get update

    sudo apt-get dist-upgrade

    sudo dpkg --set-selections < ubuntu-files

These commands tell the fresh install of Ubuntu what it needs to be installed. To install the packages .

```
sudo dselect
```

This will open up a dselect session. Type "I" and allow dselect to install of the the packages listed in your ubuntu-files document. When finished, type "Q" and hit the ENTER key to exit dselect.

Alternate : [http://ubuntuforums.org/showthread.php?t=650518](http://ubuntuforums.org/showthread.php?t=650518)

---

### Post by chriskin on 2008-07-24
i knew about the restore trick, i just wanted to know if there was a possibility to have two package managing applications open at the same time

thanks spupy :D

---

