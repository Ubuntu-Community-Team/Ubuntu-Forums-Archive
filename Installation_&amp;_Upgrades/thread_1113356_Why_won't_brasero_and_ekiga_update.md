---
title: "Why won't brasero and ekiga update?"
date: 2009-04-01
forum: Installation &amp; Upgrades
---

### Post by Bob Howland on 2009-04-01
I installed the beta copy of 9.04 about a week ago and it seems to be running just fine. I'm getting a slew of distribution updates every time I log in, of which two, brasero and ekiga, always have new packages waiting. However, I can't select them for update and they never are removed from update manager listing.

Is anybody else having this problem? Does anybody know how to clear it up?

Thanks

---

### Post by lindsay7 on 2009-04-01
I saw this and tried it today. It seemed to work.

Type sudo aptitude full-upgrade in the terminal

---

### Post by cmschoonbee on 2009-04-03
I have the same issue.  If I compare the installed versions with the upgradeable versions using ```
apt-cache policy *package-name*
```, I get the following output:
```
chris@jaunty-amd:~$ apt-cache policy brasero
brasero:
  Installed: 0.8.4-0ubuntu1
  Candidate: 2.26.0-0ubuntu3
  Version table:
     2.26.0-0ubuntu3 0
        500 http://za.archive.ubuntu.com jaunty/main Packages
 *** 0.8.4-0ubuntu1 0
        100 /var/lib/dpkg/status
chris@jaunty-amd:~$ apt-cache policy ekiga
ekiga:
  Installed: 3.0.1-1ubuntu1
  Candidate: 3.2.0-0ubuntu1
  Version table:
     3.2.0-0ubuntu1 0
        500 http://za.archive.ubuntu.com jaunty/main Packages
 *** 3.0.1-1ubuntu1 0
        100 /var/lib/dpkg/status

```

As you can see, there are significant version changes involved, not just the usual minor version upgrade.  It appears that update-manager will not update across such big version jumps, probably because there may be implications such as backward compatibility of data formats, config files etc.


The aptitude full-upgrade option recommended by lindsay7 would seem to force the upgrade.  

Update: What I did instead was use synaptic.  I just found and clicked on the brasero and ekiga packages, choosing the option to upgrade them and this seems to have worked fine.

---

### Post by JoseReyes on 2009-04-03
> **cmschoonbee said:**
> I have the same issue.  If I compare the installed versions with the upgradeable versions using ```
apt-cache policy *package-name*
```, I get the following output:
```
chris@jaunty-amd:~$ apt-cache policy brasero
brasero:
  Installed: 0.8.4-0ubuntu1
  Candidate: 2.26.0-0ubuntu3
  Version table:
     2.26.0-0ubuntu3 0
        500 http://za.archive.ubuntu.com jaunty/main Packages
 *** 0.8.4-0ubuntu1 0
        100 /var/lib/dpkg/status
chris@jaunty-amd:~$ apt-cache policy ekiga
ekiga:
  Installed: 3.0.1-1ubuntu1
  Candidate: 3.2.0-0ubuntu1
  Version table:
     3.2.0-0ubuntu1 0
        500 http://za.archive.ubuntu.com jaunty/main Packages
 *** 3.0.1-1ubuntu1 0
        100 /var/lib/dpkg/status

```

As you can see, there are significant version changes involved, not just the usual minor version upgrade.  It appears that update-manager will not update across such big version jumps, probably because there may be implications such as backward compatibility of data formats, config files etc.


The aptitude full-upgrade option recommended by lindsay7 would seem to force the upgrade.  

Update: What I did instead was use synaptic.  I just found and clicked on the brasero and ekiga packages, choosing the option to upgrade them and this seems to have worked fine.

Worked for me too... Thanks..... Ubuntu Jaunty 32bits

---

### Post by timandjulz on 2009-06-09
Bingo.  This has been bugging me since I upgraded to Jaunty.

Works on Jaunty 64bit

```
sudo apt-get update
sudo aptitude full-upgrade

```

Thanks to lindsay7!

---

