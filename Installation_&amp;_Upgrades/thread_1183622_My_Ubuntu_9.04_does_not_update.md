---
title: "My Ubuntu 9.04 does not update"
date: 2009-06-10
forum: Installation &amp; Upgrades
---

### Post by bcausevic on 2009-06-10
Hi everybody.
Ever since I upgraded my ubuntu 8.10 to 9.04  it didn't update once. I think this is not the way it should be.

 Can anyone help me please.

Amir

---

### Post by dE_logics on 2009-06-10
When did you update?...then we can say.

---

### Post by bcausevic on 2009-06-10
I Upgraded the same day ubuntu 8.10 told me of Ubuntu 9.04
It must have been over a month ago.

---

### Post by jbruced on 2009-06-10
I believe non-security issues are updated on a weekly basis.

Freaked me out also, I used to pretty much every morning having an update of some kind. If I do it manually(which I do sometimes) seems to be a long time before an automatic is triggered.

---

### Post by Sef on 2009-06-10
Applications > Accessories > Terminal 

then copy and paste in this command:

```
sudo apt-get update && sudo apt-get upgrade
```

Report any errors that you get.

---

### Post by bcausevic on 2009-06-10
I did it and it did somethings. These are the last few lines the terminal wrote:


Setting up linux-libc-dev (2.6.28-13.44) ...
Setting up linux-restricted-modules-common (2.6.28-13.17) ...
update-rc.d: warning: /etc/init.d/linux-restricted-modules-common missing LSB information
update-rc.d: see <http://wiki.debian.org/LSBInitScripts>

Setting up libmagickwand1 (7:6.4.5.4.dfsg1-1ubuntu3.1) ...

Setting up libmagickcore1 (7:6.4.5.4.dfsg1-1ubuntu3.1) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
amir@amir-desktop:~$ 


Is this OK?Is this the way it shoud be?

TNX :-)

---

### Post by Jean-Luc Daviau on 2009-06-10
Ran the compound command with update and upgrade and got somewhere (likely deferred upgrades): thanks!

Then ran sudo apt-get update and got the same-old:
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) jaunty Release.gpg                                                          
  Could not connect to 192.168.0.1:8080 (192.168.0.1), connection timed out
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) jaunty/main Translation-en_CA                                               
  Unable to connect to 192.168.0.1 8080:
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) jaunty-updates Release.gpg                                                  
  Unable to connect to 192.168.0.1 8080:
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) jaunty-updates/main Translation-en_CA                                       
  Unable to connect to 192.168.0.1 8080:
Err [http://archive.canonical.com](http://archive.canonical.com) intrepid Release.gpg                                                        
  Could not connect to 192.168.0.1:8080 (192.168.0.1), connection timed out
Err [http://archive.canonical.com](http://archive.canonical.com) intrepid/partner Translation-en_CA                   
  Unable to connect to 192.168.0.1 8080:
Err [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security Release.gpg                            
  Could not connect to 192.168.0.1:8080 (192.168.0.1), connection timed out
Err [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Translation-en_CA
  Unable to connect to 192.168.0.1 8080:
Reading package lists... Done               
W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/jaunty/Release.gpg](http://ca.archive.ubuntu.com/ubuntu/dists/jaunty/Release.gpg)  Could not connect to 192.168.0.1:8080 (192.168.0.1), connection timed out

W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/jaunty/main/i18n/Translation-en_CA.bz2](http://ca.archive.ubuntu.com/ubuntu/dists/jaunty/main/i18n/Translation-en_CA.bz2)  Unable to connect to 192.168.0.1 8080:

W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/jaunty-updates/Release.gpg](http://ca.archive.ubuntu.com/ubuntu/dists/jaunty-updates/Release.gpg)  Unable to connect to 192.168.0.1 8080:

W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/jaunty-updates/main/i18n/Translation-en_CA.bz2](http://ca.archive.ubuntu.com/ubuntu/dists/jaunty-updates/main/i18n/Translation-en_CA.bz2)  Unable to connect to 192.168.0.1 8080:

W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/intrepid/Release.gpg](http://archive.canonical.com/ubuntu/dists/intrepid/Release.gpg)  Could not connect to 192.168.0.1:8080 (192.168.0.1), connection timed out

W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/intrepid/partner/i18n/Translation-en_CA.bz2](http://archive.canonical.com/ubuntu/dists/intrepid/partner/i18n/Translation-en_CA.bz2)  Unable to connect to 192.168.0.1 8080:

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/jaunty-security/Release.gpg](http://security.ubuntu.com/ubuntu/dists/jaunty-security/Release.gpg)  Could not connect to 192.168.0.1:8080 (192.168.0.1), connection timed out

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/jaunty-security/main/i18n/Translation-en_CA.bz2](http://security.ubuntu.com/ubuntu/dists/jaunty-security/main/i18n/Translation-en_CA.bz2)  Unable to connect to 192.168.0.1 8080:

W: Some index files failed to download, they have been ignored, or old ones used instead.
W: You may want to run apt-get update to correct these problems

Recall something about updater and proxy connections but that had not worked for me. Can anyone direct me? I will search & report back if I find a solution...

---

### Post by ptn107 on 2009-06-10
The update-notifier behavior was changed in jaunty.
> * When there are security updates, Update Manager will open and show
    them (plus any other available updates) within a day.

* When there are non-security updates, Update Manager will open and
    show them *one week* after it was last opened (whether it was last
    opened manually or automatically, and regardless of whether updates
    were actually installed then).[1]

[1] [https://bugs.launchpad.net/ubuntu/+source/update-notifier/+bug/332945](https://bugs.launchpad.net/ubuntu/+source/update-notifier/+bug/332945)

---

### Post by Jean-Luc Daviau on 2009-06-11
Thanks but I removed "Update Manager" (following some other thread) some time ago.

Just now, used "Applications>Add/Remove" to try to re-install it.

Get the message box: "Downloading Package Information", then a long delay followed by:

W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/jaunty/Release.gpg](http://ca.archive.ubuntu.com/ubuntu/dists/jaunty/Release.gpg)  Could not connect to 192.168.0.1:8080 (192.168.0.1), connection timed out

W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/jaunty/main/i18n/Translation-en_CA.bz2](http://ca.archive.ubuntu.com/ubuntu/dists/jaunty/main/i18n/Translation-en_CA.bz2)  Unable to connect to 192.168.0.1 8080:

<Many more like the above>

W: Some index files failed to download, they have been ignored, or old ones used instead.

My computer cannot connect to** 192.168.0.1 8080: **but it accesses the internet, e-mails, this forum, etc.. just fine.  

Appreciate any help you can render. Will continue searching & post solution when found.

---

### Post by Therion on 2009-06-11
> **Jean-Luc Daviau said:**
> 

W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/jaunty/Release.gpg](http://ca.archive.ubuntu.com/ubuntu/dists/jaunty/Release.gpg)  Could not connect to 192.168.0.1:8080 (192.168.0.1), connection timed out

W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/jaunty/main/i18n/Translation-en_CA.bz2](http://ca.archive.ubuntu.com/ubuntu/dists/jaunty/main/i18n/Translation-en_CA.bz2)  Unable to connect to 192.168.0.1 8080:
Can you post the contents of your sources.list file?  

**This link goes to a GPG Key:** [http://ca.archive.ubuntu.com/ubuntu/dists/jaunty/Release.gpg](http://ca.archive.ubuntu.com/ubuntu/dists/jaunty/Release.gpg)

**This one goes to a file download: **[http://ca.archive.ubuntu.com/ubuntu/dists/jaunty/main/i18n/Translation-en_CA.bz2](http://ca.archive.ubuntu.com/ubuntu/dists/jaunty/main/i18n/Translation-en_CA.bz2)

Neither of those links have any business in your sources list, so it appears to me your sources.list file is hosed.

---

### Post by Jean-Luc Daviau on 2009-06-11
I had not noticed it before but this file's comments still refer to 8.10 (below).

Contents of /etc/apt/sources.list are as follows:
```

# deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5)]/ intrepid main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://archive.ubuntu.com/ubuntu/ jaunty main universe

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu/ jaunty-updates main universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
# deb http://mirror.cpsc.ucalgary.ca/mirror/ubuntu.com/packages/ jaunty universe
# deb http://mirror.cpsc.ucalgary.ca/mirror/ubuntu.com/packages/ jaunty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://ca.archive.ubuntu.com/ubuntu/ intrepid-backports main restricted universe multiverse
# deb-src http://ca.archive.ubuntu.com/ubuntu/ intrepid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb http://archive.canonical.com/ubuntu intrepid partner
# deb-src http://archive.canonical.com/ubuntu intrepid partner

# deb http://mirror.cpsc.ucalgary.ca/mirror/ubuntu.com/packages/ jaunty-security main restricted
deb http://security.ubuntu.com/ubuntu/ jaunty-security main universe
deb http://archive.ubuntu.com/ubuntu/ jaunty-proposed main universe
deb http://archive.ubuntu.com/ubuntu/ jaunty-backports main universe
# deb http://mirror.cpsc.ucalgary.ca/mirror/ubuntu.com/packages/ jaunty-security universe

```Thanks for helping out!

---

### Post by ptn107 on 2009-06-18
A default Ubuntu 9.04 sources.list is as follows:
```
deb http://us.archive.ubuntu.com/ubuntu/ jaunty main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ jaunty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ jaunty-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ jaunty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ jaunty universe
deb-src http://us.archive.ubuntu.com/ubuntu/ jaunty universe
deb http://us.archive.ubuntu.com/ubuntu/ jaunty-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ jaunty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ jaunty multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ jaunty multiverse
deb http://us.archive.ubuntu.com/ubuntu/ jaunty-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ jaunty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ jaunty-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ jaunty-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu jaunty partner
# deb-src http://archive.canonical.com/ubuntu jaunty partner

deb http://security.ubuntu.com/ubuntu jaunty-security main restricted
deb-src http://security.ubuntu.com/ubuntu jaunty-security main restricted
deb http://security.ubuntu.com/ubuntu jaunty-security universe
deb-src http://security.ubuntu.com/ubuntu jaunty-security universe
deb http://security.ubuntu.com/ubuntu jaunty-security multiverse
deb-src http://security.ubuntu.com/ubuntu jaunty-security multiverse
```
Remove all sources of 'intrepid'.  Edit your /etc/apt/sources.list to match the previous and run:
```
sudo aptitude update && sudo aptitude full-upgrade
```
If you need to reinstall the update-manager you can type:
```
sudo aptitude install update-manager update-manager-core
```

---

### Post by Jean-Luc Daviau on 2009-06-25
Thanks for the reply.

I pasted the default file into the sources.list file and commented-out all of the older stuff by adding # at the start of each line.

Saved, re-started Ubuntu and ran your first suggestion:
```
jld@JLDHOME:~$ sudo aptitude update && sudo aptitude full-upgrade
[sudo] password for jld: 
Writing extended state information... Done
Err http://us.archive.ubuntu.com jaunty Release.gpg                             
  Could not connect to 192.168.0.1:8080 (192.168.0.1), connection timed out
Err http://us.archive.ubuntu.com jaunty/main Translation-en_CA                  
  Unable to connect to 192.168.0.1 8080:
....
Err http://security.ubuntu.com jaunty-security/multiverse Translation-en_CA
  Unable to connect to 192.168.0.1 8080:
Reading package lists... Done
```

Also tried System > Administration > Update Manager and get the error:
```
W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/jaunty/Release.gpg  Could not connect to 192.168.0.1:8080 (192.168.0.1), connection timed out

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/jaunty/main/i18n/Translation-en_CA.bz2  Unable to connect to 192.168.0.1 8080:

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/jaunty/restricted/i18n/Translation-en_CA.bz2  Unable to connect to 192.168.0.1 8080:

...

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/jaunty-security/multiverse/i18n/Translation-en_CA.bz2  Unable to connect to 192.168.0.1 8080:

W: Some index files failed to download, they have been ignored, or old ones used instead.

```

I am still at a loss and apparently unable to update using:
jld@JLDHOME:~$ sudo apt-get update

It tells me:
W: Some index files failed to download, they have been ignored, or old ones used instead.
**W: You may want to run apt-get update to correct these problems**

:o That's what I was trying to do!!

Again, appreciate any help...   ...BTW my ISP is Sympatico in Toronto, Canada.

---

### Post by Jean-Luc Daviau on 2009-12-02
Thanks for the reply,

Many security upgrades DO work and I use Jaunty every day, but I keep getting this same message from Update Manager, when trying to update brasero for example:
"*Downloading 1 of 22 files*", and eventually:

"W Failed to get ... gpg... jaunty ... port :8080" per my previous post.

I have lived with it as an annoyance but would still like to resolve it. Will wade into gpg again but a little out of steam after all the running around and failure of both "Upgrade Manager" and "Software Sources" tools. 

In answer to the above questions:

1) I have several sources.list files, in /etc/apt -- many with a lock icon on them that I can only open using the "Software Sources" right-click option. That did not solve the problem.

2) In Terminal, did: **/etc/apt$ dir**
apt.conf     sourcesJLD.list  sources.list.d        trustdb.gpg
apt.conf.d   sources.list     sources.list.distUpgrade    trusted.gpg
secring.gpg  sources.list~    sources.list.save        trusted.gpg~

3) In Terminal, ran: **sudo nano /etc/apt/sources.list** to edit (one of) the file(s). Can only get one and it saved it OK, no 'lock icon'. Other sources.list files still exist, with lock icon and contain "hardy" -- these can be opened with "Software Sources" but it ultimately does not change THEM, only the one I can get to. Perhaps there is only one and the various extensions ~ implement the 'lock'?

4) sudo nano /etc/apt/sources.list.distUpgrade shows a whole pile of "Intrepid" mentions but perhaps this does not affect Jaunty.

5) sources.list contents are as shown below:
```
deb http://archive.canonical.com/ubuntu jaunty partner
deb-src http://archive.canonical.com/ubuntu jaunty partner
deb http://security.ubuntu.com/ubuntu jaunty-security restricted main multiverse universe
deb-src http://security.ubuntu.com/ubuntu jaunty-security restricted main multiverse universe
# deb http://us.archive.ubuntu.com/ubuntu/ jaunty restricted main multiverse universe
# deb-src http://us.archive.ubuntu.com/ubuntu/ jaunty restricted main multiverse universe
deb http://us.archive.ubuntu.com/ubuntu/ jaunty-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ jaunty-backports main restricted universe multiverse
deb http://us.archive.ubuntu.com/ubuntu/ jaunty-updates restricted main multiverse universe
# deb-src http://us.archive.ubuntu.com/ubuntu/ jaunty-updates restricted main multiverse universe
deb http://archive.ubuntu.com/ubuntu/ jaunty main universe restricted multiverse
```

Again, thanks for any help & will write back...   ...will read the gpg in the link (above) in thread again and see if something comes to me...

---

### Post by Jean-Luc Daviau on 2009-12-02
Use Jaunty every day and it udpdates security stuff fine, not brasero, Java 6 and other stuff: annoying/puzzling...

The sources.list file looks OK to me: I used Terminal and **sudo nano /etc/apt/sources.list** to get its contents:

```
  GNU nano 2.0.9                           File: /etc/apt/sources.list                                                            

deb http://archive.canonical.com/ubuntu jaunty partner
deb-src http://archive.canonical.com/ubuntu jaunty partner
deb http://security.ubuntu.com/ubuntu jaunty-security restricted main multiverse universe
deb-src http://security.ubuntu.com/ubuntu jaunty-security restricted main multiverse universe
# deb http://us.archive.ubuntu.com/ubuntu/ jaunty restricted main multiverse universe
# deb-src http://us.archive.ubuntu.com/ubuntu/ jaunty restricted main multiverse universe
deb http://us.archive.ubuntu.com/ubuntu/ jaunty-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ jaunty-backports main restricted universe multiverse
deb http://us.archive.ubuntu.com/ubuntu/ jaunty-updates restricted main multiverse universe
# deb-src http://us.archive.ubuntu.com/ubuntu/ jaunty-updates restricted main multiverse universe
deb http://archive.ubuntu.com/ubuntu/ jaunty main universe restricted multiverse

```

There are other sources.list files (with different extensions, one of which sources.list~ mentions Intrepid, a version I had earlier):
**/etc/apt$ dir**
apt.conf    secring.gpg      sources.list   sources.list.d          sources.list.save  trusted.gpg
apt.conf.d  sourcesJLD.list  sources.list~  sources.list.distUpgrade  trustdb.gpg     trusted.gpg~

Should I erase or rename some of these other files?

Again, thanks for the feedback!

---

