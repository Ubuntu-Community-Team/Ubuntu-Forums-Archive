---
title: "Locked packages listed in Update Manager"
date: 2009-09-01
forum: Installation &amp; Upgrades
---

### Post by Sfinx- on 2009-09-01
Hello,

I am running Ubuntu Karmic since a few weeks. In order to use a specific application, I had to lock my SVN packages (subversion, libsvn...) to an earlier version (in the Synaptic Package Manager).

However, when I run the Update Manager, it still lists the packages above as to-be-updated. I have no option to deselect them.

I have ran "aptitude hold <package-name>" for all of these but that didn't seem to work. Is there any other way I can update my system or use the Update Manager without overwriting these packages?

---

### Post by slakkie on 2009-09-01
Pinning. If you want the current version and not upgrade:

```

dpkg2pin () {
        [ -z "$1" ] && return
        local pkg
        pkg=$(dpkg -l | grep "^ii" |awk '{print $2" "$3}' | grep "$1")
        [ $? -ne 0 ] && return
        local msg
        msg="$(date +'%Y%m%d:%H%M%S')"
        echo -e "$pkg" | awk '{print "\nExplanation: Added on '$msg' by dpkg2pin\nPackage: "$1"\nPin: version "$2"\nPin-Priority: 1001\n"}' | sudo tee -a /etc/apt/preferences
}

```

Since this script actually pins all packages which have the searched value it might pin a bit too much, but you can change the preferences file afterwards.

Google for debian/ubuntu pinning for more information.

---

### Post by gnuyoga on 2009-09-01
google search for your query returns a lot of results
[http://ln-s.net/45dV](http://ln-s.net/45dV)

I suggest you should look for already filed bugs, if not create a new one 

Ubuntu Bug tracker: [https://launchpad.net/ubuntu/+bugs](https://launchpad.net/ubuntu/+bugs)

---

### Post by Sfinx- on 2009-09-01
Obviously I already googled my problem and didn't find a proper solution. Otherwise I wouldn't have started this thread!

I have found the bug listed a few times, though no solution listed anywhere. But I can imagine there are plenty users out there with the same issue that might have a temporary fix. So far I wasn't able to find one.

---

### Post by arpanaut on 2009-09-01
Your question might be better answered here:

[http://ubuntuforums.org/forumdisplay.php?s=&daysprune=&f=359](http://ubuntuforums.org/forumdisplay.php?s=&daysprune=&f=359)

The Karmic Testing Forum.

---

### Post by Sfinx- on 2009-09-01
Well, it's a known issue from years ago and hasn't been fixed since, but I guess it's worth a shot.

---

### Post by Sfinx- on 2009-09-02
I finally found a quickfix for this issue:

[http://ubuntuforums.org/showthread.php?t=43631](http://ubuntuforums.org/showthread.php?t=43631)

In short:

sudo apt-get install wajig
sudo wajig hold <package>

This thread can be set to resolved!

---

