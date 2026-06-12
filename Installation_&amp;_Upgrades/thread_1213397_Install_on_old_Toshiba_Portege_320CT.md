---
title: "Install on old Toshiba Portege 320CT?"
date: 2009-07-14
forum: Installation &amp; Upgrades
---

### Post by jimcpl on 2009-07-14
Hi,

I have an old Toshiba Portege 320CT that I kind of "inherited".  It originally ran Win95, but I've been wanting to update it to something a little more recent, so that I can give it to a friend who doesn't have any laptop.

I had tried Windows 2000 Pro and then Windows XP Home, and actually got both installed and working, but with both of those, I could not get the IDE interface to work in DMA, just PIO, and this made the machine VERY slow (like 6Mbps using HDTach, with 100% CPU utilization).  

It's so slow that I don't feel right even giving it away :(, but I think that that would be a real shame, as I got just about every peripheral they made for it, including two docks, etc.

So, I've been starting to think about trying to put Ubuntu or Xubuntu on it.  The thing is, I've done Linux installs before, but they're mostly Redhat, and I don't really want to go down this road if I'm going to end up at a deadend.

Mostly, what I'm looking to put on it is pretty simple, mainly to be used for web surfing, but I also want:

- To have the IDE DMA working
- Have it work with a wireless 11G PCMCIA adapter 

The machine has been upgraded to the maximum 96MB of RAM, and I have several drives available for this, up to 40GB.  I also have a couple of wireless cards including a Dlink DWL-G650.  One of the docks also has a CD drive built-in, but I don't have a floppy drive for it.  Also, the machine won't boot from USB.

So, I guess what I'm trying to ask is whether Ubuntu or Xubuntu would be able to do this?  Or, if not, maybe someone knows of some other distribution that might do the job?

Thanks,
Jim

---

### Post by jimcpl on 2009-07-14
Hi,

I went ahead and downloaded the current Xubuntu ISO, and burned it to CD.

However, when I boot the CD, there's a line that says something about "forceacpi" or "acpiforce", and then it boots to a "Busybox" prompt only.  This happens whether I select to try to boot to the LiveCD or try to install.

Any ideas?

Thanks,
Jim

---

### Post by earthpigg on 2009-07-15
Puppy Linux is known to run on damn near anything you throw it at -- and it isn't ubuntu-based, so *_may_* not have the same issues as anything ubuntu-based.

you could also try ubuntu minimal command-line only install and build up from there -- only possible if it can get networking going, of course.

#! (pronounced/spelle 'CrunchBang') is regarded as the most lightweight Ubuntu-derivative out there, short of CLI only install.

best of luck!

---

### Post by acimmarusti on 2009-07-15
You could also try Debian 5.0 Lenny XCFE. It was rated much better for older computers than the latest Xubuntu and it's also Debian's stable release which works sooo well!. Don't fear Debian, it has a reputation for being harder, but it really isn't. 

But Puppy Linux or Damn Small linux are very good choices if XCFE still proves too much for the computer to handle.

---

### Post by jimcpl on 2009-07-15
> **earthpigg said:**
> Puppy Linux is known to run on damn near anything you throw it at -- and it isn't ubuntu-based, so *_may_* not have the same issues as anything ubuntu-based.

you could also try ubuntu minimal command-line only install and build up from there -- only possible if it can get networking going, of course.

#! (pronounced/spelle 'CrunchBang') is regarded as the most lightweight Ubuntu-derivative out there, short of CLI only install.

best of luck!

Hi,

I've already tried Puppy.  That would boot the CD.

DSL would boot to the LiveCD, and I also was able to get it to do an HDINSTALL, but then when I booted to the installation on the CD, it got to a "box:" login, and it wouldn't take the "root" login, for which I had just set a password.

Also, BTW, DSL, when booted from the LiveCD, would also recognize one of the PCMCIA Wifi cards I have, out-of-the-box, an Orinoco Silver, but I couldn't get it to do anything with a Dlink DWL-G650 (although it's on DSL's OOB list).  

I've registered on DSL's forum, to try to post there, but the activation was failing :(...

Jim

---

### Post by jimcpl on 2009-07-15
> **acimmarusti said:**
> You could also try Debian 5.0 Lenny XCFE. It was rated much better for older computers than the latest Xubuntu and it's also Debian's stable release which works sooo well!. Don't fear Debian, it has a reputation for being harder, but it really isn't. 

But Puppy Linux or Damn Small linux are very good choices if XCFE still proves too much for the computer to handle.

Hi,

I'll take a look at Debian if I can't get anywhere with Puppy (which I think installs on the HD as Debian), but this laptop (a Toshiba Portege 320CT) is starting to look like a hopeless case :(...

Thanks,
Jim

---

### Post by jimcpl on 2009-07-15
> **jimcpl said:**
> Hi,

I'll take a look at Debian if I can't get anywhere with Puppy (which I think installs on the HD as Debian), but this laptop (a Toshiba Portege 320CT) is starting to look like a hopeless case :(...

Thanks,
Jim

acimmarusti,

Thanks for the pointer to Debian.  I was able to start the install last night, and it even detected one of my PCMCIA WIFI cards (an Orinoco silver).  It's taking "forever" to do the install (still running since last night), but so far, so good.

Thanks again,
Jim

---

### Post by acimmarusti on 2009-07-16
It would have been faster if you had downloaded the iso image in advance, instead of doing a netinstall which can take a really long time (depending on your connection and device).

You can download either the first DVD. But since the computer is old, it might only have a CD drive, in which case you could download the cd image containing XCFE:

If you go here you can find it
[http://cdimage.debian.org/debian-cd/5.0.2/i386/iso-cd/](http://cdimage.debian.org/debian-cd/5.0.2/i386/iso-cd/)

Tell me how it's going, I have several tips that would be helpful.

Good luck

---

