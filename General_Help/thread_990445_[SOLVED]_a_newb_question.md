---
title: "[SOLVED] a newb question"
date: 2008-11-22
forum: General Help
---

### Post by Bakamoto on 2008-11-22
well, since i know i am about to make someone laugh hard (me being a total newb here) i really need ur hlp guys. now as follows, i installed Ubuntu 8.10 and ofcourse messed it all up with a lame attempt to install some software trough console.

while doing that i had a power down and when i got it on i couldnt start add/remove software stuff cuz it said 

"This is a major failure of your software management system. Please check for broken packages with synaptic, check the file permissions and correctness of the file '/etc/apt/sources.list' and reload the software information with: 'sudo apt-get update' and 'sudo apt-get install -f'."

as a normal human being i tried what the system suggested, and i found my self clueless in what to do next. 

now, i have to ask, is there a way to reverse/undo the crap i've done so far? Cuz i dun wanna go back to Windows...

thanx in advance

regards

---

### Post by Toufik on 2008-11-22
Well, you don't really answer the usefull questions:
* Is your sources.list file correct?
* Does apt-get update work?
* Does apt-get -f install work?

Removing the crap will be pretty much the same as finishing the interrupted job :)

---

### Post by Bakamoto on 2008-11-22
> **Toufik said:**
> Well, you don't really answer the usefull questions:
* Is your sources.list file correct?
* Does apt-get update work?
* Does apt-get -f install work?

Removing the crap will be pretty much the same as finishing the interrupted job :)

any usefull tips in how to do it? and no, i dun think my sources.list is correct, and heres what it says when i type apt-get update:

**************:~$ apt-get update
E: Type 'ntrepid-backports' is not known on line 40 in source list /etc/apt/sources.list
**************~$

and when i type apt-get -f install:
****************:~$ apt-get -f install
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
****************:~$

---

### Post by drs305 on 2008-11-22
> **Bakamoto said:**
> any usefull tips in how to do it? and no, i dun think my sources.list is correct, and heres what it says when i type apt-get update:

**************:~$ apt-get update
E: Type 'ntrepid-backports' is not known on line 40 in source list /etc/apt/sources.list
**************~$

Backup sources.list and edit incorrect line:
```

sudo cp /etc/apt/sources.list /etc/apt/sources.list.backup
gksudo gedit +40 /etc/apt/sources.list

```

Gedit should open sources.list at line 40. Change 'ntrepid-backports' to 'intrepid-backports'. Look at the rest of the file past line 40 for errors. If you don't know what else, if anything, is wrong, post the contents here.

> 
and when i type apt-get -f install:
****************:~$ apt-get -f install
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?

First, make sure synaptic is not open. If it is, close it. Then run:
```
sudo apt-get -f install
```
It will ask for your password. Type it and when done hit Enter. You won't see the characters you are typing.

---

### Post by Bakamoto on 2008-11-22
all worked exept for the last part, it still says:

**************:~$ sudo apt-get -f install
[sudo] password for bakamoto: 
E: Type 'intrepid-backports' is not known on line 40 in source list /etc/apt/sources.list
E: The list of sources could not be read.
**************:~$ 

dunno what i have done, but i sure hope i didnt messed it all up.

---

### Post by ciscosurfer on 2008-11-22
@Bakamoto,

Please use code blocks around terminal text. 

Also, just open up /etc/apt/sources.list and look for the appropriate line.```
gksudo gedit /etc/apt/sources.list
```

---

### Post by Bakamoto on 2008-11-22
thnx guys, i just erased a line which shouldnt be there in the 1rst place. all of you helped...

me likey Ubuntu... :D

---

### Post by ciscosurfer on 2008-11-22
@Bakamoto,

The help pages are useful resources as well. 

For future reference: 
[https://help.ubuntu.com/8.10/add-applications/C/index.html](https://help.ubuntu.com/8.10/add-applications/C/index.html)
[https://help.ubuntu.com/community/Repositories/CommandLine](https://help.ubuntu.com/community/Repositories/CommandLine)

---

