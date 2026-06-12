---
title: "VLC media player installation problem"
date: 2008-11-12
forum: General Help
---

### Post by burmanabhay88 on 2008-11-12
I've installed ubuntu 8.04 and tried installing VLC using the add remove programs. it said that it conflicts with other packages already installed( I have not installed any other application so far). It advises me to use the synaptic package manager to resolve issues???? Can some one help me out.
I'd like to know which packages to remove.

---

### Post by Ryadt on 2008-11-12
Try updating your system first. 
Type in terminal```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by burmanabhay88 on 2008-11-12
> **Ryadt said:**
> Try updating your system first. 
Type in terminal```
sudo apt-get update && sudo apt-get upgrade
```

my internet speed kind of sucks. so these kind of options are ruled out. I need to know the software/packages that I need to uninstall.

---

### Post by Ryadt on 2008-11-12
Try to install through the terminal
```
sudo apt-get install vlc
```
Post back any errors.

---

### Post by oldos2er on 2008-11-12
"It advises me to use the synaptic package manager to resolve issues???? Can some one help me out."

 Have you done this? If you have broken packages, you can fix them under the 'Edit' menu.

---

### Post by burmanabhay88 on 2008-11-13
> **Ryadt said:**
> Try to install through the terminal
```
sudo apt-get install vlc
```
Post back any errors.

```
This is what it returned to me...

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
  vlc: Depends: libtar but it is not installable
       Depends: libvcdinfo0 (> 0.7.23) but it is not installable
       Depends: libvlc0 (>= 0.8.6.release.e+x264svn20071224+faad2.6.1) but it is not going to be installed
       Depends: libwxbase2.6-0 (>= 2.6.3.2.2) but it is not installable
       Depends: libwxgtk2.6-0 (>= 2.6.3.2.2) but it is not installable
       Depends: libxosd2 (>= 2.2.13) but it is not installable
       Depends: vlc-nox (= 0.8.6.release.e+x264svn20071224+faad2.6.1-0ubuntu3.2) but it is not going to be installed
       Depends: vlc-plugin-pulse but it is not going to be installed
E: Broken packages

```

Now what do I do???

---

### Post by burmanabhay88 on 2008-11-13
> **oldos2er said:**
> "It advises me to use the synaptic package manager to resolve issues???? Can some one help me out."

 Have you done this? If you have broken packages, you can fix them under the 'Edit' menu.

And how do I go about doing that???
I'm a Ubuntu/Linux Newbie...

---

### Post by mc4man on 2008-11-13
Open up synaptic, click on the edit tab on panel. Then click on 'fix broken packages', then click the 'apply' icon and see what happens.

If not fixed try searching vlc in synaptic and see if anything with vlc in the name is installed (green box),
If so, mark for removal (r. click on package) and apply.

---

### Post by burmanabhay88 on 2008-11-13
> **mc4man said:**
> Open up synaptic, click on the edit tab on panel. Then click on 'fix broken packages', then click the 'apply' icon and see what happens.

If not fixed try searching vlc in synaptic and see if anything with vlc in the name is installed (green box),
If so, mark for removal (r. click on package) and apply.

I fixed broken packages. Nothing happened as such.
Then I tried installing VLC from the Synaptic package manager only.

This is what I got...

vlc:
 Depends: libtar  but it is not installable
 Depends: libvcdinfo0 (>0.7.23) but it is not installable
 Depends: libvlc0 but it is not going to be installed
 Depends: libwxbase2.6-0 (>=2.6.3.2.2) but it is not installable
 Depends: libwxgtk2.6-0 (>=2.6.3.2.2) but it is not installable
 Depends: libxosd2 (>=2.2.13) but it is not installable
 Depends: vlc-nox but it is not going to be installed
 Depends: vlc-plugin-pulse but it is not going to be installed

---

### Post by mc4man on 2008-11-13
why don't you post your sources
```

cat /ect/apt/sources.list
```

Also in synaptic search out some of the packages listed in your error message and see what's up. Post the version number of any installed and or available or not found.

did you find anything with vlc in the name?

---

### Post by burmanabhay88 on 2008-11-13
> **mc4man said:**
> why don't you post your sources
```

cat /ect/apt/sources.list
```

Also in synaptic search out some of the packages listed in your error message and see what's up. Post the version number of any installed and or available or not found.

did you find anything with vlc in the name?


Sources.list 
____________
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse
____________________________________

there are no error messages against vlc. :(

( p.s. No more thanks to any one till my problem gets solved. :x )

---

### Post by alwayshere on 2008-11-13
use the Synaptic package manager

Depends: libtar but it is not installable
Depends: libvcdinfo0 (>0.7.23) but it is not installable
Depends: libvlc0 but it is not going to be installed
Depends: libwxbase2.6-0 (>=2.6.3.2.2) but it is not installable
Depends: libwxgtk2.6-0 (>=2.6.3.2.2) but it is not installable
Depends: libxosd2 (>=2.2.13) but it is not installable
Depends: vlc-nox but it is not going to be installed
Depends: vlc-plugin-pulse but it is not going to be installed

and search each file one at a time 

eg searh libtar 

and it should say it cant install because of another package conflict so then searh for that package/s and remove it/them . click reload 
then try and install libtar again.


keep doing this process with all the above listed packages untill done .

---

### Post by burmanabhay88 on 2008-11-13
> **alwayshere said:**
> use the Synaptic package manager

Depends: libtar but it is not installable
Depends: libvcdinfo0 (>0.7.23) but it is not installable
Depends: libvlc0 but it is not going to be installed
Depends: libwxbase2.6-0 (>=2.6.3.2.2) but it is not installable
Depends: libwxgtk2.6-0 (>=2.6.3.2.2) but it is not installable
Depends: libxosd2 (>=2.2.13) but it is not installable
Depends: vlc-nox but it is not going to be installed
Depends: vlc-plugin-pulse but it is not going to be installed

and search each file one at a time 

eg searh libtar 

and it should say it cant install because of another package conflict so then searh for that package/s and remove it/them . click reload 
then try and install libtar again.


keep doing this process with all the above listed packages untill done .

thanks... will try it out n tell you.

---

### Post by Ryadt on 2008-11-13
> **burmanabhay88 said:**
> I fixed broken packages. Nothing happened as such.
Then I tried installing VLC from the Synaptic package manager only.

This is what I got...

vlc:
 Depends: libtar  but it is not installable
 Depends: libvcdinfo0 (>0.7.23) but it is not installable
 Depends: libvlc0 but it is not going to be installed
 Depends: libwxbase2.6-0 (>=2.6.3.2.2) but it is not installable
 Depends: libwxgtk2.6-0 (>=2.6.3.2.2) but it is not installable
 Depends: libxosd2 (>=2.2.13) but it is not installable
 Depends: vlc-nox but it is not going to be installed
 Depends: vlc-plugin-pulse but it is not going to be installed
You will have to update your box.
```
sudo apt-get update && sudo apt-get upgrade
```
This will be solves the issue.

---

### Post by oldos2er on 2008-11-13
Go to System, Administration, Software Sources, and check off the boxes under 'Downloadable from the Internet.' Under the Third Party Software tab, make sure the partner repository is checked. Reload your sources.list, and try again.

---

