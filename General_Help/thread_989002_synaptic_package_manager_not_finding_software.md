---
title: "synaptic package manager not finding software"
date: 2008-11-21
forum: General Help
---

### Post by odysseus7m on 2008-11-21
desperately need help.  i'm new to linux but have been using ubuntu as my main OS for the past 5 months now, so im pretty familiar on how installing software should work. i just recently did a fresh reinstall of ubuntu 8.10. performed all the updates (i think there were 82) i then tried to install some software using synaptic but it cannot find the packages.  ironically the add/remove feature does find the software and installs but synaptic does not.  i am also able to install software via the terminal window via sudo apt-get install <program name>, but still synaptic cannot find the packages even after it has already been installed by other means. the search feature just has no returns.

here is some of the packages synaptic cannot find which i know should be available.
wine
clamav
madwifi-tools
opera
and others.

i will like to note the following:
universe/multiverse is checked and so is third party software under repositories
i have tried 4 different server locations including the main server
performed sudo apt-get update (and upgrade). no error messages
computer has been restarted several times.
synaptic package manager is set to search all and i have hit the reload button

if any other information is needed please ask. all suggestions are greatly appreciated.

---

### Post by woodenbrick on 2008-11-21
I know with Intrepid they included a new 'quick search' bar and maybe this is what is causing the problem, perhaps you have written in this bar? If you try to do a standard search after this then you end up only with results that have gone through the quick search.  

It happens to me sometimes and then takes me a while to figure out why nothing is showing up.

---

### Post by odysseus7m on 2008-11-21
no, this happens with the regular search to. the only good thing out of this is that now im forced to use the terminal window, but i still wish synaptic worked like it use to.

---

### Post by Peter09 on 2008-11-21
Are the filters (bottom left) set to ALL, if they were set to installed you would only see Installed programs.

---

### Post by odysseus7m on 2008-11-21
i think i found my own work around, i use work around because it doesnt fixes synaptic. its something wrong with that quick search. i closed synaptic opened it back up and instead of doing a quick search i went directly to normal search. it found everything i was looking for madwifi, opera, etc.

to test this out i closed then opened synaptic again. did a quick search for the same items and got 0 results. i then did a normal search and still got 0 results.

i then closed and reopened synaptic again, avoided quick search and went streight to the normal search option and was able to find the software i wanted. so im going to assume quick search totally breaks synaptic and i guess this problem is solved.

---

### Post by kindofabuzz on 2008-11-22
It's a known bug. [https://bugs.launchpad.net/ubuntu/+source/synaptic/+bug/288797](https://bugs.launchpad.net/ubuntu/+source/synaptic/+bug/288797)
do a ```
sudo update-apt-xapian-index
``` to fix it

---

### Post by Th3Professor on 2008-11-22
xapian update doesn't resolve this:
"The index /var/lib/apt-xapian-index is up to date"
...Opera browser, for example, still isn't showing in the package manager.
Was it actually *removed* from the apps list? That'd be absolutely silly. lol

---

### Post by Th3Professor on 2008-11-28
Is Opera no longer in Ubu's repo list?

---

