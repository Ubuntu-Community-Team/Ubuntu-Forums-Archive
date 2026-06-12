---
title: "synaptic problems"
date: 2008-11-23
forum: General Help
---

### Post by //source\\ on 2008-11-23
I dont know why...but my repositories will not open from synaptic package manager nor will my software sources open from System >Aministration> Software Sources. 


## -----------------------
## LINUX MINT REPOSITORIES
## -----------------------

## +++ Linux Mint 6 Felicia (stable) +++
deb [http://packages.linuxmint.com/](http://packages.linuxmint.com/) felicia main upstream import 

## +++ Backports (not as stable) +++
# deb [http://packages.linuxmint.com/](http://packages.linuxmint.com/) felicia backport 

## +++ Community (not as stable) +++
# deb [http://packages.linuxmint.com/](http://packages.linuxmint.com/) felicia community 

## +++ Romeo (unstable) +++
# deb [http://packages.linuxmint.com/](http://packages.linuxmint.com/) felicia romeo 

## +++ Source Repositories +++
# deb-src [http://packages.linuxmint.com/](http://packages.linuxmint.com/) felicia main upstream import 
# deb-src [http://packages.linuxmint.com/](http://packages.linuxmint.com/) felicia community 
# deb-src [http://packages.linuxmint.com/](http://packages.linuxmint.com/) felicia backport 
# deb-src [http://packages.linuxmint.com/](http://packages.linuxmint.com/) felicia romeo 

## -------------------
## UBUNTU REPOSITORIES
## -------------------

## +++ Ubuntu 8.10 Intrepid (stable) +++
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid main restricted universe multiverse 
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid-updates main restricted universe multiverse 
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) intrepid-security main restricted universe multiverse 

## +++ Backports & Proposed (not as stable) +++
# deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse 
# deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid-proposed main restricted universe multiverse 

## +++ Source Repositories +++
# deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid main restricted universe multiverse 
# deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid-updates main restricted universe multiverse 
# deb-src [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) intrepid-security main restricted universe multiverse 
# deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse 
# deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid-proposed main restricted universe multiverse 

## ------------------
## OTHER REPOSITORIES
## ------------------

## +++ Canonical (stable) +++
deb [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) intrepid partner 

## +++ Medibuntu (stable) +++
deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) intrepid free non-free

---

### Post by fooman on 2008-11-23
what happens when you try to update the sources from the command line?

try this in a terminal,  then post the results back here:

```
sudo apt-get update
```

---

### Post by groggyboy on 2008-12-03
i think i have the same problem.  fooman: the problem is not updating the repositories, the problem is trying to open the software sources program:```
groggyboy@ono-sendai:~$ sudo software-properties-gtk
[sudo] password for groggyboy: 
/usr/lib/python2.5/site-packages/apt/__init__.py:18: FutureWarning: apt API not stable yet
  warnings.warn("apt API not stable yet", FutureWarning)
Traceback (most recent call last):
  File "/usr/bin/software-properties-gtk", line 101, in <module>
    app = SoftwarePropertiesGtk(datadir=data_dir, options=options, file=file)
  File "/usr/lib/python2.5/site-packages/softwareproperties/gtk/SoftwarePropertiesGtk.py", line 75, in __init__
    SoftwareProperties.__init__(self, options=options, datadir=datadir)
  File "/usr/lib/python2.5/site-packages/softwareproperties/SoftwareProperties.py", line 78, in __init__
    self.reload_sourceslist()
  File "/usr/lib/python2.5/site-packages/softwareproperties/SoftwareProperties.py", line 516, in reload_sourceslist
    self.distro.get_sources(self.sourceslist)    
  File "/usr/lib/python2.5/site-packages/aptsources/distro.py", line 85, in get_sources
    "Error: could not find a distribution template")
aptsources.distro.NoDistroTemplateException

```

i suspect it's because linux mint has done some customizing to apt.  anyone know a solution?

---

### Post by clemyeats on 2008-12-04
Hi, 

This is because software-properties contains hardcoded references to Debian and Ubuntu and in the case of Linux Mint (which now uses its own LSB info) it fails to find the proper templates. 

The solution is to remove software-properties. Once removed Synaptic will use its own graphical interface to let you change your repositories. 

Clem.

---

### Post by groggyboy on 2008-12-07
@ clemyeats, your suggestion worked, but couldn't help picking at the problem.  i managed to get software-properties to work by editing the "/etc/lsb-release" file.  i replaced the contents with this:```
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=8.10
DISTRIB_CODENAME=intrepid
DISTRIB_DESCRIPTION="Ubuntu 8.10"
```

voila: software-properties works again.  the downside of this is that your computer now thinks it's running ubuntu instead of linux mint.  you can see this if you open System Monitor and look at the System tab.  I guess you can't have your cake and eat it too.  I'm not sure what other effects this would have - probably prevents you from upgrading to the next version of linux mint when it comes out.  This is maybe not a good hack for everybody.

---

### Post by jts0803odon on 2008-12-31
> **groggyboy said:**
> @ clemyeats, your suggestion worked, but couldn't help picking at the problem.  i managed to get software-properties to work by editing the "/etc/lsb-release" file.  i replaced the contents with this:```
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=8.10
DISTRIB_CODENAME=intrepid
DISTRIB_DESCRIPTION="Ubuntu 8.10"
```

voila: software-properties works again.  the downside of this is that your computer now thinks it's running ubuntu instead of linux mint.  you can see this if you open System Monitor and look at the System tab.  I guess you can't have your cake and eat it too.  I'm not sure what other effects this would have - probably prevents you from upgrading to the next version of linux mint when it comes out.  This is maybe not a good hack for everybody.

Not to bump an old thread, but this worked for me on Intrepid - I was having a problem where apt-get update would process normally in terminal, but Software Sources wouldn't work from the menu and software-properties-gtk would give me errors:

```
 /usr/lib/python2.5/site-packages/apt/__init__.py:18: FutureWarning: apt API not stable yet
  warnings.warn("apt API not stable yet", FutureWarning)
Traceback (most recent call last):
  File "/usr/bin/software-properties-gtk", line 101, in <module>
    app = SoftwarePropertiesGtk(datadir=data_dir, options=options, file=file)
  File "/usr/lib/python2.5/site-packages/softwareproperties/gtk/SoftwarePropertiesGtk.py", line 75, in __init__
    SoftwareProperties.__init__(self, options=options, datadir=datadir)
  File "/usr/lib/python2.5/site-packages/softwareproperties/SoftwareProperties.py", line 78, in __init__
    self.reload_sourceslist()
  File "/usr/lib/python2.5/site-packages/softwareproperties/SoftwareProperties.py", line 516, in reload_sourceslist
    self.distro.get_sources(self.sourceslist)    
  File "/usr/lib/python2.5/site-packages/aptsources/distro.py", line 85, in get_sources
    "Error: could not find a distribution template")
aptsources.distro.NoDistroTemplateException
```

While lsb_release -a reported the Debian distribution (DebianEdu/Skolelinux) and related info instead of the Ubuntu info you list above. Swapping the 8.10 dist name, version, nickname etc. for the Debian info in /etc/lsb-release return software sources to normal function in Intrepid.

---

