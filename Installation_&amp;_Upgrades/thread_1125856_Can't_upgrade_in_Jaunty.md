---
title: "Can't upgrade in Jaunty"
date: 2009-04-14
forum: Installation &amp; Upgrades
---

### Post by camper365 on 2009-04-14
I have a problem with my apt and stuff like that.
What happens is that it tells me this on the terminal:
```
aaron@truman~$ sudo apt-get install firefox
Reading package lists... Done
Building dependency tree       
Reading state information... Done
firefox is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
3 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up hotkey-setup (0.1-23ubuntu10) ...
/etc/init.d/hotkey-setup: 47: Syntax error: ";;" unexpected (expecting "fi")
invoke-rc.d: initscript hotkey-setup, action "start" failed.
dpkg: error processing hotkey-setup (--configure):
 subprocess post-installation script returned error exit status 2
Setting up totem-gstreamer (2.26.1-0ubuntu1) ...
update-alternatives: error or eof reading /var/lib/dpkg/alternatives/gnome-video-thumbnailer for update_mode ()
dpkg: error processing totem-gstreamer (--configure):
 subprocess post-installation script returned error exit status 2
Setting up totem-xine (2.26.1-0ubuntu1) ...
update-alternatives: error or eof reading /var/lib/dpkg/alternatives/gnome-video-thumbnailer for update_mode ()
dpkg: error processing totem-xine (--configure):
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
 hotkey-setup
 totem-gstreamer
 totem-xine
E: Sub-process /usr/bin/dpkg returned an error code (1)

```I used apt-get firefox because I knew that it was in the newest version already and that it wouldn't take any disk space.

I think that may have something to do with it.
When I run update-manager, it checks the repositories, and it tells me:
```

W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: http://us.archive.ubuntu.com jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5

W: GPG error: http://us.archive.ubuntu.com jaunty-security Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5
W: GPG error: http://us.archive.ubuntu.com jaunty-updates Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5
W: Failed to fetch cdrom://Ubuntu 9.04 _Jaunty Jackalope_ - Alpha i386 (20090312)/dists/jaunty/main/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/jaunty/Release  

W: Failed to fetch cdrom://Ubuntu 9.04 _Jaunty Jackalope_ - Alpha i386 (20090312)/dists/jaunty/restricted/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

W: Some index files failed to download, they have been ignored, or old ones used instead.

```I think that if I purge all of my apt stuff (like synaptic, aptitude, apt, etc.) then it will get fixed, but I'm not sure. Is there a way to reinstall everything that relates to package management?
I have also tried purging and reinstalling hotkey-setup, totem, etc. but that didn't work.
What could be my problem?

---

### Post by Therion on 2009-04-14
First of all open System/Administration/Software Sources and on the Ubuntu Software tab clear the checkbox for "Cdrom With Ubuntu 9.04 Jaunty Jackalope".  
Then, in the "Download From" drop down menu, select a different server, click "Close", "Reload" and then try updating again.

---

### Post by camper365 on 2009-04-15
I tried that, but I still get the warning.
Should I try reinstalling? I have my /home /usr /var and /boot on a seperate partition, so it shouldn't be too hard, but I would loose all my /etc configuration.

---

### Post by Therion on 2009-04-16
If you haven't reinstalled yet, I think you could get away with simply using a clean sources.list file.  I'm sure you could find a default list via Google or, if you're using Jaunty** 64-bit** I could post mine for you... I don't even know that the fact that I'm using the 64-bit version would matter come to think of it.  Maybe take a look at mine and compare it to yours.  I've only added Medibuntu the rest is purely "default":
> 
# deb cdrom:[Ubuntu 9.04 _Jaunty Jackalope_ - Release Candidate amd64 (20090414$
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty-updates universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty-updates multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe$
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-backports main restricted$

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner


---

### Post by mahboop on 2009-06-17
my friend Therion

my sources.list file is different than yours.
How do I know that my laptop is 32-bit or 64-bit??

and I can't update my system, I get this error:
```

W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: http://archive.ubuntu.com jaunty-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/jaunty-updates/Release  

W: Some index files failed to download, they have been ignored, or old ones used instead.


```

Here is my "sources.list" file:

```

# deb cdrom:[Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1)]/ jaunty main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://archive.ubuntu.com/ubuntu/ jaunty main restricted
deb-src http://archive.ubuntu.com/ubuntu/ jaunty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu/ jaunty-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu/ jaunty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
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
# deb http://us.archive.ubuntu.com/ubuntu/ jaunty-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ jaunty-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu jaunty partner
# deb-src http://archive.canonical.com/ubuntu jaunty partner

deb http://archive.ubuntu.com/ubuntu/ jaunty-security main restricted
deb-src http://archive.ubuntu.com/ubuntu/ jaunty-security main restricted
deb http://archive.ubuntu.com/ubuntu/ jaunty-security universe
deb-src http://archive.ubuntu.com/ubuntu/ jaunty-security universe
deb http://archive.ubuntu.com/ubuntu/ jaunty-security multiverse
deb-src http://archive.ubuntu.com/ubuntu/ jaunty-security multiverse

```

Any help please... :)

---

