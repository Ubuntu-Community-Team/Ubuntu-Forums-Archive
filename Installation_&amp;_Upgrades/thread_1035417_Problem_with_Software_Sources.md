---
title: "Problem with Software Sources"
date: 2009-01-09
forum: Installation &amp; Upgrades
---

### Post by The Afterdark on 2009-01-09
Hi guys.

I've been having a problem recently, and I can't imagine why this would have occurred.  
None of my software sources seem to work.  None.  
I'm using Ubuntu 8.10.  

Here's the error message:

```
W: GPG error: http://ubuntu.media.mit.edu intrepid Release: The following signatures were invalid: NODATA 1 NODATA 2
W: GPG error: http://ubuntu.media.mit.edu intrepid-updates Release: The following signatures were invalid: NODATA 1 NODATA 2
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: http://security.ubuntu.com hardy-security Release: The following signatures were invalid: NODATA 1 NODATA 2

W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: http://security.ubuntu.com intrepid-security Release: The following signatures were invalid: NODATA 1 NODATA 2

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/hardy-security/Release  

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/intrepid-security/Release  

W: Failed to fetch http://ubuntu.media.mit.edu/ubuntu/dists/intrepid/main/binary-i386/Packages.bz2  Sub-process bzip2 returned an error code (2)

W: Failed to fetch http://ubuntu.media.mit.edu/ubuntu/dists/intrepid/restricted/binary-i386/Packages.bz2  Sub-process bzip2 returned an error code (2)

W: Failed to fetch http://ubuntu.media.mit.edu/ubuntu/dists/intrepid/universe/binary-i386/Packages.bz2  Sub-process bzip2 returned an error code (2)

W: Failed to fetch http://ubuntu.media.mit.edu/ubuntu/dists/intrepid/multiverse/binary-i386/Packages.bz2  Sub-process bzip2 returned an error code (2)

W: Failed to fetch http://ubuntu.media.mit.edu/ubuntu/dists/intrepid-updates/main/binary-i386/Packages.bz2  Sub-process bzip2 returned an error code (2)

W: Failed to fetch http://ubuntu.media.mit.edu/ubuntu/dists/intrepid-updates/restricted/binary-i386/Packages.bz2  Sub-process bzip2 returned an error code (2)

W: Failed to fetch http://ubuntu.media.mit.edu/ubuntu/dists/intrepid-updates/universe/binary-i386/Packages.bz2  Sub-process bzip2 returned an error code (2)

W: Failed to fetch http://ubuntu.media.mit.edu/ubuntu/dists/intrepid-updates/multiverse/binary-i386/Packages.bz2  Sub-process bzip2 returned an error code (2)

W: Some index files failed to download, they have been ignored, or old ones used instead.
```


I get that for any server I select, all the time.  
I'm trying to add some eclipse plugins.

Anyone have an idea of how I could fix this?  I have no clue how this could have occurred, since I didn't touch anything in terms of software sources.

Thanks in advance.

---

### Post by taurus on 2009-01-09
Post your /etc/apt/sources.list.

Applications -> Accessories -> Terminal
```
cat /etc/apt/sources.list
```

---

### Post by The Afterdark on 2009-01-10
Oh right, here it is:
```

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://mirrors.acm.jhu.edu/ubuntu/ intrepid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://mirrors.acm.jhu.edu/ubuntu/ intrepid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://mirrors.acm.jhu.edu/ubuntu/ intrepid universe
deb http://mirrors.acm.jhu.edu/ubuntu/ intrepid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://mirrors.acm.jhu.edu/ubuntu/ intrepid multiverse
deb http://mirrors.acm.jhu.edu/ubuntu/ intrepid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb http://archive.canonical.com/ubuntu hardy partner
# deb-src http://archive.canonical.com/ubuntu hardy partner

# Line commented out by installer because it failed to verify:
deb http://security.ubuntu.com/ubuntu hardy-security main restricted
# Line commented out by installer because it failed to verify:
# deb-src http://security.ubuntu.com/ubuntu hardy-security main restricted
# Line commented out by installer because it failed to verify:
deb http://security.ubuntu.com/ubuntu hardy-security universe
# Line commented out by installer because it failed to verify:
# deb-src http://security.ubuntu.com/ubuntu hardy-security universe
# Line commented out by installer because it failed to verify:
deb http://security.ubuntu.com/ubuntu hardy-security multiverse
# Line commented out by installer because it failed to verify:
# deb-src http://security.ubuntu.com/ubuntu hardy-security multiverse
# deb http://ppa.launchpad.net/awn-testing/ubuntu hardy main
deb http://security.ubuntu.com/ubuntu/ intrepid-security restricted main multiverse universe
# deb-src http://ppa.launchpad.net/awn-testing/ubuntu hardy main

```

