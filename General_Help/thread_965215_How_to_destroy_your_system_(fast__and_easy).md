---
title: "How to destroy your system (fast  and easy)"
date: 2008-10-31
forum: General Help
---

### Post by small_sammy on 2008-10-31
Hi there to all!
I am in desperate need of your help, please keep reading, funny story follows...

I wanted to install a LAMP server on my new XUBUNTU 8.04.
Researching on the net, i found about this awesome feature i did not know the command:
```
sudo tasksel
```

So i run this from a terminal and installed the LAMP server. Before testing if the LAMP works i entered the tasksel interface again to check what other options are there...maybe I needed something else also...

So this big menu comes and I see that "Print Server" is checked by default...I think what the heck, I dont need a print server, I dont even own a printer for gods sake... So I untick this option and press the OK button...

The screen removing packages comes up, and i think this may take a while, why not roll a cigarette....and I suddenly notice it is removing packages I need...packages critical to my systems operation...packages I recently installed...FFS it is removing my gnome desktop!!! I fire up another terminal find the bloody process by ps aux, and try to kill it brutally....u know with -9 option...but nothing ...it worked to the end...removed everything... now system boots only in text mode....hell it even removed the network packages, i cannot do anything via apt-get...

So after this long post, could you help me restore my system with the live cd without formatting?

---

### Post by anjilslaire on 2008-10-31
Edit your /etc/apt/sources.list to include the Ubuntu cdrom (should be the top entry. Uncomment it. Try 
```

sudo nano /etc/apt/sources.list

```
Then after the cd is recognized as a install source, put the Ubuntu CD back in.

When the cd mounts, install gnome again from the disc:
```

sudo apt-get install ubuntu-desktop

```

UPDATE: good idea, tjwoosta :)

---

### Post by tjwoosta on 2008-10-31
[https://help.ubuntu.com/community/Tasksel]("https://help.ubuntu.com/community/Tasksel")

check out the link, it looks like you can just run tasksel again and install the ubuntu desktop

EDIT: the post above mine will probably work better

---

### Post by small_sammy on 2008-10-31
Well, update of the situation:

Uncommenting the cdrom in sources.list did not do the trick.
I found out about ```
sudo apt-cdrom add /dev/cdrom
``` which got the cdrom recognized by apt.

Doing apt-get install xubuntu-desktop i get this huge list of dependencies, and then aptitude will quit, suggesting I run 
"apt-get -f install" with no packages.

I run this command it locates all dependencies, after that it asks me as usual if I want to proceed, and that xxxMB will be used, I answer yes, and then complains once more that it could not communicate with the repositories and exits...

Also rerunning Tasksel and trying to install from there will fail ...error seems like aptitude failed..

Any other ideas...maybe I am doing smthg wrong...

---

### Post by cariboo on 2008-10-31
Are you sure you removed the networking package, as hardy doesn't start networking at the command prompt, to get it going tpye:

```
sudo dhclient eth0
```

If the networking is still there, this should get you a network connection.

Jim

---

### Post by small_sammy on 2008-10-31
Cool m8!

Networking is still there...seems we are getting somewhere.. :)

Though the ppl behind "tasksel" seem to have a very special and nasty humour... :)
Check this:
[https://bugs.launchpad.net/ubuntu/+source/tasksel/+bug/150252](https://bugs.launchpad.net/ubuntu/+source/tasksel/+bug/150252)

---

### Post by small_sammy on 2008-10-31
Update of situ:

Got networking working with abovementioned command.

Run command ```
sudo apt-get -f install
```

Found around 400 packages which will occupy 778MB in my hard drive!

**Bad joke following
Nice one....i guess the ppl behind Tasksel are the ppl behind cups...They were probably thinking: 
"You wanna remove CUPS huh? Lets see if you will ever think about it again" :)

---

### Post by Hangwire on 2008-10-31
if i were you, id pull out the power cable :D
i hope your system is okay by now :)

---

