---
title: "trouble installing gimp 2.6.3 in Hardy"
date: 2008-12-17
forum: Installation &amp; Upgrades
---

### Post by citizenchris099 on 2008-12-17
First off I'm still running Hardy (8.04)

I was able to install Gimp 2.6.1 and it worked fine. A few weeks later I performed a package update and i guess 2.6.1 was removed and the update to 2.6.3 failed. 

I've been receiving a dependency error when trying to install the new Gimp 2.6.3 in Hardy. I've tried two methods first adding deb [http://ubuntu.org.ua/](http://ubuntu.org.ua/) getdeb/ to my source list and using package manager to install. Also going strait to getdeb and downloading form the site. Each method get similar results. A dependency error regarding libgtk 2. 

I followed the insructions in this thread
[http://joeb454.ubuntuforums.org/showthread.php?t=1005743&highlight=gimp](http://joeb454.ubuntuforums.org/showthread.php?t=1005743&highlight=gimp)

and i still got the same dependency error. 

Any help regarding this issue would be greatly appreciated.I'm a designer and Gimp is absolutely essential to me. 2.4 is great but the improvements made to 2.6 are fantastic.

---

### Post by mc4man on 2008-12-17
You may be trying to install a version meant for intrepid which would among other things depend on libgtk2.0-0 (>= 2.14.1).

On hardy you should be using libgtk2.0-0 (>= 2.12.0)

You can ck. in synaptic to see/confirm

Try this .deb

[http://www.getdeb.net/search.php?keywords=gimp](http://www.getdeb.net/search.php?keywords=gimp)

You may need to also install some of the other listed packages first (or download them all, stick them in an empty folder, cd to that folder in a terminal and run
```
dpkg -i *.deb
```

---

### Post by regala on 2008-12-17
> **citizenchris099 said:**
> First off I'm still running Hardy (8.04)

I was able to install Gimp 2.6.1 and it worked fine. A few weeks later I performed a package update and i guess 2.6.1 was removed and the update to 2.6.3 failed. 

I've been receiving a dependency error when trying to install the new Gimp 2.6.3 in Hardy. I've tried two methods first adding deb [http://ubuntu.org.ua/](http://ubuntu.org.ua/) getdeb/ to my source list and using package manager to install. Also going strait to getdeb and downloading form the site. Each method get similar results. A dependency error regarding libgtk 2. 


When are you guys gonna understand that the **actual** error message is necessary to have the slightest chance to help you ?

---

### Post by citizenchris099 on 2008-12-17
> **regala said:**
> When are you guys gonna understand that the **actual** error message is necessary to have the slightest chance to help you ?

No need for the hostility my man....im at work and dont have access to my buntu box. Will post the ACTUAL error when i can. Im in tech support so I get what your jibeing at. Flies w/honey though.

---

### Post by citizenchris099 on 2008-12-17
> **mc4man said:**
> You may be trying to install a version meant for intrepid which would among other things depend on libgtk2.0-0 (>= 2.14.1).

On hardy you should be using libgtk2.0-0 (>= 2.12.0)

You can ck. in synaptic to see/confirm

Try this .deb

[http://www.getdeb.net/search.php?keywords=gimp](http://www.getdeb.net/search.php?keywords=gimp)

You may need to also install some of the other listed packages first (or download them all, stick them in an empty folder, cd to that folder in a terminal and run
```
dpkg -i *.deb
```

have tried downloading from getdeb 
The install order was:
1) gimp-data
2) libgimp
3) gimp

downloded/installed gimp-data fine though when i tried to install libgimp i got the libgtk 2 dependancy error (will post ACTUAL error so that there is any chance you can help me lol later)

anyhoo so libgimp wont install.

---

### Post by citizenchris099 on 2008-12-17
for regala and anyone else that thinks this can help to solve the issue
when i go to get deb i select to install "gimp-data" and it installs fine. then select to install "libgimp2.0" and package installer gives me in bold red letters gives me an "error:dependency not satisfiable: libgtk2.0-0" error message. hopes this helps you to help me ;)

---

### Post by mc4man on 2008-12-17
Go into synaptic, search libgtk2.0 and post version # shown

Do you remember how you originally installed gimp 2.6.1?

Also search and post ver. # of libgimp as shown in synaptic

Edit : just gave a try (never had 2.6.x installed

Went fine though noticed gimp must be removed first before libgimp would install.
Also needed all 4 additional packages installed before gimp.
[B]
gimp and libgimp must be the same version[/B] so remove existing gimp.

Possible conflicting packages (where removed to allow intial install

gimp-gnomevfs
gimp-python

---

### Post by citizenchris099 on 2008-12-17
> **mc4man said:**
> Go into synaptic, search libgtk2.0 and post version # shown

Do you remember how you originally installed gimp 2.6.1?

Also search and post ver. # of libgimp as shown in synaptic

Edit : just gave a try (never had 2.6.x installed

Went fine though noticed gimp must be removed first before libgimp would install.
Also needed all 4 additional packages installed before gimp.
[B]
gimp and libgimp must be the same version[/B] so remove existing gimp.

Possible conflicting packages (where removed to allow intial install

gimp-gnomevfs
gimp-python

acording to synaptic:
neither gimp-gnomevfs or gimp-python are installed.
libgtk2.0-0 installed
libgimp2.0 installed

i added deb [http://ubuntu.org.ua/](http://ubuntu.org.ua/) getdeb/ to my source list to get 2.6.1 going.

---

### Post by citizenchris099 on 2008-12-17
ok removed current installed version of gimp data and libgimp
activated deb [http://ubuntu.org.ua/](http://ubuntu.org.ua/) getdeb/ in my source list
did an update and (tried to) install in terminal of gimp this is what i get

sudo apt-get install gimp
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  gimp: Depends: libgimp2.0 (>= 2.6.3) but it is not going to be installed
        Depends: libgimp2.0 (<= 2.6.3-z) but it is not going to be installed
        Depends: libgtk2.0-0 (>= 2.14.1) but 2.12.9-3ubuntu5 is to be installed
        Depends: libpango1.0-0 (>= 1.21.6) but 1.20.5-0ubuntu1 is to be installed
        Depends: libpoppler-glib3 but it is not installable

---

### Post by mc4man on 2008-12-17
I don't know what that repo is you've added to your sources (different language) but it probably is at the root of your problems.

It seems more than likely that you can't install gimp 2.6.3 on hardy, certainly not one **built for intrepid**.

You can install 2.6.2 if you get one built for hardy (as in getdeb I linked for you.

You'll need to remove that source you've added before doing anything.(and gimp, libgimp0, and anything else gotten from that source if installed

Note I have 2.6.2 up and running now on hardy.

---

### Post by citizenchris099 on 2008-12-17
that source is getdeb
deb [http://ubuntu.org.ua/](http://ubuntu.org.ua/) getdeb/
its just letting you install getdeb stuff through synaptic rather than from the site. 
also w/2.6.2 i get the same issue installing libgimp2.0

i mean honestly i dont mind upgrading to 8.10 only problem is when i first tried and upgrade everything worked fine cept i had major issues getting the resolution right with my lcd hdtv. been reading up on xorg and think maybe any issues can be fixed in the xorg.comf file. but thats another thread in and of itself lol

---

### Post by mc4man on 2008-12-17
I think your missing the point here. Your source (deb [http://ubuntu.org.ua/](http://ubuntu.org.ua/) getdeb/) is giving you packages only meant for Intrepid.

If you want gimp 2.6.2 on Hardy then remove deb [http://ubuntu.org.ua/](http://ubuntu.org.ua/) getdeb/ from your sources, remove any packages you've installed thru them (if any), and get the packages needed from getdeb for **Hardy**


[http://www.getdeb.net/search.php?keywords=gimp](http://www.getdeb.net/search.php?keywords=gimp)

---

### Post by citizenchris099 on 2008-12-18
> **mc4man said:**
> I think your missing the point here. Your source (deb [http://ubuntu.org.ua/](http://ubuntu.org.ua/) getdeb/) is giving you packages only meant for Intrepid.

If you want gimp 2.6.2 on Hardy then remove deb [http://ubuntu.org.ua/](http://ubuntu.org.ua/) getdeb/ from your sources, remove any packages you've installed thru them (if any), and get the packages needed from getdeb for **Hardy**


[http://www.getdeb.net/search.php?keywords=gimp](http://www.getdeb.net/search.php?keywords=gimp)

I hear you mc4man. at this point im prolly to far gone in downloading packages i shouldnt have from that repo. im going to upgrade to ibex this weekend. Either that or install the new gimp from source. 
[https://help.ubuntu.com/community/CompilingEasyHowTo](https://help.ubuntu.com/community/CompilingEasyHowTo)

---

### Post by citizenchris099 on 2008-12-23
for those interested this issue has been solved.
I removed any and all remnants of any previously installed gimp and gimp dependencies then downloaded/installed (dependencies first) gimp 2.6.2 from the following site. thanks to those that tried to help it was greatly appreciated. 
[http://www.getdeb.net/release/3453](http://www.getdeb.net/release/3453)

---

