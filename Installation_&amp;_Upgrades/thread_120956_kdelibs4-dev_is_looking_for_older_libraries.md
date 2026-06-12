---
title: "kdelibs4-dev is looking for older libraries"
date: 2006-01-23
forum: Installation &amp; Upgrades
---

### Post by Jucato on 2006-01-23
Hi guys, I need help pretty badly.

I'm a bit new to linux in general (only started with Kubuntu 2 weeks ago). Anyway, I'm trying to install the kde-devel package so that I could compile the KSplash Moodin Engine. When I tried to use Adept/Kpackage, I couldn't install because it will break packages. So I turned to apt-get instead. However, I couldn't install because of the same reason. After much snooping around, this is what I concluded.

1. Moodin Engine needs kde-devel, so I tried installing that:
```

fenyx@fenyx:~$ sudo apt-get install kde-devel
Password:
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
  kde-devel: Depends: kdesdk but it is not going to be installed
             Depends: libartsc0-dev but it is not going to be installed
             Depends: libarts1-dev but it is not going to be installed
             Depends: kdelibs4-dev but it is not going to be installed
 **            Depends: kdebase-dev but it is not going to be installed**
             Depends: libkonq4-dev but it is not going to be installed
E: Broken packages
```

2. Seeing that I need kdebase-dev (i have kdebase installed), I tried installing it, too:
```
fenyx@fenyx:~$ sudo apt-get install kdebase-dev
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
  kdebase-dev: Depends: kate (= 4:3.4.3-0ubuntu6) but 4:3.5.0-0ubuntu0breezy1 is to be installed
               Depends: kdesktop (= 4:3.4.3-0ubuntu6) but 4:3.5.0-0ubuntu0breezy1 is to be installed
               Depends: kicker (= 4:3.4.3-0ubuntu6) but 4:3.5.0-0ubuntu0breezy1 is to be installed
               Depends: konqueror-nsplugins (= 4:3.4.3-0ubuntu6) but 4:3.5.0-0ubuntu0breezy1 is to be installed
               Depends: konqueror (= 4:3.4.3-0ubuntu6) but 4:3.5.0-0ubuntu0breezy1 is to be installed
               Depends: ksysguard (= 4:3.4.3-0ubuntu6) but 4:3.5.0-0ubuntu0breezy1 is to be installed
               Depends: kwin (= 4:3.4.3-0ubuntu6) but 4:3.5.0-0ubuntu0breezy1 is to be installed
              [B] Depends: kdelibs4-dev (>= 4:3.4.1) but it is not going to be installed
[/B]E: Broken packages
```

3. Comparing the two tests, I realize that kdelibs4-dev is a common factor, so I tried to install that:

```
fenyx@fenyx:~$ sudo apt-get install kdelibs4-dev
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
  kdelibs4-dev: [B]Depends: kdelibs4c2 (= 4:3.4.3-0ubuntu2) but 4:3.5.0-0ubuntu0breezy2 is to be installed
                Depends: kdelibs-bin (= 4:3.4.3-0ubuntu2) but 4:3.5.0-0ubuntu0breezy2 is to be installed[/B]
                Depends: libarts1-dev (>= 1.4.0) but it is not going to be installed
                Depends: libqt3-mt-dev (>= 3.3.3) but it is not going to be installed
                **Depends: libxrender-dev but it is not going to be installed**
E: Broken packages
```

4. I recognized the libxrender package and wondered what was wrong, so I tried to install it:

```
fenyx@fenyx:~$ sudo apt-get install libxrender-dev
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
  libxrender-dev: **Depends: libxrender1 (= 1:0.9.0-1) but 1:0.9.0.2-1 is to be installed**
E: Broken packages
```

That's when I realized what could be happening. Earlier (yesterday actually), I installed an upgraded version of the GIMP (2.2.10, the one in the repos is 2.2.8). In order to do that, I had to install a newer version of libxrender1 and some other libraries. I also upgraded to KDE 3.5. Now my problem is that kdelibs4-dev is still looking for the older versions, and I can't uninstall those libraries because all other GNOME apps are now dependant on it.

What should I do? Could anyone help please? It's not the I need Moodin so much, but I'm anticipating similar problems if I try to compile other Qt-based apps?

Thanks for any help! :)

---

### Post by stanz on 2006-04-05
I jus' installed this moodin and it works outta the box!
I get the same depends as u got, this avoided it all.
Gimp should still work...if you do no more upgradin`!?

Search Synaptic, use backports,

deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse
 
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse

[I]**ksplash-engine-moodin:**
Fading KDE splash screen engine: This KDE splash screen engine is based upon Linspire's engine by Sean Meiners <Sean.Meiners@LinspireInc.com>
Homepage: [http://www.kde-look.org/content/show.php?content=25705](http://www.kde-look.org/content/show.php?content=25705)

[/I]I Hope this is a help....months later ~~

---

