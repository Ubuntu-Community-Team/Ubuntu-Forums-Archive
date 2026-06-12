---
title: "bad patch?"
date: 2009-05-13
forum: Installation &amp; Upgrades
---

### Post by freakalad on 2009-05-13
I'm running 64-bit Hardy LTS (8.04) on a multi-core Intel box.

Today a "critical security update" came along & I ran with an
`sudo apt-get update && sudo apt-get upgrade` , as I usually do.

I failed to terminate my running KVM, as I assumed the update script would to all those pesky little things for me.

Now my KVM is broken & I'm unable to finish installing this patch.

I get the following when trying to do an upgrade:
```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up kvm (1:62+dfsg-0ubuntu8.1) ...
usage: update-rc.d [-n] [-f] <basename> remove
       update-rc.d [-n] <basename> defaults [NN | sNN kNN]
       update-rc.d [-n] <basename> start|stop NN runlvl [runlvl] [...] .
		-n: not really
		-f: force
dpkg: error processing kvm (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 kvm
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

I think I've seen this before & I don't think it ended very well.
Google's no good here, and I've even tried installing from the [deb package]("http://launchpadlibrarian.net/26653892/kvm_62%2Bdfsg-0ubuntu8.1_amd64.deb")

Is there a way to address this, or a general way of dealing with similar issues when they arise?

Thanks

-J

---

### Post by skymera on 2009-05-13
can you try

```
 sudo apt-get -f upgrade 
```

---

### Post by freakalad on 2009-05-13
Thanks for the snappy reply, skymera

Same results. :(

Even rebooted & tried from recovery session, and completely removed/purged KVM & tried reinstalling it, but I'm not winning.

This is pretty bad, since it's a critical security update (or this incorrect application thereof) that broke my production box. 
Wonder if anyone else have experienced this issue...

I've run this issue by the fella's of the #kvm & #debian , and they're placing the "bug" squarely in *our* court.
Not had much coherent response from the #ubuntu IRC channel

Is there some other way I can force the issue/update/upgrade? Or revert back to something working (the updates described don't affect me that much)

---

### Post by freakalad on 2009-05-13
followed advise from cocooncrash on #ubuntu-za:

edit:
  /var/lib/dpkg/info/kvm.postinst

change the line:
  update-rc.d kvm multiuser >/dev/null
to
  update-rc.d kvm defaults >/dev/null

run:
sudo aptitude -f install

Install seems OK, though I now have other issues that seem parameter-related.
May be addressed here: [http://libvirt.org/drvqemu.html#xmlconfig](http://libvirt.org/drvqemu.html#xmlconfig) (under <boot> element)

---

### Post by freakalad on 2009-05-13
Yet again, BIG props to cocooncrash (michael003)!

The install of KVM was OK eventually, but would not work because libvirt was not updated  & params have changed.

Threw me an error of:
"qemu: unknowm parameter 'boot' in '......"

Therefore had to downgrade KVM again:

aptitude install kvm=1:62+dfsg-0ubuntu7

But I seem to be running again...

So we're dealing not with 1, but 2 pretty bad issues here: the KVM upgrade is buggy, and clients won't work because libvirt has not been updated accordingly

---

### Post by CloneSan on 2009-05-13
I can second the libvirt problem, same here.

Update: seems fixed: [https://bugs.launchpad.net/ubuntu/+source/kvm/+bug/375937](https://bugs.launchpad.net/ubuntu/+source/kvm/+bug/375937)

---

### Post by freakalad on 2009-05-13
faultu KVM/libvirt update has been addressed, but not quite sure if it could be considered fixed

---

### Post by freakalad on 2009-05-21
still an issue, since this forms part of the security updates

```

apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  banshee cairo-dock
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
3 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? 
Setting up kvm (1:62+dfsg-0ubuntu8.2) ...
usage: update-rc.d [-n] [-f] <basename> remove
       update-rc.d [-n] <basename> defaults [NN | sNN kNN]
       update-rc.d [-n] <basename> start|stop NN runlvl [runlvl] [...] .
		-n: not really
		-f: force
dpkg: error processing kvm (--configure):
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
 ntp
 pulseaudio
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

