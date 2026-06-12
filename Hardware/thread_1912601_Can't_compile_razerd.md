---
title: "Can't compile razerd"
date: 2012-01-20
forum: Hardware
---

### Post by skaramanger on 2012-01-20
Howze about a bump?

Greetings,

I recently did a fresh install of kubuntu 11.10 64bit.  I am using kernel:

```
aprompt> uname -r 3.0.0-15-generic
```

I have a razer DeathAdder gaming mouse that has given me modest success if i might say so on nexuiz a fps game.  However, without being able to configure the mouse for better control, I am like a newbie.  So I downloaded the latest version of Michael Bueche's razer configuration program and set about compiling it.

```
$ sudo /etc/init.d/razerd start
 * Starting Razer device state daemon: razerd                                                               /usr/local/sbin/razerd: error while loading shared libraries: ../librazer/librazer.so: cannot open shared object file: No such file or directory
```

```
~$ ldd /usr/local/sbin/razerd
        linux-vdso.so.1 =>  (0x00007fff1d5ff000)
        ../librazer/librazer.so => not found
        libc.so.6 => /lib/x86_64-linux-gnu/libc.so.6 (0x00007f9ab97b8000)
        /lib64/ld-linux-x86-64.so.2 (0x00007f9ab9b72000)

```


I have tried following the advice in a couple of old threads from these forums without success.  I have tried creating soft links to the ../librazer/librazer.so library file and it is located in:

```
$ ls -l /usr/local/lib
total 100
drwxr-xr-x 2 root root   4096 2012-01-20 19:24 librazer
-rwxr-xr-x 1 root root  88751 2012-01-20 20:35 librazer.so
drwxrwsr-x 4 root staff  4096 2011-10-12 11:08 python2.7

```

The librazer folder is where I guess this razer config files thinks its libary file is.  So I created the librazer folder and created a link to it from the original.  I ran:

```
sudo updatedb && sudo ldconfig[CODE]

and attempted to start razerd again. No success.  I tried adding a file to the /etc/ld.so.conf.d folder with a path to the librazer.so library file called razerd.conf:


[CODE]# razer libraries
/usr/local/lib/librazer
```


 No such luck.  So now I throw out a life line to my fellow users here on the UbuntuForums.  Hope you can be of some help.

Tia

---

### Post by sparhawkthesecond on 2012-03-05
The solution (from [here)]("http://ubuntuforums.org/showthread.php?t=1578998&page=2")  is to run the instructions as per the readme, then ```
$ sudo ldconfig
``` Then restart again (or run razerd manually),  and razerd will start properly, and qrazercfg should run properly.

---

### Post by skaramanger on 2012-03-05
> **sparhawkthesecond said:**
> The solution (from [here)]("http://ubuntuforums.org/showthread.php?t=1578998&page=2")  is to run the instructions as per the readme, then ```
$ sudo ldconfig
``` Then restart again (or run razerd manually),  and razerd will start properly, and qrazercfg should run properly.

Sparhawkthesecond,

Thanks for your reply.  I have read that thread and followed it when I first set my mouse up back in 10.10 daze :).  What I did this time and didn't explain what that I downloaded the latest version and placed the code in a folder other than my home on another disk w/o thinking that I still had one an older version on my home folder.  So I just compiled the older version and it is now working.

Thanks again,

Skaramanger

---

### Post by sparhawkthesecond on 2012-03-06
Ah. Oh well, good to see you sorted it out. I also wanted to post in this thread, because it was the only (English) result when you Google the error message.

Cheers!

---

