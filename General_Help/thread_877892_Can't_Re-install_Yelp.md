---
title: "Can't Re-install Yelp"
date: 2008-08-02
forum: General Help
---

### Post by Greasyfingers on 2008-08-02
Yelp seems to have got removed in a recent tidy up, and I can't get it to re-install. It's producing [_the same problem_]("http://ubuntuforums.org/showthread.php?t=851667") with xulrunner that I had when I tried to re-install Firefox recently, but the solution to that problem isn't working here. 

Here's the output from apt-get:```
~$ sudo apt-get install yelp
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

The following packages have unmet dependencies.
  yelp: Depends: xulrunner-1.9 but it is not going to be installed
E: Broken packages
```However, xulrunner-1.9 is installed:```
~$ xulrunner -v
Mozilla XULRunner 1.9.0.1 - 2008072820
```I've tried removing and purging xulrunner (which also removes Firefox) and autoremoving. Firefox and xulrunner reinstall OK, but not Yelp. Even if I re-install Yelp and xulrunner together, apt-get (or Synaptic) will report that xulrunner is not going to be installed.

How can I fix this please?

---

### Post by Greasyfingers on 2008-08-03
I've managed to get Yelp installed - sort of - using Aptitude, but it only managed to do this by downgrading both Firefox and xulrunner, and these both now seem to be excluded from updates (and updating them will require the removal of Yelp).

Thing is, both apt-get and Aptitude report xulrunner as broken - as this is essential to both Firefox and Yelp (and who knows what else), it seems strange that an updated installation of Ubuntu cannot have both of these standard applications together. As I haven't seen this being reported as a commen problem, I guess I may have broken my installation somewhere. Any suggestions?

---

