---
title: "Wireless not working (AR5008X)"
date: 2007-10-29
forum: Hardware &amp; Laptops
---

### Post by Nilks on 2007-10-29
I got a new Zepto computer (a danish company) which came with a Atheros AR5008X 300Mbit Wireless card. It works fine in Vista, but i would really like to swith 100% to Ubuntu.

Atheros AR5008X (AR5416/5133)

I have tried with ndiswrapper and a lot of different drivers (for Vista and XP). I have tried with wifi-radar and wicd. I tried madwifi. All with no working result.

NOTE: I have blacklisted both ath_hal and ath_pci

Anyone who can supply me with some help?

EDIT:
I forgot to mention this. I am currently running 7.04 but have also tried 7.10 with no good result either.

---

### Post by Nilks on 2007-10-31
Anybody?

---

### Post by Nilks on 2007-11-05
There must be someone with an answer?

---

### Post by razibus on 2007-11-08
Hello,

I have an Atheros AR5008E-3NX AR5418 and I didn't find any solution to make it working under linux even with the last version of [madwifi]("http://snapshots.madwifi.org/madwifi-ng/").
Like you I'm trying to find answers because I read that the wifi card of the macbook wich has the same chipset is perfectly running under ubuntu.

Hope we will find something... ;)

---

### Post by razibus on 2007-11-09
I find a solution, use this version : [http://svn.madwifi.org/madwifi/trunk/](http://svn.madwifi.org/madwifi/trunk/)

---

### Post by Nilks on 2007-11-09
I installed Ubuntu 7.10 (from scratch) and tried the driver you linked to. Now it works :D

Thx

---

### Post by razibus on 2007-11-09
It's working but it's still a beta version. After several minutes I got a crash... :(

---

### Post by DaCheetah on 2007-12-10
Forgive the "total noob" question, but how does one download (or install) from that link?
Please tell me you do not have to download every file manually.
(I've also tried the latest version of madwifi from the official website, and still can't get my Linksys WPC300N (Atheros AR5416) to show up.)

---

### Post by DaCheetah on 2007-12-10
Nevermind...
I worked how to check something out in SVN.
Now that I have my Wireless working, I'm pretty sure every single piece of hardware in my laptop is running properly. *grins*
Now if I can get WINE running the Win32 stuff I still rely on, I can throw Windows out the, uh, window... (Or at least use it alot less.)

---

### Post by ValkyRi on 2008-02-02
> **razibus said:**
> I find a solution, use this version : [http://svn.madwifi.org/madwifi/trunk/](http://svn.madwifi.org/madwifi/trunk/)

Anyone can help me to install that driver. I totally have no idea how to install it.
Just if it were .deb or something.
(i have ubuntu 7.10)

---

### Post by MySeLf_PT on 2008-03-18
hi there, 

assuming that you have an internet connection (by cable perhaps)

please try these commands from a terminal (applications > acessories > terminal)

EDIT: sorry, i forgot you need the linux headers and buils essentials so you can compile simething! :P

NOW, it should work! :P

```

sudo apt-get install build-essential
sudo apt-get install linux-headers-2.6.22-14-generic
sudo apt-get install subversion
sudo svn checkout http://svn.madwifi.org/madwifi/trunk/ madwifi-ng
cd madwifi-ng
make 
make install
```

I hope this helps :)

---

### Post by yazuki101 on 2008-03-21
i have the same wifi type (AR5008X) and have been following the steps posted above. everything went fine until I tried the command 'make', this is what i got:

yazuki101@yazuki101-laptop:~/madwifi-ng$ make
Checking requirements... ok.
Checking kernel configuration... ok.
/bin/sh: cannot create svnversion.h.tmp: Permission denied
make: *** [svnversion.h] Error 1
yazuki101@yazuki101-laptop:~/madwifi-ng$

---

### Post by yazuki101 on 2008-03-21
alright, so my issue was i forgot to use the 'sudo' command. Once I had done that I got a little further but ended up with a massive list of errors.

```
yazuki101@yazuki101-laptop:~/madwifi-ng$ sudo make
[sudo] password for yazuki101:
Checking requirements... ok.
Checking kernel configuration... ok.
make -C /lib/modules/2.6.22-14-generic/build SUBDIRS=/home/yazuki101/madwifi-ng modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.22-14-generic'
  HOSTCC  /home/yazuki101/madwifi-ng/ath_hal/uudecode
/home/yazuki101/madwifi-ng/ath_hal/uudecode.c:26:19: error: stdio.h: No such file or directory
/home/yazuki101/madwifi-ng/ath_hal/uudecode.c:27:19: error: errno.h: No such file or directory
/home/yazuki101/madwifi-ng/ath_hal/uudecode.c:28:20: error: getopt.h: No such file or directory
/home/yazuki101/madwifi-ng/ath_hal/uudecode.c:29:20: error: string.h: No such file or directory
/home/yazuki101/madwifi-ng/ath_hal/uudecode.c:30:20: error: stdlib.h: No such file or directory
/home/yazuki101/madwifi-ng/ath_hal/uudecode.c:32:23: error: sys/fcntl.h: No such file or directory
/home/yazuki101/madwifi-ng/ath_hal/uudecode.c:33:22: error: sys/stat.h: No such file or directory
/home/yazuki101/madwifi-ng/ath_hal/uudecode.c: In function 'uudecode_usage':
/home/yazuki101/madwifi-ng/ath_hal/uudecode.c:37: warning: implicit declaration of function 'printf'
/home/yazuki101/madwifi-ng/ath_hal/uudecode.c:37: warning: incompatible implicit declaration of built-in function 'printf'
/home/yazuki101/madwifi-ng/ath_hal/uudecode.c: At top level:
/home/yazuki101/madwifi-ng/ath_hal/uudecode.c:40: error: expected ')' before '*' token
/home/yazuki101/madwifi-ng/ath_hal/uudecode.c:70: error: expected ')' before '*' token
/home/yazuki101/madwifi-ng/ath_hal/uudecode.c: In function 'main':
/home/yazuki101/madwifi-ng/ath_hal/uudecode.c:121: error: 'FILE' undeclared (first use in this function)
/home/yazuki101/madwifi-ng/ath_hal/uudecode.c:121: error: (Each undeclared identifier is reported only once
/home/yazuki101/madwifi-ng/ath_hal/uudecode.c:121: error: for each function it appears in.)
/home/yazuki101/madwifi-ng/ath_hal/uudecode.c:121: error: 'src_stream' undeclared (first use in this function)
/home/yazuki101/madwifi-ng/ath_hal/uudecode.c:122: error: 'dst_stream' undeclared (first use in this function)
/home/yazuki101/madwifi-ng/ath_hal/uudecode.c:122: error: 'NULL' undeclared (first use in this function)
/home/yazuki101/madwifi-ng/ath_hal/uudecode.c:130: warning: implicit declaration of function 'getopt'
/home/yazuki101/madwifi-ng/ath_hal/uudecode.c:134: error: 'optarg' undeclared (first use in this function)
/home/yazuki101/madwifi-ng/ath_hal/uudecode.c:138: warning: implicit declaration of function 'exit'
/home/yazuki101/madwifi-ng/ath_hal/uudecode.c:138: warning: incompatible implicit declaration of built-in function 'exit'
/home/yazuki101/madwifi-ng/ath_hal/uudecode.c:141: error: 'optind' undeclared (first use in this function)
/home/yazuki101/madwifi-ng/ath_hal/uudecode.c:142: error: 'stdin' undeclared (first use in this function)
/home/yazuki101/madwifi-ng/ath_hal/uudecode.c:144: warning: implicit declaration of function 'fopen'
/home/yazuki101/madwifi-ng/ath_hal/uudecode.c:146: warning: implicit declaration of function 'fprintf'
/home/yazuki101/madwifi-ng/ath_hal/uudecode.c:146: warning: incompatible implicit declaration of built-in function 'fprintf'
/home/yazuki101/madwifi-ng/ath_hal/uudecode.c:146: error: 'stderr' undeclared (first use in this function)
/home/yazuki101/madwifi-ng/ath_hal/uudecode.c:147: warning: implicit declaration of function 'strerror'
/home/yazuki101/madwifi-ng/ath_hal/uudecode.c:147: error: 'errno' undeclared (first use in this function)
/home/yazuki101/madwifi-ng/ath_hal/uudecode.c:147: warning: format '%s' expects type 'char *', but argument 4 has type 'int'
/home/yazuki101/madwifi-ng/ath_hal/uudecode.c:148: warning: incompatible implicit declaration of built-in function 'exit'
/home/yazuki101/madwifi-ng/ath_hal/uudecode.c:152: warning: incompatible implicit declaration of built-in function 'exit'
/home/yazuki101/madwifi-ng/ath_hal/uudecode.c:156: warning: implicit declaration of function 'get_line_from_file'
/home/yazuki101/madwifi-ng/ath_hal/uudecode.c:156: warning: assignment makes pointer from integer without a cast
/home/yazuki101/madwifi-ng/ath_hal/uudecode.c:157: warning: implicit declaration of function 'strncmp'
/home/yazuki101/madwifi-ng/ath_hal/uudecode.c:164: warning: incompatible implicit declaration of built-in function 'fprintf'
/home/yazuki101/madwifi-ng/ath_hal/uudecode.c:165: warning: incompatible implicit declaration of built-in function 'exit'
/home/yazuki101/madwifi-ng/ath_hal/uudecode.c:168: warning: implicit declaration of function 'strtoul'
/home/yazuki101/madwifi-ng/ath_hal/uudecode.c:170: warning: implicit declaration of function 'strchr'
/home/yazuki101/madwifi-ng/ath_hal/uudecode.c:170: warning: incompatible implicit declaration of built-in function 'strchr'
/home/yazuki101/madwifi-ng/ath_hal/uudecode.c:172: warning: incompatible implicit declaration of built-in function 'fprintf'
/home/yazuki101/madwifi-ng/ath_hal/uudecode.c:173: warning: incompatible implicit declaration of built-in function 'exit'
/home/yazuki101/madwifi-ng/ath_hal/uudecode.c:178: warning: implicit declaration of function 'strcmp'
/home/yazuki101/madwifi-ng/ath_hal/uudecode.c:179: error: 'stdout' undeclared (first use in this function)
/home/yazuki101/madwifi-ng/ath_hal/uudecode.c:182: error: 'O_WRONLY' undeclared (first use in this function)
/home/yazuki101/madwifi-ng/ath_hal/uudecode.c:182: error: 'O_CREAT' undeclared (first use in this function)
/home/yazuki101/madwifi-ng/ath_hal/uudecode.c:182: error: 'O_TRUNC' undeclared (first use in this function)
/home/yazuki101/madwifi-ng/ath_hal/uudecode.c:186: error: 'O_EXCL' undeclared (first use in this function)
/home/yazuki101/madwifi-ng/ath_hal/uudecode.c:188: warning: implicit declaration of function 'open'
/home/yazuki101/madwifi-ng/ath_hal/uudecode.c:189: error: 'S_IRWXU' undeclared (first use in this function)
/home/yazuki101/madwifi-ng/ath_hal/uudecode.c:189: error: 'S_IRWXG' undeclared (first use in this function)
/home/yazuki101/madwifi-ng/ath_hal/uudecode.c:189: error: 'S_IRWXO' undeclared (first use in this function)
/home/yazuki101/madwifi-ng/ath_hal/uudecode.c:191: warning: implicit declaration of function 'fdopen'
/home/yazuki101/madwifi-ng/ath_hal/uudecode.c:193: warning: incompatible implicit declaration of built-in function 'fprintf'
/home/yazuki101/madwifi-ng/ath_hal/uudecode.c:194: warning: format '%s' expects type 'char *', but argument 4 has type 'int'
/home/yazuki101/madwifi-ng/ath_hal/uudecode.c:195: warning: incompatible implicit declaration of built-in function 'exit'
/home/yazuki101/madwifi-ng/ath_hal/uudecode.c:199: warning: implicit declaration of function 'read_stduu'
/home/yazuki101/madwifi-ng/ath_hal/uudecode.c:201: warning: implicit declaration of function 'fclose'
make[3]: *** [/home/yazuki101/madwifi-ng/ath_hal/uudecode] Error 1
make[2]: *** [/home/yazuki101/madwifi-ng/ath_hal] Error 2
make[1]: *** [_module_/home/yazuki101/madwifi-ng] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.22-14-generic'
make: *** [modules] Error 2

```

---

### Post by MySeLf_PT on 2008-03-23
edited my post. check it! :P

PS: this post its just for "thread reply notificications" effects.

---

### Post by yazuki101 on 2008-03-23
ok, i tried to compile it again and it seemed to work in the terminal. I have restarted my system, but my wireless card is still not showing up.

---

### Post by Chicoche on 2008-05-05
you need to install the libc6-dev package to properly build the driver (so you don,t get all those errors and warnings, when you type : sudo make)
then type: 
sudo make install 
and then follow this HOWTO to configure the driver:
[http://madwifi.org/wiki/UserDocs/FirstTimeHowTo](http://madwifi.org/wiki/UserDocs/FirstTimeHowTo)
that works for me i have a fully functional wireless connection,hope it help you
-- i have the same atheros AR5008X

---

### Post by ace141 on 2008-05-11
using ubuntu 8.04 it doesn't work.
any idea?

---

### Post by Matt You on 2008-06-22
> **MySeLf_PT said:**
> hi there, 

assuming that you have an internet connection (by cable perhaps)

please try these commands from a terminal (applications > acessories > terminal)

EDIT: sorry, i forgot you need the linux headers and buils essentials so you can compile simething! :P

NOW, it should work! :P

```

sudo apt-get install build-essential
sudo apt-get install linux-headers-2.6.22-14-generic
sudo apt-get install subversion
sudo svn checkout http://svn.madwifi.org/madwifi/trunk/ madwifi-ng
cd madwifi-ng
make 
make install
```

I hope this helps :)

Just thought I'd add that I had the same problem with the same wireless chip, tried a million things, and this worked.  TRY THESE STEPS, THEN RESTART. :D

I have ubuntu hardy and an atheros ar5008x chip in a Toshiba a210.

---

### Post by gsimpson on 2008-06-22
I got madwifi working using the following on my Acer laptop

sudo apt-get update && sudo apt-get install build-essential
wget -c [http://snapshots.madwifi.org/special/madwifi-ng-r3366+ar5007.tar.gz](http://snapshots.madwifi.org/special/madwifi-ng-r3366+ar5007.tar.gz)
tar xvf madwifi-ng-r3366+ar5007.tar.gz
cd madwifi-ng-r3366+ar5007
sudo make install
sudo modprobe ath_pci
sudo modprobe wlan_scan_sta

Found it necessary to redo last 4 lines after major kernel upgrade

Thanks to [http://www.hbclinux.net.nz/acer4315-804.html](http://www.hbclinux.net.nz/acer4315-804.html)

---

### Post by hotel86 on 2008-06-22
Ok can someone give me a step by step on how to install this driver in Xubuntu on a Vista/Xubuntu dual boot A215 with out any internet connection on the xubuntu side.  Thanks.

---

### Post by quanta4135 on 2008-07-12
When I type "sudo apt-get install subversion" in terminal all I get is:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package subversion
I checked around and I can´t find an answer (except use update, but that does´nt work). I have the same laptop as Matt You so I was hoping this would fix my problem.

---

