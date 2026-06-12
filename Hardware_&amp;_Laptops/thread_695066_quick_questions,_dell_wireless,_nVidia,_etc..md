---
title: "quick questions, dell wireless, nVidia, etc."
date: 2008-02-12
forum: Hardware &amp; Laptops
---

### Post by insidi0us on 2008-02-12
I'm brand new to Linux but I want to get it working, and I was pm'd not to be afraid to ask questions.
so here's a quick rundown so far:

I downloaded and burned the ubuntu 7.10 iso and successfully booted from it and tested fine.
I partitioned my harddrive to make space for ubuntu, and I'm now collecting drivers in anticipation of installing.

system specs:

Windows XP on a Dell Vostro 1500
Intel Core 2 Duo T7250 at 2.0 GHz 
2 GB of RAM
nVidia GeForce 8600M GT
Dell Wireless 1505 Draft 802.11n 
120 GB Harddrive (I shrank C to 70GB, leaving about 40GB for Ubuntu until I get used to it. Going to Dual-boot for now)

I will need a network driver for my Wireless N, and a display driver for my 8600M GT.
I've looked around for each, but like I said, I'm new. I just downloaded and started this today. The whole console/command line thing is slightly daunting, but I can get the hang if properly guided. Hopefully someone can point me in the right direction. So far, I care most about the network driver. Anyone know what I need to do? I did download something called ndiswrapper and stuck it on a memory key, but I don't really know what to do with it once in linux, or if it will even work. Thanks in advance for any assistance.

---

