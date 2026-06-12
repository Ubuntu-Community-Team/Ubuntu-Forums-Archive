---
title: "ufw will not go away from autostart"
date: 2008-07-13
forum: General Help
---

### Post by ephracis on 2008-07-13
Hi there,

I recently played around with ufw in Hardy. It was not for me, though so I turned it of with **sudo ufw disable** and then **sudo /etc/init.d/ufw stop**

Problem now is that whenever I restart the computer ufw gets started, so I have to turn it of manually every time. First of all: why? and also: how do I get rid of this annoying thing?

---

### Post by brian_p on 2008-07-13
> **ephracis said:**
> Hi there,

I recently played around with ufw in Hardy. It was not for me, though so I turned it of with **sudo ufw disable** and then **sudo /etc/init.d/ufw stop**

Problem now is that whenever I restart the computer ufw gets started, so I have to turn it of manually every time. First of all: why? and also: how do I get rid of this annoying thing?

All the scripts in /etc/init.d are run during booting. A permanent solution is 

```
sudo apt-get remove --purge ufw

```

---

### Post by TonyGould on 2008-07-13
> **ephracis said:**
> 
First of all: why? 

The sysvconfig program lists all the services that get started up. I guess you could install sysvconfig and uncheck it there. And you could get rid of some other unnecessary stuff too.

---

### Post by lswb on 2008-07-13
Try editing /etc/ufw/ufw.conf to include this line:

ENABLED=no

(Comment or delete any other line beginning with ENABLED)

---

### Post by ephracis on 2008-07-14
Ok, so let's start here:
> 
$ **sudo ufw disable**
[sudo] password for ephracis: 
Firewall stopped and disabled on system startup

I find it bad practice that it tells me it is disable on startup if it isn't and it's not a bug (which it isn't if it's supposed to still be inside /etc/init.d, right?)

Secondly:
> 
$ **cat /etc/ufw/ufw.conf**
# /etc/ufw/ufw.conf
# 

# set to yes to start on boot
ENABLED=no

So still bad practice if the file tells me it will prevent start on boot when it doesn't.

Third:
> 
$ **sudo apt-get remove ufw**
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  *_ubuntu-standard_* ufw
0 upgraded, 0 newly installed, 2 to remove and 0 not upgraded.
After this operation, 262kB disk space will be freed.
Do you want to continue [Y/n]? n
Abort.
$ **apt-cache show ubuntu-standard**
Package: ubuntu-standard
Priority: standard
Section: metapackages
Installed-Size: 52
Maintainer: Matt Zimmerman <mdz@ubuntu.com>
Architecture: amd64
Source: ubuntu-meta
Version: 1.102
Depends: at, cpio, cron, dmidecode, dnsutils, dosfstools, ed, file, ftp, hdparm, info, inputattach, iptables, logrotate, lshw, lsof, ltrace, man-db, memtest86+, mime-support, nano, parted, popularity-contest, psmisc, rsync, strace, time, ufw, w3m, wget
Recommends: apparmor-utils, bash-completion, command-not-found, fdutils, friendly-recovery, iputils-arping, iputils-tracepath, manpages, mlocate, mtr-tiny, ntfs-3g, openssh-client, ppp, pppconfig, pppoeconf, reiserfsprogs, tcpdump, telnet, update-manager-core, uuid-runtime
Filename: pool/main/u/ubuntu-meta/ubuntu-standard_1.102_amd64.deb
Size: 24716
MD5sum: 4db68ded4a09347c4b60334bda34620b
SHA1: 31ae6f2e98514f93faf0218f7c7790047a68d300
SHA256: 0965032d19ee82171be418d925c1d2f0c2f2392359d84b267025143b5666aa57
Description: The Ubuntu standard system
 This package depends on all of the packages in the Ubuntu standard system.
 This set of packages provides a comfortable command-line Unix-like
 environment.
 .
 It is also used to help ensure proper upgrades, so it is [B][U][I]recommended that
 it not be removed.[/I][/U][/B]
Bugs: mailto:ubuntu-users@lists.ubuntu.com
Origin: Ubuntu
Task: standard

So that should *not* be an option, right?

I will try sysvconfig tho and check it out. Still, I think this area should be worked upon a little bit more, tho.

---

### Post by brian_p on 2008-07-14
> **ephracis said:**
> 

Third:

```
sudo apt-get remove ufw
```


So that should *not* be an option, right?

Having ubuntu-standard depend on uwf is a bug. In any event, ubuntu-standard is a metapackage and removing a metapackage does no harm. The recommendation is with an eye to upgrading from Hardy to the next release and can be ignored. So removing ufw from the system is an option.

All that ufw does on start up is load firewall rules so lswb's suggestion is a perfectly good one. However, if you  do not want to follow that piece of advice and want to keep it on the system there is always:

```
sudo update-rc.d -f ufw remove
```

---

