---
title: "An interesting apt-get error/situation"
date: 2008-10-10
forum: General Help
---

### Post by auphil on 2008-10-10
Here's a good one.....yesterday I installed IDL ([www.ittvis.com](www.ittvis.com)) on my 8.04 desktop box. Other than being written by monkeys, the installation script proceeded normally (once I followed the scripts inane directives).

Today, I go to install the simple Adobe Flash player, and it seems the IDL install script has screwed with my apt settings:

```
root@stimpy:~# apt-get install flashplugin-nonfree
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  konqueror-nsplugins libflashsupport msttcorefonts ttf-xfree86-nonfree xfs
The following NEW packages will be installed:
  flashplugin-nonfree
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 18.7kB of archives.
After this operation, 168kB of additional disk space will be used.
Get:1 http://us.archive.ubuntu.com hardy/multiverse flashplugin-nonfree 9.0.124.0ubuntu2 [18.7kB]
Fetched 18.7kB in 0s (27.5kB/s)            
Preconfiguring packages ...
Selecting previously deselected package flashplugin-nonfree.
(Reading database ... 134938 files and directories currently installed.)
Unpacking flashplugin-nonfree (from .../flashplugin-nonfree_9.0.124.0ubuntu2_i386.deb) ...
Setting up flashplugin-nonfree (9.0.124.0ubuntu2) ...
Downloading...
--18:32:34--  http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz
           => `./install_flash_player_9_linux.tar.gz'
Resolving fpdownload.macromedia.com... 72.247.82.70
Connecting to fpdownload.macromedia.com|72.247.82.70|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 3,044,538 (2.9M) [application/x-gzip]

    0K .......... .......... .......... .......... ..........  1%  664.06 KB/s
   50K .......... .......... .......... .......... ..........  3%    1.84 MB/s
  100K .......... .......... .......... .......... ..........  5%    2.06 MB/s
  150K .......... .......... .......... .......... ..........  6%    8.35 MB/s
  200K .......... .......... .......... .......... ..........  8%    2.28 MB/s
  250K .......... .......... .......... .......... .......... 10%    2.09 MB/s
  300K .......... .......... .......... .......... .......... 11%    7.49 MB/s
  350K .......... .......... .......... .......... .......... 13%    2.32 MB/s
  400K .......... .......... .......... .......... .......... 15%    1.57 MB/s
  450K .......... .......... .......... .......... .......... 16%    7.43 MB/s
  500K .......... .......... .......... .......... .......... 18%    1.76 MB/s
  550K .......... .......... .......... .......... .......... 20%    2.08 MB/s
  600K .......... .......... .......... .......... .......... 21%    6.21 MB/s
  650K .......... .......... .......... .......... .......... 23%    2.21 MB/s
  700K .......... .......... .......... .......... .......... 25%    2.15 MB/s
  750K .......... .......... .......... .......... .......... 26%    7.26 MB/s
  800K .......... .......... .......... .......... .......... 28%    2.32 MB/s
  850K .......... .......... .......... .......... .......... 30%    2.10 MB/s
  900K .......... .......... .......... .......... .......... 31%    6.94 MB/s
  950K .......... .......... .......... .......... .......... 33%    2.32 MB/s
 1000K .......... .......... .......... .......... .......... 35%    1.98 MB/s
 1050K .......... .......... .......... .......... .......... 36%    6.74 MB/s
 1100K .......... .......... .......... .......... .......... 38%    2.19 MB/s
 1150K .......... .......... .......... .......... .......... 40%    1.69 MB/s
 1200K .......... .......... .......... .......... .......... 42%    3.07 MB/s
 1250K .......... .......... .......... .......... .......... 43%    4.16 MB/s
 1300K .......... .......... .......... .......... .......... 45%    1.82 MB/s
 1350K .......... .......... .......... .......... .......... 47%    3.76 MB/s
 1400K .......... .......... .......... .......... .......... 48%    3.23 MB/s
 1450K .......... .......... .......... .......... .......... 50%    2.12 MB/s
 1500K .......... .......... .......... .......... .......... 52%    3.87 MB/s
 1550K .......... .......... .......... .......... .......... 53%    3.17 MB/s
 1600K .......... .......... .......... .......... .......... 55%    2.12 MB/s
 1650K .......... .......... .......... .......... .......... 57%    3.95 MB/s
 1700K .......... .......... .......... .......... .......... 58%    3.12 MB/s
 1750K .......... .......... .......... .......... .......... 60%    2.13 MB/s
 1800K .......... .......... .......... .......... .......... 62%    3.98 MB/s
 1850K .......... .......... .......... .......... .......... 63%    3.16 MB/s
 1900K .......... .......... .......... .......... .......... 65%    2.02 MB/s
 1950K .......... .......... .......... .......... .......... 67%    4.31 MB/s
 2000K .......... .......... .......... .......... .......... 68%    2.25 MB/s
 2050K .......... .......... .......... .......... .......... 70%    1.93 MB/s
 2100K .......... .......... .......... .......... .......... 72%   10.53 MB/s
 2150K .......... .......... .......... .......... .......... 73%    2.07 MB/s
 2200K .......... .......... .......... .......... .......... 75%    5.67 MB/s
 2250K .......... .......... .......... .......... .......... 77%    2.39 MB/s
 2300K .......... .......... .......... .......... .......... 79%    6.55 MB/s
 2350K .......... .......... .......... .......... .......... 80%    1.99 MB/s
 2400K .......... .......... .......... .......... .......... 82%    2.43 MB/s
 2450K .......... .......... .......... .......... .......... 84%    5.71 MB/s
 2500K .......... .......... .......... .......... .......... 85%    2.37 MB/s
 2550K .......... .......... .......... .......... .......... 87%    2.03 MB/s
 2600K .......... .......... .......... .......... .......... 89%    7.25 MB/s
 2650K .......... .......... .......... .......... .......... 90%    2.05 MB/s
 2700K .......... .......... .......... .......... .......... 92%    2.10 MB/s
 2750K .......... .......... .......... .......... .......... 94%    6.47 MB/s
 2800K .......... .......... .......... .......... .......... 95%    2.41 MB/s
 2850K .......... .......... .......... .......... .......... 97%    2.10 MB/s
 2900K .......... .......... .......... .......... .......... 99%    4.63 MB/s
 2950K .......... .......... ...                             100%    1.35 MB/s

