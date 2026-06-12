---
title: "C compiler cannot create executables"
date: 2008-08-18
forum: General Help
---

### Post by coder.com on 2008-08-18
Hello world
    please help me, I'm new to linux. 

**Requirement** : to install softwares

**Error** : when I say ./configure it says "configure: error: C compiler cannot create executables"

**I did** : I have tried installing build-essential but it says "Couldn't find any package whose name or description matched "build-essential""

Plese post link to get build-essentials. 


================> Query <=======================

root@phb:/home/prabhu# cd anjuta-2.3.5

root@phb:/home/prabhu/anjuta-2.3.5# ./configure

checking for a BSD-compatible install... /usr/bin/install -c

checking whether build environment is sane... yes

checking for a thread-safe mkdir -p... /bin/mkdir -p

checking for gawk... no
checking for mawk... mawk

checking whether make sets $(MAKE)... yes

checking whether to enable maintainer-specific portions of Makefiles... no
checking for pkg-config... /usr/bin/pkg-config

checking pkg-config is at least version 0.9.0... yes

checking for gcc... gcc

checking for C compiler default output file name... 

configure: error: C compiler cannot create executables

See `config.log' for more details.





======================> Config.log <=======================



configure:3595: error: C compiler cannot create executables


=============>> install build-essential <=====================



root@phb:/home/prabhu# sudo aptitude install build-essential
Reading package lists... Done
Building dependency tree      
Reading state information... Done
Reading extended state information     
Initializing package states... Done
Building tag database... Done
Couldn't find any package whose name or description matched "build-essential"
Couldn't find any package whose name or description matched "build-essential"
No packages will be installed, upgraded, or removed.

0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

Need to get 0B of archives. After unpacking 0B will be used.
Reading package lists... Done
Building dependency tree

Reading state information... Done
Reading extended state information   
Initializing package states... Done
Building tag database... Done

---

### Post by coder.com on 2008-08-18
Please give me solution.

---

### Post by y-lee on 2008-08-18
you need to [add Universe and Multiverse repositories]("https://help.ubuntu.com/community/Repositories/Ubuntu") first.:)

---

### Post by coder.com on 2008-08-18
Thanks but I want to install driver for my pppoe connection using ./configure....  w/o which i can't add Repositories.

---

### Post by y-lee on 2008-08-18
> **coder.com said:**
> Thanks but I want to install driver for my pppoe connection using ./configure....  w/o which i can't add Repositories.

Ok it seems you have no internet connection assuming I read that right.

Hopefully you have the LiveCD you used to install ubuntu with. If so you can try using the Cd as a repository. I believe that build-essential should be on the Cd. See [Monkey blog]("http://monkeyblog.org/ubuntu/installing.html#add_cd") on how to add the Cd to your repos.

---

### Post by mali2297 on 2008-08-18
> **coder.com said:**
> Thanks but I want to install driver for my pppoe connection using ./configure....  w/o which i can't add Repositories.

Do you mean that the computer is not connected to the internet?

If so, insert the Install CD, open Synaptic package manager, go to Settings -> Repositories and make sure that the CD-ROM repository is enabled. Then find build-essential and install it.

---

### Post by coder.com on 2008-08-19
I am having a working Internet connection but with XP.. Now I am trying to install driver for PPPOE connection on a new Ubuntu HARDY HERON....... during which i am getting above error.......

Well....... let me try using DVD depositories.:)

---

