---
title: "dpkg was interrupted"
date: 2008-08-19
forum: General Help
---

### Post by starving030 on 2008-08-19
This is what I got. I'm just tryin to watch videos on the internet.

[COLOR="Red"]ts@dt:~$ sudo apt-get install ubuntu-restricted-extras
[sudo] password for ts: 
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
ts@dt:~$ sudo dpkg --configure -a'
> [/COLOR]

running Ubuntu 8.04

---

### Post by aysiu on 2008-08-19
> **starving030 said:**
> This is what I got. I'm just tryin to watch videos on the internet.

[COLOR="Red"]ts@dt:~$ sudo apt-get install ubuntu-restricted-extras
[sudo] password for ts: 
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
ts@dt:~$ sudo dpkg --configure -a'
> [/COLOR]

running Ubuntu 8.04
Press Control-C.

Then, try pasting this into the terminal: ```
sudo dpkg --configure -a
``` Leave out the '

---

### Post by starving030 on 2008-08-19
Cool. That seemed to get it going. now it's stuck like this.

[[IMG]http://host.photogalaxy.net/thumbs/66180_Screenshot.png[/IMG]](http://host.photogalaxy.net/viewer.php?id=66180_Screenshot.png)

---

### Post by Elfy on 2008-08-19
Use tab to get to the ok and enter

---

### Post by aysiu on 2008-08-19
> **starving030 said:**
> Cool. That seemed to get it going. now it's stuck like this.

[[IMG]http://host.photogalaxy.net/thumbs/66180_Screenshot.png[/IMG]](http://host.photogalaxy.net/viewer.php?id=66180_Screenshot.png)
Press **Tab** until the *<OK>* is highlighted in [color=red]red[/color] and then hit **Enter**

---