18:32:35 (2.59 MB/s) - `./install_flash_player_9_linux.tar.gz' saved [3044538/3044538]

Download done.

    The current directory must be set to the ITT directory.
    Change the default to the ITT directory and re-run
    this script.
        
dpkg: error processing flashplugin-nonfree (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 flashplugin-nonfree
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@stimpy:~# 

```

Note the "The current directory must be set to the ITT directory..." message. This is an error I received yesterday from the IDL install script. That script REQUIRED that it be invoked from the base directory for IDL. It seems it left something SOMEWHERE that rendered apt's database jumbled.

Can anyone give me some suggestion as to how to correct this?

Thanks,
AUPhil

---

### Post by Sam on 2008-10-10
"apt-get remove flashplugin-nonfree" ???

---

### Post by auphil on 2008-10-10
> **Sam said:**
> "apt-get remove flashplugin-nonfree" ???

...yes, I tried that....in fact, it was the command immediately proceeding the one I posted. So this is technically round 2 for an attempt at installing something after the IDL installation.

...it's as if the IDL script is queued somewhere and gets called when I run apt-get install <stuff>.

---

### Post by auphil on 2008-10-10
So it appears to be a persistent situation across packages:

```
root@stimpy:/home/builds# apt-get install gkrellm
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  gkrellm
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 752kB of archives.
After this operation, 2126kB of additional disk space will be used.
Get:1 http://us.archive.ubuntu.com hardy/universe gkrellm 2.3.1-1ubuntu2 [752kB]
Fetched 752kB in 1s (421kB/s)   
Selecting previously deselected package gkrellm.
(Reading database ... 134945 files and directories currently installed.)
Unpacking gkrellm (from .../gkrellm_2.3.1-1ubuntu2_i386.deb) ...
Setting up flashplugin-nonfree (9.0.124.0ubuntu2) ...
Installing from local file /var/cache/flashplugin-nonfree/install_flash_player_9_linux.tar.gz

    The current directory must be set to the ITT directory.
    Change the default to the ITT directory and re-run
    this script.
        
dpkg: error processing flashplugin-nonfree (--configure):
 subprocess post-installation script returned error exit status 1
Setting up gkrellm (2.3.1-1ubuntu2) ...

Errors were encountered while processing:
 flashplugin-nonfree
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@stimpy:/home/builds# 

```

