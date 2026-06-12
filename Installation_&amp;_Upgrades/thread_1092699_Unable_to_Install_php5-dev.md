---
title: "Unable to Install php5-dev"
date: 2009-03-10
forum: Installation &amp; Upgrades
---

### Post by ClosAttack on 2009-03-10
I need phpize to install an Oracle Instant Client, and so I tried to install php5-dev and received this message

////////////////
sudo apt-get install -f php5-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  php5-dev: Depends: libssl-dev but it is not going to be installed
            Depends: libtool but it is not going to be installed
E: Broken package
///////////////

It should be noted that I'm running this on Linode.com so it uses a specialized xen kernel.  But this package shouldn't be a problem as people on the linode forums were installing this package w/o problems.  I also already tried to fix the "broken package" with synaptic but it seems to have done nothing.  Thanks in advance.

---

### Post by Neo_The_User on 2009-03-10
```

sudo apt-get install libtool

```

Then try again. ;)

---

### Post by ClosAttack on 2009-03-10
So I tried that and got:
///////////////////
[~] sudo apt-get install libtool
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  libtool: Depends: libc6-dev but it is not going to be installed or
                    libc-dev
E: Broken packages
//////////////

And I thought "I get it, I'll just install libc6-dev" and got this:

//////////////
[~] sudo apt-get install libc6-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  libc6-dev: Depends: libc6 (= 2.7-10ubuntu3) but 2.7-10ubuntu4 is to be installed
E: Broken packages
//////////////////////

And now I am even more confused as libc6 is installed already.  Thanks again for the help.

---

### Post by Neo_The_User on 2009-03-10
sudo apt-get install libc6

just keep doing install commands until it works. if it says its installed but wont be configured, use sudo dpkg --configure (package) for example:

sudo dpkg --configure libc6

Sooner or later, you'll have it working. Try this though.

sudo apt-get install -f && sudo apt-get install ubuntu-desktop ubuntu-standard

This is the fun of tool chains! XD

---

### Post by ClosAttack on 2009-03-10
So,

sudo apt-get install libc6

returns:

[I]Reading package lists... Done
Building dependency tree       
Reading state information... Done
libc6 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.[/I]

and

sudo dpkg --configure libc6

returns:

[I]dpkg: error processing libc6 (--configure):
 package libc6 is already installed and configured
Errors were encountered while processing:
 libc6[/I]

I did this

sudo apt-get install -f && sudo apt-get install ubuntu-desktop ubuntu-standard

But the the first two still return those same errors.

---

### Post by Neo_The_User on 2009-03-10
Get ready for hell.

```

wget http://mirrors.kernel.org/ubuntu/pool/main/g/glibc/libc6_2.8~20080505-0ubuntu7_i386.deb
sudo dpkg -i libc6*

```

If you really want problems

```

wget http://mirrors.kernel.org/ubuntu/pool/main/g/glibc/libc6_2.9-4ubuntu2_i386.deb
sudo dpkg -i libc6_2.9*

```

---

### Post by Partyboi2 on 2009-03-10
> **ClosAttack said:**
> So,

sudo apt-get install libc6

returns:

[I]Reading package lists... Done
Building dependency tree       
Reading state information... Done
libc6 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.[/I]

and

sudo dpkg --configure libc6

returns:

[I]dpkg: error processing libc6 (--configure):
 package libc6 is already installed and configured
Errors were encountered while processing:
 libc6[/I]

I did this

sudo apt-get install -f && sudo apt-get install ubuntu-desktop ubuntu-standard

But the the first two still return those same errors.

Could you post your sources.list please.
```
cat /etc/apt/sources.list
```

---

### Post by taurus on 2009-03-10
Can you post your /etc/apt/sources.list?

Applications -> Accessories -> Terminal
```
cat /etc/apt/sources.list
```

Maybe you haven't enable all the repos in there.

---

### Post by Neo_The_User on 2009-03-10
oh! just do this!

```

wget http://mirrors.kernel.org/ubuntu/pool/main/p/php5/php5-dev_5.2.6.dfsg.1-3ubuntu2_i386.deb
sudp dpkg -i php5-dev*

```

ALL DONE!

---

### Post by ClosAttack on 2009-03-10
Here is my sources.list

