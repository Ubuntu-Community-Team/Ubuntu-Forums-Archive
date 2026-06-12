---
title: "Upgrade evolution"
date: 2009-11-08
forum: Installation &amp; Upgrades
---

### Post by bob brazie on 2009-11-08
I have tried 9.10 but decided to go back to 9.04 for awhile.

9.10 had evolution 2.28.1.

I have downloaded 2.28.1 tar.bz2 to my Ubuntu 9.04 desktop but being so new to Ubuntu I don't know how to upgrade my older version or even know if it is possible.

Maybe there is a command line that would make the up grade if possible easier?

Thanks for any help in advance. Bob.

---

### Post by RedSingularity on 2009-11-08
Extract the file to your Desktop.

In terminal type..........

cd ~/Desktop/evolution-2.28.1

then in terminal......... 

sudo ./configure

then............

make

then..........

sudo make install

---

### Post by bob brazie on 2009-11-08
Could you give me some advise on these commands? Thanks. 

bash: cd: ~home/bob/Desktop/evolution-2.28.1.tar.bz21: No such file or directory
bob@bob-laptop:~$ cd ~home/bob/Desktop/evolution-2.28.1
bash: cd: ~home/bob/Desktop/evolution-2.28.1: No such file or directory
bob@bob-laptop:~$

---

### Post by RedSingularity on 2009-11-08
Have you extracted the tar file to the desktop?  You cant cd to a tar file.  You need to get the folder out.

---

### Post by bob brazie on 2009-11-08
I see........

I'm pretty new to this.

I get this error, any idea what it means?


checking for perl... /usr/bin/perl
configure: error: You need bison to build Evolution
bob@bob-laptop:~/Desktop/evolution-2.28.1$

---

### Post by RedSingularity on 2009-11-08
Try doing this........

sudo apt-get install bison

---

### Post by RedSingularity on 2009-11-08
Any other errors?  These errors are expected.  They are telling you what needs to be installed to run evolution.

---

### Post by bob brazie on 2009-11-08
<g>

Then I get this: checking for intltool >= 0.35.5... ./configure: line 6436: intltool-update: command not found
 found
configure: error: Your intltool is too old.  You need intltool 0.35.5 or later.
bob@bob-laptop:~/Desktop/evolution-2.28.1$

---

### Post by RedSingularity on 2009-11-08
Do you have the older evolution installed?  

sudo apt-get install evolution

---

### Post by bob brazie on 2009-11-08
No other errors. Does that mean I can't upgrade to the new version then?

---

### Post by bob brazie on 2009-11-08
Yes I have version 2.26.1 installed.

---

### Post by RedSingularity on 2009-11-08
Yes sir.

Do...............

make

then.........

sudo make install

---

### Post by bob brazie on 2009-11-08
bob@bob-laptop:~$ sudo apt-get install evolution
Reading package lists... Done
Building dependency tree       
Reading state information... Done
evolution is already the newest version.
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.28-11 linux-headers-2.6.28-11-generic
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
bob@bob-laptop:~$

---

### Post by RedSingularity on 2009-11-08
> **RedSingularity said:**
> Extract the file to your Desktop.

In terminal type..........

cd ~/Desktop/evolution-2.28.1

then in terminal......... 

sudo ./configure

then............

make

then..........

sudo make install

Now that there are no errors do this from the "make" part

---

### Post by bob brazie on 2009-11-08
Yes sir.

Do...............

make

then.........

sudo make install

I am not sure what/where the first "make" is supposed to go.

---

### Post by RedSingularity on 2009-11-08
Oh just follow the above instructions from the beginning and it will be easier.

---

### Post by bob brazie on 2009-11-08
Sorry.........

checking for intltool >= 0.35.5... ./configure: line 6436: intltool-update: command not found
 found
configure: error: Your intltool is too old.  You need intltool 0.35.5 or later.
bob@bob-laptop:~/Desktop/evolution-2.28.1$ make
make: *** No targets specified and no makefile found.  Stop.
bob@bob-laptop:~/Desktop/evolution-2.28.1$ 
bob@bob-laptop:~/Desktop/evolution-2.28.1$ sudo make install
make: *** No rule to make target `install'.  Stop.
bob@bob-laptop:~/Desktop/evolution-2.28.1$

---

### Post by RedSingularity on 2009-11-08
Is this a fresh install of ubuntu?

---

### Post by bob brazie on 2009-11-08
I think I am in over my head. <g>

---

### Post by bob brazie on 2009-11-08
Yes, I reinstalled 9.04 after having some problems with 9.10.

---

### Post by RedSingularity on 2009-11-08
No way.  You can get it!

---

### Post by RedSingularity on 2009-11-08
Have you done all the upgrades yet?

---

### Post by bob brazie on 2009-11-08
everyone of them.

---

### Post by RedSingularity on 2009-11-08
Check to see if you have intltool installed.

sudo apt-get install intltool

---

### Post by bob brazie on 2009-11-08
It was not but is being installed now.

---

### Post by RedSingularity on 2009-11-08
Good then try the configure command again when its done.

---

### Post by bob brazie on 2009-11-08
checking for GNOME_PLATFORM... configure: error: Package requirements (glib-2.0 >= 2.20.0
	gtk+-2.0 >= 2.16.0
	gconf-2.0 >= 2.0.0
	libbonobo-2.0 >= 2.20.3
	libbonoboui-2.0 >= 2.4.2
	libglade-2.0 >= 2.0.0
	libgnomecanvas-2.0 >= 2.0.0
	libgnomeui-2.0 >= 2.0.0
	libxml-2.0 >= 2.7.3
	shared-mime-info >= 0.22
	gnome-desktop-2.0 >= 2.26.0) were not met:

No package 'glib-2.0' found
No package 'gtk+-2.0' found
No package 'gconf-2.0' found
No package 'libbonobo-2.0' found
No package 'libbonoboui-2.0' found
No package 'libglade-2.0' found
No package 'libgnomecanvas-2.0' found
No package 'libgnomeui-2.0' found
No package 'libxml-2.0' found
No package 'gnome-desktop-2.0' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables GNOME_PLATFORM_CFLAGS
and GNOME_PLATFORM_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

bob@bob-laptop:~/Desktop/evolution-2.28.1$ 


I'm thinking it can't be installed in 9.04?

---

### Post by RedSingularity on 2009-11-08
I think you are correct good sir!  Lol sorry.   :lolflag:

---

### Post by bob brazie on 2009-11-08
Sorry to waste your time but I did learn a bunch!!

Bob.

---

### Post by RedSingularity on 2009-11-08
No way buddy!  You didnt waste my time!!  Happy to help.  And i learned something too.  :)

---

