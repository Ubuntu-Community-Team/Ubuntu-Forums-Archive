---
title: "Backing Up Existing Packages"
date: 2008-08-14
forum: General Help
---

### Post by sa125 on 2008-08-14
Hi - is there a tool that can backup all my existing package information, meaning I wont have to re-select every package I installed in case I have to re-install ubuntu or want to duplicate my software on another machine? Just something that creates some sort of backup file that I can go back to and invoke to auto-select synaptic packages when installing anew. Thanks!

---

### Post by rsambuca on 2008-08-14
A very crude (but still effective method) is to just keep a text file of all the programs you install, then just...  

```
sudo apt-get install *copy and paste your list*
```It will then install them all at once.  I am sure there is a less crude method, but this works.

---

### Post by robert shearer on 2008-08-14
check these links
 [http://www.ubuntugeek.com/creating-custom-ubuntu-live-cd-with-remastersys.html](http://www.ubuntugeek.com/creating-custom-ubuntu-live-cd-with-remastersys.html)

[http://www.remastersys.klikit-linux.com/](http://www.remastersys.klikit-linux.com/)

for a complete backup option

---

### Post by drs305 on 2008-08-14
I think this is what you are looking for. It will create a list of installed packages. Then on the new computer or later, you import the list back into the system and the update will reinstall/install all the packages in the list.

Create a list of all installed packages (created on the Desktop and named package-list in this example):
```
sudo dpkg --get-selections >~/Desktop/package-list
```

On a new computer, copy the file to the Desktop, then: 
```
sudo dpkg --clear-selections
sudo dpkg --set-selections <~/Desktop/package-list
sudo apt-get update
sudo apt-get dselect-upgrade 

```

---

### Post by rsambuca on 2008-08-14
I knew there was a more elegant solution!

---

### Post by sa125 on 2008-08-15
Thanks!

---

