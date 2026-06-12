---
title: "Cannot install FGLRX driver in Ubuntu 14.04.5"
date: 2016-12-21
forum: Hardware
---

### Post by jr49 on 2016-12-21
Hi.

I am trying to install the fglrx driver for my AMD Radeon HD 7750 in Ubuntu 14.04.5 using

```
sudo apt-get install fglrx
```
However, I get the error

```
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
 unity-control-center : Depends: libcheese-gtk23 (>= 3.4.0) but it is not going to be installed
                        Depends: libcheese7 (>= 3.0.1) but it is not going to be installed
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
```
I've tried downgrading xorg-server. This allowed me to install fglrx (an  error box did pop up half way through, but it seemed to complete okay).  Unfortunately, after rebooting and entering my password, I was shown a  black screen and taken back to the password entry screen. This seems to  be the same behaviour described (but not resolved) in this thread [here]("https://ubuntuforums.org/showthread.php?t=2273776"). 

A bit more digging revealed a big long bug report [here]("https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/1424491").  But the bug was reported nearly 2 years ago and appeared fixed by the  end of the thread.

Does anyone know the correct way to solve this please?

Thanks!

---

### Post by happydog500 on 2016-12-22
Could be, you posted 14.04.5. flgrx doesen't work past 14.04.1. I did read one that said 14.04.4, but none with 14.04.5. 

jmho,
 
 Chris.

---

