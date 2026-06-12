---
title: "Canon LBP-660 printer"
date: 2013-02-08
forum: Hardware
---

### Post by rapattack1 on 2013-02-08
Hi i found this page [http://ubuntuforums.org/showthread.php?p=12498327#post12498327](http://ubuntuforums.org/showthread.php?p=12498327#post12498327) and tried the second posts commands. I got about 3/4 of the way down and noticed that there were errors like cannot make directory and not dir with that name. At least i think thats what it said. Cups on its own doesn't have my exact model so i was googling for a solution. I do get the printers model listed in cups now but it doesn't print a test page. Would appreciate any help. I know the machine is pretty old :0)

---

### Post by schragge on 2013-02-08
The Makefile from the driver package in the linked thread does risky things like installing its binaries into */usr/bin* without checking if there already are identically named files. For example, I'm pretty sure it'll overwrite the file */usr/bin/foomatic-rip* installed by the package *foomatic-filters* with an old version of *foomatic-rip* packaged with the driver.

At this point, I'd probably first reinstall *cups* and *foomatic-filters*:
```
sudo apt-get install --reinstall cups foomatic-filters
```Then redo the driver installation procedure like this (the first several steps greyed out assuming they're already done once and not needed anymore):
```

[COLOR=grey]wget http://www.boichat.ch/nicolas/lbp660/lbp660-0.3.1.tar.gz
tar xvfz lbp660-0.3.1.tar.gz
echo '#!/bin/bash' > lbp660-0.3.1/restartcups.sh
echo '/etc/init.d/cups restart' >> lbp660-0.3.1/restartcups.sh
echo 'echo "Waiting 5 seconds..."' >> lbp660-0.3.1/restartcups.sh
echo 'sleep 5' >> lbp660-0.3.1/restartcups.sh[/COLOR]
sudo mkdir /usr/share/cups/model
sudo aa-complain cupsd
cd lbp660-0.3.1
sed -i 's,/usr/bin,/usr/local/bin,g' Makefile
sudo apt-get install build-essential
sudo make cups-install-660-a4

```

---

### Post by rapattack1 on 2013-02-08
```
carla@carla-desktop:~$ sudo apt-get install --reinstall cups foomatic-filters
[sudo] password for carla: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  thunderbird-locale-en-gb thunderbird-locale-en-us thunderbird-locale-en
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 2 reinstalled, 0 to remove and 0 not upgraded.
Need to get 97.6 kB/1,379 kB of archives.
After this operation, 0 B of additional disk space will be used.
Get:1 http://au.archive.ubuntu.com/ubuntu/ precise-updates/main foomatic-filters i386 4.0.16-0ubuntu0.2 [97.6 kB]
Fetched 97.6 kB in 0s (137 kB/s)          
Preconfiguring packages ...
(Reading database ... 213973 files and directories currently installed.)
Preparing to replace cups 1.5.3-0ubuntu6 (using .../cups_1.5.3-0ubuntu6_i386.deb) ...
cups stop/waiting
Unpacking replacement cups ...
Preparing to replace foomatic-filters 4.0.16-0ubuntu0.2 (using .../foomatic-filters_4.0.16-0ubuntu0.2_i386.deb) ...
Unpacking replacement foomatic-filters ...
Processing triggers for ureadahead ...
ureadahead will be reprofiled on next reboot
Processing triggers for ufw ...
Processing triggers for doc-base ...
Processing 1 changed doc-base file...
Registering documents with scrollkeeper...
Processing triggers for man-db ...
Setting up cups (1.5.3-0ubuntu6) ...
cups start/running, process 5325
Updating PPD files for cups ...
Setting up foomatic-filters (4.0.16-0ubuntu0.2) ...
carla@carla-desktop:~$ sudo mkdir /usr/share/cups/model
mkdir: cannot create directory `/usr/share/cups/model': File exists
carla@carla-desktop:~$ sudo aa-complain cupsd
sudo: aa-complain: command not found
carla@carla-desktop:~$ cd lbp660-0.3.1
carla@carla-desktop:~/lbp660-0.3.1$ sed -i 's,/usr/bin,/usr/local/bin,g' Makefile
carla@carla-desktop:~/lbp660-0.3.1$ sudo apt-get install build-essential
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  thunderbird-locale-en-gb thunderbird-locale-en-us thunderbird-locale-en
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  dpkg-dev g++ g++-4.6 libalgorithm-diff-perl libalgorithm-diff-xs-perl
  libalgorithm-merge-perl libdpkg-perl libstdc++6-4.6-dev
Suggested packages:
  debian-keyring g++-multilib g++-4.6-multilib gcc-4.6-doc libstdc++6-4.6-dbg
  libstdc++6-4.6-doc
The following NEW packages will be installed:
  build-essential dpkg-dev g++ g++-4.6 libalgorithm-diff-perl
  libalgorithm-diff-xs-perl libalgorithm-merge-perl libdpkg-perl
  libstdc++6-4.6-dev
0 upgraded, 9 newly installed, 0 to remove and 0 not upgraded.
Need to get 9,120 kB of archives.
After this operation, 26.9 MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://au.archive.ubuntu.com/ubuntu/ precise/main libstdc++6-4.6-dev i386 4.6.3-1ubuntu5 [1,643 kB]
Get:2 http://au.archive.ubuntu.com/ubuntu/ precise/main g++-4.6 i386 4.6.3-1ubuntu5 [6,745 kB]
Get:3 http://au.archive.ubuntu.com/ubuntu/ precise/main g++ i386 4:4.6.3-1ubuntu5 [1,444 B]
Get:4 http://au.archive.ubuntu.com/ubuntu/ precise-updates/main libdpkg-perl all 1.16.1.2ubuntu7.1 [180 kB]
Get:5 http://au.archive.ubuntu.com/ubuntu/ precise-updates/main dpkg-dev all 1.16.1.2ubuntu7.1 [469 kB]
Get:6 http://au.archive.ubuntu.com/ubuntu/ precise-updates/main build-essential i386 11.5ubuntu2.1 [5,796 B]
Get:7 http://au.archive.ubuntu.com/ubuntu/ precise/main libalgorithm-diff-perl all 1.19.02-2 [50.7 kB]
Get:8 http://au.archive.ubuntu.com/ubuntu/ precise/main libalgorithm-diff-xs-perl i386 0.04-2build2 [12.9 kB]
Get:9 http://au.archive.ubuntu.com/ubuntu/ precise/main libalgorithm-merge-perl all 0.08-2 [12.7 kB]
Fetched 9,120 kB in 10s (896 kB/s)                                             
Selecting previously unselected package libstdc++6-4.6-dev.
(Reading database ... 213973 files and directories currently installed.)
Unpacking libstdc++6-4.6-dev (from .../libstdc++6-4.6-dev_4.6.3-1ubuntu5_i386.deb) ...
Selecting previously unselected package g++-4.6.
Unpacking g++-4.6 (from .../g++-4.6_4.6.3-1ubuntu5_i386.deb) ...
Selecting previously unselected package g++.
Unpacking g++ (from .../g++_4%3a4.6.3-1ubuntu5_i386.deb) ...
Selecting previously unselected package libdpkg-perl.
Unpacking libdpkg-perl (from .../libdpkg-perl_1.16.1.2ubuntu7.1_all.deb) ...
Selecting previously unselected package dpkg-dev.
Unpacking dpkg-dev (from .../dpkg-dev_1.16.1.2ubuntu7.1_all.deb) ...
Selecting previously unselected package build-essential.
Unpacking build-essential (from .../build-essential_11.5ubuntu2.1_i386.deb) ...
Selecting previously unselected package libalgorithm-diff-perl.
Unpacking libalgorithm-diff-perl (from .../libalgorithm-diff-perl_1.19.02-2_all.deb) ...
Selecting previously unselected package libalgorithm-diff-xs-perl.
Unpacking libalgorithm-diff-xs-perl (from .../libalgorithm-diff-xs-perl_0.04-2build2_i386.deb) ...
Selecting previously unselected package libalgorithm-merge-perl.
Unpacking libalgorithm-merge-perl (from .../libalgorithm-merge-perl_0.08-2_all.deb) ...
Processing triggers for man-db ...
Setting up libdpkg-perl (1.16.1.2ubuntu7.1) ...
Setting up dpkg-dev (1.16.1.2ubuntu7.1) ...
Setting up libalgorithm-diff-perl (1.19.02-2) ...
Setting up libalgorithm-diff-xs-perl (0.04-2build2) ...
Setting up libalgorithm-merge-perl (0.08-2) ...
Setting up libstdc++6-4.6-dev (4.6.3-1ubuntu5) ...
Setting up g++-4.6 (4.6.3-1ubuntu5) ...
Setting up g++ (4:4.6.3-1ubuntu5) ...
update-alternatives: using /usr/bin/g++ to provide /usr/bin/c++ (c++) in auto mode.
Setting up build-essential (11.5ubuntu2.1) ...
carla@carla-desktop:~/lbp660-0.3.1$ sudo make cups-install-660-a4
gcc  -O2 -s lbp660.c -o lbp660
lbp660.c: In function ‘get_bitmap’:
lbp660.c:162:3: warning: incompatible implicit declaration of built-in function ‘memset’ [enabled by default]
lbp660.c: In function ‘compress_bitmap’:
lbp660.c:254:3: warning: format ‘%x’ expects argument of type ‘unsigned int’, but argument 3 has type ‘long int’ [-Wformat]
lbp660.c: In function ‘errorexit’:
lbp660.c:410:4: warning: incompatible implicit declaration of built-in function ‘exit’ [enabled by default]
lbp660.c: In function ‘print_band’:
lbp660.c:608:7: warning: format ‘%d’ expects argument of type ‘int’, but argument 4 has type ‘long int’ [-Wformat]
lbp660.c: In function ‘main’:
lbp660.c:949:4: warning: incompatible implicit declaration of built-in function ‘strcpy’ [enabled by default]
lbp660.c: In function ‘print_page’:
lbp660.c:811:21: warning: ignoring return value of ‘fread’, declared with attribute warn_unused_result [-Wunused-result]
lbp660.c: In function ‘compress_bitmap’:
lbp660.c:259:8: warning: ignoring return value of ‘fgets’, declared with attribute warn_unused_result [-Wunused-result]
lbp660.c: In function ‘get_bitmap’:
lbp660.c:166:10: warning: ignoring return value of ‘fread’, declared with attribute warn_unused_result [-Wunused-result]
lbp660.c:170:10: warning: ignoring return value of ‘fread’, declared with attribute warn_unused_result [-Wunused-result]
lbp660.c: In function ‘bitmap_seek’:
lbp660.c:150:9: warning: ignoring return value of ‘fread’, declared with attribute warn_unused_result [-Wunused-result]
lbp660.c:153:8: warning: ignoring return value of ‘fread’, declared with attribute warn_unused_result [-Wunused-result]
chmod +s lbp660
gcc  -O2 -s lbp460.c -o lbp460
lbp460.c: In function ‘compress_bitmap’:
lbp460.c:287:3: warning: format ‘%x’ expects argument of type ‘unsigned int’, but argument 3 has type ‘long int’ [-Wformat]
lbp460.c: In function ‘print_page’:
lbp460.c:793:11: warning: ignoring return value of ‘fread’, declared with attribute warn_unused_result [-Wunused-result]
lbp460.c: In function ‘compress_bitmap’:
lbp460.c:292:8: warning: ignoring return value of ‘fgets’, declared with attribute warn_unused_result [-Wunused-result]
lbp460.c: In function ‘get_bitmap’:
lbp460.c:199:10: warning: ignoring return value of ‘fread’, declared with attribute warn_unused_result [-Wunused-result]
lbp460.c:203:10: warning: ignoring return value of ‘fread’, declared with attribute warn_unused_result [-Wunused-result]
lbp460.c: In function ‘bitmap_seek’:
lbp460.c:183:9: warning: ignoring return value of ‘fread’, declared with attribute warn_unused_result [-Wunused-result]
lbp460.c:186:8: warning: ignoring return value of ‘fread’, declared with attribute warn_unused_result [-Wunused-result]
chmod +s lbp460
install -s -m a=rxs lbp660 /usr/local/bin
install -s -m a=rxs lbp460 /usr/local/bin
echo "Installing foomatic..."
Installing foomatic...
install -m a=rx foomatic-rip /usr/local/bin
install -m a=rx foomatic-gswrapper /usr/local/bin
rm -f /usr/lib/cups/filter/foomatic-rip
ln -s /usr/local/bin/foomatic-rip /usr/lib/cups/filter/foomatic-rip
echo "Foomatic installed."
Foomatic installed.
install -m a=rxs ppd/Canon-LBP-660-lbp660.ppd /usr/share/cups/model
install -m a=rxs ppd/Canon-LBP-460-lbp460.ppd /usr/share/cups/model
echo "Restarting CUPS..."
Restarting CUPS...
./restartcups.sh
Rather than invoking init scripts through /etc/init.d, use the service(8)
utility, e.g. service cups restart

Since the script you are attempting to invoke has been converted to an
Upstart job, you may also use the stop(8) and then start(8) utilities,
e.g. stop cups ; start cups. The restart(8) utility is also available.
cups stop/waiting
cups start/running, process 8174
Waiting 5 seconds...
echo "CUPS restarted."
CUPS restarted.
/usr/sbin/lpadmin -x LBP-660 | /bin/true
/usr/sbin/lpadmin -p LBP-660 -E -m Canon-LBP-660-lbp660.ppd -v file:/dev/null
lpoptions -p LBP-660 -o PageSize=A4
lpoptions -p LBP-660 -o LeftSkip=70
lpoptions -p LBP-660 -o Topskip=100
lpoptions -p LBP-660 -o AlwaysReset=True
carla@carla-desktop:~/lbp660-0.3.1$ 

```
Sorry for the volume above but i didn't know what was relevent or not. I was also not sure you wanted me to redo all of what you mentioned or not as you said something about what had been done or whatever. 
I went to test print anyway and got what is in the attached image.

---

### Post by schragge on 2013-02-08
Not sure if it helps, but I see in the output that *aa-complain cupsd* didn't work, probably because *apparmor-utils* isn't installed. To remedy this, try
```

sudo apt-get install apparmor-utils
sudo aa-complain cupsd
sudo restart cups

```

---

### Post by rapattack1 on 2013-02-09
Hmmmmmm nope it is saying that the printer is IDLE. Checked the connections. Maybe tomorrow or day after will try it on the windows machine. Someone gave this to me so even though they say its working you never know :0)

---

### Post by schragge on 2013-02-09
Try to change the *Device URI* in Printer Properties dialog from *file:/dev/null* to something like *file:/dev/usblp0* (if it's a USB printer). You can look up the right name for the printer device file with ```
ls /dev/usb*
```.

Alternatively, delete and re-add the printer in the GUI. Then it should appear with the *Device URI* something like *usb://CANON/LBP-660*.

---

### Post by rapattack1 on 2013-02-09
Its a parallel connected printer. Yes i did delete the printer and then refind

---

### Post by schragge on 2013-02-09
Then I guess the device URI should be something like *file**:/dev/lp0* (i.e. **l**ine **p**rinter #**0**).

---

### Post by pdc on 2013-02-09
getting a very elderly parallel port printer to work could be quite a mission

see this ubuntu debugging wiki

[https://wiki.ubuntu.com/DebuggingPrintingProblems#Parallel_port_printer](https://wiki.ubuntu.com/DebuggingPrintingProblems#Parallel_port_printer)

you may have to check the kernel detects the parallel port at startup; it must be early morning Sydney on Sunday; we may well not hear from you for a while!

---

### Post by rapattack1 on 2013-02-10
> **schragge said:**
> Then I guess the device URI should be something like *file**:/dev/lp0* (i.e. **l**ine **p**rinter #**0**).
I got the error you see in the image. It had the line 'parallel:/dev/lp0'

---

### Post by rapattack1 on 2013-02-10
> **pdc said:**
> getting a very elderly parallel port printer to work could be quite a mission

see this ubuntu debugging wiki

[https://wiki.ubuntu.com/DebuggingPrintingProblems#Parallel_port_printer](https://wiki.ubuntu.com/DebuggingPrintingProblems#Parallel_port_printer)

you may have to check the kernel detects the parallel port at startup; it must be early morning Sydney on Sunday; we may well not hear from you for a while!

Oh thanks will check this page out much later. Yes we are on different time frames and yes this elderly printer is a challenge he he. Its ok. Its possible i will give up as i get printers/computers stuff given to me all the time and might get newer one.
Would it be better to use a usb adapter thing? I think i have one

---

### Post by schragge on 2013-02-10
Have you also tried it with 'parallel:/dev/lp0'? And yes, try what the page linked by **pdc** says, and post the results here.

---

### Post by rapattack1 on 2013-02-10
No that is what was in the thingy...that command was in there. I didn't put it there.
Yep hopefully will get to that page sometime :0)

---

### Post by schragge on 2013-02-10
OK, then try if it works with the device URI 'parallel:/dev/lp0', too. But first, look if you have that device at all
```

ls /dev/lp*

```

---

### Post by rapattack1 on 2013-02-10
Yeah no maybe u don't understand. Um how do i put it another way. Cups or whatever the printing thing is already has that command inside of it. So if it doesn't work then it doesn't. Removed and redid so many times.

Did the new command you said to do :0)
```
carla@carla-desktop:~$ ls /dev/lp*
/dev/lp0

```

---

### Post by schragge on 2013-02-10
OK. I have a working parallel printer attached to my computer. Here is what some of the commands recommended on the page linked by **pdc** show me. Let's compare that with yours.
```
[color=green]ls -l /dev/{lp0,printer}[/color]
```
[indent]```

crw-rw---T 1 root lp 6, 0 Feb  7 15:55 /dev/lp0
srw-rw---- 1 root lp    0 Feb  8 07:40 /dev/printer

```[/indent]
```
[color=green]dmseg|grep parport[/color]
```
[indent]```

[    5.815767] parport_pc 00:09: reported by Plug and Play ACPI
[    5.815823] parport0: PC-style at 0x378 (0x778), irq 7 [PCSPP,TRISTATE]
[    9.968936] lp0: using parport0 (interrupt-driven).

```[/indent]
```
[color=green]lsmod|egrep '^(lp|parport)'[/color]
```
[indent]```

lp                     17149  0
parport_pc             22364  1
parport                31858  2 parport_pc,lp

```[/indent]
```
[color=green]ls -l /proc/sys/dev/parport/parport?/autoprobe*[/color]
```
[indent]```

-r--r--r-- 1 root root 0 Feb 10 14:57 /proc/sys/dev/parport/parport0/autoprobe
-r--r--r-- 1 root root 0 Feb 10 14:57 /proc/sys/dev/parport/parport0/autoprobe0
-r--r--r-- 1 root root 0 Feb 10 14:57 /proc/sys/dev/parport/parport0/autoprobe1
-r--r--r-- 1 root root 0 Feb 10 14:57 /proc/sys/dev/parport/parport0/autoprobe2
-r--r--r-- 1 root root 0 Feb 10 14:57 /proc/sys/dev/parport/parport0/autoprobe3

```[/indent]

---

### Post by rapattack1 on 2013-02-10
Thanks heres what i got:
```
carla@carla-desktop:~$ ls -l /dev/{lp0,printer}
ls: cannot access /dev/printer: No such file or directory
crw-rw---- 1 root lp 6, 0 Feb 10 19:29 /dev/lp0
carla@carla-desktop:~$ dmseg|grep parport
No command 'dmseg' found, did you mean:
 Command 'mmseg' from package 'sunpinyin-utils' (main)
 Command 'dmesg' from package 'util-linux' (main)
dmseg: command not found
carla@carla-desktop:~$ lsmod|egrep '^(lp|parport)'
parport_pc             32114  1 
lp                     17455  0 
parport                40904  3 ppdev,parport_pc,lp
carla@carla-desktop:~$ ls -l /proc/sys/dev/parport/parport?/autoprobe*
-r--r--r-- 1 root root 0 Feb 11 01:33 /proc/sys/dev/parport/parport0/autoprobe
-r--r--r-- 1 root root 0 Feb 11 01:33 /proc/sys/dev/parport/parport0/autoprobe0
-r--r--r-- 1 root root 0 Feb 11 01:33 /proc/sys/dev/parport/parport0/autoprobe1
-r--r--r-- 1 root root 0 Feb 11 01:33 /proc/sys/dev/parport/parport0/autoprobe2
-r--r--r-- 1 root root 0 Feb 11 01:33 /proc/sys/dev/parport/parport0/autoprobe3
```

---

### Post by schragge on 2013-02-10
> **rapattack1 said:**
> No command 'dmseg' found, did you mean:Sorry, should be dmesg|grep parport

---

### Post by rapattack1 on 2013-02-10
```
$ dmesg|grep parport
[   11.736177] parport_pc 00:05: reported by Plug and Play ACPI
[   11.736227] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[   11.820132] lp0: using parport0 (interrupt-driven).
[ 3134.599026] parport0: lp tried to release parport when not owner
[ 9469.475064] parport0: lp already owner
[ 9484.455624] parport0: lp tried to release parport when not owner
[ 9486.223032] parport0: lp already owner
[ 9501.217353] parport0: lp tried to release parport when not owner
[10713.294352] parport0: lp already owner

```

---

### Post by schragge on 2013-02-10
OK. I don't see any obvious errors in the output. I forgot to mention that [color=green]grep ^lp /etc/modules[/color] gives me ```
lp
```
I'm not sure if *lp* is really needed there. Anyway, to add it if it's not already there, try```
sudo sed -i '$a lp'
```

Now, let's try to change the device URI to [color=green]parcapt:/dev/lp0[/color]

---

### Post by rapattack1 on 2013-02-10
```
$ sudo sed -i '$a lp'
[sudo] password for carla: 
sed: no input files

```

It won't let me cheange the URI. I got an applet saying:

There was an error during the CUPS operation: 'client-error-not-possible'.

---

### Post by schragge on 2013-02-10
> **rapattack1 said:**
> sed: no input filesSorry again. Should be
```
$ sudo sed -i '$a lp' /etc/modules
```> **rapattack1 said:**
> It won't let me cheange the URI. I got an applet saying:

There was an error during the CUPS operation: 'client-error-not-possible'.
Reboot the computer and try it from the command line
```

sudo lpadmin -p LBP-660 -E -m Canon-LBP-660-lbp660.ppd -v parallel:/dev/lp0

```

---

### Post by schragge on 2013-02-10
Sorry, forget about 'parcapt'. Should be 'parallel'

---

### Post by rapattack1 on 2013-02-10
um in what part? sorry not following

---

### Post by schragge on 2013-02-10
What does 'sudo /usr/lib/cups/backend/parallel' show?

---

### Post by schragge on 2013-02-10
> **rapattack1 said:**
> um in what part? sorry not following I've already edited the post, so simply ignore it.

And please also post the output of
```
lpinfo -v
```

---

### Post by rapattack1 on 2013-02-10
```
direct parallel:/dev/lp0 "unknown" "LPT #1" "" ""

```

---

### Post by rapattack1 on 2013-02-10
```
direct parallel:/dev/lp0 "unknown" "LPT #1" "" ""
carla@carla-desktop:~$ lpinfo -v
WARNING: gnome-keyring:: couldn't connect to: /tmp/keyring-ryV1rd/pkcs11: No such file or directory
network ipp
network smb
network ipps
network https
network beh
network lpd
network ipp14
network socket
network http
direct parallel:/dev/lp0

```

---

### Post by schragge on 2013-02-10
Hmm, I'm giving up :(.

One last try. What does 'lpstat -t' show?

Just for reference, below are the links that I googled, maybe you can figure out smth. from them.
[LIST]
[*]LP bug #[lpbug]885883[/lpbug]
[*]RedHat bug #[699092]("https://bugzilla.redhat.com/show_bug.cgi?id=699052"). There it was some scanner software that held /dev/parport0 up.
[*] [This post]("http://www.unixboard.de/vb3/showthread.php?50006-Ubuntu-12-04-Installation-Drucker-Parallel-Port") on some German forum.
[/LIST]

---

### Post by rapattack1 on 2013-02-11
```
$ lpstat -t
WARNING: gnome-keyring:: couldn't connect to: /tmp/keyring-JxxqlY/pkcs11: No such file or directory
scheduler is running
system default destination: Canon-LBP-660
device for Canon-LBP-660: parallel:/dev/lp0
device for LBP-660: parallel:/dev/lp0
Canon-LBP-660 accepting requests since Mon 11 Feb 2013 02:23:40 EST
LBP-660 accepting requests since Mon 11 Feb 2013 02:42:20 EST
printer Canon-LBP-660 is idle.  enabled since Mon 11 Feb 2013 02:23:40 EST
printer LBP-660 is idle.  enabled since Mon 11 Feb 2013 02:42:20 EST

```
Sorry had to go to sleep. I was nearly falling off my computer perch lol. Was late in Australia.
OK will look at those other links soon.
Have added an image of the users/groups thing. Could it be anything there? I noticed that the first link u sent said something about changing ownership so thats why i thought of it.
Thought of something else. I remembered i had a parallel to usb adapter so i plugged that in and the system straight away installed the printer as a usb one. Then i tried to print a test page and maintenance and it said process but then went back to idle

---

### Post by rapattack1 on 2013-02-11
Ok here are some more things that happened. I also went through the troubleshooter that came up and got this log file.```
D [11/Feb/2013:19:38:52 +1100] cupsdSetBusyState: newbusy="Dirty files", busy="Active clients and dirty files"
D [11/Feb/2013:19:38:52 +1100] cupsdReadClient: 14 POST / HTTP/1.1
D [11/Feb/2013:19:38:52 +1100] cupsdSetBusyState: newbusy="Active clients and dirty files", busy="Dirty files"
D [11/Feb/2013:19:38:52 +1100] cupsdAuthorize: No authentication data provided.
D [11/Feb/2013:19:38:52 +1100] cupsdReadClient: 14 1.1 Get-Jobs 1
D [11/Feb/2013:19:38:52 +1100] Get-Jobs ipp://localhost/printers/
D [11/Feb/2013:19:38:52 +1100] [Job 15] Loading attributes...
D [11/Feb/2013:19:38:52 +1100] Returning IPP successful-ok for Get-Jobs (ipp://localhost/printers/) from localhost
D [11/Feb/2013:19:38:52 +1100] cupsdSetBusyState: newbusy="Dirty files", busy="Active clients and dirty files"
D [11/Feb/2013:19:38:52 +1100] cupsdReadClient: 14 POST / HTTP/1.1
D [11/Feb/2013:19:38:52 +1100] cupsdSetBusyState: newbusy="Active clients and dirty files", busy="Dirty files"
D [11/Feb/2013:19:38:52 +1100] cupsdAuthorize: No authentication data provided.
D [11/Feb/2013:19:38:52 +1100] cupsdReadClient: 14 1.1 Get-Jobs 1
D [11/Feb/2013:19:38:52 +1100] Get-Jobs ipp://localhost/printers/
D [11/Feb/2013:19:38:52 +1100] [Job 1] Loading attributes...
E [11/Feb/2013:19:38:52 +1100] [Job 1] Unable to queue job for destination "Canon-LBP-470"!
D [11/Feb/2013:19:38:52 +1100] [Job 9] Loading attributes...
D [11/Feb/2013:19:38:52 +1100] [Job 10] Loading attributes...
D [11/Feb/2013:19:38:52 +1100] [Job 11] Loading attributes...
D [11/Feb/2013:19:38:52 +1100] [Job 12] Loading attributes...
D [11/Feb/2013:19:38:52 +1100] [Job 13] Loading attributes...
D [11/Feb/2013:19:38:52 +1100] [Job 14] Loading attributes...
D [11/Feb/2013:19:38:52 +1100] Returning IPP successful-ok for Get-Jobs (ipp://localhost/printers/) from localhost
D [11/Feb/2013:19:38:52 +1100] cupsdSetBusyState: newbusy="Dirty files", busy="Active clients and dirty files"
D [11/Feb/2013:19:38:52 +1100] cupsdReadClient: 14 GET /admin/conf/cupsd.conf HTTP/1.1
D [11/Feb/2013:19:38:52 +1100] cupsdSetBusyState: newbusy="Active clients and dirty files", busy="Dirty files"
D [11/Feb/2013:19:38:52 +1100] cupsdAuthorize: No authentication data provided.
D [11/Feb/2013:19:38:52 +1100] cupsdIsAuthorized: username=""
D [11/Feb/2013:19:38:52 +1100] cupsdSendHeader: 14 WWW-Authenticate: Basic realm="CUPS", trc="y"
D [11/Feb/2013:19:38:52 +1100] cupsdCloseClient: 14
D [11/Feb/2013:19:38:52 +1100] cupsdSetBusyState: newbusy="Dirty files", busy="Active clients and dirty files"
D [11/Feb/2013:19:38:52 +1100] cupsdAcceptClient: 14 from localhost (Domain)
D [11/Feb/2013:19:38:52 +1100] cupsdReadClient: 14 GET /admin/conf/cupsd.conf HTTP/1.1
D [11/Feb/2013:19:38:52 +1100] cupsdSetBusyState: newbusy="Active clients and dirty files", busy="Dirty files"
D [11/Feb/2013:19:38:52 +1100] cupsdAuthorize: Authorized as carla using PeerCred
D [11/Feb/2013:19:38:52 +1100] cupsdIsAuthorized: username="carla"
D [11/Feb/2013:19:38:52 +1100] cupsdSetBusyState: newbusy="Dirty files", busy="Active clients and dirty files"
D [11/Feb/2013:19:38:52 +1100] cupsdReadClient: 14 GET /admin/conf/cupsd.conf HTTP/1.1
D [11/Feb/2013:19:38:52 +1100] cupsdSetBusyState: newbusy="Active clients and dirty files", busy="Dirty files"
D [11/Feb/2013:19:38:52 +1100] cupsdAuthorize: Authorized as carla using PeerCred
D [11/Feb/2013:19:38:52 +1100] cupsdIsAuthorized: username="carla"
D [11/Feb/2013:19:38:52 +1100] cupsdSetBusyState: newbusy="Dirty files", busy="Active clients and dirty files"
D [11/Feb/2013:19:38:52 +1100] cupsdReadClient: 14 GET /admin/conf/cupsd.conf HTTP/1.1
D [11/Feb/2013:19:38:52 +1100] cupsdSetBusyState: newbusy="Active clients and dirty files", busy="Dirty files"
D [11/Feb/2013:19:38:52 +1100] cupsdAuthorize: Authorized as carla using PeerCred
D [11/Feb/2013:19:38:52 +1100] cupsdIsAuthorized: username="carla"
D [11/Feb/2013:19:38:52 +1100] cupsdSetBusyState: newbusy="Dirty files", busy="Active clients and dirty files"
D [11/Feb/2013:19:38:52 +1100] cupsdReadClient: 14 PUT /admin/conf/cupsd.conf HTTP/1.1
D [11/Feb/2013:19:38:52 +1100] cupsdSetBusyState: newbusy="Active clients and dirty files", busy="Dirty files"
D [11/Feb/2013:19:38:52 +1100] cupsdAuthorize: Authorized as carla using PeerCred
D [11/Feb/2013:19:38:52 +1100] cupsdIsAuthorized: username="carla"
I [11/Feb/2013:19:38:52 +1100] Installing config file "/etc/cups/cupsd.conf"...
D [11/Feb/2013:19:38:53 +1100] cupsdSetBusyState: newbusy="Dirty files", busy="Active clients and dirty files"
D [11/Feb/2013:19:38:53 +1100] cupsdCloseClient: 14
D [11/Feb/2013:19:38:53 +1100] cupsdSetBusyState: newbusy="Dirty files", busy="Dirty files"
I [11/Feb/2013:19:38:53 +1100] Generating printcap /var/run/cups/printcap...
D [11/Feb/2013:19:38:53 +1100] cupsdSetBusyState: newbusy="Not busy", busy="Dirty files"
E [11/Feb/2013:19:38:53 +1100] Unknown directive SystemGroup on line 4 of /etc/cups/cupsd.conf.
E [11/Feb/2013:19:38:53 +1100] Unknown directive JobPrivateAccess on line 88 of /etc/cups/cupsd.conf.
E [11/Feb/2013:19:38:53 +1100] Unknown directive JobPrivateValues on line 89 of /etc/cups/cupsd.conf.
E [11/Feb/2013:19:38:53 +1100] Unknown directive SubscriptionPrivateAccess on line 90 of /etc/cups/cupsd.conf.
E [11/Feb/2013:19:38:53 +1100] Unknown directive SubscriptionPrivateValues on line 91 of /etc/cups/cupsd.conf.
W [11/Feb/2013:19:38:53 +1100] failed to CreateProfile: org.freedesktop.ColorManager.AlreadyExists:profile id 'Canon-LBP-660-Gray..' already exists
W [11/Feb/2013:19:38:53 +1100] failed to CreateDevice: org.freedesktop.ColorManager.AlreadyExists:device id 'cups-Canon-LBP-660' already exists
W [11/Feb/2013:19:38:53 +1100] failed to CreateProfile: org.freedesktop.ColorManager.AlreadyExists:profile id 'LBP-660-Gray..' already exists
W [11/Feb/2013:19:38:53 +1100] failed to CreateDevice: org.freedesktop.ColorManager.AlreadyExists:device id 'cups-LBP-660' already exists
W [11/Feb/2013:19:38:53 +1100] failed to CreateProfile: org.freedesktop.ColorManager.AlreadyExists:profile id 'LBP-660-2-Gray..' already exists
W [11/Feb/2013:19:38:53 +1100] failed to CreateDevice: org.freedesktop.ColorManager.AlreadyExists:device id 'cups-LBP-660-2' already exists
```
Then at the end of the trouble shooter i got this txt file
```
D [11/Feb/2013:19:38:52 +1100] cupsdSetBusyState: newbusy="Dirty files", busy="Active clients and dirty files"
D [11/Feb/2013:19:38:52 +1100] cupsdReadClient: 14 POST / HTTP/1.1
D [11/Feb/2013:19:38:52 +1100] cupsdSetBusyState: newbusy="Active clients and dirty files", busy="Dirty files"
D [11/Feb/2013:19:38:52 +1100] cupsdAuthorize: No authentication data provided.
D [11/Feb/2013:19:38:52 +1100] cupsdReadClient: 14 1.1 Get-Jobs 1
D [11/Feb/2013:19:38:52 +1100] Get-Jobs ipp://localhost/printers/
D [11/Feb/2013:19:38:52 +1100] [Job 15] Loading attributes...
D [11/Feb/2013:19:38:52 +1100] Returning IPP successful-ok for Get-Jobs (ipp://localhost/printers/) from localhost
D [11/Feb/2013:19:38:52 +1100] cupsdSetBusyState: newbusy="Dirty files", busy="Active clients and dirty files"
D [11/Feb/2013:19:38:52 +1100] cupsdReadClient: 14 POST / HTTP/1.1
D [11/Feb/2013:19:38:52 +1100] cupsdSetBusyState: newbusy="Active clients and dirty files", busy="Dirty files"
D [11/Feb/2013:19:38:52 +1100] cupsdAuthorize: No authentication data provided.
D [11/Feb/2013:19:38:52 +1100] cupsdReadClient: 14 1.1 Get-Jobs 1
D [11/Feb/2013:19:38:52 +1100] Get-Jobs ipp://localhost/printers/
D [11/Feb/2013:19:38:52 +1100] [Job 1] Loading attributes...
E [11/Feb/2013:19:38:52 +1100] [Job 1] Unable to queue job for destination "Canon-LBP-470"!
D [11/Feb/2013:19:38:52 +1100] [Job 9] Loading attributes...
D [11/Feb/2013:19:38:52 +1100] [Job 10] Loading attributes...
D [11/Feb/2013:19:38:52 +1100] [Job 11] Loading attributes...
D [11/Feb/2013:19:38:52 +1100] [Job 12] Loading attributes...
D [11/Feb/2013:19:38:52 +1100] [Job 13] Loading attributes...
D [11/Feb/2013:19:38:52 +1100] [Job 14] Loading attributes...
D [11/Feb/2013:19:38:52 +1100] Returning IPP successful-ok for Get-Jobs (ipp://localhost/printers/) from localhost
D [11/Feb/2013:19:38:52 +1100] cupsdSetBusyState: newbusy="Dirty files", busy="Active clients and dirty files"
D [11/Feb/2013:19:38:52 +1100] cupsdReadClient: 14 GET /admin/conf/cupsd.conf HTTP/1.1
D [11/Feb/2013:19:38:52 +1100] cupsdSetBusyState: newbusy="Active clients and dirty files", busy="Dirty files"
D [11/Feb/2013:19:38:52 +1100] cupsdAuthorize: No authentication data provided.
D [11/Feb/2013:19:38:52 +1100] cupsdIsAuthorized: username=""
D [11/Feb/2013:19:38:52 +1100] cupsdSendHeader: 14 WWW-Authenticate: Basic realm="CUPS", trc="y"
D [11/Feb/2013:19:38:52 +1100] cupsdCloseClient: 14
D [11/Feb/2013:19:38:52 +1100] cupsdSetBusyState: newbusy="Dirty files", busy="Active clients and dirty files"
D [11/Feb/2013:19:38:52 +1100] cupsdAcceptClient: 14 from localhost (Domain)
D [11/Feb/2013:19:38:52 +1100] cupsdReadClient: 14 GET /admin/conf/cupsd.conf HTTP/1.1
D [11/Feb/2013:19:38:52 +1100] cupsdSetBusyState: newbusy="Active clients and dirty files", busy="Dirty files"
D [11/Feb/2013:19:38:52 +1100] cupsdAuthorize: Authorized as carla using PeerCred
D [11/Feb/2013:19:38:52 +1100] cupsdIsAuthorized: username="carla"
D [11/Feb/2013:19:38:52 +1100] cupsdSetBusyState: newbusy="Dirty files", busy="Active clients and dirty files"
D [11/Feb/2013:19:38:52 +1100] cupsdReadClient: 14 GET /admin/conf/cupsd.conf HTTP/1.1
D [11/Feb/2013:19:38:52 +1100] cupsdSetBusyState: newbusy="Active clients and dirty files", busy="Dirty files"
D [11/Feb/2013:19:38:52 +1100] cupsdAuthorize: Authorized as carla using PeerCred
D [11/Feb/2013:19:38:52 +1100] cupsdIsAuthorized: username="carla"
D [11/Feb/2013:19:38:52 +1100] cupsdSetBusyState: newbusy="Dirty files", busy="Active clients and dirty files"
D [11/Feb/2013:19:38:52 +1100] cupsdReadClient: 14 GET /admin/conf/cupsd.conf HTTP/1.1
D [11/Feb/2013:19:38:52 +1100] cupsdSetBusyState: newbusy="Active clients and dirty files", busy="Dirty files"
D [11/Feb/2013:19:38:52 +1100] cupsdAuthorize: Authorized as carla using PeerCred
D [11/Feb/2013:19:38:52 +1100] cupsdIsAuthorized: username="carla"
D [11/Feb/2013:19:38:52 +1100] cupsdSetBusyState: newbusy="Dirty files", busy="Active clients and dirty files"
D [11/Feb/2013:19:38:52 +1100] cupsdReadClient: 14 PUT /admin/conf/cupsd.conf HTTP/1.1
D [11/Feb/2013:19:38:52 +1100] cupsdSetBusyState: newbusy="Active clients and dirty files", busy="Dirty files"
D [11/Feb/2013:19:38:52 +1100] cupsdAuthorize: Authorized as carla using PeerCred
D [11/Feb/2013:19:38:52 +1100] cupsdIsAuthorized: username="carla"
I [11/Feb/2013:19:38:52 +1100] Installing config file "/etc/cups/cupsd.conf"...
D [11/Feb/2013:19:38:53 +1100] cupsdSetBusyState: newbusy="Dirty files", busy="Active clients and dirty files"
D [11/Feb/2013:19:38:53 +1100] cupsdCloseClient: 14
D [11/Feb/2013:19:38:53 +1100] cupsdSetBusyState: newbusy="Dirty files", busy="Dirty files"
I [11/Feb/2013:19:38:53 +1100] Generating printcap /var/run/cups/printcap...
D [11/Feb/2013:19:38:53 +1100] cupsdSetBusyState: newbusy="Not busy", busy="Dirty files"
E [11/Feb/2013:19:38:53 +1100] Unknown directive SystemGroup on line 4 of /etc/cups/cupsd.conf.
E [11/Feb/2013:19:38:53 +1100] Unknown directive JobPrivateAccess on line 88 of /etc/cups/cupsd.conf.
E [11/Feb/2013:19:38:53 +1100] Unknown directive JobPrivateValues on line 89 of /etc/cups/cupsd.conf.
E [11/Feb/2013:19:38:53 +1100] Unknown directive SubscriptionPrivateAccess on line 90 of /etc/cups/cupsd.conf.
E [11/Feb/2013:19:38:53 +1100] Unknown directive SubscriptionPrivateValues on line 91 of /etc/cups/cupsd.conf.
W [11/Feb/2013:19:38:53 +1100] failed to CreateProfile: org.freedesktop.ColorManager.AlreadyExists:profile id 'Canon-LBP-660-Gray..' already exists
W [11/Feb/2013:19:38:53 +1100] failed to CreateDevice: org.freedesktop.ColorManager.AlreadyExists:device id 'cups-Canon-LBP-660' already exists
W [11/Feb/2013:19:38:53 +1100] failed to CreateProfile: org.freedesktop.ColorManager.AlreadyExists:profile id 'LBP-660-Gray..' already exists
W [11/Feb/2013:19:38:53 +1100] failed to CreateDevice: org.freedesktop.ColorManager.AlreadyExists:device id 'cups-LBP-660' already exists
W [11/Feb/2013:19:38:53 +1100] failed to CreateProfile: org.freedesktop.ColorManager.AlreadyExists:profile id 'LBP-660-2-Gray..' already exists
W [11/Feb/2013:19:38:53 +1100] failed to CreateDevice: org.freedesktop.ColorManager.AlreadyExists:device id 'cups-LBP-660-2' already exists
```

---

### Post by schragge on 2013-02-11
This line strikes me as odd. Why it says "Canon-LBP-470"?
```

E [11/Feb/2013:19:38:52 +1100] [Job 1] Unable to queue job for destination "Canon-LBP-470"!

```
What does 'lpinfo -l -m' show?

You can also try to open [http://localhost:631](http://localhost:631) in your browser and look at what printers are listed there and their settings, but I don't think you'll see something different there: it's only a web interface to what 'lpstat' shows on command line.

---

### Post by rapattack1 on 2013-02-11
Oh i think that was the printer model closest in number before the 660 models driver was installed. I seem to remember that was the case. I think originally some forum or something i seached said to installed the 470? then change it to 660? I think so but that was yesterday so hard to remember :0)
```
N-hpijs-pcl5e.ppd
        natural_language = en
        make-and-model = Xerox Phaser 7750DN Foomatic/hpijs-pcl5e
        device-id = MFG:Xerox;MDL:Phaser 7750DN;CMD:Adobe PostScript 3, PCL;DES:Xerox Phaser 7750, Color Laser Printer, PostScript 3, Letter/A4/Tabloid/A3 Size;DRV:Dhpijs-pcl5e,R0,M0,Sv,TI,X600,Y600,C0,t100,l100,g100,p100,s70;
Model:  name = foomatic-db-compressed-ppds:0/ppd/foomatic-ppd/Xerox-Phaser_7750DN-lj4dith.ppd
        natural_language = en
        make-and-model = Xerox Phaser 7750DN Foomatic/lj4dith
        device-id = MFG:Xerox;MDL:Phaser 7750DN;CMD:Adobe PostScript 3, PCL;DES:Xerox Phaser 7750, Color Laser Printer, PostScript 3, Letter/A4/Tabloid/A3 Size;DRV:Dlj4dith,R0,M0,TG;
Model:  name = foomatic-db-compressed-ppds:0/ppd/foomatic-ppd/Xerox-Phaser_7750DN-ljet4.ppd
        natural_language = en
        make-and-model = Xerox Phaser 7750DN Foomatic/ljet4
        device-id = MFG:Xerox;MDL:Phaser 7750DN;CMD:Adobe PostScript 3, PCL;DES:Xerox Phaser 7750, Color Laser Printer, PostScript 3, Letter/A4/Tabloid/A3 Size;DRV:Dljet4,R0,M0,Sv,TG,X600,Y600,C0,t90,l90,g60,p30,s90;
Model:  name = foomatic-db-compressed-ppds:0/ppd/foomatic-ppd/Xerox-Phaser_7750DN-ljet4d.ppd
        natural_language = en
        make-and-model = Xerox Phaser 7750DN Foomatic/ljet4d
        device-id = MFG:Xerox;MDL:Phaser 7750DN;CMD:Adobe PostScript 3, PCL;DES:Xerox Phaser 7750, Color Laser Printer, PostScript 3, Letter/A4/Tabloid/A3 Size;DRV:Dljet4d,R0,M0,TG;
Model:  name = foomatic-db-compressed-ppds:0/ppd/foomatic-ppd/Xerox-Phaser_7750DN-Postscript.ppd
        natural_language = en
        make-and-model = Xerox Phaser 7750DN Foomatic/Postscript
        device-id = MFG:Xerox;MDL:Phaser 7750DN;CMD:Adobe PostScript 3, PCL;DES:Xerox Phaser 7750, Color Laser Printer, PostScript 3, Letter/A4/Tabloid/A3 Size;DRV:DPostscript,R0,M0,TP;
Model:  name = gutenprint.5.2://xerox-phaser_7750dxf/expert
        natural_language = en
        make-and-model = Xerox Phaser 7750DXF - CUPS+Gutenprint v5.2.8-pre1
        device-id = 
Model:  name = foomatic-db-compressed-ppds:0/ppd/foomatic-ppd/Xerox-Phaser_7750DXF-hpijs-pcl5e.ppd
        natural_language = en
        make-and-model = Xerox Phaser 7750DXF Foomatic/hpijs-pcl5e
        device-id = MFG:Xerox;MDL:Phaser 7750DXF;CMD:Adobe PostScript 3, PCL;DES:Xerox Phaser 7750, Color Laser Printer, PostScript 3, Letter/A4/Tabloid/A3 Size;DRV:Dhpijs-pcl5e,R0,M0,Sv,TI,X600,Y600,C0,t100,l100,g100,p100,s70;
Model:  name = foomatic-db-compressed-ppds:0/ppd/foomatic-ppd/Xerox-Phaser_7750DXF-lj4dith.ppd
        natural_language = en
        make-and-model = Xerox Phaser 7750DXF Foomatic/lj4dith
        device-id = MFG:Xerox;MDL:Phaser 7750DXF;CMD:Adobe PostScript 3, PCL;DES:Xerox Phaser 7750, Color Laser Printer, PostScript 3, Letter/A4/Tabloid/A3 Size;DRV:Dlj4dith,R0,M0,TG;
Model:  name = foomatic-db-compressed-ppds:0/ppd/foomatic-ppd/Xerox-Phaser_7750DXF-ljet4.ppd
        natural_language = en
        make-and-model = Xerox Phaser 7750DXF Foomatic/ljet4
        device-id = MFG:Xerox;MDL:Phaser 7750DXF;CMD:Adobe PostScript 3, PCL;DES:Xerox Phaser 7750, Color Laser Printer, PostScript 3, Letter/A4/Tabloid/A3 Size;DRV:Dljet4,R0,M0,Sv,TG,X600,Y600,C0,t90,l90,g60,p30,s90;
Model:  name = foomatic-db-compressed-ppds:0/ppd/foomatic-ppd/Xerox-Phaser_7750DXF-ljet4d.ppd
        natural_language = en
        make-and-model = Xerox Phaser 7750DXF Foomatic/ljet4d
        device-id = MFG:Xerox;MDL:Phaser 7750DXF;CMD:Adobe PostScript 3, PCL;DES:Xerox Phaser 7750, Color Laser Printer, PostScript 3, Letter/A4/Tabloid/A3 Size;DRV:Dljet4d,R0,M0,TG;
Model:  name = foomatic-db-compressed-ppds:0/ppd/foomatic-ppd/Xerox-Phaser_7750DXF-Postscript.ppd
        natural_language = en
        make-and-model = Xerox Phaser 7750DXF Foomatic/Postscript
        device-id = MFG:Xerox;MDL:Phaser 7750DXF;CMD:Adobe PostScript 3, PCL;DES:Xerox Phaser 7750, Color Laser Printer, PostScript 3, Letter/A4/Tabloid/A3 Size;DRV:DPostscript,R0,M0,TP;
Model:  name = gutenprint.5.2://xerox-phaser_7750gx/expert
        natural_language = en
        make-and-model = Xerox Phaser 7750GX - CUPS+Gutenprint v5.2.8-pre1
        device-id = 
Model:  name = foomatic-db-compressed-ppds:0/ppd/foomatic-ppd/Xerox-Phaser_7750GX-hpijs-pcl5e.ppd
        natural_language = en
        make-and-model = Xerox Phaser 7750GX Foomatic/hpijs-pcl5e
        device-id = MFG:Xerox;MDL:Phaser 7750GX;CMD:Adobe PostScript 3, PCL;DES:Xerox Phaser 7750, Color Laser Printer, PostScript 3, Letter/A4/Tabloid/A3 Size;DRV:Dhpijs-pcl5e,R0,M0,Sv,TI,X600,Y600,C0,t100,l100,g100,p100,s70;
Model:  name = foomatic-db-compressed-ppds:0/ppd/foomatic-ppd/Xerox-Phaser_7750GX-lj4dith.ppd
        natural_language = en
        make-and-model = Xerox Phaser 7750GX Foomatic/lj4dith
        device-id = MFG:Xerox;MDL:Phaser 7750GX;CMD:Adobe PostScript 3, PCL;DES:Xerox Phaser 7750, Color Laser Printer, PostScript 3, Letter/A4/Tabloid/A3 Size;DRV:Dlj4dith,R0,M0,TG;
Model:  name = foomatic-db-compressed-ppds:0/ppd/foomatic-ppd/Xerox-Phaser_7750GX-ljet4.ppd
        natural_language = en
        make-and-model = Xerox Phaser 7750GX Foomatic/ljet4
        device-id = MFG:Xerox;MDL:Phaser 7750GX;CMD:Adobe PostScript 3, PCL;DES:Xerox Phaser 7750, Color Laser Printer, PostScript 3, Letter/A4/Tabloid/A3 Size;DRV:Dljet4,R0,M0,Sv,TG,X600,Y600,C0,t90,l90,g60,p30,s90;
Model:  name = foomatic-db-compressed-ppds:0/ppd/foomatic-ppd/Xerox-Phaser_7750GX-ljet4d.ppd
        natural_language = en
        make-and-model = Xerox Phaser 7750GX Foomatic/ljet4d
        device-id = MFG:Xerox;MDL:Phaser 7750GX;CMD:Adobe PostScript 3, PCL;DES:Xerox Phaser 7750, Color Laser Printer, PostScript 3, Letter/A4/Tabloid/A3 Size;DRV:Dljet4d,R0,M0,TG;
Model:  name = foomatic-db-compressed-ppds:0/ppd/foomatic-ppd/Xerox-Phaser_7750GX-Postscript.ppd
        natural_language = en
        make-and-model = Xerox Phaser 7750GX Foomatic/Postscript
        device-id = MFG:Xerox;MDL:Phaser 7750GX;CMD:Adobe PostScript 3, PCL;DES:Xerox Phaser 7750, Color Laser Printer, PostScript 3, Letter/A4/Tabloid/A3 Size;DRV:DPostscript,R0,M0,TP;
Model:  name = foomatic-db-compressed-ppds:0/ppd/foomatic-ppd/Xerox-Phaser_7760-Postscript.ppd
        natural_language = en
        make-and-model = Xerox Phaser 7760 Foomatic/Postscript (recommended)
        device-id = DRV:DPostscript,R1,M0,TP;
Model:  name = foomatic-db-compressed-ppds:1/ppd/foomatic-ppd/Xerox-Phaser_7760-Postscript.ppd
        natural_language = en
        make-and-model = Xerox Phaser 7760 Foomatic/Postscript (recommended)
        device-id = MFG:Xerox;MDL:Phaser 7760;
Model:  name = gutenprint.5.2://xerox-phaser_7760dn/expert
        natural_language = en
        make-and-model = Xerox Phaser 7760DN - CUPS+Gutenprint v5.2.8-pre1
        device-id = 
Model:  name = foomatic-db-compressed-ppds:0/ppd/foomatic-ppd/Xerox-Phaser_7760DN-hpijs-pcl5e.ppd
        natural_language = en
        make-and-model = Xerox Phaser 7760DN Foomatic/hpijs-pcl5e
        device-id = MFG:Xerox;MDL:Phaser 7760DN;CMD:Adobe PostScript 3, PCL;DES:Xerox Phaser 7760, Color Laser Printer, PostScript 3, Letter/A4/Tabloid/A3 Size;DRV:Dhpijs-pcl5e,R0,M0,Sv,TI,X600,Y600,C0,t100,l100,g100,p100,s70;
Model:  name = foomatic-db-compressed-ppds:0/ppd/foomatic-ppd/Xerox-Phaser_7760DN-lj4dith.ppd
        natural_language = en
        make-and-model = Xerox Phaser 7760DN Foomatic/lj4dith
        device-id = MFG:Xerox;MDL:Phaser 7760DN;CMD:Adobe PostScript 3, PCL;DES:Xerox Phaser 7760, Color Laser Printer, PostScript 3, Letter/A4/Tabloid/A3 Size;DRV:Dlj4dith,R0,M0,TG;
Model:  name = foomatic-db-compressed-ppds:0/ppd/foomatic-ppd/Xerox-Phaser_7760DN-ljet4.ppd
        natural_language = en
        make-and-model = Xerox Phaser 7760DN Foomatic/ljet4
        device-id = MFG:Xerox;MDL:Phaser 7760DN;CMD:Adobe PostScript 3, PCL;DES:Xerox Phaser 7760, Color Laser Printer, PostScript 3, Letter/A4/Tabloid/A3 Size;DRV:Dljet4,R0,M0,Sv,TG,X600,Y600,C0,t90,l90,g60,p30,s90;
Model:  name = foomatic-db-compressed-ppds:0/ppd/foomatic-ppd/Xerox-Phaser_7760DN-ljet4d.ppd
        natural_language = en
        make-and-model = Xerox Phaser 7760DN Foomatic/ljet4d
        device-id = MFG:Xerox;MDL:Phaser 7760DN;CMD:Adobe PostScript 3, PCL;DES:Xerox Phaser 7760, Color Laser Printer, PostScript 3, Letter/A4/Tabloid/A3 Size;DRV:Dljet4d,R0,M0,TG;
Model:  name = foomatic-db-compressed-ppds:0/ppd/foomatic-ppd/Xerox-Phaser_7760DN-Postscript.ppd
        natural_language = en
        make-and-model = Xerox Phaser 7760DN Foomatic/Postscript
        device-id = MFG:Xerox;MDL:Phaser 7760DN;CMD:Adobe PostScript 3, PCL;DES:Xerox Phaser 7760, Color Laser Printer, PostScript 3, Letter/A4/Tabloid/A3 Size;DRV:DPostscript,R0,M0,TP;
Model:  name = gutenprint.5.2://xerox-phaser_7760dx/expert
        natural_language = en
        make-and-model = Xerox Phaser 7760DX - CUPS+Gutenprint v5.2.8-pre1
        device-id = 
Model:  name = foomatic-db-compressed-ppds:0/ppd/foomatic-ppd/Xerox-Phaser_7760DX-hpijs-pcl5e.ppd
        natural_language = en
        make-and-model = Xerox Phaser 7760DX Foomatic/hpijs-pcl5e
        device-id = MFG:Xerox;MDL:Phaser 7760DX;CMD:Adobe PostScript 3, PCL;DES:Xerox Phaser 7760, Color Laser Printer, PostScript 3, Letter/A4/Tabloid/A3 Size;DRV:Dhpijs-pcl5e,R0,M0,Sv,TI,X600,Y600,C0,t100,l100,g100,p100,s70;
Model:  name = foomatic-db-compressed-ppds:0/ppd/foomatic-ppd/Xerox-Phaser_7760DX-lj4dith.ppd
        natural_language = en
        make-and-model = Xerox Phaser 7760DX Foomatic/lj4dith
        device-id = MFG:Xerox;MDL:Phaser 7760DX;CMD:Adobe PostScript 3, PCL;DES:Xerox Phaser 7760, Color Laser Printer, PostScript 3, Letter/A4/Tabloid/A3 Size;DRV:Dlj4dith,R0,M0,TG;
Model:  name = foomatic-db-compressed-ppds:0/ppd/foomatic-ppd/Xerox-Phaser_7760DX-ljet4.ppd
        natural_language = en
        make-and-model = Xerox Phaser 7760DX Foomatic/ljet4
        device-id = MFG:Xerox;MDL:Phaser 7760DX;CMD:Adobe PostScript 3, PCL;DES:Xerox Phaser 7760, Color Laser Printer, PostScript 3, Letter/A4/Tabloid/A3 Size;DRV:Dljet4,R0,M0,Sv,TG,X600,Y600,C0,t90,l90,g60,p30,s90;
Model:  name = foomatic-db-compressed-ppds:0/ppd/foomatic-ppd/Xerox-Phaser_7760DX-ljet4d.ppd
        natural_language = en
        make-and-model = Xerox Phaser 7760DX Foomatic/ljet4d
        device-id = MFG:Xerox;MDL:Phaser 7760DX;CMD:Adobe PostScript 3, PCL;DES:Xerox Phaser 7760, Color Laser Printer, PostScript 3, Letter/A4/Tabloid/A3 Size;DRV:Dljet4d,R0,M0,TG;
Model:  name = foomatic-db-compressed-ppds:0/ppd/foomatic-ppd/Xerox-Phaser_7760DX-Postscript.ppd
        natural_language = en
        make-and-model = Xerox Phaser 7760DX Foomatic/Postscript
        device-id = MFG:Xerox;MDL:Phaser 7760DX;CMD:Adobe PostScript 3, PCL;DES:Xerox Phaser 7760, Color Laser Printer, PostScript 3, Letter/A4/Tabloid/A3 Size;DRV:DPostscript,R0,M0,TP;
Model:  name = gutenprint.5.2://xerox-phaser_7760gx/expert
        natural_language = en
        make-and-model = Xerox Phaser 7760GX - CUPS+Gutenprint v5.2.8-pre1
        device-id = 
Model:  name = foomatic-db-compressed-ppds:0/ppd/foomatic-ppd/Xerox-Phaser_7760GX-hpijs-pcl5e.ppd
        natural_language = en
        make-and-model = Xerox Phaser 7760GX Foomatic/hpijs-pcl5e
        device-id = MFG:Xerox;MDL:Phaser 7760GX;CMD:Adobe PostScript 3, PCL;DES:Xerox Phaser 7760, Color Laser Printer, PostScript 3, Letter/A4/Tabloid/A3 Size;DRV:Dhpijs-pcl5e,R0,M0,Sv,TI,X600,Y600,C0,t100,l100,g100,p100,s70;
Model:  name = foomatic-db-compressed-ppds:0/ppd/foomatic-ppd/Xerox-Phaser_7760GX-lj4dith.ppd
        natural_language = en
        make-and-model = Xerox Phaser 7760GX Foomatic/lj4dith
        device-id = MFG:Xerox;MDL:Phaser 7760GX;CMD:Adobe PostScript 3, PCL;DES:Xerox Phaser 7760, Color Laser Printer, PostScript 3, Letter/A4/Tabloid/A3 Size;DRV:Dlj4dith,R0,M0,TG;
Model:  name = foomatic-db-compressed-ppds:0/ppd/foomatic-ppd/Xerox-Phaser_7760GX-ljet4.ppd
        natural_language = en
        make-and-model = Xerox Phaser 7760GX Foomatic/ljet4
        device-id = MFG:Xerox;MDL:Phaser 7760GX;CMD:Adobe PostScript 3, PCL;DES:Xerox Phaser 7760, Color Laser Printer, PostScript 3, Letter/A4/Tabloid/A3 Size;DRV:Dljet4,R0,M0,Sv,TG,X600,Y600,C0,t90,l90,g60,p30,s90;
Model:  name = foomatic-db-compressed-ppds:0/ppd/foomatic-ppd/Xerox-Phaser_7760GX-ljet4d.ppd
        natural_language = en
        make-and-model = Xerox Phaser 7760GX Foomatic/ljet4d
        device-id = MFG:Xerox;MDL:Phaser 7760GX;CMD:Adobe PostScript 3, PCL;DES:Xerox Phaser 7760, Color Laser Printer, PostScript 3, Letter/A4/Tabloid/A3 Size;DRV:Dljet4d,R0,M0,TG;
Model:  name = foomatic-db-compressed-ppds:0/ppd/foomatic-ppd/Xerox-Phaser_7760GX-Postscript.ppd
        natural_language = en
        make-and-model = Xerox Phaser 7760GX Foomatic/Postscript
        device-id = MFG:Xerox;MDL:Phaser 7760GX;CMD:Adobe PostScript 3, PCL;DES:Xerox Phaser 7760, Color Laser Printer, PostScript 3, Letter/A4/Tabloid/A3 Size;DRV:DPostscript,R0,M0,TP;
Model:  name = foomatic-db-compressed-ppds:0/ppd/foomatic-ppd/Xerox-Phaser_8200B-Postscript.ppd
        natural_language = en
        make-and-model = Xerox Phaser 8200B Foomatic/Postscript
        device-id = MANUFACTURER:Xerox;MODEL:Phaser 8200B;COMMAND SET:Adobe Level 3 PostScript;DESCRIPTION:Phaser 8200 Color Page Printer, PostScript Level 3,    Letter / Legal / A4 Size;DRV:DPostscript,R0,M0,TP;
Model:  name = foomatic-db-compressed-ppds:0/ppd/foomatic-ppd/Xerox-Phaser_8200DP-Postscript.ppd
        natural_language = en
        make-and-model = Xerox Phaser 8200DP Foomatic/Postscript
        device-id = MANUFACTURER:Xerox;MODEL:Phaser 8200DP;COMMAND SET:Adobe Level 3 PostScript;DESCRIPTION:Phaser 8200 Color Page Printer, PostScript Level 3,    Letter / Legal / A4 Size;DRV:DPostscript,R0,M0,TP;
Model:  name = foomatic-db-compressed-ppds:0/ppd/foomatic-ppd/Xerox-Phaser_8200DX-Postscript.ppd
        natural_language = en
        make-and-model = Xerox Phaser 8200DX Foomatic/Postscript
        device-id = MANUFACTURER:Xerox;MODEL:Phaser 8200DX;COMMAND SET:Adobe Level 3 PostScript;DESCRIPTION:Phaser 8200 Color Page Printer, PostScript Level 3,    Letter / Legal / A4 Size;DRV:DPostscript,R0,M0,TP;
Model:  name = foomatic-db-compressed-ppds:0/ppd/foomatic-ppd/Xerox-Phaser_8200N-Postscript.ppd
        natural_language = en
        make-and-model = Xerox Phaser 8200N Foomatic/Postscript
        device-id = MANUFACTURER:Xerox;MODEL:Phaser 8200N;COMMAND SET:Adobe Level 3 PostScript;DESCRIPTION:Phaser 8200 Color Page Printer, PostScript Level 3,    Letter / Legal / A4 Size;DRV:DPostscript,R0,M0,TP;
Model:  name = gutenprint.5.2://xerox-phaser_8400b/expert
        natural_language = en
        make-and-model = Xerox Phaser 8400B - CUPS+Gutenprint v5.2.8-pre1
        device-id = 
Model:  name = foomatic-db-compressed-ppds:0/ppd/foomatic-ppd/Xerox-Phaser_8400B-hpijs-pcl5e.ppd
        natural_language = en
        make-and-model = Xerox Phaser 8400B Foomatic/hpijs-pcl5e
        device-id = MFG:Xerox;MDL:Phaser 8400B;CMD:Adobe PostScript 3, PCL;DES:Xerox Phaser 8400, Color Printer, PostScript 3, Letter/A4 Size;DRV:Dhpijs-pcl5e,R0,M0,Sv,TI,X600,Y600,C0,t100,l100,g100,p100,s70;
Model:  name = foomatic-db-compressed-ppds:0/ppd/foomatic-ppd/Xerox-Phaser_8400B-lj4dith.ppd
        natural_language = en
        make-and-model = Xerox Phaser 8400B Foomatic/lj4dith
        device-id = MFG:Xerox;MDL:Phaser 8400B;CMD:Adobe PostScript 3, PCL;DES:Xerox Phaser 8400, Color Printer, PostScript 3, Letter/A4 Size;DRV:Dlj4dith,R0,M0,TG;
Model:  name = foomatic-db-compressed-ppds:0/ppd/foomatic-ppd/Xerox-Phaser_8400B-ljet4.ppd
        natural_language = en
        make-and-model = Xerox Phaser 8400B Foomatic/ljet4
        device-id = MFG:Xerox;MDL:Phaser 8400B;CMD:Adobe PostScript 3, PCL;DES:Xerox Phaser 8400, Color Printer, PostScript 3, Letter/A4 Size;DRV:Dljet4,R0,M0,Sv,TG,X600,Y600,C0,t90,l90,g60,p30,s90;
Model:  name = foomatic-db-compressed-ppds:0/ppd/foomatic-ppd/Xerox-Phaser_8400B-ljet4d.ppd
        natural_language = en
        make-and-model = Xerox Phaser 8400B Foomatic/ljet4d
        device-id = MFG:Xerox;MDL:Phaser 8400B;CMD:Adobe PostScript 3, PCL;DES:Xerox Phaser 8400, Color Printer, PostScript 3, Letter/A4 Size;DRV:Dljet4d,R0,M0,TG;
Model:  name = foomatic-db-compressed-ppds:0/ppd/foomatic-ppd/Xerox-Phaser_8400B-Postscript.ppd
        natural_language = en
        make-and-model = Xerox Phaser 8400B Foomatic/Postscript
        device-id = MFG:Xerox;MDL:Phaser 8400B;CMD:Adobe PostScript 3, PCL;DES:Xerox Phaser 8400, Color Printer, PostScript 3, Letter/A4 Size;DRV:DPostscript,R0,M0,TP;
Model:  name = gutenprint.5.2://xerox-phaser_8400bd/expert
        natural_language = en
        make-and-model = Xerox Phaser 8400BD - CUPS+Gutenprint v5.2.8-pre1
        device-id = 
Model:  name = foomatic-db-compressed-ppds:0/ppd/foomatic-ppd/Xerox-Phaser_8400BD-hpijs-pcl5e.ppd
        natural_language = en
        make-and-model = Xerox Phaser 8400BD Foomatic/hpijs-pcl5e
        device-id = MFG:Xerox;MDL:Phaser 8400BD;CMD:Adobe PostScript 3, PCL;DES:Xerox Phaser 8400, Color Printer, PostScript 3, Letter/A4 Size;DRV:Dhpijs-pcl5e,R0,M0,Sv,TI,X600,Y600,C0,t100,l100,g100,p100,s70;
Model:  name = foomatic-db-compressed-ppds:0/ppd/foomatic-ppd/Xerox-Phaser_8400BD-lj4dith.ppd
        natural_language = en
        make-and-model = Xerox Phaser 8400BD Foomatic/lj4dith
        device-id = MFG:Xerox;MDL:Phaser 8400BD;CMD:Adobe PostScript 3, PCL;DES:Xerox Phaser 8400, Color Printer, PostScript 3, Letter/A4 Size;DRV:Dlj4dith,R0,M0,TG;
Model:  name = foomatic-db-compressed-ppds:0/ppd/foomatic-ppd/Xerox-Phaser_8400BD-ljet4.ppd
        natural_language = en
        make-and-model = Xerox Phaser 8400BD Foomatic/ljet4
        device-id = MFG:Xerox;MDL:Phaser 8400BD;CMD:Adobe PostScript 3, PCL;DES:Xerox Phaser 8400, Color Printer, PostScript 3, Letter/A4 Size;DRV:Dljet4,R0,M0,Sv,TG,X600,Y600,C0,t90,l90,g60,p30,s90;
Model:  name = foomatic-db-compressed-ppds:0/ppd/foomatic-ppd/Xerox-Phaser_8400BD-ljet4d.ppd
        natural_language = en
        make-and-model = Xerox Phaser 8400BD Foomatic/ljet4d
        device-id = MFG:Xerox;MDL:Phaser 8400BD;CMD:Adobe PostScript 3, PCL;DES:Xerox Phaser 8400, Color Printer, PostScript 3, Letter/A4 Size;DRV:Dljet4d,R0,M0,TG;
Model:  name = foomatic-db-compressed-ppds:0/ppd/foomatic-ppd/Xerox-Phaser_8400BD-Postscript.ppd
        natural_language = en
        make-and-model = Xerox Phaser 8400BD Foomatic/Postscript
        device-id = MFG:Xerox;MDL:Phaser 8400BD;CMD:Adobe PostScript 3, PCL;DES:Xerox Phaser 8400, Color Printer, PostScript 3, Letter/A4 Size;DRV:DPostscript,R0,M0,TP;
Model:  name = gutenprint.5.2://xerox-phaser_8400dp/expert
        natural_language = en
        make-and-model = Xerox Phaser 8400DP - CUPS+Gutenprint v5.2.8-pre1
        device-id = 
Model:  name = foomatic-db-compressed-ppds:0/ppd/foomatic-ppd/Xerox-Phaser_8400DP-hpijs-pcl5e.ppd
        natural_language = en
        make-and-model = Xerox Phaser 8400DP Foomatic/hpijs-pcl5e
        device-id = MFG:Xerox;MDL:Phaser 8400DP;CMD:Adobe PostScript 3, PCL;DES:Xerox Phaser 8400, Color Printer, PostScript 3, Letter/A4 Size;DRV:Dhpijs-pcl5e,R0,M0,Sv,TI,X600,Y600,C0,t100,l100,g100,p100,s70;
Model:  name = foomatic-db-compressed-ppds:0/ppd/foomatic-ppd/Xerox-Phaser_8400DP-lj4dith.ppd
        natural_language = en
        make-and-model = Xerox Phaser 8400DP Foomatic/lj4dith
        device-id = MFG:Xerox;MDL:Phaser 8400DP;CMD:Adobe PostScript 3, PCL;DES:Xerox Phaser 8400, Color Printer, PostScript 3, Letter/A4 Size;DRV:Dlj4dith,R0,M0,TG;
Model:  name = foomatic-db-compressed-ppds:0/ppd/foomatic-ppd/Xerox-Phaser_8400DP-ljet4.ppd
        natural_language = en
        make-and-model = Xerox Phaser 8400DP Foomatic/ljet4
        device-id = MFG:Xerox;MDL:Phaser 8400DP;CMD:Adobe PostScript 3, PCL;DES:Xerox Phaser 8400, Color Printer, PostScript 3, Letter/A4 Size;DRV:Dljet4,R0,M0,Sv,TG,X600,Y600,C0,t90,l90,g60,p30,s90;
Model:  name = foomatic-db-compressed-ppds:0/ppd/foomatic-ppd/Xerox-Phaser_8400DP-ljet4d.ppd
        natural_language = en
        make-and-model = Xerox Phaser 8400DP Foomatic/ljet4d
        device-id = MFG:Xerox;MDL:Phaser 8400DP;CMD:Adobe PostScript 3, PCL;DES:Xerox Phaser 8400, Color Printer, PostScript 3, Letter/A4 Size;DRV:Dljet4d,R0,M0,TG;
Model:  name = foomatic-db-compressed-ppds:0/ppd/foomatic-ppd/Xerox-Phaser_8400DP-Postscript.ppd
        natural_language = en
        make-and-model = Xerox Phaser 8400DP Foomatic/Postscript
        device-id = MFG:Xerox;MDL:Phaser 8400DP;CMD:Adobe PostScript 3, PCL;DES:Xerox Phaser 8400, Color Printer, PostScript 3, Letter/A4 Size;DRV:DPostscript,R0,M0,TP;
Model:  name = gutenprint.5.2://xerox-phaser_8400dx/expert
        natural_language = en
        make-and-model = Xerox Phaser 8400DX - CUPS+Gutenprint v5.2.8-pre1
        device-id = 
Model:  name = foomatic-db-compressed-ppds:0/ppd/foomatic-ppd/Xerox-Phaser_8400DX-hpijs-pcl5e.ppd
        natural_language = en
        make-and-model = Xerox Phaser 8400DX Foomatic/hpijs-pcl5e
        device-id = MFG:Xerox;MDL:Phaser 8400DX;CMD:Adobe PostScript 3, PCL;DES:Xerox Phaser 8400, Color Printer, PostScript 3, Letter/A4 Size;DRV:Dhpijs-pcl5e,R0,M0,Sv,TI,X600,Y600,C0,t100,l100,g100,p100,s70;
Model:  name = foomatic-db-compressed-ppds:0/ppd/foomatic-ppd/Xerox-Phaser_8400DX-lj4dith.ppd
        natural_language = en
        make-and-model = Xerox Phaser 8400DX Foomatic/lj4dith
        device-id = MFG:Xerox;MDL:Phaser 8400DX;CMD:Adobe PostScript 3, PCL;DES:Xerox Phaser 8400, Color Printer, PostScript 3, Letter/A4 Size;DRV:Dlj4dith,R0,M0,TG;
Model:  name = foomatic-db-compressed-ppds:0/ppd/foomatic-ppd/Xerox-Phaser_8400DX-ljet4.ppd
        natural_language = en
        make-and-model = Xerox Phaser 8400DX Foomatic/ljet4
        device-id = MFG:Xerox;MDL:Phaser 8400DX;CMD:Adobe PostScript 3, PCL;DES:Xerox Phaser 8400, Color Printer, PostScript 3, Letter/A4 Size;DRV:Dljet4,R0,M0,Sv,TG,X600,Y600,C0,t90,l90,g60,p30,s90;
Model:  name = foomatic-db-compressed-ppds:0/ppd/foomatic-ppd/Xerox-Phaser_8400DX-ljet4d.ppd
        natural_language = en
        make-and-model = Xerox Phaser 8400DX Foomatic/ljet4d
        device-id = MFG:Xerox;MDL:Phaser 8400DX;CMD:Adobe PostScript 3, PCL;DES:Xerox Phaser 8400, Color Printer, PostScript 3, Letter/A4 Size;DRV:Dljet4d,R0,M0,TG;
Model:  name = foomatic-db-compressed-ppds:0/ppd/foomatic-ppd/Xerox-Phaser_8400DX-Postscript.ppd
        natural_language = en
        make-and-model = Xerox Phaser 8400DX Foomatic/Postscript
        device-id = MFG:Xerox;MDL:Phaser 8400DX;CMD:Adobe PostScript 3, PCL;DES:Xerox Phaser 8400, Color Printer, PostScript 3, Letter/A4 Size;DRV:DPostscript,R0,M0,TP;
Model:  name = gutenprint.5.2://xerox-phaser_8400n/expert
        natural_language = en
        make-and-model = Xerox Phaser 8400N - CUPS+Gutenprint v5.2.8-pre1
        device-id = 
Model:  name = foomatic-db-compressed-ppds:0/ppd/foomatic-ppd/Xerox-Phaser_8400N-hpijs-pcl5e.ppd
        natural_language = en
        make-and-model = Xerox Phaser 8400N Foomatic/hpijs-pcl5e
        device-id = MFG:Xerox;MDL:Phaser 8400N;CMD:Adobe PostScript 3, PCL;DES:Xerox Phaser 8400, Color Printer, PostScript 3, Letter/A4 Size;DRV:Dhpijs-pcl5e,R0,M0,Sv,TI,X600,Y600,C0,t100,l100,g100,p100,s70;
Model:  name = foomatic-db-compressed-ppds:0/ppd/foomatic-ppd/Xerox-Phaser_8400N-lj4dith.ppd
        natural_language = en
        make-and-model = Xerox Phaser 8400N Foomatic/lj4dith
        device-id = MFG:Xerox;MDL:Phaser 8400N;CMD:Adobe PostScript 3, PCL;DES:Xerox Phaser 8400, Color Printer, PostScript 3, Letter/A4 Size;DRV:Dlj4dith,R0,M0,TG;
Model:  name = foomatic-db-compressed-ppds:0/ppd/foomatic-ppd/Xerox-Phaser_8400N-ljet4.ppd
        natural_language = en
        make-and-model = Xerox Phaser 8400N Foomatic/ljet4
        device-id = MFG:Xerox;MDL:Phaser 8400N;CMD:Adobe PostScript 3, PCL;DES:Xerox Phaser 8400, Color Printer, PostScript 3, Letter/A4 Size;DRV:Dljet4,R0,M0,Sv,TG,X600,Y600,C0,t90,l90,g60,p30,s90;
Model:  name = foomatic-db-compressed-ppds:0/ppd/foomatic-ppd/Xerox-Phaser_8400N-ljet4d.ppd
        natural_language = en
        make-and-model = Xerox Phaser 8400N Foomatic/ljet4d
        device-id = MFG:Xerox;MDL:Phaser 8400N;CMD:Adobe PostScript 3, PCL;DES:Xerox Phaser 8400, Color Printer, PostScript 3, Letter/A4 Size;DRV:Dljet4d,R0,M0,TG;
Model:  name = foomatic-db-compressed-ppds:0/ppd/foomatic-ppd/Xerox-Phaser_8400N-Postscript.ppd
        natural_language = en
        make-and-model = Xerox Phaser 8400N Foomatic/Postscript
        device-id = MFG:Xerox;MDL:Phaser 8400N;CMD:Adobe PostScript 3, PCL;DES:Xerox Phaser 8400, Color Printer, PostScript 3, Letter/A4 Size;DRV:DPostscript,R0,M0,TP;
Model:  name = gutenprint.5.2://xerox-phaser_8500dn/expert
        natural_language = en
        make-and-model = Xerox Phaser 8500DN - CUPS+Gutenprint v5.2.8-pre1
        device-id = 
Model:  name = foomatic-db-compressed-ppds:0/ppd/foomatic-ppd/Xerox-Phaser_8500DN-hpijs-pcl5e.ppd
        natural_language = en
        make-and-model = Xerox Phaser 8500DN Foomatic/hpijs-pcl5e
        device-id = MFG:Xerox;MDL:Phaser 8500DN;CMD:Adobe PostScript 3, PCL;DES:Xerox Phaser 8500, Color Laser Printer, PostScript 3, Letter/A4 Size;DRV:Dhpijs-pcl5e,R0,M0,Sv,TI,X600,Y600,C0,t100,l100,g100,p100,s70;
Model:  name = foomatic-db-compressed-ppds:0/ppd/foomatic-ppd/Xerox-Phaser_8500DN-lj4dith.ppd
        natural_language = en
        make-and-model = Xerox Phaser 8500DN Foomatic/lj4dith
        device-id = MFG:Xerox;MDL:Phaser 8500DN;CMD:Adobe PostScript 3, PCL;DES:Xerox Phaser 8500, Color Laser Printer, PostScript 3, Letter/A4 Size;DRV:Dlj4dith,R0,M0,TG;
Model:  name = foomatic-db-compressed-ppds:0/ppd/foomatic-ppd/Xerox-Phaser_8500DN-ljet4.ppd
        natural_language = en
        make-and-model = Xerox Phaser 8500DN Foomatic/ljet4
        device-id = MFG:Xerox;MDL:Phaser 8500DN;CMD:Adobe PostScript 3, PCL;DES:Xerox Phaser 8500, Color Laser Printer, PostScript 3, Letter/A4 Size;DRV:Dljet4,R0,M0,Sv,TG,X600,Y600,C0,t90,l90,g60,p30,s90;
Model:  name = foomatic-db-compressed-ppds:0/ppd/foomatic-ppd/Xerox-Phaser_8500DN-ljet4d.ppd
        natural_language = en
        make-and-model = Xerox Phaser 8500DN Foomatic/ljet4d
        device-id = MFG:Xerox;MDL:Phaser 8500DN;CMD:Adobe PostScript 3, PCL;DES:Xerox Phaser 8500, Color Laser Printer, PostScript 3, Letter/A4 Size;DRV:Dljet4d,R0,M0,TG;
Model:  name = foomatic-db-compressed-ppds:0/ppd/foomatic-ppd/Xerox-Phaser_8500DN-Postscript.ppd
        natural_language = en
        make-and-model = Xerox Phaser 8500DN Foomatic/Postscript
        device-id = MFG:Xerox;MDL:Phaser 8500DN;CMD:Adobe PostScript 3, PCL;DES:Xerox Phaser 8500, Color Laser Printer, PostScript 3, Letter/A4 Size;DRV:DPostscript,R0,M0,TP;
Model:  name = gutenprint.5.2://xerox-phaser_8500n/expert
        natural_language = en
        make-and-model = Xerox Phaser 8500N - CUPS+Gutenprint v5.2.8-pre1
        device-id = 
Model:  name = foomatic-db-compressed-ppds:0/ppd/foomatic-ppd/Xerox-Phaser_8500N-hpijs-pcl5e.ppd
        natural_language = en
        make-and-model = Xerox Phaser 8500N Foomatic/hpijs-pcl5e
        device-id = MFG:Xerox;MDL:Phaser 8500N;CMD:Adobe PostScript 3, PCL;DES:Xerox Phaser 8500, Color Laser Printer, PostScript 3, Letter/A4 Size;DRV:Dhpijs-pcl5e,R0,M0,Sv,TI,X600,Y600,C0,t100,l100,g100,p100,s70;
Model:  name = foomatic-db-compressed-ppds:0/ppd/foomatic-ppd/Xerox-Phaser_8500N-lj4dith.ppd
        natural_language = en
        make-and-model = Xerox Phaser 8500N Foomatic/lj4dith
        device-id = MFG:Xerox;MDL:Phaser 8500N;CMD:Adobe PostScript 3, PCL;DES:Xerox Phaser 8500, Color Laser Printer, PostScript 3, Letter/A4 Size;DRV:Dlj4dith,R0,M0,TG;
Model:  name = foomatic-db-compressed-ppds:0/ppd/foomatic-ppd/Xerox-Phaser_8500N-ljet4.ppd
        natural_language = en
        make-and-model = Xerox Phaser 8500N Foomatic/ljet4
        device-id = MFG:Xerox;MDL:Phaser 8500N;CMD:Adobe PostScript 3, PCL;DES:Xerox Phaser 8500, Color Laser Printer, PostScript 3, Letter/A4 Size;DRV:Dljet4,R0,M0,Sv,TG,X600,Y600,C0,t90,l90,g60,p30,s90;
Model:  name = foomatic-db-compressed-ppds:0/ppd/foomatic-ppd/Xerox-Phaser_8500N-ljet4d.ppd
        natural_language = en
        make-and-model = Xerox Phaser 8500N Foomatic/ljet4d
        device-id = MFG:Xerox;MDL:Phaser 8500N;CMD:Adobe PostScript 3, PCL;DES:Xerox Phaser 8500, Color Laser Printer, PostScript 3, Letter/A4 Size;DRV:Dljet4d,R0,M0,TG;
Model:  name = foomatic-db-compressed-ppds:0/ppd/foomatic-ppd/Xerox-Phaser_8500N-Postscript.ppd
        natural_language = en
        make-and-model = Xerox Phaser 8500N Foomatic/Postscript
        device-id = MFG:Xerox;MDL:Phaser 8500N;CMD:Adobe PostScript 3, PCL;DES:Xerox Phaser 8500, Color Laser Printer, PostScript 3, Letter/A4 Size;DRV:DPostscript,R0,M0,TP;
Model:  name = gutenprint.5.2://xerox-phaser_8550dp/expert
        natural_language = en
        make-and-model = Xerox Phaser 8550DP - CUPS+Gutenprint v5.2.8-pre1
        device-id = 
Model:  name = foomatic-db-compressed-ppds:0/ppd/foomatic-ppd/Xerox-Phaser_8550DP-hpijs-pcl5e.ppd
        natural_language = en
        make-and-model = Xerox Phaser 8550DP Foomatic/hpijs-pcl5e
        device-id = MFG:Xerox;MDL:Phaser 8550DP;CMD:Adobe PostScript 3, PCL;DES:Xerox Phaser 8550, Color Laser Printer, PostScript 3, Letter/A4 Size;DRV:Dhpijs-pcl5e,R0,M0,Sv,TI,X600,Y600,C0,t100,l100,g100,p100,s70;
Model:  name = foomatic-db-compressed-ppds:0/ppd/foomatic-ppd/Xerox-Phaser_8550DP-lj4dith.ppd
        natural_language = en
        make-and-model = Xerox Phaser 8550DP Foomatic/lj4dith
        device-id = MFG:Xerox;MDL:Phaser 8550DP;CMD:Adobe PostScript 3, PCL;DES:Xerox Phaser 8550, Color Laser Printer, PostScript 3, Letter/A4 Size;DRV:Dlj4dith,R0,M0,TG;
Model:  name = foomatic-db-compressed-ppds:0/ppd/foomatic-ppd/Xerox-Phaser_8550DP-ljet4.ppd
        natural_language = en
        make-and-model = Xerox Phaser 8550DP Foomatic/ljet4
        device-id = MFG:Xerox;MDL:Phaser 8550DP;CMD:Adobe PostScript 3, PCL;DES:Xerox Phaser 8550, Color Laser Printer, PostScript 3, Letter/A4 Size;DRV:Dljet4,R0,M0,Sv,TG,X600,Y600,C0,t90,l90,g60,p30,s90;
Model:  name = foomatic-db-compressed-ppds:0/ppd/foomatic-ppd/Xerox-Phaser_8550DP-ljet4d.ppd
        natural_language = en
        make-and-model = Xerox Phaser 8550DP Foomatic/ljet4d
        device-id = MFG:Xerox;MDL:Phaser 8550DP;CMD:Adobe PostScript 3, PCL;DES:Xerox Phaser 8550, Color Laser Printer, PostScript 3, Letter/A4 Size;DRV:Dljet4d,R0,M0,TG;
Model:  name = foomatic-db-compressed-ppds:0/ppd/foomatic-ppd/Xerox-Phaser_8550DP-Postscript.ppd
        natural_language = en
        make-and-model = Xerox Phaser 8550DP Foomatic/Postscript
        device-id = MFG:Xerox;MDL:Phaser 8550DP;CMD:Adobe PostScript 3, PCL;DES:Xerox Phaser 8550, Color Laser Printer, PostScript 3, Letter/A4 Size;DRV:DPostscript,R0,M0,TP;
Model:  name = gutenprint.5.2://xerox-phaser_8550dt/expert
        natural_language = en
        make-and-model = Xerox Phaser 8550DT - CUPS+Gutenprint v5.2.8-pre1
        device-id = 
Model:  name = foomatic-db-compressed-ppds:0/ppd/foomatic-ppd/Xerox-Phaser_8550DT-hpijs-pcl5e.ppd
        natural_language = en
        make-and-model = Xerox Phaser 8550DT Foomatic/hpijs-pcl5e
        device-id = MFG:Xerox;MDL:Phaser 8550DT;CMD:Adobe PostScript 3, PCL;DES:Xerox Phaser 8550, Color Laser Printer, PostScript 3, Letter/A4 Size;DRV:Dhpijs-pcl5e,R0,M0,Sv,TI,X600,Y600,C0,t100,l100,g100,p100,s70;
Model:  name = foomatic-db-compressed-ppds:0/ppd/foomatic-ppd/Xerox-Phaser_8550DT-lj4dith.ppd
        natural_language = en
        make-and-model = Xerox Phaser 8550DT Foomatic/lj4dith
        device-id = MFG:Xerox;MDL:Phaser 8550DT;CMD:Adobe PostScript 3, PCL;DES:Xerox Phaser 8550, Color Laser Printer, PostScript 3, Letter/A4 Size;DRV:Dlj4dith,R0,M0,TG;
Model:  name = foomatic-db-compressed-ppds:0/ppd/foomatic-ppd/Xerox-Phaser_8550DT-ljet4.ppd
        natural_language = en
        make-and-model = Xerox Phaser 8550DT Foomatic/ljet4
        device-id = MFG:Xerox;MDL:Phaser 8550DT;CMD:Adobe PostScript 3, PCL;DES:Xerox Phaser 8550, Color Laser Printer, PostScript 3, Letter/A4 Size;DRV:Dljet4,R0,M0,Sv,TG,X600,Y600,C0,t90,l90,g60,p30,s90;
Model:  name = foomatic-db-compressed-ppds:0/ppd/foomatic-ppd/Xerox-Phaser_8550DT-ljet4d.ppd
        natural_language = en
        make-and-model = Xerox Phaser 8550DT Foomatic/ljet4d
        device-id = MFG:Xerox;MDL:Phaser 8550DT;CMD:Adobe PostScript 3, PCL;DES:Xerox Phaser 8550, Color Laser Printer, PostScript 3, Letter/A4 Size;DRV:Dljet4d,R0,M0,TG;
Model:  name = foomatic-db-compressed-ppds:0/ppd/foomatic-ppd/Xerox-Phaser_8550DT-Postscript.ppd
        natural_language = en
        make-and-model = Xerox Phaser 8550DT Foomatic/Postscript
        device-id = MFG:Xerox;MDL:Phaser 8550DT;CMD:Adobe PostScript 3, PCL;DES:Xerox Phaser 8550, Color Laser Printer, PostScript 3, Letter/A4 Size;DRV:DPostscript,R0,M0,TP;
Model:  name = gutenprint.5.2://xerox-phaser_8550dx/expert
        natural_language = en
        make-and-model = Xerox Phaser 8550DX - CUPS+Gutenprint v5.2.8-pre1
        device-id = 
Model:  name = foomatic-db-compressed-ppds:0/ppd/foomatic-ppd/Xerox-Phaser_8550DX-hpijs-pcl5e.ppd
        natural_language = en
        make-and-model = Xerox Phaser 8550DX Foomatic/hpijs-pcl5e
        device-id = MFG:Xerox;MDL:Phaser 8550DX;CMD:Adobe PostScript 3, PCL;DES:Xerox Phaser 8550, Color Laser Printer, PostScript 3, Letter/A4 Size;DRV:Dhpijs-pcl5e,R0,M0,Sv,TI,X600,Y600,C0,t100,l100,g100,p100,s70;
Model:  name = foomatic-db-compressed-ppds:0/ppd/foomatic-ppd/Xerox-Phaser_8550DX-lj4dith.ppd
        natural_language = en
        make-and-model = Xerox Phaser 8550DX Foomatic/lj4dith
        device-id = MFG:Xerox;MDL:Phaser 8550DX;CMD:Adobe PostScript 3, PCL;DES:Xerox Phaser 8550, Color Laser Printer, PostScript 3, Letter/A4 Size;DRV:Dlj4dith,R0,M0,TG;
Model:  name = foomatic-db-compressed-ppds:0/ppd/foomatic-ppd/Xerox-Phaser_8550DX-ljet4.ppd
        natural_language = en
        make-and-model = Xerox Phaser 8550DX Foomatic/ljet4
        device-id = MFG:Xerox;MDL:Phaser 8550DX;CMD:Adobe PostScript 3, PCL;DES:Xerox Phaser 8550, Color Laser Printer, PostScript 3, Letter/A4 Size;DRV:Dljet4,R0,M0,Sv,TG,X600,Y600,C0,t90,l90,g60,p30,s90;
Model:  name = foomatic-db-compressed-ppds:0/ppd/foomatic-ppd/Xerox-Phaser_8550DX-ljet4d.ppd
        natural_language = en
        make-and-model = Xerox Phaser 8550DX Foomatic/ljet4d
        device-id = MFG:Xerox;MDL:Phaser 8550DX;CMD:Adobe PostScript 3, PCL;DES:Xerox Phaser 8550, Color Laser Printer, PostScript 3, Letter/A4 Size;DRV:Dljet4d,R0,M0,TG;
Model:  name = foomatic-db-compressed-ppds:0/ppd/foomatic-ppd/Xerox-Phaser_8550DX-Postscript.ppd
        natural_language = en
        make-and-model = Xerox Phaser 8550DX Foomatic/Postscript
        device-id = MFG:Xerox;MDL:Phaser 8550DX;CMD:Adobe PostScript 3, PCL;DES:Xerox Phaser 8550, Color Laser Printer, PostScript 3, Letter/A4 Size;DRV:DPostscript,R0,M0,TP;
Model:  name = foomatic-db-compressed-ppds:0/ppd/foomatic-ppd/Xerox-Phaser_8560-Postscript.ppd
        natural_language = en
        make-and-model = Xerox Phaser 8560 Foomatic/Postscript (recommended)
        device-id = DRV:DPostscript,R1,M0,TP;
Model:  name = foomatic-db-compressed-ppds:1/ppd/foomatic-ppd/Xerox-Phaser_8560-Postscript.ppd
        natural_language = en
        make-and-model = Xerox Phaser 8560 Foomatic/Postscript (recommended)
        device-id = MFG:Xerox;MDL:Phaser 8560;
Model:  name = gutenprint.5.2://xerox-phaser_8560dn/expert
        natural_language = en
        make-and-model = Xerox Phaser 8560DN - CUPS+Gutenprint v5.2.8-pre1
        device-id = 
Model:  name = foomatic-db-compressed-ppds:0/ppd/foomatic-ppd/Xerox-Phaser_8560DN-hpijs-pcl5e.ppd
        natural_language = en
        make-and-model = Xerox Phaser 8560DN Foomatic/hpijs-pcl5e
        device-id = MFG:Xerox;MDL:Phaser 8560DN;CMD:Adobe PostScript 3, PCL;DES:Xerox Phaser 8560, Color Printer, PostScript 3, Letter/A4 Size;DRV:Dhpijs-pcl5e,R0,M0,Sv,TI,X600,Y600,C0,t100,l100,g100,p100,s70;
Model:  name = foomatic-db-compressed-ppds:0/ppd/foomatic-ppd/Xerox-Phaser_8560DN-lj4dith.ppd
        natural_language = en
        make-and-model = Xerox Phaser 8560DN Foomatic/lj4dith
        device-id = MFG:Xerox;MDL:Phaser 8560DN;CMD:Adobe PostScript 3, PCL;DES:Xerox Phaser 8560, Color Printer, PostScript 3, Letter/A4 Size;DRV:Dlj4dith,R0,M0,TG;
Model:  name = foomatic-db-compressed-ppds:0/ppd/foomatic-ppd/Xerox-Phaser_8560DN-ljet4.ppd
        natural_language = en
        make-and-model = Xerox Phaser 8560DN Foomatic/ljet4
        device-id = MFG:Xerox;MDL:Phaser 8560DN;CMD:Adobe PostScript 3, PCL;DES:Xerox Phaser 8560, Color Printer, PostScript 3, Letter/A4 Size;DRV:Dljet4,R0,M0,Sv,TG,X600,Y600,C0,t90,l90,g60,p30,s90;
Model:  name = foomatic-db-compressed-ppds:0/ppd/foomatic-ppd/Xerox-Phaser_8560DN-ljet4d.ppd
        natural_language = en
        make-and-model = Xerox Phaser 8560DN Foomatic/ljet4d
        device-id = MFG:Xerox;MDL:Phaser 8560DN;CMD:Adobe PostScript 3, PCL;DES:Xerox Phaser 8560, Color Printer, PostScript 3, Letter/A4 Size;DRV:Dljet4d,R0,M0,TG;
Model:  name = foomatic-db-compressed-ppds:0/ppd/foomatic-ppd/Xerox-Phaser_8560DN-Postscript.ppd
        natural_language = en
        make-and-model = Xerox Phaser 8560DN Foomatic/Postscript
        device-id = MFG:Xerox;MDL:Phaser 8560DN;CMD:Adobe PostScript 3, PCL;DES:Xerox Phaser 8560, Color Printer, PostScript 3, Letter/A4 Size;DRV:DPostscript,R0,M0,TP;
Model:  name = foomatic-db-compressed-ppds:0/ppd/foomatic-ppd/Xerox-Phaser_8860-cljet5.ppd
        natural_language = en
        make-and-model = Xerox Phaser 8860 Foomatic/cljet5
        device-id = MFG:Xerox;MDL:Phaser 8860;CMD:Adobe PostScript 3, PCL;DES:Xerox Phaser 8860, Color Printer, PostScript 3, Letter/A4 Size;DRV:Dcljet5,R0,M0,TG;
Model:  name = foomatic-db-compressed-ppds:0/ppd/foomatic-ppd/Xerox-Phaser_8860-hpijs-pcl5c.ppd
        natural_language = en
        make-and-model = Xerox Phaser 8860 Foomatic/hpijs-pcl5c
        device-id = MFG:Xerox;MDL:Phaser 8860;CMD:Adobe PostScript 3, PCL;DES:Xerox Phaser 8860, Color Printer, PostScript 3, Letter/A4 Size;DRV:Dhpijs-pcl5c,R0,M0,Sv,TI,X600,Y600,C1,t100,l100,g100,p100,s70;
Model:  name = foomatic-db-compressed-ppds:0/ppd/foomatic-ppd/Xerox-Phaser_8860-Postscript.ppd
        natural_language = en
        make-and-model = Xerox Phaser 8860 Foomatic/Postscript
        device-id = MFG:Xerox;MDL:Phaser 8860;CMD:Adobe PostScript 3, PCL;DES:Xerox Phaser 8860, Color Printer, PostScript 3, Letter/A4 Size;DRV:DPostscript,R0,M0,TP;
Model:  name = foomatic-db-compressed-ppds:0/ppd/foomatic-ppd/Xerox-WorkCentre_24-Postscript.ppd
        natural_language = en
        make-and-model = Xerox WorkCentre 24 Foomatic/Postscript
        device-id = MANUFACTURER:XEROX;MODEL:WorkCentre 24;DESCRIPTION:XEROX WorkCentre 24;DRV:DPostscript,R0,M0,TP;
Model:  name = foomatic-db-compressed-ppds:0/ppd/foomatic-ppd/Xerox-WorkCentre_450cp-cdj550.ppd
        natural_language = en
        make-and-model = Xerox WorkCentre 450cp Foomatic/cdj550 (recommended)
        device-id = DRV:Dcdj550,R1,M0,TG;
Model:  name = foomatic-db-compressed-ppds:1/ppd/foomatic-ppd/Xerox-WorkCentre_450cp-cdj550.ppd
        natural_language = en
        make-and-model = Xerox WorkCentre 450cp Foomatic/cdj550 (recommended)
        device-id = MFG:Xerox;MDL:WorkCentre 450cp;
Model:  name = foomatic-db-compressed-ppds:0/ppd/foomatic-ppd/Xerox-WorkCentre_470cx-lxm5700m.ppd
        natural_language = en
        make-and-model = Xerox WorkCentre 470cx Foomatic/lxm5700m (recommended)
        device-id = DRV:Dlxm5700m,R1,M0,TG;
Model:  name = foomatic-db-compressed-ppds:1/ppd/foomatic-ppd/Xerox-WorkCentre_470cx-lxm5700m.ppd
        natural_language = en
        make-and-model = Xerox WorkCentre 470cx Foomatic/lxm5700m (recommended)
        device-id = MFG:Xerox;MDL:WorkCentre 470cx;
Model:  name = splix:0/ppd/splix/xerox/wc3119.ppd
        natural_language = en
        make-and-model = Xerox WorkCentre 3119, 2.0.0
        device-id = MFG:Xerox;MDL:WorkCentre 3119;
Model:  name = splix:0/ppd/splix/xerox/wc3119fr.ppd
        natural_language = fr
        make-and-model = Xerox WorkCentre 3119, 2.0.0
        device-id = MFG:Xerox;MDL:WorkCentre 3119;
Model:  name = splix:0/ppd/splix/xerox/wc3119pt.ppd
        natural_language = pt_BR
        make-and-model = Xerox WorkCentre 3119, 2.0.0
        device-id = MFG:Xerox;MDL:WorkCentre 3119;
Model:  name = foomatic-db-compressed-ppds:0/ppd/foomatic-ppd/Xerox-WorkCentre_4118-Postscript.ppd
        natural_language = en
        make-and-model = Xerox WorkCentre 4118 Foomatic/Postscript
        device-id = MFG:Xerox;MDL:Xerox WC 4118;DRV:DPostscript,R0,M0,TP;
Model:  name = foomatic-db-compressed-ppds:0/ppd/foomatic-ppd/Xerox-WorkCentre_7228-Postscript.ppd
        natural_language = en
        make-and-model = Xerox WorkCentre 7228 Foomatic/Postscript
        device-id = MANUFACTURER:XEROX;MODEL:WorkCentre 7228;DESCRIPTION:XEROX WorkCentre 7228;DRV:DPostscript,R0,M0,TP;
Model:  name = foomatic-db-compressed-ppds:0/ppd/foomatic-ppd/Xerox-WorkCentre_7232-Postscript.ppd
        natural_language = en
        make-and-model = Xerox WorkCentre 7232 Foomatic/Postscript (recommended)
        device-id = DRV:DPostscript,R1,M0,TP;
Model:  name = foomatic-db-compressed-ppds:1/ppd/foomatic-ppd/Xerox-WorkCentre_7232-Postscript.ppd
        natural_language = en
        make-and-model = Xerox WorkCentre 7232 Foomatic/Postscript (recommended)
        device-id = MFG:Xerox;MDL:WorkCentre 7232;
Model:  name = foomatic-db-compressed-ppds:0/ppd/foomatic-ppd/Xerox-WorkCentre_7242-Postscript.ppd
        natural_language = en
        make-and-model = Xerox WorkCentre 7242 Foomatic/Postscript (recommended)
        device-id = DRV:DPostscript,R1,M0,TP;
Model:  name = foomatic-db-compressed-ppds:1/ppd/foomatic-ppd/Xerox-WorkCentre_7242-Postscript.ppd
        natural_language = en
        make-and-model = Xerox WorkCentre 7242 Foomatic/Postscript (recommended)
        device-id = MFG:Xerox;MDL:WorkCentre 7242;
Model:  name = foomatic-db-compressed-ppds:0/ppd/foomatic-ppd/Xerox-WorkCentre_7328-Postscript.ppd
        natural_language = en
        make-and-model = Xerox WorkCentre 7328 Foomatic/Postscript (recommended)
        device-id = DRV:DPostscript,R1,M0,TP;
Model:  name = foomatic-db-compressed-ppds:1/ppd/foomatic-ppd/Xerox-WorkCentre_7328-Postscript.ppd
        natural_language = en
        make-and-model = Xerox WorkCentre 7328 Foomatic/Postscript (recommended)
        device-id = MFG:Xerox;MDL:WorkCentre 7328;
Model:  name = foomatic-db-compressed-ppds:0/ppd/foomatic-ppd/Xerox-WorkCentre_7335-Postscript.ppd
        natural_language = en
        make-and-model = Xerox WorkCentre 7335 Foomatic/Postscript (recommended)
        device-id = DRV:DPostscript,R1,M0,TP;
Model:  name = foomatic-db-compressed-ppds:1/ppd/foomatic-ppd/Xerox-WorkCentre_7335-Postscript.ppd
        natural_language = en
        make-and-model = Xerox WorkCentre 7335 Foomatic/Postscript (recommended)
        device-id = MFG:Xerox;MDL:WorkCentre 7335;
Model:  name = gutenprint.5.2://xerox-workcentre_7345/expert
        natural_language = en
        make-and-model = Xerox WorkCentre 7345 - CUPS+Gutenprint v5.2.8-pre1
        device-id = 
Model:  name = foomatic-db-compressed-ppds:0/ppd/foomatic-ppd/Xerox-WorkCentre_7345-hpijs-pcl5c.ppd
        natural_language = en
        make-and-model = Xerox WorkCentre 7345 Foomatic/hpijs-pcl5c
        device-id = DRV:Dhpijs-pcl5c,R0,M0,Sv,TI,X600,Y600,C1,t100,l100,g100,p100,s70;
Model:  name = foomatic-db-compressed-ppds:1/ppd/foomatic-ppd/Xerox-WorkCentre_7345-hpijs-pcl5c.ppd
        natural_language = en
        make-and-model = Xerox WorkCentre 7345 Foomatic/hpijs-pcl5c
        device-id = MFG:Xerox;MDL:WorkCentre 7345;
Model:  name = foomatic-db-compressed-ppds:0/ppd/foomatic-ppd/Xerox-WorkCentre_7345-lj4dith.ppd
        natural_language = en
        make-and-model = Xerox WorkCentre 7345 Foomatic/lj4dith
        device-id = DRV:Dlj4dith,R0,M0,TG;
Model:  name = foomatic-db-compressed-ppds:1/ppd/foomatic-ppd/Xerox-WorkCentre_7345-lj4dith.ppd
        natural_language = en
        make-and-model = Xerox WorkCentre 7345 Foomatic/lj4dith
        device-id = MFG:Xerox;MDL:WorkCentre 7345;
Model:  name = foomatic-db-compressed-ppds:0/ppd/foomatic-ppd/Xerox-WorkCentre_7345-ljet4.ppd
        natural_language = en
        make-and-model = Xerox WorkCentre 7345 Foomatic/ljet4
        device-id = DRV:Dljet4,R0,M0,Sv,TG,X600,Y600,C0,t90,l90,g60,p30,s90;
Model:  name = foomatic-db-compressed-ppds:1/ppd/foomatic-ppd/Xerox-WorkCentre_7345-ljet4.ppd
        natural_language = en
        make-and-model = Xerox WorkCentre 7345 Foomatic/ljet4
        device-id = MFG:Xerox;MDL:WorkCentre 7345;
Model:  name = foomatic-db-compressed-ppds:0/ppd/foomatic-ppd/Xerox-WorkCentre_7345-ljet4d.ppd
        natural_language = en
        make-and-model = Xerox WorkCentre 7345 Foomatic/ljet4d
        device-id = DRV:Dljet4d,R0,M0,TG;
Model:  name = foomatic-db-compressed-ppds:1/ppd/foomatic-ppd/Xerox-WorkCentre_7345-ljet4d.ppd
        natural_language = en
        make-and-model = Xerox WorkCentre 7345 Foomatic/ljet4d
        device-id = MFG:Xerox;MDL:WorkCentre 7345;
Model:  name = foomatic-db-compressed-ppds:0/ppd/foomatic-ppd/Xerox-WorkCentre_7345-Postscript.ppd
        natural_language = en
        make-and-model = Xerox WorkCentre 7345 Foomatic/Postscript
        device-id = DRV:DPostscript,R0,M0,TP;
Model:  name = foomatic-db-compressed-ppds:1/ppd/foomatic-ppd/Xerox-WorkCentre_7345-Postscript.ppd
        natural_language = en
        make-and-model = Xerox WorkCentre 7345 Foomatic/Postscript
        device-id = MFG:Xerox;MDL:WorkCentre 7345;
Model:  name = foomatic-db-compressed-ppds:0/ppd/foomatic-ppd/Xerox-WorkCentre_7345-pxlcolor.ppd
        natural_language = en
        make-and-model = Xerox WorkCentre 7345 Foomatic/pxlcolor (recommended)
        device-id = DRV:Dpxlcolor,R1,M0,TG;
Model:  name = foomatic-db-compressed-ppds:1/ppd/foomatic-ppd/Xerox-WorkCentre_7345-pxlcolor.ppd
        natural_language = en
        make-and-model = Xerox WorkCentre 7345 Foomatic/pxlcolor (recommended)
        device-id = MFG:Xerox;MDL:WorkCentre 7345;
Model:  name = foomatic-db-compressed-ppds:0/ppd/foomatic-ppd/Xerox-WorkCentre_C2424-cljet5.ppd
        natural_language = en
        make-and-model = Xerox WorkCentre C2424 Foomatic/cljet5
        device-id = MFG:Xerox;MDL:WorkCentre C2424;CMD:Adobe PostScript 3, PCL;DES:Xerox WorkCentre C2424, Color Printer, PostScript 3, Letter/A4 Size;DRV:Dcljet5,R0,M0,TG;
Model:  name = foomatic-db-compressed-ppds:0/ppd/foomatic-ppd/Xerox-WorkCentre_C2424-hpijs-pcl5c.ppd
        natural_language = en
        make-and-model = Xerox WorkCentre C2424 Foomatic/hpijs-pcl5c
        device-id = MFG:Xerox;MDL:WorkCentre C2424;CMD:Adobe PostScript 3, PCL;DES:Xerox WorkCentre C2424, Color Printer, PostScript 3, Letter/A4 Size;DRV:Dhpijs-pcl5c,R0,M0,Sv,TI,X600,Y600,C1,t100,l100,g100,p100,s70;
Model:  name = foomatic-db-compressed-ppds:0/ppd/foomatic-ppd/Xerox-WorkCentre_C2424-Postscript.ppd
        natural_language = en
        make-and-model = Xerox WorkCentre C2424 Foomatic/Postscript
        device-id = MFG:Xerox;MDL:WorkCentre C2424;CMD:Adobe PostScript 3, PCL;DES:Xerox WorkCentre C2424, Color Printer, PostScript 3, Letter/A4 Size;DRV:DPostscript,R0,M0,TP;
Model:  name = foomatic-db-compressed-ppds:0/ppd/foomatic-ppd/Xerox-WorkCentre_M20-Postscript.ppd
        natural_language = en
        make-and-model = Xerox WorkCentre M20 Foomatic/Postscript
        device-id = MFG:Xerox;MDL:Xerox WC M20;DRV:DPostscript,R0,M0,TP;
Model:  name = foomatic-db-compressed-ppds:0/ppd/foomatic-ppd/Xerox-WorkCentre_M24-Postscript.ppd
        natural_language = en
        make-and-model = Xerox WorkCentre M24 Foomatic/Postscript (recommended)
        device-id = DRV:DPostscript,R1,M0,TP;
Model:  name = foomatic-db-compressed-ppds:1/ppd/foomatic-ppd/Xerox-WorkCentre_M24-Postscript.ppd
        natural_language = en
        make-and-model = Xerox WorkCentre M24 Foomatic/Postscript (recommended)
        device-id = MFG:Xerox;MDL:WorkCentre M24;
Model:  name = gutenprint.5.2://xerox-wc_m118/expert
        natural_language = en
        make-and-model = Xerox WorkCentre M118 - CUPS+Gutenprint v5.2.8-pre1
        device-id = MFG:XEROX;MDL:WorkCentre M118;DES:XEROX WorkCentre M118;
Model:  name = foomatic-db-compressed-ppds:0/ppd/foomatic-ppd/Xerox-WorkCentre_M118-Postscript.ppd
        natural_language = en
        make-and-model = Xerox WorkCentre M118 Foomatic/Postscript
        device-id = MANUFACTURER:XEROX;MODEL:WorkCentre M118;DESCRIPTION:XEROX WorkCentre M118;DRV:DPostscript,R0,M0,TP;
Model:  name = splix:0/ppd/splix/xerox/wcpe16.ppd
        natural_language = en
        make-and-model = Xerox WorkCentre PE16, 2.0.0
        device-id = MFG:Xerox;MDL:WorkCentre PE16;
Model:  name = splix:0/ppd/splix/xerox/wcpe16fr.ppd
        natural_language = fr
        make-and-model = Xerox WorkCentre PE16, 2.0.0
        device-id = MFG:Xerox;MDL:WorkCentre PE16;
Model:  name = splix:0/ppd/splix/xerox/wcpe16pt.ppd
        natural_language = pt_BR
        make-and-model = Xerox WorkCentre PE16, 2.0.0
        device-id = MFG:Xerox;MDL:WorkCentre PE16;
Model:  name = splix:0/ppd/splix/xerox/wcpe114e.ppd
        natural_language = en
        make-and-model = Xerox WorkCentre PE114e, 2.0.0
        device-id = MFG:Xerox;MDL:WorkCentre PE114e;
Model:  name = splix:0/ppd/splix/xerox/wcpe114efr.ppd
        natural_language = fr
        make-and-model = Xerox WorkCentre PE114e, 2.0.0
        device-id = MFG:Xerox;MDL:WorkCentre PE114e;
Model:  name = splix:0/ppd/splix/xerox/wcpe114ept.ppd
        natural_language = pt_BR
        make-and-model = Xerox WorkCentre PE114e, 2.0.0
        device-id = MFG:Xerox;MDL:WorkCentre PE114e;
Model:  name = foomatic-db-compressed-ppds:0/ppd/foomatic-ppd/Xerox-WorkCentre_PE120-Postscript.ppd
        natural_language = en
        make-and-model = Xerox WorkCentre PE120 Foomatic/Postscript
        device-id = MFG:Xerox;MDL:Xerox WC PE120;DRV:DPostscript,R0,M0,TP;
Model:  name = foomatic-db-compressed-ppds:0/ppd/foomatic-ppd/Xerox-WorkCentre_PE120-pxlmono.ppd
        natural_language = en
        make-and-model = Xerox WorkCentre PE120 Foomatic/pxlmono
        device-id = MFG:Xerox;MDL:Xerox WC PE120;DRV:Dpxlmono,R0,M0,TG;
Model:  name = foomatic-db-compressed-ppds:0/ppd/foomatic-ppd/Xerox-WorkCentre_Pro_128-Postscript.ppd
        natural_language = en
        make-and-model = Xerox WorkCentre Pro 128 Foomatic/Postscript
        device-id = MANUFACTURER:XEROX;MODEL:WorkCentre Pro 128;DESCRIPTION:XEROX WorkCentre Pro 128;DRV:DPostscript,R0,M0,TP;
Model:  name = foomatic-db-compressed-ppds:0/ppd/foomatic-ppd/Xerox-WorkCentre_Pro_133-Postscript.ppd
        natural_language = en
        make-and-model = Xerox WorkCentre Pro 133 Foomatic/Postscript
        device-id = MANUFACTURER:XEROX;MODEL:WorkCentre Pro 133;DESCRIPTION:XEROX WorkCentre Pro 133;DRV:DPostscript,R0,M0,TP;
Model:  name = foomatic-db-compressed-ppds:0/ppd/foomatic-ppd/Xerox-WorkCentre_XK35c-lex5700.ppd
        natural_language = en
        make-and-model = Xerox WorkCentre XK35c Foomatic/lex5700 (recommended)
        device-id = DRV:Dlex5700,R1,M0,TG;
Model:  name = foomatic-db-compressed-ppds:1/ppd/foomatic-ppd/Xerox-WorkCentre_XK35c-lex5700.ppd
        natural_language = en
        make-and-model = Xerox WorkCentre XK35c Foomatic/lex5700 (recommended)
        device-id = MFG:Xerox;MDL:WorkCentre XK35c;
Model:  name = drv:///sample.drv/zebracpl.ppd
        natural_language = en
        make-and-model = Zebra CPCL Label Printer
        device-id = 
Model:  name = drv:///sample.drv/zebraep1.ppd
        natural_language = en
        make-and-model = Zebra EPL1 Label Printer
        device-id = 
Model:  name = drv:///sample.drv/zebraep2.ppd
        natural_language = en
        make-and-model = Zebra EPL2 Label Printer
        device-id = 
Model:  name = drv:///sample.drv/zebra.ppd
        natural_language = en
        make-and-model = Zebra ZPL Label Printer
        device-id = 

```
[http://localhost:631/printers/](http://localhost:631/printers/)
Canon-LBP-660	Canon LBP-660	carla-desktop	Canon LBP-660 Foomatic/lbp660 (recommended)	Idle
LBP-660	LBP-660		Canon LBP-660 Foomatic/lbp660 (recommended)	Idle
LBP-660-2	Canon LBP-660	carla-desktop	Canon LBP-660 Foomatic/lbp660 (recommended)	Idle

---

### Post by pdc on 2013-02-11
mate: treat yourself; you deserve this

[http://dicksmith.com.au/product/XP9213/brother-hl2130-mono-laser-printer](http://dicksmith.com.au/product/XP9213/brother-hl2130-mono-laser-printer)

a Brother laser printer: $A44 .............. a bargain......

......it will work out of the box...... using the Brother drivers....

.........go on ......treat yourself..........you know you deserve it..

---

### Post by rapattack1 on 2013-02-11
Ha ha i know but thats a lot if your not working. Its cool coz i scored another laser and the compatible cartridges online are $17aud so might be better to let go. Oh and a friend today has an older computer with winxp so it might work with that. :P

---

### Post by schragge on 2013-02-11
Hmm, it seems to me like CUPS still tries to use the driver for LBP-470?
Please post the output of
```

ls /etc/cups/ppd
cat /etc/cups/printers.conf

```

---

### Post by rapattack1 on 2013-02-11
Ahhhhh
```
$ ls /etc/cups/ppd
Canon-LBP-660.ppd  LBP-660-2.ppd  LBP-660.ppd
carla@carla-desktop:~$ cat /etc/cups/printers.conf
cat: /etc/cups/printers.conf: Permission denied

```

---

### Post by schragge on 2013-02-11
Oh, then try
```

sudo cat /etc/cups/printers.conf

```

---

### Post by rapattack1 on 2013-02-11
```
$ sudo cat /etc/cups/printers.conf
[sudo] password for carla: 
# Printer configuration file for CUPS v1.5.3
# Written by cupsd
# DO NOT EDIT THIS FILE WHEN CUPSD IS RUNNING
<DefaultPrinter Canon-LBP-660>
UUID urn:uuid:64454b90-6264-369b-6da9-fe7c67172a75
Info Canon LBP-660
Location carla-desktop
MakeModel Canon LBP-660 Foomatic/lbp660 (recommended)
DeviceURI parallel:/dev/lp0
State Idle
StateTime 1360509820
Type 8392708
Accepting Yes
Shared Yes
JobSheets none none
QuotaPeriod 0
PageLimit 0
KLimit 0
OpPolicy default
ErrorPolicy retry-job
</Printer>
<Printer LBP-660>
UUID urn:uuid:583079c9-760a-3f98-7d2a-48272a4068ac
Info LBP-660
MakeModel Canon LBP-660 Foomatic/lbp660 (recommended)
DeviceURI parallel:/dev/lp0
State Idle
StateTime 1360510940
Type 8392708
Accepting Yes
Shared Yes
JobSheets none none
QuotaPeriod 0
PageLimit 0
KLimit 0
OpPolicy default
ErrorPolicy retry-job
</Printer>
<Printer LBP-660-2>
UUID urn:uuid:c28b0251-ebeb-3379-4ba2-7a0e118ddfd9
Info Canon LBP-660
Location carla-desktop
MakeModel Canon LBP-660 Foomatic/lbp660 (recommended)
DeviceURI usb://Canon/LBP-660
State Idle
StateTime 1360573895
Type 8392708
Accepting Yes
Shared Yes
JobSheets none none
QuotaPeriod 0
PageLimit 0
KLimit 0
OpPolicy default
ErrorPolicy retry-job
</Printer>

```

---

### Post by schragge on 2013-02-11
Sorry, I'm afraid I can't help here:(. The only hint I've got left for you is these lines in the output of 'dmesg|grep parport'
```

[ 3134.599026] parport0: lp tried to release parport when not owner
[ 9469.475064] parport0: lp already owner

```
I don't know what it really means, but suspect that these messages shouldn't be there. Looks like some program (colord? libsane-hpaio?) grabs /dev/parport0 and doesn't allow printer to use it.

---

### Post by rapattack1 on 2013-02-11
Oh thats ok I will 'bite the bullet' and buy a cartridge for the other laser printer that is more modern and was working with this machine til it ran out of toner...thanks you have made a mammoth effort :0)

---

