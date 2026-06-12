---
title: "Problem with Package Manager/Upgrade System"
date: 2009-08-29
forum: Installation &amp; Upgrades
---

### Post by diggerbdigger on 2009-08-29
Hi,
I'm running Jaunty. I noticed that the upgrade manager wasn't working today and then discovered that running any of the synaptic packages got me the following message:

Failed to check for installed and available applications

This is a major failure of your software management system. Please check for broken packages with synaptic, check the file permissions and correctness of the file '/etc/apt/sources.list' and reload the software information with: 'sudo apt-get update' and 'sudo apt-get install -f'.

I followed the advice on another thread and put in the following command:

doug@doug-desktop:~$ cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1)]/ jaunty main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) jaunty main restricted
deb-src [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) jaunty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) jaunty-updates main restricted
deb-src [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) jaunty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) jaunty universe
deb-src [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) jaunty universe
deb [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) jaunty-updates universe
deb-src [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) jaunty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) jaunty multiverse
deb-src [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) jaunty multiverse
deb [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) jaunty-updates multiverse
deb-src [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) jaunty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse
# deb-src [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security multiverse
deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) jaunty main #WineHQ - Ubuntu 9.04 "Jaunty Jackalope"


And I then put in:

doug@doug-desktop:~$ ls -al /etc/apt | grep sources
-rw-r--r--   1 root root  3064 2009-07-09 15:46 sources.list
drwxr-xr-x   2 root root  4096 2009-04-17 16:27 sources.list.d
-rw-r--r--   1 root root  3064 2009-07-09 15:46 sources.list.save


I'm sure that I've screwed something up somewhere - can anyone help?

---

### Post by Partyboi2 on 2009-08-29
What was the output to
```
sudo apt-get update
sudo apt-get -f install
```

---

### Post by drs305 on 2009-08-29
I replaced my sources.list with yours and it worked fine.

You probably have another repository list in /etc/apt/sources.list.d Often it is medibuntu.list but it could be something else. Take a look at the contents of any .list file in that folder:
```

ls /etc/apt/sources.list.d
cat /etc/apt/sources.list.d/*filename.list*

```

Have you opened Synaptic to look for broken packages as the error message asked? Open Synaptic. In the bottom left pane, select Custom Filters, then Broken. And run the commands suggested in the error message.

It usually doesn't hurt to try another mirror: Synaptic, Settings, Repositories: Download from > Other  and then select another server and press the main menu "Reload" button.

---

### Post by diggerbdigger on 2009-08-29
Hi:

sudo apt-get update

[list of http sites] then:
Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/nz.archive.ubuntu.com_ubuntu_dists_jaunty-updates_restricted_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.

then next one:

doug@doug-desktop:~$ sudo apt-get -f install
Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/nz.archive.ubuntu.com_ubuntu_dists_jaunty-updates_restricted_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.

---

### Post by diggerbdigger on 2009-08-29
I can't open the synaptic manager: I get the following:

E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/nz.archive.ubuntu.com_ubuntu_dists_jaunty-updates_restricted_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.
E: _cache->open() failed, please report.

When I put in

ls /etc/apt/sources.list.d

I got no response

Any ideas?

---

### Post by drs305 on 2009-08-29
The referenced file has an error and prevents the udpate from running. Move the offending file out of the folder and put it on your desktop so the udpate can run without error:
```

sudo mv /var/lib/apt/lists/nz.archive.ubuntu.com_ubuntu_dists_jaunty-updates_restricted_binary-i386_Packages $HOME/Desktop/nz.archive.ubuntu.com_ubuntu_dists_jaunty-updates_restricted_binary-i386_Packages
sudo apt-get update

```

If your update runs correctly, open a file browser as root and use SHIFT-DEL to remove the Desktop file:
```

gksudo nautilus $HOME/Desktop

```

I move the file rather than just delete it. It causes you to take more steps. You can just delete the file from the original folder if you prefer.

---

### Post by diggerbdigger on 2009-08-29
Sorry - I'm probably being stupid...


doug@doug-desktop:~$ sudo mv /var/lib/apt/lists/nz.archive.ubuntu.com_ubuntu_dists_jaunty-updates_restricted_binary-i386_Packages $HOME/var/lib/apt/lists/nz.archive.ubuntu.com_ubuntu_dists_jaunty-updates_restricted_binary-i386_Packages
mv: cannot move `/var/lib/apt/lists/nz.archive.ubuntu.com_ubuntu_dists_jaunty-updates_restricted_binary-i386_Packages' to `/home/doug/var/lib/apt/lists/nz.archive.ubuntu.com_ubuntu_dists_jaunty-updates_restricted_binary-i386_Packages': No such file or directory

