---
title: "Root passwords"
date: 2008-11-15
forum: General Help
---

### Post by aquarianwolf on 2008-11-15
Can anyone help me with root passwords?

I'm currently trying to update Java using terminal.

I've typed in su, it then asks me for root password, I've tried using my login password but it comes up with authentication failure.

Help!:confused:

Please.

---

### Post by Patrick793 on 2008-11-15
In Ubuntu you don't use su, you use sudo instead.

---

### Post by SunnyRabbiera on 2008-11-15
Correct, the root account is disabled in ubuntu.
And you really dont need to install java with the installer you find on java's website.
In Ubuntu we use something called a repository, to use this repository go to system then to administration then click on synaptic package manager.
Of course java is not availible right off the bat, you will have to play around a bit in synaptic to make java appear in the package list.
In synaptic click settings and then select "repositories"
a new window will pop up and from there you can enable extra repositories by clicking on the boxes in tabs 1 and 2, click all of them off except the ones that say source code.
after that you just refresh, search for sun-java6-jre and installation should be easy from there.
its just clicking on the box next to the app you want to install and mark it for installation and then hit apply each time :D

---

### Post by taurus on 2008-11-15
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

[https://help.ubuntu.com/community/InstallingSoftware](https://help.ubuntu.com/community/InstallingSoftware)

---

