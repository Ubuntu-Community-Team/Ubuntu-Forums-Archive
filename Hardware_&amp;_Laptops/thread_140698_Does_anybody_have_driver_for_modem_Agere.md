---
title: "Does anybody have driver for modem Agere"
date: 2006-03-06
forum: Hardware &amp; Laptops
---

### Post by stonex on 2006-03-06
For 2.6.12-9-386 kernel .   I'v already  try to install 2.9.10+2.9.9d but Ubuntu didn't accept it and says that i must version for 2.6.12-9-386 but i can't find it . Does somebody have that driver ? Thanks !

---

### Post by Sutekh on 2006-03-07
- Well first off I have to tell you it's gonna be some work (!).  If you are using the 32bit Ubuntu installation and I assume you are, the 2.9.10+2.9.9d is the correct one

 - I can show you how to *install* the drivers but I have no idea how to configure them.  Hopefully someone else can jump in.

 - First off do you have *any* sort of internet connection that can be used with Ubuntu or are you relying on this dialup modem?


 - Here's what I had to do to get the drivers installed (on a clean install with no internet)

**Make sure that the Install CD is an available repository**
 - You need the installation CD and it needs to be a repository in your sources.list.  In a terminal windows type ```
sudo apt-cdrom add [/CODE} and insert your CD to make it a repository.  Then edit the **sources.list** using the command
[CODE]sudo gedit /etc/apt/sources.list
```
 - Wherever you see a **deb-src http** or **deb http** insert a # at the beginning of the line.  All this does is comment/ignore the online repositories.  Save the file and use 
```
sudo apt-get update
```
 - To refresh the respositories and continue.

**Download all the packages you will need**
 - Now you will need to download _all_ these files and transfer them to Ubuntu.

