---
title: "Install Tasque using Intrepid Repository in Hardy"
date: 2009-05-19
forum: Installation &amp; Upgrades
---

### Post by villalcalde84 on 2009-05-19
I like very much Tasque. I started using it in Ubuntu Intrepid Ibex with its latest version 0.1.8.

Now I'm back with Hardy Heron and the only version I found of Tasque for Ubuntu 8.04 is 0.1.7 (at Getdeb.net), but this one does not work very well.

Googling I discovered that there is a PPA for this program ([https://launchpad.net/~tasque-packagers/+archive/ppa]("https://launchpad.net/~tasque-packagers/+archive/ppa")), but the repository for Hardy just have the version 0.1.7.

I decided to try with the repository for Jaunty, which has the latest version, 0.1.8, but using it I have to install 32 updates. Is there a problem if I install the updates of all those packages, given that those are supposed to be for Jaunty, in order to be able to install Tasque?

Thanks in advance.

---

### Post by taurus on 2009-05-19
Not a good idea to add a repo for intrepid to your hardy.  Things could go wrong and usually do go wrong eventual.  If you want the latest version which is not available for hardy, you can always build it from source.  I assume this is the one that you are talking about.

[http://live.gnome.org/Tasque/Download](http://live.gnome.org/Tasque/Download)

Basically, you would run **./configure && make && sudo make checkinstall** to build a .deb package and install it on your machine.

---

### Post by villalcalde84 on 2009-05-19
Thanks for the advice, I will not use the repository and build it from source instead.

Just a few questions, for building it from source, do I have to download the .tar.gz package, unpack it and then in the Terminal use the commands you mentioned?

Do those commands install the program, or do they just make the .deb package so that I can then use it to install Tasque?

I am not very much skilled with CLI, so I appreciate your help.

Thanks.

---

### Post by taurus on 2009-05-19
When you click the link to download, it will save to your desktop as tasque-0.1.8.tar.gz.  Now, open a terminal and install the build-essential & checkinstall packages first.

```
cd ~/Desktop
sudo apt-get update
sudo apt-get install build-essential checkinstall
```
Then, unpack it and change to the new directory and build and install it.

```
tar xvzf tasque-0.1.8.tar.gz
cd tasque-0.1.8
./configure
make
sudo make checkinstall
```
If there is a problem with ./configure (missing libraries or something), you need to search for them using synaptic and install those missing libraries first before you can run the ./configure command again.  Don't run the last two commands, make && sudo make checkinstall, until ./configure has successfully run.

---

### Post by villalcalde84 on 2009-05-19
Thanks again for your quick answer. I'll do what you mentioned and then post the result.

Great forum.

---

### Post by villalcalde84 on 2009-05-19
Finally, I could install Tasque 0.1.8 in Hardy Heron from source with no problem. It is working great.

One last question, can I use the .deb package that is created if I reinstall Ubuntu, or in other computer?

Thanks.

---

