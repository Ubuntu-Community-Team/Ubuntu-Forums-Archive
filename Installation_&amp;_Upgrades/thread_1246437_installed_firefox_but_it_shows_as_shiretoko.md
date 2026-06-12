---
title: "installed firefox but it shows as shiretoko"
date: 2009-08-21
forum: Installation &amp; Upgrades
---

### Post by mmoalem on 2009-08-21
hi there all - tried to install firefox 3.5 on 9.04 (following this link:
[http://webupd8.blogspot.com/2009/06/firefox-35-rc-1-ubuntu-repository-deb.html](http://webupd8.blogspot.com/2009/06/firefox-35-rc-1-ubuntu-repository-deb.html))
but it changed my firefox to something called shiretoko and in the about it says it's 3.5.pre - i even tried to install now the 3.6 from synaptic but even thought it said that it installed correctly the command 'firefox' still opens shiretoko - WT*!?
besides the fact that it does not upgrade it is also not recognised by my bank's website as valid browser... please please help me sort this out

---

### Post by presence1960 on 2009-08-21
> **mmoalem said:**
> hi there all - tried to install firefox 3.5 on 9.04 (following this link:
[http://webupd8.blogspot.com/2009/06/firefox-35-rc-1-ubuntu-repository-deb.html](http://webupd8.blogspot.com/2009/06/firefox-35-rc-1-ubuntu-repository-deb.html))
but it changed my firefox to something called shiretoko and in the about it says it's 3.5.pre - i even tried to install now the 3.6 from synaptic but even thought it said that it installed correctly the command 'firefox' still opens shiretoko - WT*!?
besides the fact that it does not upgrade it is also not recognised by my bank's website as valid browser... please please help me sort this out
that **_IS_** the name of Firefox 3.5.
I used it briefly and my bank's site was able to be accessed by it. But I dumped it for lack of support for some of my extensions which became disabled in Shiretoko..

---

### Post by mmoalem on 2009-08-21
thanks for that - how did you remove it?
i figured i can access the installed firefox 3.6 with the command 'firefox-3.6' - dont get why is not a straight update to 3.5... anyway - it too isn't recognised by my bank - maybe it is because the browser reports itself as a different name??? - once i used an advice from this forum to get it to report as firefox rather than ubuntu but can't remeber how to do it...

---

### Post by kestal on 2009-08-21
> **mmoalem said:**
> thanks for that - how did you remove it?
i figured i can access the installed firefox 3.6 with the command 'firefox-3.6' - dont get why is not a straight update to 3.5... anyway - it too isn't recognised by my bank - maybe it is because the browser reports itself as a different name??? - once i used an advice from this forum to get it to report as firefox rather than ubuntu but can't remeber how to do it...

Shiretoko IS Firefox 3.5 but without the branding, as for anything Jaunty or before, the official firefox version is 3.0. Karmic will get a branded firefox 3.5 while firefox 3.6 will be named Namaroka.

While some plugins and other things may not work, its probably due to compatility of 3.5. If you check under Help, and About, you'll see that its actually version 3.5.2 (if you did it recently).

---

### Post by kestal on 2009-08-21
Double-post.

---

### Post by mmoalem on 2009-08-21
thanks - it says 3.5.3pre - the 'pre' i thought meant 'beta' and i though 3.5 was stable, got a bit confused with the lot :)

---

### Post by jherskow on 2009-08-25
im very confused, i just did an updat.
so now i have Shiretoko/3.5.3pre.
but this can't possibly be the stable versiona cuz i have that on my windows machine and it supports all the addons that are now not working on my ubuntu one..

can anyone help?

---

### Post by presence1960 on 2009-08-25
> **jherskow said:**
> im very confused, i just did an updat.
so now i have Shiretoko/3.5.3pre.
but this can't possibly be the stable versiona cuz i have that on my windows machine and it supports all the addons that are now not working on my ubuntu one..

can anyone help?

The windows version and the linux version are for different platforms. What works in one may not work in another. When I switched to Linux there were a few Firefox add-ons that didn't work in Linux, but worked in windows Firefox

---

### Post by spcwingo on 2009-08-25
> **mmoalem said:**
> once i used an advice from this forum to get it to report as firefox rather than ubuntu but can't remeber how to do it...

Open a tab in Shiretoko and in the address bar enter

```
about:config
```

In the search bar that it opens, search for shiretoko.  Now, that should yield a string named general.useragent.extra.firefox.  Double click that and change it from Shiretoko/3.5.3pre to Firefox/3.5.3pre.

---

### Post by jherskow on 2009-08-26
so how do i get rid of it and change it back to the old firefox without losing my data
??

---

### Post by presence1960 on 2009-08-26
> **jherskow said:**
> so how do i get rid of it and change it back to the old firefox without losing my data
??

Go in syanaptic and mark for removal firefox 3.5, firefox 3.5 branding & firefox 3.5 gnome-support. Then mark for installation the same things firefox 3.0

---

### Post by jherskow on 2009-08-27
that just stopped Firefox from working altogether, so i re-installed them, so im back at sq.1

---

### Post by wojox on 2009-08-27
Look here:

[http://ubuntuforums.org/showthread.php?t=1193567](http://ubuntuforums.org/showthread.php?t=1193567)

---

### Post by jherskow on 2009-08-27
that's a really big and long page, my friend.

could you direct me to the part i need please?

---

### Post by ebell on 2009-08-28
I had the same problem, have Ubuntu 9.04 and upgraded to Firefox 3.5 Shiretoko.  It started locking up and when closing would not.  The way I fixed it was:

Opened a terminal window and edited the sources.list
sudo gedit /etc/apt/sources.list

Look for the two lines below and comment them out by placing 2 ## in front of the signs as shown above.  Save the sources.list file.

##deb [http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu) jaunty main 
##deb-src [http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu) jaunty main

Back to the terminal window and type
sudo apt-get clean 
This removes any cached package files that was downloaded when Shiretoko was installed.

run
sudo apt-get update
This will ensure the latest updates are installed.

Open Synaptic Package manager and removed any reference to Firefox.  

Back to the Terminal window and type the following:

sudo apt-get install firefox-3.0

Firefox was restored to 3.0.13

---

