---
title: "how to install a program from a downloaded file??"
date: 2009-01-26
forum: Installation &amp; Upgrades
---

### Post by conanboy on 2009-01-26
ok... a new windows user which had just switched to linux....
-------------------------------------------------------------
assume that there is a firefox installation file on the desktop :
xxx.tar.bz2  or xxx.tar.gz

how shall i install it?

cause when i extract it, there is no .exe file as there is in windows, so how....

--------------------------------------------------------------

beside that , what is the cmd in linux????


[COLOR="Red"]ps: additional stuff on #5,#12 [/COLOR]

tak a lot...

---

### Post by gettinoriginal on 2009-01-26
As you said, you are no longer in windows, there are no .exe files, as linux does not use .dll.  May I ask why you are trying to install it from git ??  It is installed by default in Ubuntu.

---

### Post by oldos2er on 2009-01-26
As was mentioned, Firefox is already installed in Ubuntu. If you want to make sure you have the latest updates, run ```
sudo apt-get update && sudo apt-get safe-upgrade
``` in a terminal.

 Please read [https://help.ubuntu.com/8.10/add-applications/C/index.html](https://help.ubuntu.com/8.10/add-applications/C/index.html) and [http://psychocats.net/ubuntu/installingsoftware](http://psychocats.net/ubuntu/installingsoftware)

---

### Post by Melk79 on 2009-01-26
You can also visit this site for a more detailed explanation re: Firefox. [https://help.ubuntu.com/community/FirefoxNewVersion](https://help.ubuntu.com/community/FirefoxNewVersion)

You will find though, that more and more programs are offering "one-click" type install files.  For Ubuntu they will be .deb files, other distros like Fedora use .rpm files.

---

### Post by conanboy on 2009-01-27
> **gettinoriginal said:**
> ...  It is installed by default in Ubuntu.
> **oldos2er said:**
> As was mentioned, Firefox is already installed in Ubuntu. If you want to make sure you have the latest updates, run ```
sudo apt-get update && sudo apt-get safe-upgrade
``` in a terminal.
 Please read [https://help.ubuntu.com/8.10/add-applications/C/index.html](https://help.ubuntu.com/8.10/add-applications/C/index.html) and [http://psychocats.net/ubuntu/installingsoftware](http://psychocats.net/ubuntu/installingsoftware)
> **Melk79 said:**
> You can also visit this site for a more detailed explanation re: Firefox. [https://help.ubuntu.com/community/FirefoxNewVersion](https://help.ubuntu.com/community/FirefoxNewVersion)
You will find though, that more and more programs are offering "one-click" type install files.  For Ubuntu they will be .deb files, other distros like Fedora use .rpm files.

that's off topic...really...i said"assume that there is"

thanks for the help so far.... i would just like to do something manually...

i just don't want to say some program which u guys might have not heard before....

-----ok, let's change a program...let's say: ImageMagick..i couldn't find it from the "add/remove" list, so i'll have to down it manually...

---

### Post by conanboy on 2009-01-27
[ftp://ftp.fifi.org/pub/ImageMagick/](ftp://ftp.fifi.org/pub/ImageMagick/)

it is only available in the form of

ImageMagick-6.4.6-9.7z  	 
ImageMagick-6.4.6-9.tar.bz2 	 
ImageMagick-6.4.6-9.tar.gz 	 
ImageMagick-6.4.6-9.tar.lzma 	 
ImageMagick-6.4.6-9.zip

---

### Post by oldos2er on 2009-01-27
Imagemagick is most certainly in the repositories. Which version of Ubuntu are you using, and can you please post the output of

```
cat /etc/apt/sources.list
```

?

---

### Post by grants on 2009-01-27
i've tried the 
sudo apt-get gnome-power-management

it runs some stuff but i don't know how to actully run the program after and how to get it to start upon startup.

:(

---

### Post by AlexDudko on 2009-01-27
To install a program from tarball you should first extract downloaded file, then go to the direcrory:
> cd /way-to-directory/directory-of-extracted-file
then run in terminal:
> ./configure
make
make install

There could be options of configure, so read first a readme file to the program.

---

### Post by snowpine on 2009-01-27
> **grants said:**
> i've tried the 
sudo apt-get gnome-power-management

it runs some stuff but i don't know how to actully run the program after and how to get it to start upon startup.

:(

Try starting a new thread for your problem, with a descriptive title so people can help you. :)

---

### Post by snowpine on 2009-01-27
Hi Conanboy,

One of the big differences between Windows and a Linux distro like Ubuntu is that Ubuntu uses a "repository" of software. This is software that's been "tested and approved" to work on your Ubuntu system. You can install software from the repository in several ways: add/remove programs, synaptic package manager, or the command line (apt-get or aptitutde). 

It is admirable that you want to learn to do things from the command line. ;) However, if an application is in the repositories, it is almost always best to install the version in the repositories rather than download some random installer from the internet. Again, this is a big difference from Windows. :)

---

### Post by oldos2er on 2009-01-27
> **grants said:**
> i've tried the 
sudo apt-get gnome-power-management

it runs some stuff but i don't know how to actully run the program after and how to get it to start upon startup.

:(

 There should be a menu entry in System, Preferences, Power Management.

---

### Post by conanboy on 2009-01-27
i',m not sure what others were saying... :?:

QUOTE=oldos2er;6626706]
Imagemagick is most certainly in the repositories. Which version of Ubuntu are you using, and can you please post the output of

```
cat /etc/apt/sources.list
```

?[/QUOTE]

i'm using 8.4.10....as my friend said that there is a "extra long" support live than 8.10 does (anyone tell me what is happening?)

"output",you mean where i save the file? it is safed in the desktop as it's firefox's default... so> /home/conan/Desktop/ImageMagick-6.4.6-9.tar.gz

---

### Post by conanboy on 2009-01-27
cout << "conanboy is lost" << endl;

---

### Post by oldos2er on 2009-01-27
Open a terminal using the menus Applications, Accessories, Terminal. Copy and paste the following into the terminal
```
cat /etc/apt/sources.list
```
and copy and paste the output from that command here.

---

### Post by r0g on 2009-01-28
Hi Conan,

Sorry no-one seems able to grasp you question - must be cosmic rays or something!...


>how shall i install it?

Extract the contents of the file to a folder (right-click, extract here)
Have a look for the README file - it will contain install instructions.

There's a number of ways to install stuff in linux and a .gz file could contain source-code, executables or anything so until you can tell just by looking just read the README file (or nearest thing you can find).

Ideally you'd only do that every now and then though. When you need some software look for it in System / Administration / Synaptic Package manager (forget add/remove!), if you can find it in here you're golden - it will automatically install any other programs and libraries that the app depends on and keep it, and them, up to date for you. 

Next best are .deb files, these you can just double click to install like windows installers

.gz files, as above, read the readme - they can contain source code which you have to compile (or make) as someone described above, but they could also contain executable scripts files (*.py, *.pl) or compiled executable code (*.o) which are equivalent to windows .exe files - be careful with these though, make sure you trust the source!


>beside that , what is the cmd in linux????

That's "The command line" aka "the terminal" aka "the shell", you can get it via Applications / Accessories / Terminal.  Many website's use the command line in their tutorials as it is easier than publishing loads of screen shots, quite often though there is a way to acheive the same thing graphically like you would on windows.  In particular: there is a command line program called "apt-get" that does the same thing as Synaptic Package Manager, the two are interchangable so anything you see in a tuorial that looks like "apt-get install xyz foobar rahrahrah" is equivalent to opening Synaptic and installingthe programs xyz, foobar and rahrahrah.

Anyway, I hope this is what you were looking for, good luck with your new install, it may take a bit of getting used to but you've made the right choice! :-)

---

### Post by conanboy on 2009-01-28
> **r0g said:**
> Hi Conan,
.......

thank u very very much, it must be a tough job to type so many....

before i had read your apply:
i'd spent couples of hours and i did had a thought that terminal is the cmd in linux, but i had no prove...
and i also thought that "Synaptic Package manager" is a type 0f browser where u can select the installation package...

but after your open source tutoring... i thought that maybe"Synaptic Package manager" is also a "list of program", so i had a close look and finally find the ImageMagick i want...

so, what is the different between  "Synaptic Package manager" & "add/remove"???
is it like a type of "patch" list, and that's why there's no short cut even though i had install ImageMagick???

now i'm on my way to struggling & understand how to use command line...

---

### Post by conanboy on 2009-01-28
> **oldos2er said:**
> Open a terminal using the menus Applications, Accessories, Terminal. Copy and paste the following into the terminal
```
cat /etc/apt/sources.list
```
and copy and paste the output from that command here.

i'm still not sure what u mean...

it end's up with links for ubuntu patchs (i guess lol), is it that u want me to download the stuff i want from the links? 
> 
# deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hardy main restricted
# deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hardy-updates main restricted
# deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hardy-security main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hardy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hardy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hardy universe
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hardy universe
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hardy-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hardy multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hardy multiverse
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hardy-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hardy-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse


---

### Post by hutchinsfairy on 2009-02-05
A related question: If I install a program from a source code tarball or .deb file will the package manager be 'aware' of it? 

i.e. Will I be able to uninstall it from the manager? Will it keep track of dependencies? Will it look for the program's appearance in the repo's? 

If the manager is unaware, is it possible to input the information?

Is there another application which can keep track of them?

Thanks in advance guys!
Tom

---

