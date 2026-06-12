---
title: "sun java 6 ?? file &quot;owned by root.root and copied to /tmp"
date: 2008-12-17
forum: Installation &amp; Upgrades
---

### Post by rpete on 2008-12-17
Hi, I have read many threads on sun java problems and posted earlier on this without a solution. Anyone who can help please stay with me until it works. Sun java 6 bin is shaded in synaptics and is checked in applications add/remove.  I have the file but can't get it working. When I perform many operations I get the message below: 


richard@dell-desktop:~$ sudo apt-get install sun-java6-jdk
Reading package lists... Done
Building dependency tree       
Reading state information... Done
sun-java6-jdk is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 6 not upgraded.
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




I don't know how to make the file I downloaded owned by root.root and then copy it to /tmp.  

This problem with java affects my installing third party software and I also get this message when installing ubuntu updates.  Please help!

---

### Post by joff13 on 2008-12-17
hi

it's just talking about java documentation, this shouldn't be a problem.

anyway, i think the quick way is to open synaptic and flag java to be completely removed 

then check if there are some pending stuff with apt-get

and finally install java again

---

### Post by rpete on 2008-12-17
Hi, when I tried to remove sun java I got the same message as above and was asked to retry or abort. But now sun java 6-bin is unchecked in synaptics and it unchecked in add/remove so what is the next step with apt-get?

---

### Post by dtower on 2009-03-31
I have the exact same problem, with the exact same message. Please help. This happens every time I try to do any kind of update.

Thanks!

---

### Post by harrypiper on 2009-08-19
Before you copy jdk-6u10-docs.zip to /tmp, you have to change owner and owner group of downloaded file using command "chown".
For example: "sudo chown root:root jdk-6u10-docs.zip". Then copy file to /tmp directory: "sudo cp jdk-6u10-docs.zip /tmp". And then press "Enter" in Synaptic or Terminal.

---