#
# deb cdrom:[Ubuntu-Server 8.04 _Hardy Heron_ - Release i386 (20080423.2)]/ hardy main restricted

# deb cdrom:[Ubuntu-Server 8.04 _Hardy Heron_ - Release i386 (20080423.2)]/ hardy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy main restricted multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy main multiverse universe restricted #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
## deb [http://mirror.cs.umn.edu/ubuntu/](http://mirror.cs.umn.edu/ubuntu/) hardy multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner

## deb [http://ppa.launchpad.net/freenx-team/ubuntu](http://ppa.launchpad.net/freenx-team/ubuntu) hardy main
## deb-src [http://ppa.launchpad.net/freenx-team/ubuntu](http://ppa.launchpad.net/freenx-team/ubuntu) hardy main

---

### Post by taurus on 2009-03-10
Go into System -> Administration -> Software Sources and make sure you have a check mark in front of all repos except the last one, Source code.  Then go into Third-Party Software click the one for canonical.  Close it and shutdown Software Sources.  

Now see if you can install those packages from a terminal after you have ran the update first.

```
sudo apt-get update
```

---

### Post by ClosAttack on 2009-03-10
No go, still have the same errors.

---

### Post by Neo_The_User on 2009-03-10
> **ClosAttack said:**
> No go, still have the same errors.

try the dpkg - i commands i gave ya

---

### Post by ClosAttack on 2009-03-10
First one:
[I](Reading database ... 95977 files and directories currently installed.)
Preparing to replace libc6 2.7-10ubuntu4 (using libc6_2.8~20080505-0ubuntu7_i386.deb) ...
Unpacking replacement libc6 ...
dpkg: dependency problems prevent configuration of libc6:
 libc6 depends on findutils (>= 4.4.0-2ubuntu2); however:
  Version of findutils on system is 4.2.32-1ubuntu2.