---

### Post by taurus on 2009-01-10
Try the Main Server in System -> Administration -> Synaptic Package Manager -> Settings -> Repositories.  Don't forget to click the Reload button.

---

### Post by The Afterdark on 2009-01-10
Okay, here we go. 
Errors I got once I reloaded, with the main server:

```
W: GPG error: http://archive.ubuntu.com intrepid Release: The following signatures were invalid: NODATA 1 NODATA 2
W: GPG error: http://archive.ubuntu.com intrepid-updates Release: The following signatures were invalid: NODATA 1 NODATA 2
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: http://security.ubuntu.com hardy-security Release: The following signatures were invalid: NODATA 1 NODATA 2

W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: http://security.ubuntu.com intrepid-security Release: The following signatures were invalid: NODATA 1 NODATA 2

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/hardy-security/Release  

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/intrepid-security/Release  

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/intrepid/restricted/binary-i386/Packages.bz2  Sub-process bzip2 returned an error code (2)

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/intrepid/universe/binary-i386/Packages.bz2  Sub-process bzip2 returned an error code (2)

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/intrepid/multiverse/binary-i386/Packages.bz2  Sub-process bzip2 returned an error code (2)

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/intrepid-updates/restricted/binary-i386/Packages.bz2  Sub-process bzip2 returned an error code (2)

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/intrepid-updates/universe/binary-i386/Packages.bz2  Sub-process bzip2 returned an error code (2)

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/intrepid-updates/multiverse/binary-i386/Packages.bz2  Sub-process bzip2 returned an error code (2)

W: Some index files failed to download, they have been ignored, or old ones used instead.

```


And my sources.list:

```
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://archive.ubuntu.com/ubuntu/ intrepid restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu/ intrepid-updates restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu/ intrepid universe
deb http://archive.ubuntu.com/ubuntu/ intrepid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://archive.ubuntu.com/ubuntu/ intrepid multiverse
deb http://archive.ubuntu.com/ubuntu/ intrepid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb http://archive.canonical.com/ubuntu hardy partner
# deb-src http://archive.canonical.com/ubuntu hardy partner

# Line commented out by installer because it failed to verify:
deb http://security.ubuntu.com/ubuntu hardy-security main restricted
# Line commented out by installer because it failed to verify:
# deb-src http://security.ubuntu.com/ubuntu hardy-security main restricted
# Line commented out by installer because it failed to verify:
deb http://security.ubuntu.com/ubuntu hardy-security universe
# Line commented out by installer because it failed to verify:
# deb-src http://security.ubuntu.com/ubuntu hardy-security universe
# Line commented out by installer because it failed to verify:
deb http://security.ubuntu.com/ubuntu hardy-security multiverse
# Line commented out by installer because it failed to verify:
# deb-src http://security.ubuntu.com/ubuntu hardy-security multiverse
# deb http://ppa.launchpad.net/awn-testing/ubuntu hardy main
deb http://security.ubuntu.com/ubuntu/ intrepid-security restricted multiverse universe
# deb-src http://ppa.launchpad.net/awn-testing/ubuntu hardy main

```


Anything wrong?

---

### Post by The Afterdark on 2009-01-10
Oops.  It got double posted twice for some reason.  And I don't know how to delete this post.

---

### Post by namdung on 2009-01-10
Are u able to access the Internet? If not chk ur IP settings
```
sudo gedit /etc/network/interfaces
```
DNS settings
```
sudo gedit /etc/resolv.conf
```

In *System==>Admin==>Software Sources==>Select Best Server*

I see some Hardy in ur sources list. I reckon u r using Intrepid so remove it.

Check Firewall settings.

---

### Post by The Afterdark on 2009-01-10
> **namdung said:**
> Are u able to access the Internet? If not chk ur IP settings
```
sudo gedit /etc/network/interfaces
```
DNS settings
```
sudo gedit /etc/resolv.conf
```

