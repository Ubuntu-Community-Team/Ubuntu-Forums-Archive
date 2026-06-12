---
title: "How do you uninstall virtualbox?"
date: 2009-02-20
forum: Installation &amp; Upgrades
---

### Post by jeffdp78 on 2009-02-20
Hi there!

I installed _virtualbox-2.1_2.1.2-41885_Ubuntu_hardy_i386.deb_ simply by double-clicking it. (because of gdebi package installer, ...I guess).

not the "_dpkg -i .deb_" way


And found out, recently, a new version came out (virtualbox-2.1_2.1.4-42893_Ubuntu_hardy_i386.deb). 

I don't want to mess up my system so how do I properly uninstall it using terminal?


jeff@jeff-desktop:~$ sudo dpkg -r virtualbox
[sudo] password for jeff: 
dpkg - warning: ignoring request to remove virtualbox which isn't installed.
jeff@jeff-desktop:~$ 


Thanks in advance!



----------
Ubuntu/8.04 (hardy)
Intel Pentium 4 HT 2.80Ghz
725.1 MB

---

### Post by Partyboi2 on 2009-02-20
You can remove virtualbox with
```
sudo apt-get remove package
``` change package to actually package name.
You can check the correct name of the package by
```
dpkg -l |more
```

---

### Post by tombott on 2009-02-20
```
sudo apt-get remove virtualbox-2.1
```

Or if that doesn't work run the following command:

```
sudo dpkg --get-selections > ~/installed-software.log
```

Open the file
```
gedit installed-software.log
```

Scroll down to V and find what the VirtualBox package you have installed is called then do another
```
sudo apt-get remove
```
with the correct package name.

You could also try pressing TAB after sudo apt-get remove Virtual
This will lsit all packages installed starting with Virtual.
I love the TAB auto complete!

---

### Post by jeffdp78 on 2009-02-20
Hey that was quick! sudo apt-get remove virtualbox-2.1 works!


Now I learned more terminal commands

i.e.


dpkg -l |more


sudo dpkg --get-selections > ~/installed-software.log
gedit installed-software.log


Thanks to you both! You guys are great! :KS

---

### Post by konqueror7 on 2009-02-20
why not just add it to your sources.lst?
add it to your /etc/apt/sources/lst...
```
deb http://download.virtualbox.org/virtualbox/debian hardy non-free
```

then,
```
sudo apt-get update
```
```
sudo apt-get upgrade
```

---

### Post by jeffdp78 on 2009-02-20
another terminal gem for me! I will try that after installing the new version! Thanks! :D

---

### Post by tombott on 2009-02-20
> **jeffdp78 said:**
> Hey that was quick! sudo apt-get remove virtualbox-2.1 works!


Now I learned more terminal commands

i.e.


dpkg -l |more


sudo dpkg --get-selections > ~/installed-software.log
gedit installed-software.log


Thanks to you both! You guys are great! :KS

Glad you got it sorted, I've learned loads from these forums.
Always nice to pass it on!

---

