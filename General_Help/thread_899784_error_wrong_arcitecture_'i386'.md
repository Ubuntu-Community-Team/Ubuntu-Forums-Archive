---
title: "error wrong arcitecture 'i386'"
date: 2008-08-24
forum: General Help
---

### Post by jimi_hendrix on 2008-08-24
i get the error wrong arcitecture 'i386' when i try to install .deb packages...please help. thanks in advance

note: yes i did post this in the "installation and upgrade" but i realized that forum was more focused around installing and upgrading ubuntu not apps so im not trying to double post but post my thread but to move it to the more appropriate forum (if im wrong im sorry)

---

### Post by cmay on 2008-08-24
what computer do you have.
on mine i cant get some programs like gnu/mit scheme since i am on an amd 64 bit. maybe it does not support your computer.

hope it helps.

---

### Post by tuxxy on 2008-08-24
Are you running 64-bit? of you are then get the 64bit .deb

---

### Post by hansdown on 2008-08-24
Are you using 64 bit? 

To find out, type uname -a in the terminal.

---

### Post by drs305 on 2008-08-24
You can tell which kernel version you are running with:
```
uname -r
```
My 64-bit kernel responds with:
"Linux hb1 2.6.24-19-generic #1 SMP Fri Jul 11 21:01:46 UTC 2008 **x86_64 **GNU/Linux"

The bold portion indicates I am running the 64-bit kernel.

If that is what you are running, you are likely trying to install a 32-bit package. It can be done, but I would recommend trying the 64-bit version first, if it is available. 

The second issue if you *are* running  the 64-bit version, where did the 32-bit .deb you are trying to install come from? Your repositories in sources.list may need updating, or you may need to go to the site you got the .deb and download the AMD64 or 64-bit version (Intel 64-bit is also part of the AMD64 nomenclature).

You can install 32-bit apps in 64-bit kernels with the command:
```
sudo dpkg -i --force-all package_name.deb
```
but again I would try to find the 64-bit version first.

There is also an app, getlibs, which can install the applicable 32-bit libraries which may be required by those apps. Here is a good link that explains getlibs and will give you some good information:
[getlibs: Automatically solves dependencies for 32-bit programs on 64-bit]("http://ubuntuforums.org/showthread.php?t=474790&highlight=install+32-bit")

---

### Post by jimi_hendrix on 2008-08-25
thanks...i am running 64 bit

---

