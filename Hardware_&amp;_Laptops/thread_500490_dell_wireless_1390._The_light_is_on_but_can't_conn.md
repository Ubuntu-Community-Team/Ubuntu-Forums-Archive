---
title: "dell wireless 1390. The light is on but can't connect to Internet"
date: 2007-07-13
forum: Hardware &amp; Laptops
---

### Post by duydaniel on 2007-07-13
Hello.

I am trying to install the wireless Dell 1390 from the website:
[https://help.ubuntu.com/community/WifiDocs/Driver/1390?highlight=%28WifiDocs%2FDriver%29](https://help.ubuntu.com/community/WifiDocs/Driver/1390?highlight=%28WifiDocs%2FDriver%29)

But there is something wrong at the last step:

```
root@daniel-laptop:/home/daniel/DRIVER# sudo ndiswrapper -i bcmwl5.inf
driver bcmwl5 is already installed
root@daniel-laptop:/home/daniel/DRIVER# sudo ndiswrapper -l
bcmw5 : invalid driver!
bcmwl5 : invalid driver!
bcmwls.ini : invalid driver!
bcwml5 : invalid driver!
root@daniel-laptop:/home/daniel/DRIVER# 
```

Please help... Thank you very much.:confused:

---

### Post by fredj on 2007-07-14
Open a terminal and type
ndiswrapper -v
Then post the result here. 
Also type 
lshw -class network and post the result here.

---

### Post by duydaniel on 2007-07-14
> **fredj said:**
> Open a terminal and type
ndiswrapper -v
Then post the result here. 
Also type 
lshw -class network and post the result here.

```
daniel@daniel-laptop:~$ ndiswrapper -v
utils Error: no version specified!
driver version:        1.42
vermagic:       2.6.20-15-generic SMP mod_unload 586 
daniel@daniel-laptop:~$ lshw -class netowrk
WARNING: you should run this program as super-user.
daniel@daniel-laptop:~$ sudo -i
Password:
root@daniel-laptop:~# lshw -class netowrk
root@daniel-laptop:~#     
```

Here you go sir.
I thought "supper user" meant root so I ran as root.

---

### Post by duydaniel on 2007-07-14
Is there anyway that I could [COLOR="Red"]remove[/COLOR] the file bcmwl5.inf
since the system reported:
> driver bcmwl5 is already installed
to try another guide? My wireless used to work with Ubuntu before, but I just reinstalled Ubuntu and now have to reinstall the wireless as well.

I also notice that I can't turn the wireless light off by pressing the combination Fn + F2 (in Dell i6400)

---

### Post by duydaniel on 2007-07-14
anybody helps me? I am still googling for it.

---

### Post by Ayuthia on 2007-07-14
You can remove drivers by typing:
ndiswrapper -e bcmwl5

From what it looks like, you will need to do it for all the drivers listed.  You will need to type them in without the .inf extension.  Another way to take them out is to delete all the files in /etc/ndiswrapper.  All of these commands will need to be done with sudo.

The other thing is that the utilities for ndiswrapper does not look right.  You might want to uninstall this version and get the more updated version from ndiswrapper.  Listed below are the instructions on how to get it and how to install it.

[http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,installation/](http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,installation/)

---

### Post by duydaniel on 2007-07-14
> **Ayuthia said:**
> You can remove drivers by typing:
ndiswrapper -e bcmwl5
[http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,installation/](http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,installation/)

Whenver I type 

```
ndiswrapper -e bcmwl5
```

The system respond:

```
Inappropriate ioctl for device
```

---

### Post by Ayuthia on 2007-07-14
Then you might try going into /etc/ndiswrapper and remove the files in that directory.  That is where they store the drivers that you have tried.

---

### Post by duydaniel on 2007-07-14
> **Ayuthia said:**
> Then you might try going into /etc/ndiswrapper and remove the files in that directory.  That is where they store the drivers that you have tried.

oh yeah... I went there and there are many folder... all of them are empty.
I tried to delete the ndiswrapper folder but there was no delete option (right click).

the link:
[HTML]http://ndiswrapper.sourceforge.net/j...,installation/[/HTML]
you gave me seems tricky to me since I am nooooob.

Will that be ok if I go with this guide?
[HTML]https://help.ubuntu.com/community/WifiDocs/Driver/1390?highlight=%28WifiDocs%2FDriver%29
[/HTML]

The wireless light is off now. Probably after I remove ndiswrapper from Synaptic :(

---

### Post by apoth on 2007-07-14
[This](http://ubuntuforums.org/showthread.php?t=297092&highlight=broadcom+1390) got it working for me.

---

### Post by Ayuthia on 2007-07-14
Both your option and apoth's option will work.  The most up to date version is now 1.47.

---

### Post by duydaniel on 2007-07-14
> **apoth said:**
> [This](http://ubuntuforums.org/showthread.php?t=297092&highlight=broadcom+1390) got it working for me.

WOW...
It works now sir!!!
I appreciate it.

The problem, I think, that there are too many guideline. And I did not restart appropriately... causing that trouble. :guitar: Further more, windows Vista driver should not be using, in my case, it is XP driver and work well.

---

### Post by apoth on 2007-07-15
No problem, glad it worked. :)

---

### Post by duydaniel on 2007-07-15
I don't know why... but whenever I connect to my encrypt wireless network... it always ask me to choose what encryption (128 bit or 64 ASCII or 64 bit Hex) and I type the password... but it did not connect. It only connect to unprotected wireless network.

any idea? :confused:

---