### Post by Yellow Pasque on 2008-02-12
Make sure you have the ndiswrapper package installed (you can find it on your install CD).
For ndiswrapper to work, you'll need the Windows drivers:
[http://support.dell.com/support/downloads/download.aspx?c=us&cs=04&l=en&s=bsd&releaseid=R157039&SystemID=VOS_N_1500&servicetag=&os=WLH&osl=en&deviceid=14147&devlib=0&typecnt=0&vercnt=3&catid=-1&impid=-1&formatcnt=1&libid=5&fileid=209641](http://support.dell.com/support/downloads/download.aspx?c=us&cs=04&l=en&s=bsd&releaseid=R157039&SystemID=VOS_N_1500&servicetag=&os=WLH&osl=en&deviceid=14147&devlib=0&typecnt=0&vercnt=3&catid=-1&impid=-1&formatcnt=1&libid=5&fileid=209641)
It's compressed into a self-extracting .EXE, so you'll need to have to extract the files with Windows or WINE. 

Once you have access to the driver files, it's fairly simple to use ndiswrapper. Just open a terminal and navigate to the directory where you have  the files saved, then:
```
sudo ndiswrapper -i bcmwl6.inf
sudo ndsiwrapper -l
sudo modprobe -v ndiswrapper
sudo ndiswrapper -m
```
(I threw in the ndiswrapper -l command so you could make sure it installed properly and says "device present". Also, run the modprobe command to make sure ndiswrapper will load properly when you restart.)
Then open up /etc/modules (with sudo gedit) and add ndiswrapper to the list. Save. Restart. It should work this way, but I won't guarantee it, as I don't have the same hardware. This procedure did work with my wireless card though.

---

### Post by insidi0us on 2008-02-12
hey man, thanks.
I'm certainly further along than I was before, but only because I now have it installed.
I was unaware of the whole swapspace partition stuff, but I got it sorted out.

I'm not a noob to computers, or even doing things from command line, just a super noob to linux and the basics of how it operates. 

my problem so far:
I installed ndiswrapper from the disk like you said, and it said it was successful, but when I went to run the next command, it said "no ndiswrapper utils found!"

so like I said earlier, I had downloaded the latest ndiswrapper prior to installing linux. I took a look at the install instructions for that, navigated in terminal to my usb key, and attempted to install it, but i'm all confused now. it says to:

> Download the latest version of the ndiswrapper sources from here and
extract it with the command

  tar zxvf ndiswrapper-version.tar.gz

This will create ndiswrapper-version directory. Change to that
directory and run

  make uninstall
  make

Login as root and run
  make install

Well, I get errors when I do 'make uninstall'
and i get even more errors when I type 'make'
and then i get some more when i try 'make install'
LOL :(

i forget what the errors were, I suppose I could go back and copy them. but also... I don't even know what it means by "login as root"
i tried everything I could think of, but clearly, i know too little at this point. any help?

---

### Post by ph1 on 2008-02-12
As you are normally logged in, you don't have "root" powers--basically, "super-administrator" powers.  When you type "sudo blah blah command blah," you are giving that command administrative powers temporarily.  If you log in as root, the you@yourcomputer~$ changes to have a # at the end, but that's kind of scary (at least for me), so I just "sudo" commands instead.

So you've downloaded the latest ndiswrapper (which allows Linux to use Windows drivers).  You'll have to change to the directory of your USB drive, e.g. 

```
cd /media/<USB drive name, usually 'disk'>/<folder where you download is>
```

Then "unzip" the file (called "un-tarring" in Linux) using the commands 

```
tar zxvf ndiswrapper-version.tar.gz
```

replacing "ndiswrapper-version.tar.gz" with whatever the name of your download is.  

Now use the cd command again to change to the folder where ndiswrapper was installed to.  

Type

```

make uninstall
```

To clear any old versions of ndiswrapper; then 

```
make
```

to "make" the installation file; and then 

```
sudo make install
```

to install the makefile.  This series of commands (minus the uninstall, usually) is how you install things in Linux.

---

### Post by ph1 on 2008-02-12
As an afterthought, you should be careful that you don't install ndiswrapper to your USB drive--install it to your hard disk.  I don't think I included any steps specifically mentioning that, sorry....

---

### Post by insidi0us on 2008-02-12
well, i already untarred them in windows, lol, in anticipation of having not a clue how to do so in linux. so the files are sitting nicely in their respective unziptarred folder on my usbkey. are you saying i should move the files from my usb key to my desktop folder or some other location on the harddisk, in linux?
(i noticed I can see my windows C drive, and all other partitions even... such as the stupid recovery and mediadirect partitions from dell... interesting nonetheless)

i should mention something else. i was trying to cd around, and it was telling me that folders didnt exist. i would do a dir, type a folder name letter for letter with cd in front of it, and it said no. wtfux?!

eventually i was able to get in... i don't know what i did differently. i had to cd / all the way to root and work my way through each subfolder a few times, back and forth, and finally it just worked once. ah dunno. 

anyway, i will try your sudo methods. be back a little later to report. thanks for the continued support.

---

### Post by Yellow Pasque on 2008-02-12
If you can't get the ndiswrapper to build from source, try the pre-built .debs on your install CD. Just pop the CD in and it should bring up a nautilus file browser window. Now open the following folders - /pool/main/n/ndiswrapper and copy the two .deb files to your Desktop. Install them by opening them and clicking 'Install'. Proceed from there.

---

### Post by patrickaupperle on 2008-02-12
> **insidi0us said:**
> well, i already untarred them in windows, lol, in anticipation of having not a clue how to do so in linux. so the files are sitting nicely in their respective unziptarred folder on my usbkey. are you saying i should move the files from my usb key to my desktop folder or some other location on the harddisk, in linux?
(i noticed I can see my windows C drive, and all other partitions even... such as the stupid recovery and mediadirect partitions from dell... interesting nonetheless)

i should mention something else. i was trying to cd around, and it was telling me that folders didnt exist. i would do a dir, type a folder name letter for letter with cd in front of it, and it said no. wtfux?!

eventually i was able to get in... i don't know what i did differently. i had to cd / all the way to root and work my way through each subfolder a few times, back and forth, and finally it just worked once. ah dunno. 

anyway, i will try your sudo methods. be back a little later to report. thanks for the continued support.

When you cd around make sure you type everything case sensitive. Desktop and desktop are different.

---

### Post by insidi0us on 2008-02-12
k, yea, i knew it was case sensitive, but I figured out what was my problem.
I was doing 'cd \' and it was bringing me to me@mycomputer\$... or something... instead of me@mycomputer~$.
I guess i didn't know it was a different place... so I have to do just "cd"
now i can get into the desktop directory.

I also can't create new files or copy files to ANY locations on the actual linux partition of my harddisk.
everything is access denied. the only places where I can create new files are the desktop (using the gui) or my flash drive, or the windows partition. none of these help me if i want to make a folder for personal files or whatever, somewhere on the harddisk. am i limiited to the existing folders only?


i will try timujin's suggestion. brb :)


edit* yea nothing's really working. I am getting literally, hundreds of errors when I try to 'make'.
EVERY SINGLE line is error'd. i moved everything off my usb key to my desktop, and untarred the ndiswrapper to start fresh.
i did a 'make uninstall' until there were no more "removing" lines. then did a 'make' and thats where i get all the errors.
i go ahead and try 'make install' and it looks like the same lines, all error'd again. 
then i tried what timujin said, and it showed one of them was already installed, the other one not yet.
i installed the one that wasn't yet, and re-installed the one that already existed.
then i go back in to try to install the network drivers, and it tells me ndiswrapper isnt installed, and that i can get it by typing apt-get install blah blah blah.
i do that, and try again, and still no dice. i feel like im following instructions perfectly, but im getting my *** kicked. 

i think i need a much more knowledgeable person sitting at my computer.
i'd love to use linux, but it's seeming to be about as time consuming as a major hobby, 
which i don't really have the time for at flight school. and i might be flying tomorrow, 
so i gotta get some sleep. thanks everyone for all the effort.
i'll give this another go tomorrow afternoon.

---

### Post by Yellow Pasque on 2008-02-13
Uhh, did you use the .debs like I posted? You shouldn't need to 'make' anything if you use them. Try this if you've already installed them: Type **ndiswrapper -l** (That's a small 'L').  Does it return 'No devices installed' or something similar, or does it complain about ndiswrapper not being installed?

---

### Post by insidi0us on 2008-02-13
yea i didnt do any make with those debs. i followed your instructions, and opened each. one of them was "already installed" and the other one was not. i reinstalled the one, and installed the other. im pretty sure i did a ndiswrapper -l afterwards, and it still said it wasn't installed. nothing about a device. i would have cheered if i saw even a message saying "no device"


update! life sucks. first of all, yes, it says it's currently not installed. even though both debs say "same version is already installed"
anyways, here's all the crap i've been talking about:

> kendall@starrbox:~$ cd Desktop
kendall@starrbox:~/Desktop$ cd ndiswrapper-1.52
kendall@starrbox:~/Desktop/ndiswrapper-1.52$ sudo make uninstall
[sudo] password for kendall:
NOTE: Not all installed files are removed, as different distributions install ndiswrapper files at different places.
Run uninstall as many times as necessary until no "removing" messages appear below.
kendall@starrbox:~/Desktop/ndiswrapper-1.52$ make uninstall
NOTE: Not all installed files are removed, as different distributions install ndiswrapper files at different places.
Run uninstall as many times as necessary until no "removing" messages appear below.
kendall@starrbox:~/Desktop/ndiswrapper-1.52$ ndiswrapper -l
The program 'ndiswrapper' is currently not installed.  You can install it by typing:
sudo apt-get install ndiswrapper-common
bash: ndiswrapper: command not found
kendall@starrbox:~/Desktop/ndiswrapper-1.52$

yet, when i look at both debs, they each say "Status:    Same version is already installed"
and i have a button to "Reinstall Package"
I can't find anywhere to remove them, so i can start over.
this is long, but here's what I get when I try to install ndiswrapper 1.52 using 'make':

> kendall@starrbox:~/Desktop/ndiswrapper-1.52$ sudo make
make -C driver
make[1]: Entering directory `/home/kendall/Desktop/ndiswrapper-1.52/driver'
make -C /usr/src/linux-headers-2.6.22-14-generic SUBDIRS=/home/kendall/Desktop/ndiswrapper-1.52/driver
make[2]: Entering directory `/usr/src/linux-headers-2.6.22-14-generic'
  LD      /home/kendall/Desktop/ndiswrapper-1.52/driver/built-in.o
  CC [M]  /home/kendall/Desktop/ndiswrapper-1.52/driver/crt.o
  CC [M]  /home/kendall/Desktop/ndiswrapper-1.52/driver/hal.o
  CC [M]  /home/kendall/Desktop/ndiswrapper-1.52/driver/iw_ndis.o
  CC [M]  /home/kendall/Desktop/ndiswrapper-1.52/driver/loader.o
  CC [M]  /home/kendall/Desktop/ndiswrapper-1.52/driver/ndis.o
  CC [M]  /home/kendall/Desktop/ndiswrapper-1.52/driver/ntoskernel.o
  CC [M]  /home/kendall/Desktop/ndiswrapper-1.52/driver/ntoskernel_io.o
  CC [M]  /home/kendall/Desktop/ndiswrapper-1.52/driver/pe_linker.o
  CC [M]  /home/kendall/Desktop/ndiswrapper-1.52/driver/pnp.o
  CC [M]  /home/kendall/Desktop/ndiswrapper-1.52/driver/proc.o
  CC [M]  /home/kendall/Desktop/ndiswrapper-1.52/driver/rtl.o
  CC [M]  /home/kendall/Desktop/ndiswrapper-1.52/driver/wrapmem.o
  CC [M]  /home/kendall/Desktop/ndiswrapper-1.52/driver/wrapndis.o
  CC [M]  /home/kendall/Desktop/ndiswrapper-1.52/driver/wrapper.o
  CC [M]  /home/kendall/Desktop/ndiswrapper-1.52/driver/usb.o
  CC [M]  /home/kendall/Desktop/ndiswrapper-1.52/driver/divdi3.o
  LD [M]  /home/kendall/Desktop/ndiswrapper-1.52/driver/ndiswrapper.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /home/kendall/Desktop/ndiswrapper-1.52/driver/ndiswrapper.mod.o
  LD [M]  /home/kendall/Desktop/ndiswrapper-1.52/driver/ndiswrapper.ko
make[2]: Leaving directory `/usr/src/linux-headers-2.6.22-14-generic'
make[1]: Leaving directory `/home/kendall/Desktop/ndiswrapper-1.52/driver'
make -C utils
make[1]: Entering directory `/home/kendall/Desktop/ndiswrapper-1.52/utils'
gcc -g -Wall -I../driver -o loadndisdriver loadndisdriver.c
loadndisdriver.c:15:20: error: stdlib.h: No such file or directory
loadndisdriver.c:16:19: error: stdio.h: No such file or directory
loadndisdriver.c:17:19: error: errno.h: No such file or directory
loadndisdriver.c:18:20: error: string.h: No such file or directory
loadndisdriver.c:19:20: error: libgen.h: No such file or directory
loadndisdriver.c:21:22: error: sys/mman.h: No such file or directory
loadndisdriver.c:23:23: error: sys/types.h: No such file or directory
loadndisdriver.c:24:23: error: sys/ioctl.h: No such file or directory
loadndisdriver.c:25:22: error: sys/stat.h: No such file or directory
loadndisdriver.c:26:20: error: unistd.h: No such file or directory
loadndisdriver.c:27:19: error: fcntl.h: No such file or directory
In file included from /usr/lib/gcc/i486-linux-gnu/4.1.3/include/syslimits.h:7,
                 from /usr/lib/gcc/i486-linux-gnu/4.1.3/include/limits.h:11,
                 from loadndisdriver.c:28:
/usr/lib/gcc/i486-linux-gnu/4.1.3/include/limits.h:122:61: error: limits.h: No such file or directory
loadndisdriver.c:29:19: error: ctype.h: No such file or directory
loadndisdriver.c:30:20: error: dirent.h: No such file or directory
loadndisdriver.c:31:20: error: syslog.h: No such file or directory
loadndisdriver.c:34:25: error: linux/major.h: No such file or directory
loadndisdriver.c:35:25: error: linux/ioctl.h: No such file or directory
In file included from loadndisdriver.c:37:
../driver/loader.h:24: error: expected specifier-qualifier-list before â&#8364;&#732;size_tâ&#8364;&#8482;
loadndisdriver.c: In function â&#8364;&#732;load_fileâ&#8364;&#8482;:
loadndisdriver.c:67: error: â&#8364;&#732;size_tâ&#8364;&#8482; undeclared (first use in this function)
loadndisdriver.c:67: error: (Each undeclared identifier is reported only once
loadndisdriver.c:67: error: for each function it appears in.)
loadndisdriver.c:67: error: expected â&#8364;&#732;;â&#8364;&#8482; before â&#8364;&#732;sizeâ&#8364;&#8482;
loadndisdriver.c:68: error: â&#8364;&#732;NULLâ&#8364;&#8482; undeclared (first use in this function)
loadndisdriver.c:69: error: storage size of â&#8364;&#732;statbufâ&#8364;&#8482; isnâ&#8364;&#8482;t known
loadndisdriver.c:71: warning: implicit declaration of function â&#8364;&#732;basenameâ&#8364;&#8482;
loadndisdriver.c:71: warning: initialization makes pointer from integer without a cast
loadndisdriver.c:73: warning: implicit declaration of function â&#8364;&#732;openâ&#8364;&#8482;
loadndisdriver.c:73: error: â&#8364;&#732;O_RDONLYâ&#8364;&#8482; undeclared (first use in this function)
loadndisdriver.c:75: warning: implicit declaration of function â&#8364;&#732;syslogâ&#8364;&#8482;
loadndisdriver.c:75: error: â&#8364;&#732;LOG_KERNâ&#8364;&#8482; undeclared (first use in this function)
loadndisdriver.c:75: error: â&#8364;&#732;LOG_INFOâ&#8364;&#8482; undeclared (first use in this function)
loadndisdriver.c:75: warning: implicit declaration of function â&#8364;&#732;strerrorâ&#8364;&#8482;
loadndisdriver.c:75: error: â&#8364;&#732;errnoâ&#8364;&#8482; undeclared (first use in this function)
loadndisdriver.c:76: error: â&#8364;&#732;EINVALâ&#8364;&#8482; undeclared (first use in this function)
loadndisdriver.c:79: warning: implicit declaration of function â&#8364;&#732;fstatâ&#8364;&#8482;
loadndisdriver.c:81: warning: implicit declaration of function â&#8364;&#732;closeâ&#8364;&#8482;
loadndisdriver.c:84: error: â&#8364;&#732;sizeâ&#8364;&#8482; undeclared (first use in this function)
loadndisdriver.c:86: warning: implicit declaration of function â&#8364;&#732;mmapâ&#8364;&#8482;
loadndisdriver.c:86: error: â&#8364;&#732;PROT_READâ&#8364;&#8482; undeclared (first use in this function)
loadndisdriver.c:86: error: â&#8364;&#732;MAP_PRIVATEâ&#8364;&#8482; undeclared (first use in this function)
loadndisdriver.c:86: warning: assignment makes pointer from integer without a cast
loadndisdriver.c:87: error: â&#8364;&#732;MAP_FAILEDâ&#8364;&#8482; undeclared (first use in this function)
loadndisdriver.c:93: warning: implicit declaration of function â&#8364;&#732;strncpyâ&#8364;&#8482;
loadndisdriver.c:93: warning: incompatible implicit declaration of built-in function â&#8364;&#732;strncpyâ&#8364;&#8482;
loadndisdriver.c:95: error: â&#8364;&#732;struct load_driver_fileâ&#8364;&#8482; has no member named â&#8364;&#732;sizeâ&#8364;&#8482;
loadndisdriver.c:96: error: â&#8364;&#732;struct load_driver_fileâ&#8364;&#8482; has no member named â&#8364;&#732;dataâ&#8364;&#8482;
loadndisdriver.c:69: warning: unused variable â&#8364;&#732;statbufâ&#8364;&#8482;
loadndisdriver.c: In function â&#8364;&#732;parse_setting_lineâ&#8364;&#8482;:
loadndisdriver.c:109: warning: implicit declaration of function â&#8364;&#732;isspaceâ&#8364;&#8482;
loadndisdriver.c:115: warning: implicit declaration of function â&#8364;&#732;strchrâ&#8364;&#8482;
loadndisdriver.c:115: warning: incompatible implicit declaration of built-in function â&#8364;&#732;strchrâ&#8364;&#8482;
loadndisdriver.c:115: error: â&#8364;&#732;NULLâ&#8364;&#8482; undeclared (first use in this function)
loadndisdriver.c:117: error: â&#8364;&#732;LOG_KERNâ&#8364;&#8482; undeclared (first use in this function)
loadndisdriver.c:117: error: â&#8364;&#732;LOG_INFOâ&#8364;&#8482; undeclared (first use in this function)
loadndisdriver.c:118: error: â&#8364;&#732;EINVALâ&#8364;&#8482; undeclared (first use in this function)
loadndisdriver.c:138: warning: implicit declaration of function â&#8364;&#732;strlenâ&#8364;&#8482;
loadndisdriver.c:138: warning: incompatible implicit declaration of built-in function â&#8364;&#732;strlenâ&#8364;&#8482;
loadndisdriver.c: In function â&#8364;&#732;read_conf_fileâ&#8364;&#8482;:
loadndisdriver.c:150: error: storage size of â&#8364;&#732;statbufâ&#8364;&#8482; isnâ&#8364;&#8482;t known
loadndisdriver.c:151: error: â&#8364;&#732;FILEâ&#8364;&#8482; undeclared (first use in this function)
loadndisdriver.c:151: error: â&#8364;&#732;configâ&#8364;&#8482; undeclared (first use in this function)
loadndisdriver.c:157: warning: implicit declaration of function â&#8364;&#732;lstatâ&#8364;&#8482;
loadndisdriver.c:158: error: â&#8364;&#732;LOG_KERNâ&#8364;&#8482; undeclared (first use in this function)
loadndisdriver.c:158: error: â&#8364;&#732;LOG_INFOâ&#8364;&#8482; undeclared (first use in this function)
loadndisdriver.c:158: error: â&#8364;&#732;errnoâ&#8364;&#8482; undeclared (first use in this function)
loadndisdriver.c:160: error: â&#8364;&#732;EINVALâ&#8364;&#8482; undeclared (first use in this function)
loadndisdriver.c:163: warning: implicit declaration of function â&#8364;&#732;sscanfâ&#8364;&#8482;
loadndisdriver.c:163: warning: incompatible implicit declaration of built-in function â&#8364;&#732;sscanfâ&#8364;&#8482;
loadndisdriver.c:178: warning: implicit declaration of function â&#8364;&#732;fopenâ&#8364;&#8482;
loadndisdriver.c:178: error: â&#8364;&#732;NULLâ&#8364;&#8482; undeclared (first use in this function)
loadndisdriver.c:182: warning: implicit declaration of function â&#8364;&#732;fgetsâ&#8364;&#8482;
loadndisdriver.c:194: warning: incompatible implicit declaration of built-in function â&#8364;&#732;strncpyâ&#8364;&#8482;
loadndisdriver.c:205: warning: implicit declaration of function â&#8364;&#732;fcloseâ&#8364;&#8482;
loadndisdriver.c:150: warning: unused variable â&#8364;&#732;statbufâ&#8364;&#8482;
loadndisdriver.c: In function â&#8364;&#732;load_bin_fileâ&#8364;&#8482;:
loadndisdriver.c:217: error: â&#8364;&#732;LOG_KERNâ&#8364;&#8482; undeclared (first use in this function)
loadndisdriver.c:217: error: â&#8364;&#732;LOG_INFOâ&#8364;&#8482; undeclared (first use in this function)
loadndisdriver.c:219: warning: implicit declaration of function â&#8364;&#732;tolowerâ&#8364;&#8482;
loadndisdriver.c:221: warning: implicit declaration of function â&#8364;&#732;chdirâ&#8364;&#8482;
loadndisdriver.c:222: error: â&#8364;&#732;errnoâ&#8364;&#8482; undeclared (first use in this function)
loadndisdriver.c:224: error: â&#8364;&#732;EINVALâ&#8364;&#8482; undeclared (first use in this function)
loadndisdriver.c:230: warning: incompatible implicit declaration of built-in function â&#8364;&#732;strncpyâ&#8364;&#8482;
loadndisdriver.c:232: warning: implicit declaration of function â&#8364;&#732;ioctlâ&#8364;&#8482;
loadndisdriver.c:232: warning: implicit declaration of function â&#8364;&#732;_IOWâ&#8364;&#8482;
loadndisdriver.c:232: error: expected expression before â&#8364;&#732;structâ&#8364;&#8482;
loadndisdriver.c: In function â&#8364;&#732;load_driverâ&#8364;&#8482;:
loadndisdriver.c:249: error: â&#8364;&#732;DIRâ&#8364;&#8482; undeclared (first use in this function)
loadndisdriver.c:249: error: â&#8364;&#732;driver_dirâ&#8364;&#8482; undeclared (first use in this function)
loadndisdriver.c:251: error: â&#8364;&#732;NULLâ&#8364;&#8482; undeclared (first use in this function)
loadndisdriver.c:255: error: â&#8364;&#732;LOG_KERNâ&#8364;&#8482; undeclared (first use in this function)
loadndisdriver.c:255: error: â&#8364;&#732;LOG_INFOâ&#8364;&#8482; undeclared (first use in this function)
loadndisdriver.c:257: error: â&#8364;&#732;errnoâ&#8364;&#8482; undeclared (first use in this function)
loadndisdriver.c:259: error: â&#8364;&#732;EINVALâ&#8364;&#8482; undeclared (first use in this function)
loadndisdriver.c:261: warning: implicit declaration of function â&#8364;&#732;opendirâ&#8364;&#8482;
loadndisdriver.c:267: warning: implicit declaration of function â&#8364;&#732;mallocâ&#8364;&#8482;
loadndisdriver.c:267: warning: incompatible implicit declaration of built-in function â&#8364;&#732;mallocâ&#8364;&#8482;
loadndisdriver.c:271: warning: implicit declaration of function â&#8364;&#732;memsetâ&#8364;&#8482;
loadndisdriver.c:271: warning: incompatible implicit declaration of built-in function â&#8364;&#732;memsetâ&#8364;&#8482;
loadndisdriver.c:272: warning: incompatible implicit declaration of built-in function â&#8364;&#732;strncpyâ&#8364;&#8482;
loadndisdriver.c:280: warning: implicit declaration of function â&#8364;&#732;readdirâ&#8364;&#8482;
loadndisdriver.c:280: warning: assignment makes pointer from integer without a cast
loadndisdriver.c:282: error: storage size of â&#8364;&#732;statbufâ&#8364;&#8482; isnâ&#8364;&#8482;t known
loadndisdriver.c:284: error: dereferencing pointer to incomplete type
loadndisdriver.c:287: warning: implicit declaration of function â&#8364;&#732;statâ&#8364;&#8482;
loadndisdriver.c:287: error: dereferencing pointer to incomplete type
loadndisdriver.c:288: warning: implicit declaration of function â&#8364;&#732;S_ISREGâ&#8364;&#8482;
loadndisdriver.c:289: error: dereferencing pointer to incomplete type
loadndisdriver.c:294: warning: incompatible implicit declaration of built-in function â&#8364;&#732;strlenâ&#8364;&#8482;
loadndisdriver.c:294: error: dereferencing pointer to incomplete type
loadndisdriver.c:296: warning: implicit declaration of function â&#8364;&#732;strcasecmpâ&#8364;&#8482;
loadndisdriver.c:296: error: dereferencing pointer to incomplete type
loadndisdriver.c:299: error: dereferencing pointer to incomplete type
loadndisdriver.c:302: error: dereferencing pointer to incomplete type
loadndisdriver.c:303: error: dereferencing pointer to incomplete type
loadndisdriver.c:305: error: dereferencing pointer to incomplete type
loadndisdriver.c:311: error: dereferencing pointer to incomplete type
loadndisdriver.c:312: error: dereferencing pointer to incomplete type
loadndisdriver.c:313: warning: implicit declaration of function â&#8364;&#732;strcpyâ&#8364;&#8482;
loadndisdriver.c:313: warning: incompatible implicit declaration of built-in function â&#8364;&#732;strcpyâ&#8364;&#8482;
loadndisdriver.c:314: error: dereferencing pointer to incomplete type
loadndisdriver.c:317: error: â&#8364;&#732;struct load_driver_fileâ&#8364;&#8482; has no member named â&#8364;&#732;sizeâ&#8364;&#8482;
loadndisdriver.c:318: error: â&#8364;&#732;struct load_driver_fileâ&#8364;&#8482; has no member named â&#8364;&#732;dataâ&#8364;&#8482;
loadndisdriver.c:321: error: dereferencing pointer to incomplete type
loadndisdriver.c:282: warning: unused variable â&#8364;&#732;statbufâ&#8364;&#8482;
loadndisdriver.c:344: error: expected expression before â&#8364;&#732;structâ&#8364;&#8482;
loadndisdriver.c:346: warning: implicit declaration of function â&#8364;&#732;closedirâ&#8364;&#8482;
loadndisdriver.c:348: warning: implicit declaration of function â&#8364;&#732;freeâ&#8364;&#8482;
loadndisdriver.c:355: warning: implicit declaration of function â&#8364;&#732;munmapâ&#8364;&#8482;
loadndisdriver.c:355: error: â&#8364;&#732;struct load_driver_fileâ&#8364;&#8482; has no member named â&#8364;&#732;dataâ&#8364;&#8482;
loadndisdriver.c:355: error: â&#8364;&#732;struct load_driver_fileâ&#8364;&#8482; has no member named â&#8364;&#732;sizeâ&#8364;&#8482;
loadndisdriver.c:357: error: â&#8364;&#732;struct load_driver_fileâ&#8364;&#8482; has no member named â&#8364;&#732;dataâ&#8364;&#8482;
loadndisdriver.c:357: error: â&#8364;&#732;struct load_driver_fileâ&#8364;&#8482; has no member named â&#8364;&#732;sizeâ&#8364;&#8482;
loadndisdriver.c: In function â&#8364;&#732;get_deviceâ&#8364;&#8482;:
loadndisdriver.c:367: error: storage size of â&#8364;&#732;statbufâ&#8364;&#8482; isnâ&#8364;&#8482;t known
loadndisdriver.c:370: error: â&#8364;&#732;LOG_KERNâ&#8364;&#8482; undeclared (first use in this function)
loadndisdriver.c:370: error: â&#8364;&#732;LOG_INFOâ&#8364;&#8482; undeclared (first use in this function)
loadndisdriver.c:373: error: â&#8364;&#732;errnoâ&#8364;&#8482; undeclared (first use in this function)
loadndisdriver.c:374: error: â&#8364;&#732;EINVALâ&#8364;&#8482; undeclared (first use in this function)
loadndisdriver.c:376: warning: implicit declaration of function â&#8364;&#732;snprintfâ&#8364;&#8482;
loadndisdriver.c:376: warning: incompatible implicit declaration of built-in function â&#8364;&#732;snprintfâ&#8364;&#8482;
loadndisdriver.c:407: warning: incompatible implicit declaration of built-in function â&#8364;&#732;strncpyâ&#8364;&#8482;
loadndisdriver.c:367: warning: unused variable â&#8364;&#732;statbufâ&#8364;&#8482;
loadndisdriver.c: In function â&#8364;&#732;load_deviceâ&#8364;&#8482;:
loadndisdriver.c:419: error: â&#8364;&#732;DIRâ&#8364;&#8482; undeclared (first use in this function)
loadndisdriver.c:419: error: â&#8364;&#732;dirâ&#8364;&#8482; undeclared (first use in this function)
loadndisdriver.c:423: error: â&#8364;&#732;LOG_KERNâ&#8364;&#8482; undeclared (first use in this function)
loadndisdriver.c:423: error: â&#8364;&#732;LOG_INFOâ&#8364;&#8482; undeclared (first use in this function)
loadndisdriver.c:424: warning: incompatible implicit declaration of built-in function â&#8364;&#732;memsetâ&#8364;&#8482;
loadndisdriver.c:426: error: â&#8364;&#732;errnoâ&#8364;&#8482; undeclared (first use in this function)
loadndisdriver.c:427: error: â&#8364;&#732;EINVALâ&#8364;&#8482; undeclared (first use in this function)
loadndisdriver.c:429: error: â&#8364;&#732;NULLâ&#8364;&#8482; undeclared (first use in this function)
loadndisdriver.c:434: warning: assignment makes pointer from integer without a cast
loadndisdriver.c:435: error: dereferencing pointer to incomplete type
loadndisdriver.c:436: error: dereferencing pointer to incomplete type
loadndisdriver.c:439: error: dereferencing pointer to incomplete type
loadndisdriver.c:447: error: expected expression before â&#8364;&#732;structâ&#8364;&#8482;
loadndisdriver.c: In function â&#8364;&#732;get_ioctl_deviceâ&#8364;&#8482;:
loadndisdriver.c:464: error: â&#8364;&#732;FILEâ&#8364;&#8482; undeclared (first use in this function)
loadndisdriver.c:464: error: â&#8364;&#732;proc_miscâ&#8364;&#8482; undeclared (first use in this function)
loadndisdriver.c:472: warning: implicit declaration of function â&#8364;&#732;strstrâ&#8364;&#8482;
loadndisdriver.c:472: warning: incompatible implicit declaration of built-in function â&#8364;&#732;strstrâ&#8364;&#8482;
loadndisdriver.c:473: warning: implicit declaration of function â&#8364;&#732;strtolâ&#8364;&#8482;
loadndisdriver.c:473: error: â&#8364;&#732;NULLâ&#8364;&#8482; undeclared (first use in this function)
loadndisdriver.c:483: error: â&#8364;&#732;LOG_KERNâ&#8364;&#8482; undeclared (first use in this function)
loadndisdriver.c:483: error: â&#8364;&#732;LOG_INFOâ&#8364;&#8482; undeclared (first use in this function)
loadndisdriver.c:488: warning: implicit declaration of function â&#8364;&#732;unlinkâ&#8364;&#8482;
loadndisdriver.c:489: warning: implicit declaration of function â&#8364;&#732;mknodâ&#8364;&#8482;
loadndisdriver.c:489: error: â&#8364;&#732;S_IFCHRâ&#8364;&#8482; undeclared (first use in this function)
loadndisdriver.c:489: error: â&#8364;&#732;MISC_MAJORâ&#8364;&#8482; undeclared (first use in this function)
loadndisdriver.c:490: error: â&#8364;&#732;errnoâ&#8364;&#8482; undeclared (first use in this function)
loadndisdriver.c:495: error: â&#8364;&#732;O_RDONLYâ&#8364;&#8482; undeclared (first use in this function)
loadndisdriver.c: In function â&#8364;&#732;mainâ&#8364;&#8482;:
loadndisdriver.c:511: warning: implicit declaration of function â&#8364;&#732;openlogâ&#8364;&#8482;
loadndisdriver.c:511: error: â&#8364;&#732;LOG_PERRORâ&#8364;&#8482; undeclared (first use in this function)
loadndisdriver.c:511: error: â&#8364;&#732;LOG_CONSâ&#8364;&#8482; undeclared (first use in this function)
loadndisdriver.c:511: error: â&#8364;&#732;LOG_KERNâ&#8364;&#8482; undeclared (first use in this function)
loadndisdriver.c:511: error: â&#8364;&#732;LOG_DEBUGâ&#8364;&#8482; undeclared (first use in this function)
loadndisdriver.c:513: error: â&#8364;&#732;LOG_INFOâ&#8364;&#8482; undeclared (first use in this function)
loadndisdriver.c:515: warning: implicit declaration of function â&#8364;&#732;strncmpâ&#8364;&#8482;
loadndisdriver.c:517: warning: implicit declaration of function â&#8364;&#732;printfâ&#8364;&#8482;
loadndisdriver.c:517: warning: incompatible implicit declaration of built-in function â&#8364;&#732;printfâ&#8364;&#8482;
loadndisdriver.c:527: warning: implicit declaration of function â&#8364;&#732;atoiâ&#8364;&#8482;
loadndisdriver.c:542: warning: implicit declaration of function â&#8364;&#732;atofâ&#8364;&#8482;
loadndisdriver.c:549: warning: implicit declaration of function â&#8364;&#732;strcmpâ&#8364;&#8482;
loadndisdriver.c:556: warning: incompatible implicit declaration of built-in function â&#8364;&#732;sscanfâ&#8364;&#8482;
loadndisdriver.c:590: warning: implicit declaration of function â&#8364;&#732;closelogâ&#8364;&#8482;
make[1]: *** [loadndisdriver] Error 1
make[1]: Leaving directory `/home/kendall/Desktop/ndiswrapper-1.52/utils'
make: *** [all] Error 2
kendall@starrbox:~/Desktop/ndiswrapper-1.52$

yea... lots of errors. i have no idea what any of them mean.
continuing on, here's what i get when i proceed to do a 'make install':

> kendall@starrbox:~/Desktop/ndiswrapper-1.52$ sudo make install
make -C driver install
make[1]: Entering directory `/home/kendall/Desktop/ndiswrapper-1.52/driver'
make -C /usr/src/linux-headers-2.6.22-14-generic SUBDIRS=/home/kendall/Desktop/ndiswrapper-1.52/driver
make[2]: Entering directory `/usr/src/linux-headers-2.6.22-14-generic'
  Building modules, stage 2.
  MODPOST 1 modules
make[2]: Leaving directory `/usr/src/linux-headers-2.6.22-14-generic'
echo /lib/modules/2.6.22-14-generic/misc
/lib/modules/2.6.22-14-generic/misc
mkdir -p /lib/modules/2.6.22-14-generic/misc
install -m 0644 ndiswrapper.ko /lib/modules/2.6.22-14-generic/misc
/sbin/depmod -a 2.6.22-14-generic -b /
make[1]: Leaving directory `/home/kendall/Desktop/ndiswrapper-1.52/driver'
make -C utils install
make[1]: Entering directory `/home/kendall/Desktop/ndiswrapper-1.52/utils'
gcc -g -Wall -I../driver -o loadndisdriver loadndisdriver.c
loadndisdriver.c:15:20: error: stdlib.h: No such file or directory
loadndisdriver.c:16:19: error: stdio.h: No such file or directory
loadndisdriver.c:17:19: error: errno.h: No such file or directory
loadndisdriver.c:18:20: error: string.h: No such file or directory
loadndisdriver.c:19:20: error: libgen.h: No such file or directory
loadndisdriver.c:21:22: error: sys/mman.h: No such file or directory
loadndisdriver.c:23:23: error: sys/types.h: No such file or directory
loadndisdriver.c:24:23: error: sys/ioctl.h: No such file or directory
loadndisdriver.c:25:22: error: sys/stat.h: No such file or directory
loadndisdriver.c:26:20: error: unistd.h: No such file or directory
loadndisdriver.c:27:19: error: fcntl.h: No such file or directory
In file included from /usr/lib/gcc/i486-linux-gnu/4.1.3/include/syslimits.h:7,
                 from /usr/lib/gcc/i486-linux-gnu/4.1.3/include/limits.h:11,
                 from loadndisdriver.c:28:
/usr/lib/gcc/i486-linux-gnu/4.1.3/include/limits.h:122:61: error: limits.h: No such file or directory
loadndisdriver.c:29:19: error: ctype.h: No such file or directory
loadndisdriver.c:30:20: error: dirent.h: No such file or directory
loadndisdriver.c:31:20: error: syslog.h: No such file or directory
loadndisdriver.c:34:25: error: linux/major.h: No such file or directory
loadndisdriver.c:35:25: error: linux/ioctl.h: No such file or directory
In file included from loadndisdriver.c:37:
../driver/loader.h:24: error: expected specifier-qualifier-list before â&#8364;&#732;size_tâ&#8364;&#8482;
loadndisdriver.c: In function â&#8364;&#732;load_fileâ&#8364;&#8482;:
loadndisdriver.c:67: error: â&#8364;&#732;size_tâ&#8364;&#8482; undeclared (first use in this function)
loadndisdriver.c:67: error: (Each undeclared identifier is reported only once
loadndisdriver.c:67: error: for each function it appears in.)
loadndisdriver.c:67: error: expected â&#8364;&#732;;â&#8364;&#8482; before â&#8364;&#732;sizeâ&#8364;&#8482;
loadndisdriver.c:68: error: â&#8364;&#732;NULLâ&#8364;&#8482; undeclared (first use in this function)
loadndisdriver.c:69: error: storage size of â&#8364;&#732;statbufâ&#8364;&#8482; isnâ&#8364;&#8482;t known
loadndisdriver.c:71: warning: implicit declaration of function â&#8364;&#732;basenameâ&#8364;&#8482;
loadndisdriver.c:71: warning: initialization makes pointer from integer without a cast
loadndisdriver.c:73: warning: implicit declaration of function â&#8364;&#732;openâ&#8364;&#8482;
loadndisdriver.c:73: error: â&#8364;&#732;O_RDONLYâ&#8364;&#8482; undeclared (first use in this function)
loadndisdriver.c:75: warning: implicit declaration of function â&#8364;&#732;syslogâ&#8364;&#8482;
loadndisdriver.c:75: error: â&#8364;&#732;LOG_KERNâ&#8364;&#8482; undeclared (first use in this function)
loadndisdriver.c:75: error: â&#8364;&#732;LOG_INFOâ&#8364;&#8482; undeclared (first use in this function)
loadndisdriver.c:75: warning: implicit declaration of function â&#8364;&#732;strerrorâ&#8364;&#8482;
loadndisdriver.c:75: error: â&#8364;&#732;errnoâ&#8364;&#8482; undeclared (first use in this function)
loadndisdriver.c:76: error: â&#8364;&#732;EINVALâ&#8364;&#8482; undeclared (first use in this function)
loadndisdriver.c:79: warning: implicit declaration of function â&#8364;&#732;fstatâ&#8364;&#8482;
loadndisdriver.c:81: warning: implicit declaration of function â&#8364;&#732;closeâ&#8364;&#8482;
loadndisdriver.c:84: error: â&#8364;&#732;sizeâ&#8364;&#8482; undeclared (first use in this function)
loadndisdriver.c:86: warning: implicit declaration of function â&#8364;&#732;mmapâ&#8364;&#8482;
loadndisdriver.c:86: error: â&#8364;&#732;PROT_READâ&#8364;&#8482; undeclared (first use in this function)
loadndisdriver.c:86: error: â&#8364;&#732;MAP_PRIVATEâ&#8364;&#8482; undeclared (first use in this function)
loadndisdriver.c:86: warning: assignment makes pointer from integer without a cast
loadndisdriver.c:87: error: â&#8364;&#732;MAP_FAILEDâ&#8364;&#8482; undeclared (first use in this function)
loadndisdriver.c:93: warning: implicit declaration of function â&#8364;&#732;strncpyâ&#8364;&#8482;
loadndisdriver.c:93: warning: incompatible implicit declaration of built-in function â&#8364;&#732;strncpyâ&#8364;&#8482;
loadndisdriver.c:95: error: â&#8364;&#732;struct load_driver_fileâ&#8364;&#8482; has no member named â&#8364;&#732;sizeâ&#8364;&#8482;
loadndisdriver.c:96: error: â&#8364;&#732;struct load_driver_fileâ&#8364;&#8482; has no member named â&#8364;&#732;dataâ&#8364;&#8482;
loadndisdriver.c:69: warning: unused variable â&#8364;&#732;statbufâ&#8364;&#8482;
loadndisdriver.c: In function â&#8364;&#732;parse_setting_lineâ&#8364;&#8482;:
loadndisdriver.c:109: warning: implicit declaration of function â&#8364;&#732;isspaceâ&#8364;&#8482;
loadndisdriver.c:115: warning: implicit declaration of function â&#8364;&#732;strchrâ&#8364;&#8482;
loadndisdriver.c:115: warning: incompatible implicit declaration of built-in function â&#8364;&#732;strchrâ&#8364;&#8482;
loadndisdriver.c:115: error: â&#8364;&#732;NULLâ&#8364;&#8482; undeclared (first use in this function)
loadndisdriver.c:117: error: â&#8364;&#732;LOG_KERNâ&#8364;&#8482; undeclared (first use in this function)
loadndisdriver.c:117: error: â&#8364;&#732;LOG_INFOâ&#8364;&#8482; undeclared (first use in this function)
loadndisdriver.c:118: error: â&#8364;&#732;EINVALâ&#8364;&#8482; undeclared (first use in this function)
loadndisdriver.c:138: warning: implicit declaration of function â&#8364;&#732;strlenâ&#8364;&#8482;
loadndisdriver.c:138: warning: incompatible implicit declaration of built-in function â&#8364;&#732;strlenâ&#8364;&#8482;
loadndisdriver.c: In function â&#8364;&#732;read_conf_fileâ&#8364;&#8482;:
loadndisdriver.c:150: error: storage size of â&#8364;&#732;statbufâ&#8364;&#8482; isnâ&#8364;&#8482;t known
loadndisdriver.c:151: error: â&#8364;&#732;FILEâ&#8364;&#8482; undeclared (first use in this function)
loadndisdriver.c:151: error: â&#8364;&#732;configâ&#8364;&#8482; undeclared (first use in this function)
loadndisdriver.c:157: warning: implicit declaration of function â&#8364;&#732;lstatâ&#8364;&#8482;
loadndisdriver.c:158: error: â&#8364;&#732;LOG_KERNâ&#8364;&#8482; undeclared (first use in this function)
loadndisdriver.c:158: error: â&#8364;&#732;LOG_INFOâ&#8364;&#8482; undeclared (first use in this function)
loadndisdriver.c:158: error: â&#8364;&#732;errnoâ&#8364;&#8482; undeclared (first use in this function)
loadndisdriver.c:160: error: â&#8364;&#732;EINVALâ&#8364;&#8482; undeclared (first use in this function)
loadndisdriver.c:163: warning: implicit declaration of function â&#8364;&#732;sscanfâ&#8364;&#8482;
loadndisdriver.c:163: warning: incompatible implicit declaration of built-in function â&#8364;&#732;sscanfâ&#8364;&#8482;
loadndisdriver.c:178: warning: implicit declaration of function â&#8364;&#732;fopenâ&#8364;&#8482;
loadndisdriver.c:178: error: â&#8364;&#732;NULLâ&#8364;&#8482; undeclared (first use in this function)
loadndisdriver.c:182: warning: implicit declaration of function â&#8364;&#732;fgetsâ&#8364;&#8482;
loadndisdriver.c:194: warning: incompatible implicit declaration of built-in function â&#8364;&#732;strncpyâ&#8364;&#8482;
loadndisdriver.c:205: warning: implicit declaration of function â&#8364;&#732;fcloseâ&#8364;&#8482;
loadndisdriver.c:150: warning: unused variable â&#8364;&#732;statbufâ&#8364;&#8482;
loadndisdriver.c: In function â&#8364;&#732;load_bin_fileâ&#8364;&#8482;:
loadndisdriver.c:217: error: â&#8364;&#732;LOG_KERNâ&#8364;&#8482; undeclared (first use in this function)
loadndisdriver.c:217: error: â&#8364;&#732;LOG_INFOâ&#8364;&#8482; undeclared (first use in this function)
loadndisdriver.c:219: warning: implicit declaration of function â&#8364;&#732;tolowerâ&#8364;&#8482;
loadndisdriver.c:221: warning: implicit declaration of function â&#8364;&#732;chdirâ&#8364;&#8482;
loadndisdriver.c:222: error: â&#8364;&#732;errnoâ&#8364;&#8482; undeclared (first use in this function)
loadndisdriver.c:224: error: â&#8364;&#732;EINVALâ&#8364;&#8482; undeclared (first use in this function)
loadndisdriver.c:230: warning: incompatible implicit declaration of built-in function â&#8364;&#732;strncpyâ&#8364;&#8482;
loadndisdriver.c:232: warning: implicit declaration of function â&#8364;&#732;ioctlâ&#8364;&#8482;
loadndisdriver.c:232: warning: implicit declaration of function â&#8364;&#732;_IOWâ&#8364;&#8482;
loadndisdriver.c:232: error: expected expression before â&#8364;&#732;structâ&#8364;&#8482;
loadndisdriver.c: In function â&#8364;&#732;load_driverâ&#8364;&#8482;:
loadndisdriver.c:249: error: â&#8364;&#732;DIRâ&#8364;&#8482; undeclared (first use in this function)
loadndisdriver.c:249: error: â&#8364;&#732;driver_dirâ&#8364;&#8482; undeclared (first use in this function)
loadndisdriver.c:251: error: â&#8364;&#732;NULLâ&#8364;&#8482; undeclared (first use in this function)
loadndisdriver.c:255: error: â&#8364;&#732;LOG_KERNâ&#8364;&#8482; undeclared (first use in this function)
loadndisdriver.c:255: error: â&#8364;&#732;LOG_INFOâ&#8364;&#8482; undeclared (first use in this function)
loadndisdriver.c:257: error: â&#8364;&#732;errnoâ&#8364;&#8482; undeclared (first use in this function)
loadndisdriver.c:259: error: â&#8364;&#732;EINVALâ&#8364;&#8482; undeclared (first use in this function)
loadndisdriver.c:261: warning: implicit declaration of function â&#8364;&#732;opendirâ&#8364;&#8482;
loadndisdriver.c:267: warning: implicit declaration of function â&#8364;&#732;mallocâ&#8364;&#8482;
loadndisdriver.c:267: warning: incompatible implicit declaration of built-in function â&#8364;&#732;mallocâ&#8364;&#8482;
loadndisdriver.c:271: warning: implicit declaration of function â&#8364;&#732;memsetâ&#8364;&#8482;
loadndisdriver.c:271: warning: incompatible implicit declaration of built-in function â&#8364;&#732;memsetâ&#8364;&#8482;
loadndisdriver.c:272: warning: incompatible implicit declaration of built-in function â&#8364;&#732;strncpyâ&#8364;&#8482;
loadndisdriver.c:280: warning: implicit declaration of function â&#8364;&#732;readdirâ&#8364;&#8482;
loadndisdriver.c:280: warning: assignment makes pointer from integer without a cast
loadndisdriver.c:282: error: storage size of â&#8364;&#732;statbufâ&#8364;&#8482; isnâ&#8364;&#8482;t known
loadndisdriver.c:284: error: dereferencing pointer to incomplete type
loadndisdriver.c:287: warning: implicit declaration of function â&#8364;&#732;statâ&#8364;&#8482;
loadndisdriver.c:287: error: dereferencing pointer to incomplete type
loadndisdriver.c:288: warning: implicit declaration of function â&#8364;&#732;S_ISREGâ&#8364;&#8482;
loadndisdriver.c:289: error: dereferencing pointer to incomplete type
loadndisdriver.c:294: warning: incompatible implicit declaration of built-in function â&#8364;&#732;strlenâ&#8364;&#8482;
loadndisdriver.c:294: error: dereferencing pointer to incomplete type
loadndisdriver.c:296: warning: implicit declaration of function â&#8364;&#732;strcasecmpâ&#8364;&#8482;
loadndisdriver.c:296: error: dereferencing pointer to incomplete type
loadndisdriver.c:299: error: dereferencing pointer to incomplete type
loadndisdriver.c:302: error: dereferencing pointer to incomplete type
loadndisdriver.c:303: error: dereferencing pointer to incomplete type
loadndisdriver.c:305: error: dereferencing pointer to incomplete type
loadndisdriver.c:311: error: dereferencing pointer to incomplete type
loadndisdriver.c:312: error: dereferencing pointer to incomplete type
loadndisdriver.c:313: warning: implicit declaration of function â&#8364;&#732;strcpyâ&#8364;&#8482;
loadndisdriver.c:313: warning: incompatible implicit declaration of built-in function â&#8364;&#732;strcpyâ&#8364;&#8482;
loadndisdriver.c:314: error: dereferencing pointer to incomplete type
loadndisdriver.c:317: error: â&#8364;&#732;struct load_driver_fileâ&#8364;&#8482; has no member named â&#8364;&#732;sizeâ&#8364;&#8482;
loadndisdriver.c:318: error: â&#8364;&#732;struct load_driver_fileâ&#8364;&#8482; has no member named â&#8364;&#732;dataâ&#8364;&#8482;
loadndisdriver.c:321: error: dereferencing pointer to incomplete type
loadndisdriver.c:282: warning: unused variable â&#8364;&#732;statbufâ&#8364;&#8482;
loadndisdriver.c:344: error: expected expression before â&#8364;&#732;structâ&#8364;&#8482;
loadndisdriver.c:346: warning: implicit declaration of function â&#8364;&#732;closedirâ&#8364;&#8482;
loadndisdriver.c:348: warning: implicit declaration of function â&#8364;&#732;freeâ&#8364;&#8482;
loadndisdriver.c:355: warning: implicit declaration of function â&#8364;&#732;munmapâ&#8364;&#8482;
loadndisdriver.c:355: error: â&#8364;&#732;struct load_driver_fileâ&#8364;&#8482; has no member named â&#8364;&#732;dataâ&#8364;&#8482;
loadndisdriver.c:355: error: â&#8364;&#732;struct load_driver_fileâ&#8364;&#8482; has no member named â&#8364;&#732;sizeâ&#8364;&#8482;
loadndisdriver.c:357: error: â&#8364;&#732;struct load_driver_fileâ&#8364;&#8482; has no member named â&#8364;&#732;dataâ&#8364;&#8482;
loadndisdriver.c:357: error: â&#8364;&#732;struct load_driver_fileâ&#8364;&#8482; has no member named â&#8364;&#732;sizeâ&#8364;&#8482;
loadndisdriver.c: In function â&#8364;&#732;get_deviceâ&#8364;&#8482;:
loadndisdriver.c:367: error: storage size of â&#8364;&#732;statbufâ&#8364;&#8482; isnâ&#8364;&#8482;t known
loadndisdriver.c:370: error: â&#8364;&#732;LOG_KERNâ&#8364;&#8482; undeclared (first use in this function)
loadndisdriver.c:370: error: â&#8364;&#732;LOG_INFOâ&#8364;&#8482; undeclared (first use in this function)
loadndisdriver.c:373: error: â&#8364;&#732;errnoâ&#8364;&#8482; undeclared (first use in this function)
loadndisdriver.c:374: error: â&#8364;&#732;EINVALâ&#8364;&#8482; undeclared (first use in this function)
loadndisdriver.c:376: warning: implicit declaration of function â&#8364;&#732;snprintfâ&#8364;&#8482;
loadndisdriver.c:376: warning: incompatible implicit declaration of built-in function â&#8364;&#732;snprintfâ&#8364;&#8482;
loadndisdriver.c:407: warning: incompatible implicit declaration of built-in function â&#8364;&#732;strncpyâ&#8364;&#8482;
loadndisdriver.c:367: warning: unused variable â&#8364;&#732;statbufâ&#8364;&#8482;
loadndisdriver.c: In function â&#8364;&#732;load_deviceâ&#8364;&#8482;:
loadndisdriver.c:419: error: â&#8364;&#732;DIRâ&#8364;&#8482; undeclared (first use in this function)
loadndisdriver.c:419: error: â&#8364;&#732;dirâ&#8364;&#8482; undeclared (first use in this function)
loadndisdriver.c:423: error: â&#8364;&#732;LOG_KERNâ&#8364;&#8482; undeclared (first use in this function)
loadndisdriver.c:423: error: â&#8364;&#732;LOG_INFOâ&#8364;&#8482; undeclared (first use in this function)
loadndisdriver.c:424: warning: incompatible implicit declaration of built-in function â&#8364;&#732;memsetâ&#8364;&#8482;
loadndisdriver.c:426: error: â&#8364;&#732;errnoâ&#8364;&#8482; undeclared (first use in this function)
loadndisdriver.c:427: error: â&#8364;&#732;EINVALâ&#8364;&#8482; undeclared (first use in this function)
loadndisdriver.c:429: error: â&#8364;&#732;NULLâ&#8364;&#8482; undeclared (first use in this function)
loadndisdriver.c:434: warning: assignment makes pointer from integer without a cast
loadndisdriver.c:435: error: dereferencing pointer to incomplete type
loadndisdriver.c:436: error: dereferencing pointer to incomplete type
loadndisdriver.c:439: error: dereferencing pointer to incomplete type
loadndisdriver.c:447: error: expected expression before â&#8364;&#732;structâ&#8364;&#8482;
loadndisdriver.c: In function â&#8364;&#732;get_ioctl_deviceâ&#8364;&#8482;:
loadndisdriver.c:464: error: â&#8364;&#732;FILEâ&#8364;&#8482; undeclared (first use in this function)
loadndisdriver.c:464: error: â&#8364;&#732;proc_miscâ&#8364;&#8482; undeclared (first use in this function)
loadndisdriver.c:472: warning: implicit declaration of function â&#8364;&#732;strstrâ&#8364;&#8482;
loadndisdriver.c:472: warning: incompatible implicit declaration of built-in function â&#8364;&#732;strstrâ&#8364;&#8482;
loadndisdriver.c:473: warning: implicit declaration of function â&#8364;&#732;strtolâ&#8364;&#8482;
loadndisdriver.c:473: error: â&#8364;&#732;NULLâ&#8364;&#8482; undeclared (first use in this function)
loadndisdriver.c:483: error: â&#8364;&#732;LOG_KERNâ&#8364;&#8482; undeclared (first use in this function)
loadndisdriver.c:483: error: â&#8364;&#732;LOG_INFOâ&#8364;&#8482; undeclared (first use in this function)
loadndisdriver.c:488: warning: implicit declaration of function â&#8364;&#732;unlinkâ&#8364;&#8482;
loadndisdriver.c:489: warning: implicit declaration of function â&#8364;&#732;mknodâ&#8364;&#8482;
loadndisdriver.c:489: error: â&#8364;&#732;S_IFCHRâ&#8364;&#8482; undeclared (first use in this function)
loadndisdriver.c:489: error: â&#8364;&#732;MISC_MAJORâ&#8364;&#8482; undeclared (first use in this function)
loadndisdriver.c:490: error: â&#8364;&#732;errnoâ&#8364;&#8482; undeclared (first use in this function)
loadndisdriver.c:495: error: â&#8364;&#732;O_RDONLYâ&#8364;&#8482; undeclared (first use in this function)
loadndisdriver.c: In function â&#8364;&#732;mainâ&#8364;&#8482;:
loadndisdriver.c:511: warning: implicit declaration of function â&#8364;&#732;openlogâ&#8364;&#8482;
loadndisdriver.c:511: error: â&#8364;&#732;LOG_PERRORâ&#8364;&#8482; undeclared (first use in this function)
loadndisdriver.c:511: error: â&#8364;&#732;LOG_CONSâ&#8364;&#8482; undeclared (first use in this function)
loadndisdriver.c:511: error: â&#8364;&#732;LOG_KERNâ&#8364;&#8482; undeclared (first use in this function)
loadndisdriver.c:511: error: â&#8364;&#732;LOG_DEBUGâ&#8364;&#8482; undeclared (first use in this function)
loadndisdriver.c:513: error: â&#8364;&#732;LOG_INFOâ&#8364;&#8482; undeclared (first use in this function)
loadndisdriver.c:515: warning: implicit declaration of function â&#8364;&#732;strncmpâ&#8364;&#8482;
loadndisdriver.c:517: warning: implicit declaration of function â&#8364;&#732;printfâ&#8364;&#8482;
loadndisdriver.c:517: warning: incompatible implicit declaration of built-in function â&#8364;&#732;printfâ&#8364;&#8482;
loadndisdriver.c:527: warning: implicit declaration of function â&#8364;&#732;atoiâ&#8364;&#8482;
loadndisdriver.c:542: warning: implicit declaration of function â&#8364;&#732;atofâ&#8364;&#8482;
loadndisdriver.c:549: warning: implicit declaration of function â&#8364;&#732;strcmpâ&#8364;&#8482;
loadndisdriver.c:556: warning: incompatible implicit declaration of built-in function â&#8364;&#732;sscanfâ&#8364;&#8482;
loadndisdriver.c:590: warning: implicit declaration of function â&#8364;&#732;closelogâ&#8364;&#8482;
make[1]: *** [loadndisdriver] Error 1
make[1]: Leaving directory `/home/kendall/Desktop/ndiswrapper-1.52/utils'
make: *** [install] Error 2
kendall@starrbox:~/Desktop/ndiswrapper-1.52$ 
kendall@starrbox:~/Desktop/ndiswrapper-1.52$ sudo killyourself
sudo: killyourself: command not found
kendall@starrbox:~/Desktop/ndiswrapper-1.52$

looks like a similar list of errors. WTF am i doing wrong?

---

### Post by pelle.k on 2008-02-13
don't bother with that "source tarball" (.tar.gz) you did download from sourceforge. Your windows "thinking" is showing ;)
In ubuntu, drivers and applications are "packages" (.deb, for the most part) and are installable through "add/remove software" or "synaptic" (in system menu). You don't normally download stuff of the www and install it unless you really know what you are doing.

I belive you've got those two .debs (packages) installed already, and that should be enough :) do "sudo ndiswrapper -l" in a terminal and paste the results here.
About the nvidia drivers, did you run "restricted device manager" from System menu in ubuntu? There you *should* have the option of activating display drivers.

If you think this is hard, it's because you're doing things the "wrong way". It'll get better when you know you way around ubuntu/linux. :)

---

### Post by insidi0us on 2008-02-13
> kendall@starrbox:~$ ndiswrapper -l
The program 'ndiswrapper' is currently not installed.  You can install it by typing:
sudo apt-get install ndiswrapper-common
bash: ndiswrapper: command not found
kendall@starrbox:~$ sudo apt-get install ndiswrapper-common
[sudo] password for kendall:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
ndiswrapper-common is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
kendall@starrbox:~/Desktop/ndiswrapper-1.52$ 

i've been through all of that. i feel stupid, lol.
i like when stuff just worksssssss. and if it doesnt, i like when i'm able to figure it out on my own. 
not used to having to ask a million questions.
so whats next?

---

### Post by pelle.k on 2008-02-13
Try;
```
sudo apt-get --purge autoremove ndiswrapper-common
```
then
```
sudo apt-get --reinstall install ndiswrapper-common
```

You might also try;
```
sudo apt-get install ndisgtk
```

If you succeded, try "sudo ndiswrapper -l" again...

---

### Post by Yellow Pasque on 2008-02-13
To add to pelle.k's suggestion, go into System -> Administration -> Software Sources and make sure that the only source you have it set to use is the CD (and make sure your CD is in the CD drive :) ).

---

### Post by insidi0us on 2008-02-13
ok. i *think* it's installed:
> kendall@starrbox:~$ sudo apt-get --purge autoremove ndiswrapper-common
[sudo] password for kendall:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  ndiswrapper-common* ndiswrapper-utils-1.9*
0 upgraded, 0 newly installed, 2 to remove and 0 not upgraded.
Need to get 0B of archives.
After unpacking 238kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 88955 files and directories currently installed.)
Removing ndiswrapper-utils-1.9 ...
Removing ndiswrapper-common ...
kendall@starrbox:~$ sudo apt-get --purge autoremove ndiswrapper-common
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package ndiswrapper-common is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
kendall@starrbox:~$ sudo apt-get --reinstall install ndiswrapper-common
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  ndiswrapper-source
The following NEW packages will be installed:
  ndiswrapper-common
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/19.2kB of archives.
After unpacking 106kB of additional disk space will be used.
Selecting previously deselected package ndiswrapper-common.
(Reading database ... 88932 files and directories currently installed.)
Unpacking ndiswrapper-common (from .../ndiswrapper-common_1.43-1ubuntu2_all.deb) ...
Setting up ndiswrapper-common (1.43-1ubuntu2) ...
kendall@starrbox:~$ sudo ndiswrapper -l
Error: no ndiswrapper utils found!
kendall@starrbox:~$ sudo apt-get install ndisgtk
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package ndisgtk
i assume i now need to install some utils. if i can directions on that, i think i might be able to start doing some of this on my own. i *feel* like i *might* be starting to get the hang of this... but probably not.

---

### Post by pelle.k on 2008-02-14
I'm sorry i havent been around for a few hours. sleep>work>free time you know :)
Ok then, ndisgtk is in "universe" repository, which you can add/activate in synaptic package manager. It is basically a graphical tool to load windows drivers using ndiswrapper, and i suggested it only because it will defenitely "pull" in all needed dependencies to get you going.

You can of course skip that (and only add the last component of the command line tools) and install ndiswrapper-utils-1.9 (using "sudo apt get install ndiswrapper-utils-1.9") should you want to. that is up to you.
Then, again "sudo ndiswrapper -l".

All this "trouble", is probably caused by that source you tried to install earlier on. It is normally not this difficult.

---

### Post by insidi0us on 2008-02-14
hey man no problem at all. 
i'm takin this process slow. i'm dualbooting so i'm in no hurry, just wanna learn some new stuff when i can. havent been flying much cuz of whether and flu, i'm all studied up on ground school, and my checkride isnt for a few weeks, so apart from rubik's cubes and soccer, i'm hobbyless and have some time to kill.

so ill go try to install some utils... then i will try to get my wireless drivers up and running. hopefully then i can actually get on here in linux, instead of rebooting everytime i have a problem, lol.

thanks much for everything. will report back in a bit


EDIT*

alright so i installed it. YAY! device present. put ndiswrapper in the boot modules file, etc. now i dunno where to go to get me some internetz.
i crammed as many appropriate windows as i could fit, and took a screenshot. if i can get internet on here, i'll try harder to learn on my own.
for now, this rebooting business is killin me and i just wanna get some packets moving. 
[IMG]http://www.starrtrax.net/images/linuxnet.jpg[/IMG]

---

### Post by pelle.k on 2008-02-15
way to go ;)

from there everything *should* be pretty much point-and-clicky, apart from the occasional hiccup from using actual *windows* (!) drivers in ubuntu.
Right click "network manager" (the two "monitors" in you system tray. the ones with a "!" sign right beside) and try connectiong to a wlan.

To check if the wlan does indeed work, try "sudo iwlist wlan0 scan". You can of course replace "wlan0" if the adapter has another name. btw, "iwconfig" will show the current configuration of all wireless adapters installed in your computer.

---

### Post by insidi0us on 2008-02-15
yea, i had tried that icon when i first installed linux, and throughout my trials and errors. but i had the same problem then as i still have now:
the only options i have are "enable networking" which is checked, and "connection information" which is grayed out, or "about" which doesn't do me any good.
nothing about wireless, or any way to edit any settings.

i was gonna paste the text results to the 2 commands u gave me, but i somehow didnt save my txt document to my flash drive... anyway, i did take a screenshot so here that is:

[IMG]http://www.starrtrax.net/images/nonet.jpg[/IMG]

---

### Post by the_tazinator on 2008-02-15
I have a Dell Precision M4300 that has a E1505 N wireless card in it and [these]("http://ubuntuforums.org/showthread.php?t=297092") directions worked for setting my card up. The only thing that you need to make sure to do is download the right drivers for your wireless card from Dell. DO NOT use the exact driver number that in mentioned in the post as those drivers are for the Broadcom 1390 wireless card.

---

### Post by Yellow Pasque on 2008-02-15
Try some commands for me, (text please, if you can this time)
```
sudo lshw -C network
sudo ethtool eth0
sudo ethtool wlan0
cat /etc/network/interfaces
cat /etc/modules
```

---

### Post by pelle.k on 2008-02-16
I want to add to that!
```
lsmod | grep ndiswrapper
```
```
dmesg  | grep wlan0
```

---

### Post by insidi0us on 2008-02-16
heyyyyyyyyyyyyy!!!!
i got it!!!
i'm in firefox on linux right now.... wirelessing it up!!
mmm so good to see the interweb working.
thanks to everyone for your dedication to helping me.
ultimately, i followed the tutorial from the tazinator.
now i'm no linux genius, but i don't think my problem lied in the commands.
i noticed that the driver i was using was something someone linked me to earlier in this thread, and the file was bcmwl6.inf.... well the tutorial showed bcmwl5.inf, and i remembered seeing that somewhere. so i went and found the driver i downloaded from dell shortly after i bought this laptop, and it too was a bcmwl5.inf, so i decided to use it instead. (i think THAT's what fixed it for me)
i did the whole clean the system thing... following the tutorial word for word.
though I couldn't do all of this one: 
```

sudo apt-get update
sudo apt-get install build-essential
sudo apt-get install linux-headers-`uname -r`
wget http://ftp.us.dell.com/network/R151517.EXE
```
because i had no internet connection! i guess this tutorial assumes you are WIRED, and u want WIRELESS... but i'm from ny, temporarily in virginia at flight school and all i have is a laptop and a password to a wireless network in my vacinity :D

well regardless, it worked, and here i am. i do have this feeling of uncleanliness though. i always get this way in windows, when i've installed something and uninstalled it, i feel like some crap is leftover and if it happens enough, i reformat, lol. so i might see this whole thing as a trial, and test my skills at getting my audio and video cards working, then reformat and start afresh. thanks again everyone. i'm super happy now :) !!!

---

### Post by pelle.k on 2008-02-17
**I'm not 100% sure, but i don't think compiling ndiswrapper is essential if you already are running gutsy. So, to consilidate the steps (for your next clean install);**

```
sudo apt-get install ndiswrapper-common ndiswrapper-utils-1.9
```
those packages can be installed from the cd.
```
sudo echo blacklist bcm43xx >> /etc/modprobe.d/blacklist
```
to blacklist the "built in" kernel module (driver) that obvioulsy isn't working that good ;)
```
sudo ndiswrapper -i bcmwl5.inf
```
to install the driver. just save the "bcmwl5.inf" on your HD for the next install.
```
sudo ndiswrapper -m
```
This is to make sure ndiswrapper is loaded at bootup!

Good luck!

---

### Post by insidi0us on 2008-02-18
i just got compiz working... fun stuff.

but i'm having trouble with multiple wireless networks now. i saved my apartment wireless settings to a file, but im at the airport now and im trying to get on their wifi. i put it in roaming mode, found the network here, and put in the WEP and everything, saved the settings to a new file. but it wouldn't resolve an IP. and for some reason it keeps turning my wired NIC back on... any tipz?!

---

### Post by pelle.k on 2008-02-18
I think it falls back on "wired" ethernet if the wifi doesn't work. Make sure you know the diffrence  between 64 bit, 128 bit, asci and hexadecimal passwords. Also, it's important to set the key to restricted/shared or open. essid:s *are* case sensitive as well (if you had to fill that out).
It might just be that you are having bad luck as well :/

---

### Post by insidi0us on 2008-02-18
didnt manually enter the essid. it was found during the roam. i do know the difference between 64, 128, ascii etc. its a hexadecimal password and it's working fine in windows. the only thing i didn't try was setting the key to restricted/shared or open. don't remember seeing an option for that, but i'll check it out if i hit up the airport tomorrow.

thanks

---

### Post by pelle.k on 2008-02-19
Hexadecimal is when it looks like this; "11;B2;1F" etc.
Asci is basically a phrase with letters, and if i'm not mistaken a 64 bit asci pass phrase is 13 letters long.

---

### Post by insidi0us on 2008-02-19
lol i kno. you might have read me wrong. i said i know the diff :)

---

### Post by pelle.k on 2008-02-19
Oh crap. :) I guess i'm a bit tired...

---