In *System==>Admin==>Software Sources==>Select Best Server*

I see some Hardy in ur sources list. I reckon u r using Intrepid so remove it.

Check Firewall settings.

Yeah I can access the internet, I'm posting here from the same computer that's having these problems.

I've tried doing the choose best server thing as well.  Still got errors:

```
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: http://security.ubuntu.com intrepid-security Release: The following signatures were invalid: NODATA 1 NODATA 2

W: GPG error: http://ubuntu.media.mit.edu intrepid Release: The following signatures were invalid: NODATA 1 NODATA 2
W: GPG error: http://ubuntu.media.mit.edu intrepid-updates Release: The following signatures were invalid: NODATA 1 NODATA 2
W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/intrepid-security/Release  

W: Failed to fetch http://ubuntu.media.mit.edu/ubuntu/dists/intrepid/restricted/binary-i386/Packages.bz2  Sub-process bzip2 returned an error code (2)

W: Failed to fetch http://ubuntu.media.mit.edu/ubuntu/dists/intrepid/main/binary-i386/Packages.bz2  Sub-process bzip2 returned an error code (2)

W: Failed to fetch http://ubuntu.media.mit.edu/ubuntu/dists/intrepid/universe/binary-i386/Packages.bz2  Sub-process bzip2 returned an error code (2)

W: Failed to fetch http://ubuntu.media.mit.edu/ubuntu/dists/intrepid/multiverse/binary-i386/Packages.bz2  Sub-process bzip2 returned an error code (2)

W: Failed to fetch http://ubuntu.media.mit.edu/ubuntu/dists/intrepid-updates/restricted/binary-i386/Packages.bz2  Sub-process bzip2 returned an error code (2)

W: Failed to fetch http://ubuntu.media.mit.edu/ubuntu/dists/intrepid-updates/main/binary-i386/Packages.bz2  Sub-process bzip2 returned an error code (2)

W: Failed to fetch http://ubuntu.media.mit.edu/ubuntu/dists/intrepid-updates/universe/binary-i386/Packages.bz2  Sub-process bzip2 returned an error code (2)

W: Failed to fetch http://ubuntu.media.mit.edu/ubuntu/dists/intrepid-updates/multiverse/binary-i386/Packages.bz2  Sub-process bzip2 returned an error code (2)

W: Some index files failed to download, they have been ignored, or old ones used instead.
```


I commented out the hardy updates too, but it's still not working.
I can even access ubuntu.media.mit.edu from my firefox web browser.


And in case it helps, this is the output of sudo apt-get update, in the terminal:

```
[user@local: ~]$ sudo apt-get update
Get:1 http://ubuntu.media.mit.edu intrepid Release.gpg [189B]
Ign http://ubuntu.media.mit.edu intrepid/restricted Translation-en_US       
Ign http://ubuntu.media.mit.edu intrepid/main Translation-en_US             
Hit http://security.ubuntu.com intrepid-security Release.gpg                
Ign http://security.ubuntu.com intrepid-security/restricted Translation-en_US
Ign http://ubuntu.media.mit.edu intrepid/universe Translation-en_US
Ign http://ubuntu.media.mit.edu intrepid/multiverse Translation-en_US
Get:2 http://ubuntu.media.mit.edu intrepid-updates Release.gpg [189B]
Ign http://ubuntu.media.mit.edu intrepid-updates/restricted Translation-en_US
Ign http://ubuntu.media.mit.edu intrepid-updates/main Translation-en_US
Ign http://ubuntu.media.mit.edu intrepid-updates/universe Translation-en_US
Ign http://ubuntu.media.mit.edu intrepid-updates/multiverse Translation-en_US
Get:3 http://ubuntu.media.mit.edu intrepid Release [65.9kB]
Ign http://security.ubuntu.com intrepid-security/multiverse Translation-en_US
Ign http://security.ubuntu.com intrepid-security/universe Translation-en_US
Ign http://security.ubuntu.com intrepid-security/main Translation-en_US
Get:4 http://security.ubuntu.com intrepid-security Release [44.0kB]
Get:5 http://ubuntu.media.mit.edu intrepid-updates Release [51.2kB]
Hit http://security.ubuntu.com intrepid-security/restricted Packages              
Hit http://security.ubuntu.com intrepid-security/multiverse Packages
Hit http://security.ubuntu.com intrepid-security/universe Packages
Hit http://security.ubuntu.com intrepid-security/main Packages
Get:6 http://ubuntu.media.mit.edu intrepid/restricted Packages [8408B]
Get:7 http://ubuntu.media.mit.edu intrepid/main Packages [1256kB]
Get:8 http://ubuntu.media.mit.edu intrepid/universe Packages [4542kB]                                                     
Get:9 http://ubuntu.media.mit.edu intrepid/multiverse Packages [199kB]                                                    
Get:10 http://ubuntu.media.mit.edu intrepid-updates/restricted Packages [5770B]                                           
Get:11 http://ubuntu.media.mit.edu intrepid-updates/main Packages [270kB]                                                 
Get:12 http://ubuntu.media.mit.edu intrepid-updates/universe Packages [35.0kB]                                            
Get:13 http://ubuntu.media.mit.edu intrepid-updates/multiverse Packages [3180B]                                           
Fetched 6481kB in 1min21s (79.8kB/s)                                                                                      
Reading package lists... Done

```

