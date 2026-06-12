---
title: "[SOLVED] Dapper 6.06.1 to Hardy 8.04.1 upgrade problems"
date: 2008-12-30
forum: Installation &amp; Upgrades
---

### Post by grognut on 2008-12-30
Hi All,

I'm having problems upgrading from 6.01.1 to 8.04.1.
I'm doing a parallel install before updating a working server. I installed 6.06.1 and installed php5, apache2 with mono-mod, mono, xsp2, and mono-dev.
I have done a full update first and then installed update-manager-core.
Then I ran do-release-upgrade.
The upgrade runs and then it falls over where it calculates changes. 
When I look in the /var/log/dist-upgrade/main.log I see
```
2008-12-30 21:50:37,198 DEBUG The package 'ubuntu-desktop' is marked for removal but it's in the removal blacklist
2008-12-30 21:50:37,212 ERROR Dist-upgrade failed: 'An essential package would have to be removed'

```

Can anyone help?

I can post the full logs in /var/log/dist-upgrade/ if required and any machine details but before that has anyone got any suggestions.

regards
grognut

---

### Post by stderr on 2008-12-30
I  have a feeling that you may end up having to remove the metapackage ubuntu-desktop before the upgrade can proceed. Then you'll probably have to reinstall ubuntu-desktop after the upgrade. I'm not sure, however, whether the removal of that metapackage will affect other package operations during the upgrade. Or before even - I'm not sure what depends on ubuntu-desktop.

edit: Just checked, it doesn't seem like anything depends on it. However it does say this in the release notes

```
It is also used to help ensure proper upgrades, so it is recommended that
it not be removed.
```

;) were it me, I'd just remove the package and see if it helps, but I'd rather some others weigh in with their 2 cents first...

---

### Post by grognut on 2008-12-30
Hi stderr,

Thanks for your response.

I agree that removing ubuntu-desktop might work but what seems odd to me is that it is part of the standard install and as some form of desktop is probably the most popular us of Ubuntu it should upgrade fine.

After seaching the logs I seem to get lots of "xxx has broken dep on yyy"
I did a System>Admin>Synaptic Package Manager and on the "edit" menu, clicked on "fix broken packages".
I did do-release-upgrade again but these "xxx has broken dep on yyy" remained.
Scrolling back through the console window I found 
```
Updating repository information
WARNING: Failed to read mirror file
Done http://gb.archive.ubuntu.com hardy Release.gpg
Done http://gb.archive.ubuntu.com hardy-updates Release.gpg
Done http://gb.archive.ubuntu.com hardy-backports Release.gpg
.
.
.

```
Could this mean I don't have the correct repositories enabled. I have the following listed in /etc/apt/sources.list comments removed.
```

deb-src http://gb.archive.ubuntu.com/ubuntu/ dapper main restricted
deb http://gb.archive.ubuntu.com/ubuntu/ dapper-updates main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ dapper-updates main restricted
deb http://archive.ubuntu.com/ubuntu/ dapper universe main restricted multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ dapper universe
deb http://gb.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse
deb http://security.ubuntu.com/ubuntu dapper-security main restricted
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted
deb http://security.ubuntu.com/ubuntu dapper-security universe
deb-src http://security.ubuntu.com/ubuntu dapper-security universe
```

Anyone any thoughts?

Best regards

grognut

---

### Post by grognut on 2009-01-03
Hi All,

As I've no solutions or other comments, let's word the question the other way.

Has anyone managed to upgrade from dapper to hardy successfully?

Dapper is on lts until 2011. If the uprgrade doesn't work what happens to all the dapper users in 2011, will they have to re-install from scratch? or leave the server with no security updates?
There must be an answer to this!

Cheers

grognut

---

### Post by Zill on 2009-01-03
> **grognut said:**
> ...Has anyone managed to upgrade from dapper to hardy successfully?

Dapper is on lts until 2011. If the uprgrade doesn't work what happens to all the dapper users in 2011, will they have to re-install from scratch? or leave the server with no security updates?

