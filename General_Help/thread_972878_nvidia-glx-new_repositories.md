---
title: "nvidia-glx-new repositories"
date: 2008-11-06
forum: General Help
---

### Post by rmcellig on 2008-11-06
I am trying to install nvidia-glx-new through the Synaptic Package Manager. When I do I get this error:

The following packages have unresolved dependencies. Make sure that all required repositories are added and enabled in the preferences.

What is the repository link I should add in my Software Sources?

I tried installing from the terminal and I get this:

randy@randyubuntu:~$ sudo apt-get install nvidia-glx-new
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
  nvidia-glx-new: Depends: xserver-xorg-core (>= 1:0.99.0-1) but it is not going to be installed
E: Broken packages
randy@randyubuntu:~$

---

