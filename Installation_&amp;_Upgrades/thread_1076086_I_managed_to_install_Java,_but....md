---
title: "I managed to install Java, but..."
date: 2009-02-21
forum: Installation &amp; Upgrades
---

### Post by Wizho on 2009-02-21
Hello, this is my first post and I am technically new to Linux, I just installed Ubuntu today because windows somehow messed up and I couldn't managed to boot it again, so I ran my Ubuntu live CD and made a backup of all my files in Windows to my iPod, then I made a complete installation of Ubuntu as my main OS.

I have used Ubuntu before, but just for some days, I haven't much experience on Linux.
So I went to java.com and downloaded jre-6u12-linux-i586.bin and saved it in my desktop.
Then I loged in as root and changed directories:

$ sudo bash
# cd /home/luis/Escritorio/

Then I gave permissions to the file that I saved on my desktop (Escritorio):

$ chmod +x jre-6u12-linux-i586.bin

And then installed:

# ./jre-6u12-linux-i586-rpm.bin

Then it was done, but I think it installed Java on my desktop because I have a folder with a lock on it called jre1.6.0_12
As far as I know, java is supposed to install itself to /usr/java/  but I can't create a new folder there, neither can I delete the folder on my desktop without using nautilus.
So, how do I install Java where it's supposed to be?

Sorry, I know this question is stupid for most of you but I'm new to Linux, so any help will be greatly appretiated and I really want to use Linux as my main operating software and leave Windows behind, meanwhile I'll be looking for tutorials and basic commands and more stuff for mewbies.

Also, how does installing software in Linux work?
All I know is that software come in packages, which are downloaded and installed with Synaptic, another way is to download the binaries and install them using the terminal just as I did, am I right or not?

Thanks in advance. ;)

---

### Post by markusf21 on 2009-02-21
if you have the multiverse repo enabled you can install java with synaptic

---

### Post by Partyboi2 on 2009-02-21
> **Wizho said:**
> Hello, this is my first post and I am technically new to Linux, I just installed Ubuntu today because windows somehow messed up and I couldn't managed to boot it again, so I ran my Ubuntu live CD and made a backup of all my files in Windows to my iPod, then I made a complete installation of Ubuntu as my main OS.

I have used Ubuntu before, but just for some days, I haven't much experience on Linux.
So I went to java.com and downloaded jre-6u12-linux-i586.bin and saved it in my desktop.
Then I loged in as root and changed directories:

$ sudo bash
# cd /home/luis/Escritorio/

Then I gave permissions to the file that I saved on my desktop (Escritorio):

$ chmod +x jre-6u12-linux-i586.bin

And then installed:

# ./jre-6u12-linux-i586-rpm.bin

Then it was done, but I think it installed Java on my desktop because I have a folder with a lock on it called jre1.6.0_12
As far as I know, java is supposed to install itself to /usr/java/  but I can't create a new folder there, neither can I delete the folder on my desktop without using nautilus.
So, how do I install Java where it's supposed to be?

Sorry, I know this question is stupid for most of you but I'm new to Linux, so any help will be greatly appretiated and I really want to use Linux as my main operating software and leave Windows behind, meanwhile I'll be looking for tutorials and basic commands and more stuff for mewbies.

Also, how does installing software in Linux work?
All I know is that software come in packages, which are downloaded and installed with Synaptic, another way is to download the binaries and install them using the terminal just as I did, am I right or not?

Thanks in advance. ;)

Welcome, you can search Synaptic for sun-java6-jre package and install it. Or open a Terminal (Application>Accessories>Terminal) and install with
```
sudo apt-get install sun-java6-jre
```[[COLOR=Blue]This link[/COLOR]]("https://help.ubuntu.com/community/InstallingSoftware") will explain how to install software.

---

