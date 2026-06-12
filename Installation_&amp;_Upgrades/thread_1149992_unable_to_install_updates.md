---
title: "unable to install updates"
date: 2009-05-05
forum: Installation &amp; Upgrades
---

### Post by captainkelly54 on 2009-05-05
Hi, I am relatively new to ubuntu, and I cannot install any updates.  Any time i try to install updates, I get this message:

'E: problem parsing dependency Depends, E:Error occurred while processing calamaris (NewVersion1), E: problem with MergeList /var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_jaunty_universe_bi nary-i386_Packages, E:The package lists or status file could not be parsed or opened.'

This is very annoying, because I cannot install anything, no flash, no screenlets. Nothing. Also, the computer randomly crashes!

Any help would be greatly appreciated

---

### Post by Partyboi2 on 2009-05-06
Hi, open a terminal and rm the file
```
sudo rm /var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_jaunty_universe_binary-i386_Packages
```
then recreate the file.
```
sudo apt-get update 
```

---

### Post by captainkelly54 on 2009-05-06
Hi, after entering those in to the terminal, and it working for a couple minutes. I get this error:

[FONT=monospace]Reading package lists... Error!
E: Problem parsing dependency Suggests
E: Error occurred while processing libplexus-comPonent-api-java (NewVersion1)
E: Problem with MergeList /var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_jaunty_universe_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.
[/FONT]
I'm about to loose hope on ubuntu...

Any help is greatly appreciated!!

Kelly

---

### Post by EXCiD3 on 2009-05-06
Just follow PartyBoi2's instructions again, but this time change the first line to:
```
sudo rm [FONT=Courier New]/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_jaunty_universe_binary-i386_Packages[/FONT]
```
 
and then run apt-get update again. It seems that you are just getting corrupted files. You might also want to switch your mirror to somewhere else in System->Administration->Software Sources. That might be what is causing the problem for you or an unstable internet connection.

---

### Post by captainkelly54 on 2009-05-06
Still getting errors, in each error message it says 

 'Depends' field, syntax error after reference to package 'libglib2.0-0'
E: Sub-process /usr/bin/dpkg returned an error code (2)
dpkg: parse error, in file '/var/lib/dpkg/available' near line 28803 package 'evolution-indicator':
"'Depends' field, syntax error after reference to package 'libglib2.0-0'"

(i had to type all that out myself)

When you say switch your mirror, specify what I have to do lol.

Thanks,
Kelly

---

### Post by Partyboi2 on 2009-05-06
There seems to be a problem with your /var/lib/dpkg/available file. Open a terminal and type or paste
```
sudo dpkg --clear-avail && sudo apt-get update
```This will clear the available file.

---

### Post by captainkelly54 on 2009-05-06
Alright, that installed all the updates, but now I can't open Add/Remove, Synaptic package manager, or the update manager. The window comes up, then immediately closes.

Thanks a lot for your time,
Kelly

---

### Post by Partyboi2 on 2009-05-06
Try starting Synaptic from a terminal to see if any other information is provided to what is happening
```
gksu synaptic
```

---

### Post by captainkelly54 on 2009-05-06
It's doing the same thing, opening then immediately closing. No error messages or anything

---

### Post by Partyboi2 on 2009-05-06
What is the output from the terminal for
```
 gksu update-manager
```

---

### Post by captainkelly54 on 2009-05-07
Nothing, just opens quick and closes.

This is what I put in, and as you can see...no results
kelly@Dunn-computer:~$ gksu update-manager
kelly@Dunn-computer:~$

---

### Post by Partyboi2 on 2009-05-07
Can you check to see if update-manager is installed. 
```
apt-cache policy update-manager
```

---

### Post by captainkelly54 on 2009-05-07
the result is:

