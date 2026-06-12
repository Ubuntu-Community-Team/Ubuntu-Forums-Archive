---
title: "Tor install ( not sure how)"
date: 2009-11-02
forum: Installation &amp; Upgrades
---

### Post by shadowlands on 2009-11-02
Any one willing to break this down in to a dummies guide or provide me with a link to better directions.

TOR
tor is no longer in the ubuntu repos, and the noreply.org repo may not work due to dependencies no longer in karmic. The following method uses an unofficial PPA to install tor. Please read the tor project page carefully before using tor, as there are additional setup requirements for effective use:
[http://www.torproject.org/docs/debian.html.en](http://www.torproject.org/docs/debian.html.en)

And the PPA homepage:
[https://launchpad.net/~sevenmachines/+archive/tor](https://launchpad.net/~sevenmachines/+archive/tor)

Run with sudo...

Code:

#!/bin/bash
# must be run with sudo
# Install tor
torsrc="deb [http://ppa.launchpad.net/sevenmachines/tor/ubuntu](http://ppa.launchpad.net/sevenmachines/tor/ubuntu) karmic main"
torkey=61E46227
torprint=454FEDB228E1455D687C9CBE35DA01C261E46227
# See [https://launchpad.net/~sevenmachines/+archive/tor](https://launchpad.net/~sevenmachines/+archive/tor)
# See [http://www.torproject.org/docs/debian.html.en](http://www.torproject.org/docs/debian.html.en)
test=`grep "$torsrc" /etc/apt/sources.list`
if [ "$test" = "" ]; then
	echo "$torsrc" >> /etc/apt/sources.list
fi
gpg --keyserver keys.gnupg.net --recv $torkey
gpg --export $torprint | sudo apt-key add -
apt-get update
apt-get install tor tor-geoipdb tsocks

Additional info on tor availability in karmic:
[http://ubuntuforums.org/archive/inde...t-1153938.html](http://ubuntuforums.org/archive/inde...t-1153938.html)

---

### Post by zvacet on 2009-11-02
Did you tried as described on launchpad link you posted?Go to the system<admin>software sources>third party repos and add 

```
deb http://ppa.launchpad.net/sevenmachines/tor/ubuntu karmic main 
```

Reload.In terminal type

```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 61E46227
```

After that you should be able to find **tor** in synaptic and install it.

---

### Post by shadowlands on 2009-11-02
thanks


 > **zvacet said:**
> Did you tried as described on launchpad link you posted?Go to the system<admin>software sources>third party repos and add 

```
deb http://ppa.launchpad.net/sevenmachines/tor/ubuntu karmic main 
```

Reload.In terminal type

```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 61E46227
```

After that you should be able to find **tor** in synaptic and install it.

---

### Post by EJeanmaire on 2009-11-02
Or you could just download the source code and compile it, I had no issues compiling for Karmic.

---

### Post by shadowlands on 2009-11-02
I have it up and working!! My next question is is ther any thing else I need to do to insure it is installed and working correctly?
> **EJeanmaire said:**
> Or you could just download the source code and compile it, I had no issues compiling for Karmic.

---

### Post by shadowlands on 2009-11-02
I have it up and working!! My next question is is there any thing else I need to do to insure it is installed and working correctly?

I did step two and step three. 
> **EJeanmaire said:**
> Or you could just download the source code and compile it, I had no issues compiling for Karmic.

---

### Post by shadowlands on 2009-11-02
When using the foxfire extension, how do you get to pages that are blocked because of Java, like cnn,  and live journal.

---

### Post by EJeanmaire on 2009-11-04
> **shadowlands said:**
> When using the foxfire extension, how do you get to pages that are blocked because of Java, like cnn,  and live journal.

Java can be used to release identifiable information about you; thus defeating the purpose of Tor.... i.e. turn it off for Java.

---

### Post by EJeanmaire on 2009-11-04
> **shadowlands said:**
> I have it up and working!! My next question is is there any thing else I need to do to insure it is installed and working correctly?

I did step two and step three.

You need to install Polipo
'sudo apt-get install polipo'
you need to replace the conf file in /etc/polipo to the one specified on the Tor site.

Then get Vidalia...  'sudo apt-get install vidalia'

Then get Tor-button for Firefox

---

### Post by stderr on 2009-11-04
> **shadowlands said:**
> My next question is is there any thing else I need to do to insure it is installed and working correctly?

If you've got Tor set up and running, and are using a Tor extension in Firefox, and have it enabled, then just go to [https://check.torproject.org/]("https://check.torproject.org/"). Alternatively, visit a website that echoes your IP address back to you (such as [http://www.ip-adress.com/]("http://www.ip-adress.com/")): when using Tor, the IP address you see will be the IP of the exit node on the Tor network, not your own IP. So, if you remember your original IP address, you'll see that it doesn't match your reported IP, and (chances are) the location it gives will be a long way away from your actual location.

---

### Post by shadowlands on 2009-11-07
That is so KOOL !  > **stderr said:**
> If you've got Tor set up and running, and are using a Tor extension in Firefox, and have it enabled, then just go to [https://check.torproject.org/]("https://check.torproject.org/"). Alternatively, visit a website that echoes your IP address back to you (such as [http://www.ip-adress.com/]("http://www.ip-adress.com/")): when using Tor, the IP address you see will be the IP of the exit node on the Tor network, not your own IP. So, if you remember your original IP address, you'll see that it doesn't match your reported IP, and (chances are) the location it gives will be a long way away from your actual location.

---

