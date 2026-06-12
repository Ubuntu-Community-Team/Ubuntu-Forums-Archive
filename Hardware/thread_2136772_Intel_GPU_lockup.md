---
title: "Intel GPU lockup"
date: 2013-04-18
forum: Hardware
---

### Post by kjkrum on 2013-04-18
I'm running a clean install of 12.04.02 (i.e., direct from the 12.04.02 install disk, not upgraded from 12.04.01).  All packages are up to date.  My hardware includes a Gigabyte GA-Z77-HD3 with a Sandy Bridge Celeron, and I'm using the on-board Intel HD graphics.

I keep getting GPU lockups. They're not the "false" ones often reported.  The error message (copied by hand because Apport won't let me copy from the UI) is:

```
[sandybridge-gt1] GPU lockup IPEHR: 0x23002000 IPEHR: 0x0b140001
```

Under "package", it says "xserver-xorg-video-intel (not installed)".  Further down, it tells me to upgrade or install that package.  But when I try to do so, I get this error:

```
kevin@aphrodite:~$ sudo apt-get install xserver-xorg-video-intel
[sudo] password for kevin: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 xserver-xorg-video-intel : Depends: xorg-video-abi-11
                            Depends: xserver-xorg-core (>= 2:1.10.99.901)
E: Unable to correct problems, you have held broken packages.
```

I don't understand what that means, or why I'm getting a crash report from a package that isn't even installed.  What should I do next?

---

### Post by matt_symes on 2013-04-18
Hi

Try upgrading you kernel. 

[http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)

Download and install one of the debs (3.8 kernel or some such). That has fixed it for some people.

Kind regards

---

### Post by kjkrum on 2013-04-18
Hrm.  It doesn't seem very prudent to force a release *n* system to upgrade its kernel to a version packaged for release *n* + 2.  If I start doing things like this, it will defeat the purpose of using a LTS version.

---

### Post by matt_symes on 2013-04-18
Hi

> **kjkrum said:**
> Hrm.  It doesn't seem very prudent to force a release *n* system to upgrade its kernel to a version packaged for release *n* + 2.  If I start doing things like this, it will defeat the purpose of using a LTS version.

Agreed. It's an issue that has affected sandybridge with intel graphics.

It has fixed the issue for some people though. Better to have a working system with a working kernel.

Kind regards

---

### Post by kjkrum on 2013-04-18
Has it been decided that this will never be fixed in LTS?  And would it cease to be a problem if I got a discrete video card, as I plan to do anyway?

With Apport running, it's reduced from a fatal crash to a moderate annoyance.  So I can live with it if it's eventually going to be fixed, or an upgrade will avoid it.  I'd rather preserve the integrity of my LTS system.

---

### Post by matt_symes on 2013-04-18
Hi   > **kjkrum said:**
> Has it been decided that this will never be fixed in LTS?    No idea. I would hope so as it's affected a number of users  They are aware of it and say it may be back ported (assuming this is the same issue you face)    [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/1159255](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/1159255)    >  And would it cease to be a problem if I got a discrete video card, as I plan to do anyway?    As far as i'm aware. Make sure it's Linux compatible.   Kind regards

---

### Post by paulisdead on 2013-04-18
I had the same issue on my work laptop with 12.10.  I haven't tried upgrading the kernel, but booting the older 3.5.0-17-generic kernel has fixed the lockups for me.

---

### Post by kjkrum on 2013-04-21
I seem to have fixed this.  I've gone two days without a crash or Apport message, where before I would usually get several errors within minutes of logging in.  *knocks wood*

To install xserver-xorg-video-intel, I explicitly installed xorg-video-abi-11.  This caused a large number of packages with "-lts-quantal" in their names to be uninstalled.  I have no idea when or why those packages were installed.  I was then able to install xserver-xorg-video-intel.

I rebooted and found that I had no X server at all!  I installed xserver-xorg from the console and rebooted again.  Now everything seems to be operating normally.

---

### Post by matt_symes on 2013-04-21
Hi

> **kjkrum said:**
> I seem to have fixed this.  I've gone two days without a crash or Apport message, where before I would usually get several errors within minutes of logging in.  *knocks wood*

To install xserver-xorg-video-intel, I explicitly installed xorg-video-abi-11.  This caused a large number of packages with "-lts-quantal" in their names to be uninstalled.  I have no idea when or why those packages were installed.  I was then able to install xserver-xorg-video-intel.

I rebooted and found that I had no X server at all!  I installed xserver-xorg from the console and rebooted again.  Now everything seems to be operating normally.

Thanks for posting back with this information. I'll do some search and see if this is a better work around than upgrading the kernel.

It's been a while since i looked to see what is the best way to handle this bug as it's not an issue that has affected me. I only get a certain amount of time to keep up with the big bugs in Ubuntu.

If you get the issue again then please post back and update this thread.

Kind regards

---

### Post by kjkrum on 2013-05-10
Since my last comment about two weeks ago, I experienced only one crash.  Previously they occurred several times an hour.  I updated my kernel a couple days ago, so I guess the experiment is over.  I'm now running kernel 3.5.0-28-generic #48.

---

