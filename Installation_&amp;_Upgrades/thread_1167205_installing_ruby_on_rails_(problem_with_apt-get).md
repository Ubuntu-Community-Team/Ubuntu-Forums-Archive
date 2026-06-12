---
title: "installing ruby on rails (problem with apt-get?)"
date: 2009-05-22
forum: Installation &amp; Upgrades
---

### Post by entrecote on 2009-05-22
hi
im new to ubuntu and tried to start installing ruby on rails (running on vmware workstation, the internet connection works fine, it bridged)

tried by the manual
[https://help.ubuntu.com/community/RubyOnRails](https://help.ubuntu.com/community/RubyOnRails)

and wrote at the console:
sudo apt-get install ruby-full build-essential

got output of:

reading package lists...done
building dependency tree
reading state information...done
E: couldn't find package ruby-full


what i'm missing here? newbie to ubuntu :)

---

### Post by sanderd17 on 2009-05-22
I don't know what you're missing, maybe, try if you find the package in synaptic

---

### Post by entrecote on 2009-05-22
what's synaptic?

is it possible it's something with the apt-get that missing?

---

### Post by sanderd17 on 2009-05-24
synaptic is the user interface to install what you would type after apt-get. you can find synaptic in System -> administration -> synaptic package manager. 

Search for ruby-full (make sure that you can search all apps by selecting all on the left side) and if you find it, install it instead of going with the command line. if you don't find it: check the settings -> repositories, try to select as much repositories  as you can and try again to search for ruby-full. if that doesn't work I don't know what the problem is.

---

### Post by entrecote on 2009-05-24
and if i found it in synaptic? is there a difference between the command i wrote and by checking the sqare and installing it manually?

---

### Post by entrecote on 2009-05-24
tried to install manually, got could not resole "il.archive.ubuntu.com" but the path itself is working on firefox

---

### Post by anoldhacker on 2009-07-06
> **entrecote said:**
> hi
im new to ubuntu and tried to start installing ruby on rails (running on vmware workstation, the internet connection works fine, it bridged)

tried by the manual
[https://help.ubuntu.com/community/RubyOnRails](https://help.ubuntu.com/community/RubyOnRails)

and wrote at the console:
sudo apt-get install ruby-full build-essential

got output of:

reading package lists...done
building dependency tree
reading state information...done
E: couldn't find package ruby-full


what i'm missing here? newbie to ubuntu :)


Under NO circumstances would I install rails via OS repositories.  Rails almost has to move much, MUCH faster than an OS repo should ever be allowed to move.

Install ruby.  (I'm actually nosing around to figure out if 1.9 is available in a repo for Hardy.)  Actually, you want the development library, so that's ruby1.9-dev or ruby1.8-dev.

Next, you need rubygems, version >= 1.3.1.  If your distribution does not have it, you can download and install from source.

NOW you can install the rails gems.  If you are wanting to do more than play around, however, you need to find a guide for doing things right.  Some things should be installed via repo, some via gem.

---

