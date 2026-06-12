---
title: "Can't Install Open Office"
date: 2008-12-03
forum: Installation &amp; Upgrades
---

### Post by Stvnx7 on 2008-12-03
Hello all. 

I am having problems installing Open Office 3.0 on my ubuntu desktop. I believe I broke something, so I will detail how this came about. 

I wanted to try the new KDE4, so I followed the steps outlined at [this website]("http://www.psychocats.net/ubuntu/kde"). Pretty much, consisted of editing repositories and typing in "sudo apt-get install kde-desktop." 

I didn't like KDE, so I uninstalled it using the method outlined [here]("http://www.psychocats.net/ubuntu/puregnome"). 

Now, I can't get Open Office to install. I've tried "sudo apt-get install openoffice.org," but I get an error. The error can be viewed [here]("http://paste.ubuntu.com/79595/").

I've tried installing ubuntu-desktop, even using "sudo apt-get --reinstall install ubuntu-destkop" but that has not worked. 

I've tried installing from the .deb source, using the instructions at [this website]("http://www.akemapa.com/2008/11/21/install-openoffice-3-from-source-on-ubuntu-linux/"), and I get no error, when installing, but also no Open Office. 

This is my [source.list file]("http://paste.ubuntu.com/79604/"), the one that apt-get is using.

I've made sure to use "sudo apt-get update" and "sudo apt-get upgrade." 

Any help is greatly appreciated. I would like specifically to: 

Purge the system of **any and all** Open Office installation files, and related files. Then, I'd like to be able to install Open Office. 

Thanks!

Hope you guys can help.

---

### Post by inobe on 2008-12-03
a very easy tutorial

[http://tombuntu.com/index.php/2008/10/14/install-openofficeorg-30-in-ubuntu-804-and-810/](http://tombuntu.com/index.php/2008/10/14/install-openofficeorg-30-in-ubuntu-804-and-810/)

during the setup' you will be opted to remove OO, that is your choice.

---

### Post by reddyschintu on 2008-12-03
same problem but i can insatll but its not responding after the complete dilouge

---

### Post by abn91c on 2008-12-03
if you are using the ppa launchpad repositories, they are offline now because of some kind of bug with gnome. they will be reposted later

here is a guide on how to install: [http://news.softpedia.com/news/How-To-Install-OpenOffice-org-3-0-in-Ubuntu-8-10-96449.shtml](http://news.softpedia.com/news/How-To-Install-OpenOffice-org-3-0-in-Ubuntu-8-10-96449.shtml)

here is the message about the bug: [https://launchpad.net/~openoffice-pkgs/+archive](https://launchpad.net/~openoffice-pkgs/+archive)

---

### Post by Stvnx7 on 2008-12-04
> **inobe said:**
> a very easy tutorial

[http://tombuntu.com/index.php/2008/10/14/install-openofficeorg-30-in-ubuntu-804-and-810/](http://tombuntu.com/index.php/2008/10/14/install-openofficeorg-30-in-ubuntu-804-and-810/)

during the setup' you will be opted to remove OO, that is your choice.

I followed the steps and everything seemed to work without a hitch. I was even able to install the menu icons. However, whenever I try to open Open Office Writer, I end up getting an error saying that the program has crashed. 

Where do I go from here?

---

### Post by The Big Chow Mein on 2009-02-18
> **inobe said:**
> a very easy tutorial

[http://tombuntu.com/index.php/2008/10/14/install-openofficeorg-30-in-ubuntu-804-and-810/](http://tombuntu.com/index.php/2008/10/14/install-openofficeorg-30-in-ubuntu-804-and-810/)

during the setup' you will be opted to remove OO, that is your choice.

It might be a very easy tutorial, but i still managed to go wrong : (

I have removed all of open office from my system and downloaded the OO3 package but when i got hrough the tutorial i get this error message:

```
ryan@Thor:~$ sudo dpkg -i ~/Desktop/OOO300_m15_native_packed-1_en-US.9379/DEBS/*.deb
dpkg: error processing /home/ryan/Desktop/OOO300_m15_native_packed-1_en-US.9379/DEBS/*.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 /home/ryan/Desktop/OOO300_m15_native_packed-1_en-US.9379/DEBS/*.de
```

But i am fairly sure it is there:

```

ryan@Thor:~$ cd /home/ryan/Desktop/
ryan@Thor:~/Desktop$ ls
key
OOO300_m15_native_packed-1_en-US.9379
OOo_3.0.1_LinuxIntel_install_en-US.tar.gz
ryan@Thor:~/Desktop$ 
```

i am still new to Linux, but im not sure where i am going wrong.

Any help is much appreciated!


EDIT: Thanks to anyone who had a look, but I have downloaded the package from sun (instead of a virgin media mirror) and found that i get a different file. This one came with a handy install text that i just ran in a terminal and everything went fine.

Thanks again.

---

