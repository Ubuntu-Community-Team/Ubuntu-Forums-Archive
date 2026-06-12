---
title: "Problem with repository after shutdown"
date: 2008-11-08
forum: General Help
---

### Post by Quarg on 2008-11-08
hello all, and thank you for any help.
I just installed ubuntu 8.10 a few days ago on a laptop of mine, and was just installing some apps yesterday, and left the computer alone for a while. it hibernated in the middle of a download, and the wireless card, of course, doesn't work. so I told the package manager to just install what it already had, and it started to, but hung up. I rebooted, and everything was fine, except for the package manager. when i start it up, i get 'An error has occured' message, with the following text:

 E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

I close the message, and it closes the package manager. 

I ran the command in the terminal, and it just gave me options on what to do with the command, it didn't fix the problem. does anyone know how to fix this?

---

### Post by lswest on 2008-11-08
making sure, you typed ```
sudo dpkg --configure -a
``` into the terminal?

---

### Post by Quarg on 2008-11-08
thats not the problem i ran it as root

---

### Post by lswest on 2008-11-08
I meant make sure you didn't typo it, if you did it would explain why it was displaying the help information.

Also, if that doesn't work try ```
sudo apt-get install -f
```

---

### Post by Quarg on 2008-11-08
It gives me the same error: 
graphicsfreek@ubuntu:~$ sudo apt-get install -f
[sudo] password for graphicsfreek: 
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
graphicsfreek@ubuntu:~$ 
graphicsfreek@ubuntu:~$

---

### Post by Quarg on 2008-11-08
now when I run dpkg --configure -a it gives me an error: 

dpkg: parse error, in file `/var/lib/dpkg/updates/0008' near line 1:
 newline in field name `#padding'

---

### Post by lswest on 2008-11-09
Make sure you've rebooted your computer (to empty the temp folder) and try the command again, otherwise try to run ```
sudo apt-get update && sudo apt-get upgrade
``` to see if you can resolve that error in the install file.

---