---

### Post by avtolle on 2009-01-10
That may have taken care of the problem, as there are no warnings there. Try ```
sudo apt-get upgrade
``` from the terminal and see if you get any error or warning messages with that.

---

### Post by The Afterdark on 2009-01-10
> **avtolle said:**
> That may have taken care of the problem, as there are no warnings there. Try ```
sudo apt-get upgrade
``` from the terminal and see if you get any error or warning messages with that.

No errors with that:

```
[user@local: ~]$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

But when I use the update manager, it still gives me errors.
This also prevents me from using the Synaptic Package Manager as well.

---

### Post by namdung on 2009-01-10
Change the Software Sources to **Main Server**.

Comment out the line with Intrepid security
_deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) intrepid-security_

Remove all Hardy entries.

Post output of
```
sudo apt-get update
```
```
cat /etc/apt/sources.list
```

---

### Post by dsrich on 2009-01-10
I am getting the same messages, but each time I get a "cannot connect to localhost:4001" whici is a privoxy (or other privacy-type proxy) port and I don't apparently have the proper server running.  Any suggestions how to remedy this when I can't get to any repositories, etc.?  I would hope that there is a patch somewhere for this...

---

### Post by avtolle on 2009-01-10
in Synaptic, Preferences, under the Network tab, check to see whether direct connection to the Internet is chosen. If not, select, apply and see if that works.

---

### Post by namdung on 2009-01-10
> **dsrich said:**
> I am getting the same messages, but each time I get a "cannot connect to localhost:4001" whici is a privoxy (or other privacy-type proxy) port and I don't apparently have the proper server running.  Any suggestions how to remedy this when I can't get to any repositories, etc.?  I would hope that there is a patch somewhere for this...

This is a proxy issue. Remove the proxy
```
sudo apt-get remove anon-proxy
```

---

### Post by The Afterdark on 2009-01-10
> **avtolle said:**
> in Synaptic, Preferences, under the Network tab, check to see whether direct connection to the Internet is chosen. If not, select, apply and see if that works.

Okay yeah, that was it.  
I had a proxy on firefox a while back, and I guess it didn't get removed from the package manager when I removed it from firefox.

Thanks for the help everyone!  Everything is working perfectly now.

---

### Post by dsrich on 2009-01-10
Same here - My anon-proxy was apparently crashing, so there was nothing at 4001 to respond.  Since I installed the standard anon-proxy package, I am not sure what the deal is, but I guess it is fixed now.

---

### Post by Spider Fingers on 2010-01-12
I still think this the mostly internet connection problem, this particlular situation had been happening awhile at my work, where a number of ubuntu servers were deployed one after another having the same error again and again. They had to be set to static addresses so any error in networking resulted in this crappy thing.

---

### Post by newbie2 on 2010-01-14
[http://www.webupd8.org/2009/07/ubuntu-sources-list-generator.html](http://www.webupd8.org/2009/07/ubuntu-sources-list-generator.html)
[http://repogen.simplylinux.ch/](http://repogen.simplylinux.ch/)
;)

---

### Post by Lostdrifter0001 on 2010-02-25
Not sure if this is going to help anyone but, I was getting the same error, and it turns out I had a bad stick of RAM. Once I took it out everything started to work as normal.

---

