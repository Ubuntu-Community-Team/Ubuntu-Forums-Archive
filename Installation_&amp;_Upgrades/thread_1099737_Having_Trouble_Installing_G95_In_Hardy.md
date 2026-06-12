---
title: "Having Trouble Installing G95 In Hardy"
date: 2009-03-18
forum: Installation &amp; Upgrades
---

### Post by rusty spork on 2009-03-18
I am running Hardy Heron and I am trying to install the g95 compiler.  I found this [guide]("http://ubuntuforums.org/showthread.php?t=157488") to help me out after I started having problems.  After creating the symbolic link (in sudo) I tried compiling a basic program that writes a one line statement to see if it worked:

jpm@joe-tablet:~/Desktop$ g95 test.f90
bash: g95: command not found


/home/jpm

-is where my g95-install folder is located

/usr/local/bin

-is where the symbolic link is located


What do I need to do to get g95 working properly? Thanks.

---

### Post by taurus on 2009-03-18
Did you actually link to the compiler or just the directory that you installed g95?  Post the outputs of these two commands.

```
ls -la ~
ls -la /usr/local/bin
```

---

### Post by rusty spork on 2009-03-18
First command:

[HTML]jpm@joe-tablet:~$ ls -la ~
total 8124
drwxr-xr-x 40 jpm  jpm     4096 2009-03-18 12:34 .
drwxr-xr-x  4 root root    4096 2009-02-03 09:26 ..
drwx------  3 jpm  jpm     4096 2009-02-04 07:37 .adobe
-rw-------  1 jpm  jpm     7034 2009-03-18 13:05 .bash_history
-rw-r--r--  1 jpm  jpm      220 2009-02-03 09:26 .bash_logout
-rw-r--r--  1 jpm  jpm     3115 2009-02-03 09:26 .bashrc
drwxr-xr-x  5 jpm  jpm     4096 2009-02-17 20:26 .cache
drwx------  3 jpm  jpm     4096 2009-02-03 18:46 .compiz
drwxr-xr-x  7 jpm  jpm     4096 2009-03-18 12:22 .config
drwx------  3 jpm  jpm     4096 2009-02-03 09:26 .dbus
-rw-r--r--  1 jpm  jpm       57 2009-02-17 19:00 .DCOPserver_joe-tablet__0
lrwxrwxrwx  1 jpm  jpm       35 2009-02-17 18:44 .DCOPserver_joe-tablet_:0 -> /home/jpm/.DCOPserver_joe-tablet__0
drwxr-xr-x  3 jpm  jpm     4096 2009-03-18 12:57 Desktop
-rw-------  1 jpm  jpm       28 2009-03-18 12:21 .dmrc
drwxr-xr-x  2 jpm  jpm     4096 2009-02-03 09:26 Documents
-rw-------  1 jpm  jpm       16 2009-02-03 09:26 .esd_auth
drwxr-xr-x  3 jpm  jpm     4096 2009-02-17 20:20 .evolution
lrwxrwxrwx  1 jpm  jpm       26 2009-02-03 09:26 Examples -> /usr/share/example-content
-rwxr-xr-x  1 jpm  jpm     1710 2008-10-15 18:45 flash10_en.sh
-rw-r--r--  1 jpm  jpm     1710 2008-10-15 18:45 flash10_en.sh.1
drwxr-xr-x  2 jpm  jpm     4096 2009-02-05 18:00 .fontconfig
drwxr-xr-x  4 jpm  jpm     4096 2009-03-15 01:40 g95-install
drwx------  5 jpm  jpm     4096 2009-03-18 12:47 .gconf
drwx------  2 jpm  jpm     4096 2009-03-18 13:05 .gconfd
-rw-r--r--  1 root root    6498 2008-03-01 21:35 getlibs-all.deb
-rw-r--r--  1 root root    6498 2008-03-01 21:35 getlibs-all.deb.1
-rw-r-----  1 jpm  jpm        0 2009-03-17 15:09 .gksu.lock
drwx------ 12 jpm  jpm     4096 2009-03-18 12:34 .gnome2
drwx------  2 jpm  jpm     4096 2009-02-03 09:26 .gnome2_private
drwx------  2 jpm  jpm     4096 2009-02-17 18:46 .gnupg
-rw-r--r--  1 jpm  jpm       10 2009-03-15 21:43 .gshutdown
drwxr-xr-x  2 jpm  jpm     4096 2009-02-03 09:26 .gstreamer-0.10
-rw-r--r--  1 jpm  jpm      100 2009-03-18 12:24 .gtk-bookmarks
dr-x------  2 jpm  jpm        0 2009-03-18 12:22 .gvfs
-rw-------  1 jpm  jpm     5466 2009-03-18 12:22 .ICEauthority
drwxr-xr-x  2 jpm  jpm     4096 2009-02-03 13:45 .icons
-rw-r--r--  1 root root 3962157 2008-12-01 18:04 install_flash_player_10_linux.tar.gz
-rw-r--r--  1 root root 3994294 2009-02-17 15:46 install_flash_player_10_linux.tar.gz.1
drwx------  3 jpm  jpm     4096 2009-02-03 14:31 .kde
drwx------  3 jpm  jpm     4096 2009-02-03 09:26 .local
drwx------  3 jpm  jpm     4096 2009-02-04 07:37 .macromedia
drwxr-xr-x  3 jpm  jpm     4096 2009-02-03 14:37 .mcop
-rw-------  1 jpm  jpm       31 2009-02-17 19:00 .mcoprc
drwx------  4 jpm  jpm     4096 2009-02-03 09:32 .mozilla
drwxr-xr-x  2 jpm  jpm     4096 2009-02-03 09:26 Music
drwxr-xr-x  3 jpm  jpm     4096 2009-03-17 17:25 .nautilus
-rw-r--r--  1 jpm  jpm     1054 2009-02-17 18:51 .nvidia-settings-rc
drwx------  3 jpm  jpm     4096 2009-03-15 22:14 .openoffice.org2
-rw-r--r--  1 jpm  jpm    31651 2009-03-15 21:51 output.pdf
drwxr-xr-x  2 jpm  jpm     4096 2009-02-03 09:26 Pictures
-rw-r--r--  1 jpm  jpm      675 2009-02-03 09:26 .profile
drwxr-xr-x  2 jpm  jpm     4096 2009-03-17 17:24 programs
drwxr-xr-x  2 jpm  jpm     4096 2009-02-03 09:26 Public
drwxr-xr-x  2 jpm  jpm     4096 2009-02-26 09:54 .pulse
-rw-------  1 jpm  jpm      256 2009-02-03 09:26 .pulse-cookie
drwxr-xr-x  2 jpm  jpm     4096 2009-02-03 14:35 .qt
-rw-------  1 jpm  jpm     4234 2009-03-15 21:24 .recently-used
-rw-------  1 jpm  jpm    21372 2009-03-18 12:34 .recently-used.xbel
-rw-r--r--  1 jpm  jpm        0 2009-02-12 08:06 Resize
drwx------  2 jpm  jpm     4096 2009-02-03 09:27 .ssh
-rw-r--r--  1 jpm  jpm        0 2009-02-03 09:35 .sudo_as_admin_successful
drwxr-xr-x  2 jpm  jpm     4096 2009-02-03 09:26 Templates
drwxr-xr-x  2 jpm  jpm     4096 2009-02-03 13:45 .themes
drwx------  4 jpm  jpm     4096 2009-02-03 18:46 .thumbnails
drwxr-xr-x  2 jpm  jpm     4096 2009-02-12 08:26 .update-manager-core
drwx------  2 jpm  jpm     4096 2009-02-03 09:27 .update-notifier
drwxr-xr-x  2 jpm  jpm     4096 2009-02-03 09:26 Videos
-rw-------  1 jpm  jpm      121 2009-03-18 12:21 .Xauthority
-rw-r--r--  1 jpm  jpm    31275 2009-03-18 13:01 .xsession-errors
[/HTML]



