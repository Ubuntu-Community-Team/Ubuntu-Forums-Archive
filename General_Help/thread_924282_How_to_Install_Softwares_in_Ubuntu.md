---
title: "How to Install Softwares in Ubuntu?"
date: 2008-09-19
forum: General Help
---

### Post by mrfikri on 2008-09-19
I'm a new user of Linux and I have a problem to install new softwares in my current operating system (Ubuntu). I realized, every time I download any softwares, I will get 2 files where both files formated in .deb.

I don't know what every file, for... but maybe want of them is for the software's data since I saw one of them will be named as 'data'.

I could install the 'data' file by clicking on the 'install package' button but I couldn't install the other one. When I run the file, this status will be shown: **[COLOR="Red"]Error: Dependecy is not satisfiable: libcurl3[/COLOR]**

what is the problem? and another thing, i saw this statement before I download the files: 'apt-get install homebank'. What this thing for?

---

### Post by phidia on 2008-09-19
Open your System > Administration > Synaptic Package Manager and use that to install programs (you can search for programs you want in that too).

---

### Post by llebegue on 2008-09-19
In Ubuntu many softwares are pre-packaged in a central repository. This repository handles for you all the "dependencies" relations between softwares.

On a day to day basis it means that you shouldn't have to download any software from some random internet site (unless you have some very specific needs that cannot be fulfilled in ubuntu repository).

How to find software ?

Try System > Administration > Synaptic Package manager
and use the "search" function or, alternately, ask to other users in this forum what package could fit your needs.

---

### Post by northern lights on 2008-09-19
[http://psychocats.net/ubuntu/installingsoftware]("http://psychocats.net/ubuntu/installingsoftware")

---

### Post by mrfikri on 2008-09-19
Thanks for your reply... but i found it doesn't works well for me.

you must ever installed homebank software which you can get from [http://homebank.free.fr/](http://homebank.free.fr/). i want to install it rite now.

i downloaded 2 files. i already install the data file. I looked at the synaptic manager and found the file and it was installed. what next?

what should i do to get the complete software? i mean, with the GUI... i can't install the other file. :(

---

### Post by northern lights on 2008-09-19
Homebank is in the repositories also (universe).

I.e. ```
sudo apt-get update && sudo apt-get install homebank
```will do. You should also find either package in Synaptic.

No need for manual downloads.

---

### Post by mrfikri on 2008-09-19
sorry... it doesn't work too. this came out when i use the terminal.

> root@mr-fikri:~# apt-get update && apt-get install homebank
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/main Translation-en_US
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/restricted Translation-en_US
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package homebank is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package homebank has no installation candidate



what should i do?

---

### Post by northern lights on 2008-09-19
Check [http://packages.ubuntu.com/search?keywords=homebank&searchon=names&suite=gutsy&section=all]("http://packages.ubuntu.com/search?keywords=homebank&searchon=names&suite=gutsy&section=all") for reference.

Hardy's got 3.6 in the repos, Gutsy repos include 3.3

Do you have the universe repository enabled?
--> Check under "System > Administration > Software Sources"

---

### Post by llebegue on 2008-09-19
Have you activated "universe" repository in Synaptic ?

---

### Post by mrfikri on 2008-09-19
i think, i found the problem... :p

should i connect to internet to install Homebank? or i can still install without it since i have the 2 .deb files where i downloaded them yesterday? 

i don't connect to the internet on the computer i'm trying to install Homebank. now, i'm connected on my another computer.

---

### Post by llebegue on 2008-09-19
If you want to make sure that homebank is updated in time when patches are available then you should have it istalled with an internet connection.
If not then you can try to install the .deb you have donwloaded but you will be on your own for the updates.

---

### Post by oldsoundguy on 2008-09-19
What you have to understand is that MOST of the extra programs and ALL of the updates are ON LINE at the repositories.  You have to go through the steps of enabling the repositories first, then use synaptic or add/remove (or even terminal for that matter) to install those items into your build.  For that you have to be on line.

---

### Post by mrfikri on 2008-09-19
TQ! i'm so sorry for taking much of your times. TQ for your help. I hope, it will work after this :) i'm a new user... forgive me for that.

---