kelly@Dunn-computer:~$ apt-cache policy update-manager
update-manager:
  Installed: 1:0.111.9
  Candidate: 1:0.111.9
  Version table:
 *** 1:0.111.9 0
        500 [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates/main Packages
        100 /var/lib/dpkg/status
     1:0.111.7 0
        500 [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/main Packages

---

### Post by captainkelly54 on 2009-05-07
FIXED everything is working fine. After sitting at my computer for the last week trying to get this fixed, it worked. Thank you so so soooooo much.
Haha no more crashes, and youtube and other sites work again.

Thanks again,
Kelly

---

### Post by Partyboi2 on 2009-05-08
> **captainkelly54 said:**
> FIXED everything is working fine. After sitting at my computer for the last week trying to get this fixed, it worked. Thank you so so soooooo much.
Haha no more crashes, and youtube and other sites work again.

Thanks again,
Kelly
May I ask how you fixed it?

---

### Post by captainkelly54 on 2009-05-08
[FONT=System]I have absolutely no idea haha.  After I entered[/FONT]
apt-cache policy update-manager[FONT=System]
[/FONT][FONT=System]it randomly started working. But whatever happened, it worked. So thanks a lot!![/FONT]
[FONT=monospace][/FONT]

---

### Post by captainkelly54 on 2009-05-11
Hey, back again..i cant install anything again. Now whenever I try to install anything i get this:

Errors were encountered while processing:
 sun-java6-fonts
 ttf-dejavu-extra
 ttf-dejavu
E: Sub-process /usr/bin/dpkg returned an error code (1)

What I am trying to do is install Sane, so i can use my hp psc 1200 series printer.

Any ideas what to do?

---

### Post by Partyboi2 on 2009-05-11
What is the output to
```
sudo apt-get -f install
sudo dpkg --configure -a
```

If you are using a HP printer you would probably be better off using HPlip instead of sane.

---

### Post by captainkelly54 on 2009-05-11
After sudo apt-get -f install, it stopped half-way through "segmentation faulty tree"

kelly@Dunn-computer:~$ sudo apt-get -f install
Reading package lists... Done
Segmentation faulty tree... 50%
kelly@Dunn-computer:~$ sudo dpkg --configure -a
Setting up ttf-dejavu-extra (2.28-1) ...
E: /var/lib/defoma/locked exists.
E: Another defoma process seems running, or you aren't root.
E: If you are root and defoma process isn't running undoubtedly,
E: it is possible that defoma might have aborted.
E: Please run defoma-reconfigure -f to fix its broken status.
dpkg: error processing ttf-dejavu-extra (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of ttf-dejavu:
 ttf-dejavu depends on ttf-dejavu-extra; however:
  Package ttf-dejavu-extra is not configured yet.
dpkg: error processing ttf-dejavu (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 ttf-dejavu-extra
 ttf-dejavu


That is the full output for both commands.
Also, I am back to the problem I had originally, I can't open Add/Remove programs, Synaptic, or update manager...I have no clue what's going on, and why it started working before

---

### Post by Partyboi2 on 2009-05-11
Open a terminal and[FONT=monospace]
[/FONT]```
sudo rm /var/cache/apt/*.bin
``` then
```
sudo apt-get -f install
```

---

### Post by captainkelly54 on 2009-05-12
results:

kelly@Dunn-computer:~$ sudo rm /var/cache/apt/*.bin
[sudo] password for kelly: 
kelly@Dunn-computer:~$ sudo apt-get -f install
Reading package lists... Error!
E: Problem parsing dependency Depends
E: Error occurred while processing evolution-exchange (NewVersion1)
E: Problem with MergeList /var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_jaunty_main_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.

---

### Post by Partyboi2 on 2009-05-13
It seems like you are having more problems with corrupted list files.  Open a terminal and
```
gksu nautilus /var/lib/apt/lists
```
Delete all the files (Not the Partial Folder) and then back in the terminal
```
sudo apt-get update
``` this will re create the list files in that directory.

---

### Post by captainkelly54 on 2009-05-13
I did that, and it did exactly what you said. But when trying to get updates I get this message:

E: Problem parsing dependency Depends
E: Error occurred while processing openoffice.orG-core (NewVersion1)
E: Problem with MergeList /var/lib/dpkg/status
E: The package lists or status file could not be parsed or opened.
E: _cache->open() failed, please report.

Earlier, my computer wouldn't start ubuntu, but after some fiddling I got it to work after selecting something in one of the menus. I think gradually my computer is dying. I really don't want to use windows

---

### Post by Partyboi2 on 2009-05-13
Open a teminal and 
```
sudo cp /var/lib/dpkg/status /var/lib/dpkg/status.broke 
``````
sudo cp /var/lib/dpkg/status-old /var/lib/dpkg/status
```then
```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by captainkelly54 on 2009-05-13
kelly@Dunn-computer:~$ sudo cp/var/lib/dpkg/status /var/lib/dpkg/status.broke
sudo: cp/var/lib/dpkg/status: command not found


then, I entered the other two commands and they did what they were supposed to, but the second command came back with no results. Is that right?

---

### Post by Partyboi2 on 2009-05-14
> **captainkelly54 said:**
> kelly@Dunn-computer:~$ sudo cp/var/lib/dpkg/status /var/lib/dpkg/status.broke
sudo: cp/var/lib/dpkg/status: command not found


then, I entered the other two commands and they did what they were supposed to, but the second command came back with no results. Is that right?

Opps...Sorry my mistake I forgot to add a space between 
"cp/var/lib/dpkg/status" so it was meant to be ```
sudo cp /var/lib/dpkg/status /var/lib/dpkg/status.broke
``` But it does not matter now because you went ahead with the next command. So if
```
sudo apt-get -f install
sudo dpkg --configure -a
``` comes back with no output then you should be all good (hopefully) :)

---

### Post by captainkelly54 on 2009-05-14
Well, here is everything:

kelly@Dunn-computer:~$ sudo apt-get -f install
Reading package lists... 0%
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  libgl1-mesa-dri
Suggested packages:
  libglide3
The following packages will be upgraded:
  libgl1-mesa-dri
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
3 not fully installed or removed.
Need to get 0B/2730kB of archives.
After this operation, 0B of additional disk space will be used.
(Reading database ... 128073 files and directories currently installed.)
Preparing to replace libgl1-mesa-dri 7.4-0ubuntu3 (using .../libgl1-mesa-dri_7.4-0ubuntu3.1_i386.deb) ...
Unpacking replacement libgl1-mesa-dri ...
lzma: Decoder error
dpkg-deb: subprocess <decompress> returned error exit status 1
dpkg: error processing /var/cache/apt/archives/libgl1-mesa-dri_7.4-0ubuntu3.1_i386.deb (--unpack):
 short read in buffer_copy (backend dpkg-deb during `./usr/lib/dri/i915_dri.so')
Errors were encountered while processing:
 /var/cache/apt/archives/libgl1-mesa-dri_7.4-0ubuntu3.1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
kelly@Dunn-computer:~$ sudo dpkg --configure -a
Setting up ttf-dejavu-extra (2.28-1) ...
E: /var/lib/defoma/locked exists.
E: Another defoma process seems running, or you aren't root.
E: If you are root and defoma process isn't running undoubtedly,
E: it is possible that defoma might have aborted.
E: Please run defoma-reconfigure -f to fix its broken status.
dpkg: error processing ttf-dejavu-extra (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of ttf-dejavu:
 ttf-dejavu depends on ttf-dejavu-extra; however:
  Package ttf-dejavu-extra is not configured yet.
dpkg: error processing ttf-dejavu (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 ttf-dejavu-extra
 ttf-dejavu

Errors everywhere..whats wrong with my computer :(

---

### Post by captainkelly54 on 2009-05-14
Now, when i try to install updates it says:

"One broken package on your system!
Use the "Broken" filter to locate it."

What do I do?

---

### Post by Partyboi2 on 2009-05-14
Maybe you have a corupt deb package, so try removing the deb package from the cache.
```
sudo rm /var/cache/apt/archives/libgl1-mesa-dri_7.4-0ubuntu3.1_i386.deb
```
then try fixing the broken package with
```
sudo apt-get -f install
```
```
sudo dpkg --configure -a
```

---

### Post by kabe2007 on 2009-05-15
I have the just same problem. I upgraded (clean install) from 8.10 to 9.04 (i've been using Ubuntu for a few years).

Hopefully having 2 people with the same problem will help. I get similar outputs. For example, look below. I tried to remove some packages after the installation of ubuntu-restricted-extras crashed, but I'm stuck.

Any help is greatly appreciated. Thanks

Juan

------------
juan@p7811fx:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  odbcinst1debian1 unixodbc
0 upgraded, 0 newly installed, 2 to remove and 0 not upgraded.
4 not fully installed or removed.
After this operation, 1208kB disk space will be freed.
Do you want to continue [Y/n]? 
(Reading database ... 108518 files and directories currently installed.)
Removing unixodbc ...
dpkg (subprocess): unable to execute post-removal script: Exec format error
dpkg: error processing unixodbc (--remove):
 subprocess post-removal script returned error exit status 2
Removing odbcinst1debian1 ...
dpkg (subprocess): unable to execute post-removal script: Exec format error
dpkg: error processing odbcinst1debian1 (--remove):
 subprocess post-removal script returned error exit status 2
Errors were encountered while processing:
 unixodbc
 odbcinst1debian1
E: Sub-process /usr/bin/dpkg returned an error code (1)

----------

---

### Post by captainkelly54 on 2009-05-15
More errors...

kelly@Dunn-computer:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
3 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up sun-java6-fonts (6-13-1) ...
E: /var/lib/defoma/locked exists.
E: Another defoma process seems running, or you aren't root.
E: If you are root and defoma process isn't running undoubtedly,
E: it is possible that defoma might have aborted.
E: Please run defoma-reconfigure -f to fix its broken status.
dpkg: error processing sun-java6-fonts (--configure):
 subprocess post-installation script returned error exit status 1
Setting up ttf-dejavu-extra (2.28-1) ...
E: /var/lib/defoma/locked exists.
E: Another defoma process seems running, or you aren't root.
E: If you are root and defoma process isn't running undoubtedly,
E: it is possible that defoma might have aborted.
E: Please run defoma-reconfigure -f to fix its broken status.
dpkg: error processing ttf-dejavu-extra (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of ttf-dejavu:
 ttf-dejavu depends on ttf-dejavu-extra; however:
  Package ttf-dejavu-extra is not configured yet.
dpkg: error processing ttf-dejavu (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                          Errors were encountered while processing:
 sun-java6-fonts
 ttf-dejavu-extra
 ttf-dejavu
E: Sub-process /usr/bin/dpkg returned an error code (1)
kelly@Dunn-computer:~$ sudo dpkg --configure -a
Setting up ttf-dejavu-extra (2.28-1) ...
E: /var/lib/defoma/locked exists.
E: Another defoma process seems running, or you aren't root.
E: If you are root and defoma process isn't running undoubtedly,
E: it is possible that defoma might have aborted.
E: Please run defoma-reconfigure -f to fix its broken status.
dpkg: error processing ttf-dejavu-extra (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of ttf-dejavu:
 ttf-dejavu depends on ttf-dejavu-extra; however:
  Package ttf-dejavu-extra is not configured yet.
dpkg: error processing ttf-dejavu (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 ttf-dejavu-extra
 ttf-dejavu

Sorry I'm sending you these long outputs, if I knew how to simplify them to only the parts you need, I would

---

### Post by Partyboi2 on 2009-05-16
Sending the long outputs are fine :)

Open a terminal and try as it suggests by running
```
 sudo defoma-reconfigure -f
```
then try
```
sudo apt-get -f install
```

---

### Post by Partyboi2 on 2009-05-16
> **kabe2007 said:**
> I have the just same problem. I upgraded (clean install) from 8.10 to 9.04 (i've been using Ubuntu for a few years).

Hopefully having 2 people with the same problem will help. I get similar outputs. For example, look below. I tried to remove some packages after the installation of ubuntu-restricted-extras crashed, but I'm stuck.

Any help is greatly appreciated. Thanks

Juan

------------
juan@p7811fx:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  odbcinst1debian1 unixodbc
0 upgraded, 0 newly installed, 2 to remove and 0 not upgraded.
4 not fully installed or removed.
After this operation, 1208kB disk space will be freed.
Do you want to continue [Y/n]? 
(Reading database ... 108518 files and directories currently installed.)
Removing unixodbc ...
dpkg (subprocess): unable to execute post-removal script: Exec format error
dpkg: error processing unixodbc (--remove):
 subprocess post-removal script returned error exit status 2
Removing odbcinst1debian1 ...
dpkg (subprocess): unable to execute post-removal script: Exec format error
dpkg: error processing odbcinst1debian1 (--remove):
 subprocess post-removal script returned error exit status 2
Errors were encountered while processing:
 unixodbc
 odbcinst1debian1
E: Sub-process /usr/bin/dpkg returned an error code (1)

----------
try ```
sudo apt-get -f install
``` and see if it clears.
Another thing to check is your
/var/lib/dpkg/info/unixodbc.postrm file  that it starts with
```
#!/bin/sh
```

---

### Post by kabe2007 on 2009-05-16
FIXED IT!!!

After spending some time trying everything, i figured out what was happening: one of the packages was wrongly installed. 

It was related to the sun-java package, so maybe captainkelly54 could also benefit. 

I identified the problem because there were several files installed with 0-byte length in /usr/lib/jvm/java-6-openjdk/jre/lib, among them resources.jar. I found the package that was wrongly installed in the site:

[http://packages.ubuntu.com/search?searchon=contents&keywords=resources.jar&mode=exactfilename&suite=jaunty&arch=any](http://packages.ubuntu.com/search?searchon=contents&keywords=resources.jar&mode=exactfilename&suite=jaunty&arch=any)

Then I installed each package again manually with:

sudo dpkg --install [package name], for example:

sudo dpkg --install /var/cache/apt/archives/openjdk-6-jre-lib_6b14-1.4.1-0ubuntu7_all.deb

(note: to complete the right package name, press tab)

And that was it!! (just follow dependencies if they are missing)

Hopefully it helps. Regards

Juan

---

### Post by captainkelly54 on 2009-05-16
Well, it seems that everything is working perfectly again (knock on wood) using partyboi's techniques..

Thanks a lot!!!

---

### Post by Partyboi2 on 2009-05-16
> **captainkelly54 said:**
> Well, it seems that everything is working perfectly again (knock on wood) using partyboi's techniques..

Thanks a lot!!!
Your welcome  :)

---

