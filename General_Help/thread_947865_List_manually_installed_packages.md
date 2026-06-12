---
title: "List manually installed packages?"
date: 2008-10-14
forum: General Help
---

### Post by kwilliam on 2008-10-14
So I'm planning on doing a clean install for 8.10 when it comes out. Only I want to know what all I've installed on my current system. I know dpkg --get-selections will list packages, but a lot of those are automatically installed dependencies. Apt keeps track of which packages were manually installed, because it tells me when there are cruft packages and I should run "apt-get autoremove". I've found two different ways of doing this but I'm not sure if either is right...

Using APT:
```
cat /var/lib/apt/extended_states | grep -B 1 "Auto-Installed: 0" | grep "Package" | sed "s/Package: //"|sort > apt_manually-installed_packages.txt
```

Using aptitude:
```
aptitude -F "%p" search \!~M~i~T > aptitude_manually-installed_packages.txt
```

Unfortunately, both methods return completely different lists of packages which don't overlap. The aptitude list seems to include lots of libraries that I certainly didn't install manually, while the apt list seems far too short, only including KDE4 stuff. Is there a tool that can analyze the dependencies, and find all the packages that are not depended on by any other package, and thus probably manually installed? Or seriously, what is the best way to do this? Does apt-get have a way to list packages that were automatically installed?

---

### Post by mssever on 2008-10-15
This is an issue that I've worked on off and on. To my knowledge, there are no tools to do this, and I've made several starts at writing a program to make such a list. So far, I don't have any working code.

Here's the algorithm I propose:

[LIST=1]
[*]Parse /var/lib/dpkg/status. Store the name (e.g., in an array) of every package where line 2 is "Status: install ok installed"
[*]Parse /var/lib/apt/extended_states, and discard from the array every package that has an "Auto-Installed: 1" entry.
[*]What remains is the list you need.
[/LIST]
I'm asking this thread to be moved to the Programming Talk forum since you'll probably get better help there--given that there isn't already a program that does what you need.

---

### Post by Hendrik0 on 2009-05-31
This is something I always wanted. With your info provided, I managed to set up working code that implements your algorithm:

```
comm -23 <(cat /var/lib/dpkg/status | sed -n "/Package/N;s/Package: \(.*\)\n.*install ok installed/\1/p" | sort) <(cat /var/lib/apt/extended_states | sed -n "/Package/N;s/Package: \(.*\)\nAuto-Installed: 1/\1/p" | sort)
```

The output is promising, but still the list includes many packages I know I haven’t installed manually. I have checked that those do not appear in extended_states, so they seem to have been installed automatically, but not by apt, my guess is during dist-upgrade.

---

### Post by Hendrik0 on 2009-05-31
Just noticed, the output is identical to the output of

```
aptitude -F "%p" search \!~M~i~T

```

except that the latter includes those packages marked with "Essential: yes" in line 2 in dpkg/status (which on my system is only 24).

---

### Post by Andreas1 on 2009-08-06
has there been any progress on this topic? this would be soo useful.

obviously there is still some information missing between var/lib/dpkg/status and var/lib/apt/extended_states that is elsewhere, otherwise apt-get autoremove wouldn't work, right?

---

### Post by martinbaselier on 2009-08-06
If you've got a list with installed packages you can easily use apt-get or aptitude to install them all. If they're already installed it won't matter, since they will be ignored then.

---

### Post by Cheesemill on 2009-08-06
Have a look at post #2 I made here:
[http://ubuntuforums.org/showthread.php?t=1194291](http://ubuntuforums.org/showthread.php?t=1194291)
 
You'll only want to use the installedpackages.sh script, not the apt-get purge and apt-get autoremove commands :)

---

### Post by Andreas1 on 2009-08-06
> **Cheesemill said:**
> Have a look at post #2 I made here:
[http://ubuntuforums.org/showthread.php?t=1194291](http://ubuntuforums.org/showthread.php?t=1194291)
 
You'll only want to use the installedpackages.sh script, not the apt-get purge and apt-get autoremove commands :)

thanks, that one is close, but still:

packages i remember to have installed that are not listed:

compizconfig-settings-manager
exfalso
firefox-3.5
grsync
network-manager-pptp
rox-filer
sauerbraten
sylpheed
ubuntu-restricted-extras

packages i am quite sure i didn't manually install that are listed:

gstreamer0.10-ffmpeg
gstreamer0.10-pitfdll
gstreamer0.10-plugins-bad
gstreamer0.10-plugins-bad-multiverse
gstreamer0.10-plugins-ugly
gstreamer0.10-plugins-ugly-multiverse
linux-headers-2.6.28-13
linux-headers-2.6.28-13-generic
linux-headers-2.6.28-14
linux-headers-2.6.28-14-generic
linux-image-2.6.28-13-generic
linux-image-2.6.28-14-generic
ttf-mscorefonts-installer
unrar

apart from the linux packages these are dependancies of (well, not really, they are recommended by) ubuntu-restricted-extras

---

### Post by alexgirao on 2010-09-11
hi, with all your help i came to this (and solved my problem):

```

detect all packages installed since a specified date::

    fgrep ' status installed ' /var/log/dpkg.log | sort | awk '{if (substr($0, 1, 19) >= "2010-09-01 00:00:00") {print $5;}}' | sort | uniq > tmp-installed-after

detect all packages installed before the specified date::

    fgrep ' status installed ' /var/log/dpkg.log | sort | awk '{if (substr($0, 1, 19) < "2010-09-01 00:00:00") {print $5;}}' | sort | uniq > tmp-installed-before

detect all packages officially marked as auto-installed::

    fgrep -B1 "Auto-Installed: 1" /var/lib/apt/extended_states | fgrep "Package: " | sed "s/Package: //" | sort > tmp-autoinstalled

compute manually installed packages since the specified date::

    comm -23 tmp-installed-after <(sort tmp-installed-before tmp-autoinstalled | uniq)

```
p.s.: the date i choose was the date right after os installation


many thanks

---

### Post by cgroza on 2010-09-11
I think in synaptic there is a filter for that.

---

### Post by beanluc on 2011-07-24
Well, I just looked in my .bash_history for "apt-get install"

---

### Post by krack3rz on 2011-11-19
> **beanluc said:**
> Well, I just looked in my .bash_history for "apt-get install"

This will only work if you set your history profile to unlimited since the beginning, sadly for me I hadn't, but good idea.

I cant believe there isnt a built in utility for apt or dpkg that does this at the core level.
How does software-center or synaptic get their info on what you installed when and ESPECIALLY synaptic having the ability for you to list installed stuff by "Installed (Manual)"!!!
:lolflag:


That right there should be the road to walk down to find out how its done there, finally yielding the solution.

Anyone know how Synaptic does it?

---

### Post by krack3rz on 2011-11-19
Actually the list isn't so "Manual" as it suggests, it seems like it includes some things that weren't manually installed...

Also it includes libraries that are parts of packages which contained multiple such installed stuffs.

Moving on...

---

