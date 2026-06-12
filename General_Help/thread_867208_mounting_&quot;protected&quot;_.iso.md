---
title: "mounting &quot;protected&quot; .iso"
date: 2008-07-22
forum: General Help
---

### Post by penetrarthur on 2008-07-22
Hello!

I switched to ubuntu on my laptop, but recently I have spotted a problem. There is a program i was using on windows - a map of my country. The problem is that this map is available only on windows of course. When i tried to install the program after mounting the .iso on ubuntu, it came with an error from the program: smthing like "use the original cd". When i was on windows i was using daemon tools to install it. i am quite sure that wine will install and run this program, so the only problem i have is to mount "protected" image. 

Thanks in advance.

---

### Post by bodhi.zazen on 2008-07-22
Not sure what you are trying to do , but you realize you can not run windows applications on Linux ?

You could try your application with wine ...

You can mount your iso with :

```
sudo mkdir /media/iso
sudo mount -o loop -t iso9660 /path/to/file.iso /media/iso
```

---

### Post by penetrarthur on 2008-07-23
when i mount the iso and try to install it using wine the installer says that "you have to use original cd", which is normal, because it is protected. what i need is a daemon tools alternative for linux. daemon tools allows to install protected iso's.

---

