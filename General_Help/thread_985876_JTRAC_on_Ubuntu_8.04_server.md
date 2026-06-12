---
title: "JTRAC on Ubuntu 8.04 server"
date: 2008-11-18
forum: General Help
---

### Post by dummzeuch on 2008-11-18
Hi,

I have just been tasked to install JTRAC for a company of around 25 employees on an ubuntu 8.04 based file server.

From what I got from the JTRAC homepage it seems to be a Java application that supposedly should run fine on Linux. But the project seems to lean heavily towards Windows:

"If you are not on Windows, you may want to rename the start and stop *.bat files to e.g. *.sh for Linux (*.bat is reported to work for Ubuntu). The commands within the batch files will work unchanged as long as Java has been installed correctly i.e. "java" is in the PATH and it is the expected 1.5 or greater version. You may need to do things like apply executable permissions to the batch files on Linux, e.g. "chmod +x *.bat". And also - unless you have "root" permissions, you may face problems starting services on port 80 etc."
(from the [JTRAC homepage]("http://www.jtrac.info/doc/html/installation.html"))

I find that quite worrying, because it sounds as if whoever wrote it has only very limited knowledge of Linux.

Does anybody here have experience with running JTRAC on Ubuntu 8.04 server? Is there maybe even a package for it?

twm

---

### Post by dummzeuch on 2008-11-19
> **dummzeuch said:**
> I have just been tasked to install JTRAC for a company of around 25 employees on an ubuntu 8.04 based file server.


OK, I went ahead and installed it into a VMware virtual machine running ubuntu server 8.04. The installation was a matter of installing the java runtime environment via apt-get, unzipping the JTRAC zip file to a directory, changing the owner to root, renaming the start.bat and stop.bat files to *.sh and making them executable.

I then could start JTRAC with sudo running the start.sh and stop it with the stop.sh script.

In addition I had to write my own init scripts for having it start and stop automatically when the system boots/shuts down. All in all it took around 3 hours, including the VMware and Ubuntu installation.

There is one rather odd thing, though: After stopping JTRAC, it takes quite a while for it to start again. While the first start takes only a few seconds, later on it takes up to a minute to activate the web server.

One question remains: Where in the file system would be the best place to put the JTRAC folder? I have currently put it into
/jtrac
which is definitely not the right place.

twm

---

### Post by ^_Pepe_^ on 2012-04-22
Hi, 

Please can you share the init script?

Thanks in advance

---

