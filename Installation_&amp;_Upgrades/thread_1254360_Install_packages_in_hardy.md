---
title: "Install packages in hardy"
date: 2009-08-31
forum: Installation &amp; Upgrades
---

### Post by navaneethan on 2009-08-31
I need to install somepackages like erlang,vlc,dragon,etc...
but as usual i use the command apt-get install package_name
unfortunately i can't able to get
it shows "the conflict problem ,for install this you have to remove some of the packages in your system"
synaptic too...
what i have to do?

now i also can't able to upgrade my ubuntu also

how to remove the broken dependecies? what is the reason?

[http://ubuntuforums.org/images/smilies/guitar.gif](http://ubuntuforums.org/images/smilies/guitar.gif)

---

### Post by Partyboi2 on 2009-08-31
Hi, can you post the outputs to when you try install something?

---

### Post by navaneethan on 2009-08-31
> **Partyboi2 said:**
> Hi, can you post the outputs to when you try install something?

this is the output when i m trying to install any package::

> Cannot install 'vlc'

This application conflicts with other installed software. To install 'vlc' the conflicting software must be removed first.

Switch to the 'synaptic' package manager to resolve this conflict.


---

### Post by Partyboi2 on 2009-08-31
Open a terminal and try
```
sudo apt-get -f install 
```

---

### Post by raymondh on 2009-08-31
Or you can use synaptic to mark/unmark packages and install.  Worth a try, either way (-f install or synpatic)

---

### Post by navaneethan on 2009-09-01
> **raymondhenson said:**
> Or you can use synaptic to mark/unmark packages and install.  Worth a try, either way (-f install or synpatic)

I want to install erlang in my hardy,but i have a problem to install it
what i have to do?
what is the problem with it?

root@navtux-desktop:~# sudo apt-get install erlang
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package erlang

---

### Post by oldos2er on 2009-09-01
> **navaneethan said:**
> I want to install erlang in my hardy,but i have a problem to install it
what i have to do?
what is the problem with it?

root@navtux-desktop:~# sudo apt-get install erlang
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package erlang

 If you're logged in as root, you don't need to use sudo. 

 Check System, Administration, Software Sources, and make sure the universe repository is enabled.

---

### Post by raymondh on 2009-09-01
> **oldos2er said:**
> 
 check system, administration, software sources, and make sure the universe repository is enabled.

+1

---

