---
title: "Hey need help with administration stuff"
date: 2009-09-30
forum: Installation &amp; Upgrades
---

### Post by badbran on 2009-09-30
ok so heres the deal i got ubuntu about a month ago and everything was going fine but the more i use this OS the more i discover i dont understand it :confused: so more specifically i have started making a website using dreamweaver in the last week or so. i wanted to get additional fonts so i downloaded the true font and tried to look up instructions on how to install them but none of them would work because i dont have permission. this computer is in my room so i am the only one who ever uses it. what i dont understand is why i do not have access to everything. i tried using terminal a little but am not very familiar with it yet. any advice on how to change my priveliges so i can actually access what i want or even just how to install these fonts would be greatly appreciated. thanks for your time.

---

### Post by earthpigg on 2009-09-30
hi,

you do have access to everything, you just need to invoke that authority. skim this, if you like: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

one way to do it is to preface terminal commands with 'sudo'.

ie: if a Debian or Distribution-neutral guide has this....

> type the following command:

```
# apt-get install moo
```

then you actually need to type 

```
***_sudo_*** apt-get install moo
```

the # above is telling you 'from a root shell'. instead of actually using a root shell, the Ubuntu community encourages users to use 'sudo'.

ubuntu-specific guides will usually include that in the directions. your best pet is to try to use ubuntu-specific documentation to avoid all ambiguity.

can you link us to the guides you are having trouble following? we can either clarify it, "Ubuntu-ize" the directions, or point you to Ubuntu documentation intended to accomplish the same task(s).

---

### Post by earthpigg on 2009-09-30
when using ubuntu, here is the order i generally pursue documentation:

1) ubuntu-specific documentation is best
2) debian-specific documentation will do
3) the arch linux and gentoo linux wikis are also usable for certain tasks, once you get used to the process of "Ubuntu-izing" the directions
4) all else

---

### Post by oldos2er on 2009-09-30
[https://wiki.ubuntu.com/Fonts](https://wiki.ubuntu.com/Fonts)

---

### Post by badbran on 2009-09-30
This is the web page i was trying to follow. thanks for all the replies it really helps.:)
[http://linuxhelp.blogspot.com/2005/12/adding-windows-fonts-in-linux.html](http://linuxhelp.blogspot.com/2005/12/adding-windows-fonts-in-linux.html)

---

### Post by badbran on 2009-09-30
also i thought i might add that this is the site i am trying to download the fonts from
[http://www.1001freefonts.com/graffiti-fonts.php](http://www.1001freefonts.com/graffiti-fonts.php)
and more specifically i was going for the slammertag font thanks so much for helping

---

### Post by earthpigg on 2009-09-30
looking at those directions,

try running this. it will open a root terminal.

```
sudo su
```

from there, you can launch apps and they will be run as root:

```
nautilus
```

***be warned*** that a single mis-click or typo as root can destroy your system, wipe all data, etc. Ubuntu assumes a root user is incapable of error and knows exactly what he is doing. if this is not the case, don't execute the command or click the mouse.

go back and read that paragraph over again, please.

edit: the link above, [https://wiki.ubuntu.com/Fonts](https://wiki.ubuntu.com/Fonts) , is probably your best bet, though.

---

### Post by badbran on 2009-09-30
k thanks so much i have actually figured it out now and am happily installing fonts. thanks for all your help. :D

---

