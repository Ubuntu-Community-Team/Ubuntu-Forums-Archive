---
title: "Problem installing  librmagick-ruby1.8"
date: 2009-02-03
forum: Installation &amp; Upgrades
---

### Post by IceCubeUK on 2009-02-03
I am setting up a Ruby on Rails environment on a clean install of:
Ubuntu 8.04.1
Release:        8.04
Codename:       hardy

I am trying to install librmagick-ruby1.8 but get the following error message:

~# apt-get install librmagick-ruby1.8
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
  librmagick-ruby1.8: Depends: libmagick9 but it is not installable
E: Broken packages

I have come across this thread:
[https://bugs.launchpad.net/ubuntu/+source/librmagick-ruby/+bug/220811](https://bugs.launchpad.net/ubuntu/+source/librmagick-ruby/+bug/220811)

describing the same problem. However there lacks a clear explanation for a relative Newbie on how to solve this problem.

I know the post says the problem as been fixed in Intrepid but I would much rather stick with 8.04 as this a Long Term Support Release.

---

