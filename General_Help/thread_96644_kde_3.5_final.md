---
title: "kde 3.5 final?"
date: 2005-11-29
forum: General Help
---

### Post by Digitallysick on 2005-11-29
how to i upgrade to this?? I think its final now!

---

### Post by ofek on 2005-11-29
I think you should probably wait until ubuntu builds a .deb package for it or upgrade the kubuntu-desktop to 3.5.
Compiling kde by yourself should be possible but it isn't such an easy task.

---

### Post by Wizzard on 2005-11-29
Check out the other topics or this guide [http://kubuntu.org/announcements/kde-35.php](http://kubuntu.org/announcements/kde-35.php)

---

### Post by linbetwin on 2005-11-29
What version of KDE does Kubuntu 5.10 have now? I'd like to try KDE by installing kubuntu-desktop on my Ubuntu system, but I've seen KDE 3.4.2 in SUSE 10.0, and the accessibility support (specifically the kmag magnifier) wasn't much better than in GNOME. I'm hoping KDE 3.5 will have some improvements in this area. Does anyone have any idea when will KDE 3.5 be available in the Ubuntu repos?

---

### Post by tikal26 on 2005-11-29
KDE 3.5 has been released. You can download the KDE packages from any of these sources (add to /etc/apt/sources.list):

These packages have been digitally signed using Jonathan Riddell's key. A copy of they key is also kept on people.ubuntu.com for verification. To add this key do:

 wget [http://people.ubuntu.com/~jriddell/kubuntu-packages-jriddell-key.gpg](http://people.ubuntu.com/~jriddell/kubuntu-packages-jriddell-key.gpg)
 sudo apt-key add kubuntu-packages-jriddell-key.gpg

Kubuntu 5.10 (Breezy)

    * deb [http://kubuntu.org/packages/kde35](http://kubuntu.org/packages/kde35) breezy main

These packages are available for i386 and amd64.

The packages are being uploaded to Dapper, many packages in Dapper are currently uninstallable due to a c++ transition.

---

### Post by bugi on 2005-11-29
[QUOTE=ofek]Compiling kde by yourself should be possible but it isn't such an easy task.[/QUOTE]

There is also very nice tool for building KDE as normal user, it is **Konstruct**.
[http://developer.kde.org/build/konstruct/](http://developer.kde.org/build/konstruct/)

You don't have to be root or use sudo to build it, and it even doesn't mess the current installation of KDE.

---

### Post by riskbreaker927 on 2005-11-29
Tikal, will the method you described allow me to install KDE 3.5 on a system that didn't have KDE to begin with?

---

### Post by tikal26 on 2005-11-29
I don't know. I think that you could install the base system and then you could install the kubuntu-desktop and since you have the new repo it would install the latest. I don't know what you mean by a system that doesn't have kde. Are you installing from scratch or do you have ubuntu alreay? if you have ubuntu alreay it should just install the latest packages.

---

### Post by GameManK on 2005-11-29
upgraded :) from rc1

looks like administrator mode button works now!

---

### Post by cron0 on 2005-11-29
[QUOTE=tikal26]KDE 3.5 has been released. You can download the KDE packages from any of these sources (add to /etc/apt/sources.list):

These packages have been digitally signed using Jonathan Riddell's key. A copy of they key is also kept on people.ubuntu.com for verification. To add this key do:

 wget [http://people.ubuntu.com/~jriddell/kubuntu-packages-jriddell-key.gpg](http://people.ubuntu.com/~jriddell/kubuntu-packages-jriddell-key.gpg)
 sudo apt-key add kubuntu-packages-jriddell-key.gpg

Kubuntu 5.10 (Breezy)

    * deb [http://kubuntu.org/packages/kde35](http://kubuntu.org/packages/kde35) breezy main

These packages are available for i386 and amd64.

The packages are being uploaded to Dapper, many packages in Dapper are currently uninstallable due to a c++ transition.[/QUOTE]

Is there any way to install it under Dapper without waiting for the repos. to sync? (except for konstruct)

I inserted the kubuntu repos. in my sources.list but it still gives me unresolvables dependencies.

TIA
cron0

---

### Post by Alpha_toxic on 2005-11-29
Does anyone know when should this baby show up in the repositorys??

---

### Post by SeanTater on 2005-11-29
So -- I hate to be dumb -- but I just add the repository and press safe upgrade -- then press commit changes? I don't like to take chances...

---

### Post by Alpha_toxic on 2005-11-29
ops, sorry it's actually there... didn't see it the first time :oops:

---

### Post by daller on 2005-11-29
[QUOTE=Alpha_toxic]Does anyone know when should this baby show up in the repositorys??[/QUOTE]

It will be included in the dapper repos, but I don't think it'll be in Breezy - Unless the backporting team does something...

What's so hard about adding "deb [http://kubuntu.org/packages/kde35](http://kubuntu.org/packages/kde35) breezy main" ???

---

### Post by raggamuffin on 2005-11-29
installed in only a few minutes and is working fine...

for the people still unclear on the process...

step #1... update your apt keys and sources, as described at [http://kubuntu.org/announcements/kde-35.php...](http://kubuntu.org/announcements/kde-35.php)

step #2....sudo apt-get update && sudo apt-get upgrade ...

step #3...that's it =)...

---

### Post by riskbreaker927 on 2005-11-29
Tikal, I'm running Ubuntu with Gnome 2.12. KDE is not installed on this computer. It seems to me that the instructions you gave only apply to people already running KDE... but I wasn't sure.

So should I just install the Kubuntu-desktop package and then try what you said?

---

### Post by tikal26 on 2005-11-29
yeah I would probably do that after I include the repo in synaptic and that would install the latest pakages

---

### Post by Digitallysick on 2005-11-29
Im running kde 3.5 now, it has some minor improvements, well worth the upgrade i would say, seems just as stable as always to me, and i even like the new theme it comes with, good deal

---

### Post by elglas on 2005-11-29
when I follow those instructions I get 
```
W: Couldn't stat source package list http://kubuntu.org breezy/main Packages (/var/lib/apt/lists/kubuntu.org_packages_kde35_dists_breezy_main_binary-i386_Packages) - stat (2 No such file or directory)
```
any idea of what is incorrect?

---

### Post by cron0 on 2005-11-29
```
cron0@ubuntujf:~$ sudo apt-get install kubuntu-desktop
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  kubuntu-desktop: Depends: adept but it is not going to be installed
                   Depends: akode but it is not installable
                   Depends: akregator but it is not going to be installed
                   Depends: amarok but it is not going to be installed
                   Depends: ark but it is not going to be installed
                   Depends: gtk2-engines-gtk-qt but it is not going to be installed
                   Depends: gwenview but it is not going to be installed
                   Depends: k3b but it is not going to be installed
                   Depends: kaddressbook but it is not going to be installed
                   Depends: kaffeine-gstreamer but it is not going to be installed
                   Depends: kamera but it is not going to be installed
                   Depends: karm but it is not going to be installed
                   Depends: katapult but it is not going to be installed
                   Depends: kate but it is not going to be installed
                   Depends: kaudiocreator but it is not going to be installed
                   Depends: kcontrol but it is not going to be installed
                   Depends: kcron but it is not going to be installed
                   Depends: kde-guidance but it is not going to be installed
                   Depends: kde-systemsettings but it is not going to be installed
                   Depends: kdeadmin-kfile-plugins but it is not going to be installed
                   Depends: kdebase-kio-plugins but it is not going to be installed
                   Depends: kdebluetooth but it is not going to be installed
                   Depends: kdegraphics-kfile-plugins but it is not going to be installed
                   Depends: kdemultimedia-kappfinder-data but it is not going to be installed
                   Depends: kdemultimedia-kfile-plugins but it is not going to be installed
                   Depends: kdemultimedia-kio-plugins but it is not going to be installed
                   Depends: kdenetwork-filesharing but it is not going to be installed
                   Depends: kdenetwork-kfile-plugins but it is not going to be installed
                   Depends: kdepasswd but it is not going to be installed
                   Depends: kdepim-kio-plugins but it is not going to be installed
                   Depends: kdepim-wizards but it is not going to be installed
                   Depends: kdeprint but it is not going to be installed
                   Depends: kdesktop but it is not going to be installed
                   Depends: kdm but it is not going to be installed
                   Depends: kfind but it is not going to be installed
                   Depends: kghostview but it is not going to be installed
                   Depends: khelpcenter but it is not going to be installed
                   Depends: kicker but it is not going to be installed
                   Depends: kio-apt but it is not going to be installed
                   Depends: kio-locate but it is not going to be installed
                   Depends: klaptopdaemon but it is not going to be installed
                   Depends: klipper but it is not going to be installed
                   Depends: kmail but it is not going to be installed
                   Depends: kmenuedit but it is not going to be installed
                   Depends: kmilo but it is not going to be installed
                   Depends: kmix but it is not going to be installed
                   Depends: knetworkconf but it is not going to be installed
                   Depends: knotes but it is not going to be installed
                   Depends: konq-plugins but it is not going to be installed
                   Depends: konqueror but it is not going to be installed
                   Depends: konqueror-nsplugins but it is not going to be installed
                   Depends: konserve but it is not going to be installed
                   Depends: konsole but it is not going to be installed
                   Depends: kontact but it is not going to be installed
                   Depends: konversation but it is not going to be installed
                   Depends: kooka but it is not going to be installed
                   Depends: kopete but it is not going to be installed
                   Depends: korganizer but it is not going to be installed
                   Depends: kpdf but it is not going to be installed
                   Depends: kpf but it is not going to be installed
                   Depends: kppp but it is not going to be installed
                   Depends: krdc but it is not going to be installed
                   Depends: krfb but it is not going to be installed
                   Depends: krita but it is not going to be installed
                   Depends: kscd but it is not going to be installed
                   Depends: kscreensaver but it is not going to be installed
                   Depends: ksmserver but it is not going to be installed
                   Depends: ksnapshot but it is not going to be installed
                   Depends: ksplash but it is not going to be installed
                   Depends: ksvg but it is not going to be installed
                   Depends: ksysguard but it is not going to be installed
                   Depends: ksystemlog but it is not going to be installed
                   Depends: kubuntu-default-settings but it is not going to be installed
                   Depends: kubuntu-docs but it is not going to be installed
                   Depends: kubuntu-konqueror-shortcuts but it is not going to be installed
                   Depends: kuser but it is not going to be installed
                   Depends: kwalletmanager but it is not going to be installed
                   Depends: kwifimanager but it is not going to be installed
                   Depends: kwin but it is not going to be installed
                   Depends: openoffice.org2-kde but it is not going to be installed
E: Broken packages
cron0@ubuntujf:~$
```

Any ideas? I've heard about dep. problems under Dapper but I am wondering if anybody got it working under Dapper?

I guess I must wait for the dependencies to be updated..

cron0

---

### Post by tikal26 on 2005-11-29
cron0 
this is what i read about drapper
The packages are being uploaded to Dapper, many packages in Dapper are currently uninstallable due to a c++ transition

and I am just wondering why are you using drapper and nor breezy

---

### Post by cron0 on 2005-11-30
[QUOTE=tikal26]cron0 
and I am just wondering why are you using drapper and nor breezy[/QUOTE]

I thought that using Dapper would provide with more up-to-date packages, newer versions, newer features, etc. Isn't that's the case?

I came a few month ago from being a Gentoo user, I'm used to bleeding edge stuff and that's kinda what I'm looking for. Breezy doesn't have all the newest goodies and software versions like Dapper does, right?

cron0

---

### Post by DoeRayMe on 2005-11-30
thats right, Dapper has all the latest packages, Breezy does'nt

---

### Post by daller on 2005-11-30
[QUOTE=DoeRayMe]thats right, Dapper has all the latest packages, Breezy does'nt[/QUOTE]

CAUTION: Dapper is in early development!

Dapper is going into a really unstable state, while the c++ transition takes place...

Please take care when upgrading (or wait a month or two before upgrading again!)

Do NOT use dapper on your main workstation!

---

### Post by tikal26 on 2005-11-30
ohh I see that you are a former gentoo user. so you should be finei was just wondering beuse I noticed that you were new and wonder if you were a true newbie and was worry that maybe using drapper would brake your system or something would not work and you would not know that drapper wasbleeding edge stuff and that it could brake your system.

---

### Post by cron0 on 2005-11-30
[QUOTE=tikal26]ohh I see that you are a former gentoo user. so you should be finei was just wondering beuse I noticed that you were new and wonder if you were a true newbie and was worry that maybe using drapper would brake your system or something would not work and you would not know that drapper wasbleeding edge stuff and that it could brake your system.[/QUOTE]

Yeah no problems, I'm kinda used to broken stuff ;-)

---

### Post by natzz on 2006-02-03
i did the change to kde from ubuntu and now im wondering if theres any other repositorys that need to be added for security and updates my current repository has still got alot of the ubuntu stuff ....should it all be kubuntu repositorys now ?
thanks

---

### Post by chiisu on 2006-02-04
I added the source and downloaded the packages, however I'm still running 3.4.3 :confused: I've done the same thing to update Amarok to 1.3.8 and that worked ok...

edit: I retried using "apt-get update" and "apt-get upgrade" and here is what it says.....

The following packages have been kept back:
  akregator ark artsbuilder kaddressbook kamera kappfinder karm kate
  kaudiocreator kcontrol kcron kdeadmin-kfile-plugins kdebase-bin
  kdebase-kio-plugins kdegraphics-kfile-plugins kdelibs-bin kdelibs4c2
  kdemultimedia-kfile-plugins kdemultimedia-kio-plugins kdenetwork-filesharing
  kdenetwork-kfile-plugins kdepasswd kdepim-kio-plugins kdepim-wizards
  kdeprint kdesktop kdm kfind kghostview khelpcenter kicker klaptopdaemon
  klipper kmenuedit kmilo kmix knetworkconf knotes konq-plugins konqueror
  konqueror-nsplugins konsole kontact kooka kopete korganizer kpdf kpf kppp
  krdc krfb kscd kscreensaver ksmserver ksnapshot ksplash ksvg kuser
  kwalletmanager kwifimanager kwin libkcddb1 libkonq4 libkpimexchange1
  libkpimidentities1 libkscan1 libksieve0 libktnef1
0 upgraded, 0 newly installed, 0 to remove and 68 not upgraded.

---

### Post by NeoChaosX on 2006-02-04
Do **sudo apt-get dist-upgrade**. Those held-back packages require new dependencies, and a normal upgrade doesn't download new package dependencies, only a dist-upgrade can do so.

---

### Post by chiisu on 2006-02-04
I get the same error message when doing "apt-get dist-upgrade"  :(

---

### Post by NeoChaosX on 2006-02-04
Paste the content of your /etc/apt/sources.list file, then.

---

### Post by chiisu on 2006-02-04
After I uncommented the other sources in my sources.list file, it sucessfully updated to KDE 3.5.1.  I didn't know the packages in Universe/Multiverse/Backports were required......

---

