---
title: "software in applications list but not opening/cd ./configure not working"
date: 2008-12-15
forum: Installation &amp; Upgrades
---

### Post by rpete on 2008-12-15
Hi, I have two problems with installing software and applications.  I downloaded the software program :confused:handbrake as a .deb file and installed it. It appears in my applications list under sound and video but when I click on the icon nothing happens. I downloaded it to my desktop and when I right click on the folder and click open nothing happens. In terminal I get to $handbrake and type ./configure and get "no such file or directory". Also, two .tar files I extracted and then in terminal tried to configure by "cd Desktop" , "ls" "cd <filename>" and "$<filename> ./configure" and it didn't work.

---

### Post by taurus on 2008-12-15
What is the exact name and where did you download it?

---

### Post by rpete on 2008-12-15
> **taurus said:**
> What is the exact name and where did you download it?
It is called handbrake and I downloaded it from [http://handbrake.fr](http://handbrake.fr)

---

### Post by taurus on 2008-12-15
There is no configure if you downloaded the source, HandBrake-0.9.3.tar.gz.  Instead, you just change into the directory, HandBrake-0.9.3, and run "make" to build it.

Otherwise, you can download the binary for Ubuntu.  Which version did you download, GUI or CLI?

---

### Post by rpete on 2008-12-15
> **taurus said:**
> There is no configure if you downloaded the source, HandBrake-0.9.3.tar.gz.  Instead, you just change into the directory, HandBrake-0.9.3, and run "make" to build it.

Otherwise, you can download the binary for Ubuntu.  Which version did you download, GUI or CLI?
I got the GUI.  Can you list the commands to "make" it?  I've done it once or twice but haven't got it memorized.

---

### Post by taurus on 2008-12-15
```
cd ~/Desktop
tar xvzf HandBrake-0.9.3.tar.gz
cd HandBrake-0.9.3
sudo apt-get update
sudo apt-get install jam  <-- You need this package to build HandBrake.
make
```

---

### Post by rpete on 2008-12-15
> **taurus said:**
> ```
cd ~/Desktop
tar xvzf HandBrake-0.9.3.tar.gz
cd HandBrake-0.9.3
sudo apt-get update
sudo apt-get install jam  <-- You need this package to build HandBrake.
make
```
Hi, I thought I was through, but the sudo apt-get install jam command doesn't finish. I am told I need to download jdk-6-doc.zip from java.sun.com/javase/downloads.  I have this file in synaptic manager and the box is in grey meaning it has been applied. Should I reinstall it?

---

