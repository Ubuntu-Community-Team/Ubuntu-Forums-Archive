---
title: "Bogus 8.04 updates?"
date: 2009-03-19
forum: Installation &amp; Upgrades
---

### Post by wkulecz on 2009-03-19
I've a problem with Update Manager offering apparently bogus updates.

I've 13 of these on two different systems.  I had some problems with "authorization failures" when doing updates a while back and these seemed to appear afterwords.

Examples:

Update Manager offers:
libldap-2.4-2 version: 2.49-0ubuntu0.8.04.2
libtomcat5.5-java version: 5,5,25-5ubuntu1.2

Synaptic says Installed and Latest versions are:
libldap-2.4-2 version: 2.49-0ubuntu0.8.04.1
libtomcat5.5-java version: 5,5,25-5ubuntu1.1

How do I clear the bogus updates from the Update Manager offering?

--wally.

---

### Post by avtolle on 2009-03-19
I'm a bit confused by your post. It appears to me that the two updates you offer as an example being offered through update manager are truly updates to the current versions of those apps now installed. I note that in both cases the proffered updates are .2, while the corresponding installed versions are .1.

What are your precise concerns here?

---

### Post by Dj TweeX on 2009-03-19
synaptic doesnt always displey the latest available.
try running

```
sudo apt-get update
```

after thats done try going back into synaptic & check again.

for the auth fails, id say try changing your password & see if that works.

---

### Post by Kevbert on 2009-03-19
Please post your sources.list file. If you've not changed anything or added any new sources then it may be that your using proposed updates (check System-Admin-Software Sources and check that proposed updates aren't ticked. Otherwise, it may be that your are using a third party site for updates.

---

### Post by wkulecz on 2009-03-19
My point is: the updates being offered by Update Manager will not install and they are not shown in Synaptic's list.

I thought the same apt sources was used for both Update Manager and Synaptic.

On these systems stability is far more important than "latest and greatest" but its essential I stay current with security updates lest I give Ubuntu a black-eye here.

Here is my /etc/apt/sources.list (stripped of comments):
```

deb http://ubuntu.media.mit.edu/ubuntu/ hardy main restricted
deb-src http://ubuntu.media.mit.edu/ubuntu/ hardy multiverse universe #Added by software-properties

deb http://ubuntu.media.mit.edu/ubuntu/ hardy-updates main restricted
deb-src http://ubuntu.media.mit.edu/ubuntu/ hardy-updates restricted main multiverse universe #Added by software-properties


deb http://ubuntu.media.mit.edu/ubuntu/ hardy universe
deb http://ubuntu.media.mit.edu/ubuntu/ hardy-updates universe


deb http://ubuntu.media.mit.edu/ubuntu/ hardy multiverse
deb http://ubuntu.media.mit.edu/ubuntu/ hardy-updates multiverse


deb http://archive.canonical.com/ubuntu hardy partner
# deb-src http://archive.canonical.com/ubuntu hardy partner

deb http://ubuntu.media.mit.edu/ubuntu/ hardy-security main restricted
deb-src http://ubuntu.media.mit.edu/ubuntu/ hardy-security restricted main multiverse universe #Added by software-properties
deb http://ubuntu.media.mit.edu/ubuntu/ hardy-security universe
deb http://ubuntu.media.mit.edu/ubuntu/ hardy-security multiverse

```

I did a change from the installer default "Server for United States" to a specific one when someone suggested a proxy server was the issue for the authorization failures I'd had, made no difference (we have tremendous connectivity to mit.edu here so seemed a good alternate).

I cloned one the systems in question and booted the disk at home, changed back to the the "Main server" repository set and ended up with the same 13 updates offered but not being installed when the update finished. So I've no idea where these .2 "updates" came from and why Update manager is listing them if it can't download and install them.

