---
title: "[SOLVED] space problem"
date: 2008-07-14
forum: General Help
---

### Post by mosty friedman on 2008-07-14
hey everyone,
i'm new with ubuntu and i have this problem with it that i cant figure out...sometimes when i try to open an application, it gives me this error about not having enough space..although i barely install stuff on it..is ubuntu somehow eating up space memory..how do i solve this??..

---

### Post by roel46 on 2008-07-14
hoi mosty friedman,

could you give us (an example of) an application that is complaining and the error message it gives?

groeten, roel.

---

### Post by mosty friedman on 2008-07-14
well it happened with kpdf and eclipse..actually my ubuntu gets crazy sometimes like for instance sometimes when i click on the logoff icon to logoff,restart,shutdown etc..the window doesnt show up and the toolbars disappear but the dektop n the icons keep showing..also sometimes when i click on places in the toolbar it wont show documents,music,pictures,videos folders but it shows the rest....i have to restart my system a few times to get it to work normal again and it drives me crazy..so if anyone can suggest a solution i would appreciate it.

---

### Post by mosty friedman on 2008-07-15
it gives me these errors 
cant write to file decriptor 9(error 28:No space left on device)
cant write user configuration file

---

### Post by hyper_ch on 2008-07-15
```

df -l

```

what's the output?

And use [noparse]```

```[/noparse] brackets around it.

---

### Post by mosty friedman on 2008-07-15
this is the output
Filesystem           1K-blocks      Used Available Use% Mounted on
/host/ubuntu/disks/root.disk
                      13563852  12880256         4 100% /
varrun                  512860       104    512756   1% /var/run
varlock                 512860         0    512860   0% /var/lock
udev                    512860        44    512816   1% /dev
devshm                  512860         0    512860   0% /dev/shm
lrm                     512860     39760    473100   8% /lib/modules/2.6.24-19-generic/volatile
overflow                  1024        36       988   4% /tmp
gvfs-fuse-daemon      13563852  12880256         4 100% /home/lg/.gvfs

---

### Post by mosty friedman on 2008-07-15
damn i messed it up

---

### Post by mosty friedman on 2008-07-15
what do u mean, use code brackets

---

### Post by plucky on 2008-07-15
> **mosty friedman said:**
> what do u mean, use code brackets

See the BB code List in my Signature

> /host/ubuntu/disks/root.disk
13563852 12880256 4 100% /

Could that be your problem?

---

### Post by mosty friedman on 2008-07-15
man, i'm new to this thing and i have no idea what u just

---

### Post by hyper_ch on 2008-07-15
well, what does that piece mean that he quoted (and not coded)?

You can try to understand that.

and when posting output from commands or config files use [noparse]```

```[/noparse] tags around it (and not [noparse]> [/noparse] tag [for multiple reasons])

---

### Post by plucky on 2008-07-15
> **mosty friedman said:**
> man, i'm new to this thing and i have no idea what u just

I think your root partition is at 100% i.e full.You need to clear out some space.A good one is ```
sudo apt-get clean
``` will delete all your archive downloaded files from the repositories.

Find whatever is causing your root partition to fill up and stop it e.g a backup.

Also clearing out your Trash might help.


BB code list is a list of tags you can use in the forums for formatting your questions and replies.Using ```
 tags causes the words in between the tags to be put into a window e.g [code]hello mosty
```

Good Luck

---

### Post by mosty friedman on 2008-07-15
```
Filesystem           1K-blocks      Used Available Use% Mounted on
/host/ubuntu/disks/root.disk
                      13563852  12485332    394928  97% /
varrun                  512860       104    512756   1% /var/run
varlock                 512860         0    512860   0% /var/lock
udev                    512860        44    512816   1% /dev
devshm                  512860         0    512860   0% /dev/shm
lrm                     512860     39760    473100   8% /lib/modules/2.6.24-19-generic/volatile
overflow                  1024        36       988   4% /tmp
gvfs-fuse-daemon      13563852  12485332    394928  97% /home/lg/.gvfs
/dev/sda1              1048572    573560    475012  55% /media/RECOVERY

```
it gave me this output when i typed df -l

---

### Post by mosty friedman on 2008-07-15
the sudo apt-get clean command solved the problem...but i just wanna know what caused it

---

### Post by plucky on 2008-07-15
> **mosty friedman said:**
> the sudo apt-get clean command solved the problem...but i just wanna know what caused it

You need to find what is taking up your space ```
sudo find / -type f -size +100000k
``` will display any large files on your system.See what is taking up your space.If that doesn't show anything,reduce the 100000k to 50000k and try again.

Good Luck

---

### Post by mosty friedman on 2008-07-15
thanks a lot man...one thing tough..is there any source to teach me the ubuntu commands and how to solve these common problems?? u guys seems to know a lot about ubuntu

---

### Post by fyo on 2008-07-15
> **mosty friedman said:**
> thanks a lot man...one thing tough..is there any source to teach me the ubuntu commands and how to solve these common problems?? u guys seems to know a lot about ubuntu

The command line interface (CLI) is invaluable, but can be daunting for newcomers to Linux (at least those who didn't use the command line in Windows). Here is a good introduction:

[http://www.tuxfiles.org/linuxhelp/cli.html](http://www.tuxfiles.org/linuxhelp/cli.html)

There are many other tutorials out there (just search for "introduction to linux cli" or similar), but there's a nice, short list of some must-know commands here:

[http://www.physics.ubc.ca/mbelab/computer/linux-intro/html/basics.html#essential-commands](http://www.physics.ubc.ca/mbelab/computer/linux-intro/html/basics.html#essential-commands)

I would add "df" to that list, though.

Almost all commands have a so-called "man page" (manual). Just type "man" followed by the command you wish to know about (e.g. "man df"). This will typically give you, among other things, a list of options for the command.

A couple of other random nice-to-know things:

When in the CLI and you press CTRL-R, you can recall previous commands. So, for example, if I know I typed a command in once that included "unrar", I could just press CTRL-R and start typing "unrar". It would show me the last command I issued that contained "unrar" (doesn't have to be in the beginning of the command... if I remembered a filename I used it on, that would work as well). To go further back in history (step back) using the same query, just press CTRL-R again.

"ls -la" lists ALL files in the directory.

The "-h" option is very useful for many things, including "ls" and "df". It returns the "sizes" in "human readable form". That means you get megabytes and gigabytes if the file sizes are "large", instead of everything in bytes or kilobytes (default for most things is "1K blocks", i.e. kilobytes).

"find" and "locate" can be used to locate files. The former is more powerful, but also harder to use for most people. The latter requires updatedb to be run every once in a while (may be automatic every day, it was on my Ubuntu install, but it was an upgrade of an upgrade, so I don't know what the default is for a clean Ubuntu 8.04 install).

EDIT: Just FYI, these commands are not specific to Ubuntu. They are pretty much the same across all flavors of Linux, as well as Unix and BSD (and derived systems, like Apple's OSX).

---

### Post by roel46 on 2008-07-17
hoi mosty friedman,

have a look at the tool "Disk Usage Analizer" (via Applications > Accessories). It is very useful whenever disk space problems arise.

groeten, roel.

---

