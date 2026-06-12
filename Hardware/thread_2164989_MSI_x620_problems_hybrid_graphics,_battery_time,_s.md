---
title: "MSI x620 problems: hybrid graphics, battery time, slow responseq"
date: 2013-08-02
forum: Hardware
---

### Post by va_cs2 on 2013-08-02
Hi everyone!

Let me start with saying that I am completely unfamiliar with Ubuntu, I never used it before. However, I decided that I want to try it, so I recently installed Ubuntu 12.4 LTS by using Wubi, alongside with a Windows 8 OS. My machine is an MSI x620 laptop, which works amazingly well on Windows. My problem with Ubuntu is, that it only recognizes my integrated graphics card -or, well, I don't even know if it recognizes it or not, since when I enter the grep VGA command in the terminal, I get this response: 


```

00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
05:00.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI Manhattan [Mobility Radeon HD 5430 Series]

```
Which is good I guess. However, when I check it in system-details-graphics, it claims that my driver is 'Unkown'. I have a button on my laptop with which I can change between my graphics cards, it does not seem to work with ubuntu, but I can still see that it uses my integrated Intel graphics. I don't even need the option to swtich between the too if it is too much of a hassle, I would be happy using my ATI card permanently. 

So, my question is, what is the proper way to install my driver? I tried this method: [http://ubuntuforums.org/showthread.php?t=1930450&highlight=ati+mobility+radeon+hd5430](http://ubuntuforums.org/showthread.php?t=1930450&highlight=ati+mobility+radeon+hd5430) but it did not seem to work, at the install, I get this response: 

```
=====================================================================
 AMD Catalyst(TM) Proprietary Driver Installer/Packager 
=====================================================================
Generating package: Ubuntu/precise
Resolving build dependencies...
apt 0.8.16~exp12ubuntu10.11 for amd64 compiled on Apr 18 2013 23:27:57
Usage: apt-get [options] command
       apt-get [options] install|remove pkg1 [pkg2 ...]
       apt-get [options] source pkg1 [pkg2 ...]


apt-get is a simple command line interface for downloading and
installing packages. The most frequently used commands are update
and install.


Commands:
   update - Retrieve new lists of packages
   upgrade - Perform an upgrade
   install - Install new packages (pkg is libc6 not libc6.deb)
   remove - Remove packages
   autoremove - Remove automatically all unused packages
   purge - Remove packages and config files
   source - Download source archives
   build-dep - Configure build-dependencies for source packages
   dist-upgrade - Distribution upgrade, see apt-get(8)
   dselect-upgrade - Follow dselect selections
   clean - Erase downloaded archive files
   autoclean - Erase old downloaded archive files
   check - Verify that there are no broken dependencies
   changelog - Download and display the changelog for the given package
   download - Download the binary package into the current directory


Options:
  -h  This help text.
  -q  Loggable output - no progress indicator
  -qq No output except for errors
  -d  Download only - do NOT install or unpack archives
  -s  No-act. Perform ordering simulation
  -y  Assume Yes to all queries and do not prompt
  -f  Attempt to correct a system with broken dependencies in place
  -m  Attempt to continue if archives are unlocatable
  -u  Show a list of upgraded packages as well
  -b  Build the source package after fetching it
  -V  Show verbose version numbers
  -c=? Read this configuration file
  -o=? Set an arbitrary configuration option, eg -o dir::cache=/tmp
See the apt-get(8), sources.list(5) and apt.conf(5) manual
pages for more information and options.
                       This APT has Super Cow Powers.
Unable to resolve  dh-modaliases execstack.  Please manually install and try again.

```


My other problem is that my battery life seems to be reduced in Ubuntu. With Windows (and with MSI's Eco system, with which I could change between several profiles, like 'Power Saving Mode' or 'Game Mode') my battery could last around 8 hours. Now Ubuntu says I have 3:21 hrs left, which is...well, a lot less. I would really appreciate any help with this.

My last problem is that all around, my computer seems to be a bit slower on Ubuntu than on Win8 (or 7). I mean, when I start an application from the Unity panel, it takes a while to open it, even if it's something simple, like the file explorer. (I hope that this problem will somehow magically solve itself when I update my graphics card)

So, all in all, I am aware that my MSI x620 machine is quite a Windows specific one, but I hope I can run it fine on Ubuntu too, someday. 


Eagerly (and desperately) waiting for help:

Eva

---

