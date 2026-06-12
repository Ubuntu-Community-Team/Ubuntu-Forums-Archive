---
title: "Error when adding new programs"
date: 2009-01-25
forum: Installation &amp; Upgrades
---

### Post by brottmayer on 2009-01-25
Hello,

(If this is in the wrong section of the forum, please move it to the correct place, I have no problem with that.)

I am trying to install the k9copy program from the Add/Remove program. When I hit apply to add the program, I keep getting this error message. I do not know what it means and any help would be greatly appreciated.

Here's the error message:
> 
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.


Thanks,
Brandon.

---

### Post by taurus on 2009-01-25
Close the Add/Remove window.  Then, open a terminal and run

Applications -> Accessories -> Terminal
```
sudo dpkg --configure -a
sudo apt-get update
sudo apt-get install k9copy
```

---

### Post by brottmayer on 2009-01-25
Taurus,

Thanks for responding. I did the command you said, but came up with an error. See below:

```

brottmayer@brottmayer:~$ sudo dpkg --configure -a
[sudo] password for brottmayer: 
Setting up java-common (0.30ubuntu3) ...

Processing triggers for man-db ...
Processing triggers for doc-base ...
Processing 2 added doc-base file(s)...
Registering documents with scrollkeeper...
brottmayer@brottmayer:~$ sudo apt-get update
Hit http://mx.archive.ubuntu.com intrepid Release.gpg
Ign http://mx.archive.ubuntu.com intrepid/main Translation-en_US
Hit http://security.ubuntu.com intrepid-security Release.gpg
Ign http://security.ubuntu.com intrepid-security/main Translation-en_US
Ign http://mx.archive.ubuntu.com intrepid/restricted Translation-en_US
Ign http://mx.archive.ubuntu.com intrepid/universe Translation-en_US
Ign http://mx.archive.ubuntu.com intrepid/multiverse Translation-en_US
Hit http://mx.archive.ubuntu.com intrepid-updates Release.gpg
Ign http://mx.archive.ubuntu.com intrepid-updates/main Translation-en_US
Ign http://mx.archive.ubuntu.com intrepid-updates/restricted Translation-en_US
Ign http://mx.archive.ubuntu.com intrepid-updates/universe Translation-en_US
Ign http://mx.archive.ubuntu.com intrepid-updates/multiverse Translation-en_US
Ign http://security.ubuntu.com intrepid-security/restricted Translation-en_US
Ign http://security.ubuntu.com intrepid-security/universe Translation-en_US
Ign http://security.ubuntu.com intrepid-security/multiverse Translation-en_US
Hit http://security.ubuntu.com intrepid-security Release
Hit http://mx.archive.ubuntu.com intrepid Release
Hit http://mx.archive.ubuntu.com intrepid-updates Release           
Hit http://security.ubuntu.com intrepid-security/main Packages
Hit http://mx.archive.ubuntu.com intrepid/main Packages
Hit http://mx.archive.ubuntu.com intrepid/restricted Packages
Hit http://mx.archive.ubuntu.com intrepid/main Sources
Hit http://mx.archive.ubuntu.com intrepid/restricted Sources
Hit http://mx.archive.ubuntu.com intrepid/universe Packages
Hit http://security.ubuntu.com intrepid-security/restricted Packages
Hit http://security.ubuntu.com intrepid-security/main Sources
Hit http://security.ubuntu.com intrepid-security/restricted Sources
Hit http://security.ubuntu.com intrepid-security/universe Packages
Hit http://mx.archive.ubuntu.com intrepid/universe Sources
Hit http://mx.archive.ubuntu.com intrepid/multiverse Packages
Hit http://mx.archive.ubuntu.com intrepid/multiverse Sources
Hit http://mx.archive.ubuntu.com intrepid-updates/main Packages
Hit http://mx.archive.ubuntu.com intrepid-updates/restricted Packages
Hit http://mx.archive.ubuntu.com intrepid-updates/main Sources
Hit http://mx.archive.ubuntu.com intrepid-updates/restricted Sources
Hit http://mx.archive.ubuntu.com intrepid-updates/universe Packages
Hit http://security.ubuntu.com intrepid-security/universe Sources
Hit http://security.ubuntu.com intrepid-security/multiverse Packages
Hit http://security.ubuntu.com intrepid-security/multiverse Sources
Hit http://mx.archive.ubuntu.com intrepid-updates/universe Sources
Hit http://mx.archive.ubuntu.com intrepid-updates/multiverse Packages
Hit http://mx.archive.ubuntu.com intrepid-updates/multiverse Sources
Reading package lists... Done
brottmayer@brottmayer:~$ sudo apt-get install k9copy
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  k9copy: Depends: kdebase-runtime (>= 4:4.0.66) but it is not going to be installed
          Depends: kdelibs5 (>= 4:4.0.98a) but it is not going to be installed
          Depends: libphonon4 (> 4:4.2~) but it is not going to be installed
          Depends: libqt4-opengl (>= 4.4.0) but it is not going to be installed
          Depends: libxine1 (>= 1.1.8) but it is not going to be installed
          Depends: phonon (> 4:4.2~) but it is not going to be installed
          Depends: vamps but it is not going to be installed
          Depends: dvdauthor but it is not going to be installed
          Depends: mencoder but it is not going to be installed
  sun-java6-jre: Depends: sun-java6-bin (= 6-10-0ubuntu2) but it is not going to be installed or
                          ia32-sun-java6-bin (= 6-10-0ubuntu2) but it is not installable
                 Recommends: gsfonts-x11 but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
brottmayer@brottmayer:~$ 

```

Thanks.

---

### Post by taurus on 2009-01-25
```
sudo apt-get -f install
sudo apt-get update
sudo apt-get install k9copy
```

---

### Post by oldos2er on 2009-01-25
Are all your repositories enabled? Check System, Administration, Software Sources.

---

### Post by brottmayer on 2009-01-25
OK I get to this blue screen, and I've been here before, but I do not know how to click the ok button or to ok it and go on?

---

### Post by taurus on 2009-01-25
You are talking about java license screen.  Press the Tab key to highlight the <OK> and Return to accept it.  You need to accept the license before you can install java (Sun) on your machine.

---

### Post by brottmayer on 2009-01-25
@oldos2er: I am sorry I didn't see your message...but...

@taurus: It worked. Thanks for your help with this. Now I know, "TAB" to move around. I had forgotten my dos programming. (It's been a long time!)

Thanks to both,
Brandon.

---

