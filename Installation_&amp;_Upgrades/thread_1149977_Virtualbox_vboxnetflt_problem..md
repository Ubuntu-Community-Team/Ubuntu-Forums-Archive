---
title: "Virtualbox vboxnetflt problem."
date: 2009-05-05
forum: Installation &amp; Upgrades
---

### Post by Sacriom on 2009-05-05
Can't get to install virtualbox in my ubuntu. 
This is the problem i get.

[IMG]http://img518.imageshack.us/my.php?image=errork.png[/IMG][IMG]http://img518.imageshack.us/img518/8871/errork.png[/IMG]

I had tried everything i just researched, but no solution.
Any ideas?

Ubuntu 9.04
File: virtualbox-2.2_2.2.2-46594_Ubuntu_jaunty_amd64

---

### Post by Sacriom on 2009-05-06
Ok i just fix this, don't remember how but i did this steps more less:
I was trying to update my Virtual Box 2.1.x OSE to Virtual Box 2.2 closed version, so i had the error from my last post. 
You can download the virtualbox from [http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads)
I downloaded Ubuntu 9.04 ("Jaunty Jackalope") AMD64(i have intel core 2 duo t9400)

First, i entered Synaptic Package Manager(System>Administration), then in the menu, i searched for virtualbox and selected all virtualbox stuff, and i checked marked remove completely.
Then, after removing all virtualbox stuff, i did the following commands as root:
(To enter terminal as root, type ALT+F2, and enter gksu xterm)
apt-get upgrade
sudo aptitude update
sudo aptitude install virtualbox-2.2

I think it's different to type the last command i typed to sudo apt-get install virtualbox-2.2 because it didn't worked for me, or maybe was because i wasn't in root mode.

Ok, now i had installed the virtualbox but it didn't appeared in applications, so i just typed ALT+F2, and then VirtualBox, and i had my new VBox with USB and all settings enabled.

Here's a picture.
[IMG]http://img16.imageshack.us/img16/7203/vbox.png[/IMG]

Hope this helps for someone.

---