dpkg: error processing libc6 (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 libc6
[/I]

Second one:

[I]dpkg: considering removing belocs-locales-bin in favour of libc6 ...
dpkg: no, cannot proceed with removal of belocs-locales-bin (--auto-deconfigure will help):
 locales depends on belocs-locales-bin (>= 2.4-2.2ubuntu2)
  belocs-locales-bin is to be removed.
dpkg: regarding libc6_2.9-4ubuntu2_i386.deb containing libc6:
 libc6 conflicts with belocs-locales-bin
  belocs-locales-bin (version 2.4-2.2ubuntu7) is present and installed.
dpkg: error processing libc6_2.9-4ubuntu2_i386.deb (--install):
 conflicting packages - not installing libc6
Errors were encountered while processing:
 libc6_2.9-4ubuntu2_i386.deb[/I]

And the php5-dev one:

[I]sudo dpkg -i php5-dev*
Selecting previously deselected package php5-dev.
(Reading database ... 95981 files and directories currently installed.)
Unpacking php5-dev (from php5-dev_5.2.6.dfsg.1-3ubuntu2_i386.deb) ...
Preparing to replace php5-dev 5.2.6.dfsg.1-3ubuntu2 (using php5-dev_5.2.6.dfsg.1-3ubuntu2_i386.deb.1) ...
Unpacking replacement php5-dev ...
More than one copy of package php5-dev has been unpacked
 in this run !  Only configuring it once.
dpkg: dependency problems prevent configuration of php5-dev:
 php5-dev depends on libssl-dev; however:
  Package libssl-dev is not installed.
 php5-dev depends on libtool; however:
  Package libtool is not installed.
 php5-dev depends on php5-common (>= 5.2.6.dfsg.1-3ubuntu2); however:
  Version of php5-common on system is 5.2.4-2ubuntu5.5.
dpkg: error processing php5-dev (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 php5-dev[/I]

It's starting to look bad.

---

### Post by Neo_The_User on 2009-03-10
STARTING? hahahah! as if it wasn't bad enough. let me give you some commands so you can continue dealing with this backwards toolchain problem. k? btw I could do this for days, weeks helping you out until you decide to stop so don't be afraid of wasting my time. I got plenty of time on my hands until I get gcc 4.4 to run perfectly.

```

sudo apt-get install libssl-dev
wget http://mirrors.kernel.org/ubuntu/pool/main/b/belocs-locales-bin/belocs-locales-bin_2.4-2.3ubuntu1_i386.deb
sudo dpkg -i belocs*
wget http://mirrors.kernel.org/ubuntu/pool/main/p/php5/php5-common_5.2.6.dfsg.1-3ubuntu2_i386.deb
sudo dpkg -i php5-common*

```

Post error output and lets keep going.

belocs will give you errors about itself and not dependencies so belocs would be easier to fix that php5-common if php5-common gets errors.

---

### Post by ClosAttack on 2009-03-10
Okay, thanks for the help.

---

### Post by Neo_The_User on 2009-03-10
> **ClosAttack said:**
> Okay, thanks for the help.

No problem. Post the output of those commands.

Oh! 1 more thing.

```

sudo apt-get build-dep php5-dev php5-common

```

About the libc6-dev problem:

```

sudo apt-get install libc6-dev

```

If it says it's installed:

```

wget http://mirrors.kernel.org/ubuntu/pool/main/g/glibc/libc6-dev_2.9-4ubuntu2_i386.deb
sudo dpkg -i libc6-dev*

```

If you just want to give up replace your sources.list with this and then run sudo apt-get update && sudo apt-get dist-upgrade:

```

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://archive.ubuntu.com/ubuntu/ jaunty main restricted
deb-src http://archive.ubuntu.com/ubuntu/ jaunty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu/ jaunty-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu/ jaunty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu/ jaunty universe
deb-src http://archive.ubuntu.com/ubuntu/ jaunty universe
deb http://archive.ubuntu.com/ubuntu/ jaunty-updates universe
deb-src http://archive.ubuntu.com/ubuntu/ jaunty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://archive.ubuntu.com/ubuntu/ jaunty multiverse
deb-src http://archive.ubuntu.com/ubuntu/ jaunty multiverse
deb http://archive.ubuntu.com/ubuntu/ jaunty-updates multiverse
deb-src http://archive.ubuntu.com/ubuntu/ jaunty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://cl.archive.ubuntu.com/ubuntu/ jaunty-backports main restricted universe multiverse
deb-src http://cl.archive.ubuntu.com/ubuntu/ jaunty-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb http://archive.canonical.com/ubuntu jaunty partner
deb-src http://archive.canonical.com/ubuntu jaunty partner

deb http://archive.ubuntu.com/ubuntu/ jaunty-security main restricted
deb-src http://archive.ubuntu.com/ubuntu/ jaunty-security main restricted
deb http://archive.ubuntu.com/ubuntu/ jaunty-security universe
deb-src http://archive.ubuntu.com/ubuntu/ jaunty-security universe
deb http://archive.ubuntu.com/ubuntu/ jaunty-security multiverse
deb-src http://archive.ubuntu.com/ubuntu/ jaunty-security multiverse

```

---

### Post by ClosAttack on 2009-03-10
> **Neo_The_User said:**
> STARTING? hahahah! as if it wasn't bad enough. let me give you some commands so you can continue dealing with this backwards toolchain problem. k? btw I could do this for days, weeks helping you out until you decide to stop so don't be afraid of wasting my time. I got plenty of time on my hands until I get gcc 4.4 to run perfectly.

```

sudo apt-get install libssl-dev
wget http://mirrors.kernel.org/ubuntu/pool/main/b/belocs-locales-bin/belocs-locales-bin_2.4-2.3ubuntu1_i386.deb
sudo dpkg -i belocs*
wget http://mirrors.kernel.org/ubuntu/pool/main/p/php5/php5-common_5.2.6.dfsg.1-3ubuntu2_i386.deb
sudo dpkg -i php5-common*

```

Post error output and lets keep going.

belocs will give you errors about itself and not dependencies so belocs would be easier to fix that php5-common if php5-common gets errors.

Get ready for hella errors:
```

**VPN[~] sudo apt-get install libssl-dev**
[sudo] password for chem: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  libc6: Depends: findutils (>= 4.4.0-2ubuntu2) but 4.2.32-1ubuntu2 is to be installed
  libc6-i686: PreDepends: libc6 (= 2.7-10ubuntu4) but 2.8~20080505-0ubuntu7 is to be installed
  libssl-dev: Depends: libssl0.9.8 (= 0.9.8g-4ubuntu3) but 0.9.8g-4ubuntu3.4 is to be installed
              Depends: zlib1g-dev but it is not going to be installed
  php5-dev: Depends: libtool but it is not going to be installed
            Depends: php5-common (>= 5.2.6.dfsg.1-3ubuntu2) but 5.2.4-2ubuntu5.5 is to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
**VPN[~] wget [http://mirrors.kernel.org/ubuntu/pool/main/b/belocs-locales-bin/belocs-locales-bin_2.4-2.3ubuntu1_i386.deb](http://mirrors.kernel.org/ubuntu/pool/main/b/belocs-locales-bin/belocs-locales-bin_2.4-2.3ubuntu1_i386.deb)**
--22:10:05--  [http://mirrors.kernel.org/ubuntu/pool/main/b/belocs-locales-bin/belocs-locales-bin_2.4-2.3ubuntu1_i386.deb](http://mirrors.kernel.org/ubuntu/pool/main/b/belocs-locales-bin/belocs-locales-bin_2.4-2.3ubuntu1_i386.deb)
           => `belocs-locales-bin_2.4-2.3ubuntu1_i386.deb'
Resolving mirrors.kernel.org... 204.152.191.39, 149.20.20.135
Connecting to mirrors.kernel.org|204.152.191.39|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 172,304 (168K) [text/plain]

100%[====================================>] 172,304      434.38K/s             

22:10:06 (433.53 KB/s) - `belocs-locales-bin_2.4-2.3ubuntu1_i386.deb' saved [172304/172304]
[B]
VPN[~] sudo dpkg -i belocs*[/B]
(Reading database ... 96251 files and directories currently installed.)
Preparing to replace belocs-locales-bin 2.4-2.2ubuntu7 (using belocs-locales-bin_2.4-2.3ubuntu1_i386.deb) ...
Unpacking replacement belocs-locales-bin ...
dpkg: dependency problems prevent configuration of belocs-locales-bin:
 belocs-locales-bin depends on libc6 (>= 2.8~20080505); however:
  Package libc6 is not configured yet.
dpkg: error processing belocs-locales-bin (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 belocs-locales-bin
**VPN[~] wget [http://mirrors.kernel.org/ubuntu/pool/main/p/php5/php5-common_5.2.6.dfsg.1-3ubuntu2_i386.deb](http://mirrors.kernel.org/ubuntu/pool/main/p/php5/php5-common_5.2.6.dfsg.1-3ubuntu2_i386.deb)**
--22:12:51--  [http://mirrors.kernel.org/ubuntu/pool/main/p/php5/php5-common_5.2.6.dfsg.1-3ubuntu2_i386.deb](http://mirrors.kernel.org/ubuntu/pool/main/p/php5/php5-common_5.2.6.dfsg.1-3ubuntu2_i386.deb)
           => `php5-common_5.2.6.dfsg.1-3ubuntu2_i386.deb'
Resolving mirrors.kernel.org... 149.20.20.135, 204.152.191.39
Connecting to mirrors.kernel.org|149.20.20.135|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 367,618 (359K) [text/plain]

100%[====================================>] 367,618      693.55K/s             

22:12:52 (692.64 KB/s) - `php5-common_5.2.6.dfsg.1-3ubuntu2_i386.deb' saved [367618/367618]
[B]
VPN[~] sudo dpkg -i php5-common*[/B]
(Reading database ... 96251 files and directories currently installed.)
Preparing to replace php5-common 5.2.4-2ubuntu5.5 (using php5-common_5.2.6.dfsg.1-3ubuntu2_i386.deb) ...
Unpacking replacement php5-common ...
dpkg: dependency problems prevent configuration of php5-common:
 php5-common depends on libc6 (>= 2.4); however:
  Package libc6 is not configured yet.
dpkg: error processing php5-common (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 php5-common

```

---

### Post by Neo_The_User on 2009-03-10
Just curious, how critical is this? I'm suprised you didn't re-install yet!

```

sudo dpkg --configure libc6
wget http://mirrors.kernel.org/ubuntu/pool/main/o/openssl/libssl0.9.8_0.9.8g-15ubuntu1_i386.deb
wget http://mirrors.kernel.org/ubuntu/pool/main/z/zlib/zlib1g_1.2.3.3.dfsg-12ubuntu1_i386.deb
wget http://mirrors.kernel.org/ubuntu/pool/main/f/findutils/findutils_4.4.0-2ubuntu3_i386.deb
sudo dpkg -i libssl0.9.8_0.9.8g-15ubuntu1_i386.deb
sudo dpkg -i zlib1g_1.2.3.3.dfsg-12ubuntu1_i386.deb
sudo dpkg -i findutils_4.4.0-2ubuntu3_i386.deb

```

EDIT: libtool

```

wget http://mirrors.kernel.org/ubuntu/pool/main/libt/libtool/libtool_2.2.6a-1ubuntu1_i386.deb
sudo dpkg -i libtool*

```

You do know that eventually when the toolchain is all solved (which will take ages from the looks of it) you're going to have to go back and do sudo dpkg -i php5-dev and php5-common and all that stuff right? The toolchain is only 1/2 of the problem. The actual deb packages you want (need from the looks of it) is the second half. This is going to take a long time. If you don't necessarily have to do this, I highly recommend doing a fresh install. If your just bored, then I can see why you're doing this. FYI, im cracking up like crazy at this whole situation!

---

### Post by ClosAttack on 2009-03-11
Yeah fresh install is going to have to happen as this isn't all that critical.  I just wish I knew what happened so I can avoid it in the future.  Thanks for all the help though.

Also this is my first time posting my own thread and I'm thrilled at how awesomely helpful you all are.

---

### Post by Neo_The_User on 2009-03-11
heh I try

---

### Post by mc4man on 2009-03-12
> I just wish I knew what happened so I can avoid it in the future. Thanks for all the help though.

It's a little late now for that, though the bulk of your *initial* problem centered around not having the proper hardy and hardy-updates sources enabled.
That was compounded tremendously by following the advice of someone who obviously wasn't interested in resolving the issues in a lucid manner.
Whether or not you could have resolved this successfully may be debatable, the lack of any honest attempt with the exception of 3 posts isn't.

A bit of an embarrassment to say the least.

---

### Post by war59312 on 2010-02-12
Update: [http://packages.ubuntu.com/hardy/amd64/libtool/download](http://packages.ubuntu.com/hardy/amd64/libtool/download)

Installed that and problem of php5-dev not installing solved. Sadly now getting another error..

O.K know bug: [http://pecl.php.net/bugs/bug.php?id=16770](http://pecl.php.net/bugs/bug.php?id=16770) Thankfully fixed already..

If only I knew how to install it form there? Any help?

Hi,

Sadly, I'm having an issue like this as well.

Trying to install memcached following this guide:

[http://stevelove.org/2009/09/30/how-to-install-php-memcached-on-an-ubuntu-server/](http://stevelove.org/2009/09/30/how-to-install-php-memcached-on-an-ubuntu-server/)

I notice in the one comment I need to run:

> sudo pecl install memcachedWhen I do I get:

> downloading memcached-1.0.0.tgz ...
Starting to download memcached-1.0.0.tgz (22,281 bytes)
........done: 22,281 bytes
4 source files, building
running: phpize
sh: phpize: not found
ERROR: `phpize' failedSo, then I try:

> sudo apt-get install php5-devAnd I get:

> Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  php5-dev: Conflicts: libtool (>= 2.2) but 2.2.6b-2ubuntu1 is to be installed
E: Broken packagesIf I unstall libtool then I get:

> Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  php5-dev: Depends: libtool but it is not going to be installed
E: Broken packagesThanks for the help,

Will

---

### Post by origineight on 2013-01-12
Why not walk the dependency tree up the chain and see what might be broken? For example:

```
root@staging:~# apt-get install php5-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
[B] php5-dev : Depends: libssl-dev but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
[/B]root@staging:~# **apt-get install libssl-dev**
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 libssl-dev : **Depends: zlib1g-dev** but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
root@staging:~# **apt-get install zlib1g-dev**
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
** zlib1g-dev : Depends: zlib1g (= 1:1.2.3.4.dfsg-3) but 1:1.2.7.dfsg-13 is to be installed**
E: Unable to correct problems, you have held broken packages.
root@staging:~# **apt-get install -f zlib1g=1:1.2.3.4.dfsg-3**
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  aptitude libept1.4.12
The following packages will be DOWNGRADED:
  zlib1g
0 upgraded, 0 newly installed, 1 downgraded, 2 to remove and 0 not upgraded.
Need to get 79.2 kB of archives.
After this operation, 5,487 kB disk space will be freed.
Do you want to continue [Y/n]? y
Get:1 http://ftp.us.debian.org/debian/ stable/main zlib1g amd64 1:1.2.3.4.dfsg-3 [79.2 kB]
Fetched 79.2 kB in 0s (471 kB/s)
(Reading database ... 46456 files and directories currently installed.)
Removing aptitude ...
Removing libept1.4.12 ...
Processing triggers for man-db ...
dpkg: warning: downgrading zlib1g:amd64 from 1:1.2.7.dfsg-13 to 1:1.2.3.4.dfsg-3
(Reading database ... 46429 files and directories currently installed.)
Preparing to replace zlib1g:amd64 1:1.2.7.dfsg-13 (using .../zlib1g_1%3a1.2.3.4.dfsg-3_amd64.deb) ...
Unpacking replacement zlib1g ...
Setting up zlib1g (1:1.2.3.4.dfsg-3) ...
root@staging:~# apt-get install php5-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following package was automatically installed and is no longer required:
  aptitude-common
Use 'apt-get autoremove' to remove it.
The following extra packages will be installed:
  autoconf automake libssl-dev shtool zlib1g-dev
Suggested packages:
  autoconf2.13 autoconf-archive gnu-standards autoconf-doc gettext
The following NEW packages will be installed:
  autoconf automake libssl-dev php5-dev shtool zlib1g-dev
0 upgraded, 6 newly installed, 0 to remove and 0 not upgraded.
Need to get 4,453 kB of archives.
After this operation, 15.6 MB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Get:1 http://ftp.us.debian.org/debian/ stable/main autoconf all 2.67-2 [793 kB]
Get:2 http://ftp.us.debian.org/debian/ stable/main automake all 1:1.11.1-1+squeeze1 [611 kB]
Get:3 http://ftp.us.debian.org/debian/ stable/main zlib1g-dev amd64 1:1.2.3.4.dfsg-3 [192 kB]
Get:4 http://ftp.us.debian.org/debian/ stable/main libssl-dev amd64 0.9.8o-4squeeze13 [2,289 kB]
Get:5 http://ftp.us.debian.org/debian/ stable/main shtool all 2.0.8-6 [159 kB]
Get:6 http://ftp.us.debian.org/debian/ stable/main php5-dev amd64 5.3.3-7+squeeze14 [409 kB]
Fetched 4,453 kB in 2s (1,670 kB/s)
Selecting previously unselected package autoconf.
(Reading database ... 46429 files and directories currently installed.)
Unpacking autoconf (from .../autoconf_2.67-2_all.deb) ...
Selecting previously unselected package automake.
Unpacking automake (from .../automake_1%3a1.11.1-1+squeeze1_all.deb) ...
Selecting previously unselected package zlib1g-dev.
Unpacking zlib1g-dev (from .../zlib1g-dev_1%3a1.2.3.4.dfsg-3_amd64.deb) ...
Selecting previously unselected package libssl-dev.
Unpacking libssl-dev (from .../libssl-dev_0.9.8o-4squeeze13_amd64.deb) ...
Selecting previously unselected package shtool.
Unpacking shtool (from .../shtool_2.0.8-6_all.deb) ...
Selecting previously unselected package php5-dev.
Unpacking php5-dev (from .../php5-dev_5.3.3-7+squeeze14_amd64.deb) ...
Processing triggers for man-db ...
Processing triggers for install-info ...
Setting up autoconf (2.67-2) ...
Setting up automake (1:1.11.1-1+squeeze1) ...
update-alternatives: using /usr/bin/automake-1.11 to provide /usr/bin/automake (automake) in auto mode
Setting up zlib1g-dev (1:1.2.3.4.dfsg-3) ...
Setting up libssl-dev (0.9.8o-4squeeze13) ...
Setting up shtool (2.0.8-6) ...
Setting up php5-dev (5.3.3-7+squeeze14) ...
update-alternatives: using /usr/bin/php-config5 to provide /usr/bin/php-config (php-config) in auto mode
update-alternatives: using /usr/bin/phpize5 to provide /usr/bin/phpize (phpize) in auto mode
```

---

