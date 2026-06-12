---
title: "smaller version to save hard drive space?"
date: 2009-03-03
forum: Installation &amp; Upgrades
---

### Post by sansa dude on 2009-03-03
ok im on a 10gb hard drive with my laptop and i would like to know if there is a version of xubuntu that comes with just the minimum programs installed to run it ( so no abi word, thunderbird firefox etc.) so i can download my own applications? that i want to save space?

---

### Post by kyphi on 2009-03-03
Try the Base Install from this address:  [http://www.eeebuntu.org/](http://www.eeebuntu.org/)

---

### Post by sansa dude on 2009-03-03
> **kyphi said:**
> Try the Base Install from this address:  [http://www.eeebuntu.org/](http://www.eeebuntu.org/)

is this xubuntu? and how does it run on older computers? (10 years old)

---

### Post by sansa dude on 2009-03-03
i just google a base install for xubuntu and i found this: [http://akosidexter.wordpress.com/2006/10/21/xubuntu-pimp-my-gateway-solo-3350-notebook/](http://akosidexter.wordpress.com/2006/10/21/xubuntu-pimp-my-gateway-solo-3350-notebook/)

i have abou the same specs as the com puter in it but my computer is a dell and i have a 14.1 inch screen and i have 256mb of RAM i think im at 700mhz and i have no external drive other than that its pretty much all the same. 

but in that article it said he installed a base install which was the server version. can i install that and be able to build from that?

---

### Post by ajgreeny on 2009-03-03
have a look [here]("https://help.ubuntu.com/community/Installation/MinimalCD") which installs just the minimal installation of ubuntu to which you can then add any desktop you want, and also applications as and when you need them.

---

### Post by sansa dude on 2009-03-03
ok thanks for the help, but when i install the minumal version of ubuntu can i then install xubuntu and still have the minimals? i would prefer xubuntu because it works better on the older machines

---

### Post by ajgreeny on 2009-03-03
Just install **xfce4** and not xubuntu-desktop and you will get just the DE without all the clutter that makes xubuntu what it is.  On my gnome machine with no xfce at all that means a download of 16.5MB and disk usage of 50.5MB, so still very small.  You can then add whatever you need.

---

### Post by sansa dude on 2009-03-03
Perfect!! when i get that do i just install the Xfce4 from the add/remove menu? or will i just google it an download it there?

---

### Post by ajgreeny on 2009-03-03
> **sansa dude said:**
> Perfect!! when i get that do i just install the Xfce4 from the add/remove menu? or will i just google it an download it there?
From the add/remove menu will do it.

---

### Post by sansa dude on 2009-03-03
ok i ran it now when i boot it up it will ask me for my username and password when its still in the black background before the actuall operations system starts then it comes up with a terminal and thats it. is there a code i can run to install the desktop? or did i go wrong somewhere in the setup?

---

### Post by sansa dude on 2009-03-03
ok this time i ran it agin and this time i selected the xubuntu desktopthen it asks you instead on samba (i thought you would select the OS later or something like that)
so il'l see how it goes

---

### Post by sansa dude on 2009-03-03
ok i did that and it still came up with the terminal page what am i doing wrong?

---

### Post by ajgreeny on 2009-03-04
Sorry, I think you also need to install gdm before you will get the GUI to come up automatically, though it may be that the command ```
startx
``` will also work for the moment.

---

### Post by sansa dude on 2009-03-04
> **ajgreeny said:**
> Sorry, I think you also need to install gdm before you will get the GUI to come up automatically, though it may be that the command ```
startx
``` will also work for the moment.

ok i ran that then it said its not currently installed and gave me another code line to run, so i ran it. it did a couple things and ran some packages the it came back up to the terminal line
then i rebooted and it came up with the same stuff as it did before

---

### Post by ajgreeny on 2009-03-04
Did you ```
sudo apt-get install gdm
``` to get the display manager?

---

### Post by sansa dude on 2009-03-04
ok i ran that and a whole bunch of things came up and then it finnaly said something like to continue a total of 7xxmbs will be used. so i pressed yes. just one question, will this install programs too? so i can install my programs from scratch?

---

### Post by ajgreeny on 2009-03-04
Once you get a gui you will be able to add synaptic if you want it, ```
sudo apt-get synaptic
``` or continue using *apt-get*.  Synaptic will make it much easier to search for applications.

---

### Post by sansa dude on 2009-03-04
perfect!!! ok can i now install the xubuntu with the instructions from ubuntu? and still keep the minimum applications? or will i have to install the xfce4 desktop?

---

### Post by ajgreeny on 2009-03-05
*xubuntu* is still a bit heavy on applications and you may prefer to stick just with the *xfce4* desktop, rather than *xubuntu-desktop* which brings in lots of applications.  However, *xfce4* is the desktop environment that *xubuntu* uses, so if you do decide to install *xubuntu-desktop* you will not need to also install *xfce4*; it will already be there.

---

### Post by sansa dude on 2009-03-05
> **ajgreeny said:**
> *xubuntu* is still a bit heavy on applications and you may prefer to stick just with the *xfce4* desktop, rather than *xubuntu-desktop* which brings in lots of applications.  However, *xfce4* is the desktop environment that *xubuntu* uses, so if you do decide to install *xubuntu-desktop* you will not need to also install *xfce4*; it will already be there.

ok i did run ```
sudo apt-get install xfce4
``` and got alot of files being installed (about 30mb) so where can i goto install this?  other than that i should be good thanks for all the help!!!!

---

### Post by ajgreeny on 2009-03-06
> **sansa dude said:**
> ok i did run ```
sudo apt-get install xfce4
``` and got alot of files being installed (about 30mb) so where can i goto install this?  other than that i should be good thanks for all the help!!!!
What do you mean by this?  Have you tried startx in your console (dos like) start up screen?

---

### Post by sansa dude on 2009-03-06
> **ajgreeny said:**
> What do you mean by this?  Have you tried startx in your console (dos like) start up screen?

yea i did enter it but it didn't do any thing now it comes up in regular Ubuntu with gnome

---

### Post by ajgreeny on 2009-03-07
Ok, when you get to the login screen of gdm go to the options menu and choose xfce.  That should do it.

---

