---
title: "Error while installing broadband client"
date: 2009-06-07
forum: Installation &amp; Upgrades
---

### Post by chirag64 on 2009-06-07
Hello, I'm using sify internet connection on ubuntu 9.04 (which i'm very excited to try, btw :) )

So i try to install the client and this is what my terminal says:

chirag@Chirag:~/Desktop/sify$ sudo ./install.sh
sudo: unable to resolve host Chirag
Sify Broadband Client Installed Successfully
chirag@Chirag:~/Desktop/sify$ sudo ./sifyconnect
sudo: unable to resolve host Chirag
./sifyconnect: error while loading shared libraries: libssl.so.4: cannot open shared object file: No such file or directory

Anyone has any idea how to fix this?

---

### Post by Partyboi2 on 2009-06-07
> sudo: unable to resolve host Chirag
For this check you /etc/hosts
```
gksu gedit /etc/hosts
``` that this part
```
127.0.1.1   Chirag
```
matches the same name as the output to
```
hostname
```
If unsure post the output to
```
cat /etc/hosts
hostname
```
> ./sifyconnect: error while loading shared libraries: libssl.so.4: cannot open shared object file: No such file or directory
Looks like you need to create a symbolic link to get it to work
```
 sudo ln -s /usr/lib/libssl.so /usr/lib/libssl.so.4
```
[http://www.linuxforums.org/forum/690703-post2.html](http://www.linuxforums.org/forum/690703-post2.html)

---

### Post by chirag64 on 2009-06-08
Still didn't work :(
This is what i got.
> chirag@chirag-desktop:~/Desktop/program/sify$ sudo ln -s /usr/lib/libssl.so /usr/lib/libssl.so.4
chirag@chirag-desktop:~/Desktop/program/sify$ sudo ./sifyconnect
./sifyconnect: error while loading shared libraries: libssl.so.4: cannot open shared object file: No such file or directory
chirag@chirag-desktop:~/Desktop/program/sify$ sudo ln -s /usr/lib/libssl.so /usr/lib/libssl.so.4
ln: creating symbolic link `/usr/lib/libssl.so.4': File exists
chirag@chirag-desktop:~/Desktop/program/sify$ sudo ./sifyconnect./sifyconnect: error while loading shared libraries: libssl.so.4: cannot open shared object file: No such file or directory

---

### Post by Partyboi2 on 2009-06-08
Have you got the libssl-dev package installed?
```
apt-cache policy  libssl-dev
```

---

### Post by chirag64 on 2009-06-08
It doesn't come installed with ubuntu?!?

If not, how can I install it?!? Is there any way i can download it from windows and then install the package in ubuntu, since my internet does not work on ubuntu without installing the broadband client in the first place.

---

### Post by Partyboi2 on 2009-06-08
You can go [[COLOR=Blue]here[/COLOR]]("http://packages.ubuntu.com/jaunty/libssl-dev") and download it then copy over to ubuntu and install it by double clicking on it. It may complain about missing dependencies which you will also need to download and install to get libssl-dev installed. You can search for those dependencies (Packages) from [[COLOR=Blue]here[/COLOR]]("http://packages.ubuntu.com/")

---

### Post by chirag64 on 2009-06-08
I downloaded and installed [[COLOR="Blue"]this package[/COLOR]]("http://packages.ubuntu.com/jaunty/i386/libssl0.9.8/download"), but it still gives the same error as above ](*,)

---

### Post by Partyboi2 on 2009-06-08
Have you installed  libssl-dev? 

[B]
[/B]

---

### Post by chirag64 on 2009-06-08
Sorry if this sounds noob, but how do I do that?!?

---

### Post by Partyboi2 on 2009-06-08
Go [[COLOR=Blue]here[/COLOR]]("http://packages.ubuntu.com/jaunty/i386/libssl-dev/download")  and choose a mirror and download the package, then take it to your Ubuntu installation and double click on it to install.

---

### Post by chirag64 on 2009-06-08
Downloaded and installed the package, needed to download and install another package named
zlib1g-dev_1.2.3.3.dfsg-12ubuntu2_i386.deb

Now i get the following error

> chirag@chirag-desktop:~/Desktop/program/sify$ sudo ./sifyconnect
./sifyconnect: error while loading shared libraries: libcrypto.so.4: cannot open shared object file: No such file or directory

Now which package to get?!? :|

---

### Post by Partyboi2 on 2009-06-08
All you should need to do is create another symbolic link, so open a terminal and type 
```
 sudo ln -s /usr/lib/libcrypto.so /usr/lib/libcrypto.so.4
```

---

### Post by chirag64 on 2009-06-09
Wow. It worked. Thnx a lot for ur patience :D

---

### Post by chirag64 on 2009-06-09
Now if only i could get a desktop shortcut for it?!? :D

---

### Post by Partyboi2 on 2009-06-09
Right click on your Desktop and select "Create Launcher" then change "Type" to "Application in Terminal"  for "Name" put in "Sifyconnect" and for "Command" put "/usr/bin/sifyconnect" (Do not add the quotes)
Then see if it works. :)

---

### Post by chirag64 on 2009-06-09
There was an error creating the child process for this terminal

---