### Post by ephracis on 2008-07-14
> **brian_p said:**
> Having ubuntu-standard depend on uwf is a bug.
Should I file a bug report on that?

> **brian_p said:**
> In any event, ubuntu-standard is a metapackage and removing a metapackage does no harm. The recommendation is with an eye to upgrading from Hardy to the next release and can be ignored. So removing ufw from the system is an option.
I prefer to follow recommendations since I tend to trust them. The problem still is not that ufw is installed, it's that it tells me "hey, now I am not gonna autostart anymore", and it's lying to me.

Should I file a bug report on that, too?

---

### Post by brian_p on 2008-07-14
> **ephracis said:**
> Should I file a bug report on that?

Someone already has.

> I prefer to follow recommendations since I tend to trust them. The problem still is not that ufw is installed, it's that it tells me "hey, now I am not gonna autostart anymore", and it's lying to me.

Should I file a bug report on that, too?

ufw is started, it loads the firewall rules (or not, depending on how it is configured) and exits. That's the way things are meant to be. There is no lie. There is no bug to report.

---

### Post by ephracis on 2008-07-15
> **brian_p said:**
> 
ufw is started, it loads the firewall rules (or not, depending on how it is configured) and exits. That's the way things are meant to be. There is no lie. There is no bug to report.
Sounds great, just that in my case it doesn't exists. So in the case of something not doing what it is supposed to do, that's a bug, isn't it?

The thing is that I notice this because I configured ufw to block all outgoing traffic. So when I rebooted the computer I get no network traffic. I then shut down ufw manually and I can send traffic again.

I cannot get over the fact that ufw told me (in two places) that it would not autostart anymore, yet it does. Am I the only one seeing the problem here? What am I missing? Should it be this way?

---

### Post by lswb on 2008-07-15
"I cannot get over the fact that ufw told me (in two places) that it would not autostart anymore, yet it does. Am I the only one seeing the problem here? What am I missing? Should it be this way?"

No it should not be this way. Either of the actions of issuing the command "sudo ufw disable", or editing /etc/ufw/ufw.conf to have the line "ENABLED=no" are adequate to stop ufw from running at boot. Is is posible that somewhere you have included ufw in a script or service configuration file that is starting it later in the boot process? Or possible edited /etc/init.d/ufw ?

After a fresh reboot, open a terminal and type 

   pgrep -fl ufw

If you get any results post them here.
---------------------------------------
"Having ubuntu-standard depend on ufw is a bug."

Including ufw in the ubuntu-standard package was presumably a consious decision by the developers so it is not a bug. The ubuntu-standard package "depends" on ufw, so if ufw or any of the other packages it depends on are removed, then ubuntu-standard must be removed as well. Removing ubuntu-standard (provided it was configured properly) will NOT remove any of the packages that it installed, they must be removed separately. Perhaps it will help clarify to imagine that the dependency was reversed, that is, suppose that ufw depended on ubuntu-standard instead of the other way around. Then removing ubuntu-standard WOULD cause ufw to be removed, but removing ufw would not remove ubuntu-standard.

---

### Post by brian_p on 2008-07-15
> **lswb said:**
> 
After a fresh reboot, open a terminal and type 

   pgrep -fl ufw

If you get any results post them here.

I have a feeling you think ufw runs as a daemon.

> "Having ubuntu-standard depend on ufw is a bug."

Including ufw in the ubuntu-standard package was presumably a consious decision by the developers so it is not a bug.

You need to read the bug report and its resolution more carefully.

---

### Post by lswb on 2008-07-15
> **brian_p said:**
> I have a feeling you think ufw runs as a daemon.

You're right, I didn't do my homework on that one. But it still should not load any iptable rules if the OP did as he described, correct?



> **brian_p said:**
> You need to read the bug report and its resolution more carefully.

I didn't read all the bug reports for ufw, do you know the number or some keywords I could search for to find the one relevant here?

---

### Post by brian_p on 2008-07-15
> **lswb said:**
> You're right, I didn't do my homework on that one. But it still should not load any iptable rules if the OP did as he described, correct?

I'd agree and am getting a bit lost as to what is happening with ephracis or what he thinks is happening.

> I didn't read all the bug reports for ufw, do you know the number or some keywords I could search for to find the one relevant here?

[http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg919959.html](http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg919959.html)

and follow the link there.

---

### Post by ephracis on 2008-07-16
I haven't done anything special. Just enabled ufw and added a "deny all" rule just to try it out. Now I cannot disable it. I could of course remove the "deny all" rule and everything will be fine, but I still want to know why I cannot disable it from loading the rules at boot.

No special scripts, I haven't touched any of the files inside /etc/init.d, nothing like that.

To clarify for you all...

What happens: ufw rules gets loaded when I boot, even after I have disabled it (both via the ufw command and via the ufw.conf file)
What I expect to happen: ufw will not load at boot and disable all network traffic.

---

