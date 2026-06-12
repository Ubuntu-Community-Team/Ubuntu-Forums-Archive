---
title: "Installing Eremove"
date: 2009-06-01
forum: Installation &amp; Upgrades
---

### Post by lotster on 2009-06-01
Hi! I downloaded Eremove (a POP3 E-mail remover) because I get lots of unnecessary e-mails that simply eat up my bandwidth.  I used the Windows version of Eremove for quite some time, but now I want to make the switch to Ubuntu permanently.  So I downloaded Eremove for Linux, and inside it there's a readme file that says the following:

> "Currently, it's pretty no frills in the compiling department.
Ensure you have gtk 1.x and the gtk headers installed somewhere, and then 
simply :

    make
    make install

This will compile eremove, and install it to /usr/local/bin

RUNNING
--

To run Email Remover, simply run the command :
    
    eremove"

That's the closest thing I get to installation instructions.  Any ideas about how I can get it installed?  I tried the "make" and "make install" commands in the terminal, but it keeps on giving me error messages...

Thanks!

---

### Post by lake54 on 2009-06-01
I'm new to Linux as well, so I'm hazarding a guess at what I've seen so far:

Have you tried running the terminal from the folder (i.e. changing directory) and trying the commands from there? Also how about using sudo make etc...

Sorry if that's all wrong

James

---

### Post by Partyboi2 on 2009-06-01
Hi, open a terminal (Applications>Accessories>Terminal) and install libgtk1.2-dev
```
sudo apt-get install  libgtk1.2-dev
``` Then  change to where you have downloaded the eremove-bin-1.4.tar.gz file, so for example if you downloaded it to the Desktop type
```
cd ~/Desktop
```then extract it with
```
tar xvzf eremove-bin-1.4.tar.gz
```then change into the newly created source directory with
```
cd eremove
``` then run the program with
```
./eremove
``` If you downloaded the eremove-src-1.4.tar.gz one instead you would need to install the build-essential package as well
```
sudo apt-get install build-essential
```then follow the above steps except the last one instead of typing ./eremove you would type
```
make
sudo make install
```

---

### Post by lotster on 2009-06-01
Most excellent!  Thanks for the help!  I tried extracting it using the GUI extractor previously, and tried to run it from the gui, but it wouldn't run.  Now it's sorted!  Thanks a million!

---

