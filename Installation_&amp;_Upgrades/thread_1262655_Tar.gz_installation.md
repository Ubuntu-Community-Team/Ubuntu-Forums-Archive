---
title: "Tar.gz installation"
date: 2009-09-10
forum: Installation &amp; Upgrades
---

### Post by sennin-sama on 2009-09-10
Hello, I need help with installation of tar.gz packages, after extraction wen ever i run d command "./configure" i get the error message "bash: ./configure: No such file or directory" i don't know wat to do. any help?

---

### Post by lisati on 2009-09-10
You need to do a "cd" to the folder where the extracted data files are before running the ./configure command.

---

### Post by realzippy on 2009-09-10
what are you going to compile?

---

### Post by knepig91 on 2009-09-10
After you completed the ./configure command. Type: make, then: sudo make install, then you are done

---

### Post by zipperback on 2009-09-10
There are usually a couple of different files in the directory when you uncompress a tar.gz file package.

Look for README, INSTALL, and CONFIGURE

Read those, as those usually have some very specific installation information for the application you are trying to install.

Also, you will need to be in the directory that you just uncompressed your files to when you are executing the ./configure command.

So if you uncompressed filename.tar.gz on your desktop and the new directory is called "filename", you would open a terminal window and change to that directory with the following command:

```

cd ~/Desktop/filename

```

Then you should be able to compile and install the application as you normally would.

It would be easier though, if you installed the application in question using a .deb package from either one of the repositories or see if the developer has a .deb package for Ubuntu available for download.

- zipperback
:popcorn:

---

### Post by karthick87 on 2009-09-10
Before compiling you  have to install build-essential by running this command in terminal "sudo apt-get install build-essential" it is used for compiling..

---

