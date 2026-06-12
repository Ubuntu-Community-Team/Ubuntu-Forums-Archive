---
title: "[SOLVED] Why can't this be easy (Pidgin refuses to install)"
date: 2008-12-24
forum: Installation &amp; Upgrades
---

### Post by cabbiinc on 2008-12-24
Hey there. It's me again. It would appear that anything I do on this computer I would need the help of the forums to complete the tasks.

In a previous thread I asked how to install something. I was given so many commands I don't know which one solved the problem, or if I even installed something. In the course of events I exclaimed that this would be easier in Windows, and of course talking to a bunch of Linux guys I was told 'no it's not, Ubuntu's so much better'.

Well here I am, trying to do the very next thing and Pidgin refuses to work. And I searched the forums and read thread after thread that never really seamed to solve anything. Here's my situation.

In Applications > Add/Remove... I tried to check Pidgin. I got this error:
> Cannot install 'pidgin'

This application conflicts with other installed software. To install 'pidgin' the conflicting software must be removed first.

Switch to the 'synaptic' package manager to resolve this conflict.

So I went to synaptic package manager and tried to install it there. Here's what I got:
> Could not mark all packages for installation or upgrade

The following packages have unresolved dependancies.
Make sure that all required repositories are added and enabled in preferences.

pidgin:
 Depends: libpurple0 but it is not going to be installed

When I go to libpurple0 I get:
> libpurple0:
 Depends: libsilc-1.1-2  but it is not installable

So I try to go to libsilc-1.1-2 and there's nothing there.

Remind me again how this is easier than double clicking an exe file NEXT>NEXT>NEXT>NEXT>

---

### Post by Vadi on 2008-12-24
Well, debugging an issue isn't easier than a flawless installation. That should be obvious.

