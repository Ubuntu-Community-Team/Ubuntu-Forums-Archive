---
title: "apt &quot;subprocess post-installation script returned error exit status 1&quot;"
date: 2009-05-24
forum: Hardware
---

### Post by freakalad on 2009-05-24
Running Hardy 64

Since the release of the "important/critical security update" of KVM (ver. 1:62+dfsg-0ubuntu8.2 ), I've been getting these errors, and since then I've been unable to do any further updates/upgrades or new installations.

```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
4 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up kvm (1:62+dfsg-0ubuntu7) ...
usage: update-rc.d [-n] [-f] <basename> remove
       update-rc.d [-n] <basename> defaults [NN | sNN kNN]
       update-rc.d [-n] <basename> start|stop NN runlvl [runlvl] [...] .
		-n: not really
		-f: force
dpkg: error processing kvm (--configure):
 subprocess post-installation script returned error exit status 1
Setting up dnsmasq (2.41-2ubuntu2.1) ...
usage: update-rc.d [-n] [-f] <basename> remove
       update-rc.d [-n] <basename> defaults [NN | sNN kNN]
       update-rc.d [-n] <basename> start|stop NN runlvl [runlvl] [...] .
		-n: not really
		-f: force
dpkg: error processing dnsmasq (--configure):
 subprocess post-installation script returned error exit status 1
Setting up ntp (1:4.2.4p4+dfsg-3ubuntu2.2) ...
usage: update-rc.d [-n] [-f] <basename> remove
       update-rc.d [-n] <basename> defaults [NN | sNN kNN]
       update-rc.d [-n] <basename> start|stop NN runlvl [runlvl] [...] .
		-n: not really
		-f: force
dpkg: error processing ntp (--configure):
 subprocess post-installation script returned error exit status 1
Setting up pulseaudio (0.9.10-1ubuntu1) ...
usage: update-rc.d [-n] [-f] <basename> remove
       update-rc.d [-n] <basename> defaults [NN | sNN kNN]
       update-rc.d [-n] <basename> start|stop NN runlvl [runlvl] [...] .
		-n: not really
		-f: force
dpkg: error processing pulseaudio (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 kvm
 dnsmasq
 ntp
 pulseaudio
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

At first I thought it was a bad KVM patch, and logged bugs & issues accordingly, but as the problem is growing in scope, I'm starting to suspect that the issue is more fundamental & may be related to aptitude, or something similarly lower-level.

Some earlier posts/reports on the matter:
* [apt-get/aptitude fails to install KVM via recommended update]("https://bugs.launchpad.net/ubuntu/+source/kvm/+bug/375825")
* [bad patch?]("http://ubuntuforums.org/showthread.php?t=1157830")
* [libvirt error: qemu: unknowm parameter 'boot' after kvm security update]("https://bugs.launchpad.net/ubuntu/+source/kvm/+bug/375937")

Since the issue now does not only apply to the previously KVM-issue, I'm hoping somebody may be able to point out a possible cause to this & a workable solution

Please advise

- J

---

### Post by pytheas22 on 2009-05-24
Try rebooting your machine.  At the grub menu, make sure you're booting into the most recent kernel (it should be the default, but maybe it got changed).  Then run:
```

sudo apt-get update
sudo apt-get upgrade
```

---

### Post by freakalad on 2009-05-24
yip.

been there, done that.
same result (will try again later)

`apt-get -f install` (and various other iterations of the package manager(s)) doesn't float either.

I've been informed that it may all stem from my KVM installation, which I cannot confirm at this time (I'll deal with that later via a full purge & re-install).

In the mean time, is there some way to disregard that package for the time being & continue with the rest per normal, and then get back to it later?

This seems to be a pretty generic issue, and I expect it to be pretty common (most experienced users encountering it at some point in time).
As such, is there a guide that deals with the matter? Most of my googling came up with package-specific fixes/hacks, but does not give a guide or indication on how to deal with the issue in general terms

---

### Post by pytheas22 on 2009-05-25
Sorry that didn't help.

I don't know of a way to tell 'apt-get upgrade' to skip a certain package, although there probably is a way.  Could you just remove --purge kvm first?  Or does that operation fail due to other packaging issues?  If so, you could manually remove the kvm package by following [these instructions]("http://ubuntuforums.org/showpost.php?p=1838138&postcount=3"), then try running apt-get again.
> 
This seems to be a pretty generic issue, and I expect it to be pretty common (most experienced users encountering it at some point in time).
As such, is there a guide that deals with the matter? Most of my googling came up with package-specific fixes/hacks, but does not give a guide or indication on how to deal with the issue in general terms

I've long searched for a straight-forward guide to troubleshooting apt-get, as I've also had my share of strange apt-get behavior, but have never found one, unfortunately.

---

### Post by freakalad on 2009-05-25
Thanks for the info, pytheas22.

I've tried to completely purge it, trim my sources.list WAAAAAY back & reinstall, but still get the same result.
From bitter experience, this particular case points to a faulty post-install script, but what worries me is that this is not only affecting this 1 packag, but have started affecting several more since this particular case has cropped.

In the case of this KVM install, I've managed to (TEMPORARILY) resolve the issue by editing: /var/lib/dpkg/info/kvm.postinst

change the line:
  update-rc.d kvm multiuser >/dev/null
to
  update-rc.d kvm defaults >/dev/null

& then run:
sudo aptitude -f install


This is only a band-aid, & not a solution.
As you've pointed there's no general guide dealing with these issues

---

### Post by Kevbert on 2009-05-25
> **pytheas22 said:**
> 
I don't know of a way to tell 'apt-get upgrade' to skip a certain package, although there probably is a way.  

You can do this with aptitude (don't know about apt-get) with
```
sudo aptitude unmarkauto *packagename*

