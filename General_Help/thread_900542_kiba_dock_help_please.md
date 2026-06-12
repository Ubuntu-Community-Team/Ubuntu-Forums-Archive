---
title: "kiba dock help please"
date: 2008-08-25
forum: General Help
---

### Post by bipolaric on 2008-08-25
I have downloaded and installed a kiba-dock deb package, but when I click on it nothing happens.  Also, when I tried to remove it in Applications>Add/Remove, it doesn't even register kiba-dock being installed at all. How do I remove it and What has gone wrong ?  Also, is there a .deb package out there that DOES work, as I've heard that this kiba-dock is really cool.

Thanks -Mark

---

### Post by phidia on 2008-08-25
Use dpkg see man dpk to uninstall a .deb package > sudo dpkg -r <packagename>

---

### Post by bipolaric on 2008-08-25
hi, I tried typing sudo dpkg -r <kiba-dock> in the terminal
but it came up with this

bash: syntax error near unexpected token `newline'

---

### Post by starcannon on 2008-08-25
To compile from source, here is a very well put together copy paste guide.

[http://ubuntuforums.org/showthread.php?t=554127](http://ubuntuforums.org/showthread.php?t=554127)

Enjoy

---

### Post by bipolaric on 2008-08-25
hi, the copy paste guide did not work, I think it's because the previous kiba-dock i put on won't un-install, even with the comand U gave me, there was a problem with the copy paste every time I came to make install, and it just said ***stop blah blah blah, sorry I cant be more presice but I just dont know what to do.  I think if I can get rid of the previous version, that did not work, it might copy paste correctly.

Thanks Anyway - Mark :)

---

### Post by starcannon on 2008-08-25
don't put the <> around the package name.

---

### Post by bipolaric on 2008-08-25
have successfully removed previous version of kiba-dock, but I'm still having trouble with the copy/paste guide.  Everything is fine untill I have to type <sudo make install> to which I am given <make: *** No rule to make target 'install'.stop>

what does this mean ?

---

### Post by starcannon on 2008-08-25
means you didn't grab the dependencies.

try this perhaps.
```
sudo apt-get install build-essentials
```
I always forget whether its plural or not, if that don't work, just remove the s from the end of essentials

---

### Post by bipolaric on 2008-08-25
hi, tried that, got this......

Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

Thanks - Mark

---

