---
title: "problems instaling programs.."
date: 2008-07-14
forum: General Help
---

### Post by drakoumel on 2008-07-14
hello i am new for ubuntu :D and i got some problems i am trying to instal amsn i tried many ways..
firstly from add or remove programs tho when i get to install it i get this message : 

This Application conflicts with other installed software. To install amsn the conflicting software must be removed first. 
Switch to the synaptic to resolve this conflict. 
i have the above problem when i try to install wine but i dont really know what i have to do about it...

then i tried through the terminal : sudo apt-get install amsn 
and i get this:

Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  amsn: Depends: tcl8.4 but it is not installable
        Depends: tk8.4 but it is not installable
        Depends: tcltls but it is not going to be installed
E: Broken packages

then i went from synaptic but got again this as an explanation for the error :

amsn: Depends: tcl8.4 but it is not installable
        Depends: tk8.4 but it is not installable
        Depends: tcltls but it is not going to be installed
E: Broken packages


i get this problems with most of the applications i try to install anyone can help me?

---

### Post by Ryadt on 2008-07-14
try cleaning your system first,
```
sudo apt-get autoclean
```
in synaptic choose status, choose broken packages and then mark them for complete removal.
then try reinstalling amsn.

---

### Post by drakoumel on 2008-07-14
i cleaned my system = results : Reading package lists... Done
                                Building dependency tree       
                                Reading state information... Done
then as u said went to the synaptic / status and it says 0 broken so i couldnt remove anything..
then i tried to install but i had the same results.. :-k



also how u do the thing about CODE: and then the box?

---

### Post by Ryadt on 2008-07-14
ok try this.
Run command in terminal:

```
sudo gedit /etc/apt/sources.list
```

Add the following /etc/apt/sources.list:

