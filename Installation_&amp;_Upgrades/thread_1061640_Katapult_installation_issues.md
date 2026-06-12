---
title: "Katapult installation issues"
date: 2009-02-06
forum: Installation &amp; Upgrades
---

### Post by nabilalk on 2009-02-06
Hello,

I'm having problems with installation of Katapult. 

Using terminal I tried to execute the ./configure command and got this error:


> checking for snprintf... yes
checking for X... configure: error: Can't find X libraries. Please check your installation and add the correct paths!


I was unable to get to the point where I could execute the **make** cmd.

Any ideas how to deal with this error? I would have posted on the Katapult forums, but they appear to be down until further notice Thanks!

-nka

---

### Post by Partyboi2 on 2009-02-06
Try installing the   libx11-dev package
```
sudo apt-get install  libx11-dev
```
Then do  ./configure again.

---

### Post by nabilalk on 2009-02-06
> **Partyboi2 said:**
> Try installing the   libx11-dev package
```
sudo apt-get install  libx11-dev
```
Then do  ./configure again.

Thanks, will give it a shot and post back with the results.

---

### Post by nabilalk on 2009-02-06
> **nabilalk said:**
> Thanks, will give it a shot and post back with the results.

Results: 

> libx11-dev is already the newest version.
libx11-dev set to manually installed.
The following packages were automatically installed and are no longer required:
  libxine1-x xchat-common libburn4 libxcb-xv0 libnotify-bin amarok-common
  libboost-thread1.34.1 libxine1-bin libboost-date-time1.34.1
  deluge-torrent-common ruby1.8 python-openssl libexo-0.3-0 ruby libxcb-shape0
  libtunepimp5 libifp4 thunar-data tcl8.4 xsane-common libxvmc1 libpq5
  libboost-filesystem1.34.1 libisofs6 libxcb-shm0 libnjb5 libthunar-vfs-1-2
  libxine1-console
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 5 not upgraded.

What should I do now?

---

### Post by nabilalk on 2009-02-06
> **nabilalk said:**
> Results: 



What should I do now?

After the previous apt-get install didn't work, I tried 

> sudo apt-get install kdelibs-dev

And voila! That worked. I was able to ./configure, then make, then sudo make install.

Thanks for the help.

Now that I have Katapult installed, how do I get the program to startup with the computer?

---

### Post by Partyboi2 on 2009-02-06
You can add it to "Sessions" (System>Pref>Sessions)

---