I just wish I knew where dpkg/apt-get was referencing that ITT/IDL script so I can nuke it....

---

### Post by Sam on 2008-10-10
What is the output of:
```
sudo dpkg --remove flashplugin-nonfree
```
?

---

### Post by auphil on 2008-10-13
Here's the dpkg output, my comments, followed by a dpkg add...

```
root@stimpy:/var/lib/dpkg# dpkg --remove flashplugin-nonfree
(Reading database ... 134975 files and directories currently installed.)
Removing flashplugin-nonfree ...
root@stimpy:/var/lib/dpkg# 

```

I then go to /var/cache to add manually with dpkg:

```
root@stimpy:/var/cache/apt/archives# ls
flashplugin-nonfree_9.0.124.0ubuntu2_i386.deb  gkrellm_2.3.1-1ubuntu2_i386.deb  lock  partial
root@stimpy:/var/cache/apt/archives# ls -lt
total 764
drwxr-xr-x 2 root root   4096 2008-10-10 19:24 partial
-rw-r----- 1 root root      0 2008-10-10 19:24 lock
-rw-r--r-- 1 root root  18682 2008-04-17 05:04 flashplugin-nonfree_9.0.124.0ubuntu2_i386.deb
-rw-r--r-- 1 root root 752160 2007-12-20 15:03 gkrellm_2.3.1-1ubuntu2_i386.deb
root@stimpy:/var/cache/apt/archives# dpkg --install ./flashplugin-nonfree_9.0.124.0ubuntu2_i386.deb  
(Reading database ... 134976 files and directories currently installed.)
Preparing to replace flashplugin-nonfree 9.0.124.0ubuntu2 (using .../flashplugin-nonfree_9.0.124.0ubuntu2_i386.deb) ...
Unpacking replacement flashplugin-nonfree ...
Setting up flashplugin-nonfree (9.0.124.0ubuntu2) ...
Installing from local file /var/cache/flashplugin-nonfree/install_flash_player_9_linux.tar.gz

    The current directory must be set to the ITT directory.
    Change the default to the ITT directory and re-run
    this script.
        
dpkg: error processing flashplugin-nonfree (--install):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 flashplugin-nonfree
root@stimpy:/var/cache/apt/archives# date
Mon Oct 13 13:53:39 CDT 2008
root@stimpy:/var/cache/apt/archives#
```

I'd love to know what I'm missing here....

Thanks for the help,
AUPhil

---

### Post by auphil on 2008-10-13
Well, this solved the problem, but I do not know why.

I figured the output was coming from a specific script, and I was right. I went to /usr/local/bin/idl and deleted the ITT install script.

I then reran the apt-get install flashplugin-nonfree and it worked without complaint.

I'm still baffled as to why dpkg/apt did not provide more useful diagnostic information about the problem, and why dpkg was calling that IDL/ITT install script.

Thanks,
Phil

---

### Post by cmhubertchen on 2008-10-14
I ran into the same problem running make install on my linux box at work (not ubuntu).
In my case, the problem was that there was an executable named 'install' in the IDL directory (/usr/local/bin/idl/bin/ in your case, perhaps?), and that IDL prepends its path to the *front* of the existing PATH environment variable instead of appending its path to the end of $PATH.  Thus, when apt-get (and in my case, configure) tries to locate 'install', it sees the install script from IDL instead of the standard executable.  Moving the IDL path to the end of $PATH solves the problem.
IDL is crap (compared to, say, matlab).  Unfortunately, one cannot avoid using it in some fields, like astronomy, where it is ubiquitous.  But I have digressed...

---

