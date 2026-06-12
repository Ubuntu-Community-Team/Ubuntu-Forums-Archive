---
title: "crash in open office 3.1"
date: 2009-05-13
forum: Installation &amp; Upgrades
---

### Post by hero1900 on 2009-05-13
today i install the new open office after deleting the old one
but the problem is it always crash when i try to open any program of them
any one can help??

---

### Post by alphacrucis2 on 2009-05-13
> **hero1900 said:**
> today i install the new open office after deleting the old one
but the problem is it always crash when i try to open any program of them
any one can help??

What method did you use to install it?

---

### Post by hero1900 on 2009-05-13
[http://tektrap.blogspot.com/2009/05/installing-openoffice-31-in.html](http://tektrap.blogspot.com/2009/05/installing-openoffice-31-in.html)

---

### Post by alphacrucis2 on 2009-05-13
> **hero1900 said:**
> [http://tektrap.blogspot.com/2009/05/installing-openoffice-31-in.html](http://tektrap.blogspot.com/2009/05/installing-openoffice-31-in.html)

I would try the uninstall part again. Then set up this ppa in your repos:

[URL="https://launchpad.net/~openoffice-pkgs/+archive/ppa"]https://launchpad.net/~openoffice-pkgs/+archive/ppa
[/URL]

Then

> sudo apt-get update
sudo apt-get upgrade


---

### Post by hero1900 on 2009-05-13
same problem it also crash 
it open but when i want to create blank page it crashes

[COLOR=Red]_**update:**_[/COLOR] i use this and it work i delete any thing related to the old
sudo rm -rf ~/.openoffice.org

---

### Post by rwigle on 2009-06-11
> **hero1900 said:**
> same problem it also crash 
it open but when i want to create blank page it crashes

[COLOR=Red]_**update:**_[/COLOR] i use this and it work i delete any thing related to the old
sudo rm -rf ~/.openoffice.org

I did the same, but OpenOffice Word crashes every time. I only notice this when I exit the file. (I get a crash dialogue, but it mentions no error.) After enabling the launchpad repo and getting its GPG key set up, I did the following

sudo apt-get purge openoffice
sudo rm -rf ~/.openoffice*
sudo apt-get install openoffice

I opened an XLS spreadsheet document in Calc, and got no error, but haven't tried to modify any files yet.

Hardy (using hardy repo)

---

### Post by hero1900 on 2009-06-12
the idea was to remove every thing related to old one
try synaptic and remove any thing related to openoffice then try to install 3.1

---

### Post by flibble on 2009-06-16
Hi Hero1900, Because you took the time to come back and post the solution you found, this problem only took me 5 minutes to solve.

Thank you!

---

### Post by jamaas on 2009-06-26
sudo rm -rf ~/.openoffice*


If I do this, won't I loose all my personal settings for OO, fonts, margins, paper size etc?

Thanks

Jim

---

### Post by hero1900 on 2009-06-27
Glade to serve :wink: [flibble]("http://ubuntuforums.org/member.php?u=7661")
and for you[ jamaas]("http://ubuntuforums.org/member.php?u=630") ya it will erase the hole content of the folder .openoffice so if you have some special fonts , things try to back-it-up
:popcorn:

---

