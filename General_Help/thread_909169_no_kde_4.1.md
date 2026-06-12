---
title: "no kde 4.1?"
date: 2008-09-03
forum: General Help
---

### Post by moore.bryan on 2008-09-03
i had a fresh install of ubuntu on a hand-me-down imac (ppc) and wanted to install kubuntu along-side. so, i head over to the kde 4.1 instructions for ubuntu [here]("http://www.kubuntu.org/news/kde-4.1"), add the correct repo (deb [http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu](http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu) hardy main), and run [code]sudo aptitude update && sudo aptitude install kubuntu-kde4-desktop. voila, kde **4.0**. wait; huh? **4.0**? but i followed the guide for **4.1**!

and that is where i now stand.

---

### Post by arch0njw on 2008-09-04
Try "*sudo apt-get install kdebase-kde[I]4 kdeplasma-addons*[/I]". 

Also, is this at the top of the sources.list file?  I typically add extra repositories before the standard ones.

---

### Post by moore.bryan on 2008-09-04
> **arch0njw said:**
> Try "*sudo apt-get install kdebase-kde[I]4 kdeplasma-addons*[/I]".
i'll try this when i get home; thanks...
> Also, is this at the top of the sources.list file?  I typically add extra repositories before the standard ones.
afaik, this shouldn't matter... i don't think apt works that way.

---

### Post by moore.bryan on 2008-09-05
well, at least i got some interesting feedback:
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Building tag database... Done      
No candidate version found for kdeplasma-addons
No candidate version found for kdeplasma-addons
The following packages are BROKEN:
  kdebase-kde4 
The following packages are unused and will be REMOVED:
  kappfinder-kde4 kdepasswd-kde4 kwrite-kde4 xine-ui 
The following packages have been automatically kept back:
  kde-icons-oxygen kdebase-data-kde4 kdebase-runtime-data 
  kdebase-runtime-data-common kdebase-workspace kdebase-workspace-data 
  kdelibs5-data kdepimlibs-data libkonq5-templates 
The following packages have been kept back:
  kwin-kde4 language-pack-en language-pack-gnome-en libxml2 libxml2-utils 
  python-libxml2 
1 packages upgraded, 0 newly installed, 4 to remove and 15 not upgraded.
Need to get 21.9kB of archives. After unpacking 6246kB will be freed.
The following packages have unmet dependencies:
  kdebase-kde4: Depends: dolphin-kde4 (>= 4:4.1.1-0ubuntu1~hardy1~ppa1) but 4:4.0.5-0ubuntu1~hardy1 is installed.
                Depends: kappfinder-kde4 (>= 4:4.1.1-0ubuntu1~hardy1~ppa1) but it is not installable
                Depends: kdebase-bin-kde4 (>= 4:4.1.1-0ubuntu1~hardy1~ppa1) but 4:4.0.5-0ubuntu1~hardy1 is installed.
                Depends: kdepasswd-kde4 (>= 4:4.1.1-0ubuntu1~hardy1~ppa1) but it is not installable
                Depends: kfind-kde4 (>= 4:4.1.1-0ubuntu1~hardy1~ppa1) but 4:4.0.5-0ubuntu1~hardy1 is installed.
                Depends: konqueror-kde4 (>= 4:4.1.1-0ubuntu1~hardy1~ppa1) but 4:4.0.5-0ubuntu1~hardy1 is installed.
                Depends: konqueror-nsplugins-kde4 (>= 4:4.1.1-0ubuntu1~hardy1~ppa1) but 4:4.0.5-0ubuntu1~hardy1 is installed.
                Depends: konsole-kde4 (>= 4:4.1.1-0ubuntu1~hardy1~ppa1) but 4:4.0.5-0ubuntu1~hardy1 is installed.
                Depends: kwrite-kde4 (>= 4:4.1.1-0ubuntu1~hardy1~ppa1) but it is not installable
                Depends: libkonq5 (>= 4:4.1.1-0ubuntu1~hardy1~ppa1) but 4:4.0.5-0ubuntu1~hardy1 is installed.
Resolving dependencies...
The following actions will resolve these dependencies:

Remove the following packages:
kde4-core
kdebase-kde4

Score is -9812

Accept this solution? [Y/n/q/?] 

