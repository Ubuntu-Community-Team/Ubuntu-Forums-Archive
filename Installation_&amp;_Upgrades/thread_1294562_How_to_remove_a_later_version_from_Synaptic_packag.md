---
title: "How to remove a later version from Synaptic package manager??"
date: 2009-10-18
forum: Installation &amp; Upgrades
---

### Post by dipspesh on 2009-10-18
Hello everyone,i want to know how do you remove an upgrade from the synaptic package manager?
i had installed pidgin 2.5.5 and it was working properly but the file sharing option didn't come so i copied a few terminal commands from the pidgin's site and pasted it onto the terminal,because of which the update manager showed a new update of pidgin ie. 2.6.1.
 but this version of pidgin is not working properly,so i again tried to download and install the 2.5.5 version from the internet but when i'm opening it for installation,it is showing that a later version is already present(which actually is in the synaptic package manager)..
 so how do i remove the 2.6.1 version from the synaptic package manager so that i'm able to install the 2.5.5 version again!!

please help on this because i don't know any commands for the terminal!!

---

### Post by friv_livs on 2009-10-18
First, back up your home directory. 

Then try right clicking the pidgin package in synaptic, and seeing what other packages it will remove if you select "mark for complete removal" If none of those listed are system critical (i.e. nautilus, gnome, dpkg, etc.) then just allow it to completely remove.

Then, once that is done, use the file finder to search for "pidgin" in "filesytem", and use the following terminal commands to clean up:

```
sudo su
cd "path/just/above/file_or_folder"
rm -rf  "file_or_folder"
```replacing the qouted sections with what's indicated inside from the file finder. Run the last two lines of the above script as many times as neccesary to remove all instances found.

Next, run the following command to exit root sudo:
```
exit
```Then just reinstall the pidgin package from synaptic.

---

### Post by dipspesh on 2009-10-18
I used the following commands in terminal
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com \     67265eb522bdd6b1c69e66ed7fb8bee0a1f196a8
 echo deb [http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu](http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu) \     `lsb_release --short --codename` main | \
    sudo tee /etc/apt/sources.list.d/pidgin-ppa.list


then run it from the update manager
now how do i revert back the changes???
sumbody please help....please reply to d post because i don't know any commands in the terminal!!

---

### Post by dipspesh on 2009-10-18
I removed all the files from the commands which you told me....but still the messsage is being displayed when i'm trying to install pidgin 2.5.5 and in the synaptic manager still the latest version being showed is 2.6.1....how is complete reversal possible??

---

### Post by wilee-nilee on 2009-10-18
You can force install a package in synaptic it is a lot easier then using the terminal.

---

### Post by dipspesh on 2009-10-18
HOw do i force the installation in synaptic manager when the manager itself shows d current version of pidgin to be 2.6.1.....how do i forcibly install version 2.5.5???

---

### Post by wilee-nilee on 2009-10-18
So go to synaptic and first enable systems-preferences-general-show package properties in main window. Then find your installed pidgin and it will show you in the bottom window the versions of your choice click on the one you want in the bottom window then-package force version.   I like the use of the terminal but there are many times this advice is given when it is not needed and only confuses the user if they are not familiar with CLI, and can really screw stuff up if a mistake is made.

---

### Post by dipspesh on 2009-10-18
this isn't helping i'm getting this error
pidgin:
  Depends: pidgin-data (<1:2.5.5-z) but 1:2.6.1-1ubuntu0~pidgin1.9.04 is to be installed
 
and the synaptic package manage isn't forcing the installation
wat do i do now???

---

### Post by wilee-nilee on 2009-10-18
I have never used pidgin, and I suspect all the messing around has created the problem. If it was me I would purge everything pidgin remove all files in home do a re-start then install the one you want and watch updates so that it doesn,t get updated from the version you want.
So not having used pidgin I had not taken into consideration dependencies, so be careful as the first post suggested in what your doing. I believe you can unlock these dependencies but I don't remember the process. Somebody more knowledgeable and/or the original person who posted may come back and give more to work with.

---

### Post by dipspesh on 2009-10-18
yes i agree it's getting a bit messy everytime i try to force and install i get different errors like this

E: Unable to correct problems, you have held broken packages.
E: Unable to lock the download directory
 and like this
pidgin-dbg:
 Depends: pidgin but it is not going to be installed or
     finch (=1:2.5.5-1ubuntu8.4) but 1:2.6.1-1ubuntu0~pidgin1.9.04 is to be installed or
     libpurple0 (=1:2.5.5-1ubuntu8.4) but 1:2.6.1-1ubuntu0~pidgin1.9.04 is to be installed
  Depends: pidgin-data (=1:2.5.5-1ubuntu8.4) but 1:2.6.1-1ubuntu0~pidgin1.9.04 is to be installed

pidgin:
  Depends: libpurple0 (>=1:2.5.5-1ubuntu8) but 1:2.5.5-1~getdeb1 is to be installed
pidgin:
 Depends: libpurple0 but it is not going to be installed 

someone who has a idea about pidgin and dependencies please help!!!

---

### Post by laceration on 2009-10-18
All you have to do is remove the repositories you added.  Remove the program as explained before.  Then open Menu->System->Administration->Software Sources
enter password
click on Third-Party-Software tab
and uncheck the repositories you added before -- the ones that have "pidgen-developers" in them.
After your sources update only the standard Ubuntu version will show up.

---

### Post by dipspesh on 2009-10-18
Thank you guys....this thing in the last worked...now the latest version is not being shown anymore and i've installed the previous version and i'm happy chatting!!


Thanks once more!!!!

---

### Post by wilee-nilee on 2009-10-18
> **dipspesh said:**
> Thank you guys....this thing in the last worked...now the latest version is not being shown anymore and i've installed the previous version and i'm happy chatting!!


Thanks once more!!!!

 Yipee is what I say.

---