I've tried to search for the file through the file manager and can't find it there?

---

### Post by drs305 on 2009-08-29
It looks like you copied the command within a few seconds of when I posted it. There was a typo I (almost) immediately corrected, but apparently not quickly enough! Try it again. 

```
sudo mv /var/lib/apt/lists/nz.archive.ubuntu.com_ubuntu_dists_jaunty-updates_restricted_binary-i386_Packages $HOME/**Desktop/**nz.archive.ubuntu.com_ubuntu_dists_jaunty-updates_restricted_binary-i386_Packages
```

If it still doesn't work, open nautilus to see if the file really isn't there:
```

gksudo nautilus /var/lib/apt/lists/

```

> I've tried to search for the file through the file manager and can't find it there?
Did you mean in the original location or where you tried to move it to?

---

### Post by diggerbdigger on 2009-08-29
Ok - I've physically moved nz.archive.ubuntu.com_ubuntu_dists_jaunty-updates_restricted_binary-i386_Packages to desktop

I then put in the following:

sudo cp /var/lib/dpkg/status /var/lib/dpkg/status.bad
sudo cp /var/lib/dpkg/status-old /var/lib/dpkg/status
Didn't offer any response

sudo apt-get update got this (after a load of lists):

Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/nz.archive.ubuntu.com_ubuntu_dists_jaunty-updates_universe_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.

---

### Post by diggerbdigger on 2009-08-29
I put the following files onto my desktop as each was referred to as an error when I tried to update.

nz.archive.ubuntu.com_ubuntu_dists_jaunty-updates_universe_binary-i386_Packages
nz.archive.ubuntu.com_ubuntu_dists_jaunty-updates_restricted_binary-i386_Packages
nz.archive.ubuntu.com_ubuntu_dists_jaunty-updates_multiverse_binary-i386_Packages

Now when I try to update I get the following:

sudo apt-get update
g package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/archive.canonical.com_ubuntu_dists_jaunty_partner_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.

Is something funny going on or should I keep weeding out the error files?

---

### Post by diggerbdigger on 2009-08-29
Problem solved?

I removed any files that came up as errors and the package manager and the rest is now working.

Any ideas why this had got screwed up? Everything seems to work but I'm wondering if I'm now missing something. I took out about 12 files which were distinguished in nautilus with a 'world' icon. Once these were all out everything seemed to work?

Thanks to all for help

---

### Post by drs305 on 2009-08-29
> **diggerbdigger said:**
> Problem solved?

I removed any files that came up as errors and the package manager and the rest is now working.

Any ideas why this had got screwed up? Everything seems to work but I'm wondering if I'm now missing something. I took out about 12 files which were distinguished in nautilus with a 'world' icon. Once these were all out everything seemed to work?

Thanks to all for help

The alternative was to remove all the files in /var/lib/apt/lists (but keep the subfolder /var/lib/apt/lists/partial), which saves time but I prefer to remedy problems with as little change as necessary.

You should not be missing anything. When you ran "apt-get update" APT would have looked at your repository list and updated the files, replacing any that were missing or outdated. For some reason, the files you removed had become corrupted. It could have been a problem on the server. 

You can look into /var/lib/apt/lists and should be able to see new versions of the files you replaced. The dates will not be today's date however, as the date reflects the time the lists were updated at the source.

Added: You may have a bunch of the moved files now on your Desktop. If so, they are owned by root and you won't be able to delete them as a normal user. Open a file browser with admin rights and delete them using SHIFT-DEL (otherwise they will end up in root's trash bin, which a normal user cannot empty).
```

gksudo nautilus $HOME/Desktop

```

---

### Post by swudee on 2009-09-02
I had the same problem, also in NZ !??
I disabled the repositories in System/Software Sources for Medibuntu, Virtualbox, and Restricted Extras and the update manager worked OK.
I went to delete the files in /var/lib/apt/lists and found they were gone.
I noticed that as I re-enabled the repositories and updated them, the files were re-added. So it would appear to be a simple way to cure it is to untick the boxes to remove the files, then re-tick them to generate new ones.:)

David

---

