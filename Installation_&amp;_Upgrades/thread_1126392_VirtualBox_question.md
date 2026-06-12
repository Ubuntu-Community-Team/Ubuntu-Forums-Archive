---
title: "VirtualBox question"
date: 2009-04-15
forum: Installation &amp; Upgrades
---

### Post by Bapu on 2009-04-15
In searching for the install instructions for VirtualBox on Ubuntu 8.10 I see there are only instructions for 8.04.

Does this mean:

a) I cannot install on 8.10
b) I use 8.04 instauctions for 8.10

Thanks for your input.

---

### Post by diwas on 2009-04-15
b) is probably your answer.

---

### Post by stringkarma on 2009-04-15
The documentation online sometimes doesn't get updated all that often.

Try using [http://www.virtualbox.org/wiki/Linux_Downloads]("http://www.virtualbox.org/wiki/Linux_Downloads") to add the repos and then install virtualbox-2.2 from synaptic or apt-get

---

### Post by techlive on 2009-04-15
Its really very easy to install on Ubuntu 8.10

---

### Post by jbrown96 on 2009-04-15
Just add the repo as the last poster suggests. I think the only other thing you will need to do is add yourself to the vboxusers group.

It should be ```
sudo usermod -aG vboxusers $USER
``` if I remember correctly.

---

### Post by stringkarma on 2009-04-15
You can do this step graphically in the Users and Groups administration panel too

---

### Post by Bapu on 2009-04-15
> **jbrown96 said:**
> Just add the repo as the last poster suggests.

Please bear with me, I'm new to Ubuntu (and virtualization for that matter).

what is a repo and exactly how do I add it?

Thx.

---

### Post by jbrown96 on 2009-04-15
Repos are software repositories. They are websites that you can download software from. You will need to add the address of the repository and the key (optional but highly encouraged).

Go to [this site]("http://www.virtualbox.org/wiki/Linux_Downloads") for all the info you need. I'll walk you through doing this on the command line; I think it's easier.

Open a terminal (Apps--->Acc--->terminal), and do the following.

```
gksu gedit /etc/apt/sources.list
``` A window will ask for your password and then open a text editor. Go to the bottom of this file. And paste in the appropriate address for your Ubuntu version. (If you are using Intrepid, then you would use this line: deb [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) intrepid non-free). Save and exit. You may want to put in a comment so you know what this repo is for. I would put something like ```
# Virtualbox Repository
``` You can put whatever you like, just make sure that there is a # at the beginning of the line.

Back in the terminal run ```
wget -q http://download.virtualbox.org/virtualbox/debian/sun_vbox.asc -O- | sudo apt-key add -
``` then reload your software lists with ```
sudo apt-get update
``` Then install virtualbox. ```
sudo apt-get install virtualbox-2.2
``` Once this finishes, run the usermod command from my earlier post. Reboot and you can use Virtualbox (Apps--->System Tools (??).).


There is an easier way to just download the package from that site, but you won't be able to get updates automatically for it.

---

### Post by Bapu on 2009-04-15
Thanks,

That was very considerate to post the details of how to do this.

As was probably true one time for you, some of this is overwhelming. However, what you've provided seems to be the level of detail I need right now.

I'll give the whole VirtualBox install a whirl tonight when I get home.

---

### Post by ahbart on 2009-04-15
You can do this all in the graphical application too:
```
gnome menu - system - administration - Synaptic package manager.
```
type your password to use it.
go to:
```
menu - settings - Repository
```
and choose the second tab: Third party Software
There click: add
copy this line as suggested above:
```
deb http://download.virtualbox.org/virtualbox/debian intrepid non-free
```
Leave synaptic open on the repository window.

Download this file and save it. [sun_vbox.asc](http://download.virtualbox.org/virtualbox/debian/sun_vbox.asc)
Probably you have to right click it to save it. (Save link as)

Go back to synaptic, still open and go to the tab: Authentication
Click the button: import key file. 
and select the sun_vbox.asc
ok ok

Reload synaptic (button) and search for virtualbox-2.2 and click to install it.

There are always more ways to do something! :D No offence to the CLI though! ;)

---

