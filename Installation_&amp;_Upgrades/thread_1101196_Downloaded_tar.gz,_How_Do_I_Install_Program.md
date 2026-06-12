---
title: "Downloaded tar.gz, How Do I Install Program?"
date: 2009-03-20
forum: Installation &amp; Upgrades
---

### Post by ZombiesNTea on 2009-03-20
[http://storybook.intertec.ch/joomla/index.php/installation](http://storybook.intertec.ch/joomla/index.php/installation)

Above is the link to installation instructions for a program I am trying to put onto my laptop here.  I have no idea what I am doing, nor understand how to install this (I'm new to Linux).  I went to the Add/Remove Applications, and the Synaptic Package Manager, with no luck.  With what it says in the link above, I don't know where Id go to enter that or whatnot.

I went into the compressed tar.gz file (the file the site offered for me to download) and looked around, but there was nothing that I'd done that had helped.

Could someone tell me what I'm doing wrong?

---

### Post by dandnsmith on 2009-03-20
Perhaps this will help (from the page you linked to)

=========================================
Linux

    * Download the appropriate file from the download section.
    * Copy the downloaded file to the desired directory. Storybook doesn't need root permission to install. You can install it in your home directory without any problems.

Extract the file:
$ tar xvf 
 
Install it:
$ ./install.sh

Run it:
$ ./storybook.sh
==============================================

---

### Post by Partyboi2 on 2009-03-20
Open a terminal (Applications>Accessories>Terminal) and change to where the downloaded storybook_2.1.12_linux.tar.gz file. So if its on the Desktop
```
cd ~/Desktop
```
then extract the storybook file
```
tar xvzf storybook_2.1.12_linux.tar.gz
```
then change into the new directory
```
cd storybook_2.1.12_linux
```
then run the install script
```
./install.sh
```
then
```
./storybook.sh
```

---

### Post by guywithcable on 2009-03-20
Wow, their instructions are terrible. First, open up a terminal, then you should "cd" to the directory where you downloaded the tar. The files in the tar are not in a folder, so I would make a new folder for it under your home directory, called "Storybook" or something. For example, to cd to your desktop, it's
```
cd ~/Desktop
```That's because "~" is short for your home directory (/home/username)

Then, the instructions should read:

```
Extract the file:
$ tar -xvvzf storybook_2.1.12_linux.tar.gz
 
Install it:
$ ./install.sh

Run it:
$ ./storybook.sh
```Just enter each of those commands into the terminal and hit enter.

(PS: try Scribus and BasKet, from Add/Remove ;))

---

### Post by guywithcable on 2009-03-20
> **Partyboi2 said:**
> Open a terminal (Applications>Accessories>Terminal) and change to where the downloaded storybook_2.1.12_linux.tar.gz file. So if its on the Desktop...
Beat me to it. ;)

---

### Post by Partyboi2 on 2009-03-20
> **guywithcable said:**
> Beat me to it. ;)
We both got beat ;)

---

### Post by ZombiesNTea on 2009-03-20
Thanks everyone!

I can get it to work, but I'm still having a problem.  If I decide to stop using the program, and it is closed... after having installed it before, I return to the terminal to type in "./storybook.sh" again, but it'll say that there is no such file name or directory.

Am I going to have to do the whole install process any time I use it?  Or is there a way to set it up to just be a click away under Applications?

---

### Post by guywithcable on 2009-03-20
> **ZombiesNTea said:**
> Thanks everyone!

I can get it to work, but I'm still having a problem.  If I decide to stop using the program, and it is closed... after having installed it before, I return to the terminal to type in "./storybook.sh" again, but it'll say that there is no such file name or directory.

Am I going to have to do the whole install process any time I use it?  Or is there a way to set it up to just be a click away under Applications?

Are you running that from within the directory it was installed? The "./" at the beginning means the current directory. Your terminal should show you what directory you're in, but you can also use "pwd" (print working directory).

You can use System -> Preferences -> Main Menu to add this to the Applications menu. You should use the full path in the command field if you want to do that. (something like /home/user/Storybook/storybook.sh)

---

### Post by ZombiesNTea on 2009-03-20
I just tried it, but I get this message when I click on the icon:

"Failed to execute child process "art@art-laptop/Desktop/Storybook/storybook.sh" (No such file or directory)"  (The files are in a Desktop folder titled "Storybook")

I've tried it so it just says art instead of art@art-laptop, I've also tried it without putting "Desktop" in it, I've tried it as an "Application", "Application in Terminal", and "Location", but nothing seems to be working.

---

### Post by ZombiesNTea on 2009-03-20
Are most other programs this frustrating to install?

---

### Post by ZombiesNTea on 2009-03-20
Hello?

---

### Post by guywithcable on 2009-03-20
> **ZombiesNTea said:**
> Are most other programs this frustrating to install?

No. Just some of the ones downloaded from the internet. Most programs are installed through the package manager, and installing them is as simple as checking them from a list. Unfortunately, the Storybook programmers are too lazy to make a .deb file (the Debian package file, since Ubuntu is based on Debian), so yeah, installing it is annoying. Even most programs like this are as simple as
```
./configure
make
sudo make install
```But alas, this one is different. Anyway, I think your problem is the pathname. art@art-laptop is your username and your hostname. What you want is a pathname to your home directory. In this case it's probably "/home/art", so run this

```
/home/art/Desktop/Storybook/storybook.sh
```or with shorthand
```
~/Desktop/Storybook/storybook.sh
```

---

### Post by ZombiesNTea on 2009-03-20
I put 

```
/home/art/Desktop/Storybook/storybook.sh
```

Into the main menu thing, but when I click it under applications, it doesn't open.  So I tried going into the terminal and putting that in, and it said this:

```
Unable to access jarfile lib/storybook.jar
```

---

### Post by guywithcable on 2009-03-20
> **ZombiesNTea said:**
> I put 

```
/home/art/Desktop/Storybook/storybook.sh
```Into the main menu thing, but when I click it under applications, it doesn't open.  So I tried going into the terminal and putting that in, and it said this:

```
Unable to access jarfile lib/storybook.jar
```

It sounds like a problem with their program. You could email them and see if they can help, but I don't know enough about Java, and I gotta run. Good luck :)

---

### Post by elmago79 on 2009-04-10
> **ZombiesNTea said:**
> I put 

```
/home/art/Desktop/Storybook/storybook.sh
```

Into the main menu thing, but when I click it under applications, it doesn't open.  So I tried going into the terminal and putting that in, and it said this:

```
Unable to access jarfile lib/storybook.jar
```

This is what I did to add a Storybook entry to the Application menu:

1. Create a small script in a file calles storybooklaunch.sh:

```
#!/bin/bash

cd [path of wherever you extracted the program]
./storybook.sh
```

And then link that script to the Appilcations menu. 

BTW, Storybook seems to be dead (as in no active development) so help form that direction would be unlikely.

---

### Post by drinkglory on 2009-04-19
I agree with ZombiesNTea! these instructions remind me of dos there has to be a package out there to do this if Linux is going to be a household name.

---

