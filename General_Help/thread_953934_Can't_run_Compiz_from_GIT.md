---
title: "Can't run Compiz from GIT"
date: 2008-10-20
forum: General Help
---

### Post by nazgul42 on 2008-10-20
I am running Ubuntu Hardy (8.04) with GNOME
I am trying to download and install compiz from GIT, and it is not working.  I have tried 3 different scripts now, one of which has worked a long time ago for me.  Even though the Compiz GIT page shows that nothing is wrong with compiz at this time, whenever I try to install Compiz from GIT it gives this error message:
```
regex.c:217: warning: nested extern declaration of ‘regcomp’
regex.c:217: error: ‘REG_NOSUB’ undeclared (first use in this function)
regex.c:217: error: invalid operands to binary |
regex.c:222: warning: implicit declaration of function ‘regerror’
regex.c:222: warning: nested extern declaration of ‘regerror’
make[2]: *** [regex.lo] Error 1
make[2]: Leaving directory `/home/mitchell/.git4cf/compiz/plugins'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/mitchell/.git4cf/compiz'
make: *** [all] Error 2

```
Also, if I don't really know how to install the non-GIT version of Compiz, because if I try that, none of the windows have title bars, ccsm doesn't work, and lots of other problems, so what am I doing wrong?

---

### Post by loomsen on 2008-10-20
```

wget http://download.tuxfamily.org/shames/A42A6CF5.gpg -O- | apt-key add -

```
Then add this line to your /etc/apt/sources.list, open it up by typing ```
gksu gedit /etc/apt/sources.list
```
```

deb http://download.tuxfamily.org/shames/debian-sid/desktopfx/unstable/ ./

```

Then run ```
sudo apt-get update && sudo apt-get install compiz-fusion-all
```

If it doesn't work on your next boot, make sure you added fusion-icon to your startup applications in system-->preferences-->sessions.

---

### Post by nazgul42 on 2008-10-21
OK, when I try to install compiz-fusion-all I get the error:
```
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  compiz-fusion-all: Depends: compiz-gnome (>= 0.7.9) but it is not going to be installed
E: Broken packages
```

---

### Post by loomsen on 2008-10-21
You have to completely remove everything compiz related.

```
apt-get update && sudo apt-get check 
```

To fix your system.

Then make sure you removed everything, I mean really everything compiz related from your system.

Use apt-get purge PKGNAME to do so.

Then run the steps above.

---

### Post by nazgul42 on 2008-10-22
I think I have removed all compiz stuff from my PC, but that still happens.  Also, if I try to install compiz-gnome, it gives me a compiz-gnome: Depends: libpopt0 error, and I don't want to uninstall libpopt0
Man, this is turning into a mess...

---

### Post by borlosky on 2008-11-12
i ran into similar issues with installing compiz from get. to get working i had to first remove all compiz software from add/remove, then went to synaptic, removed ALL compiz software/settings/libraries. then after all that was done, installed compiz from git, and all working 100% now.

---

