---
title: "Want to know what packages I installed."
date: 2009-01-28
forum: Installation &amp; Upgrades
---

### Post by 123Mike on 2009-01-28
I'd like to install a newer version of Ubuntu.
I don't wish to go the upgrade path, and wish to install a new fresh version.
I don't want to stumble for the next 3 months over package after package that's not installed by default. I'm not always on the internet, and thus can't run synaptic/apt-get once I disconnect.

Is it possible to extract all the installed package names, take those names with me to a newly installed Ubuntu, and that pass all those names to apt-get to install them all in one big go?

---

### Post by gettinoriginal on 2009-01-28
What packages are you talking about that are not default??  The only thing you would need from the internet are repositories for restricted or non supported applications.  May I suggest that sometime when you are online you check out this:
[http://ubuntuforums.org/showthread.php?t=801404](http://ubuntuforums.org/showthread.php?t=801404)

And Welcome to Ubuntu  :p

---

### Post by 123Mike on 2009-02-04
> **gettinoriginal said:**
> What packages are you talking about that are not default??  The only thing you would need from the internet are repositories for restricted or non supported applications.  May I suggest that sometime when you are online you check out this:
[http://ubuntuforums.org/showthread.php?t=801404](http://ubuntuforums.org/showthread.php?t=801404)

And Welcome to Ubuntu  :p

Thanks for the welcome, but instead of pointing me to a beginner forum, you could have just said something like:

dpkg-query -l | awk '{print $2}' >oldlist

Backup the oldlist file.
Then on the new installation, I put the oldlist file, and then:

dpkg-query -l | awk '{print $2}' >newlist
cat oldlist newlist | sort | uniq -u >addlist
apt-get install $(cat addlist)

Something like that.

---

### Post by gettinoriginal on 2009-02-04
Sorry, just a user here and made the mistake of thinking you needed help.

---

### Post by Bao2 on 2009-02-04
APTonCD will able you to create a .iso with all the packages you installed (if you didn't delete the cache in synaptic, I hope you no)

---

### Post by 123Mike on 2009-02-05
> **Bao2 said:**
> APTonCD will able you to create a .iso with all the packages you installed (if you didn't delete the cache in synaptic, I hope you no)

That's interesting.
However, the new Ubuntu install will have different versions of the packages. Also, I'm not 100% sure, but don't packages eventually get pushed out of this cache?
I'm looking at my cache dir, and I haven't deleted anything, yet I know I installed more than what I'm seeing in that cache dir.

---