Anyway, try the packages from here: [http://www.getdeb.net/search.php?keywords=pidgin](http://www.getdeb.net/search.php?keywords=pidgin). Ideally, 1 package = 1 "install package" button = done, instead of clicking next and skipping all the options to configure ;)

However Ubuntu comes with Pidgin pre-installed, so not sure why did you remove it in the first place.

---

### Post by cabbiinc on 2008-12-24
> **Vadi said:**
> Well, debugging an issue isn't easier than a flawless installation. That should be obvious.

Anyway, try the packages from here: [http://www.getdeb.net/search.php?keywords=pidgin](http://www.getdeb.net/search.php?keywords=pidgin). Ideally, 1 package = 1 "install package" button = done, instead of clicking next and skipping all the options to configure ;)

However Ubuntu comes with Pidgin pre-installed, so not sure why did you remove it in the first place.

I never removed, it just refused to work. Went looking for it when I read it's better than Yahoo! Messenger.

I tried your link and see three downloads. If I try to install the Pidgin it comes up with an error. So which do I start with. Pidgin, Pidgin-Data, or Libpurple0? I don't want to screw up my system again is why I'm asking.

---

### Post by cabbiinc on 2008-12-24
By the way, I'm using Hardy Heron, 8.04.

---

### Post by zeronothing on 2008-12-24
first if you are using 8.10 you can upgrade pidgin to 2.5.3 this way:

first try uninstalling pidgin using synaptic. search for pidgin,pidgin-data, and libpurple0. select each one and choose remove. apply the changes and now your ready to install the newest pidgin. 

now go to the [www.getdeb.net](www.getdeb.net) website and search for the pidgin. on this website you will need to download three packages pidgin, pidgin-data, and libpurple0. I believe you need to install each package one at a time. it should go pidgin, libpurple0, pidgin-data. if you didnt know you can just double click each package to install them.

after those steps you should now have pidgin 2.5.3 installed. the most important part to the steps is to uninstall the original pidgin and the dependant packages along with it.

---

### Post by Vadi on 2008-12-24
> **cabbiinc said:**
> I never removed, it just refused to work. Went looking for it when I read it's better than Yahoo! Messenger.

I tried your link and see three downloads. If I try to install the Pidgin it comes up with an error. So which do I start with. Pidgin, Pidgin-Data, or Libpurple0? I don't want to screw up my system again is why I'm asking.

You can't screw up, it just won't let you install. Anyway I think it's data, libpurple, and pidgin.

(I'll agree with you that the enforced order isn't nice. :()

---

### Post by cabbiinc on 2008-12-24
> **zeronothing said:**
> first if you are using 8.10 you can upgrade pidgin to 2.5.3 this way:

first try uninstalling pidgin using synaptic. search for pidgin,pidgin-data, and libpurple0. select each one and choose remove. apply the changes and now your ready to install the newest pidgin. 

now go to the [www.getdeb.net](www.getdeb.net) website and search for the pidgin. on this website you will need to download three packages pidgin, pidgin-data, and libpurple0. I believe you need to install each package one at a time. it should go pidgin, libpurple0, pidgin-data. if you didnt know you can just double click each package to install them.

after those steps you should now have pidgin 2.5.3 installed. the most important part to the steps is to uninstall the original pidgin and the dependant packages along with it.

I got the downloads from that site. I just downloaded them because if I just click install and it don't work then the next time I have to install again.

As stated before the Pidgin just will not install. I can install the Pidgin-Data but the other two refuse to install.

Error with Pidgin:
```
Error dependency is not satisfiable: libpurple0
```

When I try to install libpurple0 I get
```
Error: Dependency is not satisfiable: libsilc-1.1-2
```

I've tried both before installing Pidgin-data and after installing Pidgin-Data

---

### Post by cabbiinc on 2008-12-24
> **Vadi said:**
> You can't screw up, it just won't let you install. Anyway I think it's data, libpurple, and pidgin.

(I'll agree with you that the enforced order isn't nice. :()

I tried installing a flashplayer plug-in for Firefox and it seamingly uninstalled FF. Then it wouldn't let me install it because it was already installed but it wouldn't let me uninstall it since it wasn't installed. I don't want to go through that again.

Turns out it ruined the path for the icon to start FF, but it took quite a bit of digging to figure that out.

I tried to update FF from FF2 to FF3, was told that it wouldn't work well since I was using Ubuntu 7.10.
I tried to update Ubuntu, but it wouldn't do it over the net (I had internet connection just no browser). So I burned an alternative CD from another computer.
I updated Ubuntu, that didn't fix it.
I updated FF, that didn't fix it.
I uninstalled, that didn't fix it. 
I removed completely and reinstalled and that didn't fix it.
Finally someone suggested I look at the path for the icon and change that. That finally fixed it.

---

### Post by sledhead45 on 2008-12-24
It seems like maybe a bad update was pushed out in the last day or so? I've had pidgin running fine even a few hours ago. I then applied whatever updates the update manager told me to. I got this error with the update:

```
E: /var/cache/apt/archives/perl_5.8.8-12ubuntu0.3_i386.deb: corrupted filesystem tarfile - corrupted package archive
E: /var/cache/apt/archives/perl-base_5.8.8-12ubuntu0.3_i386.deb: corrupted filesystem tarfile - corrupted package archive
```

Similarly when trying to reinstall pidgin with apt-get:

```
Unpacking replacement perl ...
dpkg: error processing /var/cache/apt/archives/perl_5.8.8-12ubuntu0.3_i386.deb (--unpack):
 corrupted filesystem tarfile - corrupted package archive
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Preparing to replace perl-base 5.8.8-12 (using .../perl-base_5.8.8-12ubuntu0.3_i386.deb) ...
Unpacking replacement perl-base ...
dpkg: error processing /var/cache/apt/archives/perl-base_5.8.8-12ubuntu0.3_i386.deb (--unpack):
 corrupted filesystem tarfile - corrupted package archive
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/perl_5.8.8-12ubuntu0.3_i386.deb
 /var/cache/apt/archives/perl-base_5.8.8-12ubuntu0.3_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

It seems unlikely and I've never seen this before, but I have no other explination myself. wtf?

---

### Post by cabbiinc on 2008-12-24
> **sledhead45 said:**
> It seems like maybe a bad update was pushed out in the last day or so? I've had pidgin running fine even a few hours ago. I then applied whatever updates the update manager told me to. I got this error with the update:

```
E: /var/cache/apt/archives/perl_5.8.8-12ubuntu0.3_i386.deb: corrupted filesystem tarfile - corrupted package archive
E: /var/cache/apt/archives/perl-base_5.8.8-12ubuntu0.3_i386.deb: corrupted filesystem tarfile - corrupted package archive
```

Similarly when trying to reinstall pidgin with apt-get:

```
Unpacking replacement perl ...
dpkg: error processing /var/cache/apt/archives/perl_5.8.8-12ubuntu0.3_i386.deb (--unpack):
 corrupted filesystem tarfile - corrupted package archive
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Preparing to replace perl-base 5.8.8-12 (using .../perl-base_5.8.8-12ubuntu0.3_i386.deb) ...
Unpacking replacement perl-base ...
dpkg: error processing /var/cache/apt/archives/perl-base_5.8.8-12ubuntu0.3_i386.deb (--unpack):
 corrupted filesystem tarfile - corrupted package archive
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/perl_5.8.8-12ubuntu0.3_i386.deb
 /var/cache/apt/archives/perl-base_5.8.8-12ubuntu0.3_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

It seems unlikely and I've never seen this before, but I have no other explination myself. wtf?

A bad update would explain it. I'll put this on the back burner until sometime after Christmas.

Cheers!
Merry Christmas, Happy Holidays, and Season's Greetings.

---

### Post by Vadi on 2008-12-24
> **sledhead45 said:**
> It seems like maybe a bad update was pushed out in the last day or so? I've had pidgin running fine even a few hours ago. I then applied whatever updates the update manager told me to. I got this error with the update:

```
E: /var/cache/apt/archives/perl_5.8.8-12ubuntu0.3_i386.deb: corrupted filesystem tarfile - corrupted package archive
E: /var/cache/apt/archives/perl-base_5.8.8-12ubuntu0.3_i386.deb: corrupted filesystem tarfile - corrupted package archive
```

Similarly when trying to reinstall pidgin with apt-get:

```
Unpacking replacement perl ...
dpkg: error processing /var/cache/apt/archives/perl_5.8.8-12ubuntu0.3_i386.deb (--unpack):
 corrupted filesystem tarfile - corrupted package archive
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Preparing to replace perl-base 5.8.8-12 (using .../perl-base_5.8.8-12ubuntu0.3_i386.deb) ...
Unpacking replacement perl-base ...
dpkg: error processing /var/cache/apt/archives/perl-base_5.8.8-12ubuntu0.3_i386.deb (--unpack):
 corrupted filesystem tarfile - corrupted package archive
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/perl_5.8.8-12ubuntu0.3_i386.deb
 /var/cache/apt/archives/perl-base_5.8.8-12ubuntu0.3_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

It seems unlikely and I've never seen this before, but I have no other explination myself. wtf?

Try updating your pidgin from here then: [http://www.getdeb.net/search.php?keywords=pidgin](http://www.getdeb.net/search.php?keywords=pidgin)

---

### Post by sledhead45 on 2008-12-27
Seems like I just got some bad .deb in the update. I went into /var/cache/apt/archives/ and deleted the .deb packages mentioned in the error messages, then did the update again which re-downloaded the .deb's and the install went fine. Hopefully this helps someone

--travis

---

### Post by cabbiinc on 2008-12-28
> **sledhead45 said:**
> Seems like I just got some bad .deb in the update. I went into /var/cache/apt/archives/ and deleted the .deb packages mentioned in the error messages, then did the update again which re-downloaded the .deb's and the install went fine. Hopefully this helps someone

--travis

I don't know how to do that.

---

### Post by lykwydchykyn on 2008-12-28
> **cabbiinc said:**
> I don't know how to do that.

This command will clear out any downloaded .debs:
> 
sudo apt-get clean


If you prefer a GUI solution, you can do it in synaptic by opening "preferences" and going to the "file" tab, where you'll find a button to delete the cached files.

---

### Post by Cope57 on 2008-12-28
> [ubuntu] Why can't this be easy (Pidgin refuses to install)

It is actually really easy...

It was already preinstalled with Ubuntu, now what did you do to break it?

If all else fails, use [another distribution]("http://distrowatch.com") instead of Ubuntu.

---

### Post by cabbiinc on 2008-12-28
> **Cope57 said:**
> It is actually really easy...

It was already preinstalled with Ubuntu, now what did you do to break it?

If all else fails, use [another distribution]("http://distrowatch.com") instead of Ubuntu.

The preinstalled version is the one I'm having problems with. I do everything thats posted that you should do and I have problems. I'm apparently not the only one.

"If all else fails use another distribution instead of Ubuntu"
Do you trade your car in when it only needs a tune-up?

---

### Post by cabbiinc on 2008-12-28
> **lykwydchykyn said:**
> This command will clear out any downloaded .debs:


If you prefer a GUI solution, you can do it in synaptic by opening "preferences" and going to the "file" tab, where you'll find a button to delete the cached files.

So I did the sudo apt-get clean and then reinstalled the three .deb files. Worked like a charm.

Thanks

---

### Post by Vadi on 2008-12-28
> **cabbiinc said:**
> "if all else fails use another distribution instead of ubuntu"
do you trade your car in when it only needs a tune-up?

+1

---