I am also in the same boat and will need to upgrade from Dapper to Hardy soon.

AIUI, it *should* be possible to simply upgrade from one LTS version to another, but I have seen various reports of problems with this.  YMMV!

I have decided to take the more reliable route and just install Hardy as a new installation.  As I have my /home on a separate partition this should keep my data intact.  I keep all my /etc config files for reference so can use these to reconfigure my new installation as previously.

I used this technique when I upgraded my wife's Kubuntu PC recently and it seemed to work very well.

---

### Post by zvacet on 2009-01-03
I found Dapper server source list and her it is 

> deb cdrom:[Ubuntu 6.06 _Dapper Drake_ - Release i386 (20060601)]/ dapper main restricted


## Uncomment the following two lines to fetch updated software from the network
 deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper main restricted
# deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
 deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper-updates main restricted
# deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
 deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper universe
# deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse

 deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper universe multiverse
 deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe

If you installed desktop on your server then you need ubuntu-desktop for upgrade.

Maybe you should try to switch to main server,not your local to upgrade.

---

### Post by Zill on 2009-01-03
grognut:  Just to confirm that I am currently using the same Dapper UK mirrors in my /etc/apt/sources.list file as you and they are still working correctly.

I am puzzled as to why your /etc/apt/sources.list still shows Dapper repositories.  I would have thought that as you had actually started the upgrade process, one of the first things to change would have been to update this to the Hardy repositories.  If the upgrade has now left some Dapper packages and some Hardy packages, this *could* be causing the confusion.  It may be worth changing /etc/apt/sources.list to only show Hardy repositories and then running Synaptic to fix the broken packages.

