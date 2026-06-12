---
title: "libc6-dev dependency problems"
date: 2009-09-03
forum: Installation &amp; Upgrades
---

### Post by justamel on 2009-09-03
I am a total newbie on these forums, but it seems I am having similar problems trying to get an internal winmodem to work as a person who posted back in Aug,2008.
 
It's on a Compaq Presario 2100 notebook with Ubuntu 8.04 installed. I have determined that the modem needs a Linuxant HSFmodem driver, which I downloaded via another computer and transferred on a USB stick.
 
On trying to install hsfmodem driver it said it required ALSA driver (even though info. on Linuxant site seemed to indicate it was not req'd.) I downloaded appropriate ALSA driver; tried to install it and got "dependency errror - require libc6-dev".
 
I found this package via Synaptic and tried to install it but it required a different version of libc6!!
 
The version of libc6-dev which appears to be available on the system is:
libc6-dev [2.7-10 ubuntu4]
The libc6 version is: [2.7-10 ubuntu3] - this is shown as "installed"
 
When I searched at: [http://packages.ubuntu.com](http://packages.ubuntu.com) I could not find "version 4" of either of these packages!!
 
Question 1: is there a version 4 of "libc6" and "libc6-dev"??
 
I downloaded libc6-dev [2.7-10 ubuntu3] and tried to install it, but got a "broken package" error message - the ALSA driver package which wouldn't install before.
 
Question 2: will the version 3 of libc6-dev work with libc6 version 3 and satisfy the ALSA driver requirements?
 
Question 3: do I have to remove the "broken" ALSA driver package and the hsfmodem driver pkg. and start over by installing libc6-dev first? If I go through the Synaptic install/remove process can I screw up other parts of the system??
 
Hope someone can help.

---

### Post by shredder12 on 2009-09-03
By version 4 if you mean libc6-dev 2.7.10 ubuntu4 then 
check [this]("http://packages.ubuntu.com/search?keywords=libc6-dev&searchon=names&exact=1&suite=all&section=all")

it seems you are right they don't have any.

First of all in order to repair your broken packages
run in terminal
```
sudo apt-get -f install
```

and use synaptic or apt to install packages which are available in the repos..
don't download them manually

I am not sure about alsa drivers or version 4 ..but I will look for it nd see what i can do..

---

### Post by mrgnash on 2009-09-03
Ok, this is rather strange... have you enabled any third-party. PPA, or backport repositories at any stage during your upgrades? This is the only thing that I can imagine would account for libc6 and libc6-dev being out of "sync", as it were. If so, then I recommend checking your /etc/apt/sources.list file, and enable ONLY the official Ubuntu repositories.

(You may need to remove the failed install of the Alsa driver before undertaking the below:)

Run:

```
sudo apt-get update
```

Then:

```
sudo apt-get install libc6-dev
```

If that doesn't work, then:

```
sudo apt-get install libc6-dev=2.7-10 ubuntu3
```

---

### Post by mc4man on 2009-09-03
Libc6 in hardy is now up to 2.7-10ubuntu5, it's available thru hardy-updates (just updated recently from 2.7-10ubuntu4

Go System -> Admin... -> Software Sources and under the 'update' tab make sure the first 2 choices are enabled. Then click close and reload.

After that you'll find an update for libc6 and the -dev available

---

### Post by justamel on 2009-09-17
Not certain about "protocol" on forums like this, but thought I should post a message to indicate that the above titled problem is now solved.
 
As was suggested in replies I backtracked and removed the Alsa driver and HSFmodem pkgs., then sorted out the dependency problems - made sure that the "required dependencies" were satisfied first and that the versions matched.
 
Then I installed the Alsa driver first and then the HSFmodem pkg. Everything installed A-OK. I then forgot to configure HSFmodem (duh) and wondered why things appeared to not be there.
 
After configuring HSFmodem and testing to see if it would function, using Minicom, it seems fine - although this is the FREE version and is only 14K speed. Haven't paid my money ($20) and got the Key for 56K yet.
 
So I thank those who offered advice, my only comment would be that suggestions to "use Synaptic or apt-get" don't work if one does not already have an Internet connection, and to get online I first have to make the modem work - so good old "Catch-22". (I'm using a Windows computer to access this forum)
 
The bad news is that I now have a problem in that the sound card has stopped working and the system has NO sound at all, but I will start a new thread on that.

---

