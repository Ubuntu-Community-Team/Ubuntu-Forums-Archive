---
title: "Unmet &amp; broken Dependencies after removing Kubuntu"
date: 2009-04-03
forum: Installation &amp; Upgrades
---

### Post by linux_burner on 2009-04-03
I was running Kubuntu on Ubuntu 8.10 till last evening and when I was in Ubuntu environment, the update manager showed me that 14 updates were available and it was all pertaining to KDE. So I logged into KDE and updated those. AFter I restarted and logged into Ubuntu, I noticed Kopete was removed. I tried to reinstall Kopete but I got some errors (sorry I do not remember now). And I tried to log into Kubuntu, I got an error saying it could not log me in. Since I do not use Kubuntu a lot, I decided to remove it. 

I used the command to remove ubuntu from this page: [http://www.psychocats.net/ubuntu/puregnome.php](http://www.psychocats.net/ubuntu/puregnome.php)

It removed KDE alright but along with a whole bunch of packages I had installed. I noticed Amarok, VLC, Skype etc uninstalled. I could install almost everything except Kopete. I noticed that there are bunch of unmet & breaking dependencies when I try to install Kopete. This is the error I get

sudo apt-get install kopete
Reading package lists... Done
Building dependency tree      
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  kopete: Depends: kdebase-runtime (>= 4:4.2.0) but it is not going to be installed
Depends: kdelibs5 (>= 4:4.1.96) but it is not going to be installed
          Depends: kdepimlibs5 (>= 4:4.2.2) but it is not going to be installed
          Depends: libmsn0.1 but it is not installable
E: Broken packages

And I tried again to install those packages above...this is what I get

vishak@Ubuntu-vishak:~$ sudo apt-get install kdelibs5
Reading package lists... Done
Building dependency tree      
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  kdelibs5: Depends: libstreamanalyzer0 (>= 0.6.3) but it is not going to be installed
            Depends: libstreams0 (>= 0.6.3) but it is not going to be installed
E: Broken packages

Its like running in a circle, I try to install one it says the other dependencies are broken and stuff...

I also tried sudo apt-get -f install and it did not help.

I am a newbie to Linux and not sure how to get Kopete up & running again. Any help on how to proceed would be appreciated a lot.
Thanks,
-Vishak

---

### Post by Ubuntiac on 2009-04-03
I just ran into this, too with an Intrepid update.

Looks like a packaging problem somewhere. Either the libstream dependencies are needed but not uploaded, or someone's put an incorrect version number in somewhere. Just trying to find out more about this myself at the moment... I'll let you know when I find something.

---

### Post by Ubuntiac on 2009-04-04
I've filed a bug [here]("https://bugs.launchpad.net/ubuntu/+source/kde4libs/+bug/354927") and it's been confirmed. There's a package in main with a dependency only available in backports. If you turn on backports (not recommended) it will fix this, but you'll get a bunch of other things "upgraded" to less tested, more unstable versions. Alternatively, now that it's been picked up and confirmed, there should be a version with fixed dependencies coming down the line. Just keep updating + upgrading and keep an eye on that bug report.

---

### Post by pickarooney on 2009-04-04
Where is that bug report as a matter of interest? I've enabled backports but don't want to leave them on for too long.

---

### Post by Ubuntiac on 2009-04-04
Oops. Sorry about that. I forgot to add the link. I've put it in the original post now, but just for clarity's sake it's:
[https://bugs.launchpad.net/ubuntu/+source/kde4libs/+bug/354927](https://bugs.launchpad.net/ubuntu/+source/kde4libs/+bug/354927)

---