```

---

### Post by freakalad on 2009-05-25
Sweet!
Thanks for that

---

### Post by freakalad on 2009-06-02
One of the fellas in the [launchpad pointed out]("https://bugs.launchpad.net/ubuntu/+source/kvm/+bug/375825") to me that this issue is likely related to the inclusion of standard debian repositories in my sources.list

I've since removed all references to non-*ubuntu repositories, which has gone some way towards addressing the issue.
Unfortunately the issue had not completely disappeared (though now it is a LOT better)

One possible workaround suggested was to explicitly for the installation of a particular version of a package.
Example that temporarily addressed the KVM issue I had:
`sudo aptitude install kvm=1:62+dfsg-0ubuntu7`

Unfortunately I'm now getting this issue with a cron update/upgrade, despite removing all traces on non-ubuntu repo's:

```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? 
Setting up cron (3.0pl1-100ubuntu2.1) ...
usage: update-rc.d [-n] [-f] <basename> remove
       update-rc.d [-n] <basename> defaults [NN | sNN kNN]
       update-rc.d [-n] <basename> start|stop NN runlvl [runlvl] [...] .
		-n: not really
		-f: force
dpkg: error processing cron (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 cron
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Obviously, I still do not have a good grip on the issue, and information & resources is a bit scattered.

Hope someone is able to provide some insight...

- J

---

### Post by airq on 2009-09-23
Im running 8.04 64bit and have exactly the same problem with **cron 3.0pl1-100ubuntu2.1** as you. The only solution I've found (which unfortunately didn't work for me:() was:
**[https://bugs.launchpad.net/ubuntu/+source/cron/+bug/354589](https://bugs.launchpad.net/ubuntu/+source/cron/+bug/354589)**

There are two solutions described as "Fast" and "Best". The second one I don't understand, maybe someone will explain what to do. The first one caused huge swap usage after *apt-get install cron* and I had to restart my PC...

---

### Post by pytheas22 on 2009-09-23
I believe the second solution refers to fixing the package itself; this is something that has to be done by the Ubuntu packager, not by you.

Is the problem resolved now after rebooting your computer?  I'm not sure why it would have caused lots of swapping, especially after a reboot.

---

### Post by airq on 2009-09-25
> **pytheas22 said:**
> 
I'm not sure why it would have caused lots of swapping, especially after a reboot.
Let me write this once again step by step. After switching to root, I executed the following
> 
mv /usr/sbin/update-rc.d /usr/sbin/update-rc.d-ok
echo "update-rc.d cron defaults" >/usr/sbin/update-rc.d
chmod 755 /usr/sbin/update-rc.d
apt-get install cron
Here the last step caused huge swap usage, so finally I decided to restart...


After reboot I just made (which is tha last step from the launchpad "Fast" solution)
> 
mv /usr/sbin/update-rc.d-ok /usr/sbin/update-rc.d
I had to also execute (propably cus of not completed installation of cron) *dpkg --configure -a* or sth similar, but that was suggested after trying *apt-get upgrade*.

System works as before, the problem is not solved, still cron update/upgrade error appears. Maybe I should not have restarted and just let the system to work on swap memory and see what would happen...? 



BTW I use hardy on two other machines, notebook and PC in my work place, and I dont have such cron problem (everything is updated there). Both are i386 systems so at the begining I thought that it is only AMD64 version issue. But the launchpad which I linked previously shows that this problem can also appear on i386 as well.

---

### Post by pytheas22 on 2009-09-26
Are you having trouble with just the cron package, or is it preventing you from upgrading or installing other packages as well?  If it's just cron, the simplest solution is probably to purge it and reinstall.

---

### Post by fortran01 on 2009-10-08
See my latest comment on that bug.

I think this

```
echo "update-rc.d cron defaults" >/usr/sbin/update-rc.d
```

should be

```
echo "update-rc.d-ok cron defaults" >/usr/sbin/update-rc.d
```


> **airq said:**
> Im running 8.04 64bit and have exactly the same problem with **cron 3.0pl1-100ubuntu2.1** as you. The only solution I've found (which unfortunately didn't work for me:() was:
**[https://bugs.launchpad.net/ubuntu/+source/cron/+bug/354589](https://bugs.launchpad.net/ubuntu/+source/cron/+bug/354589)**

There are two solutions described as "Fast" and "Best". The second one I don't understand, maybe someone will explain what to do. The first one caused huge swap usage after *apt-get install cron* and I had to restart my PC...

---

### Post by airq on 2009-10-15
> **fortran01 said:**
> See my latest comment on that bug.

I think this

```
echo "update-rc.d cron defaults" >/usr/sbin/update-rc.d
```should be

```
echo "update-rc.d-ok cron defaults" >/usr/sbin/update-rc.d
```
The problem with cron error is solved...thanks a lot:)

---