[http://archive.ubuntu.com/ubuntu/pool/main/g/gcc-3.4/cpp-3.4_3.4.4-6ubuntu8_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/g/gcc-3.4/cpp-3.4_3.4.4-6ubuntu8_i386.deb)
[http://archive.ubuntu.com/ubuntu/pool/main/g/gcc-3.4/gcc-3.4_3.4.4-6ubuntu8_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/g/gcc-3.4/gcc-3.4_3.4.4-6ubuntu8_i386.deb)
[http://archive.ubuntu.com/ubuntu/pool/main/g/gcc-3.4/gcc-3.4-base_3.4.4-6ubuntu8_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/g/gcc-3.4/gcc-3.4-base_3.4.4-6ubuntu8_i386.deb)
[http://archive.ubuntu.com/ubuntu/pool/multiverse/s/sl-modem/sl-modem-daemon_2.9.10+2.9.9d-6ubuntu1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/multiverse/s/sl-modem/sl-modem-daemon_2.9.10+2.9.9d-6ubuntu1_i386.deb)
[http://archive.ubuntu.com/ubuntu/pool/multiverse/s/sl-modem/sl-modem-source_2.9.10+2.9.9d-6ubuntu1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/multiverse/s/sl-modem/sl-modem-source_2.9.10+2.9.9d-6ubuntu1_i386.deb)
[http://archive.ubuntu.com/ubuntu/pool/main/d/debconf/debconf-utils_1.4.56ubuntu2_all.deb](http://archive.ubuntu.com/ubuntu/pool/main/d/debconf/debconf-utils_1.4.56ubuntu2_all.deb)
[http://archive.ubuntu.com/ubuntu/pool/main/d/debhelper/debhelper_4.9.5ubuntu1_all.deb](http://archive.ubuntu.com/ubuntu/pool/main/d/debhelper/debhelper_4.9.5ubuntu1_all.deb)
[http://archive.ubuntu.com/ubuntu/pool/main/h/html2text/html2text_1.3.2a-2build1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/h/html2text/html2text_1.3.2a-2build1_i386.deb)
[http://archive.ubuntu.com/ubuntu/pool/main/i/intltool-debian/intltool-debian_0.30+20040213_all.deb](http://archive.ubuntu.com/ubuntu/pool/main/i/intltool-debian/intltool-debian_0.30+20040213_all.deb)
[http://archive.ubuntu.com/ubuntu/pool/universe/m/module-assistant/module-assistant_0.9.5ubuntu1_all.deb](http://archive.ubuntu.com/ubuntu/pool/universe/m/module-assistant/module-assistant_0.9.5ubuntu1_all.deb)
[http://archive.ubuntu.com/ubuntu/pool/main/p/po-debconf/po-debconf_0.8.23_all.deb](http://archive.ubuntu.com/ubuntu/pool/main/p/po-debconf/po-debconf_0.8.23_all.deb)

 - You need to copy these files over into Ubuntu (USB key or CD is probably easiest).  Create a folder on your Desktop and copy the files into that folder.  You then need to setup that folder as a local repository and then you can install the software from there

**Create a local repository**
```
mkdir ~/Desktop/Temp
```
 - Will create a folder called Temp on your Desktop (note the capital 'D')
```
cd ~/Desktop/Temp
sudo apt-get install build-essential
dpkg-scanpackages . /dev/null | gzip -9c > Packages.gz
```
 - Will create a local repository in that Temp folder

 - You should get an output of something like this
```
user@ubuntu:~/Desktop/Temp$ dpkg-scanpackages . /dev/null | gzip -9c > Packages.gz
 ** Packages in archive but missing from override file: **
  cpp-3.4 debconf-utils debhelper gcc-3.4 gcc-3.4-base html2text
  intltool-debian module-assistant po-debconf sl-modem-daemon sl-
  modem-source

 Wrote 11 entries to output Packages file.
user@ubuntu:~/Desktop/Temp$
```
 - Once that is done, you need to add that folder to your source.list
```
sudo gedit /etc/apt/sources.list
```
 - Then add this line
```
deb file:///home/<username>/Desktop/Temp ./
```
 - Substitute <username> with your username

 - Again refresh the repositories ```
sudo apt-get update
```


 - Now we can get down to it


**Install files from local repository**
 - Install your kernel headers (you need these to compile the sl-modem drivers)
```
sudo apt-get install linux-headers-2.6.12-9-386
```
 - Then install gcc-3.4 (the GNU C compiler)
```
sudo apt-get install gcc-3.4
```
 - Finally install the sl-modem-source
```
sudo apt-get install sl-modem-source
```

 - You will probably get asked ```
WARNING: The following packages cannot be authenticated!
  gcc-3.4-base cpp-3.4 gcc-3.4
Install these packages without verification [y/N]?
```
 - Just say Y to this.

**Compile the sl-modem driver**
 - Finally after this is installed you need to actually compile the driver, so first change to the source folder
```
cd /usr/src/
```
 - If you list the contents you will see the linux-headers and sl-modem are in here
```
user@ubuntu:/usr/src$ ls
linux-headers-2.6.12-9/     sl-modem.tar.bz2
linux-headers-2.6.12-9-386/
user@ubuntu:/usr/src$
```
 - To compile the drivers extract the source
```
sudo tar -xvjf sl-modem.tar.bz2
```
 - Change to the drivers folder
```
cd modules/sl-modem/drivers
```
 - Compile the drivers
```
sudo make
sudo make install
```

 - If all goes well then the sl-modem drivers are installed.

 - Lastly install the sl-modem-daemon
```
sudo apt-get install sl-modem-daemon
```


 - Now all you need is to know or someone to tell you how to use the sl-modem-daemon, I couldn't figure it out.  You could always check out [LinModems.org](www.linmodems.org) and see if you can get some help there.

 - Good Luck! Hope that was readable and error free (I pretty much copied all the commands I used when I tried this)

 - Cheers to [blastus](http://ubuntuforums.org/member.php?u=33611) for the HOWTO on getting gcc-3.4 installed offline

---

### Post by stonex on 2006-03-07
OK . I try this way but on step : " sudo apt-get build-essential " follow the error : " built-essential is not recognized ".

I also try manually but I missing some files ( "gettext" and "intltool" ) . What to do now !?

---

### Post by Sutekh on 2006-03-07
[QUOTE=stonex]OK . I try this way but on step : " sudo apt-get build-essential " follow the error : " built-essential is not recognized ".

I also try manually but I missing some files ( "gettext" and "intltool" ) . What to do now !?[/QUOTE]
My bad (I was bound to make a typo)

It should be ```
sudo apt-get **install** build-essential
```

Keep following the instructions, gettext and intltool will fall in line.

---

### Post by stonex on 2006-03-08
OK . It goes this way : I was install manually 13 packages , but finallyon the last step ( installing modem driver sl-modem-daemon_2.9.9 ) Ubuntu says it is wrong driver and i must have sl-modem-modules-2.6.12-9-386 but i can't find that's like . What should i do now ?

---

