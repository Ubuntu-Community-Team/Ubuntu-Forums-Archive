---
title: "Sudo problems with KDE PLEASE HELP!!"
date: 2008-10-23
forum: General Help
---

### Post by Moonfrost on 2008-10-23
All of a sudden without me doing absolutely anything now every time I want to start something using "sudo" or "kdesudo" I get this (there's an example of kate here):

```
moonfrost@moonfrost-desktop:~$ sudo kate
sudo: must be setuid root

```

So I type setuid to know what it is (I suppose it's some other kind of super user?) and it tells me that setuid is not installed and says that if I want to install it I have to type "sudo apt-get install super", so I typed that and this comes out again:

```
moonfrost@moonfrost-desktop:~$ sudo apt-get install super
sudo: must be setuid root

```

Because of this when I try to start Adept from the K menu nothing happens now (I've used adept a while ago before this and everything worked no problem and I didn't change any settings), if I type "adept" on terminal/konsole it opens but it tells me it's on view mode (or something like that) which usually means there's another instance of the program running.

I checked system monitor and there's no other instance of adept running, so I type "sudo adept" and it again tells me that I need to be setuid...does anybody know how could this have happened? as far as I know I didn't change any permission or anything. The only thing I have done regarding permissions is taking own (take own) of a directory but that was way before I used adept a couple of times without any problems at all and the directory doesn't have anything to do with root or such.

EDIT: It seems I chowned the /usr/ directory because I read on another topic in this forum and that happened to someone who chown the /usr/ directory and after a few commands using the Live CD it was fixed, I'll see if I can fix it...I wonder why the problem wasn't instant? I did that hours ago and I was able to use sudo up to probably 10 minutes ago...weird.

---

### Post by Pro-reason on 2008-10-23
In any case, you ought to use “kdesudo” with graphical apps such as Kate.

Reserve “sudo” for terminal commands.

---

### Post by Moonfrost on 2008-10-23
> **Pro-reason said:**
> In any case, you ought to use “kdesudo” with graphical apps such as Kate.

Reserve “sudo” for terminal commands.

The same thing happens, I also managed to give the usr directory back to root...but that didn't fix it, I wouldn't be having these problems if it wasn't for the root account being disabled by default and that I can't even ask that around here anymore...

---

### Post by Pro-reason on 2008-10-23
No, Ubuntu's sudo policy is not at fault.  You chowning the /usr directory is the source of the problem.

Are you sure that you managed to revert what you did?  Do this:

```

ls -lh /usr 
ls -lh /usr/bin | grep sudo

```

Paste the output here.

---

### Post by Moonfrost on 2008-10-23
> **Pro-reason said:**
> No, Ubuntu's sudo policy is not at fault.  You chowning the /usr directory is the source of the problem.

Are you sure that you managed to revert what you did?  Do this:

```

ls -lh /usr 
ls -lh /usr/bin | grep sudo

```

Paste the output here.

The first one gives me this...don't know what it means:

```
total 180K
drwxr-xr-x   2 root root  36K 2008-10-23 16:30 bin
drwxr-xr-x   2 root root 4.0K 2008-10-23 16:30 games
drwxr-xr-x  49 root root 4.0K 2008-10-23 15:32 include
drwxr-xr-x 121 root root  68K 2008-10-23 15:32 lib
drwxr-xr-x  34 root root  36K 2008-10-22 15:07 lib32
lrwxrwxrwx   1 root root    3 2008-10-21 14:04 lib64 -> lib
drwxr-xr-x  10 root root 4.0K 2008-07-01 20:21 local
drwxr-xr-x   2 root root  12K 2008-10-22 15:19 sbin
drwxr-xr-x 193 root root 4.0K 2008-10-23 15:32 share
drwxrwsr-x   5 root src  4.0K 2008-10-22 15:19 src
drwxr-xr-x   3 root root 4.0K 2008-10-22 15:00 X11R6
```

The second one gives me this:

```
-rwxr-xr-x 1 root root       92K 2008-09-26 05:19 kdesudo
-rwxr-xr-x 2 root root      128K 2008-09-01 09:17 sudo
-rwxr-xr-x 2 root root      128K 2008-09-01 09:17 sudoedit
```

When I right-click on the /usr/ folder it says it's owned by root now (it used to say it was owned by me, moonfrost) and the only reason why I took own of /usr/ was because I was tired of always having problems when I wanted to put a file (such as a rom on a rom directory for an emulator) on a program directory (it NOT being a critical system file or anything), I had to do this every time while on normal Ubuntu I just went and enabled the root account and login easily and just allowed the main user to be able to write to those specific folders and I didn't have any problems anymore, for me it seems (at least in my case) more secure to use the root account than to use the terminal on which I can make mistakes all the time, many times being critical mistakes such as this one.

EDIT: If it matters at all, I'm using Kubuntu 8.10 Intrepid Ibex release candidate with KDE 4.1.2

---

### Post by Pro-reason on 2008-10-23
The choice isn't between logging on as root and using the terminal.  They are two completely separate issues.

If you wish to do something graphically as root, do not start a KDE session as root.  Start it as a normal user, and then open your graphical apps with kdesudo.  You can do this from Konsole or Alt-F2.  For example:

```

kdesudo dolphin

```

The permissions on /usr/bin/sudo look fine.  I don't know what else went wrong.

---

### Post by Moonfrost on 2008-10-23
> **Pro-reason said:**
> The choice isn't between logging on as root and using the terminal.  They are two completely separate issues.

If you wish to do something graphically as root, do not start a KDE session as root.  Start it as a normal user, and then open your graphical apps with kdesudo.  You can do this from Konsole or Alt-F2.  For example:

```

kdesudo dolphin

```

The permissions on /usr/bin/sudo look fine.  I don't know what else went wrong.

Hmmm...well, I still can't run adept at all and I can't use sudo OR kdesudo, the same error I mentioned before comes up always, oh well...I'll probably have to re-install, thanks for the help anyway.

---