Any proxy server or firewall issues here are work are not the issue since I wouldn't have had them from home.  My wife runs 8.04 at home, and I've never gotten the authorization failure issues when updating her system (I usually do it the weekend after I've updated the work systems).  I've always kept the "Server for United States" settings as setup by the installer.

Automatic Updates for 6.06 have broken my reboots many times, usually its from changing the raid /dev/md order (I boot raid1 keep data on raid5) or out of sync nvidia modules which kill the Xserver.  Both had me cussing the first time, but I know how to fix them quickly now when it happens.

I tried adding "Proposed" and "Backports" to the clone at home last night, and again the update left the .2 updates as available, but would not install them.

--wally.

---

### Post by Kevbert on 2009-03-19
Sources.list seems fine. The only other thing I can suggest is that you may want to try another server. I've personally had problems in the past here in the UK with the UK servers and have even used a server in the Czech Republic in the past. I'm running 8.04 on both my desktop and laptop.
Synaptic is definitely wrong and it may be that your package status file has been corrupted.
Please try this in terminal:
```
cd /var/lib/dpkg
sudo mv status status-bad
sudo cp status-old status
sudo apt-get update
```
Those packages you have in Update Manager are the ones I'm using. 
See if Synaptic still reports old packages. It may be worth clicking on Reload in Synaptic after trying the above commands and seeing if that is required (as an extra step). If so, it may be a new bug.

---

### Post by wkulecz on 2009-03-19
> **Kevbert said:**
> Sources.list seems fine. The only other thing I can suggest is that you may want to try another server. I've personally had problems in the past here in the UK with the UK servers and have even used a server in the Czech Republic in the past. I'm running 8.04 on both my desktop and laptop.
Synaptic is definitely wrong and it may be that your package status file has been corrupted.
Please try this in terminal:
```
cd /var/lib/dpkg
sudo mv status status-bad
sudo cp status-old status
sudo apt-get update
```
Those packages you have in Update Manager are the ones I'm using. 
See if Synaptic still reports old packages. It may be worth clicking on Reload in Synaptic after trying the above commands and seeing if that is required (as an extra step). If so, it may be a new bug.

I did all this and it didn't change a thing.  Didn't see anything that looked remotely like an error message in the command outputs.


Still not seeing the .2 updates in Synaptic and didn't change a thing -- Update manager shows the thirteen .2 updates but doesn't install any of them.

Downloading multi-megabytes from a foreign country might get me in trouble with the network police here.  First thing I tried was a fresh set of repros that were in the US in a domain we exchange a large amount of data with.


Are you saying the .2 versions really are the most current?

--wally.

---

### Post by Kevbert on 2009-03-20
These are the latest versions I'm using:
libldap-2.4-2 version: 2.49-0ubuntu0.8.04.2
libtomcat5.5-java version: 5,5,25-5ubuntu1.2
and the files are shown as being the latest in Synaptic.
Maybe Synaptic is broken. The only other thing I can suggest is running the following in terminal
```
sudo apt-get install -f
sudo apt-get install --reinstall synaptic
```
The first command will repair any damaged packages - please check if Synaptic still reports the wrong release of packages (you may need to click on reload). The second line will reinstall Synaptic.
If you still have the problem then you need to raise a bug report in [[COLOR="Red"]launchpad[/COLOR]]("https://bugs.launchpad.net"). I've had a look there but didn't see your problem.

---

### Post by wkulecz on 2009-03-20
I saw another thread which seems inactive, but with a similar problem.

Asked for the output of:
apt-get update
apt-get upgrade

So I did these two commands, this got me from 13 to 6 updates in update manager.  So I did them again and that seems to have fixed it, at least for now.

I'm going to reinstall Update Manager and Synaptic and hope for the best.

Thanks for the ideas and verification the versions being updated to were real.

--wally.

---

### Post by wkulecz on 2009-03-24
Had six updates waiting for me today.  Fired up Update Manager and only five installed :(

linux-headers-rt v2.6.24.23.25 doesn't download or install.

Synaptic shows: 
Installed: version 2.6.24.22.24
Current: version 2.6.24.22.24

linux-rt and the other related packages are at version 2.6.24.23.25


Both  Update Manager and Synaptic were reinstalled last week.

The apt-get update, apt-get upgrade trick seems to have fixed it again.

--wally.

---

