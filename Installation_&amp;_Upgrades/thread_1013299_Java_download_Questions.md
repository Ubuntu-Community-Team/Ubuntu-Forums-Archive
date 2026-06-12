---
title: "Java download Questions"
date: 2008-12-16
forum: Installation &amp; Upgrades
---

### Post by KE4AVB on 2008-12-16
I would to install Java version 6 update 11 on Ubuntu 8.04 LTS. Which version do I need to download? The Linux RPM or Linux packages; the Sun site both versions. Is there additional instruction at are not listed on their site?

I am slowly getting the hang of this different type installations. Windows software had installers with most of their versions.

KE4AVB

---

### Post by ibutho on 2008-12-16
For Ubuntu, do not download the *rpm.bin package because thats for distributions like Fedora, openSUSE and Mandriva which are rpm based. The ordinary *bin file will work on ay distro.

---

### Post by taurus on 2008-12-16
You want the .bin (not .rpm.bin) version.  When you save it to your computer, it will be saved to ~/Desktop so you need to move it somewhere like /opt and unpack it from there before you can use it.

```
cd ~/Desktop
chmod 755 filename.bin
sudo mv filename.bin /opt
cd /opt
sudo ./filename.bin
sudo update-alternatives --config java
```

---

### Post by jamesstansell on 2008-12-16
> **taurus said:**
> You want the .bin (not .rpm.bin) version.  When you save it to your computer, it will be saved to ~/Desktop so you need to move it somewhere like /opt and unpack it from there before you can use it.

```
cd ~/Desktop
chmod 755 filename.bin
sudo mv filename.bin /opt
cd /opt
sudo ./filename.bin
sudo update-alternatives --config java
```

That last line won't work in this case because it is for java alternatives installed from the package repositories.

In the particular case of java it's possible to download the 6u11 deb files from the jaunty (ubuntu 9.04) repository and use dpkg -i to install the packages.  It's exactly the same binaries as Sun puts in their .bin files, but delivered in the friendly .deb packaging.

@KE4AVB, do you want 6u11 for your browser or just for a command-line app?

P.S. I _think_ I may have read where someone got a non-packaged JRE to show up in his "update-alternatives --config java" options but I don't have a reference right now.

---

### Post by ibutho on 2008-12-17
> **jamesstansell said:**
> That last line won't work in this case because it is for java alternatives installed from the package repositories.

In the particular case of java it's possible to download the 6u11 deb files from the jaunty (ubuntu 9.04) repository and use dpkg -i to install the packages.  It's exactly the same binaries as Sun puts in their .bin files, but delivered in the friendly .deb packaging.

@KE4AVB, do you want 6u11 for your browser or just for a command-line app?

P.S. I _think_ I may have read where someone got a non-packaged JRE to show up in his "update-alternatives --config java" options but I don't have a reference right now.

Its possible to have a version of java that is not installed from the repos to show up in your alternatives. You can do something like
```
sudo alternatives --install /usr/bin/java java /usr/java/jdk1.6.0_10/bin/java 2
sudo update-alternatives --config java

```

---

### Post by KE4AVB on 2008-12-24
Sorry taking so to respond to this thread. I have been out with sever Bronchitis. I did manage to install Java 6-07 here. I was needing Java for viewing a local weather page here. I will do some more reading here on how use the repositories and how to add new ones. Thanks for all the suggestions and will copy this thread to a file here for reference.


KE4AVB

---

