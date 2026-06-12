---
title: "error message installing jdk"
date: 2008-12-15
forum: Installation &amp; Upgrades
---

### Post by rpete on 2008-12-15
Hi, I have downloaded java development kit 6 as a .bin file. Somewhere in it is jdk-6-doc-ja.zip and jdk-6-doc.zip which I need to run several programs including handbrake. I also wanted to install an application for viewing dvd called libdvdcss2.  With handbrake and with this app I got the same error message:


richard@dell-desktop:~$ sudo apt-get install libdvdcss2
[sudo] password for richard: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libdvdcss2 is already the newest version.
libdvdcss2 set to manually installed.
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up sun-java6-doc (6-07-3ubuntu2) ...
This package is an installer package, it does not actually contain the
JDK documentation.  You will need to go download one of the
archives:

    jdk-6-doc.zip jdk-6-doc-ja.zip

(choose the non-update version if this is the first installation).
Please visit

    [http://java.sun.com/javase/downloads/](http://java.sun.com/javase/downloads/)

now and download.  The file should be owned by root.root and be copied
to /tmp.

[Press RETURN to try again, 'no' + RETURN to abort] no
Abort installation of JDK documentation
dpkg: error processing sun-java6-doc (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 sun-java6-doc
E: Sub-process /usr/bin/dpkg returned an error code (1)
richard@dell-desktop:~$ 


The part about the message I don't understand is "the file should be owned by root.root and be copied to /tmp.  How do I do these? The jdk file has been downloaded and is on my desktop as a .bin file    right click, properties, permissions, check execute, double click does not work.

---

### Post by ibutho on 2008-12-15
You need to download the required file from the sun java website as indicated above. Save it somewhere in your home directory. Go to Applications -> Accessories -> Terminal and copy the file to /tmp and make it owned by root e.g.
```
sudo cp /home/someuser/jdk-6-doc.zip /tmp/.
chown root:root /tmp/jdk-6-doc.zip
```
After that try reinstalling the package.

---

### Post by rpete on 2008-12-16
> **ibutho said:**
> You need to download the required file from the sun java website as indicated above. Save it somewhere in your home directory. Go to Applications -> Accessories -> Terminal and copy the file to /tmp and make it owned by root e.g.
```
sudo cp /home/someuser/jdk-6-doc.zip /tmp/.
chown root:root /tmp/jdk-6-doc.zip jdk-6-doc-ja.zip
```
After that try reinstalling the package.
Hi Ibutho. I am new to linux so I'm not familiar with the conventions for command lines. For example, I guessed I should replace "someuser" in your command to my user name. I am also not sure how to enter the two command lines. I guessed I should press enter after the "." in the first line. I did and was asked to enter my password and  then I got the following message. What went wrong? 

richard@dell-desktop:~$ sudo cp /home/richard/jdk-6-doc.zip /tmp/.
[sudo] password for richard: 
cp: cannot stat `/home/richard/jdk-6-doc.zip': No such file or directory
richard@dell-desktop:~$ sudo cp /home/someuser/jdk-6-doc.zip /tmp/.
cp: cannot stat `/home/someuser/jdk-6-doc.zip': No such file or directory
richard@dell-desktop:~$ sudo cp /home/richard/jdk-6-doc.zip /tmp/.
cp: cannot stat `/home/richard/jdk-6-doc.zip': No such file or directory
richard@dell-desktop:~$

---

### Post by ibutho on 2008-12-16
You are correct that you need to replace the paths in my example with the actual paths. Where in your home directory (which is /home/richard in your case) did you put the jdk-6-doc.zip file. The errors being shown on the terminal screen indicate that there is no file named called jdk-6-doc.zip in /home/richard.

---

### Post by rpete on 2008-12-16
It might that I didn't move it correctly. As I looked at the desktop contents along the toolbar was the list of places including home. I dragged the file up to the word home and released it. I went to home and it was listed there. Can I perform the copy to temp from desktop where I originally downloaded the file?

---