However, it might be easier to bite the bullet and do a clean install. :-(

---

### Post by stderr on 2009-01-03
Yeah, it changes software sources first, but it rolls back those changes if it's cancelled/errors.

Perhaps /var/log/apt.log might provide some insight? There must be another package, I figure, which it thinks about and thereby decides it needs to upgrade/remove ubuntu-desktop. Maybe finding that would help - and it should be in apt.log.

---

### Post by grognut on 2009-01-04
Thanks for the responses,

stderr: I've attached a tgz of /var/log/dist-upgrades I hope it helps.
I got a lot of "xxx has broken dep on yyy"
> I did a System>Admin>Synaptic Package Manager and on the "edit" menu, clicked on "fix broken packages".
I did do-release-upgrade again but these "xxx has broken dep on yyy" remained.
I don't know if that's normal because I've never had to try this before.

Zill: I think your solution will be my only one if the upgrade route is unsuccesful. I don't think /home was installed on a separate partition so it's going to be a Samba backup job to another machine.
BTW I'm not familiar with AIUI and YMMV. Could you explain please. I know BTW and LOL. LOL.

zvacet: I have installed from a desktop cd on the parallel system but I'm not sure if I did that on the server I want to upgrade. I may have added the  desktop afterwards because at the time I was not familiar with the command line. I'll tackle that one when I get the parallel system upgrade working.

Cheers
grognut

---

### Post by Zill on 2009-01-04
> **grognut said:**
> ...Zill: I think your solution will be my only one if the upgrade route is unsuccesful. I don't think /home was installed on a separate partition so it's going to be a Samba backup job to another machine.
BTW I'm not familiar with AIUI and YMMV. Could you explain please. I know BTW and LOL...
[URL="http://en.wiktionary.org/wiki/AIUI"]
http://en.wiktionary.org/wiki/AIUI[/URL]

[http://en.wiktionary.org/wiki/YMMV]("http://en.wiktionary.org/wiki/YMMV")

BTW, as you are apparently running a server, don't you already have regular backups you can use? ;-)

---

### Post by zvacet on 2009-01-04
> I got a lot of "xxx has broken dep on yyy"

```
sudo apt-get -f install
```

---

### Post by grognut on 2009-01-04
Hi Zill,

It's a personel server and I've been fairly relaxed about backups.
I've only a growing database to backup and the config files for mysql/apache/php/mail etc. Must do one soon though.LOL
Thanks for the acronyms.

Cheers
Andy

---

### Post by grognut on 2009-01-04
Hi zvacet

did

```
sudo apt-get -f install
```

and got
 
```
andy@andy-desktop:~$ sudo apt-get -f install
Password:
Reading package lists... Done
Building dependency tree... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
andy@andy-desktop:~$
```

I'll try 
```
do-release-upgrade
```

again and post the results in a little while.

One thought here is that I do ```
sudo bash
``` so I can edit and save config files. I don't know if that could cause a problem. I don't expect it to.

Cheers

grognut

---

### Post by grognut on 2009-01-04
Hi zvacet,

No change. It still fails at the same point ie

```
2009-01-04 13:57:12,633 DEBUG The package 'ubuntu-desktop' is marked for removal but it's in the removal blacklist
2009-01-04 13:57:12,644 ERROR Dist-upgrade failed: 'An essential package would have to be removed'
```

at the end of /var/log/dist-upgrade/main.log

Cheers

grognut

---

### Post by stderr on 2009-01-04
Just had a look through your apt.log.

Have you tried running the update via:

```
sudo do-release-upgrade -m desktop
```

Failing that, I wonder if removing 'esound' or 'pulseaudio-esound-compat' would help.

---

### Post by grognut on 2009-01-04
Hi stderr,

It has now gone passed the problem point. I can't let it download 846Mb at the moment, might get FUP'ed by Tiscali. I'll finish the update later and post the results.

Thanks 

Grognut

---

### Post by stderr on 2009-01-04
If there's something I really hate, it's "Fair Use" download caps. A truly disgusting abuse of ISP priviledges. I keep meaning to switch from Virgin cable to a truly unlimited ADSL provider (urgh) to get away from it. As much as NTL customer service was a joke, and their engineers that I encountered were worse than helpless, at least initially they offered a nice unrestricted cable service.

---

### Post by grognut on 2009-01-05
Hi stderr,

So I ignored the chances of a FUP and went ahead. I went fairly well.

I had a problem where I used the diff to compare /etc/phpmyadmin/config.footer.inc.php but didn't know how to exit.

It went on from there and fell over being unable to install the package manager.
Then it terminated the update. The last lines in the command window are:

```
generating monodoc index...
generating monodoc search index... (this can take a while)

Setting up evolution-exchange (2.22.3-0ubuntu2) ...

Setting up evolution-plugins (2.22.3.1-0ubuntu1) ...
Setting up ubuntu-desktop (1.102) ...
Setting up monodoc (1.2.6-1ubuntu2) ...
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.24-22-386
/etc/fstab.pre-uuid already exists
remove this file before running the script again
/tmp/tmpnzexMq/backports/usr/lib/python2.4/site-packages/apt/__init__.py:2: RuntimeWarning: Python C API version mismatch for module apt_pkg: This Python has API version 1013, module apt_pkg has version 1012.
  import apt_pkg
/tmp/tmpnzexMq/backports/usr/lib/python2.4/site-packages/apt/__init__.py:2: RuntimeWarning: Python C API version mismatch for module apt_pkg: This Python has API version 1013, module apt_pkg has version 1012.
  import apt_pkg

Could not install the upgrades

The upgrade aborts now. Your system could be in an unusable state. A
recovery will run now (dpkg --configure -a).

/etc/fstab.pre-uuid already exists
remove this file before running the script again
root@andy-desktop:~#

```

The last lines of /var/log/dist-upgrade are
```
2009-01-05 19:27:31,885 DEBUG Dir /home mounted on /
2009-01-05 19:27:31,885 DEBUG fs_free contains: '{'/var': <DistUpgradeController.FreeSpace object at 0xb7635c8c>, '/home': <DistUpgradeController.FreeSpace object at 0xb7635c8c>, '/boot': <DistUpgradeController.FreeSpace object at 0xb7635c8c>, '/usr': <DistUpgradeController.FreeSpace object at 0xb7635c8c>, '/': <DistUpgradeController.FreeSpace object at 0xb7635c8c>, '/var/cache/apt/archives': <DistUpgradeController.FreeSpace object at 0xb7635c8c>}'
2009-01-05 19:27:31,897 DEBUG linux-image-2.6.24-22-386 (new-install) added with 10485760 to boot space
2009-01-05 19:27:31,921 DEBUG linux-image-2.6.15-26-386 (upgrade|installed) added with 10485760 to boot space
2009-01-05 19:27:31,939 DEBUG linux-image-2.6.15-53-386 (upgrade|installed) added with 10485760 to boot space
2009-01-05 19:27:32,837 DEBUG dir '/var/cache/apt/archives' needs '845822566.0' of '<DistUpgradeController.FreeSpace object at 0xb7635c8c>' (142130311168.000000)
2009-01-05 19:27:32,838 DEBUG dir '/usr' needs '1195782144.0' of '<DistUpgradeController.FreeSpace object at 0xb7635c8c>' (141284488602.000000)
2009-01-05 19:27:32,838 DEBUG dir '/usr' needs '52428800' of '<DistUpgradeController.FreeSpace object at 0xb7635c8c>' (140088706458.000000)
2009-01-05 19:27:32,838 DEBUG dir '/boot' needs '31457280' of '<DistUpgradeController.FreeSpace object at 0xb7635c8c>' (140036277658.000000)
2009-01-05 19:27:32,838 DEBUG dir '/' needs '10485760' of '<DistUpgradeController.FreeSpace object at 0xb7635c8c>' (140004820378.000000)
2009-01-05 19:28:21,382 DEBUG setting MinAge to 10
2009-01-05 19:28:21,383 DEBUG no file '/etc/apt/apt.conf.d/25adept-archive-limits'
2009-01-05 20:25:57,943 INFO cache.commit()
2009-01-05 20:25:58,614 DEBUG removing bad script '/var/lib/dpkg/info/apache2-common.prerm'
2009-01-05 21:07:56,653 ERROR SystemError from cache.commit(): E:Sub-process /tmp/tmpnzexMq/backports/usr/bin/dpkg exited unexpectedly
2009-01-05 21:07:56,673 WARNING cache.commit() raised a SystemError but pkg_failures count is 0
2009-01-05 21:07:56,673 DEBUG running apport_pkgfailure() update-manager: SystemError in cache.commit(): E:Sub-process /tmp/tmpnzexMq/backports/usr/bin/dpkg exited unexpectedly
2009-01-05 21:31:49,890 DEBUG setting MinAge to 2
2009-01-05 21:31:49,908 DEBUG no file '/etc/apt/apt.conf.d/25adept-archive-limits'
2009-01-05 21:31:49,916 DEBUG Running PostInstallScript: '/usr/lib/udev/migrate-fstab-to-uuid.sh'
2009-01-05 21:31:50,205 ERROR SystemError from cache.commit(): installArchives() failed
2009-01-05 21:31:50,205 WARNING cache.commit() raised a SystemError but pkg_failures count is 0
2009-01-05 21:31:50,205 DEBUG running apport_pkgfailure() update-manager: SystemError in cache.commit(): installArchives() failed
2009-01-05 21:38:05,789 DEBUG setting MinAge to 2
2009-01-05 21:38:05,789 DEBUG no file '/etc/apt/apt.conf.d/25adept-archive-limits'
2009-01-05 21:38:05,789 DEBUG Running PostInstallScript: '/usr/lib/udev/migrate-fstab-to-uuid.sh'
```

This basically what happened when I tried to do an update from the graphical update manager but with lots of font problems.

Any more thoughts?

The system works at the moment but I fear a reboot may show up problems

Cheers

grognut

---

### Post by grognut on 2009-01-06
Well it rebooted OK and I re-installed the update manager using the package manager.

Seems OK now.

Is it possible to validate the update or is checking for updates OK?

Cheers

Grognut

---