Second command:


[HTML]jpm@joe-tablet:~$ ls -la /usr/local/bin
total 8
drwxr-xr-x  2 root root 4096 2009-03-18 12:47 .
drwxr-xr-x 10 root root 4096 2008-10-29 16:04 ..
lrwxrwxrwx  1 root root   26 2009-03-18 12:47 i686-unknown-linux-gnu-g95 -> i686-unknown-linux-gnu-g95[/HTML]

---

### Post by taurus on 2009-03-18
What about

```
ls -la ~/g95-install
```
Is there a bin directory?

```
ls -la ~/g95-install/bin
```

By the way, /usr/local/bin/i686-unknown-linux-gnu-g95 is basically pointing to itself!

---

### Post by rusty spork on 2009-03-18
#1

[HTML]jpm@joe-tablet:~$ ls -la ~/g95-install
total 160
drwxr-xr-x  4 jpm jpm   4096 2009-03-15 01:40 .
drwxr-xr-x 40 jpm jpm   4096 2009-03-18 12:34 ..
drwxr-xr-x  2 jpm jpm   4096 2009-03-15 01:40 bin
-rw-r--r--  1 jpm jpm 138126 2009-03-15 01:40 G95Manual.pdf
-rw-r--r--  1 jpm jpm    521 2009-03-15 01:40 INSTALL
drwxr-xr-x  3 jpm jpm   4096 2009-03-15 01:40 lib
[/HTML]


