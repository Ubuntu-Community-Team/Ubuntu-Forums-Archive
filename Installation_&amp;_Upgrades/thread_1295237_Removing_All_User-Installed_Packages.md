---
title: "Removing All User-Installed Packages"
date: 2009-10-19
forum: Installation &amp; Upgrades
---

### Post by dgposey on 2009-10-19
I'm looking to remove all user-installed packages on a lab-full of Jaunty machines, most of which dual boot also into Windows XP.  What I mean by this is that I wish to have what is, essentially, a clean install of Jaunty, with (and only with) the same packages that were existent when I installed the OS to begin with.  Ideally, I would like to have the same versions of the packages as when they were installed, too.

Why am I doing this, you ask?  When I initially installed Jaunty to this lab, I was using [Keryx]("http://www.keryxproject.org") to update the lab.  (I live in a rural part of a developing country, and would travel to the capital city to download the updates and new software.)  I have since, however, obtained a copy of the entire Jaunty repository, a little outdated, from an NGO, which I keep on an external hard drive.  Using this now on these machines, I have run into dependency problems, which I believe to be the result of using a not-fully updated repository on my external HD.  I plan, in the future (after reverting to the original package state) to only use the repos on my HD, hopefully periodically updated.

I am, of course, comfortable using either Synaptic or apt-get, though I would prefer to be able to build a script using apt-get, to speed up the process throug the entire lab.

Thanks in advance for any suggestions.

--David

---

### Post by SaintDanBert on 2009-10-19
I have Synaptic v0.61ubuntu9 and do not see any sort of search by date.
QUESTION: Does anyone know how to get Synaptic to search by date? For example, "show me packages installed after XXX and before YYY"

My Ubuntu Hardy (v8.04.3 LTS) has files **/var/log/dpkg.log** that show things that have happened. These are subject to your log roll-up processing so you might not have them all.

My last resort is to use **find ...** to discover packages installed after some historical date.

Please post your results because I think others -- like your humble servant -- would welcome the information.

~~~ 0;-Dan

---

### Post by Mark Phelps on 2009-10-21
In Synaptic, if you do File --> History, you get a panel on the left where you can select a month, and then a date.  The panel on the right will then show all the packages installed on that date.

Sorry, but apart from cut-and-paste using the information in the right panel into a text file, I don't know any way to export the information from Synaptic by date.

---

### Post by sea_monkey987 on 2009-10-25
how about using debfoster?  i think the default packages that you would want to keep with debfoster are (thanks to [http://ubuntuforums.org/showpost.php?p=4887531&postcount=65](http://ubuntuforums.org/showpost.php?p=4887531&postcount=65) for the first four)
```

linux-generic linux-headers-generic ubuntu-minimal ubuntu-standard ubuntu-desktop

```

for all the other packages, just say 'p' (for purge) and it will delete the package and all of its exclusive dependencies

---

