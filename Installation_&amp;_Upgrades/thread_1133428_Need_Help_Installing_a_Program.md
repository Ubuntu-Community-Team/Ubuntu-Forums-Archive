---
title: "Need Help Installing a Program"
date: 2009-04-22
forum: Installation &amp; Upgrades
---

### Post by homedawg913 on 2009-04-22
im new at ubuntu, and i need help installing a bot program for a game called runescape.

the program can be found on [http://www.rscheata.net/forum/index.php/page,27.html](http://www.rscheata.net/forum/index.php/page,27.html)

i need help installing the Nexus & Ibot lite version.

if anyone could please look at it and help me i would appreciate it :]

thank you.

---

### Post by homedawg913 on 2009-04-23
any help please?

---

### Post by Bakon Jarser on 2009-04-23
These programs may not work in linux.  It wouldn't let me see if they have a linux version without registering but I'm going to assume that they don't.  You'll have to try and run them with wine.  Just install wine and then try and install the program like you normally would in windows.  It will show up in applications > wine > programs.

```
sudo apt-get install wine
```

---

### Post by homedawg913 on 2009-04-23
when i used windows xp, and had this program when your going to install it, it gave you a linux, windows, and mac option so yes they have linux.. but il try with wine :]

---

### Post by coffeecat on 2009-04-23
> **homedawg913 said:**
> it gave you a linux, windows, and mac option so yes they have linux.. but il try with wine :]

If they do a native Linux version, it might be better to install this rather than run the Windows version in Wine. However, since we ordinary mortals can't get to the download page to see what's available, you're going to have to provide more information. :wink:

As you're new to Ubuntu, I'll explain. Different Linux versions use different installer packages. For Ubuntu, you need an installer package with the .deb filename extension. These are for Debian and Debian-based distros like Ubuntu. Or, if they do a specific Ubuntu .deb package, get that. Don't get a package with a .rpm extension. These are for distros like Fedora, Suse and Mandriva. And don't get a .tar.gz, tar.bz2 or .tgz package. These are source code packages. You don't want to be messing with source code just yet.

If they do an Ubuntu .deb package, simply download it to your desktop and double-click on it. If it needs dependencies (other things like libraries) it will say so. If not it will just install itself.

Otherwise, tell us more about what Linux packages are available.

---

### Post by homedawg913 on 2009-04-23
ok well, when you click install nexus lite on their page, it opens with archive manager as a botclient.zip file

when you open that zip file it contains all these folders and files in it

-FOLDERS-
Bitmaps
Config
Jars
Logs
Scripts


-TXT FILES-
Headers.txt
key.txt

-OTHER FILES-
Install.bat
install.sh
log4j.properties

hopefully this helps a bit more, if not ill try getting an account on the website for yall to get a look for yourselves..

---

### Post by Bakon Jarser on 2009-04-24
Nice.  install.sh is a shell script which should install everything automatically.  Extract all the files to a folder and double click install.sh.  It should say something like 'do you want to run this as an executable'.  click yes and hopefully it will install successfuly.  Let us know how it goes.

---

### Post by homedawg913 on 2009-04-25
When i extract to a folder, i click on the install.sh file to install it.

and a window opens up and says this on it.

java -cp .:./jars/install.jar Install $* 
chmod a+x run.sh compile.sh

---

### Post by homedawg913 on 2009-04-25
ok so i finally got it to install somehow, and i chose the linux version of it.. but when  i click run.sh as an executable file, it opens a window and then closes and wont run the program.

in the window that opens up it says>

log4j:INFO Using URL [file:/home/homedawg/Desktop/Nexus/log2j.properties for automatic log4j configuration of repository named [default].

i dont know what that means lol and after that it closes and nothing else happens

---

### Post by homedawg913 on 2009-04-27
if anyone could help that would be great

---

### Post by homedawg913 on 2009-04-27
When i run install.sh it opens a window that says this.

Install

Your Java Version: 1.6.0_0

Your Operating System: Linux

Please Select which SWT bext describes operating system and JVM(32Bit or 64Bit)

swt-3.5M6-cocoa-macosx.jar
swt-3.5M6-windows-Java64bit.jar
swt-3.4M4-linux-gtk-Java64bit.jar
swt-3.4M4-linux-gtk-ppc.jar
swt-3.4M4-linux-motif-linux-Java32bit.jar
swt-3.5M6-carbon-macosx.jar
swt-3.4M4-linux-gtk-Java32bit.jar
swt-3.5M6-windows-Java32bit.jar
swt-3.5M6-cocoa-macosx-x86_64.jar

thats all the installs i can choose from, i havent had luck with any of them

---

### Post by Bakon Jarser on 2009-04-27
unless you are running 64bit or running a power pc the best fit is swt-3.4M4-linux-gtk-Java32bit.jar.  Is there any way to contact the author of this program?  He would probably be able to help more than I can.

---

### Post by homedawg913 on 2009-04-27
Alright, thanks

---

### Post by Habboblob on 2009-09-30
This is how you would install it.
Please delete all your botclient files and start fresh.

Re-download it from this URL [http://www.impsoft.info/download.php](http://www.impsoft.info/download.php) and extract it on your desktop.
There should be a new folder called botclient on your desktop.

Now, you have to install it.

Please note these steps work with the latest version of Nexus iBot downloaded from [http://www.impsoft.info/download.php](http://www.impsoft.info/download.php)

1)Firstly, click on Application > Accessories > Terminal. 
2)Run terminal, and in it type in the following ```
cd ~/Desktop/botclient
```
3)Then type in ```
./install-mac-linux.sh
```
4)A window should pop up, fill out the settings asked, example:
-Operating System: Linux GTK 32-bit (or Linux GTK 64-bit if you have 64  bit)

-Version: Don't worry about the recommened, just scroll down and select the highest number, in my case, it is 21.130

-SQL Version: Should only have 1 option, so don't worry about that
5) Now hit install.
6) Once the window disappears. Close Terminal.
7) Re-do the steps from 1 to 2
8a) Now type in ```
./run-linux.sh
```
8b) If you recieve a permissions error, then continue to step 9, if not skip straight to step 10.
9) Type in ```
chmod +x run-linux.sh
```
10) Now type in ```
./run-linux.sh
``` and the bot should now be working.

Please reply back to me if it is not working or if it did work!
I like my feedback!

---

