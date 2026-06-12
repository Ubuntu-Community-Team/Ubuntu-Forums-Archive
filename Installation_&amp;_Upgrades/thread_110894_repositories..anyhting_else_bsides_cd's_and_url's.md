---
title: "repositories..anyhting else bsides cd's and url's?"
date: 2005-12-31
forum: Installation &amp; Upgrades
---

### Post by dutch_boi1 on 2005-12-31
hello

i was just wondering if i can add any repositories besides cd's and url's?....is it possibly 4 me 2 make a folder in the desktop for eg. and just copy .deb files into there then have synaptic package manager search in there for packages also? I have wine on my desktop and i dont know how to install it(they're .deb files):confused: ... if u could help me that'd b great:D 

thankx

---

### Post by Sutekh on 2006-01-01
Well your .deb's that are downloaded by Synaptic are put in /var/cache/apt/archives/

You could create a link on your Desktop to the cache folder.  That way when you copy a file to that link on your Desktop they would be put into the apt-cache folder
```
ln -s /var/cache/apt/archives/ Link_Name
```
Would do the trick.

Because the /var/cache/apt/archives/ folder is 'owned' by root, you will need to use 'sudo' when you copy any file into the folder.

If you put a random .deb - **some_file.deb** into that folder using
```
sudo cp some_file.deb ~/Desktop/Link_Name
```
then
```
sudo apt-get install some_file
```
Would install that file.

The command
```
sudo -i dpkg some_file.deb
```
Can also be used to install .deb's from the folder that they are in.

---

### Post by melesigene on 2006-01-01
hi,

you can install a deb package directly by using this command line :

 dpkg -i yourpackage.deb

anyway it won't check dependencies (if the package needs other packages to works properly - like additionnal libraries etc...)

the proper way will be (if you want to be sure it works : ) ) :

- command line 

apt-get install wine

- apps like synaptic or Adept

search the package and ask it to be installed

you will be sure that these two ways will take in count dependencies between packages, and all that you installed this way will works (most often)

if you still want to make a "local repository" several posts explain how to do this (I think it's painful but well, you see ...)

for a CD :
[https://wiki.ubuntu.com/AptMoveHowto?highlight=%28Move%29%7C%28How%29%7C%28to%29%7C%28Apt%29](https://wiki.ubuntu.com/AptMoveHowto?highlight=%28Move%29%7C%28How%29%7C%28to%29%7C%28Apt%29)

local/remote repository :
[http://ubuntuforums.org/showthread.php?t=42862&highlight=make+local+deb+repository](http://ubuntuforums.org/showthread.php?t=42862&highlight=make+local+deb+repository)

you can find many other posts I think

hope my reply will help

cheers !

---

### Post by dutch_boi1 on 2006-01-02
err orsum...im juz wondering, umm when i want copy a .deb file into /var/cache/apt/archives/ do i have to go by command, or can i juz cut n paste it into that folder, coz using the command is goin 2 b very annoying.......so yeh thankx 4 the help i will try it out, and also thankz for the links to the repositories:) 

thankx

---

### Post by dutch_boi1 on 2006-01-03
hey umm....i downloaded a whole list of packages, i think there is about 12 of them so yeh... i have put them onto a cd, but when i use synaptic and click edit>add cdrom, it says error cannot add, no packages found or something similar. on the cd there is 12 .deb packagez, but it duznt see them :confused: .. is there a manual way 2 add the cdrom into the synaptic repositories, like without going into the terminal, i h8 that thing. It always fails to install packages:mad: lol.

thankx

---

