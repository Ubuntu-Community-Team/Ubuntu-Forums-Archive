---
title: "apt-get &amp; update errors"
date: 2009-02-16
forum: Installation &amp; Upgrades
---

### Post by Rex Regis on 2009-02-16
I am new to Linux and Ubuntu from Windows Vista.  I have installed V. 8.10.  After installing the icon in the task-bar informed me that I had 200 odd updates, so I started downloading installing them.  After the installation (which was successful), the following window was shown:

> Problem during package list update. The package list update failed with a authentication failure. This usually happens behind a network proxy server. Please try to click on the "Run this action now" button to correct the problem or update the list manually by running Update Manager and clicking on "Check".

So I clicked the Run This Action Now button, and I got the following error message:

> A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid Release: The following signatures were invalid: NODATA 2

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/intrepid/Release](http://us.archive.ubuntu.com/ubuntu/dists/intrepid/Release) 

I also get this when I try to refresh the Synaptic package list.

The next thing is that when I try to install apps via apt-get in the terminal, no matter what app I try to get I always get the response:

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package *package name*
```

I do have access to the Internet no problem.  Is anyone able to shed some light on this matter?  The following is my sources list:

```
deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5)]/ intrepid main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://us.archive.ubuntu.com/ubuntu/ intrepid main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ intrepid-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ intrepid universe
deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid universe
deb http://us.archive.ubuntu.com/ubuntu/ intrepid-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ intrepid multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid multiverse
deb http://us.archive.ubuntu.com/ubuntu/ intrepid-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ intrepid-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb http://archive.canonical.com/ubuntu intrepid partner
deb-src http://archive.canonical.com/ubuntu intrepid partner