```

---

### Post by arch0njw on 2008-09-05
score?  That's interesting.

Add those packages to the command.  You will need all of those.  Omit "kdeplasma-addons"; looks like it isn't used anymore despite what that website says.

---

### Post by Crafty Kisses on 2008-09-05
> **moore.bryan said:**
> well, at least i got some interesting feedback:
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Building tag database... Done      
No candidate version found for kdeplasma-addons
No candidate version found for kdeplasma-addons
The following packages are BROKEN:
  kdebase-kde4 
The following packages are unused and will be REMOVED:
  kappfinder-kde4 kdepasswd-kde4 kwrite-kde4 xine-ui 
The following packages have been automatically kept back:
  kde-icons-oxygen kdebase-data-kde4 kdebase-runtime-data 
  kdebase-runtime-data-common kdebase-workspace kdebase-workspace-data 
  kdelibs5-data kdepimlibs-data libkonq5-templates 
The following packages have been kept back:
  kwin-kde4 language-pack-en language-pack-gnome-en libxml2 libxml2-utils 
  python-libxml2 
1 packages upgraded, 0 newly installed, 4 to remove and 15 not upgraded.
Need to get 21.9kB of archives. After unpacking 6246kB will be freed.
The following packages have unmet dependencies:
  kdebase-kde4: Depends: dolphin-kde4 (>= 4:4.1.1-0ubuntu1~hardy1~ppa1) but 4:4.0.5-0ubuntu1~hardy1 is installed.
                Depends: kappfinder-kde4 (>= 4:4.1.1-0ubuntu1~hardy1~ppa1) but it is not installable
                Depends: kdebase-bin-kde4 (>= 4:4.1.1-0ubuntu1~hardy1~ppa1) but 4:4.0.5-0ubuntu1~hardy1 is installed.
                Depends: kdepasswd-kde4 (>= 4:4.1.1-0ubuntu1~hardy1~ppa1) but it is not installable
                Depends: kfind-kde4 (>= 4:4.1.1-0ubuntu1~hardy1~ppa1) but 4:4.0.5-0ubuntu1~hardy1 is installed.
                Depends: konqueror-kde4 (>= 4:4.1.1-0ubuntu1~hardy1~ppa1) but 4:4.0.5-0ubuntu1~hardy1 is installed.
                Depends: konqueror-nsplugins-kde4 (>= 4:4.1.1-0ubuntu1~hardy1~ppa1) but 4:4.0.5-0ubuntu1~hardy1 is installed.
                Depends: konsole-kde4 (>= 4:4.1.1-0ubuntu1~hardy1~ppa1) but 4:4.0.5-0ubuntu1~hardy1 is installed.
                Depends: kwrite-kde4 (>= 4:4.1.1-0ubuntu1~hardy1~ppa1) but it is not installable
                Depends: libkonq5 (>= 4:4.1.1-0ubuntu1~hardy1~ppa1) but 4:4.0.5-0ubuntu1~hardy1 is installed.
Resolving dependencies...
The following actions will resolve these dependencies:

Remove the following packages:
kde4-core
kdebase-kde4

Score is -9812

Accept this solution? [Y/n/q/?] 

```
That should be good, look in your session list and it should be there.

---

### Post by gjoellee on 2008-09-05
deb [http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu](http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu) hardy main
ok, often i need to install broken packages, so try this...```

sudo apt-get install kdebase-kde4 

```then lets install KDE4.1  the easy way =) [http://www.kshoster.net/?c=downloads&h=apturl](http://www.kshoster.net/?c=downloads&h=apturl) just find "KDE4"

**EDIT: It seams that KDE4 is removed from AptUrl, but is still available in Add/Remove**

---

### Post by moore.bryan on 2008-09-05
> **Codename said:**
> That should be good, look in your session list and it should be there.
no dice, still 4.0...

> **gjoellee said:**
> deb [http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu](http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu) hardy main
ok, often i need to install broken packages, so try this...```

sudo apt-get install kdebase-kde4 

```then lets install KDE4.1  the easy way =) [http://www.kshoster.net/?c=downloads&h=apturl](http://www.kshoster.net/?c=downloads&h=apturl) just find "KDE4"

**EDIT: It seams that KDE4 is removed from AptUrl, but is still available in Add/Remove**
huh?
:-)

---

### Post by Crafty Kisses on 2008-09-05
I'll do a step-by-step tutorial right now for you:

**Go to System -> Administration -> Software Sources**

Enter your password and the Software Sources window will appear. Click the second tab "Third-Party Software," then click the 'Add' button and paste the following code in the new window that will appear:


```
deb http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu hardy main
```


Now, click the 'Add Source' button and, immediately after, the 'Close' button of the main window. It will ask you if you want to reload the information about available software. Click the 'Reload' button and wait for the Software Sources window to close.


**Step 2** - Install KDE 4.1.0

All you need to do now is to click [here]("apt://kubuntu-kde4-desktop") to install KDE 4.1

Then click the 'Yes' button to install the packages (enter your password when asked)...

Wait for the KDE 4.1 packages to be downloaded...

If you get an error while doing that, try the following:
```
sudo apt-get update
```
Then after you updated the repos, try this:```
sudo apt-get install kde-core
```

When the download is over (it will take a while if you have a slow bandwidth) you will be asked to choose a display manager (GDM or KDM-KDE4). Just click Forward...

The installation will start and, when it is over, just log out. Then select the 'KDE 4' option in the "Select Session" entry of the GNOME login manager and voila... KDE 4 fun on your desktop!

Enjoy the brand new KDE 4.1.0 on Ubuntu 8.04.

---

### Post by moore.bryan on 2008-09-05
i've already added the ppa repo; it still installs 4.0. i'm going to try the apturl link now...
--------
EDIT:
okay, so the apturl tells me i have broken packages even though apt in all its forms (i.e., apt-get, aptitude, synaptic, etc.) doesn't say so. i'm now running ```
sudo aptitude install kde-core kde4-core
```
even though i got some score in the negative, i'll see what this does.

---

### Post by Crafty Kisses on 2008-09-05
> **moore.bryan said:**
> i've already added the ppa repo; it still installs 4.0. i'm going to try the apturl link now...

Yes since you added that line in your sources, you have to download the apt link.

---

### Post by moore.bryan on 2008-09-05
i already did this AND followed your tutorial to the letter. kde 4.1 WILL NOT install. i ONLY have kde 4.0. could it be i'm running on an imac (ppc) and there ISN'T a kde 4.1 package for it yet?

---

