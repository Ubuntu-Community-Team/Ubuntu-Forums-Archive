---
title: "Absolutely nothing will install on Ubuntu.."
date: 2009-10-25
forum: Installation &amp; Upgrades
---

### Post by ajcheeseman on 2009-10-25
I've been trying to install programs and upgrades but keep getting the same stupid f***ing bull***t message.  "Only one software management tool is allowed to run at the same time -- Please close the other application e.g. "Update Manager" , "Aptitude" , or "Synaptic" first."  Then it refuses to install anything, regardless of the fact that nothing else is running.

I'm about 3 annoying window popups away from throwing my desktop off the roof after lighting it on fire.  Someone please help. :confused:

---

### Post by linux-hack on 2009-10-25
it meens that something is using the install program. if you cant find out what juste reboot. did you try to reboot ?

---

### Post by mick222 on 2009-10-25
Well maybe if you explained the problem properly you would get some help what are you trying to install? where are you installing it from? and how are you installing it would help.
Ubuntu is NOT windows don't download things from the internet install using either synaptic or add remove from the applications tab , or you can use terminal and apt-get, leave that one for now as you seem a bit new.

---

### Post by vinutux on 2009-10-25
apt use various front ends like synaptic, add/remove, update manger...etc

---

### Post by sgosnell on 2009-10-25
It's not "stupid f***ing bull***t".  There are very good reasons for not allowing multiple instances of the same program to install different packages at the same time.  Synaptic, gdebi, aptitude, update manager, and add/remove are just front-ends for apt-get, and if you have any of these running, you can't install anything from another instance.  You have one of these running somewhere, or you wouldn't get the message.

---

### Post by vinutux on 2009-10-25
> **sgosnell said:**
> it's not "stupid f***ing bull***t".  There are very good reasons for not allowing multiple instances of the same program to install different packages at the same time.  Synaptic, gdebi, aptitude, update manager, and add/remove are just front-ends for apt-get, and if you have any of these running, you can't install anything from another instance.  You have one of these running somewhere, or you wouldn't get the message.

+1

---

### Post by bouncylj on 2009-10-25
have you checked whether the update manager is running, if not go to the system menu at the top of the screen, got to system monitor and check under the processes tab, to see if it is running.

---

### Post by ajcheeseman on 2009-10-25
I couldn't have made this anymore clear.  I'm not downloading Windows crap.  Nothing else is running at all.  I'm trying to install Adobe and other standard updates for Ubuntu that are required for everything to run properly.  And yes, I've restarted, probably close to 74 million times.  I'm not a space case.  I'm just starting to believe that Ubuntu is the next biggest time vampire next to Windows.

---

### Post by sgosnell on 2009-10-25
One more time, slowly.  Update Manager is almost certainly running, and should show in your panel somewhere.  The default for it is to run automatically at boot.  You need to close it before you can install anything.

---

### Post by hogu on 2009-10-25
something is locking /var/lib/dpkg which is what the package management system needs to run.  If you can't see anything running, then either some process is running, but you can't see it, OR there maybe there is a stale lock.  I'm not sure what happens in terms of stale locks on directories, but more than likely, there is a process running somewhere that is locking it

to find it, open up a terminal, and type

sudo lsof /var/lib/dpkg/lock

that wil tell you which process is locking that directory.

for example, i ran synaptic, then ran that command, and got this:
COMMAND    PID USER   FD   TYPE DEVICE SIZE/OFF   NODE NAME
synaptic 20135 root   12uW  REG    8,5        0 219681 /var/lib/dpkg/lock


that number, under PID, is the process ID number.  kill it!

sudo kill 20135, and your worries should (hopefully) go away.

If kill doesn't work, you may need to kill it stronger,

sudo kill -9 20135.

can you try those and let us know what you get?

thanks

---

### Post by ajcheeseman on 2009-10-26
I'm sad to inform you all that I've given up and thrown my Desktop out ... that was the biggest waste of $2500 ... I can see why computer and parts manufacturers make so much money, now .

---

### Post by blah... on 2009-10-26
Seriously? Did you try what the above poster suggested at all?

---

### Post by etali on 2009-10-26
Heh, in the unlikely event that the poster was serious, that was a little extreme :)

I've fallen foul of that error before too - attempting to install the Flash plugin for firefox while doing an apt-get.  I wasn't expecting a FF plugin to want to use the package manager, so it took me a minute or two to realize what the error was talking about.

It's annoying if you have a lot of updates to do, but once you've finished that first batch of updates after a clean install, it rarely happens.  Most packages are small and download quickly, so if you ever suddenly think "oooh, I should get that package too..." you don't have to wait long.

---

### Post by pricetech on 2009-10-26
> **ajcheeseman said:**
> I'm sad to inform you all that I've given up and thrown my Desktop out ... that was the biggest waste of $2500 ... I can see why computer and parts manufacturers make so much money, now .

Too bad he doesn't say where he is.  One of us could catch it and make good use of it.

---