#2

[HTML]jpm@joe-tablet:~$ ls -la ~/g95-install/bin
total 208
drwxr-xr-x 2 jpm jpm   4096 2009-03-15 01:40 .
drwxr-xr-x 4 jpm jpm   4096 2009-03-15 01:40 ..
-rwxr-xr-x 1 jpm jpm 199698 2009-03-15 01:40 i686-unknown-linux-gnu-g95
[/HTML]

---

### Post by taurus on 2009-03-18
1.  Remove the broken link in /usr/local/bin.

```
sudo rm /usr/local/bin/i686-unknown-linux-gnu-g95
```

2.  Now try to link it again.

```

sudo ln -s /home/jpm/g95-install/bin/i686-unknown-linux-gnu-g95 /usr/local/bin
ls -la /usr/local/bin
```

---

### Post by rusty spork on 2009-03-18
I removed the broken link, linked it again, and I still got the same result I received when I tried it the first time:


[HTML]
jpm@joe-tablet:~/Desktop$ g95 test.f90
bash: g95: command not found[/HTML]

---

### Post by taurus on 2009-03-18
Do you have to use the whole name, i686-unknown-linux-gnu-g95?

```
i686-unknown-linux-gnu-g95 test.f90
```

---

### Post by rusty spork on 2009-03-18
jpm@joe-tablet:~/Desktop$ i686-unknown-linux-gnu-g95 test.f90
/tmp/ccCkOoYI.s: Assembler messages:
/tmp/ccCkOoYI.s:11: Error: suffix or operands invalid for `push'



It appears that is what I was doing wrong.  Although, I did come up with an error...

---

### Post by taurus on 2009-03-18
If you don't feel like typing out the long name when you want to use g95, you can do something about it.  

First, remove the current link in /usr/local/bin.

```
sudo rm /usr/local/bin/i686-unknown-linux-gnu-g95
```
Now, re link it but with g95 name instead.

```
sudo ln -s /home/jpm/g95-install/bin/i686-unknown-linux-gnu-g95 /usr/local/bin/g95
ls -la /usr/local/bin/g95
```
Do you see g95 from the output above?

---

### Post by rusty spork on 2009-03-18
Yeah, its working now, thank you a lot for all of your help.  I usually use the schools compiler (through a server) to compile programs.  However, I will be going on a trip and I most likely will not have internet access, so no connection to the schools sever...

---

### Post by rusty spork on 2009-03-18
I still seem to be getting that error, although I did some looking into it and it seems it might be an issue with me running 64 bit.

---

