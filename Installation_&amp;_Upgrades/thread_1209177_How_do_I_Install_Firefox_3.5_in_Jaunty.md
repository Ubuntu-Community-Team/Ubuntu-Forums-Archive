---
title: "How do I Install Firefox 3.5 in Jaunty?"
date: 2009-07-10
forum: Installation &amp; Upgrades
---

### Post by RadarBat on 2009-07-10
Where do I extract the tarball to? How do I make a launcher on the panel? I really would like to see how much faster FF 3.5 is than 3.0.

The tarball is available at: [Firefox 3.5](http://www.mozilla.com/en-US/firefox/all.html)

---

### Post by masux594 on 2009-07-10
Search in the forum about Shiretoko that is the brand new name of firefox in linux..Don't open a new thread where there isn't the needs =P

Sysc, A

---

### Post by tommcd on 2009-07-10
> **RadarBat said:**
> Where do I extract the tarball to? How do I make a launcher on the panel? I really would like to see how much faster FF 3.5 is than 3.0.

Download firefox 3.5 to your home directory. Open a terminal and run:
```
tar -xvjf firefox...tar.bz
``` (use the exact file name in the above command).
Then do:
```

cd firefox/plugins
ln -s /usr/lib/mozilla/plugins/* .
cd ~/firefox
./firefox &

```
You will now be running firefox 3.5. All of your plugins should work. 
This will not affect the current FF installed on your system. Anytime you want to run FF 3.5 just cd into the firefox directory in you home directory and run:
```
./firefox &
```
 This is how I run FF 3.5.
I don't know how to put that on the top panel though.

Shiretoko is the Ubuntu-ized version of FF 3.5. I think it is still based on a beta version of FF 3.5.

---

### Post by RadarBat on 2009-07-10
Sorry, but something is not working. I did as instructed and could not get into the /firefox directory. Is something missing in the instructions? Or am I too dense to figure it out?
Thanks for your help.   RB

EDIT: I extracted in the wrong folder (corrected). Sorry. When I run the "./firefox &" from the firefox directory, it says " could not find firefox-bin" , and firefox-bin IS in the directory. What's up?

EDIT2: I installed FF 3.5 on an Eeebuntu machine and on an Xubuntu machine using [THIS](http://codsplaice.blogspot.com/2009/07/how-to-install-firefox-35-on-eeebuntu.html) information, but when I try to install on my Ubuntu 9.04-amd64 desktop box, it does not work at all.

---

### Post by JohnLau on 2009-07-11
):P Don't use the tarball... installing it from deb packages is always better
You can follow [my guide]("http://compustorm.no-ip.org/2009/07/howto-install-firefox-3-5-on-ubuntu-jaunty/") to do it

John

---

### Post by renbla on 2009-07-11
If you are not a developer, there's no point using a tarball, it will only give you headache, use deb :)

---

### Post by tommcd on 2009-07-11
John,
Is that Shiretoko still a beta version of FF 3.5?

EDIT: The Shiretolo FF 3.5 is in the mainline Ubuntu repos. No need to use the ppa.launchpad repo. The OP can just:
**sudo apt-get install firefox-3.5**
and he will get the Shiretoko FF 3.5.
Also,
The way I described to get FF 3.5 does not actually install the FF3.5.tar.bz tarball. It just unpacks and runs from the user's home directory. It does not touch the FF that is currently installed on the system.

---

### Post by JohnLau on 2009-07-11
> **tommcd said:**
> John,
Is that Shiretoko still a beta version of FF 3.5?

EDIT: The Shiretolo FF 3.5 is in the mainline Ubuntu repos. No need to use the ppa.launchpad repo. The OP can just:
**sudo apt-get install firefox-3.5**
and he will get the Shiretoko FF 3.5.
Also,
The way I described to get FF 3.5 does not actually install the FF3.5.tar.bz tarball. It just unpacks and runs from the user's home directory. It does not touch the FF that is currently installed on the system.

No it is not a beta, as you can see from help --> about shiretoko, it is the 3.5 final.
Yes, I just checked and found out that firefox 3.5 is already in jaunty updates, so we don't need to add any ppa. Will rewrite my guide soon :D

---

### Post by randytan on 2009-07-11
Er, isn't this supposed to update automatically via synaptic manager and update manager?

---

### Post by JohnLau on 2009-07-11
It is supposed to be updated automatically in Karmic (9.10) only. I think they want to use firefox 3.5 as a 'selling point' of ubuntu Karmic...
John

---

### Post by philip5 on 2009-07-11
I have (among a bunch of other updated packages) Firefox 3.5 as packages in my repo for ubuntu 9.04 (jaunty) for anyone who like to give it a try. It installs as stand alone to firefox 3.0.x so you can keep them bouth untill a karmic dist-upgrade. 

Keep in mind that they use the same extensions/add-ons so the versions of them might not be backward compatible if you update them between the two versions. This conflict is something firefox itself solves and turn them on and off after questioning you while starting firefox or you can du it manually in the firefox add-on settings.

You find my repo at the url in my signature and at the site you also find instructions on how to add the repo if you have any problems with that.

Have fun!

---

