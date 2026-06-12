---
title: "Conflicts after Upgrading"
date: 2009-11-05
forum: Installation &amp; Upgrades
---

### Post by larry on 2009-11-05
Dear All,
I have just upgraded to 9.10, but I am experiencing some problems. 

I cannot watch youtube videos any longer. Firefox says that either I have javascript turned off or an old version of of Adobe's Flash Player.
This is the output of a few things I tried

$ sudo apt-get install sun-java6-jre sun-java6-plugin
Reading package lists... Done
Building dependency tree       
Reading state information... Done
sun-java6-jre is already the newest version.
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  sun-java6-plugin: Depends: sun-java6-bin (= 6-15-1) but 6-16-0ubuntu1.9.04 is to be installed
E: Broken packages

Furthermore, this is what happens when I try to install the flashplugin

$ sudo apt-get install adobe-flashplugin
Reading package lists... Done
Building dependency tree       
Reading state information... Done

but according to the guide
[http://ubuntuguide.org/wiki/Ubuntu:Karmic#restricted_extras](http://ubuntuguide.org/wiki/Ubuntu:Karmic#restricted_extras)
I should simply need to install the restricted extras

$ sudo apt-get install ubuntu-restricted-extras
Reading package lists... Done
Building dependency tree       
Reading state information... Done
ubuntu-restricted-extras is already the newest version.

which look OK on my system and this puzzles me.
My repos are 
$ cat /etc/apt/sources.list

##JAUNTY SUPPORTED
deb [http://ch.archive.ubuntu.com/ubuntu/](http://ch.archive.ubuntu.com/ubuntu/) karmic main restricted
deb-src [http://ch.archive.ubuntu.com/ubuntu/](http://ch.archive.ubuntu.com/ubuntu/) karmic main restricted

##JAUNTY SUPPORTED - UPDATES
deb [http://ch.archive.ubuntu.com/ubuntu/](http://ch.archive.ubuntu.com/ubuntu/) karmic-updates main restricted
deb-src [http://ch.archive.ubuntu.com/ubuntu/](http://ch.archive.ubuntu.com/ubuntu/) karmic-updates main restricted

##JAUNTY SUPPORTED - PROPOSED
deb [http://ch.archive.ubuntu.com/ubuntu/](http://ch.archive.ubuntu.com/ubuntu/) karmic-proposed main restricted
deb-src [http://ch.archive.ubuntu.com/ubuntu/](http://ch.archive.ubuntu.com/ubuntu/) karmic-proposed main restricted

##JAUNTY SUPPORTED - SECURITY
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) karmic-security main restricted
deb-src [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) karmic-security main restricted

##JAUNTY COMMUNITY SUPPORTED
deb [http://ch.archive.ubuntu.com/ubuntu/](http://ch.archive.ubuntu.com/ubuntu/) karmic universe multiverse
deb-src [http://ch.archive.ubuntu.com/ubuntu/](http://ch.archive.ubuntu.com/ubuntu/) karmic universe multiverse

##JAUNTY COMMUNITY SUPPORTED - UPDATES
deb [http://ch.archive.ubuntu.com/ubuntu/](http://ch.archive.ubuntu.com/ubuntu/) karmic-updates universe multiverse
deb-src [http://ch.archive.ubuntu.com/ubuntu/](http://ch.archive.ubuntu.com/ubuntu/) karmic-updates universe multiverse

##JAUNTY COMMUNITY SUPPORTED - PROPOSED
deb [http://ch.archive.ubuntu.com/ubuntu/](http://ch.archive.ubuntu.com/ubuntu/) karmic-proposed universe multiverse
deb-src [http://ch.archive.ubuntu.com/ubuntu/](http://ch.archive.ubuntu.com/ubuntu/) karmic-proposed universe multiverse

##JAUNTY COMMUNITY SUPPORTED - SECURITY
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) karmic-security universe multiverse
deb-src [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) karmic-security universe multiverse


##JAUNTY BACKPORTS
deb [http://ch.archive.ubuntu.com/ubuntu/](http://ch.archive.ubuntu.com/ubuntu/) karmic-backports main restricted universe multiverse
deb-src [http://ch.archive.ubuntu.com/ubuntu/](http://ch.archive.ubuntu.com/ubuntu/) karmic-backports main restricted universe multiverse

##MEDIBUNTU
 deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) karmic free non-free # disabled on upgrade to karmic
 deb-src [http://packages.medibuntu.org/](http://packages.medibuntu.org/) karmic free non-free # disabled on upgrade to karmic

##CANONICAL
deb [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) karmic partner

and they were automatically updated. Is there anything wrong with them?

I am also experiencing problems with my wireless internet connection and with the screen brightness on my laptop, but I believe this post is already long enough  ;) .
Many thanks

larry

---

### Post by larry on 2009-11-06
I am a bit puzzled: skype is failing as well
From the guide
[http://ubuntuguide.org/wiki/Ubuntu:Karmic#Skype](http://ubuntuguide.org/wiki/Ubuntu:Karmic#Skype)

$ wget -O skype_ubuntu-2.0.0.72-1_amd64.deb [http://www.skype.com/go/getskype-linux-ubuntu-amd64](http://www.skype.com/go/getskype-linux-ubuntu-amd64)
--2009-11-06 09:37:44--  [http://www.skype.com/go/getskype-linux-ubuntu-amd64](http://www.skype.com/go/getskype-linux-ubuntu-amd64)
Resolving [www.skype.com](www.skype.com)... 78.141.177.7
Connecting to [www.skype.com|78.141.177.7|:80](www.skype.com|78.141.177.7|:80)... connected.
HTTP request sent, awaiting response... 302 Found
Location: [http://www.skype.com/download/](http://www.skype.com/download/) [following]
--2009-11-06 09:37:45--  [http://www.skype.com/download/](http://www.skype.com/download/)
Reusing existing connection to [www.skype.com:80](www.skype.com:80).
HTTP request sent, awaiting response... 302 Found
Location: [http://www.skype.com/go/download](http://www.skype.com/go/download) [following]
--2009-11-06 09:37:45--  [http://www.skype.com/go/download](http://www.skype.com/go/download)
Reusing existing connection to [www.skype.com:80](www.skype.com:80).
HTTP request sent, awaiting response... 302 Found
Location: [http://www.skype.com/intl/en/download/skype/windows/](http://www.skype.com/intl/en/download/skype/windows/) [following]
--2009-11-06 09:37:45--  [http://www.skype.com/intl/en/download/skype/windows/](http://www.skype.com/intl/en/download/skype/windows/)
Reusing existing connection to [www.skype.com:80](www.skype.com:80).
HTTP request sent, awaiting response... 200 OK
Length: unspecified [text/html]
Saving to: `skype_ubuntu-2.0.0.72-1_amd64.deb'

    [ <=>                                               ] 16,127      90.5K/s   in 0.2s    

2009-11-06 09:37:45 (90.5 KB/s) - `skype_ubuntu-2.0.0.72-1_amd64.deb' saved [16127]

$ sudo dpkg -i skype_ubuntu-2.0.0.72-1_amd64.deb
[sudo] password for lorenzo: 
dpkg-deb: `skype_ubuntu-2.0.0.72-1_amd64.deb' is not a debian format archive
dpkg: error processing skype_ubuntu-2.0.0.72-1_amd64.deb (--install):
 subprocess dpkg-deb --control returned error exit status 2
Errors were encountered while processing:
 skype_ubuntu-2.0.0.72-1_amd64.deb


So, I did not download a valid debian package!?
Can anyone give me a hand?
Cheers

Lorenzo

---

### Post by Ilalmi on 2009-11-06
Concerning your skype-problem: 
The link you used is broken. Your wget got an HTML-page and saved that as a deb-file. Try the following:
```
wget http://www.skype.com/go/getskype-linux-beta-ubuntu-64
```

---

### Post by Ilalmi on 2009-11-06
Concerning firefox:
I can't help you on your java-problem, sorry. But you don't need java to watch flash-movies in firefox. 
The package you have to install is called "flashplugin-installer". This will download the Adobe flash plugin from Adobe's website and install it.

I hope this solves your problems.

---

### Post by larry on 2009-11-06
> **Ilalmi said:**
> Concerning firefox:
I can't help you on your java-problem, sorry. But you don't need java to watch flash-movies in firefox. 
The package you have to install is called "flashplugin-installer". This will download the Adobe flash plugin from Adobe's website and install it.

I hope this solves your problems.

OK, thanks for your suggestions, but it does not work.
I am rather annoyed: my laptop is still up and running, but so many little things ended up broken after this upgrade...
Hope I will be able to fix them.
Cheers

larry

---

### Post by rforums on 2009-11-06
i am also getting the same error..
"The following packages have unmet dependencies:
  sun-java6-jdk: Depends: sun-java6-bin (= 6-15-1) but 6-16-0ubuntu1.9.04 is to be installed
E: Broken packages"
but i was trying to install java jdk. I also upgraded from 9.04.
Any suggestions?

---

### Post by jmuzz on 2009-11-07
See here
[http://ubuntuforums.org/showthread.php?t=1305603](http://ubuntuforums.org/showthread.php?t=1305603)

Basically you just need to uninstall the old version:
sudo apt-get remove sun-java6-jre sun-java6-plugin sun-java6-bin sun-java6-fonts
sudo apt-get autoremove

Then it should be right to reinstall the java packages.

---

