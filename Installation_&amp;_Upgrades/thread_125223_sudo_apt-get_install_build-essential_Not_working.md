---
title: "sudo apt-get install build-essential: Not working"
date: 2006-02-03
forum: Installation &amp; Upgrades
---

### Post by yim03u on 2006-02-03
having a few problems running sudo apt-get install build-essential.

Due to the fact that 

> deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-backports main 
> universe multiverse restricted
> deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-extras main universe 
> multiverse restricted

are no longer working. I have changed it two lines to the following within sources.list

> deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary-backports
> main restricted universe multiverse
> deb [http://kambing.vlsm.org/ubuntu-backports](http://kambing.vlsm.org/ubuntu-backports)
> hoary-extras main universe multiverse restricted

having done this and ran sudo apt-get update (which works fine), i am no longer able to run sudo apt-get install build-essential, because the following errors appear:

> Reading package lists... Done
> Building dependency tree... Done
> Some packages could not be installed. This may mean
> that you have
> requested an impossible situation or if you are using
> the unstable
> distribution that some required packages have not yet
> been created
> or been moved out of Incoming.
>
> Since you only requested a single operation it is
> extremely likely that
> the package is simply not installable and a bug report
> against
> that package should be filed.
> The following information may help to resolve the
> situation:
>
> The following packages have unmet dependencies:
>   build-essential: Depends: libc6-dev but it is not
> going to be installed or
>                             libc-dev
>                    Depends: g++ (>= 3:3.3) but it is
> not going to be installed
> E: Broken packages

I really don't know what to do, beacuse I need those files (especially the c++ compiler)
Installing then using synaptic package manager seems to cause further dependancy problems.

Any ideas?

---

### Post by aysiu on 2006-02-03
Something's definitely wrong with your sources.list.
See the first link of my signature.

---

### Post by yim03u on 2006-02-04
I have copied the sources.list that you have provided in your link and exactly the same error appears:

The following packages have unmet dependencies:
  build-essential: Depends: libc6-dev but it is not going to be installed or
                            libc-dev
                   Depends: g++ (>= 3:3.3) but it is not going to be installed
E: Broken packages

It was copied word for word, abd i tried updating with a blank sources.list and it's still not working.

I have checked this file so many times and still can't find anything wrong with it.

????

---

### Post by yim03u on 2006-02-04
Actally seems to be working now! Excellent...long way to go, but this is a good start.  Thankyou.

---

