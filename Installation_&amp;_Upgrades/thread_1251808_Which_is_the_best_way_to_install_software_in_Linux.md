---
title: "Which is the best way to install software in Linux?"
date: 2009-08-28
forum: Installation &amp; Upgrades
---

### Post by exus69 on 2009-08-28
Hi everybody,

Am a new linux user and was reading about installing Nmap from a book which says that binary packages are available for most platforms however compilation and installation from the source code is the traditional and most powerful way of installing nmap because it can adapt to the library availability and directory structure of your system.

So the question is should I install Nmap or for that matter any other program through compilation and installation from source code or download and run the binary package from the console or use synaptics??

Please help

---

### Post by Kobalt on 2009-08-28
If you really are a new user, then I would advise to stick to Synaptic to install, manage and update your softwares.
Of course there are gains in compiling softwares, but it's not a world of difference (IMHO), and the ease of use of Aptitude (Synaptic) really is a blessing.

---

### Post by zvacet on 2009-08-28
You have nmap in synaptic.

---

### Post by kerry_s on 2009-08-28
if your new use synaptic, going outside the system is a roll of the dice.
i'm a old user & i only use the repos. :lolflag:

---

### Post by kpkeerthi on 2009-08-28
> **exus69 said:**
> Hi everybody,

Am a new linux user and was reading about installing Nmap from a book which says that binary packages are available for most platforms however compilation and installation from the source code is the traditional and most powerful way of installing nmap because it can adapt to the library availability and directory structure of your system.

So the question is should I install Nmap or for that matter any other program through compilation and installation from source code or download and run the binary package from the console or use synaptics??

Please help

Don't worry about all that. Choose Applications -> Add/Remove. Search nmap and select to install. Simple and easy.

---

### Post by beren.olvar on 2009-08-28
I would suggest you otherwise. Installing nmap is probably related with you wanting to learn new stuffs right? or maybe just concern about security? If that is the case try compiling from source.

IMHO repos are indeed a bless, when you want stuff to just work. In the other hand if you are interested in also learning in the process, I think to compile and install stuffs "old way" can be a good starting point.

It is true that in this way your installation can get a little messy, but for example you could try to make a .deb package from the latest nmap source. That way you may keep things clean.

Again, that is only if you want to have a little fun with linux. If what you want is just the program installed so you can use it, resort to the repos.

cheers

---

### Post by exus69 on 2009-08-28
Thx everybody for the quick replies. You guys ROCK:)

I installed nmap using the ./configure, make, make install
commands to see what happens and was surprised to see
matrix like scene with all the letters going up quickly:)
Just want to get used to the command line environment
and nothing more. Of course I'll use synaptics in the long
run.

Although I did notice that after installation that way there
was no entry of Nmap 5.0 in the synaptics. How come?? and

How to install a program through synaptics if it has already been downloaded and in a USB drive which is connected to a pc which isn't online??

Please help

---

### Post by kerry_s on 2009-08-28
for a deb that the package manager can use, install "checkinstall".
**sudo apt-get install checkinstall**

so you would do it like normal, except the last 1.


./configure
make
checkinstall


if its a .deb just click on it to install.

---

