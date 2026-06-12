---
title: "adt-get ./configure failure"
date: 2009-10-24
forum: Installation &amp; Upgrades
---

### Post by toolmanpaul on 2009-10-24
i have a thread "no-wifi" here tring to get my wireless working...that said-after reading ubuntu help for no wi-fi, i decided to install wireless-tools package, guess what? There's no wireless-tools package in the add and remove....so download the tar.gz...follow the ubuntu instructions for tar instillations and when i type ./configure i get a not valid command error.. i then type make (lots of action on the screen) and then type make install (little screen action)..but now i can't find wireless-tools in applications any where...thinking i made things worse (though computer seem to work ok) there was alot of action when i typed "make" and then "make install"..should i now type "adt-get remove purge" to rid this app.  i tried wifi radar also with the same results....could not find it after install...Note- radar was in the add and remove programs...Thanks for any help.   Paul

---

### Post by Dougie187 on 2009-10-24
Hey,

You have to be in the new directory (that was just extracted) to type ```
./configure.sh
```
Also, it might not be something that you have to do, it's just a probable step. Some installation packages might not have the configure shell script. Anyways after that you have to type ```
make
``` and then ```
make install
``` however, ```
make install
``` only installs it some local folder, so you might want to run ```
sudo make install
``` to make it actually installed on the computer, but I would test it in a local folder before you install it globally on your computer. Then to remove the program, you can't type ```
 sudo apt-get autoremove --purge wireless-tools
``` as that isn't how you installed it. Now to remove it, you have to be in the same directory that you type ```
make
make install
```
and now you have to type ```
make uninstall
``` or if you installed it globally before by prepending sudo to the make install command you would type ```
sudo make uninstall
```

Also though, I should mention that I believe wireless tools is in the repositories, so you might try typing this.```
sudo apt-get install wireless-tools
```

---

### Post by toolmanpaul on 2009-10-24
did the install stuff

---