deb http://security.ubuntu.com/ubuntu intrepid-security main restricted
deb-src http://security.ubuntu.com/ubuntu intrepid-security main restricted
deb http://security.ubuntu.com/ubuntu intrepid-security universe
deb-src http://security.ubuntu.com/ubuntu intrepid-security universe
deb http://security.ubuntu.com/ubuntu intrepid-security multiverse
deb-src http://security.ubuntu.com/ubuntu intrepid-security multiverse
```

Thanks :)

---

### Post by bapoumba on 2009-02-17
You are currently using the us repos. Please try to change it to the main repos (Sytem > Administration > Software Sources > Choose main server). Sometimes, other repos are a little back the main ones.

---

### Post by Rex Regis on 2009-02-17
No, this gives the same thing only the error message is longer:

> W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid Release: The following signatures were invalid: NODATA 2

W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates Release: The following signatures were invalid: NODATA 2

W: GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-security Release: The following signatures were invalid: NODATA 2
W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/intrepid/Release](http://archive.ubuntu.com/ubuntu/dists/intrepid/Release)  

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/intrepid-updates/Release](http://archive.ubuntu.com/ubuntu/dists/intrepid-updates/Release)  

W: Some index files failed to download, they have been ignored, or old ones used instead.

this is really annoying, because I can only install applications from directly downloading .deb packages to my desktop, and then installing them.  Does anyone have any other ideas for a solution? :neutral:

---

### Post by Rex Regis on 2009-02-17
OK, quick update.  Since changing the server as was suggested to me, the apt-get now works.  However, the error in the post above is still given when trying to check for updates, or reload the package manager etc.

---

### Post by Rex Regis on 2009-02-17
Sorry about this folks!  The above post is only partly true.  I successfully installed Amarok using apt-get, but other things, like for example the *compizconfig-settings-manager* did not work, so it seems to be on and off. ](*,)

---

### Post by bapoumba on 2009-02-17
Hmm.
Could you please post the complete output to:
```
sudo apt-get update
```

Would you happen to be behind a proxy?

Edit: looking around on the intarnetz, you may want to try this first:
```
sudo dpkg --configure -a
sudo apt-get update
```

---

### Post by Rex Regis on 2009-02-17
Thanks a lot for your help.  I have had NO experience with networks etc until I recently came to college (which is where I am now)  So your question about the proxy threw me off since I didn't really know anything about it.  Anyway, I got in touch with the IT manager here at the college to find out the answer to your question, and he took a look at my setup and solved all the problems for me, so all now works just fine!  Thanks for your help!

---

### Post by bapoumba on 2009-02-18
Cool, glad to see you got it to work :)

---

### Post by rocheteau on 2009-03-09
Hi,
In a related issue (should I have posted this in its own thread?): bapoumba indicates how to change to the main repository server using the GUI utility. How do you do that via command line? I am having a similar problem on my server machine and I believe that switching to the main server would solve it (i.e. I had the same problem on my GUI machine and it was fixed after switching). 
Thanks in advance, R.

---

### Post by rocheteau on 2009-03-09
Hi, 
How do you switch from the current repository server to the main server via the command line. A few months back such a switch corrected a similar problem on my Ubuntu desktop machine. Now my Ubuntu LAMP server is suffering from the same problem. Should I have posted this in its own thread?
Thanks in advance, R.

---

### Post by rocheteau on 2009-03-09
Sorry about the double post. I thought the first had been lost during a loss of connection.
R.

---

### Post by cubeist on 2009-03-09
You can change source repositories from the command line by opening your *sources.list* file in your favorite editor (nano, vim), like this:
```
sudo nano /etc/apt/sources.list
```

Also, since the sources list is an essential part of your system, don't forget to back it up before editing on a non-gui system (like a headless server!)

```
sudo cp /etc/apt/sources.list /etc/apt/sources.list.backup_mar09
```

---

### Post by bapoumba on 2009-03-09
> **rocheteau said:**
> Hi,
In a related issue (should I have posted this in its own thread?): bapoumba indicates how to change to the main repository server using the GUI utility. How do you do that via command line? I am having a similar problem on my server machine and I believe that switching to the main server would solve it (i.e. I had the same problem on my GUI machine and it was fixed after switching). 
Thanks in advance, R.

You need to edit the /etc/apt/sources.list and change the repo url. Could you please post the output of:
```
cat /etc/apt/sources.list
```
on the machine you want to modify ?

Edit: sorry, did not see the second page :)

---

### Post by rocheteau on 2009-03-09
Thanks very much for getting back to me. The contents of /etc/apt/sources.list are:
> # deb cdrom:[Ubuntu-Server 6.06.1 _Dapper Drake_ - Release i386 (20060807.1)]/ dapper main restricted
#deb cdrom:[Ubuntu-Server 6.06.1 _Dapper Drake_ - Release i386 (20060807.1)]/ dapper main restricted
# Line commented out by installer because it failed to verify:
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) dapper main restricted
# Line commented out by installer because it failed to verify:
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) dapper main restricted
## Major bug fix updates produced after the final release of the
## distribution.
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) dapper universe
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) dapper universe
## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
# Line commented out by installer because it failed to verify:
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
# Line commented out by installer because it failed to verify:
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe


---

### Post by bapoumba on 2009-03-09
As posted by cubeist, you can use nano, a small text editor working from the terminal.
```
sudo nano -B /etc/apt/sources.list
```
Then remove the ca. from the url, for ex:
```
deb http://[COLOR="Red"]ca.[/COLOR]archive.ubuntu.com/ubuntu/ dapper main restricted
```
for all instances.
Save with ctrl -O
Exit with ctrl -X

Then reload the file:
```
sudo apt-get update
```
All set :)

---

### Post by rocheteau on 2009-03-09
I changed the sources.list file as you suggested i.e. deletion of "ca.". After sudo apt-get update I get the following output (thanks again for your help):
> Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release.gpg [79B]
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg [189B] 
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates Release.gpg [79B]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release
Get:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports Release.gpg [79B]
Get:5 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release [79B]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages
Get:6 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates Release [79B]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Sources
Get:7 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports Release [79B]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports Release
Get:8 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Packages [79B]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Sources
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Packages
  Sub-process bzip2 returned an error code (2)
Get:9 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Packages [79B]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Packages
  Sub-process bzip2 returned an error code (2)
Get:10 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Sources [79B]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Sources
  Sub-process bzip2 returned an error code (2)
Get:11 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Sources [79B]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Sources
  Sub-process bzip2 returned an error code (2)
Get:12 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe Packages [79B]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe Packages
  Sub-process bzip2 returned an error code (2)
Get:13 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe Sources [79B]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe Sources
  Sub-process bzip2 returned an error code (2)
Get:14 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/main Packages [79B]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/main Packages
  Sub-process bzip2 returned an error code (2)
Get:15 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/restricted Packages [79B]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/restricted Packages
  Sub-process bzip2 returned an error code (2)
Get:16 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/main Sources [79B]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/main Sources
  Sub-process bzip2 returned an error code (2)
Get:17 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/restricted Sources [79B]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/restricted Sources
  Sub-process bzip2 returned an error code (2)
Get:18 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/main Packages [79B]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/main Packages
  Sub-process bzip2 returned an error code (2)
Get:19 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/restricted Packages [79B]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/restricted Packages
  Sub-process bzip2 returned an error code (2)
Get:20 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/universe Packages [79B]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/universe Packages
  Sub-process bzip2 returned an error code (2)
Get:21 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/multiverse Packages [79B]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/multiverse Packages
  Sub-process bzip2 returned an error code (2)
Get:22 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/main Sources [79B]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/main Sources
  Sub-process bzip2 returned an error code (2)
Get:23 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/restricted Sources [79B]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/restricted Sources
  Sub-process bzip2 returned an error code (2)
Get:24 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/universe Sources [79B]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/universe Sources
  Sub-process bzip2 returned an error code (2)
Get:25 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/multiverse Sources [79B]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/multiverse Sources
  Sub-process bzip2 returned an error code (2)
Fetched 1897B in 3s (549B/s)
Reading package lists...
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper/main/binary-i386/Packages.bz2](http://archive.ubuntu.com/ubuntu/dists/dapper/main/binary-i386/Packages.bz2)  Sub-process bzip2 returned an error code (2)
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper/restricted/binary-i386/Packages.bz2](http://archive.ubuntu.com/ubuntu/dists/dapper/restricted/binary-i386/Packages.bz2)  Sub-process bzip2 returned an error code (2)
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper/main/source/Sources.bz2](http://archive.ubuntu.com/ubuntu/dists/dapper/main/source/Sources.bz2)  Sub-process bzip2 returned an error code (2)
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper/restricted/source/Sources.bz2](http://archive.ubuntu.com/ubuntu/dists/dapper/restricted/source/Sources.bz2)  Sub-process bzip2 returned an error code (2)
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper/universe/binary-i386/Packages.bz2](http://archive.ubuntu.com/ubuntu/dists/dapper/universe/binary-i386/Packages.bz2)  Sub-process bzip2 returned an error code (2)
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper/universe/source/Sources.bz2](http://archive.ubuntu.com/ubuntu/dists/dapper/universe/source/Sources.bz2)  Sub-process bzip2 returned an error code (2)
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper-updates/main/binary-i386/Packages.bz2](http://archive.ubuntu.com/ubuntu/dists/dapper-updates/main/binary-i386/Packages.bz2)  Sub-process bzip2 returned an error code (2)
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper-updates/restricted/binary-i386/Packages.bz2](http://archive.ubuntu.com/ubuntu/dists/dapper-updates/restricted/binary-i386/Packages.bz2)  Sub-process bzip2 returned an error code (2)
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper-updates/main/source/Sources.bz2](http://archive.ubuntu.com/ubuntu/dists/dapper-updates/main/source/Sources.bz2)  Sub-process bzip2 returned an error code (2)
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper-updates/restricted/source/Sources.bz2](http://archive.ubuntu.com/ubuntu/dists/dapper-updates/restricted/source/Sources.bz2)  Sub-process bzip2 returned an error code (2)
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper-backports/main/binary-i386/Packages.bz2](http://archive.ubuntu.com/ubuntu/dists/dapper-backports/main/binary-i386/Packages.bz2)  Sub-process bzip2 returned an error code (2)
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper-backports/restricted/binary-i386/Packages.bz2](http://archive.ubuntu.com/ubuntu/dists/dapper-backports/restricted/binary-i386/Packages.bz2)  Sub-process bzip2 returned an error code (2)
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper-backports/universe/binary-i386/Packages.bz2](http://archive.ubuntu.com/ubuntu/dists/dapper-backports/universe/binary-i386/Packages.bz2)  Sub-process bzip2 returned an error code (2)
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper-backports/multiverse/binary-i386/Packages.bz2](http://archive.ubuntu.com/ubuntu/dists/dapper-backports/multiverse/binary-i386/Packages.bz2)  Sub-process bzip2 returned an error code (2)
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper-backports/main/source/Sources.bz2](http://archive.ubuntu.com/ubuntu/dists/dapper-backports/main/source/Sources.bz2)  Sub-process bzip2 returned an error code (2)
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper-backports/restricted/source/Sources.bz2](http://archive.ubuntu.com/ubuntu/dists/dapper-backports/restricted/source/Sources.bz2)  Sub-process bzip2 returned an error code (2)
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper-backports/universe/source/Sources.bz2](http://archive.ubuntu.com/ubuntu/dists/dapper-backports/universe/source/Sources.bz2)  Sub-process bzip2 returned an error code (2)
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper-backports/multiverse/source/Sources.bz2](http://archive.ubuntu.com/ubuntu/dists/dapper-backports/multiverse/source/Sources.bz2)  Sub-process bzip2 returned an error code (2)
W: GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release: Unknown error executing gpgv
W: GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates Release: Unknown error executing gpgv
W: GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports Release: Unknown error executing gpgv
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.


---

### Post by bapoumba on 2009-03-10
I'm not with my ubuntu system right now, so there are things I cannot check.
Looking around for the error message, could you please:
- check your system date and time
- run the update again (might have been a server sync error)
- try 
```
sudo apt-get update -o Acquire::http::No-Cache=true
```
[https://bugs.launchpad.net/ubuntu/+source/apt/+bug/24234](https://bugs.launchpad.net/ubuntu/+source/apt/+bug/24234)

---

### Post by rocheteau on 2009-03-10
I checked my system time:
date --> Tue Mar 10 13:44:55 MDT 2009
which is correct for Mountain DT but I'm on the Pacific Coast - does that matter?
I ran "sudo apt-get update -o Acquire::http::No-Cache=true" but got the same output as my previous message. 
Thanks again for your help, R.

---

### Post by bapoumba on 2009-03-10
Hmm, would you happen to be behind a proxy? In particular an ISA proxy?

---

### Post by rocheteau on 2009-03-11
I'm a bioinformatician in a large Canadian government research department. We are behind a firefall/proxy. My "yum installs" work fine on my Fedora Core machine if that is any help. I'm mostly a programmer but I will fire off an email to one of the Linux IT guys and see what he thinks.
Thanks again, R.

---

### Post by bapoumba on 2009-03-11
You're welcome.

When I was using dapper, I used to set up the apt.conf file to update behind my university proxy (squid proxy, no authentication):
[http://linux.die.net/man/5/apt.conf](http://linux.die.net/man/5/apt.conf)
The Acquire group is the one to look at. For ISA proxy, you'll probably need ntlmaps (never used it, and the set up is not that intuitive).

Was it working before? If so, it cannot be the proxy settings, unless you changed them or the research department proxy configuration got changed. FYI, when my univ started to use an automatic proxy (something .pac), I could not update/upgrade. They told me to use the old proxy for that.

I'm not sure it is a proxy problem, you should not be able to hit any of the repos. I'll keep looking for older reports with your errors :)

---

### Post by rocheteau on 2009-03-11
I used to be able to use apt-get with no problem but that was over a year ago. I have been almost exclusively on my Fedora machines since then and as I said yum is working fine. I probably won't hear back from my IT guy (3 time zones later than here) until tomorrow. I did, however, test an "apt-get update" on my other Ubuntu LAMP server (7.04) which also did not work (both with and without your suggestion of deleting "us.". Thanks again for your help - I'll thoroughly go through the link you suggest. The output (different from the first machine and I hope not a whole second issue) from the second machine:
> Ign cdrom://Ubuntu-Server 7.04 _Feisty Fawn_ - Release i386 (20070415) feisty Release.gpg
Ign cdrom://Ubuntu-Server 7.04 _Feisty Fawn_ - Release i386 (20070415) feisty/main Translation-en_US
Ign cdrom://Ubuntu-Server 7.04 _Feisty Fawn_ - Release i386 (20070415) feisty/restricted Translation-en_US
Ign cdrom://Ubuntu-Server 7.04 _Feisty Fawn_ - Release i386 (20070415) feisty Release    
Ign cdrom://Ubuntu-Server 7.04 _Feisty Fawn_ - Release i386 (20070415) feisty/main Packages
Ign cdrom://Ubuntu-Server 7.04 _Feisty Fawn_ - Release i386 (20070415) feisty/restricted Packages
Err cdrom://Ubuntu-Server 7.04 _Feisty Fawn_ - Release i386 (20070415) feisty/main Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Err cdrom://Ubuntu-Server 7.04 _Feisty Fawn_ - Release i386 (20070415) feisty/restricted Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release.gpg                               
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Translation-en_US                    
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty Release.gpg
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/main Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/universe Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/multiverse Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates Release.gpg
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/main Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports Release.gpg
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/main Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Sources
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Sources
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/universe Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/multiverse Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty Release   
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates Release
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Sources
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Sources
Err [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Packages
  404 Not Found
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports Release
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/main Packages
Err [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Packages
  404 Not Found
Err [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Sources
  404 Not Found
Err [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Sources
  404 Not Found
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/restricted Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/main Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/restricted Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/universe Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/universe Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/multiverse Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/multiverse Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/main Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/restricted Packages
Err [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Packages
  404 Not Found
Err [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Sources
  404 Not Found
Err [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Packages
  404 Not Found
Err [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Sources
  404 Not Found
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/main Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/restricted Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/main Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/restricted Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/universe Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/multiverse Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/main Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/restricted Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/universe Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/multiverse Sources
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/main Packages
  404 Not Found [IP: 91.189.88.46 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/restricted Packages
  404 Not Found [IP: 91.189.88.46 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/main Sources
  404 Not Found [IP: 91.189.88.46 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/restricted Sources
  404 Not Found [IP: 91.189.88.46 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/universe Packages
  404 Not Found [IP: 91.189.88.46 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/universe Sources
  404 Not Found [IP: 91.189.88.46 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/multiverse Packages
  404 Not Found [IP: 91.189.88.46 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/multiverse Sources
  404 Not Found [IP: 91.189.88.46 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/main Packages
  404 Not Found [IP: 91.189.88.46 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/restricted Packages
  404 Not Found [IP: 91.189.88.46 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/main Sources
  404 Not Found [IP: 91.189.88.46 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/restricted Sources
  404 Not Found [IP: 91.189.88.46 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/main Packages
  404 Not Found [IP: 91.189.88.46 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/restricted Packages
  404 Not Found [IP: 91.189.88.46 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/universe Packages
  404 Not Found [IP: 91.189.88.46 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/multiverse Packages
  404 Not Found [IP: 91.189.88.46 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/main Sources
  404 Not Found [IP: 91.189.88.46 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/restricted Sources
  404 Not Found [IP: 91.189.88.46 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/universe Sources
  404 Not Found [IP: 91.189.88.46 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/multiverse Sources
  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch cdrom:[Ubuntu-Server 7.04 _Feisty Fawn_ - Release i386 (20070415)]/dists/feisty/main/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Failed to fetch cdrom:[Ubuntu-Server 7.04 _Feisty Fawn_ - Release i386 (20070415)]/dists/feisty/restricted/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/feisty-security/main/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/feisty-security/main/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/feisty-security/restricted/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/feisty-security/restricted/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/feisty-security/main/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/feisty-security/main/source/Sources.gz)  404 Not Found
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/feisty-security/restricted/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/feisty-security/restricted/source/Sources.gz)  404 Not Found
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/feisty-security/universe/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/feisty-security/universe/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/feisty-security/universe/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/feisty-security/universe/source/Sources.gz)  404 Not Found
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/feisty-security/multiverse/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/feisty-security/multiverse/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/feisty-security/multiverse/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/feisty-security/multiverse/source/Sources.gz)  404 Not Found
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/feisty/main/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/feisty/main/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/feisty/restricted/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/feisty/restricted/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/feisty/main/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/feisty/main/source/Sources.gz)  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/feisty/restricted/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/feisty/restricted/source/Sources.gz)  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/feisty/universe/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/feisty/universe/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/feisty/universe/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/feisty/universe/source/Sources.gz)  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/feisty/multiverse/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/feisty/multiverse/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/feisty/multiverse/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/feisty/multiverse/source/Sources.gz)  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/feisty-updates/main/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/feisty-updates/main/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/feisty-updates/restricted/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/feisty-updates/restricted/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/feisty-updates/main/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/feisty-updates/main/source/Sources.gz)  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/feisty-updates/restricted/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/feisty-updates/restricted/source/Sources.gz)  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/feisty-backports/main/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/feisty-backports/main/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/feisty-backports/restricted/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/feisty-backports/restricted/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/feisty-backports/universe/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/feisty-backports/universe/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/feisty-backports/multiverse/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/feisty-backports/multiverse/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/feisty-backports/main/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/feisty-backports/main/source/Sources.gz)  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/feisty-backports/restricted/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/feisty-backports/restricted/source/Sources.gz)  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/feisty-backports/universe/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/feisty-backports/universe/source/Sources.gz)  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/feisty-backports/multiverse/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/feisty-backports/multiverse/source/Sources.gz)  404 Not Found [IP: 91.189.88.46 80]
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by bapoumba on 2009-03-11
This second error is normal, Feisty has reached end of life and the repos moved to [http://old-releases.ubuntu.com/releases/](http://old-releases.ubuntu.com/releases/)
No other mirrors any longer :)

Dapper repos are still available. Hardy is the current Long Term Support release.

One question, just out of curiosity, why did not you upgrade? It is not recommended to keep releases that do not receive at least security upgrades.

---

### Post by rocheteau on 2009-03-12
I didn't upgrade for two (bad) reasons. I had set up an internal viewer for our data which worked well after which I didn't have to worry about it and through laziness etc just didn't upgrade it. Secondly, we are firewalled off from the outside so don't have very many internal security issues at all which only added to my complacency. Now, of course, it is deservedly punishing me. Is the fix for the second error as simple as using an updated Hardy source.list? 
I appreciate your time in helping me out, 
R.

---

### Post by bapoumba on 2009-03-13
> **rocheteau said:**
> Is the fix for the second error as simple as using an updated Hardy source.list? 
I appreciate your time in helping me out, 
R.
No problem, you are welcome.

If you change the repos, feisty will not give you any errors, but you won't get any updates either, the repos are not maintained any longer.

If you wish to upgrade, either run an online upgrade, going from one release to the next (I believe you can upgrade Dapper -> Hardy as they are both LTS), or a fresh install of Hardy for ex. I'm still happily running Hardy, my son's got Intrepid and will upgrade to Jaunty when it comes out. I'll probably upgrade to the next LTS on my main machine, and to Jaunty on the others when I have time.

---

