---
title: "not working on old Mercury Amd mobo..."
date: 2013-01-10
forum: Hardware
---

### Post by n45w73 on 2013-01-10
mobo :  
old Mercury with AMD K7 integrated
SiS740 Northbridge and SiS962L Southbridge
embedded 256-bit 3D AGP Graphics Accelerator with 64MB frame buffer, supporting AGP 4X 266MHz

this is strange, i want to upgrade my current setting, ubuntu 11.10 who is no longer supported to something newer.

i tried ubuntu 12.10 and everything installed and ran fine but really slow ( ubuntu 12.x really need cpu power)

so i also installed Xubuntu 12.10 and it worked fine...

so i said to myself, i should go for the lean version,  
so i tried to run (and install ) Lubuntu 12.10 and it fail it did go through the installer process.

so i tried with lubuntu 12.04 alternate cd installation,  all installation when fine, but no success boot ...

it really look like graphic driver don't work with Lubuntu ...
but both installation with ubuntu and xubuntu works right away ...

any hints how i can fix that ?
i really like this little old mobo,  it is my home trusty printer server !

---

### Post by Yellow Pasque on 2013-01-10
> so i also installed Xubuntu 12.10 and it worked fine...
Xubuntu/xfce is fairly lean, but if you want to try LXDE, you can just install the lxde packages. I have no idea why Lubuntu won't work, but you don't have to install another Ubuntu flavor just to try its default desktop. 
Basically, install Xubuntu 12.10, and then install LXDE with:
```
sudo apt-get install lxde
```
This will give you the option of using LXDE (select it at the login screen).

---

### Post by n45w73 on 2013-01-11
> **Temüjin said:**
> Xubuntu/xfce is fairly lean, but if you want to try LXDE, you can just install the lxde packages. I have no idea why Lubuntu won't work, but you don't have to install another Ubuntu flavor just to try its default desktop. 
Basically, install Xubuntu 12.10, and then install LXDE with:
```
sudo apt-get install lxde
```
This will give you the option of using LXDE (select it at the login screen).

thanks,  

i installed lxde package, and it works fine :p
so i don't know why i can't install lubuntu directly :(

another question, is this lxde package all what i need to install to be completed lubuntu similar ? 
im also guessing that having Xfce graphic still there will not impact cpu performance when i will used lxde ? just taking dead space on hd...

:)

---

### Post by mörgæs on 2013-01-11
> **n45w73 said:**
> ...ubuntu 11.10 who is no longer supported...

A small note: 11.10 is still supported, but only through april this year.

---

### Post by Yellow Pasque on 2013-01-11
> another question, is this lxde package all what i need to install to be completed lubuntu similar ? 
Well, there is also lubuntu-core (minimal desktop) and lubuntu-desktop (full lubuntu install) packages.

> im also guessing that having Xfce graphic still there will not impact cpu performance when i will used lxde ? just taking dead space on hd...
Correct, but unless you're desperate for disk space, I wouldn't remove it. It's good to have a backup desktop in case your desktop of choice gets screwed up.

---

### Post by mysteriousdarren on 2013-01-11
I've had trouble a couple times and have reverted to installing vanilla Ubuntu 12.10 and adding lxde after its all said and done. Good thing your set to go.

---

