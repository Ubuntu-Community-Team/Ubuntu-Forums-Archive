---
title: "Expert(s) wanted - eagle-usb and gcc version..."
date: 2006-02-16
forum: Installation &amp; Upgrades
---

### Post by chrisav on 2006-02-16
Hello,

I've just installed Ubuntu on a computer.

First of all I have OpenOffice.org 2 and Firefox in English and I would like them to be in French.
I suppose I have to uninstall the versions already here before installing the new ones. Or is it easier to just add French files and how from cd or usb key?
The problem is that my modem doesn't work on Ubuntu.
So how do I uninstall, and then install them from usb key or cd? And where can I find them for Ubuntu?

The Biggest problem I have now is that my modem is a Sagem Fast 800 (I have  downloaded with another computer the Fast8x0_3-0-6.tgz file with the eagle-usb driver for linux.

But As I have read and noticed the problem is the version of the gcc.
I have to download and install gcc-3.4, gcc-3.4-base et cpp-3.4 and I suppose that I also have to uninstall gcc packages version 4, but which ones exactly and before or after installing version 3.4 files.
And what about the dependencies. I don't want to uninstall files or packages that musn't be uninstalled with gcc-4.0 and other version 4 files. 

It would be so simple ;) if there wasn't this gcc issue existing from the beginning. If I cannot do this, I cannot make my internet connexion work and so on...

All I need is a simple desktop computer working with OpenOffice.org 2 and Firefox in French and an internet connexion for my mother :) .

Thanks for all the help (I don't want my mother, who knows nothing about computers, to start on Win...ws).
Chris.

---

### Post by christhemonkey on 2006-02-16
To unninstall something, you can either just uncheck it in synaptic.
Or from a terminal
```
sudo dpkg -r nameofpackage
```

To install new packages, i would copy them off your usbstick, then put them in a folder called mydebs or similar, thenfrom a terminal:
```
cd /directory/of/whatever/you/called/the/folder
```
and then:
```
sudo dpkg -i ./thenameofpackage.deb
```

Please note, that this only works for files of sort .deb, which is most all in the repositories.  For .tgz files you must do something like:
```
sudo tar -ufg ./whatever.tgz
```
(cant remember the exact options for .tgz files, try reading man tar and replacing -ufg with whatever you think it should be)

---

### Post by christhemonkey on 2006-02-16
Oh, and for the french language Openoffice
In synaptic i think there are french-locales for openoffice2.
Just download and install them by the above method!

PS you dont have to uninstall gcc4 if you want gcc3.4 as well, they coexist on the same system.

---

### Post by chrisav on 2006-02-16
I am a complete newbie concerning GNU/Linux and Ubuntu but following the instructions given for instance on page [http://ubuntuforums.org/archive/index.php/t-79896.html](http://ubuntuforums.org/archive/index.php/t-79896.html) , I have managed to add cpp-3.4_3.4.4-6ubuntu8_i386.deb, gcc-3.4_3.4.4-6ubuntu8_i386.deb and gcc-3.4-base_3.4.4-6ubuntu8_i386.deb.

Now I can also see these packages in the synaptic "manager" although they are not "authentified".

I have also downloaded gu-Linux_fr.pdf (French version for eagle-usb information from the sagem website).

Everything worked fine until the step when I tried to use "./configure". If I remember well, almost every line answered "yes"... but at the end there was the message "error: kernel-sources cannot be found!" 

And of course after this if I try to use "make" I only have error messages on every line appearing.

I need to do all this because I am using a Sagem Fast 800 usb modem.

I need help as I don't know anything about linux commands except the ones I've just learned from the posts on this forum(s) and from help given in documents.

Thanks in advance.
Chris.

---

### Post by christhemonkey on 2006-02-17
you need to get the kernel-sources package.

---

### Post by chrisav on 2006-02-17
Hello,

Can you please tell me the name and version of the kernel-sources package I need to install?
 
Do I install it the same way than the other packages that I've already installed?

Thanks.
Chris.

NB : can I ask you in which part of the Earth you are living, in which country?

---

### Post by christhemonkey on 2006-02-18
I live in England. :D
What about you? Obviously somewhere that speaks french!

[http://packages.ubuntu.com/breezy/devel/kernel-source-2.6.10](http://packages.ubuntu.com/breezy/devel/kernel-source-2.6.10)
That one if you use breezys standard kernel.
And just use the same commands as before!
(it depends on binutils and bzip2 packages, but they should be installed by default)

---

### Post by chrisav on 2006-02-23
Hello,

I have copied kernel-source-2.6.10_2.6.10.orig.tar.gz in /usr/src and unpacked it there. It seemed to work.
Then again with the command line I copied Fast8x0_3-0-6.tgz in /usr/src and unpacked it. I then went to /usr/src/eagle-usb/eagle-usb-src and wrote "sudo ./configure" but I once more received at the end the message "error: kernel-sources cannot be found!".
I don't know what I did wrong. Do I have to do something special with the directory "kernel-source-2.6.10_2.6.10"? Like configure, make or install?


Thanks for help.
Chris. A complete beginner.

---

### Post by chrisav on 2006-02-24
Hello,

Can someone help me for this issue that is preventing me from using ubuntu linux?!

Thanks.
Chris.

---

### Post by christhemonkey on 2006-02-24
Hmm, im not too sure anymore.
Maybe you need a symbolic link to your sources;
```
sudo ln -s /usr/src/kernel-source-2.6.10_2.6.10 linux
```

---

### Post by chrisav on 2006-02-24
Hello again,

Just one precision needed: I have used the command uname -r and the answer was 2.6.12-9-386. 

At [http://packages.ubuntu.com/breezy/devel/](http://packages.ubuntu.com/breezy/devel/)  I can only see:

linux-headers-2.6.12-9-386 (2.6.12-9.23)
    Linux kernel headers 2.6.12 on 386

and not the kernel sources.

can I still use kernel-source-2.6.10 (2.6.10-6) or is it a problem?

I am going to try to install the eagle-usb driver with the debs, perhaps it's easier?

Chris.

---

### Post by christhemonkey on 2006-02-24
Its a different kernel revision so probably is a problem.
The eagle-usb driver in breezy did not work at all for me.
(yet in hoary in worked fine!)

---

### Post by chrisav on 2006-02-26
Hello,

I finally managed to connect to the Internet with eagle-usb-2.3.2.tar.bz2 unpacked and installed in /opt/eagle-usb-2.3.2.

Before I installed the 3 linux-headers-* packages from Synaptic. I don't know if it was necessary to install all of them.

Now I would like to know how to create a way to connect to and disconnect from the Internet without using the command line, just by clicking a link for instance.

Thanks.
Chris.

---