deb  [http://repository.debuntu.org/](http://repository.debuntu.org/) hardy multiverse
deb-src [http://repository.debuntu.org/](http://repository.debuntu.org/) hardy multiverse

Get GPG key:

wget [http://repository.debuntu.org/GPG-Key-chantra.txt](http://repository.debuntu.org/GPG-Key-chantra.txt) -O- | sudo apt-key add -

Update:

```
sudo apt-get update
```

then install amsn through.

---

### Post by drakoumel on 2008-07-14
sorry mate but i am new and dont know that many things.. which one do i have to get from the links u gave me?

---

### Post by Ryadt on 2008-07-14
Type in terminal```
sudo gedit /etc/apt/sources.list
```
gedit will open givin you a list of your universe. Add these 2 lines in it 
deb [http://repository.debuntu.org/](http://repository.debuntu.org/) hardy multiverse
deb-src [http://repository.debuntu.org/](http://repository.debuntu.org/) hardy multiverse
save and exit.
then in terminal type```
wget http://repository.debuntu.org/GPG-Key-chantra.txt -O- | sudo apt-key add -
```
then again in terminal type ```
sudo apt-get update
```
hope this solves it.

---

### Post by jocko on 2008-07-14
> **drakoumel said:**
> 
The following packages have unmet dependencies:
  amsn: Depends: [COLOR=Red]tcl8.4[/COLOR] but it is not installable
        Depends: [COLOR=Red]tk8.4[/COLOR] but it is not installable
        Depends: [COLOR=Red]tcltls[/COLOR] but it is not going to be installed
E: Broken packages

Can you find the packages tcl8.4, tk8.4 and tcltls in synaptic? In that case try to install them first (one by one) and then try to install amsn again. Any errors?

Otherwise: Do you have all repos activated?
Open up synaptic, go to Settings --> Repositories. In the first tab, make sure to activate all repos (except source code, which you won't need if you are new to linux). In the third tab (updates), make sure you have at least the first two (-security and -updates, and maybe -backports) activated (the -proposed repo contain packages that may not be fully tested yet, so they may break things...).

---

### Post by drakoumel on 2008-07-14
everything was done but still nothing changed .. exact same questions exact same problem :(

---

### Post by drakoumel on 2008-07-14
my last answer concerned the environment thingies not the synaptic i actualy hadnt seen it. 

for the other one i am download each one separately but it will take like 1hour or so with 1mb speed , am i downloading the wrong ones or they are that big? 
if i am correct and gotta wait for an hour are there any other settups i need to make to my system for ubuntu ? 
if i am not lets try to solve it :D 

and i am really thank full for ur help here thnx mate

---

### Post by Kevbert on 2008-07-14
Gp to Terminal and enter 
```
sudo apt-get update
sudo apt-get clean
sudo apt-get autoclean
sudo apt-get install -f
```
Hopefully these commands will sort out your problems.
Click on this [[COLOR="Red"]link[/COLOR]]("http://quickstart.phpbb.net/viewtopic.php?f=8&t=11")
This will go to the Quickstart page where you can download Quickstart and it will allow you to install the correct codecs, aMSN etc for your PC.

---

### Post by jocko on 2008-07-14
> **drakoumel said:**
> my last answer concerned the environment thingies not the synaptic i actualy hadnt seen it. 

for the other one i am download each one separately but it will take like 1hour or so with 1mb speed , am i downloading the wrong ones or they are that big? 
if i am correct and gotta wait for an hour are there any other settups i need to make to my system for ubuntu ? 
if i am not lets try to solve it :D 

and i am really thank full for ur help here thnx mate

tcl8.4 and tk8.4 are both around 1 Mb in size and tcltls is less than 70 kb, so at 1Mbit/s it would take less than a minute to download them all...
Which server do you use for your repos? If your downloads are much slower than your internet connection would allow, maybe you are using the wrong server.

Again in Synaptic --> Settings --> repositories, in the first tab there is a pull-down menu "Download from:" Select "other", and in the new window, click "Choose best server".
Now all different mirrors will be tested and in the end the fastest available mirror will be selected for you. Click "Select mirror" and close the software sources window. Back in synaptic, click "Reload" and then try again.

---

### Post by drakoumel on 2008-07-14
the last codes u sented me actually worked! THANK MATE now i can install many more thingss.. did u get what was the problem ?

---

### Post by drakoumel on 2008-07-14
also now i am installing quickstar but the synaptic has showed me like 320 MB  programs listed as important security updates bzip2 compiz compiz-core and some examples should i get those downloaded?

---

### Post by Kevbert on 2008-07-15
You should install all security updates for obvious reasons and to clear up bugs.  After a new install it's common to get well over 100 updates.  I've just re-installed Hardy and had 255 updates to install (this was actually an upgrade from 8.0.4 to 8.0.4.1).

---

### Post by drakoumel on 2008-07-15
ok i will instal them thnx :D 
also whenever i close the pc my background and other custom changes i have made go back to defualt do i have to save em in some way?

---

### Post by Kevbert on 2008-07-15
Backgrounds and other effects should not change.  How are you setting them up in the first place ?  For example with backgrounds go to System-Preferences-Appearance.  Now click on the background tab and select your background.  If it doesn't appear and you have say a picture that you want to use, click on add, browse to the folder that has the picture in, click open, then check it's selected (it will be highlighted with a ring around the picture) and now select close.
If, after a reboot, the background has changed you have a problem.

---

### Post by drakoumel on 2008-07-15
i must have done something wrong i just did my restart and it was fine :P
also guyz i am using wine in order to play WoW it says that it is compatible and runs smoothly tho for me it aint working at all.. does it matter coz i havent installed it on ubuntu but on xp and i just run the .exe ?

---

### Post by jocko on 2008-07-15
> **drakoumel said:**
> i must have done something wrong i just did my restart and it was fine :P
also guyz i am using wine in order to play WoW it says that it is compatible and runs smoothly tho for me it aint working at all.. does it matter coz i havent installed it on ubuntu but on xp and i just run the .exe ?
To run an application in wine, you need to install it through wine.

---

