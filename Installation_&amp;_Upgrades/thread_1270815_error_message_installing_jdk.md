---
title: "error message installing jdk"
date: 2009-09-20
forum: Installation &amp; Upgrades
---

### Post by nmthien on 2009-09-20
I tried to install jdk 6 on my ubuntu, using sudo apt-get install sun-java6-jdk, but it took forever to do the configure stuff with a stupid screen, and I didn't know how to stop it so I quit the terminal. Now every time I try to reinstall it, I get the error message:

Errors were encountered while processing:
 /var/cache/apt/archives/sun-java6-jre_6-16-0ubuntu1.9.04_all.deb
 /var/cache/apt/archives/sun-java6-bin_6-16-0ubuntu1.9.04_i386.deb
 /var/cache/apt/archives/sun-java6-jdk_6-16-0ubuntu1.9.04_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

I try to remove all the files sun-java6* in the archives folder and download and install them again, but still get the same message, also try to do the sudo apt-get -f install and sudo dpkg --configure -a, but it doesn't change anything.

What should I do to fix this?
And then, if it'll be fixed and I want to install jdk, am I supposed to wait such a long time for the configuration stuff?

Thank you very much!

---

### Post by Partyboi2 on 2009-09-20
Open a terminal and run
```
sudo dpkg --configure -a
```
You may need to except the license  agreement, by pressing 'Tab' till 'ok' is highlighted then 'enter'

---

### Post by nmthien on 2009-09-20
yes I did it but it didn't work still.

I got the license part, thank you :-)

---

### Post by Partyboi2 on 2009-09-20
Can you post the output to
```
sudo dpkg --configure -a
```

---

